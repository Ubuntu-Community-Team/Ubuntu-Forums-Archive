---
title: "new single install 12.10 not booting"
date: 2013-03-27
forum: New to Ubuntu
---

### Post by okkie on 2013-03-27
I installed 12.10 on a formatted 1t hard disk.
intel system
1024 memory
system will not boot Changed BIOS to boot from hard disk and back to CD, no go
Put original CD back to try and boot, re-install is offered.Done re-install,same problem.
System is loaded,just won't boot.
Also tried 'try ubuntu' , no go

Any help welcome please

---

### Post by Bashing-om on 2013-03-27
okkie' Hi !

Have you tried any of the preset boot options in ubuntu's "try" mode (purple screen,hit any key, escape) ?[INDENT=3]
hth

[/INDENT]

---

### Post by okkie on 2013-03-28
No go. The only funny thing I notice at start up is the computer does not do the normal memory test and I was wondering if GRUB might have anything to do with the problem?
Sutely if you install from a disk it must boot. Is it a system problem?

---

### Post by Bashing-om on 2013-03-28
okkie; Now-a-days things have gotten more complex with booting issues. Many times it is a UEFI or Intel Smart Response Technology - dual boot issue.
Was Windows installed/still installed ?
Did you verify the md5sum of the .iso file ?
The hard disks ever part of a "raid array" ?
How is the hard disk partitioned // MBR or GPT ? MBR can only have 4 primary partitions per disk.
Can you boot the install medium to the boot screen and choose the option to verify the installed medium's integrity ?
[INDENT=3]
where there is a will there is a way

[/INDENT]

---

### Post by okkie on 2013-03-29
I like your last sentence.My grand children are having serious issues understanding what it means.Makes one wonder how modern we can still become.
I went to a site and read about the booting complexities you are referring to. way beyond me so thanks for your help.I'm just an old UBUNTU fan for years now and would like an up and running trouble free system just for once.

windows was originally installed on the computer.Like all desktops I suppose.I removed the hard disk which was to small And formatted my 1t disk which was previously used as a slave on my other computer which has windows and Ubuntu 12.10 loaded.My wife needs windows and I am afraid to do my Ubuntu stuff as updates have screwed up everything time and again in the past and we need windows to make a living.Not to mention a lifetime's photos and music also gone.
The .iso file I used is a standard download from the official website and could be wrong.if you can refer me to a guarenteed correct download I will be glad to do that first.
I don't know if the 1t disk was ever exposed to a 'raid array' and like in the past I left partitioning etc. entirely to the installation disk. All I know for certain is the installation is done.Maybe the wrong one, but the hope is in place!

---

### Post by okkie on 2013-03-29
here is some more info:
I inserted the disk and waited till it offered me the try/install menu again,clicked install and then from the next menu selected 'something else' and got the following
/dev/sda
/dev/sda 1          ext 4            999397MB             19188 Used
/dev/sda 5          swap                 803 MB              nil used
At the bottom it gives 'device for boot loader installation
/dev/sda     ATA  ST31000528  AS [1.0 TB]
The option is /dev/sda 1  Ubuntu  12.10[12.10]
If I select that and click install itsays 'no root file system is defined, please correct this from the partitioning menu.......
I was just thinking whether this could not solve the boot problem?

---

### Post by Bashing-om on 2013-03-29
okkie;

Seems that your install medium is good.
For a standard installation grub -GRand Unified Bootloader - is installed to "sda" NOT sda1 (sda1 done for a particular purpose not relevant in this instance).
I find that 85% + of install problems are graphics (driver) related. Let's get you installed. As you want it trouble free for an extended period of time, Let's go with 12.04 as it is Long Term Support - 5 years. We are going to do the "try ubuntu" mode first and see if all your hardware works with 12.04, see what it is going to take in this test environment to get the real install working,

Small steps to make a leap forward:
Boot the install cd (bios set to CD as 1st boot priority).
At the purple splash screen (stick figure keyboard emblems at bottom of screen) -> hit any key ->
Language screen -> escape key to accept the default ->
Booting options screen -> f6 key (other options) -> arrow down to the preset option(s) space or enter to accept and then the escape key to exit; in your present case I want you to use "nomodeset" only./Additional info -> For other additions the boot options kernel boot line is now available, append any desired boot parameter to the end of the line(only if needed in that the presets are ineffective).

