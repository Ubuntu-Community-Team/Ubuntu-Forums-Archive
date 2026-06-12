---
title: "Hey im a bit new to ubuntu and i have a problem when i boot."
date: 2013-10-27
forum: New to Ubuntu
---

### Post by dylangreytak on 2013-10-27
Hey I am new to ubuntu and i am trying it out. I just built a computer and i have ubuntu but for some reason when i try to boot it had a purple screen and it wont go away. Now i have looked at many other forums on how to fix it and nothing worked. Hopefully one of you guys can help me out. I am also wondering about if i were to install windows 7 would i have to partition the harddrive? or could i just pop the disc in and duel boot?

---

### Post by LuvLinuxOS on 2013-10-27
did you live boot or just go straight into the install?

[> ~LuvLinuxOS~]("http://luvlinuxos.blogspot.com")

---

### Post by dylangreytak on 2013-10-27
It is installed.

---

### Post by fantab on 2013-10-27
Give us more info about your computer's hardware, like RAM, Graphics, Processor. Does your computer boot in BIOS mode or UEFI?

To answer you second question about installing Win7, you will have to create a separate partition on Hard Disk and then install Win7.
If this is the first time you are using Linux, then I recommend that you dual-boot Ubuntu with Windows for some time. And If I were you, I would erase the HDD, install Windows first, then install Ubuntu as Dual-boot.

But first lets see that info. And also, boot with your Ubuntu DVD/USB, and "Try Ubuntu Without Installing" option to see how Ubuntu fares on your machine. If all seems good then open Terminal [Ctrl+Alt+T], run the following commands and post its output here:
```
sudo fdisk -l
sudo parted -l
```

---

### Post by LuvLinuxOS on 2013-10-27
> It is installed.

yes, but can you live boot? This is a better question!!!

---

### Post by dylangreytak on 2013-10-29
I can not live boot. When i try to run it from my usb again it just takes me to the grub menu just as it does when it is installed....

---

### Post by fantab on 2013-10-30
To live boot, you have to select the boot devices, USB in your case, from the BIOS Boot Menu.

---

