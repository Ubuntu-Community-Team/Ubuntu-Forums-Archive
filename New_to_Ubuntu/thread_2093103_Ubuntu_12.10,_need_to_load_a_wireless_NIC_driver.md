---
title: "Ubuntu 12.10, need to load a wireless NIC driver"
date: 2012-12-09
forum: New to Ubuntu
---

### Post by thasatelliteguy on 2012-12-09
I hate to go off on a rant this early in the game, but come on people! You all think that Linux is the 'superior' OS, but it's so complex that no one can figure it out. I have tried to make the switch to Linux several times and have been thwarted every time... usually by drivers. Once again, here we go... I just loaded ubuntu 12.10 and I need to load a wireless NIC driver. The instructions seem straightforward enough, but then the menus in the guide aren't there, then there's a guide to get the menus to appear, but half the stuff in that guide are missing too. And the worst part is that since I'm still a noob, I don't have any idea what to even ask to get any help, cuz I have no reference point. I can't even tell you with any certainty what 'desktop' or 'shell' Im running. 

Could someone PLEASE help me out and get me headed in the right direction...

---

### Post by oldos2er on 2012-12-09
Post moved to its own thread. It would help if you mention which wireless device you need drivers for.

---

### Post by thasatelliteguy on 2012-12-09
OK. It's a WNDA3100 Netgear. But once again, that's not directly my problem. I have the extracted windows drivers already.  (Unless there's an easier way now) I need into the Administration menu. Or if that doesn't exist anymore, how do I even load a driver? This 'beautiful new interface' is so wonderful, I can't even figure out where I can look at an installed device?? I'm assuming the menu I'm looking for is along the lines of a "Device Manager" as far as function. So where the @#$% is it????????????

In case you haven't noticed, after 3 days of simply trying to load a damn driver, I'm EXRETEMLY FRUSTRATED and I'm about ready to spend my $39 on Win8Pro, cuz I'm tired of this BS already....

---

### Post by squakie on 2012-12-10
You attitude makes it appear you already made up your mind.  If not, patience is a virtue you need here.  This is all voluntary, and if you are completely new to linux you need to "turn off" the windows hat and start making a new one with linux.  There will be a lot of learning to do.

For example,  if it's a usb device:

lsusb

If it's a PCI device:

lspci

To find more information on your network adapters:

iwconfig

or 

ifconfig


A search of the forum using:

WNDA3100

in the search string.

A search of the internet using:

ubuntu <your release here> wnda3100

These things often turn up multiple posts.  A lot of us use these functions ourselves when trying to solve problems.

So, maybe try a little of that, see what you find, then post back what you find, what you don't find, and what you have questions on.

As an example, not being familiar with this adapter, I did a net search and found it is a dual-band n USB wireless adapter.

I also found many posts, including this how-to:

[http://www.iheartubuntu.com/2010/10/netgear-wnda3100-usb-in-ubuntu.html](http://www.iheartubuntu.com/2010/10/netgear-wnda3100-usb-in-ubuntu.html)

This particular how-to is using ndiswrapper.  If indeed it is needed to make this work it would be the exception to the rule.  It's also for an old release of ubuntu - something you have to watch out for.  A newer thread is here:

[http://ubuntuforums.org/showthread.php?t=1965989](http://ubuntuforums.org/showthread.php?t=1965989)

So, post back the output of:

lsusb

while you have the device plugged in.  The xxxx:yyyy string that appears on the line with the wireless adapter will identify the manufacturer and product of the chipset used.  knowing the chipset is the first step in getting a driver.

All of those commands are entered via a terminal window (ctrl/at/t).

It always pays to do some homework.  It also pays to try to watch the language and attitude when posting here - as the saying goes, you'll catch more flies with honey, not vinegar.

EDIT:  Addition:  forgot to mention, *if* you use ndiswrapper, the version of ubuntu (32 or 64 bit) requires the corresponding Windows XP driver (32 bit for 32-bit Ubuntu, 64-bit for 64-bit ubuntu).  You can't mix the architectures.

---

### Post by 3rdalbum on 2012-12-10
> **thasatelliteguy said:**
> I hate to go off on a rant this early in the game, but come on people! You all think that Linux is the 'superior' OS, but it's so complex that no one can figure it out. I have tried to make the switch to Linux several times and have been thwarted every time... usually by drivers. Once again, here we go... I just loaded ubuntu 12.10 and I need to load a wireless NIC driver. The instructions seem straightforward enough, but then the menus in the guide aren't there, then there's a guide to get the menus to appear, but half the stuff in that guide are missing too.

Ubuntu moves very quickly. If the guide you're using refers to things that aren't on your screen, then you're using too old a guide. Not only will it not work, but it may even break your system. Find a guide for 12.10.

Or, better option: Spend a little money and buy a wifi card that works out-of-the-box with Ubuntu. It looks like your particular card has been troublesome for years and the situation there probably won't get better.

I've bought two laptops with supported out-of-the-box wifi, a desktop with the same, one wifi stick supported out-of-the-box and two USB wifi devices that needed only a single line added to a file on 11.10, and works out-of-the-box on 12.04 and later. There are heaps of trouble-free wifi cards out there, take a look and invest the money into your sanity :-)

---

### Post by Bucky Ball on 2012-12-10
Yep, take a deeeep breath, a brain turn 15 degrees from Windows, and start the learning curve. Things are a lot different now. 

Please provide more info anyways. With the dongle plugged in, please post the output from a terminal of these two commands, one at a time:

```
lsusb
sudo lshw -C network

```Also, with it plugged in, have you done an update then checked 'Additional Drivers'?

(Just a note: ndiswrapper is almost a thing of the past, largely superseded and mainly used for cards of the past. Lots and lots of cheap wifi dongles work out of the box now.)

---

