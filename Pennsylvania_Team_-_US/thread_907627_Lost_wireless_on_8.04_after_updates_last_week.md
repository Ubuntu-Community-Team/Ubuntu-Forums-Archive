---
title: "Lost wireless on 8.04 after updates last week"
date: 2008-09-01
forum: Pennsylvania Team - US
---

### Post by cybrsaylr on 2008-09-01
Just thought of trying here.
It seems there has been many problems with laptop wireless connections after recent updates. My wireless connection ran great until updating last week. After a reboot all wireless networks are gone from my few month old Toshiba laptop and am back on a wired connection. 

Has anyone here come up with a fix to restore wireless as it ran before those updates? I've tried many on the 'fixes' suggested in the main forums but so far can't get wireless back.

---

### Post by jedijf on 2008-09-01
A little more info would be nice, to help trouble shoot.
Please open a terminal and paste the output of the follwing commands:

1) uname -r

2) lspci

3) lsmod

Once we have this info, I am sure the suggestions will start to roll in!

---

### Post by cybrsaylr on 2008-09-01
jedijf,
Here is the output of those 3 commands:

laptop:~$ uname -r
2.6.24-19-generic
tt@tt-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
0e:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
14:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
14:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
14:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
14:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
tt@tt-laptop:~$  lsmod
Module                  Size  Used by
radeon                124192  0 
drm                    82452  1 radeon
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
powernow_k8            16704  1 
cpufreq_powersave       2688  0 
cpufreq_conservative     8712  0 
cpufreq_ondemand        9740  1 
cpufreq_stats           7104  0 
freq_table              5536  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5284  0 
sbs                    15112  0 
dock                   11280  0 
container               5632  0 
sbshc                   7680  1 sbs
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
snd_hda_intel         344728  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
video                  19856  0 
output                  4736  1 video
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
serio_raw               7940  0 
snd_rawmidi            25760  1 snd_seq_midi
sdhci                  19076  0 
ricoh_mmc               4352  0 
psmouse                40336  0 
mmc_core               51460  1 sdhci
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ati_agp                 9996  0 
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
battery                14212  0 
ac                      6916  0 
button                  9232  0 
k8temp                  6656  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
i2c_piix4               9612  0 
i2c_core               24832  1 i2c_piix4
agpgart                34760  2 drm,ati_agp
soundcore               8800  1 snd
evdev                  13056  6 
pcspkr                  4224  0 
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
usbhid                 31872  0 
hid                    38784  1 usbhid
ide_cd                 32544  0 
cdrom                  37408  1 ide_cd
pata_acpi               8320  0 
ata_generic             8324  0 
pata_atiixp             8960  0 
sg                     36880  0 
sd_mod                 30720  3 
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
ehci_hcd               37900  0 
atiixp                  5648  0 [permanent]
ide_core              113996  2 ide_cd,atiixp
ohci_hcd               25348  0 
ahci                   28420  2 
r8169                  32900  0 
usbcore               146028  4 usbhid,ehci_hcd,ohci_hcd
libata                159344  4 pata_acpi,ata_generic,pata_atiixp,ahci
scsi_mod              151436  4 sbp2,sg,sd_mod,libata
thermal                16796  0 
processor              36872  2 powernow_k8,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3

---

### Post by jedijf on 2008-09-02
Try here for the madwifi drivers:

[http://madwifi.org/](http://madwifi.org/)

They may work.

Also, it's possible that you have the new driver on your system.

If you would like try 'sudo modprobe ath5k'

and see if that works; if not try the madwifi drivers.

The good news is, it seems, Atheros is open sourcing its drivers and it should be getting much better shortly!!

---

### Post by cybrsaylr on 2008-09-02
Put it in and got this:

-laptop:~$ sudo modprobe ath5k
FATAL: Module ath5k not found.



Went to [http://madwifi.org](http://madwifi.org) and downloaded the latest but am having trouble opening and installing.
 
I don't know what I'm doing wrong.
I think I did it before but this time I can't get it to run.

---

### Post by jedijf on 2008-09-03
Actually, before we go too far.

Have you checked restricted drivers?

System -- Admin -- Hardware Drivers

If there are restricted drivers there that need to be enabled, you may just need to do that.

I always presume that is checked first; sorry!!

Sometimes, especially after kernel upgrades, they have to be re-enabled due to the 'special' kernel modules that they require.

---

### Post by cybrsaylr on 2008-09-03
> **jedijf said:**
> 

If there are restricted drivers there that need to be enabled, you may just need to do that.

There are 3 listed and all are disabled and not in use presently.
They are:

ATI accelerated graphics driver

Atheros Hardware Acess Layer (HAL)

Support for Atheros 802.11 wireless Lan cards

---

### Post by jedijf on 2008-09-03
ENABLE THEM!!!

All should be well.

---

### Post by cybrsaylr on 2008-09-03
I enabled all 3 and only the, ATI accelerated graphics driver says it is 'in use'.
HAL shows a green 'in use' checkmark but after a required reboot, it goes back to a red 'not in use' red light.
The same happens with #3, Support for Atheros 802.11 wireless Lan cards

The other two show an enabled checkmark but right next to them their staus is shown as 'not in use' with a red indicator light lit.

And I still have no wireless.
I tried a few reboots doing this with the same results, no wireless.

---

### Post by jedijf on 2008-09-03
Are you plugged in to a wired internet connection?

You have to have an internet connection, enable, and possibly reboot; remain wired the whole time.

---

### Post by cybrsaylr on 2008-09-03
Have done that.
Did all that while with a working wired connection the whole time.

---

### Post by jedijf on 2008-09-03
ok, open terminal and type

sudo apt-get update

three times  ^^^ (geek heel clicking :-)  )  it works

then enable the restricted drivers and reboot

---

### Post by cybrsaylr on 2008-09-04
> **jedijf said:**
> ok, open terminal and type

sudo apt-get update

three times  ^^^ (geek heel clicking :-)  )  it works

