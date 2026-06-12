---
title: "Blackscreen after bootup, keyboard not working in recovery, usb 2-2 cant set config"
date: 2013-08-17
forum: New to Ubuntu
---

### Post by armin-frljak on 2013-08-17
Hello.
Yesterday i  updated my new Ubuntu installation, downloaded realtek  drivers, downloaded nvidia drivers, downloaded java and adobe flash  player.
 
But before that all mouse and keyboard wasnt working so i unplugged them and plugged them in.
  
Than i wrote acpi=off but didnt update grub.
 
I updated realtek drivers. Reboot. Than i updated Ubuntu.
  Reboot. 

I think nvidia drivers came with update.
 
Than i downloaded java and flashplayer, installed them, typed sudo apt-get update.

 Than i just shuted down and went to sleep. Now i have a blackscreen  after startup, there always stands something like usb 2-2 cant set  config and usb device keyboard.
 
So i wanted to try something in the recovery =  keyboard not working there. 

I also tried to boot up with nomodeset but still same problem.

So can you help me?

---

### Post by carl4926 on 2013-08-17
updated? or clean install? explain....

acpi=off - why? How?

USB keyboard may need Legacy USB support enabled in BIOS

---

### Post by armin-frljak on 2013-08-18
Bios Settings were enabled because my mouse and keyboard not worked. I had ubuntu 5 days but after this it not works. My mouse and Keyboard was not working so i did acpi=off and then they worked again. In Grub Keyboard works. I have ubuntu installed from a live cd. My second system is Windows Xp.

---

