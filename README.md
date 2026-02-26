# UbiBot WS-1 Integration for Home Assistant

[![hacs_badge](https://img.shields.io/badge/HACS-Custom-orange.svg)](https://github.com/custom-components/hacs)
[![GitHub release](https://img.shields.io/github/release/richardctrimble/ha-ubibot-ws1.svg)](https://github.com/richardctrimble/ha-ubibot-ws1/releases/)

A custom Home Assistant integration for [UbiBot WS-1](https://www.ubibot.com/) environmental monitoring devices. Data is fetched from the UbiBot cloud API, so your device must be online and reporting to UbiBot's servers.

## Sensors

### Measurement Sensors

| Sensor | Unit | Description |
|---|---|---|
| Temperature | °C | Ambient temperature |
| Humidity | % | Relative humidity |
| Light | lx | Light intensity |
| Voltage | V | Device battery/power voltage |
| WiFi Signal Strength | dBm | WiFi signal strength |
| Vibration Index | — | Vibration level |
| Knock Count | — | Detected knocks |
| Data Traffic Out | kB | Outbound data traffic |
| Data Traffic In | kB | Inbound data traffic |

### Diagnostic Sensors

The integration also exposes the following as diagnostic entities:

- MAC Address
- Last Data Update (timestamp)
- Activation Date (timestamp)
- Firmware Version
- Device ID
- Serial Number
- IP Address
- Service Plan
- Total Data Usage (kB)
- Entry ID
- WiFi Network (SSID)
- USB Power (on/off)

## Installation

### HACS (Recommended)

1. Open HACS in your Home Assistant instance
2. Go to **Integrations**
3. Click the three dots in the top right corner and select **Custom repositories**
4. Add `https://github.com/richardctrimble/ha-ubibot-ws1` with category **Integration**
5. Search for **UbiBot WS-1** and install it
6. Restart Home Assistant

### Manual

1. Download the latest release from the [releases page](https://github.com/richardctrimble/ha-ubibot-ws1/releases)
2. Copy all files into your `custom_components/ha_ubibot_ws1` directory
3. Restart Home Assistant

## Configuration

1. Go to **Settings** > **Devices & Services**
2. Click **Add Integration**
3. Search for **UbiBot WS-1**
4. Enter your credentials:
   - **API Key** — Your Channel Read API Key (found on the channel page under **API Keys** in the [UbiBot console](https://console.ubibot.com/))
   - **Channel ID** — Your device's channel ID (the numeric ID visible in the UbiBot web interface URL)

## Options

After setup, you can adjust the polling interval under the integration's options:

- **Update Interval** — How often to fetch data from the UbiBot API (1–60 minutes, default: 2 minutes)

## Troubleshooting

**"Cannot connect" error:**
- Verify your API key is a valid Channel Read API Key
- Check that your channel ID exists and the device is online

**Sensors showing "unavailable":**
- Confirm your device is actively sending data to UbiBot
- Check the Home Assistant logs for API errors

**Debug logging:**

Add this to your `configuration.yaml`:

```yaml
logger:
  logs:
    custom_components.ha_ubibot_ws1: debug
```

## Licence

Released under the [MIT Licence](LICENSE).
