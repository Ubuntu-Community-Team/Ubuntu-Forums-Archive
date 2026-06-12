---
title: "No gui after Driver install"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by Yooshua on 2008-08-24
So I am very new to Linux! I consider my self a computer savvy person so I want to try it out. I installed Ubuntu on my old box no problem. Booted it up installed all the auto updates. Then I restarted... Everything is working fine.

So I get home from work today and decided to install the display drivers via the automatic interface. Now I have a big problem. Since installing the new drivers I get no GUI after boot up. I can get to the grub troubleshooting prompt. I get the "unbuntu" logo and progress bar during load up also. After that just a blank screen.

Also I get an message that is displayed by my monitor that says optimal settings are 1600x1050 (the native resolution). So I look at my screen resolution via my monitors info menu and it says that the monitor is set to 1600x1200.

What I would like to know is there any way I can uninstall/modify the drivers via a command line interface and/or set the resolution to 1600x1050, to see if that fixes the problem?

*edit... removed old problem

Hardware specs:
Mobo: MSI intel 865G (neo 2 series)
CPU: Intel P4 2.8ghz (prescott core)
GPU: ATI X800XL (AGP bus, 256mb ram)
ram: 1ghz DDR1 400mhz
Sound: SB Audigy2
Monitor: Samsung Syncmaster 2226BW (connected via VGA cable)
Ubuntu: 8.04.01 - x86 via the liveCD

Thanks for any help!

---

### Post by Yooshua on 2008-08-24
So I was unable to uninstall the driver by doing the following.

> Guessing here: When you boot, choose recovery mode. You should get the option to run terminal mode instead of GUI.

Once you have logged in you should be able to reconfigure x windows. There is probably a handy way to do this that someone else knows. I have manually edited /etc/X11/xorg.conf

Once reconfigured you can start X again via: startx

Another option, remove the driver via aptitude. For example, if the driver is for ATI then:

sudo apt-get remove xorg-driver-fglrx

Or run "sudo aptitude" to get access to all installed packages. Use "/" to enter search mode and type "restricted". + will add packages, - removes them. "G" go'es and changes the packages you marked.

Good luck,
Tim

---

### Post by Yooshua on 2008-08-24
now I rebooted I can get to the login. I login but after that it goes to just a white screen with a cursor... UGH!

---

### Post by sadako1 on 2008-08-24
Sorry if I'm hijacking...

I also have this problem. I've tried to uninstall by the above method without luck - it says the driver isn't installed (???) - and tried to install by the standard Ubuntu method as stated in the ATI wiki. I'm wondering if it has something to do with the Compiz-fusion stuff that I installed at the same time.

ATI X1800XT 512 (PCI-E)
AMD64 3700
2GB Mushkin Redline (PC4000)
Sapphire PI mobo
Ubuntu Hardy 8.04
(Windows XP)

---

### Post by Yooshua on 2008-08-25
So I think I'm just going to do a fresh install... For the 4th time =[

---

### Post by Yooshua on 2008-08-30
So I've done my reinstall and have decided to not install any restricted drivers. What I would like to do is set the Screen resolution to 1680x1050... The problem is I don't have that option in the select resolution menu. I'm guessing I need to edit my X.org config file but I'm not sure!

---

### Post by starcannon on 2008-08-30
This should help:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

GL

---

