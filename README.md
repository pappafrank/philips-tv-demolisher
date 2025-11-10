# philips-tv-demolisher

A Python script to control Philips TVs on your LAN using the Philips TV HTTP API (v6). Just a simple automation.

---

## Features

* Auto-discovery: scans your LAN for TVs on port 1925
* Send remote keys (VolumeUp, Mute, ChannelUp, Standby, etc.)
* Get/set volume
* Toggle Ambilight and set colors
* Interactive terminal menu

## Requirements

* Python 3.8+
* `requests` library (`pip install requests`)

## Usage

```bash
sudo chmod +x philips-demolisher; ./philips-demolisher
```

Steps:

1. Script scans your subnet (default `192.168.1.0/24`).
2. Finds a Philips TV via `/6/system`.
3. Shows a menu with control options.

Examples:

* Set volume → option 11, enter number 0–60
* Set Ambilight color → option 14, enter `R,G,B`

## Endpoints Used

* `GET /6/system` — detect TV
* `POST /6/input/key` — send keys
* `GET/POST /6/audio/volume` — get/set volume
* `POST /6/ambilight/power` — on/off
* `PUT /6/ambilight/processed` — set color

## Notes

* Works only on TVs with open API (port 1925)
* Use only on your own network/devices
* Some models may require pairing/authentication (Which can be seen at the end of the json available in http://{DEVICE-IP}:1925/1/system as "pairing_type" which is none by default.)
<img width="505" height="223" alt="image" src="https://github.com/user-attachments/assets/7cd0ea18-d79c-48a2-b2ff-bc6168baf375" />
