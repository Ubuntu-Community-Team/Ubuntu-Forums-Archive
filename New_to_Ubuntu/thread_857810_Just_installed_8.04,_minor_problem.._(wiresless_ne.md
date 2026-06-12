---
title: "Just installed 8.04, minor problem.. (wiresless network)"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by MrJoeyUK on 2008-07-12
Ok i've just installed and the only problem so far (i've yet to check if vista still even boots) that it isn't recognizing my wireless network (i'm on my desktop, I installed ubuntu onto my laptop), nor does it seem to give me a option to search for one. If you nice people could point me in the right direction please. 

Thanks in advance.

---

### Post by falcon61102 on 2008-07-12
If you could go to your terminal and post the results of:
```
lspci
```
and
```
lshw -C network
```

---

### Post by MrJoeyUK on 2008-07-12
.. and how do you suggest I get the results from laptop to desktop without a connection? Hang on, going to get my USB drive. ohh it's a hard life. :) Thanks for the quick reply.

---

### Post by falcon61102 on 2008-07-12
Yeah, a USB drive would work... it's going to be too much to type.  I know it's a pain, I went through something similar.  And no problem.

---

### Post by MrJoeyUK on 2008-07-12
Ok me being the noob at linux I am I've saved all the results in gedit yet can't open them on here in windows. No way i'm writing it all out lol. Help anyone? I'm sure theres a simple answer.

---

### Post by falcon61102 on 2008-07-12
Check PM

---

### Post by MrJoeyUK on 2008-07-12
ok well Vista boots, that's the good thing. 

I'm downloadin open office.. this is so much hassle.. yawn.. 60%, wernt open office files supposed to be able to open in MSWORD?

75% (and I just noticed I spelt it wiresless, my mistake.)

Okay!
[B]
lspci [/B]
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01) 
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) 
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01) 
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) 
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1) 
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01) 
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) 
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01) 
02:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01) 
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 01) 
10:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01) 
[B]
 lshw -c network [/B]
Hardware Lister (lshw) - B.02.12.01 
usage: lshw [-format] [-options ...] 
       lshw -version 

	-version        print program version (B.02.12.01) 

format can be 
	-html           output hardware tree as HTML 
	-xml            output hardware tree as XML 
	-short          output hardware paths 
	-businfo        output bus information 

options can be 
	-class CLASS    only show a certain class of hardware 
	-C CLASS        same as '-class CLASS' 
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. ) 
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. ) 
	-quiet          don't display status 
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)

---

### Post by falcon61102 on 2008-07-12
Ok... your problems is that Ubuntu doesn't recongize the drivers for the Broadcom so you need to re-install the drivers.  If you can connect through a wired connection while in Ubuntu, great.  If not, you'll have to copy a file or two from the computer with the connection to the one with Ubuntu.  I'm going to give you the link to a HowTo because it's pretty straight forward for what you have to do.  If you have any questions or errors with it, let me know and I'll help.  

The link is:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Hardy%20Bug%20Fix](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Hardy%20Bug%20Fix)

Make sure you do the Hardy Bug Fix

Also, I made a typo earlier, it's supposed to be:
```
lshw -C Network
```

And did you get my last PM about OpenOffice... if you use Save As feature you should be able to save the file as a .doc and it will open in Word.

Hope this helps.

---

### Post by MrJoeyUK on 2008-07-12
To reply to falcon any everyone else... 

I'm online on Ubuntu now.. via ethernet. I'm following this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Hardy%20Bug%20Fix](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Hardy%20Bug%20Fix)

joe@joe-laptop:~$ echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
[sudo] password for joe: 
Sorry, try again.
[sudo] password for joe: 
blacklist bcm43xx
joe@joe-laptop:~$ sudo apt-get install ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**E: Couldn't find package ndiswrapper-utils-1.9**
joe@joe-laptop:~$ mkdir ~/bcm43xx; cd ~/bcm43xx
joe@joe-laptop:~/bcm43xx$ 
joe@joe-laptop:~/bcm43xx$ 
joe@joe-laptop:~/bcm43xx$ lspci -n | grep '14e4:43'
10:00.0 0280: 14e4:4315 (rev 01)
joe@joe-laptop:~/bcm43xx$ 

