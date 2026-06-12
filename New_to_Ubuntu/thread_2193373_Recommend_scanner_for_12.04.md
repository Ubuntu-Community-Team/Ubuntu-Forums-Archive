---
title: "Recommend scanner for 12.04"
date: 2013-12-12
forum: New to Ubuntu
---

### Post by MickeyPilgrim on 2013-12-12
I want to find a simple-to-install scanner for Ubuntu 12.04
I'd do photos, slides, documents occasionally.
Every suggestion I see goes to directions that are many years old and lead to dead links

---

### Post by DuckHook on 2013-12-12
These days, many scanners are just plug-and-play. The drivers are already in the kernel or are easily installed from the repositories. To make sure that you are buying a supported model, [this]("https://help.ubuntu.com/community/Scanners") link should prove very useful. For what it's worth, I have an HP all-in-one patched into my network. All functionality including the scanning features are automatically recognized with the installation of HPLIP from the repositories. Scanning is seamless and "just works". Be sure to stick with supported models though, unless you enjoy wrestling with compiling proprietary vendor drivers.

---

### Post by asus-user on 2013-12-12
> **MickeyPilgrim said:**
> I want to find a simple-to-install scanner for Ubuntu 12.04
I'd do photos, slides, documents occasionally.
Every suggestion I see goes to directions that are many years old and lead to dead links


So are you looking for a scanner software or for a scanner device which is supported by Ubuntu 12.04?

Have a look here: [https://help.ubuntu.com/community/Scanners](https://help.ubuntu.com/community/Scanners) 
hope it helps.

---

### Post by MickeyPilgrim on 2013-12-12
You suggested I go to 
[https://help.ubuntu.com/community/Scanners](https://help.ubuntu.com/community/Scanners)

It is really old info - one posting last year about an unsupported scanner and so much mysterious jargon.

Has anyone purchased a scanner that can plug in and run on 12.04 ??

---

### Post by mörgæs on 2013-12-12
[http://ubuntuforums.org/showthread.php?t=361236](http://ubuntuforums.org/showthread.php?t=361236)

---

### Post by MickeyPilgrim on 2013-12-12
I want to buy a scanner that will plug & play

---

### Post by MickeyPilgrim on 2013-12-12
> **mörgæs said:**
> [http://ubuntuforums.org/showthread.php?t=361236](http://ubuntuforums.org/showthread.php?t=361236)

I searched the thread, Desktop Hardware Compatibility List., and for scanners everything is very old

---

### Post by MickeyPilgrim on 2013-12-12
> **DuckHook said:**
> These days, many scanners are just plug-and-play. The drivers are already in the kernel or are easily installed from the repositories. To make sure that you are buying a supported model, [this]("https://help.ubuntu.com/community/Scanners") link should prove very useful. For what it's worth, I have an HP all-in-one patched into my network. All functionality including the scanning features are automatically recognized with the installation of HPLIP from the repositories. Scanning is seamless and "just works". Be sure to stick with supported models though, unless you enjoy wrestling with compiling proprietary vendor drivers.

DuckHook - what kind of scanner are you using?

MickeyPilgrim

---

### Post by DuckHook on 2013-12-12
The link that I gave you is the same one that asus-user pointed you to. I also noted that I use an HP all-in-one multifunction printer/scanner/copier. My model is the CM1415fnw, but HP probably doesn't make this model anymore, so my giving you my actual model info is likely of no use to you.

The referenced webpage has a link that further connects you to the SANE site which holds a database of all supported devices, complete with a search engine and another list sorted alphabetically by manufacturer. There are 417 scanners which are completely supported. [This]("http://www.sane-project.org/sane-supported-devices.html") is that linked site, which was easily accessed from the initially referenced web page. If you are prepared to install drivers from the repositories, which is not a difficult process, then you can also expand the list of offerings further. HP multifunction machines are almost all supported by HPLIP which is available from the Ubuntu Software Center.

I'm afraid that no one can just lead you by the hand here and make your decision for you. We have no idea where you intend to purchase, what they carry, what speed scanner you want, what brand you favour... these are the factors that are unique to each of us, the freedom to choose that most people reserve to themselves and which make the idea of choice such a treasured concept in the Linux world. The most we can do is to give you the tools and info to make your own decision.

It might work better for you to settle on one or two popular mainstream models and then ask the members of this forum for their experiences with these machines. You may get no responses because there are just so many brands and models out there, but at least you would then be asking a specific question that is capable of yielding the specific answers that you are looking for.

---

### Post by ajgreeny on 2013-12-12
I would also recommend HP scanners in their "all-in-one" printers, which are generally supported within a few weeks or months of appearing on the market.

If HP is a manufacturer that you will consider as a possibility, and as DuckHook says, we have no way of knowing what is available or acceptable to you, I suggest you have a look at [http://hplipopensource.com/hplip-web/supported_devices/index.html](http://hplipopensource.com/hplip-web/supported_devices/index.html) where all the info you could ever want is available, and as you can see, most of their hardware is well supported.

Bear in mind that some new models of HP will probably need an updated version of HPLIP to get full support, but that simply means downloading the new version from [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html) then follopwing the installation info at [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

---

### Post by r-senior on 2013-12-12
I've had a couple of Canon LIDE scanners and they've been fine with Ubuntu. My current one is a few years old now but is a CanoScan N124OU. No fuss, just works.

The scanner driver is SANE, so a check of their compatibility list is probably worthwhile:

[http://sane-project.org/cgi-bin/driver.pl](http://sane-project.org/cgi-bin/driver.pl)
[http://sane-project.org/sane-supported-devices.html](http://sane-project.org/sane-supported-devices.html)

---