then enable the restricted drivers and reboot

Did that.
Then enabled the 3 drivers and rebooted and still no wireless.

Checked the 3 drivers then and again only,
ATI accelerated graphics driver showed in use with a green checkmark.
the other 2,
Atheros Hardware Acess Layer (HAL)

Support for Atheros 802.11 wireless Lan cards

while checked off as enabled had the red light next to them lit and 'not in use' was indicated.

---

### Post by cybrsaylr on 2008-09-04
Just tried rebooting a couple times and can't get these 3 drivers to reboot with a green check:

1 ATI accelerated graphics driver

2 Atheros Hardware Acess Layer (HAL)

3 Support for Atheros 802.11 wireless Lan cards

The only one that comes back with a green check is #1

When I enable #2 & #3 then reboot and look at what happened #2 & #3 come back after showing 'not in use'.

---

### Post by jedijf on 2008-09-04
Try going back to the previous kernel on boot.

If it autoboots, hit escape (i believe) to get the boot screen.

If the previous kernel works, we can go from there.

Way to hang in there.  Great job!!

Or just try this:

[http://egoleo.wordpress.com/2008/06/02/howto-enable-wireless-on-acer-4520-on-ubuntu-hardy/](http://egoleo.wordpress.com/2008/06/02/howto-enable-wireless-on-acer-4520-on-ubuntu-hardy/)

which is basically where we started. :-)

---

### Post by cybrsaylr on 2008-09-05
I did try a previous kernel on boot with no luck.

Also tried the link you provided but had trouble with 
3. Untar the downloaded package and

4. Get inside the unpacked directory:

I don't use that very often, Maybe I did something wrong.

I thought I got in but it didn't get wireless networks back.

---

### Post by jedijf on 2008-09-06
Ok, without physically being there, this is the last thing i can recommend:

[http://ubuntuforums.org/showpost.php?p=4999962&postcount=1](http://ubuntuforums.org/showpost.php?p=4999962&postcount=1)


Good Luck!!

---

### Post by cybrsaylr on 2008-09-06
Well just got done trying that and still have no wireless.

After putting these commands in terminal:

Code:
> sudo apt-get install build-essential

wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)

tar xfz madwifi-ng-r2756+ar5007.tar.gz

cd madwifi-ng-r2756+ar5007

sudo make 

sudo make install

sudo modprobe ath_pci

sudo reboot


This was the results I got towards the bottom of Terminal printout:



> 100%[====================================>] 485           --.--K/s             

15:18:21 (67.53 MB/s) - `madwifi-ng-r2756+ar5007.tar.gz.2' saved [485/485]

tt@tt-laptop:~$ 
tt@tt-laptop:~$ tar xfz madwifi-ng-r2756+ar5007.tar.gz
tt@tt-laptop:~$ 
tt@tt-laptop:~$ cd madwifi-ng-r2756+ar5007
tt@tt-laptop:~/madwifi-ng-r2756+ar5007$ 
tt@tt-laptop:~/madwifi-ng-r2756+ar5007$ sudo make 
make: *** No targets specified and no makefile found.  Stop.
tt@tt-laptop:~/madwifi-ng-r2756+ar5007$ 
tt@tt-laptop:~/madwifi-ng-r2756+ar5007$ sudo make install
make: *** No rule to make target `install'.  Stop.
tt@tt-laptop:~/madwifi-ng-r2756+ar5007$ 
tt@tt-laptop:~/madwifi-ng-r2756+ar5007$ sudo modprobe ath_pci
FATAL: Error inserting ath_pci (/lib/modules/2.6.24-19-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
tt@tt-laptop:~/madwifi-ng-r2756+ar5007$ 
tt@tt-laptop:~/madwifi-ng-r2756+ar5007$ sudo reboot

I'm not sure but it looks like something didn't go through which resulted in that Fatal Error in the last lines.

---

### Post by jedijf on 2008-09-06
Do this:

sudo apt-get install linux-headers-$(uname -r)

and try again, starting at the 'tar' line.

---

### Post by cybrsaylr on 2008-09-06
Tried that...then rebooted and still no wireless.

Here's what I got

> tt@tt-laptop:~$ sudo apt-get install linux-headers-$(uname -r)
[sudo] password for tt: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.24-19-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tt@tt-laptop:~$ tar xfz madwifi-ng-r2756+ar5007.tar.gz
tt@tt-laptop:~$ 
tt@tt-laptop:~$ cd madwifi-ng-r2756+ar5007
tt@tt-laptop:~/madwifi-ng-r2756+ar5007$ 
tt@tt-laptop:~/madwifi-ng-r2756+ar5007$ sudo make 
make: *** No targets specified and no makefile found.  Stop.
tt@tt-laptop:~/madwifi-ng-r2756+ar5007$ 
tt@tt-laptop:~/madwifi-ng-r2756+ar5007$ sudo make install
make: *** No rule to make target `install'.  Stop.
tt@tt-laptop:~/madwifi-ng-r2756+ar5007$ 
tt@tt-laptop:~/madwifi-ng-r2756+ar5007$ sudo modprobe ath_pci
FATAL: Error inserting ath_pci (/lib/modules/2.6.24-19-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
tt@tt-laptop:~/madwifi-ng-r2756+ar5007$ 
tt@tt-laptop:~/madwifi-ng-r2756+ar5007$ sudo reboot

---

