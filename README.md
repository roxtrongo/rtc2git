[![Build Status](https://travis-ci.org/rtcTo/rtc2git.svg)](https://travis-ci.org/rtcTo/rtc2git)
[![Supported Versions](https://img.shields.io/badge/python-3.4%2C%203.5%2B-blue.svg)](https://travis-ci.org/rtcTo/rtc2git)
[![MIT License](https://img.shields.io/badge/license-MIT-orange.svg)](https://github.com/rtcTo/rtc2git/blob/develop/LICENSE)

# rtc2git

Una herramienta creada para migrar código e historial de códigos desde un repositorio SCM [RTC] (https://jazz.net/products/rational-team-concert/) existente en un repositorio Git.
Utiliza la CLI de RTC para recopilar la información requerida.

## Prerequirements

- RTC Server versión 5.0+ 
- **[SCM Tools](https://jazz.net/downloads/rational-team-concert/releases/5.0.1?p=allDownloads)
- Python 3.4+ (no funciona con versiones previas de o con Python 2)

## Development-Status

Este repositorio es un fork de un proyecto que ya no se encuentra en desarrollo activo.

Este proyecto ya no está en desarrollo activo, porque el autor ya no tiene acceso a ningún servidor RTC (ya que se migraron a git) y los cambios en el código solo se pueden probar.

## Uso

- Crea un archivo de configuración llamado `config.ini` y completa la información necesaria, utiliza` config.ini.sample` o `config.ini.minimum.sample` provistos como referencia
- Ejecute `migration.py`


### Pitfalls

- No se permite que su flujo de trabajo o espacio de trabajo tenga espacios en su nombre. En caso de que su nombre contenga espacios, clone y cámbieles el nombre y utilice el espacio de trabajo / flujo clonado para la migración (consulte [# 104] (https://github.com / rtcTo / rtc2git / issues / 104), [# 51] (https://github.com/rtcTo/rtc2git/issues/51)).

- A veces rtc2git no puede determinar ninguna línea de base y no encontrará ningún cambio (aceptando conjuntos de cambios 0) - Consulte la entrada de configuración de UseProvidedHistory explicada [aquí] (https://github.com/rtcTo/rtc2git/wiki/Getting-your-History- Archivos)

- El resultado proporcionado del comando de comparación de la API CLI de IBM RTC a veces no proporciona los conjuntos de cambios en el orden completamente correcto. Esto puede provocar conflictos de combinación, que deben resolverse cargando el espacio de trabajo en eclipse, resuélvalos manualmente y reanudando la migración ejecutando el rtc2git nuevamente.

## ¿Como funciona?

1. Inicializa un repositorio de git vacío y lo clona
2. En este repositorio, carga una nueva creación (que se establecerá en la línea base más antigua posible) o espacio de trabajo rtc existente
3. La línea de base de cada componente de un flujo determinado se determina
4. Para cada línea base, se ejecutará un comando de comparación
5. El resultado de la comparación se analizará para obtener la información de confirmación necesaria (como autor, comentario, fecha)
6. El cambio será aceptado en el área de trabajo
7. El comando git correspondiente se ejecutará para hacer el mismo cambio en el repositorio git

## Contribuye

Bienvenido todo tipo de Feedback! :)


### Pull-Requests

1. [Fork it](https://github.com/rtcTo/rtc2git#fork-destination-box)
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

