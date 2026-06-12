---
title: "Trying to install xubuntu on 64-bit Toshiba Satellite laptop but it won't boot"
date: 2013-05-22
forum: New to Ubuntu
---

### Post by u5688304 on 2013-05-22
I tried to install xubuntu-13.04-desktop-amd64 on my laptop using a USB memory stick and the universal USB installer from pendrivelinux.com (Universal-USB-Installer-1.9.3.4.exe). After the installation completed and I switched the laptop back on, all I got was a "grub>" command line. I restarted it with the USB memory stick in, chose to try xubuntu without installing, and ran boot-repair. After following the steps, the link I got was [paste.ubuntu.com/5688304]("http://paste.ubuntu.com/5688304") . When I restarted, I got a SecureBoot error message saying that a digital signature was missing. I then attempted to install Precise Puppy Linux using the memory stick, but I got the same error as if the memory stick wasn't there. However, when I again tried xubuntu, I was still able to boot into the trial, and ran boot-repair again. This time I got the link [paste.ubuntu.com/5690783]("http://paste.ubuntu.com/5690783"). Please advise.

EDIT: Managed to fix it. I had to disable SecureBoot in the BIOS. I had previously attempted to access BIOS by pressing ESC during bootup, which one website said was the correct key to access BIOS. However, later research uncovered a source which claimed the correct key was in fact F2. Using F2, I was able to access BIOS and disable SecureBoot.

---

### Post by ohnonot on 2013-05-23
please mark this as solved.

---

