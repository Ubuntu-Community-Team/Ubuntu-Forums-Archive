---
title: "Ripple in the screen"
date: 2014-04-21
forum: New to Ubuntu
---

### Post by ftf99 on 2014-04-21
Hi everyone.

I installed Lubuntu 14.04 on my asus eee 1101ha (gma500 video adapter), and now I have ripples on my screen. Is is like on old TV with bad antenna. I had lubuntu 13.04 before and everything was OK.

Sometimes this effect appears instantly after choosing lubuntu in GRUB, sometimes - after signin in.

Please, help me, how can I fix it?

---

### Post by ofnuts on 2014-04-21
Looks like a bad refresh rate.

---

### Post by ftf99 on 2014-04-21
There are only two options: 60Hz and Auto. I tried both - it does not help.

---

### Post by roberto15 on 2014-04-25
Hi ftf99, I have the exact same problem! I installed Lubuntu 14.04 alongside windows xp, it works great except for the ripples on the screen. I read that GMA500_GFX might solve the problem but since I'm a newbie I still have to learn how to install it. My netbook is an Eee pc 1201HA with gma 500 graphics. Hope someone can help.

---

### Post by ftf99 on 2014-04-25
> **roberto15 said:**
> Hi ftf99, I have the exact same problem! I installed Lubuntu 14.04 alongside windows xp, it works great except for the ripples on the screen. I read that GMA500_GFX might solve the problem but since I'm a newbie I still have to learn how to install it. My netbook is an Eee pc 1201HA with gma 500 graphics. Hope someone can help.

Since ubuntu 12.04 GMA500_GFX is already installed. You can check this by running lsmod | grep gma500. So I think that we should change some settings to solve the problem.

---

### Post by roberto15 on 2014-04-25
Yeah, I found it, and you are right, it has to be a setting, I suspect in the config file, cause in my case, before login in the screen looks fine, but after login it gets the ripples in the screen. Now it does it also in the login section. If it helps, I can see the message: "...trying to get blank count for disabled pipe" repeated twice just as ubuntu goes to the login screen.

---

### Post by ftf99 on 2014-04-30
It is not a solution, but after hibernation ripple is gone.

---

### Post by roberto15 on 2014-05-02
I tried hibernation buy my laptop actually crashes when I do that. In my Xorg.0.log i found these two errors:
 (EE) Failed to load module "psb" (module does not exist, 0)
(EE) Failed to load module "psbdrv" (module does not exist, 0)
part of gma500 poulsbo I beleive. 
I'm thinking of trying lubuntu 12.04 instead. Maybe it'll work better.

---

### Post by verymadpip on 2014-05-02
Hi there.
Lubuntu 12.04 is no longer supported.
I'd suggest not trying that.

---

