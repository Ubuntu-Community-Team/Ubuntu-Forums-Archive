---
title: "Problems with shut-down"
date: 2012-06-17
forum: New to Ubuntu
---

### Post by EJ42 on 2012-06-17
Just being curious. I am using a Medion E7214 (aka MSI) laptop running 12.04 LTS and I am absolutely delighted with it. But for one very small annoyance: at the end of the day when I click on shut-down the machine shuts down but after 2,3,4 seconds it restarts. I then click a second time on shut-down and then the machine gracefully complies and stays down.
The funny thing is that this behaviour is not consistent since every once in a while the shut-down works the first time around.
Since I am mostly only running Firefox and Thunderbird I am inclined to incriminate my hardware. But then I remember that this behaviour only started with Natty Narwhal and never happened with Maverick Meerkat or before.
I can easily live with this but I wonder if out there other users with the same or different machines have the same problem.

---

### Post by daslinkard on 2012-06-17
What happens when you do the following command:

```
sudo apt-get shutdown -h now
```

After you type this into a terminal it should ask for your password.  I wonder if you have the same issue shutting down using the Command Line Interface?

---

### Post by EJ42 on 2012-06-17
Thank you. Tried your solution five times in a row and worked perfectly every time.
But this now leaves open the question why it works differently when I click on the shut-down option in the upper right corner of the screen. Different commands?

---

### Post by daslinkard on 2012-06-17
I'm going to work on this one for you....I wanted to see if the sudo command worked for you first....let's see what we can find out together!!!!

---

### Post by daslinkard on 2012-06-17
1st trouble shooting question for you...in your BIOS, do you have USB devices having the ability to wake?  If so, try turning this feature off.

---

### Post by EJ42 on 2012-06-17
This will be fantastic. I am 71 years old and retired on Christmas eve 2001 after having been a professional programmer since 1974. Assembly, Cobol, Basic, C, C++, Java. Looking forward to a new challenge.

---

### Post by EJ42 on 2012-06-17
About USBs I don't know. The only exterior connections are the internet line, a Lexmark printer which is always off, a mouse and a 1Tb exterior drive which is always off too. Will now reboot to check the BIOS.

---

### Post by daslinkard on 2012-06-17
Assuming this did not fix the issue....I found another possible solution as follows:

Type in terminal:
 1. ```
sudo gedit /etc/default/grub
``` 2. Find the line: ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
``` 3. Change this to: ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"
``` 4. Save the file and close the file.  
5. Finally, in terminal: ```
sudo update-grub
```

Hopefully this gets you where you can shutdown with no issues!

---

### Post by EJ42 on 2012-06-17
Checked the BIOS. Could not see anything that would say  'auto reboot'. Sorry but the last time I played with hardware was around 1985.

---

### Post by daslinkard on 2012-06-17
No worries at all....try my post right above yours....see if changing this in the grub helps resolve the issue....

For me, I went from 11.10 to 12.04 and kept 12.04 for about a week....the issue that I had was the freezing up the distro was causing....I would be just trying to access Firefox and Thunderbird....and BOOM, BANG, BONG...my system was dead...thus I went back to 11.10....no issues.

---

### Post by EJ42 on 2012-06-17
Did it. Will keep you updated by tomorrow. Reason: remember this behaviour is (was) intermittent. So have to try it over time.

Anyway, fantastic help tank you very much.

---

### Post by daslinkard on 2012-06-17
You're very welcome....I've subscribed to this thread so when you update on what you find out....I will be notified via email!!!

---

### Post by EJ42 on 2012-06-18
Good afternoon daslinkard. Here it is 7:46am Tuesday morning. Good news the 'acpi=force' thing did the trick. I have shut down and rebooted a dozen times while having programs running or not and the shut down operation worked perfectly every time. This thead can be marked 'solved'
A great many thanks, may God give you eternal youth and a long life.
EJ.

---

### Post by EJ42 on 2012-06-18
Local Australian time: Tuesday June 19 1:27pm.  It happened again. I was too eager. Sorry, Once more unto the breach.

---

### Post by daslinkard on 2012-06-20
Is it still acting up on you?

---

### Post by EJ42 on 2012-06-21
Yes it is. I even had a case when it rebooted when I had shut it down manually using 'sudo shutdown -h now'

The only things which have changed are a bunch of automatic updates from Ubuntu.

---

