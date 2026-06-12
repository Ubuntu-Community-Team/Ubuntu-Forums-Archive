---
title: "thanks for the help"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by noobie_1 on 2008-11-15
as my username suggests,i'm _very_new to the world if Linux;a friend in another forum suggested using Ubuntu in the form if a double-boot system,as i was ranting about issues with winXP SP3 install. (go figure)

i have the 8.04 version installed on an old win98 box that was given to me because it was,well,messed up pretty bad.

this box barely meets any specs i've seen here,or elsewhere,but it works,albeit slowly. specs for this box are as follows:

400MHZ intel CPU,256MG of RAM,20GB hdd,with a 66-100 MHZ front side bus. the remaining hardware isn't anywhere close to current,either.but no issues with the Ubuntu install on any of the hardware that i can find.

the BIOS does fail one spec,as it's dated 1999, & from what Ubuntu tells me,the cutoff is Y2K. there is an error msg stating this,telling me acpi = force is required to enable ACPI. is this a big issue?

i'm not really worried,as this old pc is just a testbed for me to get used to Ubuntu & for my eventual dual-boot using my newer & much faster box. (but if anyone has any speed tweaks,i'm listening!):)

this old one also won't completely shut off;i've tried logging off,then shutdown,but the thing just sits there with the Ubuntu start-up screen still showing (not the wallpaper),& the pc still running.i just push the power button until it does shutdown.

i've been here several times to get help before deciding to join, & have not been disappointed with the results i've seen.

my eventual dual-boot will involve another hdd,as i'm not partitioning up my current internal,or my USB external for this.

any suggestions on this short of disconnecting my current win hdd's,which i did already read about would be helpful.

my knowledge of pc's isn't extensive,but i'm not exactly a complete noob,except for Ubuntu,so my hand will need to be held regarding any tricks suggested for it.

thanks again for a very informative forum!:grin:

---

### Post by zmike1 on 2008-11-15
For what it's worth, I have a fairly similar system, though I think it had a 450 Mhz cpu and it was painfully slow with ubuntu.  it ran xubuntu pretty well but I had to load it using "manual" methods.  Not terribly hard if you have some experience.  BIOS was pre 1999  -- no problem.  It always did that thing you mentioned about "forcing" something.. no issues.  
I finally stopped using it since there were just too many shortcomings for some of the programs I wanted to run.  
Have fun with it.

---

### Post by noobie_1 on 2008-11-15
hi zmike1;i actually did put Xbuntu on it,but found Ubuntu to run just as fast,if not slightly faster,than the X version does on that box. i redid that just to see what would happen using Ubuntu.

i tried X for the same reason;slow,outdated system.

i like what i see;if it runs faster(and it should be MUCH faster)on my newer box,i'll be one happy camper!

---

### Post by mbsullivan on 2008-11-16
> 
the BIOS does fail one spec,as it's dated 1999, & from what Ubuntu tells me,the cutoff is Y2K. there is an error msg stating this,telling me acpi = force is required to enable ACPI. is this a big issue?

This probably won't be too much of a problem for you. Basically, it just means that your computer will be using the old Advanced Power Management (APM) instead of ACPI for things like hibernate and suspend-to-disk. 

ACPI's generally a bigger deal for laptops, which often have other features (fan/battery control, special keys for audio, etc) that people like to interface with. I'm not sure if you use hibernate or suspend-to-disk, but if you have problems getting them to work it should be possible to force ACPI by making changes to your /boot/grub/menu.lst file. I'll post more about this if you're interested, but I don't think it's worth worrying about.

> 400MHZ intel CPU,256MG of RAM,20GB hdd,with a 66-100 MHZ front side bus. the remaining hardware isn't anywhere close to current,either.but no issues with the Ubuntu install on any of the hardware that i can find.

The RAM is going to be what destroys your performance with regular Ubuntu, probably. If you want to save memory, you could always install a lightweight window manager on your old machine, so that you save memory but can keep using Nautilus and all of the GNOME apps that come with Ubuntu.

Mike

---

### Post by SunnyRabbiera on 2008-11-16
well if its one thing that linux offers over windows and OSX is community.

---

### Post by boblemur on 2008-11-16
yeh the ACPI thing is no big deal...

if you are looking for something really speady, but a lil more tricky to setup, you can go with... ubuntu minimal ([https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD))

install the command line only version... and then run (after you enable to repos)

```
sudo apt-get install xorg slim openbox obconf obmenu openbox-themes
```

this is the system i run :) uses 64mb of ram when sitting with nothing open...

to make it shut down... go into terminal and try
```
shutdown -h -P now
```

and if that dosent work try without the -h


:) the forums are great arnt they.... and were always here to help :P

---

