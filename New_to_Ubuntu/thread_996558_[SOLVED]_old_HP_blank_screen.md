---
title: "[SOLVED] old HP blank screen"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by earle79 on 2008-11-28
ok, first things im new, to all this so please excuse my ignorance. 

Machine Spec.
hp xg910
celeron 800
128 meg ram
20gig hd
cdrom and floppy

i installed xbuntu 8.10 the alternate version.  after install finally finished, it rebooted, then a nice logo splash with loading bar, i was very happy.  then black dark blank screen, i got very sad then.  so i read some post on doing a recover mode then going to xfix.  then normal boot, sometime works, but last few time it dont.  im really lost.  i just dont know where to start?  is it my monitor(normal CRT) my video card? intel 810(82810).  please help.

---

### Post by ajmorris on 2008-11-29
> **earle79 said:**
> ok, first things im new, to all this so please excuse my ignorance. 

Machine Spec.
hp xg910
celeron 800
128 meg ram
20gig hd
cdrom and floppy

i installed xbuntu 8.10 the alternate version.  after install finally finished, it rebooted, then a nice logo splash with loading bar, i was very happy.  then black dark blank screen, i got very sad then.  so i read some post on doing a recover mode then going to xfix.  then normal boot, sometime works, but last few time it dont.  im really lost.  i just dont know where to start?  is it my monitor(normal CRT) my video card? intel 810(82810).  please help.


hi there,
the > black dark blank screen Is it completely blacked out? i.e. no text on it at all? i.e. errors, or something else. And, you mentioned the xfix method to reconfigure your xorg, you booted into recovery mode, i assume the recovery mode functioned correctly? and you were able to run xfix?

AJ

---

### Post by earle79 on 2008-11-29
yes totally blank, nothing.  should be logon screen.  yes i see all the stuff in recover mode.  but now that recovery option still leads me to blank logon

what should i type in the root"drop to shell promt" to see whats wrong?

---

### Post by ajmorris on 2008-11-29
when you boot up in 'normal' mode, and it gets to the completely blank screen, where you can not do anything. Could you please try press the key combination:  CTRL+ALT+F1   and seeing if that will get you to what is TTY. It will be a black screen, with white writing on it, sitting at a loging prompt.


AJ

---

### Post by earle79 on 2008-11-29
i just tried gksu displayconfig-gtk and said gtk warning cannot open display

---

### Post by earle79 on 2008-11-29
> **ajmorris said:**
> when you boot up in 'normal' mode, and it gets to the completely blank screen, where you can not do anything. Could you please try press the key combination:  CTRL+ALT+F1   and seeing if that will get you to what is TTY. It will be a black screen, with white writing on it, sitting at a loging prompt.


AJ
 forgot to tell you i already tried that.  and ctrl/alt/f2 and f3  nothing ever showed up and i did give a couple minutes.

---

### Post by ajmorris on 2008-11-29
> **earle79 said:**
> i just tried gksu displayconfig-gtk and said gtk warning cannot open display

yep, thats because you have to have an Xsession started to start that application... hmm, this blank screen is weird, usually you would get an error of some sort. Could you please paste the contents of your /var/log/syslog file (i.e by into recovery mode, and copy /var/log/syslog to some sort of removable device, and using another computer to paste it, or use some other means, whichever is most convenient for you)


AJ

---

### Post by earle79 on 2008-11-29
would love to but, well i cant see to figure out how to.  i have a usb drive i can use.  i did manage to open the file there is alot of mumbojumbo in there.  what am i looking for?  btw thank you very much for trying to help me

---

### Post by earle79 on 2008-11-29
i'm really stupid i guess. i found /var/log/syslog  opened it in nano, pressed ctrl-o then typed in /var/log/syslog_bk and switched to DOS file.

hit enter, then ask me another question can't remember what i did there.
so i exited nano and got my usb dive plugged in. and i figured out how to mount it from another post. 
then i typed cp -r /var/log/syslog_bk /dev/sdb1 and it says cant find the syslog_bk doesn't exist?  

what gives, now ive tried this so many times im very confused to where im at, so if anyone can tell me how(step by step) to copy syslog in a format that windows can read so i can past it to the forum that would be great.

---

### Post by linux_tech on 2008-11-29
Have you tries booting in recovery mode and typing

```
gdm start
```

---

### Post by oilchangeguy on 2008-11-29
> **earle79 said:**
> ok, first things im new, to all this so please excuse my ignorance. 

Machine Spec.
hp xg910
celeron 800
128 meg ram
20gig hd
cdrom and floppy

i installed xbuntu 8.10 the alternate version.  after install finally finished, it rebooted, then a nice logo splash with loading bar, i was very happy.  then black dark blank screen, i got very sad then.  so i read some post on doing a recover mode then going to xfix.  then normal boot, sometime works, but last few time it dont.  im really lost.  i just dont know where to start?  is it my monitor(normal CRT) my video card? intel 810(82810).  please help.

see this, taken from [www.ubuntu.com](www.ubuntu.com)

Recommended minimum requirements
Ubuntu should run reasonably well on a computer with the following minimum hardware specification. However, features such as visual effects may not run smoothly. 

700 MHz x86 processor 
384 MB of system memory (RAM) 
8 GB of disk space 
Graphics card capable of 1024x768 resolution 
Sound card 

A network or Internet connection

you need to add more ram.

---

### Post by earle79 on 2008-11-29
> **ajmorris said:**
> yep, thats because you have to have an Xsession started to start that application... hmm, this blank screen is weird, usually you would get an error of some sort. Could you please paste the contents of your /var/log/syslog file (i.e by into recovery mode, and copy /var/log/syslog to some sort of removable device, and using another computer to paste it, or use some other means, whichever is most convenient for you)


AJ

AJ i finally got it, took several tries but i did it, im proud of myself a little. its attached in a zip file, its kinda big file.

---

### Post by earle79 on 2008-11-29
[SIZE="2"]> **oilchangeguy said:**
> see this, taken from [www.ubuntu.com](www.ubuntu.com)

Recommended minimum requirements
Ubuntu should run reasonably well on a computer with the following minimum hardware specification. However, features such as visual effects may not run smoothly. 

700 MHz x86 processor 
384 MB of system memory (RAM) 
8 GB of disk space 
Graphics card capable of 1024x768 resolution 
Sound card 

A network or Internet connection

you need to add more ram.

[/SIZE]

