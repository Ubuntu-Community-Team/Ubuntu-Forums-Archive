---
title: "Can I get a do-over?"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by bob234 on 2008-04-25
Hi, newbie here. I have an intel celeron i386 PC dual boot Gutsy 7.1 w/Vista. And an RTL8185 wireless PCI card that doesn't work.
I've spent the past three weeks(part time) installing and uninstalling various ndiswrappers, windows drivers and network managers.I've blacklisted extra drivers, and tried to compile the linux driver from source, which didn't work-I think.
Now I've tried to put everything back the way it was and I can't find wlan0 anywhere. Also the page where I blacklisted the extra driver is blank now. (however it shows up when I list them.)
This is a test computer and there is no data on it. I need to know if this PCI card will work with gutsy before I install it in any of my other machines.
Is there any way I can restore Gutsy to It's original configuration so I can start fresh. I have the disk I made when I downloaded it.
Sorry I can't be more specific at this time, the machine in question is at work and I won't have access to it until after the weekend. I'll be able to post some screenshots of terminal then.
Thanks in advance; Bob.

---

### Post by Paqman on 2008-04-25
> **bob234 said:**
> 
Is there any way I can restore Gutsy to It's original configuration so I can start fresh.

Just run the installer again. Since you don't need to change any partitions it should be pretty quick.

---

### Post by nickpaton on 2008-04-25
Checking a couple of threads, and it seems that people are using the win98 drivers to get the card going.

Have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=491680") and especially the last post for the actual driver.

A useful general post for compatible cards can be seen [here]("http://linux-wless.passys.nl/")

Welcome to the forums and Ubuntu

---

### Post by jimv on 2008-04-25
I have a 8185 card in my laptop, and I've been using ndiswrapper and some xp drivers to get it to work.

Here's a post on my blog about how I got it to work:

[http://jimvernon.com/archives/53](http://jimvernon.com/archives/53)

---

### Post by bob234 on 2008-04-28
Was not able to get the installer to run again in 7.1. Downloaded and burned to cd 8.04, couldn't get that to install. Downloaded 8.04 using update function, now using Ubuntu Hardy. Still no wlan0.
Page for blacklisting drivers has returned, (gksu gedit /etc/modprobe.d/blacklist). Network Tools only shows modem and etho options.
Whwn I type lshw -C network in terminal /home/bob/Documents/lshw -C network.pngit says NETWORK UNCLAIMED (see screenshot)
I should add that I'm presently connected to the internet using a wireless access point with my ethernet connection.

---

### Post by Joeb454 on 2008-04-28
try opening a terminal and doing ```
iwconfig
``` and then post the output back here :) It will tell us what your wireless interface is called (mine was eth0 once)

---

### Post by bob234 on 2008-04-28
I typed iwconfig in terminal and this is what I got.

---

### Post by bob234 on 2008-04-28
I fixed it. I went to sudo gedit /etc/network/interfaces and removed the hash marks in front of the three lines on the middle left of the page. I must have added them when I typed in the code not realizing the were part of the prompt in one of the many sets of instructions I was following. Thanks for your help, now I can get rid of the Wireless Access Point on my desk so it's not so obvious that I have an internet connection.
My next task is to find a driver for my scanner, but that can wait until tomorrow in a new thread.Thanks, Bob.

---

