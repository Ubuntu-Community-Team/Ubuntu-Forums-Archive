---
title: "&quot;Gave up waiting for root device&quot;"
date: 2013-03-01
forum: New to Ubuntu
---

### Post by TheAdmiralty on 2013-03-01
I'm trying to get an old server to run Kubuntu at the moment, an Acer Altos G510.  Dual Xeon SL6VN processors, booting off of a Fujitsu Limited 73Gb SCSI-Ultra320 15k drive through an onboard LSI controller.

I can't get it to boot without it going into the BusyBox and saying the following:

[B]Gave up waiting for root device.  Common problems:
...
...
ALERT! dev/disk/by-uuid/<string> does not exist.  Dropping to a shell!
[/B]
I see that this has been asked before, but nothing I've found talks about what to do with a SCSI drive, nor can I understand a lot of people saying "go here and add this and it will work".  I'm brand new to Ubuntu and Linux.
I'm trying to install Kubuntu 12.10 using an IDE HDD formatted into a 2GB FAT partition, loaded with PenDriveLinux.  Installation works fine, but it won't boot off of the main SCSI drive.

Any ideas?  I've gotta say, that the curve for getting into Linux is like a brick wall... I have no problem with that myself; I love this stuff, but for the average every-day computer user, it has to be seriously daunting to even get Ubuntu installed.

---

### Post by matt_symes on 2013-03-01
Hi

> **TheAdmiralty said:**
> I'm trying to get an old server to run Kubuntu at the moment, an Acer Altos G510. Dual Xeon SL6VN processors, booting off of a Fujitsu Limited 73Gb SCSI-Ultra320 15k drive through an onboard LSI controller.

<snip>

Any ideas? I've gotta say, that the curve for getting into Linux is like a brick wall...

<snip>

for the average every-day computer user, it has to be seriously daunting to even get Ubuntu installed.

I have to say that i have never met many "average every-day computer users" that try to install Ubuntu on an old server :D

What you are trying to do is not what the average user would do so you must expect some issues.

Also the average user does not generally have these problems.

There may be a problem with the UUIDs but as this is an older server, i suspect something else may be going on.

Reboot your PC and immediately press shift key to display at the grub menu, if it is not already displayed.

 When it displays a kernel to boot, press the 'e' key to edit that kernels command line.

Scroll to the end of the kernel command line.

At the end of the kernel line, hit the space bar and then add this text

```
rootdelay=90
```

Press the two keys 'ctrl' and 'x' at the same to continue booting.

This will increase the time the kernel will wait for your discs to spin up and for the root partition to become ready.

Does this boot into Kubuntu. If it does then this fix needs to be made permenant as it is not at the moment.

If it does not fix it then the issue is something else.

EDIT: I just thought i would add that i think Kubuntu may not be the best option for such and old server.

Kind regards

---

### Post by TheAdmiralty on 2013-03-01
Yep... I certainly expect it.  Maybe even look forward to it... it's never fun to just install an operating system and have it fire right up.  :)

I'll go fire it up and see see how it works.  I have two Seagate Cheetah 10k's alongside what I have now as a boot drive... I might try installing to one of them while I'm at it, just for good measure.  Will be sure to report back with how it goes.

Much appreciated!

---

### Post by matt_symes on 2013-03-01
Hi

Just to let you know that i edited my post so you may want to read it, as i tried to make it clearer.

Kind regards

---

### Post by TheAdmiralty on 2013-03-01
Alright.  First, I went into the LSI controller configuration, and disabled all initial disk spinup delays, and then tried booting with the bootdelay=90 parameter, but it didn't do much; still drops off at the same error.  Definitely not a matter of waiting for the hardware to be ready.

I did reformat and reinstall onto the same hard drive in the same way I installed it the first time, and it ended up stopping and dumping me into the BusyBox shell, but with no error... I'm not really sure if this is progress or not.  It would be nice if it would at least have the same problems, and consistently.