And I'm trying to resolve the problem in bold, i'm looking through synaptic package manager but can't really find what i'm suppose to be looking for.

---

### Post by james_vanb on 2008-07-12
What Wireless USB are using?  Do you have the install CD?  If you do, insert - navigate to drivers for XP - What driver do you need to install (It will have a .inf extension)?

---

### Post by falcon61102 on 2008-07-12
Were you able to get it installed with the CD in?  And have you checked the Synaptic Package Manager to ensure that you will search through all the repositories?

---

### Post by james_vanb on 2008-07-12
> **MrJoeyUK said:**
>  
Reading state information... Done
**E: Couldn't find package ndiswrapper-utils-1.9**
j

Open Synaptic.  Search for ndiswrapper.  You need to mark ndiswrapper common and ndiswrapper utils for install.

---

### Post by MrJoeyUK on 2008-07-13
I'm not using wireless USB. My laptop connects to my network with a built in wifi, if that's what you meant.

 *-network UNCLAIMED     
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 01
       serial: 00:1e:ec:17:27:fc
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.1.4 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes

---

### Post by falcon61102 on 2008-07-13
Were you able to get ndiswrapper installed?

---

### Post by MrJoeyUK on 2008-07-13
This is stupid.. i've been using ubuntu for about 2 hours, you cannot possibly expect me to know what the hell you're both onabout. The amount of times I've been told ubuntu is easy to debug, easy to configure, etc.. well it certainly doesn't seem like it lol. 
My installation disc (for ubuntu..) is inserted and god knows where I tick off which tells the search to look on CD. 

Is there any kind of remote assistance function? I really cant do this, especially at this time.

EDIT: I searched for NDISWRAPPER in synaptic and nothing was found.

---

### Post by james_vanb on 2008-07-13
> **MrJoeyUK said:**
> I'm not using wireless USB. My laptop connects to my network with a built in wifi, if that's what you meant.

That's what I meant.

   > **MrJoeyUK said:**
> product: BCM4310 USB Controller
       vendor: Broadcom Corporation
 
Suggests a USB controller.