Enter key to continue the boot process to the GUI desk top;

Clear as mud ? Do you boot to the GUI ? If so, I will advise further on installing a graphics driver in this test situation that will be applied in the real install.[INDENT=2]
just try'n to help

[/INDENT]

---

### Post by okkie on 2013-03-30
I got as far as and marked 'nomodeset'. The menu then offers try ubuntu,install ubuntu, check disk, test memory and boot from hard disk.
as I scroll down the boot options line becomes available when I reach 'test memory'. I am not sure if I must then enter /additional infoon te line or something else. please clear this up for me.

---

### Post by Bashing-om on 2013-03-30
okkie;
The many options available are admittedly confusing. Let's stick to the one in that you are trying to boot up ubuntu to a graphical desktop.
At that purple screen depressing any key should result in a language screen, depressing the escape key should next see the boot options screen, the options we are presently interested in is obtained through the f6 key. Choosing "nomodeset" at this menu tells ubuntu to boot with out "kernel mode setting" (KMS) using the on-board graphics driver "vesa".//If this works to get you to a GUI, then we can look at loading an appropriate driver.  Doing so in the "try Ubuntu" mode tells us what must be done in the real install. In this "try ubuntu" mode nothing in the system its' self is touched, all is done in ram.
 
In the event that you still experience problems, I will boot up the installCD and verify a step-by-step procedure to boot up with that option.[INDENT=3]
first things first

[/INDENT]

---

### Post by okkie on 2013-03-31
Thanks for replying.
Don't ask me the sequence, but I carefully went through the steps again as best I could and 'eureca' try Ubuntu is booted. on the desktop only examples and install Ubuntu 12.10 icons.
Your wish from here is my command

---

### Post by Bashing-om on 2013-03-31
okkie;

Making progress ! Now for that leap forward; ( I strongly advise install 12.04 for long term stability) in the "try ubuntu" mode: booted to the desk top (12.10 version)-> left side of the screen is the "launcher" -> select " System Setting" ->in the task bar at the top of the screen -> Software Sources -> Additional Drivers (tab in software sources) --> install the recommended driver. Done with this stage. At this time play with ubuntu and check all your devices, that all works.

All is good ?? -> prepare to install -> 

At the initial install screen are check boxes for 3rd party sofware, I recommend checking them to accept the proprietary software that ubuntu can not offer. That will install the needed graphics drivers and music/video codecs. 
  ... now is the choice ///let the install wizard do all the install with a minimum amount of intercession on your part ( just the basic questions to establish a location and user account) OR manually set up the install. Manual install can be confusing the first couple of times one goes through it and most easily done with prior set up using GParted( as opposed to the installer's partitioner, that can also be used) to set up the partitions. That takes an awareness on your part as to how you intend to use your system. I will say this in advisement: a separate partition for /home can have its advantages, partition for "/" (which is "root") and partitions for data ...maybe separate for Windows (sharing) or dedicated for ubuntu partitions would be good things.

By far the simplest install is to choose to install ubuntu as the only operating system and "use the entire disk" The draw back to this is that you have 1TB size disk and the basic install will not make maximum use of it ...the installed operating system is but about 5 gigs. The good thing is that you may want to go ahead and do the simple install, get the hang of the new system and at a later time (re-)install ubuntu as you have found how you use the system and then partition accordingly.

The choice is yours, how now may I help?

---

### Post by okkie on 2013-04-01
additional drivers is blank.No recommended drivers
I have by the way got a 12.04 iso on CD but the machine failed to read it in the past.JUst mentioning it.

---

### Post by Bashing-om on 2013-04-01
okkie;

