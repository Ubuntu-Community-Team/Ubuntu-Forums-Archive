---
title: "Ndiswrapper Problem"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by stackman1 on 2008-07-19
I am pretty much of a newbie but have been really working to get my wireless card working and am now on the NDISWRAPPER path :)

Below is copy of my terminal session trying to wrap my windows drivers.  Have tried to show that I had no invalid driver, listed the ones I was trying to install etc but as you can see it didn't like something.

At one point I changed my LBSCMNDS.inf to lower case but that didn't help.  I even went into the Perl script in 
/usr/sbin/ndiswrapper-1.9 to find where the error message was coming from but couldn't nail it down.  

I have Gutsy Gibbon and a Linksys WPC54GS V2 (Broadcom 4318 chipset) and no internet connection on the GG machine.
It is probably something stupid like not having my drivers in a particular directory but I was following directions that should have avoided this by navigating to my driver folder and executing Ndiswrapper from there.  Don't you love computers?
Any help would be greatly appreciated.

peter@i2500:~$ sudo ndiswrapper -l
peter@i2500:~$ 
peter@i2500:~$ cd /home/peter/Desktop/Drivers
peter@i2500:~/Desktop/Drivers$ ls
bcmwl5.sys  LBSCMNDS.inf  LSBCMNDS.cat
peter@i2500:~/Desktop/Drivers$ 
peter@i2500:~/Desktop/Drivers$ sudo ndiswrapper -i LSBCMNDS.inf
installing lsbcmnds ...
couldn't open LSBCMNDS.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 181.
peter@i2500:~/Desktop/Drivers$

---

### Post by phidia on 2008-07-19
I don't know how you installed ndiswrapper, but what does > sudo modprobe ndiswrapper output?
BTW you don't need to type out the entire path to a file-linux has commandline complition so if the file exsists and you're in the correct directory just type part of the name and press the tab key-that should autofill the rest of it-it also helps you by avoiding typos and showing what's really available.
There is also a solved thread [here]("http://ubuntuforums.org/showthread.php?t=830090&highlight=ndiswrapper+broadcom+4318") on ndiswrapper with that chipset.

---

### Post by stackman1 on 2008-07-19
When I typed in your command, it asked for my password and then after I entered it it returned:

peter@i2500:/$

---

### Post by waspbr on 2008-07-19
stackman, as far as I can see you haven't really installed the drivers correctly.

got to the link at my signature and go to the wireless bit, I have a similar broadcom card with that uses the same drivers it should work, follow the procedure the wireless howto and you should be fine.

for the drivers, I am posting a link below

[http://rapidshare.com/files/79251578/driver.zip]("http://rapidshare.com/files/79251578/driver.zip")

note when following the howto you don't need to download, (un)install the ndiswrapper, from what I see everything seems to be in place , gl

---

### Post by stackman1 on 2008-07-19
Thanks Waspbr....I will give it a shot and report back....:)

---

### Post by PinkFloyd102489 on 2008-07-19
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)

---

### Post by JagDragon on 2008-07-19
I've been down the ndiswrapper path with the WPC54G, and it's not pretty, but it gets the job done. Provided you are using the latest kernel, there is actually a native driver, the b43, that gets the job done remarkably well. Here is a short tutorial I've written:

Open a new terminal
```
sudo apt-get install b43-fwcutter
wget http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2
tar -xjf broadcom-wl-4.80.53.0.tar.bz2
cd broadcom-wl-4.80.53.0/kmod
sudo b43-fwcutter -w /lib/firmware wl_apsta.o 
```
Close the terminal and reboot

This tutorial (or something like it) was found at [http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43) .
NOTE: This driver will only work on Linux kernel 2.6.24 or older. To find out what kernel version you have, type `uname -r` into a terminal. As of the time of writing, Hardy Heron (8.04) uses 2.6.24, so unless you have manually installed a newer kernel, the above tutorial will work for you.

Enjoy your wireless!

---

### Post by waspbr on 2008-07-19
actually there's even a simpler way (which I had forgotten about) if you haven't gotten around the others yet.I just checked as pointed out above you are one of the lucky buggers whose broacom is supported by the b43 cutter.

