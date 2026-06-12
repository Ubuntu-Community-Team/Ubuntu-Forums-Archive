---
title: "Ubuntu don't start"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by new123 on 2011-09-27
[FONT=monospace]I have just donwloaded Ubuntu _11.04_ and  burnt it to CD and installed it so it prompted me to restart PC and I did it.
So after reboot it showed me some GNU GRUB with list:
[/FONT]Ubuntu, with Linux 2.6.32-21-generic Ubuntu, with Linux 2.6.32-21-generic (recovery mode) Memory test (memtest 86+) Memory test (memtest 86+, serial console 115200) Microsoft Windows XP Professional (on /dev/sda1)

I selected first one on the list but then it show me default Ubuntu background (Yes I know how it looks like, I tryed Ubuntu b4 I installed it) with login window, I typed in my pass and then, I were waiting about 5-10 minutes, nothing happend... Restarted PC, and did like last time, but same situation..
When I run my Win XP nothing is wrong.. What to do?

---

### Post by The Cog on 2011-09-27
Once you are at the login screen, can you press Ctrl-Alt-F1 and get to a text login console? If so, try your login there (it doesn't echo *s as you enter your password, but carry on anyway). Can you successfully log in that way?

If you can, try these two commands:
```
sudo stop gdm
```
This first one will want your password again. It stops the graphical login manager. Then try:
```
startx
``` and see if this starts up a working GUI. 

I don't know where we go from there, but it may help to figure out what's wrong to know these answers.

---

### Post by seawolf167 on 2011-09-27
> **The Cog said:**
> If you can, try these two commands:
```
sudo **service gdm restart|stop|start**
```This first one will want your password again. It stops the graphical login manager. Then try:
```
startx
``` and see if this starts up a working GUI. 

I don't know where we go from there, but it may help to figure out what's wrong to know these answers.

See bold text to fix the above command

---

### Post by Blasphemist on 2011-09-27
When you say nothing happens after you enter your password at login, what do you mean exactly? Is there drive activity for a while at least? Does anything change on the display?

---

### Post by new123 on 2011-09-27
> **The Cog said:**
> Once you are at the login screen, can you press Ctrl-Alt-F1 and get to a text login console? If so, try your login there (it doesn't echo *s as you enter your password, but carry on anyway). Can you successfully log in that way?

If you can, try these two commands:
```
sudo stop gdm
```This first one will want your password again. It stops the graphical login manager. Then try:
```
startx
``` and see if this starts up a working GUI. 

I don't know where we go from there, but it may help to figure out what's wrong to know these answers.

I did all, login in Ctrl Alt F1 etc but same as I login normaly.

---

### Post by new123 on 2011-09-27
> **Blasphemist said:**
> When you say nothing happens after you enter your password at login, what do you mean exactly? Is there drive activity for a while at least? Does anything change on the display?

I enter my password in the login window and it disappears as it should I guess, but nothing else to appear. just a default background: [IMG]http://smartproteam.com/wp-content/uploads/2010/04/ubuntu-10.04.jpg[/IMG]

---

### Post by seawolf167 on 2011-09-27
> **new123 said:**
> I enter my password in the login window and it disappears as it should I guess, but nothing else to appear. just a default background

And hitting [CTRL][ALT][F1] doesn't bring up a black tty1 screen with a blinking cursor asking for your username/password?

---

### Post by new123 on 2011-09-27
> **seawolf167 said:**
> And hitting [CTRL][ALT][F1] doesn't bring up a black tty1 screen with a blinking cursor asking for your username/password?

CTRL ALT F1 Works, it brings black screen and I did like [[COLOR=#d40000]**The Cog**[/COLOR]]("http://ubuntuforums.org/member.php?u=437760") and _you_ said (logged in with name, pass and other stuff u wrote me to type), but when I done it all result is same as I just entered name/pass in login window without entering Ctrl Alt F1, just that backgrnd with nothing else around.

---

### Post by Blasphemist on 2011-09-27
Get the command prompt as described and then run these commands and then reboot.
```
gconftool-2 --recursive-unset /apps/compiz
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
```
Running these commands, one by one of course, will reset all settings in compiz.

---

### Post by new123 on 2011-09-27
> **Blasphemist said:**
> Get the command prompt as described and then run these commands and then reboot.
```
gconftool-2 --recursive-unset /apps/compiz
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
```Running these commands, one by one of course, will reset all settings in compiz.

.. and nothing :|

---

### Post by Blasphemist on 2011-09-27
Try Ctrl/Alt/F2 instead and see if there are messages. If there are, did anything error or what are the last few things that ran?

---

### Post by Blasphemist on 2011-09-27
I think this is an x server error and am hoping you'll get information about it. I have to go off line now for a while. This sticky thread likely has the troubleshooting you need but I am not familiar enough with the sequence to go right to it. [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

The OP of this sticky does appear to be on line if you want to try and pull him in.

---

### Post by MAFoElffen on 2011-09-28
> **new123 said:**
> [FONT=monospace]I have just donwloaded Ubuntu 10.04 and  burnt it to CD and installed it so it prompted me to restart PC and I did it.
So after reboot it showed me some GNU GRUB with list:
[/FONT]Ubuntu, with Linux 2.6.32-21-generic Ubuntu, with Linux 2.6.32-21-generic (recovery mode) Memory test (memtest 86+) Memory test (memtest 86+, serial console 115200) Microsoft Windows XP Professional (on /dev/sda1)

I selected first one on the list but then it show me default Ubuntu background (Yes I know how it looks like, I tryed Ubuntu b4 I installed it) with login window, I typed in my pass and then, I were waiting about 5-10 minutes, nothing happend... Restarted PC, and did like last time, but same situation..
When I run my Win XP nothing is wrong.. What to do?
_PART I_

Hi all... "new123" jumped over to the Graphics Resolution sticky refrering to the problem he's having in "this" thread.  I'm here to help...

Linux 2.6.32-21-generic was the original installed kernel from 10.04.3 LTS... some of the things that are being suggested are for 11.04 and don't have an effect on what he has installed now.  That also tels me that he has not had a chance to update/upgrade any files yet.

He's "new". but here's an explanation that all should be able to understand.  From his explanation and screen shot: 
 - It boots the kernel successfully.
 - X-Session starts
 - GDM starts
 --- Gnome Panels falls on it's face.

There are some fundamental questions that haven't been asked yet:
 - How much memory do you have installed?
 - Did you try booting the LiveCD and use the "try" menu option to verify that you can run Ubuntu 10.04?
 - What is Your Video GPU make and model?
> **Blasphemist said:**
> I think this is an x server error and am  hoping you'll get information about it. I have to go off line now for a  while. This sticky thread likely has the troubleshooting you need but I  am not familiar enough with the sequence to go right to it. [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

The OP of this sticky does appear to be on line if you want to try and pull him in.
Again, I'm [COLOR=Red]here[/COLOR] to help...

At the background image / after GDM, X is already started.  There doesn't seem to be the first part of the gnome panels even present.  
 - One way to check this would be to press <cntrl><alt><t> and see if the termeinal app comes up or to right-click on the background... To see if gnome is or is not loaded..  Then it would be a screen resolution problem... But since panels start at Left (0,0), I doubt that.
 - Next, post the /var/log/Xorg.0.log file to verify that Xloads correctly. I suspect it does, but...
  - Then post the /var/log/syslog to see where this is stopping and hanging in the vt7 session.

--------------------------------------------------------------------------------------------------[U]
PART II[/U]
Note- [COLOR=Red]Do not go on to Part II until you have posted the answers and logs from Part I[/COLOR]... and have some kind of feedback from me on those.  That may change what is below for a solution...

Compiz?
```

gconftool-2 --recursive-unset /apps/compiz*

```should have reset anythig in compiz back to defaults.  But there is also 
```

rm -rf .gconf

```which would delete all user changes and start fresh...
If those didn't work, you might try: 
```

compiz --replace

```If none of those work:
```

sudo stop gdm
sudo apt-get update
sudo apt-get remove --purge ubuntu-desktop
sudo apt-get install ubuntu-desktop
sudo apt-get upgrade
sudo startx

```Which would replace all the app's, gnome, compiz, metacity, xserver, etc...  Of course there is always trying a fresh reinstall and see if it gets to the same point....  It "was" a fresh install a few days ago, so he is not losing anything with that.

---

### Post by The Cog on 2011-09-28
> **seawolf167 said:**
> See bold text to fix the above commandIt didn't need fixing.

---

### Post by new123 on 2011-09-28
First of all just to say im sorry, I said I installed 10.04 but actually I installed 11.04 ver. of Ubuntu. &#711;&#711; :/

> **MAFoElffen said:**
> 

There are some fundamental questions that haven't been asked yet:
 - How much memory do you have installed?
 - Did you try booting the LiveCD and use the "try" menu option to verify that you can run Ubuntu 10.04?
 - What is Your Video GPU make and model?


- How much memory do you have installed? --- 512 MB RAM
 - Did you try booting the LiveCD and use the "try" menu option to verify that you can run Ubuntu 10.04? --- 11.04* --- Yes, it worked fine (Opening menus, changing background, FireFox, Internet, ..shutdown, restart etc.) so I installed it.

 - What is Your Video GPU make and model? ---

Card name: NVIDIA GeForce FX 5500
Manufacturer: NVIDIA
Chip type: GeForce FX 5500
Display Memory: 128.0 MB
Current Mode: 1280 x 1024 (32 bit) (60Hz)

> **MAFoElffen said:**
> 
At the background image / after GDM, X is already started.  There  doesn't seem to be the first part of the gnome panels even present.  
 - One way to check this would be to press  <cntrl><alt><t> and see if the termeinal app comes up  or to right-click on the background... To see if gnome is or is not  loaded..  Then it would be a screen resolution problem... But since  panels start at Left (0,0), I doubt that.
 - Next, post the /var/log/Xorg.0.log file to verify that Xloads correctly. I suspect it does, but...
  - Then post the /var/log/syslog to see where this is stopping and hanging in the vt7 session.


I were pressing right click and <cntrl><alt><t> but nothing happend.
How to open Xorg.0.log and syslog so I can post it here?

---

### Post by MAFoElffen on 2011-09-28
> **new123 said:**
> First of all just to say im sorry, I said I installed 10.04 but actually I installed 11.04 ver. of Ubuntu. &#711;&#711; :/

Card name: NVIDIA GeForce FX 5500
Manufacturer: NVIDIA
Chip type: GeForce FX 5500
Display Memory: 128.0 MB
Current Mode: 1280 x 1024 (32 bit) (60Hz)

I were pressing right click and <cntrl><alt><t> but nothing happend.

How to open Xorg.0.log and syslog so I can post it here?
I guess esiest fror you to post those 2 logs would be to boot on a LiveCD > Places > Home Folder > Filesystem > var > Log... Right Click on Syslog > Open with Gedit > Right Click > Select All > Copy...

Open Firefox > Go to this thread > Reply > Press the "#" on the posting tools toolbar / will insert the code tags > Right Click between the tags > paste...

Do same for Xorg.0.log...

Questions about that?

Thank you for the clarifications and info.  So you realize that your card won't run Unity and is on the cusp with having abilities  for "screen effects" right?

Hmm... I have an idea, but I'll have to test it on one of my test boxes here first... be right back.

EDIT-  In a terminal / console from your install, please post the results of 
```

compiz

```

---

### Post by LinuxFan999 on 2011-09-28
Try upgrading the RAM in your computer. You should have at least 1 Gigabyte when running Ubuntu 11.04.

---

### Post by new123 on 2011-09-28
> **MAFoElffen said:**
> I guess esiest fror you to post those 2 logs would be to boot on a LiveCD > Places > Home Folder > Filesystem > var > Log... Right Click on Syslog > Open with Gedit > Right Click > Select All > Copy...

Open Firefox > Go to this thread > Reply > Press the "#" on the posting tools toolbar / will insert the code tags > Right Click between the tags > paste...

Do same for Xorg.0.log...

Questions about that?

Thank you for the clarifications and info.  So you realize that your card won't run Unity and is on the cusp with having abilities  for "screen effects" right?

Hmm... I have an idea, but I'll have to test it on one of my test boxes here first... be right back.

EDIT-  In a terminal / console from your install, please post the results of 
```

compiz

```

Syslog
```

Sep 28 23:08:34 ubuntu kernel: imklog 4.6.4, log source = /proc/kmsg started.
Sep 28 23:08:34 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="1167" x-info="http://www.rsyslog.com"] (re)start
Sep 28 23:08:34 ubuntu rsyslogd: rsyslogd's groupid changed to 103
Sep 28 23:08:34 ubuntu rsyslogd: rsyslogd's userid changed to 101
Sep 28 23:08:34 ubuntu rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Sep 28 23:08:34 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Sep 28 23:08:34 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Sep 28 23:08:34 ubuntu kernel: [    0.000000] Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
Sep 28 23:08:34 ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Sep 28 23:08:34 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Sep 28 23:08:34 ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Sep 28 23:08:34 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Sep 28 23:08:34 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
Sep 28 23:08:34 ubuntu kernel: [    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
Sep 28 23:08:34 ubuntu kernel: [    0.000000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
Sep 28 23:08:34 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Sep 28 23:08:34 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Sep 28 23:08:34 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Sep 28 23:08:34 ubuntu kernel: [    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
Sep 28 23:08:34 ubuntu kernel: [    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
Sep 28 23:08:34 ubuntu kernel: [    0.000000] DMI 2.3 present.
Sep 28 23:08:34 ubuntu kernel: [    0.000000] DMI:    /K8T800-8237, BIOS FD 07/25/2005
Sep 28 23:08:34 ubuntu kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Sep 28 23:08:34 ubuntu kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Sep 28 23:08:34 ubuntu kernel: [    0.000000] last_pfn = 0x1fff0 max_arch_pfn = 0x100000
Sep 28 23:08:34 ubuntu kernel: [    0.000000] MTRR default type: uncachable
Sep 28 23:08:34 ubuntu kernel: [    0.000000] MTRR fixed ranges enabled:
Sep 28 23:08:34 ubuntu kernel: [    0.000000]   00000-9FFFF write-back
Sep 28 23:08:34 ubuntu kernel: [    0.000000]   A0000-BFFFF uncachable
Sep 28 23:08:34 ubuntu kernel: [    0.000000]   C0000-C7FFF write-protect
Sep 28 23:08:34 ubuntu kernel: [    0.000000]   C8000-CFFFF uncachable
Sep 28 23:08:34 ubuntu kernel: [    0.000000]   D0000-D7FFF write-back
Sep 28 23:08:34 ubuntu kernel: [    0.000000]   D8000-EFFFF uncachable
Sep 28 23:08:34 ubuntu kernel: [    0.000000]   F0000-FFFFF write-through
Sep 28 23:08:34 ubuntu kernel: [    0.000000] MTRR variable ranges enabled:
Sep 28 23:08:34 ubuntu kernel: [    0.000000]   0 base 0000000000 mask FFE0000000 write-back
Sep 28 23:08:34 ubuntu kernel: [    0.000000]   1 base 00F0000000 mask FFFC000000 write-combining
Sep 28 23:08:34 ubuntu kernel: [    0.000000]   2 disabled
Sep 28 23:08:34 ubuntu kernel: [    0.000000]   3 disabled
Sep 28 23:08:34 ubuntu kernel: [    0.000000]   4 disabled
Sep 28 23:08:34 ubuntu kernel: [    0.000000]   5 disabled
Sep 28 23:08:34 ubuntu kernel: [    0.000000]   6 disabled
Sep 28 23:08:34 ubuntu kernel: [    0.000000]   7 disabled
Sep 28 23:08:34 ubuntu kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Sep 28 23:08:34 ubuntu kernel: [    0.000000] found SMP MP-table at [c00f5130] f5130
Sep 28 23:08:34 ubuntu kernel: [    0.000000] initial memory mapped : 0 - 01c00000
Sep 28 23:08:34 ubuntu kernel: [    0.000000] init_memory_mapping: 0000000000000000-000000001fff0000
Sep 28 23:08:34 ubuntu kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Sep 28 23:08:34 ubuntu kernel: [    0.000000]  0000400000 - 001fc00000 page 2M
Sep 28 23:08:34 ubuntu kernel: [    0.000000]  001fc00000 - 001fff0000 page 4k
Sep 28 23:08:34 ubuntu kernel: [    0.000000] kernel direct mapping tables up to 1fff0000 @ 1bfb000-1c00000
Sep 28 23:08:34 ubuntu kernel: [    0.000000] RAMDISK: 1f32b000 - 1fff0000
Sep 28 23:08:34 ubuntu kernel: [    0.000000] ACPI: RSDP 000f6a90 00014 (v00 VIAK8 )
Sep 28 23:08:34 ubuntu kernel: [    0.000000] ACPI: RSDT 1fff3000 0002C (v01 VIAK8  AWRDACPI 42302E31 AWRD 01010101)
Sep 28 23:08:34 ubuntu kernel: [    0.000000] ACPI: FACP 1fff3040 00074 (v01 VIAK8  AWRDACPI 42302E31 AWRD 01010101)
Sep 28 23:08:34 ubuntu kernel: [    0.000000] ACPI: DSDT 1fff30c0 046FC (v01 VIAK8  AWRDACPI 00001000 MSFT 0100000C)
Sep 28 23:08:34 ubuntu kernel: [    0.000000] ACPI: FACS 1fff0000 00040
Sep 28 23:08:34 ubuntu kernel: [    0.000000] ACPI: APIC 1fff77c0 0005A (v01 VIAK8  AWRDACPI 42302E31 AWRD 01010101)
Sep 28 23:08:34 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Sep 28 23:08:34 ubuntu kernel: [    0.000000] 0MB HIGHMEM available.
Sep 28 23:08:34 ubuntu kernel: [    0.000000] 511MB LOWMEM available.
Sep 28 23:08:34 ubuntu kernel: [    0.000000]   mapped low ram: 0 - 1fff0000
Sep 28 23:08:34 ubuntu kernel: [    0.000000]   low ram: 0 - 1fff0000
Sep 28 23:08:34 ubuntu kernel: [    0.000000] Zone PFN ranges:
Sep 28 23:08:34 ubuntu kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Sep 28 23:08:34 ubuntu kernel: [    0.000000]   Normal   0x00001000 -> 0x0001fff0
Sep 28 23:08:34 ubuntu kernel: [    0.000000]   HighMem  empty
Sep 28 23:08:34 ubuntu kernel: [    0.000000] Movable zone start PFN for each node
Sep 28 23:08:34 ubuntu kernel: [    0.000000] early_node_map[2] active PFN ranges
Sep 28 23:08:34 ubuntu kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Sep 28 23:08:34 ubuntu kernel: [    0.000000]     0: 0x00000100 -> 0x0001fff0
Sep 28 23:08:34 ubuntu kernel: [    0.000000] On node 0 totalpages: 130943
Sep 28 23:08:34 ubuntu kernel: [    0.000000] free_area_init_node: node 0, pgdat c1784100, node_mem_map def2a200
Sep 28 23:08:34 ubuntu kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Sep 28 23:08:34 ubuntu kernel: [    0.000000]   DMA zone: 0 pages reserved
Sep 28 23:08:34 ubuntu kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Sep 28 23:08:34 ubuntu kernel: [    0.000000]   Normal zone: 992 pages used for memmap
Sep 28 23:08:34 ubuntu kernel: [    0.000000]   Normal zone: 125968 pages, LIFO batch:31
Sep 28 23:08:34 ubuntu kernel: [    0.000000] Using APIC driver default
Sep 28 23:08:34 ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Sep 28 23:08:34 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Sep 28 23:08:34 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Sep 28 23:08:34 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Sep 28 23:08:34 ubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Sep 28 23:08:34 ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
Sep 28 23:08:34 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Sep 28 23:08:34 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Sep 28 23:08:34 ubuntu kernel: [    0.000000] ACPI: IRQ0 used by override.
Sep 28 23:08:34 ubuntu kernel: [    0.000000] ACPI: IRQ2 used by override.
Sep 28 23:08:34 ubuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
Sep 28 23:08:34 ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Sep 28 23:08:34 ubuntu kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Sep 28 23:08:34 ubuntu kernel: [    0.000000] nr_irqs_gsi: 40
Sep 28 23:08:34 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 28 23:08:34 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Sep 28 23:08:34 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Sep 28 23:08:34 ubuntu kernel: [    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:dec00000)
Sep 28 23:08:34 ubuntu kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Sep 28 23:08:34 ubuntu kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
Sep 28 23:08:34 ubuntu kernel: [    0.000000] PERCPU: Embedded 13 pages/cpu @de800000 s28800 r0 d24448 u4194304
Sep 28 23:08:34 ubuntu kernel: [    0.000000] pcpu-alloc: s28800 r0 d24448 u4194304 alloc=1*4194304
Sep 28 23:08:34 ubuntu kernel: [    0.000000] pcpu-alloc: [0] 0 
Sep 28 23:08:34 ubuntu kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129919
Sep 28 23:08:34 ubuntu kernel: [    0.000000] Kernel command line: file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity
Sep 28 23:08:34 ubuntu kernel: [    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
Sep 28 23:08:34 ubuntu kernel: [    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Sep 28 23:08:34 ubuntu kernel: [    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Sep 28 23:08:34 ubuntu kernel: [    0.000000] Initializing CPU#0
Sep 28 23:08:34 ubuntu kernel: [    0.000000] allocated 2620800 bytes of page_cgroup
Sep 28 23:08:34 ubuntu kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Sep 28 23:08:34 ubuntu kernel: [    0.000000] Initializing HighMem for node 0 (00000000:00000000)
Sep 28 23:08:34 ubuntu kernel: [    0.000000] Memory: 494204k/524224k available (5188k kernel code, 29568k reserved, 2540k data, 700k init, 0k highmem)
Sep 28 23:08:34 ubuntu kernel: [    0.000000] virtual kernel memory layout:
Sep 28 23:08:34 ubuntu kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
Sep 28 23:08:34 ubuntu kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Sep 28 23:08:34 ubuntu kernel: [    0.000000]     vmalloc : 0xe07f0000 - 0xff7fe000   ( 496 MB)
Sep 28 23:08:34 ubuntu kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
Sep 28 23:08:34 ubuntu kernel: [    0.000000]       .init : 0xc178d000 - 0xc183c000   ( 700 kB)
Sep 28 23:08:34 ubuntu kernel: [    0.000000]       .data : 0xc15112a1 - 0xc178c480   (2540 kB)
Sep 28 23:08:34 ubuntu kernel: [    0.000000]       .text : 0xc1000000 - 0xc15112a1   (5188 kB)
Sep 28 23:08:34 ubuntu kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Sep 28 23:08:34 ubuntu kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Sep 28 23:08:34 ubuntu kernel: [    0.000000] Hierarchical RCU implementation.
Sep 28 23:08:34 ubuntu kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Sep 28 23:08:34 ubuntu kernel: [    0.000000]     RCU-based detection of stalled CPUs is disabled.
Sep 28 23:08:34 ubuntu kernel: [    0.000000] NR_IRQS:2304 nr_irqs:256 16
Sep 28 23:08:34 ubuntu kernel: [    0.000000] CPU 0 irqstacks, hard=de406000 soft=de408000
Sep 28 23:08:34 ubuntu kernel: [    0.000000] Console: colour VGA+ 80x25
Sep 28 23:08:34 ubuntu kernel: [    0.000000] console [tty0] enabled
Sep 28 23:08:34 ubuntu kernel: [    0.000000] Fast TSC calibration using PIT
Sep 28 23:08:34 ubuntu kernel: [    0.000000] Detected 1608.008 MHz processor.
Sep 28 23:08:34 ubuntu kernel: [    0.008003] Calibrating delay loop (skipped), value calculated using timer frequency.. 3216.01 BogoMIPS (lpj=6432032)
Sep 28 23:08:34 ubuntu kernel: [    0.008012] pid_max: default: 32768 minimum: 301
Sep 28 23:08:34 ubuntu kernel: [    0.008050] Security Framework initialized
Sep 28 23:08:34 ubuntu kernel: [    0.008083] AppArmor: AppArmor initialized
Sep 28 23:08:34 ubuntu kernel: [    0.008086] Yama: becoming mindful.
Sep 28 23:08:34 ubuntu kernel: [    0.008176] Mount-cache hash table entries: 512
Sep 28 23:08:34 ubuntu kernel: [    0.008353] Initializing cgroup subsys ns
Sep 28 23:08:34 ubuntu kernel: [    0.008358] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
Sep 28 23:08:34 ubuntu kernel: [    0.008364] Initializing cgroup subsys cpuacct
Sep 28 23:08:34 ubuntu kernel: [    0.008372] Initializing cgroup subsys memory
Sep 28 23:08:34 ubuntu kernel: [    0.008386] Initializing cgroup subsys devices
Sep 28 23:08:34 ubuntu kernel: [    0.008390] Initializing cgroup subsys freezer
Sep 28 23:08:34 ubuntu kernel: [    0.008394] Initializing cgroup subsys net_cls
Sep 28 23:08:34 ubuntu kernel: [    0.008398] Initializing cgroup subsys blkio
Sep 28 23:08:34 ubuntu kernel: [    0.008445] mce: CPU supports 5 MCE banks
Sep 28 23:08:34 ubuntu kernel: [    0.009191] SMP alternatives: switching to UP code
Sep 28 23:08:34 ubuntu kernel: [    0.021003] Freeing SMP alternatives: 20k freed
Sep 28 23:08:34 ubuntu kernel: [    0.021027] ACPI: Core revision 20110112
Sep 28 23:08:34 ubuntu kernel: [    0.027389] ftrace: allocating 23640 entries in 47 pages
Sep 28 23:08:34 ubuntu kernel: [    0.028104] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Sep 28 23:08:34 ubuntu kernel: [    0.032212] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
Sep 28 23:08:34 ubuntu kernel: [    0.071895] CPU0: AMD Sempron(tm) Processor 2800+ stepping 02
Sep 28 23:08:34 ubuntu kernel: [    0.072003] Performance Events: AMD PMU driver.
Sep 28 23:08:34 ubuntu kernel: [    0.072003] ... version:                0
Sep 28 23:08:34 ubuntu kernel: [    0.072003] ... bit width:              48
Sep 28 23:08:34 ubuntu kernel: [    0.072003] ... generic registers:      4
Sep 28 23:08:34 ubuntu kernel: [    0.072003] ... value mask:             0000ffffffffffff
Sep 28 23:08:34 ubuntu kernel: [    0.072003] ... max period:             00007fffffffffff
Sep 28 23:08:34 ubuntu kernel: [    0.072003] ... fixed-purpose events:   0
Sep 28 23:08:34 ubuntu kernel: [    0.072003] ... event mask:             000000000000000f
Sep 28 23:08:34 ubuntu kernel: [    0.072003] Brought up 1 CPUs
Sep 28 23:08:34 ubuntu kernel: [    0.072003] Total of 1 processors activated (3216.01 BogoMIPS).
Sep 28 23:08:34 ubuntu kernel: [    0.072003] devtmpfs: initialized
Sep 28 23:08:34 ubuntu kernel: [    0.072003] print_constraints: dummy: 
Sep 28 23:08:34 ubuntu kernel: [    0.072003] Time: 23:07:04  Date: 09/28/11
Sep 28 23:08:34 ubuntu kernel: [    0.072003] NET: Registered protocol family 16
Sep 28 23:08:34 ubuntu kernel: [    0.072003] EISA bus registered
Sep 28 23:08:34 ubuntu kernel: [    0.072003] node 0 link 0: io port [1000, fffff]
Sep 28 23:08:34 ubuntu kernel: [    0.072003] TOM: 0000000020000000 aka 512M
Sep 28 23:08:34 ubuntu kernel: [    0.072003] node 0 link 0: mmio [a0000, bffff]
Sep 28 23:08:34 ubuntu kernel: [    0.072003] node 0 link 0: mmio [20000000, ffb7ffff]
Sep 28 23:08:34 ubuntu kernel: [    0.072003] bus: [00, ff] on node 0 link 0
Sep 28 23:08:34 ubuntu kernel: [    0.072003] bus: 00 index 0 [io  0x0000-0xffff]
Sep 28 23:08:34 ubuntu kernel: [    0.072003] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
Sep 28 23:08:34 ubuntu kernel: [    0.072003] bus: 00 index 2 [mem 0x20000000-0xffffffff]
Sep 28 23:08:34 ubuntu kernel: [    0.072003] ACPI: bus type pci registered
Sep 28 23:08:34 ubuntu kernel: [    0.079081] PCI: PCI BIOS revision 2.10 entry at 0xfb320, last bus=1
Sep 28 23:08:34 ubuntu kernel: [    0.079084] PCI: Using configuration type 1 for base access
Sep 28 23:08:34 ubuntu kernel: [    0.080539] bio: create slab <bio-0> at 0
Sep 28 23:08:34 ubuntu kernel: [    0.081654] ACPI: EC: Look up EC in DSDT
Sep 28 23:08:34 ubuntu kernel: [    0.085416] ACPI: Interpreter enabled
Sep 28 23:08:34 ubuntu kernel: [    0.085424] ACPI: (supports S0 S1 S4 S5)
Sep 28 23:08:34 ubuntu kernel: [    0.085449] ACPI: Using IOAPIC for interrupt routing
Sep 28 23:08:34 ubuntu kernel: [    0.090098] ACPI: No dock devices found.
Sep 28 23:08:34 ubuntu kernel: [    0.090102] HEST: Table not found.
Sep 28 23:08:34 ubuntu kernel: [    0.090107] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
Sep 28 23:08:34 ubuntu kernel: [    0.090179] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Sep 28 23:08:34 ubuntu kernel: [    0.090311] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
Sep 28 23:08:34 ubuntu kernel: [    0.090315] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
Sep 28 23:08:34 ubuntu kernel: [    0.090319] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
Sep 28 23:08:34 ubuntu kernel: [    0.090323] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff] (ignored)
Sep 28 23:08:34 ubuntu kernel: [    0.090327] pci_root PNP0A03:00: host bridge window [mem 0x20000000-0xfebfffff] (ignored)
Sep 28 23:08:34 ubuntu kernel: [    0.090351] pci 0000:00:00.0: [1106:0282] type 0 class 0x000600
Sep 28 23:08:34 ubuntu kernel: [    0.090362] pci 0000:00:00.0: reg 10: [mem 0xf0000000-0xf3ffffff pref]
Sep 28 23:08:34 ubuntu kernel: [    0.090431] pci 0000:00:00.1: [1106:1282] type 0 class 0x000600
Sep 28 23:08:34 ubuntu kernel: [    0.090472] pci 0000:00:00.2: [1106:2282] type 0 class 0x000600
Sep 28 23:08:34 ubuntu kernel: [    0.090513] pci 0000:00:00.3: [1106:3282] type 0 class 0x000600
Sep 28 23:08:34 ubuntu kernel: [    0.090553] pci 0000:00:00.4: [1106:4282] type 0 class 0x000600
Sep 28 23:08:34 ubuntu kernel: [    0.090598] pci 0000:00:00.7: [1106:7282] type 0 class 0x000600
Sep 28 23:08:34 ubuntu kernel: [    0.090641] pci 0000:00:01.0: [1106:b188] type 1 class 0x000604
Sep 28 23:08:34 ubuntu kernel: [    0.090680] pci 0000:00:01.0: supports D1
Sep 28 23:08:34 ubuntu kernel: [    0.090711] pci 0000:00:0b.0: [1057:3052] type 0 class 0x000703
Sep 28 23:08:34 ubuntu kernel: [    0.090730] pci 0000:00:0b.0: reg 10: [mem 0xf6000000-0xf6000fff]
Sep 28 23:08:34 ubuntu kernel: [    0.090741] pci 0000:00:0b.0: reg 14: [io  0x9000-0x90ff]
Sep 28 23:08:34 ubuntu kernel: [    0.090797] pci 0000:00:0b.0: PME# supported from D0 D3hot D3cold
Sep 28 23:08:34 ubuntu kernel: [    0.090802] pci 0000:00:0b.0: PME# disabled
Sep 28 23:08:34 ubuntu kernel: [    0.091179] pci 0000:00:0f.0: [1106:3149] type 0 class 0x000104
Sep 28 23:08:34 ubuntu kernel: [    0.091201] pci 0000:00:0f.0: reg 10: [io  0x9400-0x9407]
Sep 28 23:08:34 ubuntu kernel: [    0.091212] pci 0000:00:0f.0: reg 14: [io  0x9800-0x9803]
Sep 28 23:08:34 ubuntu kernel: [    0.091222] pci 0000:00:0f.0: reg 18: [io  0x9c00-0x9c07]
Sep 28 23:08:34 ubuntu kernel: [    0.091232] pci 0000:00:0f.0: reg 1c: [io  0xa000-0xa003]
Sep 28 23:08:34 ubuntu kernel: [    0.091242] pci 0000:00:0f.0: reg 20: [io  0xa400-0xa40f]
Sep 28 23:08:34 ubuntu kernel: [    0.091252] pci 0000:00:0f.0: reg 24: [io  0xa800-0xa8ff]
Sep 28 23:08:34 ubuntu kernel: [    0.091300] pci 0000:00:0f.1: [1106:0571] type 0 class 0x000101
Sep 28 23:08:34 ubuntu kernel: [    0.091344] pci 0000:00:0f.1: reg 20: [io  0xac00-0xac0f]
Sep 28 23:08:34 ubuntu kernel: [    0.091399] pci 0000:00:10.0: [1106:3038] type 0 class 0x000c03
Sep 28 23:08:34 ubuntu kernel: [    0.091441] pci 0000:00:10.0: reg 20: [io  0xb000-0xb01f]
Sep 28 23:08:34 ubuntu kernel: [    0.091471] pci 0000:00:10.0: supports D1 D2
Sep 28 23:08:34 ubuntu kernel: [    0.091475] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
Sep 28 23:08:34 ubuntu kernel: [    0.091480] pci 0000:00:10.0: PME# disabled
Sep 28 23:08:34 ubuntu kernel: [    0.091498] pci 0000:00:10.1: [1106:3038] type 0 class 0x000c03
Sep 28 23:08:34 ubuntu kernel: [    0.091539] pci 0000:00:10.1: reg 20: [io  0xb400-0xb41f]
Sep 28 23:08:34 ubuntu kernel: [    0.091570] pci 0000:00:10.1: supports D1 D2
Sep 28 23:08:34 ubuntu kernel: [    0.091573] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
Sep 28 23:08:34 ubuntu kernel: [    0.091577] pci 0000:00:10.1: PME# disabled
Sep 28 23:08:34 ubuntu kernel: [    0.091595] pci 0000:00:10.2: [1106:3038] type 0 class 0x000c03
Sep 28 23:08:34 ubuntu kernel: [    0.091637] pci 0000:00:10.2: reg 20: [io  0xb800-0xb81f]
Sep 28 23:08:34 ubuntu kernel: [    0.091667] pci 0000:00:10.2: supports D1 D2
Sep 28 23:08:34 ubuntu kernel: [    0.091670] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
Sep 28 23:08:34 ubuntu kernel: [    0.091675] pci 0000:00:10.2: PME# disabled
Sep 28 23:08:34 ubuntu kernel: [    0.091698] pci 0000:00:10.3: [1106:3038] type 0 class 0x000c03
Sep 28 23:08:34 ubuntu kernel: [    0.091739] pci 0000:00:10.3: reg 20: [io  0xbc00-0xbc1f]
Sep 28 23:08:34 ubuntu kernel: [    0.091770] pci 0000:00:10.3: supports D1 D2
Sep 28 23:08:34 ubuntu kernel: [    0.091773] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
Sep 28 23:08:34 ubuntu kernel: [    0.091777] pci 0000:00:10.3: PME# disabled
Sep 28 23:08:34 ubuntu kernel: [    0.091795] pci 0000:00:10.4: [1106:3104] type 0 class 0x000c03
Sep 28 23:08:34 ubuntu kernel: [    0.091811] pci 0000:00:10.4: reg 10: [mem 0xf6001000-0xf60010ff]
Sep 28 23:08:34 ubuntu kernel: [    0.091867] pci 0000:00:10.4: supports D1 D2
Sep 28 23:08:34 ubuntu kernel: [    0.091870] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
Sep 28 23:08:34 ubuntu kernel: [    0.091875] pci 0000:00:10.4: PME# disabled
Sep 28 23:08:34 ubuntu kernel: [    0.091896] pci 0000:00:11.0: [1106:3227] type 0 class 0x000601
Sep 28 23:08:34 ubuntu kernel: [    0.091953] HPET not enabled in BIOS. You might try hpet=force boot option
Sep 28 23:08:34 ubuntu kernel: [    0.092014] pci 0000:00:11.5: [1106:3059] type 0 class 0x000401
Sep 28 23:08:34 ubuntu kernel: [    0.092031] pci 0000:00:11.5: reg 10: [io  0xc000-0xc0ff]
Sep 28 23:08:34 ubuntu kernel: [    0.092089] pci 0000:00:11.5: supports D1 D2
Sep 28 23:08:34 ubuntu kernel: [    0.092111] pci 0000:00:13.0: [10ec:8139] type 0 class 0x000200
Sep 28 23:08:34 ubuntu kernel: [    0.092127] pci 0000:00:13.0: reg 10: [io  0xc400-0xc4ff]
Sep 28 23:08:34 ubuntu kernel: [    0.092137] pci 0000:00:13.0: reg 14: [mem 0xf6002000-0xf60020ff]
Sep 28 23:08:34 ubuntu kernel: [    0.092188] pci 0000:00:13.0: supports D1 D2
Sep 28 23:08:34 ubuntu kernel: [    0.092191] pci 0000:00:13.0: PME# supported from D1 D2 D3hot D3cold
Sep 28 23:08:34 ubuntu kernel: [    0.092196] pci 0000:00:13.0: PME# disabled
Sep 28 23:08:34 ubuntu kernel: [    0.092213] pci 0000:00:18.0: [1022:1100] type 0 class 0x000600
Sep 28 23:08:34 ubuntu kernel: [    0.092237] pci 0000:00:18.1: [1022:1101] type 0 class 0x000600
Sep 28 23:08:34 ubuntu kernel: [    0.092257] pci 0000:00:18.2: [1022:1102] type 0 class 0x000600
Sep 28 23:08:34 ubuntu kernel: [    0.092278] pci 0000:00:18.3: [1022:1103] type 0 class 0x000600
Sep 28 23:08:34 ubuntu kernel: [    0.092302] PCI: peer root bus 00 res updated from pci conf
Sep 28 23:08:34 ubuntu kernel: [    0.092338] pci 0000:01:00.0: [10de:0326] type 0 class 0x000300
Sep 28 23:08:34 ubuntu kernel: [    0.092351] pci 0000:01:00.0: reg 10: [mem 0xf4000000-0xf4ffffff]
Sep 28 23:08:34 ubuntu kernel: [    0.092360] pci 0000:01:00.0: reg 14: [mem 0xe8000000-0xefffffff pref]
Sep 28 23:08:34 ubuntu kernel: [    0.092385] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Sep 28 23:08:34 ubuntu kernel: [    0.092436] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Sep 28 23:08:34 ubuntu kernel: [    0.092441] pci 0000:00:01.0:   bridge window [io  0xf000-0x0000] (disabled)
Sep 28 23:08:34 ubuntu kernel: [    0.092447] pci 0000:00:01.0:   bridge window [mem 0xf4000000-0xf5ffffff]
Sep 28 23:08:34 ubuntu kernel: [    0.092453] pci 0000:00:01.0:   bridge window [mem 0xe8000000-0xefffffff pref]
Sep 28 23:08:34 ubuntu kernel: [    0.092461] pci_bus 0000:00: on NUMA node 0
Sep 28 23:08:34 ubuntu kernel: [    0.092470] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Sep 28 23:08:34 ubuntu kernel: [    0.121585] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
Sep 28 23:08:34 ubuntu kernel: [    0.121693] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
Sep 28 23:08:34 ubuntu kernel: [    0.121799] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12)
Sep 28 23:08:34 ubuntu kernel: [    0.121903] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *5
Sep 28 23:08:34 ubuntu kernel: [    0.121982] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Sep 28 23:08:34 ubuntu kernel: [    0.122058] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Sep 28 23:08:34 ubuntu kernel: [    0.122133] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Sep 28 23:08:34 ubuntu kernel: [    0.122207] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Sep 28 23:08:34 ubuntu kernel: [    0.122339] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0
Sep 28 23:08:34 ubuntu kernel: [    0.122469] ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0
Sep 28 23:08:34 ubuntu kernel: [    0.122620] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0
Sep 28 23:08:34 ubuntu kernel: [    0.122750] ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0
Sep 28 23:08:34 ubuntu kernel: [    0.122905] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Sep 28 23:08:34 ubuntu kernel: [    0.122909] vgaarb: loaded
Sep 28 23:08:34 ubuntu kernel: [    0.123219] SCSI subsystem initialized
Sep 28 23:08:34 ubuntu kernel: [    0.123308] libata version 3.00 loaded.
Sep 28 23:08:34 ubuntu kernel: [    0.123376] usbcore: registered new interface driver usbfs
Sep 28 23:08:34 ubuntu kernel: [    0.123392] usbcore: registered new interface driver hub
Sep 28 23:08:34 ubuntu kernel: [    0.123424] usbcore: registered new device driver usb
Sep 28 23:08:34 ubuntu kernel: [    0.123580] wmi: Mapper loaded
Sep 28 23:08:34 ubuntu kernel: [    0.123582] PCI: Using ACPI for IRQ routing
Sep 28 23:08:34 ubuntu kernel: [    0.123588] PCI: pci_cache_line_size set to 64 bytes
Sep 28 23:08:34 ubuntu kernel: [    0.123673] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
Sep 28 23:08:34 ubuntu kernel: [    0.123677] reserve RAM buffer: 000000001fff0000 - 000000001fffffff 
Sep 28 23:08:34 ubuntu kernel: [    0.123814] NetLabel: Initializing
Sep 28 23:08:34 ubuntu kernel: [    0.123817] NetLabel:  domain hash size = 128
Sep 28 23:08:34 ubuntu kernel: [    0.123819] NetLabel:  protocols = UNLABELED CIPSOv4
Sep 28 23:08:34 ubuntu kernel: [    0.123835] NetLabel:  unlabeled traffic allowed by default
Sep 28 23:08:34 ubuntu kernel: [    0.134224] AppArmor: AppArmor Filesystem Enabled
Sep 28 23:08:34 ubuntu kernel: [    0.134269] pnp: PnP ACPI init
Sep 28 23:08:34 ubuntu kernel: [    0.134295] ACPI: bus type pnp registered
Sep 28 23:08:34 ubuntu kernel: [    0.134507] pnp 00:00: [mem 0x000d0000-0x000d7fff]
Sep 28 23:08:34 ubuntu kernel: [    0.134510] pnp 00:00: [mem 0x000f0000-0x000f7fff]
Sep 28 23:08:34 ubuntu kernel: [    0.134514] pnp 00:00: [mem 0x000f8000-0x000fbfff]
Sep 28 23:08:34 ubuntu kernel: [    0.134517] pnp 00:00: [mem 0x000fc000-0x000fffff]
Sep 28 23:08:34 ubuntu kernel: [    0.134520] pnp 00:00: [mem 0x1fff0000-0x1fffffff]
Sep 28 23:08:34 ubuntu kernel: [    0.134523] pnp 00:00: [mem 0xffff0000-0xffffffff]
Sep 28 23:08:34 ubuntu kernel: [    0.134527] pnp 00:00: [mem 0x00000000-0x0009ffff]
Sep 28 23:08:34 ubuntu kernel: [    0.134530] pnp 00:00: [mem 0x00100000-0x1ffeffff]
Sep 28 23:08:34 ubuntu kernel: [    0.134533] pnp 00:00: [mem 0xfec00000-0xfec00fff]
Sep 28 23:08:34 ubuntu kernel: [    0.134541] pnp 00:00: [mem 0xfee00000-0xfee00fff]
Sep 28 23:08:34 ubuntu kernel: [    0.134544] pnp 00:00: [mem 0xfff80000-0xfffeffff]
Sep 28 23:08:34 ubuntu kernel: [    0.134623] system 00:00: [mem 0x000d0000-0x000d7fff] has been reserved
Sep 28 23:08:34 ubuntu kernel: [    0.134627] system 00:00: [mem 0x000f0000-0x000f7fff] could not be reserved
Sep 28 23:08:34 ubuntu kernel: [    0.134632] system 00:00: [mem 0x000f8000-0x000fbfff] could not be reserved
Sep 28 23:08:34 ubuntu kernel: [    0.134636] system 00:00: [mem 0x000fc000-0x000fffff] could not be reserved
Sep 28 23:08:34 ubuntu kernel: [    0.134640] system 00:00: [mem 0x1fff0000-0x1fffffff] could not be reserved
Sep 28 23:08:34 ubuntu kernel: [    0.134644] system 00:00: [mem 0xffff0000-0xffffffff] has been reserved
Sep 28 23:08:34 ubuntu kernel: [    0.134649] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
Sep 28 23:08:34 ubuntu kernel: [    0.134653] system 00:00: [mem 0x00100000-0x1ffeffff] could not be reserved
Sep 28 23:08:34 ubuntu kernel: [    0.134657] system 00:00: [mem 0xfec00000-0xfec00fff] could not be reserved
Sep 28 23:08:34 ubuntu kernel: [    0.134662] system 00:00: [mem 0xfee00000-0xfee00fff] has been reserved
Sep 28 23:08:34 ubuntu kernel: [    0.134666] system 00:00: [mem 0xfff80000-0xfffeffff] has been reserved
Sep 28 23:08:34 ubuntu kernel: [    0.134672] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
Sep 28 23:08:34 ubuntu kernel: [    0.134740] pnp 00:01: [bus 00-ff]
Sep 28 23:08:34 ubuntu kernel: [    0.134744] pnp 00:01: [io  0x0cf8-0x0cff]
Sep 28 23:08:34 ubuntu kernel: [    0.134747] pnp 00:01: [io  0x0000-0x0cf7 window]
Sep 28 23:08:34 ubuntu kernel: [    0.134751] pnp 00:01: [io  0x0d00-0xffff window]
Sep 28 23:08:34 ubuntu kernel: [    0.134754] pnp 00:01: [mem 0x000a0000-0x000bffff window]
Sep 28 23:08:34 ubuntu kernel: [    0.134757] pnp 00:01: [mem 0x000c0000-0x000dffff window]
Sep 28 23:08:34 ubuntu kernel: [    0.134761] pnp 00:01: [mem 0x20000000-0xfebfffff window]
Sep 28 23:08:34 ubuntu kernel: [    0.134814] pnp 00:01: Plug and Play ACPI device, IDs PNP0a03 (active)
Sep 28 23:08:34 ubuntu kernel: [    0.134838] pnp 00:02: [io  0x4000-0x407f]
Sep 28 23:08:34 ubuntu kernel: [    0.134841] pnp 00:02: [io  0x40f0-0x40ff]
Sep 28 23:08:34 ubuntu kernel: [    0.134844] pnp 00:02: [io  0x5000-0x500f]
Sep 28 23:08:34 ubuntu kernel: [    0.134898] system 00:02: [io  0x4000-0x407f] has been reserved
Sep 28 23:08:34 ubuntu kernel: [    0.134902] system 00:02: [io  0x40f0-0x40ff] has been reserved
Sep 28 23:08:34 ubuntu kernel: [    0.134905] system 00:02: [io  0x5000-0x500f] has been reserved
Sep 28 23:08:34 ubuntu kernel: [    0.134910] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
Sep 28 23:08:34 ubuntu kernel: [    0.135290] pnp 00:03: [io  0x0010-0x001f]
Sep 28 23:08:34 ubuntu kernel: [    0.135294] pnp 00:03: [io  0x0022-0x003f]
Sep 28 23:08:34 ubuntu kernel: [    0.135297] pnp 00:03: [io  0x0044-0x005f]
Sep 28 23:08:34 ubuntu kernel: [    0.135299] pnp 00:03: [io  0x0062-0x0063]
Sep 28 23:08:34 ubuntu kernel: [    0.135302] pnp 00:03: [io  0x0065-0x006f]
Sep 28 23:08:34 ubuntu kernel: [    0.135305] pnp 00:03: [io  0x0074-0x007f]
Sep 28 23:08:34 ubuntu kernel: [    0.135308] pnp 00:03: [io  0x0091-0x0093]
Sep 28 23:08:34 ubuntu kernel: [    0.135311] pnp 00:03: [io  0x00a2-0x00bf]
Sep 28 23:08:34 ubuntu kernel: [    0.135314] pnp 00:03: [io  0x00e0-0x00ef]
Sep 28 23:08:34 ubuntu kernel: [    0.135317] pnp 00:03: [io  0x04d0-0x04d1]
Sep 28 23:08:34 ubuntu kernel: [    0.135320] pnp 00:03: [io  0x0290-0x029f]
Sep 28 23:08:34 ubuntu kernel: [    0.135323] pnp 00:03: [io  0x0800-0x0805]
Sep 28 23:08:34 ubuntu kernel: [    0.135396] system 00:03: [io  0x04d0-0x04d1] has been reserved
Sep 28 23:08:34 ubuntu kernel: [    0.135400] system 00:03: [io  0x0290-0x029f] has been reserved
Sep 28 23:08:34 ubuntu kernel: [    0.135404] system 00:03: [io  0x0800-0x0805] has been reserved
Sep 28 23:08:34 ubuntu kernel: [    0.135409] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
Sep 28 23:08:34 ubuntu kernel: [    0.135432] pnp 00:04: [dma 4]
Sep 28 23:08:34 ubuntu kernel: [    0.135435] pnp 00:04: [io  0x0000-0x000f]
Sep 28 23:08:34 ubuntu kernel: [    0.135438] pnp 00:04: [io  0x0080-0x0090]
Sep 28 23:08:34 ubuntu kernel: [    0.135441] pnp 00:04: [io  0x0094-0x009f]
Sep 28 23:08:34 ubuntu kernel: [    0.135443] pnp 00:04: [io  0x00c0-0x00df]
Sep 28 23:08:34 ubuntu kernel: [    0.135490] pnp 00:04: Plug and Play ACPI device, IDs PNP0200 (active)
Sep 28 23:08:34 ubuntu kernel: [    0.135505] pnp 00:05: [io  0x0070-0x0073]
Sep 28 23:08:34 ubuntu kernel: [    0.135520] pnp 00:05: [irq 8]
Sep 28 23:08:34 ubuntu kernel: [    0.135562] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
Sep 28 23:08:34 ubuntu kernel: [    0.135574] pnp 00:06: [io  0x0061]
Sep 28 23:08:34 ubuntu kernel: [    0.135616] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
Sep 28 23:08:34 ubuntu kernel: [    0.135628] pnp 00:07: [io  0x00f0-0x00ff]
Sep 28 23:08:34 ubuntu kernel: [    0.135635] pnp 00:07: [irq 13]
Sep 28 23:08:34 ubuntu kernel: [    0.135678] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
Sep 28 23:08:34 ubuntu kernel: [    0.135826] pnp 00:08: [io  0x03f0-0x03f5]
Sep 28 23:08:34 ubuntu kernel: [    0.135829] pnp 00:08: [io  0x03f7]
Sep 28 23:08:34 ubuntu kernel: [    0.135836] pnp 00:08: [irq 6]
Sep 28 23:08:34 ubuntu kernel: [    0.135839] pnp 00:08: [dma 2]
Sep 28 23:08:34 ubuntu kernel: [    0.135899] pnp 00:08: Plug and Play ACPI device, IDs PNP0700 (active)
Sep 28 23:08:34 ubuntu kernel: [    0.136120] pnp 00:09: [io  0x03f8-0x03ff]
Sep 28 23:08:34 ubuntu kernel: [    0.136127] pnp 00:09: [irq 4]
Sep 28 23:08:34 ubuntu kernel: [    0.136209] pnp 00:09: Plug and Play ACPI device, IDs PNP0501 (active)
Sep 28 23:08:34 ubuntu kernel: [    0.136423] pnp 00:0a: [io  0x02f8-0x02ff]
Sep 28 23:08:34 ubuntu kernel: [    0.136430] pnp 00:0a: [irq 3]
Sep 28 23:08:34 ubuntu kernel: [    0.136504] pnp 00:0a: Plug and Play ACPI device, IDs PNP0501 (active)
Sep 28 23:08:34 ubuntu kernel: [    0.136797] pnp 00:0b: [io  0x0378-0x037f]
Sep 28 23:08:34 ubuntu kernel: [    0.136807] pnp 00:0b: [irq 7]
Sep 28 23:08:34 ubuntu kernel: [    0.136875] pnp 00:0b: Plug and Play ACPI device, IDs PNP0400 (active)
Sep 28 23:08:34 ubuntu kernel: [    0.137076] pnp: PnP ACPI: found 12 devices
Sep 28 23:08:34 ubuntu kernel: [    0.137079] ACPI: ACPI bus type pnp unregistered
Sep 28 23:08:34 ubuntu kernel: [    0.137084] PnPBIOS: Disabled by ACPI PNP
Sep 28 23:08:34 ubuntu kernel: [    0.174029] Switching to clocksource acpi_pm
Sep 28 23:08:34 ubuntu kernel: [    0.174084] pci 0000:01:00.0: BAR 6: assigned [mem 0xf5000000-0xf501ffff pref]
Sep 28 23:08:34 ubuntu kernel: [    0.174089] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Sep 28 23:08:34 ubuntu kernel: [    0.174092] pci 0000:00:01.0:   bridge window [io  disabled]
Sep 28 23:08:34 ubuntu kernel: [    0.174099] pci 0000:00:01.0:   bridge window [mem 0xf4000000-0xf5ffffff]
Sep 28 23:08:34 ubuntu kernel: [    0.174104] pci 0000:00:01.0:   bridge window [mem 0xe8000000-0xefffffff pref]
Sep 28 23:08:34 ubuntu kernel: [    0.174119] pci 0000:00:01.0: setting latency timer to 64
Sep 28 23:08:34 ubuntu kernel: [    0.174124] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
Sep 28 23:08:34 ubuntu kernel: [    0.174128] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
Sep 28 23:08:34 ubuntu kernel: [    0.174131] pci_bus 0000:00: resource 6 [mem 0x20000000-0xffffffff]
Sep 28 23:08:34 ubuntu kernel: [    0.174135] pci_bus 0000:01: resource 1 [mem 0xf4000000-0xf5ffffff]
Sep 28 23:08:34 ubuntu kernel: [    0.174139] pci_bus 0000:01: resource 2 [mem 0xe8000000-0xefffffff pref]
Sep 28 23:08:34 ubuntu kernel: [    0.174196] NET: Registered protocol family 2
Sep 28 23:08:34 ubuntu kernel: [    0.174278] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Sep 28 23:08:34 ubuntu kernel: [    0.174538] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
Sep 28 23:08:34 ubuntu kernel: [    0.174649] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
Sep 28 23:08:34 ubuntu kernel: [    0.174757] TCP: Hash tables configured (established 16384 bind 16384)
Sep 28 23:08:34 ubuntu kernel: [    0.174760] TCP reno registered
Sep 28 23:08:34 ubuntu kernel: [    0.174764] UDP hash table entries: 256 (order: 1, 8192 bytes)
Sep 28 23:08:34 ubuntu kernel: [    0.174775] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
Sep 28 23:08:34 ubuntu kernel: [    0.174876] NET: Registered protocol family 1
Sep 28 23:08:34 ubuntu kernel: [    0.174913] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
Sep 28 23:08:34 ubuntu kernel: [    0.175030] pci 0000:01:00.0: Boot video device
Sep 28 23:08:34 ubuntu kernel: [    0.175034] PCI: CLS 32 bytes, default 64
Sep 28 23:08:34 ubuntu kernel: [    0.175342] cpufreq-nforce2: No nForce2 chipset.
Sep 28 23:08:34 ubuntu kernel: [    0.175531] audit: initializing netlink socket (disabled)
Sep 28 23:08:34 ubuntu kernel: [    0.175548] type=2000 audit(1317251224.172:1): initialized
Sep 28 23:08:34 ubuntu kernel: [    0.175548] Switched to NOHz mode on CPU #0
Sep 28 23:08:34 ubuntu kernel: [    0.187495] Trying to unpack rootfs image as initramfs...
Sep 28 23:08:34 ubuntu kernel: [    3.428497] Refined TSC clocksource calibration: 1608.041 MHz.
Sep 28 23:08:34 ubuntu kernel: [    3.428504] Switching to clocksource tsc
Sep 28 23:08:34 ubuntu kernel: [    3.428835] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Sep 28 23:08:34 ubuntu kernel: [    3.431152] VFS: Disk quotas dquot_6.5.2
Sep 28 23:08:34 ubuntu kernel: [    3.431227] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Sep 28 23:08:34 ubuntu kernel: [    3.432157] fuse init (API version 7.16)
Sep 28 23:08:34 ubuntu kernel: [    3.432281] msgmni has been set to 965
Sep 28 23:08:34 ubuntu kernel: [    3.432579] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Sep 28 23:08:34 ubuntu kernel: [    3.432612] io scheduler noop registered
Sep 28 23:08:34 ubuntu kernel: [    3.432614] io scheduler deadline registered
Sep 28 23:08:34 ubuntu kernel: [    3.432635] io scheduler cfq registered (default)
Sep 28 23:08:34 ubuntu kernel: [    3.432836] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep 28 23:08:34 ubuntu kernel: [    3.432870] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Sep 28 23:08:34 ubuntu kernel: [    3.433073] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Sep 28 23:08:34 ubuntu kernel: [    3.433081] ACPI: Power Button [PWRB]
Sep 28 23:08:34 ubuntu kernel: [    3.433152] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Sep 28 23:08:34 ubuntu kernel: [    3.433157] ACPI: Power Button [PWRF]
Sep 28 23:08:34 ubuntu kernel: [    3.433351] ACPI: acpi_idle registered with cpuidle
Sep 28 23:08:34 ubuntu kernel: [    3.435040] ERST: Table is not found!
Sep 28 23:08:34 ubuntu kernel: [    3.435201] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Sep 28 23:08:34 ubuntu kernel: [    3.455573] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep 28 23:08:34 ubuntu kernel: [    3.455610] isapnp: Scanning for PnP cards...
Sep 28 23:08:34 ubuntu kernel: [    3.525051] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Sep 28 23:08:34 ubuntu kernel: [    3.546640] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep 28 23:08:34 ubuntu kernel: [    3.610618] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Sep 28 23:08:34 ubuntu kernel: [    3.610737] serial 0000:00:0b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Sep 28 23:08:34 ubuntu kernel: [    3.610745] serial 0000:00:0b.0: PCI INT A disabled
Sep 28 23:08:34 ubuntu kernel: [    3.610936] Linux agpgart interface v0.103
Sep 28 23:08:34 ubuntu kernel: [    3.610971] agpgart-amd64 0000:00:00.0: AGP bridge [1106/0282]
Sep 28 23:08:34 ubuntu kernel: [    3.613210] agpgart-amd64 0000:00:00.0: AGP aperture is 64M @ 0xf0000000
Sep 28 23:08:34 ubuntu kernel: [    3.614835] brd: module loaded
Sep 28 23:08:34 ubuntu kernel: [    3.615579] loop: module loaded
Sep 28 23:08:34 ubuntu kernel: [    3.615737] i2c-core: driver [adp5520] using legacy suspend method
Sep 28 23:08:34 ubuntu kernel: [    3.615740] i2c-core: driver [adp5520] using legacy resume method
Sep 28 23:08:34 ubuntu kernel: [    3.616226] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
Sep 28 23:08:34 ubuntu kernel: [    3.616230] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
Sep 28 23:08:34 ubuntu kernel: [    3.616251] pata_acpi 0000:00:0f.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
Sep 28 23:08:34 ubuntu kernel: [    3.616314] pata_acpi 0000:00:0f.1: PCI INT A disabled
Sep 28 23:08:34 ubuntu kernel: [    3.616833] Fixed MDIO Bus: probed
Sep 28 23:08:34 ubuntu kernel: [    3.616893] PPP generic driver version 2.4.2
Sep 28 23:08:34 ubuntu kernel: [    3.616973] tun: Universal TUN/TAP device driver, 1.6
Sep 28 23:08:34 ubuntu kernel: [    3.616975] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Sep 28 23:08:34 ubuntu kernel: [    3.617091] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Sep 28 23:08:34 ubuntu kernel: [    3.617312] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
Sep 28 23:08:34 ubuntu kernel: [    3.617315] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
Sep 28 23:08:34 ubuntu kernel: [    3.617331] ehci_hcd 0000:00:10.4: PCI INT C -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
Sep 28 23:08:34 ubuntu kernel: [    3.617351] ehci_hcd 0000:00:10.4: EHCI Host Controller
Sep 28 23:08:34 ubuntu kernel: [    3.617408] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
Sep 28 23:08:34 ubuntu kernel: [    3.617489] ehci_hcd 0000:00:10.4: irq 21, io mem 0xf6001000
Sep 28 23:08:34 ubuntu kernel: [    3.661102] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
Sep 28 23:08:34 ubuntu kernel: [    3.661269] hub 1-0:1.0: USB hub found
Sep 28 23:08:34 ubuntu kernel: [    3.661274] hub 1-0:1.0: 8 ports detected
Sep 28 23:08:34 ubuntu kernel: [    3.661376] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Sep 28 23:08:34 ubuntu kernel: [    3.661398] uhci_hcd: USB Universal Host Controller Interface driver
Sep 28 23:08:34 ubuntu kernel: [    3.661452] uhci_hcd 0000:00:10.0: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
Sep 28 23:08:34 ubuntu kernel: [    3.661462] uhci_hcd 0000:00:10.0: UHCI Host Controller
Sep 28 23:08:34 ubuntu kernel: [    3.661518] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
Sep 28 23:08:34 ubuntu kernel: [    3.661544] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000b000
Sep 28 23:08:34 ubuntu kernel: [    3.661697] hub 2-0:1.0: USB hub found
Sep 28 23:08:34 ubuntu kernel: [    3.661703] hub 2-0:1.0: 2 ports detected
Sep 28 23:08:34 ubuntu kernel: [    3.661781] uhci_hcd 0000:00:10.1: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
Sep 28 23:08:34 ubuntu kernel: [    3.661789] uhci_hcd 0000:00:10.1: UHCI Host Controller
Sep 28 23:08:34 ubuntu kernel: [    3.661838] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
Sep 28 23:08:34 ubuntu kernel: [    3.661860] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000b400
Sep 28 23:08:34 ubuntu kernel: [    3.662012] hub 3-0:1.0: USB hub found
Sep 28 23:08:34 ubuntu kernel: [    3.662017] hub 3-0:1.0: 2 ports detected
Sep 28 23:08:34 ubuntu kernel: [    3.662097] uhci_hcd 0000:00:10.2: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
Sep 28 23:08:34 ubuntu kernel: [    3.662107] uhci_hcd 0000:00:10.2: UHCI Host Controller
Sep 28 23:08:34 ubuntu kernel: [    3.662152] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
Sep 28 23:08:34 ubuntu kernel: [    3.662174] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000b800
Sep 28 23:08:34 ubuntu kernel: [    3.662329] hub 4-0:1.0: USB hub found
Sep 28 23:08:34 ubuntu kernel: [    3.662334] hub 4-0:1.0: 2 ports detected
Sep 28 23:08:34 ubuntu kernel: [    3.662422] uhci_hcd 0000:00:10.3: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
Sep 28 23:08:34 ubuntu kernel: [    3.662430] uhci_hcd 0000:00:10.3: UHCI Host Controller
Sep 28 23:08:34 ubuntu kernel: [    3.662476] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
Sep 28 23:08:34 ubuntu kernel: [    3.662498] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000bc00
Sep 28 23:08:34 ubuntu kernel: [    3.662653] hub 5-0:1.0: USB hub found
Sep 28 23:08:34 ubuntu kernel: [    3.662658] hub 5-0:1.0: 2 ports detected
Sep 28 23:08:34 ubuntu kernel: [    3.662817] i8042: PNP: No PS/2 controller found. Probing ports directly.
Sep 28 23:08:34 ubuntu kernel: [    3.706938] serio: i8042 KBD port at 0x60,0x64 irq 1
Sep 28 23:08:34 ubuntu kernel: [    3.706944] serio: i8042 AUX port at 0x60,0x64 irq 12
Sep 28 23:08:34 ubuntu kernel: [    3.707056] mousedev: PS/2 mouse device common for all mice
Sep 28 23:08:34 ubuntu kernel: [    3.707206] rtc_cmos 00:05: RTC can wake from S4
Sep 28 23:08:34 ubuntu kernel: [    3.707262] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Sep 28 23:08:34 ubuntu kernel: [    3.707315] rtc0: alarms up to one year, y3k, 242 bytes nvram
Sep 28 23:08:34 ubuntu kernel: [    3.707442] device-mapper: uevent: version 1.0.3
Sep 28 23:08:34 ubuntu kernel: [    3.707541] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
Sep 28 23:08:34 ubuntu kernel: [    3.707635] device-mapper: multipath: version 1.2.0 loaded
Sep 28 23:08:34 ubuntu kernel: [    3.707638] device-mapper: multipath round-robin: version 1.0.0 loaded
Sep 28 23:08:34 ubuntu kernel: [    3.707740] EISA: Probing bus 0 at eisa.0
Sep 28 23:08:34 ubuntu kernel: [    3.707744] EISA: Cannot allocate resource for mainboard
Sep 28 23:08:34 ubuntu kernel: [    3.707747] Cannot allocate resource for EISA slot 1
Sep 28 23:08:34 ubuntu kernel: [    3.707750] Cannot allocate resource for EISA slot 2
Sep 28 23:08:34 ubuntu kernel: [    3.707753] Cannot allocate resource for EISA slot 3
Sep 28 23:08:34 ubuntu kernel: [    3.707756] Cannot allocate resource for EISA slot 4
Sep 28 23:08:34 ubuntu kernel: [    3.707760] Cannot allocate resource for EISA slot 5
Sep 28 23:08:34 ubuntu kernel: [    3.707763] Cannot allocate resource for EISA slot 6
Sep 28 23:08:34 ubuntu kernel: [    3.707766] Cannot allocate resource for EISA slot 7
Sep 28 23:08:34 ubuntu kernel: [    3.707769] Cannot allocate resource for EISA slot 8
Sep 28 23:08:34 ubuntu kernel: [    3.707771] EISA: Detected 0 cards.
Sep 28 23:08:34 ubuntu kernel: [    3.707823] cpuidle: using governor ladder
Sep 28 23:08:34 ubuntu kernel: [    3.707826] cpuidle: using governor menu
Sep 28 23:08:34 ubuntu kernel: [    3.708214] TCP cubic registered
Sep 28 23:08:34 ubuntu kernel: [    3.708381] NET: Registered protocol family 10
Sep 28 23:08:34 ubuntu kernel: [    3.709092] NET: Registered protocol family 17
Sep 28 23:08:34 ubuntu kernel: [    3.709117] Registering the dns_resolver key type
Sep 28 23:08:34 ubuntu kernel: [    3.709142] powernow-k8: Power state transitions not supported
Sep 28 23:08:34 ubuntu kernel: [    3.709175] ACPI Exception: AE_NOT_FOUND, Evaluating _PSS (20110112/processor_perflib-322)
Sep 28 23:08:34 ubuntu kernel: [    3.709190] Using IPI No-Shortcut mode
Sep 28 23:08:34 ubuntu kernel: [    3.709343] PM: Hibernation image not present or could not be loaded.
Sep 28 23:08:34 ubuntu kernel: [    3.709357] registered taskstats version 1
Sep 28 23:08:34 ubuntu kernel: [    3.709602]   Magic number: 11:628:151
Sep 28 23:08:34 ubuntu kernel: [    3.709625] bdi 1:3: hash matches
Sep 28 23:08:34 ubuntu kernel: [    3.709723] rtc_cmos 00:05: setting system clock to 2011-09-28 23:07:08 UTC (1317251228)
Sep 28 23:08:34 ubuntu kernel: [    3.709729] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Sep 28 23:08:34 ubuntu kernel: [    3.709731] EDD information not available.
Sep 28 23:08:34 ubuntu kernel: [    3.883828] isapnp: No Plug & Play device found
Sep 28 23:08:34 ubuntu kernel: [    4.698566] Freeing initrd memory: 13076k freed
Sep 28 23:08:34 ubuntu kernel: [    4.712304] Freeing unused kernel memory: 700k freed
Sep 28 23:08:34 ubuntu kernel: [    4.713040] Write protecting the kernel text: 5192k
Sep 28 23:08:34 ubuntu kernel: [    4.713088] Write protecting the kernel read-only data: 2148k
Sep 28 23:08:34 ubuntu kernel: [    4.751159] ramzswap: disk size not provided. You can use disksize_kb module param to specify size.
Sep 28 23:08:34 ubuntu kernel: [    4.751162] Using default: (25% of RAM).
Sep 28 23:08:34 ubuntu kernel: [    4.751166] ramzswap: disk size set to 127000 kB
Sep 28 23:08:34 ubuntu kernel: [    4.761740] <30>udev[67]: starting version 167
Sep 28 23:08:34 ubuntu kernel: [    4.943432] sata_via 0000:00:0f.0: version 2.6
Sep 28 23:08:34 ubuntu kernel: [    4.943455] sata_via 0000:00:0f.0: PCI INT B -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
Sep 28 23:08:34 ubuntu kernel: [    4.943501] sata_via 0000:00:0f.0: routed to hard irq line 11
Sep 28 23:08:34 ubuntu kernel: [    4.958907] Floppy drive(s): fd0 is 1.44M
Sep 28 23:08:34 ubuntu kernel: [    5.014973] scsi0 : sata_via
Sep 28 23:08:34 ubuntu kernel: [    5.016716] scsi1 : sata_via
Sep 28 23:08:34 ubuntu kernel: [    5.016807] ata1: SATA max UDMA/133 cmd 0x9400 ctl 0x9800 bmdma 0xa400 irq 20
Sep 28 23:08:34 ubuntu kernel: [    5.016811] ata2: SATA max UDMA/133 cmd 0x9c00 ctl 0xa000 bmdma 0xa408 irq 20
Sep 28 23:08:34 ubuntu kernel: [    5.017328] pata_via 0000:00:0f.1: version 0.3.4
Sep 28 23:08:34 ubuntu kernel: [    5.017351] pata_via 0000:00:0f.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
Sep 28 23:08:34 ubuntu kernel: [    5.020102] scsi2 : pata_via
Sep 28 23:08:34 ubuntu kernel: [    5.021420] scsi3 : pata_via
Sep 28 23:08:34 ubuntu kernel: [    5.023071] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xac00 irq 14
Sep 28 23:08:34 ubuntu kernel: [    5.023075] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xac08 irq 15
Sep 28 23:08:34 ubuntu kernel: [    5.027629] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Sep 28 23:08:34 ubuntu kernel: [    5.059200] 8139cp 0000:00:13.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
Sep 28 23:08:34 ubuntu kernel: [    5.112475] [drm] Initialized drm 1.1.0 20060810
Sep 28 23:08:34 ubuntu kernel: [    5.119005] FDC 0 is a post-1991 82077
Sep 28 23:08:34 ubuntu kernel: [    5.185875] ata3.00: HPA detected: current 159282179, native 160086528
Sep 28 23:08:34 ubuntu kernel: [    5.185884] ata3.00: ATA-7: Maxtor 6L080L0, BAJ41G20, max UDMA/133
Sep 28 23:08:34 ubuntu kernel: [    5.185888] ata3.00: 159282179 sectors, multi 16: LBA 
Sep 28 23:08:34 ubuntu kernel: [    5.201792] ata3.00: configured for UDMA/133
Sep 28 23:08:34 ubuntu kernel: [    5.220011] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
Sep 28 23:08:34 ubuntu kernel: [    5.432010] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
Sep 28 23:08:34 ubuntu kernel: [    5.442971] scsi 2:0:0:0: Direct-Access     ATA      Maxtor 6L080L0   BAJ4 PQ: 0 ANSI: 5
Sep 28 23:08:34 ubuntu kernel: [    5.443212] sd 2:0:0:0: Attached scsi generic sg0 type 0
Sep 28 23:08:34 ubuntu kernel: [    5.443653] sd 2:0:0:0: [sda] 159282179 512-byte logical blocks: (81.5 GB/75.9 GiB)
Sep 28 23:08:34 ubuntu kernel: [    5.443716] sd 2:0:0:0: [sda] Write Protect is off
Sep 28 23:08:34 ubuntu kernel: [    5.443720] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Sep 28 23:08:34 ubuntu kernel: [    5.443747] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 28 23:08:34 ubuntu kernel: [    5.497607]  sda: sda1 sda2 < sda5 sda6 >
Sep 28 23:08:34 ubuntu kernel: [    5.498225] sd 2:0:0:0: [sda] Attached SCSI disk
Sep 28 23:08:34 ubuntu kernel: [    5.564015] usb 3-1: new low speed USB device using uhci_hcd and address 2
Sep 28 23:08:34 ubuntu kernel: [    5.604348] ata4.00: ATAPI: HL-DT-ST DVDRAM GSA-H10A, JL02, max UDMA/33
Sep 28 23:08:34 ubuntu kernel: [    5.620210] ata4.00: configured for UDMA/33
Sep 28 23:08:34 ubuntu kernel: [    5.626724] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-H10A  JL02 PQ: 0 ANSI: 5
Sep 28 23:08:34 ubuntu kernel: [    5.631103] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Sep 28 23:08:34 ubuntu kernel: [    5.631108] cdrom: Uniform CD-ROM driver Revision: 3.20
Sep 28 23:08:34 ubuntu kernel: [    5.631269] sr 3:0:0:0: Attached scsi CD-ROM sr0
Sep 28 23:08:34 ubuntu kernel: [    5.631365] sr 3:0:0:0: Attached scsi generic sg1 type 5
Sep 28 23:08:34 ubuntu kernel: [    5.657695] 8139too: 8139too Fast Ethernet driver 0.9.28
Sep 28 23:08:34 ubuntu kernel: [    5.657768] 8139too 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Sep 28 23:08:34 ubuntu kernel: [    5.659051] 8139too 0000:00:13.0: eth0: RealTek RTL8139 at 0xc400, 00:14:85:b9:22:8a, IRQ 18
Sep 28 23:08:34 ubuntu kernel: [    5.717273] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Sep 28 23:08:34 ubuntu kernel: [    5.721520] [drm] nouveau 0000:01:00.0: Detected an NV30 generation card (0x034600b1)
Sep 28 23:08:34 ubuntu kernel: [    5.721722] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
Sep 28 23:08:34 ubuntu kernel: [    5.764007] [drm] nouveau 0000:01:00.0: ... appears to be valid
Sep 28 23:08:34 ubuntu kernel: [    5.764287] [drm] nouveau 0000:01:00.0: BMP BIOS found
Sep 28 23:08:34 ubuntu kernel: [    5.764290] [drm] nouveau 0000:01:00.0: BMP version 5.40
Sep 28 23:08:34 ubuntu kernel: [    5.764294] [drm] nouveau 0000:01:00.0: Bios version 04.34.20.69
Sep 28 23:08:34 ubuntu kernel: [    5.764298] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 2.2
Sep 28 23:08:34 ubuntu kernel: [    5.764303] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 01000300 000088b8
Sep 28 23:08:34 ubuntu kernel: [    5.764307] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 02010310 000088b8
Sep 28 23:08:34 ubuntu kernel: [    5.764311] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 01010312 00000000
Sep 28 23:08:34 ubuntu kernel: [    5.764314] [drm] nouveau 0000:01:00.0: Raw DCB entry 3: 02020321 00000303
Sep 28 23:08:34 ubuntu kernel: [    5.764543] [drm] nouveau 0000:01:00.0: Loading NV17 power sequencing microcode
Sep 28 23:08:34 ubuntu kernel: [    5.764548] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xEC5F
Sep 28 23:08:34 ubuntu kernel: [    5.782248] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xEEFA
Sep 28 23:08:34 ubuntu kernel: [    5.782260] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xF040
Sep 28 23:08:34 ubuntu kernel: [    5.782302] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xF1C9
Sep 28 23:08:34 ubuntu kernel: [    5.782308] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xF1E6
Sep 28 23:08:34 ubuntu kernel: [    5.782314] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 5 at offset 0xF203
Sep 28 23:08:34 ubuntu kernel: [    5.806219] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 6 at offset 0xF39C
Sep 28 23:08:34 ubuntu kernel: [    5.850337] input: HID 04f3:0103 as /devices/pci0000:00/0000:00:10.1/usb3/3-1/3-1:1.0/input/input2
Sep 28 23:08:34 ubuntu kernel: [    5.850570] generic-usb 0003:04F3:0103.0001: input,hidraw0: USB HID v1.10 Keyboard [HID 04f3:0103] on usb-0000:00:10.1-1/input0
Sep 28 23:08:34 ubuntu kernel: [    5.864559] [drm] nouveau 0000:01:00.0: 1 available performance level(s)
Sep 28 23:08:34 ubuntu kernel: [    5.864567] [drm] nouveau 0000:01:00.0: 0: memory 500MHz core 270MHz fanspeed 100%
Sep 28 23:08:34 ubuntu kernel: [    5.864577] [drm] nouveau 0000:01:00.0: c: memory 405MHz core 249MHz
Sep 28 23:08:34 ubuntu kernel: [    5.864654] [TTM] Zone  kernel: Available graphics memory: 254000 kiB.
Sep 28 23:08:34 ubuntu kernel: [    5.864657] [TTM] Initializing pool allocator.
Sep 28 23:08:34 ubuntu kernel: [    5.864672] [drm] nouveau 0000:01:00.0: Detected 128MiB VRAM
Sep 28 23:08:34 ubuntu kernel: [    5.864941] agpgart-amd64 0000:00:00.0: AGP 3.0 bridge
Sep 28 23:08:34 ubuntu kernel: [    5.864958] agpgart: modprobe tried to set rate=x12. Setting to AGP3 x8 mode.
Sep 28 23:08:34 ubuntu kernel: [    5.864966] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x mode
Sep 28 23:08:34 ubuntu kernel: [    5.865042] nouveau 0000:01:00.0: putting AGP V3 device into 8x mode
Sep 28 23:08:34 ubuntu kernel: [    5.865046] [drm] nouveau 0000:01:00.0: 64 MiB GART (aperture)
Sep 28 23:08:34 ubuntu kernel: [    5.865243] [drm] nouveau 0000:01:00.0: Saving VGA fonts
Sep 28 23:08:34 ubuntu kernel: [    5.908508] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Sep 28 23:08:34 ubuntu kernel: [    5.908513] [drm] No driver support for vblank timestamp query.
Sep 28 23:08:34 ubuntu kernel: [    5.910146] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 0)
Sep 28 23:08:34 ubuntu kernel: [    5.910153] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 1)
Sep 28 23:08:34 ubuntu kernel: [    5.910158] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on tmds encoder (output 2)
Sep 28 23:08:34 ubuntu kernel: [    5.910162] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on TV encoder (output 3)
Sep 28 23:08:34 ubuntu kernel: [    5.930248] input: HID 04f3:0103 as /devices/pci0000:00/0000:00:10.1/usb3/3-1/3-1:1.1/input/input3
Sep 28 23:08:34 ubuntu kernel: [    5.930380] generic-usb 0003:04F3:0103.0002: input,hidraw1: USB HID v1.10 Device [HID 04f3:0103] on usb-0000:00:10.1-1/input1
Sep 28 23:08:34 ubuntu kernel: [    5.930405] usbcore: registered new interface driver usbhid
Sep 28 23:08:34 ubuntu kernel: [    5.930408] usbhid: USB HID core driver
Sep 28 23:08:34 ubuntu kernel: [    6.048609] usb 3-2: new low speed USB device using uhci_hcd and address 3
Sep 28 23:08:34 ubuntu kernel: [    6.108661] [drm] nouveau 0000:01:00.0: allocated 1280x1024 fb: 0x49000, bo dc982000
Sep 28 23:08:34 ubuntu kernel: [    6.120217] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on vga encoder (output 0)
Sep 28 23:08:34 ubuntu kernel: [    6.120224] [drm] nouveau 0000:01:00.0: Output VGA-1 is running on CRTC 0 using output A
Sep 28 23:08:34 ubuntu kernel: [    6.121847] Console: switching to colour frame buffer device 160x64
Sep 28 23:08:34 ubuntu kernel: [    6.123032] fb0: nouveaufb frame buffer device
Sep 28 23:08:34 ubuntu kernel: [    6.123035] drm: registered panic notifier
Sep 28 23:08:34 ubuntu kernel: [    6.123046] [drm] Initialized nouveau 0.0.16 20090420 for 0000:01:00.0 on minor 0
Sep 28 23:08:34 ubuntu kernel: [    6.242098] input: Logitech Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:10.1/usb3/3-2/3-2:1.0/input/input4
Sep 28 23:08:34 ubuntu kernel: [    6.242270] generic-usb 0003:046D:C018.0003: input,hidraw2: USB HID v1.11 Mouse [Logitech Logitech USB Optical Mouse] on usb-0000:00:10.1-2/input0
Sep 28 23:08:34 ubuntu kernel: [    7.344196] Btrfs loaded
Sep 28 23:08:34 ubuntu kernel: [    7.353045] xor: automatically using best checksumming function: pIII_sse
Sep 28 23:08:34 ubuntu kernel: [    7.372005]    pIII_sse  :  4836.000 MB/sec
Sep 28 23:08:34 ubuntu kernel: [    7.372009] xor: using function: pIII_sse (4836.000 MB/sec)
Sep 28 23:08:34 ubuntu kernel: [    7.376656] device-mapper: dm-raid45: initialized v0.2594b
Sep 28 23:08:34 ubuntu kernel: [    8.032548] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
Sep 28 23:08:34 ubuntu kernel: [    8.032555] EXT4-fs (sda5): write access will be enabled during recovery
Sep 28 23:08:34 ubuntu kernel: [   11.628816] EXT4-fs (sda5): orphan cleanup on readonly fs
Sep 28 23:08:34 ubuntu kernel: [   11.628828] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 4033
Sep 28 23:08:34 ubuntu kernel: [   11.628865] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 33677
Sep 28 23:08:34 ubuntu kernel: [   11.628922] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 33672
Sep 28 23:08:34 ubuntu kernel: [   11.628933] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 30869
Sep 28 23:08:34 ubuntu kernel: [   11.628951] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 33671
Sep 28 23:08:34 ubuntu kernel: [   11.628961] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 33669
Sep 28 23:08:34 ubuntu kernel: [   11.628978] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 33655
Sep 28 23:08:34 ubuntu kernel: [   11.628988] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 33659
Sep 28 23:08:34 ubuntu kernel: [   11.629005] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 33607
Sep 28 23:08:34 ubuntu kernel: [   11.629022] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 33650
Sep 28 23:08:34 ubuntu kernel: [   11.629037] EXT4-fs (sda5): 10 orphan inodes deleted
Sep 28 23:08:34 ubuntu kernel: [   11.629040] EXT4-fs (sda5): recovery complete
Sep 28 23:08:34 ubuntu kernel: [   11.844304] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
Sep 28 23:08:34 ubuntu kernel: [   13.512310] sr 3:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 28 23:08:34 ubuntu kernel: [   13.512319] sr 3:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
Sep 28 23:08:34 ubuntu kernel: [   13.512325] Info fld=0x55a98, ILI
Sep 28 23:08:34 ubuntu kernel: [   13.512328] sr 3:0:0:0: [sr0]  Add. Sense: Illegal mode for this track
Sep 28 23:08:34 ubuntu kernel: [   13.512337] sr 3:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 5a 98 00 00 01 00
Sep 28 23:08:34 ubuntu kernel: [   13.512347] end_request: I/O error, dev sr0, sector 1403488
Sep 28 23:08:34 ubuntu kernel: [   13.512352] Buffer I/O error on device sr0, logical block 350872
Sep 28 23:08:34 ubuntu kernel: [   13.531223] sr 3:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 28 23:08:34 ubuntu kernel: [   13.531228] sr 3:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
Sep 28 23:08:34 ubuntu kernel: [   13.531232] Info fld=0x55a98, ILI
Sep 28 23:08:34 ubuntu kernel: [   13.531235] sr 3:0:0:0: [sr0]  Add. Sense: Illegal mode for this track
Sep 28 23:08:34 ubuntu kernel: [   13.531241] sr 3:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 5a 98 00 00 01 00
Sep 28 23:08:34 ubuntu kernel: [   13.531250] end_request: I/O error, dev sr0, sector 1403488
Sep 28 23:08:34 ubuntu kernel: [   13.531254] Buffer I/O error on device sr0, logical block 350872
Sep 28 23:08:34 ubuntu kernel: [   13.562883] sr 3:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 28 23:08:34 ubuntu kernel: [   13.562888] sr 3:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
Sep 28 23:08:34 ubuntu kernel: [   13.562893] Info fld=0x55a98, ILI
Sep 28 23:08:34 ubuntu kernel: [   13.562895] sr 3:0:0:0: [sr0]  Add. Sense: Illegal mode for this track
Sep 28 23:08:34 ubuntu kernel: [   13.562902] sr 3:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 5a 98 00 00 01 00
Sep 28 23:08:34 ubuntu kernel: [   13.562911] end_request: I/O error, dev sr0, sector 1403488
Sep 28 23:08:34 ubuntu kernel: [   13.562914] Buffer I/O error on device sr0, logical block 350872
Sep 28 23:08:34 ubuntu kernel: [   13.581776] sr 3:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 28 23:08:34 ubuntu kernel: [   13.581781] sr 3:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
Sep 28 23:08:34 ubuntu kernel: [   13.581786] Info fld=0x55a98, ILI
Sep 28 23:08:34 ubuntu kernel: [   13.581788] sr 3:0:0:0: [sr0]  Add. Sense: Illegal mode for this track
Sep 28 23:08:34 ubuntu kernel: [   13.581794] sr 3:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 5a 98 00 00 01 00
Sep 28 23:08:34 ubuntu kernel: [   13.581803] end_request: I/O error, dev sr0, sector 1403488
Sep 28 23:08:34 ubuntu kernel: [   13.581806] Buffer I/O error on device sr0, logical block 350872
Sep 28 23:08:34 ubuntu kernel: [   13.670452] sr 3:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 28 23:08:34 ubuntu kernel: [   13.670457] sr 3:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
Sep 28 23:08:34 ubuntu kernel: [   13.670462] Info fld=0x55a98, ILI
Sep 28 23:08:34 ubuntu kernel: [   13.670465] sr 3:0:0:0: [sr0]  Add. Sense: Illegal mode for this track
Sep 28 23:08:34 ubuntu kernel: [   13.670471] sr 3:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 5a 98 00 00 01 00
Sep 28 23:08:34 ubuntu kernel: [   13.670480] end_request: I/O error, dev sr0, sector 1403488
Sep 28 23:08:34 ubuntu kernel: [   13.670484] Buffer I/O error on device sr0, logical block 350872
Sep 28 23:08:34 ubuntu kernel: [   13.714900] sr 3:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 28 23:08:34 ubuntu kernel: [   13.714904] sr 3:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
Sep 28 23:08:34 ubuntu kernel: [   13.714909] Info fld=0x55a98, ILI
Sep 28 23:08:34 ubuntu kernel: [   13.714912] sr 3:0:0:0: [sr0]  Add. Sense: Illegal mode for this track
Sep 28 23:08:34 ubuntu kernel: [   13.714918] sr 3:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 5a 98 00 00 01 00
Sep 28 23:08:34 ubuntu kernel: [   13.714927] end_request: I/O error, dev sr0, sector 1403488
Sep 28 23:08:34 ubuntu kernel: [   13.714930] Buffer I/O error on device sr0, logical block 350872
Sep 28 23:08:34 ubuntu kernel: [   13.778411] sr 3:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 28 23:08:34 ubuntu kernel: [   13.778416] sr 3:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
Sep 28 23:08:34 ubuntu kernel: [   13.778420] Info fld=0x55a98, ILI
Sep 28 23:08:34 ubuntu kernel: [   13.778423] sr 3:0:0:0: [sr0]  Add. Sense: Illegal mode for this track
Sep 28 23:08:34 ubuntu kernel: [   13.778429] sr 3:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 5a 98 00 00 01 00
Sep 28 23:08:34 ubuntu kernel: [   13.778438] end_request: I/O error, dev sr0, sector 1403488
Sep 28 23:08:34 ubuntu kernel: [   13.778442] Buffer I/O error on device sr0, logical block 350872
Sep 28 23:08:34 ubuntu kernel: [   13.905521] sr 3:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 28 23:08:34 ubuntu kernel: [   13.905527] sr 3:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
Sep 28 23:08:34 ubuntu kernel: [   13.905532] Info fld=0x55a97, ILI
Sep 28 23:08:34 ubuntu kernel: [   13.905534] sr 3:0:0:0: [sr0]  Add. Sense: Illegal mode for this track
Sep 28 23:08:34 ubuntu kernel: [   13.905541] sr 3:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 5a 96 00 00 02 00
Sep 28 23:08:34 ubuntu kernel: [   13.905550] end_request: I/O error, dev sr0, sector 1403480
Sep 28 23:08:34 ubuntu kernel: [   13.905554] Buffer I/O error on device sr0, logical block 350870
Sep 28 23:08:34 ubuntu kernel: [   13.905558] Buffer I/O error on device sr0, logical block 350871
Sep 28 23:08:34 ubuntu kernel: [   13.911204] sr 3:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 28 23:08:34 ubuntu kernel: [   13.911208] sr 3:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
Sep 28 23:08:34 ubuntu kernel: [   13.911213] Info fld=0x55a98, ILI
Sep 28 23:08:34 ubuntu kernel: [   13.911216] sr 3:0:0:0: [sr0]  Add. Sense: Illegal mode for this track
Sep 28 23:08:34 ubuntu kernel: [   13.911222] sr 3:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 5a 98 00 00 01 00
Sep 28 23:08:34 ubuntu kernel: [   13.911231] end_request: I/O error, dev sr0, sector 1403488
Sep 28 23:08:34 ubuntu kernel: [   13.911234] Buffer I/O error on device sr0, logical block 350872
Sep 28 23:08:34 ubuntu kernel: [   13.916716] sr 3:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 28 23:08:34 ubuntu kernel: [   13.916721] sr 3:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
Sep 28 23:08:34 ubuntu kernel: [   13.916725] Info fld=0x55a98, ILI
Sep 28 23:08:34 ubuntu kernel: [   13.916728] sr 3:0:0:0: [sr0]  Add. Sense: Illegal mode for this track
Sep 28 23:08:34 ubuntu kernel: [   13.916734] sr 3:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 5a 98 00 00 01 00
Sep 28 23:08:34 ubuntu kernel: [   13.916743] end_request: I/O error, dev sr0, sector 1403488
Sep 28 23:08:34 ubuntu kernel: [   13.923643] sr 3:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 28 23:08:34 ubuntu kernel: [   13.923647] sr 3:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
Sep 28 23:08:34 ubuntu kernel: [   13.923652] Info fld=0x55a97, ILI
Sep 28 23:08:34 ubuntu kernel: [   13.923655] sr 3:0:0:0: [sr0]  Add. Sense: Illegal mode for this track
Sep 28 23:08:34 ubuntu kernel: [   13.923661] sr 3:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 5a 96 00 00 02 00
Sep 28 23:08:34 ubuntu kernel: [   13.923670] end_request: I/O error, dev sr0, sector 1403480
Sep 28 23:08:34 ubuntu kernel: [   14.826591] ISO 9660 Extensions: Microsoft Joliet Level 3
Sep 28 23:08:34 ubuntu kernel: [   14.884050] ISO 9660 Extensions: RRIP_1991A
Sep 28 23:08:34 ubuntu kernel: [   15.348543] aufs 2.1-standalone.tree-38-rcN-20110207
Sep 28 23:08:34 ubuntu kernel: [   15.439667] squashfs: version 4.0 (2009/01/31) Phillip Lougher
Sep 28 23:08:34 ubuntu kernel: [   87.131581] Adding 522236k swap on /dev/sda6.  Priority:-1 extents:1 across:522236k 
Sep 28 23:08:35 ubuntu kernel: [   91.201821] <30>udev[1201]: starting version 167
Sep 28 23:08:36 ubuntu avahi-daemon[1288]: Found user 'avahi' (UID 104) and group 'avahi' (GID 109).
Sep 28 23:08:36 ubuntu avahi-daemon[1288]: Successfully dropped root privileges.
Sep 28 23:08:36 ubuntu avahi-daemon[1288]: avahi-daemon 0.6.30 starting up.
Sep 28 23:08:36 ubuntu avahi-daemon[1288]: Successfully called chroot().
Sep 28 23:08:36 ubuntu avahi-daemon[1288]: Successfully dropped remaining capabilities.
Sep 28 23:08:36 ubuntu avahi-daemon[1289]: chroot.c: open() failed: No such file or directory
Sep 28 23:08:36 ubuntu avahi-daemon[1288]: Failed to open /etc/resolv.conf: Invalid argument
Sep 28 23:08:36 ubuntu avahi-daemon[1288]: Loading service file /services/udisks.service.
Sep 28 23:08:36 ubuntu avahi-daemon[1288]: Network interface enumeration completed.
Sep 28 23:08:36 ubuntu avahi-daemon[1288]: Registering HINFO record with values 'I686'/'LINUX'.
Sep 28 23:08:36 ubuntu avahi-daemon[1288]: Server startup complete. Host name is ubuntu.local. Local service cookie is 2047848064.
Sep 28 23:08:36 ubuntu avahi-daemon[1288]: Service "ubuntu" (/services/udisks.service) successfully established.
Sep 28 23:08:39 ubuntu NetworkManager[1398]: <info> NetworkManager (version 0.8.3.998) is starting...
Sep 28 23:08:39 ubuntu NetworkManager[1398]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Sep 28 23:08:41 ubuntu NetworkManager[1398]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Sep 28 23:08:41 ubuntu NetworkManager[1398]: <info> trying to start the modem manager...
Sep 28 23:08:41 ubuntu kernel: [   96.851061] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Sep 28 23:08:43 ubuntu modem-manager[1441]: <info>  ModemManager (version 0.4) starting...
Sep 28 23:08:44 ubuntu modem-manager[1441]: <info>  Loaded plugin AnyData
Sep 28 23:08:44 ubuntu modem-manager[1441]: <info>  Loaded plugin Generic
Sep 28 23:08:44 ubuntu modem-manager[1441]: <info>  Loaded plugin Gobi
Sep 28 23:08:44 ubuntu modem-manager[1441]: <info>  Loaded plugin Option High-Speed
Sep 28 23:08:44 ubuntu kernel: [   99.769023] parport_pc 00:0b: reported by Plug and Play ACPI
Sep 28 23:08:44 ubuntu kernel: [   99.769071] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Sep 28 23:08:44 ubuntu modem-manager[1441]: <info>  Loaded plugin Huawei
Sep 28 23:08:44 ubuntu polkitd[1450]: started daemon version 0.101 using authority implementation `local' version `0.101'
Sep 28 23:08:44 ubuntu NetworkManager[1398]: <info> monitoring kernel firmware directory '/lib/firmware'.
Sep 28 23:08:44 ubuntu modem-manager[1441]: <info>  Loaded plugin Linktop
Sep 28 23:08:44 ubuntu NetworkManager[1398]:    SCPlugin-Ifupdown: init!
Sep 28 23:08:44 ubuntu modem-manager[1441]: <info>  Loaded plugin Longcheer
Sep 28 23:08:44 ubuntu NetworkManager[1398]:    SCPlugin-Ifupdown: update_system_hostname
Sep 28 23:08:44 ubuntu NetworkManager[1398]:    SCPluginIfupdown: management mode: unmanaged
Sep 28 23:08:44 ubuntu NetworkManager[1398]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:13.0/net/eth0, iface: eth0)
Sep 28 23:08:44 ubuntu NetworkManager[1398]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:13.0/net/eth0, iface: eth0): no ifupdown configuration found.
Sep 28 23:08:44 ubuntu NetworkManager[1398]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Sep 28 23:08:44 ubuntu NetworkManager[1398]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Sep 28 23:08:44 ubuntu NetworkManager[1398]:    SCPlugin-Ifupdown: end _init.
Sep 28 23:08:44 ubuntu NetworkManager[1398]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Sep 28 23:08:45 ubuntu modem-manager[1441]: <info>  Loaded plugin Ericsson MBM
Sep 28 23:08:45 ubuntu NetworkManager[1398]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Sep 28 23:08:45 ubuntu NetworkManager[1398]:    Ifupdown: get unmanaged devices count: 0
Sep 28 23:08:45 ubuntu NetworkManager[1398]:    SCPlugin-Ifupdown: (163867680) ... get_connections.
Sep 28 23:08:45 ubuntu NetworkManager[1398]:    SCPlugin-Ifupdown: (163867680) ... get_connections (managed=false): return empty list.
Sep 28 23:08:45 ubuntu modem-manager[1441]: <info>  Loaded plugin MotoC
Sep 28 23:08:45 ubuntu NetworkManager[1398]:    Ifupdown: get unmanaged devices count: 0
Sep 28 23:08:45 ubuntu NetworkManager[1398]: <info> WiFi enabled by radio killswitch; enabled by state file
Sep 28 23:08:45 ubuntu NetworkManager[1398]: <info> WWAN enabled by radio killswitch; enabled by state file
Sep 28 23:08:45 ubuntu NetworkManager[1398]: <info> WiMAX enabled by radio killswitch; enabled by state file
Sep 28 23:08:45 ubuntu NetworkManager[1398]: <info> Networking is enabled by state file
Sep 28 23:08:45 ubuntu NetworkManager[1398]: <info> (eth0): carrier is OFF
Sep 28 23:08:45 ubuntu NetworkManager[1398]: <info> (eth0): new Ethernet device (driver: '8139too' ifindex: 2)
Sep 28 23:08:45 ubuntu NetworkManager[1398]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Sep 28 23:08:45 ubuntu NetworkManager[1398]: <info> (eth0): now managed
Sep 28 23:08:45 ubuntu NetworkManager[1398]: <info> (eth0): device state change: 1 -> 2 (reason 2)
Sep 28 23:08:45 ubuntu NetworkManager[1398]: <info> (eth0): bringing up device.
Sep 28 23:08:45 ubuntu kernel: [  100.480459] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Sep 28 23:08:45 ubuntu NetworkManager[1398]: <info> (eth0): preparing device.
Sep 28 23:08:45 ubuntu modem-manager[1441]: <info>  Loaded plugin Nokia
Sep 28 23:08:45 ubuntu NetworkManager[1398]: <info> (eth0): deactivating device (reason: 2).
Sep 28 23:08:45 ubuntu NetworkManager[1398]: <info> Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:13.0/net/eth0
Sep 28 23:08:45 ubuntu modem-manager[1441]: <info>  Loaded plugin Novatel
Sep 28 23:08:45 ubuntu modem-manager[1441]: <info>  Loaded plugin Option
Sep 28 23:08:45 ubuntu modem-manager[1441]: <info>  Loaded plugin Sierra
Sep 28 23:08:45 ubuntu modem-manager[1441]: <info>  Loaded plugin SimTech
Sep 28 23:08:45 ubuntu modem-manager[1441]: <info>  Loaded plugin X22X
Sep 28 23:08:45 ubuntu NetworkManager[1398]: <info> (eth0): carrier now ON (device state 2)
Sep 28 23:08:45 ubuntu NetworkManager[1398]: <info> (eth0): device state change: 2 -> 3 (reason 40)
Sep 28 23:08:45 ubuntu NetworkManager[1398]: <info> modem-manager is now available
Sep 28 23:08:45 ubuntu modem-manager[1441]: <info>  Loaded plugin ZTE
Sep 28 23:08:45 ubuntu NetworkManager[1398]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Sep 28 23:08:45 ubuntu NetworkManager[1398]: <info> Trying to start the supplicant...
Sep 28 23:08:45 ubuntu NetworkManager[1398]: <info> Activation (eth0) starting connection 'Auto eth0'
Sep 28 23:08:45 ubuntu NetworkManager[1398]: <info> (eth0): device state change: 3 -> 4 (reason 0)
Sep 28 23:08:45 ubuntu NetworkManager[1398]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 28 23:08:45 ubuntu NetworkManager[1398]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Sep 28 23:08:45 ubuntu NetworkManager[1398]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Sep 28 23:08:45 ubuntu NetworkManager[1398]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Sep 28 23:08:45 ubuntu NetworkManager[1398]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Sep 28 23:08:45 ubuntu NetworkManager[1398]: <info> (eth0): device state change: 4 -> 5 (reason 0)
Sep 28 23:08:45 ubuntu NetworkManager[1398]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Sep 28 23:08:45 ubuntu NetworkManager[1398]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Sep 28 23:08:45 ubuntu NetworkManager[1398]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Sep 28 23:08:45 ubuntu NetworkManager[1398]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Sep 28 23:08:45 ubuntu NetworkManager[1398]: <info> (eth0): device state change: 5 -> 7 (reason 0)
Sep 28 23:08:45 ubuntu NetworkManager[1398]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Sep 28 23:08:45 ubuntu NetworkManager[1398]: <info> dhclient started with pid 1569
Sep 28 23:08:45 ubuntu NetworkManager[1398]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Sep 28 23:08:45 ubuntu kernel: [  100.987110] ppdev: user-space parallel port driver
Sep 28 23:08:46 ubuntu avahi-daemon[1288]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::214:85ff:feb9:228a.
Sep 28 23:08:46 ubuntu avahi-daemon[1288]: New relevant interface eth0.IPv6 for mDNS.
Sep 28 23:08:46 ubuntu avahi-daemon[1288]: Registering new address record for fe80::214:85ff:feb9:228a on eth0.*.
Sep 28 23:08:47 ubuntu dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Sep 28 23:08:47 ubuntu dhclient: Copyright 2004-2010 Internet Systems Consortium.
Sep 28 23:08:47 ubuntu dhclient: All rights reserved.
Sep 28 23:08:47 ubuntu dhclient: For info, please visit https://www.isc.org/software/dhcp/
Sep 28 23:08:47 ubuntu dhclient: 
Sep 28 23:08:48 ubuntu cron[1596]: (CRON) INFO (pidfile fd = 3)
Sep 28 23:08:48 ubuntu acpid: starting up with proc fs
Sep 28 23:08:48 ubuntu dhclient: Listening on LPF/eth0/00:14:85:b9:22:8a
Sep 28 23:08:48 ubuntu dhclient: Sending on   LPF/eth0/00:14:85:b9:22:8a
Sep 28 23:08:48 ubuntu dhclient: Sending on   Socket/fallback
Sep 28 23:08:48 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Sep 28 23:08:48 ubuntu NetworkManager[1398]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Sep 28 23:08:48 ubuntu dhclient: DHCPOFFER of 192.168.1.28 from 192.168.1.20
Sep 28 23:08:48 ubuntu dhclient: DHCPREQUEST of 192.168.1.28 on eth0 to 255.255.255.255 port 67
Sep 28 23:08:48 ubuntu dhclient: DHCPACK of 192.168.1.28 from 192.168.1.20
Sep 28 23:08:48 ubuntu cron[1621]: (CRON) STARTUP (fork ok)
Sep 28 23:08:49 ubuntu dhclient: bound to 192.168.1.28 -- renewal in 1485 seconds.
Sep 28 23:08:49 ubuntu NetworkManager[1398]: <info> (eth0): DHCPv4 state changed preinit -> bound
Sep 28 23:08:49 ubuntu NetworkManager[1398]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Sep 28 23:08:49 ubuntu NetworkManager[1398]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Sep 28 23:08:49 ubuntu NetworkManager[1398]: <info>   address 192.168.1.28
Sep 28 23:08:49 ubuntu NetworkManager[1398]: <info>   prefix 24 (255.255.255.0)
Sep 28 23:08:49 ubuntu NetworkManager[1398]: <info>   gateway 192.168.1.20
Sep 28 23:08:49 ubuntu NetworkManager[1398]: <info>   hostname 'ubuntu'
Sep 28 23:08:49 ubuntu NetworkManager[1398]: <info>   nameserver '192.168.1.20'
Sep 28 23:08:49 ubuntu NetworkManager[1398]: <info> Scheduling stage 5
Sep 28 23:08:49 ubuntu NetworkManager[1398]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Sep 28 23:08:49 ubuntu NetworkManager[1398]: <info> Done scheduling stage 5
Sep 28 23:08:49 ubuntu NetworkManager[1398]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Sep 28 23:08:49 ubuntu NetworkManager[1398]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Sep 28 23:08:49 ubuntu avahi-daemon[1288]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.28.
Sep 28 23:08:49 ubuntu avahi-daemon[1288]: New relevant interface eth0.IPv4 for mDNS.
Sep 28 23:08:49 ubuntu avahi-daemon[1288]: Registering new address record for 192.168.1.28 on eth0.IPv4.
Sep 28 23:08:49 ubuntu cron[1621]: (CRON) INFO (Running @reboot jobs)
Sep 28 23:08:49 ubuntu acpid: 32 rules loaded
Sep 28 23:08:49 ubuntu acpid: waiting for events: event logging is off
Sep 28 23:08:50 ubuntu NetworkManager[1398]: <info> (eth0): device state change: 7 -> 8 (reason 0)
Sep 28 23:08:50 ubuntu NetworkManager[1398]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Sep 28 23:08:50 ubuntu NetworkManager[1398]: <info> Activation (eth0) successful, device activated.
Sep 28 23:08:50 ubuntu NetworkManager[1398]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Sep 28 23:08:51 ubuntu kernel: [  106.933770] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
Sep 28 23:08:51 ubuntu kernel: [  106.933776] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
Sep 28 23:08:51 ubuntu kernel: [  106.933795] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
Sep 28 23:08:51 ubuntu kernel: [  106.933957] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
Sep 28 23:08:55 ubuntu kernel: [  110.960009] eth0: no IPv6 routers present
Sep 28 23:09:00 ubuntu acpid: client connected from 2023[0:0]
Sep 28 23:09:00 ubuntu acpid: 1 client rule loaded
Sep 28 23:09:01 ubuntu kernel: [  117.134631] lp0: using parport0 (interrupt-driven).
Sep 28 23:09:06 ubuntu udev-configure-printer: add /devices/pnp0/00:0b/printer/lp0
Sep 28 23:09:06 ubuntu udev-configure-printer: Failed to get parent
Sep 28 23:09:06 ubuntu udev-configure-printer: add /module/lp
Sep 28 23:09:06 ubuntu udev-configure-printer: Failed to get parent
Sep 28 21:09:20 ubuntu ntpdate[2408]: step time server 91.189.94.4 offset -7200.379622 sec
Sep 28 21:09:35 ubuntu rtkit-daemon[2940]: Successfully called chroot.
Sep 28 21:09:35 ubuntu rtkit-daemon[2940]: Successfully dropped privileges.
Sep 28 21:09:35 ubuntu rtkit-daemon[2940]: Successfully limited resources.
Sep 28 21:09:35 ubuntu rtkit-daemon[2940]: Running.
Sep 28 21:09:35 ubuntu rtkit-daemon[2940]: Watchdog thread running.
Sep 28 21:09:35 ubuntu rtkit-daemon[2940]: Canary thread running.
Sep 28 21:09:37 ubuntu rtkit-daemon[2940]: Successfully made thread 2938 of process 2938 (n/a) owned by '999' high priority at nice level -11.
Sep 28 21:09:37 ubuntu rtkit-daemon[2940]: Supervising 1 threads of 1 processes of 1 users.
Sep 28 21:09:39 ubuntu ubiquity[2945]: Ubiquity 2.6.10
Sep 28 21:09:41 ubuntu rtkit-daemon[2940]: Successfully made thread 2953 of process 2938 (n/a) owned by '999' RT at priority 5.
Sep 28 21:09:41 ubuntu rtkit-daemon[2940]: Supervising 2 threads of 1 processes of 1 users.
Sep 28 21:09:41 ubuntu rtkit-daemon[2940]: Successfully made thread 2954 of process 2938 (n/a) owned by '999' RT at priority 5.
Sep 28 21:09:41 ubuntu rtkit-daemon[2940]: Supervising 3 threads of 1 processes of 1 users.
Sep 28 21:09:53 ubuntu ubiquity[2945]: log-output -t ubiquity laptop-detect
Sep 28 21:09:56 ubuntu ubiquity[2945]: log-output -t ubiquity laptop-detect
Sep 28 21:10:01 ubuntu ubiquity[2945]: switched to page language
Sep 28 21:10:05 ubuntu ubiquity[2945]: switched to page prepare
Sep 28 21:10:05 ubuntu ubiquity[2945]: switched to page language
Sep 28 21:10:13 ubuntu localechooser: info: Language = 'en'
Sep 28 21:10:13 ubuntu localechooser: info: line=en;0;US;UTF-8;en_US.UTF-8;;console-setup
Sep 28 21:10:13 ubuntu localechooser: info: Set debian-installer/language = 'en'
Sep 28 21:10:13 ubuntu localechooser: info: Default country = 'US'
Sep 28 21:10:13 ubuntu localechooser: info: Default locale = 'en_US.UTF-8'
Sep 28 21:10:13 ubuntu localechooser: info: Set debian-installer/consoledisplay = 'console-setup'
Sep 28 21:10:14 ubuntu localechooser: info: Set debian-installer/country = 'US'
Sep 28 21:10:14 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Sep 28 21:10:14 ubuntu localechooser: info: System locale (debian-installer/locale) = 'en_US.UTF-8'
Sep 28 21:10:17 ubuntu ubiquity[2945]: debconffilter_done: ubi-language (current: ubi-language)
Sep 28 21:10:30 ubuntu ubiquity[2945]: log-output -t ubiquity setupcon --save-only
Sep 28 21:10:30 ubuntu ubiquity[2945]: log-output -t ubiquity udevadm trigger --subsystem-match=input --action=change
Sep 28 21:10:30 ubuntu ubiquity[2945]: log-output -t ubiquity udevadm settle
Sep 28 21:10:31 ubuntu ubiquity: debconf: DbDriver "targetdb": could not open /target/var/cache/debconf/config.dat
Sep 28 21:10:31 ubuntu ubiquity[2945]: log-output -t ubiquity debconf-copydb configdb targetdb -p ^oem-config/ --config=Name:targetdb --config=Driver:File --config=Filename:/target/var/cache/debconf/config.dat
Sep 28 21:10:31 ubuntu ubiquity: debconf: DbDriver "targetdb": could not open /target/var/cache/debconf/config.dat
Sep 28 21:10:31 ubuntu ubiquity[2945]: log-output -t ubiquity debconf-copydb configdb targetdb -p ^keyboard-configuration/ --config=Name:targetdb --config=Driver:File --config=Filename:/target/var/cache/debconf/config.dat
Sep 28 21:10:31 ubuntu ubiquity: debconf: DbDriver "targetdb": could not open /target/var/cache/debconf/config.dat
Sep 28 21:10:31 ubuntu ubiquity[2945]: log-output -t ubiquity debconf-copydb configdb targetdb -p ^console-setup/ --config=Name:targetdb --config=Driver:File --config=Filename:/target/var/cache/debconf/config.dat
Sep 28 21:10:34 ubuntu gdm-binary[4482]: WARNING: Unable to find users: no seat-id found
Sep 28 21:10:35 ubuntu acpid: client 2023[0:0] has disconnected
Sep 28 21:10:35 ubuntu acpid: client connected from 4493[0:0]
Sep 28 21:10:35 ubuntu acpid: 1 client rule loaded
Sep 28 21:10:36 ubuntu gdm-session-worker[4504]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

```Xorg.0.log

```

[   210.857] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[   210.857] X Protocol Version 11, Revision 0
[   210.857] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[   210.857] Current Operating System: Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[   210.857] Kernel command line: file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity
[   210.858] Build Date: 19 April 2011  03:33:17PM
[   210.858] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[   210.858] Current version of pixman: 0.20.2
[   210.858]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   210.858] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   210.858] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Sep 28 21:10:35 2011
[   210.859] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   210.859] (==) No Layout section.  Using the first Screen section.
[   210.859] (==) No screen section available. Using defaults.
[   210.859] (**) |-->Screen "Default Screen Section" (0)
[   210.859] (**) |   |-->Monitor "<default monitor>"
[   210.859] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   210.859] (==) Automatically adding devices
[   210.859] (==) Automatically enabling devices
[   210.860] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   210.860]     Entry deleted from font path.
[   210.860] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   210.860]     Entry deleted from font path.
[   210.860] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   210.860]     Entry deleted from font path.
[   210.860] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   210.860]     Entry deleted from font path.
[   210.860] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   210.860]     Entry deleted from font path.
[   210.860] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[   210.860] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   210.860] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   210.860] (II) Loader magic: 0x81ffde0
[   210.860] (II) Module ABI versions:
[   210.860]     X.Org ANSI C Emulation: 0.4
[   210.860]     X.Org Video Driver: 10.0
[   210.860]     X.Org XInput driver : 12.3
[   210.860]     X.Org Server Extension : 5.0
[   210.861] (--) PCI:*(0:1:0:0) 10de:0326:1458:3401 rev 161, Mem @ 0xf4000000/16777216, 0xe8000000/134217728, BIOS @ 0x????????/131072
[   210.862] (II) Open ACPI successful (/var/run/acpid.socket)
[   210.862] (II) LoadModule: "extmod"
[   210.863] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   210.863] (II) Module extmod: vendor="X.Org Foundation"
[   210.863]     compiled for 1.10.1, module version = 1.0.0
[   210.863]     Module class: X.Org Server Extension
[   210.863]     ABI class: X.Org Server Extension, version 5.0
[   210.863] (II) Loading extension MIT-SCREEN-SAVER
[   210.863] (II) Loading extension XFree86-VidModeExtension
[   210.863] (II) Loading extension XFree86-DGA
[   210.863] (II) Loading extension DPMS
[   210.863] (II) Loading extension XVideo
[   210.863] (II) Loading extension XVideo-MotionCompensation
[   210.863] (II) Loading extension X-Resource
[   210.863] (II) LoadModule: "dbe"
[   210.864] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   210.864] (II) Module dbe: vendor="X.Org Foundation"
[   210.864]     compiled for 1.10.1, module version = 1.0.0
[   210.864]     Module class: X.Org Server Extension
[   210.864]     ABI class: X.Org Server Extension, version 5.0
[   210.864] (II) Loading extension DOUBLE-BUFFER
[   210.864] (II) LoadModule: "glx"
[   210.865] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   210.865] (II) Module glx: vendor="X.Org Foundation"
[   210.865]     compiled for 1.10.1, module version = 1.0.0
[   210.865]     ABI class: X.Org Server Extension, version 5.0
[   210.865] (==) AIGLX enabled
[   210.865] (II) Loading extension GLX
[   210.865] (II) LoadModule: "record"
[   210.866] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   210.866] (II) Module record: vendor="X.Org Foundation"
[   210.866]     compiled for 1.10.1, module version = 1.13.0
[   210.866]     Module class: X.Org Server Extension
[   210.866]     ABI class: X.Org Server Extension, version 5.0
[   210.866] (II) Loading extension RECORD
[   210.866] (II) LoadModule: "dri"
[   210.867] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   210.867] (II) Module dri: vendor="X.Org Foundation"
[   210.867]     compiled for 1.10.1, module version = 1.0.0
[   210.867]     ABI class: X.Org Server Extension, version 5.0
[   210.867] (II) Loading extension XFree86-DRI
[   210.867] (II) LoadModule: "dri2"
[   210.868] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   210.868] (II) Module dri2: vendor="X.Org Foundation"
[   210.868]     compiled for 1.10.1, module version = 1.2.0
[   210.868]     ABI class: X.Org Server Extension, version 5.0
[   210.868] (II) Loading extension DRI2
[   210.868] (==) Matched nvidia as autoconfigured driver 0
[   210.868] (==) Matched nouveau as autoconfigured driver 1
[   210.868] (==) Matched nv as autoconfigured driver 2
[   210.868] (==) Matched vesa as autoconfigured driver 3
[   210.868] (==) Matched fbdev as autoconfigured driver 4
[   210.868] (==) Assigned the driver to the xf86ConfigLayout
[   210.868] (II) LoadModule: "nvidia"
[   210.870] (WW) Warning, couldn't open module nvidia
[   210.870] (II) UnloadModule: "nvidia"
[   210.870] (II) Unloading nvidia
[   210.870] (EE) Failed to load module "nvidia" (module does not exist, 0)
[   210.870] (II) LoadModule: "nouveau"
[   210.870] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   210.871] (II) Module nouveau: vendor="X.Org Foundation"
[   210.871]     compiled for 1.10.0, module version = 0.0.16
[   210.871]     Module class: X.Org Video Driver
[   210.871]     ABI class: X.Org Video Driver, version 10.0
[   210.871] (II) LoadModule: "nv"
[   210.872] (WW) Warning, couldn't open module nv
[   210.872] (II) UnloadModule: "nv"
[   210.872] (II) Unloading nv
[   210.872] (EE) Failed to load module "nv" (module does not exist, 0)
[   210.872] (II) LoadModule: "vesa"
[   210.873] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   210.873] (II) Module vesa: vendor="X.Org Foundation"
[   210.873]     compiled for 1.10.0, module version = 2.3.0
[   210.873]     Module class: X.Org Video Driver
[   210.873]     ABI class: X.Org Video Driver, version 10.0
[   210.873] (II) LoadModule: "fbdev"
[   210.873] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   210.873] (II) Module fbdev: vendor="X.Org Foundation"
[   210.873]     compiled for 1.10.0, module version = 0.4.2
[   210.873]     ABI class: X.Org Video Driver, version 10.0
[   210.873] (II) NOUVEAU driver Date:   Fri Jan 7 13:33:36 2011 +1000
[   210.873] (II) NOUVEAU driver for NVIDIA chipset families :
[   210.873]     RIVA TNT    (NV04)
[   210.873]     RIVA TNT2   (NV05)
[   210.873]     GeForce 256 (NV10)
[   210.873]     GeForce 2   (NV11, NV15)
[   210.874]     GeForce 4MX (NV17, NV18)
[   210.874]     GeForce 3   (NV20)
[   210.874]     GeForce 4Ti (NV25, NV28)
[   210.874]     GeForce FX  (NV3x)
[   210.874]     GeForce 6   (NV4x)
[   210.874]     GeForce 7   (G7x)
[   210.874]     GeForce 8   (G8x)
[   210.874] (II) VESA: driver for VESA chipsets: vesa
[   210.874] (II) FBDEV: driver for framebuffer: fbdev
[   210.874] (++) using VT number 7

