![Validate with hassfest](https://github.com/youdroid/home-assistant-couchpotato/workflows/Validate%20with%20hassfest/badge.svg)
![HACS Validate](https://github.com/youdroid/home-assistant-couchpotato/workflows/HACS%20Validate/badge.svg)
[![hacs_badge](https://img.shields.io/badge/HACS-Default-orange.svg)](https://github.com/hacs/integration)

# CouchPotato Wanted And Already Downloaded Movies

Home Assistant component to feed Upcoming Media Card with Couchpotato's recently downloaded media, and wanted media.

## Installation
1. Install this component by copying [these files](https://github.com/youdroid/home-assistant-couchpotato/tree/master/custom_components/couchpotato) to `custom_components/couchpotato/`.
2. Install the card: [Upcoming Media Card](https://github.com/custom-cards/upcoming-media-card)
3. Add the code to your `configuration.yaml` using the config options below.
4. Add the card code to your `ui-lovelace.yaml`. 
5. **You will need to restart after installation for the component to start working.**

### Options

| key | default | required | description
| --- | --- | --- | ---
| name | coachpotato | no | Name of the sensor.
| token | | yes | Your CouchPotato token [(Find your CouchPotato token)](https://github.com/youdroid/home-assistant-couchpotato/wiki/Get-your-CouchPotato-Token)
| host | localhost | no | The host which CouchPotato is running on.
| port | 5050 | no | The port which CouchPotato is running on.
| protocol | http | no | The HTTP protocol used by CouchPotato.
| max | 10 | no | Max number of items to show in sensor.
| state | active | no | Defines the state of movies that you want to follow **[active or done]**
| sort | name | no | Parameter to sort your movies **[name or date]**

## Exemples

### Example for minimal config needed in configuration.yaml:
```yaml
    sensor:
    - platform: couchpotato
      token: YOUR_COUCHPOTATO_TOKEN
```
### Example for ui-lovelace.yaml:
```yaml
    - type: custom:upcoming-media-card
      entity: sensor.couchpotato
      title: Wanted movies
```
### Multiple sensor example for configuration.yaml:
```yaml
  - platform: couchpotato
    name: Wanted movies
    token: !secret token
    host: !secret host
    port: 5050
    protocol: 'http'
    state: 'active'

  - platform: couchpotato
    name: Downloaded movies
    token: !secret token
    host: !secret host
    port: 5050
    protocol: 'http'
    state: 'done'
```
