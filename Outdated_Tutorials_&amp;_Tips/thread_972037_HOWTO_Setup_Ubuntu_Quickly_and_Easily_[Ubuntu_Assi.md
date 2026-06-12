---
title: "HOWTO: Setup Ubuntu Quickly and Easily [Ubuntu Assistant]"
date: 2008-11-05
forum: Outdated Tutorials &amp; Tips
---

### Post by altonbr on 2008-11-05
[CENTER][SIZE=5]**Setup Ubuntu Quickly and Easily [Ubuntu Assistant]**[/SIZE][/CENTER]

[SIZE=4]**Purpose**[/SIZE]
I install fresh Ubuntu images on computers weekly and find it time consuming to manually update/upgrade Ubuntu, install third-party repositories and install extra, multimedia-oriented applications.

I [posted my script]("http://digg.com/linux_unix/The_Perfect_Desktop_Ubuntu_8_10_Intrepid_Ibex?t=20405687#c20405687") for the first time publicly on Digg.com and due to its popularity, I decided to add a support thread for it on UbuntuForums.org (this site).

I have been developing this script that I call **Ubuntu Assistant** since July 2007. The more I use it, the more simple it gets and I plan to keep it that way. At one time it was so bloated, it actually had a installer, ran 'fixes' for specific Ubuntu versions and all sorts of other garbage it didn't need.

Nowadays, the script updates/upgrades Ubuntu, installs a couple third-party repositories (like Medibuntu & Wine) and installs a couple programs and libraries.

[SIZE=4]**How does it work?**[/SIZE]
I don't have any skills with Python or GTK+ to make a proper front-end, so this is a simple BASH script (a program that can be ran from the terminal).

I advise you to run this script - once - after a fresh install of Ubuntu. It sets up everything that I (and hopefully you) will need.

This program is NOT like or similar to [Ubuntu Tweak]("http://ubuntu-tweak.com/"), [Automatix]("http://en.wikipedia.org/wiki/Automatix_%28software%29") or [Ultamatix]("http://en.wikipedia.org/wiki/Ultamatix").

[SIZE=4]**What does it do?**[/SIZE]
This script is completely open-source and I encourage you to modify it to your needs. The script has evolved from Hardy Heron 8.04 LTS to Lucid Lynx 10.04 LTS, so make sure to read the script to see what programs it installs but here is general list:

[LIST]
[*]Installs Wine, Medibuntu and some PPA repositories (so you can run Windows programs, play DVDs and get the latest and greatest of some software)
[*]Installs [GetDeb]("http://getdeb.net") and [PlayDeb]("http://playdeb.net") repositories
[*]Updates and upgrades your machine
[*]Installs all sorts of programs and libraries that the average media-centria user will use
[*]Downloads and installs some nice fonts I use
[*]Downloads and installs a Rhythmbox plugin called Jump to Playing
[*]Downloads and installs Elementary icons
[*]Changes your default theme (A lot of people may not like this, but I hate the default theme, so I hope you enjoy)
[/LIST]
I am currently porting this program to PyGTK so it more like Ubuntu Tweak (so you can choose what changes get performed) but for now, unless you know how to edit bash scripts, you'll either just have to run my script, or don't.

[SIZE=4]**Frequently Asked Questions [FAQ]**[/SIZE]
**I don't like your defaults, what can I do?**
*EDIT IT!*

I've set up the file so it can be easily modified. Delete any programs or libraries you do not want, such as:
> phatch \or add to the list with programs you want installed by default:
> banshee \
openarena \
virtualbox \**What do those backslashes mean?**
The backslashes are in place for aesthetic reasons. They're there so I can place the program names on multiple lines, making it easier for humans to read. The backslash actually escapes the newline character, making the program only see the spaces between each program in the list.

I could make it like this:
```
sudo aptitude install acroread acroread-plugins agave alsa-oss cheese
```but once you have 30 programs on one line, it can become overwhelming to edit.

[SIZE=4]**What does it NOT do?**[/SIZE]
[LIST]
[*]Compile programs - it only uses the repositories
[*]Doesn't do much if you have 'multiverse' and/or 'restricted' repositories turned off. If you're an open-source zealot, the default install of Ubuntu with the 'free software only' option turned on works quite well, so you probably won't need my script anyway!
[*]Detect what version of Ubuntu you're using. I'm trying to keep this script as simple as possible and have it separated into different downloads, per release. If you're using Warty (4.10), than may God help us all.
[*]Scratch your back, do the laundry, etc.
[/LIST]

**[SIZE=4]Downloading[/SIZE]**

[LIST]
[*]_[Hardy Heron 8.04 LTS]("http://brettalton.com/docs/ubuntu_assistant/hardy.sh")_
[*]_[Intrepid Ibex 8.10]("http://brettalton.com/docs/ubuntu_assistant/intrepid.sh")_
[*]_[Jaunty Jackalope 9.04]("http://brettalton.com/docs/ubuntu_assistant/jaunty.sh")_
[*]_[Karmic Koala 9.10]("http://brettalton.com/docs/ubuntu_assistant/karmic.sh")_
[*]_[Lucid Lynx 10.04 LTS]("http://brettalton.com/docs/ubuntu_assistant/lucid.sh")_
[/LIST]
 
**[SIZE=4]Running[/SIZE]**
You can either download the script from above or run this command to download and run the program.
_All Versions:_
```
wget --no-check-certificate http://brettalton.com/docs/ubuntu_assistant/`lsb_release -cs`.sh; chmod +x `lsb_release -cs`.sh; ./`lsb_release -cs`.sh
```[B][CENTER]Enjoy! Criticism welcome![/CENTER]
[/B]

---

### Post by jpeddicord on 2008-11-13
Approving as it seems to use supported software installation methods. For users using this to install software, please keep problems confined to this thread. :)

