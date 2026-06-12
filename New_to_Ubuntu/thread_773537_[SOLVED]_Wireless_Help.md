---
title: "[SOLVED] Wireless Help"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by NeuB27 on 2008-04-28
My system seems to recognize my wireless card, or rather it shows up in 'lspci' but there is no wireless option under my Network Settings. I use a Zonet ZEW1602A card.

---

### Post by spiderbatdad on 2008-04-28
can't find much...[http://ubuntuforums.org/showthread.php?t=722629](http://ubuntuforums.org/showthread.php?t=722629)
this guy says he got it working with ndiswrapper...but you'll need the driver...usually a .exe file which you unwrap with a program like cabextract...ndis-gtk is also in synaptic, and is a graphical tool for helping you install the driver...I have been fortunate with wireless not to need either...use forum search tool for a how-to on ndiswrapper...

---

### Post by anewguy on 2008-04-29
There are a few other posts on this card, and they all say to use ndiswrapper.  If you are not familiar with all of this, ndiswrapper is a package which allows you to use Windows network drivers in Linux.

The first thing you will need are the Windows drivers for your card.  If you have a CD that came with the card, you should be able to find a drivers subfolder on it.  It may contain subfolders for W2K, WXP, WXP64, etc.  The driver files may be zipped in which case you will need to unzip them first.  You might also try just downloading the driver files from the manufacturer's site.  Usually this will consist of a .inf file and 1 or more .sys files.  When you have found those files, copy them to your desktop, then proceed as follows:

Open a terminal window (some call it command line) via:

Applications/Accessories/Terminal

Once that window is open, do the following:

cd ~/Desktop  <= change current directory to your desktop

ls  <= will show the contents of the current directory

sudo ndiswrapper -i xxxxxx.inf <= that's a lower case "I" for install, and xxxxxx.inf should be replaced by the name of your driver .inf file as shown after the "ls" above

sudo depmod -a

sudo modprobe ndiswrapper

sudo ndiswrapper -m

sudo gedit /etc/modules

Add the following to the end of that file:

ndiswrapper

Save the file and exit the editor

Now, reboot and check under your network icon to see if your wireless shows.  :)

---

### Post by NeuB27 on 2008-04-29
Thank you a bunch to both of you, I tried those methods. They were slightly different to the methods I had tried before, but they didn't seem to work. My wireless still doesn't show up. 

Random Question: I keep seeing help documentation and forum posts saying to access System > Administration > Device Manager .... I cannot find that, are they referring to System > Preferences > Hardware Information?

---

### Post by anewguy on 2008-04-29
(1) Yes, device manager IS hardware information on the System/Preferences menu.

(2) Post the output of lspci back here

(3) Post the output of ndiswrapper -l <= lower case "L" back here

(4) Check under System/Administration/Network and see if wireless shows there.  If so, is roaming mode enabled?

We'll look at those things first, and work out from there.  :)

---

