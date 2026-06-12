---
title: "Computer crashes after bootup after attempting to install a wifi card"
date: 2013-07-11
forum: New to Ubuntu
---

### Post by JohnCarlson on 2013-07-11
I attempted to install a new trendnet wireless pc card, since my previous card died.  I could not find a driver for Ubuntu linux 12.04 so found the win-wrapper solution and attempted to install that.  Win-wrapper appeared to install ok, but when I added the driver it gave me an error.  I then tried a usb wifi adapter and it was automatically recognized and worked.  When I restarted my computer however, Now my computer is crashing shortly after bootup.  
Evidently this process corrupted something.
Here is the series of messages that pop up shortly after booting up:
"A volume of software packages has been detected"
"Would you like to open it with the package manager?"  I click on "start package manager"
"Enter password"  I enter password
"Unable to get exclusive lock - this usually means that another package management app (like apt-get or aptitude) is already running.  Please close that app first."  I click on the close button for this dialog
"software index is broken, run synaptic"

The computer crashes and goes to a text screen somewhere in this process, or if I just wait after booting up, it crashes anyway and goes to a screen dump.  The only thing I can read that's intelligible to me is "modprobe tainted"

I really need help getting my computer stable so I can use it again.

---

### Post by sudodus on 2013-07-12
Welcome to the Ubuntu Forums :-)

Have you removed the new trendnet wireless pc card?

Are you you prepared to continue in the text screen, maybe with some help from the community?

Do you remember or can you get the information from some error output, what is the offending package?

You can run

```
 sudo apt-get remove packagename
```

to remove a package with the name 'packagename'.

You can also try several commands one after another, but you must tell us where to start, to get instructions that fit your experience with the linux command line.

---

### Post by JohnCarlson on 2013-07-12
Well, this is difficult reporting the screen dump because it doesn't  appear that I can copy and paste the contents, put it on a memory card,  transfer it to my wife's working computer to get online and post it.  It  also doesn't seem like I can print the screen to my printer.  Print  Screen doesn't seem to work.  And my computer crashes long before I'm  able to go online.  Is there a way to create a report file/copy a report  file from the screen dump when my computer crashes? Maybe I could copy a  file to a usb device before crashing, that would make this a lot easier  than typing it all in by reading the screen and retyping everything  here.  But I can do that if there isn't a faster way.  Any ideas?
The first couple lines after ----cut here---- are:
[762.975121] kernel BUG at include/net/cfg80211.h:2209!
[762.975136] invalid opcode: 0000 [#1] SMP

---

### Post by JohnCarlson on 2013-07-12
Ok, I managed to copy these files from /var/log onto my usb memory stick right before crashing again.  What is the most useful for troubleshooting?  I can now copy and paste any of this information from this computer.
dpkg.log
syslog
Xorg.0.log
auth.log
kern.log
pm-powersave.log
wtmp
udev
dmesg
boot.log
Xorg.0.log.old
dmesg.0
dmesg.1.gz

---

### Post by wildmanne39 on 2013-07-12
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by sudodus on 2013-07-13
I'm not good at reading log files. [COLOR=#ff0000]I hope someone who knows what to look for is reading this and can help solve this problem.[/COLOR]

-o-

Have you removed the new trendnet wireless pc card?

Can you boot from an Ubuntu install CD/DVD/USB drive (boot a live session without installing anything)?

---

### Post by JohnCarlson on 2013-07-13
Yes, I pulled that card out as soon as I realized it wasn't going to work.  I don't have a cd or dvd writer, and I saw on the forums that I might be able to boot to a usb drive, so I bought a new flash drive, downloaded the iso file and made it bootable.  I changed my bios to boot from it, but for some reason I could not boot from it.

I am sorry for not knowing exactly what to give you for information.  I'm not new to computers, but my skills are probably dangerous, and I'm completely new to Linux.  I got this laptop second hand and it already had Ubuntu Linux on it.  I upgraded it to 12.04 about a month or so ago and it seemed to be going fine until I tried to install this ndis-wrapper and wifi card (sorry I mispoke before, stating "win-wrapper")  Anyway, I don't understand Linux yet, and I'm sure I created this problem by not understanding what I was doing, trying to follow posted information to install that card, and to fix my problem once it started, so I hope you have patience.  I'll try to provide whatever I can to help someone help me.  Thanks in advance!

---

### Post by gnometorule on 2013-07-13
> **JohnCarlson said:**
> ...so I bought a new flash drive, downloaded the iso file and made it bootable.  I changed my bios to boot from it, but for some reason I could not boot from it.

This sounds suspicious. You haven't mentioned your system yet and should add system information (If I didn't miss this). You should also add if your laptop has only Ubuntu installed, or if you dual boot (using Grub? Grub2?). 

