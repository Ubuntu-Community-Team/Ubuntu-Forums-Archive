---
title: "HOWTO: RT2500, etc. wireless cards"
date: 2007-09-30
forum: Outdated Tutorials &amp; Tips
---

### Post by wieman01 on 2007-09-30
**Dapper Drake** users should take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=192588") if this one doesn't work. This guide was tested with **Feisty Fawn**, **Gutsy Gibbon**, and **Hardy Heron**. 
--
To all **RT73** users, please also see [this post]("http://ubuntuforums.org/showthread.php?p=4732883"). Thanks to [Kiefer Rodriguez]("http://ubuntuforums.org/member.php?u=490665") for this solution.

Please post to this [Launchpad bug report]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/163020") with all of your specs, if you have problems with a Ralink based wireless adapter.

This is a simple guide for all Ralink based wireless adapters and everyone who wants to replace the Linux driver with "ndiswrapper" (e.g. because you want to make use of either [Network Manager]("http://www.gnome.org/projects/NetworkManager/") or [WICD]("http://wicd.sourceforge.net/")). 
[B]
_INSTRUCTIONS:_[/B]
[LIST]
[*]Get the latest version of the Windows driver for your card from [Linksys' website]("http://www.linksys.com/servlet/Satellite?c=L_CASupport_C1&childpagename=US%2FLayout&cid=1166859840888&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4088837314B372&displaypage=download") or from the CD that came with your device (whatever vendor). 
[/LIST]

[LIST]
[*]Install "ndiswrapper" package **with** working internet connection (Ethernet):
> sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
[/LIST]

[LIST]
[*]Install "ndiswrapper" package **without** working internet connection (alternatively, install it via Synaptic/Adept):
> sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
[/LIST]

[LIST]
[*]Load new driver module (may not be necessary any longer, but does no harm either):
> sudo depmod -a
sudo modprobe ndiswrapper

[/LIST]

[LIST]
[*]Add the module to "/etc/modules" to have it load automatically:
> echo 'ndiswrapper' | sudo tee -a /etc/modules
[/LIST]

[LIST]
[*]Create alias directive:
> sudo ndiswrapper -m
[/LIST]

[LIST]
[*]Pick a valid Ralink driver based on the chipset of your card (you might blacklist all of them if you are not sure):
> rt2500usb
rt2500pci
rt2500
rt2570
rt73usb
rt73pci
rt73
rt61usb
rt61pci
rt61
rt2860
rt2860sta
rt2x00usb
rt2x00lib
[/LIST]

[LIST]
[*]Blacklist Ralink driver:
> echo 'blacklist [COLOR="Green"]<your_ralink_driver>[/COLOR]' | sudo tee -a /etc/modprobe.d/blacklist
[/LIST]

[LIST]
[*]Now unzip the driver archive you have just downloaded (e.g. in your home directory):
> unzip [COLOR="Green"]<driver_archive>[/COLOR][COLOR="Red"].exe[/COLOR]
[/LIST]

[LIST]
[*]Now find the right driver in the resulting folder & deploy it (folder should also contain other driver files i.e. .cat, .sys):
> sudo ndiswrapper -i [COLOR="Green"]<your_ralink_driver>[/COLOR][COLOR="Red"].inf[/COLOR]
[/LIST]

[LIST]
[*]Make sure it has installed correctly:
> ndiswrapper -l
[/LIST]

[LIST]
[*]The output should yield something like this:
> [COLOR="Blue"]rt2500usb : driver installed
device (13B1:000D) present (alternate driver: rt2500usb)[/COLOR]

[/LIST]

[LIST]
[*]Last but not least open this file...
> sudo gedit /etc/network/interfaces
[/LIST]

[LIST]
[*]...and add these 2 lines if they are not there yet [COLOR="Red"][also try _without_ adding them if Network Manager does not pick up the card & reboot][/COLOR]:
> auto wlan0
iface wlan0 inet dhcp
[/LIST]
You can  now safely delete the extracted driver files & folders. Then reboot the computer and see if you can connect using your favorite networking applet (e.g. Network Manager, WICD, Wifi Radar, etc.). 

Feedback is - as always - appreciated.

_**CHANGE LOG:**_
30/09/2007: Minor fixes.
07/10/2007: Expanded "blacklist".
20/10/2007: Added missing part concerning "interfaces" file.
22/10/2007: Load module "ndiswrapper" at boot.
23/10/2007: Enhanced blacklist.
07/11/2007: Bug fix for Network Manager.
12/11/2007: Updated blacklist & module section.
13/01/2008: Launchpad bug report.
15/04/2008: Update for Hardy.
17/04/2008: RT73 note.

---

### Post by grovulent on 2007-09-30
No luck...

My problem I think is in finding a reliable copy of the windows drivers.  I can't extract them from the exe on the ralink website (cabextract, and various windows programs don't work).  so I've been trying random rt2500.inf files (+ sys and cat) found through googling.

The first set I found caused the same freeze problem when it tried to connect, the second wouldn't install via ndiswrapper - received an error 'couldn't find models section "insert model here" for multiple models.

Anyone know where to find the actual latest inf, sys, cat files?

---

### Post by wieman01 on 2007-09-30
> **grovulent said:**
> No luck...

My problem I think is in finding a reliable copy of the windows drivers.  I can't extract them from the exe on the ralink website (cabextract, and various windows programs don't work).  so I've been trying random rt2500.inf files (+ sys and cat) found through googling.

The first set I found caused the same freeze problem when it tried to connect, the second wouldn't install via ndiswrapper - received an error 'couldn't find models section "insert model here" for multiple models.

Anyone know where to find the actual latest inf, sys, cat files?
What wireless adapter have you got? You did not find anything on the vendor's website?

---

### Post by grovulent on 2007-09-30
> **wieman01 said:**
> What wireless adapter have you got? You did not find anything on the vendor's website?

Ah - silly me...  didn't think to check the laptop makers site (MSI) - downloaded their driver.. but the latest they offer is from august 2006 (whereas ralink has updated as of 2007).  Tried it - no luck - same hanging problem.  Full reboot required each time.

Might have to email MSI to see if they can release a later driver.

---

### Post by bapoumba on 2007-09-30
[https://bugs.launchpad.net/ubuntu/+bug/34902](https://bugs.launchpad.net/ubuntu/+bug/34902)
I ran in the problem yesterday...
I bought this card because it was supported. My home network is wired now, so I was not using it any longer. But yesterday, I had to when I went to my LUG's install party.

I'm not sure I'm willing to try win drivers for a chipset that used to be fully supported. Am I missing something? (in that case, please accept my apologies).

---

### Post by wieman01 on 2007-09-30
> **grovulent said:**
> Ah - silly me...  didn't think to check the laptop makers site (MSI) - downloaded their driver.. but the latest they offer is from august 2006 (whereas ralink has updated as of 2007).  Tried it - no luck - same hanging problem.  Full reboot required each time.

Might have to email MSI to see if they can release a later driver.
Do you run Feisty or Gutsy? I used to have these lockups in Dapper,  but compiling the latest "ndiswrapper" from source did solve the problem later on. No more hanging.

---

### Post by wieman01 on 2007-09-30
> **bapoumba said:**
> [https://bugs.launchpad.net/ubuntu/+bug/34902](https://bugs.launchpad.net/ubuntu/+bug/34902)
I ran in the problem yesterday...
I bought this card because it was supported. My home network is wired now, so I was not using it any longer. But yesterday, I had to when I went to my LUG's install party.

I'm not sure I'm willing to try win drivers for a chipset that used to be fully supported. Am I missing something? (in that case, please accept my apologies).
If you want to use GNOME Network Manager, you don't have a choice at the moment. You can always configure it manually by editing "/etc/network/interfaces", but I find that too big a hassle.

_**EDIT:**_
This thread is a good reference: [http://ubuntuforums.org/showthread.php?t=560229]("http://ubuntuforums.org/showthread.php?t=560229")

---

### Post by bapoumba on 2007-09-30
> **wieman01 said:**
> If you want to use GNOME Network Manager, you don't have a choice at the moment. You can always configure it manually by editing "/etc/network/interfaces", but I find that too big a hassle.
Hmm.. I removed completely network-manager, working with the conf files (n-m does not handle switching from DHCP to static IP very well..). End of the off-topic, thanks for the input, wieman01 :)

---

### Post by wieman01 on 2007-09-30
> **bapoumba said:**
> Hmm.. I removed completely network-manager, working with the conf files (n-m does not handle switching from DHCP to static IP very well..). End of the off-topic, thanks for the input, wieman01 :)
Yeah, static IPs are still an issue. Very sad... That's what keep me from using Network Manager as well.

---

### Post by bapoumba on 2007-09-30
> **wieman01 said:**
> Yeah, static IPs are still an issue. Very sad... That's what keep me from using Network Manager as well.
Have you checked [wicd]("http://wicd.sourceforge.net/")? Works perfectly with feisty (I'm with gutsy on this laptop).

---

### Post by wieman01 on 2007-09-30
> **bapoumba said:**
> Have you checked [wicd]("http://wicd.sourceforge.net/")? Works perfectly with feisty (I'm with gutsy on this laptop).
I know it does, but I have been reluctant because I don't want to use a 3rd party tool as much as I appreciate their effort. I might have to resort to it though... It makes me furious that Canonical don't get a grip on it. Such a basic feature.

Thanks anyway, mate.

---

### Post by bapoumba on 2007-09-30
> **wieman01 said:**
> I know it does, but I have been reluctant because I don't want to use a 3rd party tool as much as I appreciate their effort. I might have to resort to it though... It makes me furious that Canonical don't get a grip on it. Such a basic feature.

Thanks anyway, mate.
Agreed :)
And you're welcome!

---

### Post by grovulent on 2007-09-30
> **wieman01 said:**
> Do you run Feisty or Gutsy? I used to have these lockups in Dapper,  but compiling the latest "ndiswrapper" from source did solve the problem later on. No more hanging.


Recently upgraded from feisty to gutsy in the hope wireless would improve.  I used to be able to get it to work in feisty by editing the interfaces file... but that doesn't work anymore.

I must admit I really don't know what compiling the latest 'ndiswrapper' involves...

---

### Post by wieman01 on 2007-09-30
> **grovulent said:**
> Recently upgraded from feisty to gutsy in the hope wireless would improve.  I used to be able to get it to work in feisty by editing the interfaces file... but that doesn't work anymore.

I must admit I really don't know what compiling the latest 'ndiswrapper' involves...
Gutsy should not have such a problem. So I don't think it has anything to do with the package, but the driver, don't you think so? Gutsy works fine for me.

---

### Post by odiseo77 on 2007-09-30
Hi, I'm using a card with the rt2500 chipset on Feisty and I'll upgrade to Gutsy Gibbon as soon as the stable version comes out, but I have a question, why using ndiswrapper when these chipsets are supposed to be fully supported in Ubuntu? You mean they don't work very well in Gutsy? (Feisty's default driver is working like a charm here, in spite of the fact I'm using a smp kernel on a core 2 duo machine).

---

### Post by wieman01 on 2007-09-30
> **odiseo77 said:**
> Hi, I'm using a card with the rt2500 chipset on Feisty and I'll upgrade to Gutsy Gibbon as soon as the stable version comes out, but I have a question, why using ndiswrapper when these chipsets are supposed to be fully supported in Ubuntu? You mean they don't work very well in Gutsy? (Feisty's default driver is working like a charm here, in spite of the fact I'm using a smp kernel on a core 2 duo machine).
It is meant for those users that want to be able to use Network Manager or WICD. I suppose that you got it working through command line only, right?

---

### Post by odiseo77 on 2007-09-30
Yes, I edited my /etc/network/interfaces file to my like and my wireless connection is working like a charm here. Thanks for clarify this to me, I was getting scared about the idea of using ndiswrapper :)

---

### Post by wieman01 on 2007-09-30
> **odiseo77 said:**
> Yes, I edited my /etc/network/interfaces file to my like and my wireless connection is working like a charm here. Thanks for clarify this to me, I was getting scared about the idea of using ndiswrapper :)
Yeah, I hate to use as well, but hey, no choice. Thanks for asking, I have updated the thread and highlighted the purpose of this thread. It was indeed misleading.

---

### Post by Logarithymic on 2007-09-30
I'm using feisty fawn and tried this tutorial, followed it step by step, and WICD still won't connect for me!
I'm using WEP if that makes any difference.

---

### Post by odiseo77 on 2007-09-30
> **Logarithymic said:**
> I'm using feisty fawn and tried this tutorial, followed it step by step, and WICD still won't connect for me!
I'm using WEP if that makes any difference.

Maybe you should open a new topic since this one is related to Gutsy Gibbon? :) Anyway, if you're using WEP, then it's fairly easy to connect to your AP; simply go to 'System>Administration>Network', select the wireless interface and click on properties, enter your settings there, then click on accept, check the checkbox at the left of your wireless interface (on the main window) and it should work.

---

### Post by Logarithymic on 2007-09-30
> **odiseo77 said:**
> Maybe you should open a new topic since this one is related to Gutsy Gibbon? :) Anyway, if you're using WEP, then it's fairly easy to connect to your AP; simply go to 'System>Administration>Network', select the wireless interface and click on properties, enter your settings there, then click on accept, check the checkbox at the left of your wireless interface (on the main window) and it should work.



Didn't work :(

---

### Post by odiseo77 on 2007-09-30
> **Logarithymic said:**
> Didn't work :(

hmm, weird. Sorry if I can't be of help here, but then I'd suggest you to open a new thread in the '[Networking & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=136")' section of the forum.

Greetings.

---

### Post by grovulent on 2007-09-30
> **wieman01 said:**
> Gutsy should not have such a problem. So I don't think it has anything to do with the package, but the driver, don't you think so? Gutsy works fine for me.

Yeah - it does sound like the driver... I'd like to get my hands on the latest version from ralink...

The files should be the same right?  ie... inf, sys and cat - no matter the specific vendor?  So if anyone could post the latest versions of the driver files somewhere I'd greatly appreciate it.

---

### Post by grovulent on 2007-10-01
Sorry for double post - managed to get the latest drivers from Ralink via email.  If anyone else needs them feel free to PM me.

I'll test em out tonight.  Here's hoping.

---

### Post by wieman01 on 2007-10-01
> **grovulent said:**
> Yeah - it does sound like the driver... I'd like to get my hands on the latest version from ralink...

The files should be the same right?  ie... inf, sys and cat - no matter the specific vendor?  So if anyone could post the latest versions of the driver files somewhere I'd greatly appreciate it.
Yes, the files should be the same.

---

### Post by wieman01 on 2007-10-01
> **grovulent said:**
> Sorry for double post - managed to get the latest drivers from Ralink via email.  If anyone else needs them feel free to PM me.

I'll test em out tonight.  Here's hoping.
If you happen to have a link I could include it in my tutorial... just a thought.

---

### Post by wieman01 on 2007-10-01
> **Logarithymic said:**
> Didn't work :(
Now when you scan for other networks, what is the output?
> sudo iwlist scan
And what does this one one?
> sudo ndiswrapper -l
What sort of card have you got & what chipset?

---

### Post by Logarithymic on 2007-10-01
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

vmnet1    Interface doesn't support scanning.

vmnet8    Interface doesn't support scanning.

rausb0    No scan results

```

```
rt2500usb : driver installed
        device (13B1:000D) present (alternate driver: rt2570)

```

Card: WUSB54G
Chipset: Ralink something :-\

---

### Post by wieman01 on 2007-10-02
**@Logarithymic:**

Have you really blacklisted "rt2500usb"?

Second you need to edit your interfaces file. Do this:
> sudo gedit /etc/network/interfaces
Now replace the contents with this (don't worry, it's safe):
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
That should do. Now restart the computer and scan once again:
> sudo iwlist scan
Any results?

---

### Post by jgrf77 on 2007-10-02
ok..............i failed at the first hurdle.  Im very new to this so any help is really appreciated. here´s what happened

justin@Justinotronic:~$ sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-utils-1.9

any ideas?

cheers

---

### Post by wieman01 on 2007-10-02
> **jgrf77 said:**
> ok..............i failed at the first hurdle.  Im very new to this so any help is really appreciated. here´s what happened

justin@Justinotronic:~$ sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-utils-1.9

any ideas?

cheers
Yes, please open Synaptic and check for package "ndiswrapper-util". You might have a different version number in the repositories depending on the version of Ubuntu you are running. Can you find it? Perhaps "ndiswrapper-utils-1.8"?

---

### Post by mehaga on 2007-10-02
Hi all,

I am also having trouble with WEP :S

I have a Linksys WUSB54G card on my Ubuntu desktop, and an Intel card on my laptop.

I am trying to connect my laptop with my desktop (ad hoc), with static IPs.

I tried network manager, wifi radio, wcid, kwifi... and console (iwconfig).

If I disable encryption, I get connected pretty easy. 

When I enable WEP though, on my laptop (XP), I see a connection established but only for few seconds.

When connection is lost, XP shows my ESSID set in Ubuntu (which is the same as the one in XP) as a new network that has encryption disabled.

From errors I get from 
   iwconfig wlan0 key open 12345
I concluded that this needs to be more like
  iwconfig wlan0 key open 3132333435 ([http://www.andrewscompanies.com/tools/wep.asp]("http://www.andrewscompanies.com/tools/wep.asp"))


So, then I tried all combination of  generated WEP keys and passphrases on both computers, quotes, no quotes...

This reminds me of configuring PEAP on SuSE, couple of years ago, but it shouldn't be that difficult...

I slept only few hours, took a day off, have a horrible headache...

Help! :)

Edit: I forgot to mention that I first tried with rt2500, but iwconfig showed no wifi cards...

---

### Post by wieman01 on 2007-10-02
> **vekaz said:**
> Hi all,

I am also having trouble with WEP :S

I am trying to connect my laptop with my desktop (ad hoc), with static IPs.

I tried network manager, wifi radio, wcid, kwifi... and console (iwconfig).

If I disable encryption, I get connected pretty easy. 

When I enable WEP though, on my laptop (XP), I see a connection established but only for few seconds.

When connection is lost, XP shows my ESSID set in Ubuntu (which is the same as the one in XP) as a new network that has encryption disabled.

From errors I get from 
   iwconfig wlan0 key open 12345
I concluded that this needs to be more like
  iwconfig wlan0 key open 3132333435 ([http://www.andrewscompanies.com/tools/wep.asp]("http://www.andrewscompanies.com/tools/wep.asp"))


So, then I tried all combination of  generated WEP keys and passphrases on both computers, quotes, no quotes...

This reminds me of configuring PEAP on SuSE, couple of years ago, but it shouldn't be that difficult...

I slept only few hours, took a day off, have a horrible headache...

Help! :)
Hi, 

This post does not really belong here. Please open your own thread. No disrespect meant.

---

### Post by mehaga on 2007-10-02
I saw other people talking about WEP problems, so...

OK, I'm leaving :)

---

### Post by fulat2k on 2007-10-03
Hey folks,

Tried the ndiswrapper method, but couldn't work.  I'm  using a DLink DWL-G122 Rev B1 USB stick.  Out of the box, GG was able to detect and load the appropriate driver.  However, performing a iwlist wlan0 scanning doesn't return any results.

But all is not lost :)  Blacklisted the rt2500usb module.  Download the latest CVS tar ball for rt2570 (USB) from [http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads).  Make sure it's the latest CVS tarball, the beta doesn't compile in GG.  

Follow the instructions in the README to create an alias in /etc/modprobe.conf.  You may have to create the file if it's not there.  Then change wlan0 to rausb0 in /etc/network/interfaces.  Reboot and it should work.  

One thing's missing though, network-manager didn't detect rausb0 as a wireless device :(

Hope this helps someone.

---

### Post by wieman01 on 2007-10-04
> **fulat2k said:**
> Hey folks,

Tried the ndiswrapper method, but couldn't work.  I'm  using a DLink DWL-G122 Rev B1 USB stick.  Out of the box, GG was able to detect and load the appropriate driver.  However, performing a iwlist wlan0 scanning doesn't return any results.

But all is not lost :)  Blacklisted the rt2500usb module.  Download the latest CVS tar ball for rt2570 (USB) from [http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads).  Make sure it's the latest CVS tarball, the beta doesn't compile in GG.  

Follow the instructions in the README to create an alias in /etc/modprobe.conf.  You may have to create the file if it's not there.  Then change wlan0 to rausb0 in /etc/network/interfaces.  Reboot and it should work.  

One thing's missing though, network-manager didn't detect rausb0 as a wireless device :(

Hope this helps someone.
That's why I wrote this tutorial actually. NM does not work with native Ralink drivers yet.

---

### Post by jgrf77 on 2007-10-04
Thanks for that.  Progress has been made.  Unfortunately progress has been halted once again.

Here´s what happened

justin@Justinotronic:~$ sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.8
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-common ndiswrapper-utils-1.8
0 upgraded, 2 newly installed, 0 to remove and 5 not upgraded.
Need to get 42.6kB of archives.
After unpacking 213kB of additional disk space will be used.
Get:1 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) edgy/main ndiswrapper-common 1.18-1ubuntu2 [13.7kB]
Get:2 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) edgy/main ndiswrapper-utils-1.8 1.18-1ubuntu2 [29.0kB]
Fetched 42.6kB in 1s (23.1kB/s)               
Selecting previously deselected package ndiswrapper-common.
(Reading database ... 118215 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.18-1ubuntu2_all.deb) ...
Selecting previously deselected package ndiswrapper-utils-1.8.
Unpacking ndiswrapper-utils-1.8 (from .../ndiswrapper-utils-1.8_1.18-1ubuntu2_i386.deb) ...
Setting up ndiswrapper-common (1.18-1ubuntu2) ...
Setting up ndiswrapper-utils-1.8 (1.18-1ubuntu2) ...
justin@Justinotronic:~$ sudo depmod -a
justin@Justinotronic:~$ 
justin@Justinotronic:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-11-server/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

Any way to overcome this?  Really appreciate your help.

---

### Post by wieman01 on 2007-10-04
> **jgrf77 said:**
> Thanks for that.  Progress has been made.  Unfortunately progress has been halted once again.

Here´s what happened

justin@Justinotronic:~$ sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.8
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-common ndiswrapper-utils-1.8
0 upgraded, 2 newly installed, 0 to remove and 5 not upgraded.
Need to get 42.6kB of archives.
After unpacking 213kB of additional disk space will be used.
Get:1 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) edgy/main ndiswrapper-common 1.18-1ubuntu2 [13.7kB]
Get:2 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) edgy/main ndiswrapper-utils-1.8 1.18-1ubuntu2 [29.0kB]
Fetched 42.6kB in 1s (23.1kB/s)               
Selecting previously deselected package ndiswrapper-common.
(Reading database ... 118215 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.18-1ubuntu2_all.deb) ...
Selecting previously deselected package ndiswrapper-utils-1.8.
Unpacking ndiswrapper-utils-1.8 (from .../ndiswrapper-utils-1.8_1.18-1ubuntu2_i386.deb) ...
Setting up ndiswrapper-common (1.18-1ubuntu2) ...
Setting up ndiswrapper-utils-1.8 (1.18-1ubuntu2) ...
justin@Justinotronic:~$ sudo depmod -a
justin@Justinotronic:~$ 
justin@Justinotronic:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-11-server/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

Any way to overcome this?  Really appreciate your help.
What system are you on? 64-bit or 32-bit and what version of Ubuntu.

---

### Post by fulat2k on 2007-10-04
> **wieman01 said:**
> That's why I wrote this tutorial actually. NM does not work with native Ralink drivers yet.

Well, at least it works now.  Somehow your tutorial didn't work for me :(

---

### Post by wieman01 on 2007-10-04
> **fulat2k said:**
> Well, at least it works now.  Somehow your tutorial didn't work for me :(
Good to know it does. :-) Thanks for the feedback.

---

### Post by grovulent on 2007-10-04
Well no luck for me unfortunately...

I tried the latest drivers from ralink and the ones listed as working with ndiswrapper (on the list from their website).

I think before I wasn't correctly blacklisting the driver...  I just used rt2500 when I think it should be rt2500pci for me.  I think so because upon checking with the windows driver is installed it lists rt2500pci as the alternative driver.

Unfortunately when I blacklist this driver - the system can no longer detect the wireless device at all.

---

### Post by wieman01 on 2007-10-05
> **grovulent said:**
> Well no luck for me unfortunately...

I tried the latest drivers from ralink and the ones listed as working with ndiswrapper (on the list from their website).

I think before I wasn't correctly blacklisting the driver...  I just used rt2500 when I think it should be rt2500pci for me.  I think so because upon checking with the windows driver is installed it lists rt2500pci as the alternative driver.

Unfortunately when I blacklist this driver - the system can no longer detect the wireless device at all.
What does "ndiswrapper -l" yield after blacklisting the driver & restarting the system?

---

### Post by awakatanka on 2007-10-06
Somehow my blacklist won't work, tryed it on main and on laptop but both still load the driver. 

> 00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:05.0 PCI bridge: Hint Corp HB6 Universal PCI-PCI bridge (non-transparent mode) (rev 11)
00:07.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
00:07.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
00:08.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 04)
00:0a.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
02:08.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
02:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
 and > netmw225 : driver installed
rt2500 : driver installed
        device (1814:0201) present (alternate driver: rt2500pci)

Still got problems with speed and requesting pages where it hangs for seconds before it goes. Other wireless usb is working good without the problems.

Kubuntu gutsy beta fully updated.

---

### Post by wieman01 on 2007-10-06
> **awakatanka said:**
> Somehow my blacklist won't work, tryed it on main and on laptop but both still load the driver. 

 and 
Still got problems with speed and requesting pages where it hangs for seconds before it goes. Other wireless usb is working good without the problems.

Kubuntu gutsy beta fully updated.
Ok, what device have you blacklisted (e.g. rt2500pci) and what hardware have you got?

---

### Post by awakatanka on 2007-10-06
> **wieman01 said:**
> Ok, what device have you blacklisted (e.g. rt2500pci) and what hardware have you got?

blacklisted rt2500 and RT2500

1 pci kaart in main with rt2500 chipset and a pcmcia in laptop with rt2500 chipset.


edit:
Blacklisted the rt2500pci now and seems to work now. only signal strenght is weaker then before. But it works with networkmanager and wpa where it never worked before. but i need to do a modprobe to get it working after a restart

edit 2:
It worked but it wasnt a real improvement same problem, think i need to look a different things for my problem.

---

### Post by wieman01 on 2007-10-07
> **awakatanka said:**
> blacklisted rt2500 and RT2500

1 pci kaart in main with rt2500 chipset and a pcmcia in laptop with rt2500 chipset.


edit:
Blacklisted the rt2500pci now and seems to work now. only signal strenght is weaker then before. But it works with networkmanager and wpa where it never worked before. but i need to do a modprobe to get it working after a restart

edit 2:
It worked but it wasnt a real improvement same problem, think i need to look a different things for my problem.
After doing all the steps you still have to modprobe after restart? Does everything else work now?

---

### Post by grovulent on 2007-10-07
> **wieman01 said:**
> What does "ndiswrapper -l" yield after blacklisting the driver & restarting the system?

hi there - appreciate the help...

It says:

rt2500 : driver installed
            device (1814:0201) present (alternative driver: rt2500pci)

---

### Post by wieman01 on 2007-10-07
> **grovulent said:**
> hi there - appreciate the help...

It says:

rt2500 : driver installed
            device (1814:0201) present (alternative driver: rt2500pci)
You should definitely blacklist "rt2500pci" in that case. After a restart you cannot scan for networks, right?
> sudo iwlist scan
That generally means that something has gone wrong during the deployment of the Windows driver. Question: While you installed the .inf file, where other driver files present in the same folder (e.g. .cap, etc.)? That is a requirement that I have not highlighted.

Could you redo the whole procedure once again after blacklisting the driver? Perhaps even remove/purge "ndiswrapper" and reinstall everything from scratch. Any better?

---

### Post by awakatanka on 2007-10-07
> **wieman01 said:**
> After doing all the steps you still have to modprobe after restart? Does everything else work now?

everytime.

Everything is working then but it has stability problems. It random disconnect and its also slow, but thats probably because the lower signal strenght. 

But i believe Kubuntu also have some problems because fresh install with a other kind of wireless usb stick causes konqueror to be dead slow to on requesting pages. I going to try a ubuntu install to see if it behave the same. Going to try it also with 2 different wireless chipsets/cards

Feisty and mepis install with old drivers are fast, but they need some config work before it works in wpa mode. But knetworkmanager never worked before and now it finaly does but with those problems of speed.

---

### Post by wieman01 on 2007-10-08
> **awakatanka said:**
> everytime.

Everything is working then but it has stability problems. It random disconnect and its also slow, but thats probably because the lower signal strenght. 

But i believe Kubuntu also have some problems because fresh install with a other kind of wireless usb stick causes konqueror to be dead slow to on requesting pages. I going to try a ubuntu install to see if it behave the same. Going to try it also with 2 different wireless chipsets/cards

Feisty and mepis install with old drivers are fast, but they need some config work before it works in wpa mode. But knetworkmanager never worked before and now it finaly does but with those problems of speed.
Odd. You could modprobe the module using a normal startup script. That way, you won't have to do it manually all the time.

---

### Post by grovulent on 2007-10-08
> **wieman01 said:**
> You should definitely blacklist "rt2500pci" in that case. After a restart you cannot scan for networks, right?

That generally means that something has gone wrong during the deployment of the Windows driver. Question: While you installed the .inf file, where other driver files present in the same folder (e.g. .cap, etc.)? That is a requirement that I have not highlighted.

Could you redo the whole procedure once again after blacklisting the driver? Perhaps even remove/purge "ndiswrapper" and reinstall everything from scratch. Any better?


Well - it looks like the latest updates to the gutsy system have fixed the problems with the linux driver at least for me.  Not flawless - it still won't connect using roaming - but I can connect through network manager if I specify the ssid and password manually.

Strange that i couldn't get your workaround to work though.  The other files were there in the directory (the rt2500.cat and rt2500.sys).  Reinstalling ndiswrapper after blacklisting was something I tried - but no luck.  It may have just been a combination of the ndiswrapper version + driver files + my system - just didn't happen to add up.  But we may never know why.  

Here's hoping further updates to gutsy don't break things!

---

### Post by olbill on 2007-10-09
I have discovered the reason my Belkin 7050 version 2.00 wireless card does not work in Feisty or Gutsy.  It reports as a version 1.00 and loads the rt73usb driver as default.  I have used ndiswrapper to load the XP driver rt2500usb from the mfg web site.  Blacklist rt73usb and the wireless works great.

Good luck to all.


desktop:~$ sudo lsusb
Password:
Bus 001 Device 002: ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi
Bus 001 Device 001: ID 0000:0000  

desktop:~$ ndiswrapper -l
drivername : invalid driver!
rt2500usb : driver installed
        device (050D:7050) present (alternate driver: rt73usb)

---

### Post by JawsThemeSwimming428 on 2007-10-19
wieman01,

 I did a fresh install of Gusty Gibbon last night after I finished downloading it. In Feisty, when I disabled Network Manager my wireless worked fine. This is not the case in Feisty. I don't need to use Network Manager (it doesn't bother me either way as I am unsure of the advantages/disadvantages) but if  that is the way it will work then that's fine. You have helped me out before (witch success) and I appreciate that. I think I am going to try your tutorial when I get home tonight after work, but I have a few questions that might be helpful for the install.

1. I have the WUSB54Gv4 Linksys wireless card, how do I know what chipset it uses? Is it Ralink?

2. If I end up using ndiswrapper, what version should I use? Is the version that comes with the Gusty CD ok?

3. If I were to try to edit the interfaces file, what does that entail? Is it a lot more difficult than using ndiswrapper?

Thanks for everything, hopefully I will be posting back here with my success later tonight!

---

### Post by wieman01 on 2007-10-19
> **JawsThemeSwimming428 said:**
> wieman01,

 I did a fresh install of Gusty Gibbon last night after I finished downloading it. In Feisty, when I disabled Network Manager my wireless worked fine. This is not the case in Feisty. I don't need to use Network Manager (it doesn't bother me either way as I am unsure of the advantages/disadvantages) but if  that is the way it will work then that's fine. You have helped me out before (witch success) and I appreciate that. I think I am going to try your tutorial when I get home tonight after work, but I have a few questions that might be helpful for the install.

1. I have the WUSB54Gv4 Linksys wireless card, how do I know what chipset it uses? Is it Ralink?

2. If I end up using ndiswrapper, what version should I use? Is the version that comes with the Gusty CD ok?

3. If I were to try to edit the interfaces file, what does that entail? Is it a lot more difficult than using ndiswrapper?

Thanks for everything, hopefully I will be posting back here with my success later tonight!
Hello, 

Nice to see you again... :-)

1. It is a Ralink. I know because I happen to own one myself.

2. Use the version that comes with the CD. No problem with it.

3. There is not connection between the interfaces file and ndiswrapper. Once you have installed the driver using ndiswrapper, you can either use Network Manager or edit "interfaces" file to set up your WPA wireless LAN. But that is entirely up to you.

Please make sure that you have the latest latest version of the Windows driver that supports WPA2. That will spare you a lot of trouble.

---

### Post by JawsThemeSwimming428 on 2007-10-19
Awesome, thanks for the quick reply! Ok...I have the Ralink chipset, so which Ralink driver do I blacklist in the beginning? I will try this tonight when I get home from work (around 6-6:30 EST) and post back here to let you know how I made out! Thanks.

---

### Post by wieman01 on 2007-10-19
> **JawsThemeSwimming428 said:**
> Awesome, thanks for the quick reply! Ok...I have the Ralink chipset, so which Ralink driver do I blacklist in the beginning? I will try this tonight when I get home from work (around 6-6:30 EST) and post back here to let you know how I made out! Thanks.
To begin with you could blacklist all of them. Will do no harm. But the right one for you is "rt2500usb". See you then!

---

### Post by terdon on 2007-10-19
Hi everyone, 
     I thought I'd post here as none of the solutions above worked for me. OK, I have a Fujistu-Siemens Amilo A1630 with an on board RAlink rt2500 card which worked fine under Feisty. (Oddly enough it had never worked under windows, not even with the latest drivers nor under various flavours of SuSe).

When I upgraded to Gutsy yesterday, the card was recognised but no networks were found (using either command line or wlanassistant). 

I tried ndiswrapper but had the same problem. In the end I iused the latest CVS of serialmonkey's driver ([http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz))

Just download, untar, follow the instructions in the README of the Module directory and the add these lines to /etc/modprobe.d/blacklist:

blacklist rt2500pci
blacklist rt2x00pci
blacklist rt2x00lib

It now works fine with wlanassistant although not with wicd. I realise this thread is for people who want to use network-manager or wicd but still, at least now I can connect.


Hope this helps

---

### Post by JawsThemeSwimming428 on 2007-10-19
wieman01,

 I just went through your walkthrough step by step, and there were no errors reported. However when I open up Network Manager (after I rebooted) I only have a Wired connection and modem? The wireless isn't even in there.

---

### Post by JawsThemeSwimming428 on 2007-10-19
Also, all that is in /etc/network/interfaces is

auto lo
iface lo inet loopback


Isn't there supposed to be a wireless connection in there?

---

### Post by saz on 2007-10-19
when i rebooted my pc the wlan device wasn't there... i've installed the device correctly... i have a wusb54gv4, on feisty i used ndiswrapper (rt2570 blacklisted) no probs..

---

### Post by ricardisimo on 2007-10-19
My Network Monitor isn't working properly since upgrading. Anyone else having this problem? It displays as there being no connection, even though it's clearly up and running.

Also, it appears that I have to manually configure my connection at every boot, selecting WEP key (hexadecimal) over the default (and quite insistent) WPA Personal. Otherwise I can't connect. Any idea what that's all about?

Here's my /etc/network/interfaces:
```
auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp

auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp



iface ra0 inet dhcp
wireless-essid <coffeeshopnextdoor>

auto ra0
```

I see that Wieman also has a HowTo on WPA, which I will dive into once I can set up a reliable connection.

Finally, I remember, from when I tried running Kubuntu, that commenting out all of the extra eths and moving ra0 up the list made quite a difference. Will that help in this case? Thanks in advance.

---

### Post by wieman01 on 2007-10-19
> **JawsThemeSwimming428 said:**
> Also, all that is in /etc/network/interfaces is

auto lo
iface lo inet loopback

Isn't there supposed to be a wireless connection in there?
What happens when you put in:
> auto wlan0
iface wlan0 inet dhcp
Then reboot the PC.

_**EDIT:**_
One more thing... When you go to "Manual Configuration" in NM, is your new "wlan0" device shown? You need to activate it as I believe. Then close the networking applet and see if NM recognizes it.

---

### Post by wieman01 on 2007-10-19
> **ricardisimo said:**
> My Network Monitor isn't working properly since upgrading. Anyone else having this problem? It displays as there being no connection, even though it's clearly up and running.

Also, it appears that I have to manually configure my connection at every boot, selecting WEP key (hexadecimal) over the default (and quite insistent) WPA Personal. Otherwise I can't connect. Any idea what that's all about?

Here's my /etc/network/interfaces:
```
auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp

auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp



iface ra0 inet dhcp
wireless-essid <coffeeshopnextdoor>

auto ra0
```

I see that Wieman also has a HowTo on WPA, which I will dive into once I can set up a reliable connection.

Finally, I remember, from when I tried running Kubuntu, that commenting out all of the extra eths and moving ra0 up the list made quite a difference. Will that help in this case? Thanks in advance.
Commenting out all unused interfaces should help, yes. In fact NM required you to remove all interfaces from "/etc/network/interfaces" in the past. But I don't think that is still the case.

---

### Post by JawsThemeSwimming428 on 2007-10-19
Well, I am posting this from my Gusty machine so it would seem I got it working. The key was that my /etc/network/interfaces file had nothing in it except lo. I added my ethernet connection and wlan0, rebooted, and in network manager I selected wlan0 and it was up right away. Thanks for the nice tutorial wieman01!

---

### Post by wieman01 on 2007-10-19
> **JawsThemeSwimming428 said:**
> Well, I am posting this from my Gusty machine so it would seem I got it working. The key was that my /etc/network/interfaces file had nothing in it except lo. I added my ethernet connection and wlan0, rebooted, and in network manager I selected wlan0 and it was up right away. Thanks for the nice tutorial wieman01!
Thanks, mate, for letting us know. I will highlight this in the tutorial... I was not aware that this might be an issue. Great!

---

### Post by ricardisimo on 2007-10-19
Thanks again. So, no idea why the monitor isn't registering? Also, why does NM insist on the password type being WPA instead of WEP?

---

### Post by wieman01 on 2007-10-19
> **ricardisimo said:**
> Thanks again. So, no idea why the monitor isn't registering? Also, why does NM insist on the password type being WPA instead of WEP?
You have a Ralink card which does not work well together with NM unless you replace the driver with "ndiswrapper". You have not done so, is that right?

---

### Post by ricardisimo on 2007-10-19
No, not yet. (Damn! I was hoping he wouldn't ask that question).Here's the card's specs:
```
product: RT2500 802.11g Cardbus/mini-PCI
```
I'll go back to the start of the HowTo and get started, but in the meantime, please confirm that there is nothing peculiar about this card. It should work just fine, no?

---

### Post by ricardisimo on 2007-10-20
Something I don't get... why won't [these drivers]("http://www.ralinktech.com/ralink/Home/Support/Linux.html") work? Is this what is already being used (and failing) in Feisty and Gutsy, etc.?

---

### Post by terdon on 2007-10-20
Well, 
    the one that came with Gutsy didn't work but the latest one did for me. I have a Ralink RT2500 card.

---

### Post by ricardisimo on 2007-10-20
Huh? The one that came with Gutsy is the latest one, isn't it? I have the exact same card (I think). Does the Network Monitor work for you? Can you see your connection's activity and strength?

---

### Post by ricardisimo on 2007-10-20
Something is definitely wrong here. Right now I' m running on the 7.04 Live CD, and the connection (after some tinkering) is very, very fast, as it should be. All is not well in Gutsyland. Any ideas?

P.S. - My best connection on Gutsy was in the 20-30 kbps range.

---

### Post by Talkie_Toaster on 2007-10-20
Hey, I'm thinking of dual booting, but my wireless connection is my only connection. Is there anything I can do that doesn't need me to be connected to the Internet in Ubuntu? (I can connect in Windows fine)

---

### Post by wieman01 on 2007-10-20
> **ricardisimo said:**
> Something is definitely wrong here. Right now I' m running on the 7.04 Live CD, and the connection (after some tinkering) is very, very fast, as it should be. All is not well in Gutsyland. Any ideas?

P.S. - My best connection on Gutsy was in the 20-30 kbps range.
Hang on... what driver are you using now? You have somewhat lost me.

---

### Post by wieman01 on 2007-10-20
> **Talkie_Toaster said:**
> Hey, I'm thinking of dual booting, but my wireless connection is my only connection. Is there anything I can do that doesn't need me to be connected to the Internet in Ubuntu? (I can connect in Windows fine)
Well, if you happen to have a Ralink card and want to follow this tutorial, then you can install "ndiswrapper" from the CD ROM... you don't need a working connection for that.

---

### Post by saz on 2007-10-20
[QUOTE=]when i rebooted my pc the wlan device wasn't there... i've installed the device correctly... i have a wusb54gv4, on feisty i used ndiswrapper (rt2570 blacklisted) no probs..[/QUOTE]

anyone help?

---

### Post by wieman01 on 2007-10-20
> **saz said:**
> anyone help?
Have you added these lines to "interfaces"?
> auto wlan0
iface wlan0 inet dhcp
What does a scan yield?
> sudo iwlist scan

---

### Post by saz on 2007-10-20
can't believe I was so lamme..

```
auto wlan0
```

solved the problem obviously... xD writing from gutsy right now..

thanks wieman01! helpful as always!

P.S.: I'm using ndiswrapper cuz with the "rt2500usb" that came in gutsy would connect to my network but i would have no signal nor internet (strange).. just saying cuz dev might want to have a look at it.. as I said, i'm using a Linksys WUSB54Gv4..

---

### Post by saz on 2007-10-20
can't believe I was so lamme..

```
auto wlan0
```

solved the problem obviously... xD writing from gutsy right now..

thanks wieman01! helpful as always!

P.S.: I'm using ndiswrapper cuz with the "rt2500usb" that came in gutsy 
would connect to my network but i would have no signal nor internet 
(strange).. just saying cuz dev might want to have a look at it.. as I 
said, i'm using a Linksys WUSB54Gv4..

---

### Post by saz on 2007-10-20
oooppss... double post... sorry.. network problem i guess..

---

### Post by wieman01 on 2007-10-20
> **saz said:**
> can't believe I was so lamme..

```
auto wlan0
```

solved the problem obviously... xD writing from gutsy right now..

thanks wieman01! helpful as always!

P.S.: I'm using ndiswrapper cuz with the "rt2500usb" that came in gutsy would connect to my network but i would have no signal nor internet (strange).. just saying cuz dev might want to have a look at it.. as I said, i'm using a Linksys WUSB54Gv4..
Great. Thanks for letting me know. My fault that I did not mention that earlier... I have updated the guide accordingly. See you. :-)

---

### Post by AdHavoc on 2007-10-20
I have an RT2600 pci, so I am unsure of this will work.  My issue is that the card is recognized, and my network is found, but I can't seem to connect to it or other free networks in my area.  Can I simply follow this tutorial and blacklist one of the other things?

---

### Post by Gina on 2007-10-20
I have been testing the pre-release of Gutsy for a while and now installed the full release version.  I was unable to get wireless working  with this so have a wired connection to router.  I decided to leave having a concerted effort at getting wireless to work until the full release.  Trying now and no luck.

I have a Belkin F5D700UK PCI card that has the Ralink RT2500 chipset.  lspci entry is :-
00:0d.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

This was working fine in Feisty except that I had to down the interface, set essid and then up the interface to get it to work.  Now in Gutsy this doesn't work.  I just want a wireless connection that works and not mess with ndiswrapper or network manager etc.  I know this thread is about using ndiswrapper but I can't find anything about using the supplied driver - I expected the known bug of downing the interface to be cured in Gutsy.  I'm sure I'm missing something.  Can anyone suggest an answer, please?

This is a copy of my terminal window when I try this in Gutsy (iwconfig shows AP as Not-Associated - iwlist scan shows the correct router MAC but empty ESSID) :-

```
gina@old-desktop:~$ sudo iwconfig
[sudo] password for gina:
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

gina@old-desktop:~$ sudo ifdown wlan0
ifdown: interface wlan0 not configured
gina@old-desktop:~$ sudo iwconfig wlan0 essid mystery mode managed channel 11
gina@old-desktop:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.
gina@old-desktop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"mystery"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

gina@old-desktop:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:14:6C:A8:DA:2A
                    ESSID:""
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz
                    Signal level=-52 dBm  
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000003756a04181

gina@old-desktop:~$ 

```

---

### Post by ricardisimo on 2007-10-20
> **wieman01 said:**
> Hang on... what driver are you using now? You have somewhat lost me.

Good question. What driver am I using? How do I determine that? And also, how do I know if the driver I'm using is or is not the same as the Linux driver that RaLink provides on their website (link in previous post)? Thanks again.

---

### Post by sabrateur on 2007-10-20
Wieman, this tutorial is great!

I'm using WUSB54Gv4 (just bought it this morning) and initially although Network Manager could detect the device and showed my wireless SSID, I couldn't connect.

Thanks for showing new Ubuntu users like me how to use ndiswrapper! :)

---

### Post by ricardisimo on 2007-10-20
> I just want a wireless connection that works and not mess with ndiswrapper or network manager etc.
I'm with you, Gina. Unfortunately, I don't know that we have much choice this time around.

What I don't understand is how the support could be getting worse at every stage. My connection under Dapper was immaculate, Under Feisty I had to do the same sort of tinkering as you. And now with Gutsy I'm at a total loss... I don't think I can avoid ndiswrapper. I'm hoping that that will work. We'll see. Right now, just to be able to post here and try to download the Windows driver, I'm having to run Feisty off of the Live CD. Bizarre.

---

### Post by douradinhos on 2007-10-20
> 
    * Last but not least open this file...
      Quote:
      sudo gedit /etc/network/interfaces

    * ...and add these 2 lines if they are not there yet:
      Quote:
      auto wlan0
      iface wlan0 inet dhcp


ahhhh, now it works on 7.10!! (btw, im using rt2500usb for linksys WUSB54G v4)

tks for the tutorial

---

### Post by Suriel on 2007-10-20
> **ricardisimo said:**
> I'm with you, Gina. Unfortunately, I don't know that we have much choice this time around.

What I don't understand is how the support could be getting worse at every stage. My connection under Dapper was immaculate, Under Feisty I had to do the same sort of tinkering as you. And now with Gutsy I'm at a total loss... 

Same here. Dapper worked, Feisty worked after a few days of surfing for tips and torturing my Linux books. 

I'll not give up hope yet for Gutsy and I will not yet go for NDISWRAPPER either.

Actually, ain't this the real fun about Linux? ;)

Good to know though there is this tutorial to come back to! Good job, Wieman01.

---

### Post by ricardisimo on 2007-10-20
I've followed all of the instructions in this HowTo, and my connection is present at startup, without having to do anything extraordinary - Thank you Wieman!

Still, there is something dreadfully wrong here. This same connection that is ***superfast*** when I connect on the Feisty Live CD, is sssssllllloooooooooooooooowwwwwwwwwww on Gutsy. A small part of the problem appears to be Firefox, which is a major drag, a bigtime hog right now. But even on, say, Galeon, the connection is in single-digit kbps. Any idea as to what is going on?

 Here's my iwconfig:
```
$ sudo iwconfig
[sudo] password for ricardo:
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       IEEE 802.11g  ESSID:"<essid>"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:30:BD:65:7A:56   
          Bit Rate=1 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:14/100  Signal level:-87 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
Thanks in advance for any help.

P.S. - Here I am again on the Feisty Live CD, just checking to see if I'm crazy, imagining it all, or what... ZOOM! ZIP! It's a great high speed connection that for some reason Gutsy is slowing to a crawl. Truly bizarre.

---

### Post by wieman01 on 2007-10-20
> **AdHavoc said:**
> I have an RT2600 pci, so I am unsure of this will work.  My issue is that the card is recognized, and my network is found, but I can't seem to connect to it or other free networks in my area.  Can I simply follow this tutorial and blacklist one of the other things?
AdHavoc, 

Yes, you could try it, messing around with "ndiswrapper" won't do any damage to your system. And removing your card from the blacklist plus removing "ndiswrapper" is easy. 

I would think that you need to blacklist:
> rt2600pci
I will be here to help.

---

### Post by wieman01 on 2007-10-20
> **ricardisimo said:**
> Still, there is something dreadfully wrong here. This same connection that is ***superfast*** when I connect on the Feisty Live CD, is sssssllllloooooooooooooooowwwwwwwwwww on Gutsy. A small part of the problem appears to be Firefox, which is a major drag, a bigtime hog right now. But even on, say, Galeon, the connection is in single-digit kbps. Any idea as to what is going on?

P.S. - Here I am again on the Feisty Live CD, just checking to see if I'm crazy, imagining it all, or what... ZOOM! ZIP! It's a great high speed connection that for some reason Gutsy is slowing to a crawl. Truly bizarre.
Yes, this issue sounds very familiar. 

Let me think... it could relate to "ipv6" that is enabled by default. You need to turn it off both globally (i.e. in the system) and in Firefox. This is a helpful link for you:

_Gobal "ipv6":_
[http://ubuntuforums.org/showthread.php?t=87798]("http://ubuntuforums.org/showthread.php?t=87798")

_Firefox:_
[http://kb.mozillazine.org/Network.dns.disableIPv6]("http://kb.mozillazine.org/Network.dns.disableIPv6")

Those settings should make your browsing speed significantly faster.

---

### Post by wieman01 on 2007-10-20
> **Gina said:**
> I have been testing the pre-release of Gutsy for a while and now installed the full release version.  I was unable to get wireless working  with this so have a wired connection to router.  I decided to leave having a concerted effort at getting wireless to work until the full release.  Trying now and no luck.

I have a Belkin F5D700UK PCI card that has the Ralink RT2500 chipset.  lspci entry is :-
00:0d.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

This was working fine in Feisty except that I had to down the interface, set essid and then up the interface to get it to work.  Now in Gutsy this doesn't work.  I just want a wireless connection that works and not mess with ndiswrapper or network manager etc.  I know this thread is about using ndiswrapper but I can't find anything about using the supplied driver - I expected the known bug of downing the interface to be cured in Gutsy.  I'm sure I'm missing something.  Can anyone suggest an answer, please?[/CODE]
Gina, 

I know you don't like it but the current driver does not work as far as I can tell. It scans fine but I could never get it to connect with my WPA2 network, not to mention the fact that Network Manager could not handle it. 

As far as I remember they are in the process of redesigning Ralink based drivers and they should improve a lot in future. But as of yet, you don't have too many options if you are in need of a wireless connection.

Serialmonkey's OS Ralink driver is another option, but frankly the driver is no better either. NM does not recognize it.

---

### Post by AdHavoc on 2007-10-20
> **wieman01 said:**
> [

[LIST]
[*]Now unzip the driver archive you have just downloaded (e.g. in your home directory):

[/LIST]

[LIST]
[*]Now find the right driver in the resulting folder & deploy it (folder should also contain other driver files e.g. .cab, etc.):

[/LIST]


I got ndiswrapper from the Gutsy Gibbon cdrom, and I don't quite understand what this means.  Where is the driver archive?  Why is it dealing with .exe files?  Sorry for asking probably stupid questions, but I need to figure this out :p

---

### Post by wieman01 on 2007-10-20
> **AdHavoc said:**
> I got ndiswrapper from the Gutsy Gibbon cdrom, and I don't quite understand what this means.  Where is the driver archive?  Why is it dealing with .exe files?  Sorry for asking probably stupid questions, but I need to figure this out :p
No problem.

The archive is simply a ZIP file that contains all your driver files. Very often the extension is .EXE, however, that file is also simply a ZIP file which you can then extract. This is not very obvious, so your question is no stupid at all.

You get the (Windows) driver file from your vendor's web-site I believe.

---

### Post by JLR is me on 2007-10-21
Ok, so after much turmoil, I managed to get my wusb54gv4 to work on 7.04 (I originally was trying to do it on 7.10, but after it failing I ended up giving up) So now I'm wondering... If I were to just do an upgrade, would it keep all my settings, or would I have to go through hell to get it working again?

Edit: I restarted my computer to be sure it's working, and now the adapter isn't even being recognized...It doesn't even turn on when I'm using Ubuntu now, if I plug it in it says power on for about 3 seconds, then shuts down.

---

### Post by wieman01 on 2007-10-21
> **JLR is me said:**
> Ok, so after much turmoil, I managed to get my wusb54gv4 to work on 7.04 (I originally was trying to do it on 7.10, but after it failing I ended up giving up) So now I'm wondering... If I were to just do an upgrade, would it keep all my settings, or would I have to go through hell to get it working again?

Edit: I restarted my computer to be sure it's working, and now the adapter isn't even being recognized...It doesn't even turn on when I'm using Ubuntu now, if I plug it in it says power on for about 3 seconds, then shuts down.
Have you followed every step in the tutorial? Somehow the settings don't stick.

No, an upgrade should not mess around with current settings unless you have compiled "ndiswrapper" from source. You should be ok, although that's no promise of course.

---

### Post by JLR is me on 2007-10-21
I followed every detail exact. Theoretically it should work fine (hell, it even did work five minutes ago, untill I restarted my computer) In order of things happening,  I connected online, it asked for a keyring manager thing (Which I followed) then I restarted, and upon boot the wireless adapter doesn't work at all now.

Edit: I had an idea on what the issue was, and it seems to be right. the interfaces gedit  removed the auto wlan0 for some reason. If that happens again, is their any way to enable it from the terminal?

---

### Post by dingansich on 2007-10-21
First off, let me just thank wieman01 for all the work put in here.  Unfortunately I'm still having problems though.  I think the best thing I can do is explain what I've done (I followed the tutorial closely), and maybe someone can tell me where I've gone wrong.  Here goes...

I'm running Gutsy (amd64), with a Linksys WUSB54Gv4 interface (which worked 'out of the box' in Feisty but no longer works in Gutsy).

I downloaded the ndiswrapper-common_1.43, ndiswrapper-utils-1.9_1.43, ndisgtk_0.6 deb install packages, and the latest Linksys driver (from the Linksys site) to my  Windows partition, and copied them over to my Ubuntu partition.  ndiswrapper installed without a problem, the driver files extracted easily, and using ndiswrapper -i rt2500usb.inf the driver installed nicely.

Then I edited my /etc/network/interfaces file, which now looks like this:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

Then I edited my /etc/modprobe.d/blacklist file to include the following lines at the end of the file:
```
blacklist rt2500
blacklist RT2500
blacklist rt2500usb
```

Then I rebooted.  

Now the NM interface shows no wireless adapter installed (it used to before the ndiswrapper config).  iwconfig lists only lo and eth0 ("no wireless extensions"), as does ifconfig - though it also lists eth0:avah.

sudo ndiswrapper -l yields the following:
```

rt2500usb : driver installed
              device (13B1:000D) present (alternate driver: rt2500usb)

```

lsusb confirms that the device is at least detected on the usb bus, and that the ID number is correct.

What am I missing?  :confused: Any help is greatly appreciated!

---

### Post by wieman01 on 2007-10-21
> **dingansich said:**
> First off, let me just thank wieman01 for all the work put in here.  Unfortunately I'm still having problems though.  I think the best thing I can do is explain what I've done (I followed the tutorial closely), and maybe someone can tell me where I've gone wrong.  Here goes...

I'm running Gutsy (amd64), with a Linksys WUSB54Gv4 interface (which worked 'out of the box' in Feisty but no longer works in Gutsy).

...

lsusb confirms that the device is at least detected on the usb bus, and that the ID number is correct.

What am I missing?  :confused: Any help is greatly appreciated!
Odd... All you have said & done looks quite right. Please check "Manual Configuration..." and confirm that the "wlan0' interfaces is enabled.

Second please do a scan and post the results if possible:
> sudo iwlist scan
Does the scan yield any results & do you see your network? And what happens when you restart the network:
> sudo ifdown -v wlan0
> sudo ifup -v wlan0

---

### Post by wieman01 on 2007-10-21
> **JLR is me said:**
> I followed every detail exact. Theoretically it should work fine (hell, it even did work five minutes ago, untill I restarted my computer) In order of things happening,  I connected online, it asked for a keyring manager thing (Which I followed) then I restarted, and upon boot the wireless adapter doesn't work at all now.

Edit: I had an idea on what the issue was, and it seems to be right. the interfaces gedit  removed the auto wlan0 for some reason. If that happens again, is their any way to enable it from the terminal?
Yes, you can restart the network manually:
> sudo /etc/init.d/networking restart
See if that works. But it is strange that this sort of thing should happen in the first place...

---

### Post by terdon on 2007-10-21
> **ricardisimo said:**
> Huh? The one that came with Gutsy is the latest one, isn't it? I have the exact same card (I think). Does the Network Monitor work for you? Can you see your connection's activity and strength?

No, I got the latest CVS snapshot (see link at my previous post). If you download and install that it should work fine (I am now connected using gutsy and RT2500).

As for networkmanager I don't know, I don't use it. wlanasistant works fine,  and ```
iwlist scan
``` gives me a list of access points. So try downloading the new driver it should work if you have the same card.

---

### Post by dingansich on 2007-10-21
> Please check "Manual Configuration..." and confirm that the "wlan0' interfaces is enabled.

That's the first really odd thing. When I select "Manual Configuration..." the window that pops up doesn't even list my wireless connection!  It only lists "Wired Connection" (which is enabled) and "Modem Connection" (which is not enabled, probably because I don't have a modem connected to my PC).

> Second please do a scan and post the results if possible:

When I execute sudo iwlist scan I get the following:

```

lo        Interface doesn't support scanning.

eth0     Interface doesn't support scanning.
```

> Does the scan yield any results & do you see your network? And what happens when you restart the network:

No I don't see my network.  When I take the network down (sudo ifdown -v wlan0) I get the following:

```
ifdown: interface wlan0 not configured
```

When I try to bring it up (sudo ifup -v wlan0) I get the following (bear with me - I am typing this all out from another computer):

```
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
wlan0: ERROR while getting interface flags: No such device
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant

dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.wlan0.pid -lf /var/lib/dhcp3/dhclient.wlan0.leases wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 0
Internet Systems Consortium DHCP client V3.0.5
Copyright 2004-2006 Internet Systems Consortium
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0
```

Any ideas?  What could possibly be keeping my interface from even being detected?  Is there anywhere other than /etc/network/interfaces that this kind of information is specified?

---

### Post by wieman01 on 2007-10-21
> **dingansich said:**
> That's the first really odd thing. When I select "Manual Configuration..." the window that pops up doesn't even list my wireless connection!  It only lists "Wired Connection" (which is enabled) and "Modem Connection" (which is not enabled, probably because I don't have a modem connected to my PC).

...

Any ideas?  What could possibly be keeping my interface from even being detected?  Is there anywhere other than /etc/network/interfaces that this kind of information is specified?
Please post the contents of:
> sudo gedit /etc/network/interfaces
And:
> sudo gedit /etc/modprobe.d/ndiswrapper
Also again:
> sudo ndiswrapper -l

---

### Post by dingansich on 2007-10-21
Here's the contents of /etc/network/interfaces:

```

auto lo
iface lo inet loopback

auto eht0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

Here's the contents of /etc/modprobe.d/ndiswrapper:

```

alias wlan0 ndiswrapper

```

Here's the output of sudo ndiswrapper -l:

```

rt2500usb : driver installed
              device (13B1:000D) present (alternate driver: rt2500usb)

```

Again, thanx much for all of this help.

---

### Post by dingansich on 2007-10-21
Sorry for the double post, but I was just looking around the ndiswrapper install and noticed that in my /etc/ndiswrapper/rt2500usb directory I have 3 conf files.  They are named as follows:

13B1:000D.F.conf
13B1:0011.F.conf
13B1:001A.F.conf

The first one matches the hardware ID for the WUSB54Gv4 returned by lusb.  I'm mot sure what the others are.  I at one time tried installing some other windows drivers - but they were removed when I had no success with them (their entries no longer show in /etc/ndiswrapper).  Are these (extra?) conf files potentially causing the problem?

--edit--
Well I copied the 2 mismatched files (13B1:0011.F.conf and 13B1:001A.F.conf) to a temporary directory and rebooted.  Made no difference.

---

### Post by wieman01 on 2007-10-21
> **dingansich said:**
> Sorry for the double post, but I was just looking around the ndiswrapper install and noticed that in my /etc/ndiswrapper/rt2500usb directory I have 3 conf files.  They are named as follows:

13B1:000D.F.conf
13B1:0011.F.conf
13B1:001A.F.conf

The first one matches the hardware ID for the WUSB54Gv4 returned by lusb.  I'm mot sure what the others are.  I at one time tried installing some other windows drivers - but they were removed when I had no success with them (their entries no longer show in /etc/ndiswrapper).  Are these (extra?) conf files potentially causing the problem?

--edit--
Well I copied the 2 mismatched files (13B1:0011.F.conf and 13B1:001A.F.conf) to a temporary directory and rebooted.  Made no difference.
Ok, which driver did you blacklist and how? Could you post the relevant section please?

_**EDIT:**_
Are you on Gutsy or Feisty?

---

### Post by dingansich on 2007-10-21
I'm on Gutsy (amd64).  My adapter was working under Feisty.  It crapped out after I did the upgrade.

I blacklisted the drivers by adding them to the /etc/modprobe.d/blacklist file.  Originally I only blacklisted the rt2500usb driver, but as of now I have blacklisted all of the drivers listed in the original HOWTO:

rt2500usb
rt2500pci
rt2500
rt2570
rt73usb
rt73pci
rt73
rt2x00usb
rt2x00lib

Also, I looked into those other device IDs.  I'm not sure about 13B1:001A, but 13B1:0011 is reported as the device ID for the Linksys WUSB54Gv4 as is 13B1:000D (which is what lsusb identifies my adapter with).  In any case, as moving those (seemingly) additional conf files to a temporary directory did not make a difference, I moved them back to their original place: /etc/ndiswrapper/rt2500usb.

Incidentally, I also took a look at the output from lsmod.  ndiswrapper is listed as a loaded module, and there do not seem to be any other modules loaded that look like they might pertain to wireless networking adapters.

---

### Post by wieman01 on 2007-10-21
> **dingansich said:**
> I'm on Gutsy (amd64).  My adapter was working under Feisty.  It crapped out after I did the upgrade.

I blacklisted the drivers by adding them to the /etc/modprobe.d/blacklist file.  Originally I only blacklisted the rt2500usb driver, but as of now I have blacklisted all of the drivers listed in the original HOWTO:

rt2500usb
rt2500pci
rt2500
rt2570
rt73usb
rt73pci
rt73
rt2x00usb
rt2x00lib

Also, I looked into those other device IDs.  I'm not sure about 13B1:001A, but 13B1:0011 is reported as the device ID for the Linksys WUSB54Gv4 as is 13B1:000D (which is what lsusb identifies my adapter with).  In any case, as moving those (seemingly) additional conf files to a temporary directory did not make a difference, I moved them back to their original place: /etc/ndiswrapper/rt2500usb.

Incidentally, I also took a look at the output from lsmod.  ndiswrapper is listed as a loaded module, and there do not seem to be any other modules loaded that look like they might pertain to wireless networking adapters.
When you installed the driver file (.INF) where there any other files present e.g. .CAB or similar?

It might relate to the fact that you are on a 64-bit machine. If we cannot find a solution here I'll have to refer you to the 64-bit section... They might know a solution.

---

### Post by dingansich on 2007-10-21
When I installed the driver, the files in the directory from which I executed the ndiswrapper command were: rt2500usb.cat, rt2500usb.inf, and rt2500usb.sys.

I'm wondering if it's a a 64 bit issue as well. But AMD64 is a fairly common platform, and the WUSB54Gv4 is a common adapter.  If this were a problem I'd have thought it would be well flagged by now.  Maybe I've overlooked it?  Can anyone browsing this thread confirm that they managed to get a Linksys WUSB54Gv4 working in Gutsy on the amd64 platform?

---

### Post by wieman01 on 2007-10-21
> **dingansich said:**
> When I installed the driver, the files in the directory from which I executed the ndiswrapper command were: rt2500usb.cat, rt2500usb.inf, and rt2500usb.sys.

I'm wondering if it's a a 64 bit issue as well. But AMD64 is a fairly common platform, and the WUSB54Gv4 is a common adapter.  If this were a problem I'd have thought it would be well flagged by now.  Maybe I've overlooked it?  Can anyone browsing this thread confirm that they managed to get a Linksys WUSB54Gv4 working in Gutsy on the amd64 platform?
I am tempted to think this has to do with the "ndiswrapper" port to the 64-bit environment. I cannot offer much more support at this stage as I am clueless as to what the issue is.

---

### Post by dingansich on 2007-10-22
Well thanks much for all your help an patience.  I'll add one small development before I start poking around elsewhere.  

I figured it might be worth while going back to square one ... so I restored my /etc/network/interfaces file (it now contains only references to lo, eth0, and rausb0 - which is how the stock install of Gutsy had set it up - wlan0 is totally gone).  Then I commented out all of the additions I made to the /etc/modprobe.d/blacklist file.  Then I rebooted the machine.  Odd thing is that even after reverting to the original broken state, the wireless interface doesn't even register in the network manager, or through ifconfig or iwconfig.  It used to.  So I'm thinking that somewhere something has gone wrong - but I don't know where or how it could have happened.  lsmod doesn't list any wireless drivers loaded - so I tracked the rt2x00usb driver down that Ubuntu installs (somewhere buried under /var) and ran modprobe rt2x00usb against it.  lsmod now shows it loaded, but it doesn't list under NM, iwconfig, or ifconfig.  What's odd about this is that the symptoms of this problem are identical to those of the ndiswrapper problem.  This leads me to believe that it my not be ndiswrapper, but something else connected to how modules are loaded.  I dunno ... maybe I'm off my rocker.

Again, thanx a ton for all the help! :)

---

### Post by dingansich on 2007-10-22
Well I found the problem!  And it is a 64bit issue.  Here is the output of cat /var/log/dmesg | grep ndis:

```

ndiswrapper version 1.45 loaded (smp=yes)
ndiswrapper (check_nt_hdr:153): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
ndiswrapper (load_sys_files:216): couldn't prepare driver 'rt2500usb'
ndiswrapper (load_wrap_driver:118) couldn't load driver rt2500usb; check system log for messages from loadndisdriver
usbcore: registered new interface driver ndiswrapper

```

So that's it.  Still doesn't work, but at least I know why now.  So I guess I'm off to hunt down a 64-bit solution.

Thanx much for the help.  Hopefully this will save someone some time troubleshooting.

---

### Post by wieman01 on 2007-10-22
> **dingansich said:**
> Well I found the problem!  And it is a 64bit issue.  Here is the output of cat /var/log/dmesg | grep ndis:

```

ndiswrapper version 1.45 loaded (smp=yes)
ndiswrapper (check_nt_hdr:153): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
ndiswrapper (load_sys_files:216): couldn't prepare driver 'rt2500usb'
ndiswrapper (load_wrap_driver:118) couldn't load driver rt2500usb; check system log for messages from loadndisdriver
usbcore: registered new interface driver ndiswrapper

```

So that's it.  Still doesn't work, but at least I know why now.  So I guess I'm off to hunt down a 64-bit solution.

Thanx much for the help.  Hopefully this will save someone some time troubleshooting.
Hang on... Could you get ahold of the 64-bit version of the Windows driver? Plus the latest "ndiswrapper" CVS should support 64-bit, if not the current one also.

Try again with the 64-bit Windows driver. This is a very interesting finding, mate. Perhaps there is a solution.

---

### Post by douradinhos on 2007-10-22
my connection works fine, but everytime i restart i have to do 

sudo modprobe ndiswrapper

or my wireless conection doesnt even show.  anyway i can fix this?? my driver is rt2500usb and im on Gutsy

---

### Post by kashms on 2007-10-22
Add ndiswrapper to the end of the /etc/modules file.

---

### Post by wieman01 on 2007-10-22
> **douradinhos said:**
> my connection works fine, but everytime i restart i have to do 

sudo modprobe ndiswrapper

or my wireless conection doesnt even show.  anyway i can fix this?? my driver is rt2500usb and im on Gutsy
Yes, do this:
> sudo ndiswrapper -m
The module should be loaded on startup from now on. If that does not do try this:
> sudo -s
cat ndiswrapper >> /etc/modules
exit

---

### Post by douradinhos on 2007-10-22
*sudo ndiswrapper -m* -> didnt work, i have to sudo modprobe ndiswrapper anyway.

[I]xtanki@xtanki-desktop:~$ sudo -s
root@xtanki-desktop:~# cat ndiswrapper >> /etc/modules
cat: ndiswrapper: No such file or directory[/I]

---

### Post by wieman01 on 2007-10-22
Then do like Kashms has pointed out:
> sudo gedit /etc/modules
Then add...
> ndiswrapper
...at the very end of it. Then reboot.

---

### Post by douradinhos on 2007-10-22
It Works!! thanks kashms and wieman01 :guitar:

---

### Post by wieman01 on 2007-10-22
> **douradinhos said:**
> It Works!! thanks kashms and wieman01 :guitar:
My fault... I missed that part in the tutorial as I don't use Network Manager. NM requires you to load the module at boot. Thanks for your patience, mate. I have corrected it.

---

### Post by jnorthr on 2007-10-22
pardon me for asking this question as perhaps it is too dumb but are you runing your wireless networks as ad-hoc systems where the devices talk computer-to-computer or in infrastructure mode where there is supposed to be some device that acts as the access point ?

I've been working for a few weeks trying to get my windows XP with adsl connection and linksys wusb54g v4 network adapter to play ball with my ubuntu 7.0.4 laptop with pcmcia linksys wpc54gs v2. It worked for a few days using ad-hoc mode but something killed the wlan0 device and i lost it all. No notes as usual could bring it back. So i thought i'd try infrastructure mode cos there was no wep/wpa security on the ad-hoc settings.

My thinking was that if the XP system with internet connect could be the 'server' and all the laptops act as 'clients' that should work (in theory). So how to implement this plan ? Use ad-hoc network with weak security or infra... with something better.  Any ideas ?  :frown:

---

### Post by dingansich on 2007-10-22
I got my setup working this morning!

So there are a few things to note for amd64 users on Gutsy:

You need a 64-bit driver, which I found here: [http://forums.linksys.com/linksys/board/message?board.id=Wireless_Adapters&message.id=2699]("http://forums.linksys.com/linksys/board/message?board.id=Wireless_Adapters&message.id=2699")

Install it as you normally would (as per the sticky) with ndiswrapper.  However, this driver doesn't seem to like the wlan0 interface id, so you need to use rausb0 in your /etc/network/interfaces file.  Other than that, make sure that the appropriate drivers are listed in your /etc/modprobe.d/blacklist file, and that ndiswrapper is included in your /etc/modules file.  Reboot, and voila!  (At least that's how it worked for me.)

Thanks again to everyone that helped out with this!  :)

---

### Post by Bertybulldog on 2007-10-22
I just spent all day installing GG on my desktop in the hope that the wifi issues had finally been solved.  Unfortunately in the process my previously (mostly) working installation of Freespire 2 has been disabled (even though it is installed on another hard drive).  Freespire has its issues but at least I could get on the internet - first time as it happens.

I am absolutely staggered that something as fundamental to an operating system as providing a reliable way of connecting ot the internet is still not available in Ubuntu.  

Frankly, what on earth are they thinking of?  I'm off to reinstall my Freespire 2; I like everything else about Ubuntu, which is why I keep coming back, hoping against hope that they've finally sorted this basic issue.

FYI I tried the tutorial, but as I have no internet connection without wifi, it's a bit of a chicken and egg situation, so the whole thing falls over at the first line.

A very disappointed Berty signing off of Ubuntu for the third time. 

:(:(:(:(:(:(:(

---

### Post by terdon on 2007-10-22
That's a shame cause I have exactly the opposite experience with Ubuntu. It is in fact the ONLY operating system (the card never worked under windows nor various versions of SuSe linux)  which has recognised my onboard wireless both correctly and automatically (in feisty, see my previous post for Gutsy).

PS. What's wrong with your other system? Are you sure it is not just a simple grub/lilo error? If the system is still there, it is quite simple to load it.

---

### Post by AdHavoc on 2007-10-22
My vendor CD for Windows had the rt61 driver on it, and it installed with ndiswrapper fine... but it hasn't worked.  I'm wondering if I should add rt61 to the blacklist to get it functioning correctly?

---

### Post by wieman01 on 2007-10-22
> **dingansich said:**
> I got my setup working this morning!

So there are a few things to note for amd64 users on Gutsy:

You need a 64-bit driver, which I found here: [http://forums.linksys.com/linksys/board/message?board.id=Wireless_Adapters&message.id=2699]("http://forums.linksys.com/linksys/board/message?board.id=Wireless_Adapters&message.id=2699")

Install it as you normally would (as per the sticky) with ndiswrapper.  However, this driver doesn't seem to like the wlan0 interface id, so you need to use rausb0 in your /etc/network/interfaces file.  Other than that, make sure that the appropriate drivers are listed in your /etc/modprobe.d/blacklist file, and that ndiswrapper is included in your /etc/modules file.  Reboot, and voila!  (At least that's how it worked for me.)

Thanks again to everyone that helped out with this!  :)
Thanks for letting us know. I'll update the tutorial and mention your post concerning 64-bit.

---

### Post by wieman01 on 2007-10-22
> **Bertybulldog said:**
> FYI I tried the tutorial, but as I have no internet connection without wifi, it's a bit of a chicken and egg situation, so the whole thing falls over at the first line.
No, it does not. You either connect to Internet via Ethernet (very simple I promise) or install from CD as highlighted in the tutorial. Perhaps read it carefully once again?

---

### Post by wieman01 on 2007-10-22
> **AdHavoc said:**
> My vendor CD for Windows had the rt61 driver on it, and it installed with ndiswrapper fine... but it hasn't worked.  I'm wondering if I should add rt61 to the blacklist to get it functioning correctly?
Yes, you could try:
> rt61
rt61usb
rt61pci
Please blacklist all of them and get back to us. Would be nice to hear if it works for you or not. Thanks.

---

### Post by bigboy_pdb on 2007-10-23
For those of you who don't want to use ndiswrapper (and you'd prefer to use the modules that came with Gutsy) you might want to try the solution that worked for me. It can be found here:
[http://ubuntuforums.org/showthread.php?t=587727](http://ubuntuforums.org/showthread.php?t=587727)

---

### Post by kashms on 2007-10-23
> **AdHavoc said:**
> My vendor CD for Windows had the rt61 driver on it, and it installed with ndiswrapper fine... but it hasn't worked.  I'm wondering if I should add rt61 to the blacklist to get it functioning correctly?

Yes, you should otherwise they could be conflicting with eachother. I blacklisted rt61pci and added ndiswrapper to the end of /etc/modules and everything worked.

Right click on network manager in panel and select "Connection Information" to see which driver is being used.

---

### Post by wieman01 on 2007-10-23
> **kashms said:**
> Yes, you should otherwise they could be conflicting with eachother. I blacklisted rt61pci and added ndiswrapper to the end of /etc/modules and everything worked.

Right click on network manager in panel and select "Connection Information" to see which driver is being used.
So the RT61 works as well? Great, I have updated the "blacklist". Thanks for letting me know.

---

### Post by kashms on 2007-10-23
> **wieman01 said:**
> So the RT61 works as well? Great, I have updated the "blacklist". Thanks for letting me know.

Yes the RT61 chipset works under Gutsy. The supplied drivers called rt61pci works as well, but in my experience they were unstable. That's why I changed to Windows drivers with ndiswrapper.

---

### Post by grayarea on 2007-10-23
Sorry but I am a relative noob but upgraded from 7.04 to 7.10 and now my Belkin card refuses to work. The first install 7.04 worked without installing any driver in fact it was a breeze but now I am stuck and not sure how to fix problem. I have installed rt2500.inf ndiswrapper tells me it is installed correctly but network manager does not recognise the wireless card. I have been trying to change /etc/netowrk/interfaces but no joy. I am frustrated and deeply regretting the upgrade.
Any help appreciated.

---

### Post by wieman01 on 2007-10-23
> **grayarea said:**
> Sorry but I am a relative noob but upgraded from 7.04 to 7.10 and now my Belkin card refuses to work. The first install 7.04 worked without installing any driver in fact it was a breeze but now I am stuck and not sure how to fix problem. I have installed rt2500.inf ndiswrapper tells me it is installed correctly but network manager does not recognise the wireless card. I have been trying to change /etc/netowrk/interfaces but no joy. I am frustrated and deeply regretting the upgrade.
Any help appreciated.
Please post the results of:
> sudo iwlist scan
> sudo ifdown -v wlan0
> sudo ifup -v wlan0

---

### Post by beejaycee on 2007-10-23
> **wieman01 said:**
> 
Feedback is - as always - appreciated.

Thank you, thank you, thank you!  I struggled with my WUSB54G V4 and was finally able to get it running under Feisty but had been unable to get it working w/Gutsy.  I walked through your steps and it came up immediately after the reboot. =D>=D>  Boo-yeah!

---

### Post by grayarea on 2007-10-23
> **wieman01 said:**
> Please post the results of:

Here are the results of various ouputs. ra0 was the previous wireless name so I wonder whether it may be confused. Also of concern although the device is listed in device manager I can't find any reference if I run dmesg. I think maybe the easiest way out will be to clean install 7.04.

Sorry also not very clued in how to quote previous message

---

### Post by mummra1 on 2007-10-23
Hey wieman,
     I think I'm going to frame your ndiswrapper install guide and hang it in my room.  I upgraded to Gutsy and it broke my Belkin wireless, but now it's back up and runnin' smooth!  Thanks!

---

### Post by wieman01 on 2007-10-23
> **grayarea said:**
> Here are the results of various ouputs. ra0 was the previous wireless name so I wonder whether it may be confused. Also of concern although the device is listed in device manager I can't find any reference if I run dmesg. I think maybe the easiest way out will be to clean install 7.04.

Sorry also not very clued in how to quote previous message
Mmm... to what extend did you follow this tutorial? It seems that you have missed a few crucial steps. Do you have the right drivers for your adapter?

---

### Post by stevoo on 2007-10-24
cause i am not sure .... i have a Dell 6400 with network card 

 Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
14e4:4311 (rev 01)

And as my Wirelles connection with Gutsy is extremely buggy, i wanna give a shot to this perhaps it may work better. But i am not sure what version should i use. 
Any help will be greatly appreciated !

---

### Post by bastikr on 2007-10-24
I updated from feisty to gutsy and like many others I now have the problem that my wlan isn't working anymore. I followed your howto as good as possible, but I have the problem that when I unzipped the driver exe I found no .inf file. (I had to use cabextract since simply unzipping didn't work for me,)
does cabextract not extract all files or is it possible that my driver is different?

---

### Post by wieman01 on 2007-10-24
> **bastikr said:**
> I updated from feisty to gutsy and like many others I now have the problem that my wlan isn't working anymore. I followed your howto as good as possible, but I have the problem that when I unzipped the driver exe I found no .inf file. (I had to use cabextract since simply unzipping didn't work for me,)
does cabextract not extract all files or is it possible that my driver is different?
You should be able to unzip the file in Windows. Or could you not download the driver from the web somewhere? It should be available as an .EXE archive.

---

### Post by wieman01 on 2007-10-24
> **stevoo said:**
> cause i am not sure .... i have a Dell 6400 with network card 

 Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
14e4:4311 (rev 01)

And as my Wirelles connection with Gutsy is extremely buggy, i wanna give a shot to this perhaps it may work better. But i am not sure what version should i use. 
Any help will be greatly appreciated !
Honestly I have no experience with Broadcom drivers. I have seen tutorials in the forums, so you might want to check them out first. We could try this one, but I cannot be of much help in that case.

---

### Post by bd@cb8be8510 on 2007-10-25
I made an upgrade van feisty to gutsy. So I' cant use my wireless network either (I'm using a ASUS WL-167G USB-adapter). However if I start gutsy from the previous kernel build Kernel 2.6.20-16 all is working fine again! 

Temporarily I'm working with kernelbuild 2.6.20-16 i.s.o.
2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux.

I think that 2.6.22-14 is not loading the right drivers?
Listing the hardware gives me the following results:

Kernel 2.6.20-16 :

*-network
description: Wireless interface
physical id: 1
logical name: rausb0
serial: 00:11:d8:8e:79:2d
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=RT2500USBSTA driverversion=1.0.0 - BETA2 multicast=yes wireless=RT2500USB WLAN

Kernel 2.6.22-14 :

*-network
description: Wireless interface
physical id: 1
logical name: rausb0
serial: 00:11:d8:8e:79:2d
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

How can I skip the IEEE 802.11g driver and use the rt2500-drivers instead (as they are working fine with build 2.6.20-16)?

---

### Post by magician on 2007-10-25
Hi,


Thanks for your advices.

I studied for more then four days many threads to create a wireless connection with my usb ralink rt2500, which worked fine under feisty fawn.

I tried Rutilt, WICD, lots of other advices and finally I followed your instructions completely, but at the end again no result.

At top of the desktop there is a icon with the connection visible, but I cannot contact the router nor internet.

At another location Gutsy works fine with wired.

Now I reached the end and I am thinking of de-install Gutsy 64-bits.

My system is sempron3000_754 2048 MB of DDR 

Sometimes only I have the:

loopback interface  (lo)
Ethernet interface  (eth0)
Unknown interface  (Wmaster0)
Wireless interface (wlan0)
Wireless interface (wlan0: avani)

Another time 1,2,3 and 4
And sometimes just the first to ones, 
or number 1,2 and 4.

The more I follow the threads the more I am puzzled.

Kind Regards

John


magician@sempron3000:~$ sudo iwlist scan
[sudo] password for magician:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:03:C9:73:28:EC
                    ESSID:"Wanadoo_9594"
                    Mode:Master
                    Channel:10
                    Frequency:2.457 GHz
                    Signal level=-27 dBm  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000020361301f



magician@sempron3000:~$ sudo ifdown -v wlan0
ifdown: interface wlan0 not configured


magician@sempron3000:~$ sudo ifup -v wlan0
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant

dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.wlan0.pid -lf /var/lib/dhcp3/dhclient.wlan0.leases wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:06:f4:0e:64:20
Sending on   LPF/wlan0/00:06:f4:0e:64:20
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/avahi-autoipd
run-parts: executing /etc/network/if-up.d/avahi-daemon
run-parts: executing /etc/network/if-up.d/mountnfs
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/wpasupplicant
magician@sempron3000:~$

---

### Post by bastikr on 2007-10-25
I extracted the driver on windows and like before in linux there were no .inf files inside. Only some dll, tlb and rgs files seem to be in the exe.
I tried the same with the driver I found at [http://www.treiberupdate.de/treiber-download/download-159199-treiber-Ralink-RT2500USB.html](http://www.treiberupdate.de/treiber-download/download-159199-treiber-Ralink-RT2500USB.html)
but I got the same files as before.
Has someone an idea what I'm doing wrong?

---

### Post by Fruhwirth on 2007-10-25
I hate to be the really dumb kid, but I can' t get the unzip command to work.  

> user@user-laptop:~/RA2500driver$ unzip driver.exe
Archive:  driver.exe
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of driver.exe or
        driver.exe.zip, and cannot find driver.exe.ZIP, period.


Note, I changed the name of the file to "driver.exe" from the really, really long version. lspci says I have  RaLink RT2500 802.11g Cardbus/mini-PCI.  I'm trying to open **[this file]("http://www.ralinktech.com.tw/data/drivers/IS_AP_STA_6x_D-1.2.3.0_VA-2.0.7.0_2500_D-3.2.0.0_VA-3.2.0.0_RU-2.0.3.0_VA-1.0.18.0_AU_1.2.0.0_091407_0.1.0.29.exe")** found second-from-the-last on**[ this page]("http://www.ralinktech.com/ralink/Home/Support/Windows.html")**.  That's the correct driver, right?

I think I've got everything else in the HOWTO setup and ready to go, but it's hard to know if it will all work without the proper driver in ndiswrapper.

I googled and searched the forum and only found [**this**,]("http://ubuntuforums.org/showthread.php?p=3633610#post3633610") where I also posted. 

help?

---

### Post by ricardisimo on 2007-10-25
> **wieman01 said:**
> Yes, this issue sounds very familiar. 

Let me think... it could relate to "ipv6" that is enabled by default. You need to turn it off both globally (i.e. in the system) and in Firefox. This is a helpful link for you:

_Gobal "ipv6":_
[http://ubuntuforums.org/showthread.php?t=87798]("http://ubuntuforums.org/showthread.php?t=87798")

_Firefox:_
[http://kb.mozillazine.org/Network.dns.disableIPv6]("http://kb.mozillazine.org/Network.dns.disableIPv6")

Those settings should make your browsing speed significantly faster.

It looks like you may have hit the nail on the head. I haven't tried anything yet, so I'll make sure to let you know how it went when I do. But, I just noticed that the problem appears to be restricted to web server usage. My newsreader is downloading at 400-500 kbps, which is exactly what I've been expecting all along. Wish me luck, and thanks for those links.

P.S. - Has anyone else noticed that the Mozilla apps are dragging well beyond what they've done in the past? They just seem like complete resource hogs, and slow about it, too.

---

### Post by bd@cb8be8510 on 2007-10-26
I downloaded the latest drivers from serialmonkey, installed them and got my wireless network working again! (I' m using a See ASUS WL-167G USB-adapte) No  legacy-drivers are required.

See [http://ubuntuforums.org/showthread.php?t=584657](http://ubuntuforums.org/showthread.php?t=584657)

---

### Post by magician on 2007-10-26
> **wieman01 said:**
> **Dapper Drake** users should take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=192588") if this one doesn't work.
--
This is a simple guide for all Ralink based wireless adapters and everyone who wants to replace the Linux driver with "ndiswrapper" (e.g. because you want to make use of either [Network Manager]("http://www.gnome.org/projects/NetworkManager/") or [WICD]("http://wicd.sourceforge.net/")). 

[LIST]
[*]Get the latest version of the Windows driver for your card from [Linksys' website]("http://www.linksys.com/servlet/Satellite?c=L_CASupport_C1&childpagename=US%2FLayout&cid=1166859840888&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4088837314B372&displaypage=download") or from the CD that came with your device (whatever vendor). 
[/LIST]

[LIST]
[*]Install "ndiswrapper" package **with** working internet connection (Ethernet):

[/LIST]

[LIST]
[*]Install "ndiswrapper" package **without** working internet connection (alternatively, install it via Synaptic/Adept):

[/LIST]

[LIST]
[*]Load new driver module (may not be necessary any longer, but does no harm either):

[/LIST]

[LIST]
[*]Add the module to "/etc/modules" to have it load automatically (use "kate" instead of "gedit" in Kubuntu):

[*]Now add this to the end & save the file:

[/LIST]

[LIST]
[*]Create alias directive:

[/LIST]

[LIST]
[*]Pick a valid Ralink driver based on the chipset of your card (you might blacklist all of them if you are not sure):

[/LIST]

[LIST]
[*]Blacklist Ralink driver by opening this file...

[/LIST]

[LIST]
[*]...and adding this line at the end (e.g. blacklist rt2500usb):

[/LIST]

[LIST]
[*]Now unzip the driver archive you have just downloaded (e.g. in your home directory):

[/LIST]

[LIST]
[*]Now find the right driver in the resulting folder & deploy it (folder should also contain other driver files i.e. .cat, .sys):

[/LIST]

[LIST]
[*]Make sure it has installed correctly:

[/LIST]

[LIST]
[*]The output should yield something like this:

[/LIST]

[LIST]
[*]Last but not least open this file...

[/LIST]

[LIST]
[*]...and add these 2 lines if they are not there yet:

[/LIST]
You can  now safely delete the extracted driver files & folders. Then reboot the computer and see if you can connect using your favorite networking applet (e.g. Network Manager, WICD, Wifi Radar, etc.). 

Feedback is - as always - appreciated.

_**CHANGE LOG:**_
30/09/2007: Minor fixes.
07/10/2007: Expanded "blacklist".
20/10/2007: Added missing part concerning "interfaces" file.
22/10/2007: Load module "ndiswrapper" at boot.
23/10/2007: Enhanced blacklist.

Thanks alot Wieman1 and excellent forum
Today I decided to install Gutsy anew and without changing anything, nor following other threads I work around like you adviced.

On restart Network Manager did not work for me on my Ralink rt2500usb.

Then decided to uninstall Netwoirk Manager and installed Rutilt.

First time after restart Rutilt did not work, but received only error messages on entering allowed.
I restarted two other times and then the connection was OK.

Thanks again.

Kind :KS Regards

---

### Post by Fruhwirth on 2007-10-27
Since no one seems immediately able to help me with the "End-of-central-directory signature not found" error I tried to use [this driver file]("http://www.yournewdriver.com/Ralink_RT2500_Wireless_LAN_Card_1149.htm"). Within it, there is are drivers for "winx64" which I used because I am on GG64. It installed correctly but now I can not scan.  
> 
user@user-laptop:~$ sudo iwlist scan
[sudo] password for user:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

jesse@jesse-laptop:~$ 

My intereface file: 

> auto lo
iface lo inet loopback


auto eth0
iface eth0 inet dhcp


auto ra0
iface ra0 inet dhcp
I tried logical name wlan0 instead of ra0 in the interface file and got the same results - i.e. it's recognized but non-functional. I switched to ra0 because that was the logical name for the device under dapper. 

ndiswrapper is listed on my modules file and I blacklisted every driver that is listed in this HOWTO.  I've followed this HOWTO from top to bottom four-er-five  times or so, even uninstalling ndiswrapper and starting from scratch. I've done it all but fresh install Gutsy and start the HOWTO anew. 

It seems to me this driver file is no good or isn't right for my card. If there is anyone who has used successfully a 64-bit driver for the RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01) in accordance with wieman's fantastic HOWTO, could you please post the .inf, .cat, and .sys?  Or, can anyone tell me why I can't open the .exe file from Ralink's web site like everyone else seems to be doing?

Alternatively, if any of you wise and helpful souls think I'm sunk and wieman's HOWTO simply isn't going to work for my hardware for whatever reason, let me know that, too.

---

### Post by Startacus on 2007-10-27
I'm a beginner to Linux and I'm trying to get my Belkin 54g USB Adapter to work with the rt73 driver from their website. 

I should note that my router has a WPA TKIP passphrase set and the SSID isn't being broadcast. 

I followed the instructions above and when I run "ndiswrapper -l" It displays:
> rt73 : driver installed

It doesn't display that the hardware is present though.

When I run "sudo iwlist scan" this is the result:

> lo                        Interface doesn't support scanning.
              eth0                    Interface doesn't support scanning.
              wmaster0            Interface doesn't support scanning.
              wlan1                  Interface doesn't support scanning : Network is down

At this point I am lost. 

Another thing, my network manager icon (Like in Windows where it tells you are connected or not) has an exclamation point. When I try to enter my SSID and my password in the "Connect to Other Network Option" it looks for it but then goes back to the exclamation point. 

I would really appreciate any help that you can give.

EDIT: I used the rt2500usb driver from the CD and now it works! I just need to figure out how to get WPA to work now.............

---

### Post by wieman01 on 2007-10-27
> **Fruhwirth said:**
> Since no one seems immediately able to help me with the "End-of-central-directory signature not found" error I tried to use [this driver file]("http://www.yournewdriver.com/Ralink_RT2500_Wireless_LAN_Card_1149.htm"). Within it, there is are drivers for "winx64" which I used because I am on GG64. It installed correctly but now I can not scan.  


My intereface file: 


I tried logical name wlan0 instead of ra0 in the interface file and got the same results - i.e. it's recognized but non-functional. I switched to ra0 because that was the logical name for the device under dapper. 

ndiswrapper is listed on my modules file and I blacklisted every driver that is listed in this HOWTO.  I've followed this HOWTO from top to bottom four-er-five  times or so, even uninstalling ndiswrapper and starting from scratch. I've done it all but fresh install Gutsy and start the HOWTO anew. 

It seems to me this driver file is no good or isn't right for my card. If there is anyone who has used successfully a 64-bit driver for the RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01) in accordance with wieman's fantastic HOWTO, could you please post the .inf, .cat, and .sys?  Or, can anyone tell me why I can't open the .exe file from Ralink's web site like everyone else seems to be doing?

Alternatively, if any of you wise and helpful souls think I'm sunk and wieman's HOWTO simply isn't going to work for my hardware for whatever reason, let me know that, too.
Sorry for my absence. I was not around for 3 days.

Question... you have a 64-bit system. 64-bit can be a pain in the throat. Nevertheless, can you not find a driver on the vendor's website for instance? Have you downloaded the 64-bit version of it?

There is another HOWTO which might help if you fail to set it up using this one:

[http://ubuntuforums.org/showthread.php?t=584657]("http://ubuntuforums.org/showthread.php?t=584657")

---

### Post by wieman01 on 2007-10-27
> **bd@cb8be8510 said:**
> I made an upgrade van feisty to gutsy. So I' cant use my wireless network either (I'm using a ASUS WL-167G USB-adapter). However if I start gutsy from the previous kernel build Kernel 2.6.20-16 all is working fine again! 

Temporarily I'm working with kernelbuild 2.6.20-16 i.s.o.
2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux.

I think that 2.6.22-14 is not loading the right drivers?
Listing the hardware gives me the following results:

Kernel 2.6.20-16 :

*-network
description: Wireless interface
physical id: 1
logical name: rausb0
serial: 00:11:d8:8e:79:2d
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=RT2500USBSTA driverversion=1.0.0 - BETA2 multicast=yes wireless=RT2500USB WLAN

Kernel 2.6.22-14 :

*-network
description: Wireless interface
physical id: 1
logical name: rausb0
serial: 00:11:d8:8e:79:2d
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

How can I skip the IEEE 802.11g driver and use the rt2500-drivers instead (as they are working fine with build 2.6.20-16)?
Maybe you need to compile them against the latest kernel?

---

### Post by wieman01 on 2007-10-27
> **Startacus said:**
> I used the rt2500usb driver from the CD and now it works! I just need to figure out how to get WPA to work now.............
Great. You could try my tutorial on WPA. See if it works for you (it definitely should). :-)

---

### Post by wieman01 on 2007-10-27
> **bastikr said:**
> I extracted the driver on windows and like before in linux there were no .inf files inside. Only some dll, tlb and rgs files seem to be in the exe.
I tried the same with the driver I found at [http://www.treiberupdate.de/treiber-download/download-159199-treiber-Ralink-RT2500USB.html](http://www.treiberupdate.de/treiber-download/download-159199-treiber-Ralink-RT2500USB.html)
but I got the same files as before.
Has someone an idea what I'm doing wrong?
Aren't there any of the mentioned files on the CD that came with the card?

---

### Post by bastikr on 2007-10-28
On CD there is only a file RaLink2_RT2500USB.exe. When I extract it, I get the following files:
  - IKernel.dll
  - ctor.dll
  - IScript.dll
  - IUser.dll
  - objectps.dll
  - DotNetInstaller.exe
  - iKernel.rgs
  - ISProBE9x.tlb
  - ISProBENT.tlb

---

### Post by wieman01 on 2007-10-28
> **bastikr said:**
> On CD there is only a file RaLink2_RT2500USB.exe. When I extract it, I get the following files:
  - IKernel.dll
  - ctor.dll
  - IScript.dll
  - IUser.dll
  - objectps.dll
  - DotNetInstaller.exe
  - iKernel.rgs
  - ISProBE9x.tlb
  - ISProBENT.tlb
Any other way you can get ahold of driver files? You are right, these aren't the correct ones.

---

### Post by anteus on 2007-10-28
Loved the HOWTO! Now I get the same speed as I did in Feisty (without ndiswrapper).

---

### Post by mocha on 2007-10-28
Thanks for this HOWTO!  It worked for me!  Nice find on Rutil as well.

---

### Post by fsufitch on 2007-10-28
Hey. I'm building myself a computer to experiment with Linux on. Right now it's a pretty pathetic box but nevertheless is running Kubuntu Feisty and running it well. 
The problem is that, my box just having been upgraded from a scavengeable computer, and with me being just a penniless high school student, it doesn't have a wireless network card! I borrowed one from school, and it's a Linksys WMP54G, but doesn't have a version number marked on it, as the Linksys website says it must. I tried installing all of the drivers using the method described in this thread, but the only effect it had was to make knetworkmanager stop complaining about not being able to configure the interface. It still doesn't connect. The way I got wireless to work on my laptop (the computer I'm currently using) was to install wlassistant, then just mess around with it, but this time it doesn't seem to work.
A clue or something plz?
I'm trying to connect to a WEP'd interface and have no chance of getting it un-WEP'd as it's the only way my dad can control my internet use :). Any ideas?

Thanks,
fsufitch

---

### Post by bastikr on 2007-11-02
> Any other way you can get ahold of driver files? You are right, these aren't the correct ones.

I found some drivers in the internet that seemed to be promising, but they are build like the one I already had:(

---

### Post by xshakakee on 2007-11-03
OK, it looks like everyone is having some trouble here, with the exception of the OP.  This may not be quick, but I think I solved my problem,  First, here is my system:

AMD Sempron 2800+, socket 754
Asus K8V-VM, one of those on-board everything boards
512 MB Kingston DDR400 RAM
160 gig Maxtor HDD
RT2500 PCI card.  Belkin 7000, version 3

At least I think that's the card's name.  I haven't looked at it in a while.
I know I plugged it into a Mac, and had to download the ralink utility.
That worked.  I know it has a ralink chipset.

Anyway, I was buzzing along with Edgy (6.10) and decided to make the jump to Gutsy.  I actually did a fresh install of Ubuntu 7.10 on a new hard drive.  Big problem.  Drivers for ra2500 didn't work "right out of the box"  After some forum browsing, and lots of trial and error, I came to this solution.

Oh, and for those of you who hate to type sudo all the time, just go into terminal and type:
```

sudo su

```
enter your password at the prompt, and leave that terminal open.
Any time you need to code anything, just copy the part after "sudo".  
It really saves time.
I started out on the wired network, so I had to change my default networking parameters.
I did this by running: 
```

sudo gedit /etc/network/interfaces

```
and making it look like this:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.2.4
netmask 255.255.255.0
gateway 192.168.2.1

```
As you can see, I don't have dhcp enabled.  It's a lot easier with dhcp. (Sorry, you'll have to go back to earlier posts if you need to set up dhcp.)

I plugged in the wire, and I was on my way.  I must have done this the right way the first time, because I could resolve names at this point.  I re-installed the OS because I had an unrelated issue (it had to do with xorg.conf)

Anyway, if plugging in the wire doesn't work for you, go into Network Manager, (System --> Administration --> Network) and futz around with it until you get on the network.  Sorry, I'm going to assume you can at least get out on the internet from the wire.  If you can't do even get that, then you'll have to use a different tutorial until you can.

First, I ran:
```

sudo apt-get install build-essential linux-headers-`uname -r`

```
For some reason, this prompted me to insert the CD-Rom into the drive.  I did so, but I consider this stupid.  Going on...
(Actually, the above step is unnecessary, but I included it because this is what I originally did.  You need only download the cvs, from the wired network.)

I downloaded the latest CVS from

[http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)

I pulled down the legacy rt2500 driver, which in my case was 

rt2500-cvs-2007102623

**Do Not Download the Beta!**
The beta driver will not compile, on a default install of the OS.  You get all these dependency errors.  The CVS compiled nicely.
```

tar -xvzf rt2500-cvs-daily.tar.gz
cd rt2500-cvs-2007102623/Module
	make
	sudo make install

```
Then:
```

	echo "blacklist rt2500pci" >> /etc/modprobe.d/blacklist

```

Next, Uninstalled networking manager
```

sudo apt-get remove network-manager-gnome

```
I restarted at this point, not knowing how to remove modules and add them on the fly.

Once I did that, I had a network conflict, since I was still plugged into the wired.

A better method would have been to use the following code:
```

	sudo ifconfig wlan0 down
	sudo modprobe -r rt2500pci
	sudo modprobe rt2500

```
Then, in order to make my wired ethernet disappear:
```

sudo gedit /etc/network/interfaces

```
and edit the file so that it looks like this:
```

auto lo
iface lo inet loopback

[COLOR="Red"]#[/COLOR]auto eth0
iface eth0 inet static
address 192.168.2.4
netmask 255.255.255.0
gateway 192.168.2.1

```
Last step, at this phase, is to restart the network:
```

sudo /etc/init.d/networking restart

```

OK -- but still no network!  What gives.  Let's be patient, shall we?

I added wicd through the Synaptic package manager, following the instructions here:

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

Turns out, I didn't actually use it to set up my network, but it is a handy network monitor; a good Network Manager surrogate

What seems to have worked, from this point onward, was going back to:
```

sudo gedit /etc/network/interfaces

```
and adding the following lines, in red:
```

auto lo
iface lo inet loopback

#auto eth0[COLOR="Red"]
iface eth0 inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.2.2
gateway 192.168.2.1
dns-nameservers <ip address of nameserver1>, <ip address of nameserver2>
netmask 255.255.255.0

pre-up ifconfig wlan0 up
pre-up ifconfig wlan0 down
pre-up ifconfig wlan0 up
pre-up ifconfig wlan0 down
pre-up iwconfig wlan0 essid "My SSID"
pre-up iwconfig wlan0 mode Managed
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set EncrypType=TKIP
pre-up iwpriv wlan0 set WPAPSK="my preshared key"
pre-up ifconfig wlan0 up
[/COLOR]
```
As you can see, I modified the heck out of the eth0 portion, as well as adding
an entirely new portion, the wlan0.

Once I ran: ```
sudo /etc/init.d/networking restart
```
it all came up.  I rebooted a couple of times, and the changes seemed to have taken.

One caveat: I have a card with little blinking lights in the back, so I know when it is active.  (I actually have the USB version of this adapter, and love it because it blinks at me when active.  It's on the MAC, though.)  At some point, the lights are going to go off.  I got frustrated with this several times, and thought, what am I doing wrong?  I solved it (I think) by using various iterations of the following code:
```

sudo ifconfig wlan0 down
sudo modprobe -r rt2500pci
sudo depmod
sudo modprobe rt2500
sudo depmod

```
I ran this, and ran the restart script, and the adapter seems to have kicked in.  You need to have the original driver, rt2500pci blacklisted, in ```
/etc/modprobe.d/blacklist
```

Also, you *may* need to modify your resolv.conf.  I did because I got rid of network manager before I could even create this file.  Therefore, my machine did not know where to go for DNS resolution.  Here's how you do it.
```

sudo gedit /etc/resolv.conf

```
Make sure the following lines are in there:
```

nameserver 208.67.220.220
nameserver 208.67.220.222

```
That's all.  The mandatory OpenDNS servers is all you need.  You can also pull the nameservers from your cable/dsl provider, but I find it easier just to stick with these two.

That's it!  Fire up WICD, restart your network:
```

sudo /etc/init.d/networking restart

```
and you should be on the way!

---

### Post by bastikr on 2007-11-03
@xshakakee
Thanks a lot for your tips. This was the right way for me! My wlan is running perfectly!\\:D/
Maybe you should post this howto in an own thread, since many people won't look for it here.

---

### Post by bastikr on 2007-11-03
Okay, I got now a new strange problem. The Interface of my wlan card switches it's name after startup always into a name that does'nt occur in /etc/network/interfaces!
For example, if my /etc/network/interfaces looks like the following:

> auto lo
iface lo inet loopback

pre-up ifconfig rausb0 up
pre-up ifconfig rausb0 down
pre-up iwconfig rausb0 essid "default"
pre-up iwconfig rausb0 key "21EB0462EF11B394F8EEA982A3"
pre-up iwconfig rausb0 mode Managed
pre-up ifconfig rausb0 up
auto rausb0
iface rausb0 inet dhcp


Then after a reboot, ifconfig tells me that the interfaces name is wlan0.
When I change rausb0 to wlan0 and do /etc/init.d/networking restart
everything is alright until I reboot my system.
Then the game starts again: interface is the rausb0 and I have to change wlan0 to rausb0....

Maybe I should mention that I use Rutilt. (Don't know if this matters)

Has anyone experienced a similar problem?

---

### Post by xshakakee on 2007-11-03
bastikr, looks like there's something going on during initiation of your wireless card.  To make things easier, you might try this.
Go into /etc/network/interfaces:
```

pre-up ifconfig rausb0 up
pre-up ifconfig rausb0 down
pre-up iwconfig rausb0 essid "default"
pre-up iwconfig rausb0 key "21EB0462EF11B394F8EEA982A3"
pre-up iwconfig rausb0 mode Managed
pre-up ifconfig rausb0 up
auto rausb0
iface rausb0 inet dhcp
[COLOR="Red"]
pre-up ifconfig wlan0 up
pre-up ifconfig wlan0 down
pre-up iwconfig wlan0 essid "default"
pre-up iwconfig wlan0 key "21EB0462EF11B394F8EEA982A3"
pre-up iwconfig wlan0 mode Managed
pre-up ifconfig wlan0 up
auto wlan0
iface wlan0 inet dhcp[/COLOR]
```

See if after reboot, the network "just works"
I'll try to post a better solution for you when I've learned more about interface name aliasing, but I think this should solve your immediate problem, for now.

Oh, and I don't think the use of Rutilt vs. WICD makes a difference.  As long as you don't touch settings in the program, it shouldn't make any difference.

OK, I guess I should do a little more research on this before posting, but try this method, and see if it helps.

Obviously, you can delete or comment out the added lines if this doesn't help.  Bye for now.

---

### Post by bastikr on 2007-11-04
I was surprised that it didn't come up with other interface names, but you were right. I added both names and it works now.
It's truly not a very elegant solution, but it is one.:)

> 
I'll try to post a better solution for you when I've learned more about interface name aliasing, but I think this should solve your immediate problem, for now.


Let me now if you find out something, but thanks for your help so far.
Now I only have to set up rutilt to start automatically after bootup, but I think for this I'll look in another thread.

---

### Post by wieman01 on 2007-11-04
> **xshakakee said:**
> OK, it looks like everyone is having some trouble here, with the exception of the OP. 
What makes you think so?

If your tutorial works for other people as well, please let me know because I will include the link to your tutorial in mine. This way people are given options. I don't really like the fact that we need to use "ndiswrapper" at all, so I would appreciate your help. That said submit your tutorial and please send me the link, so that I can include it if you don't mind.

---

### Post by alanmzifa on 2007-11-05
wieman01, I'm trying to get an Asus WG107G PC Card going on Dapper (from my thread you answered last night).

It's a Ralink rt2500 chipped device.

I've followed your how-to and got it set-up wirelessly on wlan0 with no security. My goal is to get some sort of WPA set up. The rest of the network is using WPA2-PSK AES.

I've read that the card is supposed to support WPA-PSK in Windows.I'd settle for anything above WEP encryption but the higher the better.
[B]
Can you guide me through the rest?[/B] I briefly tried WICD but wouldn't even work without encryption. Currently no Network Manager, WPA Supplicant, Wifi Radar or WICD installed but stable without encryption.

thanks

---

### Post by wieman01 on 2007-11-05
> **alanmzifa said:**
> wieman01, I'm trying to get an Asus WG107G PC Card going on Dapper (from my thread you answered last night).

It's a Ralink rt2500 chipped device.

I've followed your how-to and got it set-up wirelessly on wlan0 with no security. My goal is to get some sort of WPA set up. The rest of the network is using WPA2-PSK AES.

I've read that the card is supposed to support WPA-PSK in Windows.I'd settle for anything above WEP encryption but the higher the better.
[B]
Can you guide me through the rest?[/B] I briefly tried WICD but wouldn't even work without encryption. Currently no Network Manager, WPA Supplicant, Wifi Radar or WICD installed but stable without encryption.

thanks
Hello Alan, 

Of course I'll help. So the current Windows driver supports WPA, right? That's the same driver you used in Windows with full WPA support?

You might have seen my WPA howto in my signature. Guess that's a good start. Please try it first and post your problems there. I'll guide you through it.

---

### Post by bfoos on 2007-11-05
Thanks for the guide. I was having trouble with Gutsy's built in support for the RT61 chip-set. Network connection slowing to a crawl and eventually dropping. Ndiswrapper has sorted my problem nicely. Thanks again.

---

### Post by alanmzifa on 2007-11-07
> **wieman01 said:**
> Hello Alan, 

Of course I'll help. So the current Windows driver supports WPA, right? That's the same driver you used in Windows with full WPA support?

You might have seen my WPA howto in my signature. Guess that's a good start. Please try it first and post your problems there. I'll guide you through it.

wieman01, I've foolowed that. Got the card working on no security then installed wpa supplicant and WICD. Went for WPA-PSK TKIP which the card is supposed to support under Windows but signal gets dropped straight away.

I set up using DHCP rather than static. Uninstalled WICD again, No other network management utility currenty installed. Card shows as wlan0 not ra0.

Can you suggest what I could try next?

thanks

---

### Post by wieman01 on 2007-11-07
The standard networking applet (Network Manager) should do the job actually. If you don't need static IP and DHCP will do, NM should be a breeze.
> sudo apt-get install network-manager-gnome
When you open NM, are you given an option to use WPA encryption?

---

### Post by alanmzifa on 2007-11-07
> **wieman01 said:**
> The standard networking applet (Network Manager) should do the job actually. If you don't need static IP and DHCP will do, NM should be a breeze.

When you open NM, are you given an option to use WPA encryption?

I'd tried Network Manager a couple of nights ago but it only gave me option for WEP. I can try it again.

---

### Post by wieman01 on 2007-11-07
> **alanmzifa said:**
> I'd tried Network Manager a couple of nights ago but it only gave me option for WEP. I can try it again.
Mate, if that's the case, then this might have two reasons (generally):

A. You have not installed "wpa-supplicant" (which you have, I know).

B. The Windows driver that you used can't do WPA. Get hold of the README file and see if it actually does.

That's all I can offer at the moment...

---

### Post by seul on 2007-11-08
wieman01, you are my hero! Thank you, thank you, thank you ever so much. After 1 1/2 years of trouble, ubuntu finally connects without a cable. I can't tell you how happy I am. 
Cheers, seul

---

### Post by wieman01 on 2007-11-08
**@Seul:**

Excellent, Seul. Would you mind telling me what hardware you have got? Did you have to edit your "/etc/network/interfaces" as well?

---

### Post by hacklix on 2007-11-08
It can be useful?
[http://forum.ubuntu-it.org/index.php?topic=69879.0]("http://forum.ubuntu-it.org/index.php?topic=69879.0")

---

### Post by seul on 2007-11-08
Do you mean the card or my computer hardwarewise? For the card it is a Belkin Wireless G F5D7010 ver6000uk (rt61).

I tried so many things and don't really know what I am doing when I use the terminal, so I can't really remember how my /interfaces looked like in the beginning. Currently I have
```
auto lo
iface lo inet loopback

#WIRED
auto eth0
iface eth0 inet dhcp

#WIRELESS
auto wlan0
iface wlan0 inet dhcp
```

Only thing is that it did not work before I reinstalled network manager because I couldn't choose "shared key" without netman.

I had tried ndiswrapper with edgy 1 1/2 years ago, but it didn't work, so I didn't give it another try until now. I think that the problem then was that the tutorial I was following didn't mention blacklisting.

Also, the Belkin card used to freeze my entire system when inserted (even when I did not connect), that's gone now, too.

---

### Post by wieman01 on 2007-11-08
> **hacklix said:**
> It can be useful?
[http://forum.ubuntu-it.org/index.php?topic=69879.0]("http://forum.ubuntu-it.org/index.php?topic=69879.0")
Don't really know, it's in Italian. Would should we use it for?

---

### Post by seul on 2007-11-08
I hope the info was what you were asking for. Let me know if not. Thanks again, all the best.

---

### Post by seul on 2007-11-08
I just made a dlink DWL-G122 H/W Ver C1 usb dongle work, too. What a beautiful day!

---

### Post by wieman01 on 2007-11-09
> **seul said:**
> I just made a dlink DWL-G122 H/W Ver C1 usb dongle work, too. What a beautiful day!
Seul, to answer your other question, yes, that's the info I needed. Thank you.

What chipset is that one?

---

### Post by MarkMadsen on 2007-11-09
> **wieman01 said:**
> Seul, to answer your other question, yes, that's the info I needed. Thank you.

What chipset is that one?

The D-Link DWL-G122 Rev C1 is a Ralink rt73.  It works out of the box with 7.10 (even from the liveCD) and network manager has no problems with it.

---

### Post by wieman01 on 2007-11-09
> **MarkMadsen said:**
> The D-Link DWL-G122 Rev C1 is a Ralink rt73.  It works out of the box with 7.10 (even from the liveCD) and network manager has no problems with it.
Alright... some progress at last. Thanks for letting us know. Hope this thread will become unnecessary soon.

---

### Post by seul on 2007-11-09
> **MarkMadsen said:**
> The D-Link DWL-G122 Rev C1 is a Ralink rt73.  It works out of the box with 7.10 (even from the liveCD) and network manager has no problems with it.

I, too, thought it was rt73 for the dlink, but I couldn't get it to work; neither out of the box, nor with serialmonkey ([see my post]("http://ubuntuforums.org/showthread.php?t=604690")). 


> **wieman01 said:**
> What chipset is that one?

When I fetched the driver from dlink's homepage (link is in the post), I found it was called "dr71WU.inf", I don't know if that's just the windows name for rt73 or if it is a different driver after all.

I can't use gutsy because of [this]("http://ubuntuforums.org/showthread.php?t=587984"), so I can only speak about my feisty-experience. I do know from my brief gutsy encounter that the Belkin Wireless G F5D7010 ver6000uk card worked out of the box without freezing the system.

---

### Post by ricardisimo on 2007-11-09
I hope this post isn't unwelcome, because Wieman's HowTo did, in fact, help me get my wireless up and running. However, I thought that maybe Gina and some of the other posters here would like to know about this: I was having way too many problems with Ubuntu 7.10, so I decided to try Kubuntu Gutsy instead. I was _very_ pleasantly surprised. KNetworkManager worked as close to perfectly as anything since Dapper, both on the LiveCD and installed on the hard disk. Just right-click on KNM, find your preferred connection and select it.

There were lots of things I liked about Gnome, but this may have won me over to KDE permanently. We'll see. Thanks anyways, Wieman.

---

### Post by ricardisimo on 2007-11-09
Oops! Accidental double-post. Sorry.

---

### Post by wieman01 on 2007-11-10
> **ricardisimo said:**
> I hope this post isn't unwelcome, because Wieman's HowTo did, in fact, help me get my wireless up and running. However, I thought that maybe Gina and some of the other posters here would like to know about this: I was having way too many problems with Ubuntu 7.10, so I decided to try Kubuntu Gutsy instead. I was _very_ pleasantly surprised. KNetworkManager worked as close to perfectly as anything since Dapper, both on the LiveCD and installed on the hard disk. Just right-click on KNM, find your preferred connection and select it.

There were lots of things I liked about Gnome, but this may have won me over to KDE permanently. We'll see. Thanks anyways, Wieman.
Actually I don't really believe it's a Kubuntu thing. Perhaps the current ISO is more up-to-date or repositories were after you had installed 7.10 first.

I believe this is due to the fact that they have replaced the drivers and put in the latest ones. Let's hope for the best then! Perhaps this thread is no more necessary soon.

---

### Post by Fruhwirth on 2007-11-10
> **wieman01 said:**
> Actually I don't really believe it's a Kubuntu thing. Perhaps the current ISO is more up-to-date or repositories were after you had installed 7.10 first.

I believe this is due to the fact that they have replaced the drivers and put in the latest ones. Let's hope for the best then! Perhaps this thread is no more necessary soon.

Are you saying that if I redownload Gutsy and reinstall it may be a different/work better than it did a month ago?  I wouldn't even be asking this question (I gave up on Gutsy and reinstalled Dapper due to [troubles]("http://ubuntuforums.org/showthread.php?p=3646231#post3646231")) except that when i reinstalled Dapper (the fourth time I've done so) there were network problems that did not occurr the first, second and third times I installed it.  In Dapper, basically, I can browse the internet fine, but no other network applications can connect at all. Except for having to install wlassisstant, I never had to tweak dapper in the past but now it's broken, too.

Should I redownload Gutsy and give it another try or am I just going to hate life again?

---

### Post by wieman01 on 2007-11-11
> **Fruhwirth said:**
> Should I redownload Gutsy and give it another try or am I just going to hate life again?
Well, quite a number of other posts made me believe so, but I cannot confirm it myself.

Best option for you would be to run the latest life CD. Perhaps it recognizes your card. Or you reinstall Gutsy, then update the system via Ethernet and see if the driver's been updated and is able to connect.

If you do so, do a full backup of your current system (see signature for tutorial). This way you can revert back to Dapper without having to install from scratch again.

---

### Post by Fruhwirth on 2007-11-11
I tried to install Kubuntu 7.10 for amd64. Strangely, the live CD worked just as Ricardismo said - I just used the built-in Knetworkmanager and it "just worked." Feeling hopeful, I did a fresh install of it.  How disheartening. It would not work after being installed, and tweaked, and carressed and all the rest.  I ran the live CD again, just to make sure I wasn't nuts, and lo and behold, it still worked perfectly on there.

The whole main point of a live cd is undermined if it functions so much better than operating system once it's installed.  sheesh. 

Feeling bold, I installed Mandriva and both wireless and DRI (my two most common sore spots) worked out of the box with that. But it's not 64-bit. 

So as I type this post, I'm downlaoding the 32-bit Gutsy Gibbon, hoping that my wireless and DRI work out of the box on that. I read once that 64-bit Ubuntu encodes roughly 30 percent faster than 32-bit. I do a lot of encoding, so I thought I should really try to get the 64-bit working, but that's beginning to look more and more like a pipe dream.

I'll let you know wieman01 how my wireless experience varies between GG64 and GG32. But for now Mandriva (which I do not prefer) is working perfectly.

---

### Post by dingansich on 2007-11-15
Haven't been in this thread for a while, but I seem to have most of my networking issues ironed out now, so I figured I'd add in what little I can:

A.) While the 64 bit driver for the WUS54Gv4 worked with ndiswrapper it seemed to destabilize the system (i.e. my computer would freeze)
B.) Replacing Network Manager with Wicd seemed to help with connectivity and stability
C.) Using the serial monkey driver for the RT2570 chipset, and ditching ndiswrapper, seems to have worked!  I found a howto at: [http://ubuntuforums.org/showthread.php?t=588045]("http://ubuntuforums.org/showthread.php?t=588045")

Hope this helps someone.

---

### Post by Chazall1 on 2007-11-15
I am having NO luck on getting my Wireless to Function any more, Before I added ndiswrapper, I had some functionality with picking up other non WEP Linksys connections, Now I do not even have a choice for any Wireless functions, Dell Dimension B110, Here are some outputs

ace@ace-desktop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

I added ndiswrapper and followed the How Too RT2500, etc wireless cards Gutsy in the forums.
When I add the drivers to the 'Blacklist in etc/modprobs, everything seems fine untill
I run ndiswrapper -l, my output is this,
ace@ace-desktop:~$ ndiswrapper -l
rt2500 : invalid driver!
rt2500pci : invalid driver!
ace@ace-desktop:~$ 
I have no Internet now, The NM does not give me an option for wireless!!
Here is my network interface file info as well

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 intel dhcp

Before ndiswrapper
Output   I have Gutsy on a Dell Dimension B110 Desktop using a Linksys Router with  WEP. I can not conect to my WEP. However I was connecting to the Internet using other Linksys networks in the neighborhood. This however has stoped working, I do not have ndiswrapper installed, would this make a difference???
Here are my outputs if I use wmaster0 as my interface:

ace@ace-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wmaster0
       version: 01
       serial: 00:12:17:8c:99:3c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci latency=64 module=rt2500pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 02
       serial: 00:13:20:d4:8e:45
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes

If I use wmaster0 in <interface>
ace@ace-desktop:~$ sudo ifconfig wmaster0 down
[sudo] password for ace:
ace@ace-desktop:~$ sudo dhclient -r wmaster0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Sending on   Socket/fallback
ace@ace-desktop:~$ sudo ifconfig wmaster0 up
ace@ace-desktop:~$ sudo iwconfig wmaster0 essid "lish1"
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wmaster0 ; Operation not supported.
ace@ace-desktop:~$ sudo iwconfig wmaster0 key 6063547000
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wmaster0 ; Operation not supported.
ace@ace-desktop:~$ sudo iwconfig wmaster0 mode Managed
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wmaster0 ; Operation not supported.
ace@ace-desktop:~$ sudo dhclient wmaster0
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Sending on   Socket/fallback
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

If I run wlan0, here is the output:

ace@ace-desktop:~$ sudo ifconfig wlan0 down
[sudo] password for ace:
ace@ace-desktop:~$ sudo dhclient -r wlan0
There is already a pid file /var/run/dhclient.pid with pid 6040
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:12:17:8c:99:3c
Sending on   LPF/wlan0/00:12:17:8c:99:3c
Sending on   Socket/fallback
ace@ace-desktop:~$ sudo ifconfig wlan0 up
ace@ace-desktop:~$ sudo iwconfig wlan0 essid "lish1"
ace@ace-desktop:~$ sudo iwconfig wlan0 key 6063547000
ace@ace-desktop:~$ sudo iwconfig wlan0 mode Managed
ace@ace-desktop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:12:17:8c:99:3c
Sending on   LPF/wlan0/00:12:17:8c:99:3c
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Can anyone assist me, I have no WIRELESS at this time

---

### Post by wieman01 on 2007-11-15
Hello Chazall1,

Are you 100% sure you have installed the right driver? Where did you find the driver and what chipset is your card?

---

### Post by Chazall1 on 2007-11-15
I went to the Linksys, and downloaded the latest driver fro my Wireless card, Linksys, WMP54G.

---

### Post by Chazall1 on 2007-11-15
Well # out what ndiswrapper configured in /etc/modules, and /etc/modprobe.d/blacklist. I set /etc/network/interfaces to

 auto lo
iface lo inet loopback

I have Wireless back, I have been using the internet for the past 3 hrs, on another router, not mine. I disabled my WEP about an hour ago, and the NM still showes a security key in the NM Wireless networks. I will watch and see what happens!!!!!

Thanks

---

### Post by ricardisimo on 2007-11-15
> **ricardisimo said:**
> I hope this post isn't unwelcome, because Wieman's HowTo did, in fact, help me get my wireless up and running. However, I thought that maybe Gina and some of the other posters here would like to know about this: I was having way too many problems with Ubuntu 7.10, so I decided to try Kubuntu Gutsy instead. I was _very_ pleasantly surprised. KNetworkManager worked as close to perfectly as anything since Dapper, both on the LiveCD and installed on the hard disk. Just right-click on KNM, find your preferred connection and select it.

There were lots of things I liked about Gnome, but this may have won me over to KDE permanently. We'll see. Thanks anyways, Wieman.

It just keeps getting more and more discouraging. True, KNM under the latest Gutsy Kubuntu worked immediately without any tweaking, but I still have the previous problem of connection speed. Right now I'm on the 7.04 Live CD again, and just to test my theory I'm downloading one of the Ubuntu CD images. It' s going at a decent clip, roughly 500 kbps.

Mind you, I haven't moved the wireless antenna one micron from where it was when I was running Gutsy a few minutes earlier. On 7.10 the absolute best I have been able to get is about 15-20 kbps.

So here's the question: Is there a way for me to downgrade NM or KNM to the Feisty, Edgy, or better yet, Dapper versions? Who knows... maybe Hoary's what I should be going after. This is so frustrating. I can't understand how the support can literally be getting worse with each release. Can someone explain that to me?

Thanks in advance.

---

### Post by wieman01 on 2007-11-16
> **ricardisimo said:**
> Is there a way for me to downgrade NM or KNM to the Feisty, Edgy, or better yet, Dapper versions? Who knows... maybe Hoary's what I should be going after. This is so frustrating. I can't understand how the support can literally be getting worse with each release. Can someone explain that to me?
You could downgrade by compiling older version from source, however, I believe it has nothing to do with NM but something else, perhaps the kernel. I would be surprised if replacing NM would help.

What driver to you use at the moment?

---

### Post by ricardisimo on 2007-11-16
I'm just running NM defaults in Feisty. No idea to what specific driver that translates. Here's some info:
lspci -vvv=
```
00:08.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
        Subsystem: Linksys WMP54G 2.0 PCI Adapter
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 21
        Region 0: Memory at dfffa000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [40] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
```

---

### Post by wieman01 on 2007-11-17
> **ricardisimo said:**
> I'm just running NM defaults in Feisty. No idea to what specific driver that translates. Here's some info:

And IPV6 is disabled?

---

### Post by ricardisimo on 2007-11-18
No. I read through the link you posted on disabling globally, and it seemed pretty clear to me by the end of it that doing so was either not a good idea or it was not a real solution. Besides... maybe I'm unclear on something, but wouldn't IPV6 be doing similar damage under Dapper, Edgy or Feisty as under Gutsy? Something else would seem to be the culprit.

---

### Post by deviance on 2007-11-19
I have followed this, but mine says:

device (13B1:000D) present (alternate driver: rt73usb)

Do I need to install the alternate as well as it is different?

---

### Post by wieman01 on 2007-11-19
> **deviance said:**
> I have followed this, but mine says:

device (13B1:000D) present (alternate driver: rt73usb)

Do I need to install the alternate as well as it is different?
Looks fine actually. Now continue to follow the tutorial... Can you connect to any network? If not please scan for networks and post the results:
> sudo iwlist scan

---

### Post by srkelley on 2007-11-22
I don't get the format for everything in bold. Can someone type in some examples of they should look like please?

    * Now unzip the driver archive you have just downloaded (e.g. in your home directory):
      Quote:
      unzip **<driver_archive>.exe**

    * Now find the right driver in the resulting folder & deploy it (folder should also contain other driver files i.e. .cat, .sys):
      Quote:
      sudo ndiswrapper -i **<your_ralink_driver>**.inf

    * Make sure it has installed correctly:
      Quote:
      ndiswrapper -l

    * The output should yield something like this:
      Quote:
      rt2500usb : driver installed
      device (13B1:000D) present (alternate driver: rt2500usb)

    * Last but not least open this file...
      Quote:
      sudo gedit /etc/network/interfaces

    * ...and add these 2 lines if they are not there yet [also try without adding them if Network Manager does not pick up the card & reboot]:
      Quote:
      auto wlan0
      iface wlan0 inet dhcp

---

### Post by wieman01 on 2007-11-22
> **srkelley said:**
> I don't get the format for everything in bold. Can someone type in some examples of they should look like please?

    * Now unzip the driver archive you have just downloaded (e.g. in your home directory):
      Quote:
      unzip **<driver_archive>.exe**

    * Now find the right driver in the resulting folder & deploy it (folder should also contain other driver files i.e. .cat, .sys):
      Quote:
      sudo ndiswrapper -i **<your_ralink_driver>**.inf

    * Make sure it has installed correctly:
      Quote:
      ndiswrapper -l

    * The output should yield something like this:
      Quote:
      rt2500usb : driver installed
      device (13B1:000D) present (alternate driver: rt2500usb)

    * Last but not least open this file...
      Quote:
      sudo gedit /etc/network/interfaces

    * ...and add these 2 lines if they are not there yet [also try without adding them if Network Manager does not pick up the card & reboot]:
      Quote:
      auto wlan0
      iface wlan0 inet dhcp
It basically says that you need to get hold of the latest driver file which usually comes in a ".exe" archive. So you need to download the archive, extract the files it contains and find a file that ends with ".inf". That's it.

What hardware have you got?

---

### Post by srkelley on 2007-11-22
I have a Nintendo USB adapter. i already have the driver and the executable, but I wanted to know how would I type it in. Would it be something like:

"sudo ndiswrapper -i srkelley/desktop/downloads/netu2g54.inf"

Or do I just type in the "sudo ndiswrapper -i netu2g54.inf"? I also need to know what extra bit goes before and after because I have typed in both and I don't know what it wants exactly.

---

### Post by wieman01 on 2007-11-22
That is right:
> sudo ndiswrapper -i /home/srkelley/desktop/downloads/netu2g54.inf
Then do...
> sudo ndiswrapper -l
...and post the output.

---

### Post by srkelley on 2007-11-22
shirondale@shirondale-desktop:~$ sudo ndiswrapper -i /home/srkelley/desktop/netu2g54.inf
[sudo] password for shirondale:
driver netu2g54 is already installed
shirondale@shirondale-desktop:~$ sudo ndiswrapper -l
netu2g54 : invalid driver!
rt25usbap : invalid driver!
shirondale@shirondale-desktop:~$ sudo ndiswrapper -l
netu2g54 : driver installed
shirondale@shirondale-desktop:~$ sudo ndiswrapper -i /home/srkelley/desktop/U2K2G54/Win2000/netu2g54.inf
driver netu2g54 is already installed
shirondale@shirondale-desktop:~$ 
shirondale@shirondale-desktop:~$ 

I found out that it was already installed, but that the driver was invalid (I tried the modded one first) then I used the original one and it installed, but I can't use the usb adapter as a wireless ap in any way. The pc isn't recogniizing the hardware as what should properly belong with the driver. is there anything I'd be able to do about that?

---

### Post by daengbo on 2007-11-22
I tried desperately to follow the tutorial for an RT61pci and an RT73usb, but I didn't have .sys and .inf files in my drivers. I tried for hours to download other drivers, but still had no luck there. The one driver set that did have the files failed under ndiswrapper.

Finally, I gave up, downloaded the daily build from seamonkey, and compiled. Both machines work fine, though the wireless drops about every 24 hours and has to be restarted on the rt73.

Much easier than ndiswrapper. I'd suggest the seamokey drivers.

On a side note, I'm really disappointed that the drivers are open source, are included in Gutsy, but don't seem to work well or at all. rtxxxx had worked flawlessly since Dapper for me. Meh.

---

### Post by wieman01 on 2007-11-23
> **srkelley said:**
> I found out that it was already installed, but that the driver was invalid (I tried the modded one first) then I used the original one and it installed, but I can't use the usb adapter as a wireless ap in any way. The pc isn't recogniizing the hardware as what should properly belong with the driver. is there anything I'd be able to do about that?
Looks good so far. Have you followed the other steps as well?

Please post the results of:
> sudo iwlist scan
And the contents of:
> sudo gedit /etc/network/interfaces

---

### Post by wieman01 on 2007-11-23
> **daengbo said:**
> I tried desperately to follow the tutorial for an RT61pci and an RT73usb, but I didn't have .sys and .inf files in my drivers. I tried for hours to download other drivers, but still had no luck there. The one driver set that did have the files failed under ndiswrapper.

Finally, I gave up, downloaded the daily build from seamonkey, and compiled. Both machines work fine, though the wireless drops about every 24 hours and has to be restarted on the rt73.

Much easier than ndiswrapper. I'd suggest the seamokey drivers.

On a side note, I'm really disappointed that the drivers are open source, are included in Gutsy, but don't seem to work well or at all. rtxxxx had worked flawlessly since Dapper for me. Meh.
Great. Thanks for letting us know. Does the driver also support WPA and WPA2?

---

### Post by daengbo on 2007-11-23
Wow, I'm an idiot.
[http://rt2x00.serialmonkey.com/](http://rt2x00.serialmonkey.com/)
Serialmonkey, not Seamonkey. Wow.

Anyway, WPA is said to work (I don't use it), but you must use iwpriv to set it up instead of wpa supplicant.

---

### Post by james_xxx on 2007-11-23
One thing that is still unclear to me in posts like #162, is whether or not the mods to /etc/network/interfaces will work for someone not using WPA. What if you are using WEP?

I am really frustrated with Gutsy (and *ubuntu, in general), though I have been a Kubuntu user for several years. I don't get how a wireless card will not work in one version of Ubuntu, will work the next, then again not work in the next. Is this just sloppiness? If not, is it that difficult to eventually correct this with new restricted modules, etc.?

Right now, I am able to connect to my wireless router with everything entered EXACTLY in /etc/network/interfaces with the rt2500 driver that comes with Gutsy. The problem I have is with trying to connect to other networks, say at a coffee shop , etc. Frequently I just cannot connect, no matter what I do. Even at home, my wireless still disconnects at random times. I did not have these problems in Feisty, and I wish I hadn't upgraded, especially considering that this is not the only significant issue I have experienced since upgrading.  Maybe none of this is the control of the *ubuntu devs, but I would be curious  to know. I originally had a broadcom wireless card in this laptop, but pulled it to install an rt2500, because they are (supposedly) well-supported in Linux. I guess I made a bad choice.

I presume that compiling the CVS driver like this will work until a kernel upgrade comes out... how does one remove this driver in order to compile it again in the event of a new kernel being installed?

Sorry if part of this post is just ranting.
Peace

---

### Post by wieman01 on 2007-11-24
> **james_xxx said:**
> One thing that is still unclear to me in posts like #162, is whether or not the mods to /etc/network/interfaces will work for someone not using WPA. What if you are using WEP?

I am really frustrated with Gutsy (and *ubuntu, in general), though I have been a Kubuntu user for several years. I don't get how a wireless card will not work in one version of Ubuntu, will work the next, then again not work in the next. Is this just sloppiness? If not, is it that difficult to eventually correct this with new restricted modules, etc.?

I presume that compiling the CVS driver like this will work until a kernel upgrade comes out... how does one remove this driver in order to compile it again in the event of a new kernel being installed?
Hey James, 

I share your frustration, believe me.

WEP is possible as well, no doubt. So be our guest to try and report back if you have issues connecting.

As for the CVS driver, it should work also after a kernel upgrade, but that's no guarantee. That said, however, The next Ubuntu release is just 5 months down the road, and I am sure they will fix it. So why don't you just wait and live with it until then?

---

### Post by ubulap on 2007-11-24
Just wanted to say thanks for this thread.

It allowed me to use the windows driver with ndiswrapper on a Gigabyte GN-WI05GS embedded laptop card (uses rt73 chipset) and combined with the information of your other WPA thread have it working with WPA connection (rt73usb wouldn't work with WPA)

---

### Post by ricardisimo on 2007-11-24
As I mentioned earlier, I'm back on Feisty because of a slow connection under Gutsy. However, I would love to give 7.10 a try again as soon as anyone can confirm that a sure-fire fix or significant update (kernel update, probably) has arrived. Please post here if you had my same problem and it is now fixed. And thanks again to Wieman for this article.

---

### Post by wieman01 on 2007-11-25
> **ricardisimo said:**
> As I mentioned earlier, I'm back on Feisty because of a slow connection under Gutsy. However, I would love to give 7.10 a try again as soon as anyone can confirm that a sure-fire fix or significant update (kernel update, probably) has arrived. Please post here if you had my same problem and it is now fixed. And thanks again to Wieman for this article.
No problem. As soon as I hear anything I'll post here and make mention of it in my tutorial.

---

### Post by devosion on 2007-11-26
Im receiving this error message from ndiswrapper after installing my driver and running ndiswrapper -l.

> rt2500usb: invalid driver

This is rather strange because i've used this driver for my linksys wireless adaptor before. I remembered that I didnt have the .sys file in the same directory when doing the installation this time so I decided i'd try removing the driver from ndiswrapper and got this message.

> couldn't delete /etc/ndiswrapper/rt2500usb: Inappropriate ioctl for device

Not quite sure what that meant so I went over my blacklist, which I recently filled with all the ralink drivers because I was unsure which one belonged to my chipset. And quite honestly forgot since my last installation. I noticed the rt2500usb and removed it and attempted the removal of the driver from ndiswrapper and was given the same error again.

Im not quite sure how to rectify this problem at this point, and would appreciate any help in either deleting the driver, or fixing the driver so it works.

---

### Post by wieman01 on 2007-11-26
> **devosion said:**
> Im receiving this error message from ndiswrapper after installing my driver and running ndiswrapper -l.



This is rather strange because i've used this driver for my linksys wireless adaptor before. I remembered that I didnt have the .sys file in the same directory when doing the installation this time so I decided i'd try removing the driver from ndiswrapper and got this message.



Not quite sure what that meant so I went over my blacklist, which I recently filled with all the ralink drivers because I was unsure which one belonged to my chipset. And quite honestly forgot since my last installation. I noticed the rt2500usb and removed it and attempted the removal of the driver from ndiswrapper and was given the same error again.

Im not quite sure how to rectify this problem at this point, and would appreciate any help in either deleting the driver, or fixing the driver so it works.
Are you on a 64-bit system and try to install a 32-bit driver by chance?

---

### Post by devosion on 2007-11-26
No thats not the case. This is the same driver i've used before and its worked just fine before on my architecture, which is incidentally 64bit capable but I run it 32bit anyways.

And my question and problem has pretty much flown out the window because I was tinkering away with ndiswrapper and completely uninstalled it. Then when I reinstalled it and attempted
 sudo modprobe ndiswrapper im getting a fatal message.

Perhaps if I didnt locate every single file and delete them all then I wouldnt be having this problem. :)

No biggie though because this is a brand new install of gutsy and I wont lose anything by reinstalling gutsy. Unless of course you know how I can get around the FATAL message im getting now.

> FATAL: Module ndiswrapper not found.

Even if you cant answer my question its ok. In any case im going to get some rest now.

---

### Post by wieman01 on 2007-11-26
> **devosion said:**
> No thats not the case. This is the same driver i've used before and its worked just fine before on my architecture, which is incidentally 64bit capable but I run it 32bit anyways.

And my question and problem has pretty much flown out the window because I was tinkering away with ndiswrapper and completely uninstalled it. Then when I reinstalled it and attempted
 sudo modprobe ndiswrapper im getting a fatal message.

Perhaps if I didnt locate every single file and delete them all then I wouldnt be having this problem. :)

No biggie though because this is a brand new install of gutsy and I wont lose anything by reinstalling gutsy. Unless of course you know how I can get around the FATAL message im getting now.



Even if you cant answer my question its ok. In any case im going to get some rest now.
The error message probably means that you have removed the 'ndiswrapper' package at some point. Why don't you reinstall it via Synaptic? Completely remove it if there are still files and dependencies and install it afterwards. That should fix your problem. That done start all over again. Would that fix it?

---

### Post by aldo_m on 2007-11-26
ok im getting a little problem here i tryed doing it with ndisgtk like i did the bc drivers but it says rt2500usb install hardware present:NO
o@ubuntu:~$  gedit /etc/network/interfaces
o@ubuntu:~$ sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
[sudo] password for aldo:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-common is already the newest version.
ndiswrapper-utils-1.9 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
o@ubuntu:~$ sudo depmod -a
o@ubuntu:~$ sudo modprobe ndiswrapper
 echo 'ndiswrapper' | sudo tee -a /etc/modules
ndiswrapper
o@ubuntu:~$ sudo ndiswrapper -m
module configuration already contains alias directive

aldo@ubuntu:~$ echo 'blacklist rt2500usb' | sudo tee -a /etc/modprobe.d/blacklist
blacklist rt2500usb
o@ubuntu:~$ sudo ndiswrapper -i rt2500usb.inf
driver rt2500usb is already installed
o@ubuntu:~$ ndiswrapper -l
rt2500usb : driver installed
so thene tryed it this way and not working this i s m hardware info

it dosnt have anything for a device butmyinternet works its using a linux default  driver  zd1211rw
say when i click my network bars at the topit says wireless networks {unknown usb device}

---

### Post by wieman01 on 2007-11-26
> **aldo_m said:**
> ok im getting a little problem here i tryed doing it with ndisgtk like i did the bc drivers but it says rt2500usb install hardware present:NO
o@ubuntu:~$  gedit /etc/network/interfaces
o@ubuntu:~$ sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
[sudo] password for aldo:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-common is already the newest version.
ndiswrapper-utils-1.9 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
o@ubuntu:~$ sudo depmod -a
o@ubuntu:~$ sudo modprobe ndiswrapper
 echo 'ndiswrapper' | sudo tee -a /etc/modules
ndiswrapper
o@ubuntu:~$ sudo ndiswrapper -m
module configuration already contains alias directive

aldo@ubuntu:~$ echo 'blacklist rt2500usb' | sudo tee -a /etc/modprobe.d/blacklist
blacklist rt2500usb
o@ubuntu:~$ sudo ndiswrapper -i rt2500usb.inf
driver rt2500usb is already installed
o@ubuntu:~$ ndiswrapper -l
rt2500usb : driver installed
so thene tryed it this way and not working this i s m hardware info

it dosnt have anything for a device butmyinternet works its using a linux default  driver  zd1211rw
say when i click my network bars at the topit says wireless networks {unknown usb device}
Alright... First of all what hardware/wireless device have you got?

Then do a scan please, and post the results:
> sudo iwlist scan

---

### Post by devosion on 2007-11-27
> **wieman01 said:**
> The error message probably means that you have removed the 'ndiswrapper' package at some point. Why don't you reinstall it via Synaptic? Completely remove it if there are still files and dependencies and install it afterwards. That should fix your problem. That done start all over again. Would that fix it?

Well the way I uninstalled it was first I went through and ran 'locate ndiswrapper', and deleted all the files that came up. This was probably the worst way of doing things, and manually extensive, but I did it anyways. After I completed this I tried to reinstall ndiswrapper, but aptitude still showed the package as installed. So I ran aptitude and set it for uninstall, which it did.

At this point I ran a reinstall from aptitude and everything seemed to work just fine. But when I tried to run 'ndiswrapper -l', to see if ndiswrapper would return a message, that is when I received the fatal message about the module.

Im not at my computer right now, but when I get home I will try a reinstall again and see what happens.

---

### Post by devosion on 2007-11-27
Fixed the problem. Just had to reinstall ndiswrapper manually. All that just cause I forgot to include the .sys file in the same directory as the .inf file.

---

### Post by wieman01 on 2007-11-27
> **devosion said:**
> Fixed the problem. Just had to reinstall ndiswrapper manually. All that just cause I forgot to include the .sys file in the same directory as the .inf file.
Yeah... :-) I did fall into the same trap once as well. And that's why I mention it... ;-)

---

### Post by kikos on 2007-11-27
When I first did a fresh install of Gutsy, wifi did not work. Next, I tried the serialmonkey drivers with wicd utility, but this only worked with WEP/WPA off.  So I reformatted the partition and reinstalled Gutsy.  Then, my D-Link GW-122 Rev. B1 (RT2570) usb dongle started working and it works with WPA too.

Only thing that changed between my first and second install is my router settings:  When I had the ssid hidden and mac filtering set to on, nothing worked.  Now with the ssid broadcast and mac filtering off, wireless works in Gutsy.

---

### Post by wieman01 on 2007-11-27
> **kikos said:**
> When I first did a fresh install of Gutsy, wifi did not work. Next, I tried the serialmonkey drivers with wicd utility, but this only worked with WEP/WPA off.  So I reformatted the partition and reinstalled Gutsy.  Then, my D-Link GW-122 Rev. B1 (RT2570) usb dongle started working and it works with WPA too.

Only thing that changed between my first and second install is my router settings:  When I had the ssid hidden and mac filtering set to on, nothing worked.  Now with the ssid broadcast and mac filtering off, wireless works in Gutsy.
They have replaced the drivers in the meantime... Good for you and a lot of other users. :-)

---

### Post by dysphasi on 2007-12-03
This method works great if I use roaming mode, but if I then go to manual configuration from network manager, enter all my details such as wep key, ip/gateway etc. etc.. it stops working. 

This is a problem for me because I like to autologin and don't want to have to enter my keyring password every time I log on.

Can anyone shed some light on how I might be able to set manual configuration and get this all up and running?

Thanks in advance
```

EDIT: Ok, got it working by:

1) Going to Synaptic Package Manager, then, Settings -> Repositories -> Third Party Software
2) Adding deb http://apt.wicd.net gutsy extras
3) Uninstalling network-manager and network-manager-gnome and installing wicd
4) Restarting, firing up wicd and entering my settings there, hey-presto it works :-D

Can anyone tell me what wicd does that network manager doesn't?.....Just out of curiosity

```

---

### Post by wieman01 on 2007-12-04
> **dysphasi said:**
> This method works great if I use roaming mode, but if I then go to manual configuration from network manager, enter all my details such as wep key, ip/gateway etc. etc.. it stops working. 

This is a problem for me because I like to autologin and don't want to have to enter my keyring password every time I log on.

Can anyone shed some light on how I might be able to set manual configuration and get this all up and running?

Thanks in advance
```

EDIT: Ok, got it working by:

1) Going to Synaptic Package Manager, then, Settings -> Repositories -> Third Party Software
2) Adding deb http://apt.wicd.net gutsy extras
3) Uninstalling network-manager and network-manager-gnome and installing wicd
4) Restarting, firing up wicd and entering my settings there, hey-presto it works :-D

Can anyone tell me what wicd does that network manager doesn't?.....Just out of curiosity

```
The thing is that NM can only do DHCP, so you cannot use static leases which - I know - is rediculous. But NM just can't do. Therefore the emergence of WiCD which allows you to use static IP addresses.

---

### Post by dysphasi on 2007-12-04
> **wieman01 said:**
> The thing is that NM can only do DHCP, so you cannot use static leases which - I know - is rediculous. But NM just can't do. Therefore the emergence of WiCD which allows you to use static IP addresses.

This being the case, how come I can use a static IP on my laptop with network manager?

---

### Post by wieman01 on 2007-12-04
> **dysphasi said:**
> This being the case, how come I can use a static IP on my laptop with network manager?
Can you? That would really surprise me as you would be the first one to achieve that. NM officially does not support static IP addresses. At least not when using wireless networking.

---

### Post by dysphasi on 2007-12-04
Perhaps I'm misunderstanding you here, but on my laptop, if I go to System>Administration>Network, and then into my wireless connection it lets me select 'Static IP address' in the configuration, an IP address, subnet mask and gateway address.

I then reboot and sure enough I've got this IP and can use the internet connection.

If I do the same on the desktop it won't connect when I use a static address unless I use Wicd.

---

### Post by wieman01 on 2007-12-04
> **dysphasi said:**
> Perhaps I'm misunderstanding you here, but on my laptop, if I go to System>Administration>Network, and then into my wireless connection it lets me select 'Static IP address' in the configuration, an IP address, subnet mask and gateway address.

I then reboot and sure enough I've got this IP and can use the internet connection.

If I do the same on the desktop it won't connect when I use a static address unless I use Wicd.
Got it... slight misunderstanding here. You use the standard networking applet, but not Network Manager... The convention is a bit confusing I have to admit. Network Manager lets you configure wireless networks with WPA security. The standard applet only knows WEP, so I assume you have a WEP secured network there, is that right?

The network applet is capable of static IP leases.

---

### Post by dysphasi on 2007-12-04
> **wieman01 said:**
> Got it... slight misunderstanding here. You use the standard networking applet, but not Network Manager... The convention is a bit confusing I have to admit. Network Manager lets you configure wireless networks with WPA security. The standard applet only knows WEP, so I assume you have a WEP secured network there, is that right?

The network applet is capable of static IP leases.

Ahhh...that sounds about right. Yes I do use WEP (got some old adapters that can't cope with anything else). 

Thank you for the explanation, any idea why I could only manage to connect with roaming using the applet?

---

### Post by wieman01 on 2007-12-04
> **dysphasi said:**
> Thank you for the explanation, any idea why I could only manage to connect with roaming using the applet?
Frankly I don't... Sorry, mate.

---

### Post by dysphasi on 2007-12-04
> **wieman01 said:**
> Frankly I don't... Sorry, mate.

Lol, figured as much ;) Does seem really odd, set it all up exactly as would have with any other computer, just doesn't work. Ah well, at least wicd is working really well. I like having the signal meter as well for the tray icon even when using a static ip, plus my ubuntu seems to be a lil faster loading everything up.

Thanks anyways!

---

### Post by cmirandamora on 2007-12-05
Thanks for the How-to; I´ve made my rt2500 chipset based card work with ndiswrapper and Windows driver with the router channel set on 13 (with the driver that comes with Gutsy it works out of the box but only between channels 1 to 11, and I needed to set 13 because it´s the only channel where I can watch fine the movies in my PC in my Kiis dp-600).

 The problem is the signal quality: it´s only 30%  and previously was more than 70%. ¿Do you know a way to improve it?

---

### Post by pckong on 2007-12-05
Hi,

When I try to install window driver with ndiswrapper, it said no such a file in the directory. i am sure the spelling is right. What would the problem be?

-----------------------------------------------------------------------------------------
pckong@pckong-laptop:~$ sudo ndiswrapper -i WG511v2.inf
installing wg511v2 ...
couldn't open WG511v2.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 181.
pckong@pckong-laptop:~$ 
----------------------------------------------------------------------------------------
:confused:

---

### Post by wieman01 on 2007-12-05
> **pckong said:**
> Hi,

When I try to install window driver with ndiswrapper, it said no such a file in the directory. i am sure the spelling is right. What would the problem be?

-----------------------------------------------------------------------------------------
pckong@pckong-laptop:~$ sudo ndiswrapper -i WG511v2.inf
installing wg511v2 ...
couldn't open WG511v2.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 181.
pckong@pckong-laptop:~$ 
----------------------------------------------------------------------------------------
:confused:
Well, what files are in the directory?
> cd <your directory>
> ls -l

---

### Post by wieman01 on 2007-12-05
> **cmirandamora said:**
> Thanks for the How-to; I´ve made my rt2500 chipset based card work with ndiswrapper and Windows driver with the router channel set on 13 (with the driver that comes with Gutsy it works out of the box but only between channels 1 to 11, and I needed to set 13 because it´s the only channel where I can watch fine the movies in my PC in my Kiis dp-600).

 The problem is the signal quality: it´s only 30%  and previously was more than 70%. ¿Do you know a way to improve it?
I don't know... Sorry, mate.

---

### Post by pckong on 2007-12-05
Hi Wieman,

I reinstall Ubuntu and follow the steps again, i got the LED in the network card blink! It works eventually.

But what happen before is quite weir, when i checked ndiswrapper installation with:
CODE:
ndiswrapper -l
OUTPUT:
ndiswrapper-1.50: invalid driver!
wg511v2: invalid driver!

Then I try to delete the driver and then reinstall it again,
CODE:
ndiswrapper -r wg511v2
OUTPUT:
couldn't delete /etc/ndiswrapper/wg511v2: Inappropriate ioctl for device

but thanks, finally it works!

---

### Post by sherrife on 2007-12-08
-----------------------------------------------------------------------------------------
pckong@pckong-laptop:~$ sudo ndiswrapper -i bcmwl5.inf
installing bcmwl5.inf...
couldn't open bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 181.
pckong@pckong-laptop:~$
----------------------------------------------------------------------------------------

I've got this problem as well, anyone have any ideas?  I'm a total newbie and it shows methinks :)  I've tried looking at line 181 in the .inf file but i have no idea how to interpret programming language.

---

### Post by Matteran on 2007-12-12
okay, so everything seems to be setup correctly.

with ndiswrapper -l I get:

```
rt61 : driver installed
        device (1814:0301) present (alternate driver: rt61pci)

```

and when i go into the network manager it shows the wireless connection in roaming mode. However, there doesn't seem to be anyway for me to get a list of access points or anything.

It's probably something simple, and may have already been answered, but I haven't been able to figure it out. Thanks!

[edit] NEVERMIND GUYS, I FIGURED IT OUT, THANKS!

---

### Post by sherrife on 2007-12-12
Could you explain it mate?

I'm still struggling to detect my wireless network

---

### Post by wieman01 on 2007-12-12
> **sherrife said:**
> Could you explain it mate?

I'm still struggling to detect my wireless network
I am sorry, I must have overlooked your post.

Actually, I have no clue what is going on. Do you find your adapter on the list of compatible devices found here:

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/")

---

### Post by sherrife on 2007-12-12
Yea, I've got it installed and everything, shows up on iwconfig and ifconfig, but just doesn't detect any wireless networks.

---

### Post by wieman01 on 2007-12-13
> **sherrife said:**
> Yea, I've got it installed and everything, shows up on iwconfig and ifconfig, but just doesn't detect any wireless networks.
And you did blacklist the native driver/module?

---

### Post by prplhazed on 2007-12-13
Hello all
I installed ubuntu for the first time on my new computer build and everything was great except for wireless
after reading and googling and reading and googling, this seems to be the thread that is most helpful for my problem

I have a rt2500usb device, and i tried to do the command line stuff that this thread says to but it didnt work
before i could see wireless networks but not connect
now ubuntu doesnt seem to recognize that i have wireless and only offers wired networking

any help would be greatly apreciated, ubuntu's pretty great other than this (its kinda big though)

---

### Post by wieman01 on 2007-12-14
> **prplhazed said:**
> Hello all
I installed ubuntu for the first time on my new computer build and everything was great except for wireless
after reading and googling and reading and googling, this seems to be the thread that is most helpful for my problem

I have a rt2500usb device, and i tried to do the command line stuff that this thread says to but it didnt work
before i could see wireless networks but not connect
now ubuntu doesnt seem to recognize that i have wireless and only offers wired networking

any help would be greatly apreciated, ubuntu's pretty great other than this (its kinda big though)
Ok, have you done all steps in the tutorial?

Please post the results of:
> sudo ndiswrapper -l
> sudo iwlist scan
> sudo lshw -C network

---

### Post by prplhazed on 2007-12-14
sudo ndiswrapper -l
rt2500usb : invalid driver

sudo iwlist scan
lo             Interface doesn't support scanning.

eth0        Interface doesn't support scanning.

sudo lshw -C network
for this last one i scrolled rapidly through a couple of things including "DMI" "PCI syfs"

As i don't have anything important on here yet, I'm leaning towards just whiping it and starting over

---

### Post by wieman01 on 2007-12-14
> **prplhazed said:**
> sudo ndiswrapper -l
rt2500usb : invalid driver
You have probably installed the wrong driver. If you are on 64-bit then you might have wrongly chosen a 32-bit driver, could that be? The current one is by all means the wrong one.

Where have you got it from?

---

### Post by prplhazed on 2007-12-14
I got it from the linksys website. I also have the driver cd, and while I don't know if it's outdated, I'm assuming the website has the newest one.

---

### Post by wieman01 on 2007-12-14
> **prplhazed said:**
> I got it from the linksys website. I also have the driver cd, and while I don't know if it's outdated, I'm assuming the website has the newest one.
Are you running the 64-bit version of Ubuntu?

---

### Post by prplhazed on 2007-12-14
Yes, I think so.
I can't remember for sure, is there a command to check?

---

### Post by hakova on 2007-12-15
Hi there,

I am trying to get this work so far with no success. Upon fresh installation of Kubuntu 7.10, rt2x00 modules were built and added into the kernel automatically. However, there was this error message in dmesg and the adapter did not function:

[   19.938183] ieee80211_init: failed to initialize WME (err=-17)
[   19.977417] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[   19.977480] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_put
[   19.977533] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_get
[   19.977623] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_register
[   20.000346] wmaster0: Selected rate control algorithm 'simple'

Then I tried to go with the ndiswrapper option described here, but when it comes to the "sudo ndiswrapper -i <your_ralink_driver>.inf" part, I get the following errors:

sudo ndiswrapper -i rt61.inf
installing rt61 ...
couldn't find models section "Ralink" -
installation may be incomplete
couldn't find models section "Gigabyte" -
installation may be incomplete
couldn't find models section "Edimax" -
installation may be incomplete
couldn't find models section "Sitecom" -
installation may be incomplete
couldn't find models section "Delta" -
installation may be incomplete
couldn't find models section "Hawking" -
installation may be incomplete
couldn't find models section "Conceptronic" -
installation may be incomplete
couldn't find models section "Billionton" -
installation may be incomplete
couldn't find models section "ASUS" -
installation may be incomplete
couldn't find models section "ZINWELL" -
installation may be incomplete
couldn't find models section "AMIT" -
installation may be incomplete
couldn't find models section "CASTLENET" -
installation may be incomplete
couldn't find models section "ACCTON" -
installation may be incomplete
couldn't find models section "Surecom" -
installation may be incomplete
couldn't find models section "Belkin" -
installation may be incomplete
couldn't find models section "VTech" -
installation may be incomplete
couldn't find models section "Siemens" -
installation may be incomplete
hako@kaymak:~$ ndiswrapper -l
rt61 : invalid driver!

There are other drivers in the CD that came with the wireless adapter (PCI) but this one matches to the model of the card I purchased (Edimax EW-7128G).

The output of sudo lshw -C network is as follows:

*-network
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:13:20:2d:37:db
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 firmware=5751-v3.23a latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 1
       bus info: pci@0000:04:01.0
       logical name: wmaster0
       version: 00
       serial: 00:0e:2e:e5:1b:b3
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11g

I am sorry if this is a longer-than-intended message. Any input will be much appreciated.

---

### Post by wieman01 on 2007-12-15
> **prplhazed said:**
> Yes, I think so.
I can't remember for sure, is there a command to check?
Have you downloaded and installed the 64-bit version? I cannot tell you how to check from here...

---

### Post by Erik. on 2007-12-15
Hi wieman,
you got an personal message from me.
i am trying all the day to fix my wireless internet card.
I have the linksys wrt54g card verson 2
i downloaded the driver from the linux site and i did all i could do that the tutorial says.

i go no problems whit installing.
I configured it manual but my problem is cannot not connect to the internet.
My wirreless router says i am active in the network but when i start firefox i can not get on any page i want.
Could someone help me please

---

### Post by wieman01 on 2007-12-16
> **Erik. said:**
> Hi wieman,
you got an personal message from me.
i am trying all the day to fix my wireless internet card.
I have the linksys wrt54g card verson 2
i downloaded the driver from the linux site and i did all i could do that the tutorial says.

i go no problems whit installing.
I configured it manual but my problem is cannot not connect to the internet.
My wirreless router says i am active in the network but when i start firefox i can not get on any page i want.
Could someone help me please
What steps have you done?

Please also post the results of:
> sudo iwlist scan
> sudo lshw -C network
> sudo ifdown -v wlan0
> sudo ifup -v wlan0
> sudo gedit /etc/network/interfaces

---

### Post by wieman01 on 2007-12-16
**@Erik:**

I think you are already on line as you have suggested in your email. Please post:
> route
> ping 209.85.129.99
The latter is Google.us.

There seems to be a problem with your DNS setting... Disabling IPV6 might help in that case.

---

### Post by Jhongy on 2007-12-17
Just wanted to add my experience with an RT2561/RT61-based card (D-Link AirPlus DWL-G520+ A H/W Ver C1).

It worked out of the box with Gutsy with the included driver (rt61pci). However, the connection would drop after about 10 - 15 minutes.

So I tried downloading the latest SerialMonkey legacy tarballs, and compiled and installed them according to the directions. Again, the wireless worked -- however this time, the computer would randomly crash with no entries in dmesg to say what wa causing it. I initially assumed it was overheating, and wasted a fair bit of time. Very annoying since this is a server.

Finally, I resorted to NDISwrapper with the RaLink RT2561/RT61 windows driver downloaded from RaLink's site. Third time is obviously a charm -- no crashes, and relatively smooth wifi.

I just use WEP, so if you want WPA your mileage may vary. But for anyone with an RT61-based card with stability problems in Gutsy -- go for the NDISwrapper option first!!

John

---

### Post by wieman01 on 2007-12-18
> **Jhongy said:**
> I just use WEP, so if you want WPA your mileage may vary. 
No quite. If the Windows driver can do WPA, then there is no problem at all. It even works with Network Manager. :-)

Don't use WEP by the way. It is highly flawed, very insecure, and can be cracked in a matter of minutes.

---

### Post by jocheem67 on 2007-12-29
I used the serialmonkey snapshot to configure my rt61, no probs here...so I disagree that ndiswrapper should be the first option to get the rt61chipset online.

I guess a lot has to do with setting up your /etc/network/interfaces file. That' s the hard part. It allows you to use wpa though.

[PHP]auto wlan0
iface wlan0 inet dhcp

pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid "Jochem" 
pre-up iwconfig wlan0 mode Managed
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set EncrypType=TKIP
pre-up iwpriv wlan0 set WPAPSK="you key here" 
pre-up ifconfig wlan0 up
[/PHP]

---

### Post by wieman01 on 2007-12-29
> **jocheem67 said:**
> I used the serialmonkey snapshot to configure my rt61, no probs here...so I disagree that ndiswrapper should be the first option to get the rt61chipset online.

I guess a lot has to do with setting up your /etc/network/interfaces file. That' s the hard part. It allows you to use wpa though.

[PHP]auto wlan0
iface wlan0 inet dhcp

pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid "Jochem" 
pre-up iwconfig wlan0 mode Managed
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set EncrypType=TKIP
pre-up iwpriv wlan0 set WPAPSK="you key here" 
pre-up ifconfig wlan0 up
[/PHP]
Now use Network Manager and try to connect! You still disagree?

---

### Post by jocheem67 on 2007-12-29
Removed network-manager as it does not like the rt61..using the rutilt utility, just for monitoring....

---

### Post by wieman01 on 2007-12-30
> **jocheem67 said:**
> Removed network-manager as it does not like the rt61..using the rutilt utility, just for monitoring....
Yeah, that's exactly the point of the thread. A lot of people prefer using Network Manager (for whatever reason). Anyway, good to hear the other driver works for you.

---

### Post by Thumper! on 2008-01-06
sorry i really didn't understand any of it...i'm just dumb though

i need help

i'v got a d-link WUA 2340 wireless USB adaptor and i don't have a clue how to get it working

i'v pluged my laptop into a ethnet cable for now but i really need to get it up and running, help desperatily needed

Thanks, Tom

---

### Post by wieman01 on 2008-01-07
> **Thumper! said:**
> sorry i really didn't understand any of it...i'm just dumb though

i need help

i'v got a d-link WUA 2340 wireless USB adaptor and i don't have a clue how to get it working

i'v pluged my laptop into a ethnet cable for now but i really need to get it up and running, help desperatily needed

Thanks, Tom
Hey Tom, 

Please open a terminal and issue these commands, then post the results (copy & paste):
> sudo iwlist scan
> sudo lshw -C network
> sudo cat /etc/network/interfaces
Have you tried using Network Manager for wireless?

---

### Post by PriceChild on 2008-01-07
Just curious, what's wrong with using module-assistant to compile the rt2500-source package for example?

---

### Post by wieman01 on 2008-01-07
> **PriceChild said:**
> Just curious, what's wrong with using module-assistant to compile the rt2500-source package for example?
Nothing I guess. Just a different approach. But you will have to compile it yourself from source, as the current one (I am talking about Gutsy) is defective. See this thread for more (interesting poll):

[http://ubuntuforums.org/showthread.php?t=594857]("http://ubuntuforums.org/showthread.php?t=594857")

I find using "ndiswrapper" easier then compiling stuff from source. What's your experience with it? Also curious. :-)

---

### Post by PriceChild on 2008-01-07
I've always used module-assistant to grab, build and install rt2500, and always been perfect for me :)

---

### Post by wieman01 on 2008-01-07
> **PriceChild said:**
> I've always used module-assistant to grab, build and install rt2500, and always been perfect for me :)
Ok... Could you post a link or something so that I could look into the matter? Would it work also for other Ralink based chipsets? Perhaps we gain some more insight here. I don't know why Ralink based drivers have to be such a hassle.

---

### Post by PriceChild on 2008-01-07
I don't have any link... its literally
```
sudo apt-get install module-assistant
sudo module-assistant auto-install rt2500
```

---

### Post by wieman01 on 2008-01-07
> **PriceChild said:**
> I don't have any link... its literally
```
sudo apt-get install module-assistant
sudo module-assistant auto-install rt2500
```
Thanks, mate. I will check that out. First time I hear of it...

Does the driver work well with Network Manager?

---

### Post by PriceChild on 2008-01-07
It seems to work pretty perfectly. I've heard rumours though that wpa can be hard/impossible but haven't tried myself.

---

### Post by wieman01 on 2008-01-08
> **PriceChild said:**
> It seems to work pretty perfectly. I've heard rumours though that wpa can be hard/impossible but haven't tried myself.
Do you still use WEP then? I wouldn't unless you have no say in the matter (i.e. your network's security). Anyway, thanks for letting me know. I will definitely try this out soon.

---

### Post by PriceChild on 2008-01-08
> **wieman01 said:**
> Do you still use WEP then? I wouldn't unless you have no say in the matter (i.e. your network's security). Anyway, thanks for letting me know. I will definitely try this out soon.The conditions I'm in mean encryption just isn't an option. It degrades the signal just that little bit too far. I have to just use MAC address filtering at that location.

---

### Post by wieman01 on 2008-01-08
> **PriceChild said:**
> The conditions I'm in mean encryption just isn't an option. It degrades the signal just that little bit too far. I have to just use MAC address filtering at that location.
That's too bad. Anyway, just wanted to let you know. WEP can be easily cracked and spoofing MAC addresses is a piece of cake provided that you run Linux. ;-) So your network is pretty vunerable, but of course there are other factors that you need to take into account as you have highlighted. 

Good discussion, mate. See you then.

---

### Post by PriceChild on 2008-01-08
That is very true.

However the network is on top of a big hill, a fair distance from any other buildings. Its hard enough getting a decent connection inside the building so someone stealing the connection would have to be on the grounds and very visible. There's nothing interesting on the inside of the network either except for a very very poor internet connection.

---

### Post by wieman01 on 2008-01-08
> **PriceChild said:**
> However the network is on top of a big hill, a fair distance from any other buildings. 
Haha... That is probably the best defense option there is. :-)

---

### Post by curldragon on 2008-01-10
hi wieman01, First sorry for my poor English :) i am a newer linux user.
i follow your tutorial step by step, But, finaly, i reboot my computer, my wlan0 doesn't work correct.
my lsusb info is:
> lsusb
Bus 006 Device 003: ID 0204:6025  
Bus 006 Device 002: ID 13b1:0011 Linksys WUSB54GP v4.0 802.11g Adapter

and my /etc/network/interface file include > 
auto wlan0
iface wlan0 inet dhcp


> 
root@curldragon:/home/curl# ndiswrapper -l
rt2500usb : driver installed
        device (13B1:0011) present (alternate driver: rt2500usb)


> 
root@curldragon:/home/curl# lsmod |grep ndis
ndiswrapper           185240  0 
usbcore               138632  6 ndiswrapper,usb_storage,libusual,ehci_hcd,ohci_hcd


>  iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:06:25:DE:97:E9
                    ESSID:"curldragon"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:79/100  Signal level:-45 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK


all seems correct, but  ifconfig info is
> 
wlan0     Link encap:Ethernet  HWaddr 00:14:BF:7D:1B:D9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0:ava Link encap:Ethernet  HWaddr 00:14:BF:7D:1B:D9  
          inet addr:169.254.173.211  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1


then i input iwconfig , get this:

> 
root@curldragon:/home/curl# iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Auto  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


so, i input > 
iwconfig wlan0 essid curldragon channel 6
but nothing changed.

What's wrong with me?
Hope your help very much! and thank u very much!

---

### Post by wieman01 on 2008-01-11
> **curldragon said:**
> hi wieman01, First sorry for my poor English :) i am a newer linux user.

People need to stop apologizing for their English, in particular when it's as good as yours... :-)

The scan confirms that your card is indeed working. Please post:
> sudo cat /etc/network/interfaces
What is not working? Do you use Network Manager for wireless networking? 

Everything seems set in fact. How do you plan to connect to your wireless network from here? Which application would you like to use?

---

### Post by ricardisimo on 2008-01-11
Two months ago I filed [this bug report]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/163020") in Launchpad regarding RT2500 support gradually deteriorating since Dapper. For those two months I've been meaning to link to it in this thread so that the developers can get more info from more people... and it's just been one brain-fart after another. Anyhow, there it is. Sorry for the delay. 

If your situation is at all similar to mine, please post to the bug report with all of your specs. Thanks.

---

### Post by curldragon on 2008-01-12
Thanks wieman01 .
I use "ndisgtk"  set my card , and connect to my wireless router bye WPA2, it work correct now! So thanks for your tutorial !

My second question is : How to install the same driver in a Custom kernel? like 2.6.23.1-curl . 
The file ndiswrapper.ko  is maked into the old kernel modules directory,when i  copy it to my new kernel modules directory, then do "modprobe ndiswrapper", system call me "FATAL: Module ndiswrapper not found." 
so what's the reason?

Nice to meet u Sir. :)
BTW: i like your logo!   The same as my ID, :)

---

### Post by wieman01 on 2008-01-12
> **curldragon said:**
> Thanks wieman01 .
I use "ndisgtk"  set my card , and connect to my wireless router bye WPA2, it work correct now! So thanks for your tutorial !

My second question is : How to install the same driver in a Custom kernel? like 2.6.23.1-curl . 
The file ndiswrapper.ko  is maked into the old kernel modules directory,when i  copy it to my new kernel modules directory, then do "modprobe ndiswrapper", system call me "FATAL: Module ndiswrapper not found." 
so what's the reason?

Nice to meet u Sir. :)
BTW: i like your logo!   The same as my ID, :)
Ahh... somebody knows Chinese. :-) Nice to meet you too!

You would have to compile 'ndiswrapper' once again with a new 'custom' kernel. I think you cannot reuse 'ndiswrapper.ko', that'd be too easy. :-) Does that make sense?

---

### Post by wieman01 on 2008-01-12
> **ricardisimo said:**
> Two months ago I filed [this bug report]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/163020") in Launchpad regarding RT2500 support gradually deteriorating since Dapper. For those two months I've been meaning to link to it in this thread so that the developers can get more info from more people... and it's just been one brain-fart after another. Anyhow, there it is. Sorry for the delay. 

If your situation is at all similar to mine, please post to the bug report with all of your specs. Thanks.
Thanks for the link, ricardisimo. Would you like me to include the link on the first page (in my tutorial)? It would make sense in my opinion.

---

### Post by phoenix81000 on 2008-01-12
Hallo, 

sorry to say iam a lazy person. I live in a student dorm, in Scotland. And we just got Internet and a very very sexy LAN. Now my friend has his somewhat old desktop here which we have ravaged with XP so we can have an additional work station (read CounterStrike, WOW, IRC-serv, Fileserv) However the PCI Rt2500 sweex card does not want to pick up any networks. It used to, but now it has keeled over and decided to stop working. So either its broken or windows XP has decided to screw me over, there are loads of viruses floating around here. So, as a semi experienced ubuntu linux user i though we should put ubuntu on, see if that would work.. LiveCD 7.04 does not automatically enable wireless functionality. 

So here is my question. Assuming the card isn't broken, can i test the card through a live session? Because if that would work we would have a VERY nice CUPS/FileServ/Game-Server which would just totally Rock. Imagen sharing 3 USB external HD's across the network... Ah how wonderful that would be!

Btw, the PCI card is the version with the long wire and buttplug antenna.
Cheers!

---

### Post by wieman01 on 2008-01-12
> **phoenix81000 said:**
> So here is my question. Assuming the card isn't broken, can i test the card through a live session?
In theory, yes, that should work, however, Ralink drivers are known to behave somewhat erratically if you know what I mean. So you might be OK when running the Live CD but I cannot guarantee it works after a full installation. All I can say is "Good luck" for now... but you know where you can post if you have problems connecting. We'll able to help you out.

---

### Post by phoenix81000 on 2008-01-12
Well i installed ubuntu on the 2nd hard drive.. no problems. It even found a Adhoc network! YAH so its working.. however it didnt find the normall Public network which i need. Once i started doing your howto it all went to.. well it stopped working. So i reformated and hoping it will work now. So u recommend install the wifi through your method? and whats the difrence between default and your howto?

Cheers

---

### Post by wieman01 on 2008-01-12
> **phoenix81000 said:**
> Well i installed ubuntu on the 2nd hard drive.. no problems. It even found a Adhoc network! YAH so its working.. however it didnt find the normall Public network which i need. Once i started doing your howto it all went to.. well it stopped working. So i reformated and hoping it will work now. So u recommend install the wifi through your method? and whats the difrence between default and your howto?

Cheers
No, go for the default setup, but use this tool for wireless networking:

[http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

It reportedly does a much better job, so I reckon you could give it a whirl as well. Don't change anything else.

---

### Post by phoenix81000 on 2008-01-12
I installed that program, had to unistall network-manager.. still only picking up that adhoc network. I really need to connect to that Public network.. i check the signal strength with my PSP around the wireless reciever.. it ranges from 55-65%. 

Any suggestions?

---

### Post by lH)4~mK0e on 2008-01-12
Does this work with the live cd?

---

### Post by wieman01 on 2008-01-13
> **phoenix81000 said:**
> I installed that program, had to unistall network-manager.. still only picking up that adhoc network. I really need to connect to that Public network.. i check the signal strength with my PSP around the wireless reciever.. it ranges from 55-65%. 

Any suggestions?
Have you been able to connect to any wireless network so far? Just to confirm it works.

---

### Post by wieman01 on 2008-01-13
> **miwarlock002 said:**
> Does this work with the live cd?
No, it doesn't.

---

### Post by Titonus on 2008-01-13
I get all the way to installing the drivers, and I get,

daniel@daniel-desktop:~$ sudo ndiswrapper -i rt2500.inf
installing rt2500 ...
couldn't open rt2500.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 181.
daniel@daniel-desktop:~$ sudo ndiswrapper -i rt2500.inf
driver rt2500 is already installed
daniel@daniel-desktop:~$ 

what am I doing wrong? I have the driver .inf file here on my desktop.:confused:

---

### Post by Titonus on 2008-01-13
Ok, I rebooted after "uninstalling" the driver, installed the driver when booted, and got, 

daniel@daniel-desktop:~$ ndiswrapper -l
rt2500 : driver installed
daniel@daniel-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"PCX5000"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:02:2D:55:74:B0   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

daniel@daniel-desktop:~$ 


So, now it sees the network is there, doesn't give me any signal strength, and won't connect.

---

### Post by wieman01 on 2008-01-13
> **Titonus said:**
> Ok, I rebooted after "uninstalling" the driver, installed the driver when booted, and got, 

daniel@daniel-desktop:~$ ndiswrapper -l
rt2500 : driver installed
daniel@daniel-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"PCX5000"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:02:2D:55:74:B0   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

daniel@daniel-desktop:~$ 


So, now it sees the network is there, doesn't give me any signal strength, and won't connect.
What results does a scan yield:
> sudo iwlist scan
And:
> sudo lshw -C network

---

### Post by Titonus on 2008-01-13
daniel@daniel-desktop:~$ sudo iwlist scan
[sudo] password for daniel:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:02:2D:55:74:B0
                    ESSID:"PCX5000"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz
                    Signal level=-52 dBm  
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:tsf=0000006ceac8317b
daniel@daniel-desktop:~$ sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 3
       bus info: pci@0000:01:03.0
       logical name: wmaster0
       version: 00
       serial: 00:18:f8:b0:5a:8e
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=32 module=rt61pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: 82801G (ICH7 Family) LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 01
       serial: 00:1a:92:eb:85:3e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=full firmware=N/A ip=192.168.100.88 latency=32 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s

---

### Post by wieman01 on 2008-01-13
**@Titonus:**

You card seems to work, at least there are scan results. But you are still using the old Ralink driver. Is that what you want?

---

### Post by Titonus on 2008-01-13
I want to be able to use it. Haha. Are there new drivers for my card?

---

### Post by ricardisimo on 2008-01-13
> **wieman01 said:**
> Thanks for the link, ricardisimo. Would you like me to include the link on the first page (in my tutorial)? It would make sense in my opinion.

Please feel free, and thanks again for everything.

---

### Post by wieman01 on 2008-01-13
> **Titonus said:**
> I want to be able to use it. Haha. Are there new drivers for my card?
Well, you could replace them using this very HOWTO. Or install WICD which might do a better job in regard to Ralink... That's what I have heard.

---

### Post by wieman01 on 2008-01-13
> **ricardisimo said:**
> Please feel free, and thanks again for everything.
Thanks, great. I have done so.

---

### Post by Titonus on 2008-01-13
I was following the guide, and I already removed network-manager and installed WICD. This is where I'm at after all of that. I have an old windows 1386 on a CD, which is where I got the drivers. I don't have a windows box to install the driver onto to get a new INF file though.

---

### Post by wieman01 on 2008-01-14
> **Titonus said:**
> I was following the guide, and I already removed network-manager and installed WICD. This is where I'm at after all of that. I have an old windows 1386 on a CD, which is where I got the drivers. I don't have a windows box to install the driver onto to get a new INF file though.
Anywhere eles you could get the drivers from? The vendor's web site for instance? Thing is that you won't have WPA support unless you somehow replace the driver. 

This is another option:

[http://ubuntuforums.org/showthread.php?t=584657&highlight=ralink+serialmonkey]("http://ubuntuforums.org/showthread.php?t=584657&highlight=ralink+serialmonkey")

---

### Post by Titonus on 2008-01-15
Any idea what this means?

daniel@daniel-desktop:~$ sudo /etc/init.d/networking stop
[sudo] password for daniel:
 * Deconfiguring network interfaces...                                          /etc/network/interfaces:14: duplicate interface
ifdown: couldn't read interfaces file "/etc/network/interfaces"
                                                                         [fail]


I think I messed up the interfaces file somehow. Is there a way to reset it, or just delete what evers in it and I don't know.

---

### Post by wieman01 on 2008-01-16
> **Titonus said:**
> Any idea what this means?

daniel@daniel-desktop:~$ sudo /etc/init.d/networking stop
[sudo] password for daniel:
 * Deconfiguring network interfaces...                                          /etc/network/interfaces:14: duplicate interface
ifdown: couldn't read interfaces file "/etc/network/interfaces"
                                                                         [fail]


I think I messed up the interfaces file somehow. Is there a way to reset it, or just delete what evers in it and I don't know.
You could start by posting the contents:
> sudo gedit /etc/network/interfaces
Don't worry, not much of a deal. We can fix this easily.

---

### Post by Titonus on 2008-01-16
here it is.

auto lo
iface lo inet loopback



iface eth0 inet dhcp

auto eth0

iface wlan0 inet dhcp
wireless-essid PCX5000


iface wlan0 inet dhcp 
        pre-up ifconfig wlan0 up
        pre-up ifconfig wlan0 down
        pre-up ifconfig wlan0 up
        pre-up ifconfig wlan0 down
        pre-up iwconfig wlan0 essid "PCX5000"
        pre-up iwconfig wlan0 mode Managed
        pre-up iwpriv wlan0 set AuthMode=WPAPSK
        pre-up iwpriv wlan0 set EncrypType=TKIP
        pre-up iwpriv wlan0 set WPAPSK=""
        pre-up ifconfig wlan0 up

auto wlan0

---

### Post by wieman01 on 2008-01-16
Try this instead:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
pre-up ifconfig wlan0 down
pre-up ifconfig wlan0 up
pre-up ifconfig wlan0 down
pre-up iwconfig wlan0 essid "PCX5000"
pre-up iwconfig wlan0 mode Managed
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set EncrypType=TKIP
pre-up iwpriv wlan0 set WPAPSK=""
pre-up ifconfig wlan0 up

---

### Post by Titonus on 2008-01-16
ok, that fixed the interfaces file. Networks stop and start returns this now.


daniel@daniel-desktop:~$ sudo /etc/init.d/networking stop
[sudo] password for daniel:
 * Deconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 5333
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:1a:92:eb:85:3e
Sending on   LPF/eth0/00:1a:92:eb:85:3e
Sending on   Socket/fallback
                                                                         [ OK ]
daniel@daniel-desktop:~$ sudo /etc/init.d/networking start
 * Configuring network interfaces...                                            There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:1a:92:eb:85:3e
Sending on   LPF/eth0/00:1a:92:eb:85:3e
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.100.254
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.100.254
bound to 192.168.100.88 -- renewal in 97758 seconds.
Invalid command : set
Failed to bring up wlan0.
                                                                         [ OK ]

Meaning the wireless isn't connecting.

---

### Post by wieman01 on 2008-01-17
> **Titonus said:**
> ok, that fixed the interfaces file. Networks stop and start returns this now.


daniel@daniel-desktop:~$ sudo /etc/init.d/networking stop
[sudo] password for daniel:
 * Deconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 5333
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:1a:92:eb:85:3e
Sending on   LPF/eth0/00:1a:92:eb:85:3e
Sending on   Socket/fallback
                                                                         [ OK ]
daniel@daniel-desktop:~$ sudo /etc/init.d/networking start
 * Configuring network interfaces...                                            There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:1a:92:eb:85:3e
Sending on   LPF/eth0/00:1a:92:eb:85:3e
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.100.254
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.100.254
bound to 192.168.100.88 -- renewal in 97758 seconds.
Invalid command : set
Failed to bring up wlan0.
                                                                         [ OK ]

Meaning the wireless isn't connecting.
Looks promising though. You have received a lease which essentially means you were able to connect at least once.

Please try this and restart the network:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
pre-up ifconfig wlan0 down
pre-up ifconfig wlan0 up
pre-up ifconfig wlan0 down
pre-up iwconfig wlan0 essid "PCX5000"
pre-up iwconfig wlan0 mode Managed
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set EncrypType=TKIP
pre-up iwpriv wlan0 set WPAPSK=""
I have removed the last line. Let's see what the error message looks like now.

---

### Post by Titonus on 2008-01-17
after changing the interfaces file again, 

daniel@daniel-desktop:~$ sudo /etc/init.d/networking stop * Deconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 10142
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:1a:92:eb:85:3e
Sending on   LPF/eth0/00:1a:92:eb:85:3e
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.100.254 port 67
                                                                         [ OK ]
daniel@daniel-desktop:~$ sudo /etc/init.d/networking start
 * Configuring network interfaces...                                            There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:1a:92:eb:85:3e
Sending on   LPF/eth0/00:1a:92:eb:85:3e
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPOFFER from 192.168.100.254
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.100.254
bound to 192.168.100.88 -- renewal in 118482 seconds.
Invalid command : set
Failed to bring up wlan0.
                                                                         [ OK ]
daniel@daniel-desktop:~$ 


Still no wireless.

---

### Post by wieman01 on 2008-01-18
**@Titonus:**

After restarting the network do you get a response when you 'ping' your router?
> ping 192.168.100.88
> route

---

### Post by Titonus on 2008-01-18
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.100.0   *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.100.254 0.0.0.0         UG    100    0        0 eth0


All it shows is the hardwire, not the wireless. I have successful pings on the router though.

---

### Post by wieman01 on 2008-01-18
> **Titonus said:**
> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.100.0   *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.100.254 0.0.0.0         UG    100    0        0 eth0


All it shows is the hardwire, not the wireless. I have successful pings on the router though.
Looks good actually. Can you browse the Internet? What if you try to access 192.168.100.254 using Firefox? Do you get the start page of your router?

---

### Post by Titonus on 2008-01-19
It timed out. There's no return for the local IP in firefox. :( This almost makes me want to go back to windows xp pro. I can buzz threw it like it's nothing. Ubuntu is pretty confusing.

---

### Post by wieman01 on 2008-01-19
> **Titonus said:**
> It timed out. There's no return for the local IP in firefox. :( This almost makes me want to go back to windows xp pro. I can buzz threw it like it's nothing. Ubuntu is pretty confusing.
You might have to disable IPV6. Please see post #1 of this thread and follow it. Then restart the PC and open Firefox.

[http://ubuntuforums.org/showthread.php?t=6841&highlight=ipv6]("http://ubuntuforums.org/showthread.php?t=6841&highlight=ipv6")

---

### Post by Titonus on 2008-01-19
I'm not sure what exactly that was suppose to do, but it didn't.

---

### Post by RostokMcSpoons on 2008-01-25
Hi, 

Following my troubles with the SerialMonkey rt73 drivers I'm trying your guide, and it has worked... partially.

As was the case the other drivers, I can get the damned thing to work up until the point where I reboot and cross my fingers that it'll just.. work.  And it doesn't.

I think my problems now are:

1) blacklisting doesn't seem to work - I still get rt2500 drivers showing up against usbcore
2) it doesn't seem to remember my settings in Network Manager properly, and so defaults to it switched off (which may be related to...)
3) I can't persuade it use the right ESSID - even with sudo iwconfig wlan0 essid "SpeedTouchxxx" when I follow that with sudo iwconfig wlan0 it says ESSID is "off"


I really am close to throwing the towel in on this... only geeky stubborness remains, but it's almost been ground away by the remorseless crapness of an operating system with a user interface that doesn't work properly and an obtuse command line interface which seems to be the only way to do anything useful.  Allegedly  :/

---

### Post by killerpens on 2008-01-25
Worked for me. Thanks a lot. More power to you!

---

### Post by toarlach on 2008-01-25
I'm running Gutsy (7.10) and running a rt2570 USB stick. I think I have everything installed fine. I just don't know how to connect to my wireless network with it.

I tried the menu on the networking icon, my wireless network does not show up anymore (ever since I installed the driver--but it didn't connect to it before the driver was installed anyway). 

I also tried iwconfig wlan0 essid "mynetworkname" and still no luck. 

Any suggestions people?

---

### Post by RostokMcSpoons on 2008-01-25
I'm going to zap my Ubuntu installation and try OpenSUSE.  Maybe that can work with a simple wireless dongle... somethings gotta :(

I shall report back if it works, as I'm sure there are people out there ready to give up on Linux altogether if they can't get wifi to work.

edit: the gods are against me.. the SUSE install failed at the end, perhaps because I couldn't configure my 'network devices' during the install process.  So I'm now doing a full install of Feisty to see if that works.  
I'm going to stop swearing at Bill Gates and his minions... no-one elses software is any better :(


edit:  nope, Feisty didn't work (kept locking up), so I downloaded another version of SUSE (KDE 32bit), and that's a nightmare too...

---

### Post by wieman01 on 2008-01-26
> **toarlach said:**
> I'm running Gutsy (7.10) and running a rt2570 USB stick. I think I have everything installed fine. I just don't know how to connect to my wireless network with it.

I tried the menu on the networking icon, my wireless network does not show up anymore (ever since I installed the driver--but it didn't connect to it before the driver was installed anyway). 

I also tried iwconfig wlan0 essid "mynetworkname" and still no luck. 

Any suggestions people?
What driver did you blacklist and what hardware have you got?

Please post:
> sudo iwlist scan

---

### Post by toarlach on 2008-01-26
> **wieman01 said:**
> What driver did you blacklist and what hardware have you got?

Please post:
This is what happens when I do a sudo iwlist scan...

> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:00:C5:F8:13:68
                    ESSID:"Sweely"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz
                    Signal level=-76 dBm  
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:tsf=000000000b6afaac


The "Sweely" is the name of my wireless network, but anything can be put there like "asdf", and nothing still happens when I put "Sweely" in there. 

Also, this is what happens when I do a /etc/init.d/networking (all of this being done from root)...
> 
root@csweely-desktop:/home/csweely# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                            There is already a pid file /var/run/dhclient.wmaster0.pid with pid 5607
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Sending on   Socket/fallback
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.wlan0.pid with pid 5695
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:d0:41:a1:ae:fa
Sending on   LPF/wlan0/00:d0:41:a1:ae:fa
Sending on   Socket/fallback
SIOCSIFFLAGS: Operation not supported
There is already a pid file /var/run/dhclient.wmaster0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
SIOCSIFFLAGS: Operation not supported
SIOCSIFFLAGS: Operation not supported
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Sending on   Socket/fallback
receive_packet failed on wmaster0: Network is down
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 13
send_packet: Network is down
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 11
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
RTNETLINK answers: Network is down
run-parts: /etc/network/if-up.d/avahi-autoipd exited with return code 2
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:d0:41:a1:ae:fa
Sending on   LPF/wlan0/00:d0:41:a1:ae:fa
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                                                                           [ OK ]

I'm really trying to get this working. Any help is appreciated.

---

### Post by wieman01 on 2008-01-27
**@toarlach:**

It looks to me as if you have not blacklisted the right driver. Please let me know what driver you have put on the blacklist.

Also, please post:
> sudo lshw -C network
> sudo cat /etc/network/interfaces

---

### Post by toarlach on 2008-01-27
The driver I put on the blacklist is rt2570.
, which is what it is.

Here is the output from the queries listed above...

> csweely@csweely-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 190 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 00
       serial: 00:15:f2:b4:82:51
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.2 duplex=half latency=0 link=no module=sis190 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:d0:41:a1:ae:fa
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

And here is the list from /etc/network/interfaces...
> csweely@csweely-desktop:~$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp

auto wmaster0
iface wmaster0 inet dhcp

Hopefully that provides another clue of why my rt2570 stick will not work. Ugh. Any help is appreciated. Thanks.

---

### Post by wieman01 on 2008-01-27
**Toarlach:**

Please blacklist this one:
> rt2570usb
The restart the PC and do:
> sudo iwlist scan

---

### Post by toarlach on 2008-01-27
> **wieman01 said:**
> **Toarlach:**

Please blacklist this one:

The restart the PC and do:
Okay, I blacklisted the rt2570 usb driver, and looks to me like it still does the same thing...

This is from the 'sudo iwlist scan'
csweely@csweely-desktop:~$ sudo iwlist scan
[sudo] password for csweely:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.
> 
wlan0     Scan completed :
          Cell 01 - Address: 00:00:C5:F8:13:68
                    ESSID:"Sweely"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz
                    Signal level=-77 dBm  
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:tsf=000000165a8197f9

I also did a /etc/init.d/networking restart to see if I could jump started, but it did this...
> 
csweely@csweely-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                          There is already a pid file /var/run/dhclient.wmaster0.pid with pid 5387
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Sending on   Socket/fallback
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.wlan0.pid with pid 5452
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:d0:41:a1:ae:fa
Sending on   LPF/wlan0/00:d0:41:a1:ae:fa
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:d0:41:a1:ae:fa
Sending on   LPF/wlan0/00:d0:41:a1:ae:fa
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
There is already a pid file /var/run/dhclient.wmaster0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Sending on   Socket/fallback
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                                         [ OK ]

Anything else I could try?

---

### Post by wieman01 on 2008-01-27
We have not blacklisted the right driver... What device have you got? Could you post a link to the vendor's website or something like that?

---

### Post by toarlach on 2008-01-27
> **wieman01 said:**
> We have not blacklisted the right driver... What device have you got? Could you post a link to the vendor's website or something like that?
There's not that many specs on it anywhere. It's a Netopia 3D Reach USB stick. I'll try and find photos. It comes with Bellsouth Fastaccess internet. This is the link to it below...

[http://www.netopia.com/equipment/pdf/3D_R_Wireless_Adapt_DS.pdf](http://www.netopia.com/equipment/pdf/3D_R_Wireless_Adapt_DS.pdf)

Under Linux (atleast Fiesty), it worked fine using rt2570 drivers...until I upgraded.

---

### Post by wieman01 on 2008-01-28
> **toarlach said:**
> There's not that many specs on it anywhere. It's a Netopia 3D Reach USB stick. I'll try and find photos. It comes with Bellsouth Fastaccess internet. This is the link to it below...

[http://www.netopia.com/equipment/pdf/3D_R_Wireless_Adapt_DS.pdf](http://www.netopia.com/equipment/pdf/3D_R_Wireless_Adapt_DS.pdf)

Under Linux (atleast Fiesty), it worked fine using rt2570 drivers...until I upgraded.
What happens when you do:
> sudo ndiswrapper -l
And what drivers are blacklisted right now?

Is there any sort of LED that is lit and indicating the device is connected?

---

### Post by toarlach on 2008-01-28
> **wieman01 said:**
> What happens when you do:

And what drivers are blacklisted right now?

Is there any sort of LED that is lit and indicating the device is connected?
I blacklisted rt2570 and also the one you told me to blacklist rt2570usb. 

Yes, the green LED is lit up, but the yellow activity light never flickers. With the green LED lit, that probably means the driver is installed and that Linux recognizes it, but I'm guessing it just can't connect to a wireless network for some reason.

---

### Post by wieman01 on 2008-01-28
> **toarlach said:**
> I blacklisted rt2570 and also the one you told me to blacklist rt2570usb. 

Yes, the green LED is lit up, but the yellow activity light never flickers. With the green LED lit, that probably means the driver is installed and that Linux recognizes it, but I'm guessing it just can't connect to a wireless network for some reason.
Please unplug the device, then connect again and run:
> sudo lsusb
And:
> sudo ndiswrapper -l

---

### Post by toarlach on 2008-01-28
> **wieman01 said:**
> Please unplug the device, then connect again and run:

And:
Okay, I unplugged and plugged it back in again. Here is the output of what you told me below...

> root@csweely-desktop:/home/csweely# ndiswrapper -l
rt2500 : driver installed
root@csweely-desktop:/home/csweely# lsusb
Bus 004 Device 005: ID 0781:5150 SanDisk Corp. SDCZ2 Cruzer Mini Flash Drive (thin)
Bus 004 Device 002: ID 148f:2570 Ralink Technology, Corp. 802.11g WiFi
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 045e:00e5 Microsoft Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 03f0:4911 Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000  
root@csweely-desktop:/home/csweely# 

It is the Ralink device (hence the 2570), and has worked with the rt drivers before when it was under Fiesty. I have no clue why it is not working under Gutsy.

---

### Post by wieman01 on 2008-01-29
> **toarlach said:**
> Okay, I unplugged and plugged it back in again. Here is the output of what you told me below...

It is the Ralink device (hence the 2570), and has worked with the rt drivers before when it was under Fiesty. I have no clue why it is not working under Gutsy.
Please don't forget to post the output of this one:
> sudo ndiswrapper -l
That should tell us more.

---

### Post by toarlach on 2008-01-29
> **wieman01 said:**
> Please don't forget to post the output of this one:

That should tell us more.
I did that here under root...

> root@csweely-desktop:/home/csweely# ndiswrapper -l
rt2500 : driver installed

Any ideas of why it is still not working?

---

### Post by wieman01 on 2008-01-29
> **toarlach said:**
> I did that here under root...

Any ideas of why it is still not working?
Sorry, I had missed it.

Another question, not certain if I have asked it before, but are you on Ubuntu 64-bit?

---

### Post by toarlach on 2008-01-29
> **wieman01 said:**
> Sorry, I had missed it.

Another question, not certain if I have asked it before, but are you on Ubuntu 64-bit?
Nope, I'm running Ubuntu 32bit -- Gutsy. 

Anything else I can do to try and get it to work?

---

### Post by cheetah_thompson on 2008-01-30
wusb54g wireless networking 

--------------------------------------------------------------------------------

I am a newbie trying to configure my Ubuntu "Gutsy" PC for home wireless networking with a Linksys WUSB54g card. I've followed this tutorial, but something is still not working, and I wasn't getting any response in the new users forum. I have previously had this Ubuntu PC working through a wired connection directly to my Zonet switch/wireless router, so I know the router is fine and there is nothing inherently wrong with my Ubuntu installation.

Four steps so far:

1. I know my wireless network is working as I can connect from Windows XP. And I am just using 'default' as the name without any encryption. And both lights are on on the Linksys wireless receiver.

2. I have installed ndiswrapper and ndisgtk from the Ubuntu Gutsy CD using sudo apt-get.

3. I have copied the drivers directory from my Linksys WUSB54g CD, and installed rt2500usb.inf driver (there are drivers for version 1, 2 and 4 on the CD, so I chose the latter).

4. I did 'sudo depmod -a'.

Its taken me a lot of head scratching to get this far, the wireless network still does not work, so what should I try next?

Below are the results of running different commands at the command prompt. Its encouraging that ndiswrapper believes rt2500usb is installed, and that iwconfig brings up some information under wlan0. The Link Signal level looks like a small number, but right next to the Ubuntu PC this Windows laptop is picking up the wireless network with Strength: Very Good. Do I need to edit my /etc/network/interfaces file and if so, how should it look?

Under the Network Settings GUI, wlan0 Properties dialog box has Network Name (ESSID) = default, Password type = WPA Personal, Network password = (blank, there is no password), Configuration = Automatic Configuration (DHCP). IP address, subnet mask and Gateway address are all set to blank. My router ip address is 192.168.1.1, but I don't have this set anywhere on the Ubuntu PC. I have changed the Password type to WEP key hexadecimal but it makes no difference.

When I try to browse using Firefox it just sits there with status "Looking up (url)" and fails after a minute or two.

Here are the results of those commands:

(i) ndiswrapper -l
rt2500usb : driver installed
device (13B1:000D) present (alternate driver: rt2500usb)
wusb54g : driver installed

(ii) iwconfig:
wlan0 IEEE 802.11g ESSID:"default" 
Mode:Managed Frequency:2.437 GHz Access Point: 08:10:74:0F:26:BC 
Retry min limit:7 RTS thrff Fragment thr=2346 B 
Link Signal level=-49 dBm 
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0


(iii) more /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp



auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

iface wlan0 inet dhcp
wireless-essid default

auto wlan0

auto eth0

---

### Post by wieman01 on 2008-01-30
> **toarlach said:**
> Nope, I'm running Ubuntu 32bit -- Gutsy. 

Anything else I can do to try and get it to work?
Last thing you can try is this thread:

[http://ubuntuforums.org/showthread.php?t=584657&highlight=serialmonkey+howto]("http://ubuntuforums.org/showthread.php?t=584657&highlight=serialmonkey+howto")

It is for the 'rt2500' but I am sure it applies to the 'rt2570' as well.

Plus... User Kevdog is always very helpful. Perhaps he has an idea. Just contact him by PM.

---

### Post by wieman01 on 2008-01-30
> **cheetah_thompson said:**
> wusb54g wireless networking 

--------------------------------------------------------------------------------

I am a newbie trying to configure my Ubuntu "Gutsy" PC for home wireless networking with a Linksys WUSB54g card. I've followed this tutorial, but something is still not working, and I wasn't getting any response in the new users forum. I have previously had this Ubuntu PC working through a wired connection directly to my Zonet switch/wireless router, so I know the router is fine and there is nothing inherently wrong with my Ubuntu installation.

Four steps so far:

1. I know my wireless network is working as I can connect from Windows XP. And I am just using 'default' as the name without any encryption. And both lights are on on the Linksys wireless receiver.

2. I have installed ndiswrapper and ndisgtk from the Ubuntu Gutsy CD using sudo apt-get.

3. I have copied the drivers directory from my Linksys WUSB54g CD, and installed rt2500usb.inf driver (there are drivers for version 1, 2 and 4 on the CD, so I chose the latter).

4. I did 'sudo depmod -a'.

Its taken me a lot of head scratching to get this far, the wireless network still does not work, so what should I try next?

Below are the results of running different commands at the command prompt. Its encouraging that ndiswrapper believes rt2500usb is installed, and that iwconfig brings up some information under wlan0. The Link Signal level looks like a small number, but right next to the Ubuntu PC this Windows laptop is picking up the wireless network with Strength: Very Good. Do I need to edit my /etc/network/interfaces file and if so, how should it look?

Under the Network Settings GUI, wlan0 Properties dialog box has Network Name (ESSID) = default, Password type = WPA Personal, Network password = (blank, there is no password), Configuration = Automatic Configuration (DHCP). IP address, subnet mask and Gateway address are all set to blank. My router ip address is 192.168.1.1, but I don't have this set anywhere on the Ubuntu PC. I have changed the Password type to WEP key hexadecimal but it makes no difference.

When I try to browse using Firefox it just sits there with status "Looking up (url)" and fails after a minute or two.

Here are the results of those commands:

(i) ndiswrapper -l
rt2500usb : driver installed
device (13B1:000D) present (alternate driver: rt2500usb)
wusb54g : driver installed

(ii) iwconfig:
wlan0 IEEE 802.11g ESSID:"default" 
Mode:Managed Frequency:2.437 GHz Access Point: 08:10:74:0F:26:BC 
Retry min limit:7 RTS thrff Fragment thr=2346 B 
Link Signal level=-49 dBm 
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0


Hello, 

It does look promising indeed. Please also post the output of:
> sudo iwlist scan
> sudo lshw -C network
What driver have you blacklisted by the way? 'rt2500usb'?

---

### Post by wieman01 on 2008-01-30
By the way... if all this does not help, Kevdog might be able to help out:

[http://ubuntuforums.org/showthread.php?t=574501]("http://ubuntuforums.org/showthread.php?t=574501")

---

### Post by kissson on 2008-01-30
my alternate method to deal with rt2500 using serialmonkey not ndis
may help some users in some manner
[http://ubuntuforums.org/showthread.php?t=671217](http://ubuntuforums.org/showthread.php?t=671217)

---

### Post by cheetah_thompson on 2008-01-31
OK, here is the output of those other 2 commands. I haven't blacklisted anything (not sure what blacklisting is).

:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results



:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:70:a9:99:95
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by wieman01 on 2008-01-31
> **cheetah_thompson said:**
> OK, here is the output of those other 2 commands. I haven't blacklisted anything (not sure what blacklisting is).

:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results



:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:70:a9:99:95
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
Your card has not been recognized. What driver have you blacklisted?

And please post:
> sudo ndiswrapper -l
Are you on Ubuntu 64-bit?

---

### Post by cheetah_thompson on 2008-01-31
I tried this [http://ubuntuforums.org/showthread.php?t=574501]("http://ubuntuforums.org/showthread.php?t=574501"), but not sure what my HEX_KEY is. Is that something I'm supposed to get from my DSL modem or wireless router? Anyway I can get that value using WindowsXP (which is connected to the wireless network fine)?

---

### Post by cheetah_thompson on 2008-01-31
Response of sudo ndiswrapper -l:

rt2500usb: driver installed
        device (13B1:000D) present (alternate driver: rt2500usb)
wusb54g: driver installed

I have a 32-bit version of Gutsy (purchased on CD a few weeks ago) but my processor is an AMD-64 bit.

---

### Post by wieman01 on 2008-01-31
> **cheetah_thompson said:**
> Response of sudo ndiswrapper -l:

rt2500usb: driver installed
        device (13B1:000D) present (alternate driver: rt2500usb)
wusb54g: driver installed

I have a 32-bit version of Gutsy (purchased on CD a few weeks ago) but my processor is an AMD-64 bit.
OK, as long as you are running the 32-bit version we are fine.

Did you blacklist 'rt2500usb'? What exact brand and model is the adapter?

---

### Post by cheetah_thompson on 2008-01-31
Nothing was blacklisted. I thought rt2500usb was the driver I wanted? Or should I be using wusb54g (both were on the driver CD for Windows). The wireless adapter is a Linksys WUSB54G - its an external USB wireless adapter. My wireless network is simply called "DEFAULT" and there is no password (not really worried about someone using my connection here, since the nearest house is hundreds of metres away).

---

### Post by wieman01 on 2008-01-31
> **cheetah_thompson said:**
> Nothing was blacklisted. I thought rt2500usb was the driver I wanted? Or should I be using wusb54g (both were on the driver CD for Windows). The wireless adapter is a Linksys WUSB54G - its an external USB wireless adapter. My wireless network is simply called "DEFAULT" and there is no password (not really worried about someone using my connection here, since the nearest house is hundreds of metres away).
Well, this thread is rather specific, so unless you follow this tutorial (first post), I won't be able to help you much. The idea is that you install the Windows drivers which I have highlighted in the first post.

---

### Post by cheetah_thompson on 2008-01-31
A bit confused - I have followed your first post to the letter. rt2500usb was the driver on my CD, and your first post said to install that under ndiswrapper. Since I'm out of my depth, I typed the commands in exactly the sequence you specified. The only step I did not do was blacklist that driver. Last night I did try blacklisting it & rebooting but same result: no wireless connection. 

Here is the linksys link about my WUSB54G adapter:
[http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859843775&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4377540888B30&displaypage=download#versiondetail]("http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859843775&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4377540888B30&displaypage=download#versiondetail")

---

### Post by cheetah_thompson on 2008-01-31
I see the link goes to a menu where the version is selected. Mine is version 4 of WUSB54G.

---

### Post by wieman01 on 2008-01-31
> **cheetah_thompson said:**
> I see the link goes to a menu where the version is selected. Mine is version 4 of WUSB54G.
I have got the same device working under Gutsy, so bear with me (also v4).

What driver did you blacklist then? It must 'rt2570usb'... sorry for the typo. My mistake.
> rt2570usb
Then reboot and type:
> sudo iwlist scan
> sudo lshw -C network

---

### Post by cheetah_thompson on 2008-02-02
Thanks for continuing to help. So here is the deal: I blacklisted all the drivers you mentioned in your first post (page 1 of this thread), apart from rt2500usb.inf, since that's the one from my wireless adapter CD. So yes, I blacklisted rt2570usb too. Rebooted the PC. The result appears to be a backwards step. Now with iwconfig, my access point is "Not Associated", Signal Level 0.
The results of sudo iwlist scan & sudo lshw -C network are the same as I show in my last post on page 35 of this thread.
Huge fan of Linux, not of Windows. Maybe I need to reconsider though - took minutes to get the wireless adapter to work with Windows.

---

### Post by wieman01 on 2008-02-02
> **cheetah_thompson said:**
> Thanks for continuing to help. So here is the deal: I blacklisted all the drivers you mentioned in your first post (page 1 of this thread), apart from rt2500usb.inf, since that's the one from my wireless adapter CD. So yes, I blacklisted rt2570usb too. Rebooted the PC. The result appears to be a backwards step. Now with iwconfig, my access point is "Not Associated", Signal Level 0.
The results of sudo iwlist scan & sudo lshw -C network are the same as I show in my last post on page 35 of this thread.
Huge fan of Linux, not of Windows. Maybe I need to reconsider though - took minutes to get the wireless adapter to work with Windows.
After blacklisting the 'rt2570usb' driver (which I think is the right one), what does this yield:
> sudo iwlist scan
> sudo ndiswrapper -l
> sudo lshw -C network

---

### Post by ricardisimo on 2008-02-05
I'm still checking in regularly, and I'm curious to see if anyone can confirm or deny whether the recent kernel update has had any effect. Also, a quick reminder to everyone to add your 2¢ to [this bug report]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/163020") that Wieman was kind enough to pin to his first post. If the developers don't hear from you, they won't know what we want. Thanks again to everyone, especially Wiedude.

P.S. - I've heard something about a "Thanks" button for threads, but I have yet to see one. Where would I find it?

---

### Post by wieman01 on 2008-02-05
> **ricardisimo said:**
> P.S. - I've heard something about a "Thanks" button for threads, but I have yet to see one. Where would I find it?
There is none, this thread is too old and was written before the feature was introduced.

As for the kernel update, I doubt it will have any impact. The kernel versions 2.6.24 and 2.6.25 will come with a number of improvements with regard to Ralink and the other usual suspects. But don't expect any changes prior to Hardy. :-(

---

### Post by ricardisimo on 2008-02-08
I received an email yesterday from Launchpad that my bug (and almost every other RaLink bug) is a duplicate of [Bug 134660]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/134660"). The opening statement there suggests that a fix is extremely easy: Just find the right driver at serialmonkey and implement it on Ubuntu.
[LIST=1]
[*]Is it that easy?
[*]Should I, or could I download/install whatever I need before upgrading to 7.10 (and thereby losing my connection again)?
[/LIST]
Thanks again.

---

### Post by wieman01 on 2008-02-08
> **ricardisimo said:**
> I received an email yesterday from Launchpad that my bug (and almost every other RaLink bug) is a duplicate of [Bug 134660]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/134660"). The opening statement there suggests that a fix is extremely easy: Just find the right driver at serialmonkey and implement it on Ubuntu.
[LIST=1]
[*]Is it that easy?
[*]Should I, or could I download/install whatever I need before upgrading to 7.10 (and thereby losing my connection again)?
[/LIST]
Thanks again.
I have also heard that Serialmonkey's drivers have become considerably better, however, I don't want to mess around with them, because their WPA support used to be somewhat limited. Plus they don't really support the 'wext' interface, hence you cannot use it in connection with NM.

But give it go... We could try it out together perhaps. I am very curious now... in particular with regard to WPA2 support.

---

### Post by ricardisimo on 2008-02-08
It doesn't look like it's going to happen today, unfortunately. I'm having difficulty finding a "sweet spot" with my antenna. Connection's already low, so upgrading to Gutsy will make it that much more difficult to work. Thanks for the offer of help, though. I'll take it!

---

### Post by ricardisimo on 2008-02-09
Uggh... This doesn't look like it's going to be easy. I've never successfully followed any Linux instructions longer than five or six steps (and that's just copying and pasting), and now this:
> Installation instructions for the rt2500 Module

======================================================================
Build Instructions:
====================
For 2.4 or 2.6 series kernel:
a. $tar -xvzf rt2500-x.x.x.tar.gz
    go to "./rt2500-x.x.x/Module" directory.

b. $make                # compile driver source code

c. $make install        # (as root) installs kernel module driver

_________
NOTES:

* Driver alias

        "make install" places the alias for the rt2500 driver in
        /etc/modules.conf (2.4 kernels) or /etc/modprobe.d/ralink
        (2.6 kernels).

* Read end of file for FedoraCore3 specific information.


======================================================================
To BUILD UTILITY
====================

a.  go to the "./Utility" directory

b.  run 'qmake -o Makefile raconfig2500.pro'
    If qmake command is not found in your system, you can download
    the QT tool 'qt-x11-free-3.2.1' or later at
    [http://www.trolltech.com/](http://www.trolltech.com/)

    (qmake comes with RedHat 7.3 or later QT Package)

c.  run 'make" to compile the utility source code.

d.  After all, an execution file would be generated "RaConfig2500"
    run "RaConfig2500" to config the driver as you want

======================================================================
INVOCATION
====================
Load the driver:

        $modprobe rt2500 [ifname=<name>] [debug=<mask>]

        <name> is the name of the device and defaults to "ra%d".
        If more than one adapter is installed, specify <name> in
        sprintf format (e.g. "wlan%d" - without the quotes).
        Successive devices will then be named ra0, ra1, etc., or
        (using the example) wlan0, wlan1, etc. If there are already
        wired ethernet devices named eth0 and eth1, then specifying
        <name> as "eth%d" gives the adapter the name "eth2".

        <mask> is a decimal or hex number. See TESTING file. Ignored
        if driver compiled without debug support.

Start it up:

        $ifup ra0        # If using Debian

======================================================================
CONFIGURATION:
====================
RT2500 driver can be configured via following interfaces,
i.e. (i)"iwconfig" command, (ii)"iwpriv" command, (iii) configuration
     file, (iv) RaConfig2500

i)  iwconfig comes with kernel.
ii) iwpriv usage, please refer to file "iwpriv_usage.txt" for details.
iii)copy configuration file "RT2500STA.dat" to
    /etc/Wireless/RT2500STA/RT2500STA.dat.
    Please refer to syntax descriptions below for details.
iv) RT2500 provides API : RaConfig2500, please go to directory
    ./Utility and refer to how-to-compile.txt


Configuration File : RT2500STA.dat

# Copy this file to /etc/Wireless/RT2500STA/RT2500STA.dat
# This file is a binary file and will be read on loading rt2500.o
# module.
#
# Use "vi -b RT2500STA.dat" to modify settings according to your need.
#
# 1.) set NetworkType to "Adhoc" for using Adhoc-mode, otherwise
#     using as Infrastructure-mode.
# 2.) set Channel to "0" for auto-select on Infrastructure mode.
# 3.) set SSID for connecting to your Accss-point.
# 4.) AuthMode can be "OPEN", "SHARED", "AUTO", "WPAPSK", "WPANONE".
# 5.) EncrypType can be "NONE", "WEP", "TKIP", "AES".
#
# When editing the file, make sure the filesize does not exceed 1024
# Bytes (1kb).
# Anything stored beyond the 1024 bte limit will be ignored by the
# driver.
#
[Default]
CountryRegion=0
WirelessMode=0
SSID=AP350
NetworkType=Infra
Channel=0
AuthMode=OPEN
EncrypType=NONE
DefaultKeyID=1
Key1=0123456789
Key2=
Key3=
Key4=
WPANONE=abcdefghijklmnopqrstuvwxyz
WPAPSK=abcdefghijklmnopqrstuvwxyz
TXBurst=0
TurboRate=0
BGProtection=0
ShortSlot=0
TxPreamble=2
TxRate=0
RTSThreshold=2312
FragThreshold=2312
PSMode=CAM
-----------------------------------------------
syntax is 'Param'='Value' and described below.

1.  CountryRegion=value
    value
        0:      for use channel 1-11
        1:      for use channel 1-11
        2:      for use channel 1-13
        3:      for use channel 10-11
        4:      for use channel 10-13
        5:      for use channel 14
        6:      for use channel 1-14
        7:      for use channel 3-9
2.  WirelessMode=value
    value
        0:      802.11 B/G mixed
        1:      802.11 B only
3.  SSID=value
    value
         1~32 ascii characters.
4.  NetworkType=Infra
    value
       Infra : infrastructure mode
       Adhoc : adhoc mode
5.  Channel=value
    value
        1~14 depends on  CountryRegion
6.  AuthMode=value
    value
        OPEN      For Open System
        SHARED    For Shared key system
        AUTO
        WPANONE   For pre-shared key in adhoc mode
        WPAPSK    For pre-shared key in infrastructure mode
7.  EncrypType=value
    value
        NONE      :For AuthMode=OPEN
        WEP       :For AuthMode=OPEN or AuthMode=SHARED
        TKIP      :For AuthMode=WPAPSK or AuthMode=WPANONE
        AES       :For AuthMode=WPAPSK or AuthMode=WPANONE
8.  DefaultKeyID=value
    value
        1 ~ 4
9.  Key1=value
    value
        10 or 26 hexadecimal characters eg: 012345678
        5 or 13 ascii characters eg: passd
10. Key2=value
    value
        10 or 26 hexadecimal characters eg: 012345678
        5 or 13 ascii characters eg: passd
11. Key3=value
    value
        10 or 26 hexadecimal characters eg: 012345678
        5 or 13 ascii characters eg: passd
12. Key4=value
    value
        10 or 26 hexadecimal characters eg: 012345678
        5 or 13 ascii characters eg: passd
13. WPANONE=value - use for adhoc mode
    value
        8 ~ 63 characters
          or
        64 hexadecimal characters
13. WPAPSK=value - use for infrastructure mode
    value
        8 ~ 63 characters
          or
        64 hexadecimal characters
14. TxBurst=value
    value
        0:        Disable
        1:        Enable
15. TurboRate=value
    value
        0:        Disable
        1:        Enable
16. BGProtection=value
   value
        0:        Auto
        1:        Always On
        2:        Always Off
17. ShortSlot=value
    value
        0:        Disable
        1:        Enable
18. TxPreamble=value
    value
         0:     Long
         1:     Short
         2:     Auto
19. TxRate=value
    value
         0:     Auto
         1:     1 Mbps
         2:     2 Mbps
         3:     5.5 Mbps
         4:     11 Mbps
         5:     6  Mbps  //WirelessMode must be 0
         6:     9  Mbps  //WirelessMode must be 0
         7:     12 Mbps  //WirelessMode must be 0
         8:     18 Mbps  //WirelessMode must be 0
         9:     24 Mbps  //WirelessMode must be 0
        10:     36 Mbps  //WirelessMode must be 0
        11:     48 Mbps  //WirelessMode must be 0
        12:     54 Mbps  //WirelessMode must be 0
20. RTSThreshold=value
    value
        1 ~ 2312
21. FragThreshold=value
    value
        256 ~ 2312
22. PSMode=value
    value
    MAX_PSP   Power Saving Mode

23. AdhocOfdm=value
    value
         0:     Tx MAX rate will be 11Mbps in Adhoc mode.
         1:     Tx MAX rate will be 54Mbps in Adhoc mode.

24. StaWithEtherBridge=value
    value
         0:     Disable sta with ethernet to wireless bridge.
         1:     Enable sta with ethernet to wireless bridge.


MORE INFORMATION
======================================================================
If you want for rt2500 driver to auto-load at boot time:
A) choose ra0 for first RT2500 WLAN card, ra1 for second RT2500 WLAN
   card, etc.

B) create(edit) 'ifcfg-ra0' file in /etc/sysconfig/network-scripts/,
   edit( or add the line) in /etc/modules.conf:
       alias ra0 rt2500

C) edit(create) the file /etc/sysconfig/network-scripts/ifcfg-ra0
   DEVICE='ra0'
   ONBOOT='yes'


NOTE:
   if you use dhcp, add this line too .
    BOOTPROTO='dhcp'

*D) To ease the Default Gateway setting,
    add the line
    GATEWAY=x.x.x.x
    in /etc/sysconfig/network

INFORMATION FOR FEDORA CORE 3 USERS (USE AT YOUR OWN RISK !!!)
======================================================================
While this information is directed to Fedora Core 3 users, there is no
harm in trying some hints and clues in other distros.

Before starting, make sure you don't have any ifcfg-ra* or ifcfg-eth*
that has information about Ralink wireless cards. Check also
/etc/modprobe.conf for additional 'alias' definitions.

If you have any of the files above and/or entries in modprobe.conf,
please delete them now.

Compile the module as you would do normally with:

a) $make

and as root do:

b) $make install-fedora

The module should be installed to the correct location and the rt2500
alias added to modprobe.conf (2.6 kernels) or modules.conf
(2.4 kernels).

Start 'system-config-network',
New->Wireless connection,
Select 'RaLink Ralink RT2500 802.11 Cardbus Reference Card (wlan0)'
If it does not appear, well then it didn't work for you :)

But if it did appear then configure the rest of the parameters and
activate the card in the end.

Save configuration and enjoy your new wireless device.
Help!

---

### Post by ricardisimo on 2008-02-09
By the way, the above comes from the README mentioned in the Launchpad bug report [here]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/134660").
The specific post says:


> Hi guys,
        I finally got my onboard RT2500 card working under Gutsy on my Fujitsu-Siemens Amilo A1630. The drivers that come with gutsy didn't work and nor did ndiswrapper. However, the lastest CVS snapshot of seriualmonkey's driver ([http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz)) worked great!

So, just download the file, untar, follow instructions in the README of the Module diretcory.

After you are done blackist the old drivers by adding these lines to /etc/modprobe.d/blacklist:

blacklist rt2500pci
blacklist rt2x00pci
blacklist rt2x00lib

Hope this helps!
Unfortunately it doesn't help. It's all Greek to me.

---

### Post by wieman01 on 2008-02-11
**@ricardisimo:**

See, that's exactly the reason why I don't want to mess around with it. It's plain ridiculous. ;-)

I did not have time over the weekend, so at the moment I cannot help you much. And given the extent of the instructions, I am reluctant to go through the hassle, what do you think?

---

### Post by ricardisimo on 2008-02-11
All I want is for someone to tell me "Just wait for Hardy... that will fix everything." That's all I'm hoping for.

---

### Post by axamax on 2008-02-11
invalid driver message when trying to install Belkin usb wireless adapter F5D7050B. Downloaded driver from Belkin site. followed this tutorial carefully, but when I get to
sudo ndiswrapper -i rt73.inf " i get driver rt73 is already installed

at ndiswrapper -l     I get rt73: invalid driver

Anyone got any ideas?

---

### Post by wieman01 on 2008-02-12
> **ricardisimo said:**
> All I want is for someone to tell me "Just wait for Hardy... that will fix everything." That's all I'm hoping for.
Just wait for Hardy! :-) It should ship with kernel 2.6.25 which comes with new Ralink drivers, etc. So let's keep our fingers crossed!

---

### Post by wieman01 on 2008-02-12
> **axamax said:**
> invalid driver message when trying to install Belkin usb wireless adapter F5D7050B. Downloaded driver from Belkin site. followed this tutorial carefully, but when I get to
sudo ndiswrapper -i rt73.inf " i get driver rt73 is already installed

at ndiswrapper -l     I get rt73: invalid driver

Anyone got any ideas?
You have probably chosen the wrong driver in the first place. Are you on 64-bit Ubuntu or 32-bit?

---

### Post by axamax on 2008-02-12
32 bit ubuntu
It's a usb wireless adapter. I tried both rt73 and rt73usb but no joy
How could I check the driver. This appeared to be the relevant one. The archive was F5D7050v3.exe direct from Belkin site. Is there a better on at serialmonkey?

---

### Post by wieman01 on 2008-02-12
> **axamax said:**
> 32 bit ubuntu
It's a usb wireless adapter. I tried both rt73 and rt73usb but no joy
How could I check the driver. This appeared to be the relevant one. The archive was F5D7050v3.exe direct from Belkin site. Is there a better on at serialmonkey?
The one on Serialmonkey's website is the Linux driver, the one that you have got from Belkin's website is a Windows driver. You can try Serialmonkey's driver of course, but that's an entirely different approach. 

Again I recommend you check the driver version and ensure you have got the right one. If all this does not help, then I suggest that you check out Serialmonkey.

---

### Post by axamax on 2008-02-12
thanks I'll try serialmonkey, but it looks a lot more complicated. I've just tried Hardy Alpha 4 but it wouldn't boot up.
Could you clarify one thing regarding the blacklist? Are the drivers added to the blacklist being blocked or suggested.

ie. should the line echo blacklist be excluding the drivers I DON'T want.

---

### Post by bouncer5 on 2008-02-12
Hi, I know nothing about linux sadly but I bought a TPLINK TL-WN321G (Driver is RT73 which is another name for RT2500 I belive) I don't have a clue how to get it to work, I know linux finds it which is much better than my last wireless adapter that would not show.

I need help can anyone give me like a step by step instructions please I read the topic but most of it made no sence to me.

---

### Post by wieman01 on 2008-02-12
> **axamax said:**
> thanks I'll try serialmonkey, but it looks a lot more complicated. I've just tried Hardy Alpha 4 but it wouldn't boot up.
Could you clarify one thing regarding the blacklist? Are the drivers added to the blacklist being blocked or suggested.

ie. should the line echo blacklist be excluding the drivers I DON'T want.
Anything you will put on the blacklist will prevent these very modules/drivers from being loaded. In other words, blacklisting them will exclude them since you don't want them.

---

### Post by wieman01 on 2008-02-12
> **bouncer5 said:**
> Hi, I know nothing about linux sadly but I bought a TPLINK TL-WN321G (Driver is RT73 which is another name for RT2500 I belive) I don't have a clue how to get it to work, I know linux finds it which is much better than my last wireless adapter that would not show.

I need help can anyone give me like a step by step instructions please I read the topic but most of it made no sence to me.
Have you read the instructions I have posted? And are you a bit familiar with command line?

---

### Post by ricardisimo on 2008-02-12
> **wieman01 said:**
> Just wait for Hardy! :-) It should ship with kernel 2.6.25 which comes with new Ralink drivers, etc. So let's keep our fingers crossed!

I'm assuming I'm going to have to do a fresh install of Hardy, since there is no way to leapfrog Gutsy with the upgrade option. Oh, well... it wouldn't be the first time. Thanks again.

---

### Post by wieman01 on 2008-02-12
> **ricardisimo said:**
> I'm assuming I'm going to have to do a fresh install of Hardy, since there is no way to leapfrog Gutsy with the upgrade option. Oh, well... it wouldn't be the first time. Thanks again.
Yeah, I would go for a fresh install as well. History tends to repeat itself...

---

### Post by bouncer5 on 2008-02-13
> **wieman01 said:**
> Have you read the instructions I have posted? And are you a bit familiar with command line?

I did read the instructions, but I got lost I know nothing about linux, I tryed to follow some instuctions on g***wrapper can't rember what its called exactly, it didn't help as some of the links on the page were broken, I do know that almost everythign I need to do is "code" and you use the terminal i think, other than that I dont have a  clue (Alsways beena  windows user and always hated it)

---

### Post by wieman01 on 2008-02-13
> **bouncer5 said:**
> I did read the instructions, but I got lost I know nothing about linux, I tryed to follow some instuctions on g***wrapper can't rember what its called exactly, it didn't help as some of the links on the page were broken, I do know that almost everythign I need to do is "code" and you use the terminal i think, other than that I dont have a  clue (Alsways beena  windows user and always hated it)
Do you know how to open a terminal window? If yes please type:
> sudo iwlist scan
> sudo lshw -C network
And paste the output here. Enter your user password when asked.

I can attach a screenshot if that helps you. Let me know.

---

### Post by bouncer5 on 2008-02-13
I had to add it to a tar.gz archive so I can uplaod it on windows as the file type wont show

---

### Post by wieman01 on 2008-02-13
> **bouncer5 said:**
> I had to add it to a tar.gz archive so I can uplaod it on windows as the file type wont show
Typo, please do it again:
> sudo lshw -C network

---

### Post by bouncer5 on 2008-02-13
Just relised that I typed network wrong, Ive attacthed the file spelt correctly

---

### Post by wieman01 on 2008-02-13
See... Now you should be more familiar with the command line interface. :-) Do you think you could do the same again by following my tutorial? Do you have the Windows driver files at hand?

---

### Post by bouncer5 on 2008-02-13
I have lots of drivers, I have the old windows driver (that jsut works unlike the new one) I have the one from the ralink site, And I have the linux version from the Ralink site also.

---

### Post by wieman01 on 2008-02-13
> **bouncer5 said:**
> I have lots of drivers, I have the old windows driver (that jsut works unlike the new one) I have the one from the ralink site, And I have the linux version from the Ralink site also.
For this tutorial, you need the Windows drivers from your vendor. If you have them, please give the tutorial a go. Post here if you need help, I can explain things to you if you like.

---

### Post by bouncer5 on 2008-02-13
Thanks ive took a bash at im but im stuck 

Load new driver module (may not be necessary any longer, but does no harm either):
Quote:
sudo depmod -a
sudo modprobe ndiswrapper  


first command tehre was a delay before anythign came up

then the other command dosn't seem to do anything
About the loading new driver? is that what the commadn does or am I ment to do it?

And the next bit makes less sence to me

Add the module to "/etc/modules" to have it load automatically:

Quote:
echo 'ndiswrapper' | sudo tee -a /etc/modules

---

### Post by wieman01 on 2008-02-13
What happens when you type:
> sudo ndiswrapper -l
And what steps have you performed up to now?

---

### Post by bouncer5 on 2008-02-13
I moved on to distroying a old Toshiba Satallite, I think im best starting from the begining all over again

When  I do this step

Install "ndiswrapper" package without working internet connection (alternatively, install it via Synaptic/Adept):

> 
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9  


What CD do I insert?

---

### Post by wieman01 on 2008-02-13
> **bouncer5 said:**
> I moved on to distroying a old Toshiba Satallite, I think im best starting from the begining all over again

When  I do this step

Install "ndiswrapper" package without working internet connection (alternatively, install it via Synaptic/Adept):

What CD do I insert?
The Ubuntu Live CD that is. You surely have a copy, right? Have you used Synaptic, the package manager, before? You can install the required packages using that as well.

---

### Post by YeFFreY on 2008-03-03
Hello,

Just a feedback from a newbie : 

It is not the first time that I install Ubuntu. I had a lot of problems with network from the first install (a few years ago) to the last install (this morning).

I had the Win Modem problem : adsl modem which has no driver at all for linux, and I was unable to make it work... So Adios Linux for a few years...
The next attempt was on a laptop, no network problems but the graphic card was an ATI X700 : lot of problems if you want accelerated graphics... So ubuntu very unstable, lot of freezes... Adios Ubuntu...

So a few days ago, I bought a brand new pc : Core quad, geforce (no ATI...) BUT i bought the Asus Usb stick for wireless, the well-known ASUS WL-167g...
It was not working, could only see my Essid but not able to connect to it. I found a lot of people having the same problem but every one had a different solution : ndiswrapper, rt2500usb, serialmonkey,...
After trying a lot of these, the perfect solution comes to:
1.  Do not use network applet loaded by default in Ubuntu, use Wicd
2.  Download the rt2xxx that match the version of the Asus usb stick (for me, it was rt2570 from CVS, the stable version is an old old one)
3. compile the serialmonkey driver and install it.
4. blacklist the rt2500usb
5. restart and let wicd connect to the network via 'wext'

And OUF ! it's working...

Tell me that linux is easy... Yeah tell it loud..
:guitar:

---

### Post by wieman01 on 2008-03-03
> **YeFFreY said:**
> 2.  Download the rt2xxx that match the version of the Asus usb stick (for me, it was rt2570 from CVS, the stable version is an old old one)

Is 'rt2xxx' capable of WPA/WPA2? If not people ought to stop recommending it.

---

### Post by YeFFreY on 2008-03-05
Yes, I agree with you
I didn't check because, for the moment I only try to make it work... and it's already a pain in the ***...

---

### Post by wieman01 on 2008-03-05
> **YeFFreY said:**
> Yes, I agree with you
I didn't check because, for the moment I only try to make it work... and it's already a pain in the ***...
So no WPA/WPA2 support indeed?

---

### Post by ruiruas on 2008-03-05
Hi, I own a Edimax 7318usg, wich uses the rt73 chip. It's supposed to have native linux drivers wich do not work under gutsy. After trying a few things, I decided to follow this post and blacklist all the modules listed here. It worked!!!
Thanks.

---

### Post by Ken_Lewis81 on 2008-03-07
What with Hardy coming (please test!), which uses the 2.6.24 kernel with in-place support for the RT2x00 via mac80211 network stack, does anyone have an update to this post for the new LTS?

I'm using a /etc/wpa_supplicant.conf and comments in my /etc/network/interfaces to make use of the kernel's drivers, rather than the NDIS wrapper. I haven't yet made friends with NetworkManager and so the following recipe will need to be fixed up when NM 0.7 offers GUI config for WPA/WPA2.

The /etc/wpa_supplicant is generated with:
```
sudo wpa_passphrade $wireless-network-SSID $passphrase > /etc/wpa_supplicant.conf
```
and your /etc/network/interfaces:
```

iface wlan0 dhcp
	wireless-essid $wireless-network-SSID
	pre-up iwconfig wlan0 ap $wireless-network-SSID-MAC-Address
	pre-up wpa_supplicant -Bw -iwlan0 -c/etc/wpa_supplicant.conf
	post-down killall -q wpa_supplicant

```
Please replace $wireless-network-SSID, $wireless-network-SSID-MAC-Address and $passphrase with your respective details.

Take care.
K3n.

---

### Post by wieman01 on 2008-03-09
I really hope Hardy does a better job here and this thread won't be necessary any longer. Let's hope for the best.

---

### Post by gfg on 2008-03-09
> **wieman01 said:**
> I really hope Hardy does a better job here and this thread won't be necessary any longer. Let's hope for the best.

Dosen't seem like it yet at least. Using Hardy and getting constant freezes with rt61pci during heavy network use. Maybe it will be fixed before final.

---

### Post by rob_s81 on 2008-03-12
Hi, I'm fairly new to Linux, I've started using various distro's at work and decided to make the switch at home after seeing what Ubuntu 7.10 was capable of.

I've got a belkin wireless 54g pci nic with the rt61 chipset on it and a Netgear 54g wireless router using WPAPSK with TKIP. Its worked perfectly on windows for well over a year and still does.

Using the default drivers included in Gutsy, the card would connect temporarily but would soon slow to a crawl and drop out after a few minutes and I would have to reboot the machine in order to re connect. I've tried using ndiswrapper from synaptic with the drivers from windows "oem29.inf" and "rt61.sys", and the same thing happens. I've also tried compiling the latest stable version of ndiswrapper and again no luck.

I recently found the ralink linux driver for the rt61 and this how to **[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61") **and so decided to give it a go, with some minor success. After about 30 minutes following the instructions (bare in mind this is all new to me), the card connected to the router and remained stable with a good download speed for roughly 40mins which allowed Ubuntu to download its updates, after which the system requested to be restarted, after doing this I just can't get the thing to work at all anymore.

Immediately after start up ```
ifconfig
``` only returns the loopback interface. indicating the wireless interface needed bringing up. So I used
```
ifconfig ra0 up
``` 
this brings the wireless interface up but using ```
iwconfig ra0
```all the configuration is missing. So I used the following commands to attempt to configure the card.
```
iwconfig ra0 essid "MY_SSID"
iwpriv ra0 set AuthMode=WPAPSK
iwpriv ra0 set EncrypType=TKIP
iwpriv ra0 set WPAPSK="MY WPA KEY"
```
where MY WPA KEY is generated using wpa_passphrase.
Now entering iwconfig only the ssid has been set, and the card is still not using any encryption and subsequently fails to communicate with the router.

I've checked both /etc/network/interfaces and /etc/Wireless/RT61STA/rt61sta.dat and both still have the configuration I gave them including all the WPA information.

I followed the above mentioned How-to to the letter and I'm pretty sure that I haven't missed anything. I black listed the old driver, and I am using the original rt61 chipset so I have removed network-manager.

If anyone has any suggestions as to whats going wrong please let me know. I was hoping Linux would be a bit of a challenge, but getting the wireless card working is looking impossible.
I'm pretty new to forums as well as linux, so I apologies if my post isn't formatted properly or if I've missed any information off.

Please help.

---

### Post by wieman01 on 2008-03-12
rob_s81, 

Please post the following:
> sudo iwlist scan
> sudo lshw -C network
> sudo cat /etc/network/interfaces
> sudo ndiswrapper -l
Which driver/module have you blacklisted exactly?

---

### Post by rob_s81 on 2008-03-13
I'll try to get the information you have requested tonight, as I've no network connection I hadn't read this until I got to work this morning.

It was the rt61pci module I blacklisted as the howto I mentioned instructed, using 

```
$ echo 'blacklist rt61pci' >> /etc/modprobe.d/blacklist

```

---

### Post by smo0th on 2008-03-13
My card was working in feisty but now it does not work in gutsy, I'm using a phenom CPU which is 64-bits, those are the new variables, I've tried everything in every post I've found since 3 days ago and still can't get my wireless running, my chipset is rt2500, I've tried RutilT, wicd, wlassistant and a serious combination of /etc/network/interfaces configurations but nothing works, has someone been successful on running the card with similar system specs?

any ideas? :confused:

---

### Post by wieman01 on 2008-03-13
Have yougot the 64-bit Windows driver as well?

---

### Post by rob_s81 on 2008-03-13
Here is hopefully the information you have asked for. Although my situation has now changed some what. I have now managed to get the card working temporarily again, after removing ndiswrapper and using the System -> Administration -> Network tool to configure the card. Unless I use this I can't get the card to configure.

In the how to it says you must take the interface down before configuring it with the iwpriv commands, but when I do this it complains that the interface is down and it won't do it while the it is down, bring the interface back up and it appears to work until you do iwconfig and its completely ignored all the commands...:confused:

```

$sudo iwlist scan

ra0       Scan completed :
          Cell 01 - Address: 00:1E:2A:57:AB:5C
                    Mode:Managed
                    ESSID:"MY NETWORK"
                    Channel:1
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:85/100  Signal level:-54 dBm  Noise level:-79 dBm
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:16:E3:17:B0:28
                    Mode:Managed
                    ESSID:"NEIGHBOURS NETWORK"
                    Channel:8
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:69/100  Signal level:-70 dBm  Noise level:-79 dBm

```

```

$ sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: ra0
       version: 00
       serial: 00:11:50:dd:e2:c4
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt61 ip=192.168.10.5 latency=32 link=yes module=rt61 multicast=yes wireless=RT61 Wireless
  *-network:1 DISABLED
       description: Ethernet interface
       product: RTL8139 Ethernet
       vendor: D-Link System Inc
       physical id: c
       bus info: pci@0000:00:0c.0
       logical name: eth0
       version: 10
       serial: 00:40:05:85:40:dd
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:2 DISABLED
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth1
       version: 78
       serial: 00:30:18:72:35:38
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s

```


This is a bit screwy as I've had to use the Network tool which has edited this file.

```

$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback




wpa-psk cb2f6fc4782e6a2f8389fd8975c46cc2c7c80edfa1e705108e17e462bf89afc2
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid rob-router



iface ra0 inet dhcp
wpa-psk cb2f6fc4782e6a2f8389fd8975c46cc2c7c80edfa1e705108e17e462bf89afc2
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid rob-router


auto ra0

```


ndiswrapper now removed

```

 sudo ndiswrapper -l
sudo: ndiswrapper: command not found

```

---

### Post by AdHavoc on 2008-03-13
Does anyone know if this guide works with the RaLink RT2600 chipset?

EDIT: This guide works perfectly for me on Gutsy without a hitch!  Thanks!

---

### Post by conehead77 on 2008-03-13
Thanks for this guide!
Worked on Feisty for me.

I had 2 problems:

- I didnt know where to find the windows driver for the wifi card; somewhen i noticed i could just copy the folder with the driver from my windows partition (C:/Program Files/Ralink/RT6x Wireless LAN Card/Installer/WINXP/) to the ubuntu partition and go on.

- I wasnt able to install ndiswrapper from CD, so i downloaded the .debs from [http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/)
I needed a version for Feisty and it was the 1.38 i think

Now it works and im happy :)

---

### Post by smo0th on 2008-03-14
good point o.o I'll check that

---

### Post by mikespike2 on 2008-03-14
I'm not sure how to do the blacklisting part..

I have a linksys WUSB54GS v1. Any suggestions?

---

### Post by smo0th on 2008-03-14
I did install the x64 drivers using ndiswrapper and got:

Interface doesn't accept private ioctl...
set (8BE2): Invalid argument
Failed to bring up wlan0.

I ran out of ideas ](*,)

I guess I'll end up buying another wireless card and smashing the rt2500 :-x

> **mikespike2 said:**
> I'm not sure how to do the blacklisting part..

I have a linksys WUSB54GS v1. Any suggestions?

blacklisting is to put the drivers in a list so they are prevented from being used by the system, this way you won't have driver conflicts.

---

### Post by wieman01 on 2008-03-14
> **rob_s81 said:**
> Here is hopefully the information you have asked for. Although my situation has now changed some what. I have now managed to get the card working temporarily again, after removing ndiswrapper and using the System -> Administration -> Network tool to configure the card. Unless I use this I can't get the card to configure.

ndiswrapper now removed

```

 sudo ndiswrapper -l
sudo: ndiswrapper: command not found

```
OK, so you have now removed 'ndiswrapper' and use the native Ralink driver. What's your question then? I have little experience with Ralink drivers per se, as I use 'ndiswrapper'... :confused:

---

### Post by wieman01 on 2008-03-14
> **AdHavoc said:**
> Does anyone know if this guide works with the RaLink RT2600 chipset?

EDIT: This guide works perfectly for me on Gutsy without a hitch!  Thanks!
Great, thanks for letting me know. What driver have you blacklisted? And what adapter have you got?

---

### Post by wieman01 on 2008-03-14
> **mikespike2 said:**
> I'm not sure how to do the blacklisting part..

I have a linksys WUSB54GS v1. Any suggestions?
What chipset does this model use... any idea? Please post:
> sudo lshw -C network

---

### Post by wieman01 on 2008-03-14
> **smo0th said:**
> I did install the x64 drivers using ndiswrapper and got:

Interface doesn't accept private ioctl...
set (8BE2): Invalid argument
Failed to bring up wlan0.

I ran out of ideas ](*,)

I guess I'll end up buying another wireless card and smashing the rt2500 :-x



blacklisting is to put the drivers in a list so they are prevented from being used by the system, this way you won't have driver conflicts.
No problem. Let's look at it again... So you are on 64-bit Ubuntu, am I right? And you have downloaded the 64-bit version of the wireless driver as well?

Please post the following:
> sudo ndiswrapper -l
> sudo iwlist scan
> sudo lshw -C network

---

### Post by clueless on 2008-03-14
Great guide, finaly my usb wifi works!

I found out that to make it work with knetworkmanager I had to remove the lines:

auto wlan0
iface wlan0 inet dhcp

from  /etc/network/interfaces 

I am using gutsy, by the way, that had detected and used the linux driver (rt73) but the connection was very unreliable. I hope with ndiswrapper things will get better.

Thanks!

---

### Post by wieman01 on 2008-03-14
> **clueless said:**
> Great guide, finaly my usb wifi works!

I found out that to make it work with knetworkmanager I had to remove the lines:

auto wlan0
iface wlan0 inet dhcp

from  /etc/network/interfaces 

I am using feisty, by the way, that had detected and used the linux driver (rt73) but the connection was very unreliable. I hope with ndiswrapper things will get better.

Thanks!
And thanks for the feedback. What brand/model have you got if I may ask?

---

### Post by smo0th on 2008-03-14
> No problem. Let's look at it again... So you are on 64-bit Ubuntu, am I right? And you have downloaded the 64-bit version of the wireless driver as well?

That's correct.

Ok, my output from those commands is:


smo0th@ubuntu:~/Desktop$ sudo ndiswrapper -l
wmp54gv4-x64 : driver installed
        device (1814:0201) present (alternate driver: rt2500)


smo0th@ubuntu:~/Desktop$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results




smo0th@ubuntu:~/Desktop$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: 00:1e:8c:68:36:13
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.0.7 duplex=full firmware=N/A ip=192.168.1.103 latency=0 link=yes module=atl1 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 7
       bus info: pci@0000:03:07.0
       logical name: wlan0
       version: 01
       serial: 00:12:17:63:71:2f
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2500 latency=64 module=rt2500 multicast=yes wireless=RT2500 Wireless

---

### Post by AdHavoc on 2008-03-15
> **wieman01 said:**
> Great, thanks for letting me know. What driver have you blacklisted? And what adapter have you got?

I have an Airlink101 MIMO XR 802.11g adapter using the drivers from opendrivers.com.  I blacklisted the rt61 and rt61pci (backup) drivers.

---

### Post by wieman01 on 2008-03-15
> **smo0th said:**
> link=yes module=atl1 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 7
       bus info: pci@0000:03:07.0
       logical name: wlan0
       version: 01
       serial: 00:12:17:63:71:2f
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes **[COLOR="Red"]driver=rt2500[/COLOR]** latency=64 module=rt2500 multicast=yes wireless=RT2500 Wireless
It appears the old driver is still in place. Which one have you blacklisted? Please try:
> rt2500
rt2500usb
rt2500pci
Then restart the PC and post the same stuff once again.

---

### Post by smo0th on 2008-03-15
blacklisted:
rt2500
rt2500usb
rt2500pci 

restarted pc,

output remains the same:

smo0th@ubuntu:~/files$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: 00:1e:8c:68:36:13
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.0.7 duplex=full firmware=N/A ip=192.168.1.103 latency=0 link=yes module=atl1 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 7
       bus info: pci@0000:03:07.0
       logical name: wlan0
       version: 01
       serial: 00:12:17:63:71:2f
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2500 latency=64 module=rt2500 multicast=yes wireless=RT2500 Wireless

x.x

---

### Post by Strates on 2008-03-15
I'm not able to get through the first step (the one that doesn't require an internet connection), without receiving errors. I wasn't able to go through the first part of the step, I'm assuming thats because I don't have the file on CD, I'm using a USB drive.

 I went through synaptic and installed a previous version of the ndiswrapper, but when I enter the command sudo apt-get install ndiswrapper-common ... ,
I get the error:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


Any help would be much appreciated, I've just started using Linux and i have no idea what I am doing.

                              Thx in advance, Nathan.

---

### Post by smo0th on 2008-03-15
> **Strates said:**
> I'm not able to get through the first step (the one that doesn't require an internet connection), without receiving errors. I wasn't able to go through the first part of the step, I'm assuming thats because I don't have the file on CD, I'm using a USB drive.

 I went through synaptic and installed a previous version of the ndiswrapper, but when I enter the command sudo apt-get install ndiswrapper-common ... ,
I get the error:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


Any help would be much appreciated, I've just started using Linux and i have no idea what I am doing.

                              Thx in advance, Nathan.

Seems like you have more than one synaptic session opened, if you are running synaptic and want to use apt-get you must close synaptic first in order to release the lock and be able to use apt-get, this resource can be used only by one process at a time.

---

### Post by wieman01 on 2008-03-16
> **Strates said:**
> I'm not able to get through the first step (the one that doesn't require an internet connection), without receiving errors. I wasn't able to go through the first part of the step, I'm assuming thats because I don't have the file on CD, I'm using a USB drive.

 I went through synaptic and installed a previous version of the ndiswrapper, but when I enter the command sudo apt-get install ndiswrapper-common ... ,
I get the error:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


Any help would be much appreciated, I've just started using Linux and i have no idea what I am doing.

                              Thx in advance, Nathan.
smo0th is right. Please restart the PC and try once again.

---

### Post by wieman01 on 2008-03-16
> **smo0th said:**
> blacklisted:
rt2500
rt2500usb
rt2500pci 

restarted pc,

output remains the same:

smo0th@ubuntu:~/files$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: 00:1e:8c:68:36:13
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.0.7 duplex=full firmware=N/A ip=192.168.1.103 latency=0 link=yes module=atl1 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 7
       bus info: pci@0000:03:07.0
       logical name: wlan0
       version: 01
       serial: 00:12:17:63:71:2f
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2500 latency=64 module=rt2500 multicast=yes wireless=RT2500 Wireless

x.x
It appears that the old driver is still in use. No idea why. Perhaps it has to do with your system being a 64-bit one.

All I can offer right now is that you compile the latest version of ndiswrapper from source. Kevdog has a good tutorial which explains how to do it. It could work for you.

---

### Post by smo0th on 2008-03-16
Thanks wieman01, I'll try it later, if I get to a solution I'll post it here ;)

---

### Post by clueless on 2008-03-18
> **wieman01 said:**
> And thanks for the feedback. What brand/model have you got if I may ask?
Sorry I just read your question...
It's an ASUS WL-167G.

---

### Post by Apewall on 2008-03-20
I'm trying to get my rt61/2561 based adapter working, followed the guide but after a reboot wlan0 is no longer listed under iwconfig etc.

I'm running x86_64 Gutsy and got ahold of the rt61/256x windows 64bit driver.

```
apewall@box:~$ sudo ndiswrapper -l
netr6164 : driver installed
        device (1814:0302) present (alternate driver: rt61pci)

```
I added rt61pci to the blacklist when i followed the tutorial.

```

apewall@box:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

[  GNU nano 2.0.6         File: /etc/network/interfaces                          


```

/etc/network/interfaces

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp

```

I'm not sure what else I need to do to get the driver to load.

---

### Post by wieman01 on 2008-03-20
Apewall, 

Please also post:
> sudo iwlist scan
> sudo lshw -C network
What driver/module have you blacklisted?

---

### Post by Apewall on 2008-03-22
sudo iwlist scan
```

lo            Interface doesn't suppot scanning.

eth0       Interface doesn't support scanning.

```

sudo lshw -C network
```

*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:16:17:4f:9b:d1
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network UNCLAIMED
       description: Network controller
       product: RT2561/RT61 rev B 802.11g
       vendor: RaLink
       physical id: 9
       bus info: pci@0000:05:09.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64

```

/etc/modprobe.d/blacklist
```

**blacklist rt61pci**

```

---

### Post by wieman01 on 2008-03-23
> **Apewall said:**
> sudo iwlist scan
```

lo            Interface doesn't suppot scanning.

eth0       Interface doesn't support scanning.

```

sudo lshw -C network
```

*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:16:17:4f:9b:d1
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network UNCLAIMED
       description: Network controller
       product: RT2561/RT61 rev B 802.11g
       vendor: RaLink
       physical id: 9
       bus info: pci@0000:05:09.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64

```

/etc/modprobe.d/blacklist
```

**blacklist rt61pci**

```
That's a 64-bit system, isn't it? Did you also use the 64-bit Windows driver for your adapter? That's crucial.

---

### Post by Apewall on 2008-03-24
Yes, I actually had to have a friend with windows xp 64bit run the RALINK installer to grab the 64bit driver, as it extracts it based on what your system is.

---

### Post by bundleboy on 2008-03-26
Hi guys,

i am new to linux and find it quite hard to grasp every command but could someone explain what is blacklist and why we have to do it,
to my understanding, it's to tell ubuntu not to load those drivers at startup please correct me if i am wrong.

And to my second question, if blacklist is what i think it is (i am probably wrong) why are we blacklisting e.g. rt25** when thats the driver we are trying to get running at startup/ install.

Apologies for my not so smart questions

Thanks
Karthik

---

### Post by wieman01 on 2008-03-26
> **bundleboy said:**
> I am new to linux and find it quite hard to grasp every command but could someone explain what is blacklist and why we have to do it,
to my understanding, it's to tell ubuntu not to load those drivers at startup please correct me if i am wrong.
Yes, that is right. The backlist prevents those drivers from loading.
> **bundleboy said:**
> And to my second question, if blacklist is what i think it is (i am probably wrong) why are we blacklisting e.g. rt25** when thats the driver we are trying to get running at startup/ install.
We don't use these drivers, but rather make use of 'ndiswrapper' which replaces the native Linux driver.

Does this make sense to you?

---

### Post by bundleboy on 2008-03-26
> **wieman01 said:**
> Yes, that is right. The backlist prevents those drivers from loading.

We don't use these drivers, but rather make use of 'ndiswrapper' which replaces the native Linux driver.

Does this make sense to you?

Yes and no, Replacing native drivers(understood) and no because as i understand ndiswrapper is used to so called simulate a "wrap" that fits linux but is actually in reality a windows driver that part has me lost... why would you go through so much of trouble when apps like kismet do not natively support windows driver so are we not taking a problem out and then essentially putting it back into Linux making it as  regulatory as a windows PC would be..?

Just me and my thoughts please correct me if i got things wrong..

And on the lesser confused note...
Wow you guys really do monitor these forums!!! Wonderful job and thanks wieman:KS

---

### Post by wieman01 on 2008-03-26
> **bundleboy said:**
> Yes and no, Replacing native drivers(understood) and no because as i understand ndiswrapper is used to so called simulate a "wrap" that fits linux but is actually in reality a windows driver that part has me lost... why would you go through so much of trouble when apps like kismet do not natively support windows driver so are we not taking a problem out and then essentially putting it back into Linux making it as  regulatory as a windows PC would be..?

Just me and my thoughts please correct me if i got things wrong..

And on the lesser confused note...
Wow you guys really do monitor these forums!!! Wonderful job and thanks wieman:KS
Thins is most regular users don't use tools like Kismet, Aircrack, etc. They just need a working wireless device. This tutorial is targeting those very users.

Second, as some Linux drivers have issues and don't work too well (lack of WPA suport, etc.) we revert to using 'ndiswrapper' which indeed wraps the native Windows driver and makes use of it. What's wrong with it? Yes, it isn't beautiful because most Windows drivers aren't OS, however, in many cases that's the last option you have if you don't want to buy yourself a new device.

So 'ndiswrapper' uses the Windows driver and turns your wireless adapter into a Linux compatible device. See this for more:

[http://ndiswrapper.sourceforge.net/joomla/]("http://ndiswrapper.sourceforge.net/joomla/")

---

### Post by bundleboy on 2008-03-26
O ok thanks wieman understood.. but the thing is i used to use backtrack2 on liveCD but however things were very slow therefore i tried installing ubuntu gutsy becos i heard that the cores were the same btw i am using D-Link DWL-G122 Ver:B1 for which i am suppose to use Ralink's RT2570 drivers but even after dling it and make installing it i cant get it to recognise that the driver is for my wireless adapter its not as easy in windows where u just uninstall a driver and  reinstall a different driver all GUI driven.

However your answers are much appreciated and i was thinking maybe could u point me in the right direction of what am i suppose to google or maybe what im doing wrong. [Or maybe a different Thread dealing with this issue]
Thanks in advance
Peace

---

### Post by wieman01 on 2008-03-26
This is in fact the right thread... So you have followed my tutorial to the letter? Please post the results of:
> sudo iwlist scan
> sudo lshw -C network
> sudo ndiswrapper -l
> sudo cat /etc/network/interfaces

---

### Post by bundleboy on 2008-03-26
karthik@karthik-desktop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results



karthik@karthik-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1d:92:33:e3:14
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.201 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:11:95:d4:94:57
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


karthik@karthik-desktop:~$ sudo ndiswrapper -l
karthik@karthik-desktop:~$ 
{no output}

karthik@karthik-desktop:~$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback

im sorry i dont know how to use the code boxes :(

---

### Post by wieman01 on 2008-03-26
Nonsense... deleted.

---

### Post by bundleboy on 2008-03-26
Ok will do wieman will follow everything again and will let u know the outcome
Thanks much :)

---

### Post by wieman01 on 2008-03-26
> **bundleboy said:**
> Ok will do wieman will follow everything again and will let u know the outcome
Thanks much :)
Meiyo wenti la... You know where you find me.

---

### Post by bundleboy on 2008-03-26
sg?

anyways :D

i think i may have found a way to use kismet i am documenting the steps so that i can post it but i need some help.. how do i black list i have tried ur method but when i restart and insert usb in again the drivers get loaded... i wonder what i am doing wrong can u advise please thanks man

---

### Post by wieman01 on 2008-03-26
> **bundleboy said:**
> sg?
No la... But I know SG & HK well. :-)
> **bundleboy said:**
> 
i think i may have found a way to use kismet i am documenting the steps so that i can post it but i need some help.. how do i black list i have tried ur method but when i restart and insert usb in again the drivers get loaded... i wonder what i am doing wrong can u advise please thanks man
What drivers have you blacklisted then?

Kismet won't work after you have done everything outlined in my tutorial. At least packet re-injection won't work as you need a particular patch for the Linux Ralink driver.

---

### Post by bundleboy on 2008-03-26
karthik@karthik-desktop:~$ lsmod | grep rt2570
rt2570                190656  1 
usbcore               138632  8 rt2500usb,rt2x00usb,rt2570,usb_storage,libusual,ehci_hcd,uhci_hcd

these are the drivers i currently have on
 i did....

karthik@karthik-desktop:~$ sudo rmmod rt2500usb
karthik@karthik-desktop:~$ sudo rmmod rt2x00usb

then 

karthik@karthik-desktop:~$ lsmod | grep rt2570
rt2570                190656  0 
usbcore               138632  7 ndiswrapper,rt2570,usb_storage,libusual,ehci_hcd,uhci_hcd
 see no rt2500usb nor rt 2x00usb loaded drivers loaded

then i black list

karthik@karthik-desktop:~$ echo 'blacklist <rt2x00usb>' | sudo tee -a /etc/modprobe.d/blacklist
blacklist <rt2x00usb>
karthik@karthik-desktop:~$ echo 'blacklist <rt2500usb>' | sudo tee -a /etc/modprobe.d/blacklist
blacklist <rt2500usb>

however when i plug back the device and try i get
karthik@karthik-desktop:~$ lsmod | grep rt2570rt2570                190656  1 
usbcore               138632  9 rt2500usb,rt2x00usb,ndiswrapper,rt2570,usb_storage,libusual,ehci_hcd,uhci_hcd

[Update]
karthik@karthik-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT2500USB WLAN  ESSID:""  Nickname:""
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=11 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-120 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

 how come its like this any idea?

thanks again

---

### Post by wieman01 on 2008-03-26
You need to blacklist with brackets <>...

E.g.
> echo 'blacklist rt2500usb' | sudo tee -a /etc/modprobe.d/blacklist
Please also blacklist this one:
> echo 'blacklist rt2570' | sudo tee -a /etc/modprobe.d/blacklist
Then restart the PC.

---

### Post by bundleboy on 2008-03-26
ok nvm i found out how to make kismet work i am working on setting out the documentation so that i can post it cool wieman thanks for everything

---

### Post by magomago on 2008-04-10
i don't get this whole ".exe" thing....I haven't found a set of drivers that i could unzip.  I tried my brand (MSI) , the Ralink website

I tried to go to windows to see if i could extract it, but they turned out to be straight up installation files


is there a place i can get these?

---

### Post by wieman01 on 2008-04-10
> **magomago said:**
> i don't get this whole ".exe" thing....I haven't found a set of drivers that i could unzip.  I tried my brand (MSI) , the Ralink website

I tried to go to windows to see if i could extract it, but they turned out to be straight up installation files

is there a place i can get these?
In fact you simply need to get hold of the driver files mentioned e.g. .INF, etc. Ignore the .EXE bit for a minute.

Did your device come with a CD or something like that?

---

### Post by magomago on 2008-04-10
> **wieman01 said:**
> In fact you simply need to get hold of the driver files mentioned e.g. .INF, etc. Ignore the .EXE bit for a minute.

Did your device come with a CD or something like that?

i just have a .exe on my cd....no ifs :(

---

### Post by magomago on 2008-04-10
> **magomago said:**
> i just have a .exe on my cd....no ifs :(

.inf *


I checked again to be sure...I have nothing of that sort

---

### Post by wieman01 on 2008-04-10
You can unzip the .EXE using WinZIP in Windows for instance. Or any other ZIP tool. It should contain all these files.

---

### Post by magomago on 2008-04-10
> **wieman01 said:**
> You can unzip the .EXE using WinZIP in Windows for instance. Or any other ZIP tool. It should contain all these files.

haven't been able to pull it off with 7zip or winrar :(

---

### Post by magomago on 2008-04-10
could you upload the relevant files?

thanks =)

---

### Post by wieman01 on 2008-04-10
Well, I cannot help you there. What you mean by saying "haven't been able to pull it off"? You cannot open it?

---

### Post by wieman01 on 2008-04-10
> **magomago said:**
> could you upload the relevant files?

thanks =)
I don't have them, because I am sure I have a different device. Plus I don't if that would be legal.

---

### Post by magomago on 2008-04-10
> **wieman01 said:**
> I don't have them, because I am sure I have a different device. Plus I don't if that would be legal.

its not relevant to post the dirvers =-= well if everyone can do that, how does it break legality?


and yes "pull it off" means I can't open them

---

### Post by wieman01 on 2008-04-10
Did you do right-click, and the choose "open with"? That should do the trick in Windows. Then select "WinRar" or "WinZIP".

---

### Post by magomago on 2008-04-10
> **wieman01 said:**
> Did you do right-click, and the choose "open with"? That should do the trick in Windows. Then select "WinRar" or "WinZIP".

yup

---

### Post by wieman01 on 2008-04-10
And it say cannot open file?

Another option would be to install the device using Windows and look for the corresponding files on your drive. I don't know where Windows puts them, but it needs to put'em somewhere.

---

### Post by wieman01 on 2008-04-10
Found this on MS' website:

[http://support.microsoft.com/kb/314479]("http://support.microsoft.com/kb/314479")

---

### Post by magomago on 2008-04-10
> **wieman01 said:**
> And it say cannot open file?

Another option would be to install the device using Windows and look for the corresponding files on your drive. I don't know where Windows puts them, but it needs to put'em somewhere.

the problem is i don't have an extra copy of windows...this pc with the card is linux only.

i could move it out to the other one, but its such a hasssssle

---

### Post by magomago on 2008-04-10
well thanks i'll try some more stuff tomorrow....tisbah ala kheir ;)

---

### Post by magomago on 2008-04-10
Okay so I spent more time looking at this just now. 

There is a point missing here - not all .exe are actually files that unzip.  There are some .exe files that are simply zipped files with the ability to unzip themselves.  This is why you can open them in winzip or winrar or 7zip etc etc.  

But other exes are NOT zipped files, or have their own propeitory algorithsm behind what is going on. Trying to open up any .exe in zip won't work unless its actually an encoded zip file

So I have the MSi PC60g which is based on this chipset is one of those cases (and this was mirrored by others in the thread who cannot open their specific .exe)  we can see it right here:
[http://us1.msi.com.tw/support/dvr_exe/cmu_dvr/MSI_RT6x_RT7x_1.0.0.0302.exe](http://us1.msi.com.tw/support/dvr_exe/cmu_dvr/MSI_RT6x_RT7x_1.0.0.0302.exe)

try to download that and you will see.

Now I went ahead and checked your drivers specifically for the Linksys that you posted.  Those were simply archives created with winzip that I could easily open with winrar, etc. because it was a self extracting archive.  That is why you kept repeating that we just need to open up the .exe ~ because that is what you have yourself.


So this creates another quandry for those trying the ndiswrapper method (which I would always want to emphasize as a stop gap until we can get native drivers with good quality) and do not have setup files as imply self extracting compressed files - how the he|| to get to  drivers themselves :p

I've installed the RAlink drivers on my laptop that I'm using right now (I'm not at home at the moment) but I can't seem to find the drivers and where they are stored (I'm searching at the moment but I haven't out it.  The other option (which I'll explore later) is trying to use those linksys drivers directly...but I'm honestly not sure how different the two are~ I would hope both companies are lazy and just follow a general reference board design...we'll see ;)

---

### Post by magomago on 2008-04-10
Okay excellent news =)

Things are a go!  I was right - apparently things are generic enough that they apply right across the board!

I followed ndiswrapper directions (doing it your way basically works) but I used the ATTACHED drivers to load it.  ANYONE can get these drivers by downloading the WMPG54 drivers for version 4.1 and taking out the rt61 drivers.  
It is wonderfully fast at 54MBps now.  Be forewarned - I use no protection, broadcast my SSID, and simply do a MAC lockout.  So i have no idea if this still works with WPA or WEP etc.

Hopefully in the future it will be supported out of the box, but for now I'll take ndiswrapper as that stopgap.

By the way I have a MSI PCG60 card.  

Thank you!

edit:

this is with the latest 8.04 beta as of this edit

---

### Post by wieman01 on 2008-04-11
Excellent, and thanks for letting us know. I admit, the section on unzipping the .EXE file is confusing, I might have to ramp it up a bit. But you figured it out yourself.

As for security, please use WPA. Both MAC filtering and WEP aren't secure at all, it would take an experienced Linux users 10 minutes to crack your WEP key, 10 seconds to get around MAC filtering. WPA(2) is the only way to go.

Your adapter should support WPA(2) if you have downloaded the latest driver. Give it a go.

---

### Post by blegs38552 on 2008-04-15
Ok - I downloaded the .inf and .sys files and installed the .inf file. What should I be doing with the .sys fie (rtl8185.sys)? As of now, I can get wireless only if encryption is turned completely off. Turning on either WEP or WPA results in my system locking up with CAP LOCK light flashing on and off. Only remedy is to do a hard shutdown.

Perhaps I will just have to forgo wireless for the immediate future for Linux (I dual boot and can use it with no problem in Vista). Hopefully, a reliable wireless solution will be found in the not too distant future.

Any suggestions will be appreciated.

---

### Post by wieman01 on 2008-04-16
What you do with the .INF and .SYS file? Follow my tutorial for example. Just skip this part:
> Now unzip the driver archive you have just downloaded (e.g. in your home directory):

---

### Post by blegs38552 on 2008-04-16
Following the directions to unzip, I see the following:

Now find the right driver in the resulting folder & deploy it (folder should also contain other driver files i.e. .cat, .sys):

Quote:
sudo ndiswrapper -i <your_ralink_driver>.inf  

Make sure it has installed correctly:

Quote:
ndiswrapper -l  

The output should yield something like this:

Quote:
rt2500usb : driver installed
device (13B1:000D) present (alternate driver: rt2500usb)  

Last but not least open this file...

Quote:
sudo gedit /etc/network/interfaces  

...and add these 2 lines if they are not there yet [also try without adding them if Network Manager does not pick up the card & reboot]:

Quote:
auto wlan0
iface wlan0 inet dhcp  

You can now safely delete the extracted driver files & folders. Then reboot the computer and see if you can connect using your favorite networking applet (e.g. Network Manager, WICD, Wifi Radar, etc.). 

I followed all of the steps excepting the deletion fo the files. I did receive back the message that you referred to, and see the two lines. Problem is that I am still locking up. At the risk of sounding repetitive, I still do not see any reference to installing the .sys file. I don't know if this would make a difference, but it might. Exactly what steps do I follow to install this (I am a newbie to Ubunto and Linux, but not to computers)?

---

### Post by wieman01 on 2008-04-17
No problem, this looks good so far. Ignore the .sys file, it's deployed by ndiswrapper without you even noticing it. You there is no need to install it separately.

Please issue the following commands for me and post the results:
> sudo iwlist scan
> sudo lshw -C network
Are you saying that your system locks up frequently? How often does that happen?

---

### Post by blegs38552 on 2008-04-17
neil@gatewaylaptop:~$ sudo iwlist scan
[sudo] password for neil:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

neil@gatewaylaptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:03:25:42:db:f6
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.18 duplex=full firmware=N/A ip=192.168.1.5 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:08:09.0
       logical name: wlan0
       version: 20
       serial: 00:c0:a8:d8:d9:75
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 latency=64 maxlatency=64 mingnt=32 module=r8180 multicast=yes wireless=802.11b/g

A couple of notes - when I executed these commands, I was connected through a wired (Ethernet) connect. 

You asked how frequently this occurs. Anytime I try to change my configuration to connect wirelessly to my encrypted network, or any time I try to boot when the wireless antenna is turned on, the Ethernet connection disconnected, and any form of encryption turned on.

---

### Post by Juhla Mokka on 2008-04-18
Hi 

I hope someone can help. I am a complete beginner with Linux & so have trouble reading through these threads trying to find out what's wrong.

The original problems was that my wireless connection suddenly cut out eg. bars went white after using it for a while. First it lasted about an hour but then started cutting me out after *one *minute.

I found out that I may need the Linux driver for my Ralink rt73 wireless card. I followed these instructions [http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419)

But it does not work. Just after the installation i did **ifconfig** and it showed the new **rausb0** where it used to read **wlan0**. However, I could not connect. After a re-boot the restricted drivers manager told me that the new driver is in use, but when I did **ifconfig **the **rausb0 **had disappeared and **wlan0 **was back. No internet.

Don't know what to do next?
:confused:

---

### Post by Juhla Mokka on 2008-04-18
I saw these are often asked, so posting them:

Note that rausb0 has disappeared! It was there after the installation, before re-boot.

sudo iwlist scan
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:19:E0:10:DA:68
                    Mode:Managed
                    ESSID:"censored"
                    Channel:6
                    Encryption key:on
                    Bit Rates:0 kb/s
```

sudo lshw -C network

 ```
 *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:03:0d:78:ba:00
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:19:db:9f:f8:7b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RT73STA driverversion=1.1.0.0 firmware=514(769) link=no multicast=yes wireless=RT73 WLAN


```

---

### Post by Juhla Mokka on 2008-04-18
Sorry - I have now posted a link to this question in here [http://ubuntuforums.org/showthread.php?p=4741109&posted=1#post4741109](http://ubuntuforums.org/showthread.php?p=4741109&posted=1#post4741109)

---

### Post by jaycs12 on 2008-04-24
Not sure if this is the right place but...
first using ubuntu 8.04 with wicd and have rt61 card.
this works for me...

cd ~
    mkdir ~/rt61
    cd ~/rt61
    wget [http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz)
    tar -zxvf rt61-cvs-daily.tar.gz
    cd rt61-cvs*/Module
    make
sudo modprobe -r rt61pci
    echo 'blacklist rt61pci' | sudo tee -a /etc/modprobe.d/blacklist

    sudo make install
    echo 'rt61' | sudo tee -a /etc/modules

And Edit the right parameters for your connexion

    sudo gedit /etc/network/interfaces

---

### Post by jaycs12 on 2008-04-24
Not sure if this is the right place but...
first using ubuntu 8.04 with wicd and have rt61 card.
this works for me...

cd ~
mkdir ~/rt61
cd ~/rt61
wget [http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz)
tar -zxvf rt61-cvs-daily.tar.gz
cd rt61-cvs*/Module
make
sudo modprobe -r rt61pci
echo 'blacklist rt61pci' | sudo tee -a /etc/modprobe.d/blacklist

sudo make install
echo 'rt61' | sudo tee -a /etc/modules

And Edit the right parameters for your connexion

sudo gedit /etc/network/interfaces

This also makes it possible to put your card into monitor mode!!

---

### Post by Erik. on 2008-04-25
Hi,

I have just downloaded the new ubuntu and u[graded ubuntu.
When i restart i do not have any internet at all.

I got a message that i need to install a driver to use for my wireless card but i can not install it because i do not have internet.

I downloade the files from windows and tried to install it but i have an error.

How to make it work into ubuntu 8?

---

### Post by Partyboi2 on 2008-04-25
Thanks Wiseman01 for the thread, I was able to get connected!
\\:D/

---

### Post by backupdevice on 2008-04-25
I had also problems with RT2500 drivers.

I fixed it with installing 8.04 , removing networkmanager and installing WCIP:popcorn:

---

### Post by wieman01 on 2008-04-25
I am back. Please let me know if your support requests are still valid as I won't go through all of them.

---

### Post by Erik. on 2008-04-25
Welcome back,

yeah mine is still vailid.

I am now down stairs whit my computer wired but i want to work on the wireless network.

I have installed ubuntu 8.04 today

How could i make it work for me?


Edit: what is WCIP? can i use it also?

---

### Post by ubulap on 2008-04-25
I guess backupdevice meant WICD: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) which is an alternative for Gnome Network Manager.

I haven't tried that approach with Hardy myself, though.
In my case, having a rt73 based card, the solution that worked for me with Hardy is go back to using ndiswrapper, since I have to use WPA too.

---

### Post by TiMBuS on 2008-04-25
In feisty and gutsy I could use the default serialmonkey driver that came with ubuntu as long as the router had no security on. Then when my system was setup I'd just go change to a more stable driver (which is ironically usually the latest CVS snapshot from serialmonkey, or an old driver from ralink), turn on WPA, and use 'rutilt'.

However, Hardy seems to have come with a broken driver for my rt61pci, and it likes to randomly freeze my system (with no error in the logs). This method was a good alternative, and works without a hiccup with WICD.
Thank you.

---

### Post by wieman01 on 2008-04-26
> **Erik. said:**
> Welcome back,

yeah mine is still vailid.

I am now down stairs whit my computer wired but i want to work on the wireless network.

I have installed ubuntu 8.04 today

How could i make it work for me?


Edit: what is WCIP? can i use it also?
It really depends on what wireless device you have got.

Please post the following:
> sudo lshw -C network
> sudo iwlist scan
What hardware have you got there?

---

### Post by Erik. on 2008-04-26
Hi,

I had to many problems whit 8.04 my system does not start good, i made a backup of my files and i installed 8.04 again and now i am on wired network and when you start your computer is says you need to instal drivers and i found my wireless card.
I installed the driver and when i have installed everything i will try to connect

my outputs:

```

  *-network               
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:05:06.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0f:66:1d:6e:b4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


```

```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:11:F5:FD:0B:C8
                    ESSID:""
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=90/100  Signal level=-42 dBm  Noise level=-53 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000037c93ce185
          Cell 02 - Address: 00:0F:66:51:64:39
                    ESSID:""
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=61/100  Signal level=-69 dBm  Noise level=-53 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000088e78f186


```

is all this good?

Edit:

I tried to connect whit the network manager but it does not work for me.
What do i need to install to make it work?
I am running ubuntu 8.04 now

---

### Post by wieman01 on 2008-04-26
All seems set. You should not have any problems in fact. You have a broadcom chipset, so this tutorial is of no use to you. 

However, you can try WICD. Maybe it does a better job:

[http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

---

### Post by Erik. on 2008-04-27
I downloaded and, it is a simple program.

It says i am connected to my network but when i want to load a webpage it says it can not be found.

Do i need to set something into my computer ?

---

### Post by wieman01 on 2008-04-27
> **Erik. said:**
> I downloaded and, it is a simple program.

It says i am connected to my network but when i want to load a webpage it says it can not be found.

Do i need to set something into my computer ?
Can you access your router using a browser?

---

### Post by Erik. on 2008-04-27
No i can't

When i search for an network i see it, and i also can see the signal -70dbm but when i want to connect it says i am connected and then the signal is -0dbm...

When i install the old driver should it work for me?

---

### Post by blegs38552 on 2008-04-27
Problem is still present after installing 8.04. When my wireless antenna is active on boot, I get a Kernel Panic lockup (I have a screen image of this attached).At this point, the laptop panel lights flash on and off and a hard restart u=is required. Also, since the last occurrence, the lights no longer function.




> **blegs38552 said:**
> neil@gatewaylaptop:~$ sudo iwlist scan
[sudo] password for neil:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

neil@gatewaylaptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:03:25:42:db:f6
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.18 duplex=full firmware=N/A ip=192.168.1.5 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:08:09.0
       logical name: wlan0
       version: 20
       serial: 00:c0:a8:d8:d9:75
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 latency=64 maxlatency=64 mingnt=32 module=r8180 multicast=yes wireless=802.11b/g

A couple of notes - when I executed these commands, I was connected through a wired (Ethernet) connect. 

You asked how frequently this occurs. Anytime I try to change my configuration to connect wirelessly to my encrypted network, or any time I try to boot when the wireless antenna is turned on, the Ethernet connection disconnected, and any form of encryption turned on.

---

### Post by bcrowell on 2008-04-27
I had my rt61 working in gutsy with ndiswrapper, but upgrading to hardy broke it. The output from ndiswrapper -l looks normal, and shows that the rt61 driver is installed. Can anyone suggest what to try next?

TIA!

---

### Post by wieman01 on 2008-04-28
> **bcrowell said:**
> I had my rt61 working in gutsy with ndiswrapper, but upgrading to hardy broke it. The output from ndiswrapper -l looks normal, and shows that the rt61 driver is installed. Can anyone suggest what to try next?

TIA!
Please post:
> sudo iwlist scan
> sudo lshw -C network
> sudo cat /etc/network/interfaces
> sudo ndiswrapper -l

---

### Post by wieman01 on 2008-04-28
> **Erik. said:**
> No i can't

When i search for an network i see it, and i also can see the signal -70dbm but when i want to connect it says i am connected and then the signal is -0dbm...

When i install the old driver should it work for me?
I don't know what's going on... What older driver are you referring to?

---

### Post by Erik. on 2008-04-28
I don't have any drivers installed yet, i made a clean install of 8.04.
Should i follow the thread of the bcm43xx driver?

---

### Post by thywolf on 2008-04-28
I am wondering if what I am experiencing now in Server 8.04 using native (i mean non-ndis) rt2500 drivers is caused by a buggy support of rt2500, or by something else. 
Namely, I am able to startup my wifi card, "connect" to network with WPAPSK/TKIP, but the symptom is that the ACK led on my PCMCIA card is always on, which is unusual. No communication is possible between my laptop and the router, although my router sees the wifi card as connected, and shows the signal strength constantly.

Suprisingly, the whole thing (same settings of wpa-supplicant) were working fine on FreeBSD 7.0, which I was testing recently - without any problems. Plz plz plz, Ubuntu devs.... make the Ralink wifis to work in Ubuntu... like they do in FreeBSD... Both Ralink and Ubuntu are very popular where I live.... ;)

I will switch to ndiswrapper soon, anyway.

Regards,
Chris

---

### Post by Erik. on 2008-04-28
I have the same problem, my led on the wireless card is always on and not blinking.
My router does not see my computer when it says it is connected.
I want to now it the driver + n dis wrappers works on 8.04 i can do i try.
I am using the bcm43xx chip

---

### Post by wieman01 on 2008-04-28
> **Erik. said:**
> I don't have any drivers installed yet, i made a clean install of 8.04.
Should i follow the thread of the bcm43xx driver?
Yes, this would be an option indeed.

---

### Post by Erik. on 2008-04-28
ok, i will try and i will let you know if it helped...

---

### Post by Erik. on 2008-04-28
ok,

I followed this thread:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

When i rebooted my led blinked 2 or 3 times, now i do not have wireless internet and my led is always on.
Whats my problem now?

My output:

```
erik@erik-desktop:~$ lshw -C network 
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:05:06.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0f:66:1d:6e:b4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=172.27.183.222 multicast=yes wireless=IEEE 802.11g


```

---

### Post by wieman01 on 2008-04-28
Erik., 

Please open a new thread as this tutorial is for Ralink based adapters only.

---

### Post by Erik. on 2008-04-28
oh ok
thanks for helping me here!

---

### Post by studentz on 2008-04-28
:confused:I'm stuck, the device is (RT2500 802.11g Cardbus/mini-PCI), driver ndiswrapper is on , but I cannot connect to the router. I tried: router without security instead of wpa, kernel pci=noacpi, wicd instead of network manager app please help me out.
> 
Ubuntu 8.04 (hardy)
2.6.22-14-generic 

lshw -C network
  *-network:0             
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: wlan0
       version: 01
       serial: 00:11:09:0f:1e:ae
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt2500 driverversion=1.45+Ralink Technology, Inc.,06/ latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:40:45:27:32:14
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=192.168.2.106 latency=64 maxlatency=8 mingnt=3 module=via_rhine multicast=yes

sudo ndiswrapper -l
rt2500 : driver installed
	device (1814:0201) present (alternate driver: rt2500pci)
	
iwlist scan
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
wlan0     No scan results



---

### Post by wieman01 on 2008-04-28
studentz, 

Please issue:
> sudo iwlist scan
Sometime this command does not yield any results if you don't add "sudo". 

Are you on a 64-bit system? Have you got the right drivers? Everything looks OK in fact...

---

### Post by wieman01 on 2008-04-28
studentz, 

Please issue:
> sudo iwlist scan
Sometime this command does not yield any results if you don't add "sudo". 

Are you on a 64-bit system? Have you got the right drivers? Everything looks OK in fact...

---

### Post by studentz on 2008-04-28
Hi weiman01.

My laptop is 32-bit before I upgraded to hardy my wireless worked fine.
I post the rest of inf.

Thanks

> 
 sudo iwlist scan
[sudo] password : 
lo        Interface doesn't support scanning.

wlan0     No scan results

eth0      Interface doesn't support scanning.


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

auto eth0
#iface eth0 inet dhcp
auto wlan0


---

### Post by bcrowell on 2008-04-28
(((Oops -- I meant to post this as a reply to [http://ubuntuforums.org/showpost.php?p=4819607&postcount=487](http://ubuntuforums.org/showpost.php?p=4819607&postcount=487) . I messed up and posted it at the end of the thread, so now I'm editing to add this note.)))

Thanks for the reply!

Now it's working, but I'm darned if I know why! The following is a listing of the output of the commands you suggested. This is obviously a lot less interesting than a listing under the condition where it's not working. If it fails again in the future, I'll post again.

```
root@fluffy:/home/icrowell# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1D:7E:20:35:3A
                    ESSID:"crangelos"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/100  Signal level=-70 dBm  
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000090e6a041125
          Cell 02 - Address: 00:1B:2F:49:64:8A
                    ESSID:"JOSIAH080507"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=47/100  Signal level=-76 dBm  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000002a16734e144

root@fluffy:/home/icrowell# lshw -C network
  *-network:0             
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: wmaster0
       version: 00
       serial: 00:1c:10:e3:5c:85
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.1.104 latency=32 module=rt61pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 13
       bus info: pci@0000:00:13.0
       logical name: eth0
       version: 10
       serial: 00:1d:7d:20:30:0a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s

root@fluffy:/home/icrowell# cat /etc/network/interfaces
auto lo
iface lo inet loopback
root@fluffy:/home/icrowell# ndiswrapper -l
rt61 : driver installed
	device (1814:0301) present (alternate driver: rt61pci)

```

---

### Post by wieman01 on 2008-04-29
> **studentz said:**
> Hi weiman01.

My laptop is 32-bit before I upgraded to hardy my wireless worked fine.
I post the rest of inf.

Thanks
OK then. Could you point me to the driver that you have used? Just want to check something.

---

### Post by studentz on 2008-04-29
I use the driver shipped by the laptop manufacturer (last version WinXP) 
Here is the drive inf
> 
~$ dmesg | grep rt2500
[   63.403908] ndiswrapper: driver rt2500 (Ralink Technology, Inc.,06/10/2004, 2.02.06.0000) loaded
[   63.654592] wlan0: ethernet device 00:11:09:0f:1e:ae using NDIS driver: rt2500, version: 0x20001, NDIS version: 0x500, vendor: 'IEEE 802.11g Wireless Card.', 1814:0201.5.conf



---

### Post by wieman01 on 2008-04-29
studentz, 

Really beats me... :-(

---

### Post by studentz on 2008-04-30
:confused:Hi weiman01

Here is something interesting. I use my old pcmcia network card with a similar chipset Ralink rt2500 and it works. Unfortunately, I cannot  use my pcmcia port with my nice sound card. I post all inf.

Other forum suggests to use the serial monkey rt2500 driver and blacklist the alternative driver rt2500pci which comes with the kernel. I tried to blacklist rt2500pci using "echo 'blacklist rt2500pci' | sudo tee -a /etc/modprobe.d/blacklist".This command add the line "blacklist rt2500pci" to  blacklist, but when you ask for ndiswrapper -l you still can see the alternative driver, and the wlan0 did not work.

Any suggestions?

Thanks for your time and support.


> 

~$ lspci -nn | grep Network
00:09.0 Network controller [0280]: RaLink RT2500 802.11g Cardbus/mini-PCI [1814:0201] (rev 01)
02:00.0 Network controller [0280]: RaLink RT2500 802.11g Cardbus/mini-PCI [1814:0201] (rev 01)

~$ dmesg | grep rt2500
[   59.360469] ndiswrapper: driver rt2500 (Ralink Technology, Inc.,06/10/2004, 2.02.06.0000) loaded
[   59.611257] wlan0: ethernet device 00:11:09:0f:1e:ae using NDIS driver: rt2500, version: 0x20001, NDIS version: 0x500, vendor: 'IEEE 802.11g Wireless Card.', 1814:0201.5.conf
[  288.764000] wlan1: ethernet device 00:50:18:2e:6a:83 using NDIS driver: rt2500, version: 0x20001, NDIS version: 0x500, vendor: 'IEEE 802.11g Wireless Card.', 1814:0201.5.conf


~$ lshw -C network

*-network
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan1
       version: 01
       serial: 00:50:18:2e:6a:83
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt2500 driverversion=1.45+Ralink Technology, Inc.,06/ ip=192.168.2.108 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g


  *-network:0             
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: wlan0
       version: 01
       serial: 00:11:09:0f:1e:ae
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt2500 driverversion=1.45+Ralink Technology, Inc.,06/ latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:40:45:27:32:14
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=64 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
       
       
~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:45:27:32:14  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:510 errors:0 dropped:0 overruns:0 frame:0
          TX packets:243 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:97102 (94.8 KB)  TX bytes:36866 (36.0 KB)
          Interrupt:18 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1261 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1261 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:178041 (173.8 KB)  TX bytes:178041 (173.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:09:0f:1e:ae  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Memory:febfe000-fec00000 

wlan1     Link encap:Ethernet  HWaddr 00:50:18:2e:6a:83  
          inet addr:192.168.2.108  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::250:18ff:fe2e:6a83/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3090 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3047 errors:0 dropped:2 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2961200 (2.8 MB)  TX bytes:421361 (411.4 KB)
          Interrupt:16 Memory:24000000-24002000 

~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:45:27:32:14  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:510 errors:0 dropped:0 overruns:0 frame:0
          TX packets:243 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:97102 (94.8 KB)  TX bytes:36866 (36.0 KB)
          Interrupt:18 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1261 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1261 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:178041 (173.8 KB)  TX bytes:178041 (173.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:09:0f:1e:ae  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Memory:febfe000-fec00000 

wlan1     Link encap:Ethernet  HWaddr 00:50:18:2e:6a:83  
          inet addr:192.168.2.108  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::250:18ff:fe2e:6a83/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3090 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3047 errors:0 dropped:2 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2961200 (2.8 MB)  TX bytes:421361 (411.4 KB)
          Interrupt:16 Memory:24000000-24002000 
     
~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

wlan1     Scan completed :
          Cell 01 - Address: 00:18:39:72:57:AD
                    ESSID:"TEST"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:60/100  Signal level:-57 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                        



---

### Post by wieman01 on 2008-04-30
Serialmonkey's driver is an option, however, it does not work at all with Network Manager. You will have to configure your network from command line.

If you decide to use their driver, then you have to remove 'ndiswrapper' entirely. Just remove it using Synaptics as it will confict with the other driver.

---

### Post by studentz on 2008-05-01
Hi weiman01

My subliminal question was How I can blacklist alternative drive rt2500pci so I only will have rt2500 drive working.

Thanks

---

### Post by wieman01 on 2008-05-01
You can just open the blacklist by issuing:
> sudo gedit /etc/modprobe.d/blacklist
Then add:
> rt2500pci
That should do. Just play around with the blacklist.

---

### Post by samm71790 on 2008-05-01
Hello everyone. I am running Hardy 64 with a rt2500pci on a asus m2n-e sli.

The good news is out of the box I could connect to my wpa 1/2 tkip/aes network! I had upgraded from gutsy 64 to hardy. And after messing with wcid and trying to reinstall gnome network manager I messed up everything pretty badly and was getting some HAL initialization error. 

Well I now have a fresh install of hardy that I am going to treat very gently now. The problem is that I am maxing out at 30 kb/s on all networking things combined(media streaming from my media server, internet, everything). I know it is not my modem (I'm downloading things at 800 kb/s on my torrent box...)

My router is a wrt54gl with tomato 1.19(most recent i believe) on it.

While I realize I am way ahead of some as far as out of the box working... I really don't want to copy all of my hd movies to my computer and would LOVE to be back up to my wonderful xp wireless speeds.

I am a complete noob on Ubuntu and would love to keep using it as my desktop (i even got all my games working under wine!!!) so please help me find a way around this problem and get it all up to speed... i dont want something this minor to force me back to windows. 

let me know what you want me to pull up in terminal if you want to see some settings. Also if the windows driver wrapper is my best bet and i should just follow the guide let me know, but if it is already sortof working that seams possibly counter productive.

---

### Post by wieman01 on 2008-05-02
samm71790,

As far as I can tell you are one of the lucky ones as your adapters works out of the box. As for your performance issues, all I can advise is that you try this tutorial and use "ndiswraper" rather than the orginial driver.

Problem is that you are on 64-bit which is a headache for some. You will have to get a copy of the **64-bit XP drivers** in order for this tutorial to work. Will that be a problem?

---

### Post by defenestratos on 2008-05-02
I run Hardy 64 and I followed the instructions on my Laptop with integrated RT2500 chip.
Works great until I try to hibernate when it tells me I am attempting to run a 32 bit driver on a 64 bit kernel. You don't need to be Sherlock Holmes to work out what the problem is...Is there a way around this, because on resume I have no wireless even though Wiradar sees the network.

---

### Post by wieman01 on 2008-05-02
Have you not deployed the 64-bit version of the driver? Would that solve the problem perhaps?

---

### Post by defenestratos on 2008-05-03
> **wieman01 said:**
> Have you not deployed the 64-bit version of the driver? Would that solve the problem perhaps?

As far as I am aware there is no 64 bit driver for my device. I should have a bit more of a look though. Doesn't Ndswrapper convert 32 to 64 as well?

Actually there is an abundance of them. I followed your how to with the 64 bit windows driver and all works complete with hibernate/suspend.

---

### Post by Silent Ninja on 2008-05-03
> **defenestratos said:**
> As far as I am aware there is no 64 bit driver for my device. I should have a bit more of a look though. Doesn't Ndswrapper convert 32 to 64 as well?

Actually there is an abundance of them. I followed your how to with the 64 bit windows driver and all works complete with hibernate/suspend.

I've an MSI 670 Notebook with a RaLink RT61 card (64bits ubuntu) 

I've tried to install the Windows drivers following this tutorial and I've tried a 32bits XP driver, a 64bits Vista driver, they've all installed correctly, but when I reboot the wlan0 device dissapear, so I'm guessing it doesn't work.

Anybody has made a RaLink Wireless card work with 64bits ubuntu?

---

### Post by wieman01 on 2008-05-04
> **defenestratos said:**
> As far as I am aware there is no 64 bit driver for my device. I should have a bit more of a look though. Doesn't Ndswrapper convert 32 to 64 as well?

Actually there is an abundance of them. I followed your how to with the 64 bit windows driver and all works complete with hibernate/suspend.
So problem solved? :-)

---

### Post by defenestratos on 2008-05-04
> **wieman01 said:**
> So problem solved? :-)


Problem solved!! Thank you!

---

### Post by ricardisimo on 2008-05-10
I'm assuming everyone else had the same experience I did, and that Hardy has not, in fact, solved the problem. Certainly, the LiveCD has zero connectivity. However, I got an email update from Launchpad saying the following:
> Marking this "Fix Released" as Stefan's patch is available in linux-
backports-modules:

linux-backports-modules-2.6.24 (2.6.24-16.14) hardy; urgency=low

  [Stefan Bader]

  * Added rt2x00 driver from serialmonkey.org
    - LP: #134660
Is this true? If so, how do I get a hold of the "fix" before do a fresh install of Hardy - after which install I won't have a connection at all. I realize this is kind of off-topic, and if I were smarter or braver I'd just get ndiswrapper up and running as per Wieman's tutorial. Sadly, I'm a slow-witted coward who's waited two releases for someone else to fix my problems, and would like to know if it's finally been done. Thanks for any help anyone can give.

---

### Post by The Helpful Hobo on 2008-05-11
Can someone help me with which card I have? I've installed ndiswrapper already. I have the card...
```
Realtek RTL8101E Family PCI-E
Realtek RTL8187B Wireless 802.2.11G
```

And from this list...
```
rt2500usb
rt2500pci
rt2500
rt2570
rt73usb
rt73pci
rt73
rt61usb
rt61pci
rt61
rt2x00usb
rt2x00lib
```

Help would be appreciated. Thanks in advance.

---

### Post by wieman01 on 2008-05-11
> **The Helpful Hobo said:**
> Can someone help me with which card I have? I've installed ndiswrapper already. I have the card...
```
Realtek RTL8101E Family PCI-E
Realtek RTL8187B Wireless 802.2.11G
```

And from this list...
```
rt2500usb
rt2500pci
rt2500
rt2570
rt73usb
rt73pci
rt73
rt61usb
rt61pci
rt61
rt2x00usb
rt2x00lib
```

Help would be appreciated. Thanks in advance.
Good question. Since this is a Realtek wireless adapter, I have no clue really. But you can run this & post the results:
> sudo lshw -C network
The last line ought to tell you which driver is being used.

---

### Post by tragicglee on 2008-05-16
I have a D-Link g122 USB adapter, rev b1 (rt2570/rt2500usb). To some extent, this works out of the box on Gutsy (speed/stability are non-existent, network-manager goes nuts, and then there's the whole 'ew, no WPA2' thing). I managed to get things working flawlessly using the ndiswrapper method and manual configuration in the past and was using that for months without an issue, until two days ago. I booted into WinXP for a bit, and my adapter's refused to work with ndiswrapper since. This has happened in the past but it's usually resolved with 2-3 reboots. I've seen a few others with the same problem in the past, all using USB adapters, all running into it after using Windows.

wlan1's listed in ifconfig but it's not associating with my AP, and the LEDs aren't lighting up. I'm relatively sure that the hardware's fine b/c, while it's not working with ndiswrapper, it has since worked with XP and Ubuntu x4 (Hardy Live CD -> Hardy install -> Feisty Live CD -> fresh Feisty install, all using the native driver. It seemed to be okay under Hardy, but I really dislike Hardy for some reason). I tried  ndiswrapper on my fresh install (using the exact same method and drivers I used original installation) and am having the same issue. rt2500usb, rt2750 and rt2x00 are blacklisted.

ndiswrapper -l output
```
netrtusb : driver installed
        device (2001:3C00) present (alternate driver: rt2500usb)
```

ifconfig output:
```
Link encap:Ethernet  HWAddr 00:15:E2:44:7X:X0
UP BROADCAST MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txquelen:1000
RX bytes:0 {0.0b)  TX bytes:0 (0.0b)
```

sudo iwlist scan (truncated)
```
Cell 02 - Address: XX:XX:XX:XX:XX:XX
ESSID:"My Place"
Protocol:IEEE 802.11b 
Mode: Managed
Frequency: 2.417 GHz (Channel 2)
Quality: 100/100 Signal level:-27 dBm  Noise level: -96dBm
Encryption key: on
Bit Rates: 1 Mb/s; 2MB/s; ... 54Mb/s
Extra: bcn_int=100
Extra:atim=0
IE: WPA Version 1
    Group Cipher: WEP-40
    Pairwise Ciphers (2) : TKIP WEP-40
```

/etc/network/interface contents:
```
auto wlan1
iface wlan1 inet dhcp
wireless-essid MyPlace
pre-up wpa_supplicant -Bw -Dwext -iwlan1 -c/etc/wpa_supplicant.conf 
post-down killall -q wpa_supplicant
```

If anyone has any ideas, I'd be grateful for the help. Right now,  my options seem to be: go wired at the expense of my other wireless devices; use WinXP, or rereinstall Gutsy and suffer with the native drivers. None of these are really viable, let alone appealing. This is doubly frustrating because I only went into XP so I could back things up and totally remove the native install. If I was slightly more paranoid, I'd say it knew and decided to sabatoge me.

---

### Post by wieman01 on 2008-05-17
tragicglee, 

This is so weird, have heard of it before. Could you please post this as well:
> sudo lshw -C network

---

### Post by tragicglee on 2008-05-17
```
sudo lshw -C network
 *-network               
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth0
       version: 03
       serial: 00:11:11:e4:9c:1a
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=full firmware=N/A ip=74.76.203.159 latency=64 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:15:e9:33:8d:a5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netrtusb driverversion=1.52+D-Link,06/30/2004, 1.02.00. link=no multicast=yes wireless=IEEE 802.11g

```

---

### Post by tragicglee on 2008-05-17
> **wieman01 said:**
> tragicglee, 

This is so weird, have heard of it before.

It's. Absolutely. Maddening! Somehow, it'd almost be easier to deal with if it happened every time I booted into XP, or if it happened after booting into another distro. But no, only XP. And there's never anything abnormally wrong with those XP sessions. I've seen somebody suggest it's a problem with hibernate/suspend, but I don't do either.

It's working now. I'm going to check my other 7.10 install later and see if it's also working there. If it isn't, I'll assume I did something right with this one, and try to figure out exactly what, so I can post the info on the off chance it will help anyone who runs into this at some point. 

Thanks for being willing to help, wieman01. You're a saint :)

---

### Post by wieman01 on 2008-05-18
> **tragicglee said:**
> It's. Absolutely. Maddening! Somehow, it'd almost be easier to deal with if it happened every time I booted into XP, or if it happened after booting into another distro. But no, only XP. And there's never anything abnormally wrong with those XP sessions. I've seen somebody suggest it's a problem with hibernate/suspend, but I don't do either.

It's working now. I'm going to check my other 7.10 install later and see if it's also working there. If it isn't, I'll assume I did something right with this one, and try to figure out exactly what, so I can post the info on the off chance it will help anyone who runs into this at some point. 

Thanks for being willing to help, wieman01. You're a saint :)
Thanks, mate. :-)

Wipe out XP... That's the best advice I can give. Lol!

---

### Post by Scoobylu on 2008-05-19
I'm a total noob when it comes to Linux; I only installed it yesterday.  I can't seem to get my wireless internet to work.  I found this tutorial but, because I'm such a noob, am unable to follow it.  First of all, what's "Synaptic/Adept?"  Then, what am I supposed to do with those lines under quote?  Any help would be great!  :)  The wireless card/connection isn't showing up at all in Networking.  I have a Linksys WMP54GX Wireless G PCI Adapter with SRX.

---

### Post by unutbu on 2008-05-19
Hello Scoobylu, welcome to Ubuntu. (Hey, that rhymes!)
You might want to try the steps from one of these guides:

[https://help.ubuntu.com/8.04/internet/C/troubleshooting.html](https://help.ubuntu.com/8.04/internet/C/troubleshooting.html)
[http://ubuntuforums.org/showthread.php?t=621088](http://ubuntuforums.org/showthread.php?t=621088) (Google "WMP54GX Ubuntu")

If you have problems, I suggest posting on the second thread mentioned above. That one is specifically about the WMP54gx. It looks like a number of of posters report success with bmullan's directions, so it looks hopeful that things should work out for you too.

PS. According to [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/), you have an Airgo networks chipset. This thread is about cards with the RT2500 chipset. So it's probably a good thing you didn't go very far with weiman01's instructions.

---

### Post by Cliste on 2008-05-20
Somewhat very similar to Scoobylu I'm also a complete noob- enter problem, I've tried to get my wireless card running using the ndiswrapper, but if you look at the attached picture it says that it cannot be installed on my Pc for some reason... Any ideas,:confused:

Thanks

---

### Post by wieman01 on 2008-05-20
> **Cliste said:**
> Somewhat very similar to Scoobylu I'm also a complete noob- enter problem, I've tried to get my wireless card running using the ndiswrapper, but if you look at the attached picture it says that it cannot be installed on my Pc for some reason... Any ideas,:confused:

Thanks
Open the package manager... called Synaptic. You will find it there as well.

---

### Post by Cliste on 2008-05-20
> **wieman01 said:**
> Open the package manager... called Synaptic. You will find it there as well.

I love the optimism... see attached, when I searched it it doesn't show..

Basically it's not installing on my Pc for whatever reason, any idea why, another way of trying or another wrapper

Thanks wieman...:)

---

### Post by unutbu on 2008-05-20
I think the package you need is called 
ndiswrapper-utils-1.9.

If Synaptic does not work, you could open a terminal and type

```
sudo apt-get install ndiswrapper-utils-1.9
```

If that does not work, post any error messages from the line above and, in addition, the output of

```
cat /etc/apt/sources.list
```

---

### Post by Cliste on 2008-05-20
Here she comes:

for sudo apt-get install ndiswrapper-utils-1.9 we get:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-utils-1.9
```

And for cat /etc/apt/sources.list we get:
```
ciaran@ciaran-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ie.archive.ubuntu.com/ubuntu/ hardy main restricted multiverse
deb-src http://ie.archive.ubuntu.com/ubuntu/ hardy restricted main universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ie.archive.ubuntu.com/ubuntu/ hardy-updates main restricted multiverse
deb-src http://ie.archive.ubuntu.com/ubuntu/ hardy-updates restricted main universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ie.archive.ubuntu.com/ubuntu/ hardy universe
deb http://ie.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ie.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://ie.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu hardy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu hardy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu hardy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe
deb http://ie.archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe
# deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
```

---

### Post by unutbu on 2008-05-20
Edit: Hold on... 
ie.archive.ubuntu.com has what you need. I'm not sure why your sources.list was not working. Your .deb is right here:
[http://ie.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/](http://ie.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/)

You may not want to follow my instructions below. There may be a way to get ie.archive.ubuntu.com working...
------------------------------------------------------------
Go to [http://packages.ubuntu.com/hardy/i386/ndiswrapper-utils-1.9/download](http://packages.ubuntu.com/hardy/i386/ndiswrapper-utils-1.9/download)

You'll see a list of archive mirror sites. You can test how fast is your connection is to ge.archive.ubuntu.com, for example, by typing

```
ping -c4 ge.archive.ubuntu.com
```

Test a few until you are satisfied. Then edit your sources.list:

```

cd /etc/apt
cp sources.list sources.list.bak
gksudo gedit sources.list
```

and add a line like

```
deb http://ge.archive.ubuntu.com/ubuntu hardy main
``` 

Save and exit. At the terminal, you then type

```
sudo apt-get update
sudo apt-get install ndiswrapper-utils-1.9

```

I don't see ie.archive.ubuntu.com in the list of mirrors, so once you find a mirror which is good for you, you might want to edit your sources.lst in a number of places, adding the new mirror everywhere you see ie.archive.ubuntu.com. That way in the future hopefully you won't have this problem (not with Synaptic either). Every time you make a change to sources.lst, re-run

```
sudo apt-get update
```

---

### Post by Cliste on 2008-05-20
That'd be great, but I'm interneting through XP, as such can I download and then copy it over?

Edit: I'm guessing changing from http:\ might work?

---

### Post by unutbu on 2008-05-20
Oh. Stupid me.
Open Synaptic and check the box which enables installation of packages from CD. Stick in your LiveCD. ndiswrapper is on there.

If for some reason, that does not work, you can download the *.debs from the link in my previous post. Save them on your windows partition. Then boot up Ubuntu, mount your windows partition, copy the *.debs over, and then install by double-clicking or by typing

```
sudo dpkg -i ndiswrapper-common_1.50-1ubuntu1_all.deb

sudo dpkg -i  ndiswrapper-utils-1.9_1.50-1ubuntu1_*.deb
```

You'll need a .deb that says i386 or amd64, depending on your hardware. And you'll need 
2 .debs:

[ndiswrapper-common]("http://ie.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.50-1ubuntu1_all.deb")
and ([ndiswrapper-utils-1.9 for amd64]("http://ie.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.50-1ubuntu1_amd64.deb") or 
[ndiswrapper-utils-1.9 for i386]("http://ie.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb")).

All-in-all, this is more complicated than using the LiveCD. I'd try that first.

---

### Post by Cliste on 2008-05-20
I got it off Wubi.... no Live CD :(

---

### Post by unutbu on 2008-05-20
Okay, download the .debs that are linked in my previous post onto your hard drive or (better yet) a USB stick. Then copy them into your Wubi partition.

---

### Post by Cliste on 2008-05-20
Hmmm More Fricking errors (see pic)

Any completely foolproof methods(!?) starts to miss the old .exe files, begins drifting back to windows :D

---

### Post by unutbu on 2008-05-20
ndiswrapper-utils-1.9 depends on ndiswrapper-common being installed first.

---

### Post by Cliste on 2008-05-22
Ah sorry, I didn't see that, listen thanks, it's working now, it only picks up my neighbours wireless now though, hmmm, I'll look at it before asking anything though. Thanks :D

---

### Post by Cliste on 2008-05-23
Right, some progress: 

```
ciaran@ciaran-desktop:~$ iwconfig
lo        no wireless extensions.
wmaster0  no wireless extensions.
wlan0     IEEE 802.11g  ESSID:""  
Mode:Managed  Frequency:2.437 GHz  Access Point: 00:05:5D:25:9B:F4   
Tx-Power=27 dBm   
Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
Link Quality:0  Signal level:0  Noise level:0
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0   Missed beacon:0
ciaran@ciaran-desktop:~$ sudo ndiswrapper -l
[sudo] password for ciaran:
rt2500 : driver installed
rt61 : driver installed
device (1814:0301) present (alternate driver: rt61pci)
ciaran@ciaran-desktop:~$
```

Now I've tried to delete, and skip the alternate driver as advised [here]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,troubleshooting/")
(Ndiswrapper site) however thats not working, every time i reboot it just comes back as was

---

### Post by unutbu on 2008-05-23
Have you tried
```

sudo ndiswrapper -r rt61
```
?

---

### Post by Cliste on 2008-05-23
Thanks for the quick reply:

```
ciaran@ciaran-desktop:~$ sudo ndiswrapper -r rt61pci
[sudo] password for ciaran: 
couldn't delete /etc/ndiswrapper/rt61pci: No such file or directory
ciaran@ciaran-desktop:~$ sudo ndiswrapper -l
rt2500 : driver installed
rt61 : driver installed
	device (1814:0301) present (alternate driver: rt61pci)
```

Edit: Sorry I think its the rt61pci thats the problem, the rt61 is the one which I installed from the sitecom site...

---

### Post by unutbu on 2008-05-23
Oops, sorry. 
```
echo 'blacklist rt61pci' | sudo tee -a /etc/modprobe.d/blacklist
```
This should prevent the rt61pci module from loading at boot time.

---

### Post by Cliste on 2008-05-23
That worked so well it even stopped wireless altogether see attached, on start up no wireless, no wlan0 etc either

---

### Post by Cliste on 2008-05-23
Linux is absolutely, completely and fruitlessly DEAD to me

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/)

---

### Post by unutbu on 2008-05-23
Cliste, to get back to where you were before,

```
gksudo gedit /etc/modprobe.d/blacklist
```

Go to the last line in the file, and erase:

```
blacklist rt61pci
```
Save, Exit, Reboot.

---

### Post by Ang on 2008-05-23
Hi everyone. This will be the first time that i actually have to write something. Before this it seems i have never been alone or first with a problem. :)

Anyway. My RT2500 based mini-PCI card (built in my notebook by MSI) had an extremely poor range and i read it was almost certainly because of wrong drivers. So I followed this guide and now comes my problem:

I have two wireless cards, and after installing this driver so did I finally, at least, get a lot better range with the RT2500 card. 
But I cannot connect to my router anymore with the RT2500 based card, but it can "see" the router!?

When I'm trying to connect so will the "wireless icon" just "spin" and stay grey.

Please help. Why is my RT2500 half dead?

*edit
It appears that it works for open networks. Could it be the drivers that doesn't support security networks?

---

### Post by screwballl on 2008-06-04
My install: Ubuntu 8.04, MSI6855B or Ralink RT2560F installed in a HP ze4500 (Pavilion ze4540us). It is also setup for dual boot with XP and the wireless works perfectly under XP.
I tried the method used here and for some reason it would not let me install it this way. It would say that rt2500 is installed after  "ndiswrapper -i rt2500.inf".. but then when I checked "ndiswrapper -l" it would say rt2500 is not installed. I tried to reboot and would still not work.

So here is what I did that worked perfectly, I made sure everything was installed for ndiswrapper through Synaptic Package Manager. Then under the System area was a new Windows Drivers option, I chose that, selected my rt2500.inf and it installed it in a matter of seconds.
Within minutes I was connected to my wireless network and surfing. Granted the signal is very low when I am sitting next to the router but at least I have the option now.

---

### Post by evanct on 2008-06-11
alright, i have a WUSB54GC card with rt73(taken directly from the install cd) on feisty. i've done everything EXACTLY as detailed in the stickied thread, but it still won't work. i've installed the driver, blacklisted it, but when i type ndiswrapper -l i just get this:

rt73: invalid driver!

and i can't connect. when i try to install it again, it just tells me rt73 is already installed.

on my old computer i got this same card working with the same driver, also with feisty. idk what went wrong here, this is really frustrating

i also tried the rt73 python script, it didnt work either.

edit: nevermind, i fixed it

---

### Post by devosion on 2008-06-11
> **Cliste said:**
> That worked so well it even stopped wireless altogether see attached, on start up no wireless, no wlan0 etc either

This is exactly the same problem I am having whenever I blacklist the native driver for my ralink card, wusb54gv4. Everytime I blacklist rt2500usb wlan0 disappears. Nothing I have tried has managed to get it up again. Manual configurations, reinstallations, nothing works, and im operating on a 64bit version of Hardy. Is this a bug, or is there a fix im not seeing?

By the way my wireless is operating on the native driver, just abysmally slow even after the iwconfig 54m 'fix'. Please help.

---

### Post by devosion on 2008-06-12
Well for the moment I have given up on using a 64bit version of hardy and instead am trying to get 32bit to work with my wusb54gv4.

The good news is that now when I blacklist wlan0 doesnt disappear from iwconfig. Although the bad news is that my wireless card isnt roaming upon boot-up, and when I manually setup the information for the card in network manager it often freezes my machine. This has occured twice already. The third time I tried it didn't work at all and didn't detect my network. When I performed iwlist scan nothing came up either. Is there something I am missing? I followed the instructions exactly as they were told. Any other choices besides ndiswrapper at this point?

---

### Post by wieman01 on 2008-06-14
> **devosion said:**
> Well for the moment I have given up on using a 64bit version of hardy and instead am trying to get 32bit to work with my wusb54gv4.

The good news is that now when I blacklist wlan0 doesnt disappear from iwconfig. Although the bad news is that my wireless card isnt roaming upon boot-up, and when I manually setup the information for the card in network manager it often freezes my machine. This has occured twice already. The third time I tried it didn't work at all and didn't detect my network. When I performed iwlist scan nothing came up either. Is there something I am missing? I followed the instructions exactly as they were told. Any other choices besides ndiswrapper at this point?
The only option is the native driver or Serialmonkey's one...

---

### Post by Eulolia on 2008-06-16
> **devosion said:**
> Well for the moment I have given up on using a 64bit version of hardy and instead am trying to get 32bit to work with my wusb54gv4.

The good news is that now when I blacklist wlan0 doesnt disappear from iwconfig. Although the bad news is that my wireless card isnt roaming upon boot-up, and when I manually setup the information for the card in network manager it often freezes my machine. This has occured twice already. The third time I tried it didn't work at all and didn't detect my network. When I performed iwlist scan nothing came up either. Is there something I am missing? I followed the instructions exactly as they were told. Any other choices besides ndiswrapper at this point?

Ahh, WUSB54Gv4, just spent all day trying to get this working on the 64-bit build.

In the end this driver worked very well for me in ndiswrapper with the amd64 install:

[http://files.aoaforums.com/I2130-RT2500V3.0.1.0_for_Win2003.zip.html](http://files.aoaforums.com/I2130-RT2500V3.0.1.0_for_Win2003.zip.html)

I think this is the problem lots of people are having. The drivers on the linksys site and CD are all 32bit. 32bit drivers won't work on the 64bit kernel. These ones linked in this message are dated 2005, but they're 64 bit, and seem to work perfectly in non-roaming mode (not sure about Roaming, haven't tried).

Following the instructions at post 1 or [http://ubuntuforums.org/showpost.php?p=4373325&postcount=121](http://ubuntuforums.org/showpost.php?p=4373325&postcount=121) but using the inf from the amd64 link above instead of the linksys should work fine for anyone trying to get this adapter working with x64 ubuntu.

---

### Post by Michael%S on 2008-06-18
I'm starting to give up... Ever since I brought over my main machine to my new home (in my new country) I have not been able to get online via wifi on Ubuntu. I have a Ralink RT2500 miniPCI card. I followed this guide and cannot connect. Ubuntu (well, Xubuntu now) can see the networks, whereas it couldn't before, and I once even caused Wicd to say it is connected... No dice, I still couldn't surf.

Before I tried the method described here, I tried to build rt2500-source using module-assistant... It gave me some error message and couldn't build.

Before that I was trying out a few distros before I decided to go back to the Xubuntu I know and love. The last one I tried before installing Xubuntu Hardy was Granular Linux, a Mandriva-based distro that uses apt package management... Wifi worked out of the box. So I know there is hope for me, this is just getting extremely frustrating and tiring. I am not a very experienced Linux user. I understood everything in this guide, but when I had to use module-assistant I was basically shooting in the dark for lack of understanding.

Please somebody help me.

I have two wireless routers here, connected to one another by LAN cable. one acts as gateway and one as access point... The latter is much faster, so I prefer to use it, but I can't connect to the other one either.

> $ sudo iwlist scan
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
wlan0     Scan completed :
          Cell 01 - Address: 00:19:5B:BF:8B:59
                   [neighbors' wifi]
          Cell 02 - Address: 00:13:49:A1:19:0A
                    ESSID:"ArcorWirelessLANpmKw" <--gateway
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:67/100  Signal level:-53 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:0E:2E:6F:47:2A
                    ESSID:"DIRA" <--access point
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.472 GHz (Channel 13)
                    Quality:75/100  Signal level:-48 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


> $ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
[irrelevant]
  *-network:1
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: wlan0
       version: 01
       serial: 00:50:fc:8d:38:20
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt2500 driverversion=1.52+Ralink Technology, Inc.,12/ latency=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g


Hope this helps, and I hope someone can help me sort this out.

---

### Post by unutbu on 2008-06-18
Please post

```
ifconfig
iwconfig
cat /etc/network/interfaces
```
Blank out any password/key that you have in /etc/network/interfaces. I see encryption is on on both your routers. Are you using WEP or WPA?

Also post the ip address of DIRA (the access point).

---

### Post by Michael%S on 2008-06-18
Thank you for your quick answer!
>  ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:18:dd:bf:18  
          inet addr:192.168.1.88  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:18ff:fedd:bf18/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12684 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10189 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14113895 (13.4 MB)  TX bytes:1302959 (1.2 MB)
          Interrupt:16 Base address:0x8800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:338 errors:0 dropped:0 overruns:0 frame:0
          TX packets:338 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24071 (23.5 KB)  TX bytes:24071 (23.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:50:fc:8d:38:20  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:305 (305.0 B)  TX bytes:2911 (2.8 KB)
          Interrupt:22 Memory:b3800000-b3802000 

wlan0:avahi Link encap:Ethernet  HWaddr 00:50:fc:8d:38:20  
          inet addr:169.254.5.112  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:22 Memory:b3800000-b3802000 

> $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Auto  Frequency:2.472 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=-110 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

> ~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

iface wlan0 inet static
address 192.168.1.88
netmask 255.255.255.0
gateway 192.168.1.1
wireless-key s:******
wireless-essid DIRA

iface eth0 inet static
address 192.168.1.88
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0


DIRA is located at 191.168.1.222 and uses WEP. The gateway is at 192.168.1.1, and Wicd reports it uses WEP too, but I don't remember if that is correct.
I should also note I have a laptop running Xubuntu as well, and I tried to mimic its configuration as much as possible in the network options, interfaces, Wicd, etc.

---

### Post by unutbu on 2008-06-18
Edit /etc/network/interfaces:
```
**auto wlan0**
iface wlan0 inet static
address 192.168.1.88
netmask 255.255.255.0
**gateway 191.168.1.222**
wireless-key s:******    <-- the wireless-key should be a 26 character hex string. "s:" should not be there.
wireless-essid DIRA
```

Then try 
```
sudo /etc/init.d/networking restart
```
Depending on your driver, sometimes you need to reboot instead of using the above command. For other drivers, all you need to do is remove the driver and re-insert it with 
```

modprobe -r <driver>
modprobe <driver>
```
Since you are using ndiswrapper, the `modprobe -r` command might make your system hang, so if the 
`sudo /etc/init.d/networking restart` command does not work, try powering off your machine and rebooting. Note: you may have to power off the machine. A soft reboot may not reset your wireless card to the proper state.

---

### Post by Michael%S on 2008-06-18
I purposely set the gateway to 1.1 because with 1.222 it doesn't work - neither in Windows on this machine, nor in Xubuntu on the other.
And how should I set my key? The actual key is an ascii string, 13 characters long.

---

### Post by unutbu on 2008-06-18
Michael%S, you are right that the WEP key can be 13 text digits. That would be the same as 26 hex digits.

I'm sorry I don't know enough to diagnose your problem immediately. For what they are worth, here are a few thoughts:

1) You are getting stuck at the stage of obtaining a DHCP lease. I know this because I see in your ifconfig:

> 
wlan0:avahi Link encap:Ethernet HWaddr 00:50:fc:8d:38:20
inet addr:169.254.5.112 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
Interrupt:22 Memory:b3800000-b3802000

The "avahi" indicates that wlan0 was looking for and failed to receive an IP address via DHCP. avahi steps in and assigns an ip address (169.254.5.112) but this of course does not help you communicate on the 196.168.1.* network. 

I think if you are using wicd that it does not read /etc/network/interfaces. So my guess is that wicd has been configured to look for a DHCP connection. 
Is your router also configured for DHCP? and are you going for a DHCP or a static connection?

Assuming you are going  for a DHCP connection, go to your router's "DHCP Settings" configuration page, make sure the DHCP Start Address and End Address allocate sufficient addresses to accomodate all (both?) your machines.

Another way to see that the problem involves DHCP leases is to check the output of 
```

sudo /etc/init.d/networking restart
```
The output would include something like

```
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
```

2) I tried setting up a connection with an rt2500 card using WICD and had problems. I found success after removing WICD and reinstalling network-manager  and network-manager-gnome. I don't know if it was necessary to reinstall network-manager and network-manager-gnome, however, because in the end I  got the connection working manually using 
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495).

Since WICD seems to interfere with the reading of /etc/network/interfaces, I think you would have to uninstall WICD if you want to try to connect using /etc/network/interfaces.

If you haven't tried that yet (or even if you have), perhaps it is worth a/another shot.

3) I don't have any experience with bridging, so if you say the proper thing to do is set the gateway to 192.168.1.1 instead of the bridge device, then I can only defer to your experience. 

However, I find that rather odd, since I thought the philosophy behind networking is that each device has its own routing table, and gets to decide how to interact with packets based on its routing table. 

My simplistic picture of a bridge therefore was that you send packets to the bridge (192.168.1.222) as though it were the gateway, and DIRA (the bridge) use its routing table to decide to forward all packets to the gateway (192.168.1.1). 

Maybe a more knowledgable forum reader can settle this.

---

### Post by Michael%S on 2008-06-18
Oh, when I posted the ifconfig output the card was set to DHCP. Actually I'm going for static IP, I set it up like I want it in Wicd and even managed to get Wicd to connect, but couldn't surf. Here was the ifconfig output when I was "connected"
```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:18:dd:bf:18  
          inet6 addr: fe80::2e0:18ff:fedd:bf18/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:68786 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57780 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:67407152 (64.2 MB)  TX bytes:8727511 (8.3 MB)
          Interrupt:16 Base address:0x8800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:712 errors:0 dropped:0 overruns:0 frame:0
          TX packets:712 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:42925 (41.9 KB)  TX bytes:42925 (41.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:50:fc:8d:38:20  
          inet addr:192.168.1.88  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:363 (363.0 B)  TX bytes:6718 (6.5 KB)
          Interrupt:22 Memory:b3800000-b3802000 
```
But it doesn't work any better with DHCP, and my router is certainly configured correctly for DHCP.

I will try the manual method tomorrow, it looks interesting and I haven't tried it yet. It's getting late here. :)

As for bridging, you're right in theory, but DIRA is not configured to do things automatically and cannot be configured to do so as far as I know. In fact, DIRA still thinks it's a router in Israel, where I used to live. I'm not sure I've exhausted all options as far as teaching DIRA to use the real router as its router, but my meager attempts so far have been fruitless. It also seems to work just fine the way it is when I tell the machine to use 1.1 as gateway, on all other systems and machines but this one.

Anyhow, thanks for your time and help, perhaps the guide you linked to might solve my problem after all.

---

### Post by Michael%S on 2008-06-19
It worked! The manual configuration solved the problem! (With a little tweaking of my own)
And I think I found the problem as well: for some reason[FONT=Fixedsys] route add default gw 192.168.1.1[/FONT] returned an error when I tried it - but when I put eth0 down first, it worked and the problem was solved.
So I'm guessing for some reason two interfaces can't be set to the same gateway at the same time. This might have been the reason things didn't work before either.

The odd thing is that even when I was supposedly connected but didn't have the gateway set up, I couldn't access DIRA on ...1.222 via http. It only worked after I resolved the gateway issue.

---

### Post by wieman01 on 2008-06-20
unutbu, 

Just a word of appreciation. Thanks for helping me out. I don't have much time at the moment and have limited access to the internet during the week, so I appreciate the effort you are putting into this. Big thank you.

---

### Post by unutbu on 2008-06-20
Thanks for the words of encouragement, weiman01. I was at times worried I was dragging the thread off topic. 
With that concern set aside, I'm glad to be of service.

---

### Post by EarthMind on 2008-06-22
Thank you for this guide, now I'm finally able to use my Asus wlan-167g USB adapter on Linux, this was the only reason that prevented me from keeping Ubuntu installed.

One note: restarting Ubuntu didn't make it work so I had to execute the following command in order to connect:
```
sudo /etc/init.d/networking restart
```

And I also have a question:
Now that I followed your instructions my Network Manager doesn't have a wireless connection interface anymore so how do I enable this again? I'm using 8.04

Edit: Never mind, found an even better tool called Wicd

Many thanks

---

### Post by unutbu on 2008-06-22
EarthMind, I'm not following you when you say 
"Network Manager doesn't have a wireless connection interface anymore" can you describe this further?
or post a screenshot with Applications>Accessories>Take a Screenshot. (Extra points for keeping the png file size small).

Is the problem that the connection isn't being established at boot time? and you have to run
```
sudo /etc/init.d/networking restart
```
every time manually?

If so, please post

```
cat /etc/network/interfaces
```

---

### Post by EarthMind on 2008-06-25
> **unutbu said:**
> EarthMind, I'm not following you when you say 
"Network Manager doesn't have a wireless connection interface anymore" can you describe this further?
or post a screenshot with Applications>Accessories>Take a Screenshot. (Extra points for keeping the png file size small).

Is the problem that the connection isn't being established at boot time? and you have to run
```
sudo /etc/init.d/networking restart
```
every time manually?

If so, please post

```
cat /etc/network/interfaces
```

Well what I meant is that, and I noticed that this has been mentioned before somewhere on this forum, the Network Manager applet didn't search for wireless networks anymore after I used this guide. But I also found a much better tool in that topic which is called Wicd so my problem is solved.

Thanks for the help

---

### Post by Lee_is_alive on 2008-06-29
Hi All,

I'm using a sitecom WL 181 which uses the ra2860sta.ko module. Currently everything is running fine (on a AMD 64), but every time I reboot I need to insert the module:
```

sudo insmod /opt/Ralink/os/linux/rt2860sta.ko

```
Instead of doing this manually I would this to be done on boot.
For this I created the following folder:
```

/opt/lib/`uname -r`/ralink

```
and copied the module in here. After this I added this line in /etc/modules
```

rt2860sta

```
However this is not working, and trying to use
```

sudo modprobe rt2860sta

results in:

lee@lee-desktop:~$ sudo modprobe rt2860sta
FATAL: Module rt2860sta not found.

```
Any advice on how I can make modprobe pick up my module? How can I find back the what is really the name of the module? because now I'm trying with rt2860sta, just because the module name is rt2860sta.ko. But I believe the module name could just as well be "Ralink" or something else?

I was thinking that I would need to add something in /etc/modprobe.d/aliases
or add a file linking the a name "rt2860sta" to the rt2860sta.ko module?

But as I am far from a Linux expert, I don't know what to put there.

Any help is much appreciated!!!

Cheers,

Lee

---

### Post by unutbu on 2008-06-29
Did you download the tar.bz2, [http://www.ralinktech.com.tw/data/drivers/2008_0522_RT2860_Linux_STA_v1.6.1.0.tar.bz2](http://www.ralinktech.com.tw/data/drivers/2008_0522_RT2860_Linux_STA_v1.6.1.0.tar.bz2)
from [http://web.ralinktech.com/ralink/Home/Support/Linux.html?](http://web.ralinktech.com/ralink/Home/Support/Linux.html?)

It sounds like you've run make, but maybe you have not run

```

sudo make install
```

I've looked in the Makefile, and it seems like
the "sudo make install" command should put rt2860sta.ko in
/lib/modules/`uname -r`/kernel/drivers/net/wireless/
and run depmod -a for you. 
It does not look to me like it would put the module in /opt/Ralink/os/linux, but I could be wrong -- I'm not that good at reading Makefiles.

Anyway, if you haven't already done so, try running  "sudo make install" or "sudo checkinstall -D make install" (see below). This
should make the module load at boot. If that doesn't work, then try explicitly loading the module at boot by editing /etc/modules and appending

```
rt2860sta
```

to the end of the file. (You already tried this, but your kernel won't find rt2860sta.ko unless it is somewhere in the /lib/modules/`uname -r` directory tree and depmod -a has been run.)

Let me emphasize, I don't recommend you moving the module and running depmod -a manually unless you have to, because I might be wrong. It would be best to use the tar.bz2's Makefile's "sudo make install" command or to use checkinstall:

Regarding checkinstall:

There is a problem with running make install: it potentially spews files all over the place and there is no record of where it placed what. You also have to keep the Makefile so you can run "make uninstall" if necessary. 

A better way to install files from tar.bz2s is to use the checkinstall package.
To install it:
```
sudo apt-get install checkinstall
```

Then instead of running
```

sudo make install
```
you run
```

sudo checkinstall -D make install  # creates the .deb package
dpkg --contents package.deb 	   # to see which files will be installed **before you install it**.
dpkg -i package.deb         	   # to install

```

Once you install it from a .deb, you can also use these commands:
```

dpkg --listfiles package    # to list what files have been installed
dpkg -r package             # to remove
```

---

### Post by blackaardvark on 2008-06-29
Hi guys,

I've got a Belkin 7050 v3 usb which uses the rt73 driver (ralink right?)

My problem is that my machine's loading incorrect drivers at start up.  I've tried blacklisting them but they're loaded anyway..

It's gotten to the point where i have to put in lsmod, check which one's are loaded and then do "modprobe -r rt2XXXusb" for each one EVERY TIME I START UP!

Perhaps I have the wrong blacklist file???  I do know that I have multiple firmware directories but that can't matter can it?

---

### Post by unutbu on 2008-06-29
1) Are you using Hardy 8.04? According to 
[http://ubuntuforums.org/showthread.php?p=4732883](http://ubuntuforums.org/showthread.php?p=4732883)
your wireless card should (most likely) be supported out-of-the-box.

2) Please post

```
grep -r "blacklist rt" /etc/modprobe.d
```

---

### Post by blackaardvark on 2008-06-29
I'm using 7.10 for now as I have my reservations about upgrading just yet with all the work I have planned.

Here's the result of that grep call:

```
/etc/modprobe.d/blacklist:blacklist rt73usb
/etc/modprobe.d/blacklist:blacklist rt2570
/etc/modprobe.d/blacklist:blacklist rt2500usb
/etc/modprobe.d/blacklist:blacklist rt2x00lib
/etc/modprobe.d/blacklist:blacklist rt2x00usb
grep: /etc/modprobe.d/alsa-base.save: Permission denied
/etc/modprobe.d/blacklist~:blacklist rt73usb
/etc/modprobe.d/blacklist~:blacklist rt2570
/etc/modprobe.d/blacklist~:blacklist rt2500usb
/etc/modprobe.d/blacklist~:blacklist rt2x00lib
/etc/modprobe.d/blacklist.dpkg-old:blacklist rt73usb
/etc/modprobe.d/blacklist.dpkg-old:blacklist rt2570
```

Thanks for the speedy reply, it's very much appreciated!

---

### Post by unutbu on 2008-06-29
Is it the same unwanted modules that constantly show up? If so, which ones are they?
Also, please post (modules.out and depmod.out)
```

cat /etc/modules > modules.out
grep wireless /lib/modules/`uname -r`/modules.dep > depmod.out

```
> 
I do know that I have multiple firmware directories but that can't matter can it?
Can you describe more about this? Where are the directories, and how are they tied into the system?

---

### Post by blackaardvark on 2008-06-29
When I say I have multiple firmware directories I mean that every time I update the kernel it creates a separate directory for each one, so 
```
ls /lib64/firmware 
``` 
gives me: 
```
2.6.17-10-generic  2.6.20-15-generic  2.6.22-14-generic
2.6.17-11-generic  2.6.20-16-generic 

```
I probably explained that in the wrong way :confused:

The module I need is rt73, the others (rt2x00usb,rt2500usb,rt73usb) interfere with it (they create an interface called wmaster0).  

As requested here's those output files.

---

### Post by unutbu on 2008-06-29
Remove "ndiswrapper" from /etc/modules. (Unless you have a second wireless device that requires ndiswrapper).

The ndiswrapper modules is only necessary when you are trying to use a Windows driver from within Linux. The rt73 is a native (Linux) driver, so ndiswrapper is not necessary. 

Your depmod.txt lacks a line for your rt73.ko driver. That means rt73.ko driver has not been properly installed within the /lib/modules/`uname -r` directory tree. 

Where did you get the rt73.ko driver? If you got it from a tar.gz or tar.bz2 file then it should have come with a Makefile. I have a feeling you have not yet run

sudo make install or 
sudo checkinstall -D make install

Either by luck or by virtue of having a one-track mind, I think my post
[http://ubuntuforums.org/showpost.php?p=5285199&postcount=567](http://ubuntuforums.org/showpost.php?p=5285199&postcount=567)
is relevant to your situation as well.

So in summary:
1) Remove "ndiswrapper" from /etc/modules
2) Read [http://ubuntuforums.org/showpost.php?p=5285199&postcount=567](http://ubuntuforums.org/showpost.php?p=5285199&postcount=567)
3) If unsure what to do, post an explanation/link about where you got the rt73 driver

---

### Post by wieman01 on 2008-07-05
Just an update: Also works with the **rt2860** chipset... Took me 5 minutes to set it up.

---

### Post by _El_Chojin_ on 2008-07-11
I'm using Ubuntu Hardy + Conceptronic C54Ri wich use ralink chipset and i have made this but system locks all time so what can i do, i have done a lot of how to (before make one i make a new install of ubuntu but all how to failed and i cant use ubuntu).
I'm loader rt61.inf with ndiswrapper someone has same card as me and can help me to solve this big problem.

Thanks.

---

### Post by yosumi on 2008-07-11
wow finally a guide that works. i've wasted a whole day trying to make Linksys WUSB11 v2.6 work. i should've read this thread sooner!

---

### Post by wieman01 on 2008-07-12
> **_El_Chojin_ said:**
> I'm using Ubuntu Hardy + Conceptronic C54Ri wich use ralink chipset and i have made this but system locks all time so what can i do, i have done a lot of how to (before make one i make a new install of ubuntu but all how to failed and i cant use ubuntu).
I'm loader rt61.inf with ndiswrapper someone has same card as me and can help me to solve this big problem.

Thanks.
If it continues locking up, then you will have to compile diswrapper from source. Seen this before and generally compiling solves the problem.

---

### Post by _El_Chojin_ on 2008-07-12
After do it my card is not recogniced by the system, only appears eth0 and lo with ifconfig -a :S
Maeby i mustn't load rt61.inf and i must load other driver??

---

### Post by wieman01 on 2008-07-12
> **_El_Chojin_ said:**
> After do it my card is not recogniced by the system, only appears eth0 and lo with ifconfig -a :S
Maeby i mustn't load rt61.inf and i must load other driver??
Are you on a 32-bit or 64-bit system?

You can check for the right driver here:

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/")

---

### Post by _El_Chojin_ on 2008-07-12
I was trying to install it on a 64 bit system and now i'm going to install it on a 32 bit system to try.
C54Ri is not listed on that page.

---

### Post by _El_Chojin_ on 2008-07-12
With 32 bits system works fine i think because i have been using it 2hour and didn't lock computer so i think that on 32bits system how to works good.

Could be interesting to look why this how to don't work with 64 bits system.

Thanks for the how to.

---

### Post by DieselSnorter on 2008-07-13
.

---

### Post by DieselSnorter on 2008-07-13
ME AGAIN!!!
okay, same box, but I'm trying to get a WMP54Gv4 (RT2500) PCI card working now. i still have the Belkin dongle, and that works, but I can't leave things alone.

So.currently I'm on the Belkin and life is good. But when i shut it down and disconnect it, and bring up the PCI adapter, it sees my connection, but won't connect to it.

I've installed it via Ndiswrapper (piece of cake) and pretty much just copied the config from the other adapter for my /etc/network/interfaces file.

ifconfig -a

> 
wlan1 Link encap:Ethernet HWaddr 00:1c:df:1c:49:1c
inet addr:192.168.0.107 Bcast:192.168.0.255 Mask:255.255.255.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1097 errors:0 dropped:0 overruns:0 frame:0
TX packets:730 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:911570 (890.2 KB) TX bytes:138640 (135.3 KB)

wlan2 Link encap:Ethernet HWaddr 00:12:17:a0:19:c3
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:20 Memory:fdbfe000-fdc00000

wlan2:avahi Link encap:Ethernet HWaddr 00:12:17:a0:19:c3
inet addr:169.254.6.84 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
Interrupt:20 Memory:fdbfe000-fdc00000
Wlan1 is my Belkin, Wlan2 is the Linksys.

ndiswrapper -l
> 
rt2500 : driver installed
device (1814:0201) present (alternate driver: rt2500pci)
rt73 : driver installed
device (050D:705A) present (alternate driver: rt73usb)
lspci

> 
04:06.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
Subsystem: Linksys WMP54G 2.0 PCI Adapter
Flags: bus master, slow devsel, latency 32, IRQ 20
Memory at fdbfe000 (32-bit, non-prefetchable) [size=8K]
Capabilities: <access denied> 
now, what's funny, is if I have them both scan.

iwlist scan

wlan 1 finds my AP as a G.

> 
Cell 02 - Address: 00:0F:66:E4:73:5E
ESSID:"*****"
Protocol:IEEE 802.11g
Mode:Managed
Frequency:2.442 GHz (Channel 7)
Quality:37/100 Signal level:-72 dBm Noise level:-96 dBm
Encryption keyn
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
12 Mb/s; 48 Mb/s
Extra:bcn_int=60
Extra:atim=0
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) 
But Wlan2 sees is as B
> 
Cell 01 - Address: 00:0F:66:E4:73:5E
ESSID:"*****"
Protocol:IEEE 802.11b
Mode:Managed
Frequency:2.442 GHz (Channel 7)
Quality:32/100 Signal level:-75 dBm Noise level:-96 dBm
Encryption keyn
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
12 Mb/s; 48 Mb/s
Extra:bcn_int=60
Extra:atim=0
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK 
my config file (etc/network/interfaces)

> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback



# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.

auto wlan1
iface wlan1 inet dhcp
wpa-driver wext
wpa-ssid *****
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP TKIP
wpa-group CCMP TKIP
wpa-key-mgmt WPA-PSK
wpa-psk KEY

auto wlan2
iface wlan2 inet dhcp
wpa-driver wext
wpa-ssid *****
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP TKIP
wpa-group CCMP TKIP
wpa-key-mgmt WPA-PSK
wpa-psk KEY
iwconfig

> 
wlan2 IEEE 802.11g ESSIDff/any
Mode:Auto Frequency:2.437 GHz Access Point: Not-Associated
Bit Rate:54 Mb/s Tx-Power:20 dBm Sensitivity=-120 dBm
RTS thr=2347 B Fragment thr=2346 B
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

wlan1 IEEE 802.11g ESSID:"*****" Nickname:"*****"
Mode:Managed Frequency:2.442 GHz Access Point: 00:0F:66:E4:73:5E
Bit Rate=24 Mb/s Tx-Power:20 dBm Sensitivity=-121 dBm
RTS thr=2347 B Fragment thr=2346 B
Power Managementff
Link Quality:34/100 Signal level:-74 dBm Noise level:-96 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
So, oh great mand wonderful OZ...can you figure this one out?

Thanks in advance.

Eric

---

### Post by unutbu on 2008-07-13
Are you trying to get two wireless cards connected to the same computer to both talk to the same access point (router)?

---

### Post by DieselSnorter on 2008-07-13
yes, but not at the same time....
My goal is to replace the USB with the PCI...but I need to get the PCI working first. 

I have removed the RT73 driver from Ndiswrapper to make sure there wasn't a conflict, I have completely removed it from my system, and the linksys still won't connect.  
If I use a GUI monitor (kwifimanager) I can see it connecting to the AP while it tries to get an IP, but then it drops every few seconds.  
this isn't a HUGE deal, but I would much prefer to have the on board adapter.

---

### Post by unutbu on 2008-07-13
Have you checked that your router is not doing MAC filtering, or if it is, that 00:12:17:a0:19:c3 is included in the list of accepted MACs?

Also, I notice that ifconfig returns
```

wlan2:**avahi** Link encap:Ethernet HWaddr 00:12:17:a0:19:c3
inet addr:169.254.6.84 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
Interrupt:20 Memory:fdbfe000-fdc00000
```

The presence of "avahi" indicates that wlan2 failed to receive an IP address from the router via DHCP. I'm not sure exactly why this might be, but it would probably be good to double check the DHCP settings on the router.

Finally, please post the output of 

```
route -n
```

---

### Post by DieselSnorter on 2008-07-13
I am doing MAC filitering, but I verified that it is permitted on my router. 
i've double checked it about 13 times just in case I fat fingered. 
My router isn't actually doing my DHCP, my PFSense firewall is.  just FYI. 

I'm currently connected on the RT73 (or I have no connection) so this is what is showing as valid. 

> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan1
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 wlan1


i'm going ot drop my connection, set ifconfig wlan1 down and unplug it, then bring up the Linksys and post the results after I get them and reconnect to the USB.

just for fun, I'll give you the ifup -v wlan2

> Configuring interface wlan2=wlan2 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/hostapd
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: wpa-driver wext
wpa_supplicant: /sbin/wpa_supplicant -B -P /var/run/wpa_supplicant.wlan2.pid -i wlan2 -D wext -C /var/run/wpa_supplicant
Starting /sbin/wpa_supplicant...
ioctl[SIOCSIWPMKSA]: Invalid argument
wpa_supplicant: ctrl_interface socket located at /var/run/wpa_supplicant/wlan2
wpa_supplicant: wpa-ap-scan 1 -- OK
wpa_supplicant: configuring network block -- 0
wpa_supplicant: wpa-ssid "*****" -- OK
wpa_supplicant: wpa-psk ***** -- OK
wpa_supplicant: wpa-pairwise CCMP TKIP -- OK
wpa_supplicant: wpa-group CCMP TKIP -- OK
wpa_supplicant: wpa-key-mgmt WPA-PSK -- OK
wpa_supplicant: wpa-proto RSN -- OK
wpa_supplicant: enabling network block 0 -- OK

dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.wlan2.pid -lf /var/lib/dhcp3/dhclient.wlan2.leases wlan2
There is already a pid file /var/run/dhclient.wlan2.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan2/00:12:17:a0:19:c3
Sending on   LPF/wlan2/00:12:17:a0:19:c3
Sending on   Socket/fallback
DHCPDISCOVER on wlan2 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan2 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan2 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/50firestarter
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...fail!
run-parts: /etc/network/if-up.d/50firestarter exited with return code 2
run-parts: executing /etc/network/if-up.d/avahi-autoipd
run-parts: executing /etc/network/if-up.d/avahi-daemon
run-parts: executing /etc/network/if-up.d/clamav-freshclam-ifupdown
run-parts: executing /etc/network/if-up.d/mountnfs
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/openssh-server
run-parts: executing /etc/network/if-up.d/wpasupplicant


route -n

> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 wlan2
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 wlan2


ifdown -v wlan2

> Configuring interface wlan2=wlan2 (inet)
run-parts --verbose /etc/network/if-down.d
run-parts: executing /etc/network/if-down.d/50firestarter
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...fail!
run-parts: /etc/network/if-down.d/50firestarter exited with return code 2
run-parts: executing /etc/network/if-down.d/avahi-autoipd
run-parts: executing /etc/network/if-down.d/clamav-freshclam-ifupdown
run-parts: executing /etc/network/if-down.d/wpasupplicant
dhclient3 -r -pf /var/run/dhclient.wlan2.pid -lf /var/lib/dhcp3/dhclient.wlan2.leases wlan2
There is already a pid file /var/run/dhclient.wlan2.pid with pid 8564
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan2/00:12:17:a0:19:c3
Sending on   LPF/wlan2/00:12:17:a0:19:c3
Sending on   Socket/fallback
DHCPRELEASE on wlan2 to 192.168.0.1 port 67
ifconfig wlan2 down
run-parts --verbose /etc/network/if-post-down.d
run-parts: executing /etc/network/if-post-down.d/avahi-daemon
run-parts: executing /etc/network/if-post-down.d/hostapd
run-parts: executing /etc/network/if-post-down.d/wireless-tools
run-parts: executing /etc/network/if-post-down.d/wpasupplicant
wpa_supplicant: terminating wpa_supplicant daemon via pidfile /var/run/wpa_supplicant.wlan2.pid
Stopped /sbin/wpa_supplicant (pid 8530).

---

### Post by unutbu on 2008-07-13
> i'm going ot drop my connection, set ifconfig wlan1 down and unplug it, then bring up the Linksys and post the results after I get them and reconnect to the USB.

When you switch NICs, do you shutdown the machine and powerup with wlan2 connected? 
ndiswrapper does not always behave properly when NICs are hotswapped.

If that doesn't help, I'm afraid I've run out of ideas...

---

### Post by DieselSnorter on 2008-07-15
so I tried removing the RT73 driver from Ndiswrapper, then shut down.  Removed the RT73 from my system.  Booted up, installed the linksys driver, configured the interfaces file, rebooted....same problem. 

I think the problem lies here

> Starting /sbin/wpa_supplicant...
ioctl[SIOCSIWPMKSA]: Invalid argument
wpa_supplicant: ctrl_interface socket located at /var/run/wpa_supplicant/wlan2

but I haven't the foggiest idea how to fix it.

---

### Post by unutbu on 2008-07-15
Perhaps try this thread to get wpa working: [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

### Post by wieman01 on 2008-07-19
DieselSnorter, 

Still struggling with this?
> ioctl[SIOCSIWPMKSA]
Have you got any separate wpa_supplicant file for your system? It complains about an invalid line, and I like to know which one it might be referring to.

---

### Post by ubugeek on 2008-07-19
> **_El_Chojin_ said:**
> With 32 bits system works fine i think because i have been using it 2hour and didn't lock computer so i think that on 32bits system how to works good.

Could be interesting to look why this how to don't work with 64 bits system.

Thanks for the how to.

Yes, the howto was indispensable.  The kernel rt61 module wasn't working well at all, however after installing the ndiswrapper modules and getting my 64-bit drivers installed via that, it STILL locks my 8.04.1 system up under heavy network load (specifically torrents, but today YouTube brought it down as well).

I'm running a version of Hardy at work, and it runs flawlessly.  I upgraded my Vista box to Hardy and now due to the flaky wireless drivers I can barely use it as a workstation.  I'm not giving up in the slightest but damn this is annoying. :)

---

### Post by nsegative on 2008-07-19
Hmm I'm having problems with the rt2860. I turned wlan on in the bios on my eeepc901 (wireless led is lit up blue). I installed ndiwrapper and the graphic tool. Then I put the winxp driver onto usb, put it on the desktop. LSPCI shows "01:00.0 Network cntroller: RaLink unknwon device 0781". Installing the driver in cnsole and doing ndiswrapper -l:
Installed drivers: rt2860 Invalid Driver!. 

The graphic vesion of ndiswrapper says:
rt2860. Hardware present: no. 

Any idea?

---

### Post by unutbu on 2008-07-19
nsegative, perhaps take a look at xodeus's post #6:
[http://ubuntuforums.org/showthread.php?t=708499](http://ubuntuforums.org/showthread.php?t=708499)

---

### Post by nsegative on 2008-07-19
> **unutbu said:**
> nsegative, perhaps take a look at xodeus's post #6:
[http://ubuntuforums.org/showthread.php?t=708499](http://ubuntuforums.org/showthread.php?t=708499)
Can't, this is why I am using this program. I got it to work once but reformated to a bigger hd and can't get it to work again. The eeepc has no ethernet working either, and no cd so there's no way to get the build-install package (and all the ones ive tried required tons and tons of libraries in a never ending cycle).

---

### Post by JamesRock on 2008-07-19
Just wanted to thank you for taking the time for writing such excellent and detailed instructions, they worked perfectly for me first go!

---

### Post by nsegative on 2008-07-19
Never mind I'm retarded. I installed ndiswrapper version 1.20 for both utilities and common. Once I noticed that in my usb drive I installed version 1.50 and it worked fine again. Back online on the eeepc :)

---

### Post by sputnikkk on 2008-07-20
Ok so is the ndiswrapper and windows driver method absolutely neccessary to make my working WPA2 Static IP configuration "stick" through reboots?

Wireless WPA2, Static IP, Networking WORKS ... but my issue is if i put it into NetworkManager, I have to do it at every reboot.  The computer illiterate user of this desktop will not be able to do this and other such required nonsense on reboots.

How can I make my settings stick?

---

### Post by wieman01 on 2008-07-20
> **sputnikkk said:**
> Ok so is the ndiswrapper and windows driver method absolutely neccessary to make my working WPA2 Static IP configuration "stick" through reboots?

Wireless WPA2, Static IP, Networking WORKS ... but my issue is if i put it into NetworkManager, I have to do it at every reboot.  The computer illiterate user of this desktop will not be able to do this and other such required nonsense on reboots.

How can I make my settings stick?
The only way to make it stick at the moment it configuring your WPA2 settings manually (look at my WPA tutorial in the signature). I don't think Network Manager is ready yet for static IP addresses. Sad though.

---

### Post by wesswei on 2008-07-20
> **wieman01 said:**
> The only way to make it stick at the moment it configuring your WPA2 settings manually (look at my WPA tutorial in the signature). I don't think Network Manager is ready yet for static IP addresses. Sad though.

Thanks wieman! I totally missed the second post in your wpa howto which explains this... bug.

I did this to update the links for all the rc folders.
```
sudo update-rc.d wireless-networking defaults 40
```

Thanks again.

---

### Post by sputnikkk on 2008-07-21
I solved all this BS from NetworkMisManager by installing Wicd.

I tried to be all geeky and core like a command line commando - but in the end - the Wicd GUI saved the day.

> **wieman01 said:**
> The only way to make it stick at the moment it configuring your WPA2 settings manually (look at my WPA tutorial in the signature). I don't think Network Manager is ready yet for static IP addresses. Sad though.

---

### Post by limkopi on 2008-07-28
i try this but it became worst before i did this ubuntu still can detect my wireless device and all but after i did this and reboot i dont even have a wireless option anywhere can you plz help thanks

---

### Post by unutbu on 2008-07-28
Please tell us the manufacturer/model of your wireless card, and also post the output of 
```

sudo lshw -C net
lsmod | grep ndiswrapper
ndiswrapper -l
```

---

### Post by linuxquestusa on 2008-07-28
> **wieman01 said:**
> **Dapper Drake** users should take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=192588") if this one doesn't work. This guide was tested with **Feisty Fawn**, **Gutsy Gibbon**, and **Hardy Heron**. 
--
To all **RT73** users, please also see [this post]("http://ubuntuforums.org/showthread.php?p=4732883"). Thanks to [Kiefer Rodriguez]("http://ubuntuforums.org/member.php?u=490665") for this solution.

Please post to this [Launchpad bug report]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/163020") with all of your specs, if you have problems with a Ralink based wireless adapter.

This is a simple guide for all Ralink based wireless adapters and everyone who wants to replace the Linux driver with "ndiswrapper" (e.g. because you want to make use of either [Network Manager]("http://www.gnome.org/projects/NetworkManager/") or [WICD]("http://wicd.sourceforge.net/")). 
[B]
_INSTRUCTIONS:_[/B]
[LIST]
[*]Get the latest version of the Windows driver for your card from [Linksys' website]("http://www.linksys.com/servlet/Satellite?c=L_CASupport_C1&childpagename=US%2FLayout&cid=1166859840888&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4088837314B372&displaypage=download") or from the CD that came with your device (whatever vendor). 
[/LIST]

[LIST]
[*]Install "ndiswrapper" package **with** working internet connection (Ethernet):

[/LIST]

[LIST]
[*]Install "ndiswrapper" package **without** working internet connection (alternatively, install it via Synaptic/Adept):

[/LIST]

[LIST]
[*]Load new driver module (may not be necessary any longer, but does no harm either):

[/LIST]

[LIST]
[*]Add the module to "/etc/modules" to have it load automatically:

[/LIST]

[LIST]
[*]Create alias directive:

[/LIST]

[LIST]
[*]Pick a valid Ralink driver based on the chipset of your card (you might blacklist all of them if you are not sure):

[/LIST]

[LIST]
[*]Blacklist Ralink driver:

[/LIST]

[LIST]
[*]Now unzip the driver archive you have just downloaded (e.g. in your home directory):

[/LIST]

[LIST]
[*]Now find the right driver in the resulting folder & deploy it (folder should also contain other driver files i.e. .cat, .sys):

[/LIST]

[LIST]
[*]Make sure it has installed correctly:

[/LIST]

[LIST]
[*]The output should yield something like this:

[/LIST]

[LIST]
[*]Last but not least open this file...

[/LIST]

[LIST]
[*]...and add these 2 lines if they are not there yet [COLOR="Red"][also try _without_ adding them if Network Manager does not pick up the card & reboot][/COLOR]:

[/LIST]
You can  now safely delete the extracted driver files & folders. Then reboot the computer and see if you can connect using your favorite networking applet (e.g. Network Manager, WICD, Wifi Radar, etc.). 

Feedback is - as always - appreciated.

_**CHANGE LOG:**_
30/09/2007: Minor fixes.
07/10/2007: Expanded "blacklist".
20/10/2007: Added missing part concerning "interfaces" file.
22/10/2007: Load module "ndiswrapper" at boot.
23/10/2007: Enhanced blacklist.
07/11/2007: Bug fix for Network Manager.
12/11/2007: Updated blacklist & module section.
13/01/2008: Launchpad bug report.
15/04/2008: Update for Hardy.
17/04/2008: RT73 note.
Everything works until I type the following command:

Quote:
ndiswrapper -l  

When I type this command the message comes back as

invalid driver

and that is for rt2500usb.inf, rt2500usb.sys and rt2500usb.cat.

Please help resolve this

---

### Post by unutbu on 2008-07-28
linuxquestusa, open a terminal and type

```
cd path/to/drivers     # change the path to the correct path where rt2500usb.* are located
sudo ndiswrapper -r rt2500usb
sudo ndiswrapper -i rt2500usb.inf
ndiswrapper -l
```

What is the output?
Also, if it doesn't work, please tell us what make/model wireless card you are using.

---

### Post by limkopi on 2008-07-29
> **unutbu said:**
> Please tell us the manufacturer/model of your wireless card, and also post the output of 
```

sudo lshw -C net
lsmod | grep ndiswrapper
ndiswrapper -l
```

i have a linksys WUSB54G ver.4
i did what you told me to do this is what i get
[CODE]
jordan@jordan-desktop:~$ sudo lshw -C net
[sudo] password for jordan: 
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 11
       serial: 00:01:6c:dc:d3:d8
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5751-v3.29a ip=192.168.1.68 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
jordan@jordan-desktop:~$ lsmod | grep ndiswrapper
ndiswrapper           244736  0 
usbcore               169904  9 gspca,ndiswrapper,zc0301,usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd
jordan@jordan-desktop:~$ ndiswrapper -l
rt2500usb : driver installed
	device (13B1:000D) present (alternate driver: rt2500usb)
jordan@jordan-desktop:~$ 

jordan@jordan-desktop:~$ sudo lshw -C net
[sudo] password for jordan: 
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 11
       serial: 00:01:6c:dc:d3:d8
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5751-v3.29a ip=192.168.1.68 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
jordan@jordan-desktop:~$ lsmod | grep ndiswrapper
ndiswrapper           244736  0 
usbcore               169904  9 gspca,ndiswrapper,zc0301,usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd
jordan@jordan-desktop:~$ ndiswrapper -l
rt2500usb : driver installed
	device (13B1:000D) present (alternate driver: rt2500usb)
jordan@jordan-desktop:~$ 

hope you can help thx

---

### Post by unutbu on 2008-07-29
limkopi, the good news is that the "lsmod" and "ndiswrapper -l" seem to indicate the driver is properly installed.

The bad news is lshw is not listing the wireless adapter. It's as though the computer does not recognize the Linksys has been plugged in. I'm not sure why this is so.

Would you please do the following:
Power down (not just reboot), then power up the computer, with the WUSB54G attached to a USB port
Then run:

```
lsusb        # I'm just curious to see if the WUSB54G will show up here
bzip2 -c < /var/log/messages > messages.bz2
dmesg | bzip2 -c > dmesg.bz2
```

Please post the output of "lsusb" and post messages.bz2, dmesg.bz2 as attachments.

---

### Post by Darwiesh on 2008-08-07
[B]thanQ .....
i have did all these steps my dear  :( the ndiswrapper  installed successfuly but the driver can't get any wireless connection  i tried in all ways but i failed ...the problem is when i go to administrator >>wireless i can see my driver RTL8185 and all thing is good and driver installed but the nothing goes on ....need your help 
my OSs are Ubuntu 8.04  64 bit  & Vista ultimate 32 bit[/B]

---

### Post by unutbu on 2008-08-09
Darwiesh, please post the output of 

```
ifconfig
iwconfig
iwlist scan
lsmod | grep ndis
```

---

### Post by TheMaxzilla on 2008-08-10
Ok, so I followed all of the instructions in the HOWTO, and it worked, no errors. But it won't connect to any networks. Can someone please help me resolve this problem? I don't know what other information to give you, so...

---

### Post by fooman on 2008-08-15
just dug out an old nf2 motherboard (abit nf7...*classic*).  through on an nvidia 6600gt, a gig of ram and a belkin wireless g card that had not been used in awhile.  it has the rt2500 chipset.

tried a few different approaches to get the card up to speed but had no luck.  even tried this thread once before with no luck.  decided to try from scratch, sooo...reinstalled hardy and after running the updates, i headed right to this thread *first*.

worked like a dream this time.  :)

thanks

---

### Post by HereInOz on 2008-08-17
Hi All,

I have a MSI cb56g2 PCMCIA card with a Ralink 2500 chip on it, and it worked fine in Gutsy with the standard rt2500pci driver connecting with WPA-PSK security.

Since upgrading to Hardy, the connection has been very weak (low level) and the network speed has been awful - about 20KB/s across the lan - like slow internet speeds. 

I re-installed Gutsy as a test, and it all began to work well again.   

So I installed Hardy again, and then used the "how to" to set up the adaptor using ndiswrapper and the driver downloaded from the MSI site, and while I can connect when the Access Point is set to WEP 64 bit security, I am unable to get a connection when I set the Access Point to WPA-PSK.

Has anyone experienced this, and can anyone offer any suggestions as to how I might improve the situation.

Cheers,

Alan.

---

### Post by DavidTangye on 2008-08-19
I have installed an RT2500 PC card without needing Windows drivers (nor therefore ndiswrapper) under Hardy. Its a Minitar Wireless Cardbus MN54GCB-R: Ralink RT2500 chipset (see all cards based on this chipset at [http://ralink.rapla.net/](http://ralink.rapla.net/))

Also see Chipsets supported by Linux ([http://www.wlug.org.nz/WirelessChipsets](http://www.wlug.org.nz/WirelessChipsets))
• PrismGTWirelessChipset by Intersil
• RT2x00WirelessChipset (2500) by RaLink
• Intel IPW2200
• AtherosWirelessChipset
• BroadcomWirelessChipset

for more info. There is no need to install Windows drivers for many people.

---

### Post by DavidTangye on 2008-08-19
That is interesting that the Windows driver seems to run that adapter faster. You might find that the windows driver does not support WPA. Look inside the ascii support file (.cat or .inf or something) that comes in the driver set. It indicates whether WPA is supported in its codes. You should see WEP in the definitions of its internal data codes. That is what I did with a Netgear Window driver, which confirmed that WPA was not going to work. If you do not see WPA I guess that means it is not supported in the driver.

---

### Post by leona on 2008-08-29
I am having problems with an rt2500pci card. it will list my network but it refuses to connect to it, any ideas?  I have turned off all security, so I'm sure that's not an issue.  Using 'stock' setup (no nsdiwrappers etc) yet, that how to looks complicated and last resort if I can't get it working.

---

### Post by unutbu on 2008-08-29
leona, have you tried using Network Manager? 
(Clicking on Wireless, the Properties button, uncheck the roaming mode box, enter your ESSID, and going for a DHCP connection?)

---

### Post by leona on 2008-08-29
> **unutbu said:**
> leona, have you tried using Network Manager? 
(Clicking on Wireless, the Properties button, uncheck the roaming mode box, enter your ESSID, and going for a DHCP connection?)
Hi there, thank you but yes with little joy, it doesn't even seem to be making any attempt to contact the router, I can't see it in my 'attached devices' list. very odd.

---

### Post by unutbu on 2008-08-29
To help us gather more information about your situation, please post the output of the following commands
```

ifconfig 
iwconfig
iwlist scan
cat /etc/network/interfaces
sudo /etc/init.d/networking restart

```

---

### Post by leona on 2008-08-29
> **unutbu said:**
> To help us gather more information about your situation, please post the output of the following commands
```

ifconfig 
iwconfig
iwlist scan
cat /etc/network/interfaces
sudo /etc/init.d/networking restart

```

Hi & thanks, I've got the first 3, just go and get you the rest of them :)

from lspci -nn
```

00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge [1106:3189]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8235 PCI Bridge [1106:b168]
00:0b.0 FireWire (IEEE 1394) [0c00]: NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr [1033:00f2] (rev 01)
**00:0e.0 Network controller [0280]: RaLink RT2500 802.11g Cardbus/mini-PCI [1814:0201] (rev 01)**
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.3 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 82)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8235 ISA Bridge [1106:3177]
00:11.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 50)
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 74)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV44A [GeForce 6200] [10de:0221] (rev a1)

```

From iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:6C:01:26:7A   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

from ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:0c:6e:07:18:21  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth0:avahi Link encap:Ethernet  HWaddr 00:0c:6e:07:18:21  
          inet addr:169.254.2.3  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3059 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3059 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:154824 (151.1 KB)  TX bytes:154824 (151.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0e:2e:50:64:38  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-0E-2E-50-64-38-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

From lshw -C Network
```

  *-network:0             
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: e
       bus info: pci@0000:00:0e.0
       logical name: wmaster0
       version: 01
       serial: 00:0e:2e:50:64:38
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci latency=32 module=rt2500pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:0c:6e:07:18:21
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s

```

---

### Post by leona on 2008-08-29
Ok here is the rest

iwlist scan
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

```
cat /etc/network/interfaces
```

auto lo
iface lo inet loopback

iface eth0 inet dhcp
gateway 192.168.1.200

auto eth0

```
and finally
sudo /etc/init.d/networking restart
```

[sudo] password for linux: 
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 18140
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:0c:6e:07:18:21
Sending on   LPF/eth0/00:0c:6e:07:18:21
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.200 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:0c:6e:07:18:21
Sending on   LPF/eth0/00:0c:6e:07:18:21
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]

```

I hope that is of help in working out what the problem is.

Just looking at this myself, shouldn't there be a wlan0 config in the interfaces file?  Can I add one manually?

Thank you.

---

### Post by unutbu on 2008-08-29
First: my biggest concert is the output of iwlist scan:```


wlan0     No scan results
```

Even without a connection, "iwlist scan" should return a list of all the access points (routers) your network adapter can detect. If you are not seeing anything, it means the signal between your network adapter and the router is not good. Maybe just to debug this situation, would it be possible to bring the router closer to your computer? 

No connection will ever be formed until "iwlist scan" starts returning some access points, so keep fiddling with the physical location of your network adapter and router until you start seeing something.


Second: Is your eth0 (ethernet card) plugged into anything? If not, it may be helpful to 
shut it off for now by doing two things:
```

sudo ifdown eth0

gksu gedit /etc/network/interfaces
```

Put a # sign in front of these two lines:

```

iface eth0 inet dhcp
#gateway 192.168.1.200

#auto eth0

```


Third: Network Manager seems to have failed to make a proper entry for your wlan0 wireless interface. No worries, we can do it ourselves:

Add these lines to /etc/network/interfaces:
```

auto wlan0
iface wlan0 inet dhcp
gateway 192.168.1.1       # Change 192.168.1.1 to your router's IP address
netmask 255.255.255.0
```

Fourth: reboot your computer. Do a hard power off / power on. Some network adapters seem to need this. After you get things working, you may find you do not need this, but let's do this to eliminate one otherwise hard-to-debug problem.

---

### Post by leona on 2008-08-30
Sorry for the delay in reply, that wasn't straigh forward, had noticed it had decided to disable all network devices, so I removed the interface file and set it up again via network.

So some success in that it can now 'see' at network, but it still refuses to connect to it, even though I have no security, as far as my router is telling me, its not even bothering to make a connection.

```

 iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:6C:01:26:7A
                    ESSID:"xena"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=49/100  Signal level=-66 dBm  
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000002f3c9ae5c

```

---

### Post by unutbu on 2008-08-30
Congratulations. We're making progress.

Here are some options:

[list]
[*]Try Network Manager again. It's easy, so why not?
[*]Check /etc/network/interfaces looks as described in my previous post.
[*]Type
```

sudo /etc/init.d/networking restart

```
[*]Shutdown/power up. If no connection starts automaically, type
```

sudo /etc/init.d/networking restart

```
I know it sounds silly, but sometimes it works.
[*]If none of the above work, we can try the solution taken from 
[http://ubuntuforums.org/showthread.php?t=684495:](http://ubuntuforums.org/showthread.php?t=684495:)
```

sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "xena"
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

``` If it works we can then put these commands in a script so the computer can run them at boot time for you automatically.
[/list]

---

### Post by leona on 2008-08-31
Hi there unutbu and thank you again, sadly though, this hasn't worked, it will sit there and display a network, just will not connect to it. Very odd, 
Is it worth persuing this further or locate a card that will work?

---

### Post by unutbu on 2008-08-31
leona, since you can get output from "iwlist scan", your network card can communicate with your router. Your router told your network card that its essid is "xena", for example. Therefore, your hardware is probably fine, and it is only a matter of configuring software to make everything work. 

I do not think buying a different card is necessary. Sorry for the trouble you're having. I'm afraid it has more to do with my inability to deliver the right piece of advice than any inherent problem with your hardware. (Note to forum readers: I welcome suggestions! All help appreciated!)

Here are some options:
[list]
[*]Post the output of

route
iwconfig
sudo /etc/init.d/networking restart
cat /etc/network/interfaces

Perhaps an error message will give us a clue as to what is going wrong.
[*]Try using wicd instead of Network Manager. Some forum posters have reported that their cards worked automatically after installing wicd and going through the usual configuration GUI. Be warned however, that installing wicd uninstalls Network Manager. So if wicd does not work for you and you want to return to Network Manager, you will need to download the network-manager-gnome and network-manager .deb (package) files from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) from a computer with an internet connection, copy them to your machine, and re-install them by double-clicking on the debs.
[*]Wait for a more knowledgable forum reader to kindly lend a hand. (Sorry I haven't been more helpful).
[/list]

---

### Post by leona on 2008-08-31
Hey unutbu, I really do appriecate your help and that you took time out to lend a hand, so don't go apologiesing ok, its ok, Linux can be very frustrating at thimes, I feel you need a LOT of paicents to get on with this OS, and a degree in computer sience (which I don't have) would also help :)
Ok I'll try and get you that out put you asked for this week, I agree with your reasoning though, that its detecting the network, but something is preventing it from using it, some debugging infomation would be good, to try to determine why its refusting to work, is there some verbosity mode I could put it in to see output? Not that I'd understand what it would be saying, but could google it :)
Thank you again.

---

### Post by leona on 2008-09-01
it would seem, from doing some forum searches, that this is a long standing known bug with the current kernal and NetworkManger (so why hasn't it been fixed?), seems the work around is to install windows driver somehow, al seems a bit, what's the word, messy and complicated, to me, was hoping for a more cleaner soluciton.

---

### Post by unutbu on 2008-09-01
If you go to the first post in this thread, you will find wieman01's step-by-step guide on using ndiswrapper with your wireless adapter. If you have any questions about that guide, you can post back here. I'll be happy to help if I can. 

(Here is a tip, though, that may help: a lot of very active experienced forum helpers don't bother reading posts with dozens of replies -- like this one. Sometimes creating a new thread in the Absolute Beginners forum generates a better response because there are teams of helpers there who search for unanswered posts.)

---

### Post by leona on 2008-09-03
Hi unutbu, thank you, yes I'll print off those instructins and see how far I get with them, I have the windows disk.

Maybe if enough people report this bug on [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/134660") there might be some hope of it being fixed.

---

### Post by leona on 2008-09-03
oh no, I am a stupid, stupid, stupid girl! Cut me off a large slice of humble pie, it was MY mistake.

I forgot to check the router, I had removed all security, but what I had overlooked was "Wireless Card Access List" I had forgotten I had set this up, once I had disabled this, the card worked, so now I've added its MAC address to the list, enabled security and restarted it works now (although only a 20% signal, but its only 6 foot away from the router!).

So thank you so much for your help, but this time, it was the squidgy bit between the keyboard and the chair that was the problem, I feel so dum, d'oh! :(

---

### Post by unutbu on 2008-09-03
Ah! I'm really glad to hear you got it working. MAC filtering... I'll have to try to remember that for next time.

Thanks for getting back to us and posting the solution.

---

### Post by wieman01 on 2008-09-04
> **leona said:**
> oh no, I am a stupid, stupid, stupid girl! Cut me off a large slice of humble pie, it was MY mistake.

I forgot to check the router, I had removed all security, but what I had overlooked was "Wireless Card Access List" I had forgotten I had set this up, once I had disabled this, the card worked, so now I've added its MAC address to the list, enabled security and restarted it works now (although only a 20% signal, but its only 6 foot away from the router!).

So thank you so much for your help, but this time, it was the squidgy bit between the keyboard and the chair that was the problem, I feel so dum, d'oh! :(
Glad to hear it works. By the way... MAC filtering adds no real security at all. Please use WPA2 encryption instead which is the best option there is. MAC addresses can be faked in a matter of seconds.

---

### Post by wieman01 on 2008-09-04
> **unutbu said:**
> Ah! I'm really glad to hear you got it working. MAC filtering... I'll have to try to remember that for next time.

Thanks for getting back to us and posting the solution.
Unutbu, there are more such "hidden traps". See section "Common stumbling blocks" in this thread:

[http://ubuntuforums.org/showthread.php?t=202834]("http://ubuntuforums.org/showthread.php?t=202834")

I had totally forgotten about them as well... :-)

---

### Post by Cushie on 2008-09-05
**Hardy 8.04** with **Belkin f5d7050, USB g** adapter the hardware is recognised as v1000 but I used v3000 which also has the **rt2500usb** drivers.
Note v4000 uses the zd1211 which is set up automatically with Hardy's own drivers.

The driver files must be copied to the home directory , not a sub directory.  All went well except :-
ndiswrapper -l gave the alternate driver as p54usb (dont think that is a problem?)

Set up using Network manager rebooted and and all OK.


I notice there is a GUI front end ndisgtk  **Windows Wireless Drivers** which may be worth a try, I installled it and ran it from Sytem/administration  and it shows the rt2500usb present.

Many thanks for the workout, appreciated.

---

### Post by Maupertus on 2008-09-07
*Ahum, blush* euhm...what if you made a mistake and used the WMP54G v 4.1 Rt61 driver for the blacklist etc. instead of the v 4.0 Rt2500... 

(sorry, I can just feel the earth open beneath me right now :lolflag:)

---

### Post by wieman01 on 2008-09-07
> **Maupertus said:**
> *Ahum, blush* euhm...what if you made a mistake and used the WMP54G v 4.1 Rt61 driver for the blacklist etc. instead of the v 4.0 Rt2500... 

(sorry, I can just feel the earth open beneath me right now :lolflag:)
You can remove stuff from the blacklist... just open it with a text editor. Do you know how to do that?

---

### Post by Maupertus on 2008-09-08
I hope you can help me, as I haven't got that much experience with wifi cards. 

I basicly followed your guide like so:

Blacklist Ralink driver:

> 
echo 'blacklist Rt61' | sudo tee -a /etc/modprobe.d/blacklist/
Now find the right driver in the resulting folder & deploy it (folder should also contain other driver files i.e. .cat, .sys)

> 
sudo ndiswrapper -i <your_ralink_driver>.inf/

and the output was as follows:

> 
rt61 : driver installed
device (13B1:000D) present (alternate driver: rt61pci)


But that killed my connection after restart.
When I looked at the hardware I saw that although I just bought the card, it's a WMP54G v4 not a v4.1, can you tell me how to correct my mistake?

Thanks!

---

### Post by the_weekend on 2008-09-21
> **dingansich said:**
> I got my setup working this morning!

So there are a few things to note for amd64 users on Gutsy:

You need a 64-bit driver, which I found here: [http://forums.linksys.com/linksys/board/message?board.id=Wireless_Adapters&message.id=2699]("http://forums.linksys.com/linksys/board/message?board.id=Wireless_Adapters&message.id=2699")

Install it as you normally would (as per the sticky) with ndiswrapper.  However, this driver doesn't seem to like the wlan0 interface id, so you need to use rausb0 in your /etc/network/interfaces file.  Other than that, make sure that the appropriate drivers are listed in your /etc/modprobe.d/blacklist file, and that ndiswrapper is included in your /etc/modules file.  Reboot, and voila!  (At least that's how it worked for me.)

Thanks again to everyone that helped out with this!  :)

This driver worked okay for me, but I found this one works better: [http://www.planetamd64.com/lofiversion/index.php?t14735.html](http://www.planetamd64.com/lofiversion/index.php?t14735.html)

---

### Post by Blackmag+c on 2008-09-27
hey 

I have the rt73usb chipset 

and as far as I can tell the steps worked and I was surfing for maybe like 5 minutes and then it just dropped and now won't connect again.

the ouput of  ndiswrapper -l

was 'rt73 : invalid driver!'

what gives?
[B]
ID 148f:2573 RaLink Technology, Corp.[/B]

---

### Post by wieman01 on 2008-09-29
Perhaps you have the wrong driver... Are you on 32-bit or 64-bit? Where does the driver come from?

---

### Post by Narel on 2008-10-10
I have the Netopia 3D Reach (Ralink rt2500 usb adapter). I'm really having a hard time installing it. Ndiswrapper is installed and that about how far I have got done.

---

### Post by unutbu on 2008-10-10
Hello Narel,

When you boot up do you see any lights on the wireless card turn on?
If so, it means the machine detects the wireless adapter. 
If not, it means we need to check that ndiswrapper and the Windows driver have been installed properly.

Please open a terminal ([http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal))
and post the output of the following commands:
```

lsusb
ndiswrapper -l
cat /etc/network/interfaces
iwlist scan
```

---

### Post by Narel on 2008-10-10
Yeah, there is a constant green light, but it should be blinking orange.

I am at work right now, but I'll post the output when I get back home.

---

### Post by Narel on 2008-10-10
narel@Sonny:~$ lsusb 
Bus 004 Device 008: ID 0781:9393 SanDisk Corp.  
Bus 004 Device 007: ID 148f:2570 Ralink Technology, Corp. 802.11g WiFi 
Bus 004 Device 001: ID 0000:0000   
Bus 003 Device 001: ID 0000:0000   
Bus 002 Device 001: ID 0000:0000   
Bus 001 Device 001: ID 0000:0000   
narel@Sonny:~$ ndiswrapper -l 
narel@Sonny:~$ cat /etc/network/interfaces 
auto lo 
iface lo inet loopback 
 
narel@Sonny:~$ iwlist scan 
lo        Interface doesn't support scanning. 
 
wmaster0  Interface doesn't support scanning. 
 
wlan0     No scan results 
 
eth0      Interface doesn't support scanning. 
 
narel@Sonny:~$

---

### Post by unutbu on 2008-10-10
Okay Narel. The "ndiswrapper -l" output would have read something like```


neta5agu : driver installed
	device (07D1:3A08) present
```

if the Windows driver had been installed. That is, you should have gotten some output, although your driver is something other than "neta5agu". So it appears you have installed the ndiswrapper package (since the machine knew about the ndiswrapper command) but the Windows driver has not yet been installed.

You know, I believe Hardy comes with native driver support for RT2500 cards, so we don't we try connecting using the native driver first?

Do you see an icon on your gnome panel that looks like two overlapping computers? That would be the Network Manager app. Click on it and try to configure the wireless device using Network Manager first. If you don't see the Network Manager icon, right-click on the gnome panel, select "Add to Panel" and then select "Network Monitor".

You'll will need to know the router's ESSID. Try going for a Automatic Configuration using (DHCP) first. To make establishing a connection easier, I recommend shutting off WEP or WPA encryption on the router for now and just try to establish a clear connection first. Once you get such a connection, you can then try to add security. Also make sure MAC address filtering is turned off on your router (for now).

Configure the settings, make a note of your settings, then see if your network connection is working by using a web browser and/or by typing
```

iwlist scan
ping 209.85.171.99   # google.com
```

If it doesn't work, type 
```

sudo /etc/init.d/networking restart
```

If it still doesn't work click on the Network Manager icon and toggle the "Enable" box. The GUI for Network Manager is different from Gutsy to Hardy so my description here may not be correct in the specifics. But the idea is to toggle wireless off and then on to try to get the connection to restart. 

Also note that sometimes even when you have the right configuration settings in Network Manager, your wireless adapter may not work until you shutdown the machine and do a power up. (Rebooting may not be sufficient, you may have to shutdown and then power on.)

So if all that still does not work, try shutting down and powering up. Sometimes the wireless card needs to be powered up with the right settings in order for it to work.

If none of that works, post back with a description of what you tried, and we'll think about what to do next. We can always try the ndiswrapper approach if the above doesn't work.

---

### Post by Narel on 2008-10-11
I had some progress. I was able to go to Google, but it took some time for the page to load. It also started openssl-blacklist, but it had a slow download speed and it stopped after a few seconds. The light on usb adapter blinks orange for a few seconds and it goes solid green.

---

### Post by Narel on 2008-10-11
I shutdown my pc and turn it back on. Now the internet connection is working for longer periods of times and then it will stop. It repeats that process over and over. What am I missing? Can I fix the problem?

---

### Post by Narel on 2008-10-11
Can anyone help me? Also, I changed the channels.

---

### Post by unutbu on 2008-10-11
Please post the output of 
```

iwlist scan

```

---

### Post by Narel on 2008-10-11
lo interface doesn't support scanning.
eth0 interface doesn't support scanning.
wmaster0 interface doesn't support scanning.
wlan0 no scan results

---

### Post by unutbu on 2008-10-12
Narel, I don't know for sure the solution to your problem.

Even without a connection, "iwlist scan" should return a list of all the access points (routers) your network adapter can detect. If you are not seeing anything, it means the signal between your network adapter and the router is not good. Maybe just to debug this situation, would it be possible to bring the router closer to your computer? Or try minimizing dense matter or metal along the straight-line path between the two devices. 

No connection will ever be formed until "iwlist scan" starts returning some access points, so keep fiddling with the physical location of your network adapter and router until you start seeing something.

If you managed to reach a Google page, then it means "iwlist scan" must have been working at that time, but then the connection was lost some time later. 
It would be interesting to see the output of iwlist scan when the connection is working.

---

### Post by Narel on 2008-10-12
Okay. 
Thx

Should I try the ndiswrapper again?

---

### Post by unutbu on 2008-10-12
You have two choices, both reasonable:

Option 1: Stick with the native Linux driver
Option 2: Try ndiswrapper+Windows driver

Option 1 Pros:
[list]
[*]First, you seem to be quite close to having a good connection. Usually, once you succeed in forming a connection, it just works. If for some reason the connection is lost, usually it can be regained by toggling the "Enable wireless" box in Network Manager, or by typing
```

sudo /etc/init.d/networking restart

```
(Have you tried that already?)
[*]Second, by using the native Linux driver you can benefit from bug fixes or improvements in the driver as they come out. If you use ndiswrapper+Windows driver, you are at the mercy of a black box. 
[/list]

Option 2 Pros:
[list]
[*]If the native driver is for some reason not working for you, you might as well try 
the Windows driver.
[/list]

So, this is what I would suggest: try making your current setup work by experimenting with
the location of the router and wireless adapter, and by issuing

```
iwlist scan                           # to see the quality of the connection
sudo /etc/init.d/networking restart   # to start/restart a connection
```

If you find no way to establish a strong connection, then
try ndiswrapper. Start by reading weiman01's excellent guide:
[http://ubuntuforums.org/showthread.php?t=563547](http://ubuntuforums.org/showthread.php?t=563547)

You'll need Windows XP drivers for you wireless adapter. You might be able to locate the latest driver for the Netopia 3D Reach on the web, or you can try the one that came on a CD with your device.

---

### Post by harveywb on 2008-10-12
> **wieman01 said:**
> **Dapper Drake** users should take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=192588") if this one doesn't work. This guide was tested with **Feisty Fawn**, **Gutsy Gibbon**, and **Hardy Heron**. 
--
To all **RT73** users, please also see [this post]("http://ubuntuforums.org/showthread.php?p=4732883"). Thanks to [Kiefer Rodriguez]("http://ubuntuforums.org/member.php?u=490665") for this solution.

Please post to this [Launchpad bug report]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/163020") with all of your specs, if you have problems with a Ralink based wireless adapter.

This is a simple guide for all Ralink based wireless adapters and everyone who wants to replace the Linux driver with "ndiswrapper" (e.g. because you want to make use of either [Network Manager]("http://www.gnome.org/projects/NetworkManager/") or [WICD]("http://wicd.sourceforge.net/")). 
[B]
_INSTRUCTIONS:_[/B]
[LIST]
[*]Get the latest version of the Windows driver for your card from [Linksys' website]("http://www.linksys.com/servlet/Satellite?c=L_CASupport_C1&childpagename=US%2FLayout&cid=1166859840888&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4088837314B372&displaypage=download") or from the CD that came with your device (whatever vendor). 
[/LIST]

[LIST]
[*]Install "ndiswrapper" package **with** working internet connection (Ethernet):

[/LIST]

[LIST]
[*]Install "ndiswrapper" package **without** working internet connection (alternatively, install it via Synaptic/Adept):

[/LIST]

[LIST]
[*]Load new driver module (may not be necessary any longer, but does no harm either):

[/LIST]

[LIST]
[*]Add the module to "/etc/modules" to have it load automatically:

[/LIST]

[LIST]
[*]Create alias directive:

[/LIST]

[LIST]
[*]Pick a valid Ralink driver based on the chipset of your card (you might blacklist all of them if you are not sure):

[/LIST]

[LIST]
[*]Blacklist Ralink driver:

[/LIST]

[LIST]
[*]Now unzip the driver archive you have just downloaded (e.g. in your home directory):

[/LIST]

[LIST]
[*]Now find the right driver in the resulting folder & deploy it (folder should also contain other driver files i.e. .cat, .sys):

[/LIST]

[LIST]
[*]Make sure it has installed correctly:

[/LIST]

[LIST]
[*]The output should yield something like this:

[/LIST]

[LIST]
[*]Last but not least open this file...

[/LIST]

[LIST]
[*]...and add these 2 lines if they are not there yet [COLOR="Red"][also try _without_ adding them if Network Manager does not pick up the card & reboot][/COLOR]:

[/LIST]
You can  now safely delete the extracted driver files & folders. Then reboot the computer and see if you can connect using your favorite networking applet (e.g. Network Manager, WICD, Wifi Radar, etc.). 

Feedback is - as always - appreciated.

_**CHANGE LOG:**_
30/09/2007: Minor fixes.
07/10/2007: Expanded "blacklist".
20/10/2007: Added missing part concerning "interfaces" file.
22/10/2007: Load module "ndiswrapper" at boot.
23/10/2007: Enhanced blacklist.
07/11/2007: Bug fix for Network Manager.
12/11/2007: Updated blacklist & module section.
13/01/2008: Launchpad bug report.
15/04/2008: Update for Hardy.
17/04/2008: RT73 note.

In using amd-64 ubuntu hardy didn't install correctly even using 64 bit driver from realtek for 8185. Installed x86 version of ubuntu and all was fine. I would have liked to gotten the 64 bit installed. Computer was DELL 531.

---

### Post by tsteuerwald on 2008-11-21
Hi all!

I have currently again a very old problem:
WLAN is only working after an additional ifdown/ifup. :-(

It's a MSI PC54G2 (Ralink RT2500 chip based), I'm using Ubuntu 8.10. I've been using now ndiswrapper since 9 months. At the beginning I had sometimes the ifdown/ifup issue, but since three-four month this issue didn't appeared any longer.
Since two days it happens very often, let's say everytime :mad:

All the time I had these two lines in /etc/rc.local:
```

ifdown wlan0
ifup wlan0

```

Now I commented out these lines and changed it to:
```

/etc/init.d/networking restart

```

I've added also one line per script file to check if it is executed on startup.

In /etc/rc.local:
```

echo "works" > /tmp/test_rclocal

```

In /etc/init.d/networking:
```

echo "works" > /tmp/test_networking

```

This is the content of /etc/network/interfaces:
```

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-psk <my-network-key>
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid <my-ssid>
pre-up ifconfig wlan0 up 

```

Next thing I will try is to pipe the output of the networking script to a file in /var/log to see the output.

Anyhow this issue is really annoying, I'm wondering why this can not be fixed reliable.

Cheers
Timo

---

### Post by wieman01 on 2008-11-21
Still the same issue. No resolution yet.

---

### Post by tsteuerwald on 2008-11-21
Any other reliable alternative beside using ndiswrapper?
After upgrading to Ubuntu 8.10 the blacklist entries of the built-in drivers has been commented out and there appeared again the issue that this driver is pretty slow. Especially if you have a 16.000 Kbit/s DSL flatrate. :) So it seems that these drivers won't help. :(

---

### Post by unutbu on 2008-11-21
tsteuerwald, the suggestion below does not really unearth the cause of the problem, but it may help cut down on the annoyance:

Put this in a file like /usr/local/bin/get_connection.sh

```

#!/bin/bash
ipaddr=google.com
sleep_amount=1
dig +time=1 +retry=0 "$ipaddr" 2>/dev/null 1>&2
while [ "$?" -ne 0 ] && [ "$sleep_amount" -le 1000 ]; do
    /etc/init.d/networking restart
    sleep "$sleep_amount"
    sleep_amount=$(($sleep_amount*2))
    echo "$sleep_amount"
    dig +time=1 +retry=0 "$ipaddr" 2>/dev/null 1>&2
done

```

Make it executable:```

chmod 755 /usr/local/bin/get_connection.sh
```

Then put 
```

/usr/local/bin/get_connection.sh &
```

in /etc/rc.local.

The 'dig' command will have a return value of 0 if you have a connection to ipaddr,
and will return a non-zero value if you don't have a connection.

If you don't have a good connection, then the script will fall into the while-loop, and keep calling "/etc/init.d/networking restart" until you have a connection. The time between calls to get_connection.sh will increase geometrically. Thus, when you boot up, the restart command will be called frequently until you have a connection -- if a connection is possible. If you happen to boot up when no network connection is possible, the frequency of the calls will slow down until it finally gives up after 10 or so tries.

---

### Post by tsteuerwald on 2008-11-21
Thank you very much unutbu! You are my personal hero of the day! :)
That seems to be a pretty good workaround.
Anyhow, I'm wondering why this pretty popular ifdown/ifup problem still exists.

Cheers
Timo

---

### Post by wieman01 on 2008-11-22
Very nice, unutbu. You ought to own this thread, I mean it. :-)

---

### Post by unutbu on 2008-11-22
tsteuerwald, wieman01, thank you for your kind words. They make me feel great! :)

---

### Post by Ant68 on 2008-12-11
hello,
I am struggling to set up the wifi connection for my RTL8185 wireless card. I have followed all the instructions at the beginning of this post and I had it to work for hardy (8.04). 

I have now upgraded to intrepid and followed all the instructions again but with no luck.The driver seems not to be set up correctly and when I try to configure the network manager the system freezes.

I have set up different variations of the interfaces file. the latest being the default one:
> auto lo
iface lo inet loopback

This is what I get when I start the network again:
> my-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.
Ignoring unknown interface eth1=eth1.


iwlist:

> hemona@hemona-desktop:~$ iwlist scan
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
eth1      Interface doesn't support scanning.
wmaster0  Interface doesn't support scanning.
wlan0     No scan results
pan0      Interface doesn't support scanning.



What do you suggest I am doing to get the wireless RTL8185 working with 8.10?

---

### Post by unutbu on 2008-12-11
I'm not sure if I can help you Ant68. I have no particular knowledge about the rtl8185, 
and so I'm mainly going by the information in this post:
[http://ubuntuforums.org/showpost.php?p=3967740&postcount=2](http://ubuntuforums.org/showpost.php?p=3967740&postcount=2)
(I don't recommend you follow those directions literally, however, since Ubuntu 8.10 ships with ndiswrapper 1.52, while those instructions downloads and compiles ndiskwrapper 1.50.)

Nevertheless, let's check how close your setup matches that which would be achieved by following those instructions. Please post the output of the following:
```

ls -lR /etc/ndiswrapper/
ndiswrapper -l
cat /etc/modules
cat /etc/modprobe.d/blacklist
```

Turn off all encryption (WEP or WPA) on your router.
Turn off MAC address filtering on your router.
We can try turning these things back on later after we succeed at getting a connection.

---

### Post by tlois on 2008-12-13
I am adding this for eee box b202 users who have installed ubuntu 8.10 with AzurWave aw-ne766 wireless- rt2860 driver.  After working on the wireless problem for a few days, I finally found this and it worked:

[http://www.ubuntu-eee.com/wiki/index.php5?title=Getting_the_network_drivers_working_on_the_901](http://www.ubuntu-eee.com/wiki/index.php5?title=Getting_the_network_drivers_working_on_the_901)

for the people like me, who know just a little about linux, sometimes you can get hung up by just not capitalizing a word in the terminal.  type things exactly as they are.  

another good thing to have around the house is a linksys usb wireless dongle.  that worked no problem and helped to continue getting the internal wireless working.  

sorry if this is in the wrong place or is already here, but read this thread until i was bleary eyed last night.  gave up.  did a google search with apparently just the right terms and found the above.  

(to the people who post all this great stuff, thanks.  i am having a lot of fun with linux/ubuntu.  now have versions of it on an eee701, an ibm thinkpad and this new little baby)

---

### Post by unutbu on 2008-12-13
Congratulations, tlois, on getting networking running! That's often the most challenging part of setting up a linux box. 

Moreover, thank you for taking the time to post what worked for you. If enough of us do that, linux will become easier and easier to use :)

Enjoy your new Linux/Ubuntu systems!

---

### Post by brun059 on 2008-12-23
tlois, can only confirm what unutbu said : "thank you", your link gives me hope again :) 

your post plus the one from surfed at [http://forum.eeeuser.com/viewtopic.php?id=49865&p=1](http://forum.eeeuser.com/viewtopic.php?id=49865&p=1) together finally made it work for me.

(after a long weekend trying to get ubuntu 8.10 working on my eee-1000 I was on the verge of giving in, bowing to big-MS and install XP :(  )

eee eeepc wireless intrepid 8.10 ralink ra2860

---

### Post by tlois on 2009-01-01
Following up here to say that I installed eeebuntu on the eee box and everything worked without adding driver wrappers, etc.  (Did it because of a strange reboot freeze problem with regular Ubuntu.)  

Bruno, glad you got it figured out.  I'll, personally, never go back to MS.

Happy New Year.

---

### Post by ProNux on 2009-02-10
Guys,

I have Edimax EW-7318USg based on RT73.  I got this working using the native Linux driver from Ralink when I started using Ubuntu on kernel version 2.6.24-19.  But lately, after installation of kernel 2.6.24-22 onwards, the WLAN became unstable.  Even after removing the later kernels and booting to the old kernel version.

I tried running Live Intrepid Ibex and found it stable.

Have I missed something here?

Thanks.

---

### Post by unutbu on 2009-02-10
Well, I could be wrong, but given the facts you've reported, it seems to me that the "instability" is not related to the kernel.

Wireless devices have no memory. If the drivers and config files are the same, the performance of the device will be the same as long as there is no hardware failure. 

So if you've reverted to your old kernel and are still experiencing instability, then
the cause is either hardware failure or some environmental condition like bad weather or electromagnetic interference.

My experience with wireless devices suggest that dropped connections have a gamma function probability distribution (yes, I admit it, I collect such data) -- similar to the wait times of radioactive decay. A funny side-effect of this is that sometimes dropped connections seem to happen quite frequently and then during other periods quite infrequently. You need to collect a considerable amount of data before you can tell if one setup is truly more stable than another.

This is just my inexpert opinion. I hope this helps. I'd love to be proven wrong and learn something new.

---

### Post by ProNux on 2009-02-10
Thanks for the info unutbu.  

I forgot to mention that I am on dual-boot (Windows XP/Ubuntu Hardy).  At Windows, I got no problems at all, running continuously for hours.  I tend to agree that it may not be kernel related.

At the network manager, sometimes, the WLAN has no IP address reported (0.0.0.0) but on the net monitor, it has (192.168.0.XXX, DHCP).

When my connection drops, I just do

```
sudo dhclient rausb0
```

to restore.  But still, this is not the corrective action.

By the way, I just have found this thread today.  Might read it all over again tomorrow (it's 1AM now, gotta sleep :)).  Thanks for this thread.

---

### Post by wieman01 on 2009-02-10
You're welcome. Not sure how useful this thread still is, most Ralink related problems seem to have been solved as of 8.10. Let's keep it open for a few more months then.

---

### Post by ProNux on 2009-02-10
> **wieman01 said:**
> You're welcome. Not sure how useful this thread still is, most Ralink related problems seem to have been solved as of 8.10. Let's keep it open for a few more months then.
Thanks.

I might switch to Interpid if I cannot fix it soon.  But still, I am just curious what's the reason behind the instability.  And upgrading to Intrepid only gets rid of my RT73 problem, not solving it.

---

### Post by ProNux on 2009-02-12
Guys, I think my problem (unstable RT73 USB WLAN)is related to "conflict" with the built-in WLAN of my laptop.

Will it really cause the problem since both WLANs are active and both acquires separate IP addresses from one AP?  What I did was just disable my built-in WLAN (Intel 3945).

So far, my RT73 is now okay.

Got to say sorry to my RT73 Wlan...

---

### Post by wieman01 on 2009-02-12
Good for you, dude. Yes, a conflict seems possible.

---

### Post by Fevrin on 2009-04-29
Now that Jaunty's been released, I thought I'd give it a go (64-bit), but the inability to connect wirelessly has stopped me straight away. Intrepid (64-bit) also has this issue, but Hardy (64-bit) doesn't.

I have a Hawking HWP54G rev. 01 card, which uses the rt2500pci driver, according to Jaunty's version of 'lspci -vvnn'.  But I won't bore you with details; I'll let the following speak for itself:

Hardy 'lspci -vvnn':
```
03:07.0 Network controller [0280]: RaLink RT2500 802.11g Cardbus/mini-PCI [1814:0201] (rev 01)
    Subsystem: Edimax Computer Co. Unknown device [1432:0b54]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 32, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at fe8fc000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: [40] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
```Jaunty 'sudo lspci -vvnn':
```
03:07.0 Network controller [0280]: RaLink RT2500 802.11g Cardbus/mini-PCI [1814:0201] (rev 01)
    Subsystem: Edimax Computer Co. Device [1432:0b54]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at fe8fc000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: [40] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: rt2500pci
    Kernel modules: rt2500pci
```Hardy 'ifconfig wlan0':
```
wlan0     Link encap:Ethernet  HWaddr 00:0e:3b:04:93:27  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:3bff:fe04:9327/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:65414 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46443 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:68231535 (65.0 MB)  TX bytes:15130286 (14.4 MB)
```Jaunty 'sudo ifconfig wlan0':
```
wlan0     Link encap:Ethernet  HWaddr 00:0e:3b:04:93:27
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```Hardy 'sudo iwconfig wlan0':
```
wlan0     IEEE 802.11g  ESSID:"HOME"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1B:11:62:B9:20  
          Bit Rate=1 Mb/s   Tx-Power=27 dBm  
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B  
          Encryption key: sorry!
          Link Quality=62/100  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```Jaunty 'sudo iwconfig wlan0':
```
wlan0     IEEE 802.11bg  ESSID:"HOME"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated  
          Tx-Power=20 dBm  
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B  
          Encryption key: sorry!
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```Hardy 'sudo iwlist wlan0 scanning':
```
wlan0     Scan completed :
          Cell 01 - Address: 00:1B:11:62:B9:20
                    ESSID:"HOME"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/100  Signal level=-56 dBm  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000002cee6024158
```Jaunty 'sudo iwlist wlan0 scanning':
```
wlan0     Scan completed :                                                                                                        
  2           Cell 01 - Address: 00:1B:11:62:B9:20
  3                     ESSID:"HOME"
  4                     Mode:Master
  5                     Channel:6
  6                     Frequency:2.437 GHz (Channel 6)
  7                     Quality=52/100  Signal level:-55 dBm
  8                     Encryption key:on
  9                     IE: Unknown: 0004484F4D45
 10                     IE: Unknown: 010482848B96
 11                     IE: Unknown: 030106
 12                     IE: Unknown: 2A0100
 13                     IE: Unknown: 32080C1218243048606C
 14                     IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
 15                     IE: Unknown: DD1E00904C334E101EFFFF000000000000000000000000000000000000000000
 16                     IE: Unknown: DD1A00904C3406070700000000000000000000000000000000000000
 17                     IE: Unknown: 2D1A4E101EFFFF000000000000000000000000000004000000000000
 18                     IE: Unknown: 3D1606070300000000000000000000000000000000000000
 19                     IE: Unknown: DD050050F20502
 20                     IE: Unknown:                                                                                                       DD820050F204104A0001101044000102103B00010310470010B64B8D83CDCF327F82984058B975B1C81021000E442D4C696E6B2053797374656D731023000744495    22D3635351024000541312F4132104200046E6F6E651054000800060050F204000110110017587472656D65204E204749474142495420526F757465721008000200    04
 21                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
 22                               9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
 23                               48 Mb/s; 54 Mb/s
 24                     Extra:tsf=000002cdc71e0bc9
 25                     Extra: Last beacon: 56ms ago
```and both /etc/network/interfaces were the same:

```
auto lo
iface lo inet loopback
```Also, I've attached the relevant part of dmesg's output.  So does anyone see anything wrong or can you think of anything as to why my wireless card works in Hardy, but not either of its successors?  I'm concerned that future Ubuntu releases may not support my card for good :(

Lastly, I have to say that it's kind of annoying that this forum's file attachment component doesn't accept a file without an extension....

---

### Post by unutbu on 2009-04-29
Fevrin, I can't say for sure if this will help you or not, but perhaps try this:
```

#!/bin/bash
sudo ifup wlan0
# routerip=192.168.1.1
routerip=google.com
sleep_amount=1
dig +time=1 +retry=0 "$routerip" 2>/dev/null 1>&2
while [ "$?" -ne 0 ] && [ "$sleep_amount" -le 1000 ]; do
    sudo /etc/init.d/networking restart
    sleep "$sleep_amount"
    sleep_amount=$(($sleep_amount+2))
    echo "$sleep_amount"
    dig +time=1 +retry=0 "$routerip" 2>/dev/null 1>&2
done
```

Save the script in, say, ~/bin/up

Make it executable

```
chmod 755 ~/bin/up
```

and run it like this:

```
up
```

The script will check if an internet connection exists, and if not, it will run "sudo /etc/init.d/networking restart". It will do this repeatedly until a connection is established. 

I find I sometimes have to run the "networking restart" command a few times before connection is actually established.

---

### Post by joylessdave on 2009-05-10
ive just installed xubuntu 9.04 on a old pc with a pci wifi card 

i don't know who the manufacturer of the card is, the chip on the card is a RT2560F

ethernet is working correctly

lspci identifies the card as 

```
00:09.0 Network controller: RALink RT2500 802.11g Cardbus/mini-PCI (rev 01)
```

both networkmanager and wicd can see the card and both pick up the wireless networks in the area

networkmanager continually asks for the wep key 
wicd just fails at obtaining IP address

dmesg | grep wlan0 give the following:
```
[   46.254306] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   51.878227] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   54.044791] wlan0: authenticate with AP 00:18:4d:6a:2d:f0
[   54.070900] wlan0: authenticated
[   54.070934] wlan0: associate with AP 00:18:4d:6a:2d:f0
[   54.073588] wlan0: RX AssocResp from 00:18:4d:6a:2d:f0 (capab=0x431 status=0 aid=2)
[   54.073608] wlan0: associated
[   54.079767] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   54.432269] wlan0: authenticate with AP 00:18:4d:6a:2d:f0
[   54.475778] wlan0: authenticated
[   54.475807] wlan0: associate with AP 00:18:4d:6a:2d:f0
[   54.567281] wlan0: RX ReassocResp from 00:18:4d:6a:2d:f0 (capab=0x431 status=0 aid=2)
[   54.567302] wlan0: associated
[   64.504044] wlan0: no IPv6 routers present
[  135.976616] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  136.107420] wlan0: deauthenticating by local choice (reason=3)
[  136.891150] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  138.364948] wlan0: authenticate with AP 00:18:4d:6a:2d:f0
[  138.366480] wlan0: authenticated
[  138.366496] wlan0: associate with AP 00:18:4d:6a:2d:f0
[  138.370080] wlan0: RX AssocResp from 00:18:4d:6a:2d:f0 (capab=0x431 status=0 aid=2)
[  138.370101] wlan0: associated
[  138.386809] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  148.504098] wlan0: no IPv6 routers present
[  215.014572] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  215.078821] wlan0: deauthenticating by local choice (reason=3)
[  215.386372] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  216.852863] wlan0: authenticate with AP 00:18:4d:6a:2d:f0
[  216.854278] wlan0: authenticated
[  216.854293] wlan0: associate with AP 00:18:4d:6a:2d:f0
[  216.857888] wlan0: RX AssocResp from 00:18:4d:6a:2d:f0 (capab=0x431 status=0 aid=2)
[  216.857907] wlan0: associated
[  216.861966] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  227.080044] wlan0: no IPv6 routers present
[  295.022396] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  295.087992] wlan0: deauthenticating by local choice (reason=3)
[  295.382375] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  296.852864] wlan0: authenticate with AP 00:18:4d:6a:2d:f0
[  296.854348] wlan0: authenticated
[  296.854363] wlan0: associate with AP 00:18:4d:6a:2d:f0
[  296.858085] wlan0: RX AssocResp from 00:18:4d:6a:2d:f0 (capab=0x431 status=0 aid=2)
[  296.858105] wlan0: associated
[  296.862180] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  307.020045] wlan0: no IPv6 routers present
```

i read in several other forums that the no ipv6 routers message is common and that disabling ipv6 makes no difference but just to be safe i blacklisted ipv6 

ip a | grep inet6 now give no response however dmesg | grep wlan0 still has the no ipv6 routers message

unfortunately i cannot disable encryption as people are using the network at the same time to test if it can connect at all

i then attempted to setup the connection manually however the card is not identified by ifconfig / iwconfig if a network manager is not running

~~~~~~~~UPDATE~~~~~~~

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:e0:4c:00:ed:d2  
          inet addr:192.168.0.46  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fe00:edd2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:816 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:358770 (358.7 KB)  TX bytes:4027 (4.0 KB)
          Interrupt:5 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:840 (840.0 B)  TX bytes:840 (840.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:13:d3:6a:8a:08  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:113 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:122211 (122.2 KB)  TX bytes:24414 (24.4 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-D3-6A-8A-08-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

wlist scan

```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:18:4D:6A:2D:F0
                    ESSID:"Gmans"
                    Mode:Master
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=52/100  Signal level:-46 dBm  
                    Encryption key:on
                    IE: Unknown: 0005476D616E73
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030103
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101060003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F010100240000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000780542934c
                    Extra: Last beacon: 1340ms ago
          Cell 02 - Address: 00:90:D0:4C:2B:A2
                    ESSID:"walkermicki"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/100  Signal level:-79 dBm  
                    Encryption key:on
                    IE: Unknown: 000B77616C6B65726D69636B69
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180200F0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000018252aa9837
                    Extra: Last beacon: 1148ms ago

pan0      Interface doesn't support scanning.


```

cat /etc/network/interfaces

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp

```

sudo /etc/init.d/networking restart

```

 * Reconfiguring network interfaces...                                          
	Ignoring unknown interface eth0=eth0.

```

I noticed my interfaces file was a little empty so i added 

```

auto wlan0
iface wlan0 inet dhcp
gateway 192.168.0.1
netmask 255.255.255.0

```

after this alteration 
dmesg | grep wlan0 reads
```

[   46.083949] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  177.554823] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  180.116878] wlan0: authenticate with AP 00:18:4d:6a:2d:f0
[  180.118369] wlan0: authenticated
[  180.118385] wlan0: associate with AP 00:18:4d:6a:2d:f0
[  180.121936] wlan0: RX AssocResp from 00:18:4d:6a:2d:f0 (capab=0x431 status=0 aid=2)
[  180.121956] wlan0: associated
[  180.126027] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  190.640096] wlan0: no IPv6 routers present
[  259.073073] wlan0: deauthenticating by local choice (reason=3)
[  267.150626] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

which has made no difference

---

### Post by unutbu on 2009-05-10
Perhaps try editing /etc/network/interfaces directly:
```

auto wlan0
iface wlan0 inet dhcp
wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX
wireless-essid XXXXXXXXXXXX
```

It might not be true for all setups, but I find with mine that all wireless configuration files must be in place at boot time for the NIC to be setup properly. So you may have to do a shutdown / power up cycle after editing /etc/network/interfaces to see if it works.

If it doesn't work, please post the output of
```

ifconfig
iwconfig
sudo /etc/init.d/networking restart
```
Please post ifconfig again, so we can see if editing /etc/network/interfaces made any difference.

---

### Post by wieman01 on 2009-05-10
Another thought... I had the same problem this morning with my Ralink adapter. I had to switch the USB connector from my USB hub directly to the PC. It worked after that.

---

### Post by joylessdave on 2009-05-11
made those changes unfortunatly no luck

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:e0:4c:00:ed:d2  
          inet addr:192.168.0.46  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fe00:edd2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13827 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10403 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18754612 (18.7 MB)  TX bytes:979569 (979.5 KB)
          Interrupt:5 Base address:0xe000 

```

iwconfig

```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Gmans"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

sudo /etc/init.d/networking restart
```
 
 * Reconfiguring network interfaces...                                          /etc/network/interfaces:2: misplaced option
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:2: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"
                                                                         [fail]


```

cat /etc/network/interfaces
```

# This file describes the network interfaces available on your system
and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-key 1c7d1d63ccc1610b6af218d9a0
wireless-essid Gmans

```

unfortunatly its a pci card not a usb dongle i had a go at switching the pci slots around but no luck

thanks

JLD

---

### Post by unutbu on 2009-05-11
Ahah. This might be part of the problem:

```
 * Reconfiguring network interfaces...                                          /etc/network/interfaces:2: misplaced option
ifdown: couldn't read interfaces file "/etc/network/interfaces"
**/etc/network/interfaces:2: misplaced option**
```


Run
```

gksu gedit /etc/network/interfaces
```

Put a # sign at the front of the 2nd line:

Change```


# This file describes the network interfaces available on your system
and how to activate them. For more information, see interfaces(5).
```

to
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
```

Save and exit gedit. The # sign tells the machine that line is just a comment.

Shutdown and reboot. 

Also, you might want to edit your previous post so your real wireless-key is not showing.
It probably means nothing since we don't know where you are, but why tempt fate?

---

### Post by joylessdave on 2009-05-11
because of the error reading the interfaces file i restored the backup and i get 

cat interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

/etc/init.d/networking restart
```

 * Reconfiguring network interfaces...                                          Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:e0:4c:00:ed:d2
Sending on   LPF/eth0/00:e0:4c:00:ed:d2
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 192.168.0.46 from 192.168.0.1
DHCPREQUEST of 192.168.0.46 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.46 from 192.168.0.1
bound to 192.168.0.46 -- renewal in 232765 seconds.
 * if-up.d/mountnfs[eth0]: waiting for interface lo before doing NFS mounts
                                                                         [ OK ]

```

i edited the replaced interfaces file to read

cat interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

#WIFI
auto wlan0
iface wlano inet dhcp

```


/etc/init.d/networking restart
 
```

* Reconfiguring network interfaces...                                          Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:e0:4c:00:ed:d2
Sending on   LPF/eth0/00:e0:4c:00:ed:d2
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.0.46 from 192.168.0.1
DHCPREQUEST of 192.168.0.46 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.46 from 192.168.0.1
bound to 192.168.0.46 -- renewal in 237714 seconds.
 * if-up.d/mountnfs[eth0]: waiting for interface lo before doing NFS mounts
 * if-up.d/mountnfs[eth0]: waiting for interface wlan0 before doing NFS mounts
Ignoring unknown interface wlan0=wlan0.
                                                                         [ OK ]

```

i notice the last line of the networking rstart says that wlan0 is unknown however ifconfig reads
```

eth0      Link encap:Ethernet  HWaddr 00:e0:4c:00:ed:d2  
          inet addr:192.168.0.46  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fe00:edd2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:834 errors:0 dropped:0 overruns:0 frame:0
          TX packets:517 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:722539 (722.5 KB)  TX bytes:58665 (58.6 KB)
          Interrupt:5 Base address:0xe000 

wlan0     Link encap:Ethernet  HWaddr 00:13:d3:6a:8a:08  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18072 (18.0 KB)  TX bytes:6056 (6.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-D3-6A-8A-08-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

so i don't know what is going on 

thanks

jld

---

### Post by unutbu on 2009-05-11
You seem have two network interfaces: eth0 and wlan0.
eth0 is a wired network interface, and
wlan0 is a wireless network interface.

eth0 is already communicating with a router. And it successfully obtains an IP address:
```

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.0.46 from 192.168.0.1
DHCPREQUEST of 192.168.0.46 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.46 from 192.168.0.1
bound to 192.168.0.46 -- renewal in 237714 seconds.
```

eth0 is communicating on the 192.168.0.* network.
You can only have one network interface per network.

wlan0 can not communicate on the same network, since your machine has to decide which interface to use when it sends packets out on the 192.168.0.* network. Right now, it looks like eth0 is filling that role. 

So what are you trying to do with wlan0? Do you have a second router? Do you want to disable eth0 and use wlan0 instead?

Also, there seems to be a problem with your lo interface:
```

 * if-up.d/mountnfs[eth0]: waiting for interface lo before doing NFS mounts
```

I'm not sure what is causing this, or how to fix it. 
Please post the contents of /etc/hosts.

---

### Post by kay-man on 2009-05-11
Seems to me you have an error in your /etc/network/interfaces.

In this line:

```
iface wlano inet dhcp
```

you spelled wlano with an o (an ooooh) at the end instaed of a 0 (zero). So you're referencing an unknown interface.

Change it and see and run

```
sudo /etc/init.d/networking restart
```

---

### Post by wieman01 on 2009-05-11
> **paulklos said:**
> Seems to me you have an error in your /etc/network/interfaces.

In this line:

```
iface wlano inet dhcp
```

you spelled wlano with an o (an ooooh) at the end instaed of a 0 (zero). So you're referencing an unknown interface.

Change it and see and run

```
sudo /etc/init.d/networking restart
```
Darn, you're right. Thanks for paying attention!

---

### Post by joylessdave on 2009-05-11
the machine is only connected over ethernet while i try and get wifi working (its easier to post the output of the commands if im using the same machine)

my etc/hosts file reads
```

27.0.0.1       localhost
127.0.1.1       The-den.localdomain     The-den

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

the error i was referring to not knowing what was happening was the error in my interfaces file where i had typed wlano instead of wlan0

having corrected this and rebooted i still cannot connect to the wireless network

following the correction of my interfaces file and still not being able to connect i get the following (with no ethernet cable connected)

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:e0:4c:00:ed:d2  
          inet6 addr: fe80::2e0:4cff:fe00:edd2/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:872 errors:0 dropped:0 overruns:0 frame:0
          TX packets:724 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:732012 (732.0 KB)  TX bytes:152142 (152.1 KB)
          Interrupt:5 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1820 (1.8 KB)  TX bytes:1820 (1.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:d3:6a:8a:08  
          inet6 addr: fe80::213:d3ff:fe6a:8a08/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:185 errors:0 dropped:0 overruns:0 frame:0
          TX packets:109 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:76079 (76.0 KB)  TX bytes:22121 (22.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-D3-6A-8A-08-61-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

iwconfig

```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Gmans"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:18:4D:6A:2D:F0   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=49/100  Signal level:-43 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```
/etc/init.d/networking restart
```

 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 2342
removed stale PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:e0:4c:00:ed:d2
Sending on   LPF/eth0/00:e0:4c:00:ed:d2
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:e0:4c:00:ed:d2
Sending on   LPF/eth0/00:e0:4c:00:ed:d2
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 * if-up.d/mountnfs[eth0]: waiting for interface wlan0 before doing NFS mounts
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:13:d3:6a:8a:08
Sending on   LPF/wlan0/00:13:d3:6a:8a:08
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]

```

---

### Post by joylessdave on 2009-05-11
ok this is very weird 
i went and got a drink came back 
did a dmesg | grep wlan0 to see if anything new had shown up 
checked my ipcop dhcp logs and it had mystically connected 

going to restart and see if it will connect again

~~~~UPDATE~~~~~

after 2 reboots its still connecting so i have no idea why it wasn't before

thanks for all the help 

JLD

---

### Post by kay-man on 2009-05-11
I had this error myself recently :D

Cool that it's working, anyway!

---

### Post by wieman01 on 2009-05-12
Done nothing, really. Glad you got it working, dude.

---

### Post by coubury on 2009-09-13
Can anyone help i followed the guide in the OP 

I have a edimax EW711uan it used the RT2500 chipset.

I am using backtrack 4 in vmware 

here is my problem

> root@bt:~# sudo /etc/network/interfaces
sudo: /etc/network/interfaces: command not found
root@bt:~# sudo ndiswrapper -i /root/Desktop/Driver/rt2500usb.inf
installing rt2500usb ...
root@bt:~# ndiswrapper -l
rt2500usb : driver installed
rt73 : driver installed
root@bt:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

root@bt:~# iface wlan0 inet dhcp
bash: iface: command not found
root@bt:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:29:3e:0e:65
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe3e:e65/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:331 errors:0 dropped:0 overruns:0 frame:0
          TX packets:188 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:328973 (328.9 KB)  TX bytes:13845 (13.8 KB)
          Interrupt:19 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)




/etc/network/interfaces is not found

also when i type iwconfig the wireless usb adapter is not found

any ideas?

---

### Post by wieman01 on 2009-09-13
Which version of Ubuntu are you running? 7.10? There is no need to install a separate driver, things have improved a lot since I published this tutorials.

---

### Post by coubury on 2009-09-13
No

I have not updated my avatar since last year

Im using backtrack 4 in vmware

The new Backtrack uses ubuntu right?

---

### Post by wieman01 on 2009-09-13
> **coubury said:**
> No

I have not updated my avatar since last year

Im using backtrack 4 in vmware

The new Backtrack uses ubuntu right?
I don't really know what Backtrack is to be honest.

---

### Post by coubury on 2009-09-13
you serious? Of course you know what backtrack 4 is :S

Anyone it uses Ubuntu i need a guide to get my wireless adapter working  AS far as i know Backtrack 4 uses the latest version of Ubuntu

So can you help me please sir? I need to get my RT2500usb working.

It's a edimax ew-7711Uan usb adapter

Can you help me please?

---

### Post by unutbu on 2009-09-13
This guide was written at a time when ndiswrapper was more of a necessity.
Now there are open source drivers for Wireless cards that use RT2500 chips.
I think you'll get better results using those drivers than by trying to use ndiswrapper.

I suggest you uninstall ndiswrapper:
```

sudo apt-get purge ndiswrapper
```

and then try the guide referenced here:
[http://ubuntuforums.org/showthread.php?t=1048423](http://ubuntuforums.org/showthread.php?t=1048423)

---

### Post by wieman01 on 2009-09-14
> **coubury said:**
> you serious? Of course you know what backtrack 4 is :S

Anyone it uses Ubuntu i need a guide to get my wireless adapter working  AS far as i know Backtrack 4 uses the latest version of Ubuntu

So can you help me please sir? I need to get my RT2500usb working.

It's a edimax ew-7711Uan usb adapter

Can you help me please?
I was serious but obviously it was a little late or early (can't remember) over here when I replied. I am with you now.

The latest Serialmonkey (Ralink) drivers should actually be included as of Jaunty. I am surprised the 2500 creates an issue.

Please follow unutbu's advice and report back how it goes.

---

### Post by kevinguillorytraining on 2009-10-09
Wow. My driver problem is resolved now

---

### Post by wieman01 on 2009-10-09
> **kevinguillorytraining said:**
> Wow. My driver problem is resolved now
Which adapter have you got and what chipset is it exactly? Just out of curiousity...

---

### Post by coubury on 2009-11-19
> **unutbu said:**
> This guide was written at a time when ndiswrapper was more of a necessity.
Now there are open source drivers for Wireless cards that use RT2500 chips.
I think you'll get better results using those drivers than by trying to use ndiswrapper.

I suggest you uninstall ndiswrapper:
```

sudo apt-get purge ndiswrapper
```

and then try the guide referenced here:
[http://ubuntuforums.org/showthread.php?t=1048423](http://ubuntuforums.org/showthread.php?t=1048423)


I followed this. But it appears my card is still not being reconized

Im using BT3 this time with a RT2870 driver it's a EW-7711uan

> bt ~ # wget  
[http://ubunturt2870.pbworks.com/f/2009_0820_RT2870_Linux_STA_V2.2.0.0.tar.bz2](http://ubunturt2870.pbworks.com/f/2009_0820_RT2870_Linux_STA_V2.2.0.0.tar.bz2)
--11:33:41--   
[http://ubunturt2870.pbworks.com/f/2009_0820_RT2870_Linux_STA_V2.2.0.0.tar.bz2](http://ubunturt2870.pbworks.com/f/2009_0820_RT2870_Linux_STA_V2.2.0.0.tar.bz2)
            => `2009_0820_RT2870_Linux_STA_V2.2.0.0.tar.bz2'
Resolving ubunturt2870.pbworks.com... 208.96.18.237, 208.96.18.238
Connecting to ubunturt2870.pbworks.com|208.96.18.237|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 584,289 (571K) [application/x-bz2]

100%[====================================>] 584,289      137.67K/s     
ETA 00:00

11:33:48 (137.59 KB/s) - `2009_0820_RT2870_Linux_STA_V2.2.0.0.tar.bz2'  
saved [584289/584289]

bt ~ # tar xvfj 2009_0820_RT2870_Linux_STA_V2.2.0.0.tar.bz2
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/action.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/ba_action.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/br_ftph.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/client_wds.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/cmm_aes.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/cmm_asic.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/cmm_cfg.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/cmm_cmd.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/cmm_data.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/cmm_data_usb.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/cmm_info.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/cmm_mac_usb.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/cmm_profile.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/cmm_sanity.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/cmm_sync.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/cmm_tkip.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/cmm_wep.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/cmm_wpa.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/crypt_aes.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/crypt_arc4.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/crypt_hmac.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/crypt_md5.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/crypt_sha2.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/dfs.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/eeprom.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/ee_prom.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/mlme.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/netif_block.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/rt2870.bin
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/rtmp_init.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/rtmp_mcu.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/rtmp_timer.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/rtusb_bulk.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/rtusb_data.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/rtusb_io.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/rt_channel.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/spectrum.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/common/vr_ikans.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/action.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/ap.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/chip/
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/chip/mac_usb.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/chip/rt2870.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/chip/rtmp_mac.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/chip/rtmp_phy.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/chlist.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/client_wds.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/client_wds_cmm.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/crypt_aes.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/crypt_arc4.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/crypt_hmac.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/crypt_md5.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/crypt_sha2.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/dfs.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/dot11i_wpa.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/eeprom.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/firmware.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/iface/
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/iface/rtmp_usb.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/link_list.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/mlme.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/netif_block.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/oid.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/os/
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/os/rt_linux.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/rtmp.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/rtmp_chip.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/rtmp_cmd.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/rtmp_def.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/rtmp_dot11.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/rtmp_iface.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/rtmp_mcu.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/rtmp_os.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/rtmp_timer.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/rtmp_type.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/rtusb_io.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/rt_ate.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/rt_config.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/spectrum.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/spectrum_def.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/vr_ikans.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/wpa.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/include/wpa_cmm.h
2009_0820_RT2870_Linux_STA_V2.2.0.0/iwpriv_usage.txt
2009_0820_RT2870_Linux_STA_V2.2.0.0/Makefile
2009_0820_RT2870_Linux_STA_V2.2.0.0/os/
2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/
2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/config.mk
2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/Makefile.4
2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/Makefile.6
2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/Module.symvers
2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/modules.order
2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/rt_ate.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/rt_linux.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/rt_main_dev.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/rt_profile.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/rt_usb.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/sta_ioctl.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/usb_main_dev.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/vr_ikans.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/README_STA
2009_0820_RT2870_Linux_STA_V2.2.0.0/RT2870STA.dat
2009_0820_RT2870_Linux_STA_V2.2.0.0/RT2870STACard.dat
2009_0820_RT2870_Linux_STA_V2.2.0.0/sta/
2009_0820_RT2870_Linux_STA_V2.2.0.0/sta/assoc.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/sta/auth.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/sta/auth_rsp.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/sta/connect.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/sta/dls.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/sta/rtmp_ckipmic.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/sta/rtmp_data.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/sta/sanity.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/sta/sync.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/sta/wpa.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/sta_ate_iwpriv_usage.txt
2009_0820_RT2870_Linux_STA_V2.2.0.0/tools/
2009_0820_RT2870_Linux_STA_V2.2.0.0/tools/bin2h
2009_0820_RT2870_Linux_STA_V2.2.0.0/tools/bin2h.c
2009_0820_RT2870_Linux_STA_V2.2.0.0/tools/Makefile
bt ~ # cd 2009_0820_RT2870_Linux_STA_V2.2.0.0
bt 2009_0820_RT2870_Linux_STA_V2.2.0.0 #
bt 2009_0820_RT2870_Linux_STA_V2.2.0.0 #
bt 2009_0820_RT2870_Linux_STA_V2.2.0.0 # cd os/linux
bt linux #
bt linux # rm config.mk
bt linux #
bt linux # wget [http://ubunturt2870.pbwiki.com/f/config.mk](http://ubunturt2870.pbwiki.com/f/config.mk)
--11:34:26--  [http://ubunturt2870.pbwiki.com/f/config.mk](http://ubunturt2870.pbwiki.com/f/config.mk)
            => `config.mk'
Resolving ubunturt2870.pbwiki.com... 208.96.32.2, 208.96.32.3
Connecting to ubunturt2870.pbwiki.com|208.96.32.2|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://ubunturt2870.pbworks.com/f/config.mk](http://ubunturt2870.pbworks.com/f/config.mk) [following]
--11:34:27--  [http://ubunturt2870.pbworks.com/f/config.mk](http://ubunturt2870.pbworks.com/f/config.mk)
            => `config.mk'
Resolving ubunturt2870.pbworks.com... 208.96.18.238, 208.96.18.237
Connecting to ubunturt2870.pbworks.com|208.96.18.238|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10,760 (11K) [application/x-mk]

100%[====================================>] 10,760        --.--K/s

11:34:28 (128.87 MB/s) - `config.mk' saved [10760/10760]

bt linux # cd 2009_0820_RT2870_Linux_STA_V2.2.0.0
-bash: cd: 2009_0820_RT2870_Linux_STA_V2.2.0.0: No such file or directory
bt linux # cd /root/2009_0820_RT2870_Linux_STA_V2.2.0.0
bt 2009_0820_RT2870_Linux_STA_V2.2.0.0 # sudo make
make -C tools
make[1]: Entering directory `/root/2009_0820_RT2870_Linux_STA_V2.2.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/root/2009_0820_RT2870_Linux_STA_V2.2.0.0/tools'
/root/2009_0820_RT2870_Linux_STA_V2.2.0.0/tools/bin2h
cp -f os/linux/Makefile.6  
/root/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/Makefile
make  -C  /lib/modules/2.6.21.5/build  
SUBDIRS=/root/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux modules
make: *** /lib/modules/2.6.21.5/build: No such file or directory.  Stop.
make: *** [LINUX] Error 2
bt 2009_0820_RT2870_Linux_STA_V2.2.0.0 #
bt 2009_0820_RT2870_Linux_STA_V2.2.0.0 # sudo make install
make -C /root/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux -f  
Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory  
`/root/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /root/2009_0820_RT2870_Linux_STA_V2.2.0.0/RT2870STA.dat  
/etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.21.5/kernel/drivers/net/wireless/
install -m 644 -c rt2870sta.ko  
/lib/modules/2.6.21.5/kernel/drivers/net/wireless/
install: cannot stat `rt2870sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory  
`/root/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux'
make: *** [install] Error 2
bt 2009_0820_RT2870_Linux_STA_V2.2.0.0 #
bt 2009_0820_RT2870_Linux_STA_V2.2.0.0 # sudo modprobe rt2870sta
bt 2009_0820_RT2870_Linux_STA_V2.2.0.0 #
bt 2009_0820_RT2870_Linux_STA_V2.2.0.0 # sudo modprobe -r rt2870sta
bt 2009_0820_RT2870_Linux_STA_V2.2.0.0 # sudo modprobe rt2870sta
bt 2009_0820_RT2870_Linux_STA_V2.2.0.0 # sudo ifconfig ra0 up
ra0: ERROR while getting interface flags: No such device
bt 2009_0820_RT2870_Linux_STA_V2.2.0.0 #



If i type iwconig i get


bt ~ # sudo ifconfig ra0 down
ra0: ERROR while getting interface flags: No such device
bt ~ # iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

bt ~ #



Can you help please?

---

### Post by jlangholzj on 2010-09-13
Lets see how this goes....blasted windows drivers take forever.


I've got a rt2860 chipset wireless card, running lucid.

my router is a WPA2 security and Its has know issues with the standard linux drivers that are included with connecting to WPA2 servers. why this is, i don't know.

I've followed another fellas tutorial on getting it to work and it does, kind of. lol. It likes to drop my signal quite frequently and not be happy with any secured networks. 

...judging from your other threads i think you've got some insight into this... :p

anywho...when these dang windows drivers are done DL'n I'll let you know how things go. 


also, would this method work for say another chipset of drivers?? I've got a buddy who has a chipset that the manufacture wont allow linux drivers to be produced (damn medieval ijiots). I knew there was a way with the wrapper to run the windows driver but could i just follow your steps only with different names and such??

thanks in advance

-J

---

