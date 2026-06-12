---
title: "Trying to install Linux on a hp ProBook x360 11"
date: 2024-08-30
forum: New to Ubuntu
---

### Post by seannmc on 2024-08-30
I bought an old hp ProBook x360 11 which ran well under Win11, but I was looking to learn Linux.
I've tried installing Ubuntu Cinnamon, Mint and Studio.  Deservedly, the hp ProBook x360 11 has a reputation of being a hard install.

I created a boot flash drive using BelenaEtcher, changed the boot order to boot first off of USB, and booted. The computer runs well off of the flash drive.  However when I click on "Install" the install crashes around the Curtain - Curtain hook step.  Booting the computer off of the incomplete install, the Login screen displays, but apparently my login account wasn't created, and I can't get in.

I rebooted off the flash drive and the install re-initiates. Opening the terminal, i waited until the install crashes again, close the installer and try running bootfix. Bootfix doesn't work saying that I have to close the installer (already done- I can't find the process to close a TSR installer).

I either have to find a way to close a hidden process for the installer, or boot off the HD incomplete install and find a way to create a user account so I can run bootfix without an install in the backgrounds.

Suggestions?

---

### Post by Perfect Storm on 2024-08-30
Hello,

Did you ran checksum on the .iso file?
Is fast boot and secure boot disabled?
Do you dual boot?

---

### Post by seannmc on 2024-08-31
> **Perfect Storm said:**
> Hello,

Did you ran checksum on the .iso file?
Is fast boot and secure boot disabled?
Do you dual boot?

Thanks for responding. 
Checksum: yes,
I’ll have to check for fastboot. Secure boot is off.
This was just a Linux boot (Linux only). I overwrote Windows.

---

### Post by tea for one on 2024-08-31
Your HP Probook 11 - Is it the model with 4GB RAM and Celeron processor?
If so, try a lighter flavour e.g. Xubuntu or Lubuntu.

Secondly, if the installer then fails/stops/crashes, create the USB with one of the following:-
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://www.ventoy.net/en/doc_start.html](https://www.ventoy.net/en/doc_start.html)
Startup Disk Creator (included in Ubuntu iso)

---

### Post by QIII on 2024-08-31
Support request, not chat.

Moved to **New to Ubuntu**

---

### Post by seannmc on 2024-09-02
> **tea for one said:**
> Your HP Probook 11 - Is it the model with 4GB RAM and Celeron processor?
If so, try a lighter flavour e.g. Xubuntu or Lubuntu.

Secondly, if the installer then fails/stops/crashes, create the USB with one of the following:-
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://www.ventoy.net/en/doc_start.html](https://www.ventoy.net/en/doc_start.html)
Startup Disk Creator (included in Ubuntu iso)

Thanks for your response.
The BIOS / (whatever the Linux equivalent is called) says it is an Intel Pentium CPU N4200 @ 1.10.GHz with 4 GB of memory.

Looking at the HP Tech Manual, the computer will not support more than 4 GB. (Was hoping I could upgrade it.)

---

### Post by yancek on 2024-09-02
If you managed to get Ubuntu installed on that computer it would not run well so take the suggestion above and install a lighter version if you can:  Xubuntu, Lubuntu, Bodhi and others.

>   but apparently my login account wasn't created, and I can't get in.


When you did the install, did you create a user with a password which is required to complete an install?

---

### Post by seannmc on 2024-09-03
> **yancek said:**
> If you managed to get Ubuntu installed on that computer it would not run well so take the suggestion above and install a lighter version if you can:  Xubuntu, Lubuntu, Bodhi and others.



When you did the install, did you create a user with a password which is required to complete an install?

Thanks for replying. It asked for a real name, an email address, a user name and a password. I supplied all the requested, and have tried installing both with requiring password and without. In both cases, booting off the HD brings e to a login. I came across a post about editing grub to change a password, and I received the error that the account wasn't found.

---

### Post by seannmc on 2024-09-03
> **Perfect Storm said:**
> Hello,

?
Is fast boot and secure boot disabled?


Thanks. I can't find a reference to fast boot in the bios, but had disabled secure boot.

---

### Post by Perfect Storm on 2024-09-03
No problem, it means that your computer is older. In case of newer computer it's advise to disable it.

---

### Post by tea for one on 2024-09-03
> **seannmc said:**
> Thanks for replying. It asked for a real name, [COLOR="#FF0000"]an email address[/COLOR], a user name and a password. I supplied all the requested, and have tried installing both with requiring password and without. In both cases, booting off the HD brings e to a login. I came across a post about editing grub to change a password, and I received the error that the account wasn't found.
The installer for Xubuntu or Lubuntu does not request an email address.
Some misunderstanding in play here?

---

