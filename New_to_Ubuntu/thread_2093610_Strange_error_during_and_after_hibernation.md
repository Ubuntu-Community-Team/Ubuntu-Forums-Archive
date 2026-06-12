---
title: "Strange error during and after hibernation"
date: 2012-12-11
forum: New to Ubuntu
---

### Post by GiacoSore on 2012-12-11
Good morning,
I'm a beginner with ubuntu and I have a problem,
when switching off my pc I choose to hibernate, and also turning it on after hibernation, appear messages of which I can't understand the meaning.

These errors that appear while I'm switching off:
[numbers] PM: Device PNP0C0D:00 failed to restore: error -19
[numbers] legacy_resume(): acpi_device_resume+0x0/0x27 returns -19
[numbers] PM: Device PNP0C0D:00 failed to thaw: error -19


and these when I turn it on after hibernation
[numbers] PM: Device PNP0C0D:00 failed to restore: error -19
[numbers] legacy_resume(): acpi_device_resume+0x0/0x27 returns -19
[numbers] PM: Device PNP0C0D:00 failed to restore: error -19

Is there someone that can help me to understand what it means?

---

### Post by Wim Sturkenboom on 2012-12-11
I could find a bug report for it for 11.04 : [https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/810191](https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/810191)

---