### Post by NeuB27 on 2008-04-30
Thank you so much for replying.
1. thanks
2. (the computer is off right now, and isn't connected to the internet anymore) but lspci did list the wireless card as attached, and gave drivers for it. I believe it was "05.02.0 Ethernet Controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)" [from previous problems post]
3.(again)It said that the driver(which I wanted) was installed and the device(and id) was present.
4.No, thats what has me so confused, I followed these steps and nothing shows up. Not in network settings, nothing under the icon, even wlan0 hasn't shown up as an iwconfig, or anything else setting...

---

### Post by anewguy on 2008-04-30
> **NeuB27 said:**
> Thank you so much for replying.
1. thanks
2. (the computer is off right now, and isn't connected to the internet anymore) but lspci did list the wireless card as attached, and gave drivers for it. I believe it was "05.02.0 Ethernet Controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)" [from previous problems post]
3.(again)It said that the driver(which I wanted) was installed and the device(and id) was present.
4.No, thats what has me so confused, I followed these steps and nothing shows up. Not in network settings, nothing under the icon, even wlan0 hasn't shown up as an iwconfig, or anything else setting...


lspci won't show the driver, just the device.  What happens with most of the wireless cards is they are recognized as hardware (that's why they show in lspci) but no drivers are installed (so the wireless doesn't show up anywhere).

I know they have multiple ways of doing things, but ndiswrapper is sort-of a fail-safe method of installing the drivers.

So, since we know the piece of hardware is recognized, but apparently no drivers are loaded, when you have the computer back on please post back here the result of:

sudo ndiswrapper -l

That will help in getting started trying to fix this.  :)

---

### Post by Tom--d on 2008-04-30
First of all.. 

Do you have the right windows driver for your wireless card?

and yes.. we need the result of 
```
ndiswrapper -l
```

---

### Post by NeuB27 on 2008-04-30
Ndiswrapper lists the name of the driver that I installed, its name is netmw126, and it lists the id location of the device. I believe that it is the right driver, I am using 7.10 amd 64 and chose the xp64 driver from the manufacturer cd. I'll post the exact number in a moment.

---

### Post by NeuB27 on 2008-04-30
from ndiswrapper -l
'
netmw126 : driver installed
        device (11AB:1FAA) present
'
for some reason .. when I turned the computer on, it was listing a wireless option, roaming is enabled, however no networks appear, I know that there are at least two within range ( as I am using one to reply with my laptop ) I've tried to do the manual configuration before, and it did not work well ( something caused the OS to stop loading ) so if someone would like to help me get the roaming mode to work I would love it. Or alternately make a guess at what went wrong last time. 
from lspci
'
05.02.0 Ethernet Controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
' same as before.
iwconfig  has information for wlan0 now
'
IEEE 802.11g  ESSID:off/any
Mode: Managed Channel:0 Access Point: Not-Associated
Bit Rate:1 Mb/s  Sensitivity= -200 dBm
RTS thr=2346 B  Fragment thr=2346 B
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excesive retries:0 Invalid misc:0  Missed beacon:0
'
Let me know if there is any other information that can help, thanks again.

---

### Post by xBigJayx on 2008-04-30
hello i have the same prob on my laptop and iahev tried to install the the madwifi it didnt work then i downloaded a win xp driver for my atheros 802.11 wifi and used the ndiswrapper and this is the ndiswrapper -l answer i got 
root@jad-laptop:/media/ubuntu/xp32# ndiswrapper -l
netathwx : driver installed
	device (168C:001C) present (alternate driver: ath_pci)

what should i do to uninstall the ath_pci or is there a solution to my rob?

---

### Post by NeuB27 on 2008-04-30
So I tried to "Connect to Other Wireless Network..." and put in all of the information, however it did not connect, but now it shows the Network (less than 20ft away, not iron walls) with no signal, I am assuming that it is still not seeing anything, so I now don't really know what to do. Should I look for different drivers?

To xBigJayx.. you might want to start a new thread to find the answer, I don't have a clue. I know that 'ndiswrapper -r nameofdriver.inf' will remove the driver... but I don't know what it's being listed as alternative really means.

P.S. OK..... so I just had to use the reset button on my computer to remove it from a frozen non-responsive state.. in ubuntu. I had just done the above stated, and opened System > Administration > Services (I meant to click on Screens and Graphics) and then opened System > Administration > Screens and Graphics .. to change the monitor that I was using, and the mouse and keyboard stopped responding for 5 minutes or so. After restart, wireless no longer shows up.
lspci still lists the card the same.
iwconfig shows no wlan0
ndiswrapper -l shows the driver and device are there ( at the same locations )
and I have already added ndiswrapper to /etc/modules with gedit.. what now. I would love to not do a fresh install.

---

### Post by anewguy on 2008-04-30
Even though you used the driver from the CD, and at times it was at least functioning (you wouldn't have been able to see or connect to any wireless networks if it wasn't), this is what I would do:

(1) get back to a clean slate with ndiswrapper:

ndiswrapper-l

for each driver that shows:

sudo ndiswrapper -e xxxxxx <= where xxxxxx is the name of the driver as shown in the output above

repeat this until nothing is returned.

(2) Download the current driver of the correct architecture from the manufacturer's site

(3) use ndiswrapper and install that driver.  Remember to do the sudo depmod -a followed by a modprobe ndiswrapper.  

It's also possible there is a driver module that is active in Linux that is conflicting with yours.  More research would need to be done to find this out, at which time it could be blacklisted in /etc/modprobe.d/blacklist.

I know this seems like a pain, but believe me, for most of us, there are 2 big hurdles to overcome to use Linux of any flavor:

- video drivers
- wireless drivers

It can be a real pain - I know cause I've been there in the past with many other computers and wireless cards.  All I can ask is to bear with us and we'll do our best to get this running for you.

Also, if wireless networking doesn't appear to work, you can try activating and connecting via the command line.  If you would like to try this, let me know and I'll post back instructions.

:)