While I (fortunately) have not yet had to deal with UEFI boots under Ubuntu (or Windows, for the matter), failing to boot a live USB sounds as if you work maybe under a UEFI motherboard, using a pre-UEFI bootable USB. In this case, I just know that there are issues, and steps to take first. Here is a sample link about what to do, which doesn't necessarily help you: [http://ubuntuforums.org/showthread.php?t=2111720](http://ubuntuforums.org/showthread.php?t=2111720). You should then also consider to read the wikipedia entry about UEFI. I think before you do anything else, you'll need clarity about this, and get the live USB to work because if you can't even do that, installing/uninstalling drivers and hardware is going to be a challenge. As I haven't had to deal with such issues, I won't be of any help, but you might update the name of your post to reflect the issue more precisely (If that's possible? I think it is - if not, consider asking a different question such as "Getting Ubuntu live USB to work on UEFI motherboard for (insert name and precise model of your computer)." 

Good luck!

---

### Post by varunendra on 2013-07-13
@ John,

It appears from your first post that perhaps you happened to have an update offered when you momentarily had connection. There was an installation in progress and you restarted it prematurely, causing the package-manager lock "Open". However, that should not cause the crashing issue.

I suspect that maybe you had a graphics driver being installed when you restarted. Either that driver wasn't properly installed or is having other issues (graphics drivers are the most common reasons for system crashes, but are not the only reasons).

When the system starts to boot (at the purple splash screen), can you access the grub menu by pressing a key (shift or Esc perhaps)? If you can, try booting into "recovery mode" (the second option in the grub menu). If you can boot into recovery mode (gui or text only, whatever possible), we can attempt to find the cause and cure it. Otherwise, I'm afraid your only 'sane' option is to just do a re-install.

---

### Post by JohnCarlson on 2013-07-13
I did a little more research and found commands to get computer  information from the recovery bootup prompt.  When I have more time  tonight I'll retype the screen dump information from when my computer  crashes.  And yes, I did respond to a prompt to upgrade to 12.04 and  said, why not?  After I did so I did have some screen glitches but have  been booting into Ubuntu 2d and haven't had any problems until trying to  install this wifi card.  I'm not trying to be suspicious about this.   It's technically challenging for me and frustrating to figure out how to  get the information needed to get to the bottom of this:
```

processor:  0
vendor_id:  GenuineIntel
cpu family: 6
model:       9
model name:  Intel(R) Pentium(R) M Processor 1400MHz
stepping:    5
microcode: 0x5
cpu MHz:  600.000
cache size: 1024kb
fdiv_bug:  no

Linux  version 3.2.0 -48-generic (buildd@lamiak) (gcc version 4.6.3 (Ubuntu  /LINARO 4.6.3-1ubuntu5) ) #74-Ubuntu SMP THU JUN 6 19:45:16 UTC 2013  John@john-laptop:~$

memtotal:  507584kb
memfree: 152404kb
buffers:  117016kb
cached: 143652kb
swapcached: 0kb
active: 98872kb
inactive: 191436kb
active(anon): 30296kb
inactive (anon): 192kb
active (file): 68576kb

swap partition:
filename       type       size        used     priority
/dev/sda5    partition  1253372   0          -1

lspci shows:
00:1d.1 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev81)
00:1f.0 ISA bridge: Intel Corporation 82801 DBM (ICH4-M) LPC Interface bridge (rev01)
00:1f.1 IDE interface: Intel Corporation 82801 DBM (ICH4-M) IDE Controller (rev01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801 DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: NVIDIA Corporation NV34M [GeForce FX Go5200 64M] (rev a1)
02:00.0 Ethernet controller Broadcom corporation BCM4401 100BASE-T (rev 01)
02:01.0 CARDBUS bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev02)
02:01.1 FireWire (ieee 1394): Texas Instruments PCI4510 IEEE-1394 Controller
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g wireless LAN Controller (rev02)

```

