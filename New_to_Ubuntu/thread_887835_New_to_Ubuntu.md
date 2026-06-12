---
title: "New to Ubuntu"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by grcjman2008 on 2008-08-12
Well, I finally did it.  I made the transition from Windows XP to Ubuntu yesterday.  So far I really like it.  I do have a question, and if it's been asked before (which I'm sure it has) I apologize for asking again. Just please direct me to the correct thread.  

For the past 2 1/2 years I've been using Firefox as my web broswer with Windows.  I've always been able to watch You Tube videos, but now Firefox on Ubuntu doesn't do so.  I know I can use Totem Movie Player to watch You Tube videos, and I already have it configured to do this, but I really would prefer to be able to watch them again through Firefox as I once was able to.

What do I need to do in order to do this?  Thanks.

---

### Post by tamoneya on 2008-08-12
you just need to install flashplugin.  Run these commands in terminal:```
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```

---

### Post by michaelaly on 2008-08-12
Then if you have audio issues(no sound in Youtube videos) try this [http://ubuntuforums.org/showthread.php?t=789578&highlight=sound+flash](http://ubuntuforums.org/showthread.php?t=789578&highlight=sound+flash)

---

### Post by gjoellee on 2008-08-12
click on the link below and wait up to 15sec before a window appears, click yes and Flash will download and install itself (you need flash to look at youtube videos)
[apt://flashplugin-nonfree](apt://flashplugin-nonfree)

---

### Post by t0p on 2008-08-12
Welcome to ubuntu!!

As a number of people have already said, you need the flash plugin to watch youtube vids in firefox.

You'll also need to install other codecs if you want to play mp3s, wmv files, and other popular media file formats.  The easiest way to install these codecs is to get the **ubuntu-restricted-extras** package.  In terminal, type the command

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by grcjman2008 on 2008-08-12
> **tamoneya said:**
> you just need to install flashplugin.  Run these commands in terminal:```
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```

Thanks for the responses.  For some reason it's still not working correctly. I entered the first command and hit enter, to which a lot of data popped up.  Then when it was finished, I entered the second command and hit enter.

I tried to check out a You Tube video after doing this and at first it looked like it was going to load, then it stopped.  No picture, no sound.

---

### Post by okey666 on 2008-08-12
Do other flash apps work (games etc) and I always find a reastart tends to clear things up.

---

### Post by grcjman2008 on 2008-08-12
> **okey666 said:**
> Do other flash apps work (games etc) and I always find a reastart tends to clear things up.

No, they don't.  I restarted a couple of times.  I also tried to install Adobe Flashplayer for Linux...nothing still.

---

### Post by grcjman2008 on 2008-08-12
> **gjoellee said:**
> click on the link below and wait up to 15sec before a window appears, click yes and Flash will download and install itself (you need flash to look at youtube videos)
[apt://flashplugin-nonfree](apt://flashplugin-nonfree)

I get a window stating that it has already been installed...still not working.

---

### Post by grcjman2008 on 2008-08-12
> **t0p said:**
> Welcome to ubuntu!!

As a number of people have already said, you need the flash plugin to watch youtube vids in firefox.

You'll also need to install other codecs if you want to play mp3s, wmv files, and other popular media file formats.  The easiest way to install these codecs is to get the **ubuntu-restricted-extras** package.  In terminal, type the command

```
sudo apt-get install ubuntu-restricted-extras
```

I've installed these already as well.

---

### Post by MasterJS on 2008-08-12
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

go there and click the drop down arrow where it says "Select Which Version to Download...". Choose tar.gz for Linux

Save the .tar.gz file to your desktop and wait for the file to download completely.
Unpackage the file. A directory called install_flash_player_9_linux will be created.
In terminal, navigate to this directory (by typing ```
cd /home/(the name of your user)/Desktop/install_flash_player_9_linux
``` then enter) and then type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.

---

### Post by grcjman2008 on 2008-08-12
I just did that, and still nothing yet.

---

### Post by herteljt on 2008-08-13
> **grcjman2008 said:**
> Well, I finally did it.  I made the transition 
What do I need to do in order to do this?  Thanks.


Here are my two cents:

2) I would try the guide at this link [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

If you want to check and see if flash is installed open up Firefox and put the following into the address bar:

```
about:plugins
```

You should see Shockwave Flash and be able to read the version installed.


2) Are you running a 64-bit computer by chance?  I think the process is different for 64-bit.  Here are two links that may help (keep in mind this is only if you are running a 64-bit computer)


[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

[https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins?action=show&redirect=FirefoxAMD64Flash9#head-74ed36356cdab258889ed4e9ad010f068e13ff38](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins?action=show&redirect=FirefoxAMD64Flash9#head-74ed36356cdab258889ed4e9ad010f068e13ff38)

---

### Post by okey666 on 2008-08-13
> **herteljt said:**
> 

2) Are you running a 64-bit computer by chance?  I think the process is different for 64-bit.  Here are two links that may help (keep in mind this is only if you are running a 64-bit computer)


Just to clarify run:
```
uname -a
```

and see if it says more like:
> Linux Server 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 _i686_ GNU/Linux

thats probably 32-bit (note the underlined bit) and if it says something more like:
> Linux key-oscar 2.6.24-19-rt #1 SMP PREEMPT RT Fri Jul 11 23:20:22 UTC 2008 _x86_64_ GNU/Linux
thats means your 64-bit.

You probably also remember which one you picked when you downloaded it.

edit:although personally I have 64-bit hardy and it worked no problem for me (just installed as firefox advised)

---

### Post by grcjman2008 on 2008-08-14
> **herteljt said:**
> Here are my two cents:

2) I would try the guide at this link [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

I've done that step by step to no avail. It never asks me if I want to install missing plug ins.  When I go to You Tube I get a black screen for a split second in the area where the video should play, then it just disappears and is blank.

> If you want to check and see if flash is installed open up Firefox and put the following into the address bar:

```
about:plugins
```

You should see Shockwave Flash and be able to read the version installed.

This is what I get:

    File name: libgnashplugin.so
    Shockwave Flash 8.0 r99. Gnash 0.8.2, the GNU Flash Player. Copyright © 2006, 2007, 2008

> 2) Are you running a 64-bit computer by chance?  I think the process is different for 64-bit.  Here are two links that may help (keep in mind this is only if you are running a 64-bit computer)

No, 32 bit.

> **okey666 said:**
> Just to clarify run:
Code:

uname -a

and see if it says more like:
Quote:
Linux Server 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux

This is what I get:

Linux greg-desktop 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux

---

### Post by Koheleth on 2008-08-17
Try another browser [www.opera.com](www.opera.com) install the package for Ubuntu and see what happens.  Then post back here.

---

### Post by sharks on 2008-08-17
a thread for noobs:
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

---

### Post by Sorivenul on 2008-08-17
> This is what I get:

File name: libgnashplugin.so
Shockwave Flash 8.0 r99. Gnash 0.8.2, the GNU Flash Player. Copyright © 2006, 2007, 2008

Looks like you have both GNASH and Flash installed.  This may be causing conflicts (I did this on my first Ubuntu install as well).  Try removing GNASH from your system and see what happens.  
```
sudo apt-get remove gnash
```

---

### Post by Okicombo on 2008-08-17
Thanks for the code Tamoneya!It worked pefectly. I am always looking for code to run in shell just to get used to it, and learn more about Linux.

---

### Post by hyper_ch on 2008-08-17
It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)

---

