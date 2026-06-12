---
title: "New to ubuntu some problems"
date: 2024-10-15
forum: New to Ubuntu
---

### Post by theelf on 2024-10-15
Hi, greetings, sorry my english,  im new to ubuntu, im still using windows xp  but decide to update, and since i dont like win10+ much, and in 80/90s i was unix user, i just installed ubuntu to give a try, i installed 24.10


I really love the desktop,  but i have a  problem i cant solve,   i cant see any option to save window positions,  always open in top-left corner, i cant work, spend half time using mouse to move windows, totally unusable


Im stuck.  Tried xubuntu and xfce remember window position, but like ubuntu gui



thanks


NOTE: I tried a extension, smart automove, that move windows to a remembered position, but it take a fraction of second to move the window after creates and lookd bad


NOTE2: I try to add --geometry parammeters to gnome-terminal and nautilus but no luck...

---

### Post by TheFu on 2024-10-15
> **theelf said:**
> Hi, greetings, sorry my english,  im new to ubuntu, im still using windows xp  but decide to update, and since i dont like win10+ much, and in 80/90s i was unix user, i just installed ubuntu to give a try, i installed 24.10

That's a huge leap.  Wow.  I ran both OSes for 15+ yrs before finally deciding to drop MSFT stuff.  
However, I fear you picked the wrong release.  24.10 is NOT an LTS, which means in 6 months, you need to install 25.04 (also not an LTS), then in another 6 months, you'll need to install 25.10 (also not an LTS). Basically, you'll be installing a new OS every 6 months for 1.5 yrs, until the next LTS comes around.  That's a bunch of work for someone that hasn't switched OSes since 2002! 

Instead, before you have too much invested in 24.10, if it were me, I'd do a fresh install of 24.04 which is the last LTS release.  If the computer is from the WinXP timeframe, it is unlikely that the flagship Ubuntu Desktop with Gnome will be a good experience.  Gnome really wants a new computer and lacking that, a good-to-great GPU.

> **theelf said:**
> I really love the desktop,  but i have a  problem i cant solve,   i cant see any option to save window positions,  always open in top-left corner, i cant work, spend half time using mouse to move windows, totally unusable
We need to know the exact DE you are using.  24.10 is very new.  I haven't looked at Gnome with 24.10. I did load up Kubuntu 24.10 for about 45 minutes on Sunday.  I usually don't bother with non-LTS releases.  Switching an entire OS every 6 months is just too often for me and I've been running Linux non-stop since 1993.

So, the first thing I'd strongly suggest is that you read about the differences between LTS and non-LTS Ubuntu Releases.  That is absolutely critical to understand to keep your system in-support. Running an unsupported, unpatched, version is Linux has some risks.  Best not to use it.  Stay on LTS releases.

> **theelf said:**
> Im stuck.  Tried xubuntu and xfce remember window position, but like ubuntu gui  I'm guessing you mean Gnome DE?
You can run **inxi -b** to see the current DE used.  Also, it is likely that the display server is Wayland, not X/Windows. Wayland works great for many people, but it doesn't work well for me. It break common Unix workflows because it fixed/prevents some of the security problems that X11 has always had.

> **theelf said:**
> 
thanks


NOTE: I tried a extension, smart automove, that move windows to a remembered position, but it take a fraction of second to move the window after creates and lookd bad


NOTE2: I try to add --geometry parammeters to gnome-terminal and nautilus but no luck...

--geometry is from X11.  Many newer programs don't support it.  Doesn't that suck?  Placement of windows on the desktop is usually the job of the window manager, WM.  With Gnome, they are getting away from normal, standards-following, WMs.  That sorta sucks.

