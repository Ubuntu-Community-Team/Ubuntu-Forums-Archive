---
title: "HOW TO repair a broken xorg.conf from the command line"
date: 2006-12-17
forum: Outdated Tutorials &amp; Tips
---

### Post by L14UX_1NS1D3 on 2006-12-17
A few days ago I messed around with trying to install glx and ended up leaving me stranded with a command line login. Being the noob that I am I atempted the impossible, to fix my xorg.conf. for this you will need too learn a little command line voodoo. nothing to hard.

commands:
cd: enter a directory 
ls: list the files in a directory
cp: copy files to another directory 
mv: move files to another directory or rename file

-------------------------------------------------------------------

what I did was first enter the directory 

$cd /etc/X11/

than list the files in the directory 

$ls

I renamed the broken xorg.conf to xorg.conf.broken

/etc/X11$ mv xorg.conf xorg.conf.broken

I made a backup of the backup 

sudo cp xorg.conf.backup /home

than made the backup conf file to the default conf by removing the .backup

mv xorg.conf.backup xorg.conf

--------------------------------------------------------------------------
rebooted my box and did a little victory dance :mrgreen:

---

### Post by aysiu on 2006-12-17
This all assumes you actually **made** a backup. But even if you did, you could save yourself some steps here: ```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.broken
sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
``` You don't need to do all that *cd*ing and moving to your /home directory first.

If you don't have a backup copy, you can also do ```
sudo dpkg-reconfigure xserver-xorg
``` to re-create the /etc/X11/xorg.conf file. Presumably, Feisty Fawn will have something called "bulletproof X," which means you'll never be stuck at the command-line unless you want to be.

By the way, I've moved your HowTo to the appropriate section in the forums.

---

### Post by aidanr on 2006-12-17
also "nano /etc/X11/xorg.conf" to edit the file from the command line to reverse any changes you made that borked it

---

### Post by aysiu on 2006-12-17
> **aidanr said:**
> also "nano /etc/X11/xorg.conf" to edit the file from the command line to reverse any changes you made that borked it
Don't you need a *sudo* in there? You can also create a backup copy of the broken one by inserting a *-B* flag in there: ```
sudo nano -B /etc/X11/xorg.conf
```

---

### Post by L14UX_1NS1D3 on 2006-12-23
thanks for the tip I. It'll definitly save me some writing :KS

---

### Post by ivanoats on 2006-12-23
Hi - I am trying to do this but can't get to a command line in ubuntu. I've tried alt-f4 ( actually all the function keys) any tips?

---

### Post by LameBMX on 2006-12-23
> **ivanoats said:**
> Hi - I am trying to do this but can't get to a command line in ubuntu. I've tried alt-f4 ( actually all the function keys) any tips?

if X has initialized you will need to use ctrl - alt - F(1-6)
also if you have a newer keyboard .. check the F Lock

*EDIT*
the terminal on F1 is where X is running at ... so ctrl-alt-F1 ... and you will see a bunch of goobly-gock ... hit ctrl-C to break out of X running (sorry about the n00b language im definately not an expert)

---

### Post by ivanoats on 2006-12-23
Thanks for responding. Unfortunately Ctrl-Alt-F1 (or any other F key) does not work. Any other suggestions?

---

### Post by L14UX_1NS1D3 on 2007-01-29
Hi.
If you want  to just use the command line all you have to do is logout restart and press "ESC"
at boot and you will be given the option to logon with just a terminal or fail-safe terminal and from there you will be able do your repair.

Hope that helps! :wink:

---

