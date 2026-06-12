---
title: "[SOLVED] IE with Feisty?"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by MooseMagnet on 2008-07-23
I'd like to view the "Watch Instantly" movies available with my Netflix account, but they are viewable on IE only. Is there any good way I can use Internet Explorer? (Feisty on Dell laptop.)

Thanks.

---

### Post by tuxxy on 2008-07-23
There is a mozilla plugin named **User Agent Switcher** this will allow you to change your browsers identity to IE which will most likely allow you to watch them online videos.  

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

If not you can run in WINE i beleive, although I would recommend virtualbox, which will allow you to run windows while in Uubuntu.  Great if you needed IE like that and any other windows app without having to reboot.

[http://www.virtualbox.org/](http://www.virtualbox.org/)

```
sudo apt-get install virtualbox
```

---

### Post by billgoldberg on 2008-07-23
Try [ie4linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page").

---

### Post by MooseMagnet on 2008-07-23
I added the User Agent Switcher add-on, and switched to Internet Explorer 7. When I try to view a movie, it tells me I must enable ActiveX. How can I do this?

When I try to install WINE it tells me this:

W: Failed to fetch [http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/virtualbox_1.5.0-24069-1_Ubuntu_feisty_i386.deb](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/virtualbox_1.5.0-24069-1_Ubuntu_feisty_i386.deb)
  404 Not Found

How can I fix this?

Thanks.

---

### Post by LowSky on 2008-07-23
the link you posted was to Virtualbox, and you don't need virtualbox to install wine.
use this code for wine

sudo apt-get install wine

for IE4Linux
[http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu](http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu)

---

### Post by MooseMagnet on 2008-07-23
sudo apt-get install wine

I get this:

Err [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main wine 0.9.47~winehq0~ubuntu~7.04-1
  404 Not Found
Failed to fetch [http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/wine_0.9.47~winehq0~ubuntu~7.04-1_i386.deb](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/wine_0.9.47~winehq0~ubuntu~7.04-1_i386.deb)  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by Thelasko on 2008-07-23
You will also need cabextract.
 ```
sudo apt-get install wine cabextract

```
Cabextract is needed to decompress certain Microsoft files.  It's all in the instructions on the IEs4linux page.

Let us know how it works.

Happy Hunting!

---

### Post by Thelasko on 2008-07-23
The Automatix website appears to be no more.  No major loss, Automatix was obsolete anyway.  I suggest uninstalling Automatix and taking it out of your sources list.

---

### Post by MooseMagnet on 2008-07-23
Removed automatix from the repositories, then wine and ies4linux installed beautifully.

Browsing with ie6 for linux. :)

Tried to "View Instantly' a movie from Netflix, but it still won't work. Guess more is needed than just the IE browser, maybe XP with service pack such-and-such ..... or whatever.

Bummer. Thanks for the help.

Anybody been able to do this?

---

### Post by LowSky on 2008-07-23
I just looked on Netflix page and it state that Netflix  installs a program to view the movies. If that program relies on Windows' Registry files then I have to say that you may be out of luck.
But don't feel to sad I hear Apple Users are screaming about the same issue. I would send a nice letter to Netflix asking for a timefram as to when they will support Linux.

---

### Post by Thelasko on 2008-07-23
[Wikipedia]("http://en.wikipedia.org/wiki/Netflix#Watch_Instantly") mentions something about WMP 11.  I know WMP 10 can be installed in Wine, but I don't know anything about 11.  I suggest installing 10 and try to upgrade to 11.

I am also unsure about WMP working with IEs4linux.  IEs4linux installs IE in it's own "prefix" directory.  This is to keep it from mucking with the default Wine registry.

Bottom line is, if somebody managed to get WGA to work in Wine, there should be no reason Netflix won't work.  It just requires enough hacking.

---

### Post by MooseMagnet on 2008-07-23
I'll contact them and do what I can.

---

### Post by Thelasko on 2008-07-23
I did find [this page]("http://ubuntuforums.org/showthread.php?t=620640&page=2") that looks promising.  Look ta post 18.

---

### Post by MooseMagnet on 2008-07-23
Post #20 looks promising to me - VirtualBox. But it doesn't seem to be available for Feisty. I'll need to upgrade to Gutsy. And before I do that I need to get to the store and purchase a USB storage device and backup my files. I'll post later, if/when I get it working.

Thanks for the help.

---

### Post by Thelasko on 2008-07-24
You could probably use VMware too.  VMware is free (as in beer) just not open source like Vbox.

---

### Post by timcredible on 2008-07-24
the user agent switcher won't work, neither will ie in wine because netflix requires that you run a version of windows that supports DRM.  a vmware solution (virtualbox or vmware) may work, but you have to have a copy of windows and the DRM 'patch', or whatever is required for windows to recognize and adhere to the DRM stuff.

---

### Post by calvert888 on 2008-07-24
Yeah, I'm a Netflix member too and found this frustrating. But that's why I'm still running a dual boot system with WinXP on my other partition... well, that and for gaming. I'm just not yet to the point where I can give up Windows altogether, unfortunately. If I were trying again, I'd go the VMWare route. Last time I tried to get this to work, I was still unacquainted with VMWare. Good luck!

---

### Post by Thelasko on 2008-07-24
> but you have to have a copy of windows and the DRM 'patch', or whatever is required for windows to recognize and adhere to the DRM stuff.

I believe that is Windows Media Player 11.

---

