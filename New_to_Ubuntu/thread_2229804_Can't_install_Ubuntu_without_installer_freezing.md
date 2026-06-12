---
title: "Can't install Ubuntu without installer freezing"
date: 2014-06-15
forum: New to Ubuntu
---

### Post by Christian_Ereira on 2014-06-15
I decided it was time to install Ubuntu on my old XP laptop. After many attempts I managed to get the laptop to boot from the 12.04 alternate installer on a CD (the only thing the laptop will boot from other than the hard drive). The installer was very nearly finished (around 80%) when the laptop decided to freeze. I left it for a while in case it managed to sort itself out, but it stayed frozen. I restarted the laptop and Ubuntu had erased everything. Every time I run the installer it freezes at random points. I can boot from the graphical installer, but I get an error message. How can I fix this?

---

### Post by yancek on 2014-06-15
>  I can boot from the graphical installer, but I get an error message. How can I fix this?         ]

You forgot to post the error message can't help much.
Did you compare the minimum hardware requirements for your computer with what you have on your machine?
A default install with Unity will probably need 1GB of RAM.  The minimum is 512MB. 
The installer will give you several options.  If another OS is detected, you will get an 'Install Alongside' option as well as the 'Erase and Use Entire Disk' and 'Something Else' options.  Something Else is the manual install which requires making some choices on the part of the user but also shows you what is happening each step of the way.  Which option did you choose?

---

### Post by sandyd on 2014-06-15
Moved to Absolute Beginners Section

---

### Post by Christian_Ereira on 2014-06-15
The graphical installer didn't get that far. After the initial loading screen it takes me to a BusyBox screen with an error. I cannot post the exact error as the installer takes hours to get to this point.

---

### Post by yancek on 2014-06-15
You didn't post the error message you mentioned in your first post.
Did you compare your hardware to the minimum requirements?  You didn't post that info here either.

---

### Post by buzzingrobot on 2014-06-15
The initial screen the installer displays offers a choice between "Try Ubuntu" or "Install Ubuntu".  If you choose to install, a new screen asks if you want to install updates during the installation and if you want to install some third-party software.  Then, you are shown a screen that asks you to choose how you want the disk(s) to be partitioned for use (this is disguised in "user friendly" language about replacing Windows or installing "alongside" Windows). 

The reason it seemed Ubuntu had "erased" everything when you rebooted is that the partitions are adjusted and formatted as soon as you move beyond that display. That's necessary to install Ubuntu, or any other new OS. E.g., partitioning and formatting is the first thing the Windows installer does.

The time it takes to install depends on the speed of the drives involved, but that time should be measured in minutes, not hours.

The exact wording of the error message(s) you are seeing is the only diagnostic tool available here.

---

### Post by squakie on 2014-06-15
It may just be that the hardware ("an old XP laptop") just won't support full-blown "normal" Ubuntu.  If the laptop is old enough, if memory is below 1gb, if the CPU is older, if the resulting graphics adapter is older (which they all would be), I would suggest you try either lubuntu or xubuntu instead of full-blown Ubuntu.  These 2 versions use different desktop managers so they aren't as graphics dependent as "normal" Ubuntu.  My understanding is that xubuntu is the lightest version and would probably run well on older hardware.

As already mentioned, we need the exact error message.  We also need the specs of your laptop - at a minimum the manufacturer and the model.

---

