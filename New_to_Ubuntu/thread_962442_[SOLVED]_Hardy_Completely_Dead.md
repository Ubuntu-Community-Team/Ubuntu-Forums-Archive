---
title: "[SOLVED] Hardy Completely Dead"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by scientist434 on 2008-10-29
It all started about a week ago. I was using firefox 3 and openoffice 2.4 and then the screen went black for a second and then it just kicked me back out to the log on screen. Didn't worry to much about it figured it was just a minor glitch. Happened again last night but was running firefox and the default pdf viewer. Now I can't even log back in every time I try I either just get a the default log in background and doesn't even load desktop or it partly loads desktop but can't interact with anything. Only things that seem to work are hitting ctr + alt + backspace. Oh and if the desktop loads enough to see the start menus and things even though I can't click on them I can still use compiz and rotate my desktop cube but nothing else.

system specs. 
Hardy 8.04.1
2.4 ghz amd X2
2 gb RAM
nvidia geforce 8600


I am have to go to college so post replies will try to get back on in 4 or 5 hours to give responses.

---

### Post by NewJack on 2008-10-29
Have you installed any new programs or make any updates recently?

If not, maybe it is a hardware issue?  I would check the video card, RAM or see how hot your machine is running.

---

### Post by dracayr on 2008-10-29
maybe it's got to do with compiz. At startup, press esc, and select recovery mode from the menu. then select "drop to root prompt" (By the way, you could also try to choose "Fix x server" and see if that helps.). enter ```
gconftool-2 --type string --set /apps/gnome-session/rh/window_manager "metacity"
``` If nothing helps, wait until friday and then type ```
apt-get dist-upgrade
``` to upgrade to 8.10

dracayr

---

### Post by scientist434 on 2008-10-29
I don't think it is a hardware issue since I can dual boot vista just fine with out issue. I installed the updates that came out yesterday. I also installed my usb printer driver. It is a cannon pixama mp 160 had to use mp 150 driver cause I couldn't find a 160 driver. I will try disabling compiz when I get home but I haven't had a problem with compiz and I have been running since hardy beta 2. 

I if I can't get it working pretty soon I will just do the upgrade to intrepid. Is the beta pretty stable?

Oh forgot to mention in original post I can't turn the computer off for some reason it just locks up if i shutdown from log in screen. Second time I shut it down it just went beep beep like ten times then just made a constant beeeeeeep. till I held the power button.

---

### Post by ajgreeny on 2008-10-29
Yesterdays updates included a kernel update.  Try booting into a previous kernel when you get the grub menu, preferably the 2.6.24-19 one, and see if that helps.  I know the last two kernel updates have caused a lot of angst for a number of people, with situations similar to yours occurring for some.

---

### Post by billgoldberg on 2008-10-29
This might not fix your problem but it's an option if you're install is trashed.

Ubuntu 8.10 Intrepid Ibex comes out tomorrow.

---

### Post by scientist434 on 2008-10-29
ok tried the older version of the kernel. Same thing I got before exept it did let me shutdown. Tried going back to "metacity" also reset x-config at the same time. Now I can see everything on my desktop and I can see the aplications places and System bottoms but I can't click on anything. The only thing. I can interact with my widget that shows processor and ram usages. I can also interact with things on my desktop. Like my openoffice files open just fine. I can also navigate around since I have an external hardrive which shows up on the desktop so I can get to all my files. its just the tool bar at the top and bottom of the screen don't work at all. So it helped some any other Idea's. Right now I am backing everything up. 

THanks for all the help so far.

Edit:
apparently things working was just a short term thing when I went to copy things file browser quit working. I am now just looking at a tan screen.

---

### Post by usafe7ret on 2008-10-29
Regarding the statement above that kernel updates have caused "angst" in some users,

I am one of the angst-ridden users.  I have had issues with my nvidia FX5200 card drivers not being used and had to do a repair process that had me killing xserver and restarting it.

The process went well and the system worked until the last round of updates.

Now, I can't even get to the prompt screen.  

I am going to do a reinstall of the system back to Hardy and then get it functional.  I hate loosing drivers for my Brother printer, but I fixed it once before and can do it again.

Is there any way to pick and choose the updates you want to load and then delete the others you don't want?  I know you can uncheck them from synaptic update manager, but they keep showing up with the next round of updates. :confused:

I really don't care about updating DST zone changes for Argentina in my PC since I am in the US.

Sorry for the mini rant, but I really like Ubuntu and the way it runs my system when all is functional.

---

### Post by scientist434 on 2008-10-29
I don't know about updates I usually just install all of them which in this case i think killed me. I have decided to just reinstall the whole thing backed up all of my files using a Ubuntu live cd so i could actully do things. Now just reinstalling Hardy then going to try upgrading to Intrepid.

So not really solved but don't need help any more.

---

### Post by ajgreeny on 2008-10-29
> Is there any way to pick and choose the updates you want to load and then delete the others you don't want? I know you can uncheck them from synaptic update manager, but they keep showing up with the next round of updates. :confused:
In synaptic just uncheck the ones you don't want to update and update the rest.  Now go to the update icon a second time then the Package menu and choose to Lock Version.  These should now no longer show up in the update manager system tray icon, but will be locked to the version you have already.

---

