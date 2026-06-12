---
title: "can't boot after fresh install"
date: 2011-08-19
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by lime4x4 on 2011-08-19
I installed the aug 17th build for 64 bit. Now the computer won't boot it hangs after checking battery. Below is a copy of the boot log. This is also a desktop computer so i don't know why it's checking the battery state.

fsck from util-linux 2.19.1

fsck from util-linux 2.19.1

/dev/sdb1: clean, 137676/4276224 files, 1075205/17089843 blocks

/dev/sdc1: clean, 40950/61054976 files, 130070218/244190208 blocks

Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox

 * Starting AppArmor profiles       [80G 
[74G[ OK ]

 * Starting Kernel Oops catching service kerneloops       [80G 
[74G[ OK ]

speech-dispatcher disabled; edit /etc/default/speech-dispatcher

Checking for running unattended-upgrades: 

 * Starting bluetooth       [80G 
[74G[ OK ]

 [33m*[39;49m PulseAudio configured for per-user sessions

saned disabled; edit /etc/default/saned

 * Checking battery state...       [80G 
[74G[ OK ]

---

### Post by rtalcott on 2011-08-19
I also have this issue on a machine...have not had time to deal with it though...
rt

---

### Post by Toz on 2011-08-19
Can we get some info about the specifics of your system? Most importantly, I think, the video card that you have. If you have access to a terminal (Ctrl+Alt+F1), then typing in:
```
lspci | grep VGA
``` would be helpful.

Perhaps all you need is to specify the nomodset and/or xforcevesa kernel parameters to get access to the gui so that you can install the correct video drivers.

Also have a look at: [http://ubuntuforums.org/showthread.php?t=1743535]("http://ubuntuforums.org/showthread.php?t=1743535")

---

### Post by sgage on 2011-08-19
> **lime4x4 said:**
> I installed the aug 17th build for 64 bit. Now the computer won't boot it hangs after checking battery. Below is a copy of the boot log. This is also a desktop computer so i don't know why it's checking the battery state.

fsck from util-linux 2.19.1

fsck from util-linux 2.19.1

/dev/sdb1: clean, 137676/4276224 files, 1075205/17089843 blocks

/dev/sdc1: clean, 40950/61054976 files, 130070218/244190208 blocks

Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox

 * Starting AppArmor profiles       [80G 
[74G[ OK ]

 * Starting Kernel Oops catching service kerneloops       [80G 
[74G[ OK ]

speech-dispatcher disabled; edit /etc/default/speech-dispatcher

Checking for running unattended-upgrades: 

 * Starting bluetooth       [80G 
[74G[ OK ]

 [33m*[39;49m PulseAudio configured for per-user sessions

saned disabled; edit /etc/default/saned

 * Checking battery state...       [80G 
[74G[ OK ]

I've had this problem several times in the past. Try reinstalling nvidia-current from a recovery login, then run nvidia-xconfig. That usually works for me.

---

### Post by Harry33 on 2011-08-19
> **sgage said:**
> I've had this problem several times in the past. Try reinstalling nvidia-current from a recovery login, then run nvidia-xconfig. That usually works for me.

Nowadays it might be a better idea to just reinstall nvidia-current and not to run command "nvidia-xconfig". This command modifies xorg.conf file.
That is because the file /etc/X11/xorg.conf is not needed anymore, not even with proprietary drivers, and can be removed.

---

### Post by sgage on 2011-08-19
> **Harry33 said:**
> Nowadays it might be a better idea to just reinstall nvidia-current and not to run command "nvidia-xconfig". This command modifies xorg.conf file.
That is because the file /etc/X11/xorg.conf is not needed anymore, not even with proprietary drivers, and can be removed.

I know that, but I've sometimes found that it helps - it makes a perfectly good xorg.conf. Sometimes that has gotten it going for me.

---

### Post by Harry33 on 2011-08-19
> **sgage said:**
> I know that, but I've sometimes found that it helps - it makes a perfectly good xorg.conf. Sometimes that has gotten it going for me.

That command also add lines about keyboard and mouse, even if thouse drivers are not installed and evdev is used instead.

---

### Post by sgage on 2011-08-19
> **Harry33 said:**
> That command also add lines about keyboard and mouse, even if thouse drivers are not installed and evdev is used instead.

Yes, I suppose I should not generalize that what works for me will work for everyone. Easy to forget how many different configurations of hardware are out there...

Works for me, though :KS

---

### Post by Harry33 on 2011-08-19
> **sgage said:**
> Yes, I suppose I should not generalize that what works for me will work for everyone. Easy to forget how many different configurations of hardware are out there...

Works for me, though :KS

Sgage, I did not mean to say it would not work. I believe it works for most setups.
However, if it does not work, it is worth trying to delete xorg.conf and let the system autodetect device settings.

---

### Post by lime4x4 on 2011-08-19
890fxa-gd65 mother board. amd 4core processor. 8 gigs of ram. 80 gig ssd drive for root file system and a 500 gig sata drive for home. Running 2 nvidia based video cards a geforce 8600 and a geforce 450. I was able to get to a recovery console and installed nvidia-current and ran nvidia-xconfig. Still doesn't boot. Also is there an easier way to get to the recovery console? The pc boots pretty fast the only way i'm able to get to the recovery console is to cycle the power button a few times while booting.





ubuntu@ubuntu:~$ lspci | grep VGA
02:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600 GT] (rev a1)
05:00.0 VGA compatible controller: nVidia Corporation GF106 [GeForce 450 GTS] (rev a1)

---

### Post by lime4x4 on 2011-08-21
Well i got it to work. I ended up saving my data from my /home drive to another drive. Reinstalled oneiric and left it format the /home drive as well.

---