I thought that i could run Xubuntu on older stuff?  i know 128 isnt a lot but the few times i did manage to get logged in it just ran a little slow. i saw a few people running that much with xubuntu and they said it was a little slow, i know its gonna be, but i don't need all the 3d stuff or anything.  you think that is my real problem? if so i will try to find some more ram somewhere.

---

### Post by earle79 on 2008-11-29
> **linux_tech said:**
> Have you tries booting in recovery mode and typing

```
gdm start
```

no i havent i will try it right now.

---

### Post by oilchangeguy on 2008-11-29
> **earle79 said:**
> [SIZE="2"]

[/SIZE]

I thought that i could run Xubuntu on older stuff?  i know 128 isnt a lot but the few times i did manage to get logged in it just ran a little slow. i saw a few people running that much with xubuntu and they said it was a little slow, i know its gonna be, but i don't need all the 3d stuff or anything.  you think that is my real problem? if so i will try to find some more ram somewhere.

my mistake. i gave you the specs for ubuntu. here's the specs for xubuntu
Recommended minimum requirements
300 MHz processor 
256 MB of system memory (RAM) 
8 GB of disk space 
Graphics card capable of 800x600 resolution

you still need more ram than you presently have. if you can't do that you may need to try puppy linux, or damn small linux. or even a fresh install of xp. xp was designed to run on a machine with your specs. there's many things you can do to xp to disable some to the ram eating things. this will allow the computer to run the os and the much needed anti-virus software. i suggest avg, it's not very power hungry. but your best bet is to find out your systems max ram, and upgrade to it. then whatever os you use will run at it's best.

---

### Post by earle79 on 2008-11-29
hey i tried GDM start, and it locks up saying error loading human theme.

---

### Post by earle79 on 2008-11-29
just an update i managed to download OzOS liveCD and it boots pretty well.  A little slow, but might improve after install on hard drive.

---

### Post by ajmorris on 2008-11-29
> **oilchangeguy said:**
> my mistake. i gave you the specs for ubuntu. here's the specs for xubuntu
Recommended minimum requirements
300 MHz processor 
256 MB of system memory (RAM) 
8 GB of disk space 
Graphics card capable of 800x600 resolution

you still need more ram than you presently have. if you can't do that you may need to try puppy linux, or damn small linux. or even a fresh install of xp. xp was designed to run on a machine with your specs. there's many things you can do to xp to disable some to the ram eating things. this will allow the computer to run the os and the much needed anti-virus software. i suggest avg, it's not very power hungry. but your best bet is to find out your systems max ram, and upgrade to it. then whatever os you use will run at it's best.

ubuntu and xubuntu can still start with 128mb of RAM, however, are a little sluggish. You can easily run a fully functional, and fast system using just a straight WM, instead of a DE, like openbox, or fluxbox. And this issue is before it even goes to start xfce, it is before it starts Xorg, and starts the login manager.

AJ

---

### Post by ajmorris on 2008-11-29
> **oilchangeguy said:**
> my mistake. i gave you the specs for ubuntu. here's the specs for xubuntu
Recommended minimum requirements
300 MHz processor 
256 MB of system memory (RAM) 
8 GB of disk space 
Graphics card capable of 800x600 resolution

you still need more ram than you presently have. if you can't do that you may need to try puppy linux, or damn small linux. or even a fresh install of xp. xp was designed to run on a machine with your specs. there's many things you can do to xp to disable some to the ram eating things. this will allow the computer to run the os and the much needed anti-virus software. i suggest avg, it's not very power hungry. but your best bet is to find out your systems max ram, and upgrade to it. then whatever os you use will run at it's best.

ubuntu and xubuntu can still start with 128mb of RAM, however, are a little sluggish. You can easily run a fully functional, and fast system using just a straight WM, instead of a DE, like openbox, or fluxbox. And this issue is before it even goes to start xfce, it is before it starts Xorg, and starts the login manager.

AJ

---

### Post by ajmorris on 2008-11-29
> **earle79 said:**
> AJ i finally got it, took several tries but i did it, im proud of myself a little. its attached in a zip file, its kinda big file.

strange... X doesnt even attempt to start, nor does a TTY session, its almost as if the kernel just freezes, without any errors...

Boot into recovery mode, and try to start X, via either 'startx' or 'gdm start'  If it works, or even if it doesnt, it doesnt matter, edit /boot/grub/menu.lst (either in your xsession, or in TTY) and append to the kernel line, of the kernel you are trying to use:
noapic,nolapic

reboot, and try again... its a long shot, and probably wont work, but worth a shot.

Also, are you using x86 or x86_64 architecture?

AJ

---

### Post by earle79 on 2008-11-29
> **ajmorris said:**
> strange... X doesnt even attempt to start, nor does a TTY session, its almost as if the kernel just freezes, without any errors...

Boot into recovery mode, and try to start X, via either 'startx' or 'gdm start'  If it works, or even if it doesnt, it doesnt matter, edit /boot/grub/menu.lst (either in your xsession, or in TTY) and append to the kernel line, of the kernel you are trying to use:
noapic,nolapic

reboot, and try again... its a long shot, and probably wont work, but worth a shot.

Also, are you using x86 or x86_64 architecture?

AJ

ok, well not sure what your saying there but i will try it.

so you didnt see any errors in that log?

how do i be sure? everything i downloaded said i386 so i guess thats what your talking about right?

---

### Post by ajmorris on 2008-11-30
> **earle79 said:**
> ok, well not sure what your saying there but i will try it.

so you didnt see any errors in that log?

how do i be sure? everything i downloaded said i386 so i guess thats what your talking about right?

no, no errors in the log, (unless i glanced over something and missed it) it just *stopped* and didnt finish loading...

yep, i386 means you are using an x86 operating system.

how are those kernel paramaters in /boot/grub/menu.lst coming along?


AJ

---

### Post by earle79 on 2008-11-30
well, dont get mad but at me but i gave up on xubuntu.  i downloaded linux mint with fluxbox.  runs pretty well except FREAKIN Belkin wireless card.  driving me insane i just can't get it to see it as a wlan.  i have run so many tutorials i dont even know which one i have done and not done.  any if you know anything about wireless and ndiswrapper let me know cause im drowing here.  i have a post started about it on this site.  thanks for trying to help me.

---

