# EdgeCrash-AI: TinyML Collision and CNG Leak Detection for Vehicles

An ESP32-based automotive safety system that fuses accelerometer and gas-sensor data to detect **vehicle collisions** and **CNG gas leaks in the cabin**, running a quantized TinyML model on the edge.

**Status:** Hardware prototyping stage (schematic and PCB layout complete in KiCad)
**Context:** Built as the hardware design for a Tamil Nadu hackathon team. My role: Hardware Specialist (hardware design and PCB development).

---

## Problem

CNG-powered vehicles can develop cabin leaks, and serious collisions need an immediate response. Cloud-dependent systems add latency and fail without connectivity. EdgeCrash-AI runs detection **on the device**, so it can respond in real time.

## How it works

1. **Sense:** an accelerometer captures motion and impact data; a gas sensor monitors cabin air for CNG.
2. **Fuse and classify:** sensor readings are windowed and fed to a quantized TinyML model trained in Edge Impulse.
3. **Decide:** the model classifies each window as `[normal / collision / gas leak, update to match your classes]`.
4. **Act:** on detection, the system `[describe: buzzer, alert, message, relay, etc.]`.

```
[Accelerometer] ─┐
                 ├─► [ESP32 + TinyML model] ─► [Alert / Output]
[Gas sensor]  ───┘
```

## Hardware

| Part | Details |
|------|---------|
| Microcontroller | ESP32 (dual-ESP32 design) |
| Motion sensing | `[accelerometer model, e.g. MPU6050]` |
| Gas sensing | `[gas sensor model, e.g. MQ-series]` |
| Power | `[supply and regulation details]` |
| PCB | 2-layer, designed in KiCad (schematic, placement, signal and power routing) |

### Schematic

![Schematic](Dual%20ESP%2032-Schematic.jpg)

### PCB layout

![PCB layout](Dual%20ESP%2032-PCB.jpg)

KiCad source: [`dual ESP 32.kicad_sch`](dual%20ESP%2032.kicad_sch)

## TinyML model

- **Platform:** Edge Impulse
- **Model:** quantized for on-device inference on ESP32
- **Classes:** `[list classes]`
- **Training data:** `[how collected: real recordings, simulated impacts, gas exposure method]`
- **Results:** `[accuracy, confusion matrix summary]`
- **Model size / RAM / latency:** `[fill in from Edge Impulse deployment tab]`

## Repository contents

| File | Description |
|------|-------------|
| `dual ESP 32.kicad_sch` | KiCad schematic |
| `Dual ESP 32-Schematic.jpg` | Schematic image |
| `Dual ESP 32-PCB.jpg` | PCB layout image |
| `TinyML-Powered ... Detection (02).docx` | Project write-up |
| `firmware/` | `[ESP32 firmware, to be added]` |

## Current status and roadmap

- [x] Schematic capture
- [x] Component placement and routing in KiCad
- [x] TinyML model trained in Edge Impulse
- [ ] PCB fabrication
- [ ] Assembly and bring-up testing
- [ ] Field testing of collision and gas detection
- [ ] Validate detection accuracy on real hardware

## Tools

KiCad · ESP32 · C++ (Arduino-style firmware) · Edge Impulse · I2C/UART

## Author

**Dharineesh T A**, Embedded Hardware & IoT Engineer (fresher)
[LinkedIn](https://linkedin.com/in/dharineesh-thangavel) · [GitHub](https://github.com/techforge78-eng)
