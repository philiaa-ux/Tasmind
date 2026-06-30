# 1. Tasmota Device Initial Setup (TLS 8883 & MQTT Security)

This guide covers flashing Tasmota firmware and securely connecting your device to TasMind.

---

## 1.1 Firmware Flashing
1. Open [Tasmota Web Installer](https://web.tasmota.github.io/) in Chrome or Edge.
2. Connect your device via USB and click **"Install"**. (Takes 2-3 mins)

## 1.2 Wi-Fi Setup (AP Mode)
1. Connect to the `tasmota-xxxxxx-xxxx` Wi-Fi network.
2. Visit `http://192.168.4.1` and enter your home Wi-Fi SSID & password. Save.

## 1.3 Module Configuration (GPIO)
1. Go to **Configuration → Configure Module** via the device IP.
2. Assign GPIO pins:
   - Relays: `Relay 1`, `Relay 2`
   - Temp/Humidity: `AM2301`
   - Light/Gas: `ANALOG`
3. Save and reboot.

## 1.4 MQTT Security Settings (CRITICAL)

> ⚠️ **User and Topic MUST be identical!**

1. Go to **Configuration → Configure MQTT**.
2. Fill in:

| Field | Value | Note |
|-------|-------|------|
| **Host** | TasMind MQTT Broker IP | Provided by admin |
| **Port** | `8883` | **Must use 8883** (TLS) |
| **User** | `tasmota_ai2` (example) | Unique device ID |
| **Topic** | `tasmota_ai2` (example) | **Must match User!** |
| **Password** | Issued token | Device-specific |

- ✅ User = Topic → Connection success
- ❌ User ≠ Topic → Authentication failure

## 1.5 Friendly Name
1. Go to **Configuration → Configure Other**.
2. Set **Friendly Name 1~N** (e.g., `Living Room Heater`).
3. Ensure `MQTT Enable` is checked and save.

🎉 **Done!** Your device is now ready for TasMind.
