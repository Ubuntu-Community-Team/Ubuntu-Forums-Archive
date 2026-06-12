---
title: "Adobe flash player"
date: 2014-07-04
forum: New to Ubuntu
---

### Post by peter118 on 2014-07-04
Just installed Lubuntu after years with XP. Trying to download and install apps is a long and frustrating challenge with no success after hours of trying. Very frustrating. How does one install adobe flash player ? I went to the Adobe site and selected a couple different versions for Linux but how the heck do you execute the set up / install . I have read something about plugins and going to the Lunbuntu download center etc on some other threads but I am lost. With XP I just downloaded it hit setup or exe whatever and away it goes.This learning curve with linux is to the point where I feel like scrapping this whole OS. Hours to figure out a simple function that took maybe a couple minutes with XP. UGH :confused::confused::confused::confused::confused:

---

### Post by Bucky Ball on 2014-07-04
Open Synaptic Package Manager and install: flashplugin-installer. 

That easy. No need to install anything from Adobe. Always look in the repositories first, or ask here or elsewhere. ;)

Incidentally, Adobe has withdrawn support for Flash and Firefox finishes with version 11.2 from memory. The only way to have the current Flash is to install Chromium Browser and then Pepper flash (using pepperflashplugin-nonfree) and you will get to 12.**, but only in Chromium. It is 'exclusively Google'. Firefox will remain with 11.2.

Good luck.

---

### Post by grahammechanical on 2014-07-04
Ah, but at least with ubuntu/lubuntu we get a supported OS and a free upgrade to the next version.

Adobe stopped developing a Linux version of flash player a few years ago. And it is also proprietary software so flash player itself is not available for download through the software centre. So, we install an open source installer that installs the Adobe flash plugin. That installer takes all the complications away.

Remember, we are not customers unless we purchase the product. And we do not purchase Ubuntu or its flavours like Lubuntu. They are a gift. And so is advice from this forum.

---

### Post by craig10x on 2014-07-04
Or you can go to google chrome's website and download the deb file which you then can install using the ubuntu software center...Google Chrome has the pepperflash built into it already as well as a neat pdf reader and also installs a ppa in your software sources so you get the latest Chrome as soon as it's released (through your software updater)....

Chrome has an agreement with adobe to supply the newest flash for their pepperflash plug in which is used on ALL Chrome editions (Windows, Mac and Linux)....

---

### Post by caver12 on 2014-07-04
You can also install gnash, and gnash-plugin, in synaptic. That way you have Flash in Firefox. I use it instead of Adobe. It supports more than Firefox but I don't know if Chrome/Chromium can use it.

---

### Post by monkeybrain20122 on 2014-07-04
> **caver12 said:**
> You can also install gnash, and gnash-plugin, in synaptic. That way you have Flash in Firefox. I use it instead of Adobe. It supports more than Firefox but I don't know if Chrome/Chromium can use it.

Does gnash work for you for more than may be one demo on Youtube?

In my experience gnash and lightspark are both waste of space. When they work (for the < 5 demo videos on Youtube) they perform even worse than flash.

Op can get flash working in Firefox easily by just installing restricted-extras. While flash 11.2 is a bit outdated, it works for liken 95+ of the sites and lightyears better than gnash.

---

### Post by monkeybrain20122 on 2014-07-04
> **craig10x said:**
> Or you can go to google chrome's website and download the deb file which you then can install using the ubuntu software center...Google Chrome has the pepperflash built into it already as well as a neat pdf reader and also installs a ppa in your software sources so you get the latest Chrome as soon as it's released (through your software updater)....

Chrome has an agreement with adobe to supply the newest flash for their pepperflash plug in which is used on ALL Chrome editions (Windows, Mac and Linux)....

I get pepper flash working on Firefox
[http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html](http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html)
For a pre-alpha it works very well. There are glitches like webcam and some buttons on some sites but for the most common use cases (video streaming) it is fully working already.

---

### Post by monkeybrain20122 on 2014-07-04
> **peter118 said:**
> Just installed Lubuntu after years with XP. Trying to download and install apps is a long and frustrating challenge with no success after hours of trying. Very frustrating. How does one install adobe flash player ? I went to the Adobe site and selected a couple different versions for Linux but how the heck do you execute the set up / install . I have read something about plugins and going to the Lunbuntu download center etc on some other threads but I am lost. With XP I just downloaded it hit setup or exe whatever and away it goes.This learning curve with linux is to the point where I feel like scrapping this whole OS. Hours to figure out a simple function that took maybe a couple minutes with XP. UGH :confused::confused::confused::confused::confused:

Open synaptic and find "lubuntu-restricted-extras", install that package and it will install flash as well as other media codecs you need. As others say you don't install directly from adobe's site like in Windows. Same goes with other media plugins.

---

### Post by buzzingrobot on 2014-07-04
> **peter118 said:**
> Just installed Lubuntu after years with XP. Trying to download and install apps is a long and frustrating challenge with no success after hours of trying. Very frustrating. 

Forget the Windows way of searching for software packaged as archives at some random site. That's not how it's done.  Tens of thousands of software packages are in the Ubuntu repositories. Search in Synaptic, click, done.

---