### Post by daslinkard on 2012-06-22
Run the following command:

```
sudo apt-get install -f
```

This should find and allow you to fix any errors.  Let me know the output.

---

### Post by EJ42 on 2012-06-22
ej@ej-E7214:~$ sudo apt-get install -f
[sudo] password for ej: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gstreamer0.10-fluendo-mp3:i386 liboil0.3:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
ej@ej-E7214:~$

---

### Post by daslinkard on 2012-06-22
Have you tried updating the grub?

```
sudo update-grub
```

---

### Post by EJ42 on 2012-06-23
Yes. I have run 'sudo update-grub'. Seamed to work for a short while but when coming back after mid-morning coffee the old problem came back. All I am running is Firefox, Thunderbird and the occasional terminal and calculator. It's just a small annoyance once or twice a day, probably caused by hardware.
Oh forgot: first thing I run every morning is LibreOffice Calc to update a spreadsheet with daily data. Then I don't touch it anymore for the day.

---

### Post by daslinkard on 2012-06-24
This [link]("http://www.sinarpelangi.com/ubuntu-can-not-shutdown-solution-2/") has similar sudo commands that I originally gave....it seems that the shutdown is slightly different.  Maybe try this tutorial and go from there.

---

### Post by EJ42 on 2012-06-25
Will do and shall keep you informed if I find something of importance.

Thank you very much for your endeavours.

EJ.

---

### Post by daslinkard on 2012-06-25
No worries....now question....did this happen after you did an upgrade to 12.04 or did you do an install?

---

### Post by EJ42 on 2012-06-25
I have not done a full install for years. Actually the problem appeared with 11.04 and maybe even the one before but not before that. It simply persisted when I upgraded to 12.04.
The funny thing is that before you and I started to work on it shutdown would work as expected one time in ten whereas now it works maybe six times in ten. So there is a improvement but the problem still lurks in the background.

---

### Post by daslinkard on 2012-06-26
I'm wondering if because you have done upgrades in the past if this is not creating the issue....what about backing up your info and doing a full install of 12.04?

---

### Post by EJ42 on 2012-06-27
I have toyed with that idea for some time now. The reason for is; one starts with a clean sheet, the reason against is; it negates the very concept of continuity involved with seamless upgrading.
I am saying this while being fully aware that regular backups are the back-bone of IT and are easily automated.
Backups are meant to be either a emergency solution in case of catastrophe or as a means to document evolution when multiple backups are kept over time.
Having said that I confess that your suggestion has triggered an urge. I will now purchase another exterior drive, back everything up and reinstall from scratch.

PS: Back in the early eighties when we had removable winchester disks I had been working on a program from about ten in the morning, now it was around three at night and I was dead tired; so I made an error. the OS froze. No problem, I had backups. So I installed the first one and because I was tired I made the same error again. A hour later having exhausted each and every one of my three backup disks I went to bed and had to wait two weeks to get a new copy of the OS (Amos if anyone remembers that).

---

### Post by daslinkard on 2012-06-27
Good luck....and let me know how the fresh install works for you!  I'll be here if you have any questions, etc.

---

### Post by EJ42 on 2012-07-09
OK so I have bought a 1TB drive and fitted it into the second bay of my machine. While I was at it and because I was given an offer I could not refuse I also bought a 8GB memory slab. After taking out the 1GB slab and leaving in the original 2GB slab I now have 10GB of DDR3 in my machine. Everything seamed to work fine but when transferring files to and from both hard drives or from another external hard drive the screen turns blank and I must turn the machine off and on again to bring it back to life.

Below a dump of my memory and also of my storage devices, the new 1TB disk does not seem to be recognised but I can access it.


