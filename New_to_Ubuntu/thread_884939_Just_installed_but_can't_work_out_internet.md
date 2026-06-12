---
title: "Just installed but can't work out internet"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by Ian dewhurst on 2008-08-09
Hello, 

I am a bit of a n00b to ubuntu but not to computers and decided to jump from microsoft xp to ubuntu after a bit of research and use of the virtual computer.
Anyway after partitioning my HD and then installing ubuntu (using a dual boot with xp)
I can't get my damn internet to work. I have searched on google and on here (very useful) I have become confused about how to set up my internet.
I use a laptop with a usb netgear wireless adaptor and want to join the network (mums computer)it is protected by WEP and don't know where to start and how to connect, I will also need to persuade her boyfriend who set it up for the WEP pass.

Thankyou all in advance.

---

### Post by anewguy on 2008-08-09
Start by giving us the model, etc., details of the adaptor.  We can try to go from there.  :)

---

### Post by Ian dewhurst on 2008-08-09
Oh poo yes that would have been helpful, its a netgear wpn111 usb adaptor.

---

### Post by 7raTEYdCql on 2008-08-09
if you are connected via pppoe then use the 
```
sudo pppoeconf 
```

then follow the rest as usual

---

### Post by Ian dewhurst on 2008-08-09
I feel like a bit of a tool for asking but where do I enter this?

---

### Post by carandraug on 2008-08-09
In the terminal.

Go to the top menu named applications, and then under accessories search for Terminal.

---

### Post by Ian dewhurst on 2008-08-09
Cheers shall give that a bash!

---

### Post by Ian dewhurst on 2008-08-10
Have tried a few times now but I keep getting this message:

>  Sorry I scanned 1 interface but the acess concentrator of your provider did not respond. Please check your network and mode cables. Another reason for the fail scan may also be another running which controls the codes 

That is the message but not word for word unfortunately.

---

### Post by Joeb454 on 2008-08-10
Do you have the option for connecting to a wireless network?

---

### Post by Ian dewhurst on 2008-08-10
I am not sure, where would one check this?

---

### Post by Joeb454 on 2008-08-10
There should be an option at the top right of your screen

---

### Post by Ian dewhurst on 2008-08-10
Is this the networking icon, if it is it did only giv me two options and wireless was not one of them.

---

### Post by Ian dewhurst on 2008-08-10
I have tried this guide but don't know whether it is any use as I use a USB

[https://help.ubuntu.com/8.04/internet/C/troubleshooting.html#troubleshooting-driver](https://help.ubuntu.com/8.04/internet/C/troubleshooting.html#troubleshooting-driver)
I can't check for hardware information as it is not installed and I can't install it as it wants to refresh the page and it needs the interent to do this.

I am really starting to loose heart with this:confused:

---

### Post by epiphonygirl on 2008-08-10
Please don't give up, stick with it...trust me its worth it from the volumes of information you learn.  I have a Lenovo R61e Thinkpad that has the worst chipset imaginable to get to connect to wireless and it took me about two weeks and a lot of help to connect, but it happened! :D Mine was a PCI card tho so it won't help you a lot.
Option one:
If your laptop has an ethernet port you should try to connect directly to the router and update that way as well as search for proprietary drivers.
Option 2:
You said that you have a dual boot with Windows, correct? Well one way to get around that issue is to install the usb card in windows and then check the device manager to get its specs that way. You could then download ndiswrapper and the windows drivers for your card, put them on a flash drive and install them that way...if that works better for you.

---

### Post by Crafty Kisses on 2008-08-10
> **epiphonygirl said:**
> Please don't give up, stick with it...trust me its worth it from the volumes of information you learn.  I have a Lenovo R61e Thinkpad that has the worst chipset imaginable to get to connect to wireless and it took me about two weeks and a lot of help to connect, but it happened! :D Mine was a PCI card tho so it won't help you a lot.
Option one:
If your laptop has an ethernet port you should try to connect directly to the router and update that way as well as search for proprietary drivers.
Option 2:
You said that you have a dual boot with Windows, correct? Well one way to get around that issue is to install the usb card in windows and then check the device manager to get its specs that way. You could then download ndiswrapper and the windows drivers for your card, put them on a flash drive and install them that way...if that works better for you.
Yeah, but you also have to realize Linux is not for everyone, if he doesn't have the patience to work out problems then Linux definitely is not for this person.

---

### Post by Ian dewhurst on 2008-08-10
> **epiphonygirl said:**
> Please don't give up, stick with it...trust me its worth it from the volumes of information you learn.  I have a Lenovo R61e Thinkpad that has the worst chipset imaginable to get to connect to wireless and it took me about two weeks and a lot of help to connect, but it happened! :D Mine was a PCI card tho so it won't help you a lot.
Option one:
If your laptop has an ethernet port you should try to connect directly to the router and update that way as well as search for proprietary drivers.
Option 2:
You said that you have a dual boot with Windows, correct? Well one way to get around that issue is to install the usb card in windows and then check the device manager to get its specs that way. You could then download ndiswrapper and the windows drivers for your card, put them on a flash drive and install them that way...if that works better for you.

Good thinking catwoman will try tommorow, I think I do have to patience to stick with it, I own a classic mini lol!

With anything though you loose heart try again another day and attempt to get somewhere, it did also not recognise my ip and the device itself doesn't flash I wonder if it is turned on *ponders on a reboot*

---

### Post by anewguy on 2008-08-10
Indeed, as already mentioned, you want to install the drivers using ndiswrapper.  Be sure you use the XP (not Vista) drivers.  You should have a .inf and at least 1 .sys file.  You can probably copy these right off your Windows partition to your Ubuntu desktop (or other folder) just by opening the browser ("Places").  Once you've done that, if you need specific instructions, post back here and we'll give you step-by-step (you may want to search the forum first, as there are MANY posts describing how to use ndiswrapper).

Sorry it took so long to get back here - been rather busy. :)

