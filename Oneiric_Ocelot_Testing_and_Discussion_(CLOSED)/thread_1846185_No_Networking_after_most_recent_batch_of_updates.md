---
title: "No Networking after most recent batch of updates"
date: 2011-09-18
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by residualbit on 2011-09-18
I just installed a few updates and it seems to have killed my networking. The network manager icon no longer shows in the top panel.

Completely vanilla install of oneric 64 bit. I've just been installing updates.

Ideas?

---

### Post by residualbit on 2011-09-18
when I try to run nm-applet, I get an error loading shared libraries so libnss3.so

---

### Post by residualbit on 2011-09-18
I wiped and re-installed the beta from scratch. Wifi and wired networking were working fine. Installed updates. No networking, no icon in the panel...ideas?

---

### Post by ronacc on 2011-09-18
just for info I just updated my 64bit oneiric ( gnome-shell) install and have no problem with networking .

---

### Post by residualbit on 2011-09-18
re-imaged back to 11.04 for now. If anyone else had this issue and fixed it, let me know.

---

### Post by reddawg60 on 2011-09-19
I installed 11.10 last night everything worked, as soon as updated and restarted my network no longer worked.

I look at **/etc/network/interfaces** and it looked like this

[B]auto lo
iface lo inet [/B]

_lo_ i guess is the loop back device

i changed the lo to my Ethernet device so it looks like this

[B]auto eth0
iface eth0 inet dhcp[/B]

now my network works but i did not get my network icon back.

---

### Post by residualbit on 2011-09-19
Interesting. I am on wifi, so I don't know if that would work for me. I wanted to go through and create a bug report, but the update installs 450+ packages so it would be hard to tell which is the culprit. I think I may wait until Thursday and try again with beta 2.

---

### Post by TDK800 on 2011-09-20
same here, latest updates killed networking.

ethernet cable connection and wifi not working anymore, but usb connected mobile modem still works.

---

### Post by smurftheweb on 2011-09-20
Confirm same problem - was working fine before update, and then no networking or network applet.

I can confirm the following fixed worked for me (as suggested by reddawg60). I have a wired ethernet port, using the r8169 driver. Instructions assume one ethernet port called eth0.

1. Edit /etc/network/interfaces
Add the lines:

> auto eth0
iface eth0 inet dhcp2. Force ubuntu to reload the modules
Either reboot, or
sudo rmmod r8169
sudo modprobe r8169

After this you should be connected again - you can use ifconfig to check. This will **not** fix the applet.

---

### Post by HazE_nMe on 2011-09-21
This is due to missing libnss3.so in /usr/lib/x86_64-linux-gnu/
or /usr/lib/i386-linux-gnu/

Run dpkg -L libnss3 and verify location of libnss3.so

Check location to see if libnss3.so exists

If it does not you should reinstall linbss3

I had to do this manually (not with apt)

