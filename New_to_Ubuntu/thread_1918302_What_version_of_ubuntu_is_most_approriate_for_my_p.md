---
title: "What version of ubuntu is most approriate for my pc"
date: 2012-01-31
forum: New to Ubuntu
---

### Post by SAIYANPRINCE on 2012-01-31
Hi, I want to install ubuntu onto my pc but I would like to know which version would suit it best. I really am sick of windows and how slow and unreliable it can get so i am really looking forward to change to ubuntu,

My pc has only 504mb ram (i know it sucks but i will be replacing it in the near future.) So I want the lightest possible version, one that is fast and consistent. As for looks, I will just get compiz and see if it runs fine. Right now I'm leaning towards Lubuntu, but if anything is better for me then please suggest. ty

and sorry if this is a dumb question im new here

---

### Post by Rodney9 on 2012-01-31
Lubuntu would be a good choice or Xubuntu


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by RedRat on 2012-01-31
I just found this in a reply to another question:

Low ram = Try [**Peppermint**]("http://www.peppermintos.com/") or

Xubuntu/Lubuntu

You might look into Peppermint, I just checked out its web page and it looks interesting for low RAM machines.

Before installing any of these versions, I would do research about the advantages AND the disadvantages of each of these systems. Your machine has very low memory and it may well be that it is too low, but you can give any of these a shot using the LiveCD.

---

### Post by LinuxFan999 on 2012-01-31
Considering the amount of RAM in your computer, I would recommend Lubuntu 11.10. I have found that Xubuntu 11.10 is extremely sluggish on less than 768 MB of RAM. Xubuntu 10.04 would run on your computer, but it was quite buggy, and is now outdated, so I would not recommend using it.

---

### Post by Kixtosh on 2012-01-31
My "policy" for older hardware with low RAM, that I apply at home and with friends/family/neighbors, is this:

[LIST]
[*]Use LTS (long term support) releases. There is no point in troubleshooting possible problems every six months when a new release comes out, and newer releases tend to want to use the available resources of newer machines more and more. The current LTS of Ubuntu and it's derivatives is Lucid Lynx 10.04.
[*]Use the lightweight desktop environment always, LXDE, not Gnome or Xfce. Lubuntu comes with LXDE by default, but it can be easily added to other versions as well.
[*]Lubuntu, Peppermint and Xubuntu _with LXDE_ are all excellent choices, using very little RAM (100 MB, more or less, but it'll vary somewhat above and below that figure).
[*]Wary Puppy is another excellent choice to try. Start up and shut down times tend to be be slower than the three solutions mentioned above, but sometimes something will work with Puppy "out of the box" that requires additional research and work to get it functional with Lubuntu, Peppermint or Xubuntu.
[*]Anything with more than 512 MB of RAM and a 1 GHz CPU doesn't need a lightweight version, and will not benefit significantly from having one (the benefits in such cases do not outweigh the limitations, in my view).
[/LIST]
All of these solutions tend to start up in under one minute, and shut down in ten seconds, except for Puppy, which is generally a bit slower in my trials. 

They should also run applications reasonably well, but a browser may take up to ten seconds to open up from a cold boot. Subsequent browser sessions will be much faster. Office applications will be similarly sluggish, but there are lightweight solutions for those as well, if compatibility with Microsoft Office documents is not a priority. For applications, Puppy will be as fast or somewhat faster than the others on old machines.

All of these options tend to have good  support for external PCMCIA wireless cards and other external wireless  solutions, since older devices rarely have built-in wireless. All three  of those mentioned worked out of the box with the laptops in my signature, and so did Wary Puppy.

[LIST]
[*]The main advantage of Wary Puppy is that you don't even have to install it. It runs from a CD to load itself into RAM (so the CD can then be removed and the drive made available for normal use). Wary Puppy can also be used in conjunction with a USB drive for saving documents, and then operate as a completely portable operating system, for use on any computer anywhere.
[*]The main advantage of Peppermint is that it uses "pseudo-cloud" links on the desktop of web based applications from Google for documents, spreadsheets etc. It also has a pretty cool looking desktop theme, if you ask me! There is no LTS release of Peppermint, to the best of my knowledge.
[*]The main advantage of Lubuntu is that it's a lightweight LXDE environment that's all ready to go. It has also been extremely active in the past couple of years, so there's a lot of development "energy" being fed into it. There is no LTS release currently, since it wasn't an official distro in April of 2010, but I think an LTS release of Precise Pangolin 12.04 is planned, three months from now. I find the desktop unappealing (but that's a matter of taste).
[*]The main advantage of Xubuntu is that you might prefer using it with Xfce, if it doesn't slow you down too much. You may also prefer the Xubuntu variant of LXDE compared to the Lubuntu variant. Xubuntu Lucid Lynx is also a LTS release. I have not found it "buggy", as LinuxFan999 suggested, but this probably depends on what hardware might be causing it to behave badly.
[/LIST]
[http://www.xubuntu.org/](http://www.xubuntu.org/)
[http://peppermintos.com/](http://peppermintos.com/)
[http://lubuntu.net/](http://lubuntu.net/)
[http://puppylinux.org/main/Long-Term-Supported%20WaryPuppy.htm]("http://puppylinux.org/main/Long-Term-Supported%20WaryPuppy.htm")

---

### Post by SAIYANPRINCE on 2012-01-31
> **Kixtosh said:**
> My "policy" for older hardware with low RAM, that I apply at home and with friends/family/neighbors, is this:

[LIST]
[*]Use LTS (long term support) releases. There is no point in troubleshooting possible problems every six months when a new release comes out, and newer releases tend to want to use the available resources of newer machines more and more. The current LTS of Ubuntu and it's derivatives is Lucid Lynx 10.04.
[*]Use the lightweight desktop environment always, LXDE, not Gnome or Xfce. Lubuntu comes with LXDE by default, but it can be easily added to other versions as well.
[*]Lubuntu, Peppermint and Xubuntu _with LXDE_ are all excellent choices, using very little RAM (100 MB, more or less, but it'll vary somewhat above and below that figure).
[*]Wary Puppy is another excellent choice to try. Start up and shut down times tend to be be slower than the three solutions mentioned above, but sometimes something will work with Puppy "out of the box" that requires additional research and work to get it functional with Lubuntu, Peppermint or Xubuntu.
[*]Anything with more than 512 MB of RAM and a 1 GHz CPU doesn't need a lightweight version, and will not benefit significantly from having one (the benefits in such cases do not outweigh the limitations, in my view).
[/LIST]
All of these solutions tend to start up in under one minute, and shut down in ten seconds, except for Puppy, which is generally a bit slower in my trials. 

They should also run applications reasonably well, but a browser may take up to ten seconds to open up from a cold boot. Subsequent browser sessions will be much faster. Office applications will be similarly sluggish, but there are lightweight solutions for those as well, if compatibility with Microsoft Office documents is not a priority. For applications, Puppy will be as fast or somewhat faster than the others on old machines.

All of these options tend to have good  support for external PCMCIA wireless cards and other external wireless  solutions, since older devices rarely have built-in wireless. All three  of those mentioned worked out of the box with the laptops in my signature, and so did Wary Puppy.

[LIST]
[*]The main advantage of Wary Puppy is that you don't even have to install it. It runs from a CD to load itself into RAM (so the CD can then be removed and the drive made available for normal use). Wary Puppy can also be used in conjunction with a USB drive for saving documents, and then operate as a completely portable operating system, for use on any computer anywhere.
[*]The main advantage of Peppermint is that it uses "pseudo-cloud" links on the desktop of web based applications from Google for documents, spreadsheets etc. It also has a pretty cool looking desktop theme, if you ask me! There is no LTS release of Peppermint, to the best of my knowledge.
[*]The main advantage of Lubuntu is that it's a lightweight LXDE environment that's all ready to go. It has also been extremely active in the past couple of years, so there's a lot of development "energy" being fed into it. There is no LTS release currently, since it wasn't an official distro in April of 2010, but I think an LTS release of Precise Pangolin 12.04 is planned, three months from now. I find the desktop unappealing (but that's a matter of taste).
[*]The main advantage of Xubuntu is that you might prefer using it with Xfce, if it doesn't slow you down too much. You may also prefer the Xubuntu variant of LXDE compared to the Lubuntu variant. Xubuntu Lucid Lynx is also a LTS release. I have not found it "buggy", as LinuxFan999 suggested, but this probably depends on what hardware might be causing it to behave badly.
[/LIST]
[http://www.xubuntu.org/](http://www.xubuntu.org/)
[http://peppermintos.com/](http://peppermintos.com/)
[http://lubuntu.net/](http://lubuntu.net/)
[http://puppylinux.org/main/Long-Term-Supported%20WaryPuppy.htm]("http://puppylinux.org/main/Long-Term-Supported%20WaryPuppy.htm")

Thanks for the info... I think I will go for lubuntu. But I have some more questions if you dont mind. First off you said it uses around 100mb ram. Do you know how much xp uses? Also will compiz work to its full potential? So can i just download any effect and it will run alright? And as for it being ugly you can just download themes and docks and stuff right?

---

### Post by Kixtosh on 2012-02-01
I would think that Lubuntu uses less RAM than W2K. In fact, just to satisfy your curiosity, W2K can be quite a bit slower than Lubuntu when freshly installed, and much slower than Lubuntu after a few months of normal usage, but _significantly faster_ than Lubuntu to open and run slightly older Microsoft Office applications (2000 or XP versions) when compared to OpenOffice or LibreOfice!

XP uses a lot more RAM, and struggles more and more to run after a few months of updates in my experience. Apart from the security issues, this was my main reason for abandoning it in the end. Windows XP is always using virtual memory, frequently to the limits of what has been allocated, whereas Lubuntu will probably make little use of swap memory with 512 MB of RAM available ... at least that is what I have observed. There are plenty of users that will suggest that 2 GB of RAM is the real world minimum for XP. The main difference for me was that W2K or XP both slowed down horribly over time, until the next fresh install became necessary (for whatever reason). Linux does not, and "fresh installs" became a thing of the past. I can stick with a stable, optimized system for two years, until the next LTS release. Then it's "cross your fingers" time again! Fortunately, I can always fall back on Wary Puppy if need be. Now that LTS releases are going to be supported for five years (starting this year) instead of just three in the past, the "comfort window" will be even more comfortable!

As for compiz and changing themes and docks: all of this is possible, in theory, but I don't amuse myself with that stuff on older machines. You may be unlikely to get far with special effects with older video capabilities, in particular, and it might just make everything jittery and uncouth instead of flashy and sophisticated! My priority is usually to keep them running as fast as possible, with as little fuss and troubleshooting as possible (hence the use of LTS releases only, so that the O.S. only changes every two years, not every six months). In practice, though, you can knock yourself out with the Ubuntu Software Center and Synaptic Package Manager ... not to mention Terminal commands ... adding anything that you feel like trying, including themes and docks.

---

### Post by tdawgf on 2012-02-01
> **SAIYANPRINCE said:**
> Thanks for the info... I think I will go for lubuntu. But I have some more questions if you dont mind. First off you said it uses around 100mb ram. Do you know how much xp uses? Also will compiz work to its full potential? So can i just download any effect and it will run alright? And as for it being ugly you can just download themes and docks and stuff right?

XP, technically, i have seen run on a machine with only 128 mb of ram (it claimed low memory after boot, but still operated) but most low end machines with xp back in the day had 256 mb. I think Lubuntu is a good choice. I had it up and running on an old e-machine with a 900 mhz processor and 384ish mb of ram. It didn't have any binary video drivers and couldn't watch youtube or anything. But it was perfect for web browsing, e-mail, and office work, which is what it was being used for. Lubuntu idled at 90mb for me too. I ended up taking it to school for my tech class, and the school asked if they could have it to donate to a local family for a child to use for school. It made my day.

---

### Post by chickenPie4breakfast on 2012-02-01
Is there a guide to changing your desktop -  say if you have gnome but want to change to LXDE?
Also will there be much difference between running Gnome with Compiz turned off (as I have) and LXDE - I have never gone in for fancy graphic effects.

---

### Post by mastablasta on 2012-02-01
> **chickenPie4breakfast said:**
> Is there a guide to changing your desktop - say if you have gnome but want to change to LXDE?
Also will there be much difference between running Gnome with Compiz turned off (as I have) and LXDE - I have never gone in for fancy graphic effects.
 
 
nothing to do with original thread. but yes you can do that. you install LXDE desktop and then you switch to it on login.
why not try out Lubuntu and see if there is any major difference for you?
 
the biggest one is different file manager and the way windows & fonts are drawn. if it doesn't matter to you then...

---

### Post by 3rdalbum on 2012-02-01
Anything preventing you from buying a 1 GiB stick of RAM? Then you could run regular Ubuntu 11.10.

---

### Post by tdawgf on 2012-02-01
> **3rdalbum said:**
> Anything preventing you from buying a 1 GiB stick of RAM? Then you could run regular Ubuntu 11.10.

I am guessing with the amount of ram he has, then he has at the absolute latest ddr2. DDR2 is actually getting fairly expensive now. and I wonder if the motherboard could even support a 1 gig strip.

---

### Post by Kixtosh on 2012-02-01
Yes, that's possible, but even an extra 256 MB of RAM would leave him fairly comfortable for using Ubuntu. He hasn't mentioned the complete specifications of his laptop yet, I don't think.

---

### Post by Kixtosh on 2012-02-01
> **chickenPie4breakfast said:**
> Is there a guide to changing your desktop -  say if you have gnome but want to change to LXDE?
Also will there be much difference between running Gnome with Compiz turned off (as I have) and LXDE - I have never gone in for fancy graphic effects.
I haven't found a guide, but I believe that when I added LXDE to Xubuntu, I simply did the following:

[LIST=1]
[*]Download and install LXDE from the Ubuntu Software Center (see the Applications menu in the top panel).
[*]Log out of Ubuntu/Xubuntu or whatever you're using, but do not shut down.
[*]Choose the newly installed LXDE desktop from the login screen options and log in normally.
[/LIST]
That should do it, I think. If your machine normally boots straight to the desktop, it should continue to do so, but with LXDE instead of whatever you had, unless you reverse the steps above.

---

### Post by Cheesemill on 2012-02-01
> **chickenPie4breakfast said:**
> Is there a guide to changing your desktop -  say if you have gnome but want to change to LXDE?

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

Look at the articles under the subtitle 'Playing Around' about 1 page down on the left hand side.

---

### Post by SAIYANPRINCE on 2012-02-01
> **tdawgf said:**
> I am guessing with the amount of ram he has, then he has at the absolute latest ddr2. DDR2 is actually getting fairly expensive now. and I wonder if the motherboard could even support a 1 gig strip.

I dont want to upgrade this computer at all because I will be buying a new one soon. But until then I just want a fast and fun os.

---

### Post by rgreener25 on 2012-02-01
I would go for lubuntu it is really lightweight

---

### Post by 23senick on 2012-02-01
I have Lubuntu 10.04 (Long Term) on an old Dell with 512mb RAM and 800 processor, I installed it for precisely the reasons mentioned.  Runs well.  I'd go for that, though might be tempted to try latest version.

---

### Post by Bartender on 2012-02-02
> **SAIYANPRINCE said:**
> Do you know how much xp uses? 

I've fired up XP numerous times, then opened up Task Manager, gone to Performance tab, then let XP idle for 20 minutes or so.  It settled out at about 700+ MB of RAM usage.

I've been pricing DDR2 lately.  About $35 for brand new Crucial 2GB (2 X 1GB sticks).  It sucks that 2GB of old DDR2 RAM costs roughly the same as 8GB of the latest and greatest.

---

### Post by mastablasta on 2012-02-02
> **Bartender said:**
> I've fired up XP numerous times, then opened up Task Manager, gone to Performance tab, then let XP idle for 20 minutes or so. It settled out at about 700+ MB of RAM usage.

that's way to much. what kind of things you had installed?!?!
 
i was running XP on 256MB mashcine. it ran a bit slow bit ran.
 
My idle is about 350-380MB. 
running: VNC, Antivir, Comodo firewall, Various update progs (google update and the like), printer drivers/assistant whatever BS they have and a few other minor stuff...
 
at work is arround 330. no firewall and also some other stuff are different.

---

### Post by Kixtosh on 2012-02-02
> **mastablasta said:**
> that's way to much. what kind of things you had installed?!?! ...With nothing but Office and the usual Microsoft applications on my XP, I always found that it would use whatever I put in there. I started out with 512 MB dual channel memory, and then upgraded to the maximum for the laptop, which was 1.2 GB. In both cases, XP seemed to make maximum use of RAM quite frequently, and was always dipping heavily into virtual memory, of which it made constant use at all times. I'm not saying this is necessarily a bad thing (I understand that a good O.S. should make maximum use of the resources available to it). I'm just making the observation. W2K was happy enough with 256 MB of RAM, but also made heavy and constant use of virtual memory.

When things were running smoothly, I found standard browsing and office productivity applications ran well in W2K or XP, as I hinted earlier. They opened fast and worked fine, until something would occasionally go mad and hog too much CPU or RAM and I'd have to shut it down. My main complaints, in comparison to Ubuntu (I won't mention security), were:

[LIST]
[*]Clumsy and sluggish updates, which would sometimes fail completely until I noticed they weren't happening any more at all.
[*]Increasingly slow boot times and shut down. My solution to that was to use hibernation or standby very often.
[/LIST]

---

### Post by mastablasta on 2012-02-03
heh... ouch. let's see. work maschine - MS office 2007 installed...
 
Running: 7 tabs in IE8, outlook 2007, total commander, SAP production, MS forefront endpoint protection, Onenote... -- idling at 686MB RAM.
 
why would it make more use of ram when idling.... maybe this is something do to with drivers. i never had any of those issues. maybe it also depends on CPU available to the OS?!
 
256MB ram is too low for windows XP. Even if you turn down the eyecandy applications still quickly fill it up and start to use disk for storing. XFCE and LXDE work quite well on it. Gnome2 as well before some latest updates. you can reduce DE's imprint by using a simpler theme, removing virtual desktops. i managed to get it down to little over 100MB on Ubuntu 10.04 Gnome. but osme updates later (maybe it was the applciaitons i was using) made it fill it up and even befor eit filled up completelly it started swapping. 
 
XFCE (the old "!) works much better now. as did debian stable when i tried it.

---

