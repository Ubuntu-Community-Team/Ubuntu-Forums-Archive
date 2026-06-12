---
title: "Changing screensavers"
date: 2013-02-10
forum: New to Ubuntu
---

### Post by regice9 on 2013-02-10
Hello. I was wondering if you could change the settings and/or the actual default screensaver for Ubuntu (12.04)

---

### Post by Lucius Ferus on 2013-02-10
yes, just go to the settings manager and choose Desktop or appearance, go through the different folders an change whatever you want.

---

### Post by Frogs Hair on 2013-02-10
You may be interested in the link . [http://www.howtogeek.com/114027/how-to-add-screensavers-to-ubuntu-12.04/](http://www.howtogeek.com/114027/how-to-add-screensavers-to-ubuntu-12.04/)

---

### Post by GameX2 on 2013-02-10
EDIT: Crap, I typed for too long. XD

You can also try this:

```
sudo apt-get remove gnome-screensaver
```We want to remove the original screensaver manager to avoid a conflict.  Then we'll install Xscreensaver, which is more powerful (Well, the logo is ugly, but that's pretty much the only point I don't like):
```

sudo apt-get install xscreensaver xscreensaver-gl-extra xscreensaver-data-extra xscreensaver-screensaver-bsod
```If you want to, you can get additionnal cool screensavers by typing this (Make sure that Xscreensaver is not running.  If so, terminate the process):

```
sudo apt-get install rss-glx
```Navigate to /usr/bin/, and run the file: rss-glx_install.  That will copy the extras screensavers to the Xscreensaver directory.

Start Xscreensaver, configure it (You can set it to randomize screensavers if you want).
Next, we want to make Xscreensaver start at login.  Open "Startup Applications" and add this line for Xscreensaver:

```
xscreensaver -nosplash
```Last thing, set a customized shortcut to start the screensaver (Ctrl-Alt-L, Windows-L..) .  You might want to go to "Keyboard Options" or use Ubuntu Tweak, or Compiz-Config-Settings-Manager (CCSM) to do this.

Good luck. ;)  Enjoy!

---

### Post by regice9 on 2013-02-10
I understand this, and thank you, but there is one last question that I have. A couple of days ago, one of my friends showed me this really cool screensaver on his Windows laptop, and I was wondering if there was any way to convert it or something like that to run on ubuntu.

---

### Post by GameX2 on 2013-02-10
I've tested it and it work through Wine:

[http://www.ehow.com/how_7345498_convert-windows-screensaver-linux.html](http://www.ehow.com/how_7345498_convert-windows-screensaver-linux.html)
[http://wiki.winehq.org/ScreenSavers](http://wiki.winehq.org/ScreenSavers)

Basically, when Wine is installed, you'll need to run this from a terminal:

```
cd /navigate/to/folder
wine ./nameofscreensaver.scr /s
```The /S parameter turn it fullscreen.

I only tested it on a basic Windows XP screensaver, however.  Maybe that won't work with everyone.
Be aware that you'll need to make a script run at startup to activate the screensaver.

I'm no expert but I might suggest you put something like this in your startup applications (Creathe a Shell Script, in "Proprieties", make it executable "Allow execute this file as a program"):

```

#!/bin/bash
sleep 300
#300 seconds, for 5 minutes of wait time
cd /navigate/to/folder
wine ./nameofscreensaver.scr /s

```But to restart the script when the screensaver exit, I'm not sure, plese correct me..  Maybe the use of a GOTO will work (I'm guessing, this is a Windows command, maybe won't even work under Linux) ?

---

### Post by regice9 on 2013-02-10
> **GameX2 said:**
> I've tested it and it work through Wine:

[http://www.ehow.com/how_7345498_convert-windows-screensaver-linux.html](http://www.ehow.com/how_7345498_convert-windows-screensaver-linux.html)
[http://wiki.winehq.org/ScreenSavers](http://wiki.winehq.org/ScreenSavers)

Basically, when Wine is installed, you'll need to run this from a terminal:

```
cd /navigate/to/folder
wine ./nameofscreensaver.scr /s
```The /S parameter turn it fullscreen.

I only tested it on a basic Windows XP screensaver, however.  Maybe that won't work with everyone.
Be aware that you'll need to make a script run at startup to activate the screensaver.

I'm no expert but I might suggest you put something like this in your startup applications (Creathe a Shell Script, in "Proprieties", make it executable "Allow execute this file as a program"):

```

#!/bin/bash
sleep 300
#300 seconds, for 5 minutes of wait time
cd /navigate/to/folder
wine ./nameofscreensaver.scr /s

```But to restart the script when the screensaver exit, I'm not sure, plese correct me..  Maybe the use of a GOTO will work (I'm guessing, this is a Windows command, maybe won't even work under Linux) ?

The problem is, however, that somehow it is an .exe, not an .scr

---

### Post by GameX2 on 2013-02-10
> **regice9 said:**
> The problem is, however, that somehow it is an .exe, not an .scr

Oh, Wine does support EXE files, it's his main purpose.  It's made to open EXE files on Linux (Far from perfect, but pretty good).
Try it with Wine, we'll see.

I've read that a SCR is only an EXE with a modified extension (Maybe that's not true).

---

### Post by regice9 on 2013-02-10
Yeah, I've already tried with Wine, but when I do, all it does is just slow down my laptop, even after 30 minutes, and to stop it I have to restart.

---