---

### Post by JohnCarlson on 2013-07-14
I retyped the screen dump that I get when my computer crashes:

```
>                                                             Ubuntu 12.04
                                                               . . . . * checking battery  state...                                                       
531.417239]  -----------cut  here---------                                                                                                                  [ok]
[531.417266] kernel BUG at  include/net/cfg80211.h:2209!                                                                                  [ok]
[531.417283] invalid opcode: 0000 [#1] SMP
[531.417300]  Modules linked in: wl(P+) cfg80211 lib80211 nls_utf8 isofs dm_crypt  snd_intel18x0 joydev snd_ac97_codec ac97_bus usblp snd_pcm snd_seq_midi  snd_rawmidi snd_seq_midi_event snd_seq dcdbas dm_multipath snd_timer  snd_seq_device psmouse snd soundcore serio_raw snd_page_alloc pcmcia  mac_hid bnep rfcomm parport_pc bluetooth ppdev yenta_socket pcmcia_rsrc  pcmcia_core binfmt_misc shpchp lp parport dm_raid45 xor dm_mirror  dm_region_hash dm_log nouveau ttm drm_kms_helper drm firewire_ohci  firewire_core crc_itu_t i2c_algo_bit mxm_wmi wmi video [last unloaded:  cfg80211]  [ok]

My screen blanked out while I was reading it, so I  had to reboot and let my computer crash again in order to read it.  It  appears the screen dump was all the same except the numbers to the left  in brackets changed:

[938.117012] 
[938.117021] Pid: 3637,  comm: modprobe Tainted: P    W  0 3.2.0-48-generic #74-Ubuntu Dell  Computer Corporation Inspiron 8600  /0P3490
[938.117061] EIP: 0060:[<elca0496>] EFLAGS: 00210246 CPU: 0
[938.117132] EIP is at wdev priv.part.7+0x3/0x5 [wl]
[938.117147] EAX: 00000000 EBX: dc685480 ECX: dc685480 EDX: dc997090
[938.117164] ESI: dc997090 EDI: dc99700c EBP: dd54cec ESP: dd545cec
[938.117182]  DS: 007b ES: 007b FS:00d8 GS: 00e0 ss: 0068
[938.117198] Process modprobe (pid: 3637, ti-dd544000 task=dd5a8000 task.ti=dd544000)
[938.117217] Stack:
[938.117225] dd545d00 e1c9f924 dc685480 dc997090 dc99700c dd545d14 e1c9857f dc997000
[938.117259] ddd1c800 dc685000 dd545dc0 e1c98f48 c104b6f5 00000000 ffffffbb 00000000
[938.117292] c191f5d3 dd545d7d dd545db0 00200246 dd545d6e c170e984 000003aa 0001c7d4
[938.117325] Call Trace:
[938.117385]  [<e1c9f924>] wl_cfg80211_detach+0xc4/0xd0 [wl]
[938.117450]  [<e1c9857f>] wl_free_if.isra.10+0x1f/0xa0 [wl]
[938.117513]  [<e1c98f48>] wl_free+0x58/0x250 [wl]
[938.117531]  [<c104b6f5>] ? console_trylock+0x15/0x60
[938.117583]  [<e1bb8e92>] ? wlc_attach+0xf6c/0xfda [wl]
[938.117647]  [<e1ca0409>] wl_pci_probe+0x51a/0x53a [wl]
[938.117668]  [<c157884d>] ? _raw_spin_lock_irqsave+0x2d/0x40
[938.117687]  [<c136ff55>]  ? pm_runtime_enable+0x45/0x70
[938.117706]  [<c12bfdb7>] local_pci_probe+0x47/0xb0
[938.117722]  [<c12c12b8>] pci_device_probe+0x68/0x90
[938.117739]  [<c1197787>] ? sysfs_create_link+0x17/0x20
[938.117757]  [<c1367c9d>] really_probe+0x4d/0x150
[938.117772]  [<c1371389>] ? pm_runtime_barrier+0x49/0xb0
[938.117789]  [<c1367eda>] driver_probe_device+0x3a/0x60
[938.117806]  [<c1367f91>] driver_attach+0x91/0xa0
[938.117821]  [<c1367f00>] ? driver_probe_device+0x60/0x60
[938.117838]  [<c1367011>] bus_for_each_dev+0x51/0x80
[938.117854]  [<c1367ad1>] driver_attach+0x21/0x30
[938.117869]  [<c1367f00>] ? driver_probe_device+0x60/0x60
[938.117886]  [<c13677af>] bus_add_driver+0x17f/0x260
[938.117902]  [<c12c12e0>] ? pci_device_probe+0x90/0x90
[938.117918]  [<c1368466>] driver_register+0x66/0x110
[938.117935]  [<c12c1062>] _pci_register_driver+0x42/0xc0
[938.117996]  [<e1811017>] wl_module_init+0x17/0x1000 [wl]
[938.118013]  [<c1001125>] do_one_initcall+0x35/0x170
[938.118027]  [<e1811000>] ? 0xe1810fff
[938.118045]  [<c108686c>] sys_init_module+0xac/0x210
[938.118060]  [<c1131d63>] ? sys_close+0x73/0xc0
[938.118075]  [<c15789f4>] syscall_call+0x7/0xb
[938.118075]  [<c1580000>] ?do_IRQ+0x10/0xc0
[938.118087]   Code: d0 e8 ef 82 8d df 89 f0 e8 78 8a ff ff 89 d8 e8 21 e8 61 df 31 d2  89 f8 e8 c8 74 6c df 58 5b 5e 5f 5d c3 55 89 ef 0f 0b 55 89 e5  <0f> 0b 55 89 e5 3e 8d 74 26 00 0f 0b 55 89 e5 3e 8d 74 26 00 0f
[938.118253] EIP: [<e1ca0496>] wdev_priv.part.7+0x3/0x5 [wl] SS:ESP 0068:dd545cec
[938.118253] [drm] nouveau 0000:01:00:0: Calling LVDS script 6:
[938.118411] [drm] nouveau 0000:01:00:0: 0xDE71: Parsing digital output script table
[938.118444] [drm] nouveau 0000:01:00:0: Calling LVDS Script 2:
[938.635295] [drm] nouveau 0000:01:00:0: 0xDF8E: Parsing digital output script table
[938.635326] [drm] nouveau 0000:01:00:0: Calling LVDS Script 5:
[938.683074] [drm] nouveau 0000:01:00:0: 0xDE5A: Parsing digital output script table
```

