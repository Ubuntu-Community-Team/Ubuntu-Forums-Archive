---
title: "How can I diagnose my sluggish system?"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by Monona on 2008-10-30
I've been getting increasingly frustrated with the sluggishness of my ubuntu.  It seems like since Gutsy, things have gotten less responsive and programs take longer to load.

I have all the desktop effects turned off.  When I'm running top in the terminal, occasionally I'll notice that firefox or amarok will be hogging the CPU.  Even when I'm not using these programs, though, I'm noticing a pretty significant lag.

I don't really know where to start looking to diagnose this problem.  If I can get pointed in the right direction (or directions), I would really appreciate it.

I'm running Hardy 8.04 with kernel 2.6.24-21-rt on a Acer Travelmate 4010 with a 1.60 GHz Pentium M processor.

Thanks!

---

### Post by Zeedok on 2008-10-30
How much RAM does your system have?

How big is your SWAP? (Look at gnome system -> administration -> system monitor (third tab - system resources) for a GUI representation of how much SWAP is being used.

If you find that Ubuntu is a little too heavy for your hardware, you could always try Xubuntu - the XFCE desktop is much lighter and runs heaps faster than Ubuntu on the same hardware.  You still get most of the same programs and I really enjoyed using it on an old (I mean really old) laptop.

Good luck.

---

### Post by Monona on 2008-10-30
Thanks for the quick response!

My RAM would be displayed on the System Monitor as Memory, right?  If that's the case, I have 483.5 MiB of RAM.  Usage is right around 75% right now.

My Swap is 1.9 GiB.  45% being used right now.

What are the cons of switching to Xubuntu?  It's the same stuff under the hood, but with a different look and interface, right?  Would I still be able to keep stuff like Firefox bookmarks and add-ons?  Or would I have to do a fresh install?

---

### Post by acceph on 2008-10-30
hello
i am new in ubuntu 
i have installed 2 OS for my PC (Ubuntu and Windows XP)
if i log in using windows XP => Ubuntu partition will be hidden, 
but when i log in using Ubuntu, windows partition still appear..
is it possible to hide the windows partition in ubuntu?
how to do this?

Regards

---

### Post by SunnyRabbiera on 2008-10-30
> **Monona said:**
> Thanks for the quick response!

My RAM would be displayed on the System Monitor as Memory, right?  If that's the case, I have 483.5 MiB of RAM.  Usage is right around 75% right now.

My Swap is 1.9 GiB.  45% being used right now.

What are the cons of switching to Xubuntu?  It's the same stuff under the hood, but with a different look and interface, right?  Would I still be able to keep stuff like Firefox bookmarks and add-ons?  Or would I have to do a fresh install?

No if you use the xubuntu desktop package all will be fine

---

### Post by Zeedok on 2008-10-30
Your RAM and SWAP look OK, but I'm no expert.

Xubuntu ships with firefox and if you just switched to Xubuntu by going to the terminal and entering:
```

sudo aptitude install xubuntu-desktop
```

your bookmarks and addons will all still be there (these 'personalised' configurations are installed in you "Home" folder - in a hidden Firefox folder, which you can see by pressing "ctrl h" or going to the view menu in nautilis).

I'm not entirely sure (when I used Xubuntu I did a clean install) but I think if you switch to xubuntu (using the command above) all the programs you already have will still be there (some of the default Xubuntu programs are different - eg Xubuntu ships with Abiword, Ubuntu with OpenOffice).  

There are some other differences - for example Xubuntu uses 'Thunar' ([http://thunar.xfce.org/index.html](http://thunar.xfce.org/index.html)) as the file manager rather than 'Nautilus'([http://www.gnome.org/projects/nautilus/](http://www.gnome.org/projects/nautilus/)) which is used by Ubuntu.  Some of the menu options are called different things etc, but really it's not hard to adapt, and if the trade off is a much faster system (no matter how good your hardware is) then it might be worth it.  Also, most of the programs you use commonly are the same anyway.

Give it a go, you might like it.

---

### Post by random turnip on 2008-10-30
> **Monona said:**
> I've been getting increasingly frustrated with the sluggishness of my ubuntu.  It seems like since Gutsy, things have gotten less responsive and programs take longer to load.

I have all the desktop effects turned off.  When I'm running top in the terminal, occasionally I'll notice that firefox or amarok will be hogging the CPU.  Even when I'm not using these programs, though, I'm noticing a pretty significant lag.

I don't really know where to start looking to diagnose this problem.  If I can get pointed in the right direction (or directions), I would really appreciate it.

I'm running Hardy 8.04 with kernel 2.6.24-21-rt on a Acer Travelmate 4010 with a 1.60 GHz Pentium M processor.

Thanks!

1.6 GHz isn't much, are you sure its not simply your system isn't fast enough to run Ubuntu at full speed?
Check the specs of your system with the recomended specs of Ubuntu.

---

### Post by skymera on 2008-10-30
I'm pretty sure it's fast enough. I've run Ubuntu on 256MB RAM and 800MHz AMD.

---

### Post by hyper_ch on 2008-10-30
open a terminal, install htop and let htop run all the time... if it gets sluggy, have a look at how the processes are being handled.

---

### Post by Monona on 2008-11-03
Xubuntu sounds like it's worth trying, but I'm having some trouble with it:

I installed xubuntu-desktop, and my login screen is now Xubuntu.  However, when I try to choose Xfce under "Select session" and then log in, it seems that I'm still in the default GNOME desktop.

How do I choose Xubuntu or make it my default?  Should I just try a clean install, and how can I save my "home" folder and all my settings/bookmarks/etc. if I choose to do a clean install?

Thanks!

---