I am back. That - there are no additional drivers available- indicates you are perhaps running an old graphics card  that may no longer be supported. Let's look and see what we are working with.
Boot up the live cd to the desk top and activate a terminal with the key combo ctl+alt+t.
To see your graphics card and info;
Post the output of terminal codes:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga
```
And by the way, as it may relate to bios, what version of Windows did the machine come with ?[INDENT]
one step at a time and we will get there

[/INDENT]

---

### Post by okkie on 2013-04-02
Hi Bash,Itrust this is whatn you are after.Just before grep in the second line there is a straightup line which the computer will not give me.I used forward slash and the machine put in the back slash.Might not be the desired result.Funny but the computer is suddenly extremely sluggish. 

ubuntu@ubuntu:~$ sudo lshw -^C
ubuntu@ubuntu:~$ sudo lshw -c display
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: NV34 [GeForce FX 5200]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
       configuration: latency=32 maxlatency=1 mingnt=5
       resources: memory:ec000000-ecffffff memory:e0000000-e7ffffff memory:ed000000-ed01ffff
ubuntu@ubuntu:~$ lspci -nnk \ grep -ia3 vga
Usage: lspci [<switches>]

Basic display modes:
-mm		Produce machine-readable output (single -m for an obsolete format)
-t		Show bus tree

Display options:
-v		Be verbose (-vv for very verbose)
-k		Show kernel drivers handling each device
-x		Show hex-dump of the standard part of the config space
-xxx		Show hex-dump of the whole config space (dangerous; root only)
-xxxx		Show hex-dump of the 4096-byte extended config space (root only)
-b		Bus-centric view (addresses and IRQ's as seen by the bus)
-D		Always show domain numbers

Resolving of device ID's to names:
-n		Show numeric ID's
-nn		Show both textual and numeric ID's (names & numbers)
-q		Query the PCI ID database for unknown ID's via DNS
-qq		As above, but re-query locally cached entries
-Q		Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]	Show only devices in selected slots
-d [<vendor>]:[<device>]			Show only devices with specified ID's

Other options:
-i <file>	Use specified ID database instead of a3
-p <file>	Look up kernel modules in a given file instead of default modules.pcimap
-M		Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>	Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>	Set PCI access parameter (see `-O help' for a list)
-G		Enable PCI access debugging
-H <mode>	Use direct hardware access (<mode> = 1 or 2)
-F <file>	Read PCI configuration dump from a given file
ubuntu@ubuntu:~$

---

### Post by okkie on 2013-04-02
previous install was windows xp

---

### Post by mörgæs on 2013-04-02
UEFI is not a problem here, but the graphics card is somewhat old. 

Don't try to put Ubuntu on this computer, but Lubuntu 12.10 will work fine. Best is to begin with only open-source graphics drivers.

---

### Post by Bashing-om on 2013-04-02
+1 ... 
> 
ubuntu@ubuntu:~$ sudo lshw -^C
ubuntu@ubuntu:~$ sudo lshw -c display
  *-display UNCLAIMED means no graphics driver is loaded.

You will be much happier with a lighter version of 'buntu.[INDENT=2]
just my thoughts

[/INDENT]

---

### Post by d0006 on 2013-04-02
> **okkie said:**
> Hi Bash,Itrust this is whatn you are after.Just before grep in the second line there is a straightup line which the computer will not give me.

Try **SHIFT-backslash** for the pipe symbol ( straightup line).  On many keyboards this looks like two small vertical lines on top of each other. When you print it it looks like one vertical line (the pipe).

---

### Post by okkie on 2013-04-03
Thanks to all. Like everybody I want this computer to work right as it is the last one in my lifetime.I will go out today and find the best graphics card I can afford if one is available and report back

---

### Post by mörgæs on 2013-04-03
If you are planning on only standard use (office applications and the like, not playing heavy games) your present card will work fine. No need for spending money.

---

### Post by okkie on 2013-04-03
well gentlemen, after all this suffering I went to a shop to find out you cannot get graphic cards anymore. I then went to a second hand shop to see if I cannot pick up something there, explained my problem and was told of somebody who is selling everything before emigrating. Got there and bought a two year old all SATA computer and Flat screen for If I do the conversion, around $75. Jackpot.
I installed Ubuntu 12.10 in a few minutes and everything is perfect.
I suppose this problem is now solved and will mark it accordingly.
Thanks again for all the help.



                                                                                       SOLVED

---

