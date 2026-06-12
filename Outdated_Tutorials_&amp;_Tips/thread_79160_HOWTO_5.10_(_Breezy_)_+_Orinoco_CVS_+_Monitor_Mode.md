---
title: "HOWTO: 5.10 ( Breezy ) + Orinoco CVS + Monitor Mode + Kismet"
date: 2005-10-19
forum: Outdated Tutorials &amp; Tips
---

### Post by jshein on 2005-10-19
Ok. Here is my updated HOWTO for getting monitor mode to work on 5.10 - Breezy with an orinoco card and kismet.

This is now confirmed to work on AMD64 and i386.

**Updated 2006-01-26 -> Updated orinoco Driver link to the rc4 driver**

**_NOTICE!_  The newer orinoco drivers will not work with newer firmwares on the cards v8.0+, so in order to use this you will have to downgrade your firmware to an earlier version.**

**Please read the entire howto before starting**

All commands are done as root, so either type sudo at the beginning of each line or type

> #sudo su

Start by making a temporary directory.

> #mkdir /orinoco
#cd /orinoco

Backup your existing drivers into that directory

> #mkdir backup
#cp /lib/modules/`uname -r`/kernel/drivers/net/wireless/orinoco* /orinoco/backup/
#cp /lib/modules/`uname -r`/kernel/drivers/net/wireless/hermes* /orinoco/backup/

Then install the necesary packages to build the packages

> #apt-get install linux-source build-essential gcc-3.4
#apt-get install linux-headers-<arch>

where <arch> is replaced by your running kernel architechture

386
386-smp
686
686-smp
k7
k7-smp

Go into the /usr/src directory

> #cd /usr/src

Extract the kernel source

> #bunzip2 linux-source-2.6.12.tar.bz2
#tar -xvf linux-source-2.6.12.tar

Create a symlink to the source

> #ln -s /usr/src/linux-source-2.6.12 /usr/src/linux

cd to the orinoco directory that you created earlier

> #cd /orinoco

Get the orinoco drivers source

> #wget [http://heanet.dl.sourceforge.net/sourceforge/orinoco/orinoco-0.15rc4.tar.gz](http://heanet.dl.sourceforge.net/sourceforge/orinoco/orinoco-0.15rc4.tar.gz)

Extract the source

> #tar -zxvf orinoco-0.15rc4.tar.gz

Go into the directory created

> cd orinoco-0.15rc4

Get the patches for the drivers

> #wget [http://www.kismetwireless.net/code/orinoco-0.15rc2-dragorn-02.diff](http://www.kismetwireless.net/code/orinoco-0.15rc2-dragorn-02.diff)

Test patching the drivers

> #patch -p1 --dry-run < orinoco-0.15rc2-dragorn-02.diff

And if there are no errors, patch the drivers

> patch -p1 < orinoco-0.15rc2-dragorn-02.diff

make the drivers

> #make

Install the drivers

> #make install

Install kismet

> #apt-get install kismet ethereal-common

Edit the .config file

> #nano /etc/kismet/kismet.conf

Locate the source line and and make it look like this

> source=orinoco,eth1,orinocosource

Insert your card, wait a few seconds, and stop the card with:

> #ifdown eth1

Insert your card and check that it is working, with monitor mode enabled

> #iwpriv eth1


Should list monitor mode, if it doesn't then check the output of

> #dmesg

If kismet will not work chances are that you have an incompatible firmware and will have to downgrade. 

