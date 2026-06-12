---
title: "Screen Resolution in 8.10?"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by mapes12 on 2008-10-30
Just installed 8.10 but can't change screen res to 1024x768. The max System>Preferences>Screen Resolution will let me go to is 800x600. When I had this problem in a previous version I managed to edit the xorg.conf file but this file in 8.10 is substantially stripped down and comments that some changes that were previously editable can longer be performed by editing xorg.conf. Does anybody have any ideas how I can increase my screen res please?

Mark

---

### Post by PmDematagoda on 2008-10-30
First of all, what are the specifications of your VGA card?

---

### Post by mapes12 on 2008-10-30
Here's the output from lshw:

```
ubuntu-desktop            
    description: Mini Tower Computer
    product: HP Server
    vendor: Hewlett-Packard
    version: TC2120
    serial: Chassis Serial Number
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=mini-tower cpus=1 uuid=03149042-1208-0062-8110-000E7FFF5FDB
  *-core
       description: Motherboard
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Award Software, Inc.
          physical id: 0
          version: 6.00.23 RV (09/08/2003) (09/08/2003)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.66GHz
          vendor: Intel Corp.
          physical id: 3
          bus info: cpu@0
          version: 15.2.9
          slot: Primary CPU
          size: 2667MHz
          capacity: 3400MHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: L1 Cache
             size: 8KiB
             capacity: 32KiB
             capabilities: pipeline-burst synchronous internal varies unified
        *-cache:1
             description: L2 cache
             physical id: a
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst synchronous internal varies unified
     *-memory
          description: System Memory
          physical id: 1e
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DIMM1
             size: 256MiB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: DIMM2
             size: 256MiB
             width: 64 bits
        *-bank:2
             description: DIMM DRAM Synchronous
             physical id: 2
             slot: DIMM3
             size: 256MiB
             width: 64 bits
        *-bank:3
             description: DIMM DRAM Synchronous
             physical id: 3
             slot: DIMM4
             size: 256MiB
             width: 64 bits
     *-pci:0
          description: Host bridge
          product: GCNB-LE Host Bridge
          vendor: Broadcom
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 32
          width: 32 bits
          clock: 33MHz
        *-network
             description: Ethernet interface
             product: NetXtreme BCM5702X Gigabit Ethernet
             vendor: Broadcom Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             logical name: eth0
             version: 02
             serial: 00:0e:7f:ff:5f:db
             size: 100MB/s
             capacity: 1GB/s
             width: 64 bits
             clock: 66MHz
             capabilities: pcix pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5702-v2.24a ip=192.168.1.71 latency=64 link=yes mingnt=64 module=tg3 multicast=yes port=twisted pair speed=100MB/s
        *-multimedia
             description: Multimedia audio controller
             product: YMF-724F [DS-1 Audio Controller]
             vendor: Yamaha Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Yamaha DS-1 PCI latency=32 maxlatency=25 mingnt=5 module=snd_ymfpci
        *-display UNCLAIMED
             description: VGA compatible controller
             product: Rage XL
             vendor: ATI Technologies Inc
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 27
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=32 mingnt=8
        *-isa
             description: ISA bridge
             product: CSB6 South Bridge
             vendor: Broadcom
             physical id: f
             bus info: pci@0000:00:0f.0
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=piix4_smbus latency=32 module=i2c_piix4
        *-ide
             description: IDE interface
             product: CSB6 RAID/IDE Controller
             vendor: Broadcom
             physical id: f.1
             bus info: pci@0000:00:0f.1
             logical name: scsi0
             logical name: scsi1
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_serverworks latency=64 module=pata_serverworks
           *-disk:0
                description: ATA Disk
                product: Maxtor 6Y080L0
                vendor: Maxtor
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: YAR4
                serial: Y2D958VE
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=7f247f24
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 3a1babfc-d160-497b-ae0a-98f452bb961f
                   size: 12GiB
                   capacity: 12GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-10-30 15:20:15 filesystem=ext3 modified=2008-10-30 16:09:15 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2008-10-30 15:40:24 state=mounted
              *-volume:1
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /home
                   version: 1.0
                   serial: 182ad22f-1719-4cc4-9a4e-3fdf601bbee3
                   size: 58GiB
                   capacity: 58GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-06-20 17:52:33 filesystem=ext3 modified=2008-10-30 16:10:09 mount.fstype=ext3 mount.options=rw,relatime,errors=continue,data=ordered mounted=2008-10-30 16:10:09 state=mounted
              *-volume:2
                   description: Linux swap volume
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   version: 1
                   serial: 05a5e1c0-05a8-47b2-9145-8cefa29e722c
                   size: 3169MiB
                   capacity: 3169MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
           *-disk:1
                description: ATA Disk
                product: ExcelStor Techno
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sdb
                version: V32O
                serial: VNR20EG2B2H3CB
                size: 76GiB (82GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=1bfd1bfc
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sdb1
                   version: 1.0
                   serial: e3b7d3b1-bebb-4baf-ab13-27cc6b436425
                   size: 38GiB
                   capacity: 38GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-06-20 17:31:02 filesystem=ext3 modified=2008-10-30 14:10:31 mounted=2008-10-30 12:51:09 state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sdb2
                   version: 3.1
                   serial: 4880c04b-6b29-1e4a-b0c3-97ebe5d3e9b7
                   size: 38GiB
                   capacity: 38GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2008-06-20 13:36:04 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-cdrom
                description: DVD writer
                product: DVDR1628P1
                vendor: PHILIPS
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: Q1.1
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-usb
             description: USB Controller
             product: CSB6 OHCI USB Controller
             vendor: Broadcom
             physical id: f.2
             bus info: pci@0000:00:0f.2
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80 module=ohci_hcd
     *-pci:1
          description: Host bridge
          product: GCNB-LE Host Bridge
          vendor: Broadcom
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: GCLE-2 Host Bridge
          vendor: Broadcom
          physical id: 102
          bus info: pci@0000:00:0f.3
          version: 00
          width: 32 bits
          clock: 33MHz
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 56:16:90:17:de:ba
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
mark@ubuntu-desktop:~$ 
```

