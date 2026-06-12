---
title: "Windows V.S Ubuntu in RAM Usage"
date: 2009-02-04
forum: Other OS Talk
---

### Post by izizzle on 2009-02-04
Ok, so. I came BACK to linux after about a year with windows, and I got it to run pretty smooth. With only the startup programs I needed, XP was taking up about 300MB of RAM. I was wondering,  How does this compare to Ubuntu with beryl and kiba-dock on, plus a few exta startup apps? About how much RAM would Ubuntu take? 

P.S: I couldn't find any RAM comparisons on the net.

---

### Post by OrangeCrate on 2009-02-04
A direct comparison will be difficult to impossible, I would guess. Regardless of what you have installed, Linux is going to try to use all of your RAM. Here's a good read:

**Linux Memory Management or 'Why is there no free RAM?'**

> Traditional Unix tools like 'top' often report a surprisingly small amount of free memory after a system has been running for a while. For instance, after about 3 hours of uptime, the machine I'm writing this on reports under 60 MB of free memory, even though I have 512 MB of RAM on the system. Where does it all go?

[http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf)

---

### Post by thundermonty on 2009-02-04
well, bare bones ubuntu is like 100mb but with beryl and a dock it can be up to 250mb. once you start something like firefox though then it would go up.

---

### Post by izizzle on 2009-02-04
Thats pretty good. I am on XP right now and have 310MB in use with google chrome as the only program open.

---

### Post by agim on 2009-02-04
I don't use top, I generally use the gui tools or conky.

My startup ram with kde 4.2, with effects on, konq preloaded and 5 widgets is 320 MB RAM. A clean install of gnome uses 220 MB RAM, and Xubuntu uses around 180 MB ram.

I have 1GB system. With a dual core 1.4 ghz cpu.

---

### Post by -grubby on 2009-02-04
As I type this XP is using about 84 MB (well, if you add the cache to available RAM). I'm running Opera, Pidgin, and Irssi. 

I'd say that Ubuntu with wmii uses about 100 MB running the same apps.

---

### Post by cardinals_fan on 2009-02-04
My SliTaz + dwm desktop uses 32 MB for the blank desktop.  With Firefox (10 tabs), cplay, conky, and GQView open, it's using ~140 MB.

Ubuntu uses a bit more.  I found XP comparable.

---

### Post by jrusso2 on 2009-02-04
Linux uses less memory.  I need a gig to run Vista and two gigs to run it well.  I need 512 mb on the same pc to run Ubuntu with KDE.  And a gig or ram runs it real well.

---

### Post by izizzle on 2009-02-04
How did you get XP to run at 84MB with all those apps on?! Mine runs at 380 with only Google Chrome, and I have modified everything in msconfig.

---

### Post by cardinals_fan on 2009-02-04
> **izizzle said:**
> How did you get XP to run at 84MB with all those apps on?! Mine runs at 380 with only Google Chrome, and I have modified everything in msconfig.
What processes do you have running?

---

### Post by izizzle on 2009-02-04
See the attatchment.

---

### Post by cardinals_fan on 2009-02-04
If you're running Classic anyway, why not disable themes?

Consider a signature-based antivirus (or none at all) - ThreatFire is an option.

---

### Post by Meow27 on 2009-02-04
windows XP naked (no service pack) runs ~50 mb ram without any extra process >.>

---

### Post by pmicheal on 2009-02-04
When I installed ubuntu on my system I got more sleep time of PC. My PC sleep due to load. On Windows XP all things work smoothly. But I don't know why I got this problem.

[Linux Archive]("http://www.linux-archive.org/")

---

### Post by izizzle on 2009-02-04
Isn't classic a theme? I was afraid that if I disable themes, I would end up without a GUI. Is it ok to disable themes if I am running classic?

---

### Post by cardinals_fan on 2009-02-04
> **izizzle said:**
> Isn't classic a theme? I was afraid that if I disable themes, I would end up without a GUI. Is it ok to disable themes if I am running classic?
Classic is a theme.  You don't need themes for a GUI.

---

### Post by izizzle on 2009-02-05
OK, I turned it and a couple other off and uninstalled my antivirus. Now, with chrome open, I have 280MB in use....

Not having an antivirus is just too dangerous. Do you recommend any that are VERY low on mem usage?

---

### Post by Koori23 on 2009-02-05
> **izizzle said:**
> OK, I turned it and a couple other off and uninstalled my antivirus. Now, with chrome open, I have 280MB in use....

Not having an antivirus is just too dangerous. Do you recommend any that are VERY low on mem usage?