---

### Post by directcharitycontribution on 2008-11-13
cool

---

### Post by swegner on 2008-11-13
The script looks safe anyway.  Although, it might be nice to comment what each of the installed software packages does.  This seems to be a list quite tailored to your needs, and probably not all of this software is necessary for the average user.

My other comment is, there is a standardized way to make all of these modifications via a clean, integrated user interface.  Rather than forcing new Ubuntu users right into bash scripts and the commandlines, it may be better to direct them to the numerous UI-based tutorials for installing software, adding ubuntu-restricted-extras, installing WINE, etc.

---

### Post by altonbr on 2008-11-21
> **jacobmp92 said:**
> Approving as it seems to use supported software installation methods. For users using this to install software, please keep problems confined to this thread. :)

Thanks!

> **directcharitycontribution said:**
> cool

Did you like it?

> **swegner said:**
> The script looks safe anyway.  Although, it might be nice to comment what each of the installed software packages does.  This seems to be a list quite tailored to your needs, and probably not all of this software is necessary for the average user.

My other comment is, there is a standardized way to make all of these modifications via a clean, integrated user interface.  Rather than forcing new Ubuntu users right into bash scripts and the commandlines, it may be better to direct them to the numerous UI-based tutorials for installing software, adding ubuntu-restricted-extras, installing WINE, etc.

I'll try and pipe my results to zenity and use a checkbox for all the software people want installed, but the purpose of this was for people like me - computer technicians - that need to do a few basic things, fast.

It is much more time consuming to install WINE and Medibuntu repositories, update/upgrade, then install all the required libraries through the GUI than using this script.

Who knows, maybe someone with Python skills can help me out?

---

### Post by altonbr on 2010-05-10
I did a major overhaul of the main post as it hasn't been updated since Ubuntu 8.10 Intrepid Ibex.

The scripts have been updated since Hardy all the way up to Lucid.

I'm in the process of porting this script from BASH to PyGTK, so look out for it soon!

Enjoy :)

---

### Post by altonbr on 2010-06-01
I'm now [hosting the code]("http://github.com/brettalton/ubuntu-assistant") on github.com.

---

### Post by altonbr on 2010-07-12
Changed the 'running' line to automatically detect the version of Ubuntu you are running.

```
wget http://brettalton.com/docs/ubuntu_assistant/`lsb_release -cs`.sh; chmod +x `lsb_release -cs`.sh; ./`lsb_release -cs`.sh
```

---