On your other note, I believe that Redhat Linux was officially supported by the G510 at one time, but I'd like something... well... a little nicer to work with and look at.  Kubuntu might not be the 'best' option, but I'm willing to keep trying until I get something to work on this.  It's really just a project/excuse for me to have an absurdly overbuilt desktop humming beside me. ;-)   It might be worth trying to use a base Ubuntu install and replace Unity with KDE of that, but I really don't think it would solve any of my boot issues.

Not every day you find all the hardware needed to turn something into a desktop pc; had to gut an old Gateway for an audio card, and it's running on an ATI Rage 128 right now that can't even play videos over the internet... amazing how hard PCI video cards are getting to find.  Another 2x512Mb of ECC Reg memory in the mail... at least old enterprise class parts are dirt cheap.

---

### Post by matt_symes on 2013-03-01
Hi

Shame about the rootdelay. That would have been a nice easy fix. I must work on my hunches :)

> dumping me into the BusyBox shell, but with no error...

That is progress. what happens when you type exit at that prompt, as there is no error ?

You should be able able to view dmesg in busybox as well and see what the kernel has done. 

Try to find out at what point initramfs dropped you to busybox.

Please keep me posted as i'm off to sleep in a moment and it sounds like a good project.

Kind regards

---

### Post by TheAdmiralty on 2013-03-02
Just learned that it will only do that once, on the first boot immediately after installation.  First boot will always have the graphical splash screen, and drop into BusyBox with no error; anything after that will run in ascii and end with the "Gave up waiting" error.

Trying to exit the BusyBox page results in the BusyBox message being repeated; only way it seems to get out of that page is to use the reboot command.

"dmesg" replies with about ten pages of text, but the most I could make out of it was that it looped on "scsi 2:0:1:1 >CDB / test unit ready: 00 00 00 00 00 00" and then would fail several test and repeat itself.  I can take a picture of the final page if needed... is there a parameter that displays one page at a time?  I know DOS has that option, but I'm still finding my way around Linux's subsystems.

The last four lines are as follows:
[B]sdc: unknown partition table
sd 2:0:1:0 >[sdc] attached scsi disk
sdb: sdb1 sdb2 < sdb5 >
sd 2:0:0:0 >[sdb] attached scsi disk
[/B]Not sure if that's helpful or not, but i figure it's worth putting up.

On a random side note, one of the Cheetah drives is showing up on the LiveOS as being 964MiB, although I'm almost positive this is because of my constantly reformatting things and/or breaking RAID arrays.

Appreciate the help, by the way. :)

---

### Post by matt_symes on 2013-03-02
Hi

A picture of the final page of the dmesg log would be most useful.

**EDIT:**

To display 1 page at a time use the command

```
most
```

so you would be looking at 

```
dmesg | most
```

Use the spacebar to get the next page and q to exit.

I believe most is part of busybox.

You can also get the initramfs log by editing the kernel command line as you did before but adding

```
debug
```

to the end.

I believe the initramfs log is stored in the directory

/tmp

Kind regards

---

### Post by schragge on 2013-03-02
Well, you can *grep* the output of *dmesg* for *scsi* and/or *sd*:
```

dmesg|grep 'scsi\|sd'

``` This will probably still spit out too much data. But *more* should be part of initramfs BusyBox, so
```
dmesg|grep 'scsi\|sd'|more
```

---

### Post by TheAdmiralty on 2013-03-02
That should work, thanks.  I was trying to use |less instead of |most; I'll get a picture up here ASAP.

UPDATE:

I have a picture of the last page of *dmesg* output, along with a video of *dmesg* running.  I don't have much experience with this, but it seems to be spitting out an awful lot.  I did try *| most*, but it must not be included in the BusyBox shell.  Wasn't found.