To answer your Antivirus question. I LOVE NOD32 by Eset for Windows. Unfortunately, it's 30 USD a year or so.

One thing you have to watch for when reporting RAM usages in XP vs Ubuntu.. Ubuntu will report any onboard video card RAM. XP won't. At least, that's what I noticed when installing Intrepid on my Desktop vs installing Intrepid on my laptop.

I'm curious what MSCONFIG would report for your system. You probably have AdobeReader crap running, OfficeStartup and a lot of other useless crap running in the background that won't put an icon in the system tray.



If you're going to turn off AntiVirus in XP, at least run as a "limited account" and don't use Internet Explorer, wait I have more suggestions:

Get rid of "File and Print Sharing for Windows, QOS Packet Scheduler, disable NETBOIS over TCPIP . If you share files and stuff, obviously that won't work anymore. I've uninstalled all of those things on any XP box I've ever had and didn't have one adverse effect. I was ONLY using my XP box for MS Office, Websurfing, email.. etc. I wasn't doing anything hardcore on it.

---

### Post by izizzle on 2009-02-05
I have all the crap turned off. I've been working too long with XP to now/not know what to turn off :)

Thanks though!

---

### Post by cardinals_fan on 2009-02-05
> **izizzle said:**
> 
Not having an antivirus is just too dangerous. Do you recommend any that are VERY low on mem usage?
I disagree, but ThreatFire is good.  Not that light, but very useful and not too heavy either.

---

### Post by jrusso2 on 2009-02-05
> **izizzle said:**
> How did you get XP to run at 84MB with all those apps on?! Mine runs at 380 with only Google Chrome, and I have modified everything in msconfig.

It would be difficult and take some major surgery to do it but i have seen
people run XP on a i386 with like 8 mb of ram on the web.

---

### Post by jrusso2 on 2009-02-05
> **cardinals_fan said:**
> Classic is a theme.  You don't need themes for a GUI.

Classic is the stripped down Windows 2000 looking XP theme.

---

### Post by izizzle on 2009-02-05
Thats just crazy...out of my reach....Iv'e used Threatfire before, it was O.K....

---

### Post by Koori23 on 2009-02-05
> **jrusso2 said:**
> It would be difficult and take some major surgery to do it but i have seen
people run XP on a i386 with like 8 mb of ram on the web.


I would think just the NT Kernel loaded into memory would require more than 8 meg. 

XPlite might be what you're looking for. You would have to reinstall Windows I guess. From what I've read, you can run an XP system without IE installed at all.

Anyone had any experience with this configuration? I would think you'd have a memory advantage somehow if you pick and choose.

---

### Post by wolfen69 on 2009-02-06
> **OrangeCrate said:**
> A direct comparison will be difficult to impossible, I would guess. Regardless of what you have installed, Linux is going to try to use all of your RAM. Here's a good read:

**Linux Memory Management or 'Why is there no free RAM?'**



[http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf)

if you are talking about machines with less than 512ram, then yeah, it could be a problem. but most computers in the last year or 2 come with at least 1gb. with multiple apps open, (firefox,bittorrent,tv tuner,cd burning) i only use about 400mb. that's not too bad. if memory is an issue, there are many lightweight distros to choose from.

---

### Post by Rokurosv on 2009-02-06
I'd say the Ubuntu default install uses almost the same amount of RAM as my XP installation, about 180-210MB. Disabling a few stuff in Ubuntu can lower that number I guess.

---

### Post by izizzle on 2009-02-07
Yeah probably. But I have 1GB of RAM, and am looking to upgrade to 2GB, so I think I'm set.

Like I said before, I was just wondering...

---

### Post by OrangeCrate on 2009-02-07
> **wolfen69 said:**
> if you are talking about machines with less than 512ram, then yeah, it could be a problem. but most computers in the last year or 2 come with at least 1gb. with multiple apps open, (firefox,bittorrent,tv tuner,cd burning) i only use about 400mb. that's not too bad. if memory is an issue, there are many lightweight distros to choose from.

How Linux manages memory, has nothing to do with 512 meg or 1 gig of RAM, it has to do with how memory is allocated in disk cache and disk buffer.

You should probably read the link I provided. Also, here's just one of the bazillion threads on the forums, discussing the same issue:

[http://ubuntuforums.org/showthread.php?t=404567](http://ubuntuforums.org/showthread.php?t=404567)

Edit:

And, here's another explanation, that's maybe a bit simpler to understand than the Gentoo thread:

[http://knowledgelayer.softlayer.com/questions/205/Linux+Memory+Management](http://knowledgelayer.softlayer.com/questions/205/Linux+Memory+Management)

---