[   210.874] drmOpenDevice: node name is /dev/dri/card0
[   210.874] drmOpenDevice: open result is 8, (OK)
[   210.874] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[   210.874] drmOpenDevice: node name is /dev/dri/card0
[   210.874] drmOpenDevice: open result is 8, (OK)
[   210.874] drmOpenByBusid: drmOpenMinor returns 8
[   210.874] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[   210.874] (II) [drm] nouveau interface version: 0.0.16
[   210.874] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   210.874] (WW) Falling back to old probe method for vesa
[   210.874] (WW) Falling back to old probe method for fbdev
[   210.874] (II) Loading sub module "fbdevhw"
[   210.874] (II) LoadModule: "fbdevhw"
[   210.875] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   210.875] (II) Module fbdevhw: vendor="X.Org Foundation"
[   210.875]     compiled for 1.10.1, module version = 0.0.2
[   210.875]     ABI class: X.Org Video Driver, version 10.0
[   210.876] (II) Loading sub module "dri"
[   210.876] (II) LoadModule: "dri"
[   210.876] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   210.876] (II) Module dri: vendor="X.Org Foundation"
[   210.876]     compiled for 1.10.1, module version = 1.0.0
[   210.876]     ABI class: X.Org Server Extension, version 5.0
[   210.876] (II) NOUVEAU(0): Loaded DRI module
[   210.876] drmOpenDevice: node name is /dev/dri/card0
[   210.876] drmOpenDevice: open result is 9, (OK)
[   210.876] drmOpenDevice: node name is /dev/dri/card0
[   210.876] drmOpenDevice: open result is 9, (OK)
[   210.876] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[   210.876] drmOpenDevice: node name is /dev/dri/card0
[   210.876] drmOpenDevice: open result is 9, (OK)
[   210.876] drmOpenByBusid: drmOpenMinor returns 9
[   210.876] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[   210.876] (II) [drm] DRM interface version 1.4
[   210.877] (II) [drm] DRM open master succeeded.
[   210.877] (--) NOUVEAU(0): Chipset: "NVIDIA NV34"
[   210.877] (II) NOUVEAU(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   210.877] (==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
[   210.877] (==) NOUVEAU(0): RGB weight 888
[   210.877] (==) NOUVEAU(0): Default visual is TrueColor
[   210.877] (==) NOUVEAU(0): Using HW cursor
[   210.877] (==) NOUVEAU(0): GLX sync to VBlank disabled.
[   210.982] (II) NOUVEAU(0): Output VGA-1 has no monitor section
[   211.048] (II) NOUVEAU(0): Output DVI-I-1 has no monitor section
[   211.104] (II) NOUVEAU(0): Output TV-1 has no monitor section
[   211.209] (II) NOUVEAU(0): EDID for output VGA-1
[   211.210] (II) NOUVEAU(0): Manufacturer: PHL  Model: 82b  Serial#: 361404
[   211.210] (II) NOUVEAU(0): Year: 2006  Week: 2
[   211.210] (II) NOUVEAU(0): EDID Version: 1.3
[   211.210] (II) NOUVEAU(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[   211.210] (II) NOUVEAU(0): Signal levels configurable
[   211.210] (II) NOUVEAU(0): Sync:  Separate  Composite  SyncOnGreenSerration on. V.Sync Pulse req. if CompSync or SyncOnGreen
[   211.210] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[   211.210] (II) NOUVEAU(0): Gamma: 2.20
[   211.210] (II) NOUVEAU(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[   211.210] (II) NOUVEAU(0): Default color space is primary color space
[   211.210] (II) NOUVEAU(0): First detailed timing is preferred mode
[   211.210] (II) NOUVEAU(0): redX: 0.639 redY: 0.339   greenX: 0.284 greenY: 0.604
[   211.210] (II) NOUVEAU(0): blueX: 0.143 blueY: 0.085   whiteX: 0.313 whiteY: 0.329
[   211.210] (II) NOUVEAU(0): Supported established timings:
[   211.210] (II) NOUVEAU(0): 720x400@70Hz
[   211.210] (II) NOUVEAU(0): 640x480@60Hz
[   211.210] (II) NOUVEAU(0): 640x480@67Hz
[   211.210] (II) NOUVEAU(0): 640x480@72Hz
[   211.210] (II) NOUVEAU(0): 640x480@75Hz
[   211.210] (II) NOUVEAU(0): 800x600@56Hz
[   211.210] (II) NOUVEAU(0): 800x600@60Hz
[   211.210] (II) NOUVEAU(0): 800x600@72Hz
[   211.210] (II) NOUVEAU(0): 800x600@75Hz
[   211.210] (II) NOUVEAU(0): 832x624@75Hz
[   211.210] (II) NOUVEAU(0): 1024x768@60Hz
[   211.210] (II) NOUVEAU(0): 1024x768@70Hz
[   211.210] (II) NOUVEAU(0): 1024x768@75Hz
[   211.210] (II) NOUVEAU(0): 1280x1024@75Hz
[   211.210] (II) NOUVEAU(0): 1152x864@75Hz
[   211.210] (II) NOUVEAU(0): Manufacturer's mask: 0
[   211.210] (II) NOUVEAU(0): Supported standard timings:
[   211.210] (II) NOUVEAU(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[   211.210] (II) NOUVEAU(0): Supported detailed timing:
[   211.210] (II) NOUVEAU(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
[   211.210] (II) NOUVEAU(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[   211.210] (II) NOUVEAU(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[   211.210] (II) NOUVEAU(0): Serial No:  BZ  361404
[   211.210] (II) NOUVEAU(0): Monitor name: Philips 170S
[   211.210] (II) NOUVEAU(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 83 kHz, PixClock max 145 MHz
[   211.210] (II) NOUVEAU(0): EDID (in hex):
[   211.210] (II) NOUVEAU(0):     00ffffffffffff00410c2b08bc830500
[   211.210] (II) NOUVEAU(0):     021001031f221b78eebeb5a356489a24
[   211.210] (II) NOUVEAU(0):     155054bfef8081800101010101010101
[   211.210] (II) NOUVEAU(0):     010101010101302a009851002a403070
[   211.210] (II) NOUVEAU(0):     1300520e1100001e000000ff0020425a
[   211.210] (II) NOUVEAU(0):     20203336313430340a20000000fc0050
[   211.210] (II) NOUVEAU(0):     68696c69707320313730530a000000fd
[   211.210] (II) NOUVEAU(0):     00384c1e530e000a2020202020200008
[   211.210] (II) NOUVEAU(0): EDID vendor "PHL", prod id 2091
[   211.210] (II) NOUVEAU(0): Using EDID range info for horizontal sync
[   211.210] (II) NOUVEAU(0): Using EDID range info for vertical refresh
[   211.210] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   211.210] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   211.210] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   211.210] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   211.210] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   211.210] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   211.210] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   211.211] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   211.211] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   211.211] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   211.211] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   211.211] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   211.211] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   211.211] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   211.211] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   211.211] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   211.211] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   211.211] (II) NOUVEAU(0): Printing probed modes for output VGA-1
[   211.211] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   211.211] (II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   211.211] (II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   211.211] (II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[   211.211] (II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   211.211] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   211.211] (II) NOUVEAU(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   211.211] (II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   211.211] (II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   211.211] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   211.211] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   211.211] (II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
[   211.211] (II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   211.211] (II) NOUVEAU(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   211.211] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   211.211] (II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   211.276] (II) NOUVEAU(0): EDID for output DVI-I-1
[   211.332] (II) NOUVEAU(0): EDID for output TV-1
[   211.332] (II) NOUVEAU(0): Output VGA-1 connected
[   211.332] (II) NOUVEAU(0): Output DVI-I-1 disconnected
[   211.332] (II) NOUVEAU(0): Output TV-1 disconnected
[   211.332] (II) NOUVEAU(0): Using exact sizes for initial modes
[   211.332] (II) NOUVEAU(0): Output VGA-1 using initial mode 1280x1024
[   211.332] (II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   211.332] (--) NOUVEAU(0): Virtual size is 1280x1024 (pitch 0)
[   211.332] (**) NOUVEAU(0):  Driver mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
[   211.332] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   211.332] (**) NOUVEAU(0):  Driver mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
[   211.332] (II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   211.332] (**) NOUVEAU(0):  Driver mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
[   211.332] (II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   211.332] (**) NOUVEAU(0):  Driver mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.1 kHz, 75.1 Hz
[   211.332] (II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[   211.332] (**) NOUVEAU(0):  Driver mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.1 Hz
[   211.332] (II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   211.332] (**) NOUVEAU(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
[   211.332] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   211.332] (**) NOUVEAU(0):  Driver mode "832x624": 57.3 MHz (scaled from 0.0 MHz), 49.7 kHz, 74.6 Hz
[   211.332] (II) NOUVEAU(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   211.332] (**) NOUVEAU(0):  Driver mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.2 Hz
[   211.332] (II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   211.332] (**) NOUVEAU(0):  Driver mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
[   211.332] (II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   211.332] (**) NOUVEAU(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
[   211.332] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   211.332] (**) NOUVEAU(0):  Driver mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.2 Hz
[   211.332] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   211.332] (**) NOUVEAU(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.8 Hz
[   211.332] (II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
[   211.332] (**) NOUVEAU(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
[   211.332] (II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   211.332] (**) NOUVEAU(0):  Driver mode "640x480": 30.2 MHz (scaled from 0.0 MHz), 35.0 kHz, 66.7 Hz
[   211.332] (II) NOUVEAU(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   211.332] (**) NOUVEAU(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
[   211.332] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   211.332] (**) NOUVEAU(0):  Driver mode "720x400": 28.3 MHz (scaled from 0.0 MHz), 31.5 kHz, 70.1 Hz
[   211.332] (II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   211.332] (**) NOUVEAU(0): Display dimensions: (340, 270) mm
[   211.332] (**) NOUVEAU(0): DPI set to (95, 96)
[   211.332] (II) Loading sub module "fb"
[   211.332] (II) LoadModule: "fb"
[   211.333] (II) Loading /usr/lib/xorg/modules/libfb.so
[   211.333] (II) Module fb: vendor="X.Org Foundation"
[   211.333]     compiled for 1.10.1, module version = 1.0.0
[   211.334]     ABI class: X.Org ANSI C Emulation, version 0.4
[   211.334] (II) Loading sub module "exa"
[   211.334] (II) LoadModule: "exa"
[   211.334] (II) Loading /usr/lib/xorg/modules/libexa.so
[   211.334] (II) Module exa: vendor="X.Org Foundation"
[   211.334]     compiled for 1.10.1, module version = 2.5.0
[   211.334]     ABI class: X.Org Video Driver, version 10.0
[   211.334] (II) Loading sub module "shadowfb"
[   211.334] (II) LoadModule: "shadowfb"
[   211.335] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[   211.340] (II) Module shadowfb: vendor="X.Org Foundation"
[   211.340]     compiled for 1.10.1, module version = 1.0.0
[   211.340]     ABI class: X.Org ANSI C Emulation, version 0.4
[   211.340] (II) UnloadModule: "vesa"
[   211.340] (II) Unloading vesa
[   211.340] (II) UnloadModule: "fbdev"
[   211.340] (II) Unloading fbdev
[   211.340] (II) UnloadModule: "fbdevhw"
[   211.340] (II) Unloading fbdevhw
[   211.340] (--) Depth 24 pixmap format is 32 bpp
[   211.341] (II) NOUVEAU(0): Opened GPU channel 1
[   211.341] (II) NOUVEAU(0): [DRI2] Setup complete
[   211.341] (II) NOUVEAU(0): [DRI2]   DRI driver: nouveau
[   211.341] (II) NOUVEAU(0): GART: 64MiB available
[   211.343] (II) NOUVEAU(0): GART: Allocated 16MiB as a scratch buffer
[   211.343] (II) EXA(0): Driver allocated offscreen pixmaps
[   211.343] (II) EXA(0): Driver registered support for the following operations:
[   211.343] (II)         Solid
[   211.343] (II)         Copy
[   211.343] (II)         Composite (RENDER acceleration)
[   211.343] (II)         UploadToScreen
[   211.343] (II)         DownloadFromScreen
[   211.343] (==) NOUVEAU(0): Backing store disabled
[   211.343] (==) NOUVEAU(0): Silken mouse enabled
[   211.348] (II) NOUVEAU(0): [XvMC] Associated with NV30 texture adapter.
[   211.348] (II) NOUVEAU(0): [XvMC] Extension initialized.
[   211.348] (==) NOUVEAU(0): DPMS enabled
[   211.348] (II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   211.348] (--) RandR disabled
[   211.348] (II) Initializing built-in extension Generic Event Extension
[   211.348] (II) Initializing built-in extension SHAPE
[   211.348] (II) Initializing built-in extension MIT-SHM
[   211.348] (II) Initializing built-in extension XInputExtension
[   211.348] (II) Initializing built-in extension XTEST
[   211.348] (II) Initializing built-in extension BIG-REQUESTS
[   211.348] (II) Initializing built-in extension SYNC
[   211.348] (II) Initializing built-in extension XKEYBOARD
[   211.348] (II) Initializing built-in extension XC-MISC
[   211.348] (II) Initializing built-in extension SECURITY
[   211.348] (II) Initializing built-in extension XINERAMA
[   211.348] (II) Initializing built-in extension XFIXES
[   211.348] (II) Initializing built-in extension RENDER
[   211.348] (II) Initializing built-in extension RANDR
[   211.349] (II) Initializing built-in extension COMPOSITE
[   211.349] (II) Initializing built-in extension DAMAGE
[   211.349] (II) Initializing built-in extension GESTURE
[   211.377] (II) AIGLX: Trying DRI driver /usr/lib/dri/nouveau_dri.so
[   211.378] (II) AIGLX: dlopen of /usr/lib/dri/nouveau_dri.so failed (/usr/lib/dri/nouveau_dri.so: cannot open shared object file: No such file or directory)
[   211.378] (II) AIGLX: Trying DRI driver /usr/lib/dri-alternates/nouveau_dri.so
[   211.378] (II) AIGLX: dlopen of /usr/lib/dri-alternates/nouveau_dri.so failed (/usr/lib/dri-alternates/nouveau_dri.so: cannot open shared object file: No such file or directory)
[   211.378] (II) AIGLX: Trying DRI driver /usr/lib32/dri/nouveau_dri.so
[   211.378] (II) AIGLX: dlopen of /usr/lib32/dri/nouveau_dri.so failed (/usr/lib32/dri/nouveau_dri.so: cannot open shared object file: No such file or directory)
[   211.378] (II) AIGLX: Trying DRI driver /usr/lib32/dri-alternates/nouveau_dri.so
[   211.378] (II) AIGLX: dlopen of /usr/lib32/dri-alternates/nouveau_dri.so failed (/usr/lib32/dri-alternates/nouveau_dri.so: cannot open shared object file: No such file or directory)
[   211.378] (II) AIGLX: reverting to software rendering
[   211.378] (II) AIGLX: Screen 0 is not DRI capable
[   211.378] (II) AIGLX: Trying DRI driver /usr/lib/dri/swrast_dri.so
[   211.516] (II) AIGLX: Loaded and initialized swrast
[   211.516] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[   211.519] (II) NOUVEAU(0): NVEnterVT is called.
[   211.519] (II) NOUVEAU(0): Setting screen physical size to 338 x 270
[   211.519] resize called 1280 1024
[   211.536] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   211.550] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   211.550] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   211.550] (II) LoadModule: "evdev"
[   211.551] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   211.552] (II) Module evdev: vendor="X.Org Foundation"
[   211.552]     compiled for 1.10.0.902, module version = 2.6.0
[   211.552]     Module class: X.Org XInput Driver
[   211.552]     ABI class: X.Org XInput driver, version 12.3
[   211.552] (II) Using input driver 'evdev' for 'Power Button'
[   211.552] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   211.552] (**) Power Button: always reports core events
[   211.552] (**) Power Button: Device: "/dev/input/event1"
[   211.552] (--) Power Button: Found keys
[   211.552] (II) Power Button: Configuring as keyboard
[   211.552] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[   211.552] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   211.552] (**) Option "xkb_rules" "evdev"
[   211.552] (**) Option "xkb_model" "pc105"
[   211.552] (**) Option "xkb_layout" "us"
[   211.556] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   211.556] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   211.556] (II) Using input driver 'evdev' for 'Power Button'
[   211.556] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   211.556] (**) Power Button: always reports core events
[   211.556] (**) Power Button: Device: "/dev/input/event0"
[   211.556] (--) Power Button: Found keys
[   211.556] (II) Power Button: Configuring as keyboard
[   211.556] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[   211.556] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   211.556] (**) Option "xkb_rules" "evdev"
[   211.556] (**) Option "xkb_model" "pc105"
[   211.556] (**) Option "xkb_layout" "us"
[   211.563] (II) config/udev: Adding input device HID 04f3:0103 (/dev/input/event2)
[   211.563] (**) HID 04f3:0103: Applying InputClass "evdev keyboard catchall"
[   211.563] (II) Using input driver 'evdev' for 'HID 04f3:0103'
[   211.563] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   211.563] (**) HID 04f3:0103: always reports core events
[   211.563] (**) HID 04f3:0103: Device: "/dev/input/event2"
[   211.563] (--) HID 04f3:0103: Found keys
[   211.563] (II) HID 04f3:0103: Configuring as keyboard
[   211.563] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:10.1/usb3/3-1/3-1:1.0/input/input2/event2"
[   211.563] (II) XINPUT: Adding extended input device "HID 04f3:0103" (type: KEYBOARD)
[   211.563] (**) Option "xkb_rules" "evdev"
[   211.563] (**) Option "xkb_model" "pc105"
[   211.563] (**) Option "xkb_layout" "us"
[   211.565] (II) config/udev: Adding input device HID 04f3:0103 (/dev/input/event3)
[   211.565] (**) HID 04f3:0103: Applying InputClass "evdev keyboard catchall"
[   211.565] (II) Using input driver 'evdev' for 'HID 04f3:0103'
[   211.565] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   211.565] (**) HID 04f3:0103: always reports core events
[   211.565] (**) HID 04f3:0103: Device: "/dev/input/event3"
[   211.565] (--) HID 04f3:0103: Found 1 mouse buttons
[   211.565] (--) HID 04f3:0103: Found scroll wheel(s)
[   211.565] (--) HID 04f3:0103: Found relative axes
[   211.565] (--) HID 04f3:0103: Found absolute axes
[   211.565] (II) evdev-grail: failed to open grail, no gesture support
[   211.565] (--) HID 04f3:0103: Found keys
[   211.565] (II) HID 04f3:0103: Configuring as mouse
[   211.565] (II) HID 04f3:0103: Configuring as keyboard
[   211.565] (II) HID 04f3:0103: Adding scrollwheel support
[   211.565] (**) HID 04f3:0103: YAxisMapping: buttons 4 and 5
[   211.565] (**) HID 04f3:0103: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   211.565] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:10.1/usb3/3-1/3-1:1.1/input/input3/event3"
[   211.565] (II) XINPUT: Adding extended input device "HID 04f3:0103" (type: KEYBOARD)
[   211.565] (**) Option "xkb_rules" "evdev"
[   211.565] (**) Option "xkb_model" "pc105"
[   211.565] (**) Option "xkb_layout" "us"
[   211.566] (EE) HID 04f3:0103: failed to initialize for relative axes.
[   211.566] (II) HID 04f3:0103: initialized for absolute axes.
[   211.566] (**) HID 04f3:0103: (accel) keeping acceleration scheme 1
[   211.566] (**) HID 04f3:0103: (accel) acceleration profile 0
[   211.566] (**) HID 04f3:0103: (accel) acceleration factor: 2.000
[   211.566] (**) HID 04f3:0103: (accel) acceleration threshold: 4
[   211.567] (II) config/udev: Adding input device Logitech Logitech USB Optical Mouse (/dev/input/event4)
[   211.567] (**) Logitech Logitech USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[   211.567] (II) Using input driver 'evdev' for 'Logitech Logitech USB Optical Mouse'
[   211.567] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   211.567] (**) Logitech Logitech USB Optical Mouse: always reports core events
[   211.567] (**) Logitech Logitech USB Optical Mouse: Device: "/dev/input/event4"
[   211.567] (--) Logitech Logitech USB Optical Mouse: Found 3 mouse buttons
[   211.567] (--) Logitech Logitech USB Optical Mouse: Found scroll wheel(s)
[   211.567] (--) Logitech Logitech USB Optical Mouse: Found relative axes
[   211.567] (--) Logitech Logitech USB Optical Mouse: Found x and y relative axes
[   211.567] (II) Logitech Logitech USB Optical Mouse: Configuring as mouse
[   211.567] (II) Logitech Logitech USB Optical Mouse: Adding scrollwheel support
[   211.567] (**) Logitech Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
[   211.567] (**) Logitech Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   211.567] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:10.1/usb3/3-2/3-2:1.0/input/input4/event4"
[   211.567] (II) XINPUT: Adding extended input device "Logitech Logitech USB Optical Mouse" (type: MOUSE)
[   211.567] (II) Logitech Logitech USB Optical Mouse: initialized for relative axes.
[   211.568] (**) Logitech Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
[   211.568] (**) Logitech Logitech USB Optical Mouse: (accel) acceleration profile 0
[   211.568] (**) Logitech Logitech USB Optical Mouse: (accel) acceleration factor: 2.000
[   211.568] (**) Logitech Logitech USB Optical Mouse: (accel) acceleration threshold: 4
[   211.568] (II) config/udev: Adding input device Logitech Logitech USB Optical Mouse (/dev/input/mouse0)
[   211.568] (II) No input driver/identifier specified (ignoring)
[   216.368] (II) NOUVEAU(0): EDID vendor "PHL", prod id 2091
[   216.368] (II) NOUVEAU(0): Using hsync ranges from config file
[   216.368] (II) NOUVEAU(0): Using vrefresh ranges from config file
[   216.368] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   216.368] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   216.368] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   216.368] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   216.368] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   216.369] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   216.369] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   216.369] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   216.369] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   216.369] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   216.369] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   216.369] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   216.369] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   216.369] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   216.369] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   216.369] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   216.369] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   216.846] (II) NOUVEAU(0): EDID vendor "PHL", prod id 2091
[   216.846] (II) NOUVEAU(0): Using hsync ranges from config file
[   216.846] (II) NOUVEAU(0): Using vrefresh ranges from config file
[   216.846] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   216.846] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   216.846] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   216.846] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   216.846] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   216.846] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   216.846] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   216.846] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   216.846] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   216.846] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   216.846] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   216.846] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   216.846] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   216.846] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   216.846] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   216.846] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   216.846] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   217.181] (II) NOUVEAU(0): EDID vendor "PHL", prod id 2091
[   217.181] (II) NOUVEAU(0): Using hsync ranges from config file
[   217.181] (II) NOUVEAU(0): Using vrefresh ranges from config file
[   217.181] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   217.181] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   217.181] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   217.181] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   217.181] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   217.181] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   217.181] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   217.181] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   217.181] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   217.181] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   217.181] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   217.181] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   217.181] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   217.181] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   217.181] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   217.181] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   217.182] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   217.515] (II) NOUVEAU(0): EDID vendor "PHL", prod id 2091
[   217.515] (II) NOUVEAU(0): Using hsync ranges from config file
[   217.515] (II) NOUVEAU(0): Using vrefresh ranges from config file
[   217.515] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   217.515] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   217.515] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   217.515] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   217.515] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   217.515] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   217.515] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   217.515] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   217.515] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   217.515] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   217.515] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   217.515] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   217.515] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   217.515] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   217.515] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   217.515] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   217.515] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   226.604] (II) NOUVEAU(0): EDID vendor "PHL", prod id 2091
[   226.604] (II) NOUVEAU(0): Using hsync ranges from config file
[   226.604] (II) NOUVEAU(0): Using vrefresh ranges from config file
[   226.604] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   226.604] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   226.604] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   226.604] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   226.604] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   226.604] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   226.604] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   226.604] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   226.604] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   226.604] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   226.604] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   226.604] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   226.604] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   226.604] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   226.604] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   226.604] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   226.605] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)

