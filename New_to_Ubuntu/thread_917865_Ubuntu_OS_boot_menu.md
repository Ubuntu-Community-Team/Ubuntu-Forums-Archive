---
title: "Ubuntu OS boot menu?"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by dESAI on 2008-09-12
Greetings good peopl!

Just successfully completed a new install of 8.04. I'm very impressed and I'm very happy. All is working as it should, except for one little thing.

I installed Ubuntu on a new HD (2nd HD). I removed my primary (win) HD while I did the installation. After the install I reconnected the Win HD.

As it is now, I have to select the boot drive via bios, to switch between OS's.

I remember that on my previous installation, I had a boot menu that allowed me to select the OS I wanted to use (and I remember I could configure it somewhere too. 

I think it is not active now because the Win HD was not connected during the U' install. But I can't find the place where I can activate and configure the boot menu. 

Thanks in advance to all you good people who take the time to help me. You're all beautiful xD

Have a groovy weekend!

---

### Post by dhtseany on 2008-09-12
When you first turn on your computer does the GRUB boot loader open? If not:

[http://ubuntuforums.org/showthread.php?t=169234](http://ubuntuforums.org/showthread.php?t=169234)

Peace
Sean

---

### Post by dESAI on 2008-09-12
> **dhtseany said:**
> When you first turn on your computer does the GRUB boot loader open? If not:

[http://ubuntuforums.org/showthread.php?t=169234](http://ubuntuforums.org/showthread.php?t=169234)

Peace
Sean


It goes straight to the desktop. No questions, delays, or errors.
Cheers!

---

### Post by dhtseany on 2008-09-12
Ok then you need to use that link I gave and follow that guide. 

Basically you'll need to add another line to the GRUB config file. 

Remember to make a copy of the contents of that file just be safe!

If you need help just ask :)

Peace
Sean

(Hint: The new hard drive will probably be hda1 instead of hda0 ;))

---

### Post by caljohnsmith on 2008-09-12
Since you had your primary drive disconnected when you installed Ubuntu to your 2nd HDD, Ubuntu installed it's Grub to the master boot record (MBR) of that HDD. That's why whenever you want to boot Ubuntu, you have to use your BIOS to boot your Ubuntu HDD, and not your Windows HDD. I think the easiest solution for you would be to leave your BIOS set to boot the Ubuntu HDD, and then just add an entry for Windows in your /boot/grub/menu.lst so you can boot your Windows drive. If you want to do that, here is how:

When you are in Ubuntu, open a terminal, and do:
```
gksudo gedit /boot/grub/menu.lst
```
At the bottom of the menu.lst file, add the following:
```
title  Windows
root   (hd1,0)
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
I think that is all it will take to boot Windows, assuming Windows is on the first partition of its HDD. If that doesn't work, then let me know what errors it gives and also post the output of:
```
sudo fdisk -lu
```
Let me know how it goes. :)

---

### Post by dESAI on 2008-09-12
> **caljohnsmith said:**
> Since you had your primary drive disconnected when you installed Ubuntu to your 2nd HDD, Ubuntu installed it's Grub to the master boot record (MBR) of that HDD. That's why whenever you want to boot Ubuntu, you have to use your BIOS to boot your Ubuntu HDD, and not your Windows HDD. I think the easiest solution for you would be to leave your BIOS set to boot the Ubuntu HDD, and then just add an entry for Windows in your /boot/grub/menu.lst so you can boot your Windows drive. If you want to do that, here is how:

When you are in Ubuntu, open a terminal, and do:
```
gksudo gedit /boot/grub/menu.lst
```
At the bottom of the menu.lst file, add the following:
```
title  Windows
root   (hd1,0)
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
I think that is all it will take to boot Windows, assuming Windows is on the first partition of its HDD. If that doesn't work, then let me know what errors it gives and also post the output of:
```
sudo fdisk -lu
```
Let me know how it goes. :)

Thanks chief! I'll try it in an hour or so.
So there is no application (with a GUI) where I can activate and configure this?

I was sure I saw one... I remember it even allowed me say how many seconds it should wait for someone to select the OS before proceeding.


Peace!
Stay cool!

---

### Post by dESAI on 2008-09-12
> **dhtseany said:**
> Ok then you need to use that link I gave and follow that guide. 

Basically you'll need to add another line to the GRUB config file. 

Remember to make a copy of the contents of that file just be safe!

If you need help just ask :)

Peace
Sean

(Hint: The new hard drive will probably be hda1 instead of hda0 ;))


I give it a try and see how it goes :)

1,000 thanks!

---

### Post by rbc on 2008-09-12
I think the GUI app you are talking about is startup-manager. It is in the repos. But i do not think you can make additions to the menu.lst using startup-manager

---

### Post by dESAI on 2008-09-13
> **caljohnsmith said:**
> Since you had your primary drive disconnected when you installed Ubuntu to your 2nd HDD, Ubuntu installed it's Grub to the master boot record (MBR) of that HDD. That's why whenever you want to boot Ubuntu, you have to use your BIOS to boot your Ubuntu HDD, and not your Windows HDD. I think the easiest solution for you would be to leave your BIOS set to boot the Ubuntu HDD, and then just add an entry for Windows in your /boot/grub/menu.lst so you can boot your Windows drive. If you want to do that, here is how:

When you are in Ubuntu, open a terminal, and do:
```
gksudo gedit /boot/grub/menu.lst
```
At the bottom of the menu.lst file, add the following:
```
title  Windows
root   (hd1,0)
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
I think that is all it will take to boot Windows, assuming Windows is on the first partition of its HDD. If that doesn't work, then let me know what errors it gives and also post the output of:
```
sudo fdisk -lu
```
Let me know how it goes. :)

That worked PERFECTLY!

1,000,000 thanks!

Now if I can just get Photoshop, Dreamweaver and some online poker software software working.

---

### Post by caljohnsmith on 2008-09-13
> **dESAI said:**
> That worked PERFECTLY!

1,000,000 thanks!

Now if I can just get Photoshop, Dreamweaver and some online poker software software working.
Glad it's worked for you! :) 

Have you installed Wine yet to try and run your Windows apps? I know that photoshop can definitely be run in Wine, but I'm not sure about Dreamweaver or your poker software. If you go to appdb.winehq.org, you can search for your Windows apps and see how much success others have had when running them in Wine. Good luck, and if you have any more specific questions related to running your Windows programs in Wine, it would be good to start a new thread instead of posting here. :)

---