What laptop do you have?  You need to find out which driver the wireless is using and download same (Assuming you don't have an install CD - Meaning an install CD for the wireless not ubuntu) to use ndiswrapper.

---

### Post by aktiwers on 2008-07-13
Hey MrJoey,

This is how you install it. I really think it is easiest for you, if you plug in a cable connection to the computer.

1) Download the drivers here (direct link)
 [http://ftp.us.dell.com/network/R174291.exe](http://ftp.us.dell.com/network/R174291.exe) 

2) Follow the instructions from here:
 [http://linux.dell.com/wiki/index.php...le_ndiswrapper]("http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper")
 
When you unzip the driver, you'll have a DRIVER_US directory which contains the right file to use.. (bcmwl5.inf).

Good luck..  I found the info from [another post]("http://ubuntuforums.org/showpost.php?p=4143330&postcount=3") here at the forums

---

### Post by Tim Sharitt on 2008-07-13
Can you connect via a ethernet cable temporarily.

---

### Post by MrJoeyUK on 2008-07-13
Thanks akti. Also, I've found the repositories, searched from disc and therefore NDISWRAPPER is appearing on synaptic search now, common and utils.

EDIT: well tim I said a few posts up i'm connected on Ubuntu now via ethernet cable. Which is why I wondered why I was required to type all this crap into terminal.. lol Akti's way seems ALOT easier from where i'm sitting.

---

### Post by Tim Sharitt on 2008-07-13
Sorry, I thought you were connected on Vista. If you can't get ndiswrapper to work install b43-fwcutter from synaptic. This will install the firmware required to use the b43 driver.

---

### Post by james_vanb on 2008-07-13
If your driver is the bcmwl5.  That is the same driver my Belkin Wireless card is using.

Download ndiswrapper from Synaptic - System > Applications > Synaptic Package Manger.  There are 2 applications - ndiswrapper common and ndiswrapper utils 1.9.

If you were able to download the bcmwl5 drivers ( You need an .inf and .sys file).  

Open Places > home

left click in open space and create folder. I called mine Belkin as this is the wireless card I'm using.

Open the file that contains the driver files - drag and drop all files contained in the file to the file you just created - it should be a .sys, .inf and maybe a .cat.

Go to this link:

[http://ubuntuforums.org/showthread.p...hlight=BCM4306](http://ubuntuforums.org/showthread.p...hlight=BCM4306) 

I used Step 3 and on to get mine working - Step 3 begins with the following command:

```
sudo ndiswrapper -i bcmwl5
```

You have to modify that command to point to the file you created, In my case it looked like this:

```
sudo ndiswrapper -i /home/(yourusername)/Belkin/bcmwl5.inf
```

Then just copy and paste the commands that follow in Step 3 all the way to the end.

Keep in mind that commands are case sensitive i.e. my file was Belkin not belkin.

---

### Post by MrJoeyUK on 2008-07-13
Ok, the driver has finished DL/ing and I got the following:

tmp/R174291.exe could not be opened, because the associated helper application does not exist. Change the association in your preferences.

After noticing ati's link is practically the same thing I did it all again.. sooooo

joe@joe-laptop:~$ sudo apt-get install ndiswrapper-common ndiswrapper-utils ndisgtk
[sudo] password for joe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-common is already the newest version.
Package ndiswrapper-utils is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  ndiswrapper-common
E: Package ndiswrapper-utils has no installation candidate
joe@joe-laptop:~$ echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
blacklist bcm43xx
joe@joe-laptop:~$ sudo ndiswrapper -i /tmp/DRIVER/bcmwl5.inf
couldn't open /tmp/DRIVER/bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.
joe@joe-laptop:~$ 

Am I making progress here????

---

### Post by aktiwers on 2008-07-13
Let us know how it works for you :)

You have simply been unlucky with the support of the wireless card, when you get it working you can be sure the rest wont be as hard, really!

The guide I posted above should work, note you can copy/paste into the Terminal from the guide, using CTRL+C to copy and SHIFT+INSERT to paste into terminal!

Also in step 4 of the guide, you might want to make sure the path to the driver is identical with  your location of the driver.

```

sudo ndiswrapper -i [COLOR=Red]/tmp/DRIVER/bcmwl5.inf
```
[/COLOR]
That path should fit  the path on your computer. If you are unsure just delete the path in red here and drag/drop the file into the terminal..

Good luck pal

---

### Post by aktiwers on 2008-07-13
You should not double-click the exe file. Right-click it and pick "Extract here"

EDIT:
If you are getting confused, let me know.. I will write it down for you step by step ;)

---

### Post by aktiwers on 2008-07-13
> **MrJoeyUK said:**
> 

Am I making progress here????

yes we are almost there! ;)

---

### Post by MrJoeyUK on 2008-07-13
Ok, I attempted to re-download the driver only to have it stop at 10% and now wont start again at all.. not even a 'save file' box before starting. Just my luck.. maybe it's a problem with the dell servers. 

It's kinda funny, you can be a master at windows but linux is a whole different ball game, I feel like a computer noob all over again on linux.

Could someone else try it? [http://ftp.us.dell.com/network/R174291.exe](http://ftp.us.dell.com/network/R174291.exe) just to confirm it is infact not downloading, and it isn't just me and my so far extremely bad luck with ubuntu

---

### Post by aktiwers on 2008-07-13
Hang in there :)

Im downloading it now.. lets see if it stops on 10% (Im on a slow connection here).

I trust me I know how you feel - I felt the same way switching to Linux, though I must say that I learned Linux way faster than Windows. The first 2 weeks are hard, then the fun begins and when everything setup and configured it runs like a dream. At least for me and the PCs I have installed it on.

