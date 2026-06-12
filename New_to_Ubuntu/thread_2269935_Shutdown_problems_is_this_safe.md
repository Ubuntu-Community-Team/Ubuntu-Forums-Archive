---
title: "Shutdown problems: is this safe?"
date: 2015-03-19
forum: New to Ubuntu
---

### Post by heebiejeebies2 on 2015-03-19
Hi all,  the only things I cannot seem to get working in Ubuntu 14.04 are shutdown, restart and suspend.  Surprisingly hibernation works most of the time, so I just do that when I've finished with the session and it usually works fine.  But when I actually restart or shut down, the screen goes immediately blank, without any indication that the system is actually stopping processes or anything.  The fan and power light stay on, and the only way out from here is to hold the power switch down.  I notice if I do this from the terminal using "sudo shutdown -h now" then the same thing happens, but the hard disk doesn't make a "fweeee" noise when I hold the power switch down.  I'm happy enough to keep doing this if it's the only way (I've tried about 5 other suggestions from other threads that didn't work) - but is this going to damage my computer or the installation?
Thanks!

---

### Post by Bucky Ball on 2015-03-19
Repeatedly doing a hard shutdown is not good for your computer or hard drive. Hopefully someone can leap in with some help. 

In an effort to avoid a hard shutdown, when you hit the blank screen, can you get to a tty with control+alt+F1? If so, then try:

```
sudo reboot -h now
```

---

### Post by ajgreeny on 2015-03-19
Also what happens and what errors, if any, do you see if you close all running applications, then open a terminal and use command ```
sudo shutdown -h now
```

---

### Post by heebiejeebies2 on 2015-03-19
Bucky Ball - darn, I'd hate to have fixed so many errors with this thing and then have to can it and go back to windows just because of a blasted shutdown problem!  And no, ctrl-alt-f1 does nothing at the blank screen.

ajgreeny - when I type that into the terminal, sometimes it says "System is going down for reboot NOW!" And other times it just immediately closes the terminal then goes to the blank screen.

---

### Post by Bucky Ball on 2015-03-19
Couple of questions. Is this a fresh install and if so did you check the installer for defects before installing? There's an option when you boot the disk/USB. If a fresh install, perhaps try again and this time check the md5sum. Does Ubuntu work fine from the install media?

If not a fresh install, what were you doing when the black screen started occuring? Did you switch on one day and the problem just started? After a recent upgrade/update?

Are you dual-booting with Windows or is the Ubuntu only on the disk?

---

### Post by heebiejeebies2 on 2015-03-19
This installation is about 2 weeks old, and no - it doesn't work from the LiveCD either.  It's always done the same thing.  I didn't check for defects when I installed it but I used several different LiveCDs and it did the same thing.  It's just ubuntu on this drive, not windows.

It really does seem like everything stops except the fan, though - is it definitely dangerous?  I'd say the hard drive is stopped given the lack of a "fweee" noise on powering off - which I've definitely noticed when hard-powering off by other means.

---

### Post by heebiejeebies2 on 2015-03-19
Oh well - back to Windows then!  What a bummer!  This is the 4th computer I've tried to install Linux on and every time there's been one weak link that's ruined the whole thing.  How the hell do so many people get this thing working!?

---

### Post by QIII on 2015-03-19
Just lucky, I guess!  ;)

You know, you get a sore head from bashing your head against a wall.  An OS just isn't worth all that.  I don't share some people's religious fervor for Linux, so I don't mind just saying to use Windows if that works for you.  The machine should do what you want, not make you bloody your forehead.

Install Linux in a virtual machine if you want to keep puttering with it.  Relax.  Have a cup of joe.  Take a long walk.

---

### Post by mc4man on 2015-03-19
If you are still on then maybe post the results of this - 
```
sudo lshw -C display
```
(- I've found a semi obscure issue regarding shutdowns that can affect *some*  Intel Integrated Graphics machines

---

### Post by heebiejeebies2 on 2015-03-19
> **QIII said:**
> Just lucky, I guess!  ;)

You know, you get a sore head from bashing your head against a wall.  An OS just isn't worth all that.  I don't share some people's religious fervor for Linux, so I don't mind just saying to use Windows if that works for you.  The machine should do what you want, not make you bloody your forehead.

Install Linux in a virtual machine if you want to keep puttering with it.  Relax.  Have a cup of joe.  Take a long walk.

I agree, it's just very annoying when you get so close.  It's like your horse tripping in the home stretch of the Kentucky Derby or something.  And I'll have to go back to W*****s (obscenity censored) and PAY for it, since I accidentally wiped it during the Ubuntu installation.  Gaaaaaaad.  Maybe I'll just buy a typewriter instead!

---

