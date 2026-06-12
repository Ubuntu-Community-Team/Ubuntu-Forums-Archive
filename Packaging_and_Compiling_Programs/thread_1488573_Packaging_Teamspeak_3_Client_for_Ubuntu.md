---
title: "Packaging Teamspeak 3 Client for Ubuntu"
date: 2010-05-20
forum: Packaging and Compiling Programs
---

### Post by MunkyJunky on 2010-05-20
Hey everyone - 

I'm interested in packaging the Teamspeak 3 client up for Ubuntu Lucid, since no-one else seems to have done this yet. However, I haven't done any packaging before, so I'm getting a little confused as to what's applicable in the Packaging Guide - the Teamspeak 3 client comes as a .run file, which unpacks a .sh file. 

I'm just getting a little confused as to how I go about converting a .sh file into a .deb - any information on how to would be great, from "good articles to IRC channels where I can get some help. 

Cheers, 
MunkyJunky

---

### Post by SevenMachines on 2010-05-20
hi there. It looks like teamspeak is a closed commercial license of some sort and source code isnt available, only a pre-built binary. this makes is very problematic and I really couldnt recommend you attempt to try to package it, especially if you're relatively new to packaging. If it is possible, its likely to be difficult, and you would need to go over its license to see if that was even allowed.

---

### Post by SevenMachines on 2010-05-20
for irc you might want to try ubuntu-motu, they know about this stuff

---

### Post by MunkyJunky on 2010-05-20
Thanks for the reply - 

Basically, a few hours after posting this I realised I've been going about it the wrong way. The idea behind what I want to do is create a .deb file that a user can download and run, which will then install the Teamspeak 3 client and create menu items for it, since the installer from their website only creates a runnabel script to start Teamspeak. 

Before I even started thinking about this (3 weeks ago) I asked the Teamspeak developers ([http://forum.teamspeak.com/showthread.php?t=54010](http://forum.teamspeak.com/showthread.php?t=54010)) and they said as long as I don't modify the binary package, and their licence is displayed, it's all good. 

What I'm actually looking to do is essentially "wrap up" the teamspeak .run file & my .sh file into a single .deb file, which, upon installation, runs the .sh script (which in turn installs the .run file, and creates menu items).

---

### Post by SevenMachines on 2010-05-21
unfortunately this kind of thing touches a lot of policy and licensing things that are out of my pay grade so i can't really be of too much help, hopefully someone else knows more and can. 
You could take a look at nvidia-current packaging or something like googleearth-package as these deal with this kind of situation, i think nvidia-current includes sh files whereas googleearth-package deals with 'wrapping' a sh install file, maybe thats the simpler way. 
I imagine some sort of unpacking of the .sh file in debian/rules, some sort of .preinst script to handle the licensing display, and a debian/install file to place the files in the right places would work. But then you also have the problem of what to do with the prebuilt binaries it uses (libqt?), best to use the libqt system wide installation, but then you have the problem of using qt libraries most likely different to the ones teamspeak has been built against. As I say, questions of policy and best practice in those sorts of situations are a little beyond me

---