---

### Post by mapes12 on 2008-10-30
Bump..............sorry!

---

### Post by HittingSmoke on 2008-10-30
> **mapes12 said:**
> Just installed 8.10 but can't change screen res to 1024x768. The max System>Preferences>Screen Resolution will let me go to is 800x600. When I had this problem in a previous version I managed to edit the xorg.conf file but this file in 8.10 is substantially stripped down and comments that some changes that were previously editable can longer be performed by editing xorg.conf. Does anybody have any ideas how I can increase my screen res please?

Mark

Try installing and using EnvyNG to install your graphics card drivers. I get the same problem using the restricted drivers manager or installing drivers via apt-get. EnvyNG always configures everything right the first time.

```
sudo apt-get install envyng
```

Run it from your menu and it's all self explanatory from there

---

### Post by kokoni on 2008-10-30
> **mapes12 said:**
> Just installed 8.10 but can't change screen res to 1024x768. The max System>Preferences>Screen Resolution will let me go to is 800x600. When I had this problem in a previous version I managed to edit the xorg.conf file but this file in 8.10 is substantially stripped down and comments that some changes that were previously editable can longer be performed by editing xorg.conf. Does anybody have any ideas how I can increase my screen res please?

Mark

xmmm bro i have the same problem i have the previous version of ububtu and the max screen resolution is 800*600 ..have u made anything from terminal?cause if i enable the nvidia on board card mou i go out of range....

---

### Post by mapes12 on 2008-10-30
> xmmm bro i have the same problem i have the previous version of ububtu and the max screen resolution is 800*600 ..have u made anything from terminal?cause if i enable the nvidia on board card mou i go out of range....

I'll give the EnvyNG a go when I get back to the office at the weekend. Not heard of it before and after Googling it and finding the authors site it looks like a good utility.

---

### Post by homerm06 on 2008-10-31
Hi, I have the same trouble. I entered the sudo code just as you posted it but I get > E: Couldn't find package envyng


Any other tricks? I have Ubuntu 8.10 just installed on an eMachines W5243 PC.

---

### Post by homerm06 on 2008-10-31
Good news, I found a little trick lol. Ok it's not a trick. Try installing the resrticed driver.

System>Administration>Hardware Drivers and download/install the recommended video card driver...