### Post by heebiejeebies2 on 2015-03-19
> **mc4man said:**
> If you are still on then maybe post the results of this - 
```
sudo lshw -C display
```
(- I've found a semi obscure issue regarding shutdowns that can affect *some*  Intel Integrated Graphics machines

YESYESYESYESYESYESYES?  That's me!  First it says

**PCI (sysfs)**

And then

[B]  *-display               
       description: VGA compatible controller
       product: ValleyView Gen7
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0e
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:108 memory:90000000-903fffff memory:80000000-8fffffff ioport:2050(size=8)
[/B]

---

### Post by heebiejeebies2 on 2015-03-20
Does the aforementioned gobbledygook mean anything to anyone?

At any rate, WE MAY HAVE A DEVELOPMENT.  I found a terminal command (I'll past it later when I can find it, for posterity) which seems to have made "sudo shutdown -h now" turn the computer off properly.  So as long as that holds, the only thing I need to know now is - how do I make the shutdown menu halt the system?  Or alternatively, how do I allow a non-admin to halt the system?

---

### Post by mc4man on 2015-03-20
I'm not up on issues with intel-atom & or baytrail graphics. Here I have GeForce GT 755M (not used in linux) & Haswell (HD 4600) 
What I've found in recent times (14.04+) is that the default included nouveau drivers can cause slow log out/ins & *sometimes* a hang in restarts/shutdowns.
So I get rid of nouveau ( xserver-xorg-video-nouveau ) as it's not needed here.

You could give  that a try if inclined though may be more related to your  intel-atom, ect. rather than some unused driver
What kernel are you using?
uname -r will show

---

### Post by heebiejeebies2 on 2015-03-20
Thanks, the kernel is 3.16.0-31-generic

I can try getting rid of that driver I guess, would that be **sudo service xserver-xorg-video-nouveau remove**?? And it's definitely not needed?  The computer's not going to blow up if I remove it, is it?

---

### Post by heebiejeebies2 on 2015-03-20
Also, for future-googlers, this is the code I typed into the terminal.  The terminal reacted weirdly and I didn't think it had done anything, but now **sudo shutdown -h now** actually turns the computer off, so I guess it did!

[CENTER][CENTER] [COLOR=#222222][FONT=consolas]echo "blacklist dw_dmac" | sudo tee -a /etc/modprobe.d/blacklist.conf[/FONT][/COLOR][/CENTER][/CENTER] [CENTER][CENTER] [COLOR=#222222][FONT=consolas]echo "blacklist dw_dmac_core" | sudo tee -a /etc/modprobe.d/blacklist.conf


[/FONT][/COLOR][/CENTER][/CENTER]

---

### Post by mc4man on 2015-03-21
> **heebiejeebies2 said:**
> Thanks, the kernel is 3.16.0-31-generic

I can try getting rid of that driver I guess, would that be **sudo service xserver-xorg-video-nouveau remove**?? And it's definitely not needed?  The computer's not going to blow up if I remove it, is it?
No it won't blow & no, wrong command. If ever ...

```
sudo apt-get purge xserver-xorg-video-nouveau
```

---

### Post by mc4man on 2015-03-21
Also to note- 
I put in a 2nd 14.04 install using 14.04.2 & it continues to show some shutdown/restart issues. completely resolved by getting rid of the plymouth packages  can be safely removed (I've no interest in 5 red lights at all.
So you could also try - 
```
sudo apt-get purge plymouth-theme-ubuntu-text plymouth-theme-ubuntu-logo
```
Now while not required when removing the above it's better then to also remove quiet & splash from grub which also should remove the vt-handoff nonsense

To do that edit /etc/default/grub & remove quiet splash from GRUB_CMDLINE_LINUX_DEFAULT= line (line 11 here) so it's just this, assuming you hadn't added anything to that line - 
```
GRUB_CMDLINE_LINUX_DEFAULT=""
```
Then run this & restart in current manner, any positive effects should show in future shutdowns/restarts
```
sudo update-grub
```

If trying & wanting to use gedit then go - 
```
sudo -H gedit /etc/default/grub
```

---

### Post by heebiejeebies2 on 2015-03-21
You are a champion.  I will try these and see how they go.  If you have saved me from going back to W*****s then I will carve a sculpture of your body and worship it.

---

### Post by heebiejeebies2 on 2015-03-22
Your suggestions didn't seem to fix anything but I've noticed I can now shutdown through Cairo Dock or though the app "qshutdown". It seems to be the terminal command I posted earlier that made the difference.  The regular ubuntu menu still doesn't shut down but oh well - problem solved! Thanks everyone!

---

### Post by Bucky Ball on 2015-03-23
Good news. Please see the second link in my signature for how to mark the thread as solved. Thanks.

---