Download libnss3 here:
[http://packages.ubuntu.com/oneiric/amd64/libnss3/download](http://packages.ubuntu.com/oneiric/amd64/libnss3/download)
or
[http://packages.ubuntu.com/oneiric/i386/libnss3/download](http://packages.ubuntu.com/oneiric/i386/libnss3/download)

I reinstalled through software center and then verified that libnss3.so exists.

---

### Post by VinDSL on 2011-09-21
> **HazE_nMe said:**
> This [no networking] is due to missing libnss3.so in /usr/lib/x86_64-linux-gnu/
or /usr/lib/i386-linux-gnu/

Run dpkg -L libnss3 and verify location of libnss3.so

Check location to see if libnss3.so exists

If it does not you should reinstall linbss3

I had to do this manually (not with apt)

Download libnss3 here:
[http://packages.ubuntu.com/oneiric/amd64/libnss3/download](http://packages.ubuntu.com/oneiric/amd64/libnss3/download)
or
[http://packages.ubuntu.com/oneiric/i386/libnss3/download](http://packages.ubuntu.com/oneiric/i386/libnss3/download)

I reinstalled through software center and then verified that libnss3.so exists.
Greets, fellow Arizonan!

Don't mean to be a smart AZ, but how does one download / reinstall the above, without a web connection?!?!?

---

### Post by luckylukeskywalker on 2011-09-21
> **VinDSL said:**
> Greets, fellow Arizonan!

Don't mean to be a smart AZ, but how does one download / reinstall the above, without a web connection?!?!?

You can use for example another computer to download it, and then transfer it using a memorystick. After that just double-click the file.

The solution worked for me :-) Now I'm connected again

---

### Post by robert shearer on 2011-09-21
Got networking back but still no network applet (using gnome-session-fallback desktop)
and the date/time applet errors and fails to load.

Anyone else experienced/fixed this ?

**EDIT**.. fixed by following this post...
[http://ubuntuforums.org/showpost.php?p=11273457&postcount=8](http://ubuntuforums.org/showpost.php?p=11273457&postcount=8)
 network applet returned **and** the date/time applet came back too !
Thanks to Brouham.

---

### Post by SilverLoz on 2011-09-21
This is why I love Ubuntu and it's community. I went to bed last night with my network having disappeared. I wake up this morning and here's the answer! Thanks, HazE_nMe; the fix worked a treat!

---

### Post by el_koraco on 2011-09-21
> **VinDSL said:**
> Greets, fellow Arizonan!

Don't mean to be a smart AZ, but how does one download / reinstall the above, without a web connection?!?!?

You make a backup profile in /etc/network/interfaces (I'm assuming it's for wireless, the wired connection is explained on the previous page): 


```
# This file describes the network interfaces available on your system 
# and how to activate them. For more information, see interfaces(5).  
The loopback network interface auto lo iface lo inet loopback  

#auto wlan0 
#iface wlan0 inet dhcp 
#wpa-ssid xxx 
#wpa-psk yyy

```Replace wlan0 with your interface name (be it ath0, eth1, whatever), xxx with your ssid and yyy with your passkey in ASCII. When the connection via Network-Manager drops, stop network-amanager, uncomment the wlan stuff, and run 

```
sudo ifdown wlan0 && sudo ifup wlan0
```You should have the connection, even on runlevel 1. You might have to play with the ssid and password options if you're using WEP.

---

### Post by ClyN3il on 2011-09-21
I got internet working using the recommendations you can see in this thread, but not nm-applet. When I try to run nm-applet, I get:

> nm-applet: error while loading shared libraries: libnss3.so: cannot open shared object file: No such file or directory

But libnss3.so is already installed. After forcing it to reinstall (sudo apt-get install --reinstall libnss3) and trying to run nm-applet, I got this:

> ** (nm-applet:4767): WARNING **: _nm_object_get_property: Error getting 'NetworkingEnabled' for /org/freedesktop/NetworkManager: (2) The name org.freedesktop.NetworkManager was not provided by any .service files


** (nm-applet:4767): WARNING **: nm_client_get_devices: error getting devices: The name org.freedesktop.NetworkManager was not provided by any .service files

** Message: applet now removed from the notification area

** (nm-applet:4767): WARNING **: get_all_cb: couldn't retrieve system settings properties: (2) The name org.freedesktop.NetworkManager was not provided by any .service files.

** (nm-applet:4767): WARNING **: Failed to register as an agent: (2) The name org.freedesktop.NetworkManager was not provided by any .service filesI'm sure it'll be fixed in due time...at least I have internet working so it's ok I guess...

---

### Post by chenzhiwei on 2011-09-21
> **HazE_nMe said:**
> This is due to missing libnss3.so in /usr/lib/x86_64-linux-gnu/
or /usr/lib/i386-linux-gnu/

Run dpkg -L libnss3 and verify location of libnss3.so

Check location to see if libnss3.so exists

If it does not you should reinstall linbss3

I had to do this manually (not with apt)

Download libnss3 here:
[http://packages.ubuntu.com/oneiric/amd64/libnss3/download](http://packages.ubuntu.com/oneiric/amd64/libnss3/download)
or
[http://packages.ubuntu.com/oneiric/i386/libnss3/download](http://packages.ubuntu.com/oneiric/i386/libnss3/download)

I reinstalled through software center and then verified that libnss3.so exists.

thank you!
This can resolve my problem.

---

### Post by rrohde on 2011-09-21
Just to bad that now, even after I got Gnome Network Manager to work (thanks for the participants of this thread here), neither my wired nor wireless connection are being managed by it, and wireless simply doesn't work... What a showstopper, especially for a beta release!

---

### Post by Curnel_D on 2011-09-21
I can confirm same problem.  But I just can't be arsed to keep screwing with it.  That fact, combined with the fact that I'm interested in trying out the Win8 dev preview means that I'm done with 11.10 completely till release.  

So far, even for an alpha and beta release, there's just been far far too many mistakes, not just in obvious testing errors, but blatant design flaws that makes me think that I probably won't even bother upgrading my every day linux partition.

---

### Post by PuddingKnife on 2011-09-21
I will try this fix when I get home from work today, thanks Haze

---

### Post by apfejes on 2011-09-21
It was mentioned in another thread:  

```
sudo cp /usr/lib/thunderbird-7.0/libnss3.so /usr/lib/x86_64-linux-gnu/

```

then reboot and upgrade packages, then reinstall libnss3:

```
sudo apt-get install --reinstall libnss3
```

Worked for me - did not require messing with getting networking up again.

---

### Post by rrohde on 2011-09-21
Am I the only one who has a "Waiting for network configuration" message during the splash-screen phase while booting up? 

Even after the fixes suggested here, Gnome Network Manager does not manage my wired and wireless connections; however, it does appear in the panel again, albeit not taking care of my connections.

---

### Post by svenole on 2011-09-21
If you've got a wired network connected, the command "ifconfig ethX up ; dhclient ethX" will get you online. I didn't have a wired network, so I connected my iPhone with shared network enabled via cable and did the same command on that interface. 

Now i downloaded the libnss3_3.12-9+ckbi-1.82-0ubuntu1_i386.deb package, opened it as an archive, navigated down to usr/lib/i386-linux-gnu/ and extracted libnss3.so. I then copied this file to /usr/lib/i386-linux-gnu/ on the system itself and rebooted. Everything got  back to normal. 

Seems that somebody made an error so that the package distributed in the upgrade didn't include the library file libnss3.so.

---

### Post by tghe-retford on 2011-09-21
> **rrohde said:**
> Am I the only one who has a "Waiting for network configuration" message during the splash-screen phase while booting up? 
I get the same thing as well, has been the case for about a couple of weeks now. Fixed if an ethernet cable is attached to the computer, but very impractical for a laptop!

---

### Post by TunaCanTommy on 2011-09-21
See the post above (#21) - that's the simplest fix for this problem.
As soon as you copy libness3.so over to the proper folder, reboot and you will have networking back, and the icons.

---

### Post by altor on 2011-09-21
I was able to reinstall libnss3 and to reach the ne tbut no way to have  nm-applet back. 

The same error messages as ClyN3il posted (#16)

Someone  can  help us?

---

### Post by wgarcia on 2011-09-21
I got network and icon back with the instructions in #21. 

Has anybody registered a bug for this?

---

### Post by kaktus621 on 2011-09-21
I followed the instructions of post #21 and it worked only partially. I do have an internet connection again. The only problem is that I can't access _any_ website through https, only http works. EDIT: Suprisingly, this problem only occurs in Google Chrome, not in Firefox.

Furthermore, the "sudo apt-get install --reinstall libnss3" just returned "E: Internal Error, No file name for libnss3" (yes, I did apt-get update && apt-get upgrade before that).

---

### Post by jbicha on 2011-09-21
> **wgarcia said:**
> I got network and icon back with the instructions in #21. 

Has anybody registered a bug for this?

Yes, it was definitely reported as a critical bug and a fix was released within a few hours. (See the [ca-certificates thread]("http://ubuntuforums.org/showthread.php?t=1847446")). However, it's a fix for the broken packaging update that removed libnss3; it doesn't actually restore it.

---

### Post by wgarcia on 2011-09-21
jbicha, I couldn't find the bug you mention, I just reported a new one and would dup it if you post the link to the other one. 

Mine is:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/855891](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/855891)

---

### Post by whoop on 2011-09-21
> **kaktus621 said:**
> 
Furthermore, the "sudo apt-get install --reinstall libnss3" just returned "E: Internal Error, No file name for libnss3" (yes, I did apt-get update && apt-get upgrade before that).


I had that problem too.
try sudo apt-get install --reinstall libnss3 libnss3:i386

---

### Post by paul_in_london on 2011-09-21
These updates came through about half an hour ago:

```
Aptitude 0.6.4: log report
Wed, Sep 21 2011 23:31:21 +0100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 4 packages, and remove 0 packages.
===============================================================================
[UPGRADE] libnss3 3.12.9+ckbi-1.82-0ubuntu5 -> 3.12.9+ckbi-1.82-0ubuntu6
[UPGRADE] libnss3 3.12.9+ckbi-1.82-0ubuntu5 -> 3.12.9+ckbi-1.82-0ubuntu6
[UPGRADE] libnss3-1d 3.12.9+ckbi-1.82-0ubuntu5 -> 3.12.9+ckbi-1.82-0ubuntu6
[UPGRADE] libnss3-1d 3.12.9+ckbi-1.82-0ubuntu5 -> 3.12.9+ckbi-1.82-0ubuntu6
===============================================================================

Log complete.
paul@oneiric-64:~$
```

---

### Post by Coplen on 2011-09-22
I've done everything listed and I still have to do these before the internet works:

sudo ifdown -a
sudo ifup -a

---

### Post by VinDSL on 2011-09-22
> **apfejes said:**
> Worked for me - did not require messing with getting networking up again.
Sorta worked for me, but...

My networking problems were complicated by the xorg-edgers PPA, which needed to be purged, thus I needed a web connection to restore the original packages.

Anyway, between restoring the missing libnss3.so file, and purging xorg-edgers PPA, life is beautiful again.  ;)

---

### Post by dino99 on 2011-09-22
should be fixed now with the latest packages, but have lost the network icon on top taskbar (gnome-classic)

---

### Post by Harry33 on 2011-09-22
> **dino99 said:**
> should be fixed now with the latest packages, but have lost the network icon on top taskbar (gnome-classic)

I can see the icon on all of my Gnome-shell setups.
And I do not even have the package network-manager-gnome (the systray applet on panel) installed.
):P

---

### Post by robert shearer on 2011-09-22
> **dino99 said:**
> should be fixed now with the latest packages, but have lost the network icon on top taskbar (gnome-classic)

Fixed...for me...
[http://ubuntuforums.org/showpost.php?p=11271539&postcount=13](http://ubuntuforums.org/showpost.php?p=11271539&postcount=13)
using this posts instructions...
[http://ubuntuforums.org/showpost.php?p=11273457&postcount=8](http://ubuntuforums.org/showpost.php?p=11273457&postcount=8)

---

### Post by rbrick49 on 2011-09-22
I am not saying nothing

---

### Post by dino99 on 2011-09-22
> **robert shearer said:**
> Fixed...for me...
[http://ubuntuforums.org/showpost.php?p=11271539&postcount=13](http://ubuntuforums.org/showpost.php?p=11271539&postcount=13)
using this posts instructions...
[http://ubuntuforums.org/showpost.php?p=11273457&postcount=8](http://ubuntuforums.org/showpost.php?p=11273457&postcount=8)

good point, thanks :)

---

### Post by tobluntoo on 2011-09-22
Hi there, i'm very new to all this linux & ubuntu malarky (but lovin' it nonetheless :-) & to be honest technology & computing in general, so all this terminal, commanding, sudo, code stuff is totally over my head at the mo (hopefully that should change in the next few weeks.....) & just wanted to know if it's safe to update yet? 

I installed 11.10 a few days ago, updated, lost me broadcom driver support, became baffled & overwhelmed(!), so just decided to re-install and not update, which has been fine for the last couple of days as i'm too scared to try updating again! So is it ok to just tick & click all updates now?

Also, I was wondering if the Beta 2 has arrived as scheduled today and if so whether that & the official release will require a re-install or just a click in the update manager?

---

### Post by dino99 on 2011-09-22
safe ??? as you says, its still beta, meaning lot of pending issues.
so, what is safe for experienced users can be very scary for you :(

by the way, if updates brings fear for you, and your system is working smootly, why should you upgrade to be stuck ? (final release is not so far)

---

### Post by tobluntoo on 2011-09-22
Aye, you've a good point :-) just wanted to see if the updates might fix a couple of minor bugs - software centre being a wee bit slow and unreliable and a slightly long boot-time compared to 11.04, no biggie though. 

Should probably wait, but knowing me & my absurd urge to fiddle, i'll probably give it a whirl anyway, and maybe pick up a wee bit of understanding in the process.....or just end up baffled & confused again! :-)

---

### Post by dino99 on 2011-09-22
ok lets go: tweak, tweak, break
but its out of topic (stop spamming)

---

### Post by cariboo on 2011-09-22
> **tobluntoo said:**
> Hi there, i'm very new to all this linux & ubuntu malarky (but lovin' it nonetheless :-) & to be honest technology & computing in general, so all this terminal, commanding, sudo, code stuff is totally over my head at the mo (hopefully that should change in the next few weeks.....) & just wanted to know if it's safe to update yet? 

I installed 11.10 a few days ago, updated, lost me broadcom driver support, became baffled & overwhelmed(!), so just decided to re-install and not update, which has been fine for the last couple of days as i'm too scared to try updating again! So is it ok to just tick & click all updates now?

Also, I was wondering if the Beta 2 has arrived as scheduled today and if so whether that & the official release will require a re-install or just a click in the update manager?

The purpose of running a testing release is to break it and report bugs, it takes a bit of specialized knowledge to keep it running on a daily basis. I would suggest you stick with an LTS release until you learned the ins and outs of the system. Running Oneiric as you've seen can lead to a system that is not completely usable, I hope you've got a backup installation of a stable release so that your system is still usable.

There is no scheduled release time for Beta 2, it will be released when it's ready. If you want notification of when it's released, I'd suggest you subscribe to the [Ubuntu-announce]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-announce") mailing list

---

### Post by residualbit on 2011-09-22
Man, I logged in to check if anyone responded recently and the thread is 5 pages deep. Turns out I had email notifications turned off. Gotta love this community.

Anyway, I'm still on 11.04, going to try 11.10 again tonight. Anyone try to do a fresh install of beta 2? If so, do you still have to do the fixes mention in previous posts? Just wondering so I can mark this as solved.

---

### Post by fjgaude on 2011-09-22
> **nkirk1 said:**
> Man, I logged in to check if anyone responded recently and the thread is 5 pages deep. Turns out I had email notifications turned off. Gotta love this community.

Anyway, I'm still on 11.04, going to try 11.10 again tonight. Anyone try to do a fresh install of beta 2? If so, do you still have to do the fixes mention in previous posts? Just wondering so I can mark this as solved.

No need to do anything with a fresh Beta2 install. All should work correctly... still many bugs but that is to be expected.

---

### Post by TunaCanTommy on 2011-09-22
Nevermind . . . .

---

### Post by VinDSL on 2011-09-23
> **dino99 said:**
> so, what is safe for experienced users can be very scary for you :(
Heh!

First LoL of the day!

Thanks!  :D

---

### Post by shaneo1 on 2011-09-23
Ok I thought i would just add another post

I have followed every link and fix going on this thread, I have the Network Applet Icon and the drop down menu you I can edit connections, but I can not search wireless networks or connect to one without have to run:

[PHP]sudo /etc/init.d/networking restart INTERFACE=wlan0[/PHP]

To get me connected to the internet.

The applet says  wireless networks device not ready and setting network manager says unavailable. 

I have check that I have the driver file installed, the libnss3.so has been manually moved to the correct place.  

On boot I get the waiting for network messages.  Where am I going wrong?  Any ideas guys?

Thanks

---

### Post by cariboo on 2011-09-23
Can you post the output of:

```
lshw -C network
```

to let us see if the device is being detected properly, and the correct driver is loaded.

You can create a text file by adding:

```
> network.txt
```

to the end of the first command, that way you can move the file to a system that does have internet access.

---

### Post by shaneo1 on 2011-09-23
```
[B] *-network               
       description: Ethernet interface
       product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: 00:a0:d1:ae:eb:0e
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no multicast=yes port=twisted pair
       resources: irq:48 memory:da200000-da23ffff ioport:4000(size=128)
  *-network
       description: Wireless interface
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 00
       serial: 00:22:fa:07:bb:5e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-11-generic firmware=8.83.5.1 build 33692 ip=192.168.1.2 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:46 memory:d8100000-d8101fff
[/B]
```

Heres my output.  Thanks :)

---

### Post by cariboo on 2011-09-23
It looks like your wireless device is detected, and the correct driver is loaded, I haven't had any experience with the intel chipset, but there is a thread about it [here]("http://ubuntuforums.org/showthread.php?t=1844396&highlight=intel+wireless")

---

### Post by shaneo1 on 2011-09-24
Its only detected because I have to type 

```
sudo /etc/init.d/networking restart INTERFACE=wlan0

```

when I login. This is the result

```
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service smbd reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload smbd
RTNETLINK answers: File exists
```

But I get connected.  The issue I have is that in system settings the network manager says the device is unavailable and the nm-applet is greyed out and says 'device not ready'

I had to manually add my wireless network in interfaces.  Is this how everyone else is doing it?? until the bug is fixed??

---

### Post by shaneo1 on 2011-09-24
Ok I fixed my problem, purged network-manager, rebooted, then installed network-manager again.  

hatch out the settings in /etc/network/interfaces and restarted the computer again, everything is work well now.  

I have an Intel wifi card, for those who want to know.

Thanks to everyone for your help..

Ubuntu Rocks!

---

### Post by ELD on 2011-09-25
Has anyone filed a bug for this?

---

### Post by ombra on 2011-09-30
> **shaneo1 said:**
> Ok I fixed my problem, purged network-manager, rebooted, then installed network-manager again.  

hatch out the settings in /etc/network/interfaces and restarted the computer again, everything is work well now.  

I have an Intel wifi card, for those who want to know.

Thanks to everyone for your help..

Ubuntu Rocks!

Thanks man, you saved me :D

---

### Post by ELD on 2011-10-02
Can anyone say if it has been fixed without workarounds? As i don't want to update my notebook when the final version is out if i have to mess around with networking.

---

### Post by wgarcia on 2011-10-02
Yes, it was fixed a couple of days after the bug appeared. If you hadn't updated during those days nothing wrong was noticed when updating.

---

### Post by ELD on 2011-10-05
Well i updated my 11.04 to 11.10 today on my notebook and it seems my browsing has gone to a crawl again :/

It also seems to crash the net for other people still so it's not fixed.

---

### Post by wgarcia on 2011-10-06
The particularly bug mentioned in this thread was simply caused by a misplaced library, that one was certainly fixed, so what you are seeing is something different. I had another bug:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/865982](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/865982)

but I haven't seen it again since a couple of updates this week in some libraries related to networking.

---

### Post by ELD on 2011-10-06
The bug you linked to is from 2005....

---

### Post by wgarcia on 2011-10-06
Sorry, I pasted the link incorrectly (the last two numbers of the bug were missing). It is really:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/865982](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/865982)

I've edited the other post too.

---

### Post by ELD on 2011-10-06
I dont think it is the same bug as it sounds quite different. Mine doesnt actually say ive disconnected byt the 11.10 crashes the router as my girlfriends windows pc states its lost connection. Its very reproducable my end.

---

