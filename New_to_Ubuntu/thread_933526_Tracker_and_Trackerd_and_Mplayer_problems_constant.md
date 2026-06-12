---
title: "Tracker and Trackerd and Mplayer problems constantly running 100% memory and cpu loss"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by Ximal on 2008-09-29
I constantly am noticing a Mplayer popping up in sequence showing 100% or 50% at minimum after using DeVeDe to convert my home video files to dvd iso files... Though Once I kill trackerd and tracker it stops for a minute then comes back... I have to reboot to get it to stop popping up... That is Mplayer...  I kill Process the tracker(d)'s and they stop coming up "period" . So I am wandering what the heck is going on... I've looked to see if mencoder or any other program is still running on my pc through the system monitor but it's not... I've ran my root kit hunter and virus scans to see if they're is anything out of the ordinary.. Though nothing big... 

I also noticed I'm constantly running at 90 to 100% ram use.. I am wandering if there is a terminal command for me to use to clear the ram cache when no program is working except for say ktorrent... and even so when I close it ... It remains at nearly 100% the ram , that is... Anyhow... any solutions.... would be welcome .... Thanks ?

---

### Post by perlluver on 2008-09-29
> **Ximal said:**
> I constantly am noticing a Mplayer popping up in sequence showing 100% or 50% at minimum after using DeVeDe to convert my home video files to dvd iso files... Though Once I kill trackerd and tracker it stops for a minute then comes back... I have to reboot to get it to stop popping up... That is Mplayer...  I kill Process the tracker(d)'s and they stop coming up "period" . So I am wandering what the heck is going on... I've looked to see if mencoder or any other program is still running on my pc through the system monitor but it's not... I've ran my root kit hunter and virus scans to see if they're is anything out of the ordinary.. Though nothing big... 

I also noticed I'm constantly running at 90 to 100% ram use.. I am wandering if there is a terminal command for me to use to clear the ram cache when no program is working except for say ktorrent... and even so when I close it ... It remains at nearly 100% the ram , that is... Anyhow... any solutions.... would be welcome .... Thanks ?

To remove tracker, open up System>Preferences>Sessions and look for Tracker, and Trackerd, then remove them.  Also make sure you remove them from running processes which is the next tab under the same place.

---

### Post by Ximal on 2008-09-29
is there a way to get my ram cleared out though ?

---

### Post by treepolitik on 2008-12-22
In a moderately similar situation to Ximal's, my computer at some points overloads so much that any input from keyboard or mouse is incredibly difficult or nonexistent.  Which means I cannot even open the System Monitor to find the culprit.  Could it be because **I have no swap space**?   Or is it Firefox(I've had bad experiences with memory skyrocketing on browsers left open for a while).  Also the Add/Remove Applications seems incredibly slow...I generally cannot open anything else while that thing is running.  

I did an interesting experiment by leaving half the desktop to System Monitor...
I looked at the System Monitor after an unplug and a reboot, and the most active program appears to be Xorg, which looks like it's the main internet security program, if I am correct.  I had previously suspected a Denial of Service attack, because I got my updates late and there might already be stuff on my computer despite that nothing new is getting in.

Music Player has a mind of its own and starts when the computer starts.  So I opened Administration>System Monitor>Processes, closed Music Player, and found that its process name is rhythmbox.  Then I went to Preferences>Sessions>Current Sessions to make sure that it's not running in the background as something else.  I would also argue that Preferences>Sessions>Session Options>Remember Currently Running Applications is a viable alternative to hibernation, and might keep annoying programs from opening on their own after you close them. 

What is nautilus? and metacity?  They just seem to pop out of nowhere.  Tomboy uses around 80% CPU when starting, and occasionally up to 30% when sleeping.

gnome-app-inst(Add/Remove Programs) and dpkg(the corresponding Bash worker) are uninterruptible when working.    Sudo(root), also uninterruptible, uses up to 80% CPU or so at one point during the addition of new programs with gnome-app-inst.  That explains why I lose control of my mouse.  Note that gnome-app-insta uses up to about 30% CPU if you leave "All" on the left and don't select a subcategory.  

Now, I add Firefox to the mix.  Firefox climbs to an uninterruptible 60% CPU while it starts.  

In the meantime, I open Terminal, which appears to use 0 CPU when sleeping most of the time.

When I attempt to install a package with gdebi-gtk(Package Installer), it turns out to be the straw that breaks the camel's back.  Everything freezes up, including System Monitor's numbers.  Nearly 100% CPU usage is showing by simply observing the "thinking light"(HDD).
------------------------------------------------------------------------
Is there a set maximum CPU usage for each individual program, so that we can figure out which programs we can have open at the same time?  I'll be searching the repositories for a program that can warn me *before* opening a program, that the memory will go too high.

When I had Windows, I had Ctrl-Alt-Delete to at least see what was using all of the CPU, and I love Force Quit when I can use the mouse.  
As Ximal might be wondering, does Linux have a key combo that has ultimate priority over any other system process that halts and prevents all CPU activity until revealing the culprit?  

Ideally, I would like to also be able to read in text whatever the computer is doing, in the corner of my screen, regardless of the type of code the computer is reading.

---