EDIT:  Does the network you were trying manually to connect to require any authentification, or is it an open network with no passwords, etc..?  Also, make sure the name matches exactly - remember the thing that I've bit myself on a few times:  Linux is case sensitive, so "MYROUTER" cannot be found with anything but all caps.

---

### Post by anewguy on 2008-04-30
> **xBigJayx said:**
> hello i have the same prob on my laptop and iahev tried to install the the madwifi it didnt work then i downloaded a win xp driver for my atheros 802.11 wifi and used the ndiswrapper and this is the ndiswrapper -l answer i got 
root@jad-laptop:/media/ubuntu/xp32# ndiswrapper -l
netathwx : driver installed
	device (168C:001C) present (alternate driver: ath_pci)

what should i do to uninstall the ath_pci or is there a solution to my rob?

Well, you did one part right for sure - used the XP driver.  From what I have understood in the past, the Vista drivers won't work yet.  As for the alternate driver, I'm no so sure that's bad.  What symptoms do you have now?  If you look in network manager, do any wireless networks show (they have to be within range and be broadcasting their ID)?

---

### Post by NeuB27 on 2008-04-30
In reply, I would love to know how to proceed during within the command line.

---

### Post by anewguy on 2008-04-30
Okay, here we go with the command line stuff.  It is assumed you either have left the driver installed or you have reinstalled it (with ndiswrapper). In the following, MyNET should be replaced with the name of the network you want to connect to, and keyxxxxxx should be replaced with the wep key (if there is one):

(1) config the name of the network you want to connect to with:

sudo iwconfig eth1 essid MyNet

(2) IF the network uses a key, config the key:

sudo iwconfig eth1 key keyxxxxxx

(3) bring up the ethernet:

sudo ifconfig eth1 up

(4) attach the client:

sudo dhclient3 eth1

(5) after (4) returns to the command line, try pinging a location:

ping [www.yahoo.com](www.yahoo.com)


Let us know how this goes. :)

---

### Post by NeuB27 on 2008-05-01
A few questions, just so that I can learn more, why eth1? wouldn't that be a typical wired network? Or can the name be anything? also isn't ifconfig for wired stuff only? Lastly what is dhclient3?

---

### Post by anewguy on 2008-05-01
> **NeuB27 said:**
> A few questions, just so that I can learn more, why eth1? wouldn't that be a typical wired network? Or can the name be anything? also isn't ifconfig for wired stuff only? Lastly what is dhclient3?

Well, I'll do my best to answer, but someone else may need to kick in (I know it works but not real sure about the pieces).

First, I have a ethernet jack on my PC and it is for whatever reason (the order in which they are detected, starting with "internal" buses like PCI, then going to "external" buses like USB) eth0.  So, I have to use eth1 .

I have not clue about ifconfig, but it works.  I assume it is for network devices, not just a hardwired connection.

Dhclient3 I believe is just the client that connects your terminal window command line to the config'd device.

That's how I understand it all in basic terms.  I know it works - I've used it on my PC when video card driver problems wouldn't allow me to boot into the GUI, so I had to log to the command line, use the above to activate the net, then download a new driver.

