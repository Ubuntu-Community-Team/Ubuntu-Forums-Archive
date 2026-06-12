---
title: "Help dual boot ubuntu &amp; windows 10 UEFI"
date: 2015-08-03
forum: New to Ubuntu
---

### Post by joerack on 2015-08-03
Hello all, I tried to install ubuntu along with windows, I had to create the partitions manually, and create a uefi new voice to force linux booting, but everytime I select shimx64.efi I get a non gui interface saying 
Minimal bash-like line editing is supported.

Please help

---

### Post by oldfred on 2015-08-03
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

What brand/model system? What video card/chip?
Does live installer boot in live mode ok.
Is Windows in UEFI or BIOS boot mode. Above report will confirm, but you want to always boot (including live installer) in same mode as Windows is installed either UEFI or BIOS.

---

