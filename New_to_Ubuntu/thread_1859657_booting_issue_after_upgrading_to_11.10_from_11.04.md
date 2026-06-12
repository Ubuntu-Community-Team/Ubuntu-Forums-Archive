---
title: "booting issue after upgrading to 11.10 from 11.04"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by indyeah on 2011-10-14
Hi Guys,

This morning i upgraded from 11.04 to 11.10 through update manager.When i try to boot into ubuntu (dual boot with windows 7) i get ubuntu purple screen with "waiting for network configuration" and then "waiting 60 seconds more for network configuration" and then blank screen and thats it.I tried booting into safe mode and tried updating grub,updating broken packages and when i click on boot into normal mode it shows booting ubuntu without proper network configuration and then remains like that till i manually click on shut down button.

Any help will be appreciated.I dont wana do clean re install of 11.10.

---

### Post by lwaaleboer on 2011-10-14
> **indyeah said:**
> Hi Guys,

This morning i upgraded from 11.04 to 11.10 through update manager.When i try to boot into ubuntu (dual boot with windows 7) i get ubuntu purple screen with "waiting for network connection" and then "waiting 60 seconds more for network connection" and then blank screen and thats it.I tried booting into safe mode and tried updating grub,updating broken packages and when i click on boot into normal mode it shows error like modem failure and then same waiting for network connection.

Any help will be appreciated.I dont wana do clean re install of 11.10.

Yep, got the same problem.:sad:

---

### Post by indyeah on 2011-10-14
I updated my original post to show the actual message i get while booting into ubuntu 11.10.....I have LiveCD with me just in case i need to reinstall.But before that i want your help to atleast disable this netowrk configuration message so i can boot into 11.10.

Waiting for some tips and help.

bumpety bump :(

---

### Post by petzoldf on 2011-10-14
[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441)

Post #24 works perfect to resolve the problem

---

### Post by indyeah on 2011-10-14
> **petzoldf said:**
> [https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441)

Post #24 works perfect to resolve the problem

Thanks for the update i already read that.

I am marking this thread as solved as i re-installed 11.10

---

### Post by mark.0 on 2011-10-22
> **petzoldf said:**
> [https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441)

Post #24 works perfect to resolve the problem

ctrl+alt+f1 does nothing for me and it still just sits there. How else can I access the file system to make these changes?

EDIT: I ended up getting to it through recovery console. but this "fix" broke my system. Boots okay now, but when ubuntu loads incorectly when I log in as a user I just see a file menubar with the options from nautilus and the background image.... THATS IT. Thanks for breaking my system further :) Looks like a clean install is a must.

---

### Post by revnoah on 2012-07-07
I also ended up having this problem. Fortunately, I had just performed a very recent full backup so I just ended up reinstalling Ubuntu with 12.04.

One thing that was interesting in my case is that my modem and router got zapped in a storm and I was without internet for awhile. I had tethered my phone to the PC when I was looking up some info online and the problem occurred after I disconnected the USB device and tried to connected via ethernet to my modem. I'm not sure how relevant any of this though there may be some correlation in the events.

---

### Post by Rockstarever on 2012-12-18
ok i think this should solve our problem. go to terminal and type [PHP]sudo nano /etc/network/interfaces
[/PHP]
now delete what ever there is and just enter the following 

auto lo
iface lo inet loopback

press ctrl+x and enter. 

what you done here is just edited your network interface settings. this will no more bring up the "waiting for network configuration message" and you would be able to boot normally. good luck. post if it helped. and put up the question to solved.


also check out my post [http://ubuntuforums.org/showthread.php?p=12416542#post12416542]("http://ubuntuforums.org/showthread.php?p=12416542#post12416542")

---

