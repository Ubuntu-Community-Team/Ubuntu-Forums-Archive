---
title: "I want to build a nice GUI for editing xorg.conf. Something that has never been done"
date: 2007-05-24
forum: Programming Talk
---

### Post by tanelt on 2007-05-24
For CRT users like me, there has never been a nice GUI program for modifying the vertical and horizontal synchronization ranges, generating and inserting custom modelines and selecting which resolutions to use. I would like to make such a program, so that new Ubuntu users who use CRT monitors wouldn't have to live in agony any more. **Manually editing the xorg.conf file is something that could very quickly and effectively make newbies just dump Linux and move back to Windows where it "just works" and where they don't have to manually edit configuration files just to use a certain resolution for example.** 


The sad thing is that I have absolutely no knowledge about any programming languages, so I'm afraid I'm not the best person to do it. :( But I don't care, I'm willing to learn. =)

There's no such program, and probably never will be, unless someone does something about it. I know most of the developers are thinking something along the lines of *"CRTs will die sooner or later and eventually everyone has an LCD monitor, so lets just show the CRT users the middle finger and lets continue perfecting the support for LCD monitors, because that's an easier task anyway."*

But how many **millions **of people are still using CRTs? Dozens? Hundreds?


So, here's what I would like to accomplish:

[LIST]
[*] A nice clean interface, something like the Ubuntu installer has.
[*] The program must be fairly quick and lightweight, not a resource hog.
[*] Tthe ability to automatically detect the monitor type, vertrefresh, horisync, etc. (if possible) and automatically insert them to xorg.conf.
[*] The ability to automatically generate custom modelines and automatically insert them to xorg.conf.
[*] A list where to select all the resolutions the user wants to use, plus a box to insert custom resolutions into.
[*] **And I repeat -- it all has to be GUI ONLY! NO manual xorg.conf editing required.**
[/LIST]

So, where do I begin? Any recommendations? I don't care how long it takes to create it. I'm happy if there is at least **some kind of progress** in this behalf.

---

### Post by WW on 2007-05-24
Have you seen xorg-edit? [http://ubuntuforums.org/showthread.php?t=156243](http://ubuntuforums.org/showthread.php?t=156243)

---

### Post by Stephen Howard on 2007-05-24
Maybe first have a mess around with these packages, as they seem to do something similar (the first one seems more mature than the gtk program, but I've not tried either): 

> kxgenerator 
displayconfig-gtk

Also, have a look at the debian xorg configuration script.  It should be at /usr/share/bug/xserver-xorg.  It presumably shows how the back end would work.

---

### Post by Seq on 2007-05-24
If you want an all-encompasing configuration tool, you will need to handle things like input devices, the actual graphics card options (beyond the display), etc.

Of note is that Xorg is going to be ditching the need for most of the configuration files. You can still have and use them, but auto detection and hot plug support will be much improved.

---

### Post by pmasiar on 2007-05-24
> **tanelt said:**
> The sad thing is that I have absolutely no knowledge about any programming languages, so I'm afraid I'm not the best person to do it. :( But I don't care, I'm willing to learn. =)

No: YOU are the best person to fix what itches you. That is the whole point of open source: fix your itch, and share with others. And *I* use CTR too, and it is pain, but I learned the magic commandline to fix it... But I support you and like your attitute!

> But how many **millions **of people are still using CRTs? Dozens? Hundreds?

CRT will be used for years to come IMHO. Outside of USA, nobody throws PC when upgrading (or when it has too many viruses - yes don't laugh, it happened).

> So, where do I begin? Any recommendations? I don't care how long it takes to create it. I'm happy if there is at least **some kind of progress** in this behalf.

Python will be best language to do that, see my sig how to start. Learn Python, wxPython for GUI, and off you go! Good luck!

---

### Post by Cappy on 2007-05-24
I would definitely be interested in integrating some kind of interface into System-->Preferences-->Screen Resolution. I think it's stupid that you have to edit the xorg.conf to change the Refresh Rate (actually I had to use the nvidia tool) and any unset screen resolutions. Why doesn't Ubuntu just have a check box that you can check for undetected resolutions. That would make it really easy =-/

---

### Post by tanelt on 2007-05-29
Thanks for the replies!

Hmm, I had no idea about xorg-edit, it looks like they have a great thing going there. I'm going to
learn Python sooner or later, so maybe I'll try to contribute to the xorg-edit project if possible.

---

### Post by xtacocorex on 2007-05-29
I never really understood the need for a GUI based program to edit xorg.conf when you have to restart X anyway to see the results which in turn, ends the program you were running.  Seems counter-productive to me, but then again I'm a senile FORTRAN programmer. 

I'll back pmasair with using Python, it'll be quick and easy to get something up and running, plus is has good support for GTK+.  I have done a code with Python and GTK+ with the GUI developed in Glade and it turned out pretty well.

---