```

---

### Post by new123 on 2011-09-28
> **MAFoElffen said:**
> [U]
PART II[/U]
Note- [COLOR=Red]Do not go on to Part II until you have posted the answers and logs from Part I[/COLOR]... and have some kind of feedback from me on those.  That may change what is below for a solution...

Compiz?
```

gconftool-2 --recursive-unset /apps/compiz*

```should have reset anythig in compiz back to defaults.  But there is also 
```

rm -rf .gconf

```which would delete all user changes and start fresh...
If those didn't work, you might try: 
```

compiz --replace

```If none of those work:
```

sudo stop gdm
sudo apt-get update
sudo apt-get remove --purge ubuntu-desktop
sudo apt-get install ubuntu-desktop
sudo apt-get upgrade
sudo startx

```Which would replace all the app's, gnome, compiz, metacity, xserver, etc...  Of course there is always trying a fresh reinstall and see if it gets to the same point....  It "was" a fresh install a few days ago, so he is not losing anything with that.

I have just did all steps of part two, and at startup I get MsgBox :
"It seems like you do not have the hardware requrements to run Unity. Please choose Ubuntu Classic at login screen and you will be using traditional envroment"
(seems like [LinuxFan999]("http://ubuntuforums.org/member.php?u=1448317") was right)

but anyway I log in as always I did, and all shown up, menus etc. just like I run it from LiveCD. (Thats good) but the only difference is FireFox cant start, I get error msg when I try to run it :
"You Firefox profile cannot be loaded. It may be missing or inaccessible."

---

### Post by MAFoElffen on 2011-09-28
> **new123 said:**
> I have just did all steps of part two, and at startup I get MsgBox :
"It seems like you do not have the hardware requrements to run Unity. Please choose Ubuntu Classic at login screen and you will be using traditional envroment"
(seems like [LinuxFan999]("http://ubuntuforums.org/member.php?u=1448317") was right)

but anyway I log in as always I did, and all shown up, menus etc. just like I run it from LiveCD. (Thats good) but the only difference is FireFox cant start, I get error msg when I try to run it :
"You Firefox profile cannot be loaded. It may be missing or inaccessible."
"No Unity" is also what I said when I saw your video card...  
> **new123 said:**
> 
```