Short of telling you to find the Ubuntu Desktop Help at [https://help.ubuntu.com/stable/ubuntu-help/index.html](https://help.ubuntu.com/stable/ubuntu-help/index.html) , I can't help with Gnome questions.  I actually use a WM from 1996 still and don't use any DE.  We all have different tastes, right?

But really, you should get an LTS release and use that.  Ubuntu Desktop 24.04 has 5 yrs of standard support.  Other "flavors" running different DEs on 24.04 only have 3 yrs of support.

---

### Post by Dennis N on 2024-10-15
> I really love the desktop, but i have a problem i cant solve, i cant see any option to save window positions, always open in top-left corner, i cant work, spend half time using mouse to move windows, totally unusable.

You are correct about this problem. It's not Ubuntu itself, but seems application dependent because I have a few applications (examples: Audacious, LibreOffice) that remember their last screen position and window size. Others, including many (all?) Gnome applications (like Files, Calendar, etc.) don't. So its clear applications can control this.  

And its not just in Gnome 47 (used by Ubuntu 24.10). Previous recent Gnome releases are the same.

In Tweaks, you can opt to center the window when launching applications. But that isn't much help.

---

### Post by theelf on 2024-10-15
> **TheFu said:**
> That's a huge leap.  Wow.  I ran both OSes for 15+ yrs before finally deciding to drop MSFT stuff.  
However, I fear you picked the wrong release.  24.10 is NOT an LTS, which means in 6 months, you need to install 25.04 (also not an LTS), then in another 6 months, you'll need to install 25.10 (also not an LTS). Basically, you'll be installing a new OS every 6 months for 1.5 yrs, until the next LTS comes around.  That's a bunch of work for someone that hasn't switched OSes since 2002! 

Instead, before you have too much invested in 24.10, if it were me, I'd do a fresh install of 24.04 which is the last LTS release.  If the computer is from the WinXP timeframe, it is unlikely that the flagship Ubuntu Desktop with Gnome will be a good experience.  Gnome really wants a new computer and lacking that, a good-to-great GPU.


We need to know the exact DE you are using.  24.10 is very new.  I haven't looked at Gnome with 24.10. I did load up Kubuntu 24.10 for about 45 minutes on Sunday.  I usually don't bother with non-LTS releases.  Switching an entire OS every 6 months is just too often for me and I've been running Linux non-stop since 1993.

So, the first thing I'd strongly suggest is that you read about the differences between LTS and non-LTS Ubuntu Releases.  That is absolutely critical to understand to keep your system in-support. Running an unsupported, unpatched, version is Linux has some risks.  Best not to use it.  Stay on LTS releases.

  I'm guessing you mean Gnome DE?
You can run **inxi -b** to see the current DE used.  Also, it is likely that the display server is Wayland, not X/Windows. Wayland works great for many people, but it doesn't work well for me. It break common Unix workflows because it fixed/prevents some of the security problems that X11 has always had.



--geometry is from X11.  Many newer programs don't support it.  Doesn't that suck?  Placement of windows on the desktop is usually the job of the window manager, WM.  With Gnome, they are getting away from normal, standards-following, WMs.  That sorta sucks.

Short of telling you to find the Ubuntu Desktop Help at [https://help.ubuntu.com/stable/ubuntu-help/index.html](https://help.ubuntu.com/stable/ubuntu-help/index.html) , I can't help with Gnome questions.  I actually use a WM from 1996 still and don't use any DE.  We all have different tastes, right?

But really, you should get an LTS release and use that.  Ubuntu Desktop 24.04 has 5 yrs of standard support.  Other "flavors" running different DEs on 24.04 only have 3 yrs of support.


Hi, thanks a lot for reply,  my idea is to install a OS and never update, i dont like to update, and never do. Im still using same XP x64 install since i installed in 2007, just every new computer i had,  i just image to new hdd, never reinstalled.  The only thing i care to keep more or less updated is web browser. Im still using paint shop pro 7 for image, winamp for music, turbo c for programing etc etc

Anyways, i tried ubuntu 24.04 but same problem, gnome did not remember window positions,  and i realize something, xfce did not too, i mistake,  just have two options, under mouse or middle screen, did not test much more, but i "visually" dont like much xfce. It happen to me same with windows 10, the OS works fine, but is horrible, dark mode is broken,  there is no consistent in gui, some windows use old style, others app mode, others net, a disaster, gnome out of box look soo nice, but sadly window remembering is a must for me

ubuntu run fine in my computer, is a i5, 16gb ram, and for now a secondary 256gb SSD for ubuntu to try, i have XP in a 1TB NVMe that if I decide to keep ubuntu will use



I really hope to find a solution,  i will try 24.04 more in deep, and came back later

thanks


> **Dennis N said:**
> You are correct about this problem. It's not Ubuntu itself, but seems application dependent because I have a few applications (examples: Audacious, LibreOffice) that remember their last screen position and window size. Others, including many (all?) Gnome applications (like Files, Calendar, etc.) don't. So its clear applications can control this.

And its not just in Gnome 47 (used by Ubuntu 24.10). Previous recent Gnome releases are the same.

In Tweaks, you can opt to center the window when launching applications. But that isn't much help.


Thanks a lot for your reply, yes, i checked gnome 46 and same problem, it seems gnome dont do remember window position, but rely on every program to do, and seems almost nobody do...

---

### Post by paulycalvin on 2024-10-18
I don't know if you could just install gnome-tweaks and set windows to open in the center. If you want to try that.

open the terminal and typ

sudo apt install gnome-tweaks

open the app and find the setting to open windows in the center.

---

### Post by shadowtabby on 2024-10-18
Heyo,

Thank you for your reply.  Man this change from windows to linux, ha been overwhelming.  Mostly in a good way.  The amount of people that are willing to help and not run you down because you're new, honestly makes this the best experience.

Thank you I will try this now.

---

### Post by shadowtabby on 2024-10-18
Heyo,

Thank you for your reply.  Man this change from windows to linux, ha been overwhelming.  Mostly in a good way.  The amount of people that are willing to help and not run you down because you're new, honestly makes this the best experience.

Thank you I will try this now.

---

