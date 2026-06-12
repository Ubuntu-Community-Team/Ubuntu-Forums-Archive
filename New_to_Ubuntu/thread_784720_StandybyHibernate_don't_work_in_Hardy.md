---
title: "Standyby/Hibernate don't work in Hardy"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by gkrules on 2008-05-06
I upgraded to Hardy Heron a few days ago. Whenever i try to standby or hibernate the system starts a terminal and the terminal just stays there forever...ive had it stuck at that terminal screen for over 8 hours before. I used Gutsy Gibbon and the standby and hibernate modes worked fine. Im dual-booting with Windows Vista and the standby and hibernate works fine in it. 
Specs:
Compaq Presario F756NR 
1.9 ghz AMD Dual Core 
nVidia GeForce 7000M/nForce 610m
Atheros AR5007 wireless
conexant HD audio


would it be one of those thats stopping it from doing it?
or is it just one of the bugs in hardy

---

### Post by glennric on 2008-05-06
Do you have uswsusp installed?  

Also, could you post the output of 
```
cat /var/log/pm-suspend.log
```

---

### Post by gkrules on 2008-05-06
> **glennric said:**
> Do you have uswsusp installed?  

Also, could you post the output of 
```
cat /var/log/pm-suspend.log
```

i have no idea wat uswsusp is so unless it comes preinstalled
i probably dont have it



and here's the output
```
Tue May  6 18:41:39 EDT 2008: running suspend hooks.
===== Tue May  6 18:41:39 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/00clear =====
===== Tue May  6 18:41:39 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/05led =====
===== Tue May  6 18:41:39 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/10NetworkManager =====
===== Tue May  6 18:41:39 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/20video =====
kernel.acpi_video_flags = 0
===== Tue May  6 18:41:39 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/49bluetooth =====
===== Tue May  6 18:41:39 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/50modules =====
/usr/lib/pm-utils/functions: line 200: 22950 Segmentation fault      modprobe -r $1
# could not unload 'ath_pci', usage count was 0

```


im guessing its a problem with ath_pci which is my wireless card
im using madwifi.

---

### Post by gkrules on 2008-05-06
ok i tried to install that uswsusp but when i try to configure it i get 
```
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for LIBPCI... no
checking for pci_init in -lpci... no
checking for pci_init in -lpci... no
configure: error: Required pciutils >= 2.2.4 not found

```


i already have uswsusp 0.6 so i was trying to update it...the ubuntu repositories havnt updated it yet so i had to do it manually
i get this error message in uswsusp 0.6:
```
bob@bob-laptop:~/suspend-0.8$ sudo s2disk
s2disk: Could not stat the resume device file. Reason: No such file or directory
bob@bob-laptop:~/suspend-0.8$ sudo s2ram
sudo: s2ram: command not found

```

---

### Post by spuck on 2008-05-08
Can't hibernate either, not exactly the same though. I have to power down my PC manually, and when starting up again sometimes it doesn't start up like I left it but just like a regular boot and sometimes my ps/2 keyboard doesn't even work (so I have to do 2 restarts usually).

Oh and I get a nice popup that says "Sleep Failed". :)

```
spuck@PC:~/XBMC$ cat /var/log/pm-suspend.log
Thu May  8 01:02:50 CEST 2008: running hibernate hooks.
===== Thu May  8 01:02:50 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/00clear =====
===== Thu May  8 01:02:50 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/05led =====
===== Thu May  8 01:02:50 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/10NetworkManager =====
===== Thu May  8 01:02:50 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/20video =====
===== Thu May  8 01:02:50 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/49bluetooth =====
===== Thu May  8 01:02:50 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/50modules =====
===== Thu May  8 01:02:51 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/90clock =====
===== Thu May  8 01:02:52 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/94cpufreq =====
===== Thu May  8 01:02:52 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/95led =====
===== Thu May  8 01:02:52 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/99video =====
Thu May  8 01:02:52 CEST 2008: done running hibernate hooks.
/usr/lib/pm-utils/functions: line 161: echo: write error: Invalid argument
Thu May  8 10:32:50 CEST 2008: running thaw hooks.
===== Thu May  8 10:32:50 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/99video =====
===== Thu May  8 10:32:50 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/95led =====
===== Thu May  8 10:32:50 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/94cpufreq =====
===== Thu May  8 10:32:50 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/90clock =====
===== Thu May  8 10:32:51 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/50modules =====
 * Reconfiguring network interfaces...
Ignoring unknown interface eth0=eth0.
   ...done.
===== Thu May  8 10:32:52 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/49bluetooth =====
===== Thu May  8 10:32:52 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/20video =====
===== Thu May  8 10:32:52 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/10NetworkManager =====
===== Thu May  8 10:32:52 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/05led =====
===== Thu May  8 10:32:52 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/00clear =====
Thu May  8 10:32:52 CEST 2008: done running thaw hooks.

```