Card name: NVIDIA GeForce FX 5500
Manufacturer: NVIDIA
Chip type: GeForce FX 5500
Display Memory: 128.0 MB
Current Mode: 1280 x 1024 (32 bit) (60Hz)

```Thank you for the clarifications and info. [COLOR=Red] So you realize that your  card won't run Unity and is on the cusp with having abilities  for  "screen effects" right?[/COLOR]

NVidia and Unity starts playing togetther at the Geoforce 6 series and above.  That's why I asked you to run "Ubuntu Classic".

Memory upgrade? IMHO- 512GB is plenty of memory for him.  As I have plenty of test boxes here (8 running desktop edition) Gnome minimum is 256MB, better with 512MB (even under Oneiric).  1GB runs faster and mutlit-tasks better, but not required.  Now if you were running SLI, I'd bump that up.

For your Firefox profile issue:

(Back up your ~/.mozilla folder.)  
- Open nautilus, 
- Go to your home folder
- Hit ctrl+h (to show hidden files) 
- Right click on the .mozilla folder
- Select "rename".  
- Rename the folder to .backup-mozilla.  
- Try to start Firefox. 

The above process should start the Firefox applicattion and since it doesn't find a .mozilla folder, it should create a new one with a default user profile.

Tell me how it goes... Theres 2 other alternate ways to deal with that.

---

### Post by new123 on 2011-09-28
> **MAFoElffen said:**
> 
For your Firefox profile issue:

(Back up your ~/.mozilla folder.)  
- Open nautilus, 
- Go to your home folder
- Hit ctrl+h (to show hidden files) 
- Right click on the .mozilla folder
- Select "rename".  
- Rename the folder to .backup-mozilla.  
- Try to start Firefox. 

The above process should start the Firefox applicattion and since it doesn't find a .mozilla folder, it should create a new one with a default user profile.

WoW man nice, it works! Finaly :) Hey thanks alot, so I guess this is solved, Ty again 4 helping me ;)

---

### Post by MAFoElffen on 2011-09-28
> **new123 said:**
> WoW man nice, it works! Finaly :) Hey thanks alot, so I guess this is solved, Ty again 4 helping me ;)
So... I know we threw a lot at you at once, but... As reference to other users with this problem, finding this thread and reading it later down the road... Please explain briefly the "what steps" worked for you.

Then close this thread using the "Thread Tools"  button above and select "solved" from the pulldown menu.

---

### Post by new123 on 2011-09-28
> **MAFoElffen said:**
> So... I know we threw a lot at you at once, but... As reference to other users with this problem, finding this thread and reading it later down the road... Please explain briefly the "what steps" worked for you.

Then close this thread using the "Thread Tools"  button above and select "solved" from the pulldown menu.

Well, 1st thanks any1 who tryed to help.. but these codes are the only ones that helped me, so, if any1 have problem like I described in start...

> **MAFoElffen said:**
> 
```

