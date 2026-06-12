---
title: "KDE can't recognize display"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by tuatha1337 on 2008-10-06
Hey folks, I looked for a thread like this, but to no avail.

So here's my issue, I've just installed Kubuntu 8.04 on my machine again (somehow I keep breaking it, also, it's been a while since I've been able to connect my Linux machine to the net). However, both before and after reinstalling in on a particular hard drive (Western Digital 150GB 10000RPM SATA 1.5) The GUI won't start at all. In the command line I've run the startkde command, but it returns several errors indicating that it is unable to open, find, connect to, or contact the display, and stats that $DISPLAY is not set. Keep in mind I'm completely restricted to the command line at this point. Anyone up for the project of helping me figure this out? Maybe something's wrong with my hardware...

---

### Post by tuatha1337 on 2008-10-07
bump

---

### Post by tuatha1337 on 2008-10-09
Someone out there has to know something =)

---

### Post by PierreDeKat on 2008-10-09
I've got a few things that you might want to look at, for starters:

1) What's your video card/adapter setup? 
     A) Is your video card more or less supported by Kubuntu, to the extent that it will work with Kubuntu? 
     B) Do you have a card and onboard adapters competing? See #2

2) What's your BIOS setup looking like? 
     A) If you have a video card and onboard display adapter, you might need to disable the onboard adapter.
     B) Have you got a master and slave setup for two different hard drives? And did you set the jumpers correctly for master and slave?

3) Assuming everything above is okay, I would start to suspect your latest installation.
     A) Did you do anything problematic with your partitioning?
     B) Did the installation crash?

---

### Post by tuatha1337 on 2008-10-10
Yay, a response. K, so:
1) I'm using onboard graphics on an ECS P4M800PRO-M motherboard. (See: VIA VT8237)
  A) I am positive this setup works under Kubuntu, as I have a previous version of Kubuntu installed on another hard drive on this setup.
  B) Nope. The onboard graphics is the only one operating.
2) BIOS is American Megatrends v02.59. Best that I can tell, everything checks out there.
  A) Hmm, can't seem to find any such options for tinkering with the video, graphics, or display. But I did find a toggle for "OnBoard SATA-IDE" with options Disabled, IDE, and RAID. Current setting is on IDE. See B).
  B) This question does indeed pique my interest. As I had problems a short bit ago with something along these lines. Here's the story behind that. I have 2 HDDs and an ODD in my machine. However, the ODD and one of the HDDs are ATA/IDE drives, and the other HDD is a Raptor drive on SATA. Oddly enough, I had recently taken apart my computer to clean it and when I put it back together I had accidentally gotten the master and slave connectors on the cable backwards (making the HDD the slave), so the computer recognized the IDE HDD as having bad sectors and recommended it should be replaced. After reversing the cables, the problem was miraculously fixed. Seeing as how I'm trying to boot from my SATA, could this be the problem? (I'll check after I post this)

3)
  A) Partitioning shouldn't have produced any problems, I reformatted the entire drive for it.
  B) Best I can tell the installation went swimmingly.

[EDIT: I toggled the option in 2A and it made it so that the SATA drive was completely unrecognized.]
[EDIT: I checked the installation CD for errors and found none, also, I can get the CD to run the demo perfectly.]

---

### Post by tuatha1337 on 2008-10-10
I return. I double checked all the connections and the computer recognizes the SATA drive as the 3rd master. The only way to change this is to deactivate all support for IDE in the BIOS. On start-up I get the following text after I get the Kubuntu loader screen:
```

Starting K Display Manager: kdm.
 * Starting Avahi mDNS/DNS-SD Daemon avahi-daemon   [ OK ]
 * Starting Common Unix Printing System: cupsd      [ OK ]
 * Starting powernowd...                            
 * CPU frequency scailing not supported...          [ OK ]
 * Starting DHCP D-Bus daemon dhcdbd                [ OK ]
 * Starting Hardware abstraction layer hald         [ OK ]
 * Starting bluetooth                               [ OK ]
 * Starting anac(h)ronistic cron anacron            [ OK ]
 * Starting deferred execution schedule atd         [ OK ]
 * Starting periodic command scheduler crond        [ OK ]
 * Checking battery state...                        [ OK ]
 * Running local boot scripts (/etc/rc.local)       [ OK ]
_

```

From here I can Ctrl-Alt-F# to the standard terminal login screen.

---

### Post by tuatha1337 on 2008-10-13
bump

---

### Post by tuatha1337 on 2008-10-14
Still needing help if anyone's up for it...

---

### Post by tuatha1337 on 2008-10-17
deleted

---

### Post by tuatha1337 on 2008-11-08
Gah! I can't leave it alone... Bump....

---