---

### Post by glennric on 2008-05-08
> **gkrules said:**
> i have no idea wat uswsusp is so unless it comes preinstalled
i probably dont have it
Actually, I was going to tell you to uninstall it if you had it.  You shouldn't need a newer version of that than is in the repositories if you are going to use it.  


> **gkrules said:**
> 
and here's the output
```
Tue May  6 18:41:39 EDT 2008: running suspend hooks.
===== Tue May  6 18:41:39 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/00clear =====
===== Tue May  6 18:41:39 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/05led =====
===== Tue May  6 18:41:39 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/10NetworkManager =====
===== Tue May  6 18:41:39 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/20video =====
kernel.acpi_video_flags = 0
===== Tue May  6 18:41:39 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/49bluetooth =====
===== Tue May  6 18:41:39 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/50modules =====
/usr/lib/pm-utils/functions: line 200: 22950 Segmentation fault      modprobe -r $1
# could not unload 'ath_pci', usage count was 0

```


im guessing its a problem with ath_pci which is my wireless card
im using madwifi.
Yeah, it looks like a problem with the ath_pci card.  Hmm, I am not sure how to deal with this in Hardy yet.

---

### Post by Sinkingships7 on 2008-05-08
[QUOTE=gkrules;4898769]ok i tried to install that uswsusp but when i try to configure it i get 
```
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for LIBPCI... no
checking for pci_init in -lpci... no
checking for pci_init in -lpci... no
configure: error: Required pciutils >= 2.2.4 not found

```


 I think the reason for this error is that you don't have the proper compiling tools installed.
```
sudo apt-get install build-essential
```

---

### Post by glennric on 2008-05-08
spook:  Can you post the output of 
```
cat /sys/power/disk
```

---

### Post by OldTimeTech on 2008-05-08
I would of said you need to install pciutils, either by using synaptic or terminal.

---

### Post by spuck on 2008-05-08
> **glennric said:**
> spook:  Can you post the output of 
```
cat /sys/power/disk
```

okay?

```
spuck@PC:~$ cat /sys/power/disk
test testproc [shutdown] reboot 
```

---

### Post by MadsRH on 2008-05-08
I have the same problem! (Do I have to start my own thread?)

I get this from:
```
cat /sys/power/disk
[platform] test testproc shutdown reboot
```

---

### Post by gkrules on 2008-05-08
i getthe same as spuck and mads for 
cat /sys/power/disk

do u guys have atheros wireless cards too?

---

### Post by MadsRH on 2008-05-08
> **gkrules said:**
> do u guys have atheros wireless cards too?
[B]
Yes!!![/B] Can that be it?

---

### Post by gkrules on 2008-05-08
yea the atheros card is wats stopping me from hibernating

---

### Post by gkrules on 2008-05-08
the other dudes having trouble
put this in terminal

cat /var/log/pm-suspend.log

post the result of that
im pretty sure both of u will get "# could not unload 'ath_pci'"
we need a way to get ath_pci to unload

---

### Post by glennric on 2008-05-08
I came up with a method that might help those of you with the ath_pci problem.  I was getting a similar error in /var/log/pm-suspend.log from a different wireless card, although it was still suspending and resuming ok.  This took that error away for me at least.  

First I need to know if those wireless cards are pcmcia cards or just pci cards.

---

### Post by glennric on 2008-05-08
Spuck:  You are having a different problem.  Notice that your output of "cat /sys/power/disk" does not have "platform" listed, and in your /var/log/pm-suspend.log you have something about an error on line 162 of /usr/lib/pm-utils/functions.  Well that line does the following
```
echo -n "platform" > /sys/power/disk
```
This gives an error because your hardware does not support that type of acpi shutdown method.  Either that or you have somehow disabled it, check your bios.
If you don't see anything in your bios you could try editing /usr/lib/pm-utils/functions and changing platform to shutdown.  Not sure if that will work though.

