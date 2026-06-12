---
title: "vostro/gutsy sound problems"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by pmura1 on 2008-05-01
Hello, I just got a brand new Dell Vostro1500 laptop.  The first thing that I did (after downloading avast for XP) was to Dual boot with Ubuntu 7.10.  I downloaded from a DVD in LINUX FORMAT magazine That seemed to go smoothly enough, but there are a few problems that need to be taken care of.  

I'll address them one at a time so the first is that there is no sound.  It is ok when I run windows but nothing when I run Ubuntu.  At Systems> Preferences> Sound> Devices **there is nothing at the Default Mixer Tracks slot**.  When I click there, there is a Bar that goes through the slot.

I also get a message box that says *"Unable to start the settings manager 'gnome-settings-daemon'. ...This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager."*  I have no idea what this means or how to fix it, please help.

Thank you

---

### Post by dicecca112 on 2008-05-01
> **pmura1 said:**
> Hello, I just got a brand new Dell Vostro1500 laptop.  The first thing that I did (after downloading avast for XP) was to Dual boot with Ubuntu 7.10.  I downloaded from a DVD in LINUX FORMAT magazine That seemed to go smoothly enough, but there are a few problems that need to be taken care of.  

I'll address them one at a time so the first is that there is no sound.  It is ok when I run windows but nothing when I run Ubuntu.  At Systems> Preferences> Sound> Devices **there is nothing at the Default Mixer Tracks slot**.  When I click there, there is a Bar that goes through the slot.

I also get a message box that says *"Unable to start the settings manager 'gnome-settings-daemon'. ...This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager."*  I have no idea what this means or how to fix it, please help.

Thank you

Do you have no sound at all?

If you don't try sudo apt-get install  linux-backports-modules-2.6.22-14-generic

and then restart

other issue read here [http://ubuntuforums.org/showthread.php?t=579167](http://ubuntuforums.org/showthread.php?t=579167)

---

### Post by pmura1 on 2008-05-01
Do you have no sound at all?

If you don't try sudo apt-get install linux-backports-modules-2.6.22-14-generic

and then restart

other issue read here [http://ubuntuforums.org/showthread.php?t=579167](http://ubuntuforums.org/showthread.php?t=579167)


Dicecca112, Thank you.  I'll try it.  But, sorry, I am really new to this... what do I need to do to get to the place that I can enter that?  

I have no sound at all... not even the click of the mouse or keypad.

---

### Post by dicecca112 on 2008-05-01
> **pmura1 said:**
> Do you have no sound at all?

If you don't try sudo apt-get install linux-backports-modules-2.6.22-14-generic

and then restart

other issue read here [http://ubuntuforums.org/showthread.php?t=579167](http://ubuntuforums.org/showthread.php?t=579167)


Dicecca112, Thank you.  I'll try it.  But, sorry, I am really new to this... what do I need to do to get to the place that I can enter that?  

I have no sound at all... not even the click of the mouse or keypad.

applications -> accessories -> terminal

type that in

enter your password

it'll download and install that

reboot

---

### Post by 85fb on 2008-05-01
I did that same thing. entered into terminal but it says couldnt find package lunux-backports-modules-2.6.22-14-generic

stumped. again.

---

### Post by dicecca112 on 2008-05-01
> **85fb said:**
> I did that same thing. entered into terminal but it says couldnt find package lunux-backports-modules-2.6.22-14-generic

stumped. again.

typo on my part linux-backports-modules-2.6.22-14-generic

---

### Post by pmura1 on 2008-05-04
Hello, Sorry Dicecca12... I was away from my computer for a few days.  I tried your suggestion above and it said that it** couldn't find the package**.  

In fact, I tried to get **module-assistant** and I get a message that says that it couldn't find that either.

I also tried **update assistan**t and it said that my system is up-to-date.

I'm having a bunch of problems with 7.10.  **should I try an upgrade to 8.04**?
Could it be that the disc I installed from is faulty?


Another thing that I noticed was that the speaker icon in the toolbar at upper right has an "x" on it.  When clicking it it says "No volume control GStreamer plugins and/or devices  found."  I don't know if this a seperate issue, but thought that it might be relevant. 

 Thanks again (to anyone)

---

