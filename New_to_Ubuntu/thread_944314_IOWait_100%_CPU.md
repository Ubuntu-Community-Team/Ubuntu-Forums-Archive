---
title: "IOWait? 100% CPU"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by lian1238 on 2008-10-11
Hi guys,

Sometimes, the system monitor applet on my panel goes green (the color of IOWait). But I can't find out what program is using up all the CPU. I have a top monitor on conky, and they are showing normal usage. The 100% CPU usage of IOWait is causing lags in my music and slows down my computer. Can anyone tell me how I can find the source of this 100% CPU usage?

Thanks.

---

### Post by alanparly on 2008-10-15
Hi lian1238,
I have the same problem.
The 100%CPU flood can happen using different applications: firefox with flash pages, amule (other people had the same problem with this two applications), but also nautilus, for example just viewing some pictures. I tried switching off the bluetooth and wireless but nothing changed. I don't have nor tracker or beagle installed, as I use Ubuntu Studio 8.04. The best solution i found is to use the 2.6.24-16-rt kernel version: with this the flooding rate is reduced (it could happens just twice in an hour); with other kernel version the flooding rate increase dramatically.
Of course I tried the top monitor as you, but nothing seems to happen during the problem.
Please, anyone can help us?

P.S. Sorry for my English, I'm from Italy

---

### Post by hyper_ch on 2008-10-15
do you have an encrypted file system?

---

### Post by lian1238 on 2008-10-15
> **hyper_ch said:**
> do you have an encrypted file system?

Nope. I didn't do anything to the default kernel.

---

### Post by rybaxs on 2008-10-15
What is your Computer Specs and Ubuntu Version?
Memory = ?
CPU = ?


Is your desktop effects activated?

---

### Post by lian1238 on 2008-10-15
> **rybaxs said:**
> What is your Computer Specs and Ubuntu Version?
Memory = ?
CPU = ?


Is your desktop effects activated?

CPU: Intel Core 2 Duo 1.66 GHz, 667 MHz FSB, 2 MB L2 cache
Memory: 1 GB

compiz = on;

Sometimes, when I'm playing music with Exaile, it first goes up to 50% (first core running full), then it'd go to 100% (second core running full) and lags my music. This doesn't show in top. Only on the system monitor applet (IOWait). Could it be that Exaile is scanning for music? .. Wait I've just check and it was set to scan every 25 minutes. Turned that off now.

I can assume that this was the cause. But I'd like to know how to find out which process is doing the IOWait-ing.

---

### Post by alanparly on 2008-10-15
Asus laptop with Centrino DuoT2300E 1.66Ghz, 1024mb Ram memory, graphic intel int gma 950 gfx. Ubuntu installed in partition, in another partition I have Windows Xp Professional. Root 10Gb, Home 15Gb, Swap 2Gb.

Compiz=on

I don't use Exaile.

Any idea of other hidden process that can do something every X minutes?

---

### Post by Tomatz on 2008-10-15
Could be tracker trying to index the contents of a large archive or .iso. Try disabling tracker in sessions, reboot and see if the problem persists.

---

### Post by alanparly on 2008-10-15
@Tomatz

I use Ubuntu Studio 8.04, so no Tracker or Beagle are installed (I checked on Synaptic). Maybe there could be something else indexing my archive? I mean, the equilvalent of Tracker/Beagle used for Ubuntu Studio? I just know that two applications, but maybe there's another one I don't know..

---

### Post by Tomatz on 2008-10-15
Have you tried viewing "all processes" in system monitor when this happens?

---

### Post by durand on 2008-10-15
Found this great program recently.
```
sudo aptitude install iotop
```
In a terminal, run **iotop**.

---

### Post by jerome1232 on 2008-10-15
> **durand said:**
> Found this great program recently.
```
sudo aptitude install iotop
```
In a terminal, run **iotop**.

Do you know what repo that's in? I'm not finding it in my package list. I have universe/multiverse enabled.

---

