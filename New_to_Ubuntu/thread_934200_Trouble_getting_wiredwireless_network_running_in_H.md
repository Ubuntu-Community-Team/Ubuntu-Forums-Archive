---
title: "Trouble getting wired/wireless network running in Hardy"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by BrokenVisage on 2008-09-30
So I anticipated some complications getting the internet on my Dell laptop working with Ubuntu, but not like this. For some reason I only have 'lo' as a network controller. Ubuntu sees my wireless NIC card and onboard LAN, and initially I tried getting the wireless card to work without connecting to the Internet first, but gave up on that fairly quickly. Then when I went to get a wired connection going of course that doesn't work either and I can't find any mention of eth* or wlan0 now.

Can somebody PLEASE walk me through getting my Hardy build setup wired at the least so I can download the repositories and get wireless finally going? I have video issues too but first thing's first. I'm at work right now and don't have my laptop so I can't do any commands or look up things, but I can remember a couple of things about what I've done so far and am pretty tech savvy this seemingly idiot-proof problem aside. So if someone could lend me a hand in getting the my networking going that would be great. Thanks guys.

---

### Post by Idefix82 on 2008-09-30
I'm afraid you will need to be in front of your laptop for this. Can you start by typing
```
lshw -C network
```
and posting the output here?
By the way, what laptop exactly do you have?

---

### Post by northern lights on 2008-09-30
Can you please post the output of ```
sudo lshw -C network
```
Thank you.

---

### Post by BrokenVisage on 2008-09-30
My laptop is a Dell Inspiron 8600. Tests I've seen using it with previous builds of Ubuntu all looked pretty good, so I was confident it would work out of the box. I must of fuxed something up trying to get my wireless card to work. Will definately try any commands you guys ask for and will post the results once I get home, but for now all I can do is answer questions about my issue and try to explain everything as best I can. Believe me, I've done a lot of Googling trying to resolve this and thought I came across the solution several times, but there's always something involving downloading more repositories and since I can't download that's where it stopped.

---

### Post by superprash2003 on 2008-09-30
i had a dell inspiron too.. got my card working using this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by northern lights on 2008-09-30
> **BrokenVisage said:**
> since I can't download that's where it stopped.
That's a vicious cycle indeed.

Do you have any other computer at home that can connect to the net?
That'd be really helpful. Transferring .debs and resolving dependencies is still a hassle, but with adequate help from the forums, I'm sure you'll get it sorted out.

The output will tell you (or us) whether the device is being recognized and if so, whether it's a driver issue or a question of network settings or both.

Copy the output to a textfile, move that on a flashdrive, and thus paste it here from an online machine.

---

### Post by BrokenVisage on 2008-09-30
> **northern lights said:**
> That's a vicious cycle indeed.

Do you have any other computer at home that can connect to the net?
That'd be really helpful. Transferring .debs and resolving dependencies is still a hassle, but with adequate help from the forums, I'm sure you'll get it sorted out.

The output will tell you (or us) whether the device is being recognized and if so, whether it's a driver issue or a question of network settings or both.

Copy the output to a textfile, move that on a flashdrive, and thus paste it here from an online machine.

Sure, I have plenty of other computers on the Internet at my house, and have been doing the old DL-to-Flash Drive-to-Laptop procedure to get debs and other files from the web onto my laptop, but still nothing seemed to work right. Granted I'm not a linux genius by any means, I do like to think I know what I'm doing and understand reasons/procedures for doing it, but really for the most part I'm just copying commands that were given to other people who needed help in a similar situation to mine, mostly from threads on here. It just seemed like no matter what I tried to do it keep looking to connect online to download something, so I got frustrated and havn't touched it for a couple days now. But I'll definitely fire it up tonight and post what you guys ask.

---

### Post by BrokenVisage on 2008-09-30
OK guys, here's my output from 'sudo lshw -C Network'  

  *-network               
       description: 802.11b CardBus
       vendor: Broadcom
       physical id: 0
       version: 8.0
       slot: Socket 0
       resources: irq:11
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:03:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0c:41:2e:ea:da
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by BrokenVisage on 2008-09-30
_/\_
||
_||_

---

### Post by BrokenVisage on 2008-10-01
once more before bed

---

### Post by spiritsongtress on 2008-10-01
> **BrokenVisage said:**
> once more before bed

Ahh its a broadcom know if its B43XX if so One of thses should work: [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)
Trust me I have a broadcom card... (pain the BUTT)

---

### Post by BrokenVisage on 2008-10-01
> **spiritsongtress said:**
> Ahh its a broadcom know if its B43XX if so One of thses should work: [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)
Trust me I have a broadcom card... (pain the BUTT)

