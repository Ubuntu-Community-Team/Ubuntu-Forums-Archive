---
title: "[SOLVED] How to edit Motion's config file"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by Motion_Noob on 2008-11-24
I downloaded Motion from here: [http://packages.ubuntu.com/intrepid/graphics/motion](http://packages.ubuntu.com/intrepid/graphics/motion)  , and installed it, ffmpeg, and mysql-client (and all of the packages that GDebi Package Installer told me were required dependencies) on the Intrepid Ibex version of Ubuntu (8.10).

After having installed all these packages, I would like to edit the Config file options of Motion, which are listed here: [http://www.lavrsen.dk/twiki/bin/view/Motion/ConfigFileOptions](http://www.lavrsen.dk/twiki/bin/view/Motion/ConfigFileOptions) .

But I'm a noob, and I have the following questions:

1.) When I try to open the motion.conf file (that I find in File System | Etc | Motion) using Text Editor, I get the following error: "Could not open the file /etc/motion/motioni.conf  - You do not have the permissions necessary to open the file."

I have only one user account (that I know of) on this machine, and I'm logged on with it. How can I edit this file?

2.) Do I really want to edit the motion.conf file (with Text Editor, for instance), to effectuate the changes I want (changes to options like 'ffmpeg_timelapse' and 'area_detect') ? Or is the proper method of making these changes to (re-)run the Make command?

(I didn't run a Make command, as far as I know, since I didn't compile the source code, but rather downloaded and installed several packages.)

AFAIK, Motion is a command line only program, with no GUI. Even though I've been using Ubuntu's default GUI to install all the necessary packages, I assume that from here on, I'll have to use a terminal window to do anything/everything with Motion.

Thanks for you help.

---

### Post by DieB on 2008-11-24
for 1) use : > sudo gedit path-to-file

sudo grants you superuser/admin power.

in unix and linux it is common way to have a root user and normal users, ubuntu changed it - to fight [bug #1]("https://bugs.launchpad.net/ubuntu/+bug/1") - to sudo.

more you can fin here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

hope that is an answer

p.s.: if it is a command line programm you will need to run it in a terminal.
for help use "man name-of-program" in a terminal

---

