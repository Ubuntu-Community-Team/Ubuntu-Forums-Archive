---
title: "Orinoco Drivers With Monitor Mode In 6.10 (Edgy Eft)"
date: 2006-10-28
forum: Outdated Tutorials &amp; Tips
---

### Post by webcrawler42 on 2006-10-28
getting the orinoco drivers to work in edgy eft is rather quite easy, despite what other guides say the only thing you have to download is the prepatched plasmahh drivers ([http://www.projectiwear.org/~plasmahh/orinoco-0.13e-SN-14.tar.bz2](http://www.projectiwear.org/~plasmahh/orinoco-0.13e-SN-14.tar.bz2))

1. download & extract "orinoco-0.13e-SN-14.tar.bz2" to your desktop
2. open the terminal and type "cd /Desktop/orinoco-0.13e-SN-14/", which puts you in the prepatched driver directory
3. still in terminal type "sudo make" which will compile the drivers, i had a bunch of errors pop up, but as long as it finishes compiling it shouldn't matter
4. still in terminal type "sudo cp *.ko /lib/modules/2.6.17-10-generic/kernel/drivers/net/wireless", this will copy the newly compiled drivers to where they will be loaded by ubuntu (i have been told by ninocass you can "sudo cp *.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless" and it will "enter the users kernel version incase someone is running this under a different kernel", i have not tested if this works yet)
5. REBOOT, needed to load the new patched drivers
6. open a new terminal and type "iwpriv eth1" (may not be eth1, use ifconfig to check) to make sure you did everything correctly it should show monitor mode as 2

---

### Post by Mach1US on 2006-10-29
I`v tried to copy drivers and i get " cp: cannot stat `*.ko': No such file or directory " .
I`v tried in /home dir and in /Desktop/orinoco-0.13e-SN-14$ with same result
Am i supposed to be in different directory ?:-k

---

### Post by webcrawler42 on 2006-10-31
are there .ko drivers in the directory, what is the "ls" read out if you cd into the driver directory, and are you in the extracted driver dir when you try to copy them?

---

### Post by jakobw on 2006-11-03
How do you load the compiled drivers, after copying into the proper dirextory? Is that everything you did with a fresh installed ubuntu 6.10? I'm kind of hesitating, because I had lots of trouble with orinoco-driver-stuff before. ;-)
Thanks in advance, Jake

---

### Post by webcrawler42 on 2006-11-03
> How do you load the compiled drivers
They are actually loaded on the reboot, after they are copied to the correct directory.

> Is that everything you did with a fresh installed ubuntu 6.10?
Yes, that is why i said "despite what other guides say the only thing you have to download is the prepatched plasmahh drivers (http://www.projectiwear.org/~plasmah...-SN-14.tar.bz2)"

> I'm kind of hesitating, because I had lots of trouble with orinoco-driver-stuff before.
I have had lots of trouble also, that is why i wrote this guide.

---

### Post by Mach1US on 2006-11-05
Thanks for all the help .
 In fact i was in extracted dir and still i have gotten same message .
For some reason i can not figure it out on my own.
After aditional attempts i`m  still getting same message.
that`s my output:
m@D6000:~/Desktop/orinoco-0.13e-SN-14$ sudo cp *.ko /lib/modules/2.6.17-10-generic/kernel/drivers/net/wireless
cp: cannot stat `*.ko': No such file or directory
m@D6000:~/Desktop/orinoco-0.13e-SN-14$ ls
airport.c    hermes.h      ieee802_11.h     orinoco.c     orinoco.o      orinoco_tmd.c
hermes.c     hermes.o      Makefile         orinoco_cs.c  orinoco_pci.c  README.orinoco
hermes.conf  hermes_rid.h  Modules.symvers  orinoco.h     orinoco_plx.c  userhermes.c
m@D6000:~/Desktop/orinoco-0.13e-SN-14$

any clues ???:-k [-o<

---

### Post by jakobw on 2006-11-05
sweet!it really does work I think. thats the corresponding line I get from "iwpriv eth1" : [COLOR="Red"]monitor   ( 8 B E 8 )    :    set     2   int     & get     0  [/COLOR] 
So I would say the 2 means monitor mode is enabled. Anyway, I still can not read any accesspoints when I run "iwlist eth1 scanning", even not the one I am connected to. In fact, I get the massage "eht1 Interface doesn't support scanning." So I'll have to play around with this.

@webcrawler42 did you try "iwlist eth1 scanning"? And what is your hardware, a pcmcia card? what chipset & firmware?

@Mach1US looks like you got no *.ko files.... no wonder you can't copy them. try unpacking again. good luck!

---

### Post by webcrawler42 on 2006-11-05
> Thanks for all the help .
In fact i was in extracted dir and still i have gotten same message .
For some reason i can not figure it out on my own.
After aditional attempts i`m still getting same message.
that`s my output:
m@D6000:~/Desktop/orinoco-0.13e-SN-14$ sudo cp *.ko /lib/modules/2.6.17-10-generic/kernel/drivers/net/wireless
cp: cannot stat `*.ko': No such file or directory
m@D6000:~/Desktop/orinoco-0.13e-SN-14$ ls
airport.c hermes.h ieee802_11.h orinoco.c orinoco.o orinoco_tmd.c
hermes.c hermes.o Makefile orinoco_cs.c orinoco_pci.c README.orinoco
hermes.conf hermes_rid.h Modules.symvers orinoco.h orinoco_plx.c userhermes.c
m@D6000:~/Desktop/orinoco-0.13e-SN-14$

any clues ??? 

yes, you have not compiled the drivers (i think you forgot to "sudo make"), hence there are no .ko files, try fallowing my guide step by step and make sure you are using edgy eft.

---

### Post by webcrawler42 on 2006-11-05
> @webcrawler42 did you try "iwlist eth1 scanning"? 

not familiar with "iwlist eth1 scanning" i just use kismet, i suggest you try it too.

> And what is your hardware, a pcmcia card? what chipset & firmware?

is your wifi card eth1? my hardware is a orinoco gold classic 802.11b, 8410-WD, pcmia, Hermes I chipset and 8.72 firmware.

---

### Post by jakobw on 2006-11-06
yes my card is a pcmcia card with the same chipset as yours. Well, after a while I figured that you have to run iwlist as root (sudo) to get any scanning results. So it's working :-D after all. I guess I'll give kismet a try....

Great tutorial though!

---

### Post by jakobw on 2006-11-06
hi webcrawler42, would you mind explaining in a few words how to set up kismet?I would appreciate this!
thanks

---

### Post by webcrawler42 on 2006-11-06
Webcrawler42's Kismet Guide (For Orinocos)
----------------------------------------------------------------
1.Sudo gedit the config file (standardly in "/usr/local/etc/kismet.conf")
2.Set the user Kismet will drop privileges to by changing the "suiduser" configuration option.
3.Set the capture source by changing the "source" configuration option to "orinoco,eth1,orinocosource"
4.run kismet with "sudo kismet"

---

### Post by jakobw on 2006-11-07
I'm happy, it's working!! :-D Thanks webcrawler42

---

### Post by jakobw on 2006-11-07
alright, I gonna bother you again webcrawler. :-D hope you don't mind but since you are so familiar with the topic....
When I quit kismet I cannot use the the card anymore, it seems like something is messed. So what I can do is reboot or just switch the card to the other pcmcia slot what is both not a nice solution. You have the same problem and maybe a way out? I would guess its a driver problem...
Thanks for any help

---

### Post by webcrawler42 on 2006-11-07
i don't have that problem, but are you exiting with Q or just closing the terminal?

---

### Post by jakobw on 2006-11-08
either way it sucks. *Q* is the proper way though I guess. Can you actually eject the card and insert it again so that its still working? cause when I do that I get the same problem like with kismet, the slot I had the card in before isn't working. Same thing with putting my laptop in standby. Only shutting down the interface with *sudo ifdown eth1* and turning it on again with *sudo ifup eth1* is working but not when I plug out the card in between those two commands. So it might be a problem with something else than the driver... whatever it is I can't figure it out.
thanks anyway

---

### Post by webcrawler42 on 2006-11-08
> either way it sucks. Q is the proper way though I guess. Can you actually eject the card and insert it again so that its still working? cause when I do that I get the same problem like with kismet, the slot I had the card in before isn't working. Same thing with putting my laptop in standby. Only shutting down the interface with sudo ifdown eth1 and turning it on again with sudo ifup eth1 is working but not when I plug out the card in between those two commands. So it might be a problem with something else than the driver... whatever it is I can't figure it out.
thanks anyway

i don't have that problem so i can't help you, sorry

---

### Post by h2gofast on 2006-11-10
make -C /lib/modules/2.6.17-10-386/build SUBDIRS=/home/h2/Desktop/orinoco-0.13e-SN-14 modules
make: *** /lib/modules/2.6.17-10-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2


I got this error, headers are installed, any suggestions?

---

### Post by webcrawler42 on 2006-11-11
> make -C /lib/modules/2.6.17-10-386/build SUBDIRS=/home/h2/Desktop/orinoco-0.13e-SN-14 modules
make: *** /lib/modules/2.6.17-10-386/build: No such file or directory. Stop.
make: *** [modules] Error 2

I got this error, headers are installed, any suggestions?

what are you doing? are you following my guide? is this what happens when you type make? try just cding into the driver dir and making from there.

you don't need the headers, they come with the stock install.

---

### Post by h2gofast on 2006-11-11
thanks for the reply, yep I'm in the directory
root@z1900:/home/h2/Desktop/orinoco-0.13e-SN-14# pwd
/home/h2/Desktop/orinoco-0.13e-SN-14
root@z1900:/home/h2/Desktop/orinoco-0.13e-SN-14# make
make -C /lib/modules/2.6.17-10-386/build SUBDIRS=/home/h2/Desktop/orinoco-0.13e-SN-14 modules
make: *** /lib/modules/2.6.17-10-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2

Not sure what to do next. I'm pretty comfortable with linux, but I'm no guru.

---

### Post by webcrawler42 on 2006-11-11
are you using edgy eft?, if so try removing the headers (the stock install comes with what you need) they are not needed and they have only given me problems.

---

### Post by h2gofast on 2006-11-11
yep, edgy all the way I'll try removing headers, I can always put them back.

---

### Post by DtJee on 2006-11-15
Hmmm kismet is working..but NetworkManager stopped detecting my card.. why??

---

### Post by webcrawler42 on 2006-11-15
> Hmmm kismet is working..but NetworkManager stopped detecting my card.. why?? someone else seems to have this same problem, but i don't...are you quiting with Q?

what fixes it?, rebooting, ifconfig eth1 up/down, ejecting the card...?

---

### Post by DtJee on 2006-11-16
Will try it later

---

### Post by FrodoB on 2006-11-16
I believe that this is right. If kismet is using your device, you lose network connectivity on that device. Wardrivers have at least two wireless devices in their rigs for that reason.

---

### Post by rewz2006 on 2006-11-27
i cant change directory this is wots happening

brad@brad-laptop:~$ cd /Desktop/orinoco-0.13e-SN-14/
bash: cd: /Desktop/orinoco-0.13e-SN-14/: No such file or directory

i don't understand why because ive extracted the file to my desktop

---

### Post by rewz2006 on 2006-11-27
if sorted my previous problems i was missing a ~ after cd now my problem is 

ifconfig ath0
ath0      Link encap:Ethernet  HWaddr 00:20:A6:4C:FA:C3  
          inet6 addr: fe80::220:a6ff:fe4c:fac3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
ath0 which is my proxim card is not setting to monitor mode

---

### Post by webcrawler42 on 2006-12-03
what do your sources look like under kismet should be something like "orinoco,ath0,orinoco", also what does "iwpriv ath0" spit out?

---

### Post by Mach1US on 2006-12-09
HeY Webcrawler42 ,great job on your how to.
I got kismet going and i have been playing with airsnort as well as tried some online guides with no results.
You seem to know your way around WEP cracking ,could you give more detail on the processes ,tools and configurations we could use in ubuntu to do actual key recovery.
;)

---

### Post by webcrawler42 on 2006-12-09
"recovery", i love it...

not really wanting to reinvent the wheel because there are many good guides out here i'm going to point you here [http://passivemode.net/updates/2006/8/1/ubuntu-wep-cracking.html](http://passivemode.net/updates/2006/8/1/ubuntu-wep-cracking.html), which should get you on the right track. (note:you will have to tweak some stuff probably ath0=eth0, but it has the right idea behind it)

---

### Post by tturrisi on 2006-12-09
Just want to say thanks!
I have several cards for my laptop, 2 atheros cards and a 2wire w/ agere chipset.  The 2wire is the same chipset as the older orinocos but its version is 8.72.  I have been trying for a year to get monitor mode to work with that card.  This guide had it in monitor mode in 5 minutes!  And it works fine w/ kismet, except sometimes kismet does not cleanly take it out of monitor mode, but that's a known issues w/ kismet.  Thanjs again!

As for the post above with the ath0 device, this guide does not apply to it because ath0 is an atheros chipset.  There are Proxim orinoco cards that have an atheros chipset. I know, I have one!  The atheros chipsets use the madwifi driver which natively supports monitor mode.  The kismet config should be like this:
source=madwifi_ag,wifi0,madwifi
while my 2wire orinoco is this:
source=orinoco,eth2,hermes1

---

### Post by webcrawler42 on 2006-12-10
glad i could help tturrisi, mine doesn't come out of monitor mode nicely at all, but then again...known issue.

---

### Post by ninocass on 2006-12-14
nice how to :)

cant i suggest using:

```

sudo cp *.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless

```
the `uname -r` will enter the users kernel version incase someone is running this under a different kernel than yourself :)

cheers 

nino

---

### Post by webcrawler42 on 2006-12-14
just updated the guide..., thx for the tip

---

### Post by Mach1US on 2006-12-14
Thanks webcrawler42  for the link , lots of good info there.
I have another problem with my orinoco card when i use
 " sudo aireplay -1 0 -e [COLOR="Gray"]ESSID[/COLOR] -a [COLOR="Gray"]BSSID[/COLOR] -h 0:1:2:3:4:5 eth2 "
i get :
" ioctl(SIOCGIFINDEX) failed: No such device "
and this is my Iwconfig :
 "  (...) eth2      IEEE 802.11-DS  ESSID:"non-specified SSID !!"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   Sensitivity:1/3  
          Retry limit:4   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=0/92  Signal level=134/153  Noise level=134/153
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
and my dmesg:
[17184334.952000] pcmcia: registering new device pcmcia0.0
[17184335.196000] orinoco.c 0.13e (David Gibson <hermes@gibson.dropbear.id.au> and others)
[17184335.196000] Compiled with Wireless extensions v.20
[17184335.200000] orinoco_cs.c 0.13e (David Gibson <hermes@gibson.dropbear.id.au> and others)
[17184335.280000] eth2: Station identity 001f:0001:0008:0048
[17184335.280000] eth2: Looks like a Lucent/Agere firmware version 8.72
[17184335.280000] eth2: Ad-hoc demo mode supported
[17184335.280000] eth2: IEEE standard IBSS ad-hoc mode supported
[17184335.280000] eth2: WEP supported, 104-bit key
[17184335.280000] eth2: MAC address 00:02:2D:AB:84:C7
[17184335.280000] eth2: Station name "HERMES I"
[17184335.284000] eth2: ready
[17184335.284000] eth2: index 0x01: , irq 3, io 0x0100-0x013f
[17184335.664000] eth2 (WE) : Driver using old /proc/net/wireless support, please fix driver !
[17184520.732000] device eth2 entered promiscuous mode
[17184520.732000] audit(1166127248.725:3): dev=eth2 prom=256 old_prom=0 auid=4294967295
 
What can this mean  : " Driver using old /proc/net/wireless support, please fix driver ! "
This card works great with kismet and does work with airodump , i can not figure out what gives:-k

---

### Post by webcrawler42 on 2006-12-14
[http://www.wirelessdefence.org/Contents/Aircrack_aireplay.htm](http://www.wirelessdefence.org/Contents/Aircrack_aireplay.htm)

"aireplay:
...
*Orinoco drivers not supported"

---

### Post by hannestum on 2006-12-17
I also wanted to say thanks for the tutorial. Now "monitor" is sown when I type iwpriv.
Kismet works well withe the driver. My only Problem is that airsnort doesn't work and i don't know why. When I start airsnort and press the start button nothing happens although kismet recognizes networks.

Maybe someone can help

---

### Post by webcrawler42 on 2006-12-17
you probably don't have it configured right, i got it to work once with my orinoco, i think, maybe it was another card anyways...most people use aircrack instead, google a guide.

---

### Post by hannestum on 2006-12-18
Mhmh, I'm wondering because although monitor is shown under iwpriv and also kismet works.
But when I want to start airodump-ng it says: 
   ioctl(SIOCSIWMODE) failed: Invalid argument
   Error setting monitor mode on eth1

The strange thing is that I can set the card in Mnitor mode manually via the iwpriv command, but i can't do it with iwconfig eth1 mode monitor because it says:
     Error for wireless request "Set Mode" (8B06) :
     SET failed on device eth1 ; Invalid argument.

---

### Post by h2gofast on 2006-12-19
aptitude install build-essential linux-headers-`uname -r` gcc-3.4 subversion sharutils 

solved my issue for not finding a build directory

cheers

---

### Post by just_old_bob on 2006-12-20
Hi, can anyone give me newb instructions on how to install the USB version of this card. The one I have is the Orinoco USB Client Silver. It has the hermes chip.

Thanks
bob

---

### Post by webcrawler42 on 2006-12-20
bob-
you should be able to just follow my guide, it should work for all hermes chipsets

h2gofast-
glad to hear you got it working

hannestum-
ill help you out in a week or so, once i get my new notebook

---

### Post by eightysix on 2006-12-22
Anyone get these drivers to work with the Lucent Orinoco Gold PC24E-H-FC?

---

### Post by webcrawler42 on 2006-12-23
what do ifconfig and iwconfig spit out?

---

### Post by eightysix on 2006-12-23
> **webcrawler42 said:**
> what do ifconfig and iwconfig spit out?

Well, eth1 comes if just fine when I do iwconfig:

```
eth1      IEEE 802.11-DS  ESSID:""  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.422 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off

```

But when I try to do "iwlist eth1 scan" I get this:

```
eth1      Failed to read scan data : No data available
```

Also, when I do "iwpriv eth1", everything seems fine:

```
eth1      Available private ioctls :
          force_reset      (8BE0) : set   0       & get   0      
          card_reset       (8BE1) : set   0       & get   0      
          set_port3        (8BE2) : set   1 int   & get   0      
          get_port3        (8BE3) : set   0       & get   1 int  
          set_preamble     (8BE4) : set   1 int   & get   0      
          get_preamble     (8BE5) : set   0       & get   1 int  
          set_ibssport     (8BE6) : set   1 int   & get   0      
          get_ibssport     (8BE7) : set   0       & get   1 int  
          monitor          (8BE8) : set   2 int   & get   0      
          dump_recs        (8BFF) : set   0       & get   0 
```

I can run Wifi-Radar/Kismet and the light on my card is on when it's running.

Edit: Here's what I got after doing a "dmesg | grep eth1":

```
[  201.102129] eth1 (WE) : Driver using old /proc/net/wireless support, please fix driver !
[  269.024443] eth1: no IPv6 routers present
```

---

### Post by webcrawler42 on 2006-12-24
...so eightysix what is your problem, kismet works doesn't it?, after you quit kismet it is normal for your card not to work again untill you reboot.

---

### Post by eightysix on 2006-12-24
> **webcrawler42 said:**
> ...so eightysix what is your problem, kismet works doesn't it?, after you quit kismet it is normal for your card not to work again untill you reboot.

My problem is that my card won't access any APs let alone scan using "iwlist eth1 scan" at all.

---

### Post by webcrawler42 on 2006-12-24
what about using the connection manager?, make sure you enable the connection.

---

### Post by eightysix on 2006-12-24
> **webcrawler42 said:**
> what about using the connection manager?, make sure you enable the connection.

Never mind, I got it working just fine. Just had to jam the card into the PCMCIA slot a little more. :D

---

### Post by webcrawler42 on 2006-12-24
lol, glad you got it working, i have to do the same thing.

---

### Post by just_old_bob on 2006-12-28
Unfortunately since I have the USB version I need the orinoco_usb.ko to get it working. All of the tars I have downloaded were intended for older an release. I did get one to produce hermes.ko, but that's it. I tried this set from 

[https://svn.sourceforge.net/svnroot/orinoco/branches/usb/](https://svn.sourceforge.net/svnroot/orinoco/branches/usb/)

which produced no errors but no drivers either.

---

### Post by webcrawler42 on 2006-12-28
did you download all the files on that page?, if not do that and then try, there are certain required files like "Makefile".

---

### Post by rtcary on 2006-12-30
Everything worked as stated in the instructions until the end.  When I type in

iwpriv eth1


I get:  no private ioctls

The Proxim ".ko" files are in the directory.  What have I missed?

Todd

---

### Post by just_old_bob on 2006-12-31
Yep, I downloaded them all to the same folder. This is what happened:


me@me-desktop:~$ cd Desktop/poop
me@me-desktop:~/Desktop/poop$ sudo make
Password:
make -C /usr/src/linux-headers-2.6.17-10-generic M=/home/me/Desktop/poop KERNELRELEASE=2.6.17-10-generic modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
me@me-desktop:~/Desktop/poop$ sudo make install
make -C /usr/src/linux-headers-2.6.17-10-generic M=/home/me/Desktop/poop KERNELRELEASE=2.6.17-10-generic modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make -C /usr/src/linux-headers-2.6.17-10-generic M=/home/me/Desktop/poop KERNELRELEASE=2.6.17-10-generic modules_install \
                INSTALL_MOD_DIR=kernel/drivers/net/wireless
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  DEPMOD  2.6.17-10-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
/sbin/depmod -ae
me@me-desktop:~/Desktop/poop$

As you can see I ran make and then make install. I checked after both to see if "orinoco_usb" was anywhere on the hard drive, no luck.

On a side note: Using the drivers you suggested it made all of the drivers it contained, but the only other one that produced any modules only produced the "hermes.ko". Why would that be?

---

### Post by webcrawler42 on 2006-12-31
> On a side note: Using the drivers you suggested it made all of the drivers it contained, but the only other one that produced any modules only produced the "hermes.ko". Why would that be?

beacuse it just makes 1 module for all hermes chipsets, have you tried using hermes.ko or just following my guide all the way through, because it should work for everything with the hermes chipset.

---

### Post by rtcary on 2006-12-31
The Orinoco 802.11a/b (8460-05), I believe, uses the Atheros chip set.  I am a newbie at Linux, so all of this is a big mystery to me.

---

### Post by elcasey on 2006-12-31
> **h2gofast said:**
> make -C /lib/modules/2.6.17-10-386/build SUBDIRS=/home/h2/Desktop/orinoco-0.13e-SN-14 modules
make: *** /lib/modules/2.6.17-10-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2

I'm having the same problem here. I even went into /lib/modules/2* and made a "build" directory. Same error, whether or not I use "sudo" in front of make. There is a Makefile in the directory, but no configure script (of course).

I don't know how to "uninstall headers" (only been using the OS 2.5 months), but i'd like to get this card working. I just got it and a 7dBi antenna and I'm wanting to roll! 8)

---

### Post by just_old_bob on 2006-12-31
I printed out the instructions so I could follow step by step. 

Here's the install:
```
me@me-desktop:~$ cd /Desktop/orinoco-0.13e-SN-14/
bash: cd: /Desktop/orinoco-0.13e-SN-14/: No such file or directory
me@me-desktop:~$ cd Desktop/orinoco-0.13e-SN-14/
me@me-desktop:~/Desktop/orinoco-0.13e-SN-14$ sudo make
Password:
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/me/Desktop/orinoco-0.13e-SN-14 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
me@me-desktop:~/Desktop/orinoco-0.13e-SN-14$ sudo cp *.ko /lib/modules/2.6.17-10-generic/kernel/drivers/net/wireless
me@me-desktop:~/Desktop/orinoco-0.13e-SN-14$ 

```

And after restart:
```
me@me-desktop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

me@me-desktop:~$ iwconfig
lo        no wireless extensions.

sit0      no wireless extensions.

me@me-desktop:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 047e:0300 Agere Systems, Inc. (Lucent) 
Bus 002 Device 001: ID 0000:0000  
me@me-desktop:~$ dmesg
[17179569.184000] Linux version 2.6.17-10-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 22:28:26 UTC 2006 (Ubuntu 2.6.17-10.34-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001fee0000 (usable)
[17179569.184000]  BIOS-e820: 000000001fee0000 - 000000001fee3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001fee3000 - 000000001fef0000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001fef0000 - 000000001ff00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 510MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f3830
[17179569.184000] On node 0 totalpages: 130784
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126688 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 VIAK8T                                ) @ 0x000f76b0
[17179569.184000] ACPI: RSDT (v001 VIAK8T AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fee3040
[17179569.184000] ACPI: FADT (v001 VIAK8T AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fee30c0
[17179569.184000] ACPI: MADT (v001 VIAK8T AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fee7e00
[17179569.184000] ACPI: DSDT (v001 VIAK8T AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x4008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:7 APIC version 16
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 1ff00000:ded00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda2 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 2200.029 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179571.968000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.968000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179571.976000] Memory: 508904k/523136k available (1910k kernel code, 13596k reserved, 1069k data, 308k init, 0k highmem)
[17179571.976000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.056000] Calibrating delay using timer specific routine.. 4405.67 BogoMIPS (lpj=8811358)
[17179572.056000] Security Framework v1.0.0 initialized
[17179572.056000] SELinux:  Disabled at boot.
[17179572.056000] Mount-cache hash table entries: 512
[17179572.056000] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[17179572.056000] CPU: After vendor identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[17179572.056000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179572.056000] CPU: L2 Cache: 1024K (64 bytes/line)
[17179572.056000] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[17179572.056000] Checking 'hlt' instruction... OK.
[17179572.072000] SMP alternatives: switching to UP code
[17179572.072000] Freeing SMP alternatives: 16k freed
[17179572.072000] checking if image is initramfs... it is
[17179572.476000] Freeing initrd memory: 5323k freed
[17179572.476000] ACPI: Core revision 20060707
[17179572.476000] ACPI: Looking for DSDT ... not found!
[17179572.572000] CPU0: AMD Athlon(tm) 64 Processor 3700+ stepping 01
[17179572.572000] Total of 1 processors activated (4405.67 BogoMIPS).
[17179572.576000] ENABLING IO-APIC IRQs
[17179572.576000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[17179572.720000] Brought up 1 CPUs
[17179572.720000] migration_cost=0
[17179572.720000] NET: Registered protocol family 16
[17179572.720000] EISA bus registered
[17179572.720000] ACPI: bus type pci registered
[17179572.720000] PCI: PCI BIOS revision 2.10 entry at 0xf9fd0, last bus=1
[17179572.720000] PCI: Using configuration type 1
[17179572.720000] Setting up standard PCI resources
[17179572.728000] ACPI: Interpreter enabled
[17179572.728000] ACPI: Using IOAPIC for interrupt routing
[17179572.728000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179572.728000] PCI: Probing PCI hardware (bus 00)
[17179572.732000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:0f.0
[17179572.732000] PCI: Quirk-MSI-K8T Soundcard On
[17179572.732000] PCI: MSI-K8T soundcard on
[17179572.732000] Boot video device is 0000:01:00.0
[17179572.732000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179572.772000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 *11 12)
[17179572.772000] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 6 7 10 11 12)
[17179572.772000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12) *5
[17179572.772000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[17179572.772000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 *10 11 12)
[17179572.772000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[17179572.772000] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[17179572.772000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[17179572.772000] ACPI: PCI Interrupt Link [ALKA] (IRQs *20), disabled.
[17179572.776000] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
[17179572.776000] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
[17179572.776000] ACPI: PCI Interrupt Link [ALKD] (IRQs *23), disabled.
[17179572.776000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179572.776000] pnp: PnP ACPI init
[17179572.780000] pnp: PnP ACPI: found 13 devices
[17179572.780000] PnPBIOS: Disabled by ACPI PNP
[17179572.780000] PCI: Using ACPI for IRQ routing
[17179572.780000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179572.804000] pnp: 00:02: ioport range 0x4000-0x407f could not be reserved
[17179572.804000] pnp: 00:02: ioport range 0x5000-0x500f has been reserved
[17179572.804000] PCI: Bridge: 0000:00:01.0
[17179572.804000]   IO window: e000-efff
[17179572.804000]   MEM window: fb000000-fcffffff
[17179572.804000]   PREFETCH window: f0000000-f7ffffff
[17179572.804000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179572.804000] NET: Registered protocol family 2
[17179572.844000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179572.844000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179572.844000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179572.844000] TCP: Hash tables configured (established 16384 bind 8192)
[17179572.844000] TCP reno registered
[17179572.844000] audit: initializing netlink socket (disabled)
[17179572.844000] audit(1167562392.844:1): initialized
[17179572.844000] VFS: Disk quotas dquot_6.5.1
[17179572.844000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.844000] Initializing Cryptographic API
[17179572.844000] io scheduler noop registered
[17179572.844000] io scheduler anticipatory registered
[17179572.844000] io scheduler deadline registered
[17179572.844000] io scheduler cfq registered (default)
[17179572.844000] isapnp: Scanning for PnP cards...
[17179573.196000] isapnp: No Plug & Play device found
[17179573.212000] Real Time Clock Driver v1.12ac
[17179573.212000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179573.212000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.212000] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.212000] mice: PS/2 mouse device common for all mice
[17179573.212000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179573.212000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.212000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.212000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179573.212000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179573.212000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.212000] EISA: Probing bus 0 at eisa.0
[17179573.212000] Cannot allocate resource for EISA slot 4
[17179573.212000] Cannot allocate resource for EISA slot 5
[17179573.212000] EISA: Detected 0 cards.
[17179573.212000] TCP bic registered
[17179573.212000] NET: Registered protocol family 1
[17179573.212000] NET: Registered protocol family 8
[17179573.212000] NET: Registered protocol family 20
[17179573.212000] Using IPI No-Shortcut mode
[17179573.212000] ACPI: (supports S0 S3 S4 S5)
[17179573.216000] Freeing unused kernel memory: 308k freed
[17179573.240000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179574.276000] Capability LSM initialized
[17179574.296000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[17179574.296000] ACPI: Getting cpuindex for acpiid 0x1
[17179574.296000] ACPI: Thermal Zone [THRM] (40 C)
[17179574.536000] VP_IDE: IDE controller at PCI slot 0000:00:0f.0
[17179574.536000] ACPI: PCI Interrupt Link [ALKA] disabled and referenced, BIOS bug
[17179574.536000] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[17179574.536000] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 169
[17179574.536000] PCI: Via IRQ fixup for 0000:00:0f.0, from 255 to 9
[17179574.536000] VP_IDE: chipset revision 6
[17179574.536000] VP_IDE: not 100% native mode: will probe irqs later
[17179574.536000] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.0
[17179574.536000]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb:DMA
[17179574.536000]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:DMA
[17179574.536000] Probing IDE interface ide0...
[17179574.952000] hda: Maxtor 6Y160P0, ATA DISK drive
[17179575.232000] hdb: ST38410A, ATA DISK drive
[17179575.288000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179575.308000] Probing IDE interface ide1...
[17179576.172000] hdc: DVDRW USB1008UI, ATAPI CD/DVD-ROM drive
[17179576.956000] hdd: CD-ROM CMD5X11, ATAPI CD/DVD-ROM drive
[17179577.012000] ide1 at 0x170-0x177,0x376 on irq 15
[17179577.016000] hda: max request size: 512KiB
[17179577.028000] hda: 320173056 sectors (163928 MB) w/7936KiB Cache, CHS=19929/255/63, UDMA(133)
[17179577.028000] hda: cache flushes supported
[17179577.028000]  hda: hda1 hda2 hda3
[17179577.048000] hdb: max request size: 128KiB
[17179577.048000] hdb: 16841664 sectors (8622 MB) w/512KiB Cache, CHS=16708/16/63, UDMA(66)
[17179577.048000] hdb: cache flushes not supported
[17179577.048000]  hdb: hdb1
[17179577.092000] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[17179577.092000] Uniform CD-ROM driver Revision: 3.20
[17179577.108000] hdd: ATAPI 52X CD-ROM drive, 128kB Cache
[17179578.188000] usbcore: registered new driver usbfs
[17179578.188000] usbcore: registered new driver hub
[17179578.188000] USB Universal Host Controller Interface driver v3.0
[17179578.188000] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[17179578.188000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 177
[17179578.188000] PCI: Via IRQ fixup for 0000:00:10.0, from 11 to 1
[17179578.188000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[17179578.188000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[17179578.188000] uhci_hcd 0000:00:10.0: irq 177, io base 0x0000fe00
[17179578.192000] usb usb1: configuration #1 chosen from 1 choice
[17179578.192000] hub 1-0:1.0: USB hub found
[17179578.192000] hub 1-0:1.0: 2 ports detected
[17179578.296000] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 177
[17179578.296000] PCI: Via IRQ fixup for 0000:00:10.1, from 11 to 1
[17179578.296000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[17179578.296000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[17179578.296000] uhci_hcd 0000:00:10.1: irq 177, io base 0x0000fd00
[17179578.296000] usb usb2: configuration #1 chosen from 1 choice
[17179578.296000] hub 2-0:1.0: USB hub found
[17179578.296000] hub 2-0:1.0: 2 ports detected
[17179578.400000] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 177
[17179578.400000] PCI: Via IRQ fixup for 0000:00:10.2, from 3 to 1
[17179578.400000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[17179578.400000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[17179578.400000] uhci_hcd 0000:00:10.2: irq 177, io base 0x0000fc00
[17179578.400000] usb usb3: configuration #1 chosen from 1 choice
[17179578.400000] hub 3-0:1.0: USB hub found
[17179578.400000] hub 3-0:1.0: 2 ports detected
[17179578.504000] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 177
[17179578.504000] PCI: Via IRQ fixup for 0000:00:10.3, from 3 to 1
[17179578.504000] uhci_hcd 0000:00:10.3: UHCI Host Controller
[17179578.504000] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[17179578.504000] uhci_hcd 0000:00:10.3: irq 177, io base 0x0000fb00
[17179578.504000] usb usb4: configuration #1 chosen from 1 choice
[17179578.504000] hub 4-0:1.0: USB hub found
[17179578.504000] hub 4-0:1.0: 2 ports detected
[17179578.608000] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 177
[17179578.608000] PCI: Via IRQ fixup for 0000:00:10.4, from 5 to 1
[17179578.608000] ehci_hcd 0000:00:10.4: EHCI Host Controller
[17179578.608000] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[17179578.608000] ehci_hcd 0000:00:10.4: irq 177, io mem 0xfdfff000
[17179578.608000] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179578.608000] usb usb5: configuration #1 chosen from 1 choice
[17179578.608000] hub 5-0:1.0: USB hub found
[17179578.608000] hub 5-0:1.0: 8 ports detected
[17179578.764000] Attempting manual resume
[17179578.788000] kjournald starting.  Commit interval 5 seconds
[17179578.788000] EXT3-fs: mounted filesystem with ordered data mode.
[17179579.900000] usb 2-2: new full speed USB device using uhci_hcd and address 2
[17179580.060000] usb 2-2: configuration #1 chosen from 1 choice
[17179587.184000] input: PC Speaker as /class/input/input1
[17179587.560000] parport: PnPBIOS parport detected.
[17179587.560000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179587.608000] Floppy drive(s): fd0 is 1.44M
[17179587.628000] FDC 0 is a post-1991 82077
[17179587.632000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179587.652000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179587.848000] Linux agpgart interface v0.101 (c) Dave Jones
[17179587.860000] agpgart: Detected AGP bridge 0
[17179587.864000] agpgart: AGP aperture is 128M @ 0xe8000000
[17179588.184000] input: ImExPS/2 Logitech Wheel Mouse as /class/input/input2
[17179588.268000] orinoco.c 0.13e (David Gibson <hermes@gibson.dropbear.id.au> and others)
[17179588.268000] Compiled with Wireless extensions v.20
[17179588.396000] nvidia: module license 'NVIDIA' taints kernel.
[17179588.396000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 185
[17179588.396000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
[17179588.684000] ts: Compaq touchscreen protocol output
[17179588.824000] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[17179588.824000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 193
[17179588.824000] PCI: Via IRQ fixup for 0000:00:11.5, from 5 to 1
[17179588.824000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[17179589.500000] lp0: using parport0 (interrupt-driven).
[17179589.520000] Adding 1550264k swap on /dev/disk/by-uuid/6d1a69e9-5cd9-4bc4-9989-414e97382784.  Priority:-1 extents:1 across:1550264k
[17179589.672000] EXT3 FS on hda2, internal journal
[17179589.996000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179590.028000] NTFS volume version 3.1.
[17179591.336000] NET: Registered protocol family 17
[17179594.772000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17179596.524000] ACPI: Power Button (FF) [PWRF]
[17179596.524000] ACPI: Power Button (CM) [PWRB]
[17179596.600000] ibm_acpi: ec object not found
[17179596.628000] pcc_acpi: loading...
[17179596.860000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.60.2)
[17179596.868000] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[17179598.864000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[17179598.864000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17179598.864000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[17179599.332000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179599.332000] apm: overridden by ACPI.
[17179603.676000] Bluetooth: Core ver 2.8
[17179603.676000] NET: Registered protocol family 31
[17179603.676000] Bluetooth: HCI device and connection manager initialized
[17179603.676000] Bluetooth: HCI socket layer initialized
[17179603.724000] Bluetooth: L2CAP ver 2.8
[17179603.724000] Bluetooth: L2CAP socket layer initialized
[17179603.744000] Bluetooth: RFCOMM socket layer initialized
[17179603.744000] Bluetooth: RFCOMM TTY layer initialized
[17179603.744000] Bluetooth: RFCOMM ver 1.7
[17179731.008000] NET: Registered protocol family 10
[17179731.008000] lo: Disabled Privacy Extensions
[17179731.008000] IPv6 over IPv4 tunneling driver
me@me-desktop:~$ 


```

I forgot to copy the results of lsmod. I'm using an old FAT32 formatted drive as a temporary storage for all this stuff since I can only get online in Linux by hanging my computer out the window to catch a signal. Don't really like doing that.

---

### Post by elcasey on 2006-12-31
I finally got the drivers installed, and monitor mode shows up when I do an "iwpriv eth2." I had to install, using apt-get, "linux-headers-2.6.17-10-386," although I noticed the original tutorial uses the "-generic" headers. I was able to copy the .ko drivers using the alternate copy command with "uname -r" and it finally worked out. I uninstalled the headers after installation of the drivers.

Everything appears to be working at this point, after some hair-pulling moments when I couldn't get online (router needed to be reset - even the wired connection wasn't working).

Thanks for a quick, dirty (and once I figured out the problem) effective howto.

---

### Post by just_old_bob on 2006-12-31
lsmod results show two driver modules loaded
```
me@me-desktop:~$ lsmod
Module                  Size  Used by
ipv6                  272288  8 
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sony_acpi               6412  0 
sbs                    16804  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
hotkey                 11556  0 
dev_acpi               12292  0 
container               5632  0 
button                  7952  0 
battery                11652  0 
asus_acpi              17688  0 
ac                      6788  0 
af_packet              24584  0 
nls_iso8859_1           5248  1 
nls_cp437               6912  1 
vfat                   14720  1 
fat                    56348  1 vfat
nls_utf8                3200  1 
ntfs                  112116  1 
lp                     12964  0 
snd_seq_dummy           4996  0 
snd_seq_oss            36480  0 
snd_seq_midi            9984  0 
snd_seq_midi_event      8960  2 snd_seq_oss,snd_seq_midi
snd_seq                59120  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx            30360  1 
gameport               17160  1 snd_via82xx
snd_ac97_codec         97696  1 snd_via82xx
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  2 snd_seq,snd_pcm
snd_page_alloc         11400  2 snd_via82xx,snd_pcm
snd_mpu401_uart        10240  1 snd_via82xx
tsdev                   9152  0 
snd_rawmidi            27264  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          9868  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
nvidia               4554836  12 
snd                    58372  13 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
i2c_viapro              9876  0 
soundcore              11232  1 snd
i2c_core               23424  3 i2c_ec,nvidia,i2c_viapro
orinoco                47760  0 
hermes                  9984  1 orinoco
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
amd64_agp              13124  1 
agpgart                34888  2 nvidia,amd64_agp
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
evdev                  11392  1 
pcspkr                  4352  0 
psmouse                41352  0 
serio_raw               8452  0 
floppy                 63044  0 
ext3                  142728  1 
jbd                    62228  1 ext3
ehci_hcd               34696  0 
uhci_hcd               24968  0 
usbcore               134912  3 ehci_hcd,uhci_hcd
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
ide_disk               18560  6 
via82cxxx              10500  0 [permanent]
generic                 6276  0 
thermal                15624  0 
processor              31560  1 thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability
me@me-desktop:~$ 

```

---

### Post by webcrawler42 on 2007-01-01
> **rtcary said:**
> The Orinoco 802.11a/b (8460-05), I believe, uses the Atheros chip set.  I am a newbie at Linux, so all of this is a big mystery to me.

by looking at "http://www.ekahau.com/products/client/supported_pc_cards.html" it does use the Atheros chipset so you will have to use a different set of drivers, try searching the forum.

---

### Post by just_old_bob on 2007-01-01
I dun didit!

Downloaded all of those files again and created a directory structure like what was there. I guess I was holding my head in just the correct position and the 17 remaining fully functioning brain cells formed a synaptic cluster because I realized that in order for me to run make before I had to open it in gedit and save it without any extension. I did that with get_ezusb_fw.htm in the firmware folder and with kbuild.htm, makefile.htm & mkconf.htm. Then I used ndiswrapper to load the drivers for my PCI wireless card and hung my computer out the window to get a signal.  Ran the script (?) and it gave me a couple errors and then downloaded a windows driver zip and created 2 files. I copied them all into /lib/firmware. I ran make and make install in the main folder (for those files) and it gave me no errors. Restarted and had a signal after configuring it.  I had to reset it with iwpriv and fiddle with my lame home built reflector, but hey I'm on line now.

Thanks for all the help.

---

### Post by webcrawler42 on 2007-01-01
no problem for whatever help i gave, glad you got it working.

---

### Post by carnageultra on 2007-01-03
this card has been such a pain.. after trying for 2days with backtrack i gave up when backtrack started having problems detecting the slot.. Now i did every thing from your instructions (thanks of making it)....
The files copy over to the wireless folder after reboot i still don't see Monitor.

Any reason for this?
i'm on 6.10 with the latest madwifi driver, I'm thinking this is the reason so i will just format
cause i'm to lazy to do it manually.:-|

---

### Post by webcrawler42 on 2007-01-04
look up how you can ban the madwifi driver so it forces the orinoco, can't remember how to do it off hand.

---

### Post by tturrisi on 2007-01-04
> **carnageultra said:**
> this card has been such a pain.. after trying for 2days with backtrack i gave up when backtrack started having problems detecting the slot.. Now i did every thing from your instructions (thanks of making it)....
The files copy over to the wireless folder after reboot i still don't see Monitor.

Any reason for this?
i'm on 6.10 with the latest madwifi driver, I'm thinking this is the reason so i will just format
cause i'm to lazy to do it manually.:-|
> look up how you can ban the madwifi driver so it forces the orinoco, can't remember how to do it off hand.
You cannot use the orinoco driver in place of the madwifi driver!
Drivers work with specific chipsets and these chipsets are in the device itself and cannot be changed.
orinoco drivers work with the following chipsets only:
[http://www.nongnu.org/orinoco/](http://www.nongnu.org/orinoco/)
madwifi drivers work with atheros chipsets only.

madwifi already has built in support for monitor mode thus no need to patch madwifi to get monitor mode.  For example, a stock madwifi install as in the Ubuntu restricted-modules will be able to put an atheros card into rfmon mode and the card even works with Kismet:
```
kismet.conf
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=madwifi_ag,wifi0,madwifi
```

---

### Post by webcrawler42 on 2007-01-05
sorry tturrisi, you are right.  i thought he was using the madwifi drivers with the Hermes I chipset.  just out of curiosity, how did u know he had an atheros card? he didn't say so, unless the madwifi drivers gave it away, i though he installed those instead of the orinoco drivers by accident.

---

### Post by tturrisi on 2007-01-05
> **webcrawler42 said:**
> sorry tturrisi, you are right.  i thought he was using the madwifi drivers with the Hermes I chipset.  just out of curiosity, how did u know he had an atheros card? he didn't say so, unless the madwifi drivers gave it away, i though he installed those instead of the orinoco drivers by accident.
yes, madwifi gave it away.
Either or, if he does have a hermes chipset then he has no business fooling w/ madwifi, and vice versa.  Orinoco_cs, orinoco, will work only w/ these chipsets:   Hermes by Lucent/Agere, Spectrum24 Trilogy by Symbol (including flashless cards) and Prism 2, 2.5 and 3 by Intersil.  Currently, orinoco usb is experimental.  Note:  thye newest orinoco driver (2006/08/16) now supports monitor mode again, but not for Agere firmware 7.xx and 8.xx, which is WHY the patch you linked to works with these hermes (agere) cards.  The firmware for thes devices is burnt onto the chipset itself, that's why rfmon is not nativiley supported. 

Advice for users who buy a card like this:  BEFORE using the card in windows, locate & download the older windows drivers & use them instead of the latest drivers w/ 7.xx or 8.xx firmware versions.  If the latest drivers are installed in windows, the driver setup pgm will flash the chipset w/ the new firmware, making rfmon break in linux, thus requiring the patch provided in this guide.  Had I known this when I first got my card I would not need the patch!  Newer versions of the card come pre-flashed with the new firmware, thus the patch is required for rfmon.

---

### Post by hannestum on 2007-01-08
Te easiest Way to get old OINOCO Cards working under Edgy is to downgrade the firmware of your card to 6.06! This FW works in monitor mode with the new 0.15 drivers.
Get the Firmware: [http://ftp.lucky.net/pub/radio/software/ORINOCO/PC_Card/Firmware/](http://ftp.lucky.net/pub/radio/software/ORINOCO/PC_Card/Firmware/)
Firmware downgrade is only working under Windows!

---

### Post by tturrisi on 2007-01-08
> **hannestum said:**
> Te easiest Way to get old OINOCO Cards working under Edgy is to downgrade the firmware of your card to 6.06! This FW works in monitor mode with the new 0.15 drivers.
Get the Firmware: [http://ftp.lucky.net/pub/radio/software/ORINOCO/PC_Card/Firmware/](http://ftp.lucky.net/pub/radio/software/ORINOCO/PC_Card/Firmware/)
Firmware downgrade is only working under Windows!
Yes that works, but not for all cards that use the orinoco drivers.  Some cards have lucent-agere chipsets made by other vendors and these cards can't be flashed using that utility.  It's only for specific orinoco models.  I've a 2wire orinoco card w/ an agere chipset that can't be flashed by that util, thus I need the patched drivers.

---

### Post by webcrawler42 on 2007-01-31
everyone get everything working?

---

### Post by zcrxsir88 on 2007-02-03
I did all that worked great, but now my card isnt detected.  How do i undo!?!?

\haha

Thanks

---

### Post by webcrawler42 on 2007-02-03
i haven't tested this, but it should work, just remove the .kos that you added for the orinoco card, reboot, then follow my guide again.

---

### Post by h2gofast on 2007-02-09
I got it working under kismet, had some issues with aircrack that could be user related.  Hibernate, or suspend do not work with the card.  Shutdown is fine of course but when I wake up my laptop from hibernate or suspend I cannot get the card to work as it did before.  It's like the pcmcia slot is off unless I reboot.

---

### Post by webcrawler42 on 2007-02-10
all of aircrack should work except for aireplay. I have disabled "Hibernate/suspend" in my bios because i never use it, so hopefully someone else has some answers.

---

### Post by acidblue on 2007-03-01
Is there a way to do this in Dapper?
I got a Lucent orinoco card that works under Mepis with the  'orinoco_cs driver.
Just can't get it to work in Unbuntu...

---

### Post by oranguman on 2007-03-01
hi, thanks a lot for the help webcrawler. your how-to worked for me right off the bat. 


my question is, does anyone know where I can download the "clean" version of the orinoco driver? I forgot to back it up, I think that the patched version has overwritten it. I'm having trouble with my network manager at the moment.

edit: found em'.

---

### Post by rtcary on 2007-03-02
Where did you find the clean driver?

---

### Post by tturrisi on 2007-03-02
> **rtcary said:**
> Where did you find the clean driver?

If you have the same kernel that's on the live cd, boot the live cd and copy the .ko files to your a dir on the hd.

---

### Post by webcrawler42 on 2007-03-02
> **acidblue said:**
> Is there a way to do this in Dapper?
I got a Lucent orinoco card that works under Mepis with the  'orinoco_cs driver.
Just can't get it to work in Unbuntu...

you should just be able to get the drivers for your kernel build from here
[http://www.projectiwear.org/~plasmahh/orinoco.html](http://www.projectiwear.org/~plasmahh/orinoco.html)
and almost everything in my guide should be the same (except for the kernel build), try using this option when following my guide "(i have been told by ninocass you can "sudo cp *.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless" and it will "enter the users kernel version incase someone is running this under a different kernel", i have not tested if this works yet)"

---

### Post by acidblue on 2007-03-04
I am using a custom kernel: 2.6..15.7-ubuntu1rocko
didn't change anything used oldconfig when i compiled.
couldn't get kernel source for cd installed kernel
Using Dapper 6.06 think it came with 2.6.11-28 or something 
simular.
Anyway I downloaded the orinoco-0.13e-SN-12 driver since that seems to 
be the right one for the kernel i'm running (according to the website)
But when i run 'make' i get the following error's:

acidblue@darkmatter:~/orinoco-0.13e-SN-12$ make
make -C /lib/modules/2.6.15.7-ubuntu1rocko/build SUBDIRS=/home/acidblue/orinoco- 0.13e-SN-12 modules
make[1]: Entering directory `/usr/src/linux-source-2.6.15'
/bin/sh: /home/acidblue/orinoco-0.13e-SN-12/.tmp_versions/hermes.mod: Permission  denied
/bin/sh: /home/acidblue/orinoco-0.13e-SN-12/.tmp_versions/orinoco.mod: Permissio n denied
  CC [M]  /home/acidblue/orinoco-0.13e-SN-12/orinoco_cs.o
/home/acidblue/orinoco-0.13e-SN-12/orinoco_cs.c: In function ‘orinoco_cs_attach’ :
/home/acidblue/orinoco-0.13e-SN-12/orinoco_cs.c:249: warning: assignment from in compatible pointer type
/home/acidblue/orinoco-0.13e-SN-12/orinoco_cs.c:196: warning: unused variable ‘r et’
/home/acidblue/orinoco-0.13e-SN-12/orinoco_cs.c: In function ‘orinoco_cs_detach’ :
/home/acidblue/orinoco-0.13e-SN-12/orinoco_cs.c:284: warning: implicit declarati on of function ‘dev_to_instance’
/home/acidblue/orinoco-0.13e-SN-12/orinoco_cs.c:284: warning: initialization mak es pointer from integer without a cast
/home/acidblue/orinoco-0.13e-SN-12/orinoco_cs.c: In function ‘orinoco_cs_event’:
/home/acidblue/orinoco-0.13e-SN-12/orinoco_cs.c:611: warning: initialization mak es pointer from integer without a cast
/home/acidblue/orinoco-0.13e-SN-12/orinoco_cs.c: At top level:
/home/acidblue/orinoco-0.13e-SN-12/orinoco_cs.c:768: error: unknown field ‘probe ’ specified in initializer
/home/acidblue/orinoco-0.13e-SN-12/orinoco_cs.c:768: warning: excess elements in  struct initializer
/home/acidblue/orinoco-0.13e-SN-12/orinoco_cs.c:768: warning: (near initializati on for ‘orinoco_driver’)
/home/acidblue/orinoco-0.13e-SN-12/orinoco_cs.c:769: error: unknown field ‘suspe nd’ specified in initializer
/home/acidblue/orinoco-0.13e-SN-12/orinoco_cs.c:769: warning: excess elements in  struct initializer
/home/acidblue/orinoco-0.13e-SN-12/orinoco_cs.c:769: warning: (near initializati on for ‘orinoco_driver’)
/home/acidblue/orinoco-0.13e-SN-12/orinoco_cs.c:770: error: unknown field ‘resum e’ specified in initializer
/home/acidblue/orinoco-0.13e-SN-12/orinoco_cs.c:770: warning: excess elements in  struct initializer
/home/acidblue/orinoco-0.13e-SN-12/orinoco_cs.c:770: warning: (near initializati on for ‘orinoco_driver’)
/home/acidblue/orinoco-0.13e-SN-12/orinoco_cs.c:772: error: unknown field ‘remov e’ specified in initializer
/home/acidblue/orinoco-0.13e-SN-12/orinoco_cs.c:772: warning: excess elements in  struct initializer
/home/acidblue/orinoco-0.13e-SN-12/orinoco_cs.c:772: warning: (near initializati on for ‘orinoco_driver’)
/home/acidblue/orinoco-0.13e-SN-12/orinoco_cs.c: In function ‘exit_orinoco_cs’:
/home/acidblue/orinoco-0.13e-SN-12/orinoco_cs.c:813: warning: passing argument 1  of ‘orinoco_cs_detach’ from incompatible pointer type
/home/acidblue/orinoco-0.13e-SN-12/orinoco_cs.c: At top level:
/home/acidblue/orinoco-0.13e-SN-12/orinoco_cs.c:818: fatal error: opening depend ency file /home/acidblue/orinoco-0.13e-SN-12/.orinoco_cs.o.d: Permission denied
compilation terminated.
make[2]: *** [/home/acidblue/orinoco-0.13e-SN-12/orinoco_cs.o] Error 1
make[1]: *** [_module_/home/acidblue/orinoco-0.13e-SN-12] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.15'
make: *** [modules] Error 2


Any help is greatly appreciated.

---

### Post by webcrawler42 on 2007-03-04
try "sudo make", i never was able to get the drivers to work under 6.06 dapper, thats why i switched to 6.10 edgy eft.

---

### Post by zod32 on 2007-04-01
Any chance that this will work with feisty fawn?

---

### Post by webcrawler42 on 2007-04-04
I don't know, but I guess we'll find out April 19th (final release), unless someone wants to test it on the beta.

---

### Post by zaerion on 2007-04-09
i've been reading this thread and have been trying to update my orinoco drivers to support monitor mode.  i'm using an iBook and am not sure if these drivers are correct for my airport card.  when i try to 'sudo make' i get an error when compiling 'airport.c'.  note sure if i have to do anything different, but just thought i'd ask.  ^^

---

### Post by webcrawler42 on 2007-04-09
can you post your ifconfig and iwconfig please?

---

### Post by tturrisi on 2007-04-11
If this is your Airport card:
M7600LL/D
then it uses the orinoco driver.  If not, then your card has an atheros chipset or a broadcom chipset:
[http://linux-wless.passys.nl/query_part.php?brandname=Apple](http://linux-wless.passys.nl/query_part.php?brandname=Apple)

---

### Post by ninocass on 2007-04-19
ANy updates for fiesty im getting:

```


make -C /lib/modules/2.6.20-15-386/build SUBDIRS=/home/nino/origno/orinoco-0.13e-SN-14 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-386'
  CC [M]  /home/nino/origno/orinoco-0.13e-SN-14/hermes.o
  CC [M]  /home/nino/origno/orinoco-0.13e-SN-14/orinoco.o
In file included from /home/nino/origno/orinoco-0.13e-SN-14/orinoco.c:444:
/home/nino/origno/orinoco-0.13e-SN-14/orinoco.h:86: warning: ‘packed’ attribute ignored for field of type ‘uint8_t[16]’
/home/nino/origno/orinoco-0.13e-SN-14/orinoco.h:217: warning: ‘packed’ attribute ignored for field of type ‘char[16]’
/home/nino/origno/orinoco-0.13e-SN-14/orinoco.c: In function ‘alloc_orinocodev’:
/home/nino/origno/orinoco-0.13e-SN-14/orinoco.c:5141: error: ‘struct net_device’ has no member named ‘get_wireless_stats’
/home/nino/origno/orinoco-0.13e-SN-14/orinoco.c:5166:67: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/nino/origno/orinoco-0.13e-SN-14/orinoco.c:5166: error: ‘INIT_WORK’ undeclared (first use in this function)
/home/nino/origno/orinoco-0.13e-SN-14/orinoco.c:5166: error: (Each undeclared identifier is reported only once
/home/nino/origno/orinoco-0.13e-SN-14/orinoco.c:5166: error: for each function it appears in.)
make[2]: *** [/home/nino/origno/orinoco-0.13e-SN-14/orinoco.o] Error 1
make[1]: *** [_module_/home/nino/origno/orinoco-0.13e-SN-14] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-386'
make: *** [modules] Error 2


```

And no *.ko files are being made :(

---

### Post by webcrawler42 on 2007-04-20
> **ninocass said:**
> ANy updates for fiesty im getting:

```


make -C /lib/modules/2.6.20-15-386/build SUBDIRS=/home/nino/origno/orinoco-0.13e-SN-14 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-386'
  CC [M]  /home/nino/origno/orinoco-0.13e-SN-14/hermes.o
  CC [M]  /home/nino/origno/orinoco-0.13e-SN-14/orinoco.o
In file included from /home/nino/origno/orinoco-0.13e-SN-14/orinoco.c:444:
/home/nino/origno/orinoco-0.13e-SN-14/orinoco.h:86: warning: &#8216;packed&#8217; attribute ignored for field of type &#8216;uint8_t[16]&#8217;
/home/nino/origno/orinoco-0.13e-SN-14/orinoco.h:217: warning: &#8216;packed&#8217; attribute ignored for field of type &#8216;char[16]&#8217;
/home/nino/origno/orinoco-0.13e-SN-14/orinoco.c: In function &#8216;alloc_orinocodev&#8217;:
/home/nino/origno/orinoco-0.13e-SN-14/orinoco.c:5141: error: &#8216;struct net_device&#8217; has no member named &#8216;get_wireless_stats&#8217;
/home/nino/origno/orinoco-0.13e-SN-14/orinoco.c:5166:67: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/nino/origno/orinoco-0.13e-SN-14/orinoco.c:5166: error: &#8216;INIT_WORK&#8217; undeclared (first use in this function)
/home/nino/origno/orinoco-0.13e-SN-14/orinoco.c:5166: error: (Each undeclared identifier is reported only once
/home/nino/origno/orinoco-0.13e-SN-14/orinoco.c:5166: error: for each function it appears in.)
make[2]: *** [/home/nino/origno/orinoco-0.13e-SN-14/orinoco.o] Error 1
make[1]: *** [_module_/home/nino/origno/orinoco-0.13e-SN-14] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-386'
make: *** [modules] Error 2


```

And no *.ko files are being made :(

try using [http://www.projectiwear.org/~plasmahh/orinoco-0.13e-SN-15.tar.bz2](http://www.projectiwear.org/~plasmahh/orinoco-0.13e-SN-15.tar.bz2)

---

### Post by webcrawler42 on 2007-04-21
Anyone else have any input for feisty?

---

### Post by webcrawler42 on 2007-04-21
After 10 pages and 10,000+ reads, I would like to say that I am retiring from this thread due to the release of feisty and getting rid of my Orinoco card.

---

### Post by JulianLx on 2007-04-22
Hi,
I tryed it in my Kubuntu 7.04 and I get the following output that means" linux/config.h doesnot exist".

julian@la-peca:~/Desktop/orinoco-0.13e-SN-14$ sudo make
make -C /lib/modules/2.6.20-15-386/build SUBDIRS=/home/julian/Desktop/orinoco-0.13e-SN-14 modules
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.20-15-386'
  CC [M]  /home/julian/Desktop/orinoco-0.13e-SN-14/hermes.o
/home/julian/Desktop/orinoco-0.13e-SN-14/hermes.c:41:26: error: linux/config.h: No existe el fichero ó directorio
make[2]: *** [/home/julian/Desktop/orinoco-0.13e-SN-14/hermes.o] Error 1
make[1]: *** [_module_/home/julian/Desktop/orinoco-0.13e-SN-14] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.20-15-386'
make: *** [modules] Error 2
julian@la-peca:~/Desktop/orinoco-0.13e-SN-14$  

 Some hint? What can I do?

---

### Post by JulianLx on 2007-04-22
I tried with an older 2.6.11 kernel I had from Edgy and got the following that seemed to be alright

```
julian@la-peca:~/Desktop/orinoco-0.13e-SN-14$ sudo make
make -C /lib/modules/2.6.17-11-386/build SUBDIRS=/home/julian/Desktop/orinoco-0.13e-SN-14 modules
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.17-11-386'
  CC [M]  /home/julian/Desktop/orinoco-0.13e-SN-14/hermes.o
  CC [M]  /home/julian/Desktop/orinoco-0.13e-SN-14/orinoco.o
In file included from /home/julian/Desktop/orinoco-0.13e-SN-14/orinoco.c:444:
/home/julian/Desktop/orinoco-0.13e-SN-14/orinoco.h:86: aviso: se ignora el atributo &#8216;packed&#8217; para el campo de tipo &#8216;uint8_t[16]&#8217;
/home/julian/Desktop/orinoco-0.13e-SN-14/orinoco.h:217: aviso: se ignora el atributo &#8216;packed&#8217; para el campo de tipo &#8216;char[16]&#8217;
  CC [M]  /home/julian/Desktop/orinoco-0.13e-SN-14/orinoco_cs.o
In file included from /home/julian/Desktop/orinoco-0.13e-SN-14/orinoco_cs.c:42:
/home/julian/Desktop/orinoco-0.13e-SN-14/orinoco.h:86: aviso: se ignora el atributo &#8216;packed&#8217; para el campo de tipo &#8216;uint8_t[16]&#8217;
/home/julian/Desktop/orinoco-0.13e-SN-14/orinoco.h:217: aviso: se ignora el atributo &#8216;packed&#8217; para el campo de tipo &#8216;char[16]&#8217;
/home/julian/Desktop/orinoco-0.13e-SN-14/orinoco_cs.c: En la función &#8216;orinoco_cs_probe&#8217;:
/home/julian/Desktop/orinoco-0.13e-SN-14/orinoco_cs.c:192: aviso: variable &#8216;i&#8217; sin usar
/home/julian/Desktop/orinoco-0.13e-SN-14/orinoco_cs.c:192: aviso: variable &#8216;ret&#8217; sin usar
/home/julian/Desktop/orinoco-0.13e-SN-14/orinoco_cs.c: En la función &#8216;orinoco_cs_config&#8217;:
/home/julian/Desktop/orinoco-0.13e-SN-14/orinoco_cs.c:402: aviso: variable &#8216;i&#8217; sin usar
/home/julian/Desktop/orinoco-0.13e-SN-14/orinoco_cs.c: En el nivel principal:
/home/julian/Desktop/orinoco-0.13e-SN-14/orinoco_cs.c:76: aviso: se definió &#8216;dev_info&#8217; pero no se usa
/home/julian/Desktop/orinoco-0.13e-SN-14/orinoco_cs.c:99: aviso: se definió &#8216;dev_list&#8217; pero no se usa
/home/julian/Desktop/orinoco-0.13e-SN-14/orinoco_cs.c:577: aviso: se definió &#8216;orinoco_cs_event&#8217; pero no se usa
/home/julian/Desktop/orinoco-0.13e-SN-14/orinoco_cs.c:115: aviso: &#8216;orinoco_cs_attach&#8217; se declaró &#8216;static&#8217; pero nunca se definió
  CC [M]  /home/julian/Desktop/orinoco-0.13e-SN-14/orinoco_plx.o
In file included from /home/julian/Desktop/orinoco-0.13e-SN-14/orinoco_plx.c:134:
/home/julian/Desktop/orinoco-0.13e-SN-14/orinoco.h:86: aviso: se ignora el atributo &#8216;packed&#8217; para el campo de tipo &#8216;uint8_t[16]&#8217;
/home/julian/Desktop/orinoco-0.13e-SN-14/orinoco.h:217: aviso: se ignora el atributo &#8216;packed&#8217; para el campo de tipo &#8216;char[16]&#8217;
  CC [M]  /home/julian/Desktop/orinoco-0.13e-SN-14/orinoco_tmd.o
In file included from /home/julian/Desktop/orinoco-0.13e-SN-14/orinoco_tmd.c:78:
/home/julian/Desktop/orinoco-0.13e-SN-14/orinoco.h:86: aviso: se ignora el atributo &#8216;packed&#8217; para el campo de tipo &#8216;uint8_t[16]&#8217;
/home/julian/Desktop/orinoco-0.13e-SN-14/orinoco.h:217: aviso: se ignora el atributo &#8216;packed&#8217; para el campo de tipo &#8216;char[16]&#8217;
  CC [M]  /home/julian/Desktop/orinoco-0.13e-SN-14/orinoco_pci.o
In file included from /home/julian/Desktop/orinoco-0.13e-SN-14/orinoco_pci.c:113:
/home/julian/Desktop/orinoco-0.13e-SN-14/orinoco.h:86: aviso: se ignora el atributo &#8216;packed&#8217; para el campo de tipo &#8216;uint8_t[16]&#8217;
/home/julian/Desktop/orinoco-0.13e-SN-14/orinoco.h:217: aviso: se ignora el atributo &#8216;packed&#8217; para el campo de tipo &#8216;char[16]&#8217;
/home/julian/Desktop/orinoco-0.13e-SN-14/orinoco_pci.c:379: aviso: inicialización desde un tipo de puntero incompatible
  Building modules, stage 2.
  MODPOST
  CC      /home/julian/Desktop/orinoco-0.13e-SN-14/hermes.mod.o
  LD [M]  /home/julian/Desktop/orinoco-0.13e-SN-14/hermes.ko
  CC      /home/julian/Desktop/orinoco-0.13e-SN-14/orinoco.mod.o
  LD [M]  /home/julian/Desktop/orinoco-0.13e-SN-14/orinoco.ko
  CC      /home/julian/Desktop/orinoco-0.13e-SN-14/orinoco_cs.mod.o
  LD [M]  /home/julian/Desktop/orinoco-0.13e-SN-14/orinoco_cs.ko
  CC      /home/julian/Desktop/orinoco-0.13e-SN-14/orinoco_pci.mod.o
  LD [M]  /home/julian/Desktop/orinoco-0.13e-SN-14/orinoco_pci.ko
  CC      /home/julian/Desktop/orinoco-0.13e-SN-14/orinoco_plx.mod.o
  LD [M]  /home/julian/Desktop/orinoco-0.13e-SN-14/orinoco_plx.ko
  CC      /home/julian/Desktop/orinoco-0.13e-SN-14/orinoco_tmd.mod.o
  LD [M]  /home/julian/Desktop/orinoco-0.13e-SN-14/orinoco_tmd.ko
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.17-11-386'
julian@la-peca:~/Desktop/orinoco-0.13e-SN-14$ sudo cp *.ko /lib/modules/2.6.17-11-386/kernel/drivers/net/wireless
julian@la-peca:~/Desktop/orinoco-0.13e-SN-14$    

```

But after reboot I got

```
julian@la-peca:~$ sudo iwpriv eth1
Password:
eth1      no private ioctls.

julian@la-peca:~$ iwlist eth1 scanning
eth1      Interface doesn't support scanning.

julian@la-peca:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:D0:59:17:85:67
          inet addr:10.0.0.1  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::2d0:59ff:fe17:8567/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:362 errors:0 dropped:0 overruns:0 frame:0
          TX packets:435 errors:0 dropped:0 overruns:0 carrier:0
          collisions:3 txqueuelen:1000
          RX bytes:207481 (202.6 KiB)  TX bytes:45493 (44.4 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:767 errors:0 dropped:0 overruns:0 frame:0
          TX packets:767 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:22243 (21.7 KiB)  TX bytes:22243 (21.7 KiB)

```

but eth0 is the PCI of my laptop! My wireless card is a Symbol Spetrum24 PCMCIA supposed to be supported by the Orinoco driver. I tested the card in a Windows XP yesterday and was OK.
When I check at KInfoCenter for PCMCIA devices, I get that the PCMCIA slot is empty.

---