### Post by durand on 2008-10-15
Ohh....I just realised that its currently only in Intrepid Universe :( Maybe you can compile it yourself? It's not too big.

---

### Post by durand on 2008-10-15
Or infact, forum search came up with this: [http://ubuntuforums.org/showthread.php?t=876738](http://ubuntuforums.org/showthread.php?t=876738)

---

### Post by jerome1232 on 2008-10-15
> **durand said:**
> Ohh....I just realised that its currently only in Intrepid Universe :( Maybe you can compile it yourself? It's not too big.

No biggie the .deb [here]("http://packages.ubuntu.com/intrepid/all/iotop/download") works fine under hardy!

---

### Post by alanparly on 2008-10-16
@Tomatz: all process in system monitor says that nothing is happening during a freeze.. So I tried this:

System>administration>registry system

Then I checked kern.log, syslog and messages, and I found something strange..

These are the results after a freeze:

**in messages:**
Oct 15 18:18:05 Alan-laptop kernel: [ 2670.504986]          cdb 25 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Oct 15 18:18:05 Alan-laptop kernel: [ 2670.504987]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
Oct 15 18:18:05 Alan-laptop kernel: [ 2675.547373] ata1: port is slow to respond, please be patient (Status 0xd1)
Oct 15 18:18:05 Alan-laptop kernel: [ 2680.538882] ata1: device not ready (errno=-16), forcing hardreset
Oct 15 18:18:05 Alan-laptop kernel: [ 2680.538889] ata1: soft resetting link
Oct 15 18:18:05 Alan-laptop kernel: [ 2680.889293] ata1.00: configured for UDMA/100
Oct 15 18:18:05 Alan-laptop kernel: [ 2681.081785] ata1.01: configured for UDMA/25
Oct 15 18:18:05 Alan-laptop kernel: [ 2681.081809] ata1: EH complete
Oct 15 18:18:05 Alan-laptop kernel: [ 2681.085621] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
Oct 15 18:18:05 Alan-laptop kernel: [ 2681.085799] sd 0:0:0:0: [sda] Write Protect is off
Oct 15 18:18:05 Alan-laptop kernel: [ 2681.086193] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 15 18:18:05 Alan-laptop kernel: [ 2681.086574] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
Oct 15 18:18:05 Alan-laptop kernel: [ 2681.086741] sd 0:0:0:0: [sda] Write Protect is off
Oct 15 18:18:05 Alan-laptop kernel: [ 2681.087412] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

**in syslog:**
Oct 15 18:18:05 Alan-laptop kernel: [ 2670.504973] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Oct 15 18:18:05 Alan-laptop kernel: [ 2670.504984] ata1.01: cmd a0/00:00:00:08:00/00:00:00:00:00/b0 tag 0 pio 8 in
Oct 15 18:18:05 Alan-laptop kernel: [ 2670.504986]          cdb 25 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Oct 15 18:18:05 Alan-laptop kernel: [ 2670.504987]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
Oct 15 18:18:05 Alan-laptop kernel: [ 2670.504991] ata1.01: status: { DRDY ERR }
Oct 15 18:18:05 Alan-laptop kernel: [ 2675.547373] ata1: port is slow to respond, please be patient (Status 0xd1)
Oct 15 18:18:05 Alan-laptop kernel: [ 2680.538882] ata1: device not ready (errno=-16), forcing hardreset
Oct 15 18:18:05 Alan-laptop kernel: [ 2680.538889] ata1: soft resetting link
Oct 15 18:18:05 Alan-laptop kernel: [ 2680.889293] ata1.00: configured for UDMA/100
Oct 15 18:18:05 Alan-laptop kernel: [ 2681.081785] ata1.01: configured for UDMA/25
Oct 15 18:18:05 Alan-laptop kernel: [ 2681.081809] ata1: EH complete
Oct 15 18:18:05 Alan-laptop kernel: [ 2681.085621] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
Oct 15 18:18:05 Alan-laptop kernel: [ 2681.085799] sd 0:0:0:0: [sda] Write Protect is off
Oct 15 18:18:05 Alan-laptop kernel: [ 2681.085803] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 15 18:18:05 Alan-laptop kernel: [ 2681.086193] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 15 18:18:05 Alan-laptop kernel: [ 2681.086574] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
Oct 15 18:18:05 Alan-laptop kernel: [ 2681.086741] sd 0:0:0:0: [sda] Write Protect is off
Oct 15 18:18:05 Alan-laptop kernel: [ 2681.086744] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 15 18:18:05 Alan-laptop kernel: [ 2681.087412] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA


**in kern.log:**
Oct 15 18:18:05 Alan-laptop kernel: [ 2670.504973] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Oct 15 18:18:05 Alan-laptop kernel: [ 2670.504984] ata1.01: cmd a0/00:00:00:08:00/00:00:00:00:00/b0 tag 0 pio 8 in
Oct 15 18:18:05 Alan-laptop kernel: [ 2670.504986]          cdb 25 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Oct 15 18:18:05 Alan-laptop kernel: [ 2670.504987]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
Oct 15 18:18:05 Alan-laptop kernel: [ 2670.504991] ata1.01: status: { DRDY ERR }
Oct 15 18:18:05 Alan-laptop kernel: [ 2675.547373] ata1: port is slow to respond, please be patient (Status 0xd1)
Oct 15 18:18:05 Alan-laptop kernel: [ 2680.538882] ata1: device not ready (errno=-16), forcing hardreset
Oct 15 18:18:05 Alan-laptop kernel: [ 2680.538889] ata1: soft resetting link
Oct 15 18:18:05 Alan-laptop kernel: [ 2680.889293] ata1.00: configured for UDMA/100
Oct 15 18:18:05 Alan-laptop kernel: [ 2681.081785] ata1.01: configured for UDMA/25
Oct 15 18:18:05 Alan-laptop kernel: [ 2681.081809] ata1: EH complete
Oct 15 18:18:05 Alan-laptop kernel: [ 2681.085621] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
Oct 15 18:18:05 Alan-laptop kernel: [ 2681.085799] sd 0:0:0:0: [sda] Write Protect is off
Oct 15 18:18:05 Alan-laptop kernel: [ 2681.085803] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 15 18:18:05 Alan-laptop kernel: [ 2681.086193] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 15 18:18:05 Alan-laptop kernel: [ 2681.086574] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
Oct 15 18:18:05 Alan-laptop kernel: [ 2681.086741] sd 0:0:0:0: [sda] Write Protect is off
Oct 15 18:18:05 Alan-laptop kernel: [ 2681.086744] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 15 18:18:05 Alan-laptop kernel: [ 2681.087412] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

Any idea?

---

### Post by rybaxs on 2008-10-16
How much is the free space of your hard disk?
Try to see on your Laptop Bios (Video shared Memory)
Make it to the lowest shared memory from RAM.

h0pe i can help..

Ah.. in my computer I quit Ubuntu Studio edition because it stop installing at the middle of the installation, I try the desktop edition. <- sorry about this.

---

### Post by alanparly on 2008-10-16
@rybaxs

As soon as i get home (now i'm in office) I try the Bios. Have you though about this solution in reading my kern.log, syslog and messages posts or is just an intuition?
I think I have about 10Gb free in root partition and 12Gb free in  home partition, but I don't think the problem could be caused by a lack of space, 'cause I got the freezes even just after installing, also with Ubuntu desktop edition (smaller than the Studio).
What a pity you can't use the Studio Edition, it's beautiful!

---

### Post by Tomatz on 2008-10-16
I think its a problem with your dvd drive see the link below:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/64587](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/64587)

Try disconnecting your CD/DVD drive (internally) and see if the problem persists. If it does not persist then we can try to work out a solution ;)

P.s What is the make and model number of your drive?

---

### Post by alanparly on 2008-10-16
@Tomatz

..ehm.. i'm using a laptop, how can I disconnect the CD/DVD drive?

On the Italian Ubuntu Forum a guy suggested it could be a problem with the sata disk... a driver bug

Could it be?

What can I do?

Thank you so much,, Tomatz

---

### Post by Tomatz on 2008-10-16
> **alanparly said:**
> @Tomatz

..ehm.. i'm using a laptop, how can I disconnect the CD/DVD drive?

On the Italian Ubuntu Forum a guy suggested it could be a problem with the sata disk... a driver bug

Could it be?

What can I do?

Thank you so much,, Tomatz

What is the make and model of the laptop (and/or the dvd drive)? We need to find updated firmware for you dvd rom so we can flash it.

---

### Post by Tomatz on 2008-10-16
Also does it have an option in the BIOS to change **IDE mode** from **"legacy" or "combined"** mode to **"AHCI", "RAID" or "native"**?

This may solve the problem without the need for flashing the drive.

---

### Post by alanparly on 2008-10-16
@Tomatz

Asus laptop with Centrino DuoT2300E 1.66Ghz, 1024mb Ram memory, graphic intel int gma 950 gfx

The problem seems the same as in the forum you linked.
I'll try the "easy" solution, working after inserting a cd on the drive. If it doesn't work I need your help, as I don't have the knowledge to flash the dvd rom...!  :-)

I could also try with the BIOS

Thank you by now

---

### Post by alanparly on 2008-10-17
Hi everybody,

I've tried the easy solution (run Ubuntu with a cd inserted in the cd drive) and well, it seems to work! I used Ubuntu for just 45 minutes, but even with: Firefox, 4 tabs, one with a youtube video playing; Azureus on; Synaptic opened; pic opened from Nautilus, and the -19-rt kernel version (wich gaves me a lot of 100%CPU floods), no freezes at all.

I know it's just a trick, and I want to test it working for much more time, but it works. Maybe the right solution could be flashing the drive or operate on the BIOS settings, but, as for now, I want to enjoy my Ubuntu Studio perfectly working for a couple of days, and then maybe I could try to operate the "right" solution, if somebody want to help me.

Thanx everybody to help me, especially Tomatz who linked me on the right path. :popcorn:

---

### Post by Tomatz on 2008-10-17
> **alanparly said:**
> Hi everybody,

I've tried the easy solution (run Ubuntu with a cd inserted in the cd drive) and well, it seems to work! I used Ubuntu for just 45 minutes, but even with: Firefox, 4 tabs, one with a youtube video playing; Azureus on; Synaptic opened; pic opened from Nautilus, and the -19-rt kernel version (wich gaves me a lot of 100%CPU floods), no freezes at all.

I know it's just a trick, and I want to test it working for much more time, but it works. Maybe the right solution could be flashing the drive or operate on the BIOS settings, but, as for now, I want to enjoy my Ubuntu Studio perfectly working for a couple of days, and then maybe I could try to operate the "right" solution, if somebody want to help me.

Thanx everybody to help me, especially Tomatz who linked me on the right path. :popcorn:


NP! Glad you have a solution at last. Just post back if you need more help ;)

:popcorn:

---

### Post by bigmonster on 2009-07-06
Exactly same problem. Hi iowait randomly every few minutes. I absolutely love ubuntu (9.04) but this is driving me mad because it freez my audio playback for a fraction of a second. I have tried disconnecting all external devices and disabling what i could find. Still the same. Different audio and video players-still the same. I have been running ubuntu in live mode, from my hard drive and from usb pendrive... Same problem over again. Hi iowait is only visible on that little monitor on the task bar. I'm using Toshiba laptop 1.47ghz with 1.25 gb RAM and plenty of space on hdd. It's nothing fancy, no bluetooth, webcam etc. My BIOS is locked so nothing crucial can be adjusted. Had the same problem in kubuntu and mint... It really starting to put me off... In other words HELP.

---

### Post by lian1238 on 2009-08-14
> **bigmonster said:**
> Exactly same problem. Hi iowait randomly every few minutes. I absolutely love ubuntu (9.04) but this is driving me mad because it freez my audio playback for a fraction of a second. I have tried disconnecting all external devices and disabling what i could find. Still the same. Different audio and video players-still the same. I have been running ubuntu in live mode, from my hard drive and from usb pendrive... Same problem over again. Hi iowait is only visible on that little monitor on the task bar. I'm using Toshiba laptop 1.47ghz with 1.25 gb RAM and plenty of space on hdd. It's nothing fancy, no bluetooth, webcam etc. My BIOS is locked so nothing crucial can be adjusted. Had the same problem in kubuntu and mint... It really starting to put me off... In other words HELP.
Have you tried install iotop and watching it during the iowait peak?

---