Edit:
the download is on 20% now
Its on 40% now..  try downloading it again

---

### Post by Tim Sharitt on 2008-07-13
The problem most likely isn't with the file you downloaded. The problem is that it is a windows executable. To use that driver you must extract the driver in windows first and transfer it to ubuntu. 
Alternatively, to avoid using ndiswrapper altogether, open a terminal and type:
```
sudo apt-get install b43-fwcutter
``` 
It should come up with a prompt asking if you want to download the firmware, type y and [Enter]. You may have to reboot once to reload the driver.

---

### Post by aktiwers on 2008-07-13
> **Tim Sharitt said:**
> The problem most likely isn't with the file you downloaded. The problem is that it is a windows executable. To use that driver you must extract the driver in windows first and transfer it to ubuntu. 
Alternatively, to avoid using ndiswrapper altogether, open a terminal and type:
```
sudo apt-get install b43-fwcutter
```It should come up with a prompt asking if you want to download the firmware, type y and [Enter]. You may have to reboot once to reload the driver.


You can extract the exe on Ubuntu as well ;) 

Right-click and pick "extract here"

---

### Post by MrJoeyUK on 2008-07-13
> **Tim Sharitt said:**
> The problem most likely isn't with the file you downloaded. The problem is that it is a windows executable. To use that driver you must extract the driver in windows first and transfer it to ubuntu. 
Alternatively, to avoid using ndiswrapper altogether, open a terminal and type:
```
sudo apt-get install b43-fwcutter
``` 
It should come up with a prompt asking if you want to download the firmware, type y and [Enter]. You may have to reboot once to reload the driver.

Okay done. It made a long list blah blah I rebooted and took my ethernet cable out, still hasn't recognized my wireless. Or is there more steps to be done here? :popcorn:

EDIT: The download is starting now.. strange, anyway I guess I don't need that anymore

---

### Post by Tim Sharitt on 2008-07-13
Did you already blacklist the b43 driver? From a terminal try:
```
sudo modprobe b43
```
Also, When you click on the network manager icon in the system tray, does it show a wireless network.

---

### Post by MrJoeyUK on 2008-07-13
> **Tim Sharitt said:**
> Did you already blacklist the b43 driver? From a terminal try:
```
sudo modprobe b43
```

joe@joe-laptop:~$ sudo modprobe b43
[sudo] password for joe: 
joe@joe-laptop:~$ 

No news means good news right?

But yeah I've already done the 'echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist' command.

---

### Post by Tim Sharitt on 2008-07-13
The only other thing I can think of is that possibly your wireless card still uses the old driver. In that case you could try:
```
sudo apt-get install bcm43xx-fwcutter
```
This is the firmware for the legacy driver without crypto support. To avoid rebooting after this installs try:
```
sudo rmmod bcm43xx
sudo rmmod b43
sudo modprobe bcm43xx
```

---

### Post by Tim Sharitt on 2008-07-13
As a side note, you may have to select the wireless network from the network manager icons pull down menu (left-click on the network icon beside the clock).

---

### Post by MrJoeyUK on 2008-07-13
sudo apt-get install bcm43xx-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  bcm43xx-fwcutter
0 upgraded, 1 newly installed, 0 to remove and 18 not upgraded.
Need to get 25.8kB of archives.
After this operation, 119kB of additional disk space will be used.
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe bcm43xx-fwcutter 1:006-3 [25.8kB]
Fetched 25.8kB in 0s (175kB/s)          
Preconfiguring packages ...
Selecting previously deselected package bcm43xx-fwcutter.
(Reading database ... 95875 files and directories currently installed.)
Unpacking bcm43xx-fwcutter (from .../bcm43xx-fwcutter_1%3a006-3_i386.deb) ...
Setting up bcm43xx-fwcutter (1:006-3) ...
--06:29:02--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
           => `wl_apsta.o'
Resolving downloads.openwrt.org... 195.56.146.238
Connecting to downloads.openwrt.org|195.56.146.238|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 652,866 (638K) [application/x-object]

100%[====================================>] 652,866      242.72K/s             

06:29:05 (242.15 KB/s) - `wl_apsta.o' saved [652866/652866]


  filename   :  wl_apsta.o
  version    :  3.130.20.0
  MD5        :  e08665c5c5b66beb9c3b2dd54aa80cb3
  microcodes :  2 4 5 11 
  pcms       :  4 5 

  microcode  :  2
  revision   :  0x0127
  patchlevel :  0x000e
  date       :  2005-04-18
  time       :  02:36:27

  microcode  :  4
  revision   :  0x0127
  patchlevel :  0x000e
  date       :  2005-04-18
  time       :  02:36:27

  microcode  :  5
  revision   :  0x0127
  patchlevel :  0x000e
  date       :  2005-04-18
  time       :  02:36:27

  microcode  :  11
  revision   :  0x0127
  patchlevel :  0x000e
  date       :  2005-04-18
  time       :  02:36:27

