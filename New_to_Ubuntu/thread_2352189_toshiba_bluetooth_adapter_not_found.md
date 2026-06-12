---
title: "toshiba bluetooth adapter not found"
date: 2017-02-10
forum: New to Ubuntu
---

### Post by mm84 on 2017-02-10
Hi I am new to ubuntu and like it too much. But it is not detecting my bluetooth adapter. I have run two commands to see the availability of bluetooth hardware viz.

**$ lsmod | grep toshiba**
toshiba_acpi           36864  0
sparse_keymap          16384  1 toshiba_acpi
wmi                    20480  1 toshiba_acpi
toshiba_bluetooth      16384  0
video                  36864  2 i915,toshiba_acpi

**$ dmesg |grep -i Bluetooth**
[ 8833.369885] Bluetooth: Core ver 2.21
[ 8833.369918] Bluetooth: HCI device and connection manager initialized
[ 8833.369924] Bluetooth: HCI socket layer initialized
[ 8833.369928] Bluetooth: L2CAP socket layer initialized
[ 8833.369939] Bluetooth: SCO socket layer initialized

but Blues say no bluetooth adapter found.
Am using 16.04 LTS.

---

