---
title: "Blank screen with mouse pointer"
date: 2017-10-13
forum: New to Ubuntu
---

### Post by candle2 on 2017-10-13
Hi, ive been using lubuntu for about six months and im pretty new to linux. 

I recently downloaded too many gamed on the gnome software center and filled the.hard drive to 0 bytes free space.

I shut it down, I get the log in, I enter the password, it keeps looping back. I finally figure out how to.boot to terminal, on my machine press esc at dell logo, recovery mode, drop to root.

Took me a very long time to.figure out how to cd .. Then cd home etc, but eventually foind my way out of root and deleted a bunch of music and videos. A lot of files. Also ran "try to make free space" from grub recovery menu wgich deleted old versions of the OS and freed 1000 MBs.

ive had to run manual fsck quite a few times during this process of trying stuff and rebooting.

Now im still stuck on blank screen after logging in. no icons etc. I have a mouse pointer. I keep rebooting into terminal and deleting stuff. Cant find the games directory.

Any suggestions? Is it still a lack of free space causing this? I suspect fsck changed too many things? I dont know what im doing and I miss that GUI.

Lubuntu LTS drll inspiron

THANK YOU SO MUCH FOR YR HELP

---

### Post by mörgæs on 2017-10-14
Does the command **startx** open the GUI?

---

### Post by inerstellar-cowboy on 2017-10-17
Good for you taking those first steps!

how much space are you working with on your system? I am a noob myself, but I've been around long enough to crash my system once or twice

A simple solution might be to backup what you need, documents, pictures, etc. and fresh install lubuntu (or another lightweight distro suited to your system)

---

### Post by candle2 on 2017-10-22
how do you check free space from root terminal? startx does not work. I'm still deleting stuff, is this going to solve it? does anyone else have some advice? lubuntu 16 LTS on dell Inspiron. is it possible to access a USB hard drive in recovery mode from drop to root prompt? would hate to reinstall, it was very difficult for me.

---

### Post by mörgæs on 2017-10-22
Please run **df -i** and **df -hi** and post the results in CODE tags.

---

