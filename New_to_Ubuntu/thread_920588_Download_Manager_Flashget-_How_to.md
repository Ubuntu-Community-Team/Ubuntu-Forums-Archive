---
title: "Download Manager: Flashget- How to"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by casaduana on 2008-09-15
How to run Flashget in Ubuntu V 8.04

1- Install Wine
2- Install Flashget, which will install itself in "wine" programs; Open Flashget so it shows in Taskbar
3- Install Flashgot as an add-on in Firefox

4- Restart Firefox, type:"about:config" in address box in Firefox (do not type quotes) and click Go arrow or hit Enter/Return
5- Firefox will show a caution page, hit enter anyway; scroll down to "flashgot.useWine"; right click on this line to change Boolean to "True"
6- Close and restart Firefox; click on Tools, Flashgot, ...more options. In window that comes up, click on Download Manager box to open and you will see Flashget is visible, click on "Flashget"; click on "Okay"; close and restart Firefox.
7- Flashget will now work as in Windows, with single or multiple downloads, with pause, schedule, restart of downloads in Rapidshare, etc.

Happy Downloading to All!

---

### Post by bangmalley on 2008-09-16
no offense here, but easier way is:
[https://addons.mozilla.org/en-US/firefox/addon/201](https://addons.mozilla.org/en-US/firefox/addon/201)

may not have as many features as flashget but get the jobs done.

---

### Post by BryanMarley on 2008-09-16
thanks, for me it worked.

---

### Post by deebocean on 2008-09-23
thanks a lot, so helpful

---

### Post by izak on 2009-06-01
This post should be made more visible. I tried various different ubuntu native solutions (from wget through to graphical stuff like kget and others). 

Flashget in wine works easier and better. I'm all for using good linux alternatives, but in this case the windows program is just better. 

There were even cases where wget could not get past 4-6Mb of a 60Mb download, but flashget could.

---

### Post by Virus666 on 2010-01-12
> **casaduana said:**
> How to run Flashget in Ubuntu V 8.04

1- Install Wine
2- Install Flashget, which will install itself in "wine" programs; Open Flashget so it shows in Taskbar
3- Install Flashgot as an add-on in Firefox

4- Restart Firefox, type:"about:config" in address box in Firefox (do not type quotes) and click Go arrow or hit Enter/Return
5- Firefox will show a caution page, hit enter anyway; scroll down to "flashgot.useWine"; right click on this line to change Boolean to "True"
6- Close and restart Firefox; click on Tools, Flashgot, ...more options. In window that comes up, click on Download Manager box to open and you will see Flashget is visible, click on "Flashget"; click on "Okay"; close and restart Firefox.
7- Flashget will now work as in Windows, with single or multiple downloads, with pause, schedule, restart of downloads in Rapidshare, etc.

Happy Downloading to All!

I tried at least 5 download manager in Ubuntu, none of them complete equivalent of FlashGet. Thus, I had to install FlashGet 1.73 (Classic) via Wine by that instruction. However I cannot get work 2 critical option.

**[SIZE=3]1)[/SIZE]** In Windows when I try to download a file, **FlashGot** directs me a **FlashGet** window which allows me to change the destination of download, enter a username/password, type of download etc... But in Ubuntu, download immediately begins and I have to be contented with default options of FlashGet; default download properies can be only changed in tools menu.

How can I enable download properties of FlashGet at the beginning of download? Does upgrade the FlashGet help?


[SIZE=3]**2)**[/SIZE] Sometimes I download big amount of files (operating system iso, hd movies etc...). Naturally, I leave the PC for download and go to bed. In Windows, FlashGet has an shut down option and it shuts down the PC after all the downloads finished. In Ubuntu, FlashGet does not shut down the PC; only the Wine. I know that's normal; FlashGet tries to shut down Windows, hence in Ubuntu it can shut down only Wine.

Is there any way to make a script which shuts down Ubuntu when Wine/FlashGet is closed? Here are the processes of Wine/FlashGet: **flashget.exe**, **wineserver**, **explorer.exe**, **services.exe**, **winedevice.exe**

**System:** Ubuntu 9.04 Jaunty Jackalope, Firefox 3.0.17, FlashGot 1.2.1.09, Wine 1.0.1, FlashGet 1.9.6.1073

**Edit:** **[SIZE=3]1[/SIZE]** has been solved by upgrading FlashGet to 1.9.6.1073. :-) Now, only [SIZE=3]**2**[/SIZE] has stayed unsolved... And do not **EVER** install lastest version of FlashGet (3.3) on your Ubuntu; it is totally unstable and unusable...

---

### Post by Virus666 on 2010-01-13
BUMP...

Any idea?...

---

### Post by Virus666 on 2010-01-14
BUMP again...

Is there any idea for making a **script** that shuts PC when FlashGet/Wine is closed?... How?

---