### Post by peter118 on 2014-07-04
Thanks. I did the "lubuntu restristed package" and  I got it to install something somewhere. Where do you find all this stuff that was supposedly installed? I would like in addition to some kind of flash player a download torrent client. I used to use vuze and I see "transmission" here in my start /internet menu. Is that used for torrents and if not is it possible to install vuze? One more thing , this gnome player only seems to play avi's. How do you get it to play .wmv or .mp4 files or can you? Do i need to get a different player or newer version or add file types to gnome player so it can play them and how is that done.I used to use vlc player and that played just about everything. Sorry for all the questions but this is just getting so frustrating. I can't seem to find where anything is after it installs.When these packages are installed aren't there icons somewhere to lead you to what was installed???? :confused::confused:

---

### Post by JeQhdMD on 2014-07-04
Transmission is an excellent torrent program, as is Deluge, as is Ktorrent, and so on.  There are at least 15 torrent managers for linux (many of these will run in windows also).   If you use the standard method of installing programs in Linux (via Package Managers using prescribed repositories (aka sources)), then, the program will be installed to the appropriate category in your Lubuntu menu.   Usually, the package will tell you where it is installed, although there are MANY ways to find out (via the CLI (command line interface -)), via standard menu search windows, etc.

Long story short . . . if you had/have an experienced Linux user available to sit with you, it takes about an hour or maybe two for most folks to grasp 90% of the basics.  Since you sound like that's not going to be your situation, just get a decent notebook, read these forums and MANY (thousands) of web sites, youtube tutorials etc. that provide info on using Linux.   Remember, Linux (via Unix) was around first, and so it's methods are different than windows.

---

### Post by buzzingrobot on 2014-07-05
> **peter118 said:**
> Thanks. I did the "lubuntu restristed package" and  I got it to install something somewhere. Where do you find all this stuff that was supposedly installed? I would like in addition to some kind of flash player a download torrent client. I used to use vuze and I see "transmission" here in my start /internet menu. Is that used for torrents and if not is it possible to install vuze? One more thing , this gnome player only seems to play avi's. How do you get it to play .wmv or .mp4 files or can you? Do i need to get a different player or newer version or add file types to gnome player so it can play them and how is that done.I used to use vlc player and that played just about everything. Sorry for all the questions but this is just getting so frustrating. I can't seem to find where anything is after it installs.When these packages are installed aren't there icons somewhere to lead you to what was installed???? :confused::confused:

You don't need to "find" them.  The packages contain scripts to ensure all the components are copied to the correct locations.  When you relaunch Firefox, you should see Adobe Flash listed as a plugin.  The fonts, codecs, etc., also included in the "lubuntu restricted packaged" are also installed and ready to use. (Go to Lubuntu's settings to change fonts, if you wish.)

Transmission is a popular torrent client.  Vuze is in the 14.04 repositories, if you are using Lubuntu 14.04. VLC is in also in the repositories. 

Ubuntu's repositories are servers where software packaged for Ubuntu is stored.  Synaptic, the Software Center, and other similar applications are front-end tools that list all the packages stored in those repositories, and allow you to search and select packages for installation. The packages will then be downloaded and installed. (This is the equivalent to having all Microsoft software plus tens of thousands of packages from independent vendors stored at one location accessible from one application.)

Menu entries should be automatically constructed for software installed from the repositories. Lubuntu is intended as a light-weight menu-driven system.  Ubuntu Unity and Ubuntu Gnome use a more icon-oriented interface without Windows-style menus.

---

### Post by Bucky Ball on 2014-07-05
Again, yea, Vuze is in the repositories. Just look and do some research. It runs natively on Ubuntu ...

Just open the Software Centre or Synaptics and have a look. Don't complicate it. Forget Windows thinking and take a 180 degree swing in either direction. Deep breath! ;) :-k

PS: The title of this thread is about Adobe Flash. If you begin other support requests that have nothing to do with the title of the thread and on the second page of the thread you severely limit your chances of getting support. Best to start a new thread with a descriptive title. ;)

---

### Post by peter118 on 2014-09-22
Thanks to all for your help.I am slowly learning this operating system and what goes along with it.I appreciate the wealth of knowledge here and the amount of apps available. Have a great day !!!!!  :p

---

### Post by Mike_Walsh on 2014-09-22
> **peter118 said:**
> Thanks to all for your help.I am slowly learning this operating system and what goes along with it.I appreciate the wealth of knowledge here and the amount of apps available. Have a great day !!!!!  :p

If you're interested, Peter, it's quite easy to set Lubuntu up with a 'Mac-style' dock at the bottom of your screen, and to move your taskbar up to the top, like this:-


[ATTACH=CONFIG]256612[/ATTACH]

The fancy wallpaper is my own doing, by the way; I've always had an interest in graphic design!

It's an amazing operating system. Although it's designed for older hardware, I know a few people who run it on 'top-end' systems, they like it that much.

However, as Bucky pointed out, this is getting away from the original thread subject. If you want to contact me through the private messages, I'd be more than happy to explain some of the points to you.....or carry on with enquiring through the forums; there's a lot of amazingly well-informed, happy-to-help individuals on here; it's all part of what makes the Ubuntu community so great, and a pleasure to be a part of.


Regards,

Mike.

---

