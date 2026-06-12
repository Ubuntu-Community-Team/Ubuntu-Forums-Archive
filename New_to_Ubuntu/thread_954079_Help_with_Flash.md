---
title: "Help with Flash"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by HumanSancho on 2008-10-20
Hi im fairly new to Ubuntu. I have had some problems installing flash.
I entered in the terminal "sudo apt-get install flashplugin-nonfree"
Im pretty sure it worked because now whenever I put it in the terminal i get this:

michael@michael:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
michael@michael:~$

the problem is I still dont have flash player. I cant watch youtube videos and flash games dont work. If someone could help me that would be great.

Thanks!

---

### Post by Kosimo on 2008-10-20
Go here>

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

Download the adobe official .deb for Ubuntu and try to install it
It should work.

If doesn't you can install it manually following this guide:

(First steps on the first topic)
[http://ubuntuforums.org/showthread.php?t=795019](http://ubuntuforums.org/showthread.php?t=795019)

---

### Post by HumanSancho on 2008-10-20
Oh i think i forgot to mention that im using outdated hardware and running dapper drake (bored weekend project:)). 
Will this work with 6.06

---

### Post by Kosimo on 2008-10-20
> **HumanSancho said:**
> Oh i think i forgot to mention that im using outdated hardware and running dapper drake (bored weekend project:)). 
Will this work with 6.06

Nope, that .deb works with Hardy Heron or newer.

---

### Post by HumanSancho on 2008-10-20
Thanks for your help anyways.

---

### Post by Kosimo on 2008-10-20
> **HumanSancho said:**
> Thanks for your help anyways.

You're using dapper  6.06 for any particular reason?
If your hardware is old you can give it a try to Xubuntu 8.04.1

---

### Post by aysiu on 2008-10-20
It's possible that the package manager thinks it's installed but it's not installed. 

Can you paste these commands into the terminal and then post the output back here? ```
sudo updatedb
locate libflash
dpkg -s flashplugin-nonfree
uname -m
cat /etc/lsb-release
``` The first command may take a few minutes to execute. That's okay.

---

### Post by HumanSancho on 2008-10-20
Im only running Dapper Drake because my older brother use to use it and I found a book of his.
Should i try xubuntu 8.04?
I have a Dell Dimension 4300 with 512 mb of ram.
Im really new to Linux, my brother just recently got me interested.

---

### Post by HumanSancho on 2008-10-20
Wow! There really is a helpful community!
Well I pasted the entire thing into the terminal and this is what happened:

michael@michael:~$ sudo updatedb
Password:
michael@michael:~$


Thats it

---

### Post by kansasnoob on 2008-10-20
The Flash 10 Plugin recommended by Kosimo is great. You should also have sun-java6 and gstreamer plugins, you can get the bare essentials by(if it's ubuntu):

```
sudo apt-get install ubuntu-restricted-extras
```

But you'll then have to reinstall flash 10. BTW if you install the new flash 10 via apt it shows up in synaptic as "adobe-flashplugin" whereas the previous version showed up as "flashplugin-nonfree".

Rather than installing just the "restricted-extras" I prefer using synaptic and installing ALL gstreamer (I just type gstreamer in the synaptic search and I install everything that begins with gstreamer), and also all sun-java6-**** **EXCEPT -doc and -source**!

OH IGNORE PLEASE!

---

### Post by HumanSancho on 2008-10-20
Kansasnoob,
 Should i just type that in the terminal?
this is what happened:

michael@michael:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ubuntu-restricted-extras
michael@michael:~$

---

### Post by eternalnewbee on 2008-10-20
Hi there. This is what solved my problem:
sudo apt-get update && sudo apt-get autoremove totem-mozilla && sudo apt-get install mozilla-mplayer flashplugin-nonfree.
Good luck.

---

### Post by eternalnewbee on 2008-10-20
Hi there. This is what solved my problem:
sudo apt-get update && sudo apt-get autoremove totem-mozilla && sudo apt-get install mozilla-mplayer flashplugin-nonfree.
Good luck.

---

### Post by HumanSancho on 2008-10-20
Thanks for the help

---

### Post by kansasnoob on 2008-10-20
> **HumanSancho said:**
> Im only running Dapper Drake because my older brother use to use it and I found a book of his.
Should i try xubuntu 8.04?
I have a Dell Dimension 4300 with 512 mb of ram.
Im really new to Linux, my brother just recently got me interested.

Sorry about my other post, I kept getting interrupted and hadn't seen that you're using Dapper.

But my answer to this, "Should i try xubuntu 8.04?", is YES! That is if the current install is Dapper Xubuntu. You should be able to run either Ubuntu or Xubuntu on that. And 6.06 (Dapper) should upgrade to Hardy (8.04) just fine if you have a fast internet connection.

A fresh install of either 8.04 or 8.10 Beta would be much easier to work with. Intrepid (8.10) is only 3 days from Release Candidate stage and if this is just a project I'd go for it!

Just stay away from the daily builds! Today's is oversize and doesn't fit a CD.

---

### Post by kansasnoob on 2008-10-20
Check out:

> Upgrade from 6.06 LTS to 8.04 LTS

Here:

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by gandaran on 2008-10-21
HumanSancho
if you want flash to work in ubuntu 6.06, you can do it, it's easy
first remove the flashplugin-nonfree you installed, that package is outdated, doesn't work, you'll have to install directly from the adobe site.
now open firefox go to youtube, click on that missing plugin message, and just follow the process to install adobe flash.
another way download adobe flash tar.gz package here [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
unpack/extract the package, now drag the libflashplayer.so file to the hidden home .mozilla/plugins folder (home/'user'/.mozilla/plugins), make the plugins folder first.

---