### Post by ajmorris on 2008-11-30
> **earle79 said:**
> well, dont get mad but at me but i gave up on xubuntu.  i downloaded linux mint with fluxbox.  runs pretty well except FREAKIN Belkin wireless card.  driving me insane i just can't get it to see it as a wlan.  i have run so many tutorials i dont even know which one i have done and not done.  any if you know anything about wireless and ndiswrapper let me know cause im drowing here.  i have a post started about it on this site.  thanks for trying to help me.


np, glad you have some linux up and running :) And linux mint is a lot like ubuntu anyway...

What belkin card do you have? is it PCI? -- if so, paste here the output of ```
sudo lspci
```

is it usb? -- if so, paste here the output of ```
sudo lsusb
```


AJ

---

### Post by earle79 on 2008-11-30
You ask and ye shall receive ten times more info i know but i really would like to get this working 2nite. yeah it is pci and its a belkin f5d7000 v2 at least thats what all this stuff says.

```
earle@linuxdesktop ~ $ lspci
00:00.0 Host bridge: Intel Corporation 82810 GMCH (Graphics Memory Controller Hub) (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810 (CGC) Chipset Graphics Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 02)
01:08.0 Communication controller: Agere Systems LT WinModem (rev 02)
01:09.0 Ethernet controller: Belkin Unknown device 700f (rev 20)

earle@linuxdesktop ~ $ lspci -n
00:00.0 0600: 8086:7120 (rev 03)
00:01.0 0300: 8086:7121 (rev 03)
00:1e.0 0604: 8086:2418 (rev 02)
00:1f.0 0601: 8086:2410 (rev 02)
00:1f.1 0101: 8086:2411 (rev 02)
00:1f.2 0c03: 8086:2412 (rev 02)
00:1f.3 0c05: 8086:2413 (rev 02)
00:1f.5 0401: 8086:2415 (rev 02)
01:08.0 0780: 11c1:044e (rev 02)
01:09.0 0200: 1799:700f (rev 20)
earle@linuxdesktop ~ $ 

earle@linuxdesktop ~ $ lspci -nm
00:00.0 "0600" "8086" "7120" -r03 "" ""
00:01.0 "0300" "8086" "7121" -r03 "8086" "7123"
00:1e.0 "0604" "8086" "2418" -r02 "" ""
00:1f.0 "0601" "8086" "2410" -r02 "" ""
00:1f.1 "0101" "8086" "2411" -r02 -p80 "8086" "2411"
00:1f.2 "0c03" "8086" "2412" -r02 "8086" "2412"
00:1f.3 "0c05" "8086" "2413" -r02 "8086" "2413"
00:1f.5 "0401" "8086" "2415" -r02 "8086" "5643"
01:08.0 "0780" "11c1" "044e" -r02 "1235" "044e"
01:09.0 "0200" "1799" "700f" -r20 "1799" "700f"
earle@linuxdesktop ~ $ 

earle@linuxdesktop ~ $ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-16-generic SMP mod_unload 586 
earle@linuxdesktop ~ $ 

earle@linuxdesktop ~ $ lshw -class network

WARNING: you should run this program as super-user.

  *-network UNCLAIMED     

       description: Ethernet controller

       product: Belkin

       vendor: Belkin

       physical id: 9

       bus info: pci@0000:01:09.0

       version: 20

       width: 32 bits

       clock: 33MHz

       capabilities: cap_list

       configuration: latency=64 maxlatency=64 mingnt=32
earle@linuxdesktop ~ $
```

---

### Post by ajmorris on 2008-11-30
have you installed any ndiswrapper drivers yet? if so, please post the output of ndiswrapper -l

