---
title: "Cannot access HDDs on PCIe SATA Controller Card Ubuntu 12.04"
date: 2013-01-04
forum: New to Ubuntu
---

### Post by baseballa51 on 2013-01-04
**Software:**
OS: Dual Boot Windows 7 x64 and Ubuntu 12.04 x64 (running smoothly)

**Custom Desktop:**
Mobo: Gigabyte GA-M61PME-S2
CARD: RocketRAID 2640 x1 PCIE 1x 4 port SATA Controller
HDDS: 4x 1tb Seagate Barracuda SATA

**Problem:**
I cannot access my HDDs connected to my SATA controller card. I have run this same setup on either 11.04 or 10.04 (can't remember) and everything worked fine (with native default drivers I believe). This card and all four drives work well in Windows 7 so it shouldn't be a hardware issue unless it is an incompatibility for 12.04 (which I doubt since this card has worked on other versions of ubuntu).
[B]
This is what I have tried so far:[/B]
-search GUI to mount drives (none found)
-list installed hardware in terminal (SATA Controller is there but no HDDs)
-run Disk Utility and scan file system for new hardware (nothing)
-Installed proprietary driver for card and Ubuntu Server 12.04 (to no avail)
-searched forums for hours


I am a somewhat intermediate Linux user and expert hardware and Windows user.

Any input on my situation is greatly appreciated and I thank you in advance.

---

### Post by DuckHook on 2013-01-04
This problem is more suited to the Hardware forum, but hope the moderators don't mind.

Seems to me the critical element is:

> **baseballa51 said:**
> -Installed proprietary driver for card and Ubuntu Server 12.04 (to no avail)

Please provide further details. What driver? Where from? How installed? Install docs for your card are [here]("http://www.highpoint-tech.com/PDF/RR26XX/RR264x_UM_EN_10_110308.pdf") and mention an install CD. What were the names of the Linux drivers on the CD? Does...

```
lsmod
```...show the driver memory-resident or is it missing? If missing, try:

```
locate -b '\name_of_driver'
```substituting the name of your SATA driver for name_of_driver, to see where the install process placed it. Then do:

```
sudo modprobe -r name_of_driver
sudo modprobe name_of_driver
```to unload, then reload driver. Post error output of this last action back to this thread.

---

### Post by baseballa51 on 2013-01-10
Thank you for your response, DuckHook.

After hours upon hours and many failed attempts, I have officially driven myself to the point of insanity attempting to install this driver.  I would like to make a correction to my previous post and change my linux user status to a beginner.
[B]
Here is the driver I downloaded:[/B] [www.highpoint-tech.com/BIOS_Driver/rr26xx/2640X1-2640X4-2642/Linux/v1.5.12.0822/Ubuntu/rr26xx-ubuntu-11.10-x86_64-v1.5.12.0720.tgz](www.highpoint-tech.com/BIOS_Driver/rr26xx/2640X1-2640X4-2642/Linux/v1.5.12.0822/Ubuntu/rr26xx-ubuntu-11.10-x86_64-v1.5.12.0720.tgz)

this is the latest driver I've found on the website (11.10) so I may have to perform some sort of kernel upgrade? (so I have read on outdated drivers)

**I followed the installation instructions here:**
[www.highpoint-tech.com/BIOS_Driver/rr26xx/2640X1-2640X4-2642/Linux/v1.5.12.0822/Installation_Guide/Install_Ubuntu_RR2640_2642.pdf](www.highpoint-tech.com/BIOS_Driver/rr26xx/2640X1-2640X4-2642/Linux/v1.5.12.0822/Installation_Guide/Install_Ubuntu_RR2640_2642.pdf)

I cannot get the install.sh file to execute either by 'run' or 'run in terminal' until I open my file manager (sudo nautilus) in super user mode. Then I can 'run' the file and terminal response is as follows:
[B]
Please reboot the system to use the new driver module.[/B]

After restart I see that no drives appear anywhere I have looked.

I 'run in terminal' the same install.sh file and terminal responds as follows:

[B]
(gnome-terminal:10692): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:994:22: Not a valid image

(gnome-terminal:10692): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1001:22: Not a valid image

(gnome-terminal:10692): Gtk-WARNING **: Theme parsing error: nautilus.css:10:20: Not using units is deprecated. Assuming 'px'.

(gnome-terminal:10692): Gtk-WARNING **: Theme parsing error: nautilus.css:18:20: Not using units is deprecated. Assuming 'px'.

(gnome-terminal:10692): Gtk-WARNING **: Theme parsing error: nautilus.css:28:20: Not using units is deprecated. Assuming 'px'.

(gnome-terminal:10692): Gtk-WARNING **: Theme parsing error: nautilus.css:31:0: 'sideb' is not a valid property name
The value "(no value set)" of configuration key /apps/gnome-terminal/keybindings/new_profile is not a valid accelerator
The value "(no value set)" of configuration key /apps/gnome-terminal/keybindings/toggle_menubar is not a valid accelerator
The value "(no value set)" of configuration key /apps/gnome-terminal/keybindings/reset is not a valid accelerator
The value "(no value set)" of configuration key /apps/gnome-terminal/keybindings/reset_and_clear is not a valid accelerator
The value "(no value set)" of configuration key /apps/gnome-terminal/keybindings/detach_tab is not a valid accelerator
The value "(no value set)" of configuration key /apps/gnome-terminal/keybindings/switch_to_tab_11 is not a valid accelerator
The value "(no value set)" of configuration key /apps/gnome-terminal/keybindings/switch_to_tab_12 is not a valid accelerator[/B]


As per your advice I ran **lsmod** but based on the print response I am unsure what to look for:

[B]Module                  Size  Used by
snd_hda_codec_realtek   224173  1 
ppdev                  17113  0 
ip6t_LOG               16974  4 
bnep                   18281  2 
rfcomm                 47604  0 
xt_hl                  12521  6 
bluetooth             180153  10 bnep,rfcomm
ip6t_rt                12558  3 
nf_conntrack_ipv6      13906  7 
nf_defrag_ipv6         13412  1 nf_conntrack_ipv6
snd_emu10k1_synth      17293  0 
snd_emux_synth         42825  1 snd_emu10k1_synth
snd_seq_virmidi        13525  1 snd_emux_synth
snd_seq_midi_emul      17854  1 snd_emux_synth
binfmt_misc            17540  1 
ipt_REJECT             12576  1 
ipt_LOG                12919  5 
snd_emu10k1           157352  5 snd_emu10k1_synth
xt_limit               12711  12 
xt_tcpudp              12603  18 
xt_addrtype            12713  4 
xt_state               12578  14 
snd_ac97_codec        134869  1 snd_emu10k1
snd_hda_intel          33773  3 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
ac97_bus               12730  1 snd_ac97_codec
edac_core              53746  0 
snd_seq_midi           13324  0 
edac_mce_amd           23709  0 
ip6table_filter        12815  1 
dm_multipath           23275  0 
snd_pcm                97275  5 snd_emu10k1,snd_hda_intel,snd_hda_codec,snd_ac97_codec
ip6_tables             27864  3 ip6t_LOG,ip6t_rt,ip6table_filter
k8temp                 13057  0 
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nf_nat_ftp             12704  0 
nf_nat                 25891  1 nf_nat_ftp
nf_conntrack_ipv4      19716  9 nf_nat
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
nf_conntrack_ftp       13452  1 nf_nat_ftp
nf_conntrack           81926  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12810  1 
serio_raw              13211  0 
ip_tables              27473  1 iptable_filter
x_tables               29891  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd_rawmidi            30748  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
emu10k1_gp             12650  0 
snd_util_mem           14117  2 snd_emux_synth,snd_emu10k1
gameport               19693  2 emu10k1_gp
snd_hwdep              17764  3 snd_emux_synth,snd_emu10k1,snd_hda_codec
parport_pc             32866  1 
snd_seq_midi_event     14899  2 snd_seq_virmidi,snd_seq_midi
snd_seq                61929  5 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_midi_event
snd_timer              29990  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         14540  5 snd_emu10k1_synth,snd_emu10k1,snd_seq_midi,snd_rawmidi,snd_seq
snd                    79041  26 snd_hda_codec_realtek,snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_hda_intel,snd_hda_codec,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_hwdep,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  3 snd_emu10k1,snd_hda_intel,snd_pcm
mac_hid                13253  0 
i2c_nforce2            13058  0 
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
usb_storage            49198  0 
uas                    18180  0 
dm_raid45              78155  0 
xor                    12894  1 dm_raid45
dm_mirror              22203  0 
dm_region_hash         20961  1 dm_mirror
dm_log                 18564  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 653005  0 
zlib_deflate           27139  1 btrfs
libcrc32c              12644  1 btrfs
nouveau               775039  3 
usbhid                 47238  0 
hid                    99636  1 usbhid
ttm                    76949  1 nouveau
drm_kms_helper         46978  1 nouveau
firewire_ohci          41000  0 
drm                   241971  5 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13423  1 nouveau
mxm_wmi                13021  1 nouveau
wmi                    19256  1 mxm_wmi
firewire_core          63600  1 firewire_ohci
floppy                 70207  0 
crc_itu_t              12707  1 firewire_core
video                  19596  1 nouveau
forcedeth              63460  0 
sata_nv                32286  4 
pata_amd               14118  0 
zram                   18642  1 [/B]


The last part of your reply is as follows:

locate -b '\install.sh'
[B]/home/beast/install.sh
/home/beast/.local/share/Trash/files/install.sh
/usr/share/doc/toshset/toshiba-acpi/2.6.26/install.sh
/usr/share/doc/toshset/toshiba-acpi/2.6.28/install.sh
/usr/src/linux-headers-3.2.0-32/arch/arm/boot/install.sh
/usr/src/linux-headers-3.2.0-32/arch/blackfin/boot/install.sh
/usr/src/linux-headers-3.2.0-32/arch/ia64/install.sh
/usr/src/linux-headers-3.2.0-32/arch/m32r/boot/compressed/install.sh
/usr/src/linux-headers-3.2.0-32/arch/m68k/install.sh
/usr/src/linux-headers-3.2.0-32/arch/mn10300/boot/install.sh
/usr/src/linux-headers-3.2.0-32/arch/parisc/install.sh
/usr/src/linux-headers-3.2.0-32/arch/powerpc/boot/install.sh
/usr/src/linux-headers-3.2.0-32/arch/s390/boot/install.sh
/usr/src/linux-headers-3.2.0-32/arch/sh/boot/compressed/install.sh
/usr/src/linux-headers-3.2.0-32/arch/x86/boot/install.sh
/usr/src/linux-headers-3.2.0-35/arch/arm/boot/install.sh
/usr/src/linux-headers-3.2.0-35/arch/blackfin/boot/install.sh
/usr/src/linux-headers-3.2.0-35/arch/ia64/install.sh
/usr/src/linux-headers-3.2.0-35/arch/m32r/boot/compressed/install.sh
/usr/src/linux-headers-3.2.0-35/arch/m68k/install.sh
/usr/src/linux-headers-3.2.0-35/arch/mn10300/boot/install.sh
/usr/src/linux-headers-3.2.0-35/arch/parisc/install.sh
/usr/src/linux-headers-3.2.0-35/arch/powerpc/boot/install.sh
/usr/src/linux-headers-3.2.0-35/arch/s390/boot/install.sh
/usr/src/linux-headers-3.2.0-35/arch/sh/boot/compressed/install.sh
/usr/src/linux-headers-3.2.0-35/arch/x86/boot/install.sh[/B]


sudo modprobe -r install.sh
**FATAL: Module install.sh not found.**
sudo modprobe install.sh
**FATAL: Module install.sh not found.**



Additionally, I have gone through numerous install guides/tutorials/videos for installing a .tgz file and none seem to allow the installation of this driver.

My Apologies for the lengthy reply but it's probably necessary.

Thank you again for devoting your time to assist me.

---

### Post by DuckHook on 2013-01-10
The lengthy reply is not only complete, but essential. You deserve kudos for trying to work things out yourself.

install.sh is not a program but a shell script (like the old DOS "batch" files--if you go back that far--but much more powerful). The name of your driver is actually something else, which your documentation doesn't name. You can find the name within the shell script by opening it up in an editor instead of trying to run it. No other way except this sort of detective work, I'm afraid. BTW, "drivers" are called "modules" in Linux, hence, *lsmod* (list modules) or *modprobe* (module probe--"probe" is geek-speak for pushing something into resident memory, in this case, a module). The gist of it is: you won't find anything useful by trying to *locate* install.sh, nor will you find a module called install.sh by using *lsmod* because install.sh is just a script being called upon to perform a series of modifications to your system that result in the real module being made part of your boot-loading process. If doing detective work, the module's name may actually be something like "rr264x" or similar (though it could be something much different as well).

I would recommend that you try installing the driver again, but this time, not relying on the graphical tools like *nautilus*. Instead, follow the steps in the guide with some modifications:

1. Open a terminal either from your menu or using <Ctrl>+<Alt>+<t>
2. Follow the instructions by typing:
```
sudo mkdir /tmp/dd
sudo tar xzvf [path_to_driver]/rr26xx-ubuntu-x-x.tgz -C /tmp/dd
cd /tmp/dd
sudo sh install.sh
```

where [path_to_driver] is the path to the directory where you have copied/downloaded your driver. Also, running a shell script uses the *sh* command as per the last line of the instructions. Because you are monkeying around with processes and directories that require root privileges, you must preface most of your commands with *sudo* (*cd* is the exception).

If this still doesn't work, post back the error output to this thread again. Please wrap your output in [CODE]output[\CODE] markers (where "\" is replaced with "/") for easier readability.

Last but not least, if you can't get to this problem within the next 24 hours, please post back to this thread with a short heads-up alerting to this. I usually delete thread subscriptions with no activity after 2 or 3 days, and it was lucky that I hadn't done so with yours.

---

### Post by baseballa51 on 2013-01-11
I will not be able to play around with this until tomorrow night or some time Saturday. Work is fairly demanding. 

Thank you again and I'm fortunate you did not remove this from your list of active threads.

Good evening.):P