I hope this works :) I just did it and it worked for me. :popcorn:

---

### Post by flameproof on 2008-10-31
I had the same problem. Just could get max. 800x600 screen.

I installed the "restricted drivers" (NVidia 177 in my case)

It didn't do anything, but since this was not my first priority I didn't do anything about. But then, without doing anything more I suddenly got the 1024 option later.

---

### Post by triulo on 2008-10-31
I have a similar problem in that my preferred screen resolution is not offered in "Screen Resolution" or by xrandr. In fact my monitor nags when it's not at 1280x1024. I had the same problem in Hardy but used desktopconfig-gtk which is now gone.

```
>xrandr -q
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1360 x 1360
VGA disconnected (normal left inverted right x axis y axis)
TMDS-1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8
   1152x864       60.0
   1024x768       60.0*
   800x600        60.3
   640x480        59.9
```

I checked the "Hardware Drivers" tool and nothing is listed. Compiz is working. I have a Lenovo with an integrated Q965 video card (so EnvyNG won't work for me):

```
>lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)
```

I also tried deleting xorg.conf - didn't work. Then I recreated xorg.conf by using: sudo dpkg-reconfigure xserver-xorg (or sudo dpkg-reconfigure -phigh xserver-xorg), didn't work. Then I tried editing xorg.conf to the include desired modelines, etc but that didn't work either.

```
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        Vendorname      "ViewSonic"
        Modelname       "ViewSonic VA912b"
        Modeline  "800x600" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
        Modeline  "1280x1024" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
                   Modes "1280x1024" "800x600"
        EndSubSection
EndSection
```

Perhaps my xorg.conf is still too generic?

---

### Post by homerm06 on 2008-10-31
> **flameproof said:**
> I had the same problem. Just could get max. 800x600 screen.

I installed the "restricted drivers" (NVidia 177 in my case)

It didn't do anything, but since this was not my first priority I didn't do anything about. But then, without doing anything more I suddenly got the 1024 option later.

Did you restart the computer before you noticed the change? I had to reboot mine that's why.

---

### Post by mapes12 on 2008-11-01
Progress so far..................

I managed to find the installation guide for EnvyNG here:

[http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

and downloaded the package with this command:

```
sudo apt-get install envyng-gtk
```

but for some reason when I typed in the command ```
sudo envyng -g
``` to start the application in GUI mode I get this repsonse:

```
ERROR: Make sure that envyng-qt is installed
```

So, I then installed this package with ```
sudo apt-get install envyng-qt
``` and I can start the application in a GUI window.

However, the only ATI driver listed is 8.543-Oubuntu4 as shown in the attached screenshot. And, as you can see on the right of the screenshot this driver is not compatible nor recommended. I have tried using it but it does not resolve my problem of being able to change my screen res to 1024x768.

Here is a reminder of the lshw output for my grapics adaptor which is built into the motherboard:

 ```
*-display UNCLAIMED
             description: VGA compatible controller
             product: Rage XL
             vendor: ATI Technologies Inc
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 27
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=32 mingnt=8
```

Any help would be greatly appreciated. :confused:

---

### Post by mapes12 on 2008-11-03
Can anybody help??

---

### Post by mapes12 on 2008-11-04
I've been searching on the web for 2 days now but can't find a solution to my problem. On checking the X.Org Wiki here:

[http://www.x.org/wiki/Projects/Drivers?action=show&redirect=VideoDrivers](http://www.x.org/wiki/Projects/Drivers?action=show&redirect=VideoDrivers)

it appears that no Linux driver is supported for my Rage XL video device. I have edited xorg.conf to use the supported ati driver instead of the default vesa driver. This gave me more screen resolution options but the highest one still remains too low at 800x600.

Therefore, my only option is to replace my video device with a supported graphics card. For £4.50 inc P&P I've managed to get a card off ebay with the S3 Savage (16MB) chipset, which is supported by the X.Org project. Just waiting for it to arrive in the mail to try it out. I will post again on this thread when I have it up and working to report on progress. I know the S3 card is an old spec but I don't want to spend much on this (likewise) old base unit. I don't run any graphic intense applications.

Bye for now ):P

---

### Post by rggavubt on 2008-11-06
I have an Nvidia GeForce 8800 GTS card and had the same problem...max resolution was 800X600.  I activated the 173 nvidia driver and fixed my problem by going to system, administration, Nvidia X Server Settings, then X Server Display Configuration.  I selected 1024X768 and clicked apply and I was fixed.  This section also showed my correct monitor.:popcorn:
Just found out that when I restart PC resolution reverts back to 800X600 and monitor is unspecified.  Tried "save configuration to X" but didn't fix it on reboot??

I found out that if you set resolution to 1024X768 and go to terminal and enter :
"sudo nvidia-settings" and then save to X configuration it sticks.  I rebooted and the resolution remained at 1024X768.

---

### Post by mapes12 on 2008-11-06
Thanks rggavubt

Mine is an ATI device onboard the motherboard and so I don't have the same options as if I had a Nvidia card.

I've even tried this HowTo but it still didn't work: [http://ubuntuforums.org/showpost.php?p=6086662&postcount=8](http://ubuntuforums.org/showpost.php?p=6086662&postcount=8)

All my hopes are now on the S3 Savage card..........when it arrives. :(

---

### Post by mapes12 on 2008-11-08
Well, the S3 Savage 4 PCI card arrived this morning but when I opened up my case the PCI slots are 64 bit 3.3 volt long ones :oops:. The PCI card is the normal 5 volt 32 bit variety. So it wont fit ](*,)

I've had another look on eBay but none of the graphics cards are for these old PCI slots. The box is a HP server tc2120 probably built when the ark was launched, but it has a decent spec with an Intel P4 2.66 Ghz CPU and 1MB RAM.

I was originally running Ubuntu 7.10 before upgrading to 8.10 the other day. This 800x600 screen res is just no good for my eyes. Therefore, I've rolled back and installed 8.04 LTS but on boot up, yes you've guessed it, max screen res 800x600. I had come across this post when I was originally trying to solve the problem in 8.10: [http://ubuntuforums.org/showpost.php?p=6086662&postcount=8](http://ubuntuforums.org/showpost.php?p=6086662&postcount=8) but it didn't work with 8.10. So, I gave it another go in 8.04 and it worked!! I'm now in the 1024x768 res I need. I've booted up a couple of times and everything seems stable except for one thing. When the username screen pops up the dialogue box has moved from the centre of the screen toward the bottom right slightly and the "Options" menu that should be in the bottom left has disappeared. I can't see that it matters because once I've entered my username and password the system starts up and everything is positioned where it should be with the res now comfortable.

---

### Post by drakeman007 on 2008-11-08
MMM you already install the ati restricted drivers from ubuntu updates? the update solve my problem, in a previous post you say that you installed nvidia restricted, but the ati drivers?

---

### Post by mapes12 on 2008-11-08
> you already install the ati restricted drivers from ubuntu updates?

How would I do this please?

---

### Post by dave28734 on 2009-04-19
Try following at your own risk, but it did work for me.

Increase resolution higher than 800X640 in Ubuntu 8.10.

After unsuccessfully trying several remedies, the following worked for me.

Ran Knoppix 5.1 live cd.  The resolution was great.  Copied knoppix /etc/X11/xorg.conf to a text file.
Could not copy to a cd or flash drive because of permission problem.  Sent file as attachement by email to me.  Restarted
computer into ubuntu 7.10 and saved email attachment to desktop.  Created folder xorg.conf-old on Desktop and copied ubuntu 8.10 /etc/X11/xorg.conf to it.  Selected all contents in ubuntu 8.10 /etc/X11/xorg.conf and deleted it.  Copied downloaded knoppix file to ubuntu/etc/X11.xorg.conf. Logged out and back in.  An error window appeared with several options including "view error log".  I looked at the error log and it indicated that the line "RgbPath      "/usr/share/X11/rgb" could not be used.  In my case it was line 18.  I edited the ubuntu  /etc/X11/xorg.conf file and commented out that line to look like this:

#RgbPath      "/usr/share/X11/rgb"

I then saved the file and logged out and back in and it has been working perfectly since.  I have options fo 1152X864 and below for screen resolution.  Could probably add higher but have not yet tried it.

Hope this helps someone.

---

