---
title: "Laptop won't boot from USB, Disc or Wubi"
date: 2012-07-31
forum: New to Ubuntu
---

### Post by lunarescence on 2012-07-31
I'm running a Sony Vaio S Series, latest model with Insydeh20 bios.

I've tried to install Ubuntu via USB and CD however it will never boot from an external device! I have changed the boot order, first I enabled to boot from an external device, then I changed the boot order so that the external device would boot first. It didn't recognise it. I burnt it to CD and set the Bios to boot from internal optical drive. It didn't work either. I've installed it via Wubi. It won't give me an option to boot with Ubuntu. I have tried all of these methods on an older laptop and it all works fine, however the only difference I can note is the BIOS is different and the boot options are slightly different.

I've also tried pressing 'esc' to when the laptop is booting and for all methods all I get is windows 7.

I'm out of ideas, please help :S

---

### Post by 3177 on 2012-07-31
are you saying you successfully installed ubuntu using wubi, and now cant boot into said installation?
If so you need to change your boot order back to normal.

---

### Post by clappboard on 2012-07-31
First of all, I would HIGHLY recommend installing Ubuntu using a CD or USB drive.  Your experience will be more stable.  But if you really do want to use Wubi, check _[here]("http://askubuntu.com/questions/131827/no-boot-option-after-ubuntu-install")_ and see if any of the suggestions work for you.

---

### Post by 3177 on 2012-07-31
I believe the OP has windows installed.

---

### Post by lunarescence on 2012-07-31
USB and CD booting didn't work for me, that is why I resorted to Wubi. I'd prefer NOT to use it, but I can't figure out why my laptop won't boot from any external devices even though I changed the boot order. And I know that I've burned them correctly because I tested it on an older computer.

I have Windows 7 Home Premium. 

> **3177 said:**
> are you saying you successfully installed ubuntu using wubi, and now cant boot into said installation?
If so you need to change your boot order back to normal.

I got the screen to choose an OS when I restarted, however it came up with an error when I tried to boot in Ubuntu. I can try it again and reset to the default boot order? Will that make a difference?

---

### Post by 3177 on 2012-08-01
> **lunarescence said:**
> 
I got the screen to choose an OS when I restarted, however it came up with an error when I tried to boot in Ubuntu. I can try it again and reset to the default boot order? Will that make a difference?

it sounded to me that you still have multiple devices(possibly hard drives) connected to your computer at startup. Ive had issues with externals connected to my laptop, and upon booting, the computer hangs before GRUB. Changing my boot order fixed the problem for me, and yours seems similar.

---

### Post by techvish81 on 2012-08-01
> **lunarescence said:**
> USB and CD booting didn't work for me, that is why I resorted to Wubi. I'd prefer NOT to use it, but I can't figure out why my laptop won't boot from any external devices even though I changed the boot order. And I know that I've burned them correctly because I tested it on an older computer.

I have Windows 7 Home Premium. 



I got the screen to choose an OS when I restarted, however it came up with an error when I tried to boot in Ubuntu. I can try it again and reset to the default boot order? Will that make a difference?

i think you should try to recover/update bios.

i found this link, could be helpful to you, so edited the post.

[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi]("http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi")

---

### Post by 3177 on 2012-08-02
i totally forgot about this (remembered as i was looking at the previous post's link). You should probably use easyBCD.(free program for windows)
download and install easyBCD on windows, open it, then switch to the other OS tab. there will be a drop down menu, click it and add GRUB/Ubuntu. Upon re-booting, you will be greeted with the Winblows bootloader. the second option (under windows) will be Ubuntu. Press enter on ubuntu and it will bring you to GRUB2. press enter on your preferred kernel, and your there.

---

### Post by coldraven on 2012-08-02
I usually boot from a SD card in my internal card reader but if I have my external USB drive plugged in it will not work. So check that you have removed all other USB devices that might confuse the BIOS.

---

### Post by Horbo on 2012-12-25
If your BIOS won't cooperate, install Plop boot manager.
It has drivers for USB and CD, and will let you boot the machine from any device you like.

[http://www.plop.at/en/bootmanager/intro.html](http://www.plop.at/en/bootmanager/intro.html)

---

