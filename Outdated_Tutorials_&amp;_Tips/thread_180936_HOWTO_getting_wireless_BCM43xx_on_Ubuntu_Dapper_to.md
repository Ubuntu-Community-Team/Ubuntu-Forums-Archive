---
title: "HOWTO: getting wireless BCM43xx on Ubuntu Dapper to work."
date: 2006-05-23
forum: Outdated Tutorials &amp; Tips
---

### Post by imrumpf on 2006-05-23
I was constantly having trouble with this BCM43xx wireless card which is in my Compaq V5105CA laptop. I tried everything under the moon to get it working, and even ndiswrapper didn't seem to fix it fully. But I have now found a solution which works for me and I'd like to share it with others. 

The easiest way to install the Broadcom43xx drivers in Dapper is to execute a script that has already been written for this purpose. Before you execute the script, you'll need to install the bcm43xx-fwcutter package. (Note: You must be connected to the internet in order for apt-get and the script to work properly.) 
  ```
sudo apt-get install bcm43xx-fwcutter
sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh 

``` This has worked wonders for me, no ndiswrapper AND my wireless network light works now. 

Quick question to those who use this tutorial.....anybody know of a way to toggle the wireless network light on and off? currently it is on 24/7 and I'd like to find a way to turn it off via the button.

For more of an in-depth explanation, visit this [link]("https://wiki.ubuntu.com/WifiDocs/Driver/Broadcom43xx"). These instructions came directly from he Ubuntu Wiki, but looking at the nummber of problems in these forums with this chipset of wireless cards, most people do not know about it yet.

---

### Post by xXx 0wn3d xXx on 2006-05-23
Here's how to get ndiswrapper to work:

> sudo apt-get install ndiswrapper-utils

now type:

> sudo nano /etc/modules

add "ndiswrapper" to a blank line -- no quotes

now edit:

> sudo nano /etc/modprobe.d/blacklist

and add "blacklist bcm43xx"

Now edit /etc/iftab

> sudo nano /etc/iftab

and change (wireless cards are usually eth1) eth1 to wlan0

Your almost done:

> sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
sudo ndiswrapper -m
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile

To start ndiswrapper:

> sudo modprobe ndiswrapper

Configure your card under System > Administration > Networking.

Now comment out eth0 (your ethernet if you were using it)

> sudo gedit /etc/network/interfaces

and comment # out any eth1 lines. Leave lo or loopback interface as it is.

Note: you will need the firmware for your card.

---

### Post by MetalMusicAddict on 2006-05-23
Which method will give a faster connection? Using the native driver it seems slower than ndiswrapper under Breezy.

---

### Post by benzete on 2006-08-31
Console hangs at "bash: $conffile: ambiguous redirect" when i try the cat $conffile command.  Any ideas?

---

### Post by trubblemaker on 2006-10-17
nevermind the radio state thing it's a really old bug that was fixed ages ago, it's not necessary to set the radio state.

---

