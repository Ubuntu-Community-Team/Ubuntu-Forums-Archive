---
title: "HOWTO: Latest madwifi svn snapshot"
date: 2005-12-18
forum: Outdated Tutorials &amp; Tips
---

### Post by Lambert on 2005-12-18
As every user has options with gnu/linux you can also see this howto. The instructions there will let you keep restricted modules working.
[http://ubuntuforums.org/showthread.php?t=113405&highlight=MADWIFI]("http://ubuntuforums.org/showthread.php?t=113405&highlight=MADWIFI")

This howto will install the latest svn snapshot of the madwifi-ng driver for pci devices based on the atheros chipset. The difference between this and the other [howto]("http://ubuntuforums.org/showthread.php?t=75451i") on madwifi in this section is the other will update to the latest madwifi-old module and this installs madwifi-ng. 
The newer features found in the -ng version can be found [here]("http://madwifi.org/wiki/ngFeatures"). 

This update is not necessary unless 
1. your pci device is not working with current version that comes with breezy.
2. Or you can use if you removed restricted modules to use latest nvidia/fglrx drivers
3. You build a custom kernel but note these instructions do not include steps to properly make and install when using custom kernel. I can add these later as I'm not sure of all steps and currently don't have a custom kernel to work with. If somebody else wants to post some instructions, I'll edit them into the original post.

***Note:*** madwifi does not currently support USB devices with the atheros chipset and the roadmap shows it will be sometime before USB support is built into the driver(version 2.0). You can watch progress at [www.madwifi.org]("http://www.madwifi.org")


[B]Warning:
[/B]The atheros driver that comes with Breezy is part of the restricted-modules package. This will need to be removed before you can install the latest driver. All modules in this package will be removed and may affect areas such as your graphic driver. If you need to use a module in this package then you will also have to recompile and install that module. There are howtos on the latest nvidia and fglrx in the tips and tricks section.

Here are the modules in the restricted-module package

Currently the following modules are included:
 - madwifi (Atheros)
 - fglrx (ATI)
 - nvidia
 - fcdsl, fcdsl2, fcdslsl, fcdslslusb, fcdslusb, fcdslusb2, fcdslusba,
   fcpci, fcpcmcia, fcpcmcia_cs, fcusb, fxusb (AVM ISDN)
 - ltmodem (Winmodem)

[HOWTO: latest fglrx]("http://ubuntuforums.org/showthread.php?t=78466&highlight=fglrx")
[HOWTO: latest nvidia]("http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidia")
[B]
.1 Preperation

[/B]You will need a working internet connection to complete this howto.
Basic knowledge of moving around in the terminal is required
1. Remove the following package
```
sudo apt-get --purge linux-restricted-modules-`uname -r`
``` 2. Install the following packages
```
sudo apt-get install build-essential linux-headers-`uname -r` gcc-3.4 subversion sharutils
``` 

[B]1.0 Download

[/B]```
cd /usr/src
``` 
```
sudo svn checkout http://svn.madwifi.org/trunk madwifi-ng
``` 
move into the directory that was created

```
cd /usr/src/madwifi-ng
``` 
[B]1.1 Build 

[/B]There is an error that comes up if you don't follow this step first.

Open Makefile.inc

```
sudo gedit Makefile.inc
``` 
towards the bottom is a line line that needs to be modified.
[B]
COPTS+=    -Werror

[/B]change this line and remove the -Werror part so line now looks like this.

[B]COPTS+=

[/B]This will not affect driver in anyway, it's just something in the way ubuntu built the kernel for breezy which will prevent installing the driver.

**Note:** *I and others have been able to build, install, and use this driver with no problems but as provided by marcantonio, see about setting up file to ensure gcc-3.4 is used to build driver in this post.*
[http://ubuntuforums.org/showpost.php?p=628632&postcount=35]("http://ubuntuforums.org/showpost.php?p=628632&postcount=35")

Now

```
sudo make
``` 
There will be some warnings but you can ignore those. Look for any errors as these will need to be addressed before moving on to next step.

**1.2 Install**

```
sudo make install
``` 
You may get this warning

```
WARNING:
It seems that there are modules left from previous MadWifi installations.
You should consider removing them before you continue, or else you might
experience problems during operation. Remove old modules?

[l]ist, [r]emove, [i]gnore or e[x]it (l,r,i,[x]) ?
``` 

You should remove with option r

If all goes well your last few lines should look like this.

```
(export MODULEPATH=/lib/modules/2.6.15-8-686/net; depmod -ae)
echo "KERNELRELEASE=2.6.15-8-686" > ./install.log
echo "DESTDIR=" >> ./install.log
``` 

[B]1.3 Insert module

[/B]```
sudo modprobe ath_pci
``` 
[B]1.4 Create the interface

[/B]```
wlanconfig ath0 create wlandev wifi0 wlanmode sta
``` 

You should now have the latest madwifi driver working. Just configure your network and connect.

If it does not then try to restart your network

```
sudo /etc/init.d/networking restart
``` 
or reboot after completing the next step.

[B]2.0 Configure for boot

Edit Feb 4th: With latest driver, this part is no longer needed. Kept in howto for historical reference.[/B]
When you reboot the interface will not be set up. Add a line like this for the interface in the /etc/network/interfaces

pre-up wlanconfig ath0 create wlandev wifi0 wlanmode sta

Example

iface ath0 inet dhcp
pre-up wlanconfig ath0 create wlandev wifi0wlanmode sta
wireless-essid xxxx
wireless-key xxxx


[B]3.0 Uninstall

[/B]If you want to uninstall this module just move back to the directory

```
cd /usr/src/madwifi-ng
``` 
and 

```
 sudo make uninstall
``` 
[B]Notes
[/B]If you want to use wpa encryption with -ng driver you will need latest wpasupplicant. See instructions [here]("http://madwifi.org/wiki/UserDocs/802.11i").

---

### Post by pugs on 2005-12-23
Gave this a shot earlier....Had some errors though and not sure how to correct them.  This is what it spits out at the end:

make[3]: *** [/usr/src/madwifi-ng/net80211/if_media.o] Error 1
make[2]: *** [_module_/usr/src/madwifi-ng/net80211] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/src/madwifi-ng/net80211'
make: *** [modules] Error 1

I dont see anything above it about errors, besides this line:

cc1: warnings being treated as errors

Any help would be greatly appreciated.

---

### Post by Lambert on 2005-12-23
It may not have anything about errors above this but there is more information needed above this. Can you post the entire output after running the command.

---

### Post by pugs on 2005-12-23
Yah, I think I see the problems, but have no idea how to fix them:

root@BigLaptop:/usr/src/madwifi-ng# make
Checking requirements... ok.
Checking kernel configuration... ok.
mkdir -p ./symbols
for i in ./ath_hal ./net80211 ath_rate/sample ./ath; do \
        make -C $i || exit 1; \
done
make[1]: Entering directory `/usr/src/madwifi-ng/ath_hal'
cp -f ./../hal/public/i386-elf.opt_ah.h opt_ah.h
cp -f ./../hal/linux/ah_osdep.c ah_osdep.c
/usr/bin/uudecode ./../hal/public/i386-elf.hal.o.uu
make -C /usr/src/linux-headers-2.6.12-10-686 SUBDIRS=/usr/src/madwifi-ng/ath_hal MODVERDIR=/usr/src/madwifi-ng/ath_hal/../symbols modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-10-686'
  CC [M]  /usr/src/madwifi-ng/ath_hal/ah_osdep.o
  LD [M]  /usr/src/madwifi-ng/ath_hal/ath_hal.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /usr/src/madwifi-ng/ath_hal/.hal.o.cmd for /usr/src/madwifi-ng/ath_hal/hal.o
  CC      /usr/src/madwifi-ng/ath_hal/ath_hal.mod.o
  LD [M]  /usr/src/madwifi-ng/ath_hal/ath_hal.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686'
make[1]: Leaving directory `/usr/src/madwifi-ng/ath_hal'
make[1]: Entering directory `/usr/src/madwifi-ng/net80211'
make -C /usr/src/linux-headers-2.6.12-10-686 SUBDIRS=/usr/src/madwifi-ng/net80211 MODVERDIR=/usr/src/madwifi-ng/net80211/../symbols modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-10-686'
  CC [M]  /usr/src/madwifi-ng/net80211/if_media.o
cc1: warnings being treated as errors
In file included from include/linux/if_ether.h:107,
                 from include/linux/netdevice.h:29,
                 from /usr/src/madwifi-ng/net80211/if_media.c:60:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
make[3]: *** [/usr/src/madwifi-ng/net80211/if_media.o] Error 1
make[2]: *** [_module_/usr/src/madwifi-ng/net80211] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/src/madwifi-ng/net80211'
make: *** [modules] Error 1

---

### Post by Lambert on 2005-12-23
Ok, do this

in user /usr/src/madwifi-ng

open up Makefile.inc

sudo gedit Makefile.inc

towards the bottom you'll see a line COPT   -Werror

erase the -Werror part and save the file.

then sudo make again

You'll see a bunch of warnings in the output but should complete and you can go onto the make install step.

---

### Post by Rob2687 on 2005-12-23
couple of problems

```
robert@linux:~$ sudo apt-get purge linux-restricted-modules-`uname -r`
E: Invalid operation purge
robert@linux:~$

```

```
robert@linux:~$ sudo apt-get install build-essentials linux-headers-`uname -r` gcc-3.4 subversion
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package build-essentials
robert@linux:~$

```

```
robert@linux:/usr/src/madwifi-ng$ sudo make
Checking requirements... FAILED
The 'uudecode' tool was not found on your system. Please make sure
it is installed in your PATH, then try again.
make: *** [sanitycheck] Error 1

```

---

### Post by Lambert on 2005-12-23
errors in my entry and didn't double check.

change purge to  --purge

change build-essentials to build-essential

---

### Post by pugs on 2005-12-23
Thanks.  Its up and working now.  I just have one question...well probably alot more, but the main one is this one.  What does this do:

wlanconfig ath0 create wlandev wifi0 wlanmode sta

When do that and get the network started up...when I run "ifconfig" I have 2 listings.  One is ath0 and one is wifi0.  Maybe I just dont fully understand the way madwifi works.  When I originally installed kubuntu, I only had ath0.  All is well and working, just trying to figure out what the extra one does and if I need to ever refer to it for example when setting up the wpa_supplicant....

It seems like I have to refer to ath0 when issuing ifup or ifdown as they dont seem to think wifi0 exists, probably because it doesnt have an entry in interfaces...

---

### Post by Lambert on 2005-12-23
[quote=pugs]Thanks.  Its up and working now.  I just have one question...well probably alot more, but the main one is this one.  What does this do:

wlanconfig ath0 create wlandev wifi0 wlanmode sta


When do that and get the network started up...when I run "ifconfig" I have 2 listings.  One is ath0 and one is wifi0.  Maybe I just dont fully understand the way madwifi works.  When I originally installed kubuntu, I only had ath0.  All is well and working, just trying to figure out what the extra one does and if I need to ever refer to it for example when setting up the wpa_supplicant....

It seems like I have to refer to ath0 when issuing ifup or ifdown as they dont seem to think wifi0 exists, probably because it doesnt have an entry in interfaces...[/quote] 
Madwifi-ng has some interesting work going into to. I don't know of another driver doing what they are doing but I also don't follow all drivers.

I might not explain this properly but this is how I understand it so far.

wifi0 is a base interface that sits on top of the driver. When you ran the wlanconfig command it builds an interface ontop of the wifi0 interface. With the madwifi device you can build multiple interfaces ontop of the wifi0 base so your card can run in multiple ways at the same time. Your card can be an ap for others while also runing in stationary client mode where it's connected to a router. You can run multiple aps at one time. 


For a typical home owner none of this is necessary as they just need a single interface to connect to a router but it adds flexibility for certain users/situations.

So to answer your question what does the wlanconfig command do? it sets up an interface, assigns the name ath0 and sets it up in station mode.

If you decide to look more into wpa it will be on the ath0 interface and not on thewifi0 interface.

[http://madwifi.org/wiki/UserDocs/WPA_PSK_on_Both_Ends]("http://madwifi.org/wiki/UserDocs/WPA_PSK_on_Both_Ends")

I haven't played with this yet but I don't believe you have to compile the latest wpasupplicant, you may be able to use wpasupplicant from the repositories.

---

### Post by pugs on 2005-12-24
That makes quite a bit of sense...thanks alot.

I did think up another question for you.  I know the -ng is supposed to add some extra "enhanced" features...  The main ones that might be of interest at least to me are things like SuperG mode...Is it possible to run up to 108 Mbps or not yet?  The other one is the XR to gain some distance from the router, not a biggy for me, but some might find it useful.

There is some info here about changing some of the modes but I think the -ng might be different:

[http://madwifi.org/wiki/FAQ/HowDoI](http://madwifi.org/wiki/FAQ/HowDoI)

There it mentions putting it into mode 3, however with the -ng drivers I have now, when I do: iwpriv ath0 get_mode it returns 11g instead of just an integer...looks like it is a 6 character string now.  Also, get_turbo returns 1.  However my Router doesnt have a setting for static turbo mode so I may not be able to see higher speeds anyway.

---

### Post by pugs on 2005-12-24
[QUOTE=pugs]That makes quite a bit of sense...thanks alot.

I did think up another question for you.  I know the -ng is supposed to add some extra "enhanced" features...  The main ones that might be of interest at least to me are things like SuperG mode...Is it possible to run up to 108 Mbps or not yet?  The other one is the XR to gain some distance from the router, not a biggy for me, but some might find it useful.

There is some info here about changing some of the modes but I think the -ng might be different:

[http://madwifi.org/wiki/FAQ/HowDoI](http://madwifi.org/wiki/FAQ/HowDoI)

There it mentions putting it into mode 3, however with the -ng drivers I have now, when I do: iwpriv ath0 get_mode it returns 11g instead of just an integer...looks like it is a 6 character string now.  Also, get_turbo returns 1.  However my Router doesnt have a setting for static turbo mode so I may not be able to see higher speeds anyway.[/QUOTE]

Well as usual, I am a moron.  There is a nice users guide in the docs directory included with the madwifi-ng source.  It answers alot of this.  Apparently Mode 6 is what you want for 11g with dynamic turbo.  But either it is not implemented yet or I have issues.  I am guessing the former since I can switch from mode 3 to 2 and back easily enough.  When I try to go to mode 6 I get this:

root@BigLaptop:/usr/src/madwifi-ng/docs# iwpriv ath0 mode 6
Interface doesn't accept private ioctl...
mode (8BE2): Invalid argument

Yes, I got sick of typing sudo...especially on something I will probably end up reinstalling a few times before I get a nice clean install that I want to use ;)

---

### Post by pugs on 2005-12-24
[QUOTE=Rob2687]robert@linux:/usr/src/madwifi-ng$ sudo make
Checking requirements... FAILED
The 'uudecode' tool was not found on your system. Please make sure
it is installed in your PATH, then try again.
make: *** [sanitycheck] Error 1
[/QUOTE]

Sorry I missed this earlier.  I just used Adept for all the package install/removal.  If you have all the repositories enabled and type in uudecode it should sniff out the package you need.  Well, you made me do it...the package that contains it is **sharutils**

Also, if you plan to us ifup/ifdown you will probalby want to add something like:

post-down wlanconfig ath0 destroy

to the interfaces file.  I ran into a little problem with that while trying to get WPA-PSK running...still no luck with that.  There are some wpa settings accessible through iwpriv but I do not know if that affects using the card as a station or as an access point...I guess 128 bit wep will have to do for now...

---

### Post by Rob2687 on 2005-12-24
Yeah, I get an error with wpa_supplicant
"Association request to the driver failed"
It seems to have a problem associating with the AP or something. If I set ap_scan in wpa_supplicant.conf to 2 then it like half associates with the ap or something O_o ... iwconfig will show the right essid and give a signal strength but the mac address says 00:00:00:00...

---

### Post by Lambert on 2005-12-24
Have you looked at this?

[https://wiki.ubuntu.com/WPAHowto](https://wiki.ubuntu.com/WPAHowto)

---

### Post by pugs on 2005-12-24
[QUOTE=Lambert]Have you looked at this?

[https://wiki.ubuntu.com/WPAHowto](https://wiki.ubuntu.com/WPAHowto)[/QUOTE]

That is the one I tried following this time around.  I am not sure where they are going from with that.  They say to "Now simply start wpa_supplicant in debug mode for testing" well they dont mention if you should shutdown the connection or have it running or what.  I tried it a few different ways, but may not have tried all combinations.  I dont know if they are starting with a working wireless connection or what...I will give it another shot when I get some time.

---

### Post by Rob2687 on 2005-12-24
Only the latest stable version of wpasupplicant has support for madwifi-ng.
Edit: yup, recompiling did the trick.

---

### Post by Vetto on 2005-12-25
```
 root@harpoonix:/usr/src/madwifi-ng# wlanconfig ath0 create wlandev wifi0 wlanmode sta
wlanconfig: ioctl: No such device
```

?? what does this mean

Nevermind...rebooted and then the command worked.

I do however have an ath0 and a wifi0 interfaces both.  Only the ath0 has wireless extensions though...

---

### Post by pugs on 2005-12-25
[QUOTE=Rob2687]Only the latest stable version of wpasupplicant has support for madwifi-ng.
Edit: yup, recompiling did the trick.[/QUOTE]

So did you have to download wpasupplicant and compile it yourself?

---

### Post by Rob2687 on 2005-12-25
[QUOTE=pugs]So did you have to download wpasupplicant and compile it yourself?[/QUOTE]

Yes.
I followed the madwifi wiki posted a few posts back.

If you still want to wpasupplicant service to start at bootup, make install will put the new wpasupplicant in /usr/local/bin so you need to edit /etc/init.d/wpasupplicant and add that folder to the file.

---

### Post by Vetto on 2005-12-28
[QUOTE=Lambert]
[B]2.0 Configure for boot
[/B]When you reboot the interface will not be set up. Add a line like this for the interface in the /etc/network/interfaces

pre-up wlanconfig ath0 create wlandev wifi0 wlanmode sta

Example

iface ath0 inet dhcp
pre-up wlanconfig ath0 create wlandev wifi0wlanmode sta
wireless-essid xxxx
wireless-key xxxx
[/QUOTE]

This got my Netgear WG511T pccard working finally, but upon bootup it hangs at "configuring network interfaces"... eventually reports OK then FAILS at "Waiting for network interfaces to come up"

All I have to do to get it up is press the "activate" button in kcmwifi (KDE3.5) once the system is loaded.  ANy ideas?

---

### Post by Lambert on 2005-12-29
Post your interfaces file here minus the personal data. 

I also see a typo in my example. there should be a space between wifi0 wlanmode

I'm not sure if your earlier question was answered.
wifi0 is actually a base interface on top of the driver. This interface doesn't connect to anything except an interface that is created.  The command you use builds a station interface on top of that so you can connect to your ap. The design of the madwifi driver allows you to build multiple interfaces and run the wireless device in multiple modes and ways at the same time. For a typical home user, nothing important, the command gives you an interface to connect to your home router. For more complex networking enviroments, lots of flexibility to ensure connection and productivity.

---

### Post by Vetto on 2005-12-29
Hereis my interfaces file:

```
# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

iface ath0 inet dhcp
pre-up wlanconfig ath0 create wlandev wifi0 wlanmode sta
wireless-essid AcmeRockets
wireless-key **********

auto ath0
```

I have to hit "activate" in kde's applet and also "dhclient ath0" to get online every time.

---

### Post by Lambert on 2005-12-29
Try this

remove the auto ath0 line from the file

and underneath the map eth0 add

map ath0

---

### Post by Vetto on 2005-12-29
[QUOTE=Lambert]Try this...[/QUOTE]

will do, wll repost in a couple hours when i can reboot.

thanks

---

### Post by Vetto on 2005-12-29
OK.  With those changes in the interfaces file, the ath0 interface is no longer there. (although the bootup is faster)

I removed the changes, it is back to what I posted earlier.
I ran iwconfig after the system was up:

**Before configuring with kcmwifi**
```
ath0      IEEE 802.11g  ESSID:"AcmeRockets"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

**After configuring with kcmwifi**
```
ath0      IEEE 802.11g  ESSID:"AcmeRockets"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:09:5B:47:B5:F6   
          Bit Rate=11 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:*edited*   Security mode:restricted
          Power Management:off
          Link Quality=36/94  Signal level=-59 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Is there another file that KDE uses for this configuration other than the standard interfaces file?  Seems like the security mode and the channel is not configuring automatically.

---

### Post by stanwebber on 2005-12-29
do i need to remove gcc 4 & compile this module with gcc 3.4 for breezy?  the makefile isn't accepting requests to use gcc 3.4 instead

---

### Post by Lambert on 2005-12-29
[quote=Vetto]
Is there another file that KDE uses for this configuration other than the standard interfaces file?  Seems like the security mode and the channel is not configuring automatically.[/quote]

I'm not familiar with kde so I'm not sure. kcmwifi very well could pull from another file as I believe most thirdparty type wireless management software does.

But as far as start up it's either networking or hotplug that starts the card.

(auto ath0 starts during networking and map ath0 starts during hotplug but it made it worse for you so ??) (pcmcia cards usually require hotplug to start and not networking)

You can try to add some lines to your interface file.

wireless-enc on
wireless-channel __
wireless-mode managed
wireless-key [open | restricted] (pick one of these and don't use brackets or pipe)

---

### Post by Lambert on 2005-12-29
[quote=stanwebber]do i need to remove gcc 4 & compile this module with gcc 3.4 for breezy?  the makefile isn't accepting requests to use gcc 3.4 instead[/quote]

I didn't have to remove gcc-4 so it shouldn't be a problem. Post the last 30 lines that you get before it exits.

Have you done any other customization or is it just the stock breezy install?

---

### Post by pugs on 2005-12-31
I would try setting your wireless channel in the interfaces file.  It seems that when you run wlanconfig before kcmwifi ath0 is using a different channel at the time then it is after you run kcmwifi.

I did not remove GCC 4, but I did have to add GCC 3.4 to my kubuntu install to get everything to compile happily...

---

### Post by Vetto on 2005-12-31
[QUOTE=pugs]I would try setting your wireless channel in the interfaces file.  It seems that when you run wlanconfig before kcmwifi ath0 is using a different channel at the time then it is after you run kcmwifi.[/QUOTE]

ok, now i am on the correct channel and ap...but i cannot get an ip (dhcp).

Here is the differences in the pre kcmwifi and post kcmwifi:

before:```
 Encryption key:9B51-0DF0-F8   Security mode:restricted
```

After:```
Encryption key:9B51-0DF0-F8 [4]   Security mode:restricted

```

In the ap, i have 4 keys and i am using key 4..thus the [4] after the key in the post-kcmwifi iwconfig.  is this relevant?  After running kcmwifi I obviously can get an IP, but still not before.

since this is getting off-topic, please post reply to [http://www.ubuntuforums.org/showthread.php?t=110745]("http://www.ubuntuforums.org/showthread.php?t=110745")

---

### Post by ephman on 2006-01-01
hi,

odd situation, didn't see a fix for it in the forums here, but i'll ask anyhow.  i followed the instructions but now it seems that whenever i have a lot of connections it drops my connection to the router.  i've tried this on a few different routers and the same thing occurs.  now mind you i have a custom kernel, and know that there it isn't listed in this HOWTO configure for a custom kernel but the card works just fine when i'm going to webpage to webpage, the moment i turn on a bittorrent kabang it shuts down.  i know it's a longshot but any ideas???

thanks,
ephman

---

### Post by Lambert on 2006-01-01
When this happens check the /var/log/syslog file and post any lines related.

---

### Post by ephman on 2006-01-01
[QUOTE=Lambert]When this happens check the /var/log/syslog file and post any lines related.[/QUOTE]

hi,

ok, here's the syslog output:

Jan  1 15:26:27 localhost kernel: [4294793.421000] ath0: no IPv6 routers present
Jan  1 15:26:27 localhost kernel: [4294794.077000] wifi0: no IPv6 routers present
Jan  1 15:26:47 localhost dhclient: Internet Systems Consortium DHCP Client V3.0.2
Jan  1 15:26:47 localhost dhclient: Copyright 2004 Internet Systems Consortium.
Jan  1 15:26:47 localhost dhclient: All rights reserved.
Jan  1 15:26:47 localhost dhclient: For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
Jan  1 15:26:47 localhost dhclient: 
Jan  1 15:26:47 localhost dhclient: sit0: unknown hardware address type 776
Jan  1 15:26:47 localhost dhclient: sit0: unknown hardware address type 776
Jan  1 15:26:47 localhost kernel: [4294814.165000] NET: Registered protocol family 17
Jan  1 15:26:47 localhost dhclient: Listening on LPF/ath0/00:20:a6:4b:e6:bf
Jan  1 15:26:47 localhost dhclient: Sending on   LPF/ath0/00:20:a6:4b:e6:bf
Jan  1 15:26:47 localhost dhclient: Sending on   Socket/fallback
Jan  1 15:26:47 localhost dhclient: DHCPREQUEST on ath0 to 255.255.255.255 port 67
Jan  1 15:26:54 localhost dhclient: DHCPREQUEST on ath0 to 255.255.255.255 port 67
Jan  1 15:26:54 localhost dhclient: DHCPACK from 192.168.1.1
Jan  1 15:26:54 localhost dhclient: bound to 192.168.1.39 -- renewal in 34643 seconds.
Jan  1 15:26:57 localhost kernel: [4294824.226000] wifi0: no IPv6 routers present
Jan  1 15:26:58 localhost kernel: [4294824.593000] ath0: no IPv6 routers present
Jan  1 15:27:25 localhost gconfd (root-8091): GConf server is not in use, shutting down.
Jan  1 15:27:25 localhost gconfd (root-8091): Exiting
Jan  1 15:29:29 localhost gconfd (root-8647): starting (version 2.12.0), pid 8647 user 'root'
Jan  1 15:29:29 localhost gconfd (root-8647): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jan  1 15:29:29 localhost gconfd (root-8647): Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only configuration source at position 1
Jan  1 15:29:29 localhost gconfd (root-8647): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 2
Jan  1 15:29:29 localhost gconfd (root-8647): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
Jan  1 15:29:29 localhost gconfd (root-8647): Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4
Jan  1 15:29:29 localhost gconfd (root-8647): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Jan  1 15:29:29 localhost gconfd (root-8647): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
Jan  1 15:29:29 localhost gconfd (root-8647): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
Jan  1 15:29:30 localhost kernel: [4294976.770000] ip_conntrack version 2.1 (3070 buckets, 24560 max) - 248 bytes per conntrack
Jan  1 15:29:31 localhost kernel: [4294978.179000] Inbound IN=ath0 OUT= MAC=00:20:a6:4b:e6:bf:00:0f:db:42:2c:78:08:00:45:00:05:d4:f3:a6:40:00:74:06:6a:f1:d4:9f:0c:1d:c0:a8:01:27:1a:e1:ac:8f:cd:6b:66:bf:eb:98:6d:90:80:18:3f:af:46:45:00:00:01:01:08:0a:00:05:f2:8a:00:00:20:3b:78:fb:96:43:58:80:b9:02:0a:17:8e:f4:7f:e4:4b:d3:38:d3:39:91:bc:4c SRC=212.159.12.29 DST=192.168.1.39 LEN=1492 TOS=0x00 PREC=0x00 TTL=116 ID=62374 DF PROTO=TCP SPT=6881 DPT=44175 WINDOW=16303 RES=0x00 ACK PSH URGP=0 
Jan  1 15:29:31 localhost kernel: [4294978.310000] Inbound IN=ath0 OUT= MAC=00:20:a6:4b:e6:bf:00:0f:db:42:2c:78:08:00:45:00:05:d4:23:05:40:00:6b:06:78:36:c1:5c:eb:bc:c0:a8:01:27:1a:e1:96:5b:e7:df:b1:0e:ea:68:c2:fc:80:10:3f:87:82:04:00:00:01:01:08:0a:00:01:22:71:00:00:23:4f:00:00:40:15:00:00:00:08:42:54:5f:50:49:45:43:45:01:00:00:04:34:00 SRC=193.92.235.188 DST=192.168.1.39 LEN=1492 TOS=0x00 PREC=0x00 TTL=107 ID=8965 DF PROTO=TCP SPT=6881 DPT=38491 WINDOW=16263 RES=0x00 ACK URGP=0
Jan  1 15:29:31 localhost kernel: [4294978.311000] Inbound IN=ath0 OUT= MAC=00:20:a6:4b:e6:bf:00:0f:db:42:2c:78:08:00:45:00:00:a0:66:cf:40:00:72:06:8e:87:18:5b:38:d7:c0:a8:01:27:c0:00:89:12:4a:ff:11:18:e7:07:d7:09:80:18:fb:c4:e4:d3:00:00:01:01:08:0a:00:90:cb:55:00:00:21:8b:38:2b:b2:f2:e5:75:56:e3:77:d8:7f:e6:23:eb:ad:a6:d5:bb:65:ee:da:4e SRC=24.91.56.215 DST=192.168.1.39 LEN=160 TOS=0x00 PREC=0x00 TTL=114 ID=26319 DF PROTO=TCP SPT=49152 DPT=35090 WINDOW=64452 RES=0x00 ACK PSH URGP=0 
Jan  1 15:29:32 localhost kernel: [4294978.415000] Inbound IN=ath0 OUT= MAC=00:20:a6:4b:e6:bf:00:0f:db:42:2c:78:08:00:45:00:05:d4:23:06:40:00:6b:06:78:35:c1:5c:eb:bc:c0:a8:01:27:1a:e1:96:5b:e7:df:b6:ae:ea:68:c2:fc:80:10:3f:87:da:ae:00:00:01:01:08:0a:00:01:22:71:00:00:23:4f:f9:e1:24:21:7d:5a:91:28:0f:17:97:04:20:65:7e:1d:fc:0e:78:78:10:e7 SRC=193.92.235.188 DST=192.168.1.39 LEN=1492 TOS=0x00 PREC=0x00 TTL=107 ID=8966 DF PROTO=TCP SPT=6881 DPT=38491 WINDOW=16263 RES=0x00 ACK URGP=0 
Jan  1 15:29:32 localhost kernel: [4294978.504000] Inbound IN=ath0 OUT=


also, something i noticed that might or might not make sense is that when i try to boot into this custom kernel i have (2.6.12-10-686), madwifi doesn't fire up.  i have to do it manually.  here's my interfaces file:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

iface ath0 inet static
wireless-essid neuromancer
address 192.168.0.99
netmask 255.255.255.0
gateway 192.168.0.1


auto ath0


now i also tried to include:

wlanconfig ath0 create wlandev wifi0 wlanmode sta

but that didn't work to start it up at boot time.

thanks,
ephman

---

### Post by ephman on 2006-01-04
anything please for the above post?

---

### Post by marcantonio on 2006-01-04
First, thanks for a great HOWTO.

I would recommend using gcc 3.4 to compile the modules as the default kernel in breezy is compiled with that version.  On a stock breezy system gcc is symlinked to gcc-4, even if you install gcc 3.4 as above.  The easiest way to use gcc 3.4 is to edit madwifi-ng/hal/public/i386-elf.inc and change this line:
```
CC=    ${TOOLPREFIX}gcc
```
to this:
```
CC=    ${TOOLPREFIX}gcc-3.4
```

This also removes the need to edit Makefile.inc, as in the HOWTO.

---

### Post by Lambert on 2006-01-04
ephman,

As far as torent and dropping connection I don't know. You will need to ask/look around the madwifi development for an answer. Maybe check the irc.

When you say it doesn't start on boot, do you get an ath0 interface or do you have to run the wlanconfig command to create that interface?

I use a simple pre-up wlanconfig ath0 create wlandev wifi0 wlanmode sta to create the interface and don't have any problems. If this isn't working for you then you can try this.

The following creates an ath0 interface with a udev rule.

create this file

```
 sudo touch  /etc/udev/rules.d/65-madwifi.rules
```

change permissions

```
sudo chmod 777 /etc/udev/rules.d/65-madwifi.rules
```

add these lines to it

```

# Madwifi devices
#
# See wlanconfig(8) for more information
#
# Access Point configuration
#KERNEL=="wifi[0-9]*", DRIVER=="ath_pci", ACTION=="add", RUN+="/sbin/wlanconfig ath create wlandev %k wlanmode ap"
#
# Normal station configuration
KERNEL=="wifi[0-9]*", DRIVER=="ath_pci", ACTION=="add", RUN+="/sbin/wlanconfig ath create wlandev %k wlanmode sta"
```

notice the line not commented. This creates the ath0 interface at boot with a udev rule for client station mode.

Something else to consider. Some pcmcia devices load with hotplug and not networking. remove the auto ath0 line and add a map ath0 line under the mapping hotplug section.

---

### Post by cheuschober on 2006-01-09
Hi. Great guide - very thorough and very clear.

One question, though: how would one completely undo all of this and remove the madwifi snapshot and return to the previous version?

Running a Toshiba Satellite A45 with what lshow claims is an atheros 5212 abg -- now, that seems a little odd to me if only because never do I ever remember having 802.11a functionality or even remember it being advertised but 'eh.

In any case, installation was simple -- and it worked, amazingly. So amazingly, in fact, I was able to use WEP encryption which was until this point, impossible with my laptop even under M$W. Of course, at some point or another while configuring my fresh Breezy installation I had to restart and when I did it stopped working. I still get wifi0 as  being related to my card but with no more ath0 and an lshow now lists my wireless card as being 'Unclaimed' by any driver. I've got to admit this has happened before and it confuses the h*** outta me as to how/why linux can just lose a piece of hardware like that.

I'd like to restore to pre-madwifi-ng and then try it again but admittedly don't know how (utter newb). At this point, with a couple of weeks of sitting in the corner of my living room (where the router is), facing a wall with my 3ft lan cable -- I just don't have the heart to go through yet another fresh ubuntu installation and spend another two weeks trying  to get this up. :-p

I was curious if a driver could be forced on a device but I guess that's really not an option so a complete uninstallation seems to be the solution?

Best and thanks for any help offered,
~C

---

### Post by Lambert on 2006-01-09
[quote=marcantonio]First, thanks for a great HOWTO.

I would recommend using gcc 3.4 to compile the modules as the default kernel in breezy is compiled with that version.  On a stock breezy system gcc is symlinked to gcc-4, even if you install gcc 3.4 as above.  The easiest way to use gcc 3.4 is to edit madwifi-ng/hal/public/i386-elf.inc and change this line:
```
CC=    ${TOOLPREFIX}gcc
``` to this:
```
CC=    ${TOOLPREFIX}gcc-3.4
``` 
This also removes the need to edit Makefile.inc, as in the HOWTO.[/quote]

hmmm, interesting. If kernel is compiled with 3.4, can a module be compiled with a different compiler and still work? Doesn't the install script recognize the kernel's compile version and export the correct compiler into the variables?

If someone would answer or I'll research when I get a chance.

---

### Post by ephman on 2006-01-09
[QUOTE=Lambert]
I use a simple pre-up wlanconfig ath0 create wlandev wifi0 wlanmode sta to create the interface and don't have any problems. If this isn't working for you then you can try this.

The following creates an ath0 interface with a udev rule.

create this file

```
 sudo touch  /etc/udev/rules.d/65-madwifi.rules
```

change permissions

```
sudo chmod 777 /etc/udev/rules.d/65-madwifi.rules
```

add these lines to it

```

# Madwifi devices
#
# See wlanconfig(8) for more information
#
# Access Point configuration
#KERNEL=="wifi[0-9]*", DRIVER=="ath_pci", ACTION=="add", RUN+="/sbin/wlanconfig ath create wlandev %k wlanmode ap"
#
# Normal station configuration
KERNEL=="wifi[0-9]*", DRIVER=="ath_pci", ACTION=="add", RUN+="/sbin/wlanconfig ath create wlandev %k wlanmode sta"
```

notice the line not commented. This creates the ath0 interface at boot with a udev rule for client station mode.
[/QUOTE]

did the trick thanks,

ephman

---

### Post by Lambert on 2006-01-09
[quote=cheuschober]

I'd like to restore to pre-madwifi-ng and then try it again but admittedly don't know how (utter newb). At this point, with a couple of weeks of sitting in the corner of my living room (where the router is), facing a wall with my 3ft lan cable -- I just don't have the heart to go through yet another fresh ubuntu installation and spend another two weeks trying  to get this up. :-p

~C[/quote]

It is possible to force a driver to bind to a device but in this case you would have two of the same drivers installed but different versions so there would be a conflict.

To remove the -ng version just go into the original directory where you built and installed the driver and type this command.

```
sudo make uninstall
```

---

### Post by cheuschober on 2006-01-09
[QUOTE=Lambert]It is possible to force a driver to bind to a device but in this case you would have two of the same drivers installed but different versions so there would be a conflict.
[/QUOTE]

Thanks for the help. Uninstalled, tried the old driver to no avail. Uninstalled that and reinstalled madwifi-ng but my device is still unclaimed -- how would one go about this binding? If the os is too ignorant to know what hardware it has I feel it's my duty to inform it.

Output of: sudo lshw -C network 
```

*-network:0 UNCLAIMED
       description: Ethernet controller
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 5
       bus info: pci@01:05.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       resources: iomemory:cfff0000-cfffffff irq:22
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@01:08.0
       logical name: eth0
       version: 83
       serial: 00:08:0d:ee:84:d0
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.4.8-k2-NAPI duplex=full firmware=N/A ip=192.168.221.101 link=yes multicast=yes port=MII speed=100MB/s
       resources: iomemory:cffef000-cffeffff ioport:cf40-cf7f irq:20

```

Output of:  lspci -vvx -s 01:05.0
```

0000:01:05.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
        Subsystem: Askey Computer Corp.: Unknown device 7058
        Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 22
        Region 0: Memory at cfff0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <available only to root>
00: 8c 16 13 00 02 00 90 02 01 00 00 02 08 a8 00 00
10: 00 00 ff cf 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 01 50 00 00 4f 14 58 70
30: 00 00 00 00 44 00 00 00 00 00 00 00 0b 01 0a 1c

```

Thank you for any an all of your assistance! This worked once before using the madwifi-ng drivers! I have to believe it can happen again.

Best,
~Chad

---

### Post by marcantonio on 2006-01-10
[QUOTE=Lambert]hmmm, interesting. If kernel is compiled with 3.4, can a module be compiled with a different compiler and still work? Doesn't the install script recognize the kernel's compile version and export the correct compiler into the variables?

If someone would answer or I'll research when I get a chance.[/QUOTE]

Compiling a kernel and a kernel module with two different versions of GCC can cause problems, of that I'm sure.  Frankly, I'm surprised things work so well in this case.

As far as the autodetecting the right version of GCC to use, it definately doesn't in this case.  It just takes gcc out of your path.  I've seen GCC version detecting done in ./configure scripts, but not detection of the kernel compiler.

---

### Post by Lambert on 2006-01-10
Is this a pcmcia card? or internal mini-pci device?

If it's a pcmcia device I'd like to unplug it and see what the output of dmesg is. Or if you can run dmesg and dig through the part where the wireless is being activated to see why it's not binding automatically. It should and there may be a problem.


Otherwise try this 

```
sud modprobe ath_pci
```

then rerun the lshw command to see if it has changed at all.

---

### Post by cheuschober on 2006-01-10
[QUOTE=Lambert]Is this a pcmcia card? or internal mini-pci device?

If it's a pcmcia device I'd like to unplug it and see what the output of dmesg is. Or if you can run dmesg and dig through the part where the wireless is being activated to see why it's not binding automatically. It should and there may be a problem.


Otherwise try this 

```
sud modprobe ath_pci
```

then rerun the lshw command to see if it has changed at all.[/QUOTE]

Not sure if this was directed at me but hoping it was cause I sure do need the assist! :-D My device is most certainly an internal mini-pci. The sudo modprobe ath_pci has returned no change in the binding.

Here's the portion of the dmesg I expect you were referring to:

```
[4295886.833000] ath_hal: module license 'Proprietary' taints kernel.
[4295886.837000] ath_hal: 0.9.16.13 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413, DFS)
[4295886.851000] wlan: 0.8.4.2 (Atheros/multi-bss)
[4295886.899000] ath_rate_sample: 1.2
[4295886.904000] ath_pci: 0.9.4.5 (Atheros/multi-bss)
[4295886.906000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 22 (level, low) -> IRQ 22
[4295886.907000] wifi%d: unable to attach hardware: 'Hardware didn't respond as expected' (HAL status 3)
[4295886.907000] ACPI: PCI interrupt for device 0000:01:05.0 disabled

```

The 5212 is an a/b/g model as far as I know and I am 90% certain that what I have is just the b/g model (the 5004 or similar I think -- anyone want to confirm?). I've had problems with drivers and this particular card from day one no matter what OS I've used -- I will pull out the screwdriver later tonight to take a look at the chipset itself and see what that says, but let's, as an exercise, assume that this is actually a different atheros chipset but one still supported in the madwifi module... are there ways to force the module to see it as the 'correct' chipset?

Many thanks!
~Chad

Edit: Just checked the chipset--much to my surprise it is most definately an AR5212A... so where would I best go from here?

---

### Post by Lambert on 2006-01-11
[QUOTE=cheuschober]Not sure if this was directed at me but hoping it was cause I sure do need the assist! :-D 

 I've had problems with drivers and this particular card from day one no matter what OS I've used -- [/QUOTE]

With the dmesg output I don't believe it's your device or the driver. See this link.

[(hal status 3)]("http://madwifi.org/wiki/UserDocs/Troubleshooting#WhenIloadtheath_pcimoduleIgetunabletoattachhardware:HardwaredidntrespondasexpectedHALstatus3")

---

### Post by cheuschober on 2006-01-11
[QUOTE=Lambert]With the dmesg output I don't believe it's your device or the driver. See this link.

[(hal status 3)]("http://madwifi.org/wiki/UserDocs/Troubleshooting#WhenIloadtheath_pcimoduleIgetunabletoattachhardware:HardwaredidntrespondasexpectedHALstatus3")[/QUOTE]

It works! And reliably too for the last 5 hours amidst restarts and a general wifi-stress test I put it through! I'm so happy I could kiss ya Lambert! Heh! Thank you so very very much. It -was- that particular issue.

Thanks again for all your hard work!
~Chad

---

### Post by ErikTheRed on 2006-01-13
Having a similar problem to others in this thread, where my card does not associate properly.

When I do iwconfig ath0 is associated with my wifi network, but it doesn't show the MAC address. When i try to have wpa_supplicant run manually instead of using wpa_supplicant.conf, i get the following:

> Trying to associate with SSID 'Spaceball One'
Authentication with 00:00:00:00:00:00 timed out.


I am trying to use WPA Supplicant, maybe that makes a difference?

---

### Post by Lambert on 2006-01-13
Breezy comes with wpasupplicant 0.4.5 and -ng needs 0.4.7 so which version are you using?

Also have you tried these instructions?

[http://madwifi.org/wiki/UserDocs/802.11i](http://madwifi.org/wiki/UserDocs/802.11i)

I can't be much help with wpa as it's not warranted in my situation so I haven't tried using it yet, some day when I'm bored and the family doesn't need internet access:smile:

---

### Post by ErikTheRed on 2006-01-16
I think I got WPA working, but the start-up script doesn't seem to work. Any alternatives? I'm really inexperienced with startup scripts, so I'll need help.

EDIT: Well, I actually don't have wpa_supplicant working correctly. But I'm content using WEP for now. Still need help with the start-up script.

---

### Post by Lambert on 2006-01-16
[quote=ErikTheRed]I think I got WPA working, but the start-up script doesn't seem to work. Any alternatives? I'm really inexperienced with startup scripts, so I'll need help.

EDIT: Well, I actually don't have wpa_supplicant working correctly. But I'm content using WEP for now. Still need help with the start-up script.[/quote]

You may want to start a new thread in networking or another section so more people see this and can help you with wpa or the script.

---

### Post by cheuschober on 2006-02-02
More troubles abrew...

It was brilliant! It worked! For about 5 hours. :( 

Since then I've gone through three full re-installations of ubuntu just to test a theory -- every installation has treated my hardware slightly differently with no changes from my end. Twice the 386 kernel was installed by default and once the 686 kernel was installed by default. As it pertains to wireless in some cases it didn't recognize the A5212 at all others, like the last case, recognized it out of the box until the first /etc/init.d/networking restart was necessary and then fully cashed out and refused to work. Since then I've removed the pre-packaged madwifi and went through the madwifi-ng which took me by surprise and worked for a total of 7 minutes and then ceased communicating. I've tried everything I could think of but two major problems persist.

The first is that any virtual interfaces created over wifi0 utterly ignore whatever is found in my /etc/network/interfaces file. I can have "iface ath0 inet static... etc" and issue a "wlanconfig ath0 create..." to successfully create ath0 as an interface but none of the information found in the interfaces file is being used. In fact once or twice (but not consistently) after destroying / recreating / ifup / 'generally fiddling with' it has adopted the settings of a considerably older ath0 interface (one I deleted from /etc/network/interfaces weeks ago).

The second issue is this strange behaviour where after ifconfig'ing and iwconfig'ing my way to a 'working' interface I find myself capable of pinging my own interface and pinging the router but incapable of anything more. A ping to [www.yahoo.com](www.yahoo.com) elicits an "Uknown Host" message most of the time and occasionally "Network not found." Now, I'm no network genius but this sounds like a DNS issue, yes? The funny thing is every other computer on the network is working perfectly with the router so I have little cause to believe it's the router.

Any thoughts / advice / help are always appreciated.

~Chad

---

### Post by Lambert on 2006-02-03
Not sure if I have much to offer in this situation but here are my thoughts.


The driver is just an interface between the kernel and the device so they can communicate with each other. If you can activate the card, set a static ip and ping the device (and the router as you stated in problem 2), you have a working driver.

It is in the kernel and other apps such as wireless tools that works with the kernel to configure and manage the networking settings. This is where I believe your problems lie.



So now to problem number 1

> The first is that any virtual interfaces created over wifi0 utterly ignore whatever is found in my /etc/network/interfaces file. I can have "iface ath0 inet static... etc" and issue a "wlanconfig ath0 create..." to successfully create ath0 as an interface but none of the information found in the interfaces file is being used. In fact once or twice (but not consistently) after destroying / recreating / ifup / 'generally fiddling with' it has adopted the settings of a considerably older ath0 interface (one I deleted from /etc/network/interfaces weeks ago)

I would like to see your interface file if you wouldn't mind posting. XXX out any personal data. You did say using static in the comment. I don't know if there is a cache somewhere when using static but with dhcp if there is no dhcp packet received, there is a cache it will revert and try to use.


Problem 2
> The second issue is this strange behaviour where after ifconfig'ing and iwconfig'ing my way to a 'working' interface I find myself capable of pinging my own interface and pinging the router but incapable of anything more. A ping to [www.yahoo.com](www.yahoo.com) elicits an "Uknown Host" message most of the time and occasionally "Network not found." Now, I'm no network genius but this sounds like a DNS issue, yes? The funny thing is every other computer on the network is working perfectly with the router so I have little cause to believe it's the router.

If you're using static ip addressing, have you set up name servers to resolve name look up? post output of the resolv.conf file. Also try to ping yahoo via the ip address of yahoo instead of domain name?

cat /etc/resolv.conf

Also try to ping yahoo via the ip address of yahoo instead of domain name?

If you have a working winxp box you can compare what's here with what the winxp box says. ON winxp use the ipconfig /all command to show you the information.


This is not a driver problem so if you wouldn't mind starting a new thread under the networking section I or someone else can help you there. You may just want to link back to your post here and mention you started discussing your problems there.

---

### Post by cheuschober on 2006-02-05
Thanks Lambert. I've posted the requested outputs at a [new thread found here.]("http://www.ubuntuforums.org/showthread.php?t=125638").

I'm most troubled by the idea that the system is ignoring /etc/network/interfaces and doing such things as choosing to create its own interfaces (ath0) unprompted. The issue with DNS I believe will be resolved when this gets resolved as I would guess resolv.conf is also being ignored by the interface. Note that my eth0 (wired) interface is functioning as expected which is where I point the finger at the madwifi drivers / atheros card.

Thank you for being so patient with troubled users like me!

Best,
~Chad

---

### Post by Ms. Phitt on 2006-02-19
At the risk of being somewhat redundant of the howto's preceding this post, I've reproduced here my attempt at a simplified set of directions, given that the steps kind of have to be patched together from 3 different locations  ([1]("http://ubuntuforums.org/showpost.php?p=628632&postcount=35") [2]("http://ubuntuforums.org/archive/index.php/t-105437.html") [3]("http://madwifi.org/wiki/UserDocs/FirstTimeHowTo")) graciously provided by the authors, and then some, as it exists now.  Thank you ever so much to those who took the time to provide them.  The following originally started as a post to my blog, as I prepare to do a presentation on Madwifi for my LinuxChix group.  I could get Madwifi working on SuSE 10.0 but not on Ubuntu / Kubuntu 5.10, and spent a lot of time trying to figure out why.  I thought it might also be helpful to someone here, to have everything in a linear order and all in one place.  Otherwise, well.... <DELETE>  :)

This assumes you have a fresh install of Ubuntu or Kubuntu 5.10 with the default kernel version 2.6.12-9-386 and that you download a madwifi snapshot more recent than January 23, 2006 (r1407).

First, you will need to make it so the package manager can access packages not maintained by K/Ubuntu (in other words, third-party software).  This is not enabled by default.  As root, use your favorite text editor (vi, gedit, emacs, pico, etc.) to open /etc/apt/sources.list .  Here, I used *vi*:
```
sudo vi /etc/apt/sources.list
```
and remove the # from in front of these two lines:
```
deb http://us.archive.ubuntu.com/ubuntu breezy universe
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe
```
Save and close.

The madwifi driver is included in the package linux-restricted-modules-2.6.12-9-386 and will conflict with the new one you are installing, so the package needs to be uninstalled before you start.  Warning: apt-get (and by extension, the Adept gui interface) will, in its infinite wisdom, mark 2 packages for upgrade and 1 for install as soon as you do.  (Grrr.)  So you have to then uninstall these too, in order to avoid conflicts.  You can do all of this from Adept, searching for and marking each package for removal, or from the command line using:
```
sudo apt-get remove --purge linux-restricted-modules-`uname -r`
```
Now watch for the names of the packages it wants to install/upgrade.  They should be removed using the format *sudo apt-get remove --purge packagename*:
```
sudo apt-get remove --purge linux-restricted-modules-2.6.12-10-386

sudo apt-get remove --purge linux-restricted-modules-386

sudo apt-get remove --purge linux-image-2.6.12-10-386
```
You'll need to install some packages that madwifi will need:
```
sudo apt-get install build-essential linux-headers-`uname -r` gcc-3.4 subversion sharutils
```
Now you're ready to download the madwifi driver:
```
cd /usr/src
*/usr/src$* sudo svn checkout http://svn.madwifi.org/trunk madwifi-ng
```
It probably made a new folder called madwifi-ng , in which case you can 
```
*/usr/src$* cd madwifi-ng
```
to move into the new directory (/usr/src/madwifi-ng) .

Now you will need to force madwifi to compile using gcc 3.4 .  Use your favorite text editor to open /usr/src/madwifi-ng/hal/public/i386-elf.inc ; here I used *vi*:
```
*/usr/src/madwifi-ng$* vi hal/public/i386-elf.inc
```
Find this line:
```
CC=    ${TOOLPREFIX}gcc
```
and change it to this:
```
CC=    ${TOOLPREFIX}gcc-3.4
```
Save and close.

Now you are ready to install:
```
make uninstall

make

make install
```
You may get this warning:
 
 WARNING:
 It seems that there are modules left from previous MadWifi installations.
 You should consider removing them before you continue, or else you might
 experience problems during operation. Remove old modules?
 
 [l]ist, [r]emove, [i]gnore or e[x]it (l,r,i,[x]) ? 
 
```
r
```
 to remove.

[INDENT][I]Optional:  If you're using KDE you can launch kwifimanager to help monitor the wireless card's status.  You can go to K Menu -> Internet -> Wireless LAN Manager (KWifiManager), or open a new shell and type
```
kwifimanager
```
There will probably be a red "X" through the bar graph, indicating that no wireless card has been found.[/I][/INDENT]

You are now ready to load the driver module: 
```
modprobe ath_pci
```
[INDENT]*If you're using kwifimanager, the red "X" should disappear.*[/INDENT]
You should now be able to type
```
iwconfig
```
and see something like this:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""
          Mode:Managed  Channel:0  Access Point: 00:00:00:00:00:00
          Bit Rate:0 kb/s   Tx-Power:13 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:1  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
Now start the scanning module, which will allow you to scan for local wireless networks (also known as a site survey):
```
sudo modprobe wlan_scan_sta
```
Start the the wireless interface:
```
sudo ifconfig ath0 up
```
If you know there's at least one wireless network nearby, start a site survey.

[INDENT]*If you're using kwifimanager, you can click "Scan for networks" and should get a list of networks in a popup dialogue.*[/INDENT]
Otherwise you can use:
```
sudo wlanconfig ath0 list scan
```
You should get something like this:
```
SSID            BSSID              CHAN RATE  S:N   INT CAPS
default         00:12:34:56:78:9a    1   11M 22:0   100 E
janeshmane      00:24:68:ac:e1:35    6   54M 51:0   100 EPS ATH
joeshmoe        00:11:33:55:77:99    5   54M  2:0   100 EPs
```
If you got this far, you know it's working.  If you're using KDE you should be able to go into K Menu -> System Settings -> Network Settings, go into Administrator Mode (ALT-M, if you can't see the Administrator Mode button), and edit the rest of your settings from there... unless you have WPA encryption, in which case you will need [wpa_supplicant]("http://hostap.epitest.fi/wpa_supplicant/") .  And since WEP is now easily crackable by any script kiddie with the right script, I strongly suggest that you *should* be using WPA.  But I know that is another subject for another thread.

---

### Post by weizilla on 2006-02-21
I just installed the latest drivers following the instructions in the above post. what should I use to graphically connect to an access point? Will installing network-manager or wifiradar mess up anything that I installed or try to use any of the old components? I can get wireless access points around me through the terminal commands but when I go to the Networking tool (came built into Ubuntu), it says that my wireless card is not configured and not activated.

---

### Post by reweiss on 2006-02-26
Hi @ all I'm newbi and I need your help :) 
Untill now everything works fine i could bild the driver without problems. But when i make "build install" i get this message:
(export MODULEPATH=/lib/modules/2.4.20-31.9/net; /sbin/depmod -ae)
depmod: *** Unresolved symbols in /lib/modules/2.4.20-31.9/net/ath_hal.o
depmod:         proc_dointvec
depmod:         unregister_sysctl_table
depmod:         register_sysctl_table
depmod: *** Unresolved symbols in /lib/modules/2.4.20-31.9/net/ath_pci.o
depmod:         __kfree_skb
depmod:         alloc_skb
depmod:         pskb_expand_head
depmod:         ether_setup
depmod:         pci_free_consistent
depmod:         alloc_etherdev
depmod:         unregister_netdev
depmod:         alloc_netdev
depmod:         skb_copy
depmod:         pci_alloc_consistent
depmod:         proc_dointvec
depmod:         unregister_sysctl_table
depmod:         register_netdev
depmod:         skb_over_panic
depmod:         softnet_data
depmod:         proc_dointvec_minmax
depmod:         irq_stat
depmod:         register_sysctl_table
depmod: *** Unresolved symbols in /lib/modules/2.4.20-31.9/net/wlan.o
depmod:         register_netdevice
depmod:         __netdev_watchdog_up
depmod:         eth_type_trans
depmod:         __kfree_skb
depmod:         alloc_skb
depmod:         pskb_expand_head
depmod:         skb_under_panic
depmod:         skb_realloc_headroom
depmod:         unregister_netdevice
depmod:         create_proc_entry
depmod:         skb_copy
depmod:         wireless_send_event
depmod:         netif_receive_skb
depmod:         proc_dostring
depmod:         request_module
depmod:         proc_mkdir
depmod:         PDE
depmod:         proc_dointvec
depmod:         unregister_sysctl_table
depmod:         dev_alloc_name
depmod:         dev_queue_xmit
depmod:         ___pskb_trim
depmod:         remove_proc_entry
depmod:         netif_rx
depmod:         skb_over_panic
depmod:         proc_net
depmod:         dev_close
depmod:         skb_clone
depmod:         dev_open
depmod:         irq_stat
depmod:         register_sysctl_table
depmod:         skb_copy_expand
depmod: *** Unresolved symbols in /lib/modules/2.4.20-31.9/net/wlan_acl.o
depmod:         irq_stat
depmod: *** Unresolved symbols in /lib/modules/2.4.20-31.9/net/wlan_ccmp.o
depmod:         crypto_alloc_tfm
depmod:         skb_under_panic
depmod:         crypto_cipher_setkey
depmod:         ___pskb_trim
depmod:         skb_over_panic
depmod:         crypto_free_tfm
depmod:         mem_map
depmod:         crypto_cipher_encrypt
depmod: *** Unresolved symbols in /lib/modules/2.4.20-31.9/net/wlan_scan_ap.o
depmod:         irq_stat
depmod: *** Unresolved symbols in /lib/modules/2.4.20-31.9/net/wlan_scan_sta.o
depmod:         irq_stat
depmod: *** Unresolved symbols in /lib/modules/2.4.20-31.9/net/wlan_tkip.o
depmod:         skb_under_panic
depmod:         ___pskb_trim
depmod:         skb_over_panic
depmod: *** Unresolved symbols in /lib/modules/2.4.20-31.9/net/wlan_wep.o
depmod:         skb_under_panic
depmod:         ___pskb_trim
depmod:         skb_over_panic
make -C ./tools  install || exit 1
make[1]: Entering directory `/usr/src/madwifi-ng/tools'
install -d /usr/local/bin
for i in athstats 80211stats athkey athchans athctrl athdebug 80211debug wlanconfig; do \
        install $i /usr/local/bin/$i; \
        strip /usr/local/bin/$i; \
done
install -d /usr/local/man/man8
install -m 0644 man/*.8 /usr/local/man/man8
make[1]: Leaving directory `/usr/src/madwifi-ng/tools'
[root@localhost madwifi-ng]#

I don't know what to do :( Of course the modprobe doesn't work after! What can i make! Thanks alot for all help!

---

### Post by reweiss on 2006-02-26
Hi @ all I'm newbi and I need your help
Untill now everything works fine i could bild the driver without problems. But when i make "build install" i get this message:
(export MODULEPATH=/lib/modules/2.4.20-31.9/net; /sbin/depmod -ae)
depmod: *** Unresolved symbols in /lib/modules/2.4.20-31.9/net/ath_hal.o
depmod: proc_dointvec
depmod: unregister_sysctl_table
depmod: register_sysctl_table
depmod: *** Unresolved symbols in /lib/modules/2.4.20-31.9/net/ath_pci.o
depmod: __kfree_skb
depmod: alloc_skb
depmod: pskb_expand_head
depmod: ether_setup
depmod: pci_free_consistent
depmod: alloc_etherdev
depmod: unregister_netdev
depmod: alloc_netdev
depmod: skb_copy
depmod: pci_alloc_consistent
depmod: proc_dointvec
depmod: unregister_sysctl_table
depmod: register_netdev
depmod: skb_over_panic
depmod: softnet_data
depmod: proc_dointvec_minmax
depmod: irq_stat
depmod: register_sysctl_table
depmod: *** Unresolved symbols in /lib/modules/2.4.20-31.9/net/wlan.o
depmod: register_netdevice
depmod: __netdev_watchdog_up
depmod: eth_type_trans
depmod: __kfree_skb
depmod: alloc_skb
depmod: pskb_expand_head
depmod: skb_under_panic
depmod: skb_realloc_headroom
depmod: unregister_netdevice
depmod: create_proc_entry
depmod: skb_copy
depmod: wireless_send_event
depmod: netif_receive_skb
depmod: proc_dostring
depmod: request_module
depmod: proc_mkdir
depmod: PDE
depmod: proc_dointvec
depmod: unregister_sysctl_table
depmod: dev_alloc_name
depmod: dev_queue_xmit
depmod: ___pskb_trim
depmod: remove_proc_entry
depmod: netif_rx
depmod: skb_over_panic
depmod: proc_net
depmod: dev_close
depmod: skb_clone
depmod: dev_open
depmod: irq_stat
depmod: register_sysctl_table
depmod: skb_copy_expand
depmod: *** Unresolved symbols in /lib/modules/2.4.20-31.9/net/wlan_acl.o
depmod: irq_stat
depmod: *** Unresolved symbols in /lib/modules/2.4.20-31.9/net/wlan_ccmp.o
depmod: crypto_alloc_tfm
depmod: skb_under_panic
depmod: crypto_cipher_setkey
depmod: ___pskb_trim
depmod: skb_over_panic
depmod: crypto_free_tfm
depmod: mem_map
depmod: crypto_cipher_encrypt
depmod: *** Unresolved symbols in /lib/modules/2.4.20-31.9/net/wlan_scan_ap.o
depmod: irq_stat
depmod: *** Unresolved symbols in /lib/modules/2.4.20-31.9/net/wlan_scan_sta.o
depmod: irq_stat
depmod: *** Unresolved symbols in /lib/modules/2.4.20-31.9/net/wlan_tkip.o
depmod: skb_under_panic
depmod: ___pskb_trim
depmod: skb_over_panic
depmod: *** Unresolved symbols in /lib/modules/2.4.20-31.9/net/wlan_wep.o
depmod: skb_under_panic
depmod: ___pskb_trim
depmod: skb_over_panic
make -C ./tools install || exit 1
make[1]: Entering directory `/usr/src/madwifi-ng/tools'
install -d /usr/local/bin
for i in athstats 80211stats athkey athchans athctrl athdebug 80211debug wlanconfig; do \
install $i /usr/local/bin/$i; \
strip /usr/local/bin/$i; \
done
install -d /usr/local/man/man8
install -m 0644 man/*.8 /usr/local/man/man8
make[1]: Leaving directory `/usr/src/madwifi-ng/tools'
[root@localhost madwifi-ng]#

I don't know what to do :( Of course the modprobe doesn't work after! What can i make! Thanks alot for all help!

---

### Post by reweiss on 2006-02-26
Oh what did i do :( Sorry for double post

---

### Post by Lambert on 2006-02-27
Are you using a standard breezy install? 

Your MODULEPATH is showing a 2.4 kernel?

what's output of 

cat /proc/version
and
modinfo ath_pci

---

### Post by Ms. Phitt on 2006-03-10
[QUOTE=weizilla]I just installed the latest drivers following the instructions in the above post. what should I use to graphically connect to an access point? Will installing network-manager or wifiradar mess up anything that I installed or try to use any of the old components? I can get wireless access points around me through the terminal commands but when I go to the Networking tool (came built into Ubuntu), it says that my wireless card is not configured and not activated.[/QUOTE]Sorry it took me so long to see your reply.  Glad that helped! :) 

I haven't been using Gnome for some time so I don't have an immediate answer for you on this.  If I get a chance to install and try it I'll let you know what I find.  You can, however, specify an access point from the command prompt:
```
ifconfig ath0 down
iwconfig ath0 essid "*your_ssid_name*"
ifconfig ath0 up
```
do type the quotes.

Or if you want to specify by the access point's MAC address:
```
ifconfig ath0 down
iwconfig ath0 ap *00:11:22:33:44:55*
ifconfig ath0 up
```
of course replacing the fake address above with your AP's MAC address.

There are some more detailed directions [here]("http://madwifi.org/wiki/UserDocs/FirstTimeHowTo").  IMHO, the hardest part by far is just getting it to the point you're at now, where it works and scans for AP's.  Hang in there, you've almost got it.  :)

P.S.  Make sure your ethernet is down with
```
ifconfig eth0 down
```
before you bring ath0 up, or you may have problems getting proper default gateway and DNS from DHCP.  Don't ask me why.  <shrug>...

---

### Post by irober02 on 2006-04-01
I tried this Howto unsuccessfully and now (for the second time in one week) have broken the madwifi drivers on my laptop! :-( -I hope I can avoid another ubuntu install.

One deaprture from the procedure came when it tried to remove linux-image-2.6.12-10-386. Dire warnings about the consequences of deleting the current kernel led me to skip that step.

I proceded anyway (not so wise, I guess) and when I try to modprobe ath_pci I get the following:

WARNING: Error inserting ath_rate_sample (/lib/modules/2.6.12-10-386/net/ath_rate_sample.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ath_pci (/lib/modules/2.6.12-10-386/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)


I've had a look at dmesg which reports:

4367964.170000] ath_rate_sample: disagrees about version of symbol ieee80211_iterate_nodes
[4367964.170000] ath_rate_sample: Unknown symbol ieee80211_iterate_nodes
[4367964.176000] ath_pci: Unknown symbol ath_rate_tx_complete
[4367964.176000] ath_pci: disagrees about version of symbol ieee80211_encap
[4367964.176000] ath_pci: Unknown symbol ieee80211_encap
[4367964.176000] ath_pci: disagrees about version of symbol ieee80211_input
[4367964.176000] ath_pci: Unknown symbol ieee80211_input
[4367964.176000] ath_pci: disagrees about version of symbol ieee80211_ifattach
[4367964.177000] ath_pci: Unknown symbol ieee80211_ifattach
[4367964.177000] ath_pci: disagrees about version of symbol ieee80211_beacon_update
[4367964.177000] ath_pci: Unknown symbol ieee80211_beacon_update
[4367964.177000] ath_pci: Unknown symbol ieee80211_find_channel
[4367964.177000] ath_pci: disagrees about version of symbol ieee80211_find_rxnode
[4367964.178000] ath_pci: Unknown symbol ieee80211_find_rxnode
[4367964.178000] ath_pci: Unknown symbol ath_rate_attach
[4367964.178000] ath_pci: Unknown symbol ieee80211_vap_setup
[4367964.178000] ath_pci: disagrees about version of symbol ieee80211_ifdetach
[4367964.179000] ath_pci: Unknown symbol ieee80211_ifdetach
[4367964.179000] ath_pci: disagrees about version of symbol ieee80211_free_node
[4367964.179000] ath_pci: Unknown symbol ieee80211_free_node
[4367964.179000] ath_pci: Unknown symbol ieee80211_input_monitor
[4367964.179000] ath_pci: Unknown symbol ath_rate_newassoc
[4367964.180000] ath_pci: disagrees about version of symbol ieee80211_crypto_newkey
[4367964.180000] ath_pci: Unknown symbol ieee80211_crypto_newkey
[4367964.180000] ath_pci: disagrees about version of symbol ieee80211_crypto_setkey
[4367964.180000] ath_pci: Unknown symbol ieee80211_crypto_setkey
[4367964.180000] ath_pci: disagrees about version of symbol ieee80211_dump_pkt
[4367964.180000] ath_pci: Unknown symbol ieee80211_dump_pkt
[4367964.181000] ath_pci: Unknown symbol ieee80211_ioctl_create_vap
[4367964.181000] ath_pci: Unknown symbol ieee80211_dfs_test_return
[4367964.181000] ath_pci: Unknown symbol ieee80211_stop_running
[4367964.181000] ath_pci: disagrees about version of symbol ieee80211_cipher_none
[4367964.182000] ath_pci: Unknown symbol ieee80211_cipher_none
[4367964.182000] ath_pci: disagrees about version of symbol ieee80211_crypto_delkey
[4367964.182000] ath_pci: Unknown symbol ieee80211_crypto_delkey
[4367964.182000] ath_pci: disagrees about version of symbol ieee80211_media_change
[4367964.182000] ath_pci: Unknown symbol ieee80211_media_change


Any suggestions?


bye

ian

---

### Post by rgmussel on 2006-04-14
Working on this problem for 4 days (and perhaps a little longer](*,) ). Thank you so much!

---

### Post by Abdi110 on 2006-04-20
Bash tells me I don't have wlanconfig, where do I get this from?

Edit: Wow I'm a retard, some how I forgot to make install.

---

### Post by oigreslima on 2006-05-01
[QUOTE=Lambert]

[/B]```
wlanconfig ath0 create wlandev wifi0 wlanmode sta
``` 

[/QUOTE]

I receive:

[QUOTE=OIGRESLIMA]wlanconfig: No such device[QUOTE]

What i do?

Thanks

---

### Post by cheuschober on 2006-06-03
Hi All. Back for more punishment it seems.

Did a fresh install of dapper (xubuntu) and wanted to build madwifi-ng again but suddenly I'm running into some nasty errors during make. I'm 90% sure I have all the pieces I need (though I've switched out the 386 kernel for the 686, it shouldn't make a difference... right?).

Any thoughts, guidance, pointers would be hugely appreciated.

Error during 'make':```
Checking requirements... ok.
Checking kernel configuration... ok.
if [ -d .svn ]; then \
                ver=`svnversion -nc . | sed -e 's/^[^:]*://;s/[A-Za-z]//'`; \
                echo "#define SVNVERSION \"svn r$ver\"" > svnversion.h; \
        elif [ -s SNAPSHOT ]; then \
                ver=`sed -e '/^Revision: */!d;s///;q' SNAPSHOT`; \
                echo "#define SVNVERSION \"svn r$ver\"" > svnversion.h; \
        fi; \

make -C /lib/modules/2.6.15-23-686/build SUBDIRS=/usr/local/src/madwifi-ng modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-23-686'
  CC [M]  /usr/local/src/madwifi-ng/ath/ah_osdep.o
cc1: error: unrecognized command line option "-Wno-pointer-sign"
make[3]: *** [/usr/local/src/madwifi-ng/ath/ah_osdep.o] Error 1
make[2]: *** [/usr/local/src/madwifi-ng/ath] Error 2
make[1]: *** [_module_/usr/local/src/madwifi-ng] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-23-686'
make: *** [modules] Error 2
```

Many thanks,
~Chad

---

### Post by cheuschober on 2006-06-03
Okay... problem fixed... when I had last built the madwifi-ng snapshot (several months ago) it wouldn't compile with my current gcc and I had to use 3.4 as suggested. Now I've not idea what the "-Wno-pointer-sign" is or, honestly, what any of the rest of the errors referred to but I know just enought to be dangerous and know that it was a gcc error.  I tried my current GCC build and it compiled.

If anyone else can confirm I would make the suggestion to amend the how-to to reflect that gcc-3.4 is no longer compiling and to use the current gcc instead.

Best! :mrgreen:

---

### Post by Satvic on 2007-06-05
i'm linux nOOb, any help would be appreciated: 

I can't pass past MAKE due to ERROR 2 ... seems like a lot of variables are missing. I'm on latest uBuntu 7.04 with Dell D610 and Atheros bazed 8471-WD card with latest download of madwifi: 

** same error with kernel 2.6.20-16-generic
** removing -WERROR   doesn't do anything just as leaving it... 

sat@usdh:/media/sda3/aircrack/madwifi-0.9.3.1$ sudo make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/media/sda3/Aircrack/madwifi-0.9.3.1 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /media/sda3/Aircrack/madwifi-0.9.3.1/ath/if_ath.o
  CC [M]  /media/sda3/Aircrack/madwifi-0.9.3.1/ath/if_ath_pci.o
  LD [M]  /media/sda3/Aircrack/madwifi-0.9.3.1/ath/ath_pci.o
  CC [M]  /media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/ah_os.o
  HOSTCC  /media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c: In function 'uudecode_usage':
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c: At top level:
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c: In function 'main':
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:121: error: for each function it appears in.)
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal/uudecode] Error 1
make[2]: *** [/media/sda3/Aircrack/madwifi-0.9.3.1/ath_hal] Error 2
make[1]: *** [_module_/media/sda3/Aircrack/madwifi-0.9.3.1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [modules] Error 2
sat@usdh:/media/sda3/aircrack/madwifi-0.9.3.1$

---

### Post by tturrisi on 2007-06-05
> **Satvic said:**
> i'm linux nOOb, any help would be appreciated: 

I can't pass past MAKE due to ERROR 2 ... seems like a lot of variables are missing. I'm on latest uBuntu 7.04 with Dell D610 and Atheros bazed 8471-WD card with latest download of madwifi: 


uninstall any madwifi restricted modules PRIOR to downloading & building madwifi-ng else will get build errors.
[http://www.aircrack-ng.org/doku.php?id=madwifi-ng](http://www.aircrack-ng.org/doku.php?id=madwifi-ng)

---