Thanks, I came across a page like this that talked about getting Broadcom cards to work, but couldn't get that fwcutter program to install correctly or something. I do remember transfering it over to my laptop via USB drive, but for some reaosn it didn't work. I'll try doing it from scratch again during lunch today, will post my results.

---

### Post by BrokenVisage on 2008-10-01
> **spiritsongtress said:**
> Ahh its a broadcom know if its B43XX if so One of thses should work: [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)
Trust me I have a broadcom card... (pain the BUTT)

Quick question...

Should I be downloading/using the bcm43xx driver for lunix 2.6.24 or lunix 2.6.25 and newer? I see where it says what to do for the 4306 cards, but what version of linux am I? Is the 2.6.24 Kernel installed by default through Hardy?

Thanks

---

### Post by Bucky Ball on 2008-10-01
[quote=BrokenVisage]Should I be downloading/using the bcm43xx driver for lunix 2.6.24 or lunix 2.6.25 and newer? I see where it says what to do for the 4306 cards, but what version of linux am I? I assume 2.6.25 and newer, right?[/quote]

You should be able to use the b43 driver (which is in System->Administration->Hardware Devices) with one tick in conjunction with b43-fwcutter without worrying about those details. If you can't get online though this could be problematic. If you haven't updated the machine since installing, then the Broadcom B43 Driver will not be there already. Your machine could be letting you know there is a restricted driver available for your wireless card. Not sure if the restricted drivers are on the live cd but you could put the cd in, enable it in Software Sources then look for it and b43-fwcutter in Synaptics.

If you tick the hardware driver I vaguely remember it asking if I want to install b43-fwcutter also and you just click yes, but you are gonna need to find out if you can get it from the cd first. 

But if you can get the ethernet cable up ... Are you booting the machine with your ethernet cable plugged in already? When you have the machine going, try pasting this in a terminal:

sudo /etc/init.d/networking restart

... and see if the cable comes up.

