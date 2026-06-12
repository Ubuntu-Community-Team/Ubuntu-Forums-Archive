---
title: "HOWTO: Ralink RT2570 usb wireless driver"
date: 2005-12-21
forum: Outdated Tutorials &amp; Tips
---

### Post by Lambert on 2005-12-21
This howto derived from this [thread]("http://ubuntuforums.org/showthread.php?t=106328"). 
Similar thread can be found [here.]("http://ubuntuforums.org/showpost.php?p=618022&postcount=3") Haven't compared but that thread has two posts w/ verified working driver following those instructions.


Homepage for the rt2570 driver can be found [here.]("http://rt2x00.serialmonkey.com/wiki/index.php/Downloads") 

This [link]("http://http://rt2x00.serialmonkey.com/wiki/index.php/Hardware") shows a list of devices reported by users to work with the rt2xxx drivers. Which the rt2570 section shows the dwl-g122 as working with this driver. I've seen quite a few posts lately about getting this device to work. Post your results and success stories for others to see. 

[B]Preparation
[/B]If not installed already, these packages need to be installed.

```
sudo apt-get install build-essential linux-headers-`uname -r` gcc-3.4
``` 
At the time this was written driver was rt2570-1.1.0-b1. If driver is updated commands will need to change to that file name.


[B]Step 1 Download and untar file
[/B]
Get file
Go [here]("http://rt2x00.serialmonkey.com/wiki/index.php/Downloads") and choose the rt2570beta driver. You'll get a choice of mirrors where to download from. Save it to file.

Now copy the file to /usr/src
```
sudo cp /path/to/file/rt2570-1.1.0-b1.tar.gz /usr/src/
``` 
Move to /usr/src
```
cd /usr/src
``` 

Untar file
```
sudo tar -xzvf rt2570-1.1.0-b1.tar.gz
``` 
Move into file
```
cd rt2570-1.1.0b1/Module
``` 
**Step 2 Make and install file**

```
sudo make
``` 

```
sudo make install
``` 
**Step 3 Set up and load module**

make a directory for the .ko file
```
sudo mkdir /lib/modules/`uname -r`/drivers/
``` 
copy file over to new directory
```
sudo cp /lib/modules/2.6.12/extra/rt2570.ko /lib/modules/`uname -r`/drivers/
``` 
Then insert module into kernel
```
sudo insmod /lib/modules/`uname -r`/drivers/rt2570.ko
``` 
```
sudo lsmod -a
``` 
Configure your wireless device through /etc/network/interfaces. Here is a sample file.

                             iface rausb0 inet dhcp
 wireless-essid apname
 wireless-key xxxxxxxxx
 wireless-mode Managed
 auto rausb0

restart the networking service

```
sudo /etc/init.d/networking restart
``` 


Now try to bring up your device

```
sudo ifconfig rausb0 up
``` 
To load module at boot add it to /etc/modules file

```
sudo echo rt2570 >> /etc/modules
``` 
[B]Report bugs
[/B]This driver is a beta driver and there are probably bugs. In /usr/src/rt2570-1.1.0-b1/Modules/ there is a file TESTING. Read this file as it gives information on logging and reporting bugs.

---

### Post by jnorth on 2006-01-08
Hi - just following up on this... I'm one of the users who's been able to get the rt2570 driver working for a WUSB54Gv4 device.  There are a few extra steps that I had to do to get it working on my system.  You can see  the whole process I followed [here]("http://ubuntuforums.org/showpost.php?p=618022&postcount=3"), but basically, follow Lambert's steps except for these things:
1. On my system - I couldn't get modprobe/insmod to see the driver unless I put the rt2570.ko file in another directory:
```
sudo mv /lib/modules/2.6.xx/extra/rt2570.ko /lib/modules/2.6.xx-xx-xxx/kernel/drivers/net/wireless/rt2570.ko
```
2. Also, the install put the alias line in a new file called modprobe.conf, which isn't standard order on Debian/Ubuntu - may as well move it to the correct area:
```
sudo mv /etc/modprobe.conf /etc/modutils/rt2570
```
3. As per Lambert, load the module up and you should be good to go with the rest of your ifconfig/iwconfig steps, or use the gui to configure.
```
sudo depmod -a
sudo update-modules
sudo modprobe rt2570
```

---

### Post by ned.b on 2006-01-09
Thanks Lambert - this worked! :-)

---

### Post by Ailis on 2006-01-10
I managed to get this to work...sorta. I've got one problem left. The wireless suddenly goes inactive and I have to go to *system --> administration -->networking* and activate it manually again. (I also have to do this when I start up).

Any ideas what may be the problem?

---

### Post by danish_demon on 2006-01-13
[QUOTE=Lambert]
Configure your wireless device through /etc/network/interfaces. Here is a sample file.

iface rausb0 inet dhcp
 wireless-essid apname
 wireless-key xxxxxxxxx
 wireless-mode Managed
 auto rausb0

[/QUOTE]