ej@ej-E7214:~$ sudo lshw -C memory
[sudo] password for ej: 
  *-firmware              
       description: BIOS
       vendor: American Megatrends Inc.
       physical id: 0
       version: 4.6.3
       date: 06/24/2010
       size: 64KiB
       capacity: 960KiB
       capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification
  *-cache:0
       description: L1 cache
       physical id: 5
       slot: L1-Cache
       size: 32KiB
       capacity: 32KiB
       capabilities: internal write-back unified
  *-cache:1
       description: L2 cache
       physical id: 6
       slot: L2-Cache
       size: 256KiB
       capacity: 256KiB
       capabilities: internal varies unified
  *-cache:2
       description: L3 cache
       physical id: 7
       slot: L3-Cache
       size: 3MiB
       capacity: 3MiB
       capabilities: internal varies unified
  *-memory
       description: System Memory
       physical id: 29
       slot: System board or motherboard
       size: 10GiB
     *-bank:0
          description: DIMM DDR3 Synchronous 1066 MHz (0.9 ns)
          product: HMT325S6BFR8C-H9
          vendor: Undefined
          physical id: 0
          serial: 2DC38EBE
          slot: A1_DIMM0
          size: 2GiB
          width: 64 bits
          clock: 1066MHz (0.9ns)
     *-bank:1
          description: DIMM Synchronous [empty]
          product: Array1_PartNumber1
          vendor: A1_Manufacturer1
          physical id: 1
          serial: A1_SerNum1
          slot: A1_DIMM1
          width: 64 bits
     *-bank:2
          description: DIMM DDR3 Synchronous 1066 MHz (0.9 ns)
          product: CMSO8GX3M1A1333C9
          vendor: Corsair
          physical id: 2
          serial: 00000000
          slot: A1_DIMM2
          size: 8GiB
          width: 64 bits
          clock: 1066MHz (0.9ns)
     *-bank:3
          description: DIMM Synchronous [empty]
          product: Array1_PartNumber3
          vendor: A1_Manufacturer3
          physical id: 3
          serial: A1_SerNum3
          slot: A1_DIMM3
          width: 64 bits
ej@ej-E7214:~$ 



ej@ej-E7214:~$ sudo lshw -C disk
[sudo] password for ej: 
  *-disk:0                
       description: ATA Disk
       product: WDC WD5000BEVT-0
       vendor: Western Digital
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 01.0
       serial: WD-WXF1A5019446
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000b8281
  *-cdrom
       description: DVD-RAM writer
       product: CDDVDW SN-S083C
       vendor: TSSTcorp
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: SB01
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
ej@ej-E7214:~$

---

### Post by daslinkard on 2012-07-11
Did you partition the 2nd hard drive to have Linux on it?

---

### Post by EJ42 on 2012-07-11
I tried a few variations but the only thing which seems to work is no partition under ext4 i.e. full drive with no partition
.
Anyway I have now been told that my machine only takes a maximum of 8GB of ram i.e. two slabs of 4GB each.

On one or two occasions I have fleetingly seen messages about segmentation faults, so I now think that having put a full 8GB into on bank plus the original 2GB in another is creating the contrary of what I originally intended.

I will now take out the 8GB slab only leaving the 2GB in. If that works I shall purchase two slabs of 4GB.

I must be able to back-up my whole system again before we start from scratch.

---

### Post by EJ42 on 2012-07-11
Yes!!!

Taking out the 8GB slab returned everything to normal. I could back-up my Home directory to the new HD without a glitch.

Vindicates the old adage that too much of a good thing can have nasty side effects.

But once bitten twice shy: I will now purchase the 2 x 4GB I should have in the first place and then we go back to the shutdown problem i.e. re-install the whole thing.

Thanks for staying with me. Have a nice day.

---

### Post by daslinkard on 2012-07-26
I just wanted to follow up with you to see how everything is going with your shutdown issues.

---

### Post by EJ42 on 2012-07-27
Well, having backed-up the totality of my home account I then re-installed 12.04 from a CD with the ISO image. I then had to upgrade 319 changes which had accumulated.

At long last it seemed to work but then again bingo the problem came back. Since it is intermittent I suspect a combination of programs being run either in a certain order or concurrently. I also suspect data downloaded from the Net but which one? I am not talking here about viruses, etc... . I do not download movies or other such things, just browsing newspapers and blogs from Europe and the US one page at a time.

In between I have installed 8GB of ram which is the maximum allowed by my machine and since then the problem has not shown up, but I am still testing.

PS: Immediately before re-installing I had a look at my system files and some of them were corrupt. Could that have been it? The machine was working normally apart from the shut-down problem. So the corrupt files may just have been logs or other unimportant ones.

---

### Post by EJ42 on 2012-07-27
Sorry!

Friday 27 July 18:38 (6:37pm) Eastern Australia time.

It has happened again.

Have been downloading some free TV shows and simultaneously watching them using MPlayer. Also copied some files from one HD to another.

Clicked on shut-down, worked, two seconds later came back on.

Could it be that shut-down becomes restart under some circumstances. Any idea where the shut-down code resides?

---