[http://www.linuxwireless.org/en/users/Drivers/b43](http://www.linuxwireless.org/en/users/Drivers/b43)

---

### Post by BrokenVisage on 2008-10-01
OK here's where I'm at... I got the fwcutter and transfered it to my Ubuntu laptop. Extracted it and everything, went the 'make' the program and got bunch of errors that look like this: 
fwcutter_list.h:128: warning: (near initialization for â€˜_cb8d70972b885b1f8883b943c0261a3c[10]â€™)
fwcutter_list.h:129: error: unknown field â€˜offsetâ€™ specified in initializer
fwcutter_list.h:129: warning: excess elements in struct initializer
fwcutter_list.h:129: warning: (near initialization for â€˜_cb8d70972b885b1f8883b943c0261a3c[11]â€™)
fwcutter_list.h:129: error: unknown field â€˜typeâ€™ specified in initializer
fwcutter_list.h:129: warning: excess elements in struct initializer
fwcutter_list.h:129: warning: (near initialization for â€˜_cb8d70972b885b1f8883b943c0261a3c[11]â€™)
fwcutter_list.h:129: error: unknown field â€˜lengthâ€™ specified in initializer
.....
.....
.....
make: *** [fwcutter.o] Error 1
dave@dave-laptop:~/b43-fwcutter-011$

So, something is obviously wrong with that and I wouldn't know where to begin in fixing it. There are another thousand or so lines of errors I cut out as well but I'm sure nothing within them would be able to identify any posible culprit anyway.

Then I tried restarting my network controllers after booting with the CAT5 cable connected and got this:

dave@dave-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.wlan0.pid with pid 6751
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:0c:41:2e:ea:da
Sending on   LPF/wlan0/00:0c:41:2e:ea:da
Sending on   Socket/fallback
SIOCSIFFLAGS: No such file or directory
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:0c:41:2e:ea:da
Sending on   LPF/wlan0/00:0c:41:2e:ea:da
Sending on   Socket/fallback
receive_packet failed on wlan0: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
RTNETLINK answers: Network is down
run-parts: /etc/network/if-up.d/avahi-autoipd exited with return code 2
[ OK ]

Of course the wlan0 wouldn't be working, but no sign of any eth* entries, so I don't know.

I did find another thread with someone having what looks to be a very similar issue and also with the same wireless card as me [Here]("http://ubuntuforums.org/showthread.php?t=328272")

It got into using NDISwrapper, which I tried to install before my lunch was over but one of the steps involved a directory that I don't even have. So if none of you can help me get this going I may try that route again to see where it gets me.

---

### Post by Bucky Ball on 2008-10-01
Either way, you are going to need to be online to do it, kinda ironic really. You could download the b43 and b43-fwcutter packages on another machine and get them in there that way I guess. The page I gave you before gives exact directions on how to get b43 going. Ndiswrapper will work if you are ready for the nightmare (so I've heard but it never worked for me in months) but is superceded by b43 for your card.

[http://www.linuxwireless.org/en/users/Drivers/b43](http://www.linuxwireless.org/en/users/Drivers/b43)

[quote=BrokenVisage]It got into using NDISwrapper, which I tried to install before my lunch was over but one of the steps involved a directory that I don't even have.[/quote]

Get used to that. Broadcom cards are a b****h with ndiswrapper.

If you have other computers online, maybe research the correct packages for b43, put them on a usb dongle and transfer them over to the other machine and should be plain sailing. As I say, catch22 because if you had the updates it would be offering you these drivers automatically.

---

### Post by BrokenVisage on 2008-10-02
> **Bucky Ball said:**
> Either way, you are going to need to be online to do it, kinda ironic really. You could download the b43 and b43-fwcutter packages on another machine and get them in there that way I guess. The page I gave you before gives exact directions on how to get b43 going. Ndiswrapper will work if you are ready for the nightmare (so I've heard but it never worked for me in months) but is superceded by b43 for your card.

[http://www.linuxwireless.org/en/users/Drivers/b43](http://www.linuxwireless.org/en/users/Drivers/b43)



Get used to that. Broadcom cards are a b****h with ndiswrapper.

If you have other computers online, maybe research the correct packages for b43, put them on a usb dongle and transfer them over to the other machine and should be plain sailing. As I say, catch22 because if you had the updates it would be offering you these drivers automatically.

I really don't care what I end up using so long as it gets me online for the time being. The page you linked is very nice and straight-forward, but like I mentioned above I get a bazillion makefile errors when I try to simply make it, should I be doing this this as root maybe? 

I'm really getting annoyed that whenever I come across a simple enough procedure like this something doesn't work for me but it seems to be such a minor step that shouldn't break according to the instructions so it doesn't go into workarounds. I'm all for using the fwcutter approach but wouldn't know where to begin in troubleshooting those make errors, I'd like to assume that it's a single point of failure though and could be fixed by doing something I didn't do or a step I somehow skipped.

---

### Post by Bucky Ball on 2008-10-02
Open Synaptics and look for:

**build-essential**

If it is there, tick if it's not ticked. That could be the problem with your 'make' errors.

If it's not there, you may have to see if you can find it on your live cd. You can enable the cd in Synaptics by hitting Settings->Repositories. That will open the Software Sources gui.

Update: [http://ubuntuforums.org/archive/index.php/t-251602.html](http://ubuntuforums.org/archive/index.php/t-251602.html)

That will help out with getting the build essential packages.

---

### Post by BrokenVisage on 2008-10-03
> **Bucky Ball said:**
> Open Synaptics and look for:

**build-essential**

If it is there, tick if it's not ticked. That could be the problem with your 'make' errors.

If it's not there, you may have to see if you can find it on your live cd. You can enable the cd in Synaptics by hitting Settings->Repositories. That will open the Software Sources gui.

Update: [http://ubuntuforums.org/archive/index.php/t-251602.html](http://ubuntuforums.org/archive/index.php/t-251602.html)

That will help out with getting the build essential packages.

There are so many dependancies involved with this method that it seems ridiculous to do it this way. I don't understand why I can't update respoitories from my LiveCD if that really is an option like people are saying. I check all the available repositories in the GUI and try to reload, but it always fails at one of the initial update steps when it tries to download index files or something from the Internet. After that it just stops and it seems nothing is updated, and there doesn't seem to be a way to get around having it check the Internet unless I missed something. Should I just be concentrating on getting my wired connection going before anything else now?

---

### Post by Bucky Ball on 2008-10-03
> **BrokenVisage said:**
> Should I just be concentrating on getting my wired connection going before anything else now?

Might be an idea.

---

### Post by BrokenVisage on 2008-10-03
> **Bucky Ball said:**
> Might be an idea.

In that case, short of continually rebooting with my network cable plugged in until I magically get a connection, what commands should I run to see if Ubuntu even sees an Ethernet controller and if so have it try to reconfigure the thing? Thanks.

---

### Post by Idefix82 on 2008-10-03
Unfortunately, Hardy doesn't see your Ethernet card at all. Otherwise it would appear in the list you get with lshw. Can you try
```
lspci
```
and see if the card comes up there?

---

### Post by Bucky Ball on 2008-10-03
Open System->Admin->Network and make sure your wired connection is ticked and active.

Give this a shot:

[http://davestechsupport.com/blog/2008/03/08/how-to-setup-internet-connections-in-ubuntu/](http://davestechsupport.com/blog/2008/03/08/how-to-setup-internet-connections-in-ubuntu/)

Down the page some it gets into more detail.

... and yes, post result of lspci from your terminal (copy and paste). :)

---