at any rate, here is a guide for that card:
[http://www.linuxquestions.org/questions/linux-wireless-networking-41/belkin-f5d7000-wireless-card-in-linux-complete-guide-386847/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/belkin-f5d7000-wireless-card-in-linux-complete-guide-386847/)


AJ

---

### Post by earle79 on 2008-12-01
OK, i finally found the right one its version 7  using the win98 version.  there is still a few issues though.  im rebooting now it was acting wierd.  still dont have actual connection but i got the driver installed. 

when i then type sudo ndiswrapper -m it says "modprobe config already contains alias directive" 

so dont know what that means.  i just know that wcid doest pick anything up but network manager did.  oh its done rebooting.  i will check some things.

---

### Post by earle79 on 2008-12-01
ok got some issues no connection yet and i have to sleep but here is dmesg for you to look at.  why is it resetting so much?

```
 ________________________
/ I'll burn my books.    \
|                        |
\ -- Christopher Marlowe /
 ------------------------
       \   ,__,
        \  (oo)____
           (__)    )\
              ||--|| *
earle@linuxdesktop ~ $ dmesg
[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e7400 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000007ef0000 (usable)
[    0.000000]  BIOS-e820: 0000000007ef0000 - 0000000007effc00 (ACPI data)
[    0.000000]  BIOS-e820: 0000000007effc00 - 0000000007f00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000007f00000 - 0000000008000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 126MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 32496) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    32496
[    0.000000]   HighMem     32496 ->    32496
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    32496
[    0.000000] On node 0 totalpages: 32496
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 221 pages used for memmap
[    0.000000]   Normal zone: 28179 pages, LIFO batch:7
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7280 checksum 0
[    0.000000] ACPI: RSDP 000F7280, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 07EFCAB8, 002C (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 07EFFB64, 0074 (r1 HP     Hawk      6040000 PTL     F4240)
[    0.000000] ACPI: DSDT 07EFCAE4, 3080 (r1  INTEL  Whitney  6040000 MSFT  100000B)
[    0.000000] ACPI: FACS 07EFFFC0, 0040
[    0.000000] ACPI: BOOT 07EFFBD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Allocating PCI resources starting at 10000000 (gap: 08000000:f7f00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e8000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e8000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 32243
[    0.000000] Kernel command line: root=/dev/sda1 ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (0110b000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 512 (order: 9, 2048 bytes)
[    0.000000] Detected 801.847 MHz processor.
[   24.265505] Console: colour VGA+ 80x25
[   24.265518] console [tty0] enabled
[   24.265765] Dentry cache hash table entries: 16384 (order: 4, 65536 bytes)
[   24.265980] Inode-cache hash table entries: 8192 (order: 3, 32768 bytes)
[   24.279298] Memory: 115548k/129984k available (2157k kernel code, 13892k reserved, 998k data, 364k init, 0k highmem)
[   24.279321] virtual kernel memory layout:
[   24.279324]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   24.279327]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   24.279331]     vmalloc : 0xc8800000 - 0xff7fe000   ( 879 MB)
[   24.279334]     lowmem  : 0xc0000000 - 0xc7ef0000   ( 126 MB)
[   24.279338]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[   24.279341]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   24.279345]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   24.279354] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   24.279444] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   24.359478] Calibrating delay using timer specific routine.. 1605.25 BogoMIPS (lpj=3210514)
[   24.359553] Security Framework initialized
[   24.359575] SELinux:  Disabled at boot.
[   24.359613] AppArmor: AppArmor initialized
[   24.359624] Failure registering capabilities with primary security module.
[   24.359648] Mount-cache hash table entries: 512
[   24.360002] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[   24.360039] CPU: L1 I cache: 16K, L1 D cache: 16K
[   24.360046] CPU: L2 cache: 128K
[   24.360055] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000 00000000
[   24.360092] Compat vDSO mapped to ffffe000.
[   24.360134] Checking 'hlt' instruction... OK.
[   24.376106] SMP alternatives: switching to UP code
[   24.379599] Freeing SMP alternatives: 11k freed
[   24.379994] Early unpacking initramfs... done
[   25.451090] ACPI: Core revision 20070126
[   25.451328] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   25.454048] ACPI: setting ELCR to 0200 (from 0a00)
[   25.454701] CPU0: Intel Celeron (Coppermine) stepping 0a
[   25.454720] SMP motherboard not detected.
[   25.454726] Local APIC not detected. Using dummy APIC emulation.
[   25.454863] Brought up 1 CPUs
[   25.454923] CPU0 attaching sched-domain:
[   25.454932]  domain 0: span 01
[   25.454938]   groups: 01
[   25.455651] net_namespace: 64 bytes
[   25.455677] Booting paravirtualized kernel on bare hardware
[   25.457356] Time:  5:10:36  Date: 12/01/08
[   25.457462] NET: Registered protocol family 16
[   25.458407] EISA bus registered
[   25.458448] ACPI: bus type pci registered
[   25.459775] PCI: PCI BIOS revision 2.10 entry at 0xfd99e, last bus=1
[   25.459786] PCI: Using configuration type 1
[   25.459791] Setting up standard PCI resources
[   25.468887] ACPI: EC: Look up EC in DSDT
[   25.474603] ACPI: Interpreter enabled
[   25.474614] ACPI: (supports S0 S1 S5)
[   25.474641] ACPI: Using PIC for interrupt routing
[   25.487841] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   25.488268] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[   25.488279] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[   25.488880] PCI: Transparent bridge - 0000:00:1e.0
[   25.488929] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   25.489050] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SLOT._PRT]
[   25.493487] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *9 10 11 14 15)
[   25.493731] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 14 15)
[   25.493961] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
[   25.494193] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 14 15)
[   25.494701] Linux Plug and Play Support v0.97 (c) Adam Belay
[   25.494836] pnp: PnP ACPI init
[   25.494866] ACPI: bus type pnp registered
[   25.502510] ACPI Error (dsopcode-0548): Field [ALB2] at 120 exceeds Buffer [CRSA] size 104 (bits) [20070126]
[   25.502532] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPC0.SIO_.LPT_._CRS] (Node c5b08360), AE_AML_BUFFER_LIMIT
[   25.502594] ACPI Error (uteval-0233): Method execution failed [\_SB_.PCI0.LPC0.SIO_.LPT_._CRS] (Node c5b08360), AE_AML_BUFFER_LIMIT
[   25.502612] pnp: PnPACPI: METHOD_NAME__CRS failure for PNP0400
[   25.504018] pnp: PnP ACPI: found 13 devices
[   25.504033] ACPI: ACPI bus type pnp unregistered
[   25.504044] PnPBIOS: Disabled by ACPI PNP
[   25.505130] PCI: Using ACPI for IRQ routing
[   25.505146] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   25.523490] NET: Registered protocol family 8
[   25.523502] NET: Registered protocol family 20
[   25.523798] AppArmor: AppArmor Filesystem Enabled
[   25.527460] Time: tsc clocksource has been installed.
[   25.535672] system 00:01: ioport range 0x1000-0x105f has been reserved
[   25.535683] system 00:01: ioport range 0x1060-0x107f has been reserved
[   25.535691] system 00:01: ioport range 0x1180-0x11bf has been reserved
[   25.535700] system 00:01: ioport range 0x1c00-0x1c7f has been reserved
[   25.535707] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[   25.535714] system 00:01: ioport range 0x800-0x87f has been reserved
[   25.535728] system 00:01: iomem range 0xff800000-0xffffffff could not be reserved
[   25.567546] PCI: Bridge: 0000:00:1e.0
[   25.567560]   IO window: 2000-2fff
[   25.567571]   MEM window: f4100000-f41fffff
[   25.567578]   PREFETCH window: disabled.
[   25.567601] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   25.567644] NET: Registered protocol family 2
[   25.607726] IP route cache hash table entries: 1024 (order: 0, 4096 bytes)
[   25.608391] TCP established hash table entries: 4096 (order: 3, 32768 bytes)
[   25.608511] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[   25.608623] TCP: Hash tables configured (established 4096 bind 4096)
[   25.608630] TCP reno registered
[   25.619929] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[   26.476223]  it is
[   27.600293] Freeing initrd memory: 8658k freed
[   27.600961] Simple Boot Flag at 0x36 set to 0x1
[   27.602356] audit: initializing netlink socket (disabled)
[   27.602403] audit(1228108238.324:1): initialized
[   27.610834] VFS: Disk quotas dquot_6.5.1
[   27.611190] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   27.611848] io scheduler noop registered
[   27.611859] io scheduler anticipatory registered
[   27.611865] io scheduler deadline registered
[   27.611936] io scheduler cfq registered (default)
[   27.611974] Boot video device is 0000:00:01.0
[   27.613067] isapnp: Scanning for PnP cards...
[   27.967398] isapnp: No Plug & Play device found
[   28.191006] Real Time Clock Driver v1.12ac
[   28.191529] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   28.191856] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   28.192451] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   28.195020] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   28.196280] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   28.199882] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   28.200163] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   28.200594] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   28.203868] serio: i8042 KBD port at 0x60,0x64 irq 1
[   28.203886] serio: i8042 AUX port at 0x60,0x64 irq 12
[   28.207723] mice: PS/2 mouse device common for all mice
[   28.208261] EISA: Probing bus 0 at eisa.0
[   28.208282] Cannot allocate resource for EISA slot 1
[   28.208290] Cannot allocate resource for EISA slot 2
[   28.208324] EISA: Detected 0 cards.
[   28.208334] cpuidle: using governor ladder
[   28.208339] cpuidle: using governor menu
[   28.208915] NET: Registered protocol family 1
[   28.209026] Using IPI No-Shortcut mode
[   28.209124] registered taskstats version 1
[   28.209347]   Magic number: 4:255:162
[   28.209439]   hash matches device ttyq2
[   28.209583] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   28.209589] EDD information not available.
[   28.211345] Freeing unused kernel memory: 364k freed
[   28.238999] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   29.964378] fuse init (API version 7.9)
[   30.056073] ACPI: Invalid PBLK length [5]
[   31.448507] SCSI subsystem initialized
[   31.623801] usbcore: registered new interface driver usbfs
[   31.623879] usbcore: registered new interface driver hub
[   31.664178] usbcore: registered new device driver usb
[   31.822952] USB Universal Host Controller Interface driver v3.0
[   31.823591] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   31.823604] PCI: setting IRQ 11 as level-triggered
[   31.823611] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   31.823638] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   31.823648] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[   31.824289] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[   31.824344] uhci_hcd 0000:00:1f.2: irq 11, io base 0x00001080
[   31.824773] usb usb1: configuration #1 chosen from 1 choice
[   31.824853] hub 1-0:1.0: USB hub found
[   31.824874] hub 1-0:1.0: 2 ports detected
[   31.887783] libata version 3.00 loaded.
[   31.979065] ata_piix 0000:00:1f.1: version 2.12
[   31.979221] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   31.997586] scsi0 : ata_piix
[   32.038882] scsi1 : ata_piix
[   32.039073] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0x10a0 irq 14
[   32.039081] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0x10a8 irq 15
[   32.166919] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   32.203612] ata1.00: ATA-5: QUANTUM FIREBALLlct20 20, APL.0900, max UDMA/100
[   32.203627] ata1.00: 39876480 sectors, multi 8: LBA 
[   32.203673] ata1.00: limited to UDMA/33 due to 40-wire cable
[   32.219610] ata1.00: configured for UDMA/33
[   32.341688] usb 1-1: configuration #1 chosen from 1 choice
[   32.539180] ata2.00: ATAPI: LG      CD-ROM CRD-8485B, 1.00, max MWDMA2
[   32.555204] Floppy drive(s): fd0 is 1.44M
[   32.576625] FDC 0 is a post-1991 82077
[   32.703138] ata2.00: configured for MWDMA2
[   32.703551] scsi 0:0:0:0: Direct-Access     ATA      QUANTUM FIREBALL APL. PQ: 0 ANSI: 5
[   32.704230] scsi 1:0:0:0: CD-ROM            LG       CD-ROM CRD-8485B 1.00 PQ: 0 ANSI: 5
[   34.614797] Driver 'sd' needs updating - please use bus_type methods
[   34.619753] sd 0:0:0:0: [sda] 39876480 512-byte hardware sectors (20417 MB)
[   34.619802] sd 0:0:0:0: [sda] Write Protect is off
[   34.619811] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   34.619869] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.620041] sd 0:0:0:0: [sda] 39876480 512-byte hardware sectors (20417 MB)
[   34.620076] sd 0:0:0:0: [sda] Write Protect is off
[   34.620083] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   34.620140] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.620154]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   34.644234] usbcore: registered new interface driver libusual
[   34.659046]  sda1 sda2 <<6>Initializing USB Mass Storage driver...
[   34.673381] scsi2 : SCSI emulation for USB Mass Storage devices
[   34.675416] usbcore: registered new interface driver usb-storage
[   34.675441] USB Mass Storage support registered.
[   34.675780] usb-storage: device found at 2
[   34.675788] usb-storage: waiting for device to settle before scanning
[   34.681365]  sda5 >
[   34.681662] sd 0:0:0:0: [sda] Attached SCSI disk
[   34.702834] sr0: scsi3-mmc drive: 0x/48x cd/rw xa/form2 cdda tray
[   34.702853] Uniform CD-ROM driver Revision: 3.20
[   34.703033] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   34.713365] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   34.713428] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   35.906094] Attempting manual resume
[   35.906111] swsusp: Resume From Partition 8:5
[   35.906117] PM: Checking swsusp image.
[   35.918099] PM: Resume from disk failed.
[   36.036054] kjournald starting.  Commit interval 5 seconds
[   36.036100] EXT3-fs: mounted filesystem with ordered data mode.
[   39.675674] usb-storage: device scan complete
[   39.678657] scsi 2:0:0:0: Direct-Access     Lexar    USB Flash Drive  1100 PQ: 0 ANSI: 0 CCS
[   39.689569] sd 2:0:0:0: [sdb] 3932160 512-byte hardware sectors (2013 MB)
[   39.692562] sd 2:0:0:0: [sdb] Write Protect is off
[   39.692574] sd 2:0:0:0: [sdb] Mode Sense: 43 00 00 00
[   39.692580] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   39.704558] sd 2:0:0:0: [sdb] 3932160 512-byte hardware sectors (2013 MB)
[   39.707577] sd 2:0:0:0: [sdb] Write Protect is off
[   39.707591] sd 2:0:0:0: [sdb] Mode Sense: 43 00 00 00
[   39.707598] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   39.707616]  sdb: sdb1
[   39.753855] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   39.753976] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   52.205929] Linux agpgart interface v0.102
[   52.298867] agpgart: Detected an Intel i810 Chipset.
[   52.433142] intel_rng: FWH not detected
[   52.442597] agpgart: AGP aperture is 64M @ 0xf8000000
[   52.540044] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   52.607436] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   53.004908] iTCO_vendor_support: vendor-support=0
[   53.261432] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   53.261707] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   53.261726] iTCO_wdt: No card detected
[   53.325590] i810_smbus 0000:00:01.0: i810/i815 i2c device found.
[   53.946802] logips2pp: Detected unknown logitech mouse model 63
[   54.154721] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   54.473293] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input2
[   54.497186] input: Power Button (FF) as /devices/virtual/input/input3
[   54.509376] ACPI: Power Button (FF) [PWRF]
[   54.509799] input: Power Button (CM) as /devices/virtual/input/input4
[   54.524725] ACPI: Power Button (CM) [PWRB]
[   55.094580] ndiswrapper: driver blkwgdv7 (Belkin,10/19/2006,5.87.19.106) loaded
[   55.095349] PCI: Enabling device 0000:01:09.0 (0110 -> 0113)
[   55.095821] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
[   55.095830] PCI: setting IRQ 9 as level-triggered
[   55.095837] ACPI: PCI Interrupt 0000:01:09.0[A] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[   56.168591] mpu401 00:0c: activated
[   57.066179] ndiswrapper: using IRQ 9
[   63.436628] wlan0: ethernet device 00:17:3f:2e:5d:06 using NDIS driver: blkwgdv7, version: 0x50056, NDIS version: 0x500, vendor: 'Belkin Wireless G Notebook/Desktop Card                                     ', 1799:700F.5.conf
[   63.436783] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   63.437103] usbcore: registered new interface driver ndiswrapper
[   63.437712] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[   63.437768] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   64.031732] intel8x0_measure_ac97_clock: measured 55254 usecs
[   64.031745] intel8x0: clocking to 48000
[   64.595530] NET: Registered protocol family 17
[   65.277364] parport0: PC-style at 0x378 [PCSPP,TRISTATE,EPP]
[   65.373610] lp0: using parport0 (polling).
[   65.869662] Adding 361420k swap on /dev/sda5.  Priority:-1 extents:1 across:361420k
[   66.694318] EXT3 FS on sda1, internal journal
[   67.107627] device-mapper: uevent: version 1.0.3
[   67.107738] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   70.001276] ip_tables: (C) 2000-2006 Netfilter Core Team
[   72.394481] No dock devices found.
[   78.036958] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   78.036974] apm: overridden by ACPI.
[   78.373733] ppdev: user-space parallel port driver
[   79.616648] audit(1228108290.822:2): type=1502 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4803 profile="/usr/sbin/cupsd" namespace="default"
[   85.942101] Bluetooth: Core ver 2.11
[   85.944402] NET: Registered protocol family 31
[   85.944419] Bluetooth: HCI device and connection manager initialized
[   85.944430] Bluetooth: HCI socket layer initialized
[   86.169688] Bluetooth: L2CAP ver 2.9
[   86.169705] Bluetooth: L2CAP socket layer initialized
[   86.215292] Bluetooth: RFCOMM socket layer initialized
[   86.216653] Bluetooth: RFCOMM TTY layer initialized
[   86.216673] Bluetooth: RFCOMM ver 1.8
[   93.937284] [drm] Initialized drm 1.1.0 20060810
[   93.961136] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 9
[   93.961160] ACPI: PCI Interrupt 0000:00:01.0[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
[   93.961176] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   93.961611] [drm] Initialized i810 1.4.0 20030605 on minor 0
[   93.962897] mtrr: base(0xf8000000) is not aligned on a size(0x180000) boundary
[   94.145845] [drm] Using v1.4 init.
[   97.708413] [drm:drm_release] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[   97.708425] 	driver to use reclaim_buffers_idlelocked() instead.
[   97.708428] 	I will go on reclaiming the buffers anyway.
[ 1177.327379] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1191.326650] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1201.325057] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1211.324158] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1225.323550] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1237.321615] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1255.319796] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1269.328711] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1283.317087] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1303.315137] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1317.313831] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1329.312646] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1343.311223] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1357.309873] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1371.308498] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1389.317015] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1403.305383] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1431.302730] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1443.301568] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1457.310454] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1469.299441] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1483.297592] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1525.293530] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1543.291811] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1557.290399] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1581.288073] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1597.286574] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1611.285232] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1623.284010] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1637.290726] ndiswrapper (mp_reset:62): wlan0 is being reset
earle@linuxdesktop ~ $ 

```





> **earle79 said:**
> OK, i finally found the right one its version 7  using the win98 version.  there is still a few issues though.  im rebooting now it was acting wierd.  still dont have actual connection but i got the driver installed. 

when i then type sudo ndiswrapper -m it says "modprobe config already contains alias directive" 

so dont know what that means.  i just know that wcid doest pick anything up but network manager did.  oh its done rebooting.  i will check some things.

---

### Post by ajmorris on 2008-12-02
can you please post the output of ```
sudo ndiswrapper -l
``` 

Also, you have your wlan0 interface, can you connect to your AP at all?



AJ

---

### Post by earle79 on 2008-12-02
AJ my friend.  I have concluded that I must be a complete retard.  I let someone else talk me into using 8.10 again.  I downloaded #!CrunchBang Live CD.(this by the way is the 5th different distro).  I also found a 256MB RAM chip to install along with my 128MB.  Freakin ran awesome on Live CD.  And most of all everything worked, Wireless Lan, Sound,etc.  I was so happy I said what the hell just install it, cause it will run even better then right?Oh man, was I wrong.  

Im back to the blank screen, can't get to logon screen.  Can't get to terminal.  Tried to recover mode and fix x, same result.  Tried the nosplash on boot up.  I can't drop to shell, cause it ask for root password and the one I put in for logon at the install don't work.

I don't even know where to start. Just please Someone HELP ME.PLEASE..I think I might go in the corner and cry now.

---

### Post by ajmorris on 2008-12-03
> **earle79 said:**
> AJ my friend.  I have concluded that I must be a complete retard.  I let someone else talk me into using 8.10 again.  I downloaded #!CrunchBang Live CD.(this by the way is the 5th different distro).  I also found a 256MB RAM chip to install along with my 128MB.  Freakin ran awesome on Live CD.  And most of all everything worked, Wireless Lan, Sound,etc.  I was so happy I said what the hell just install it, cause it will run even better then right?Oh man, was I wrong.  

Im back to the blank screen, can't get to logon screen.  Can't get to terminal.  Tried to recover mode and fix x, same result.  Tried the nosplash on boot up.  I can't drop to shell, cause it ask for root password and the one I put in for logon at the install don't work.

I don't even know where to start. Just please Someone HELP ME.PLEASE..I think I might go in the corner and cry now.


lol, you're not a retard, everyone has to start somewhere ;)

This blank screen is a bit weird.. have you tried the noapic,nolapic boot options that i mentioned in one of my earlier posts, to add to /boot/grub/menu.lst ?

As for the root password, you are going to have to log into a live cd, and 'chroot' into your partition, to change it, since it is not working. A chroot, is just, where you mount your ubuntu partition, (say to /mnt/ubuntu) then run sudo chroot /mnt/ubuntu

You are now using your ubuntu environment when you do this. But, before i tell you how to reset your root password... i just need to check up on something... i seem to remember something about telling people how to reset their root password is against the UbuntuForums CoC... i just need to double check :)