extracting bcm43xx_microcode2.fw ...
extracting bcm43xx_microcode4.fw ...
extracting bcm43xx_microcode5.fw ...
extracting bcm43xx_microcode11.fw ...
extracting bcm43xx_pcm4.fw ...
extracting bcm43xx_pcm5.fw ...
extracting bcm43xx_initval01.fw ...
extracting bcm43xx_initval02.fw ...
extracting bcm43xx_initval03.fw ...
extracting bcm43xx_initval04.fw ...
extracting bcm43xx_initval05.fw ...
extracting bcm43xx_initval06.fw ...
extracting bcm43xx_initval07.fw ...
extracting bcm43xx_initval08.fw ...
extracting bcm43xx_initval09.fw ...
extracting bcm43xx_initval10.fw ...

joe@joe-laptop:~$ sudo rmmod bcm43xx
**ERROR: Module bcm43xx does not exist in /proc/modules**
joe@joe-laptop:~$ sudo rmmod b43
joe@joe-laptop:~$ sudo modprobe bcm43xx

Am i truly screwed? :(

---

### Post by MrJoeyUK on 2008-07-13
You mean the two overlapping black screens icon? all that's appearing is Wired Network, Connect to 802.1x Protected Wired Network, and Manual Configuration

---

### Post by Tim Sharitt on 2008-07-13
Does anything happen when you click on "Connect to 802.1x Protected Wired Network"?

---

### Post by MrJoeyUK on 2008-07-13
Yeah.. a box comes up with Network Name, EAP Method, Phase 2 type, Identity, Password, etc etc but that's for a wired network right? (presumably the one i'm using now..)

Maybe I should come back another day, when different people are on.. this is stressin me out lol

---

### Post by Tim Sharitt on 2008-07-13
That should be your wireless network. Type in whatever passwords are required for your network (should be the same as you use in windows) and you should be ready to go.

---

### Post by ugm6hr on 2008-07-13
@MrJoeyUK:
There are lots of people trying to help you here, but it seems you're not having much luck with ndiswrapper.

The first option for BCM4310 is usually the native Linux driver. This can be reached from Hardware Drivers in System->Administration, and generally appears as wl or b43.  

Unfortunately, there has recently been a problem with this.  Nevertheless, it appears to have been fixed in the "hardy-proposed" repository (see your Software Sources in System->Administration).

You would have to edit your blacklist file again to try this (i.e. blacklist ndiswrapper and unblacklist everything else).