---

### Post by baseballa51 on 2013-01-12
I feel I'm getting closet but still not quite there.
(and not exactly sure about format of output code you requested) but here goes:



Something else to keep in mind is that this module package was for Ubuntu 11.10 and is the latest available through the manufacturer’s website. I have read of some kernel update or something of the sort.


========================================================================
**sudo mkdir /tmp/dd**
**[**[sudo] password for beast:**]**

**sudo tar xzvf /home/beast/rr/rr26xx.tgz -C /tmp/dd**
**[**boot/
boot/rr26xx3.0.0-12-genericx86_64.ko.gz
boot/rr26xx3.0.0-12-serverx86_64.ko.gz
install.sh
postinst2.sh
postinst.sh
preinst.sh
readme.txt**]**

**sudo sh install.sh**
**[**sh: 0: Can't open install.sh**]**

=========================================================================

Then I changed directories to the home folder where I have the module package and extracted contents and tried the same commands:

=========================================================================
**sudo tar xzvf /home/beast/rr/rr26xx.tgz -C /home/beast/rr**
**[**[sudo] password for beast:**]**
**[**boot/
boot/rr26xx3.0.0-12-genericx86_64.ko.gz
boot/rr26xx3.0.0-12-serverx86_64.ko.gz
install.sh
postinst2.sh
postinst.sh
preinst.sh
readme.txt[B]]

sudo sh install.sh[/B]
**[**Please reboot the system to use the new driver module.[B]]

[/B]=========================================================================After that I noticed the files in the rr folder (where I extracted all the files) have a red X on them. I rebooted the system and still nothing to see of my drives.

=========================================================================

I noticed that when I view the information in the install.sh file the driver/module name was simply 'rr26xx' instead of 'rr26xx3.0.0-12-genericx86_64.ko.gz' which is the driver/module file I am attempting to install; however, the directory which the files extract to is named 'rr26xx', not the file name itself. I deleted and re-extracted the file contents and opened the install.sh file again and changed the 'rr26xx' to 'rr26xx3.0.0-12-genericx86_64.ko.gz', saved, and tried again in terminal:
 
=========================================================================


 **sudo sh install.sh**
 **[**[sudo] password for beast:
 Please reboot the system to use the new driver module.**]**
  

 

 After reboot nothing to be found.
 
========================================================================

**sudo modprobe -r rr26xx3.0.0-12-genericx86_64.ko.gz ** 
 **[**[sudo] password for beast:  
 FATAL: Module rr26xx3.0.0_12_genericx86_64.ko.gz not found. **]**
 

 **rr26xx3.0.0-12-genericx86_64.ko.gz**  
 **[**FATAL: Module rr26xx3.0.0_12_genericx86_64.ko.gz not found. **]**

 =========================================================================

Here are a few other commands I've tried with no success:
 

 **./configure**
 [bash: ./configure: No such file or directory]
 

 **make**
 [make: *** No targets specified and no makefile found.  Stop.]
 

 =========================================================


After getting pretty fed up with the terminal I installed HardInfo (program that detects hardware on a system) and it came up with the card and it's attributes.
Keep in mind, no driver modules have been installed yet though it knows the card is installed and has all the information about it. 


***SEE ATTACHMENT "HardInfo" SCREENSHOT***



Is there somewhere I can navigate to or a command I can type in terminal to activate it or allow drives attached to it to be seen through Nautilus?


After tonight I think I'm about 12-13 hours in. I wonder why I didnt have to go through any of this before on previous versions of Ubuntu. Is it crazy to think Ubuntu would remove support of a device like this for this current version?


Thank you for your help.

---

### Post by baseballa51 on 2013-01-12
I went searching for some other commands in terminal which would show me some more information about the hardware in my system and this is what I came up with:


**lshw**
.....................
.....................
    [*-scsi UNCLAIMED
             description: SCSI storage controller
             product: RocketRAID 2640 SAS/SATA Controller
             vendor: HighPoint Technologies, Inc.
             physical id: 0
             bus info: pci@0000:02:00.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: scsi pm msi pciexpress bus_master cap_list
             configuration: latency=0
             resources: ioport:b000(size=128) memory:fa000000-fa000fff memory:fc000000-fc03ffff
.................
.................
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@4:0.0.1
             logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@4:0.0.2
             logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@4:0.0.3
             logical name: /dev/sde]..............


The card is there, seems to be supported fresh out of installation, and disks are there.

I see "unclaimed" which means to me that it is perhaps disabled?

Is there a way to ENABLE it?

There is an abundance of information on how to disable hardware in ubuntu but I find none on enabling it (unless it's a wireless adapter). After reading through numerous forums it appears to be something users wish ubuntu had natively -- some tool for enabling/disabling hardware easily.

Can I enable this device?

---

### Post by DuckHook on 2013-01-12
I've split my reply into two parts--a general explanation and further steps. If not interested, skip general explanation and go straight to further steps.

General Explanation:

Support for old or obscure hardware is often dropped in Linux. These forums are filled with people who need help because they have a device no longer supported in the latest kernel without special measures. The reason for this is actually a good one, but it doesn't help people who are in a fix like you. You see, unlike Windows, Linux supports most hardware in the kernel itself. The advantages of this are:

1. Seamless installation (for supported hardware). Install a new video/sound/network card and it just works. No need to install another driver to get it working.
2. OS portability. I have a number of Ubuntu installs on various media like USB sticks and USB drives. Even though these installs were made on a very specific machine, I can easily plug any of these USB sticks/drives into a different machine, from laptops to desktops to servers, all with completely different hardware, and 9 times out of 10, they will boot up with no fuss or bother. Other OSes can't do that. They are very system specific and swapping a HD into a different machine will usually result in kernel panic or simply refusal to boot.

The downside of this philosophy is kernel bloat. The kernel tends to get too big and cumbersome trying to support all those devices. So the developers must aggressively prune as they add new hardware support. Result: orphaned hardware like yours. Well, actually, this isn't quite accurate or fair. The result is that you now have to load your own modules, but since Windows forces you to load device drivers for everything from the get go, having to do so in Linux isn't really any different. The process is just more obscure.

Further Steps:

This is what is happening. I'll try to be more specific this time:

1. The file: *rr26xx3.0.0-12-genericx86_64.ko.gz* is not your module either. It is yet another compressed file that must be decompressed for the install process to succeed. The *.gz* suffix stands for *gnu zip*, which is the open source equivalent of the well-known Windows compression *zip *format.

2. The install script *install.sh* should automatically extract the contents of the *.gz* file into a directory that it creates in your modules library. The resulting file will be: *rr26xx3.0.0-12-genericx86_64.ko*

3. This file will likely be placed into a system library (without seeing your install script, it's only educated guesswork). However, the actual directory that this module will be copied to is very obscure. Directory structures get very complicated in the guts of the Linux operating system.

4. the *.ko* suffix in your file stands for *kernel object*. This means that the kernel is supposed to load this object into its operating space at boot time so that it functions as a part of the kernel. If you refer to the general explanation above, this has the effect of appending this module's functionality back into the kernel, just as if this functionality was still built in.

5. Once properly loaded, your module will show up in *lsmod* as *rr26xx*, or something similarly brief. Even though the *.ko* file is called *rr26xx3.0.0-12-genericx86_64.ko* no module developer labels the actual running module process with all of the version info. When the module is loaded, it is almost always stripped of the extraneous info to leave a name that is short and sweet. **This difference is important:** the kernel object file is the long-winded *rr26xx3.0.0-12-genericx86_64.ko* but the running module itself will likely be something much shorter--a good guess would be *rr26xx* or even just *rr26*. Therefore, when we succeed in getting it loaded, don't go looking for a long-winded name in *lsmod*.

6. In your case, the install script ran properly the second time around. It created a directory somewhere (we don't know where), extracted the file, tried to set up your boot scripts to load the module every time you booted, and then exited after thinking that it had behaved like a good little script. So, in all likelihood, a file now exists in your vast library tree named: [I]rr26xx3.0.0-12-genericx86_64.ko
[/I]
7. Let's look for it. Do

```
locate rr26xx3.0.0-12-genericx86_64.ko
```we are looking for something in /lib/modules/[some_kernel_version]/kernel/drivers/.../rr26xx3.0.0-12-genericx86_64.ko

remember, the predicted path is just an educated guess. The install script could have placed it anywhere. The confusion is compounded by the fact that Linux changes its directory structure with some releases. Post this output back to this thread.

8. I suspect that your install script placed the module in the wrong library, likely belonging to an older version of your kernel. To see what version of the kernel you are currently running, do:

```
uname -a
```we want to compare this output with the [some_kernel_version] output in step 7 above. Post this output back to this thread.

9. It is also possible that the install script tried to change the wrong startup files. If the script was written for an old version of Ubuntu, the startup files will have changed.

You are very close to solving this problem so take heart. It's a long-winded process I've just laid out, but follow it step by step and you should be that much closer to making this card work.

---

### Post by DuckHook on 2013-01-12
> **baseballa51 said:**
> ...Can I enable this device?

You enable it by successfully installing its driver module.

---

### Post by baseballa51 on 2013-01-13
How do you know the install script ran successfully?
[B]

Here is a copy of the install.sh file:[/B]

#!/bin/sh
# Post installation for debian 3.1 installation

# THis is the module name. Should be valid.
HPTMOD=rr26xx

#
# Do NOT edit the following in most cases
#
ININITRD=0

if test "${HPTMOD}set" = "set" ; then
    echo "Error! Which module to install?";
    exit 1;
fi

if [ ! -d /lib/modules/ ]; then
    echo "Error! Can not find any system module installation directory!";
    exit 1;
fi

RELEASES=$( ls /lib/modules/ )

if test "${RELEASES}"set = "set" ; then
    echo "Error! No kernel package has been installed!";
    exit 1;
fi

if [ "`/bin/uname -m`" = "x86_64" ];then
    ARCH=x86_64
else
    ARCH=i386
fi

VERSION=$( ls /lib/modules/ | cut -c1-3 | uniq )
if which mkinitramfs >/dev/null 2>/dev/null ; then
    mkinitrd=mkinitramfs
else
    mkinitrd=mkinitrd
fi


if ( grep "^$HPTMOD" -s -q /etc/${mkinitrd}/modules ); then # debian 3.1, ubuntu 5.10 (6.x? 7.x?)
    ININITRD=1
elif ( grep "^MODULES=most" -s -q /etc/initramfs-tools/initramfs.conf ); then # debian 4.0
    ININITRD=1
    echo "ROOTDELAY=180" >> /etc/initramfs-tools/initramfs.conf
elif ( grep "^$HPTMOD" -s -q /etc/initramfs-tools/modules ) ; then # debian 4.0
    ININITRD=1
else
    echo "No initrd config file found, will not rebuild initrd image."
fi

for RELEASE in ${RELEASES}; do
    if [ -f boot/${HPTMOD}${RELEASE}${ARCH}.ko.gz -a -d /lib/modules/${RELEASE}/kernel ] ; then
        if test $HPTMOD = "hptmv" || test $HPTMOD = "hptmv6" || test $HPTMOD = "rr174x" || test $HPTMOD = "rr2310_00"; then
            find /lib/modules/${RELEASE} -name 'sata_mv.*' -delete
        fi
        if test $HPTMOD = "rr272x_1x" || test $HPTMOD = "rr274x_3x" ||  test $HPTMOD = "rr276x" || test $HPTMOD = "rr278x" ; then
            find /lib/modules/${RELEASE} -name 'mvsas.*' -delete
        fi
        if test $HPTMOD = "hptiop"; then
            find /lib/modules/${RELEASE} -name 'hptiop.*' -delete
        fi
        if test $HPTMOD = "hpt374" || test $HPTMOD = "hpt37x2"; then
            find /lib/modules/${RELEASE} -name 'pata_hpt3*.ko' -delete
            find /lib/modules/${RELEASE} -name 'hpt366.ko' -delete
        fi
        gzip -dc boot/$HPTMOD${RELEASE}${ARCH}.ko.gz > /lib/modules/${RELEASE}/kernel/drivers/scsi/${HPTMOD}.ko    
        depmod -a ${RELEASE}
        if test $ININITRD = "1" ; then
            echo "Update initrd file /boot/initrd.img-${RELEASE} for ${RELEASE}"
            mv /boot/initrd.img-${RELEASE} /boot/initrd.img-${RELEASE}.bak
            ${mkinitrd} -o /boot/initrd.img-${RELEASE} ${RELEASE}
        fi
    fi
done


if test $ININITRD = "1" ; then
    # in case driver not in initrd and udev not load the driver module
    if [ ! -f /etc/modules ] || ( ! grep "^$HPTMOD" /etc/modules -s -q ); then
        echo $HPTMOD >> /etc/modules
        echo sd_mod >> /etc/modules
    fi
    echo "Please reboot the system to use the new driver module."
    exit 0
elif [ ! -f /etc/modules ] || ( ! grep "^$HPTMOD" /etc/modules -s -q ); then
    echo $HPTMOD >> /etc/modules
    echo sd_mod >> /etc/modules
    if test $HPTMOD = "hptmv" || test $HPTMOD = "hptmv6" || test $HPTMOD = "rr174x" || test $HPTMOD = "rr2310_00" ; then
        if ( lsmod | grep sata_mv -s -q ); then
            echo "Unloading conflicting module sata_mv..."
            rmmod sata_mv
            if ( lsmod | grep sata_mv -s -q ) ; then
                echo "Failed to unload module sata_mv, it may be in use, please reboot the system."
                exit 0
            fi
        fi
    elif test $HPTMOD = "hpt374" || test $HPTMOD = "hpt37x2"; then
        if ( lsmod | grep hpt366 -s -q ); then
            echo "Unloading conflicting module hpt366..."
            rmmod hpt366
            if ( lsmod | grep hpt366 -s -q ) ; then
                echo "Failed to unload module hpt366, it may be in use, please reboot the system."
                exit 0
            fi
        fi
        if ( lsmod | grep pata_hpt37x -s -q ); then
            echo "Unloading conflicting module pata_hpt37x..."
            rmmod pata_hpt37x
            if ( lsmod | grep pata_hpt37x -s -q ) ; then
                echo "Failed to unload module pata_hpt37x, it may be in use, please reboot the system."
                exit 0
            fi
        fi
    elif test $HPTMOD = "hptiop" ; then
        if ( lsmod | grep hptiop -s -q ); then
            echo "Unloading previous loading module hptiop..."
            rmmod hptiop
            if ( lsmod | grep hptiop -s -q ) ; then
                echo "Failed to unload module hptiop, it may be in use, please reboot the system."
                exit 0
            fi
        fi
    elif test $HPTMOD = "rr272x_1x" || test $HPTMOD = "rr274x_3x" || test $HPTMOD = "rr276x" || test $HPTMOD = "rr278x" ; then
        if ( lsmod | grep mvsas -s -q ); then
            echo "Unloading previous loading module mvsas..."
            rmmod mvsas
            if ( lsmod | grep mvsas -s -q ) ; then
                echo "Failed to unload module mvsas, it may be in use, please reboot the system."
                exit 0
            fi
        fi
    fi
    echo "Loading $product driver module $HPTMOD."
    modprobe $HPTMOD
    modprobe sd_mod
    exit 0
fi==========================================================================[B]


locate rr26xx3.0.0-12-genericx86_64.ko[/B]
[Desktop/    Downloads/  Pictures/  rr26xx/                                      Templates/
Documents/  Music/      Public/    rr26xx-ubuntu-11.10-x86_64-v1.5.12.0720.tgz  Videos/]
=========================================================================
Then I changed directories to the folder where it is located and ran the same command again:

**beast@beast-M61PME-S2:~/rr26xx$ sudo locate rr26xx3.0.0-12-genericx86_64.ko**
[/root/.local/share/Trash/files/rocketraid/boot/rr26xx3.0.0-12-genericx86_64.ko.gz]

=========================================================================
I looked through the majority of folders in /lib for the .ko file and couldn't find it.
=========================================================================

**uname -a**
[Linux beast-M61PME-S2 3.2.0-35-generic #55-Ubuntu SMP Wed Dec 5 17:42:16 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux]

========================================================================

I will try to devote some time tomorrow on this. Thank you.

---

### Post by DuckHook on 2013-01-13
@baseballa51

Can't look into it now. Have family over tonight so will look into it after they leave. Apologies for delay.

---

### Post by baseballa51 on 2013-01-14
well after about 22 hours and half my sanity gone it's finally installed.

I found this thread:  [http://www.flynsarmy.com/2012/11/installing-rocketraid-2760a-drivers-on-ubuntu-12-10/](http://www.flynsarmy.com/2012/11/installing-rocketraid-2760a-drivers-on-ubuntu-12-10/)

and it was the money-maker!!

I had to change some things around since this was for a different card but when I was complete my terminal looked like this:

=================================================================

  	 	 	 	 	 	   user@computer:~$ mkdir ~/driver  
  Desktop/    Downloads/  examples.desktop  Pictures/  rr2/     Templates/  
 Documents/  driver/     Music/            Public/    rr26xx/  Videos/  
 user@computer:~$ cd ~/driver  
 user@computer:~/driver$ wget [http://www.highpoint-tech.com/BIOS_D....5.12.0720.tgz](http://www.highpoint-tech.com/BIOS_D....5.12.0720.tgz)  
 --2013-01-14 00:44:14--  [http://www.highpoint-tech.com/BIOS_D....5.12.0720.tgz](http://www.highpoint-tech.com/BIOS_D....5.12.0720.tgz)  
 Resolving [www.highpoint-tech.com](www.highpoint-tech.com) ([www.highpoint-tech.com](www.highpoint-tech.com))... 205.134.255.100  
 Connecting to [www.highpoint-tech.com](www.highpoint-tech.com) ([www.highpoint-tech.com)|205.134.255.100|:80](www.highpoint-tech.com)|205.134.255.100|:80)... connected.  
 HTTP request sent, awaiting response... 404 Not Found  
 2013-01-14 00:44:15 ERROR 404: Not Found.  
 

 user@computer:~/driver$ tar -xzvf rr26xx.tgz  
 boot/  
 boot/rr26xx3.0.0-12-genericx86_64.ko.gz 
 boot/rr26xx3.0.0-12-serverx86_64.ko.gz  
 install.sh  
 postinst2.sh  
 postinst.sh  
 preinst.sh  
 readme.txt  
 stubs@beast:~/driver$ mkdir module  
 stubs@beast:~/driver$ cd module  
 stubs@beast:~/driver/module$ tar -xzvf rr264x-linux-src-v1.4-120524-1520.tar.gz  
 rr264x-linux-src-v1.4/  
 rr264x-linux-src-v1.4/inc/  
 rr264x-linux-src-v1.4/inc/array.h  
 rr264x-linux-src-v1.4/inc/him.h  
 rr264x-linux-src-v1.4/inc/himfuncs.h  
 rr264x-linux-src-v1.4/inc/hptintf.h  
 rr264x-linux-src-v1.4/inc/ldm.h  
 rr264x-linux-src-v1.4/inc/linux/  
 rr264x-linux-src-v1.4/inc/linux/Makefile.def 
 rr264x-linux-src-v1.4/inc/linux/osm.h  
 rr264x-linux-src-v1.4/inc/list.h  
 rr264x-linux-src-v1.4/lib/  
 rr264x-linux-src-v1.4/lib/linux/  
 rr264x-linux-src-v1.4/lib/linux/free-i686-regparm0/ 
 rr264x-linux-src-v1.4/lib/linux/free-i686-regparm0/him_odin.o 
 rr264x-linux-src-v1.4/lib/linux/free-i686-regparm0/jbod.o 
 rr264x-linux-src-v1.4/lib/linux/free-i686-regparm0/ldm_raid.o 
 rr264x-linux-src-v1.4/lib/linux/free-i686-regparm0/partition.o 
 rr264x-linux-src-v1.4/lib/linux/free-i686-regparm0/raid0.o 
 rr264x-linux-src-v1.4/lib/linux/free-i686-regparm0/raid1.o 
 rr264x-linux-src-v1.4/lib/linux/free-i686-regparm0/raid5.o 
 rr264x-linux-src-v1.4/lib/linux/free-i686-regparm3/ 
 rr264x-linux-src-v1.4/lib/linux/free-i686-regparm3/him_odin.o 
 rr264x-linux-src-v1.4/lib/linux/free-i686-regparm3/jbod.o 
 rr264x-linux-src-v1.4/lib/linux/free-i686-regparm3/ldm_raid.o 
 rr264x-linux-src-v1.4/lib/linux/free-i686-regparm3/partition.o 
 rr264x-linux-src-v1.4/lib/linux/free-i686-regparm3/raid0.o 
 rr264x-linux-src-v1.4/lib/linux/free-i686-regparm3/raid1.o 
 rr264x-linux-src-v1.4/lib/linux/free-i686-regparm3/raid5.o 
 rr264x-linux-src-v1.4/lib/linux/free-x86_64-regparm0/ 
 rr264x-linux-src-v1.4/lib/linux/free-x86_64-regparm0/him_odin.o 
 rr264x-linux-src-v1.4/lib/linux/free-x86_64-regparm0/jbod.o 
 rr264x-linux-src-v1.4/lib/linux/free-x86_64-regparm0/ldm_raid.o 
 rr264x-linux-src-v1.4/lib/linux/free-x86_64-regparm0/partition.o 
 rr264x-linux-src-v1.4/lib/linux/free-x86_64-regparm0/raid0.o 
 rr264x-linux-src-v1.4/lib/linux/free-x86_64-regparm0/raid1.o 
 rr264x-linux-src-v1.4/lib/linux/free-x86_64-regparm0/raid5.o 
 rr264x-linux-src-v1.4/lib/linux/free-x86_64-regparm3/ 
 rr264x-linux-src-v1.4/lib/linux/free-x86_64-regparm3/him_odin.o 
 rr264x-linux-src-v1.4/lib/linux/free-x86_64-regparm3/jbod.o 
 rr264x-linux-src-v1.4/lib/linux/free-x86_64-regparm3/ldm_raid.o 
 rr264x-linux-src-v1.4/lib/linux/free-x86_64-regparm3/partition.o 
 rr264x-linux-src-v1.4/lib/linux/free-x86_64-regparm3/raid0.o 
 rr264x-linux-src-v1.4/lib/linux/free-x86_64-regparm3/raid1.o 
 rr264x-linux-src-v1.4/lib/linux/free-x86_64-regparm3/raid5.o 
 rr264x-linux-src-v1.4/osm/  
 rr264x-linux-src-v1.4/osm/linux/  
 rr264x-linux-src-v1.4/osm/linux/div64.c 
 rr264x-linux-src-v1.4/osm/linux/hptinfo.c 
 rr264x-linux-src-v1.4/osm/linux/install.sh 
 rr264x-linux-src-v1.4/osm/linux/osm_linux.c 
 rr264x-linux-src-v1.4/osm/linux/osm_linux.h 
 rr264x-linux-src-v1.4/osm/linux/os_linux.c 
 rr264x-linux-src-v1.4/osm/linux/patch.sh 
 rr264x-linux-src-v1.4/product/  
 rr264x-linux-src-v1.4/product/rr2640/  
 rr264x-linux-src-v1.4/product/rr2640/linux/ 
 rr264x-linux-src-v1.4/product/rr2640/linux/config.c 
 rr264x-linux-src-v1.4/product/rr2640/linux/Makefile 
 rr264x-linux-src-v1.4/README  
 user@computer:~/driver/module$ cd rr264x-linux-src-v1.4/product/rr2640/linux/  
 user@computer:~/driver/module/rr264x-linux-src-v1.4/product/rr2640/linux$ make  
 make[1]: Entering directory `/usr/src/linux-headers-3.2.0-35-generic'  
   CC [M]  /home/stubs/driver/module/rr264x-linux-src-v1.4/product/rr2640/linux/.build/os_linux.o 
   CC [M]  /home/stubs/driver/module/rr264x-linux-src-v1.4/product/rr2640/linux/.build/osm_linux.o 
   CC [M]  /home/stubs/driver/module/rr264x-linux-src-v1.4/product/rr2640/linux/.build/div64.o 
   CC [M]  /home/stubs/driver/module/rr264x-linux-src-v1.4/product/rr2640/linux/.build/hptinfo.o 
   CC [M]  /home/stubs/driver/module/rr264x-linux-src-v1.4/product/rr2640/linux/.build/config.o 
   LD [M]  /home/stubs/driver/module/rr264x-linux-src-v1.4/product/rr2640/linux/.build/rr26xx.o 
   Building modules, stage 2.  
   MODPOST 1 modules  
 WARNING: could not find /home/stubs/driver/module/rr264x-linux-src-v1.4/product/rr2640/linux/.build/.him_odin.o.cmd for /home/stubs/driver/module/rr264x-linux-src-v1.4/product/rr2640/linux/.build/him_odin.o 
   CC      /home/stubs/driver/module/rr264x-linux-src-v1.4/product/rr2640/linux/.build/rr26xx.mod.o 
   LD [M]  /home/stubs/driver/module/rr264x-linux-src-v1.4/product/rr2640/linux/.build/rr26xx.ko 
 make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-35-generic'  
 user@computer:~/driver/module/rr264x-linux-src-v1.4/product/rr2640/linux$ gzip rr26xx.ko  
 user@computer:~/driver/module/rr264x-linux-src-v1.4/product/rr2640/linux$ mv rr26xx.ko.gz ~/driver/boot/rr26xx$(uname -r)$(uname -m).ko.gz  
 user@computer:~/driver/module/rr264x-linux-src-v1.4/product/rr2640/linux$ cd ~/driver  
 user@computer:~/driver$ sudo bash preinst.sh  
 [sudo] password for stubs:  
 This step succeeded! Now you can press ALT+F7 to switch back to the installation screen!  
 user@computer:~/driver$ sudo bash install.sh  
 Update initrd file /boot/initrd.img-3.2.0-35-generic for 3.2.0-35-generic  
 Please reboot the system to use the new driver module.  
 user@computer:~/driver$ 



=====================================================================


Since it was for a different card I just visited highpoint-technologies.com and downloaded the .tgz files directly into the directories I created as I was moving along in terminal instead of the wget command. either will work.


I hope this information helps -- it appears there are many users seeking information on RocketRAID cards.


Good luck to those who are in need and remember that PERSISTENCE PAYS OFF!   ):P


P.S. Thank you for your help DuckHook; your input on this matter helped me learn terminal better.

  
[]("http://www.flynsarmy.com/2012/11/installing-rocketraid-2760a-drivers-on-ubuntu-12-10/")

---