Also, if the live cd booted... one should think that you should at least get to X trying to start... as the live cd doesnt have noapic,nolapic kernel paramaters specified... however, give it a shot anyway...

It is possible that your error *is* X trying to start, but your syslog that you posted earlier, gave no mention of X even trying to start, just a freeze, loading the kernel, as it didnt get all the way (same thing is experienced when trying to boot a system that needs noapic,nolapic but doesnt have them enabled)  SO, this problem is indeed strange... so give the kernel paramaters a shot, if they dont work, we'll try something else, im determined to rectify this issue :)


AJ

---

### Post by linux_tech on 2008-12-03
If you are unable to get to terminal, press ALT+Ctrl+F1 after drum sound to get to console
First show output of
```
sudo lshw -C video
```
```
free -m
```
```
cat /proc/sys/vm/swappiness
```
```
 xrandr
```

then attach file with output of:
```
sudo nano /etc/X11/xorg.conf
```

Did this work?- "sudo /etc/init.d/gdm start"

If you can get back to desktop
go to System->Administrator->Hardware Drivers -
Is there anything there listed for the video that can be activated?

---

### Post by linux_tech on 2008-12-03
With the lower RAM amt in the computer you should set up a swap file.
For the video screen issue, have you tried setting the driver to vesa or vga yet?