Read more: [http://ubuntuforums.org/showthread.php?t=848622](http://ubuntuforums.org/showthread.php?t=848622)

EDIT: The original How-To: [http://ph.ubuntuforums.com/showthread.php?t=779754](http://ph.ubuntuforums.com/showthread.php?t=779754)

---

### Post by MrJoeyUK on 2008-07-13
> **Tim Sharitt said:**
> That should be your wireless network. Type in whatever passwords are required for your network (should be the same as you use in windows) and you should be ready to go.

Well I tried that. I don't have a pass on my network,so I just typed in my network name and clicked connect and nothing happened.. it just told me a passphrase or encryption key is required. I took all of my security off my network months ago (silly, I know).

The thing which gets me is I was running 8.04 yesterday through VirtualBox and it connected to my wireless then.. I mean that practically installs everything exactly the same right?

---

### Post by ugm6hr on 2008-07-13
> **Tim Sharitt said:**
> That should be your wireless network. Type in whatever passwords are required for your network (should be the same as you use in windows) and you should be ready to go.

This is not for wifi:
> Connect to 802.1x Protected **Wired** Network

---

### Post by Tim Sharitt on 2008-07-13
Sorry, I'm blind i guess.

---

### Post by aktiwers on 2008-07-13
I also sent you this PM, but what the heck I post it here too:

Now reading through your post it seams like you have done most already. I will write it down step by step for you and you can skip the steps you already done. Or do them all to be sure you have done them.

1) Download the driver to your desktop
[http://ftp.us.dell.com/network/R174291.exe](http://ftp.us.dell.com/network/R174291.exe)

2) Extract the file. Right-click and pick "extract here".
(If there is no suck option open terminal and type:
```
unzip R17491.exe
```Argh! Now you have tons of files on your Desktop. Delete them all except for the DRIVER_US folder.

3) Now make sure you have Ndiswrapper installed
```
sudo apt-get install ndiswrapper-common ndiswrapper-utils ndisgtk
```4) Blacklist the older driver:
```
echo 'blacklist bcm43' | sudo tee -a /etc/modprobe.d/blacklist 
```5) Install the windows driver with ndiswrapper:
```
sudo ndiswrapper -i /home/joe/Desktop/DRIVER_US/bcmwl5.inf 
```6) Make sure it is installed
```
ndiswrapper -l 
```If the output looks okay [wifi name ect..  ]

The lets do the last steps

7)
```
sudo depmod -a 
sudo modprobe ndiswrapper 
```8) Make ndiswrapper load on startup
```
gksudo gedit /etc/modules
```and add the word: ndiswrapper

9) Restart X hit CTRL+ALT+Backspace

Now log back in and right-click your network manager icon that is located close to your clock and make sure it has Wireless enabled.

Then left-click and see if it gives you a list of wireless connections.

---