---

### Post by sudodus on 2013-07-14
> **JohnCarlson said:**
> I did a little more research and found commands to get computer  information from the recovery bootup prompt.  When I have more time  tonight I'll retype the screen dump information from when my computer  crashes.  And yes, I did respond to a prompt to upgrade to 12.04 and  said, why not?  After I did so I did have some screen glitches but have  been booting into Ubuntu 2d and haven't had any problems until trying to  install this wifi card.  I'm not trying to be suspicious about this.   It's technically challenging for me and frustrating to figure out how to  get the information needed to get to the bottom of this:
```

processor:  0
vendor_id:  GenuineIntel
cpu family: 6
model:       9
model name:  Intel(R) Pentium(R) M Processor 1400MHz
stepping:    5
microcode: 0x5
cpu MHz:  600.000
cache size: 1024kb
fdiv_bug:  no

Linux  version 3.2.0 -48-generic (buildd@lamiak) (gcc version 4.6.3 (Ubuntu  /LINARO 4.6.3-1ubuntu5) ) #74-Ubuntu SMP THU JUN 6 19:45:16 UTC 2013  John@john-laptop:~$

memtotal:  507584kb
memfree: 152404kb
buffers:  117016kb
cached: 143652kb
swapcached: 0kb
active: 98872kb
inactive: 191436kb
active(anon): 30296kb
inactive (anon): 192kb
active (file): 68576kb

swap partition:
filename       type       size        used     priority
/dev/sda5    partition  1253372   0          -1

lspci shows:
00:1d.1 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev81)
00:1f.0 ISA bridge: Intel Corporation 82801 DBM (ICH4-M) LPC Interface bridge (rev01)
00:1f.1 IDE interface: Intel Corporation 82801 DBM (ICH4-M) IDE Controller (rev01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801 DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: NVIDIA Corporation NV34M [GeForce FX Go5200 64M] (rev a1)
02:00.0 Ethernet controller Broadcom corporation BCM4401 100BASE-T (rev 01)
02:01.0 CARDBUS bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev02)
02:01.1 FireWire (ieee 1394): Texas Instruments PCI4510 IEEE-1394 Controller
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g wireless LAN Controller (rev02)

```
There are problems with some Pentium M CPUs, that new versions of Ubuntu need 'fake-PAE' to run, but it does not seem that you suffer from that problem. It is more likely, that you have problems with the nvidia graphics and/or the wireless chip.

