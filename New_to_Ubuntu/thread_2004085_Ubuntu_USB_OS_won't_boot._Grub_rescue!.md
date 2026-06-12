---
title: "Ubuntu USB OS won't boot. Grub rescue!"
date: 2012-06-15
forum: New to Ubuntu
---

### Post by cpm1980 on 2012-06-15
Hello all, so I'm a bit stuck with my computer. I have a Acer netbook and I just want to start fresh. I kinda stuffed my first atempt up and now it's sad face! So heres what happened, I ran Ubuntu 12.4 of a USB and then installed, all was working fine until I was prompted to select the drives or partitions for the grub directory. I made the wrong selection. Because of my lack of knowledge I couldn't fix it and just wanted to start again. I used a USB GParted and tried to format the hard drive thinking if nothing was on I could just start again. This didn't work! Now when I try and boot from the USB Ubuntu I get the error: no such device: 8be2feaa-6689(goes on) grub rescue>
Now I'm stuck, please help me, I just want to start fresh.

---

### Post by mapes12 on 2012-06-15
Are you saying that the Netbook will not boot from the USB stick?

---

### Post by ixtok on 2012-06-15
I would use another computer to create a new live usb then re-install.

---

### Post by cpm1980 on 2012-06-15
The netbook will not boot from the USB with Ubuntu on it. I used a second computer to create a new live USB and the netbook still won't boot. 
It will only boot if I have a USB runing GParted live on it.

---

### Post by mapes12 on 2012-06-15
Hmmm, If it were my machine then I would take the HDD back to its factory gate condition by running Killdisk across it then starting again:-

[http://how-to-erase-hard-drive.com/eraser.htm](http://how-to-erase-hard-drive.com/eraser.htm)

Killdisk is a DOS application so there is every chance that the USB startup will work.

If you get to the point where the Netbook will boot from the Ubu USB stick then run the install with all the default options i.e. don't bother setting up partitions for Grub and what not. You can experiment with that once you have a working system. When you have a working system then make a backup of it using the backup function in Remastersy. Then if it all falls over again it's very easy to reinstall the Remastersys backup and away you go again.

---

### Post by wilee-nilee on 2012-06-15
My acer provides a boot from menu outside the bios with a f12 prompt at powering on, like as if you were using the f2 to get to the bios, use the f12 function.

I believe you have to unlock this f12 function in the bios as well.

---

### Post by cpm1980 on 2012-06-15
Okay, so i tried to set up kill disk on a usb but i failed. The second computer I'm using is my girlfriends Macbook. I can use a program called crossover to run .exe programs but not all the fanctionality is there. (it wouldnt let me select the usb)
How ever i did get the F12 boot menu to work but after selecting to boot of the USB the same error message returned. Sad Face.

---

### Post by wilee-nilee on 2012-06-15
> **cpm1980 said:**
> Okay, so i tried to set up kill disk on a usb but i failed. The second computer I'm using is my girlfriends Macbook. I can use a program called crossover to run .exe programs but not all the fanctionality is there. (it wouldnt let me select the usb)
How ever i did get the F12 boot menu to work but after selecting to boot of the USB the same error message returned. Sad Face.

Use unetbootin to load the ubuntu to the usb.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Hopefully beyond this your only problem may be a graphic driver problem getting to a live desktop.

And if you get it installed update it and clone it before you tweak it till its broken again.

---

### Post by cpm1980 on 2012-06-15
> **wilee-nilee said:**
> Use unetbootin to load the ubuntu to the usb.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Hopefully beyond this your only problem may be a graphic driver problem getting to a live desktop.

And if you get it installed update it and clone it before you tweak it till its broken again.

Its alive, its alive. Thank you everybody for your help. In the end unetbootin saved the day. Very easy to use and i would recommend it to anybody who finds themselves in the same place as i did. 
Cheers Wilee-Nilee:popcorn:

---

