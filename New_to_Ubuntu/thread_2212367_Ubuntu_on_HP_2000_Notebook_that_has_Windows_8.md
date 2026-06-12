---
title: "Ubuntu on HP 2000 Notebook that has Windows 8"
date: 2014-03-20
forum: New to Ubuntu
---

### Post by michael-piziak on 2014-03-20
Need help with Ubuntu 12.04 LTS (32 bit) install disk on HP 2000 Notebook that has Windows 8

Let me just start by saying I have installed Ubuntu on many desktops and laptops, but this one is giving me fits and I think it's because it has Windows 8 on it & Windows 8 is trying to control everything.

How can I force the computer to boot from the Ubuntu disk?  Upon start up there is no indication I can hit an F key to take me to a screen to select to boot from the cd/dvd drive.

---

### Post by Korkel on 2014-03-21
Can you enter the BIOS/Boot menu?

If you put the CD/DVD in the system (or an USB) in the system and you enter the BIOS or Boot menu you can choose from what you want to start first?
Turn the system on and keep pressing ESC. Tell me if you can boot from the CD/DVD.

---

### Post by edeneen on 2014-03-21
I had a Win8 laptop with the same problem.  Go into BIOS, change boot from EUFI to legacy, then you will be able to change the boot order (boot from CD rom, flash drive or HD), set to boot from CD before HD, load the disc, rebooot and it should boot from the CD and offer up the install options.  Hope this helps.

---