---

### Post by sudodus on 2013-07-14
> **JohnCarlson said:**
> I retyped the screen dump that I get when my computer crashes:
```

[938.118253] [drm] nouveau 0000:01:00:0: Calling LVDS script 6:
[938.118411] [drm] nouveau 0000:01:00:0: 0xDE71: Parsing digital output script table
[938.118444] [drm] nouveau 0000:01:00:0: Calling LVDS Script 2:
[938.635295] [drm] nouveau 0000:01:00:0: 0xDF8E: Parsing digital output script table
[938.635326] [drm] nouveau 0000:01:00:0: Calling LVDS Script 5:
[938.683074] [drm] nouveau 0000:01:00:0: 0xDE5A: Parsing digital output script table
```

```
kernel BUG at  include/net/cfg80211.h:2209!
```

You seem to run or try to run with nouveau, which is the free version of driver for nvidia. It might work better if you install a proprietary driver. But on the other hand, it used to work before you installed the driver for the wifi device. 

What about the complaint about 'kernel BUG ... net ...'? I suspect that points to something you might try to remove.

---

### Post by JohnCarlson on 2013-07-14
> **sudodus said:**
> You seem to run or try to run with nouveau, which is the free version of driver for nvidia. It might work better if you install a proprietary driver. But on the other hand, it used to work before you installed the driver for the wifi device. 

What about the complaint about 'kernel BUG ... net ...'? I suspect that points to something you might try to remove.

Any idea what this is and how to remove it?  Is it a file I can rename or delete?

---

### Post by steeldriver on 2013-07-14
It's hard to follow the chain of events here

Did you have a working installation before you attempted to install the Trendnet card / ndiswrapper? Is the Broadcom device shown in your lsusb output the original device and have you previously been able to get a working connection using that?

Can you get to a terminal prompt (maybe a virtual terminal / console by hitting the Ctrl-Alt-F1 combination and logging in there)? If so you can try purging everything related to ndiswrapper. You can then maybe start from scratch and try to get either the Broadcom or the new Trendnet devices working with native Linux drivers - the exact procedure will depend on the precise chipset(s) and what version of Ubuntu you are running. If you can't get a virtual terminal then you may need to boot into recovery mode and work from there.

---

### Post by JohnCarlson on 2013-07-14
Here is the chain of events:
A few months ago I upgraded to Ubuntu 12.04.  I ran into video problems but discovered I could select Ubuntu 2d at the login screen and everything ran fine that way, so I went with it.

Last week my wifi card stopped working.  It was a ZyXEL 802.11b/g Wireless Cardbus Adapter G-102.  the power light was no longer blinking on it.  I assumed the card died.  My computer was still running fine at this point.

I went out and bought the only card available at a store near me.  A TRENDnetTEW-641pc.  I tried to find drivers for it, but could not.  I then saw the NDIS-Wrapper solution online and tried to install that.  That seemed to install ok and came up.  Then I tried to "Add" this new video card.  An error occurred and I tried several times.  Then I determined it wasn't going to work and I removed the driver from NDIS-Wrapper.  However somewhere during this process of trying to get the wireless running, my computer crashed.  I rebooted.  The computer began crashing and I began getting the error messages in dialog boxes that I posted at the beginning of this thread.  I probably corrupted something mucking around with this driver.  But I don't know what I did.

My son-in-law gave me an old USB wireless adapter and I plugged it in and it started working but I don't have it in.  So at least if I get this going again, I will probably have an easy wireless solution.

I can boot up, but those same prompts come up, and I crash shortly afterward.  I can get to a terminal and type in commands as well as select the recovery console when I first log in.  However if I go on for a few minutes I usually crash with the same screen dump that I typed into the forum post.  The computer still works but I am crashing frequently and it's not usable for long after booting up.  I was able to copy some log files to my usb stick in the hopes that they would help someone figure out my issues, but nobody responded that those would be helpful.