Last page:
[http://i579.photobucket.com/albums/ss235/Mark3Website/100_0037_zps71ee41bb.jpg](http://i579.photobucket.com/albums/ss235/Mark3Website/100_0037_zps71ee41bb.jpg)

Video:
[http://s579.beta.photobucket.com/user/Mark3Website/media/100_0038_zps6a504435.mp4.html](http://s579.beta.photobucket.com/user/Mark3Website/media/100_0038_zps6a504435.mp4.html)
^Sorry for the quality... photobucket absolutely killed it during upload.

---

### Post by TheAdmiralty on 2013-03-02
UPDATE 2:

I just reformatted the drive and installed Zorin OS 6 in place of Kubuntu 12.10, and it has the exact same problem.  Installed fine, made it to splash screen, drops to BusyBox.  Reboot, and it "Gave up waiting for root device."

UPDATE 3:

Zorin now boots to nothing but a black screen with the flashing white cursor.  No clue what's going on, but I'm going to reinstall everything another time and see what I get.

---

### Post by matt_symes on 2013-03-02
Hi

I wonder if your initramfs is missing some scsi driver that is on the LiveCD/USB but not in your initramfs ?

EDIT:

Boot into a liveCD/USB.

mount the scsi drive and check you can write to it and type

```
lsmod | sort
```

Post the results back here.

EDIT2:

BTW: That photo looked peachy. Noothing wrong that i could see in the text displayed. Looks like the drives are fine.

I couold not make head nor tail of the video though.

Kind regards

---

### Post by Bashing-om on 2013-03-02
If I might make an interjection.
As the drives were previously used in a server, recon they were in a raid array and there exist meta data on those hard drives ?
I do not recall what the effect would seem when trying to install on top of that "meta data", but is this worth a thought ?
[INDENT]

think'n to excess ??
[/INDENT]

---

### Post by TheAdmiralty on 2013-03-02
Alright, I'm posting this from Zorin, which I finally got to boot; PenDriveLinux was giving me constant bad disks, so I redid the LiveOS with LiLi.
 I'm assuming the basic subsystems are close enough between it and Ubuntu to still be useful, but if not, I can do a Live boot of Kubuntu 12.10 now that I have a working boot disk creator.
*lsmod | sort *outputs the following:
```
ac97_bus               12642  1 snd_ac97_codec
binfmt_misc            17292  1 
bluetooth             158479  10 rfcomm,bnep
bnep                   17830  2 
btrfs                 638248  0 
cfi_probe              12582  0 
cfi_util               17434  1 cfi_probe
chipreg                13117  2 cfi_probe,scb2_flash
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
dm_mirror              21822  0 
dm_multipath           22747  0 
dm_raid45              76451  0 
dm_region_hash         16100  1 dm_mirror
drm                   197641  2 r128
fat                    55605  1 vfat
floppy                 60184  0 
gameport               15060  1 snd_ens1371
gen_probe              12624  1 cfi_probe
hid                    77428  1 usbhid
i2c_piix4              13093  0 
libcrc32c              12543  1 btrfs
lp                     17455  0 
mac_hid                13077  0 
map_funcs              12630  1 scb2_flash
Module                  Size  Used by
mptbase                96852  2 mptspi,mptscsih
mptscsih               39530  1 mptspi
mptspi                 22474  18 
mtd                    35584  1 scb2_flash
nls_cp437              12751  1 
nls_iso8859_1          12617  1 
overlayfs              27550  1 
parport                40930  3 parport_pc,ppdev,lp
parport_pc             32114  1 
pata_serverworks       13189  1 
ppdev                  12849  0 
psmouse                86520  0 
r128                   40572  1 
rfcomm                 38139  0 
scb2_flash             12710  0 
serio_raw              13027  0 
snd                    62218  11 snd_ens1371,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_ac97_codec        110213  1 snd_ens1371
snd_ens1371            24819  2 
snd_page_alloc         14108  1 snd_pcm
snd_pcm                80916  2 snd_ens1371,snd_ac97_codec
snd_rawmidi            25424  2 snd_ens1371,snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_timer              28931  2 snd_pcm,snd_seq
soundcore              14635  1 snd
squashfs               36095  1 
sworks_agp             13286  0 
tg3                   141369  0 
usbhid                 41937  0 
vfat                   17308  1 
xor                    25987  1 dm_raid45
zlib_deflate           26622  1 btrfs

```

Still won't boot off of the SCSI drive, doing the exact same thing as described before.  I'm putting up a new picture of the *dmesg* output on first boot; it's a little different on Zorin than what Kubuntu was giving me.
[http://i579.photobucket.com/albums/ss235/Mark3Website/100_0039_zpsd3610d4d.jpg](http://i579.photobucket.com/albums/ss235/Mark3Website/100_0039_zpsd3610d4d.jpg)

---

### Post by matt_symes on 2013-03-03
Hi

> **Bashing-om said:**
> If I might make an interjection.
As the drives were previously used in a server, recon they were in a raid array and there exist meta data on those hard drives ?
I do not recall what the effect would seem when trying to install on top of that "meta data", but is this worth a thought ?[INDENT]

think'n to excess ??
[/INDENT]


```

dm_log                 
18193  3 dm_raid45,dm_mirror,dm_region_hash dm_mirror              
21822  0  dm_multipath           
22747  0  dm_raid45              
76451  0  dm_region_hash         
16100  1 dm_mirror
```

Bashing_om. That is worth checking.

These are raid drivers. They are loaded amongst other drivers. 

Were the drives part of a raid array ? Do you have then set up as a raid array ?

Kind regards

---

### Post by TheAdmiralty on 2013-03-03
They were, but all three drives have been set as independent under the LSI configuration. The configuration looks like this:
```

FUJITSU 15K                      Independant                        Disk 0                    Root Drive
SEAGATE CHEETAH 1                Ind. (Ex-RAID1)                    Disk 1
SEAGATE CHEETAH 2                Ind. (Ex-RAID1) (Unpowered)        Disk 2

```
The Fujutsi drive was never in any RAID array; I got it shortly after the server itself. Both Seagate Cheetahs came with the server in RAID-1 with each other, but the array was split. The operating system is being installed to the Fujitsu drive. The last Cheetah drive isn't connected, due to the fact that I only have three Molex connectors at the moment; two are used for internal drives, and the last one for the HDD I'm using as a LiveOS drive.

---

### Post by schragge on 2013-03-04
It may sound silly, but have you tried to explicitly specify *root=* and *rootdelay=* as kernel boot options? I mean, while at Grub menu, edit the kernel line as described at [uhelp]community/Grub2/Troubleshooting[/uhelp], and change the root=UUID=*long_string_of_hexadecimals* part to something like
```
root=/dev/[COLOR=#ff0000]sda1[/COLOR] rootdelay=120
```where [COLOR=#FF0000]sda1[/COLOR] is your root partition.

---

### Post by matt_symes on 2013-03-04
Hi

Which disk did you install Ubuntu on ?

Here's another kernel boot parameter you can try.

```
scsi_mod.scan=sync
```

Kind regards

---

### Post by schragge on 2013-03-04
For the record: [how to enable verbose SCSI logging]("http://www.novell.com/support/kb/doc.php?id=7007138").

BTW, there's *pata_serverworks* for Broadcom ServerWorks IDE controller, [s]but I didn't noticed any[/s] SCSI driver in the *lsmod* output: *mptscsih*, *mptbase*, *mptspi*, but no *scsi_mod* :?:
```

[COLOR=green]$[/COLOR] modinfo mptbase | grep debug
parm:           mpt_debug_level: debug level - refer to [mptdebug.h]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/message/fusion/mptdebug.h") - (default=0)
parm:           mpt_fwfault_debug:Enable detection of Firmware fault and halt Firmware on fault - (default=0) (int)

```

I've also found this: [LSI Fusion MPT]("http://hwraid.le-vert.net/wiki/LSIFusionMPT"). And this: [Instructions to enable SATA-IDE mode for HT1000]("ftp://ftp.supermicro.com/CDR-APLUS2_2.01_for_A+_AMD_SP5100_platform/MANUALS/Instructions_for_Serworks_HT1000_SATA.pdf"). Also have a look at [mpt-status]("http://manpages.ubuntu.com/manpages/precise/en/man8/mpt-status.8.html") and [megaraid.txt]("https://www.kernel.org/doc/Documentation/scsi/megaraid.txt") ([ChangeLog.megaraid]("https://www.kernel.org/doc/Documentation/scsi/ChangeLog.megaraid"), [ChangeLog.megaraid_sas]("https://www.kernel.org/doc/Documentation/scsi/ChangeLog.megaraid_sas")). *lsiutil* can be downloaded from [here]("http://karlsbakk.net/LSIUtil%20Kit%201.63/") (somehow, I can find only an older version on [LSI website]("http://www.lsi.com/Search/Pages/downloads.aspx?k=lsiutil")).

Now, I'd like to see the output of
```
lspci -vmmnn | egrep -A6 '^Class:[[:blank:]](IDE|SCSI)'
```

---

### Post by matt_symes on 2013-03-05
Hi

That would make sense scragge.

I am still wonder if his initramfs is missing the scsi drivers for the LSI card.

Kind regards

---

### Post by schragge on 2013-03-05
Well, this is what I get on my system (Debian wheezy):
```

[COLOR=green]$[/COLOR] [COLOR=blue]uname -a[/COLOR]
Linux infa64imgs 3.2.0-4-amd64 #1 SMP Debian 3.2.35-2 x86_64 GNU/Linux
[COLOR=green]$[/COLOR] [COLOR=blue]zcat /boot/initrd.img-`uname -r`|cpio -it|egrep '/(scsi/[lms]|fusion/)'|sort[/COLOR]
60856 blocks
lib/modules/3.2.0-4-amd64/kernel/drivers/message/fusion/mptbase.ko
lib/modules/3.2.0-4-amd64/kernel/drivers/message/fusion/mptfc.ko
lib/modules/3.2.0-4-amd64/kernel/drivers/message/fusion/mptsas.ko
lib/modules/3.2.0-4-amd64/kernel/drivers/message/fusion/mptscsih.ko
lib/modules/3.2.0-4-amd64/kernel/drivers/message/fusion/mptspi.ko
lib/modules/3.2.0-4-amd64/kernel/drivers/scsi/libfc
lib/modules/3.2.0-4-amd64/kernel/drivers/scsi/libfc/libfc.ko
lib/modules/3.2.0-4-amd64/kernel/drivers/scsi/libiscsi.ko
lib/modules/3.2.0-4-amd64/kernel/drivers/scsi/libiscsi_tcp.ko
lib/modules/3.2.0-4-amd64/kernel/drivers/scsi/libsas
lib/modules/3.2.0-4-amd64/kernel/drivers/scsi/libsas/libsas.ko
lib/modules/3.2.0-4-amd64/kernel/drivers/scsi/libsrp.ko
lib/modules/3.2.0-4-amd64/kernel/drivers/scsi/lpfc
lib/modules/3.2.0-4-amd64/kernel/drivers/scsi/lpfc/lpfc.ko
lib/modules/3.2.0-4-amd64/kernel/drivers/scsi/megaraid
lib/modules/3.2.0-4-amd64/kernel/drivers/scsi/megaraid.ko
lib/modules/3.2.0-4-amd64/kernel/drivers/scsi/megaraid/megaraid_mbox.ko
lib/modules/3.2.0-4-amd64/kernel/drivers/scsi/megaraid/megaraid_mm.ko
lib/modules/3.2.0-4-amd64/kernel/drivers/scsi/megaraid/megaraid_sas.ko
lib/modules/3.2.0-4-amd64/kernel/drivers/scsi/mpt2sas
lib/modules/3.2.0-4-amd64/kernel/drivers/scsi/mpt2sas/mpt2sas.ko
lib/modules/3.2.0-4-amd64/kernel/drivers/scsi/mvsas
lib/modules/3.2.0-4-amd64/kernel/drivers/scsi/mvsas/mvsas.ko
lib/modules/3.2.0-4-amd64/kernel/drivers/scsi/mvumi.ko
lib/modules/3.2.0-4-amd64/kernel/drivers/scsi/scsi_debug.ko
lib/modules/3.2.0-4-amd64/kernel/drivers/scsi/scsi_mod.ko
lib/modules/3.2.0-4-amd64/kernel/drivers/scsi/scsi_tgt.ko
lib/modules/3.2.0-4-amd64/kernel/drivers/scsi/scsi_transport_fc.ko
lib/modules/3.2.0-4-amd64/kernel/drivers/scsi/scsi_transport_iscsi.ko
lib/modules/3.2.0-4-amd64/kernel/drivers/scsi/scsi_transport_sas.ko
lib/modules/3.2.0-4-amd64/kernel/drivers/scsi/scsi_transport_spi.ko
lib/modules/3.2.0-4-amd64/kernel/drivers/scsi/scsi_transport_srp.ko
lib/modules/3.2.0-4-amd64/kernel/drivers/scsi/scsi_wait_scan.ko
lib/modules/3.2.0-4-amd64/kernel/drivers/scsi/sd_mod.ko
lib/modules/3.2.0-4-amd64/kernel/drivers/scsi/ses.ko
lib/modules/3.2.0-4-amd64/kernel/drivers/scsi/sg.ko
lib/modules/3.2.0-4-amd64/kernel/drivers/scsi/sr_mod.ko
lib/modules/3.2.0-4-amd64/kernel/drivers/scsi/stex.ko
lib/modules/3.2.0-4-amd64/kernel/drivers/scsi/st.ko
lib/modules/3.2.0-4-amd64/kernel/drivers/scsi/sym53c8xx_2
lib/modules/3.2.0-4-amd64/kernel/drivers/scsi/sym53c8xx_2/sym53c8xx.ko

```

---

### Post by matt_symes on 2013-03-05
Hi

At the busy box prompt, does pressing

```
ctrl + d
```

continue the boot cycle ?

Kind regards

---

### Post by TheAdmiralty on 2013-03-05
Just got back; I'll be sure to read through everything that was posted and keep you updated.

UPDATE:

I just ran into an IDE DVD reader; I'm going to burn several different distros and see if I have any luck with it.

---

### Post by TheAdmiralty on 2013-03-06
It boots.

I'll describe what I did, because it seems to have really been an issue of trying to do something the LiveOS wasn't intended to do.

I completely gutted the hard drive bays on this, and removed the Fujitsu drive entirely.  I then shifted the remaining two Cheetah drives upward and jumped them to ID0 and ID1. Secondly, I added an IDE DVD-ROM drive and booted it off of a DVD burnt with Zorin.  Booted into the Installation menu and installed on the first drive.

On restart, it passed the default GRUB menu, went through the splash screen, and stopped at BusyBox.  [ctrl] + [d] caused it to repeat itself. I rebooted, and changed the GRUB boot line to include *root=/dev/sda1 noapic rootdelay=120*

It actually booted to the desktop.

This is just my relatively uneducated assumption, but it would appear that it isn't possible to get a reliable installation from a LiveOS fron IDE, over an LSI controller, and onto a SCSI drive.
I still have problems, but they're nothing software related, or fixable at the moment (IE, not enough graphical power).   I'll go try it again to make sure that wasn't a fluke.  As long as it's repeatable, I'll go edit the GRUB config and make it permanent; will also probably set it to skip over the GRUB delay altogether if possible.

---

### Post by matt_symes on 2013-03-07
Hi

I'm glad you got it working :)

Does it still boot if you remove the noapic kernel option ?

Kind regards

---

### Post by TheAdmiralty on 2013-03-07
Just tested it, and yes, it will boot without *noapic*.  The two kernel options that are needed are *root=/dev/sda1* and *rootdelay=120*.

---

