---
title: "Installed Ubuntu with Universal Usb Installer but Blackscreen?"
date: 2013-10-14
forum: New to Ubuntu
---

### Post by Mk7dKs6 on 2013-10-14
Windows 7 failed to boot on my laptop so I've been trying to boot it with Ubuntu to recover my hard disk files and work. I installed Ubuntu on a flash drive using Universal USB Installer.  

I tried it with the following isos
ubuntu-12.04.3-desktop-amd64
ubuntu-12.04.3-desktop-i386
ubuntu-13.04-desktop-i386

I can see the startup screen asking me whether I want to boot from USB and I can edit the settings if I press tab. However, none of them the above installations seem to work with my laptop's screen.  I get a black blank screen.  In some of the isos I installed, when I press arrow keys, I can hear sound from what I can presume is a selection menu but nothing on the screen.  I think my solution is to change some of the commands "boot from USB" settings? I am not sure what to change?

I think my windows issue is separate from ubuntu issue because windows can load the windows 7 background and an oversized mouse pointer on the screen for 'startup repair' but ubuntu can't load anything on my laptop screen.

Edit: Windows 7 can now boot normally now liek before I had the problem.

---

### Post by mastablasta on 2013-10-14
try nomodeset in boot options: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

what is the graphics chip?

---

### Post by TheFu on 2013-10-14
[https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen)

---

### Post by Keith_Valin on 2013-10-15
Look at your computer's BIOS (Start-up menu, usually says press a key to enter), you're probably using UFEI Boot, use CSM Boot instead.  If you can't find these boot options disable secure boot.

---

