---
title: "What's the best way to extract MAC address data from HOSTAPD"
date: 2015-11-02
forum: Programming Talk
---

### Post by mike381 on 2015-11-02
I'm an experienced developer (with microsoft technologies), but I'm struggling to figure some things out with Ubuntu on Raspberry Pi.  I'm working on an academic project with my son and we'd like to grab the MAC addresses from HOSTAPD communications.  We want to track how often someone attempts to join a publicly available wifi (which is to say. . . .  our test subjects are his sister and their friends).

I played around with FruityWifi and got some of it to work, but I couldn't figure out how to get the small slice of data that I was looking for.  I could see the log info (which was great), but I couldn't figure out where or how I could programatically extract what I needed..

I tried DarkStat and it never seemed to create the log files.

I tried using TCPDUMP, but I don't see the MAC address data of in-range devices in the output.  Only those of connected deviced (as far as I could tell).

The bigger problem is that I don't know what I don't know.  I'm a glutton for punishment, so I'll figure out whatever needs to be figured out, but It would be helpful to hear that I'm barking up the right tree and then continue my fight with Linux (new to me) and Python (new to me).  Any advice is greatly appreciated.

Does anyone have any ideas on an efficient and easy way to do this?  I don't need elegant. I just want to help my son with his science project.

---