You can get the firmwares from the bottom of the page at [http://airsnort.shmoo.com/orinocoinfo.html](http://airsnort.shmoo.com/orinocoinfo.html)     
Windows .exe format only unfortunatly.

---

### Post by renesr on 2005-10-23
Thanks .

Has been a great help until:
 
#cvs -z3 -d:ext:anoncvs@savannah.gnu.org:/cvsroot/orinoco co orinoco

Please let me know where to get the above.

Thanks

---

### Post by jshein on 2005-10-23
2005-10-23

Added installing cvs to the howto

> #apt-get install cvs

---

### Post by gerv on 2005-10-24
Surely you need to recompile the drivers after patching them?

Gerv

---

### Post by jshein on 2005-10-25
Fixed the order of the steps in the HOWTO.

I made a mistake copying it from my notes.

---

### Post by GoldBuggie on 2005-10-25
I can never get the orinoco source to compile. It gives me "error The kernel source is not configured". Any ideas on why this happens?

---

### Post by jshein on 2005-10-25
I updated the HOWTO To address this issue.

You are missing the kernel-headers

#apt-get install linux-headers-<arch>

where <arch> is replaced by your running kernel architechture

386
386-smp
686
686-smp
k7

---

### Post by GoldBuggie on 2005-10-25
Thank you you have been soo helpful. I would kiss you but it semas I can't at the moment :-#

:D

The applying of this seems to have done a great deal for me. Wireless still doesn't work. But *dmesg* gave me this msg for the first time [I]

eth1: Monitor mode support is buggy in this firmware, not enabling

[/I]So the drivers are probably correct and such..not to downgrade the firmware from 8.10 to something else. Now only to figure out how to use those .exe files.

---------------------
Little Comp Info: Toshiba Laptop Portege 4010; kernel 686

---

### Post by GoldBuggie on 2005-10-26
I finally got the it to work. Partially anyways. Since 8.0+ firmware versions of Lucent/Agere are such a pain I found out that a good way to go about things without changing firmware is to choose the patched 0.13e drivers. I got it to work with a patched 0.13e rev.8. 

iwpriv eth1 finally gave me
[I]monitor      (8BE8) : set   2 int   & get   0

[/I]So I finally got a correct driver. Not to figure out how to get a connection with this strange dhcp somwehere. Couldn't quite manage it on the first try.

Thanks for your help.

btw...you can download already patched 0.13e version from this place [http://www.projectiwear.org/~plasmahh/orinoco.html]("http://www.projectiwear.org/%7Eplasmahh/orinoco.html")
The .diff's are there if you want to reverse the patch :confused:

Hope this helps you 8.X firmware guys. :D

---

### Post by gerv on 2005-10-26
A few more tips which helped me:

I had to create a symlink in /lib/modules called "2.6.12", pointing to "2.6.12-9.386". Without it, the modules installed to the wrong place and weren't used. YMMV.

I also had to kill the DHCP daemon (dhclient3) before kismet would detect anything. This is in the kismet troubleshooting guide.

---

### Post by Cannedbread on 2005-10-28
Im running an enterasys "roamabout" which is supossedly an orinoco gold rebrand.  its got some kind of japanes firmware that allows access to 14 channels. it could not scan for APs or go into monitor mode out of the box, but after following these instructions scanning works. "monitor" does not come up on iwpriv, however kistmet loads and sorta works. (it picks up my neighbors AP but not my own, weird.)

I bought the card with the understanding that the orinoco gold is one of the most compatable linux wifi cards available. but upon plugging it into my system it doesnt support scanning. its the same with all the orinoco variants that i tried. why the hell isnt this version of the driver standard? this sort of tutorial wouldnt be necissary....

But still i thank you millions, i was stumped for months and not even the guys at the personal telco project and the PDX LUG could tell me what to do.

---

### Post by banunu on 2005-11-05
Big THANK YOU to jshein & also GoldBuggie for finally making clear the magic incantations to get Kismet working!  I am running Breezy on a thinkpad t22 with an Enteresys card flashed as an Orinoco Gold; dmesg says:

eth1: Firmware determined as Lucent/Agere 8.72

and 'uname -r' says 2.6.12-9-686

I have never understood how to make an installed Linux do Kismet properly, now I know why and what to do about it...  In the past I always just rebooted into Knoppix STD but other than jshein's excellent instruction the big thing was that the latest Orinoco drivers don't do monitor mode with the latest Orinoco firmware, what an unfortunate state of affairs!

I found the info here on this topic interesting, though the directions are not spot on for Ubuntu like those of jshein:

[http://www.linuxquestions.org/questions/answers/398](http://www.linuxquestions.org/questions/answers/398)

Anyway, I followed jshein's instructions and everything compiled fine and worked as one might expect though monitor mode was not enabled with my 8.72 firmware; I then downloaded orinoco-0.13e-SN-8.tar.bz2 from [http://www.projectiwear.org/%7Eplasmahh/orinoco.html](http://www.projectiwear.org/%7Eplasmahh/orinoco.html), and made that driver normally (ie make; make install; cp *.ko to the right place...) and for the first time I have working Kismet on my regular linux box.  Whew!

I think a lot of people have been thrown off by the broken monitor mode with the latest drivers & firmware; I wonder what the technical tradeoffs are in using an older driver vs an older firmware, but from past experience with various devices I am loathe to use old firmware that was presumably fixed for a good reason, and I generally hope current drivers are fully functional with latest firmwares.  Mind you I am no expert on Linux or Orinocos though.

Thanks again everyone for input on this topic.  I have had to do some tinkering to get a fully functional Kubuntu (java 1.5, Kismet, APM and Thinkpad fixes etc etc), but the info on Ubuntu has been so good that I now have a solid setup with more functionality than has ever been possible for me before,  You all are a credit to this excellent system.

---

### Post by jshein on 2005-11-07
Not a problem at all.

Happy wardriving :cool:

---

### Post by LodeRunner on 2005-11-13
Have any of you guys had trouble upgrading your firmware?

Kismet now actually starts after following OP's directions, but it lags my mouse like crazy and it does not see any packets, so I assumed that the card is not going into monitor mode.

I stuck it in a windows laptop and downloaded the firmware upgrader exes.  Every single one of them gave me a "No wireless card driver found."  This despite the fact that the card works perfectly in XP.  It suggested that I update my drivers and/or my firmware.  I'm not sure how they expect me to upgrade my firmware in order to run the firmware upgrader, but whatever.

My card was purchased off of eBay  without any drivers or documentation.  The card itself is bare metal with a sticker on it saying something along the lines of "Lucent Gold 128-bit, Euro edition."  It has two antenna ports, but no built-in antenna.  I was wary about buying such an oddball, but the price was right and the seller was throwing in a mag mount omni external antenna.

As far as I can tell, the Euro version would add a couple extra channels and lower the power output slightly, but as I said the card works fine in XP and Linux (except for monitor mode.)

I could only find two orinoco drivers on the web, one of which turned out to be merely a network monitoring utility instead of a driver.  I installed the new driver, and tried the firmware updaters again.  All gave me the same message, except 8.10 and 6.06 (the oldest and newest firmware versions.)  These two instead said:

"The wireless card driver currently installed on your computer is not compatible with this utility.  Please check out website for information about the latest availiable drivers and firmware updates. 

Details:
NDIS 5 Miniport driver
Variant 2, Version 7.82

Wireless Station Update (Windows)
Variant 1, Version 4.20"

So I'm pretty much at a loss right now.  Does anyone know of any other orinoco drivers?  I'd be willing to give someone a few bucks if they could burn a copy of their driver CD for me, especially if they actually have a euro orinoco.

Edit:  Windows recognizes it as an Orinoco and sets it up automatically (no Found New Hardware Wizard crap), so that much of its identity is not in question.

---

### Post by ssam on 2005-11-13
will this allow something like networkmanager or iwlist to list avaible access points?

---

### Post by falkex on 2005-11-14
have a small problem...

```

wget http://www.kismetwireless.net/code/o...ragorn-02.diff
--14:29:41--  http://www.kismetwireless.net/code/o...ragorn-02.diff
           => `o...ragorn-02.diff'
Resolving www.kismetwireless.net... 65.61.200.83
Connecting to www.kismetwireless.net|65.61.200.83|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
14:29:42 ERROR 404: Not Found.
```

Checked on [http://www.kismetwireless.net/code](http://www.kismetwireless.net/code) and the file doesn't exist but alot of others do... how do I know witch one to use?

---

### Post by falkex on 2005-11-14
[QUOTE=falkex]have a small problem...

```

wget http://www.kismetwireless.net/code/o...ragorn-02.diff
--14:29:41--  http://www.kismetwireless.net/code/o...ragorn-02.diff
           => `o...ragorn-02.diff'
Resolving www.kismetwireless.net... 65.61.200.83
Connecting to www.kismetwireless.net|65.61.200.83|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
14:29:42 ERROR 404: Not Found.
```

Checked on [http://www.kismetwireless.net/code](http://www.kismetwireless.net/code) and the file doesn't exist but alot of others do... how do I know witch one to use?[/QUOTE]


Sorry for the noob post realized that "o...ragorn-02.diff" meant orinoco-0.15rc2-dragorn-02.diff

---

### Post by falkex on 2005-11-14
Now I got one more step...

and then this happens...

```
patch -p1 --dry-run < orinoco-0.15rc2-dragorn-02.diff
patching file orinoco.c
Hunk #1 succeeded at 465 with fuzz 2 (offset 18 lines).
Hunk #2 succeeded at 532 with fuzz 2 (offset 22 lines).
Hunk #3 FAILED at 1198.
Hunk #4 FAILED at 1254.
Hunk #5 FAILED at 1274.
Hunk #6 FAILED at 1385.
Hunk #7 FAILED at 2368.
Hunk #8 succeeded at 3106 with fuzz 2 (offset 145 lines).
Hunk #9 succeeded at 5071 with fuzz 2 (offset 263 lines).
Hunk #10 FAILED at 5248.
Hunk #11 FAILED at 5331.
7 out of 11 hunks FAILED -- saving rejects to file orinoco.c.rej
patching file orinoco.h
Reversed (or previously applied) patch detected!  Assume -R? [n]
```

---

### Post by jshein on 2005-11-15
Reply to SSAM:

> will this allow something like networkmanager or iwlist to list avaible access points?

Yes it will. Try wifi-radar.


Reply to falkex:

Try re-synchronizing with the cvs server, and doing it again. Possibly there could be buggy CVS code posted for that day. ( Part of the potential problems of using CVS ) But it should be fixed within a day.  Another possibility is that they have changed the code so that the curent patch will no longer function. 

Has anyone else had this occur?

---

### Post by falkex on 2005-11-15
Resyncing worked fine. 
Patched and installed...
But now when I started kismet I hade problems anyway.

If you wanna help...

```
sudo kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 (orinocosource): Enabling monitor mode for orinoco source interface eth1 channel 6...
Source 0 (orinocosource): Opening orinoco source interface eth1...
Allowing clients to fetch WEP keys.
WARNING:  Disabling GPS logging.
Logging networks to //root/00-01-03-Kismet-Nov-16-2005-1.network
Logging networks in CSV format to //root/00-01-03-Kismet-Nov-16-2005-1.csv
Logging networks in XML format to //root/00-01-03-Kismet-Nov-16-2005-1.xml
Logging cryptographically weak packets to //root/00-01-03-Kismet-Nov-16-2005-1.weak
Logging cisco product information to //root/00-01-03-Kismet-Nov-16-2005-1.cisco
Logging data to //root/00-01-03-Kismet-Nov-16-2005-1.dump
Writing data files to disk every 300 seconds.
Mangling encrypted and fuzzy data packets.
Tracking probe responses and associating probe networks.
Reading AP manufacturer data and defaults from //etc/kismet/ap_manuf
Reading client manufacturer data and defaults from //etc/kismet/client_manuf
Using network-classifier based data encryption detection
Dump file format: wiretap (local code) dump
Crypt file format: airsnort (weak packet) dump
Kismet 2005.08.R1 (Kismet)
Logging data networks CSV XML weak cisco
Listening on port 2501.
Allowing connections from 127.0.0.1/255.255.255.255
Failed to set up UI server: TcpServer bind() failed: Cannot assign requested address
Didn't detect any networks, unlinking network list.
Didn't detect any networks, unlinking CSV network list.
Didn't detect any networks, unlinking XML network list.
Didn't detect any Cisco Discovery Packets, unlinking cisco dump
Didn't capture any packets, unlinking dump file
Didn't see any weak encryption packets, unlinking weak file
WARNING: Sometimes cards don't always come out of monitor mode
         cleanly.  If your card is not fully working, you may need to
         restart or reconfigure it for normal operation.
Kismet exiting.

```

---

### Post by jshein on 2005-11-15
Did you disable the card before starting kismet up?

#sudo ifdown eth1

Double check the howto as well to make sure you did not skip any steps.

Let me know...

---

### Post by mushanti on 2005-11-27
after following the instructions given, I get the following:

root@moksha:/orinoco/orinoco# patch -p1 < orinoco-0.15rc2-dragorn-02.diff patching file orinoco.c
Hunk #1 FAILED at 447.
Hunk #2 succeeded at 415 with fuzz 2 (offset -95 lines).
Hunk #3 succeeded at 722 with fuzz 1 (offset -454 lines).
Hunk #4 succeeded at 779 with fuzz 1 (offset -453 lines).
Hunk #5 succeeded at 799 (offset -453 lines).
Hunk #6 succeeded at 910 (offset -453 lines).
Hunk #7 succeeded at 1883 (offset -463 lines).
Hunk #8 succeeded at 2493 with fuzz 1 (offset -468 lines).
Hunk #9 succeeded at 4256 with fuzz 2 (offset -552 lines).
Hunk #10 succeeded at 4384 with fuzz 2 (offset -601 lines).
Hunk #11 FAILED at 4467.
2 out of 11 hunks FAILED -- saving rejects to file orinoco.c.rej
patching file orinoco.h
Hunk #1 succeeded at 111 (offset -29 lines).
patching file prism2header.h
root@moksha:/orinoco/orinoco#

What should I do?

---

### Post by jshein on 2005-11-27
This is most likely an issue with the daily build from CVS. 

Try again tomorrow and post the results.If you are still ahving issues then I will be glad to assist.

---

### Post by mushanti on 2005-11-28
Got it working with the 0.13 drivers as mentionned earlier in this thread.

Thanks!

[QUOTE=jshein]This is most likely an issue with the daily build from CVS. 

Try again tomorrow and post the results.If you are still ahving issues then I will be glad to assist.[/QUOTE]

---

### Post by john280z on 2005-11-29
Jshien,

   Your cvs command pulls 'latest' cvs which is orinoco-0.15rc3 (ver 3).
The patch is for orinoco-0.15rc2, the two do not work together!

   Your write up was very helpful to me.

---

### Post by ardoaamch on 2005-11-29
[QUOTE=john280z]Jshien,

   Your cvs command pulls 'latest' cvs which is orinoco-0.15rc3 (ver 3).
The patch is for orinoco-0.15rc2, the two do not work together!

   Your write up was very helpful to me.[/QUOTE]

Where would one get the orinoco-0.15rc2 that the article refers to?  I've had this working before, but now with the rc3 I can't get the card scanning.

---

### Post by GoldBuggie on 2005-11-29
Get the drivers here
[http://savannah.nongnu.org/projects/orinoco]("http://savannah.nongnu.org/projects/orinoco")

---

### Post by ardoaamch on 2005-11-29
[QUOTE=GoldBuggie]Get the drivers here
[http://savannah.nongnu.org/projects/orinoco]("http://savannah.nongnu.org/projects/orinoco")[/QUOTE]

So then would one download the 0.15rc2 and extract it, then run the patch from that directory?  I tried that and it doesn't seem to work.

Here's my output from make. Everything works fine up til here.

make -C /usr/src/linux-headers-2.6.12-10-686 M=/orinoco/orinoco/orinoco-0.15rc2 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-686'
  CC [M]  /orinoco/orinoco/orinoco-0.15rc2/hermes.o
In file included from /orinoco/orinoco/orinoco-0.15rc2/hermes.c:54:
/orinoco/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_present':
/orinoco/orinoco/orinoco-0.15rc2/hermes.h:400: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_set_irqmask':
/orinoco/orinoco/orinoco-0.15rc2/hermes.h:406: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_read_words':
/orinoco/orinoco/orinoco-0.15rc2/hermes.h:447: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_write_words':
/orinoco/orinoco/orinoco-0.15rc2/hermes.h:467: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_clear_words':
/orinoco/orinoco/orinoco-0.15rc2/hermes.h:483: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.c: In function `hermes_issue_cmd':
/orinoco/orinoco/orinoco-0.15rc2/hermes.c:105: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.c:109: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.c:115: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.c:116: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.c:117: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.c:118: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.c: In function `hermes_init':
/orinoco/orinoco/orinoco-0.15rc2/hermes.c:150: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.c:151: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.c:160: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.c:168: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.c:177: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.c:178: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.c:186: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.c:191: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.c:194: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.c:211: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.c:213: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.c: In function `hermes_docmd_wait':
/orinoco/orinoco/orinoco-0.15rc2/hermes.c:253: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.c:258: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.c:277: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.c:280: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.c:281: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.c:282: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.c:285: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.c: In function `hermes_allocate':
/orinoco/orinoco/orinoco-0.15rc2/hermes.c:308: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.c:313: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.c:330: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.c:331: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.c: In function `hermes_bap_seek':
/orinoco/orinoco/orinoco-0.15rc2/hermes.c:355: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.c:359: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.c:379: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.c:380: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.c:384: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.c:388: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.c: In function `hermes_read_ltv':
/orinoco/orinoco/orinoco-0.15rc2/hermes.c:487: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.c:492: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.c: In function `hermes_write_ltv':
/orinoco/orinoco/orinoco-0.15rc2/hermes.c:528: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.c:529: warning: passing arg 2 of `writew' makes pointer from integer without a cast
  CC [M]  /orinoco/orinoco/orinoco-0.15rc2/orinoco.o
In file included from /orinoco/orinoco/orinoco-0.15rc2/orinoco.c:508:
/orinoco/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_present':
/orinoco/orinoco/orinoco-0.15rc2/hermes.h:400: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_set_irqmask':
/orinoco/orinoco/orinoco-0.15rc2/hermes.h:406: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_read_words':
/orinoco/orinoco/orinoco-0.15rc2/hermes.h:447: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_write_words':
/orinoco/orinoco/orinoco-0.15rc2/hermes.h:467: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_clear_words':
/orinoco/orinoco/orinoco-0.15rc2/hermes.h:483: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/orinoco.c: In function `__orinoco_ev_alloc':
/orinoco/orinoco/orinoco-0.15rc2/orinoco.c:1001: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/orinoco.c:1010: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/orinoco.c: In function `__orinoco_ev_tx':
/orinoco/orinoco/orinoco-0.15rc2/orinoco.c:1022: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/orinoco.c: In function `__orinoco_ev_txexc':
/orinoco/orinoco/orinoco-0.15rc2/orinoco.c:1029: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/orinoco.c:1042: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/orinoco.c: In function `orinoco_tx_timeout':
/orinoco/orinoco/orinoco-0.15rc2/orinoco.c:1091: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/orinoco.c:1092: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/orinoco.c:1092: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/orinoco.c: In function `__orinoco_ev_rx':
/orinoco/orinoco/orinoco-0.15rc2/orinoco.c:1391: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/orinoco.c: In function `__orinoco_ev_info':
/orinoco/orinoco/orinoco-0.15rc2/orinoco.c:1677: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/orinoco.c: In function `__orinoco_down':
/orinoco/orinoco/orinoco-0.15rc2/orinoco.c:1920: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/orinoco.c: In function `orinoco_reset':
/orinoco/orinoco/orinoco-0.15rc2/orinoco.c:2469: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/orinoco.c: In function `orinoco_interrupt':
/orinoco/orinoco/orinoco-0.15rc2/orinoco.c:2563: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/orinoco.c:2607: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/orinoco.c:2609: warning: passing arg 1 of `readw' makes pointer from integer without a cast
  CC [M]  /orinoco/orinoco/orinoco-0.15rc2/orinoco_nortel.o
In file included from /orinoco/orinoco/orinoco-0.15rc2/orinoco_nortel.c:67:
/orinoco/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_present':
/orinoco/orinoco/orinoco-0.15rc2/hermes.h:400: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_set_irqmask':
/orinoco/orinoco/orinoco-0.15rc2/hermes.h:406: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_read_words':
/orinoco/orinoco/orinoco-0.15rc2/hermes.h:447: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_write_words':
/orinoco/orinoco/orinoco-0.15rc2/hermes.h:467: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_clear_words':
/orinoco/orinoco/orinoco-0.15rc2/hermes.h:483: warning: passing arg 2 of `writew' makes pointer from integer without a cast
  CC [M]  /orinoco/orinoco/orinoco-0.15rc2/orinoco_pci.o
In file included from /orinoco/orinoco/orinoco-0.15rc2/orinoco_pci.c:117:
/orinoco/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_present':
/orinoco/orinoco/orinoco-0.15rc2/hermes.h:400: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_set_irqmask':
/orinoco/orinoco/orinoco-0.15rc2/hermes.h:406: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_read_words':
/orinoco/orinoco/orinoco-0.15rc2/hermes.h:447: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_write_words':
/orinoco/orinoco/orinoco-0.15rc2/hermes.h:467: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_clear_words':
/orinoco/orinoco/orinoco-0.15rc2/hermes.h:483: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/orinoco_pci.c: In function `orinoco_pci_cor_reset':
/orinoco/orinoco/orinoco-0.15rc2/orinoco_pci.c:158: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/orinoco_pci.c:164: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/orinoco_pci.c:171: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/orinoco_pci.c:174: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco/orinoco-0.15rc2/orinoco_pci.c: In function `orinoco_pci_suspend':
/orinoco/orinoco/orinoco-0.15rc2/orinoco_pci.c:330: error: too many arguments to function `pci_save_state'
/orinoco/orinoco/orinoco-0.15rc2/orinoco_pci.c: In function `orinoco_pci_resume':
/orinoco/orinoco/orinoco-0.15rc2/orinoco_pci.c:347: error: too many arguments to function `pci_restore_state'
make[2]: *** [/orinoco/orinoco/orinoco-0.15rc2/orinoco_pci.o] Error 1
make[1]: *** [_module_/orinoco/orinoco/orinoco-0.15rc2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686'
make: *** [modules] Error 2

---

### Post by GoldBuggie on 2005-11-29
I do not know why it does not work for you. As superuser you should be able to just unpack it...patch it and compile. Try and do it without the patch and see if it works. Maybe the version works without the patch for you? But alas I do not know what might cause the error you are recieving. Sorry! Hopefully someone that has had experience in these kind of errors can help.

---

### Post by ardoaamch on 2005-11-30
The new drivers in CVS are 0.15rc3.  To get my card working right, I followed these steps almost exactly.  With the rc3 I suppose there is no need to patch the drivers.  So after you get the drivers from CVS and go into the orinoco folder (/orinoco/orinoco) just do a make, make install.  There were a few warnings, although I've been told to ignore these as they typically make no difference, only errors do. 

I've got a Dell Truemobile 1150 and now iwlist eth1 scan works for me.

---

### Post by jshein on 2005-11-30
I updated the HOWTO to reflect the change in CVS.

Now linking directly the the final rc2 driver.

---

### Post by linubix on 2005-12-02
Hello all...

Thanks for the great info, it has been very helpful.

I have followed these directions step-by-step and now I am having the same problem as ardoaamch is having when I try to make the drivers. Has anyone determined what causes these warnings? I have googled for answers but all that I find is that these are compiler warnings, no specifics on cause or remediation.

I have a few other questions (obviously I am new to this): 

1. What is the purpose of creating the symlink to the source? I understand the basics of what a symlink does for us (pg. 675, Linux Complete 2nd Ed. :rolleyes: ) but in this case what exactly is it for?

2. How does the system know to use the new drivers? Is it due to the make install command?

Any help is most appreciated, thanks.

---

### Post by jax on 2005-12-03
Hi linubix

I'm also having this problem when I run 'make'.

I have been trying to get monitor mode working on and off for about 2 years now. I've tried googling etc., but no solution to this problem.

Anyone got any ideas?

jax.

---

### Post by linubix on 2005-12-04
Just a small update...

I was finally able to get *make* to work by making a few simple changes to the driver. There were still a long list of warnings but the 2 errors at the end of the list are gone. I ran *make install* and it worked. I verified that the new driver loaded using *dmesg* (it did) but  iwpriv eth0 shows that monitor mode is still not available. *Dmesg* shows that the loaded driver is now orinico_cs 0.15rc2STA...I am guessing that this is correct.

Anyone have any ideas?

---

### Post by GoldBuggie on 2005-12-04
You don't have firmware 8.+ right? This howto works really well for installing all drivers but alas the latest driver might not always be the best one. It depends on which firmware you have. I had to use a differnt driver from what was suggested.

---

### Post by shadow07 on 2005-12-04
I can tell you that I have an official Orinoco Gold card, with the latest firmware (8.27 I believe).  Anwyay, I was able to not only compile the RC3 drivers, but use them as well.  I can scan for wireless networks, and I don't have any errors in dmesg log.  Also, NetworkManager 0.4.1 is able to scan wireless networks, and I can associate with unprotected networks.

---

### Post by linubix on 2005-12-06
GoldBuggie - 
I have 5 different Lucent WaveLAN Gold cards...firmware ranges from 7.28 to 8.10...

shadow07 -
I decided to start over clean and I just finished re-installing 5.10 and all updates. I am hoping to eventually figure out why I am having troubles. Trial and error...that seems to be how most of you have figured it out. 

I wonder if I should try using the 8.10 firmware card with the rc3 driver?

As always, any advice is most welcome.

Thanks

---

### Post by shadow07 on 2005-12-08
I rebuilt my laptop about 3 times.  This last time I happened to stumble across this thread.  The driver provided with the base OS does not provide scanning capability with my Orinoco GOLD card.  I first started with RC2 and the patch.  Applying the patch failed numerous times.  And compiling the driver failed as well.  So, I scrapped it, and got RC3.  Did not apply any patch.  Simply compiled it, installed the drivers.  Vola.  My Orinoco card is detected, and NetworkManager can scan for wireless networks.  And I didn't even downgrade the firmware on my card.  It is still at the latest and greatest from Agere Systems/Orinoco.

---

### Post by lord2013 on 2005-12-13
I have the same problem on a fresh setup 5.10 (Breezy) with all patches applied.
Does anybody have a soluton for that compiling error?

Version 0.15rc3 compiles fine for me but without monitor mode.

Thanks in advance!

---

### Post by el_Salmon on 2005-12-26
Orinoco 0.15x doesn't work for me. Although, Orinoco 0.13e works fine (look at [ Orinoco Scan & Monitor Mode Patch Page]("http://www.projectiwear.org/~plasmahh/orinoco.html")). I've followed these steps:
-> Become root:
```
sudo su
```
-> Backup drivers:
```
mkdir /orinoco
cd /orinoco
mkdir backup
cp /lib/modules/`uname -r`/kernel/drivers/net/wireless/orinoco* /orinoco/backup/
cp /lib/modules/`uname -r`/kernel/drivers/net/wireless/hermes* /orinoco/backup/
```
-> Install tools and sources:
```
apt-get install linux-source build-essential gcc-3.4 
apt-get install linux-headers-<arch>
```
where <arch> is replaced by your running kernel architechture:
386
386-smp
686
686-smp
k7
k7-smp

-> Prepare linux sources (replace 2.6.12 for current version) :
```
cd /usr/src
tar -jxvf linux-source-2.6.12.tar.bz2
ln -s /usr/src/linux-source-2.6.12 /usr/src/linux
```
-> Get orinoco patch and compile it:
```
cd /orinoco 
http://www.projectiwear.org/~plasmahh/orinoco-0.13e-SN-8.tar.bz2
tar -jxvf orinoco-0.13e-SN-8.tar.bz2
cd orinoco-0.13e-SN-8
make
```
-> Install it:
```
cp /orinoco/orinoco-0.13e-SN-8/*.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/orinoco
```
-> Stop wifi card:
```
ifdown eth1
```
-> Eject and insert card. Try it:
```
dmesg
iwpriv eth0
```

---

### Post by seekyrr on 2006-01-11
On apt-get install linux-source build-essential gcc-3.4, I got the error that it was not specific.

I downloaded the linux-source-2.16.12.

Other wise I followed the directions and everything went great until the Make command.

When I try to run Make it says
Makefile:35 *** The kernel source is not configured. Stop.

Any ideas?

EDIT.

I went and installed the gcc-3.4 files through Synaptic and tried Make again.. But still get same error
Thanks

Seek

---

### Post by seekyrr on 2006-01-11
I updated everything I could with Synaptic, removed the compiled driver folder and tried to remake.

Still not working and may reinstall OS and try again if you think it will help.  Here are the outputs from my current try.

Make

make: Warning: File `/usr/src/linux-headers-2.6.12-10-386/.config' has modification time 1.9e+08 s in the future
make -C /usr/src/linux-headers-2.6.12-10-386 M=/orinoco/orinoco-0.15rc2 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
make[1]: Warning: File `/usr/src/linux-headers-2.6.12-10-386/arch/i386/Makefile' has modification time 1.7e+08 s in the future
make[2]: Warning: File `scripts/Makefile.lib' has modification time 1.7e+08 s in the future
  CC [M]  /orinoco/orinoco-0.15rc2/hermes.o
In file included from /orinoco/orinoco-0.15rc2/hermes.c:54:
/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_present':
/orinoco/orinoco-0.15rc2/hermes.h:400: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_set_irqmask':
/orinoco/orinoco-0.15rc2/hermes.h:406: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_read_words':
/orinoco/orinoco-0.15rc2/hermes.h:447: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_write_words':
/orinoco/orinoco-0.15rc2/hermes.h:467: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_clear_words':
/orinoco/orinoco-0.15rc2/hermes.h:483: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.c: In function `hermes_issue_cmd':
/orinoco/orinoco-0.15rc2/hermes.c:105: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.c:109: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.c:115: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.c:116: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.c:117: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.c:118: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.c: In function `hermes_init':
/orinoco/orinoco-0.15rc2/hermes.c:150: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.c:151: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.c:160: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.c:168: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.c:177: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.c:178: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.c:186: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.c:191: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.c:194: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.c:211: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.c:213: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.c: In function `hermes_docmd_wait':
/orinoco/orinoco-0.15rc2/hermes.c:253: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.c:258: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.c:277: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.c:280: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.c:281: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.c:282: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.c:285: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.c: In function `hermes_allocate':
/orinoco/orinoco-0.15rc2/hermes.c:308: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.c:313: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.c:330: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.c:331: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.c: In function `hermes_bap_seek':
/orinoco/orinoco-0.15rc2/hermes.c:355: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.c:359: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.c:379: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.c:380: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.c:384: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.c:388: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.c: In function `hermes_read_ltv':
/orinoco/orinoco-0.15rc2/hermes.c:487: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.c:492: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.c: In function `hermes_write_ltv':
/orinoco/orinoco-0.15rc2/hermes.c:528: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.c:529: warning: passing arg 2 of `writew' makes pointer from integer without a cast
  CC [M]  /orinoco/orinoco-0.15rc2/orinoco.o
In file included from /orinoco/orinoco-0.15rc2/orinoco.c:508:
/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_present':
/orinoco/orinoco-0.15rc2/hermes.h:400: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_set_irqmask':
/orinoco/orinoco-0.15rc2/hermes.h:406: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_read_words':
/orinoco/orinoco-0.15rc2/hermes.h:447: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_write_words':
/orinoco/orinoco-0.15rc2/hermes.h:467: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_clear_words':
/orinoco/orinoco-0.15rc2/hermes.h:483: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/orinoco.c: In function `__orinoco_ev_alloc':
/orinoco/orinoco-0.15rc2/orinoco.c:1001: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/orinoco.c:1010: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/orinoco.c: In function `__orinoco_ev_tx':
/orinoco/orinoco-0.15rc2/orinoco.c:1022: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/orinoco.c: In function `__orinoco_ev_txexc':
/orinoco/orinoco-0.15rc2/orinoco.c:1029: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/orinoco.c:1042: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/orinoco.c: In function `orinoco_tx_timeout':
/orinoco/orinoco-0.15rc2/orinoco.c:1091: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/orinoco.c:1092: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/orinoco.c:1092: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/orinoco.c: In function `__orinoco_ev_rx':
/orinoco/orinoco-0.15rc2/orinoco.c:1391: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/orinoco.c: In function `__orinoco_ev_info':
/orinoco/orinoco-0.15rc2/orinoco.c:1677: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/orinoco.c: In function `__orinoco_down':
/orinoco/orinoco-0.15rc2/orinoco.c:1920: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/orinoco.c: In function `orinoco_reset':
/orinoco/orinoco-0.15rc2/orinoco.c:2469: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/orinoco.c: In function `orinoco_interrupt':
/orinoco/orinoco-0.15rc2/orinoco.c:2563: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/orinoco.c:2607: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/orinoco.c:2609: warning: passing arg 1 of `readw' makes pointer from integer without a cast
  CC [M]  /orinoco/orinoco-0.15rc2/orinoco_nortel.o
In file included from /orinoco/orinoco-0.15rc2/orinoco_nortel.c:67:
/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_present':
/orinoco/orinoco-0.15rc2/hermes.h:400: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_set_irqmask':
/orinoco/orinoco-0.15rc2/hermes.h:406: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_read_words':
/orinoco/orinoco-0.15rc2/hermes.h:447: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_write_words':
/orinoco/orinoco-0.15rc2/hermes.h:467: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_clear_words':
/orinoco/orinoco-0.15rc2/hermes.h:483: warning: passing arg 2 of `writew' makes pointer from integer without a cast
  CC [M]  /orinoco/orinoco-0.15rc2/orinoco_pci.o
In file included from /orinoco/orinoco-0.15rc2/orinoco_pci.c:117:
/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_present':
/orinoco/orinoco-0.15rc2/hermes.h:400: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_set_irqmask':
/orinoco/orinoco-0.15rc2/hermes.h:406: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_read_words':
/orinoco/orinoco-0.15rc2/hermes.h:447: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_write_words':
/orinoco/orinoco-0.15rc2/hermes.h:467: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_clear_words':
/orinoco/orinoco-0.15rc2/hermes.h:483: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/orinoco_pci.c: In function `orinoco_pci_cor_reset':
/orinoco/orinoco-0.15rc2/orinoco_pci.c:158: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/orinoco_pci.c:164: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/orinoco_pci.c:171: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/orinoco_pci.c:174: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/orinoco_pci.c: In function `orinoco_pci_suspend':
/orinoco/orinoco-0.15rc2/orinoco_pci.c:330: error: too many arguments to function `pci_save_state'
/orinoco/orinoco-0.15rc2/orinoco_pci.c: In function `orinoco_pci_resume':
/orinoco/orinoco-0.15rc2/orinoco_pci.c:347: error: too many arguments to function `pci_restore_state'
make[2]: *** [/orinoco/orinoco-0.15rc2/orinoco_pci.o] Error 1
make[1]: *** [_module_/orinoco/orinoco-0.15rc2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make: *** [modules] Error 2

Dmsg

[4295266.319000] orinoco 0.14alpha2 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[4295266.325000] orinoco_cs 0.14alpha2 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[4295266.418000] eth1: Hardware identity 0001:0001:0004:0000
[4295266.418000] eth1: Station identity  001f:0001:0006:0004
[4295266.418000] eth1: Firmware determined as Lucent/Agere 6.04
[4295266.418000] eth1: Ad-hoc demo mode supported
[4295266.418000] eth1: WEP supported, 104-bit key
[4295266.418000] eth1: MAC address 00:01:F4:EC:B7:6F
[4295266.419000] eth1: Station name "HERMES I"
[4295266.419000] eth1: ready
[4295266.425000] eth1: index 0x01: Vcc 5.0, irq 3, io 0x0100-0x013f
[4295404.589000] device eth1 entered promiscuous mode
[4295415.490000] eth1: no IPv6 routers present

When I run Kismet

kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 (orinocosource): Enabling monitor mode for orinoco source interface eth1 channel 6...
FATAL: Could not find 'monitor' private ioctl or use the newer style 'mode monitor' command.  This typically means that the drivers have not been patched or the correct drivers are being loaded. See the troubleshooting section of the README for more information.

---

### Post by guilag on 2006-01-17
I have not been able to make the driver orinoco-15-rc2 but instead I have downloaded the new package rc4 and it went fine.

Thanks for the great howto !

---

### Post by jshein on 2006-01-26
2006-01-27

I have updated the HOWTO to include the rc4 orinoco driver.

I have tried following my HOWTO on 2 fresh systems ( Breezy ) and it has compiled for me with no issues.

Thank you guilag for pointing this out, and I am glad my HOWTO has been helpful.

---

### Post by jippers on 2006-01-28
Hi there, this is a great walkthough for setting up this popular wifi card and ubuntu, but I'm having a problem applying the patch.  I've followed everything in the latest version but the patching isn't succesful.

root@fapt0p:/orinoco/orinoco-0.15rc4# patch -p1 --dry-run < orinoco-0.15rc2-dragorn-02.diff
patching file orinoco.c
Hunk #1 FAILED at 447.
Hunk #2 succeeded at 415 with fuzz 2 (offset -95 lines).
Hunk #3 succeeded at 721 with fuzz 1 (offset -455 lines).
Hunk #4 succeeded at 778 with fuzz 1 (offset -454 lines).
Hunk #5 succeeded at 798 (offset -454 lines).
Hunk #6 succeeded at 909 (offset -454 lines).
Hunk #7 succeeded at 1882 (offset -464 lines).
Hunk #8 succeeded at 2492 (offset -469 lines).
Hunk #9 succeeded at 4255 with fuzz 2 (offset -553 lines).
Hunk #10 succeeded at 4383 with fuzz 2 (offset -602 lines).
Hunk #11 FAILED at 4466.
2 out of 11 hunks FAILED -- saving rejects to file orinoco.c.rej
patching file orinoco.h
Hunk #1 succeeded at 110 (offset -30 lines).
patching file prism2header.h

What should I do?

EDIT:

I've gone ahead and tried downloading orinoco-0.15rc2.tar.gz and the patch did successfully work.  Although when compiling the driver, I got the exact same errors after 'make' as seekyr in the prior posts above.

EDIT the second:

I followed el_Salmon's advice and installe 0.13e version of the driver from his posted link and now I can see Monitor mode available in iwpriv.

---

### Post by casualprogrammer on 2006-01-30
A good, working ( for me ) alternative can be found here:

[http://www.wains.be/?p=4](http://www.wains.be/?p=4)

I am running Ubuntu 5.10 (2.6.12-10-386) on a Sony notebook ( Vaio PCG-SRX51P ) with integrated Lucent/Agere Orinoco mini PCI card.

Casual

---

### Post by adub on 2006-02-05
patch -p1 < orinoco-0.15rc2-dragorn-02.diff
i get this command as well

Hunk #3 FAILED at 1087.
Hunk #4 FAILED at 1143.
Hunk #5 FAILED at 1163.




i get the below error on make command

make[2]: *** [/orinoco/orinoco-0.15rc4/orinoco.o] Error 1
make[1]: *** [_module_/orinoco/orinoco-0.15rc4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make: *** [modules] Error 2

---

### Post by adub on 2006-02-05
also note i couldnt get the above link working i dont know if me running the old lucent orinoco gold has anything to do with this

[http://www.wains.be/?p=4](http://www.wains.be/?p=4)

this is the last hardware bit i have to get working on my new laptop  =)

the orinoco gold card works perfectly im online with it now just no monitor mode

thanks to all who can help i get make errors when attempting the above link and i have edit the Makefile to tell it where /usr/src/linux is etc downloaded all required packages to build etc as indicated in the tutorial

---

### Post by adub on 2006-02-05
make[2]: *** [/home/adub/Desktop/orinoco-0.13e-SN-10/orinoco-0.13e-SN-10/orino                                                                             co_cs.o] Error 1
make[1]: *** [_module_/home/adub/Desktop/orinoco-0.13e-SN-10/orinoco-0.13e-SN-                                                                             10] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: *** [modules] Error 2


oh so for so many post in succession i left something out on the wains  work around i get the above error message on the   #make   and i still get  hunk <-lol  errors when running the perl command

---

### Post by onyx on 2006-02-05
Hey everyone, I just installed Ubuntu today and was trying to get my Orinoco Gold card to work.

Like GoldBuggie, I had the best luck with the patched 0.13e Rev. 8 drivers on [http://www.projectiwear.org/~plasmahh/orinoco.html]("http://www.projectiwear.org/~plasmahh/orinoco.html").  I did need to reboot for some reason, but then it worked great and "iwpriv eth1" showed monitor mode.

Oh, also like gerv said I need to do a symlink from 2.6.12 to 2.6.12-10-386 (ln -s /lib/modules/2.6.12-10-386 /lib/modules/2.6.12).  

I was pretty much working off a fresh install and needed a bunch of extra stuff.  But kismet seems to be working great now.

Just wanted to thank everyone for their help, I was glad to get this working this quickly! :-)

---

### Post by firephish on 2006-02-14
Hi Everyone,

Thanks for the great howto and comments!

I have one query though, i have followed the method of GoldBuggie with the 0.13e Rev. 8 drivers from [http://www.projectiwear.org/~plasmahh/orinoco.html](http://www.projectiwear.org/~plasmahh/orinoco.html) 

Kismet / airodump etc appear to work fine, however if i do an iwpriv it tells me my card is not in monitor mode?

Also trying to manually get the card into monitor mode fails, ie:

iwpriv ath0 monitor
Invalid command : monitor

Wierd thing is as kismet is starting up i see the following:

the "Enabling monitor mode for orinoco source interface ath0 channel ... " apprears to execute without errors! Also and ifconfig ath0 shows the card is running as PROMISC!

Anyone have some ideas as to why kismet works but the card appears not to be in monitor mode with an iwpriv?

Thanks

---

### Post by casualprogrammer on 2006-02-16
Hi firephish,

you state:

"Also trying to manually get the card into monitor mode fails, ie:

iwpriv ath0 monitor
Invalid command : monitor"

It doesnt work, because monitor needs two attributes: 1/0 for on or off and channel

Try 

sudo iwpriv ath0 monitor 1 1

Casual

---

### Post by adub on 2006-02-16
# make
make -C /usr/src/linux-headers-2.6.12-10-386 M=/orinoco/orinoco-0.15rc4 KERNELRELEASE=2.6.12-10-386 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
CC [M] /orinoco/orinoco-0.15rc4/orinoco.o
/orinoco/orinoco-0.15rc4/orinoco.c: In function `orinoco_rx_monitor':
/orinoco/orinoco-0.15rc4/orinoco.c:724: error: storage size of 'hdr' isn't known
/orinoco/orinoco-0.15rc4/orinoco.c:724: warning: unused variable `hdr'
/orinoco/orinoco-0.15rc4/orinoco.c: At top level:
/orinoco/orinoco-0.15rc4/orinoco.c:4258: warning: 'orinoco_ioctl_setprism2header' defined but not used
/orinoco/orinoco-0.15rc4/orinoco.c:4292: warning: 'orinoco_ioctl_setfcsbytes' defined but not used
make[2]: *** [/orinoco/orinoco-0.15rc4/orinoco.o] Error 1
make[1]: *** [_module_/orinoco/orinoco-0.15rc4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make: *** [modules] Error 2



I followed the tutorial i have build-essential and the other necessary steps of the tutorial in ubuntu forums

i have an orinoco gold classic of coarse

i have done CC=gcc-3.4 to make sure it is compiling with the right gcc

i just dont know from here??

thanks to all who reply


TRYING TO GET MONITOR MODE WORKING BTW THE DRIVERS THAT COME WITH 5.10/BREEZY GET THE CARD WORKING BUT NOT THE MONITOR MODE

---

### Post by adub on 2006-02-16
monitor mode is working perfectly now followed el_salmons method after trying every combination of everything else

to anyone viewing this thread el_salmons method is on the first page with the original method by jshein

---

### Post by firephish on 2006-02-17
[QUOTE=casualprogrammer]Hi firephish,

you state:

"Also trying to manually get the card into monitor mode fails, ie:

iwpriv ath0 monitor
Invalid command : monitor"

It doesnt work, because monitor needs two attributes: 1/0 for on or off and channel

Try 

sudo iwpriv ath0 monitor 1 1

Casual[/QUOTE]


hmmm, still gives the same error. ie "invalid command"

Almost like its not using the correct diver ... oh well i'll keep on trying!

Thanks

---

### Post by casualprogrammer on 2006-02-17
[QUOTE=jshein]
You can get the firmwares from the bottom of the page at [http://airsnort.shmoo.com/orinocoinfo.html](http://airsnort.shmoo.com/orinocoinfo.html)     
Windows .exe format only unfortunatly.[/QUOTE]

Hi jshein,

on visiting [http://airsnort.shmoo.com/orinocoinfo.html](http://airsnort.shmoo.com/orinocoinfo.html) for firmware, as you suggested, the following caught my eye:

[QUOTE=Snax]News Flash - 2/19/04
The orinoco drivers now suppport monitor mode in CVS. Monitor mode is now handled via the iwconfig interface. Prism headers are not available.[/QUOTE]

This made me somewhat curious, I fetched the drivers cvs from [http://savannah.nongnu.org/cvs/?group=orinoco](http://savannah.nongnu.org/cvs/?group=orinoco) and compiled them, as per your above howto.

Everything went smooth, only I could see neither monitor mode advertised by iwpriv, nor would Kismet run. Also iwconfig, as mentioned by snax, would not get me any further.

Finally I found the remark about firmware at the bottom, alas all the links are broken. Googling found me: [http://download.melsa.net.id/Orinoco/Firmware/](http://download.melsa.net.id/Orinoco/Firmware/) and [http://support.proxim.com/cgi-bin/proxim.cfg/php/enduser/std_adp.php?p_faqid=1082](http://support.proxim.com/cgi-bin/proxim.cfg/php/enduser/std_adp.php?p_faqid=1082)

I managed to downgrade my firmware to 7.52 from 8.72 ( Windows XP ) and to my surprise everything works smoothly ( Kismet, Airsnort, Aircrack ), although iwpriv still does not advertise monitor mode as an option:

eth1      Available private ioctls :
          force_reset      (8BE0) : set   0       & get   0
          card_reset       (8BE1) : set   0       & get   0
          set_port3        (8BE2) : set   1 int   & get   0
          get_port3        (8BE3) : set   0       & get   1 int
          set_preamble     (8BE4) : set   1 int   & get   0
          get_preamble     (8BE5) : set   0       & get   1 int
          set_ibssport     (8BE6) : set   1 int   & get   0
          get_ibssport     (8BE7) : set   0       & get   1 int
          get_rid          (8BE9) : set   0       & get 1024 byte

Now I don't have to recompile and reinstall drivers with every kernel upgrade, as obviously Snax is right in his remark, that monitor mode is finally supported for the distribution.

Casual

---

### Post by scrillamaan on 2006-02-22
Shoutout and thanks to el_Salmon. I have post 8.0 firmware and his method worked great.:mrgreen:

---

### Post by dosadi on 2006-02-27
[QUOTE=seekyrr]When I try to run Make it says
Makefile:35 *** The kernel source is not configured. Stop.
I went and installed the gcc-3.4 files through Synaptic and tried Make again.. But still get same error
Seek[/QUOTE]

Yeah, I get a similar message:
Makefile:8: *** Kernel tree not found - please set KERNEL_PATH.  Stop.

I'm figuring that this is becasue I downloaded the 686 kernel headers accidentally and was running 386, I had done uname -m rather than uname -r as I should have. I'm going to switch to the 686 kernel to fix the problem rather than compile another 386 kernel.

In your case, the line in Makefile is differentn so I'm assuming we're compiling different versions of the wireless card's driver, but the problem is probably the same. Maybe you downloaded the wrong kernel headers? I used Adept (Kubuntu package manager) to install all the linux kernel packages for 686 and just left the image for 386 installed (it's the kernel I was booted into so of course I can't uninstall that). Now I will probably reboot it to get the 686 kernel booted rather than do this the hard way and try to tell Makefile where the kernel pieces and parts are. You could try using Synaptec (is that the Gnome package manager? can't remember) to do something similar. Use uname -r to figure out what kernel you are running, and make sure you have the headers and other bits for the right archetecture. 

Hopefully what I just did was sensible and I will reboot successfully. I posted before doing so as I don't want to remember where this page was but still wanted to share what I'm trying. Woohoo here we go . . . .

---

### Post by el_Salmon on 2006-03-04
I have created [a HOWTO in Ubuntu Wiki: Orinoco Monitor Mode]("https://wiki.ubuntu.com/OrinocoMonitorMode")

Thank you everyone!

---

### Post by ThUnD3rM0rPh on 2006-03-15
First, Hi all.

now for my problem. I'm using Dapper flight 5, but as far as i can see that shouldn't be the problem. First i tried following the how-to on the first page. well i couldn't get it to patch the file without errors, so i gave up on that. now i'm trying to use the 0.13e drivers from [www.projectiwear.org/~plasmahh/orinoco.html](www.projectiwear.org/~plasmahh/orinoco.html). This because it gets me quickly past the patching that wouldn't work for me. now when i run make on these drivers i get a few errors.

root@Firestorm:/orinoco/orinoco-0.13e-SN-8# make CC=gcc-3.4
make -C /lib/modules/2.6.15-18-386/build SUBDIRS=/orinoco/orinoco-0.13e-SN-8 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-18-386'
  CC [M]  /orinoco/orinoco-0.13e-SN-8/hermes.o
  CC [M]  /orinoco/orinoco-0.13e-SN-8/orinoco.o
  CC [M]  /orinoco/orinoco-0.13e-SN-8/orinoco_cs.o
/orinoco/orinoco-0.13e-SN-8/orinoco_cs.c: In function `orinoco_cs_error':
/orinoco/orinoco-0.13e-SN-8/orinoco_cs.c:153: warning: implicit declaration of function `pcmcia_report_error'
  CC [M]  /orinoco/orinoco-0.13e-SN-8/orinoco_plx.o
  CC [M]  /orinoco/orinoco-0.13e-SN-8/orinoco_tmd.o
  CC [M]  /orinoco/orinoco-0.13e-SN-8/orinoco_pci.o
/orinoco/orinoco-0.13e-SN-8/orinoco_pci.c:379: warning: initialization from incompatible pointer type
  Building modules, stage 2.
  MODPOST
*** Warning: "pcmcia_report_error" [/orinoco/orinoco-0.13e-SN-8/orinoco_cs.ko] undefined!
  CC      /orinoco/orinoco-0.13e-SN-8/hermes.mod.o
  LD [M]  /orinoco/orinoco-0.13e-SN-8/hermes.ko
  CC      /orinoco/orinoco-0.13e-SN-8/orinoco.mod.o
  LD [M]  /orinoco/orinoco-0.13e-SN-8/orinoco.ko
  CC      /orinoco/orinoco-0.13e-SN-8/orinoco_cs.mod.o
  LD [M]  /orinoco/orinoco-0.13e-SN-8/orinoco_cs.ko
  CC      /orinoco/orinoco-0.13e-SN-8/orinoco_pci.mod.o
  LD [M]  /orinoco/orinoco-0.13e-SN-8/orinoco_pci.ko
  CC      /orinoco/orinoco-0.13e-SN-8/orinoco_plx.mod.o
  LD [M]  /orinoco/orinoco-0.13e-SN-8/orinoco_plx.ko
  CC      /orinoco/orinoco-0.13e-SN-8/orinoco_tmd.mod.o
  LD [M]  /orinoco/orinoco-0.13e-SN-8/orinoco_tmd.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-18-386'

running just make gave me the same errors.
if there is anything else you guys need to know, just ask, i'm fairly new to this bit of linux :)

[B]edit: i got another version to work. but now i'm having trouble downgrading my card...  it says the firmware is Lucent/Agere 8.72
the firmware flash prog (both of the 7.xx versions) says the card isn't connected or the drivers isn't install. well i've tried two different drivers and the card is in. i guess it's not ment to be.

hmm i just rememberd something. the card works perfectly under knoppix-std, what is up with that? [/B]

**EDIT2: okay so i need a win 98 machine to do it.. to bad my old laptop with win98 is at my parents.. a plane trip away :(**

**EDIT3** Lookslike i've missunderstood this somewhat.. i'll just try a different .13e driver

---

### Post by cy218 on 2006-05-30
Hi all

The wiki worked great for me. One question though:

My disk is filling up fast so is there any of the stuff I downloaded (source and so on) that I can delete now my card works in scanning mode?

Hope that's enough info

Ta

Cy

---

### Post by changlinn on 2006-06-29
I have never been able to get this to work, really annoying me.
I have a problem patch the drivers everytime, now on dapper, still the same issue.

patch -p1 --dry-run < orinoco-0.15rc2-dragorn-02.diff

patching file orinoco.c

Hunk #1 FAILED at 447.

Hunk #2 succeeded at 443 with fuzz 2 (offset -67 lines).

Hunk #3 succeeded at 764 with fuzz 1 (offset -412 lines).

Hunk #4 succeeded at 821 with fuzz 1 (offset -411 lines).

Hunk #5 succeeded at 841 (offset -411 lines).

Hunk #6 succeeded at 952 (offset -411 lines).

Hunk #7 succeeded at 1921 (offset -425 lines).

Hunk #8 succeeded at 2533 (offset -428 lines).

Hunk #9 succeeded at 4306 with fuzz 2 (offset -502 lines).

Hunk #10 succeeded at 4434 with fuzz 2 (offset -551 lines).

Hunk #11 FAILED at 4517.

2 out of 11 hunks FAILED -- saving rejects to file orinoco.c.rej

patching file orinoco.h

Hunk #1 succeeded at 124 (offset -16 lines).

patching file prism2header.h

---

### Post by el_Salmon on 2006-06-29
[READ IT, please]("https://wiki.ubuntu.com/OrinocoMonitorMode")

---

### Post by uberpinguin on 2006-07-24
The orinoco project has moved to SVN.  To get the new, functional drivers you must execute ```
svn co https://svn.sourceforge.net/svnroot/orinoco orinoco
```  This version of the driver has monitor mode built-in, so you don't need the dragorn patch any more.  Note that some firmwares are known not to work with  monitor mode, and will have it disabled.  To force-enable monitor mode for all firmwares, orinoco.c must be modified on line 116 (or thereabouts) to read ```
 static int force_monitor = 1;
```  This may or may not allow you to use monitor mode - it depends on your firmware.

---