i am with you until this part. do i actually put in "apname" for essid?  how do i find out what my wireless-key is?  help somebody, please.:(

---

### Post by Lambert on 2006-01-16
[quote=Ailis]I managed to get this to work...sorta. I've got one problem left. The wireless suddenly goes inactive and I have to go to *system --> administration -->networking* and activate it manually again. (I also have to do this when I start up).

Any ideas what may be the problem?[/quote]

Suddenly goes inactive? hmm go to terminal and type dmesg after this happens. Also check /var/log/syslog
Hopefully one of these will give someoutput

Also sometimes signal interference can casue a connection to drop. Can you change and try another channel?

---

### Post by Lambert on 2006-01-16
[quote=danish_demon]i am with you until this part. do i actually put in "apname" for essid?  how do i find out what my wireless-key is?  help somebody, please.:([/quote]

You need to know the ssid of the router you want to connect to. You can try to scan for the router with this command if you don't know it.

sudo iwlist rausb0 scan

here is a sample

```
 Cell 05 - Address: 00:12:17:A6:AA:3F
                    ESSID:"linksys-g"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=6/94  Signal level=-89 dBm  Noise level=-95 dBm
                    Encryption key:on

```

so if this was the router you wanted to connect to this is what it would look like.

iface rausb0 inet dhcp
wireless-essid linksys-g
wireless-mode managed
wireless-key xxxxx
auto rausb0

What is the key? You have to know it. But if there is no encryption on the router you don't need a key, you can just remove that line.

---

### Post by danish_demon on 2006-01-16
thanks lambert.  i was able to figure it out by comparing the relevant info to that on my desktop (which i am online with via ndiswrapper).  i sometimes have the same problem as that other person though (i.e. not working at start-up or suddently dropping the connection).  i'll try the things you suggested though.

---

### Post by Ailis on 2006-01-28
> Suddenly goes inactive? hmm go to terminal and type dmesg after this happens. Also check /var/log/syslog
Hopefully one of these will give someoutput

Also sometimes signal interference can casue a connection to drop. Can you change and try another channel?

The dmesg command gives a lot of cryptic output. Most of it seems to repeat itself though, so I'll just show you the last lines:

```

08:00 SRC=192.168.1.1 DST=192.168.1.101 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=2224 2 PROTO=UDP SPT=19743 DPT=137 LEN=58
[4314829.914000] hub 4-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[4314829.914000] usb 4-2: USB disconnect, address 5
[4314829.915000] unregister_netdev( )
[4314831.013000] usb 4-2: new high speed USB device using ehci_hcd and address 6
[4314831.278000] idVendor = 0x13b1, idProduct = 0xd
[4314831.280000] INIT bRadio=1
[4314832.462000] RT25usb  Driver version 1.1.0

```

The syslog-file also has a lot of output in it. Difficult to say what's the interesting part in it. Does this make any sense:

```

Jan 28 19:29:40 localhost dhclient: DHCPRELEASE on rausb0 to 192.168.1.1 port 67
Jan 28 19:29:40 localhost dhclient: send_packet: Network is unreachable
Jan 28 19:29:40 localhost dhclient: send_packet: please consult README file rega$
Jan 28 19:29:40 localhost kernel: [4314832.462000] RT25usb  Driver version 1.1.0

```

I'm not sure I understand what another channel is. I'm a newbie at all this stuff. :-| 
Thanks for the help so far:)

---

### Post by Lambert on 2006-01-28
Didn't see anything in what you posted.

A channel is just like a radio station, it broadcasts at a certain frequency. So your router and wireless adaptor are connected on a specific channel (or frequency).

You can run iwconfig to see what frequency you're on.

```
Frequency:2.437 GHz
```

This is channel six.

To change frequency you need to first change your router settings. See your routers documentation for how to access and administer your router's settings. Then after making the change you'll have to reconnect on the new channel. Driver is usually set at auto so this should happen with out doing anything except deactivating and reactivating the card. If you need to specify channel you can do it like this.

sudo iwconfig ra0 channel X
or 
sudo iwconfig ra0 freq 2.4XXG

replaces X with relevant data.

---

### Post by Ailis on 2006-01-29
Ok, thanks. Don't think I'll attempt that just yet though. The connection's been up and running nonstop all day for a change. I think it's only been one day when it disconnected every fifth minute. As long as it's not like that I think I'll manage. Maybe I'll get rid of the problem when I upgrade to Dapper. :)

---

### Post by antisc on 2006-02-08
edit: mistake

---

### Post by Kartik Babu on 2006-02-09
I think I have a weirder problem. I compiled and installed the driver, and did depmod -a, modprobe rt2570 and lsmod shows that the driver has been loaded.

My /etc/network/interfaces file looks like this:

```
kbabu@workhorse:~$ more /etc/network/interfaces
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

# The primary network interface
iface eth0 inet dhcp

#wireless network interface using Linksys WUSB54GC

iface rausb0 inet dhcp
wireless-essid whatever
wireless-mode ad-hoc
auto rausb0
```

now when I restart my networking, I still dont see rausb0

using ifconfig rausb0 up gives me this error:
```
kbabu@workhorse:~$ sudo ifconfig rausb0 up
rausb0: ERROR while getting interface flags: No such device

```

Halp!! whats going on here? I want to use the ad-hoc mode because Its necessary to setup a point-to-point wireless connection between two PC's there really isnt a wireless access point available. Shouldnt the interface at least be up? so that I can use iwconfig and configure it as I please?

thanks

---

### Post by aeiah on 2006-02-13
hi. im new. hello.

im basically writing this for those people who like me, havent got easy access to a wired connection to aquire all the packages needed to install this wireless card. this post has all the .deb files listed that you'll need to (hopefully) get the Ralink RT2570 usb wireless driver working when you have no net access. (ok, ill stop trying to cram possible key words in now).

this is the 3rd time ive installed this driver, the first time was on the i386 kernel, the 2nd on the k7-smp kernel and the third time was 10 minutes ago, all without a hitch. this most recent installation was on a clean i386 install after i managed to completley mangle the xserver. i dont have easy access to a wired connection right now, so i set about downloading the required .deb packages from [http://packages.ubuntu.org](http://packages.ubuntu.org) within my windows xp installation over wlan. it took me aaagess, going back and forth, finding out i needed yet another .deb file so the first .deb would install etc. so hopefully this'll save someone a bit of time.

this worked for me running ubuntu breezy and the basic spec of my system is an AMD64 3800 X2 on an nForce 4 motherboard.


---the possibly useful stuff---

create a folder that is easy to access within ubuntu (like a shared FAT partition) or a folder to later burn to a cd and save everything you download to it.

- open the first page of this thread in a new tab and save the page 

- download the wireless driver from the link provided at the start of this thread

download these from [http://packages.ubuntu.com](http://packages.ubuntu.com) , making sure you select the correct type for your kernel (i386, k7-smp, etc). as always, type 'uname -r' in the terminal/command prompt if unsure:

gcc-3.4-base_3.4.4-6ubuntu8_i386.deb
cpp-3.4_3.4.4-6ubuntu8_i386.deb
gcc-3.4_3.4.4-6ubuntu8_i386.deb
linux-headers-2.6.12-9_2.6.12-9.23_i386.deb
linux-headers-2.6.12-9-386_2.6.12-9.23_i386.deb
linux-kernel-headers_2.6.11.2-0ubuntu13_i386.deb
libc6-dev_2.3.5-1ubuntu12_i386.deb
binutils_2.16.1-2ubuntu6_i386.deb
make_3.80-9_i386.deb

boot to linux, find the folder you placed them in (or place them in a folder if they're on a cd or other media) and do

sudo dpkg -i gcc-3.4-base_3.4.4-6ubuntu8_i386.deb
sudo dpkg -i cpp-3.4_3.4.4-6ubuntu8_i386.deb

etc, in the listed order, then follow the HOW TO that you saved. if any errors come up requesting packages to be installed before others, then im sorry, i messed the order up :p just do them in the order it tells you.

hope it helps the next person like me who spent far too long tracking down those packages.

---

### Post by newuser111 on 2006-02-13
it worked perfectly first time following what is written in  the first post, thanks for this howto

much better than the pages of ndiswrapperr nonsense, hopefully drivers like this will sort out the problem wireless support in linux

---

### Post by bailout on 2006-02-14
I followed aeih's list of packages as I also  don't have access to a wired connection. It seemed to be ok except binutils should be third in the list I think.

However, I was puzzled as to the kernel number 2.6.12-9 as my grub page says 2.6.12-10. When I tried to dl the version 10 headers I just get a 404 page??? So I went ahead with the -9 files.

When I then tried following the driver install from the first page I got an error msg on the make stage

???@???:/usr/src/rt2570-1.1.0-b1/Module$ sudo make
make: *** /lib/modules/2.6.12-10-386/build: No such file or directory.  Stop.
rt2570.ko failed to build!
make: *** [module] Error 1

Is this because I am running on the -10 kernel and have -9 headers installed?

I still have the -9 kernel so I will try booting into that and trying again.

Do driver installs of this type need redoing with every kernel upgrade?

---

### Post by newuser111 on 2006-02-15
the kernel headers have to match the same kernel version

---

### Post by rama on 2006-02-15
I followed the steps up to the part where we try to restart the network interface. At that point my computer hangs. If I dont clean up the /etc/network/interfaces file from the extra lines it also hangs on boot. 
the wierd thing is that I can see the device installed but not configured from the "networking" application. If I click on properties the copmuter hangs ... again.

My wifi device is a D-Link DWL-g122 rev. C usb stick. Does this simply mean that the drived does not support this rev. of the device? Does the kernel version have anything to do with this? Mine is 2.6.12-10-k7.

---

### Post by Lambert on 2006-02-17
[quote=rama]I followed the steps up to the part where we try to restart the network interface. At that point my computer hangs. If I dont clean up the /etc/network/interfaces file from the extra lines it also hangs on boot. 
the wierd thing is that I can see the device installed but not configured from the "networking" application. If I click on properties the copmuter hangs ... again.

My wifi device is a D-Link DWL-g122 rev. C usb stick. Does this simply mean that the drived does not support this rev. of the device? Does the kernel version have anything to do with this? Mine is 2.6.12-10-k7.[/quote]

post output of these commands

```
sudo cat /proc/version
sudo modinfo rt2570
```

---

### Post by rama on 2006-02-17
```
sudo cat /proc/version
Linux version 2.6.12-10-k7 (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Feb 13 12:29:26 UTC 2006

sudo modinfo rt2570
filename:       /lib/modules/2.6.12-10-k7/drivers/rt2570.ko
description:    Ralink RT2570 usb 802.11g WLAN driver 1.0.0 - CVS 2005/06/01
author:         http://rt2x00.sourceforge.net
license:        GPL
vermagic:       2.6.12-10-k7 K7 gcc-3.4
depends:        usbcore
alias:          usb:v0411p0066d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0067d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp7050d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp705Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE000d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0707pEE13d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1706d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1707d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6861d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6865d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6869d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p8001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p8007d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v114Bp0110d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p000Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0011d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p001Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp1706d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2570d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2573d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp9020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C02d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14F8p2570d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C00d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C03d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p008Bd*dc*dsc*dp*ic*isc*ip*
srcversion:     E42BF015183EEDE0D4C1F4B
parm:           debug:Enable level: accepted values: 1 to switch debug on, 0 to switch debug off. (i)

```

Hope it helps.

---

### Post by pedor on 2006-02-17
When I try to make, I get the following error message

make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
make[1]: Makefile: Filen eller katalogen finns inte 
               (file or directory does not exist)
make[1]: *** Ingen regel för att skapa målet "Makefile".  Stannar.
               (no rule to create goal 'Makefile'. Stops.)
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
rt2570.ko failed to build!
make: *** [module] Fel 1

I have the 2.6.12-9-386 kernel. I need help. What can be the cause of this
problem?:confused:

---

### Post by Lambert on 2006-02-17
[quote=rama]```
sudo cat /proc/version
Linux version 2.6.12-10-k7 (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Feb 13 12:29:26 UTC 2006

sudo modinfo rt2570
filename:       /lib/modules/2.6.12-10-k7/drivers/rt2570.ko
description:    Ralink RT2570 usb 802.11g WLAN driver 1.0.0 - CVS 2005/06/01
author:         http://rt2x00.sourceforge.net
license:        GPL
vermagic:       2.6.12-10-k7 K7 gcc-3.4
depends:        usbcore
alias:          usb:v0411p0066d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0067d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp7050d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp705Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE000d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0707pEE13d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1706d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1707d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6861d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6865d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6869d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p8001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p8007d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v114Bp0110d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p000Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0011d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p001Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp1706d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2570d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2573d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp9020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C02d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14F8p2570d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C00d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C03d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p008Bd*dc*dsc*dp*ic*isc*ip*
srcversion:     E42BF015183EEDE0D4C1F4B
parm:           debug:Enable level: accepted values: 1 to switch debug on, 0 to switch debug off. (i)

``` 
Hope it helps.[/quote]

kernel and gcc build looks ok. See post two though of this thread. Your modinfo shows the module in /lib/mod/kernel/driver/ and that post suggests moving it to /lib/module/kernel/driver/net/wireless. that post shows to mv from .../extra/ you need to replace the extra path with the path shown in in your modinfo output though so you don't have two driver files in the kernel path.

then run the command

sudo depmod -a

and try to modprobe module and then configure device.

---

### Post by psychomantis4 on 2006-02-18
Hi,

I'm trying to make the file, and it keeps giving me the message:

> alex@ubuntu:/usr/src/rt2570-1.1.0-b1/Module$ sudo make
make[1]: Entering directory `/lib/modules/2.6.12-9-386/build'
make[1]: Nothing to be done for `modules'.
make[1]: Leaving directory `/lib/modules/2.6.12-9-386/build'
rt2570.ko failed to build!
make: *** [module] Error 1

Do I have to add a package, or remove something?

-Alex

---

### Post by Lambert on 2006-02-18
[quote=psychomantis4]Hi,

I'm trying to make the file, and it keeps giving me the message:



Do I have to add a package, or remove something?

-Alex[/quote]

Where did you pull linux headers from? the install cd or do you have other internet access and you pulled from repos?

---

### Post by rama on 2006-02-19
[QUOTE=Lambert]kernel and gcc build looks ok. See post two though of this thread. Your modinfo shows the module in /lib/mod/kernel/driver/ and that post suggests moving it to /lib/module/kernel/driver/net/wireless. that post shows to mv from .../extra/ you need to replace the extra path with the path shown in in your modinfo output though so you don't have two driver files in the kernel path.

then run the command

sudo depmod -a

and try to modprobe module and then configure device.[/QUOTE]

Could you clarify this a bit please? I dont know if after sudo make I should do:
sudo make install or just copy the rt2570.ko file to :
/lib/modules/`uname -r`/kernel/drivers/net/wireless/rt2570.ko
and then do 

```
sudo mv /etc/modprobe.conf /etc/modutils/rt2570
sudo depmod -a
sudo update-modules
sudo modprobe rt2570

```

I am trying to do a clean install again. The first step I took was to remove any additional kernels I had installed. Then I noticed that the how to says to install gcc-3.4 so I ll try to do something like: 
```
su
CC=gcc-3.4
export CC
exit
CC=gcc-3.4
export CC
```
before sudo make.
I m also wondering what lsmod -a does since when I execute it I get :
Usage: lsmod

---

### Post by psychomantis4 on 2006-02-19
I got the list from the previous page of this thread, and downloaded them from the ubuntu source webpage. Here's the list:

> gcc-3.4-base_3.4.4-6ubuntu8_i386.deb
cpp-3.4_3.4.4-6ubuntu8_i386.deb
gcc-3.4_3.4.4-6ubuntu8_i386.deb
linux-headers-2.6.12-9_2.6.12-9.23_i386.deb
linux-headers-2.6.12-9-386_2.6.12-9.23_i386.deb
linux-kernel-headers_2.6.11.2-0ubuntu13_i386.deb
libc6-dev_2.3.5-1ubuntu12_i386.deb
binutils_2.16.1-2ubuntu6_i386.deb
make_3.80-9_i386.deb

Do I need anything else?  All of them installed flawlessly, yet I get the same error.  Thanks for the response!!

---

### Post by bailout on 2006-02-19
What version kernel are you using? That list has the 12-9 version, if you have updated from apt you are probably running the 12-10 version. Grub will tell you when you start up. When I did it I couldn't find the 12-10 packages on the source webpage - the links just went to a 404 page. I still had the 12-9 kernel installed so I installed the driver on that and then went online to get the latest headers package through adept and then repeated for the 12-10 kernel.

---

### Post by psychomantis4 on 2006-02-20
I'm running 12-9.  I guess it would build easier and be more efficient with the 12-10 kernel, huh?  Updating the kernel and reconfiguring everything kinda takes awhile, and I have class in the morning...I'll upgrade tomorrow and let you know how it goes.  Thanks for the help!

---

### Post by bailout on 2006-02-20
If you are running 12-9 then you should be fine with those packages. I just wondered if you had updated to 12-10 and hence had the same problem as I did. I installed fine with 12-9 at first.

---

### Post by psychomantis4 on 2006-02-20
Ahh, crap.  Lol, do you recommend that I go to 12-10 anyways?  Because I installed all those packages and I keep on getting that same message.  Do you think with the new kernel it would fix the problem?  And how would I go about that, would I just type in 'sudo apt-get upgrade'?

---

### Post by Floppyjoe on 2006-02-26
When i enter the make command after untaring the driver file, I get an error

Make: *** /lib/modules/2.6.12-9-386/build: no such file or directory. stop.  rt2570.ko failed to build!
Make: *** [module] Error 1

---

### Post by jnorth on 2006-02-26
[QUOTE=Floppyjoe]When i enter the make command after untaring the driver file, I get an error

Make: *** /lib/modules/2.6.12-9-386/build: no such file or directory. stop.  rt2570.ko failed to build!
Make: *** [module] Error 1[/QUOTE]


Looks like you need to get the headers for your architecture to complete your build environment.  You can use synaptic/aptitude or whatever gui you use, or just open a command prompt and run(for your kernel, older may need to substitue "kernel-headers")```
sudo apt-get install linux-headers-`uname -r`
```

Then try to make again - that should do you!  If not, post the error back again and we look further.

---

### Post by williamghanley on 2006-03-02
[QUOTE=jnorth]Looks like you need to get the headers for your architecture to complete your build environment.  You can use synaptic/aptitude or whatever gui you use, or just open a command prompt and run(for your kernel, older may need to substitue "kernel-headers")```
sudo apt-get install linux-headers-`uname -r`
```

Then try to make again - that should do you!  If not, post the error back again and we look further.[/QUOTE]

i tried this and i got this message:
 sudo apt-get install linux-headers-`uname -r`
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?

 what thoughts anyone

---

### Post by jnorth on 2006-03-02
[QUOTE=williamghanley]i tried this and i got this message:
 sudo apt-get install linux-headers-`uname -r`
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?

 what thoughts anyone[/QUOTE]

Most likely you have synaptic/aptitude/kynaptic or some other package manager running.  If you can't find what it is that is locking the directory, then just do a reboot and try again before opening anything else.

If you still have trouble you could try booting to recovery mode... hopefully you can find what it is you have running without that though.

---

### Post by trorion on 2006-03-07
I've succesfully installed the card but it seems to have a problem for me.  It frequently does not come on at all when I boot (though the lights come on) and when it does come on I find very slow speeds (cable modem and my speed is in the 600-800 bytes/sec)

```
some of my outputs:
sudo /etc/init.d/networking restart
sudo ifconfig rausb0 up


fochs@trorion:~$ sudo cat /proc/version
Password:
Linux version 2.6.12-10-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Jan 16 17:18:08 UTC 2006
fochs@trorion:~$



fochs@trorion:~$ sudo modinfo rt2570
filename:       /lib/modules/2.6.12-10-386/drivers/rt2570.ko
description:    Ralink RT2570 usb 802.11g WLAN driver 1.1.0 BETA1 2005/07/31
author:         http://rt2x00.sourceforge.net
license:        GPL
vermagic:       2.6.12-10-386 386 gcc-3.4
depends:        usbcore
alias:          usb:v0411p0066d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0067d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp7050d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0707pEE13d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1706d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1707d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6861d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6865d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6869d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p8001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p8007d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v114Bp0110d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p000Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0011d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp1706d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2570d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp9020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C02d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14F8p2570d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C00d*dc*dsc*dp*ic*isc*ip*
srcversion:     BB18C8BB53E08164CA9DFEA
parm:           debug:Enable level: accepted values: 1 to switch debug on, 0 to switch debug off. (i)



My /etc/network/interfaces file:
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
	map rausb0

# The primary network interface
iface eth0 inet dhcp

iface rausb0 inet dhcp
wireless-essid network-name
wireless-mode managed

auto rausb0
```

I don't know if anyone can help or not.

---

### Post by jnorth on 2006-03-08
[QUOTE=trorion]I've succesfully installed the card but it seems to have a problem for me.  It frequently does not come on at all when I boot (though the lights come on) and when it does come on I find very slow speeds (cable modem and my speed is in the 600-800 bytes/sec)

......
[/QUOTE]

Wierd - seems like more of a network thing than a driver thing.  Then I'm no "Master of Linux" either - only been playing with it for the last 4-5 years.

If your box boots again sometime and it doesn't seem to have loaded the driver, try running an 'iwconfig rausb0' from the shell and see if it gives you something like this:
```

jnorth@calypso:~$ iwconfig rausb0
rausb0    RT2500USB WLAN  ESSID:"xxxxxxxxxxxx"
          Mode:Managed  Frequency=2.437 GHz  Access Point: xx:xx:xx:xx:xx:xx
          Bit Rate=11 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=0/70  Signal level:-57 dBm  Noise level:-195 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jnorth@calypso:~$

```
If so, your driver is working fine, we can move on to a network issue.  Also, you might check your signal levels compared to mine above - that gives me about 80% at the -57dBm level.  The link quality for some reason doesn't work.

I have my network set up with static IP's, but I also had to pull the hotplug entry for eth0/eth1 out of my ifconfig, it was causing long boot times and for some reason, anytime I opened up KDE's network gui, it would change the default route back to eth0 instead of rausb0.

Here's my ifconfig, maybe it can help also.
```

jnorth@calypso:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
auto rausb0
iface rausb0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1
jnorth@calypso:~$

```

Sorry for not having anything more specific, all I can say is that if your driver is loading correctly, it's mroe than likely a network/routing slowdown.  If you find out anything else we can look at that.

---

### Post by trorion on 2006-03-08
OK, iwconfig rausb0:
```
rausb0    RT2500USB WLAN  ESSID:"id"
Mode:Managed  Frequency=2.437 GHz  Access Point: 00:xx:xx:xx:xx:xx
Bit Rate=11 Mb/s
RTS thr:off   Fragment thr:off
Link Quality=0/70  Signal level:-32 dBm  Noise level:-200 dBm
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
I'm guessing that the access point should be different?
My speed is 100-300bytes/s

When I activate my eth0 I get 80KB/s

I'm going to try re-doing my interfaces file I think.  If that doesn't work I'll re-install from scratch.

---

### Post by jnorth on 2006-03-08
[QUOTE=trorion]OK, iwconfig rausb0:
......
I'm guessing that the access point should be different?
My speed is 100-300bytes/s

When I activate my eth0 I get 80KB/s

I'm going to try re-doing my interfaces file I think.  If that doesn't work I'll re-install from scratch.[/QUOTE]

Is your essid actually set at "id" or was that commented out?  If it was at "id" and your access point ssid is named different, as far as I know, that shoudln't even let you connect.

Anyway - I haven't figured out why eth0 or other interfaces being enabled/disabled causes issues - it does that on mine too, except it's when eth0 is enabled that I experience lower speeds and hangs.

One other thing - are your bandwidth measurements throughput to the 'outside' - ie file downloads, etc, or are they test on your local network, say to another home server?  Not to insult you, but just making sure they are inside your local network.

---

### Post by trorion on 2006-03-09
All of my throughput was based on [www.cnnfn.com](www.cnnfn.com) and I'm not trying to get exact with it.  I know it's not a real number but the difference is great enough and consistent enough that that I don't have a problem saying the setup is whacked.

As far as the "id" yeah, I edited that.

Originally my connection point was 00:00:00:00... so basically it had no connection.

I decided I wanted to get my /home on it's own mountpoint and since I have so very little on the system I just re-formatted the drive and will try re-installing the drivers tonight.  It's a d-link d-122 rev.B card that i'm using so I suppose I should use the 2700 drivers.  I think my first time around I tried the 2500 then did the 2x00 test drivers but I don't remember for certain.

We'll see what happens!

Is there a link anywhere that would give information on all the different commands I can use to find out what's going on with my card?

iwconfig *cardname*: tells you this that and the other [see man iwconfig]

or something like that?

---

### Post by tomsyco on 2006-03-17
I am recieving this durring build

tom@ubuntu:~/usr/src/rt2570-1.1.0b1/Module sudo make
make[1]: Entering directory `/lib/modules/2.6.12-10-386/build'
make[1]: *** No rule to make target `modules'. Stop.
make[1]: Leaving directory `/lib/modules/2.6.12-10-386/build'
rt2570.ko failed to build!
make: *** [module] Error 1

I have installed everything that was mentioned but i still cant get it to work.
Please help!

---

### Post by mitanc on 2006-03-19
I just followed the guide and got these drivers up and running in a snap yesterday.  The only thing was, I setup the drivers as the first thing after my install, and soon after Ubuntu decided to update my system.  As an effect my kernel was upgraded as well and when I rebooted, the wireless modules were no longer in effect.  

I apt-get'd the new kernel headers and installed the stuff again and now it thanksfully works fine.  What I want to know is if there is a way to install the modules once so when my kernel gets upgraded yet again, I don't have to go thru the same procedure?

---

### Post by tomjennings on 2006-03-24
Thank you, thank you, thank you! I've been battling the Linksys WUSB45G rev4, yours was the first beam of light through the gloom...

I installed with your howto, as-is; lucky for me, same minor kernel rev, didn't even have to edit command lines.

Not to complain (since I'm not offering to fix it :-) but the ubuntu help/wikis point to a lot of NDIS wedge crap to run a M$ driver for this solution; maybe the beta driver here isn't ready for prime time, I'm sure I'll find out in coming weeks :-)

Note that my WUSB54G has a different product code than most I find on the net:

root@hornet:~# lsusb
blah blah    ID 13b1:000d  
...

000d instead of the more common 0011. Hence no descriptive comment.


ubuntu 5.10, VIA EPIA 5000, Linksys WUSB54G rev4; dedicated semi-headless wireless music server in a vintage automobile. No possiblity of a PCI wifi card, stuck with USB. 

root@hornet:~# uname -a
Linux hornet 2.6.12-10-386 #1 Sat Mar 11 16:13:17 UTC 2006 i686 GNU/Linux

PS: Didn't have to restart networking; ifup rausb0 was enough after loading module. I was umm reluctant to restart net, since I was ssh'ed in from outside the machine.

Note that other ubuntu user's notes on ubuntu-specific paths for module junk.

Thanks again for the fabuluous information. 

tomj

---

### Post by trorion on 2006-03-24
The good news...Dapper has the driver by default and we don't have to do any of this.

---

### Post by acegolfer on 2006-03-25
[QUOTE=trorion]The good news...Dapper has the driver by default and we don't have to do any of this.[/QUOTE]

I did a clean install of Dapper Flight 5 and can't find the driver for rt2570. BTW, my adapter is WUSB54G V4 with Ralink chipset. 

I had to follow the steps plus 2 additional ones to configure the rausb0. WEP works but WPA still doesn't work for me. 

After changing the /etc/network/interfaces to configure WPA and rebooting, the PC doesn't activate the adapter. When I manually activate rausb0, the PC hangs.

I'm almost giving up running Ubuntu on my wireless PC. My wired server machine runs Ubuntu almost flawlessly 24/7.

---

### Post by chameleon on 2006-03-28
When I do this 

```
sudo insmod /lib/modules/2.6.15-19-386/drivers/rt2570.ko
```

I get this

```
insmod: error inserting '/lib/modules/2.6.15-19-386/drivers/rt2570.ko': -1 Unknown symbol in module
```

Anyone know what this might mean?

---

### Post by Revolution on 2006-03-30
[QUOTE=chameleon]When I do this 

```
sudo insmod /lib/modules/2.6.15-19-386/drivers/rt2570.ko
```

I get this

```
insmod: error inserting '/lib/modules/2.6.15-19-386/drivers/rt2570.ko': -1 Unknown symbol in module
```

Anyone know what this might mean?[/QUOTE]

Everyone seems to be running 2.6.12-10-386 Kernel except you.

---

### Post by htinn on 2006-03-30
If you're using Dapper (I'm using Flight 5) you don't need to compile or install the driver, but you still need to activate the hardware (and maybe edit the interfaces file).

---

### Post by chameleon on 2006-03-30
> If you're using Dapper (I'm using Flight 5) you don't need to compile or install the driver, but you still need to activate the hardware (and maybe edit the interfaces file).

Thanks - I'm running Dapper through VMware on XP, which is connected to a WLAN through a Belkin G USB. This is the part that slightly mystifies me: how do I get Ubuntu to see the adapter? No rausb0 when I do lsmod.

---

### Post by mrios on 2006-04-01
[QUOTE=tomsyco]I am recieving this durring build

tom@ubuntu:~/usr/src/rt2570-1.1.0b1/Module sudo make
make[1]: Entering directory `/lib/modules/2.6.12-10-386/build'
make[1]: *** No rule to make target `modules'. Stop.
make[1]: Leaving directory `/lib/modules/2.6.12-10-386/build'
rt2570.ko failed to build!
make: *** [module] Error 1

I have installed everything that was mentioned but i still cant get it to work.
Please help![/QUOTE]

This is driving me up a wall. I am having this error left and right. Very annoying. I have a ppc machine... does this make any difference? ](*,) 

Any help would be appreciated. I am considering updating to Dapper prematurely just to get this driver working, because my laptop is pretty much useless without wireless. 

Any ideas?

-MR

---

### Post by ladyseven on 2006-04-06
I installed the rt2570, the compile and everything went really well... but it comes up with

```
SIOCSIFADDR: No such device
rausb0: ERROR while getting interface flags: No such device
rausb0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up rausb0.
```

Now, I traversed the interweb for a while, and noticed that my device (WUSB54GC) is categorized as **RT2501 (RT73 ?)** on [ralink.rapla](http://ralink.rapla.net/)... Now, I apologise if this is a stupid question; did I waste my time compiling a module for a device I don't even have? In other words, is the WUSB54GC not covered by 2570?

EDIT: it was ralink.rapla.net, not ralink.sf.net I found the listing of the device.

---

### Post by monomaniacpat on 2006-04-10
I enter 'sudo lsmod -a' and the terminal respond 'usage: lsmod' - is that what's meant to happen?

If so, having gedit'd 'interfaces'....

[QUOTE=Lambert]You need to know the ssid of the router you want to connect to. You can try to scan for the router with this command if you don't know it.

sudo iwlist rausb0 scan

here is a sample

```
 Cell 05 - Address: 00:12:17:A6:AA:3F
                    ESSID:"linksys-g"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=6/94  Signal level=-89 dBm  Noise level=-95 dBm
                    Encryption key:on

```

so if this was the router you wanted to connect to this is what it would look like.

iface rausb0 inet dhcp
wireless-essid linksys-g
wireless-mode managed
wireless-key xxxxx
auto rausb0

What is the key? You have to know it. But if there is no encryption on the router you don't need a key, you can just remove that line.[/QUOTE]

I can't find out the ssid from scanning, since the usb dongle isn't installed yet! Is there a way to find it out from windows?

---

### Post by monomaniacpat on 2006-04-10
I managed to find out my SSID and gedit'd the file accordingly... Having followed the next couple of commands, I produce this response:

```
patrick@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ ok ]
patrick@ubuntu:~$ sudo ifconfig rausb0 up
rausb0: ERROR while getting interface flags: No such device

```

What am I doing wrong?

---

### Post by plush on 2006-04-11
I have Dapper Flight 6 installed, and I've tried doing modprobe rt2570.  When I try iwconfig or ifconfig rausb0 isn't listed.  It does come up in Device manager.  I also can't manually enable it by doing ifconfig rausb0 up.  Am I missing something?

---

### Post by dc2447 on 2006-04-12
Trying this howto on dapper

davidcam@han:~$ sudo apt-get install build-essential linux-headers-`uname -r` gcc-3.4
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
E: Couldn't find package linux-headers-2.6.15-19-386
davidcam@han:~$ uname -a
Linux han.fu-1.net 2.6.15-19-386 #1 PREEMPT Mon Mar 20 16:46:02 UTC 2006 i686 GNU/Linux

---

### Post by Princey on 2006-04-24
I'm having problems setting up my Dlink DWL-G122 HW ver.:B.1 F/W Ver.:2.02 usb card. I followed the howto step by step and got stuck at > sudo lsmod -a as it returned the code > Usage: lsmod I continued reading throughout this post and realised a user with exact settings as mine had similar problem and was asked to follow Post 2 in the thread. This I did but with no results. If I input the code > sudo echo rt2570 >> /etc/modules I get this as my response > bash: /etc/modules: Permission denied. I know the card is seen, here's the output of my network/interfaces file. Note that I have a wired connection but would really like not to use it as I need to re-order the position of my main computer. > # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

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

# The primary network interface

iface eth1 inet static
address 192.168.0.104
netmask 255.255.255.0
gateway 192.168.0.1


auto eth1

iface rausb0 inet dhcp
wireless-essid MCES Network
wireless-key xxxxxxxxxxxxx
wireless-mode Managed
crypto-mode Restricted
channel 6

auto rausb0 
The thing is if I bring up kwifi connection under the internet submenu, it lists my network but lists it on the channel 1 although I have it specified in my /network/interfaces. Any ideas?

_________
Edit:
If I set it to static via the GUI instead of dhcp, it shows that it's connected, however, > iwconfig yields > o        no wireless extensions.

eth1      no wireless extensions.

sit0      no wireless extensions.

rausb0    RT2500USB WLAN  ESSID:"MCES Network"
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=11 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=0/70  Signal level:-120 dBm  Noise level:-200 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 and the kwifi interface still shows me connected only on channel 1 with no access point and the rate should be 54 Mb/s not 11

---

### Post by feersum_endjinn on 2006-04-24
hi! How do i go about scouring my system so that I can delete all my failed attempts, ie i first tried ndiswrapper and then the linux driver 'rt2500usb', then i found this howto. My problem is i've gone through the howto to install the rt2570 driver but when i look at iwconfig the driver it is using is rt2500usb, which doesn't work it seems. I think i've gotten rid of the ndiswrapper stuff using locate and just deleting everything i found, crude but i was fed up and it felt good deleting stuff. anyway, how do i uninstall rt2500usb and rt2570 so i can start over?

appreciate the help, G.

---

### Post by Neobuntu on 2006-04-26
[QUOTE=monomaniacpat]I managed to find out my SSID and gedit'd the file accordingly... Having followed the next couple of commands, I produce this response:

```
patrick@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ ok ]
patrick@ubuntu:~$ sudo ifconfig rausb0 up


```

What am I doing wrong?[/QUOTE]

I am right where you are with...

"rausb0: ERROR while getting interface flags: No such device"

Yes the Belkin USB F5D7050v4 is pluged in and lit up. Isn't it a ZyDAS chipset????? The darn thing will not tell us, from Ubuntu, which chipset it is(Unless I'm missing something else). Gee, I wonder why they do it this way?  :P I tried rebooting too. 

Which USB 802.11"g" just works (driver auto installed with Ubuntu 5.10 and up?) This is getting old, fast.

---

### Post by nolagirl05 on 2006-04-26
Hi - I am very new to Ubuntu...but I'm trying to learn!

This how-to was very helpful.  I am installing these drivers for a Belkin 54mbps 850.11g USB adapter.  I can see the wireless card now, which was not there before, but whenever I try to do anything with it (like configure it) Ubuntu starts running very, very slowly and eventually hangs altogether.  Ubuntu runs normally until I try to configure the card, then it locks up.

I have tried moving the driver to another folder, per the second post in this thread, but it didn't solve the problem.  Does anyone have any other ideas?  Let me know what other info I need to post and I will try...although it might be difficult with no internet connection on the p.c.

Thanks so much!

-Carrie

---

### Post by htinn on 2006-04-27
Until the new rt2x00 drivers get up to speed, I've found that using the "linux-image-server" kernel will help you avoid crashing.

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/37370](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/37370)

EDIT: "-server" kernel did not work out. Still getting random cut-outs that are impossible to recover from (a worse situation than using the k7/386 kernels).

---

### Post by obidose on 2006-04-28
Quote:
Originally Posted by monomaniacpat
I managed to find out my SSID and gedit'd the file accordingly... Having followed the next couple of commands, I produce this response:

Code:

patrick@ubuntu:~$ sudo /etc/init.d/networking restart * Reconfiguring network interfaces... [ ok ] patrick@ubuntu:~$ sudo ifconfig rausb0 up


What am I doing wrong?

I am right where you are with...

"rausb0: ERROR while getting interface flags: No such device"

--------------------------------------------------------
This is exactly the problem I have, it all seems to go fine but the device will not be detected. I first tried this on a 386 and it worked fine but now on my Imac g3 it doesn't.

---

### Post by JNasci7906 on 2006-04-28
ok so far i got step one to work but when i got to step 2 i get this....

make: *** /lib/modules/2.6.12-10-386/build: No such file or directory.  Stop.
rt2570.ko failed to build!
make: *** [module] Error 1


ok im totally new to this but if i browse through the folders the icon above the rt2570 folder has a LOCK....could this be preventing me? Do i need root access?

sorry im a total newb, but we gotta start somewhere

---

### Post by htinn on 2006-04-29
You need to make sure this works completely:

```
sudo apt-get install build-essential linux-headers-`uname -r` gcc-3.4
```

---

### Post by obidose on 2006-04-29
This is hacking me off so much. As of now i figure i have 2 options.

1) Try and see if the new dapper beta does all the right things or...
2)Buy a wireless ethernet bridge and forget about the poor wireless usb support