gconftool-2 --recursive-unset /apps/compiz*

```should have reset anythig in compiz back to defaults.  But there is also 
```

rm -rf .gconf

```which would delete all user changes and start fresh...
If those didn't work, you might try: 
```

compiz --replace

```If none of those work:
```

sudo stop gdm
sudo apt-get update
sudo apt-get remove --purge ubuntu-desktop
sudo apt-get install ubuntu-desktop
sudo apt-get upgrade
sudo startx

```Which would replace all the app's, gnome, compiz, metacity,  xserver, etc...  Of course there is always trying a fresh reinstall and  see if it gets to the same point....  It "was" a fresh install a few  days ago, so he is not losing anything with that.
---------------------------------------------------------
And ofcourse, if theres a problem with Firefox..

> **MAFoElffen said:**
> 
For your Firefox profile issue:

(Back up your ~/.mozilla folder.)  
- Open nautilus, 
- Go to your home folder
- Hit ctrl+h (to show hidden files) 
- Right click on the .mozilla folder
- Select "rename".  
- Rename the folder to .backup-mozilla.  
- Try to start Firefox. 

The above process should start the Firefox applicattion and since it   doesn't find a .mozilla folder, it should create a new one with a   default user profile.



That's all lol, thank u guys :)

---

### Post by smcrossman on 2011-10-03
> **seawolf167 said:**
> See bold text to fix the above command

This likely needs to be a new thread...but in researching I found this and the first command fixes my problem.

I am running 11.04 64 bit. Suddenly whenever I boot up it goes through a  lot of text and stops. I hit alt+F1 login on the tty1 screen just fine.  I've used a lot of apt commands to upgrade, fix, etc., but couldn't get it to load a gui system.  The first command

sudo......restart
loads up the gui and it seems to run fine from there.  I am generally using basic ubuntu, but my laptop I use a lot of kubuntu and have been slowly moving some things from that system onto the desktop so the tools are more consistent.

What have I corrupted or deleted or overriden that I need to repair so it will load appropriately? Any ideas?

---