[http://wireless.kernel.org/en/users/Drivers/b43#supported]("http://wireless.kernel.org/en/users/Drivers/b43#supported")

just go to synaptic search for b43, the b43-fwcutter option should show, then just check the box, and apply the isntall. As it installs it opens up a dialogue asking if it should fetch the drivers for you, check the box and press foward. you should be done,

---

### Post by stackman1 on 2008-07-19
WASPBR....I only now got back to my computer but I haven't started anything yet, so I will try the above.  Two things though:

1.  My Gutsy Gibbon uses the 2.26.22.14 kernel

2.  It is has no working internet connection; I have an ethernet      problem as well but decided to attack the wireless connection first.

Wish me luck - thanks all
Peter

---

### Post by pgte3 on 2008-07-19
stackman1 could you post the network wireless portion of the lshw command. Here is an example of mine:

           *-network
                description: Wireless interface
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:14:00.0
                logical name: wifi0
                version: 01
                serial: 00:1f:3a:8e:fa:8e
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath_pci ip=192.168.1.100 latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g

How did you determine the wireless card and chip set you are using?

---

### Post by stackman1 on 2008-07-19
*-network UNCLAIMED
          description: Network controller
          product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
          vendor: Broadcom Corporation
          physical id: 0
          bus info: pci@0000:02:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
 
I can't remember how I determined it was a Broadcom chipset, maybe through LSPCI command.  I have been on so many sites over the last week I am losing track.

---

### Post by pgte3 on 2008-07-19
I did a few quick searches for your wireless card. I did not see a Linux driver for the card. It looks like you are going to have to go the ndiswrapper route. I found a few post that deal with your card specifically. I hope these are helpful.

[http://wiki.linuxquestions.org/wiki/Broadcom_4318_Airforce_one_54g_card](http://wiki.linuxquestions.org/wiki/Broadcom_4318_Airforce_one_54g_card)
[http://www.linuxquestions.org/hcl/showproduct.php/product/3587/sl/b](http://www.linuxquestions.org/hcl/showproduct.php/product/3587/sl/b)

---

### Post by stackman1 on 2008-07-19
Pgte3...I followed the instructions from your first link (which was essentially the track I was on when I started the thread) but this time it appears my driver was installed.  Thanks for that.  But even so I have not reached the promised land.

Here are some excerpts from that laptop's terminal sessions:
****
peter@i2500:~$ ndiswrapper -l
peter@i2500:~$ cd /home/peter/drivers
peter@i2500:~/drivers$ ls
bcmwl5.sys  LBSCMNDS.inf
peter@i2500:~/drivers$ ndiswrapper -i LBSCMNDS.inf
couldn't create /etc/ndiswrapper/lbscmnds: Permission denied at /usr/sbin/ndiswrapper-1.9 line 152.
peter@i2500:~/drivers$ ndiswrapper -l
peter@i2500:~/drivers$ sudo ndiswrapper -i LBSCMNDS.inf
installing lbscmnds ...
peter@i2500:~/drivers$ ndiswrapper -l
lbscmnds : driver installed
peter@i2500:~/drivers$ sudo ndiswrapper -m
module configuration already contains alias directive
****
****
LSHW

 *-network
          description: Wireless interface
          product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
          vendor: Broadcom Corporation
          physical id: 0
          bus info: pci@0000:02:00.0
          logical name: eth0
          version: 02
          serial: 00:14:bf:76:15:64
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master ethernet physical wireless
          configuration: broadcast=yes driver=ndiswrapper+lbscmnds driverversion=1.45+The Linksys Group, Inc.,02/ latency=64 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g

peter@i2500:~$ iwconfig
lo        no wireless extensions.

eth0      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
****

I rebooted my modem & router; no luck...

As I have said, the ethernet port(direct cable connection) is also not working but even still - isn't it odd that my wireless info is associated with eth0 and not eth1....

Any insights - greatly appreciated.

---

### Post by falcon61102 on 2008-07-19
By the looks of it, ndiswrapper did install the drivers, however, they don't seem to be running right.  When you installed the drivers did you go through and blacklist the old ones?  Also, where did you get the drivers that you are using now?

---

### Post by falcon61102 on 2008-07-19
> **stackman1 said:**
> 
As I have said, the ethernet port(direct cable connection) is also not working but even still - isn't it odd that my wireless info is associated with eth0 and not eth1....


It should actually show up as wlan0, meaning your first wireless network device.  If you run:
```
sudo gedit /etc/iftab
```
You should see your network devices listed.  You may have to edit that file a little bit in order to get them in the right order.  If you could post that here, we might be able to help figure out what to move around.

---

### Post by stackman1 on 2008-07-19
I believe I took the drivers off the CD that came with my network adapter from Linksys.  I was instructed to update /etc/modprobe.d/blacklist with the following code: 
blacklist bcm43xx (but the file already had that code within).

I will switch back to the laptop in question and run the gedit you've requested. Thanks

---

### Post by falcon61102 on 2008-07-19
You may have to blacklist a couple other drivers.  Normally using bcm43xx, you can cover all of them but sometimes you have to add more but I think you can hold off on doing that right now.

Once you get a look at that file, if present, we may know more.

---

### Post by stackman1 on 2008-07-19
When I tried to edit the iftab file it was empty; /etc/iftab file does not exist....

---

### Post by falcon61102 on 2008-07-19
Yeah, I noticed when I just tried getting a look at mine that I didn't have one either.  I think its the drivers that you're using.  My suggestion is to try some new ones.

I'm going to post a link I got of the Feisty - No Fluff HowTo for some drivers that people have said to work with your card and if you need help going through the process of removing the old ones and installing the new ones I'll help walk you through it.

Here's the link:
[ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe)

---

### Post by JagDragon on 2008-07-19
> **JagDragon said:**
> I've been down the ndiswrapper path with the WPC54G, and it's not pretty, but it gets the job done. Provided you are using the latest kernel, there is actually a native driver, the b43, that gets the job done remarkably well. Here is a short tutorial I've written:

Open a new terminal
```
sudo apt-get install b43-fwcutter
wget http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2
tar -xjf broadcom-wl-4.80.53.0.tar.bz2
cd broadcom-wl-4.80.53.0/kmod
sudo b43-fwcutter -w /lib/firmware wl_apsta.o 
```
Close the terminal and reboot

This tutorial (or something like it) was found at [http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43) .
NOTE: This driver will only work on Linux kernel 2.6.24 or older. To find out what kernel version you have, type `uname -r` into a terminal. As of the time of writing, Hardy Heron (8.04) uses 2.6.24, so unless you have manually installed a newer kernel, the above tutorial will work for you.

Enjoy your wireless!

I have one of these cards, and this really does work. To make it work, what you have to do is (from another computer) download [b43-fwcutter.deb]("http://mirrors.kernel.org/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_011-1_i386.deb") and [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2) .

Copy them to your home directory, run ```
sudo dpkg -i b43-fwcutter.deb
``` to install it (say NO when it asks you to fetch the drivers), and run what I have written above from after the wget command.
```

tar -xjf broadcom-wl-4.80.53.0.tar.bz2
cd broadcom-wl-4.80.53.0/kmod
sudo b43-fwcutter -w /lib/firmware wl_apsta.o 
```
Close the terminal and reboot

Take it from me - this is better than ndiswrapper.

---

### Post by falcon61102 on 2008-07-19
Not to argue with you, but being that he already has ndiswrapper installed, its a simple matter of uninstalling the old drivers and installing the new.  Whereas to use b43fwcutter from here he would also have to remove all the ndiswrapper components as well.  Either way though it should work with the right drivers.

---

### Post by miwaypet on 2008-07-19
Since I have to install my wireless using ndiswrapper, can I help you out?

You typed: peter@i2500:~/drivers$ ndiswrapper -i LBSCMNDS.inf
It should be: ./LBSCMNDS

Readout states: lbscmnds : driver installed
It should also say: hardware present.

So lets do this: $ sudo ndiswrapper -r LBSCMNDS

                 $ sudo ndiswrapper -i ./LBSCMNDS.inf

                 (should say something to the effect of installing driver)

                 $ sudo modprobe -r ndiswrapper

                 $ sudo modprobe ndiswrapper

                 $ sudo ndiswrapper -m

                 $ sudo ndiswrapper -l (driver installed; hardware present.)

                 $ sudo bash -c 'echo "ndiswrapper" >> /etc/modules'

Completely power down the machine. Start back up again. If you saw hardware present earlier you should now see your wireless network.

Hope this helps.

---

### Post by falcon61102 on 2008-07-19
Yeah, that looks about right.  

Might have to work around the Hardy bug, but you won't know that until restart anyway.

---

### Post by pgte3 on 2008-07-19
stackman1 what is the model machine you are attempting to configure? For example I am running on a Toshiba A215-S5837. This information can be help when searching for a possible solution.

---

### Post by stackman1 on 2008-07-19
I rebooted my ubuntu laptop and was preparing to enter in Miwaypet's commands but I typed the following and am wondering if I should still proceed....it appears I am now getting a message about a device present.....should I just go ahead and type the commands or has something changed by rebooting?

peter@i2500:~$ sudo ndiswrapper -l
lbscmnds : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
peter@i2500:~$

---

### Post by falcon61102 on 2008-07-19
For some reason the bcm43xx is still loading and that could be one of the reasons you can't get online.

---

### Post by stackman1 on 2008-07-19
Pgte3...I am running a Inspiron 2500 (dell)

As suggested by an earlier link I know that the command

blacklist bcm43xx

resides in the /etc/modprobe.d/blacklist file.  Is there a way for me to know that this file is being executed/loaded?

---

### Post by JagDragon on 2008-07-20
I may be sounding a bit repetitive, but ditch ndiswrapper. Support for this card is mininmal only, NetworkManager does not work with ndiswrapper (or this card at least), meaning that you have to enter every painful network detail by hand. For every network you log on to.

Please try the b43 driver. It supports both Managed and Monitor mode (Meaning that NetworkManager can use it to search for and manage networks), and it works like a charm, no further configuration. Please try it, it will take you tops 10 minutes.

Download [b43-fwcutter.deb]("http://mirrors.kernel.org/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_011-1_i386.deb") and [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2) .

Copy them to your home directory using a CD or a USB drive, and then run the following code through a terminal to install the b43 driver.
```

sudo dpkg -i b43-fwcutter.deb
tar -xjf broadcom-wl-4.80.53.0.tar.bz2
cd broadcom-wl-4.80.53.0/kmod
sudo b43-fwcutter -w /lib/firmware wl_apsta.o 
```
Close the terminal and reboot, and you will have a working WPC54G.

To prove that this works, see the screenshot here: 
[[IMG]http://img262.imageshack.us/img262/8215/b43wpc54gxt3.th.jpg[/IMG]](http://img262.imageshack.us/my.php?image=b43wpc54gxt3.jpg)

If you look at the lsmod command, you can see that b43 is indeed working. If you look at the lspci command, you will see that I have the same card to you, but a slightly different chipset (me=4306, you=4318). If you hop over to the driver homepage and go to the [supported cards section]("http://linuxwireless.org/en/users/Drivers/b43#supported"), you will find that your chipset works as well as mine.

Ndiswrapper gets the job done, but b43 is native Linux and gets all of the jobs done. ;)

---

### Post by stackman1 on 2008-07-20
Jag, I am willing to try anything and it sounds like this approach yields a more flexible outcome. Thanks for hanging in there, stay tuned.

---

### Post by stackman1 on 2008-07-20
Jag, I have downloaded the tar file but when I click on your link for the b43 fwcutter file it *edits* a load module, not a download site?

---

### Post by stackman1 on 2008-07-20
I found this site to download the fwcutter; any suggestions on which one to download?

[http://bu3sch.de/b43/fwcutter/]("http://bu3sch.de/b43/fwcutter/")

---

### Post by stackman1 on 2008-07-20
I have moved the following two files via a flash drive to my ubuntu laptop:

b43-fwcutter-011.tar.bz2

broadcom-wl-4.80.53.0.tar.bz2

_Based on your instructions:_
sudo dpkg -i b43-fwcutter.deb
tar -xjf broadcom-wl-4.80.53.0.tar.bz2
cd broadcom-wl-4.80.53.0/kmod
sudo b43-fwcutter -w /lib/firmware wl_apsta.o

I leave the broadcom-wl-4.80.53.0.tar.bz2 in compressed mode?  But the b43-fwcutter-011.tar.bz2 is not.

Remember I am new....
1.  When you say copy them to home *Copy them to your home directory using a CD or a USB drive* - I suppose in my case that would be /home/peter  .....?

2.  Then do I unpack fwcutter within /home/peter?  What command do I use?

3.  Finally, assuming that works, I execute your instructions from within the /home/peter folder?

Thanks

---

### Post by JagDragon on 2008-07-20
Whoa there!

How did you manage to download the .deb so that it edits it? I didn't even know you could do that ... Anyway.

Try following my instructions again, but this time download a b43-fwcutter.deb, not a .tar.gz or anything else. Dpkg only installs .deb files, which are Ubuntu/Debian packages. You can find a list of mirrors for the .deb here: [http://packages.ubuntu.com/hardy/i386/b43-fwcutter/download](http://packages.ubuntu.com/hardy/i386/b43-fwcutter/download)

After you have the actual file, try runnning the thing from the top again ;)

Glad I could be of assistance - keep me updated.

---

### Post by stackman1 on 2008-07-20
I had not run anything yet, so I went and downloaded the non-bz file for fwcutter but it looks like it doesn't like my version of something:

peter@i2500:~$ cd /home/peter
peter@i2500:~$ ls
b43-fwcutter_011-1_i386.deb    Documents  nautilus-debug-log.txt  Templates
broadcom-wl-4.80.53.0.tar.bz2  drivers    new file~               Videos
Desktop                        Examples   Pictures                xorg.conf2~
dmesg.boot                     Music      Public
peter@i2500:~$ sudo dpkg -i b43-fwcutter_011-1_i386.deb
[sudo] password for peter:
Selecting previously deselected package b43-fwcutter.
(Reading database ... 88956 files and directories currently installed.)
Unpacking b43-fwcutter (from b43-fwcutter_011-1_i386.deb) ...
dpkg: dependency problems prevent configuration of b43-fwcutter:
 [B]b43-fwcutter depends on libc6 (>= 2.7-1); however:
  Version of libc6 on system is 2.6.1-1ubuntu9.[/B]
dpkg: error processing b43-fwcutter (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 b43-fwcutter
peter@i2500:~$

---

### Post by JagDragon on 2008-07-20
Whoops, my mistake. I thought that that library came with Ubuntu. Easy to fix, though, download the [libc6.deb]("http://packages.ubuntu.com/hardy/i386/libc6/download") and run it at the same time as b43-fwcutter.
```
sudo dpkg -i libc6.deb b43-fwcutter.deb
```

Sorry about that, I know how tireing it is switching computers the whole time.

---

### Post by stackman1 on 2008-07-20
I assume I don't need to uninstall anything....I will give it a shot

---

### Post by stackman1 on 2008-07-20
Here is my latest & greatest:

peter@i2500:~$ cd /home/peter
peter@i2500:~$ ls
b43-fwcutter_011-1_i386.deb    Desktop    drivers   libc6_2.7-10ubuntu3_i386.deb  new file~  Public     Videos
broadcom-wl-4.80.53.0.tar.bz2  Documents  Examples  Music                         Pictures   Templates  xorg.conf2~
peter@i2500:~$ sudo dpkg -i libc6_2.7-10ubuntu3_i386.deb b43-fwcutter_011-1_i386.deb
dpkg: regarding libc6_2.7-10ubuntu3_i386.deb containing libc6:
 libc6 conflicts with tzdata (<< 2007k-1)
  tzdata (version 2007f-3ubuntu1) is present and installed.
dpkg: error processing libc6_2.7-10ubuntu3_i386.deb (--install):
 conflicting packages - not installing libc6
(Reading database ... 88965 files and directories currently installed.)
Preparing to replace b43-fwcutter 1:011-1 (using b43-fwcutter_011-1_i386.deb) ...
Unpacking replacement b43-fwcutter ...
dpkg: dependency problems prevent configuration of b43-fwcutter:
 [B]b43-fwcutter depends on libc6 (>= 2.7-1); however:
  Version of libc6 on system is 2.6.1-1ubuntu9.[/B]
dpkg: error processing b43-fwcutter (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6_2.7-10ubuntu3_i386.deb
 b43-fwcutter
peter@i2500:~$ 

Should I have un-installed something first?  I am using Gutsy Gibbon (7.10).

---

### Post by JagDragon on 2008-07-20
Try running the commands separately.
```
sudo dpkg -i libc6.deb
sudo dpkg -i b43-fwcutter.deb

```

What is your kernel version? ```
uname -r
```

---

### Post by stackman1 on 2008-07-20
2.26.22.14

---

### Post by stackman1 on 2008-07-20
Looks like more of the same...

peter@i2500:~$ cd /home/peter
peter@i2500:~$ ls
b43-fwcutter_011-1_i386.deb    Desktop    drivers   libc6_2.7-10ubuntu3_i386.deb  new file~  Public     Videos
broadcom-wl-4.80.53.0.tar.bz2  Documents  Examples  Music                         Pictures   Templates  xorg.conf2~
peter@i2500:~$ sudo dpkg -i libc6_2.7-10ubuntu3_i386.deb
[sudo] password for peter:
dpkg: regarding libc6_2.7-10ubuntu3_i386.deb containing libc6:
 libc6 conflicts with tzdata (<< 2007k-1)
  tzdata (version 2007f-3ubuntu1) is present and installed.
dpkg: error processing libc6_2.7-10ubuntu3_i386.deb (--install):
 conflicting packages - not installing libc6
Errors were encountered while processing:
 libc6_2.7-10ubuntu3_i386.deb
peter@i2500:~$

---

### Post by stackman1 on 2008-07-20
Is TZDATA the problem?

---

### Post by stackman1 on 2008-07-28
> **waspbr said:**
> stackman, as far as I can see you haven't really installed the drivers correctly.

got to the link at my signature and go to the wireless bit, I have a similar broadcom card with that uses the same drivers it should work, follow the procedure the wireless howto and you should be fine.

for the drivers, I am posting a link below

[http://rapidshare.com/files/79251578/driver.zip]("http://rapidshare.com/files/79251578/driver.zip")

note when following the howto you don't need to download, (un)install the ndiswrapper, from what I see everything seems to be in place , gl

WASPBR....I got off on a different approach with fwcutter but it ran into dependency problems....so I went back and read my thread and tried the link you provided (sauronsmatrix)
[http://ubuntuforums.org/showpost.php?p=3491929&postcount=257]("http://ubuntuforums.org/showpost.php?p=3491929&postcount=257")

And while I only partially was successful with the commands: I didn't do any of the make commands and the blacklisting told me my permission wasn't available....I just rebooted and did an iwlist scanning command as suggested and clearly my nic card sees my linksys router (minnesota_router) and my neighbors (Air_Harry).  Can you walk me through whatever I have to do to activate my connection?  I've been trying to use network administration but can't seem to get it going.....I feel like I am almost there!.....thanks in advance Peter.

peter@i2500:~$ sudo iwlist scanning
[sudo] password for peter:
lo        Interface doesn't support scanning.

eth0      Scan completed :
          Cell 01 - Address: 00:1D:7E:E8:74:86
                    ESSID:"minnesota_router"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:46/100  Signal level:-66 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:18:39:70:F0:1F
                    ESSID:"Air Harry"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:12/100  Signal level:-88 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK

peter@i2500:~$ cd /home/peter/Desktop/Drivers
peter@i2500:~$

---

### Post by waspbr on 2008-07-29
hmmm, weird about the blacklisting... provided you were on root mode your should have been able to do it. Another way of blacklisting is to do


```
sudo gedit /etc/modprobe.d/blacklist
```

and then enter an entry manually (normally to the bottom of the page)

for example

```
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist ssb
```

BUT

if you can already see the connections then I **guess** there's no point...

anyway you should be almost there, on your top left corner-ish, you should see a the network-manager applet icon. left clicking on it should display all the connections it sees. chose the one you want, it should then prompt you for the appropriate passkey for the security settings you have.

good luck.

---

### Post by stackman1 on 2008-07-29
Was..I didn't see the icon on the upper left but on upper right there was an icon with double monitors and that took me back into the network settings dialog but when I put in the essid and password for my wep....it doesn't respond.  

The iwlist command shows that I can pick up the signal but the iwconfig command shows that my computer is not configured to bring in the signal.  I don't know why Network Admin is not working but it gives me no feedback.

Can you or someone give me the terminal commands to try and force the issue, at least that way I will get some message feedback from the terminal.

(This is an Inspiron 2500 Dell Laptop (2002) which I wiped XP off of and loaded Gutsy Gibbon on....looks like the driver issue is behind me - thanks to you guys - but it seems my machine needs a bit more configuration to activate the wireless process).

peter@i2500:~$ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Scan completed :
          Cell 01 - Address: 00:1D:7E:E8:74:86
                    ESSID:"minnesota_router"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:62/100  Signal level:-56 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

peter@i2500:~$ sudo iwconfig
lo        no wireless extensions.

eth0      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Thanks
Peter

---

### Post by caljohnsmith on 2008-07-29
Have you seen this guide for setting up your network connection via the CLI without using Network Manager? 

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

I think that may be what you are looking for at this point.

---

### Post by stackman1 on 2008-07-29
Thanks Cal...I'll take a look.

---