As to using a wireless ethernet bridge, is this gaurunteed to work without any driver issues? Will it be just as if i was connecting a cat5 straight from my ubuntu machine to the router?

---

### Post by htinn on 2006-04-29
Dapper includes the beta driver for rt2570, but in my experience it's extremely unreliable. D-Link makes THE WORST driver I have ever seen. It may be a year or longer before we see a nice reliable driver written by people who actually know what they're doing.

---

### Post by rwabel on 2006-05-01
same for me with my netopia usb wireless stick. :-(
only solution to get connection again is by unplug and replug the usb stick.
I hope the bug report helps to fix it asap

---

### Post by joostp on 2006-05-03
I also get this message:

make: *** /lib/modules/2.6.12-10-386/build: No such file or directory. Stop.
rt2570.ko failed to build!
make: *** [module] Error 1

The reason for this is that I have problems installing gcc-3.4. I think this isn't available on my cd-rom. Is there another way to install this?

---

### Post by obidose on 2006-05-03
To install gcc 3.4 without a network connection on ubuntu machine:

[http://www.ubuntuforums.org/showthread.php?t=79896](http://www.ubuntuforums.org/showthread.php?t=79896)

---

### Post by rwabel on 2006-05-07
I've now tried the CVS version of RT2570. After compilin I just copied the new .ko file to the existing one from dapper. Now the signal strenghts is displayed correctly. As before I can see my AP and when I try to connect, it just can't. :-( setting it up manually with Gnome network doesn't freeze my system luckily but wifi still isn't working with my netopia usb wifi.

---

### Post by b.treu on 2006-05-08
I am by no means an expert, but after the nearly 5 hour total struggle I put up I felt compelled to try and contribute to this thread. Before finding this forum I tried following numerous others without success. These are my steps mixed with Lambert's steps, and jnorth's steps.

1. Follow Lambert's guide through step 2.
2. After completing step 2 switch to jnorths instructions, but just copy the .ko file. The command should look like this:

        sudo cp /usr/src/rt2570-1.1.0-b1/Module/rt2570.ko /lib/modules/2.6.xx-        xx-xxx/kernel/drivers/net/wireless/rt2570.ko

4.After these have been completed go to the gnome panel System--> Administration--> Network Connections

A new Icon for a Wireless connection should be present. From here you should be able to configure your wireless setting with ease in the GUI rather than command prompt. \\:D/ 
Thanks to everyone everywhere contributing to the cause! Peace to all!

---

### Post by rwabel on 2006-05-08
I'm under dapper and there is already a rt2570.ko file, but under ..../usb/net/rt2570/ I think. I guess you are using breezy as this is also a breezy thread :-)

I've already tried to use no encryption, but still a connection to the AP doesn't work. everything else seems to be perfect. signal strenghts AP can be seen. very strange

---

### Post by justafish on 2006-05-10
I was getting the same error some people mentioned above
```
make[1]: Entering directory `/lib/modules/2.6.12-10-amd64-generic/build'
make[1]: *** No rule to make target `modules'.  Stop.[CODE]
```
make[1]: Leaving directory `/lib/modules/2.6.12-10-amd64-generic/build'
rt2570.ko failed to build!
make: *** [module] Error 1
[/CODE]

The cause is the kernel sources not being configured correctly. Make sure you have a build symlink to /usr/src/linux in the modules directory

```
sudo ln -s /usr/src/linux /lib/modules/2.6.12-10-amd64-generic/build
```

---

### Post by chiefy on 2006-05-11
Hi. I am new to Ubuntu, but I just wanted to say a big "THANK YOU" to everyone in this thread because otherwise, I wouldn't have had the first clue as to how to get my wireless card working under breezy.

So I am happy to report (in case anyone out there is searching) that I got Breezy (5.10) to work with a Zonet ZEW2500P wireless USB card using the methods described here.

Though I can't really recommend this card with linux, it's extremely buggy. My connection goes up and down and it takes forever to transfer files via Samba or FTP via wireless.

---

### Post by isw on 2006-05-27
Hello,

I succesfully installed the rt2570 driver on my laptop with Buffalo AirStation g54 WLI-U2-KG54-AI  USB drive, following Lambert's post on the first page.

Ubuntu kernel 2.6.12-9-386 , including same kernel header version!. Had problems compiling the driver before I matched those versions. 

And another interesting note... 

The "AI" means that the usb wifi drive stores windows drivers on it, it has a small (really small) switch on one side, with this switch 'on' ubuntu found a cd-rom drive and a keyboard :). 
After I switched it 'off' however, the system detects it as a wi-fi drive, yay!

Happy surfing.

// isw

---

### Post by pukie on 2006-12-08
Hi,

I have a problem very strange.

I have an ASUS WL-167g that needs the rt2570.

Anyway when I used it the first time it worked very well, the only one problem was:

-not always get the connection on, starting the pc
-when I try to start manually the connection with "Wireless Assistant", sometimes I have to try more than one time
-always after some hours "idle" the connection goes down and I need to get it up manually with : sudo /etc/init.d/networking restart (I cant use "Wireless Assistant" because the AP is not found).

Reading logs and dmesg I don't see anything wrong, anyway I noticed that each time the connection goes down, the channel (frequency) goes changes by its self from 11 to 1 (when I restart manually the network, the right channel comes back).

For these problems I tried to configure the driver following step by step the Lambert's instructions...the installation was good, I have had no problems or errors, but the adaptor is still giving the same problem.

I don't know if following the instruction suggested by jnorth could help me:

> **jnorth said:**
> Hi - just following up on this... I'm one of the users who's been able to get the rt2570 driver working for a WUSB54Gv4 device.  There are a few extra steps that I had to do to get it working on my system.  You can see  the whole process I followed [here]("http://ubuntuforums.org/showpost.php?p=618022&postcount=3"), but basically, follow Lambert's steps except for these things:
1. On my system - I couldn't get modprobe/insmod to see the driver unless I put the rt2570.ko file in another directory:
```
sudo mv /lib/modules/2.6.xx/extra/rt2570.ko /lib/modules/2.6.xx-xx-xxx/kernel/drivers/net/wireless/rt2570.ko
```
2. Also, the install put the alias line in a new file called modprobe.conf, which isn't standard order on Debian/Ubuntu - may as well move it to the correct area:
```
sudo mv /etc/modprobe.conf /etc/modutils/rt2570
```
3. As per Lambert, load the module up and you should be good to go with the rest of your ifconfig/iwconfig steps, or use the gui to configure.
```
sudo depmod -a
sudo update-modules
sudo modprobe rt2570
```

this is my iwconfig:

rausb1    RT2500USB WLAN  ESSID:"USR9108"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:14:C1:18:EF:CC
          Bit Rate=54 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=63/100  Signal level:-68 dBm  Noise level:-203 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

When the connection goes down I have the same result but the frequency that changes to 2.412 Ghz (channel 1).

I can add that I was using the same adaptor with Mandrake without any problem.

Have you (or someone) any idea about this? 
I have a US Robotics router that supports RTS, could be solve the problem?
I also tried to "force" the channel 11 with "sudo iwconfig rausb1 channel 11" without solving the problem. ](*,) 

Thank you.

> **Lambert said:**
> This howto derived from this [thread]("http://ubuntuforums.org/showthread.php?t=106328"). 
Similar thread can be found [here.]("http://ubuntuforums.org/showpost.php?p=618022&postcount=3") Haven't compared but that thread has two posts w/ verified working driver following those instructions.


Homepage for the rt2570 driver can be found [here.]("http://rt2x00.serialmonkey.com/wiki/index.php/Downloads") 

This [link]("http://http://rt2x00.serialmonkey.com/wiki/index.php/Hardware") shows a list of devices reported by users to work with the rt2xxx drivers. Which the rt2570 section shows the dwl-g122 as working with this driver. I've seen quite a few posts lately about getting this device to work. Post your results and success stories for others to see. 

[B]Preparation
[/B]If not installed already, these packages need to be installed.

```
sudo apt-get install build-essential linux-headers-`uname -r` gcc-3.4
``` 
At the time this was written driver was rt2570-1.1.0-b1. If driver is updated commands will need to change to that file name.


[B]Step 1 Download and untar file
[/B]
Get file
Go [here]("http://rt2x00.serialmonkey.com/wiki/index.php/Downloads") and choose the rt2570beta driver. You'll get a choice of mirrors where to download from. Save it to file.

Now copy the file to /usr/src
```
sudo cp /path/to/file/rt2570-1.1.0-b1.tar.gz /usr/src/
``` 
Move to /usr/src
```
cd /usr/src
``` 

Untar file
```
sudo tar -xzvf rt2570-1.1.0-b1.tar.gz
``` 
Move into file
```
cd rt2570-1.1.0b1/Module
``` 
**Step 2 Make and install file**

```
sudo make
``` 

```
sudo make install
``` 
**Step 3 Set up and load module**

make a directory for the .ko file
```
sudo mkdir /lib/modules/`uname -r`/drivers/
``` 
copy file over to new directory
```
sudo cp /lib/modules/2.6.12/extra/rt2570.ko /lib/modules/`uname -r`/drivers/
``` 
Then insert module into kernel
```
sudo insmod /lib/modules/`uname -r`/drivers/rt2570.ko
``` 
```
sudo lsmod -a
``` 
Configure your wireless device through /etc/network/interfaces. Here is a sample file.

                             iface rausb0 inet dhcp
 wireless-essid apname
 wireless-key xxxxxxxxx
 wireless-mode Managed
 auto rausb0

restart the networking service

```
sudo /etc/init.d/networking restart
``` 


Now try to bring up your device

```
sudo ifconfig rausb0 up
``` 
To load module at boot add it to /etc/modules file

```
sudo echo rt2570 >> /etc/modules
``` 
[B]Report bugs
[/B]This driver is a beta driver and there are probably bugs. In /usr/src/rt2570-1.1.0-b1/Modules/ there is a file TESTING. Read this file as it gives information on logging and reporting bugs.

---

### Post by -::Bas::- on 2006-12-09
Sry

---

### Post by bodhi.zazen on 2006-12-15
Nice How-to

This thread has been added to the UDSF wiki.

[Ralink_RT2570_usb_wireless_driver](http://doc.gwos.org/index.php/Ralink_RT2570_usb_wireless_driver)

---

### Post by FRuMMaGe on 2007-06-04
Mine says "No Such Device".

Why won't it pick up rausb0!

---

### Post by tubu on 2007-06-11
First of all, many thanks to all the boys and girls who contribute to this great forum... it helped me a lot!

Combining the instructions from Lambert and jnorth got me in sight of the finish line (although lots have te be done after finishing on my system). In sight but nut quite there yet.

after restarting the networking service there's a lot of text, but this is concerning me..
> 
IOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
Error for wireless request "Set Mode" (8B06) :
    SET failed on device rausb0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device rausb0 ; No such device.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
rausb0: ERROR while getting interface flags: No such device
rausb0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up rausb0.

but maybe that's solved when the code for bringing up the device is enterded. But to no avail...
> 
sudo ifconfig rausb0 up
results in:
> rausb0: ERROR while getting interface flags: No such device


It seems i'm not the only one with this problem...
If someone can help me that would be great, I'm getting tired of looking around on forums and google to solve the mistakes i've made. 
 
Hopefully, the next post will be made through wireless internet!
Thanks in advance

---

### Post by Princey on 2007-06-11
What are you using? Dapper, Edgy, Fiesty? You don't need this tutorial if you're using Fiesty. It has out of the box support. You didn't state which version of Ubuntu you're using.

---

### Post by tubu on 2007-06-12
Stupid mistake on my part, sorry. I know i have to post information about the error, i just forgot to post info about my system.

Dapper (kubuntu, but that doesn't matter, right). I've read that Fiesty provides out of the box support but i couldn't find a ppc version.

---

### Post by Talkie_Toaster on 2007-10-20
Hey. I get an error when I try to "make" the file. Keeps saying the .ko file was not created or something. I couldn't copy over the exact error as I had to go back into windows to connect to the Internet and post this. Any ideas?

---

### Post by l_tenhunen on 2007-11-07
> ```
sudo make
```

This is where I am stuck. I am running Kubuntu Gutsy Gibbon and trying to get a Buffalo USB Wlan adapter to work ([http://www.buffalo-technology.com/products/wireless/wireless-g/wireless-g-keychain-usb-20-adapter/]("http://www.buffalo-technology.com/products/wireless/wireless-g/wireless-g-keychain-usb-20-adapter/"),  WLI-U2-KG54L).
After I ran sudo make I get the following:
> 
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /usr/src/rt2570-1.1.0-b2/Module/rtusb_main.o
/usr/src/rt2570-1.1.0-b2/Module/rtusb_main.c: In function âusb_rtusb_probeâ:
/usr/src/rt2570-1.1.0-b2/Module/rtusb_main.c:1905: error: âdev_baseâ undeclared (first use in this function)
/usr/src/rt2570-1.1.0-b2/Module/rtusb_main.c:1905: error: (Each undeclared identifier is reported only once
/usr/src/rt2570-1.1.0-b2/Module/rtusb_main.c:1905: error: for each function it appears in.)
/usr/src/rt2570-1.1.0-b2/Module/rtusb_main.c:1905: error: âstruct net_deviceâ has no member named ânextâ
make[2]: *** [/usr/src/rt2570-1.1.0-b2/Module/rtusb_main.o] Error 1
make[1]: *** [_module_/usr/src/rt2570-1.1.0-b2/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
rt2570.ko failed to build!
make: *** [module] Error 1

Anyone have something similar? I'd appreciate help 	](*,)

---

### Post by ubtpenguin on 2008-01-13
> **l_tenhunen said:**
> This is where I am stuck. I am running Kubuntu Gutsy Gibbon and trying to get a Buffalo USB Wlan adapter to work ([http://www.buffalo-technology.com/products/wireless/wireless-g/wireless-g-keychain-usb-20-adapter/]("http://www.buffalo-technology.com/products/wireless/wireless-g/wireless-g-keychain-usb-20-adapter/"),  WLI-U2-KG54L).
After I ran sudo make I get the following:


Anyone have something similar? I'd appreciate help 	](*,)

I have exactly same proble. I am compiling on Ubuntu 7.10 gusty

penguin@emperor:/usr/src/rt2570-1.1.0-b2/Module$ sudo make
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /usr/src/rt2570-1.1.0-b2/Module/rtusb_main.o
/usr/src/rt2570-1.1.0-b2/Module/rtusb_main.c: In function ‘usb_rtusb_probe’:
/usr/src/rt2570-1.1.0-b2/Module/rtusb_main.c:1905: error: ‘dev_base’ undeclared (first use in this function)
/usr/src/rt2570-1.1.0-b2/Module/rtusb_main.c:1905: error: (Each undeclared identifier is reported only once
/usr/src/rt2570-1.1.0-b2/Module/rtusb_main.c:1905: error: for each function it appears in.)
/usr/src/rt2570-1.1.0-b2/Module/rtusb_main.c:1905: error: ‘struct net_device’ has no member named ‘next’
make[2]: *** [/usr/src/rt2570-1.1.0-b2/Module/rtusb_main.o] Error 1
make[1]: *** [_module_/usr/src/rt2570-1.1.0-b2/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
rt2570.ko failed to build!

---

### Post by ubtpenguin on 2008-01-13
> **ubtpenguin said:**
> I have exactly same proble. I am compiling on Ubuntu 7.10 gusty

penguin@emperor:/usr/src/rt2570-1.1.0-b2/Module$ sudo make
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /usr/src/rt2570-1.1.0-b2/Module/rtusb_main.o
/usr/src/rt2570-1.1.0-b2/Module/rtusb_main.c: In function ‘usb_rtusb_probe’:
/usr/src/rt2570-1.1.0-b2/Module/rtusb_main.c:1905: error: ‘dev_base’ undeclared (first use in this function)
/usr/src/rt2570-1.1.0-b2/Module/rtusb_main.c:1905: error: (Each undeclared identifier is reported only once
/usr/src/rt2570-1.1.0-b2/Module/rtusb_main.c:1905: error: for each function it appears in.)
/usr/src/rt2570-1.1.0-b2/Module/rtusb_main.c:1905: error: ‘struct net_device’ has no member named ‘next’
make[2]: *** [/usr/src/rt2570-1.1.0-b2/Module/rtusb_main.o] Error 1
make[1]: *** [_module_/usr/src/rt2570-1.1.0-b2/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
rt2570.ko failed to build!

Okay I solved this problem by downloading patched driver version 1.6.1. I don't know why serial monkey has 1.1.0 version. 

I successfully compiled driver and did make install
but it gave me an error that I don't have modprobe.conf
well I ignored it 
and I blacklist 4 modules
rt2x00usb
rt2x00lib
rt73usb
rt73

and did 
sudo depmod -a
sudo modules-update
sudo modprobe rt2570
sudo lsmod rt2570 showed successful install.

But when I did 

ifconfig -a 
it doesn't show rausb0 device.

I am using ubuntu 7.10 amd on HP S3200T (this machine has ralink 2571 usb wireless card)

any ideas? 

:lolflag:

---

### Post by bobulator on 2008-03-08
I've seen on the posts here that many people come up with the error:

rt2570.ko failed to build!

The way I got around this problem was to install the cvs daily driver instead of the beta and, to my suprise, it compiled and installed successfully!

However, I am having problems such as when I typed in 'sudo ifconfig rausb0 up' in the console, it replies 'rausb0: ERROR while getting interface flags: No such device'

Any ideas?

PS  The solution I found worked for me, it's no guarantee that it'll work for you o' course :)

---

### Post by th3p4yn3 on 2008-04-01
I just cant figure out how to make my USB wireless work.

I am running 7.10 Gutsy, using a Chiefmax NKRUSB-400 for a wireless USB, which uses RaLink. 

I am not sure if the driver issue or not...the only one I could get to make without errors was from...

[http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz)

Installs fine

Here are my config files...

/etc/network/interfaces

```

auto lo
iface lo inet loopback

iface rausb0 inet dhcp
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid th3
wpa-psk dharma33
auto rausb0

```

/etc/wpa_supplicant.conf

```

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=2
fast_reauth=1

network={
ssid="th3"
proto=WPA
key_mgmt=WPA-PSK
pairwise=TKIP
group=TKIP
psk="dharma33"
}

```

Here is where I run into a problem, when I restart the network service. I can configure the GUI under System > Administration > Network, and it looks fine.

```

th3p4yn3@th3p4yn3-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.rausb0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/rausb0/00:00:00:00:00:00
Sending on   LPF/rausb0/00:00:00:00:00:00
Sending on   Socket/fallback
ioctl[SIOCSIWPMKSA]: Network is down
ioctl[SIOCSIWMODE]: Network is down
Could not configure driver to use managed mode
ioctl[SIOCGIWRANGE]: Network is down
ioctl[SIOCSIWAUTH]: Network is down
WEXT auth param 7 value 0x1 - ioctl[SIOCSIWENCODEEXT]: Network is down
ioctl[SIOCSIWENCODEEXT]: Network is down
ioctl[SIOCSIWENCODEEXT]: Network is down
ioctl[SIOCSIWENCODEEXT]: Network is down
ioctl[SIOCSIWAUTH]: Network is down
WEXT auth param 4 value 0x0 - ioctl[SIOCSIWAUTH]: Network is down
WEXT auth param 5 value 0x1 - There is already a pid file /var/run/dhclient.rausb0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/rausb0/00:00:00:00:00:00
Sending on   LPF/rausb0/00:00:00:00:00:00
Sending on   Socket/fallback
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]

```

What is all this "Network is down"?? I can assure that the AP is working properly as I have an XP box right next to me and I can plug this same USB wireless on that machine, works just fine.

I get no blinking lights on the device.

No iwpriv commands will work on the device, it says "Network is down" as well as this command

```

wpa_supplicant -w -Dwext -iath0 -c/etc/wpa_supplicant.conf

```

I also have to reboot my system after plugging in the USB device, as it creates some overall stability problems.

Can anyone please give me some advice!!

Thanks

---

### Post by bobulator on 2008-04-25
[SOLVED]

The error was due to the USB ports on the side of my computer (which I usually use) working with other devices, but strangely, the wifi coonector did not register.(must get that sorted out sometime)

---

### Post by FSHero on 2008-06-03
Hello all, I recently got a Ralink-chipset wireless NIC card working; please read [http://ubuntuforums.org/showthread.php?p=5105680](http://ubuntuforums.org/showthread.php?p=5105680).

@th3p4yn3: I haven't ever tried WPA on my network, only ever WEP :(  However, I have got the errors:
```

No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
previously. I think this was when I manually loaded my rt2570 module using insmod. Does your driver load automatically at system startup, or are you "insmod"-ing it? Perhaps you should do "depmod -a" then add "rt2570" to your /etc/modules, then restart your machine and try again. Note that this is entirely empirical -- I'm only suggesting what I have read from other posts/threads!

---