Believe me, some else out there is WAY smarter than me on this - I'm a relative beginner myself.

---

### Post by xBigJayx on 2008-05-01
> **anewguy said:**
> Well, you did one part right for sure - used the XP driver.  From what I have understood in the past, the Vista drivers won't work yet.  As for the alternate driver, I'm no so sure that's bad.  What symptoms do you have now?  If you look in network manager, do any wireless networks show (they have to be within range and be broadcasting their ID)? 

listen i have uninstalled all the drivers that where already installed  and then reinstalled each driver alone and the problem persist i just put my configuration and try to connect it doesn't find my router...

---

### Post by anewguy on 2008-05-01
> **xBigJayx said:**
> listen i have uninstalled all the drivers that where already installed  and then reinstalled each driver alone and the problem persist i just put my configuration and try to connect it doesn't find my router...

It would be better if you opened your own thread on your problem, so we can try to fix 1 problem here, not 2.

Thanks
:)

---

### Post by NeuB27 on 2008-05-02
Next problem, a few times now the terminal window has stopped and not returned to the "name@machinename~: " prompt. After like 20 minutes I just closed the window. Presently ( when I last turned it off ) the wireless option was showing up, I tried the above mentioned steps to set up via terminal ... however it did not accept the key.. perhaps it was expecting a different type? How do I set the encryption for it to expect? Also, after it rejected the Key, it no longer would accept the essid setting, I tried to change that, and it would way invalid argument. I tried the finishing commands anyway (dh..) and it did a lot of things, all ending in essentially 'you lose' and a stated lack of network/DHCP/connection. Kinda lost for now. So I guess, 
A) Are there more settings for iwconfig or ifconfig so that you can set the encryption type and stuff like that. ( I looked under the --help and it didn't seem to have any options that looked right ).
B) Is the fact that these problems are arising due to a larger problem, and if so .. how should I address that problem. 
C) Is there a linux driver somewhere that maybe works? or some way other than ndisgtk/ndiswrapper, that I can approach this problem? Would wine allow me to set up the windows drivers easier somehow?
D) Wow is it frustrating not know where to go next! I've looked through the forums for similar problems ( and found someone with the same card, but they didn't say how it got fixed and will not reply to pms/emails ) and online for further documentation or help advice, but it doesn't seem to help. I'm about at the end of my rope. I would rather wire the connection than look to the windows alternatives, but if I will encounter this many problems (azureus also doesn't seem to set up quite right)... maybe my computer just hates linux/ubuntu?

Well sorry for the complaint at the end, I know that all of you who have helped me are trying a lot, and I appreciate it more than I can say, the willingness to help others is an extreme draw towards the open source model. Thank you again.

---

### Post by Louey on 2008-05-02
Don't know if this link will help but it is quite thorough on installing wireless cards.
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

Good luck...

---

### Post by anewguy on 2008-05-02
I think I would try the link posted above by Louey, then if you still have problems I think I would consider trying to reinstall Ubuntu from scratch, maybe even back 1 release for now to 7.10.  I really don't know where to go from here - kinda exhausted my knowledge - but some of the problems sound like more than network driver problems, that's why I would consider dropping back a release and reinstalling.  Maybe there's something about 8.04 that right now doesn't get along with your PC, though I have no idea what that could be.

Sorry I can't be of more help!!

Everyone out there - please try to help out here!!

Thanks!!  :):)

---

### Post by NeuB27 on 2008-05-02
I am already on 7.10. I installed it about 3 days before HH went final/non-testing/whatever you call it. I've been trying to fix this problem since then. Thanks for the link, I'll check it out.

---

### Post by xBigJayx on 2008-05-04
> **anewguy said:**
> It would be better if you opened your own thread on your problem, so we can try to fix 1 problem here, not 2.

Thanks
:)

I did but i got no reply so i found this thread with similar prob i tried to publish mine anyway nth helped me till now.

thanks anyway.

---