### Post by mikewhatever on 2014-05-03
Very odd. I've also installed Lubuntu 14.04 on a Dell mini 10 with Intel's GMA500. It sucks badly, but no ripples.
There are some psb related errors:
> less /var/log/Xorg.0.log | grep psb
[    30.464] (==) Matched psb as autoconfigured driver 0
[    30.464] (==) Matched psb_drv as autoconfigured driver 1
[    30.464] (==) Matched psb as autoconfigured driver 2
[    30.464] (==) Matched psb_drv as autoconfigured driver 3
[    30.465] (II) LoadModule: "psb"
[    30.467] (WW) Warning, couldn't open module psb
[    30.467] (II) UnloadModule: "psb"
[    30.467] (II) Unloading psb
[    30.467] (EE) Failed to load module "psb" (module does not exist, 0)
[    30.467] (II) LoadModule: "psbdrv"
[    30.469] (WW) Warning, couldn't open module psbdrv
[    30.469] (II) UnloadModule: "psbdrv"
[    30.469] (II) Unloading psbdrv
[    30.469] (EE) Failed to load module "psbdrv" (module does not exist, 0)
[    30.510] (==) Matched psb as autoconfigured driver 0
[    30.510] (==) Matched psb_drv as autoconfigured driver 1
[    30.510] (==) Matched psb as autoconfigured driver 2
[    30.510] (==) Matched psb_drv as autoconfigured driver 3
[    30.510] (II) LoadModule: "psb"
[    30.513] (WW) Warning, couldn't open module psb
[    30.513] (II) UnloadModule: "psb"
[    30.513] (II) Unloading psb
[    30.513] (EE) Failed to load module "psb" (module does not exist, 0)
[    30.513] (II) LoadModule: "psbdrv"
[    30.515] (WW) Warning, couldn't open module psbdrv
[    30.515] (II) UnloadModule: "psbdrv"
[    30.515] (II) Unloading psbdrv
[    30.515] (EE) Failed to load module "psbdrv" (module do

---

### Post by roberto15 on 2014-05-03
Hi,
Thanks for letting me know, I'll stick with 14.04 hopefully we'll find a solution.

---

### Post by roberto15 on 2014-05-03
I get the exact same thing in my xorg.0.log, The ripples are very small but throughout the screen.

---

### Post by linuxuser330250 on 2014-05-17
I also have the exact same problem. My hardware: ASUS Eee PC 1101HA.

I installed Ubuntu 12.04.4 LTS and everything worked fine. The system was quite usable and the speed was almost the same as with Windows XP (the second system on this dualboot installation).

Anyway, I just upgraded this netbook with an SSD, and since XP support had ended I decided to try Vista, because I have an unused license laying around. That took quite some time!

After Vista was up and running, I reinstalled Ubuntu and decided to upgrade from 12.04 to 14.04 LTS. And here I am: 14.04 has two issues: one is speed in general, since Unity is very demanding on the hardware! So Xubuntu or Lubuntu would have been the better choice. The second issue (which seems to be across the [L|X|]ubuntu distribution) is the ripple or flicker issue.

I would very much like to see a solution to this.
It is a fresh Ubuntu 14.04 installation. I also have the Xorg.log messages about missing psb and psbdrv modules.

---

### Post by roberto15 on 2014-05-17
Lubuntu is a lot faster than XP on my Eee PC. But still haven't found the solution to the annoying ripples. The other problem I have is that it won't come back from hibernation, but I think that's a known issue and hope will be solved soon. This is my first linux experience and it's nice to be able to do a lot more than with XP, so I'll continue using it, hopefully someone can help.

---

### Post by eages on 2014-05-23
I have an 1101HAb and experienced similar issues on other distributions (archbang if I recall). I've not experienced this same problem on Xubuntu 14.04 however. The problem I /have/ encountered however is my on button doesn't seem to hook my laptop out of standby anymore. Also, I get apportcheckresume errors on boot. Hibernation seems to work but the screen is black once resume finishes. Judging by the logs in this thread, I'd like to suggest that the issue possibly stems from the modules being renamed to gma500_gfx recently (I recall reading that change in a changelog somewhere). That's the name of the module currently running on my machine. The others mentioned here seem to be missing.

---

### Post by roberto15 on 2014-05-24
I think I killed 3 birds with one stone, so to speak. With the following instructions I was able to make my netbook Hibernate properly, enable Suspend and removed the ripples from my screen.
 
Caveats:
	- I did it on a Asus Eeee pc with the infamous Poulsbo. Don't know if it works on other netbooks/laptops
	- your netbook or laptop should have the hibernate function.
	- Suspend only works after using hibernate once.
 
This is what I did:
 
Press Ctrl+ALt+T on your keyboard to open the terminal. When it opens, run:
 
sudo pm-hibernate
 
After your computer turns off, switch it back on. Did your open applications re-open? If hibernate doesn't work, check if your swap partition is at least as large as your available RAM.
 
To re-enable hibernate, run the commands below one by one to edit the config file:
 
sudo -i
 
cd /var/lib/polkit-1/localauthority/50-local.d/
 
gedit com.ubuntu.enable-hibernate.pkla
 
Copy and paste below lines into the file and save it.
 
[Re-enable hibernate by default in logind]
Identity=unix-user:*
Action=org.freedesktop.login1.hibernate
ResultActive=yes
 
I restarted my netbook, the ripples where there again, so I made it hibernate, when it came back on, the ripples where gone, the screen looks crisp and I was able to use the Suspend function. 
So, now all I do is start it up, make it hibernate (which only takes a few seconds) , make it come back on and no more ripples and with the advantage of a very useful Suspend function. 
 
Hope it works for you guys as well as it did for me!

---

### Post by Wim_Peeters on 2014-05-28
Hello,

I just started getting ubuntu 14.04 on my (old) sony vaio p netbook -- as a Windows XP substitute. 
It was very slow at first, so I installed Xubuntu 14.04 (no 3d) and now things work generally fine. Very happy with it and I've started converting some other machines to (x)ubuntu as it has most of the features I need (a better "evernote" application would be nice). No issues in general.
On the vaio-p however, I'm still having some screen issues though : indeed "ripples" but also at startup there seems to be an issue with gma500 and "disabled pipes" ? Video is choppy and also doesn't sync with audio.

---

### Post by roberto15 on 2014-05-30
Hi,
The solution I posted before was for Lubuntu 14.04 . I believe that for Ubuntu and Xubuntu the directory path is different and the commands are slightly different than what I posted above. I remember seeing it somewhere on the net. try google for hibernate enabling and your ubuntu version. Does hibernate work in your machine? and do the ripples dissapear after turning it on again?

---