---

### Post by Ian dewhurst on 2008-08-11
I have managed to get the driver files for the usb device, but am still struggling trying to transfer the ndiswrapper files.

I found a good couple of guides on here and was wondering how to transfer them from XP to ubuntu so I:

a; don't have to keep re-booting to xp to read the guide
b; don't have to write it down it is pretty lenghty.

I have had a look at ubuntu's version of MS office and was happy to see that it supported .doc files to save in so my question is can I open .doc files to view in ubuntu?

Here are the guides I would like to view in ubuntu to try and get it working:

[http://ubuntuforums.org/showthread.php?t=652910&highlight=wpn111](http://ubuntuforums.org/showthread.php?t=652910&highlight=wpn111)

[http://ubuntuforums.org/showthread.php?t=844856&highlight=wpn111](http://ubuntuforums.org/showthread.php?t=844856&highlight=wpn111)

---

### Post by cgkades on 2008-08-11
[removed my own stupidity]

---

### Post by halitech on 2008-08-11
Ubuntu doesn't have a version of MS office, it has Open Office (or Star Office or KOffice) but no MS Office. It will certainly open .doc files as I do that all the time. Can even open .pps and excel spreadsheets

---

### Post by Ian dewhurst on 2008-08-11
Thankyou all for being so patcient with me but I can't seem to work the driver for my netgear wpn111 usb.
I have placed it on my desktop and as I try to exeute the programme it appears it wants to load it in the terminal but then the window sharply closes, this is a .inf file.

Also I have extracted the ndiswrapper 1.51 file to my desktop and I ran this code in the terminal
```
 tar zxvf ndiswrapper-version.tar.gz 
```
But the response is that the file is not recognised.

---

### Post by halitech on 2008-08-11
the version in Synaptic should work fine. Go to System - Administration _ Synaptic Package manager

do a search for ndis. Install ndiswrapper, ndiswrapper-common and ndisgtk.

After installing those 3 items, locate the ndisgtk program (I believe under System - Administration - Windows Wireles drivers) and use it to browse to where you have the .inf and .sys files and it will install them correctly for you.

---

### Post by Ian dewhurst on 2008-08-11
This is where it gets slightly annoying refering to an earlier post.
I read about installing this and guess what it ain't there!
Nothing under ndisgtk and ndiswrapper which I thought to be pretty odd as I was unde the impression that it came standard with ubuntu.

Me thinks I may have to connect to an ethernet of some description as I am running out of options.

---

### Post by halitech on 2008-08-11
what version do you have installed? I have 7.10 and a laptop with 8.04 and both of them have ndisgtk in the list.

---

### Post by Ian dewhurst on 2008-08-11
its the 8.04 hardy heron one.

---

### Post by halitech on 2008-08-11
I'll have to dig out the laptop and fire it up and double check but I'm pretty sure it has ndisgtk in the list...

---

### Post by Ian dewhurst on 2008-08-11
I thought I would do a screenshot to show you, does this mean I may have to re-install ubuntu?

---

### Post by halitech on 2008-08-11
if you have the live cd, boot into it and check and see if  ndiswrapper, ndisgtk and ndiswrapper-common are listed there. If they are, boot back into your installed version and in a terminal
```
sudo apt-get update
``` then ```
sudo apt-get install ndisgtk
``` and see what happens

---

### Post by anewguy on 2008-08-12
I'll add a couple of things:

(1) When I installed 8.04, most of the repositories where turned off so Synaptic didn't find squat.  Early posts from when it was first released indicated this was a common problem.  Go to Synaptic, then click on settings and repositories and be sure that a minimum main and universe are checked, then do a reload to fetch the package lists.

(2) If for some reason ndiswrapper still does not show, you can install it from the LiveCD without booting the Livecd.  One way is to just add it as a source in Synaptic, the other involves navigating in the file browser (this is quite easy - let me know if you need more info).

(3) Ndisgtk is a gui'd front end so you don't have to use ndiswrapper from the command line.  It's up to you if you want to install it, as it can be used either way if you do.

(4) Just for grins, what does "ndiswrapper -l <enter>" (that's a lower case "L" for "list") return from the command line?

:)

---

### Post by Ian dewhurst on 2008-08-12
I shall try the command when I get home, as I am at work now.

I could go into the ubunu I have unstalled here and check for the the synpatic packages to see if they are there as I installed it on this machine in the same way.

I think I may have also screwed myself slightly as I didn't use a live Cd I installed ubuntu through wubi.

---

### Post by Ian dewhurst on 2008-08-12
Can't install ndiswrapper through the synaptic, still doesn't show, annoying thing is it shows up in the add/remove but I need a working internet connection (gets easier huh :rolleyes:)

When I typed the command ndiswrapper -l in terminal it begins to appear to install a file but on the very last command line it says ndiswrapper common not reconised.

Is there any other way? It appears I may have to re-install.

---

### Post by anewguy on 2008-08-12
Without the LiveCd things may get a little more complicated.  The truth of the matter is, given this is a new install, I'd download the LiveCD and reinstall from there.  If ndiswrapper is not installed, it can then be installed right from the cd.

---

### Post by Ian dewhurst on 2008-08-12
Righty-ho I shall give that a bash, hopefully my next post will be through ubuntu *keeps fingers crossed*

---

### Post by Ian dewhurst on 2008-08-18
Hello everyone sorryfor the belated reply, but..........

I have made progress! I have created a liveCd and re-installed ubuntu and have managed to install ndiswrapper (the three items in the synaptic manager) and have managed to install the drivers for the device as well. Both are working properly, as checked through the terminal with:

```
 ndiswrapper -l 
```

```
 ndiswrapper -v 
```

But yet the device is still not blinking at me.

---

### Post by Ian dewhurst on 2008-08-18
Just a bit of an update I don't know whether this poses any relevance but under

```
 iwconfig 
```

The return value was no wireless extensions under both parts

---

### Post by halitech on 2008-08-18
when you did 
```
ndiswrapper -l
```
and
```
ndiswrapper -v
```
what was the output?

---

### Post by Ian dewhurst on 2008-08-18
The correct one according to this guide but I could do a quick .txt file to confirm? [http://ge.ubuntuforums.com/showthread.php?t=652910](http://ge.ubuntuforums.com/showthread.php?t=652910)

---

### Post by halitech on 2008-08-18
so you are getting a message that device is present and the driver is installed?

---

### Post by Ian dewhurst on 2008-08-18
Yes:

---

### Post by Ian dewhurst on 2008-08-19
I also get this under iwconfig:

lo no wireless extensions.

eth1 no wireless extensions.

---

### Post by Ian dewhurst on 2008-08-19
bump

---

### Post by Ian dewhurst on 2008-08-19
I think I may have found the problem that my netgear devie won't blink, its carp!!!!

After checking through wireless devices under the driver installed it lists no hardware connected.

I have a tempramental device even in XP you have to unplug and re-plug it a few times for it to blink and god help you if you even sneeze on it as it goes off and then the whole cycle begins again!

I think its time for a new one, shall purchase one later on in the week and see if I can connect that way or just keep trying with ubuntu.:lolflag:

---

### Post by Ian dewhurst on 2008-09-22
Right I am finally starting to see the end of this I have now managed to get wireless appear under network icon top right of the screen.

I also get these in terminal:
When I type iwconfig I get:
```

lo no wireless extensions

eth0 no wireless extensions

wlan0 IEEE 802.11g ESSID:"achilles"
mode:managed Channel:0 Access point: not association
Tx-Power=0 dbm
Retry limit:7 RTS thr:off Fragment thr=2346 B
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 RX invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

```

under ifconfig I get:
```

eth0 Link encap:ethernet HWaddr 00:1a:4b:72:9e:2e
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqeuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt 16

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:40 errors:0 dropped:0 overruns:0 frame:0
TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqeuelen:0
RX bytes:2760 (2.6 KB) TX bytes:2760 {2.6 KB)

```

My netgear device is still not winking at me.

---