---

### Post by gkrules on 2008-05-08
i have no idea....its builtin on a laptop

i have an Atheros AR5007 
i dont kno if that helps or not..

---

### Post by glennric on 2008-05-08
Post the output of 
```
pccardctl ls
```

---

### Post by gkrules on 2008-05-08
i get nothing it jus goes back to 
gkrules@gkrules-laptop: ~$

---

### Post by glennric on 2008-05-08
Then it must not be a pcmcia card.  Hmm, the script I made won't work directly for you, but we may be able to modify it to make it work.  Post the output of "lspci"

---

### Post by gkrules on 2008-05-08
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

---

### Post by glennric on 2008-05-08
Are you currently accessing the internet via that wireless card?
If not try to run
```
sudo rmmod ath_pci
```
and see what the output of that is.

---

### Post by glennric on 2008-05-08
Also post the output of 
```
modinfo ath_pci
```

---

### Post by gkrules on 2008-05-08
modinfo ath_pci

filename:       /lib/modules/2.6.24-16-generic/net/ath_pci.ko
license:        Dual BSD/GPL
version:        trunk
description:    Support for Atheros 802.11 wireless LAN cards.
author:         Errno Consulting, Sam Leffler
srcversion:     EF5714FF89F840AB57EB838
alias:          pci:v0000168Cd00009013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000101Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
depends:        ath_hal,wlan
vermagic:       2.6.24-16-generic SMP mod_unload 586 
parm:           beacon_cal:int
parm:           countrycode:Override default country code (int)
parm:           maxvaps:Maximum VAPs (int)
parm:           outdoor:Enable/disable outdoor use (int)
parm:           xchanmode:Enable/disable extended channel mode (int)
parm:           rfkill:Enable/disable RFKILL capability (int)
parm:           tpc:Enable/disable per-packet transmit power control (TPC) capability (int)
parm:           autocreate:Create ath device in [sta|ap|wds|adhoc|ahdemo|monitor] mode. defaults to sta, use 'none' to disable (charp)
parm:           ratectl:Rate control algorithm [amrr|minstrel|onoe|sample], defaults to 'sample' (charp)
parm:           ath_debug:Load-time driver debug output enable (int)
parm:           ieee80211_debug:Load-time 802.11 debug output enable (int)

---

### Post by gkrules on 2008-05-08
and that first one

im using the wireless card and rm deletes stuff so i cant do that one

---

### Post by glennric on 2008-05-08
rmmod doesn't actually delete anything.  It unloads modules.  The reason I asked if you are using that wireless card to access the internet is because it will cut your internet connection if that command succeeds.  You would have to modprobe the module back in and restart networking to get it back (or reboot).

---

### Post by glennric on 2008-05-08
I am not really sure how to help you.  Your wireless card is a pci express card.  The problem seems to be that when the suspend and hibernate scripts try to rmmod the modules for your network card it fails and a segmentation fault ensues.  This may be happening at the time it tries to unload the ath_pci module or when it tries to unload something later that depends on it.  You could try submitting a bug.

---

### Post by gkrules on 2008-05-08
oh i see
i tried the rmmod thing
after i did that...suspend and hibernate both work....
is there a way to create a launcher that will automatically rmmod it and then suspend the computer?

---

### Post by glennric on 2008-05-08
Yes, that is what I was trying to get at.
So when you did the rmmod thing did it say anything, or just do it?

---

### Post by gkrules on 2008-05-08
it just did it
a line came up in terminal and then gkrules@gkrules-laptop came up
and then i tried to hibernate and it worked

---

### Post by glennric on 2008-05-08
Create a script in /etc/pm/sleep.d (name it whatever you want but make sure the name starts with the number 49) with the contents:
```
#!/bin/bash

case "$1" in
	hibernate|suspend)
		rmmod ath_pci
		;;
	thaw|resume)
                modprobe ath_pci
                invoke-rc.d networking restart
		;;
	*)
		;;
esac

exit $?
```

This is our first try at least.

---

