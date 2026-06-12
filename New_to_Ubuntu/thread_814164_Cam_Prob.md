---
title: "Cam Prob"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by londonlad on 2008-05-31
hi guys,

i have a CREATIVE VISTA IM WEBCAM, & i cant seem to get it to work, help please..........serious n00b here!

---

### Post by RudolfMDLT on 2008-05-31
Hi,

Give [this table]("http://opensource.creative.com/webcam.html") a look through, it might help. If you get stuck or you still can't get it working I'll try my best to help you get it working! I had some troubles getting my Logitech to work a couple of years ago! :)

Goodluck,

Rudolf

---

### Post by londonlad on 2008-05-31
i have a VF0260 cam, but i really aint gotta clue what to do next! :(

---

### Post by londonlad on 2008-05-31
hhheeelllppp................:(

---

### Post by cariboo on 2008-05-31
Give this link a try:

[http://ubuntuforums.org/showthread.php?t=744991](http://ubuntuforums.org/showthread.php?t=744991)

Jim

---

### Post by scottslinux on 2008-05-31
I went through a long list of web cams and found that the quickcam communicate STX works very well with ubuntu out of the box.  It works with camorama, skype and cheese.  If you are tired of trying to make cameras just invest a few dollars in this and you will have a working webcam.  This camera is avail currently in stores.

Good Luck
Scott

---

### Post by londonlad on 2008-05-31
> **cariboo907 said:**
> Give this link a try:

[http://ubuntuforums.org/showthread.php?t=744991](http://ubuntuforums.org/showthread.php?t=744991)

Jim

*i dont understand **ANY** of that! :(

---

### Post by Prospero2006 on 2008-05-31
Try this:

```

apt-get install webcam-server

```

It requires you also run apache, and you have to copy a couple of applets from /usr/share/doc/webcam-server/applet/ to /var/www.

You'll have to get in and edit the applet file, but it does work with my cheap-o creative webcam.

---

### Post by RudolfMDLT on 2008-06-01
LOL - Just went through those instructions! Okay,

You need to install some extra stuff and the hopefully we can get this working. Copy and paste the commands quoted and then follow the instruction that I pasted below. If you get stuck, post back!

> sudo apt-get install build-essential
copy and paste that in the terminal.

>   [B]Install debian module package
[/B]
First, see Ov51xJpegHackedSource for how to add the correct sources to your sources.list

A quick way to build the module is to issue those commands

[QUOTE]sudo apt-get update
sudo apt-get install ov51x-jpeg-source module-assistant
sudo module-assistant a-i ov51x-jpeg 

If this fails first try the same with -t to look at log:

> module-assistant -t a-i ov51x-jpeg 

And then read more documentation on module-assistant.

If then you still think it comes from the package, please mail the issue to [email]ov51x-jpeg@rastageeks.org[/email]

If everything worked so far, then you have a working module installed... You may simply unplug/plug the webcam, or modprobe ov51x-jpeg to see it working ! [/QUOTE] 

Goodluck,

Rudolf

---

### Post by londonlad on 2008-06-01
dont understand **any** of that! :(

---

### Post by RudolfMDLT on 2008-06-03
Sorry for only getting back to you now - Final exams are insane!

The bold stuff below are linux commands.
sudo - Puts you in SuperUser mode
apt-get - a text base program like Synaptic that installs packages 
install - a command that tells apt-get what to do
build-essential - a package that I believe you will need to compile and use your drivers.

You need to open up the terminal(Look under the Applications menu) and copy and paste them into the terminal, one by one. CTRL+V
doesn't work in the terminal, you have to say CTRL+SHIFT+V to paste the commands or righclick and say "paste".

> **sudo apt-get install build-essential**


[B]sudo apt-get update
sudo apt-get install ov51x-jpeg-source module-assistant
sudo module-assistant a-i ov51x-jpeg[/B]

If this fails first try the same with -t to look at log:
[COLOR="Blue"]a Hook is just something you add to modify a command or tell a program how to do something.[/COLOR]

**module-assistant -t a-i ov51x-jpeg**

I hope this clears up some stuff.

---

