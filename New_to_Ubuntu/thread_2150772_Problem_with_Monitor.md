---
title: "Problem with Monitor"
date: 2013-06-02
forum: New to Ubuntu
---

### Post by mikep6321 on 2013-06-02
I have picked up some type of virus which has changed the way I am able to view the pixels of my monitors. I run the 64bit Ubuntu 12.1. I have tried every resolution setting combination on 4 different monitors from a 32 inch (which worked just fine prior to this problem) to this tiny 17 inch monitor. The look of the monitors is very fuzzy and makes it seem like you are wearing a pair of glasses prescribed for someone else. It is very nauseating. I believe it was from downloading free art but could be from web browsing or maybe inspecting elements of how other have set up websites. I have more than 20 sites I have built or am in the process of building of which I am handling.

After 5 days of trying to solve this problem I suspect that it has something to do with the video card input (maybe).

One of the monitors said you do not have the correct graphic or video input (or something like that) to run this monitor. I have a brand new computer t-seris Azrock motherboard with 32 gig DDR3 ram, with AMD A4-3400 APU with Radeon(tm) HD Graphics × 2 processor, 2 gig sparkle PCIe 2 video card and 2 terra byte hard drive with 650 power supply. So it has plenty of computer to do what is needed. I have tried every setting combined with every setting on every monitor. I have tried HDMI connection and VGA connection with all of the computers and all of the monitors on my network.

I worked with CenturyLink for over an hour ( finally got someone in the U.S. after being routed through the Phillippines for more than an hour) and I have worked with the guy who build the computer for over 3 hours to solve this problem to no avail. 

My monitor worked great for over 3 months then one day all 3 computers in my office went to this odd and very problematic pixelated look 5 days ago. It is like being seasick using this computer.

It has affected every monitor on my network including my older XP Pro system. 

By the way I really like Unbutu. I very much rely on my computer to make a living so I need to fix  this problem.

One thing to note is it always says "graphics- unknown".

Mike Peterson

---

### Post by newb85 on 2013-06-02
So...wait...what kind of virus could you have picked up that would have affected both 12.10 and XP systems?

Is this a problem all the time, or just when you're viewing websites?

Where does it say "graphics- unknown"?

---

### Post by Mark Phelps on 2013-06-02
That "graphics unknown" is a well-known bug with System Info -- so you can ignore it.  IF the system didn't recognize your graphics card and/or monitor, you would be seeing a blank, black screen, not a desktop.

Bad graphics on one PC, when seen both in Linux and in Windows, is often an indication of a bad card -- even though this is new, it could still be bad.

Fuzzy graphics can be simply the use of the wrong refresh rate.

I can't conceive of a "virus" that would cause this kind of problem -- especially one that affects both Linux and MS Windows.

You're saying EVERY monitor on EVERY PC is doing this? OR, only every monitor you hook up to THIS PC?

---

### Post by newb85 on 2013-06-02
Is it possible this problem is caused by an inconsistency in the power coming in?  (If, for example, it's not the 60 or 50 Hz it's supposed to be...)

---

### Post by mikep6321 on 2013-06-05
How would I know how many Hz are coming into my system and how do you change that if it were the case. And why would it effect every monitor in  the office. I thought maybe it might have something to do with the router but I was on the phone with the Centurylink IT guys for over an hour. They checked the gigs coming into the box 20 gigs of download speed. We tried every place in the XP to change the monitor settings to no avail. 

I have switched all monitors and all settings in each computer and by running hitman, essentials, auslogic and none were of any help. I have tried restoring the XP to a earlier setting 3 times again to no avail. In the ubuntu I have tried all settings in display, appearance, brightness, and color. Nothing has worked it still looks as though I am looking through someones prescription glasses. And I can only look at this for less than a few minutes.

These are the things that I have not ruled out. The power supply (but why all power supplies in all computers?), something that has effected the way the video cards tells the sytem how to display the  dots on the monitors, the router (although the problem occurs even when the router is off and unplugged).

Things that I have ruler out: settings (I have tried for 6 days and have reset every possible setting in all 4 computers with all 5 monitors), the power to the computers ( I have tried the computers in other rooms and I have put a voltage meter on each outlets. The outlets are fine and the voltage is where I would expect it to be.)

I am still having the problem. Cannot wok on the computers. My next step is to remove all operating sytems sytems try to save files I believe are not contaminated and reinstall all programs. Seems like a lot of work but what is my oprions.

Mikep

---

### Post by mikep6321 on 2013-06-05
How do I know what is the right refresh rate? Where do I find the refresh rate? How does the refresh rate get changed on all computers?

---

### Post by mikep6321 on 2013-06-05
Yes every computer (2 computers with ubuntu 12.1 and 2 computers with XP).