---

### Post by linux_tech on 2008-12-03
> **earle79 said:**
> AJ my friend.  I have concluded that I must be a complete retard.  I let someone else talk me into using 8.10 again.  I downloaded #!CrunchBang Live CD.(this by the way is the 5th different distro).  I also found a 256MB RAM chip to install along with my 128MB.  Freakin ran awesome on Live CD.  And most of all everything worked, Wireless Lan, Sound,etc.  I was so happy I said what the hell just install it, cause it will run even better then right?Oh man, was I wrong.  

Im back to the blank screen, can't get to logon screen.  Can't get to terminal.  Tried to recover mode and fix x, same result.  Tried the nosplash on boot up.  I can't drop to shell, cause it ask for root password and the one I put in for logon at the install don't work.

I don't even know where to start. Just please Someone HELP ME.PLEASE..I think I might go in the corner and cry now.

I'll check back later to see if there are any updates.

---

### Post by earle79 on 2008-12-03
ok, well now im having even more issues. i cant even seem to get any live cd to boot to the desktop. get to right before it at then just blank screen or blank screen with text cursor flashing at top left.

it only worked once but i ran recover mode ran xfix and typed startx then resume normal boot and it worked.  but the system locked up soon after booting fully.  i did manage to see that xconfig has my display as UNCLAIMED.

