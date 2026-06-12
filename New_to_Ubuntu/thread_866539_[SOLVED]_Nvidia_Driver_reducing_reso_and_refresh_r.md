---
title: "[SOLVED] Nvidia Driver reducing reso and refresh rate...help?"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by The MAX on 2008-07-21
So I have most of the drivers installed and have linux working damn near perfect to where I want it. However I still haven't installed any graphics drivers for my 8800GT. 
I notice in System->Administration->hardware drivers there is already an Nvidia accelerated graphics driver (latest cards) listed that I can use. When I select that and restart my computer is at a reduced resolution (normally use 1600x1200) of 1154 x whatever or something and the refresh rate is either 50 or 51....?
Anyways, from what I've been reading in here it might have something to do with editing the xord.conf file? but I'm not sure so I wanted to make this post to see if anyone could give me a clear answer.

I've also downloaded the drivers from Nvidia and haven't been able to figure out how to NOT run an x server to install the drivers.

Anyways, help is appreciated, thanks in advance.

---

### Post by wolfen69 on 2008-07-21
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then restart x, or reboot. if that doesnt work, we can try other things.

---

### Post by The MAX on 2008-07-21
yeah that didn't work.
I mean without that driver installed my reso is fine, but shouldn't I be using an Nvidia driver?
Also a little more info on exactly what you want me to do if thats okay. I didn't know if you wanted me to enable it then try the command or what, but I tried every possible combo and nothing seemed to give me good results with having the nvidia driver enabled.
Thanks for the help. More to come? lol

---

### Post by The MAX on 2008-07-22
anyone? I'm sure this must be a common issue as This is a very popular card, others probably just know how to deal with it. lol

---

### Post by ibuclaw on 2008-07-22
```
sudo apt-get install nvidia-settings
```

Then look it up in the "System>Administration>NVIDIA X Server Settings"

You should be able to set all things there.

[EDIT]
If you wish to save the settings to the xorg.conf file, run
```
gksu nvidia-settings
```

Regards
Iain

---

### Post by xfyler on 2008-07-22
^^ thx works

---

### Post by The MAX on 2008-07-22
AH HA! Appears to work beautifully. Thanks for the help.

Just to clairfy to anyone else with this issue and is total noob

Go to System->Administration-> Hardware Drivers 
enter your password
enable the nvidia driver then you can restart ubuntu without a total restart with the command
```
sudo shutdown now
```
select resume normal boot
Login
run this in terminal
```
sudo apt-get install nvidia-settings
```
Go to System->Administration->Nvidia X Server Settings 
and voila, you can use this app to manually change your resolution and refresh rate.

Thanks Again Guys

---

### Post by Dileeshvar on 2008-07-22
hello guys,
thanks for your post but it solved only half of my problem Nvidia X server settings is installed but I am getting a resolution maximum of 640X480 !!!
please some one help me out !!!

---

### Post by The MAX on 2008-07-22
are you trying to change it in the ubuntu screen resolution control or in the nvidia x server app?

Cause that was my problem, the ubuntu standard was giving me restrictions but the nvidia app allows me to change it to whatever.

---

### Post by Dileeshvar on 2008-07-22
> **The MAX said:**
> are you trying to change it in the ubuntu screen resolution control or in the nvidia x server app?

Cause that was my problem, the ubuntu standard was giving me restrictions but the nvidia app allows me to change it to whatever.

No actually I did try to change my resolution in Nvidia X server settings only but i was getting a maximum resolution of 600X480 where as it was 800X600 before I installed the Nvidia x server !!
so please help me out !!

---

### Post by xfyler on 2008-07-23
so I run nvidia-settings as root, set the new refresh rate, then click on save to xorg.conf, but after restart is back only 60Hz (my is 85Hz).

do you know whre is problem?

---

### Post by smergs on 2008-08-05
Thanks guys.  Just installed ubuntu yesterday and the slow refresh rate on my old crt monitor has been driving me crazy today.  I have two identical monitors sitting side by side.  One was running Windows at 85 Hz and this one was running at 63.  It's amazing how much flicker I was getting on the ubuntu machine before.  Especially noticable out of the side of my eye when looking over at the windows screen!

All is good now.  Thanks!!!!

---