---

### Post by newb85 on 2013-06-05
I don't know much about how monitors work, but I would imagine the actual refresh rate is affected by the cycles per second of the power in your office.

---

### Post by Zill on 2013-06-05
> **mikep6321 said:**
> ...My next step is to remove all operating sytems sytems try to save files I believe are not contaminated and reinstall all programs...
Not necessarily the case. ;-)

Simply insert the Ubuntu DVD you originally used to install Ubuntu 12.10 and then reboot and select the "Try Ubuntu without installing" option.  This will run Ubuntu as a "live" DVD without changing your HDD at all and will be using a "default" installation.  See if the graphics look any better then.  You may like to run the same live DVD on all the PCs you have that exhibit this problem (just make sure the BIOS boot-order is set to boot from the CD/DVD drive *first*).  If you post back here with the results it may help us establish exactly what is going on.

ps.  Welcome to Ubuntu forums and please appreciate that everyone here is just another user voluntarily offering help - that is how Linux support works. ;-)

---

### Post by mikep6321 on 2013-06-05
I will reboot from DVD. Then let you know.
Mikep

---

### Post by Mark Phelps on 2013-06-05
> **mikep6321 said:**
> How do I know what is the right refresh rate? You don't, by default.  The refresh rate is a factor in the clarity of the display and changes based on the resolution.  In general, flat panels today tend to use a refresh rate of 60Hz (meaning, the display refreshes 60 time-per-second). But, newer displays are coming out all the time and recently, I saw one mentioned that uses a refresh rate of 200Hz.

>  Where do I find the refresh rate? 
For (1) the monitor, or (2) the OS running on the PC?

Every monitor has a limited set of refresh rates it can support.  This is generally contained in any documentation that comes with the monitor.  IF the monitor also has an OSD (On Screen Display), it will have menus for changing refresh rates -- and it will not allow you to set a refresh rate it not support.

The OSs, both MS Windows and Linux distros, have apps that allow you to set both screen resolution and refresh rates. In recent Ubuntu versions, this is the Display app which is found using the Dash.  By default, the Ubuntu panel only displays resolutions and refresh rate combinations that the video drivers AND the monitor support.

> How does the refresh rate get changed on all computers?
This is just guesswork on my part because it can happen any number of ways.  Someone could access the OSDs for all the monitors and change the refresh rates.  Someone could access the screen apps for all the OSs and change the resolutions and refresh rates.

If you're asking how does it happen without human intervention, it does not.  Monitors don't just change their display settings, nor do PCs.  Someone has to intervene to make this happen.  

But ... it can happen easily if someone is messing around with driver updates and/or OS updates/upgrades.

---

### Post by mikep6321 on 2013-06-21
Still a problem. But I did have a notice box that came up. It said "your comuter is running on low resolution mode". It gave me three choices one of which one was to run in this mode for one session only and another was to change the mode to the preset  mode. I said fix the problem now and hit next. Unfortunately nothing happened. Now my question is where is the resolution mode at in the file sytem and once I find it how do I change the resolution.

PS I have tried every setting combination in the system settings and every monitor setting in the monitor setup.

Mikep

---

### Post by Zill on 2013-06-21
I am still puzzled by your original statement:
> **mikep6321 said:**
> ...My monitor worked great for over 3 months then one day all 3 computers in my office went to this odd and very problematic pixelated look 5 days ago. It is like being seasick using this computer.

It has affected every monitor on my network including my older XP Pro system...
While it is *possible* that all your Ubuntu installations on multiple PCs could show similar problems *if* they were all installed from a *single* DVD that has corrupted data on it, this *cannot* have any effect on your XP installations unless you are running Wubi.  So, please clarify the following:

[LIST=1]
[*]Did you originally install Ubuntu on multiple PCs using the *same* 12.10 DVD?
[*]Did you originally install Ubuntu on a *different* partition to XP (i.e. not as a Wubu install)?
[/LIST]
> **mikep6321 said:**
> Still a problem...
I presume you are referring to running your Live DVD (12.10) with the "Try Ubuntu without installing" option?  If this is the case then do you get the same problem with only *one* or *all* the PCs?  If only one PC/monitor has the problem then we should concentrate on resolving this.  If the problem is seen on multiple PC/monitors then it seems your Ubuntu DVD is corrupted and you should download it again and burn a new DVD.  Make sure the [MD5sum]("https://help.ubuntu.com/community/HowToMD5SUM") is correct to verify a good download.
> **mikep6321 said:**
> PS I have tried every setting combination in the system settings and every monitor setting in the monitor setup.
I suggest you reset the monitor(s) to default settings and then leave the controls alone.  Ubuntu should normally work with monitors straight out-of-the-box.

---

