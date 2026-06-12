---
title: "Getting Wireless Going - I think I'm Halfway There"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by sp1derman on 2008-09-27
Hey,

I have a Dell Inspiron 1525. I have a Broadcom BCM4328 802.11a/b/g/n (rev 03)

I had to install ndiswrapper to get my wireless going and I did. The driver shows as installed and after I first got everything finish I was able to detect all the wireless networks in my area and connect to one of them (but not my own). I restarted ubuntu and then when I went back to the Network Manager Icon in the top right corner of the screen and click it as I did before there are no longer any available networks listed. A left click gives me the option of Manual Configuration and a right click gives me the choice to enable or disable networking, edit wireless Networks with "connection information" greyed out.

When I go through System->Administration->Network my wireless connection is listed as "Black And White" which is the name of my network but I still don't have any wireless connectivity.

This is very confusing for me. The most confusing part is that originally, when I could see listed networks, I could attempt to connect to "Black And White" and was unable to because my key didn't work,but it works fine in windows.

Anyways...I'd really like to be able to get those wireless networks back listed in the Network Manager shortcut...I'm not sure if anyone can help with any of this but  I'd appreciate any that anyone can offer.



**I'm currently plugged into directly..

---

### Post by DapperMe17 on 2008-09-27
Spidy,

Built-in Broadcom chips are tricky, even more so with Hardy.

First, I suggest that you uninstall network-manager & go with Wicd.

Sometimes, Wicd can make "miracles" happen.


I suspect that if you're running Hardy, that this "might" be related to the "ssb" bug. 

I've installed Ubuntu on a BCM4306 & have had luck with [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Especially, the part at the bottom that describes the "Hardy bug".

---

