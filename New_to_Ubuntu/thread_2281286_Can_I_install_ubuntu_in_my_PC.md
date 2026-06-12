---
title: "Can I install ubuntu in my PC?"
date: 2015-06-05
forum: New to Ubuntu
---

### Post by sandaruwan_kodithu on 2015-06-05
My System Requirments are:896 MB of RAM
                                       2.66GHz  celeron cpu
                                       
ubutu new versions are does not work in my computer.please help me.

---

### Post by grahammechanical on 2015-06-05
You should be trying Lubuntu or Xubuntu

[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

[URL="http://xubuntu.org/getxubuntu/requirements/"]http://xubuntu.org/getxubuntu/requirements/

[/URL][https://ubuntu-mate.org/about/](https://ubuntu-mate.org/about/)

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

[http://ubuntugnome.org/](http://ubuntugnome.org/)

The graphic adapter on that machine is the most likely piece of equipment that will prevent getting a good user experience with both Ubuntu and Ubuntu Gnome.

Regards.

---

### Post by HermanAB on 2015-06-06
Lubuntu or Xubuntu will work on a low end machine.

---

### Post by newb85 on 2015-06-06
Lubuntu is the lightest officially supported member of the Ubuntu family.  From the website

> 
[COLOR=#666666][FONT=Ubuntu]Lubuntu is a good operating system for many old computers, but not for all of them. Some computers have too little horsepower or memory. A rule of thumb is that the computer should not be more than 10 years old.[/FONT][/COLOR]
[COLOR=#666666][FONT=Ubuntu]Memory (RAM)[/FONT][/COLOR]
[COLOR=#666666][FONT=Ubuntu]For advanced internet services like Google+, Youtube, Google Docs and Facebook, your computer needs at least 1 GB RAM.[/FONT][/COLOR]
[COLOR=#666666][FONT=Ubuntu]For local programs like Libre Office and simple browsing habits, your computer needs at least 512 MB RAM.[/FONT][/COLOR]
[COLOR=#666666][FONT=Ubuntu]Processor (CPU)[/FONT][/COLOR]
[COLOR=#666666][FONT=Ubuntu]The minimum specification for CPU is Pentium 4 or Pentium M or AMD K8.[/FONT][/COLOR]
[COLOR=#666666][FONT=Ubuntu]Older processors are too slow and AMD K7 has problems with flash video.[/FONT][/COLOR]
[COLOR=#666666][FONT=Ubuntu]Graphics chip / card[/FONT][/COLOR]
[COLOR=#666666][FONT=Ubuntu]Nvidia, AMD/ATI/Radeon and Intel work out of the box, or the system can be tweaked to work fairly easily. You can get help at the [Ubuntu Forums]("http://ubuntuforums.org/"). With such graphics, or if you don't know, try the current Lubuntu version.[/FONT][/COLOR]




Looks like the CPU the OP listed should be fine for Lubuntu.  The RAM, however might be a little weak.  This is probably one of those cases where the best way to know is to try.  Since Lubuntu's installation media run the environment without installation, it should be easy to try.

---

### Post by Rob Sayer on 2015-06-06
Having used both xubuntu and lubuntu on my 1Gb netbook I'd heartily recommend lubuntu.  14.04 LTS would probably be the best choice.

The only downside of LXDE compared to XFCE is that it doesn't have as many GUI config tools.  But lxde is *much* faster.

---

### Post by mattharris4 on 2015-06-07
I concur with Lubuntu as the best choice here and then you still need to up the RAM to at least 1.5GB.  1GB RAM will be OK for about 80% of websites IME.  Your processor only Passmarks at 254 which is terribly weak, you will be OK on most sites with a RAM upgrade but CPU intensive sites such as SFGate will scroll and load jerkily at best.

In my experience with the 32 bit version of Xubuntu I didn't find it much more CPU and RAM hoggy than Lubuntu is.  It does have fancier graphics (that may or may not be an issue with a Celeron, I tried it with an old Pentium 4 scoring in the mid 300's) but seemed to run OK for me.  Both OSes take about 1300MB RAM to run SFGate with 6-8 tabs open at once in Firefox for me.  80% of so of sites I use will run for me on 1GB of RAM using both Lubuntu and Xubuntu.

---

### Post by mastablasta on 2015-06-08
actually KDE is not bad at 1GB ram and all effects turned off. it should get about 220 MB on idle. however Lubuntu is still lighter. as is Xubuntu.

with low ram it really makes a difference. more is then left for applications

---

### Post by RobGoss on 2015-06-08
A lighter version of Ubuntu is surely the way to go with those specs.

---

### Post by oldrocker99 on 2015-06-08
I will add that Ubuntu MATE is very lightweight as well, lighter even than Lubuntu. Here's an LibreOffice spreadsheet showing that MATE has the lowest RAM usage:[https://www.dropbox.com/s/293xikeyuxdq40t/Link%20to%20Desktop%20Environment%20Benchmarks.ods?dl=0](https://www.dropbox.com/s/293xikeyuxdq40t/Link%20to%20Desktop%20Environment%20Benchmarks.ods?dl=0). Note that different desktops have higher numbers in various benchmarks, but MATE does have the lowest RAM usage.

I love MATE because it recreates the old GNOME 2.3 desktop which I fell in love with back with Ubuntu 8.04, lo these many years ago.

---

### Post by mattharris4 on 2015-06-08
> **mastablasta said:**
> actually KDE is not bad at 1GB ram and all effects turned off. it should get about 220 MB on idle. however Lubuntu is still lighter. as is Xubuntu.

with low ram it really makes a difference. more is then left for applications

I only have limited experience with KDE (I think Canonical's version is Kubuntu but don't quote me on that) and do not have RAM and CPU usage numbers during my general use on it.  I understand that it is a mid-weight OS that is purported to have similar RAM and CPU usage as Xubuntu.  It is free to use so it might be worth a try.  On a 32-bit computer if my usage stats with Xubuntu and Lubuntu transfer over to the OP's use I don't expect it to be much different under heavy load.

Now that I have replaced my ancient desktop with something newer (a refurb HP pre-UEFI model with a Core 2 Duo 3.16GHz, 4GB RAM and a 500GB HDD) I can play around more with the old P4 computer and possibly help people with information on what runs best on old hardware such as my P4 and the OP's laptop.  I replaced it because even using Xubuntu several sites I read daily would not run correctly due to either a computer part failing (I tested the 3.5GB of RAM and the 500GB HDD, both passed with flying colors, I do need to get it under bright light to check for swollen or leaky capacitors and any other signs of electrical component failure) or the old P4 3.0 GHz CPU (Passmark score 358) being too slow for them -- for example Netflix movie playing was a disaster full of skips and jerks even using Xubuntu -- unwatchable, SFGate and MLive were also loading poorly, freezing up and scrolling jerkily and slowly.  The usability of the old P4 computer had worsened drastically over the past month or so with Edubuntu/GNOME GUI and installing Xubuntu did not help much.  I was thinking of giving Puppy Linux a trial run on it but I might try Kubuntu for a bit as well.  When I get around to trying different OSes in an installed environment (as opposed to a USB boot) I will certainly post the results.  At this point that computer is going to be just for playing around with light Linux OSes, it is 8-9 years old so it certainly isn't worth attempting a CPU upgrade on it considering my replacement refurb computer was only $165 shipped.  Depending on what websites the OP reads he may have a similar problem with his laptop.

A little off topic but since I mentioned the replacement computer I will say that I won't be putting any Linux OS on the replacement computer until I have used it for a couple of months to ascertain that it isn't defective as I don't wish to mess up my warranty (which is one year but after 2-3 months assuming it isn't showing any defects I would probably be willing to take a chance and dual-boot with a Canonical OS on it).  It came with Win 7 Professional which isn't actually a bad OS -- I like it much better than Win 8.1, that is for sure.  

I hope the OP can at least get some further use out of his laptop thanks to Canonical and the community support team for whatever OS he chooses.  There are several advantages to this approach including the already discussed monetary savings as well as the ethical issues such as not supporting the near monopoly that Microsoft has on consumer computing nowadays and lessening his environmental carbon use footprint by postponing both the purchase of a new laptop and contributing to the waste stream by trashing a working computer that is just out of date (granted he may have to purchase a new battery -- probably only about $20 on Amazon -- regardless but a computer battery is a lot less waste than a whole laptop, the battery can be recycled whereas trashing a whole computer contributes quite a bit of waste to his local garbage dump).

---

### Post by mastablasta on 2015-06-09
I still fail to see the issue with 8.1 - faster than 7, looks nice, numerous improvements over 7. ok the full screen menu is kind of weird on desktop, but then again there are 3rd party tools. also I dont' really access the mnu that much. and getting to the app is I think same as with Unity - win key+type the app name. or win key then down icon to browse through the apps.

anyway Kubuntu is heavier than Xubuntu but it still works nice on 1 GB as long as effects are turned off. but it does have that windows way of doing things so it might be easier for windows people coming over to navigate through it.

---

### Post by mattharris4 on 2015-06-09
Mastablasta, everyone has the right to their own opinion.  Just because I prefer Win 7 over 8.1 doesn't mean everyone should, I think people have the right to have their own opinions on that.  However, from what I have read about Win 10 it is supposed to incorporate the best of 7 and 8.1 into one OS.  I think if it does that well Microsoft has a chance to keep their monopoly, if Win 10 goes over like a lead balloon Microsoft is done as it exists today (the moral implications of Microsoft maintaining a virtual monopoly are somewhat scary to me, especially with the NSA going around "requesting" backdoor access to the major OSes -- including Linux if Linus' father's hunch is correct, that is really scary to me and Microsoft could theoretically agree to give them that backdoor in exchange for a ban on other OSes use in the US if their owners don't cave to the NSA as well).

Back to scheduled programming, one concern I have for the OP that is not easily cured is his CPU.  It is terribly weak, it will still work fine for most websites but if a site he logs onto regularly taxes the CPU too much (SFGate, here's looking at you) he will still have a poor experience with this particular computer.  After further consideration I think I would try Lubuntu on it if I were him and if it doesn't surf the web smoothly with that OS unfortunately the only real solution to that is a different computer.  He could try Puppy Linux or Tiny Core on it but he would still have to deal with a CPU hog browser (Firefox or Chromium/Chrome) to have anything close to full functionality on the webpages he reads.  Going with second or third tier Linux OSes also has one big problem -- lack of support from its developers.  If he runs into an issue with a major feature he could be SOL (Flash compatibility and PDF downloaders are two possible issues here).

---