### Post by MrJoeyUK on 2008-07-13
To all who care (no doubt some of you have got tired of me, I got to stage 5-6 and had the following..

joe@joe-laptop:~$ sudo apt-get install ndiswrapper-common ndiswrapper-utils ndisgtk
[sudo] password for joe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-common is already the newest version.
Package ndiswrapper-utils is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  ndiswrapper-common
E: Package ndiswrapper-utils has no installation candidate
joe@joe-laptop:~$ echo 'blacklist bcm43' | sudo tee -a /etc/modprobe.d/blacklist
blacklist bcm43
joe@joe-laptop:~$ sudo ndiswrapper -i /home/joe/Desktop/DRIVER_US/bcmwl5.inf
driver bcmwl5 is already installed
joe@joe-laptop:~$ ndiswrapper -l
bcmwl5 : invalid driver!
joe@joe-laptop:~$

---

### Post by cosine352 on 2008-07-13
have you tried this?

[http://www.linuxwireless.org/en/users/Drivers/b43#devicefirmware]("http://www.linuxwireless.org/en/users/Drivers/b43#devicefirmware")

---

### Post by aktiwers on 2008-07-13
Im sorry this is so much trouble..  will you try this guide then?
[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

Its made for exactly your card.

Before you do, please remove the driver we installed:
```
ndiswrapper -e  bcmwl5.inf
```

Again I am sorry this is such a hassle for you, when this is done you will be able to enjoy your Ubuntu much more painless I hope :)

Wireless cards are really a thing that keep away new people.  

Good luck

---

### Post by falcon61102 on 2008-07-13
Hey, sorry I dropped off the planet for a while... our server went down at work.

It sounds like you have the driver installed, but I'm guessing you still can't connect.  Be patient and run this old command:
```
lshw -C network
```

Look at towards the bottom of your wireless entry, the one that says wlan0 and has information about Broadcom... if it says Module=ssb, that's probably your problem.  Let me know and I'll walk you through fixing it.  You are almost there.  Just a little more patience.

---

### Post by falcon61102 on 2008-07-13
Ok... This is going to be a compilation of two HowTo's:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper))

Because you already have some drivers and ndiswrapper installed, we have to do a little back tracking before we can do a fresh install.  I'm going to try to take this slow to make sure that I get it all right and that it will be easy to follow.

Make sure you are connected via your wired internet connection for this one.

The first thing we want to do is stop ndiswrapper and the other modules from running:
```
sudo rmmod ndiswrapper
sudo rmmod b44
sudo rmmod b43
sudo rmmod b43legacy
sudo rmmod ssb
```

Now that we don't have any modules loaded in the kernal we can remove the old ones and install the new ones.  

First we want to blacklist the drivers we don't want to run.  To do this we need to edit the blacklist.
```
sudo gedit /etc/modprobe.d/blacklist
```

If it's not already listed you want to add the following entries:
```
blacklist bcm43xx
blacklist ssb
```
Save and Close the File.

Since you have tried installing previous drivers and it didn't work, we want to start with a clean slate.  

To Unistall your current drivers:
```
sudo ndiswrapper -r bcmwl5
```

To remove ndiswrapper:
```
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper
```

REBOOT

Now it's time for a fresh install (hopefully the last one you're going to do).
```
sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`
sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build
mkdir -p ~/bcm43xx/ndiswrapper; cd ~/bcm43xx/ndiswrapper
sudo wget http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.53.tar.gz -Ondiswrapper.tar.gz
tar xvzf ndiswrapper.tar.gz
cd ndiswrapper*
make distclean
make
sudo make install
```

This is going to download the newest version of ndiswrapper and extract it to a folder in your Home directory.  It is then going to make the install to use.

Now it's time to download the correct drivers for your card.  Based on lspci you have a Broadcom Corporation BCM4310 USB Controller (rev 01) so you need the following drivers:
```
 cd ~/bcm43xx
wget http://myspamb8.googlepages.com/R174291-pruned.zip
unzip R174291-pruned.zip
```

That will download and unzip the drivers into the bcm43xx folder in you Home folder.

To reinstall the drivers using ndiswrapper you should be able to copy and paste this:
```
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
```

Once that completes the new drivers should be installed.  You may see your Wireless access points listed now.  If so, you're good to go.  Based on experience with that card, you're going to have to use the Hardy Bug Fix though.  To test this run:
```
sudo lshw -C network
```

Under the section for your wireless card you should see a line towards the bottom that contains "Module=".  If that says Module=ssb then you need the bug fix:
```
sudo rmmod b43
sudo rmmod b44
sudo rmmod b43legacy #this step added Apr 27 2008
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
sudo modprobe b44
```

Try that sequence first, see if you can see the wireless access points in under "Wireless Networks" and run:
```
sudo lshw -C network
```
To see if it still says Module=ssb.  If you can access the net and you no longer see Module=ssb then you got it, if not skip this next step and go down below.  To ensure that your system loads these settings at boot use the following:
```
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper 
```


If the above settings didn't work, go through the above bug fix again, this time stopping once you reach:
```
sudo modprobe ndiswrapper
```
And then try to access your wireless.  You should now have access if the above didn't work.  Again you are going to want to ensure these load up at each boot so run:
```
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS' | sudo tee -a /etc/modprobe.d/ndiswrapper 
```

You should now be able to get online.  I hope so anyway... :)

Like I said in the beginning, this is a compilation of:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper))

And all credit due for figuring all this out goes to the orinal writers (can't find their names).

---

### Post by MrJoeyUK on 2008-07-13
Ok everyone, after over 24 hours the problem is finally fixed.. Now I can enjoy the Linux experience. I'd like to thank all who contributed to helping me, especially aktiwers and falcon61102, I think I would of commited suicide by now if it weren't for these two. :)

---

