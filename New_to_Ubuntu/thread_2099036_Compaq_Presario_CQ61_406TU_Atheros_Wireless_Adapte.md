---
title: "Compaq Presario CQ61 406TU Atheros Wireless Adapter"
date: 2012-12-28
forum: New to Ubuntu
---

### Post by robertthebruce on 2012-12-28
solved - upgraded my thinking to ext4 with everything in / and it worked out of box




Compaq Presario CQ61 406TU
1.4CPU, 512Ram, 40GHDD
Grub Dual Boot Win7
Ubuntu 12.04.1 LTS Server

i have the dreaded
> 02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 
Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)Im having problems with it starting reliably...

I've tiried a lot of the methods here and am embarrassed to post this as there is already a plethora of info about it so i thought if i blog my steps maybe someone could nudge me along in  the right direction...

As to the many methods i have tried here i would next like to try blacklisting but im not sure exactly what to blacklist. My best guess is ath_pci and i tried that last install along with disabling ip6. I could have sworn it worked for one boot but that was one boot of many....

i am also sort of following this thread
[http://ubuntuforums.org/showthread.php?p=12425691#post12425691](http://ubuntuforums.org/showthread.php?p=12425691#post12425691)


I've just done a fresh install and going thru the updates grades

> apt-get update> sudo apt-get upgrade. I normally also 
> sudo apt-get dist-upgradebut im holding off until i sort the wireless connect issue.

After above it says reboot required so i reboot twice, i havnt tried that yet......nope, reboot twice at that particular point doesnt fix it.... 

On the first boot from the install I have to sudo ifup wlan0
iwconfig before ifup on first boot from install

> 
wlan0     IEEE 802.11bgn  ESSID:"BigPondE90E07"
          Mode:Managed  Access Point: Not Associated Tx power=14dBm
          Retry  long limit:70  RTS thr:off   Fragment thr:off
          Power Management:on

eth0      no wireless extensions.
Then i run 
> 
sudo ifup wlan0it reports
> 
ssh stop/waiting
ssh start/running, process 1327
I then iwconfig and get this
> 
robert@camserver3:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"BigPondE90E07"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 58:98:35:E9:0E:07
          Bit Rate=26 Mb/s   Tx-Power=15 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=34/70  Signal level=-76 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:26   Missed beacon:0
eth0      no wireless extensions.
running sudo lshw -C network from the other thread i get this but im exhauseted for the moment
>   *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: c4:17:fe:2f:d7:44
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-29-generic-pae firmware=N/A ip=10.0.0.3 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:93500000-9350ffff
  *-network DISABLED
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:26:9e:f0:54:99
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=off broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:91410000-91410fff memory:91400000-9140ffff memory:91420000-9142ffff
robert@camserver3:~$So im just going to put a cup of tea on and come back to look at this result:popcorn:


ps - what have i done with the quote tags? is it normal the front one shows in the page...darn it..

---

### Post by robertthebruce on 2012-12-28
so ive now done this
> 
cat /etc/modprobe.d/blacklist-ath_pci.confand getting this
> 
robert@camserver3:~$ cat /etc/modprobe.d/blacklist-ath_pci.conf
# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
blacklist ath_pci
from what i can gather that command may have made an entry into the a file by creating a file... i reckon that's pretty clever, one day i may have time to read more about that...

---

### Post by robertthebruce on 2012-12-28
nahh, that didnt work...

imof to sudo nano /etc/modprobe.d/blacklist.conf

and adding

blacklist ath5k
blacklist ath9k

and just for the hell of it,,,

# blacklist ath_pci

( but i think i already did that with itas own file earlier):confused:


going for a reboot...

---

### Post by robertthebruce on 2012-12-28
npe, lost wlan0 completely... have gone back to modprobe to hash one of them....

and a reboot

---

### Post by robertthebruce on 2012-12-28
nope, hashing the first one didnt bring the wifi light to blue (on)

have visa-versa'a....

if this doesnt activate the wifi light from orange im going to boot into window to reactivate the wifi then boot back to u and see if the one stated will pick up

---

### Post by robertthebruce on 2012-12-28
..lovely, the iface light actuvated blue which means the card can recover from blacklisting....

ive unhashed ath9 and hashed in ath5 in the conf file and will then ty a reboot
robertthebruce is online now Report Post       Edit/Delete Message Reply With Quote Multi-Quote This Message Quick reply to this message
Old 20 Minutes Ago       #7
robertthebruce
First Cup of Ubuntu
 

    

ok, so it doesnt like ath9 at all...
and unblacking ath5 brings up the card which is great
ive unhased/BL's aht_pci as well on this boot just to see what happens........nopr....i amy have to unblack it with that earlier command...hmmmm.....
robertthebruce is online now Report Post       Edit/Delete Message Reply With Quote Multi-Quote This Message Quick reply to this message
Old 6 Minutes Ago       #8
robertthebruce
First Cup of Ubuntu

    


The wifi-light turn from orange to blue reliably

i did this by blacklisting ath9
i had earlier modprobe blacklisted ath_pci which had no effect..
i have now "rm"d that modprobe
reboot
robertthebruce is online now Report Post       Edit/Delete Message Reply With Quote Multi-Quote This Message Quick reply to this message
Unread 1 Minute Ago       #9
robertthebruce
First Cup of Ubuntu
 

nahhh, all that hasnt worked.... im back at the full circle of the last install

it's wierd... after boot

sudo ifup wlan0
reports that it is already configured (but its not)

then it doesnt matter how long i wait it will not connect untill i run some command that touchs some part of it....even the modules file which it is not mentioned except by dependency

sudo ifup wlano
reports that ssh start stop string



i am not sure where to go to from here
robertthebruce is online now Report Post

---

### Post by robertthebruce on 2012-12-28
how lovely is this.... it 2am... AGAIN! wafpoc!

---

### Post by robertthebruce on 2012-12-28
> **robertthebruce said:**
> 
i have now "rm"d that modprobe
ends up i iddnt rm the mod file i actually rm's my entire blacklist file...

cant fnid the recycle bin so reloading 12

---

### Post by squakie on 2012-12-28
You need to not blacklist ath9k - that's the driver you need.  I also noticed you are connecting to some network:  BigPondE90E07

So, maybe a little clarification on what you mean by "not starting reliably".  At startup?  After hibernating?  After suspend?

---

### Post by robertthebruce on 2012-12-28
hi Squakie many thanks for your reply...

yes you are correct i need ath5k blacklisted.

what i meant by "reliably" was that within the first few boots from install it seems i cannot reliably configure it,,,,
it worked during install - ie blue light comes on and connects to essid BigPond
it worked with ifup on second boot (after upgrades, ie blue light comes on during boot and connects to essid BigPond

on third boot blue light does not change, 
ifup says its configured, 
iwconfig is empty
i then run ifup again and light turns blue and connects....

I've done another fresh install....

---

### Post by robertthebruce on 2012-12-28
Half fixed...
i've blacklisted ath9k
now the wireless card starts reliably , ie light goes from orange to blue during boot...

---

### Post by robertthebruce on 2012-12-29
[B]
note from AudioMike

Re: Toshiba nb305-n310 atheros wireless adapter[/B] 			
 			 			 		   		 		 		Try this roadmap:
[https://sites.google.com/site/easyli...oject/internet]("https://sites.google.com/site/easylinuxtipsproject/internet")
 		                   		  		  		 		 			 				__________________
				Tips for beginners with Ubuntu:
[http://sites.google.com/site/easylinuxtipsproject](http://sites.google.com/site/easylinuxtipsproject)
In for a pleasant surprise? Give Xubuntu a try: 
[http://sites.google.com/site/easylin...roject/xubuntu]("http://sites.google.com/site/easylinuxtipsproject/xubuntu")

---

### Post by robertthebruce on 2012-12-29
roadmap Contents

    1 No wireless connection at all
        1.1 Install drivers - they are installed as far as a cli noob can know
        1.2 Switch the wireless card on - it goes from orange to blue and shows up in iwconfig
        1.3 Wireless internet is being blocked by Bluetooth - dont have BT
        1.4 Install the wireless Backports modules - have held back on these, i have 12.04 server 
        1.5 Improve backward compatibility - have held back on these, i have 12.04 server
        1.6 Turn the kernel module acer_wmi off or on - have tried the visa-versa blacklisting


blacklist ath5k
#blacklist ath9k
#blacklist ath_pci
#blacklist acer_wmi
#acer_wmi




        1.7 Use the Windows driver with Ndiswrapperhave held back on these, i have 12.04 server

    2 Bad wireless connection
        2.1 Disable power management for the wireless card
        2.2 Set your router to "G-only"
    3 No wired internet on a dual boot computer
    4 Want more?

ooooooooooooooooooooooooooooooooooooooo

im having a bit of hope in this the supplicant method
[http://askubuntu.com/questions/143988/how-do-i-bring-up-my-wireless-network-at-boot](http://askubuntu.com/questions/143988/how-do-i-bring-up-my-wireless-network-at-boot)

at first i left a bracket out...
then i wasnt sure if the quotes around the ssid and pass should have been there or not.... so have tried the multis on that

supplicant method hasnt worked and isnt a solution at this stage

0000000000000000000000000000000000000000

---

### Post by audiomick on 2012-12-29
> **robertthebruce said:**
> 
ps - what have i done with the quote tags? is it normal the front one shows in the page...darn it..

The quote box always has "quote" above it. You should, however, use the # button to put code tages around terminal output. You can see in the first post that there a heap of smileys in the output.

If I use quote tags I get
>  This is my output with lots of colons and things
:) :-k 

and in code tags, it looks like this
```
This is my output with lots of colons and things
:) :-k 
```

The code box also makes a scroll bar on the side if the output is very long.

---

### Post by robertthebruce on 2012-12-29
thanks for that Audiomick...

I've tried the blacklist method to no avail...
I've tried the supplicant method for 12.01 server to no avail...
I've tried the blacklist method to no avail...

am trying the next two steps, i hope they are suitable to server
Install the wireless Backports modules 
        Improve backward compatibility

---

### Post by robertthebruce on 2012-12-29
im also searching for how to install the additional drivers in cli for 12.04server??

---

### Post by robertthebruce on 2012-12-29
```

robert@camserver3:~$ sudo apt-get install linux-backports-modules-cw-3.3-precise-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  linux-backports-modules-cw-3.3-3.2.0-35-generic linux-image-3.2.0-35-generic
Suggested packages:
  fdutils linux-doc-3.2.0 linux-source-3.2.0 linux-tools
The following NEW packages will be installed:
  linux-backports-modules-cw-3.3-3.2.0-35-generic
  linux-backports-modules-cw-3.3-precise-generic linux-image-3.2.0-35-generic
0 upgraded, 3 newly installed, 0 to remove and 79 not upgraded.
Need to get 40.8 MB of archives.
After this operation, 121 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y

```

fingers crossed

---

### Post by robertthebruce on 2012-12-29
nope, backports didnt do it... slowed wlan0 down if anything

---

### Post by audiomick on 2012-12-29
> **robertthebruce said:**
> im also searching for how to install the additional drivers in cli for 12.04server??

You need to know what the package name is, and then it should be

```
sudo apt-get install <package name>
```

---

### Post by steeldriver on 2012-12-29
I've been trying to follow this thread but tbh it's very confusing 

> Im having problems with it starting reliably...What exactly was the original problem? It shouldn't be necessary to blacklist anything since your lshw indicates it is loading/using ath9k which afaik is the correct driver based on your PCI IDs

The ath9k driver pretty much works out of the box for most people - one of my laptops used a similar Atheros device without problems on both 11.10 and 12.04 - the only thing I've remember having to do is disable hardware encryption (nohwcrypt=1)

---

### Post by squakie on 2012-12-29
Hence my earlier post about not blacklisting it.  I wonder what you have done about bluetooth - even if you don't have a bluetooth device bluetooth still gets loaded (at least it used to).  Do a lsmod and see if you see some modules that would indicate bluetooth, then blacklist those and reboot.

As an example, on my desktop (no bluetooth adapter and hence no bluetooth) I still have the following showing in my lsmod:

bluetooth             209199  10 bnep,rfcomm

---

### Post by robertthebruce on 2012-12-29
im sorry the thread is confusing - im just throwing stuff at it 'cause i dont really know what im doing...

thank you for the tip about bluetooth, i will go back to that and try to find the module....

ive got an basic issue that will probably take me three hours to master....the buffer in putty isnt long enough for the complete reply and i dont know how to go back up the console on the actual pc, ie i can only seen the displayed screen...
I say three hours because i am dreading googling "see up moniter" or something equally openended
"



wlan0 works for me but only after restarting the network

below is dmesg and lshw

dmesg

```
                resources: irq:43 ioport:2000(size=256) memory:91410000-91410fff memory:91400000-9140ffff memory:91420000-9142ffff
        *-usb:3
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:40a0(size=32)
        *-usb:4
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:4080(size=32)
        *-usb:5
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:4060(size=32)
        *-usb:6
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:4040(size=32)
        *-usb:7
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:20 memory:94505800-94505bff
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: ICH9M LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:42 ioport:4108(size=8) ioport:411c(size=4) ioport:4100(size=8) ioport:4118(size=4) ioport:4020(size=32) memory:94505000-945057ff
           *-disk
                description: ATA Disk
                product: TOSHIBA MK3256GS
                vendor: Toshiba
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: LH01
                serial: 106LF0R5S
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0fdb3d96
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 52c4-b586
                   size: 98MiB
                   capacity: 100MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2012-12-29 11:35:21 filesystem=ntfs label=System Reserved state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 3ef925ca-b1aa-3c47-913d-443051f9e4c2
                   size: 39GiB
                   capacity: 39GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2012-12-29 12:03:25 filesystem=ntfs state=clean
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   size: 258GiB
                   capacity: 258GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /boot
                      capacity: 94MiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=continue,user_xattr,acl,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      capacity: 1059MiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 2118MiB
                      capabilities: nofs
                 *-logicalvolume:3
                      description: Linux filesystem partition
                      physical id: 8
                      logical name: /dev/sda8
                      logical name: /usr
                      capacity: 4237MiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=continue,user_xattr,acl,barrier=1,data=ordered state=mounted
                 *-logicalvolume:4
                      description: Linux filesystem partition
                      physical id: 9
                      logical name: /dev/sda9
                      logical name: /var
                      capacity: 7416MiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=continue,user_xattr,acl,barrier=1,data=ordered state=mounted
                 *-logicalvolume:5
                      description: Linux filesystem partition
                      physical id: a
                      logical name: /dev/sda10
                      logical name: /home
                      capacity: 244GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=continue,user_xattr,acl,barrier=1,data=ordered state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7561S
                vendor: hp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: AH73
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:94506000-945060ff ioport:4000(size=32)
        *-generic UNCLAIMED
             description: Signal processing controller
             product: 82801I (ICH9 Family) Thermal Subsystem
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:94504000-94504fff
  *-battery
       product: EV06047
       vendor: DP-SAN44
       physical id: 1
       slot: In the back
       capacity: 4400mWh
       configuration: voltage=10.8V
robert@camserver3:~$

```


```
 width channel with regulatory rule:
[    5.174964] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000                  mBm)
[    5.174966] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz                  width channel with regulatory rule:
[    5.174970] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000                  mBm)
[    5.174972] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that                  fits a 20 MHz wide channel
[    5.176856] cfg80211: Ignoring regulatory request Set by core since the drive                 r uses its own custom regulatory domain
[    5.280342] HDMI status: Codec=3 Pin=3 Presence_Detect=0 ELD_Valid=0
[    5.280475] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.                 0/sound/card0/input9
[    5.280930] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/ca                 rd0/input10
[    5.281113] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/so                 und/card0/input11
[    5.282422] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.282428] i915 0000:00:02.0: setting latency timer to 64
[    5.311559] i915 0000:00:02.0: irq 45 for MSI/MSI-X
[    5.311568] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    5.311570] [drm] Driver supports precise vblank timestamp query.
[    5.311615] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+me                 m,decodes=io+mem:owns=io+mem
[    5.355087] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_contr                 ol'
[    5.355913] Registered led device: ath9k-phy0
[    5.355922] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xf84a0000, irq=16
[    5.364737] fixme: max PWM is zero.
[    5.617204] type=1400 audit(1356798389.161:2): apparmor="STATUS" operation="p                 rofile_load" name="/sbin/dhclient" pid=536 comm="apparmor_parser"
[    5.617216] type=1400 audit(1356798389.161:3): apparmor="STATUS" operation="p                 rofile_replace" name="/sbin/dhclient" pid=497 comm="apparmor_parser"
[    5.617711] type=1400 audit(1356798389.161:4): apparmor="STATUS" operation="p                 rofile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=536 comm="                 apparmor_parser"
[    5.617744] type=1400 audit(1356798389.161:5): apparmor="STATUS" operation="p                 rofile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=497 com                 m="apparmor_parser"
[    5.618001] type=1400 audit(1356798389.161:6): apparmor="STATUS" operation="p                 rofile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=536 comm="appar                 mor_parser"
[    5.618034] type=1400 audit(1356798389.161:7): apparmor="STATUS" operation="p                 rofile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=497 comm="ap                 parmor_parser"
[    5.619874] type=1400 audit(1356798389.161:8): apparmor="STATUS" operation="p                 rofile_replace" name="/sbin/dhclient" pid=486 comm="apparmor_parser"
[    5.620457] type=1400 audit(1356798389.165:9): apparmor="STATUS" operation="p                 rofile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=486 com                 m="apparmor_parser"
[    5.620760] type=1400 audit(1356798389.165:10): apparmor="STATUS" operation="                 profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=486 comm="a                 pparmor_parser"
[    5.742579] fbcon: inteldrmfb (fb0) is primary device
[    5.766687] cfg80211: Ignoring regulatory request Set by core since the drive                 r uses its own custom regulatory domain
[    5.766693] cfg80211: World regulatory domain updated:
[    5.766695] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gai                 n, max_eirp)
[    5.766698] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 20                 00 mBm)
[    5.766701] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 20                 00 mBm)
[    5.766703] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 20                 00 mBm)
[    5.766706] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 20                 00 mBm)
[    5.766709] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 20                 00 mBm)
[    5.943238] psmouse serio1: synaptics: Touchpad model: 1, fw: 6.5, id: 0x1c0b                 1, caps: 0xa04751/0xa00000/0x0
[    5.976130] Console: switching to colour frame buffer device 170x48
[    5.981041] fb0: inteldrmfb frame buffer device
[    5.981044] drm: registered panic notifier
[    5.992725] acpi device:03: registered as cooling_device2
[    5.993539] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNX                 VIDEO:00/input/input12
[    5.993767] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[    5.994909] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    6.017614] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/seri                 o1/input/input13
[    6.549915] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    6.732788] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    7.372316] EXT3-fs (sda6): using internal journal
[    7.608730] kjournald starting.  Commit interval 5 seconds
[    7.720833] EXT3-fs (sda5): using internal journal
[    7.720841] EXT3-fs (sda5): mounted filesystem with ordered data mode
[    8.297861] kjournald starting.  Commit interval 5 seconds
[    8.299432] EXT3-fs (sda10): using internal journal
[    8.299438] EXT3-fs (sda10): mounted filesystem with ordered data mode
[    8.790626] kjournald starting.  Commit interval 5 seconds
[    8.790840] EXT3-fs (sda8): using internal journal
[    8.790845] EXT3-fs (sda8): mounted filesystem with ordered data mode
[    9.119883] kjournald starting.  Commit interval 5 seconds
[    9.120100] EXT3-fs (sda9): using internal journal
[    9.120104] EXT3-fs (sda9): mounted filesystem with ordered data mode
[  129.652029] type=1400 audit(1356798513.194:11): apparmor="STATUS" operation="                 profile_replace" name="/sbin/dhclient" pid=748 comm="apparmor_parser"
[  129.652555] type=1400 audit(1356798513.198:12): apparmor="STATUS" operation="                 profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=748 co                 mm="apparmor_parser"
[  129.652853] type=1400 audit(1356798513.198:13): apparmor="STATUS" operation="                 profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=748 comm="a                 pparmor_parser"
[  129.679367] type=1400 audit(1356798513.222:14): apparmor="STATUS" operation="                 profile_load" name="/usr/sbin/mysqld" pid=749 comm="apparmor_parser"
[  129.704139] type=1400 audit(1356798513.250:15): apparmor="STATUS" operation="                 profile_load" name="/usr/sbin/tcpdump" pid=751 comm="apparmor_parser"
[  130.061227] type=1400 audit(1356798513.606:16): apparmor="STATUS" operation="                 profile_replace" name="/usr/sbin/mysqld" pid=805 comm="apparmor_parser"
[  207.667529] init: network-interface (wlan0) pre-start process (544) killed by                  TERM signal
[  208.012466] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  208.936564] wlan0: direct probe to 58:98:35:e9:0e:07 (try 1/3)
[  209.136074] wlan0: direct probe to 58:98:35:e9:0e:07 (try 2/3)
[  209.140551] wlan0: direct probe responded
[  209.140603] wlan0: authenticate with 58:98:35:e9:0e:07 (try 1)
[  209.146071] wlan0: authenticated
[  209.153516] wlan0: associate with 58:98:35:e9:0e:07 (try 1)
[  209.156957] wlan0: RX AssocResp from 58:98:35:e9:0e:07 (capab=0x411 status=0                  aid=2)
[  209.156960] wlan0: associated
[  209.156965] wlan0: moving STA 58:98:35:e9:0e:07 to state 1
[  209.156967] wlan0: moving STA 58:98:35:e9:0e:07 to state 2
[  209.165179] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  209.234736] wlan0: moving STA 58:98:35:e9:0e:07 to state 3
[  212.256028] wlan0: deauthenticated from 58:98:35:e9:0e:07 (Reason: 2)
[  212.271951] wlan0: moving STA 58:98:35:e9:0e:07 to state 2
[  212.271954] wlan0: moving STA 58:98:35:e9:0e:07 to state 1
[  212.271956] wlan0: moving STA 58:98:35:e9:0e:07 to state 0
[  212.276162] cfg80211: All devices are disconnected, going to restore regulato                 ry settings
[  212.276168] cfg80211: Restoring regulatory settings
[  212.276176] cfg80211: Calling CRDA to update world regulatory domain
[  212.280675] cfg80211: Ignoring regulatory request Set by core since the drive                 r uses its own custom regulatory domain
[  212.280718] cfg80211: World regulatory domain updated:
[  212.280720] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gai                 n, max_eirp)
[  212.280723] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 20                 00 mBm)
[  212.280727] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 20                 00 mBm)
[  212.280730] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 20                 00 mBm)
[  212.280733] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 20                 00 mBm)
[  212.280736] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 20                 00 mBm)
[  213.030935] cfg80211: Found new beacon on frequency: 2467 MHz (Ch 12) on phy0
[  213.246877] wlan0: authenticate with 58:98:35:e9:0e:07 (try 1)
[  213.444052] wlan0: authenticate with 58:98:35:e9:0e:07 (try 2)
[  213.446036] wlan0: authenticated
[  213.446208] wlan0: associate with 58:98:35:e9:0e:07 (try 1)
[  213.452521] wlan0: RX ReassocResp from 58:98:35:e9:0e:07 (capab=0x411 status=                 0 aid=2)
[  213.452524] wlan0: associated
[  213.452528] wlan0: moving STA 58:98:35:e9:0e:07 to state 1
[  213.452530] wlan0: moving STA 58:98:35:e9:0e:07 to state 2
[  216.471756] wlan0: deauthenticated from 58:98:35:e9:0e:07 (Reason: 2)
[  216.478739] wlan0: moving STA 58:98:35:e9:0e:07 to state 1
[  216.478742] wlan0: moving STA 58:98:35:e9:0e:07 to state 0
[  216.479024] cfg80211: All devices are disconnected, going to restore regulato                 ry settings
[  216.479029] cfg80211: Restoring regulatory settings
[  216.479037] cfg80211: Calling CRDA to update world regulatory domain
[  216.483417] cfg80211: Ignoring regulatory request Set by core since the drive                 r uses its own custom regulatory domain
[  216.483465] cfg80211: World regulatory domain updated:
[  216.483468] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gai                 n, max_eirp)
[  216.483471] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 20                 00 mBm)
[  216.483475] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 20                 00 mBm)
[  216.483478] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 20                 00 mBm)
[  216.483481] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 20                 00 mBm)
[  216.483484] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 20                 00 mBm)
[  217.450850] wlan0: authenticate with 58:98:35:e9:0e:07 (try 1)
[  217.453390] wlan0: authenticated
[  217.453556] wlan0: associate with 58:98:35:e9:0e:07 (try 1)
[  217.459896] wlan0: RX ReassocResp from 58:98:35:e9:0e:07 (capab=0x411 status=                 0 aid=2)
[  217.459900] wlan0: associated
[  217.459903] wlan0: moving STA 58:98:35:e9:0e:07 to state 1
[  217.459905] wlan0: moving STA 58:98:35:e9:0e:07 to state 2
[  218.573515] wlan0: moving STA 58:98:35:e9:0e:07 to state 3
[  219.744029] wlan0: no IPv6 routers present
[ 1712.124126] wlan0: moving STA 58:98:35:e9:0e:07 to state 2
[ 1712.124130] wlan0: moving STA 58:98:35:e9:0e:07 to state 1
[ 1712.124132] wlan0: moving STA 58:98:35:e9:0e:07 to state 0
[ 1712.144202] cfg80211: All devices are disconnected, going to restore regulato                 ry settings
[ 1712.144255] cfg80211: Restoring regulatory settings
[ 1712.144265] cfg80211: Calling CRDA to update world regulatory domain
[ 1712.148533] cfg80211: Ignoring regulatory request Set by core since the drive                 r uses its own custom regulatory domain
[ 1712.148576] cfg80211: World regulatory domain updated:
[ 1712.148578] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gai                 n, max_eirp)
[ 1712.148582] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 20                 00 mBm)
[ 1712.148585] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 20                 00 mBm)
[ 1712.148588] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 20                 00 mBm)
[ 1712.148591] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 20                 00 mBm)
[ 1712.148594] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 20                 00 mBm)
[ 1713.098800] wlan0: authenticate with 58:98:35:e9:0e:07 (try 1)
[ 1713.100781] wlan0: authenticated
[ 1713.100946] wlan0: associate with 58:98:35:e9:0e:07 (try 1)
[ 1713.106210] wlan0: RX ReassocResp from 58:98:35:e9:0e:07 (capab=0x411 status=                 0 aid=2)
[ 1713.106214] wlan0: associated
[ 1713.106217] wlan0: moving STA 58:98:35:e9:0e:07 to state 1
[ 1713.106220] wlan0: moving STA 58:98:35:e9:0e:07 to state 2
[ 1714.118758] wlan0: moving STA 58:98:35:e9:0e:07 to state 3
robert@camserver3:~$

```


im try to find the module number by
i google "bluetooth standard" and come up with IEEE and 80215
so i google "ubuntu IEEE 80215" and it's bluetooth and wifi, it's all on the same stack or something equally confounding...

thanks for yor help

---

### Post by audiomick on 2012-12-29
> **robertthebruce said:**
> 
below is dmesg and lshw


The interesting bit of lshw about your network stuff is apparently cut off. That output starts somewhere in the middle, and the network stuff is usually nearer the top.

Try
```
sudo lshw -C network
```

the option -C restricts it to the subsequently named hardware class. Much shorter output.

---

### Post by robertthebruce on 2012-12-29
from [http://askubuntu.com/questions/67758/how-can-i-deactivate-bluetooth-on-system-startup](http://askubuntu.com/questions/67758/how-can-i-deactivate-bluetooth-on-system-startup)



untill i work out the bt module...i have tried

installed rfkill
```
sudo nano /etc/rc.local and add this before line with exit 0:
  rfkill block bluetooth
```

didnt work

---

### Post by robertthebruce on 2012-12-31
undone all that...


no bluetooth here
```
robert@camserver3:~$ sudo lshw -short
H/W path           Device      Class       Description
======================================================
                               system      Notebook
/0                             bus         3069
/0/0                           memory      1MiB BIOS
/0/f                           processor   Celeron(R) Dual-Core CPU       T3100  @ 1.90GHz
/0/f/10                        memory      1MiB L2 cache
/0/f/12                        memory      32KiB L1 cache
/0/f/1.1                       processor   Logical CPU
/0/f/1.2                       processor   Logical CPU
/0/11                          memory      32KiB L1 cache
/0/13                          memory      2GiB System Memory
/0/13/0                        memory      2GiB SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
/0/13/1                        memory      SODIMM [empty]
/0/100                         bridge      Mobile 4 Series Chipset Memory Controller Hub
/0/100/2                       display     Mobile 4 Series Chipset Integrated Graphics Controller
/0/100/2.1                     display     Mobile 4 Series Chipset Integrated Graphics Controller
/0/100/1a                      bus         82801I (ICH9 Family) USB UHCI Controller #4
/0/100/1a.1                    bus         82801I (ICH9 Family) USB UHCI Controller #5
/0/100/1a.7                    bus         82801I (ICH9 Family) USB2 EHCI Controller #2
/0/100/1b                      multimedia  82801I (ICH9 Family) HD Audio Controller
/0/100/1c                      bridge      82801I (ICH9 Family) PCI Express Port 1
/0/100/1c/0        wlan0       network     AR9285 Wireless Network Adapter (PCI-Express)
/0/100/1c.1                    bridge      82801I (ICH9 Family) PCI Express Port 2
/0/100/1c.1/0      eth0        network     RTL8101E/RTL8102E PCI Express Fast Ethernet controller
/0/100/1d                      bus         82801I (ICH9 Family) USB UHCI Controller #1
/0/100/1d.1                    bus         82801I (ICH9 Family) USB UHCI Controller #2
/0/100/1d.2                    bus         82801I (ICH9 Family) USB UHCI Controller #3
/0/100/1d.3                    bus         82801I (ICH9 Family) USB UHCI Controller #6
/0/100/1d.7                    bus         82801I (ICH9 Family) USB2 EHCI Controller #1
/0/100/1e                      bridge      82801 Mobile PCI Bridge
/0/100/1f                      bridge      ICH9M LPC Interface Controller
/0/100/1f.2        scsi0       storage     82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [A
/0/100/1f.2/0      /dev/sda    disk        320GB TOSHIBA MK3256GS
/0/100/1f.2/0/1    /dev/sda1   volume      100MiB Windows NTFS volume
/0/100/1f.2/0/2    /dev/sda2   volume      39GiB Windows NTFS volume
/0/100/1f.2/0/3    /dev/sda3   volume      258GiB Extended partition
/0/100/1f.2/0/3/5  /dev/sda5   volume      94MiB Linux filesystem partition
/0/100/1f.2/0/3/6  /dev/sda6   volume      1059MiB Linux filesystem partition
/0/100/1f.2/0/3/7  /dev/sda7   volume      2118MiB Linux swap / Solaris partition
/0/100/1f.2/0/3/8  /dev/sda8   volume      4237MiB Linux filesystem partition
/0/100/1f.2/0/3/9  /dev/sda9   volume      7416MiB Linux filesystem partition
/0/100/1f.2/0/3/a  /dev/sda10  volume      244GiB Linux filesystem partition
/0/100/1f.2/1      /dev/cdrom  disk        DVD RW AD-7561S
/0/100/1f.3                    bus         82801I (ICH9 Family) SMBus Controller
/0/100/1f.6                    generic     82801I (ICH9 Family) Thermal Subsystem
/1                             power       EV06047
robert@camserver3:~$

```

sudo lshw > hardware.txt

no metntion of bluetooth there
```

[    0.961419] Cannot allocate resource for EISA slot 4
[    0.961423] Cannot allocate resource for EISA slot 5
[    0.961428] Cannot allocate resource for EISA slot 6
[    0.961432] Cannot allocate resource for EISA slot 7
[    0.961437] Cannot allocate resource for EISA slot 8
[    0.961441] EISA: Detected 0 cards.
[    0.961456] cpufreq-nforce2: No nForce2 chipset.
[    0.961535] cpuidle: using governor ladder
[    0.961660] cpuidle: using governor menu
[    0.961664] EFI Variables Facility v0.08 2004-May-17
[    0.961988] TCP cubic registered
[    0.962145] NET: Registered protocol family 10
[    0.962884] NET: Registered protocol family 17
[    0.962892] Registering the dns_resolver key type
[    0.962919] Using IPI No-Shortcut mode
[    0.963085] PM: Hibernation image not present or could not be loaded.
[    0.963104] registered taskstats version 1
[    0.970652]   Magic number: 8:230:337
[    0.970696] thermal thermal_zone0: hash matches
[    0.970708] tty tty58: hash matches
[    0.970786] rtc_cmos 00:04: setting system clock to 2012-12-31 15:19:20 UTC (1356967160)
[    0.970826] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.970831] EDD information not available.
[    0.971212] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.268051] usb 2-4: new high-speed USB device number 2 using ehci_hcd
[    1.372057] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.372933] ata1.00: ATA-8: TOSHIBA MK3256GSY, LH013C, max UDMA/100
[    1.372940] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.373919] ata1.00: configured for UDMA/100
[    1.374108] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK3256GS LH01 PQ: 0 ANSI: 5
[    1.374282] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.374314] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.374342] sd 0:0:0:0: [sda] Write Protect is off
[    1.374349] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.374373] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.500087]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 sda8 sda9 sda10 >
[    1.501119] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.660050] usb 4-1: new low-speed USB device number 2 using uhci_hcd
[    1.864074] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.879883] ata2.00: ATAPI: hp      DVD RW AD-7561S, AH73, max UDMA/100
[    1.894981] ata2.00: configured for UDMA/100
[    1.898127] scsi 1:0:0:0: CD-ROM            hp       DVD RW AD-7561S  AH73 PQ: 0 ANSI: 5
[    1.902765] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.902774] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.902943] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.903044] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.220077] ata5: SATA link down (SStatus 0 SControl 300)
[    2.540059] ata6: SATA link down (SStatus 0 SControl 300)
[    2.540138] Freeing unused kernel memory: 716k freed
[    2.540455] Write protecting the kernel text: 5628k
[    2.540525] Write protecting the kernel read-only data: 2328k
[    2.562172] udevd[97]: starting version 175
[    2.676625] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.676666] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.676705] r8169 0000:03:00.0: setting latency timer to 64
[    2.676777] r8169 0000:03:00.0: irq 43 for MSI/MSI-X
[    2.677416] r8169 0000:03:00.0: eth0: RTL8102e at 0xf8038000, 00:26:9e:f0:54:99, XID 04c00000 IRQ 43
[    2.683562] input: USB USB Keykoard as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input5
[    2.683692] generic-usb 0003:1A2C:0002.0001: input,hidraw0: USB HID v1.10 Keyboard [USB USB Keykoard] on usb-0000:00:1a.1-1/input0
[    2.699748] input: USB USB Keykoard as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.1/input/input6
[    2.700393] generic-usb 0003:1A2C:0002.0002: input,hidraw1: USB HID v1.10 Device [USB USB Keykoard] on usb-0000:00:1a.1-1/input1
[    2.700434] usbcore: registered new interface driver usbhid
[    2.700439] usbhid: USB HID core driver
[    3.226014] kjournald starting.  Commit interval 5 seconds
[    3.226053] EXT3-fs (sda6): mounted filesystem with ordered data mode
[    3.759569] init: ureadahead main process (257) terminated with status 5
[    4.122506] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.175789] Adding 2168828k swap on /dev/sda7.  Priority:-1 extents:1 across:2168828k
[    4.271524] udevd[333]: starting version 175
[    4.469099] lp: driver loaded but no devices found
[    4.628995] wmi: Mapper loaded
[    4.645752] cfg80211: Calling CRDA to update world regulatory domain
[    4.719574] [drm] Initialized drm 1.1.0 20060810
[    4.812575] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    4.812644] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[    4.812687] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[    5.040672] ath9k 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.040691] ath9k 0000:02:00.0: setting latency timer to 64
[    5.092111] ath: EEPROM regdomain: 0x6a
[    5.092113] ath: EEPROM indicates we should expect a direct regpair map
[    5.092117] ath: Country alpha2 being used: 00
[    5.092118] ath: Regpair used: 0x6a
[    5.092123] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    5.092126] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.092129] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    5.092132] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.092134] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    5.092137] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.092139] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    5.092142] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.092144] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    5.092147] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.092149] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    5.092152] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.092155] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    5.092158] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.092160] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    5.092163] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.092165] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    5.092168] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.092170] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    5.092173] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.092176] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    5.092178] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.092181] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[    5.092183] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.092186] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[    5.092189] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    5.092191] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    5.093987] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[    5.162545] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[    5.163396] Registered led device: ath9k-phy0
[    5.163407] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xf8660000, irq=16
[    5.165792] HDMI status: Codec=3 Pin=3 Presence_Detect=0 ELD_Valid=0
[    5.166568] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[    5.166841] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[    5.167043] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    5.167844] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.167853] i915 0000:00:02.0: setting latency timer to 64
[    5.200161] i915 0000:00:02.0: irq 45 for MSI/MSI-X
[    5.200169] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    5.200171] [drm] Driver supports precise vblank timestamp query.
[    5.200226] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    5.207980] input: HP WMI hotkeys as /devices/virtual/input/input10
[    5.265028] fixme: max PWM is zero.
[    5.549949] Linux video capture interface: v2.00
[    5.588778] uvcvideo: Found UVC 1.00 device HP Webcam-101 (0408:0f41)
[    5.592665] input: HP Webcam-101 as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input11
[    5.592761] usbcore: registered new interface driver uvcvideo
[    5.592763] USB Video Class driver (1.1.1)
[    5.631217] fbcon: inteldrmfb (fb0) is primary device
[    5.685624] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[    5.685629] cfg80211: World regulatory domain updated:
[    5.685631] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    5.685634] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.685637] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    5.685640] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    5.685642] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.685645] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.717514] type=1400 audit(1356931165.243:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=501 comm="apparmor_parser"
[    5.717526] type=1400 audit(1356931165.243:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=523 comm="apparmor_parser"
[    5.718050] type=1400 audit(1356931165.243:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=501 comm="apparmor_parser"
[    5.718080] type=1400 audit(1356931165.243:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=523 comm="apparmor_parser"
[    5.718337] type=1400 audit(1356931165.243:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=501 comm="apparmor_parser"
[    5.718383] type=1400 audit(1356931165.243:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=523 comm="apparmor_parser"
[    5.719125] type=1400 audit(1356931165.243:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=502 comm="apparmor_parser"
[    5.720381] type=1400 audit(1356931165.247:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=502 comm="apparmor_parser"
[    5.720686] type=1400 audit(1356931165.247:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=502 comm="apparmor_parser"
[    5.909699] Console: switching to colour frame buffer device 170x48
[    5.914801] fb0: inteldrmfb frame buffer device
[    5.914804] drm: registered panic notifier
[    5.945978] acpi device:03: registered as cooling_device2
[    5.947017] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input12
[    5.947216] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[    5.947635] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    6.040422] psmouse serio1: synaptics: Touchpad model: 1, fw: 6.5, id: 0x1c0b1, caps: 0xa04751/0xa00000/0x0
[    6.109233] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input13
[    6.366173] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    6.684808] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    7.199538] EXT3-fs (sda6): using internal journal
[    7.308176] kjournald starting.  Commit interval 5 seconds
[    7.308368] EXT3-fs (sda5): using internal journal
[    7.308373] EXT3-fs (sda5): mounted filesystem with ordered data mode
[    7.988975] kjournald starting.  Commit interval 5 seconds
[    7.990544] EXT3-fs (sda10): using internal journal
[    7.990549] EXT3-fs (sda10): mounted filesystem with ordered data mode
[    8.406754] kjournald starting.  Commit interval 5 seconds
[    8.406978] EXT3-fs (sda8): using internal journal
[    8.406983] EXT3-fs (sda8): mounted filesystem with ordered data mode
[    8.885567] kjournald starting.  Commit interval 5 seconds
[    8.885815] EXT3-fs (sda9): using internal journal
[    8.885820] EXT3-fs (sda9): mounted filesystem with ordered data mode
[  129.401515] type=1400 audit(1356931288.927:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=756 comm="apparmor_parser"
[  129.402052] type=1400 audit(1356931288.927:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=756 comm="apparmor_parser"
[  129.402345] type=1400 audit(1356931288.927:13): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=756 comm="apparmor_parser"
[  129.428817] type=1400 audit(1356931288.955:14): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=757 comm="apparmor_parser"
[  129.453590] type=1400 audit(1356931288.979:15): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=759 comm="apparmor_parser"
[  129.868806] type=1400 audit(1356931289.395:16): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=815 comm="apparmor_parser"
[  175.665289] init: network-interface (wlan0) pre-start process (546) killed by TERM signal
[  175.892196] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  176.815588] wlan0: authenticate with 58:98:35:e9:0e:07 (try 1)
[  176.819354] wlan0: authenticated
[  176.826900] wlan0: associate with 58:98:35:e9:0e:07 (try 1)
[  176.830353] wlan0: RX AssocResp from 58:98:35:e9:0e:07 (capab=0x411 status=0 aid=3)
[  176.830357] wlan0: associated
[  176.830360] wlan0: moving STA 58:98:35:e9:0e:07 to state 1
[  176.830363] wlan0: moving STA 58:98:35:e9:0e:07 to state 2
[  176.837443] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  177.841807] wlan0: moving STA 58:98:35:e9:0e:07 to state 3
[  187.592026] wlan0: no IPv6 routers present

```

---

### Post by robertthebruce on 2012-12-31
solved - upgraded my thinking to ext4 with everything in / and it worked out of box

---