on other odd tidbit.  i found a disk that has some version of slax i think version 6.  i attempted it also, and when i ran command startx it gave me this error. 

EE) intel(0): Given bpp (32) is not supported by i810 driver

 then i found this...[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/178837]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/178837")

there is a patch for the driver on that site that is supposed to help that issue, should i choose to try it, how the help do i get it on my hard drive in the correct place, because when i get into recover mode and try to drop to shell it ask for a password, but my system password doesnot work.  

by the way, i want to say thank you to everyone one who is trying to help me.  i am trying to do everything that is suggested, but im kinda stuck right now.

---

### Post by ajmorris on 2008-12-04
yep, if you wanna apply the steps outlined in the bug report, you will have to boot into a live cd, and mount your ubuntu partition in it, and apply the steps.

I have checked it out also, it is not against the CoC for me to tell you how to reset your root password (it is discouraged, but since you cannot log into your recovery session, i believe it will be alright)

So, boot into a live cd, or another linux media of some kind.

Step 1)```
 sudo fdisk - l
```   (this will list the partitions on your computer, find whichever one is your ubuntu partition)

Step 2) ```
sudo mkdir /mnt/ubuntu
```

Step 3) ```
sudo mount /dev/sda# /mnt/ubuntu
```  (where '#' is the number fdisk -l tells you. NOTE, your partition may not be sda, it will depend on how many hard disks or devices you have)

Step 3) ```
sudo chroot /mnt/ubuntu
```

Step 4) ```
 export PS1="(CHROOT) $PS1"
``` (NOTE: this step is not required, it is just handy if you are going to be opening more than one terminal, and need to easilly determine which one is your chroot -- all it does, is add (CHROOT) out the front of your hostname)

Step 5) ```
passwd
```

This will prompt for you to provide a "new UNIX password". It will appear as though no characters are being entered, but they are, so just enter your desired password, and press enter, and the same for the repeat of it, and you're done, root password reset.


AJ

---

### Post by earle79 on 2008-12-04
> **ajmorris said:**
> [SIZE="1"]yep, if you wanna apply the steps outlined in the bug report, you will have to boot into a live cd, and mount your ubuntu partition in it, and apply the steps.

I have checked it out also, it is not against the CoC for me to tell you how to reset your root password (it is discouraged, but since you cannot log into your recovery session, i believe it will be alright)

So, boot into a live cd, or another linux media of some kind.

Step 1)```
 sudo fdisk - l
```   (this will list the partitions on your computer, find whichever one is your ubuntu partition)

Step 2) ```
sudo mkdir /mnt/ubuntu
```

Step 3) ```
sudo mount /dev/sda# /mnt/ubuntu
```  (where '#' is the number fdisk -l tells you. NOTE, your partition may not be sda, it will depend on how many hard disks or devices you have)

Step 3) ```
sudo chroot /mnt/ubuntu
```

Step 4) ```
 export PS1="(CHROOT) $PS1"
``` (NOTE: this step is not required, it is just handy if you are going to be opening more than one terminal, and need to easilly determine which one is your chroot -- all it does, is add (CHROOT) out the front of your hostname)

Step 5) ```
passwd
```

This will prompt for you to provide a "new UNIX password". It will appear as though no characters are being entered, but they are, so just enter your desired password, and press enter, and the same for the repeat of it, and you're done, root password reset.


AJ[/SIZE]

OK, I will do that, when I get home.  Just have one question about this though, does this do the same thing? this was from ubuntogeek.com

> If you forgot you password for your ubuntu system you can recover using the following steps
Turn your computer on.

Press ESC at the grub prompt.

Press e for edit.

Highlight the line that begins kernel ………, press e

