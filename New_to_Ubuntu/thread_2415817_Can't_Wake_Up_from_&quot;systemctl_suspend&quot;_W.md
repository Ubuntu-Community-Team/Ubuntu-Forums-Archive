---
title: "Can't Wake Up from &quot;systemctl suspend&quot; While Laptop Lid Is Closed"
date: 2019-04-01
forum: New to Ubuntu
---

### Post by tomcloud on 2019-04-01
Hi everyone,
    I can't seem to **wake up my laptop using Logitech keyboard which connected to the external monitor while laptop lid is closed**.
I'm sure the wake up function is working fine since the system wakes up when the lid is opened. And when I use Windows 10
I can achieve my goal that is to wake up from sleep mode using the same devices with closed lid.
What can I do to make this right? I been working this problem for some days now... pls help me...

Here are some infos listed. 

```
 lsusb
[COLOR=#0000ff]Bus 002 Device 002: ID 8087:8000 Intel Corp. [/COLOR][COLOR=#0000ff]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR]
[COLOR=#0000ff]Bus 001 Device 002: ID 8087:8008 Intel Corp. [/COLOR]
[COLOR=#0000ff]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR]
[COLOR=#0000ff]Bus 004 Device 002: ID 0451:8340 Texas Instruments, Inc. [/COLOR]
[COLOR=#0000ff]Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub[/COLOR]
[COLOR=#0000ff]Bus 003 Device 003: ID 8087:07dc Intel Corp. [/COLOR]
[COLOR=#0000ff]Bus 003 Device 006: ID 0451:82ff Texas Instruments, Inc. [/COLOR]
[COLOR=#0000ff]Bus 003 Device 005: ID 1038:1369 SteelSeries ApS [/COLOR]
[COLOR=#0000ff]Bus 003 Device 004: ID 046d:c338 Logitech, Inc. [/COLOR]
[COLOR=#0000ff]Bus 003 Device 002: ID 0451:8342 Texas Instruments, Inc. [/COLOR]
[COLOR=#0000ff]Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[/COLOR] 
```[COLOR=#0000ff]

[/COLOR]```
grep . /sys/bus/usb/devices/*/power/wakeup[COLOR=#000000]
[/COLOR][COLOR=#0000ff]/sys/bus/usb/devices/1-1/power/wakeup:disabled[/COLOR]
[COLOR=#0000ff]/sys/bus/usb/devices/2-1/power/wakeup:disabled[/COLOR]
[COLOR=#0000ff]/sys/bus/usb/devices/3-1.1/power/wakeup:enabled[/COLOR]
[COLOR=#0000ff]/sys/bus/usb/devices/3-1.2/power/wakeup:enabled[/COLOR]
[COLOR=#0000ff]/sys/bus/usb/devices/3-1/power/wakeup:enabled[/COLOR]
[COLOR=#0000ff]/sys/bus/usb/devices/3-6/power/wakeup:enabled[/COLOR]
[COLOR=#0000ff]/sys/bus/usb/devices/4-1/power/wakeup:disabled[/COLOR]
[COLOR=#0000ff]/sys/bus/usb/devices/usb1/power/wakeup:disabled[/COLOR]
[COLOR=#0000ff]/sys/bus/usb/devices/usb2/power/wakeup:disabled[/COLOR]
[COLOR=#0000ff]/sys/bus/usb/devices/usb3/power/wakeup:disabled[/COLOR]
[COLOR=#0000ff]/sys/bus/usb/devices/usb4/power/wakeup:disabled
[/COLOR] 
```[COLOR=#0000ff]


[/COLOR]
[If I enable usb3 then my system just wakes up seconds after suspend, so I can only disabled it.]



It's my first question posted online in English, so ... thank u for bearing and reading it through!

---

