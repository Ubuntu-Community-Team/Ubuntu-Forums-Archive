---
title: "installing wusb100 driver"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by skywalkrNCSU on 2008-10-03
I am completely new to linux and ubuntu (just installed the latest version) and I am trying to install the driver for my usb wireless card.  I got ndiswrapper installed fine after a lot of trouble (like I said I am a total noob) but when I try to install my driver I get this error...

I type:

ndiswrapper -i rt2870.inf

and I get

couldn't open rt2870.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9
line 219

I figured the problem is where the file rt2870.inf is located but I could not find the directory /usr/sbin/ndiswrapper-1.9

I am just trying to get this installed so I can get on the internet with ubuntu so if you can help me out I would really appreciate it and please try to keep it as simple as you can.

---

### Post by anewguy on 2008-10-03
I don't know what threads you have read, but I'll try to give you some basics.

The first thing I would do is consider ndisgtk.  It is a GUI'd front-end to ndiswrapper and some newbies have better luck with that.

For ndiswrapper itself, follow the following:

(1) Log on via a terminal window

(2) make a new directory to hold your driver files:

mkdir mydriverfolder <enter>

(3) copy all of the .inf and .sys files for your driver to that folder:

cp {wherever the files are}/*.* mydriverfolder <enter>

(4) clear all drivers known to ndiswrapper:

sudo ndiswrapper -l <enter> That's a lower case "L" for list

if nothing is returned, go on to step (5)

for each thing listed in the output:

sudo ndiswrapper -e xxxxxxx <enter> Where xxxxxxx is one of the names returned in the list.

Repeat the above 2 steps until nothing is returned.

(5) cd mydriverfolder <enter>

(6) sudo ndiswrapper -i xxxxxx.inf <enter> Obviously, xxxxxx.inf should be replaced with the appropriate driver .inf file.

If this returns an error:

ls -al <enter>  Copy/paste the output from that back in a new reply here and don't continue.

(7) sudo depmod -a <enter>

(8/) sudo ndiswrapper -m <enter>

(9) cd /etc <enter>

(10) sudo gedit modules <enter>  This will call up an editor and open the file "modules" in that editor.

Go to the end of that file, then add a new line containing the following:

ndiswrapper

Now save the file, exit the editor and REBOOT.

(11)  click system/administration/network

(12)  see if the wireless section shows.  If so, be sure roaming mode is enabled.  If the wireless section doesn't show, post back here, but try the ending steps anyway.

(13) Click on the network manager icon (2 little terminals on the top bar) and see if it lists any wireless networks.

Dave :)

---

### Post by skywalkrNCSU on 2008-10-03
Thanks a lot dave I will give it a shot!

---

### Post by ralley4 on 2009-06-05
> **anewguy said:**
> I don't know what threads you have read, but I'll try to give you some basics.

...

Dave :)



I found this thread while trying to setup my wusb100 device. I followed these instructions, but I am not having any luck.

Since there is no indication as to the version anywhere on the device, I was unsure as to which to download, so I downloaded and tried them all. It looks like I have the drivers installed, but I am not sure how to configure the interface.


This is output using the v1 XP64 driver:

```
~/wusb100/v1_xp$ sudo ndiswrapper -l

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

rt2870 : driver installed
    device (1737:0070) present
```This is output using the v1 vista64 driver, which is the same as v2:


```
~/wusb100/v1_vista$ sudo ndiswrapper -l

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

netr28ux : driver installed
    device (1737:0070) present
```In all cases, I have a new Unknown Interface (pan0) listed under Network Tools. I am not sure what to do from here. Any help would be greatly appreciated!

2009-06-07 Update:

I found a native driver that works great. The link is posted below:
[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

---

