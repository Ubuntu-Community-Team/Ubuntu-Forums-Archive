---
title: "HP Probook 5310m and Ubuntu, not booting"
date: 2022-12-09
forum: New to Ubuntu
---

### Post by frank-layden69 on 2022-12-09
Hi all, I'm new to Ubuntu. Have an old HP Probook 5310m and USB stick with latest Ubuntu version. Installed it on Lenovo laptop, no problem and Ubuntu starts from hard drive now.

On the other hand HP Probook 5310m same thing, installation no problem, ejecting USB stick as instructed, and booting the computer. And it does not start, tried everything in BIOS

Rsult:
Pre-boot eXecution Environment (PXE) v2.1
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting PXE ROM

Non System disk or dis error
replace and strike any key when ready.
--
In BIOS boot order:
Notebook hard Drive
USB Floppy
USB CD-Rom
USB Hard Drive
Notebook Ethernet
SD Card

Is there boot loader or grub missing? How do I get this set-up to work?

Thanks for help

---

### Post by tea for one on 2022-12-09
Specification of the HP Probook 5310m may yield a clue?
Does it meet the minimum requirements for Ubuntu?

---

### Post by frank-layden69 on 2022-12-09
Yes it should. It runs Ubuntu just find in Test-mode, but does not load from hard-disk.

---

### Post by maglin2 on 2022-12-09
An internet search for* PXE-E61: Media test failure, check cable* yields a lot of results. Most suggest bios boot order or hdd connection fault, or failing hdd.
Has any OS recently booted from this hdd?

---

### Post by didiaargh on 2022-12-19
This night, I seem to have stumbled upon the solution, I had the same problem with a Probook 6570b. But I cannot remember how, I was just very happy to see purple when I opened it &#128156;

---

### Post by jackram on 2022-12-24
I had the same issue with my HP ProBook 6570b, I was able to test Ubuntu using a USB, but after installing Ubuntu onto the hard disk, I was met with a "OS not detected" error (not exactly the same error you encountered). 

I realized that in BIOS, I had legacy BIOS boot enabled when testing Ubuntu and switching that to UEFI boot solved that issue. I found the solution after going through the steps in [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair), where the output of **[B]Create a Boot-Info Summary**[/B] showed me what the issue was.

Maybe generating a boot-info report will find a more specific issue.

---