Go to the very end of the line, add rw init=/bin/bash

press enter, then press b to boot your system.

Your system will boot up to a passwordless root shell.


---

### Post by ajmorris on 2008-12-04
> **earle79 said:**
> OK, I will do that, when I get home.  Just have one question about this though, does this do the same thing? this was from ubuntogeek.com

That is to edit your grub boot option on the fly, to go into a recovery mode. (it does not remain after a boot) (that same method was what you used to add noapic,nolapic earlier, except without the init=/bin/bash)  But yes, that is a way to access recovery mode without having to reset your password, as that will log into a paswordless shell


AJ

---

### Post by earle79 on 2008-12-04
ok guys.  i have some errors when trying to startx.  here is Xorg.0.log file.
```

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux LinuxBox 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Dec  5 17:10:17 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@0:1:0) Intel Corporation 82810 (CGC) Chipset Graphics Controller rev 3, Mem @ 0xf8000000/0, 0xf4000000/0
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched intel from file name intel.ids
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"

(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.4.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33,
	Mobile IntelÂ® GM45 Express Chipset,
	Intel Integrated Graphics Device, G45/G43, Q45/Q43
(II) Primary Device is: PCI 00@00:01:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) intel(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 16/16
(==) intel(0): Depth 16, (==) framebuffer bpp 16
(==) intel(0): RGB weight 565
(==) intel(0): Default visual is TrueColor
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"

(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) intel(0): initializing int10
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 1024 kB
(II) intel(0): VESA VBE OEM: Intel(R) 8xx Chipset Video BIOS
(II) intel(0): VESA VBE OEM Software Rev: 4.1
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(R) 8xx Chipset
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) intel(0): VESA VBE DDC supported
(II) intel(0): VESA VBE DDC Level 2
(II) intel(0): VESA VBE DDC transfer in appr. 1 sec.

```

here is my xorg.conf file
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

when i run lshw -C video it has display as UNCLAIMED product 82810 Chipset Graphics Controller it is an intel chip

i am looking up some of the error myself now, but maybe someone knows what i should do next.

just so you know also i never mentioned it before cause didnt think it was relevant but i have unplugged my kvm switch and tried to boot with NO success either way.

also i have found that now it doesnt matter for whatever reason i cant run any live cd anylonger.  the resetting password thing is not an option until i find a live cd that will boot.  to see any of these files i am using a rootless shell, dont know if that matters or not.

---

### Post by earle79 on 2008-12-04
just realized the log is not showing the agpgart error its says on my screen when i try to startx from rootless shell that /dev/agpgart not found

---

### Post by earle79 on 2008-12-05
ok, well I'm getting really frustrated. I can't seem to get anything to work.  The only live CD i can boot all the way to the desktop is ozOS.  I have just in the past week been able to boot and load several different versions.  I have CrunchBang installed, but I can't get to the desktop no matter what I try.  I can't even get Slax 6 to boot to the desktop.  What the heck am I doing wrong.

I wanted to just use the the ozOS xorg.conf but apparently it doesn't use that file.  I did manage to use my xubuntu alternate cd and booted to fix a broken system.  when I try to startx from there i get /dev/agpgart does not exist, and that it found screens but none usable.  what does that mean. it also says that when i try to use slax 6.

I think i am gonna try to just install ubuntu server and install flux or open box seeing as I can't get any live cd to work I still am in question as to whether i will be wasting my time.

I kinda liked the crunchbang I wish i could just get the live cd to run again.  or even LinuxMintFluxBox was cool too.

now that I have more RAM i should be able to use those light window managers.  I think its just now reading my monitor(hansol 701a) correctly or my onboard video(intel 82810).  maybe both.

i should mention that when i attempt to boot crunchbang live instead on logon i get a blank screen with a cursor blinking. dont know if that matters?

any suggestions? should i just give up?

---

### Post by earle79 on 2008-12-06
I got a question, about *"acpi=off"* and *"nolacpi"*.  would either one of those cause the keyboard to not work?  When I use those options and also along with *"nosplash"* when booting, I can get to a text based login but cant type.  I have tried turning *"legacy usb"* off and on both with same results.  I read something about that could cause mouse and keyboard not to work.  what does the option of *"quiet"* mean?

---

### Post by earle79 on 2008-12-07
**[SIZE="6"][COLOR="Red"]**UPDATE**[/COLOR][/SIZE]**

Well, again I guess I just live for brain pain but I completely reinstalled Xubuntu from alternate CD.  Installed great, no issues.  Rebooted right to the desktop, so I thought it was all good.  Like a retard, I said lets reboot to see if it works again.  That was a big NO! First thing I did was tried the acpi=off in grub.  It worked one time.  Now it won't.

So I tried recover mode, with and without acpi=off.  When I try startx it goes to the desktop. But my mouse does not work, the only thing I can do is press F1 and F2 and it goes to terminal and desktop.

Thes last couple of times I tried recover mode startx I get Internal Error - failed to initialize HAL when the desktop loads.  xfix didn't work.  the only message I get in the teminal when x starts is error setting MTRR base.

Can someone please help me.  I will try to see if i can get dmesg off there to this computer and also xorg.0.log too.

---

### Post by earle79 on 2008-12-08
ok guys, need a little help here.  Heres what I want to try.  Since obviously 8.10 will not run my video card, 8.04 won't run my wireless card.  I want to get everything related to the wireless card copied to a 8.04 install or everything video related copied to a 8.10 install.

First thing is this possible?  How can I find the driver that my wireless card is using?  will there be other files that go along with that?  I think this would be the easier route to go with if its gonna work.

Thanks to everyone so far that has attempted to help me.  This is a great forum. I will continue my quest for ubuntu sytem on this computer.  I also have an older laptop coming 2morrow so I get to have some more fun.

---

### Post by earle79 on 2008-12-08
[B][COLOR="Blue"][SIZE="4"]HA HA Well I can mark this thread solved.  It seems that I'm an idiot.  The one thing that I was trying to get to work the wireless card was causing all the issues.  I unplugged the Belkin F5D7000 V7, rebooted, and finally I see a login screen and a desktop after logging in.  A solid week of installing reinstalling, wrecking xorg files and all I had to do was unplug the pci card.  I should have know that, because that like PC repair 101.lol  Anyway now I have to figure out this card.

Thanks to everyone that has replied given advise.  It was real fun.[/SIZE][/COLOR][/B]

---