### Post by spuck on 2008-05-08
> **glennric said:**
> Spuck:  You are having a different problem.  Notice that your output of "cat /sys/power/disk" does not have "platform" listed, and in your /var/log/pm-suspend.log you have something about an error on line 162 of /usr/lib/pm-utils/functions.  Well that line does the following
```
echo -n "platform" > /sys/power/disk
```
This gives an error because your hardware does not support that type of acpi shutdown method.  Either that or you have somehow disabled it, check your bios.
If you don't see anything in your bios you could try editing /usr/lib/pm-utils/functions and changing platform to shutdown.  Not sure if that will work though.

I added acpi=off in the boot options too be able too boot (and install) ubuntu but that's about it S3 is enabled in bios.
That probably has something to do with it but I don't see why ubuntu wants me to turn off my PC manually each time I wanna shut down my PC. 

And where do I find this standby button? There's only a hibernate but I'd be fine with standby, if my PC weren't so damn noisy I'd just leave it on. :(

---

### Post by glennric on 2008-05-08
If you have added acpi=off to your kernel parameters then you won't be able to use the suspend and hibernation features.  Those use acpi.

It is possible that you may be able to use them if you install uswsusp.  If that is installed you won't be using the scripts.  It will default to the s2disk program included in that package.

---

### Post by gkrules on 2008-05-08
hmmm that worked but two things:
hibernating took about 1min 30sec 
booting up from hibernation took 2min

and after i logged back on 7% of my swap was used... i hav 4 gigs of ram so swap is rarely used... does it just go back to 0% after a reboot? or do i hav to format it again?



oo and when i booted up my wireless was working fine...i didnt have to do the modprobe thing


EDIT: i had to install my video driver again after i came back from hibernation
i dont know if this is because of the script or because of something else

---

### Post by glennric on 2008-05-08
When you hibernate your memory is saved to your swap partition.  It may have left some stuff there.  It will pull it out as it needs it.

---

### Post by glennric on 2008-05-08
As to the slow time it takes to hibernate and resume...well unfortunately linux has some things to iron out in that respect.  It does take to long.  

You shouldn't have to do the modprobe thing at all, the script should take care of that.

---

### Post by gkrules on 2008-05-08
oh well its good enough for me anyway 
i might try to tweak it a lil once i get better with linux
but for now its fine i guess
thanks for everything

---

### Post by MadsRH on 2008-05-09
I get this:

filename:       /lib/modules/2.6.24-16-generic/madwifi/ath_pci.ko
license:        Dual BSD/GPL
version:        0.9.4
description:    Support for Atheros 802.11 wireless LAN cards.
author:         Errno Consulting, Sam Leffler
srcversion:     D3FD3BD11169A96DBCFF8DE
alias:          pci:v0000168Cd00009013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000101Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
depends:        ath_hal,wlan
vermagic:       2.6.24-16-generic SMP mod_unload 586 
parm:           countrycode:Override default country code (int)
parm:           maxvaps:Maximum VAPs (int)
parm:           outdoor:Enable/disable outdoor use (int)
parm:           xchanmode:Enable/disable extended channel mode (int)
parm:           rfkill:Enable/disable RFKILL capability (int)
parm:           autocreate:Create ath device in [sta|ap|wds|adhoc|ahdemo|monitor] mode. defaults to sta, use 'none' to disable (charp)
parm:           ratectl:Rate control algorithm [amrr|minstrel|onoe|sample], defaults to 'sample' (charp)
parm:           ath_debug:Load-time debug output enable (int)

---

### Post by drlisacuddy on 2008-05-09
Hi, i tried your suspend script, put it in sleep.d, but the computer still doesn't suspend :( Any ideas? I have the Atheros 5007 chipset and it has the same problem.

---

### Post by gkrules on 2008-05-09
make sure wen u save the script...make the beginning of the file name 49
like 49suspendscript

---

### Post by voltaire99 on 2008-05-16
I have the same problem due to the Atheros card.  Did anyone ever create a script of some other fix for this?

---

### Post by Geek2theCore on 2009-03-20
I'll add another interesting twist to this. I have a Toshiba M60, and it exhibits all the same "features" (successful suspend resume, unhelpful failure message), the pm-suspend.log is completely clean, with no sign of an error, but mine returns with a squeal through the laptop speakers at full volume, like a feedback loop. If I don't turn down the speakers before I resume in the morning, it's enough to wake the dead. But other than the error message and squeal there is no failure of any device on resume. I can instantly use anything, including sound.

I'm on Hardy 8.04.1

---