I read that I could run the Ubuntu setup program and select a repair option, but the only way I could do that (because I can't burn a CD or DVD) is to put it on a USB stick and make it bootable.  I tried.  My computer bios has the option to boot to the USB but it did not work.  And I saw no install program.  So I gave up on that idea.

I think I tried some other repair utility, but my computer crashed before I could get anywhere.  I also tried some things that were mentioned on the forums on the command line, but it didn't resolve the crashing.  Again, I'm novice at this and I am not familiar with Ubuntu or what can be done in the terminal.  

I don't think I removed NDIS-Wrapper.  I'm not sure about drivers.  This where I'm at right now.  My computer is still crashing with the same screen dump and I don't know what to do with this or where to start.  I tried to provide as much information in this thread that I could, including system information and two hours of typing all those numbers and text from my screen dump, into this forum, so someone more knowledgeable might be able to tell what is going on.

Any ideas on what to do first?  What commands should I type to get the information out to help solve this crashing problem?  I'd be happy to fix my video problem if that's what is causing the problem as someone mentioned above.  But where do I even start?
Thanks in advance for any help you can give.

---

### Post by sudodus on 2013-07-15
> **JohnCarlson said:**
> Here is the chain of events:
A few months ago I upgraded to Ubuntu 12.04.  I ran into video problems but discovered I could select Ubuntu 2d at the login screen and everything ran fine that way, so I went with it.

Last week my wifi card stopped working.  It was a ZyXEL 802.11b/g Wireless Cardbus Adapter G-102.  the power light was no longer blinking on it.  I assumed the card died.  My computer was still running fine at this point.

I went out and bought the only card available at a store near me.  A TRENDnetTEW-641pc.  I tried to find drivers for it, but could not.  I then saw the NDIS-Wrapper solution online and tried to install that.  That seemed to install ok and came up.  Then I tried to "Add" this new video card.  An error occurred and I tried several times.  Then I determined it wasn't going to work and I removed the driver from NDIS-Wrapper.  However somewhere during this process of trying to get the wireless running, my computer crashed.  I rebooted.  The computer began crashing and I began getting the error messages in dialog boxes that I posted at the beginning of this thread.  I probably corrupted something mucking around with this driver.  But I don't know what I did.

My son-in-law gave me an old USB wireless adapter and I plugged it in and it started working but I don't have it in.  So at least if I get this going again, I will probably have an easy wireless solution.

I can boot up, but those same prompts come up, and I crash shortly afterward.  I can get to a terminal and type in commands as well as select the recovery console when I first log in.  However if I go on for a few minutes I usually crash with the same screen dump that I typed into the forum post.  The computer still works but I am crashing frequently and it's not usable for long after booting up.  I was able to copy some log files to my usb stick in the hopes that they would help someone figure out my issues, but nobody responded that those would be helpful.

[COLOR=#0000ff]I read that I could run the Ubuntu setup program and select a repair option, but the only way I could do that (because I can't burn a CD or DVD) is to put it on a USB stick and make it bootable.  I tried.  My computer bios has the option to boot to the USB but it did not work.  And I saw no install program.  So I gave up on that idea.
[/COLOR]
I think I tried some other repair utility, but my computer crashed before I could get anywhere.  I also tried some things that were mentioned on the forums on the command line, but it didn't resolve the crashing.  Again, I'm novice at this and I am not familiar with Ubuntu or what can be done in the terminal.  

I don't think I removed NDIS-Wrapper.  I'm not sure about drivers.  This where I'm at right now.  My computer is still crashing with the same screen dump and I don't know what to do with this or where to start.  I tried to provide as much information in this thread that I could, including system information and two hours of typing all those numbers and text from my screen dump, into this forum, so someone more knowledgeable might be able to tell what is going on.

Any ideas on what to do first?  What commands should I type to get the information out to help solve this crashing problem?  I'd be happy to fix my video problem if that's what is causing the problem as someone mentioned above.  But where do I even start?
Thanks in advance for any help you can give.

I suggest that you keep trying to make your computer boot from a USB stick. I think the light-weight flavour of Ubuntu, ***Xubuntu 12.04.2 'Precise Pangolin' 32-bit***, will work well with your computer. Download it from

[http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)

Check that the download was successful with ***md5sum*** according to
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
```
5ab48a21e8db6c2136faacf7781ca8d3 xubuntu-12.04.2-desktop-i386.iso
```

You cannot simply copy the iso file to the USB stick, but you must use a special tool to make it bootable. ***Unetbootin*** works from Windows as well as Ubuntu (graphical user interface). ***Cloning with dd*** works from Ubuntu, also from a text screen (if your graphical user interface does not work). See these links.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
and[URL="http://ubuntuforums.org/showthread.php?t=1958073"]
Howto make USB boot drives[/URL]

Test if the USB stick can boot another computer, so that you can tell if the problem is with the USB stick or your computer.

You can try several settings in the BIOS menus to make the computer boot from USB (the USB drive should be before the internal hard disk in the boot order). Sometimes you can 'pretend' that the USB stick is a hard disk drive (it is a *mass storage device*, and treated in the same way as a hard disk). In this case, the USB stick should be connected at boot, and should be selected as the 'first hard disk drive' to boot from.

When you can boot from a USB drive, you will be able to ***save your personal files***, try to repair the installed system and if necessary make a fresh install.

Good luck :-)

---

### Post by steeldriver on 2013-07-15
BTW this is likely just because you are starting up the computer with the bootable USB inserted (even though you're not actually booting from it):
> **JohnCarlson said:**
> 
Here is the series of messages that pop up shortly after booting up:
"A volume of software packages has been detected"
"Would you like to open it with the package manager?"

---

### Post by JohnCarlson on 2013-07-15
```
> Test if the USB stick can boot another computer, so that you can tell if the problem is with the USB stick or your computer.

You can try several settings in the BIOS menus to make the computer boot  from USB (the USB drive should be before the internal hard disk in the  boot order). Sometimes you can 'pretend' that the USB stick is a hard  disk drive (it is a *mass storage device*, and treated in the same  way as a hard disk). In this case, the USB stick should be connected at  boot, and should be selected as the 'first hard disk drive' to boot  from.

When you can boot from a USB drive, you will be able to ***save your personal files***, try to repair the installed system and if necessary make a fresh install.

Good luck :smile:

I ltook a closer look at the USB device I bought and discovered it was a special backup USB with a data encryption program on it and two partitions.  It turns out the unlocked partition set so it was not bootable.  Anyway, I used the disk utility on my wife's computer to remove the secure partition and make one whole partition that was bootable.  Then I put the iso file (from your link) and ran a utility to make it a bootable operating system on the USB.  That worked.  Then when I was booting up my broken laptop, I hit f-12, selected boot from USB like I did before, but this time it worked.  I got all my data off the computer and installed a fresh install, no messing around.  It works perfectly.  I never got to the bottom of fixing the crashing problem, but I am happy with Xubuntu and the end result.  I'm now reinstalling the programs I need through the software center.

Thanks for pointing to the USB issue so I could get this far.  I'm back up and running now.

```

---

### Post by sudodus on 2013-07-16
> **JohnCarlson said:**
> 

I ltook a closer look at the USB device I bought and discovered it was a special backup USB with a data encryption program on it and two partitions.  It turns out the unlocked partition set so it was not bootable.  Anyway, I used the disk utility on my wife's computer to remove the secure partition and make one whole partition that was bootable.  Then I put the iso file (from your link) and ran a utility to make it a bootable operating system on the USB.  That worked.  Then when I was booting up my broken laptop, I hit f-12, selected boot from USB like I did before, but this time it worked.  I got all my data off the computer and installed a fresh install, no messing around.  It works perfectly.  I never got to the bottom of fixing the crashing problem, but I am happy with Xubuntu and the end result.  I'm now reinstalling the programs I need through the software center.

Thanks for pointing to the USB issue so I could get this far.  I'm back up and running now.


I'm glad you found the problem with the USB drive, and that you could fix it and make a fresh install of Xubuntu :-)

-o-

Just two more things:

1. Next time you need to start a thread at the Ubuntu Forums, please don't put regular text within code tags. It makes it hard to read. Use code tags only for command lines, shell scripts and output text from the terminal.

2. Please mark this thread as SOLVED: Edit the first post, go advanced and put SOLVED into the **[prefix]**.

---

### Post by JohnCarlson on 2013-07-16
Thank you.

---

