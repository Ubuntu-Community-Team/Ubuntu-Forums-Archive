---
title: "Svgalib on startup with a bash script??? HELP!!"
date: 2008-07-05
forum: Programming Talk
---

### Post by jesushero on 2008-07-05
I'm trying to get xmame.svgalib (the svgalib version of mame arcade emulator) to run on boot so as to get a computer setup as a dedicated mame-box.. 

I've tried a few different scripts on /etc/rc.local 

1) I've tried the raw command:

/usr/games/xmame.svgalib -ef 1 

(the -ef 1 is a video effect) 

It runs as root with no problems. However, since it runs as root, it has problems reading and writing the config, history and hi-score files which are normally based in the home directory of the user that runs mame. 

2) Tried su:

su - arcade -c "/usr/games/xmame.svgalib -ef 1"

This starts as desired (starts loading xmame.svgalib as user arcade using the environment of user arcade and /home/arcade as the home directory. However, it fails to run after the file loading due to the following error:

svgalib: can't open /dev/tty0

(I assume this has to do with groups, owners and permissions, since user arcade does not have adequate permissions to access a different tty and initialize a different display mode with svgalib... I've tampered with these settings but nothing worked so far!)

3) Tried rungetty

/sbin/rungetty -u arcade -w /home/arcade /dev/tty0 "/usr/games/xmame.svgalib -ef 1"

This seems to run but doesn't do anything and returns no error messages. Tried running the same command logged in as root, and did nothing! 


So, any help would be greatly appreciated!! I actually need to learn how to make dedicated machines for different kinds of applications (mostly artistic) using startup scripts.. I thought the mame project would be a fun and good starting point!!

---

### Post by geirha on 2008-07-05
Try adding the rungetty to /etc/inittab instead of /etc/rc.local. Look at the examples in the man-page. Have it run on tty1.

---

