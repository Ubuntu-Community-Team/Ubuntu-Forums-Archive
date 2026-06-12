---
title: "Install Ubuntu and manual partitioning"
date: 2023-06-09
forum: New to Ubuntu
---

### Post by m-elodie on 2023-06-09
Hello!

I'm trying to fresh install Ubuntu 23.04 on a new disk.
Ideally I would like to use 4 partitions like I did last time, but it doesn't go well.
What I did until now is that I use 2 disks. One for the current one, and one for the previous version.
So what I would like to do is to install over the existing partitions of Ubuntu 21.

When I start and go to manual partitioning (Manual but using the GUI), I have:
sda1 vfat 976 MB 
sda2 swap 31GB // I read somewhere I need twice the RAM amount. Not sure why it's 31, it should be 32 but it works.
sda3 ext4 / 122GB. Ubuntu 23,04
sda3 ext4 /home 1TB

So the idea would be to format only sda3.

The problem: The "next" button is grayed out, no way to proceed.

Any idea of the reason?

Next question:
I tried to restart and make a new partition table (without save and proceed).
When creating a new partition, I have only 4 options: Ext4, XFS, Btrfs and swap. How do I create an EFI partition?
In the past, I could choose "efi" for the first one, and it was pretty straight forward.
Once created, using "change" provides more configs, but not efi.

Thanks for your help.

Elodie

---

### Post by guiverc on 2023-06-09
You didn't provide specifics as to what Ubuntu 23.04 you're actually using.

- Ubuntu 23.04 Server uses the `subiquity` installer
- Ubuntu 23.04 Desktop's *default* ISO uses the `ubuntu-desktop-installer`
- Ubuntu 23.04 Desktop's *legacy* or *alternate *ISO uses the `ubiquity` installer that was default on prior releases of Ubuntu Desktop

The *NEXT* button is usually *greyed out* only if something hasn't been specified, or a *problem* has been detected and you cannot proceed, however you've not yet indicated which Ubuntu 23.04 product you're using, and if it's a desktop system - which ISO you are using (*given that dictates which installer you are asking about*). 

FYI:  It's common for no *swap partition* to be used today; as *swapfiles* are in most cases easier to manage, so why opt for *swap partition *?

---

### Post by m-elodie on 2023-06-09
Hello!

Thanks for your reply.
I'm using Ubuntu iso file downloaded directly from ubuntu.com
The filename is ubuntu-23.04-desktop-amd64.iso
As for using a swap file, let's state it frankly: I don't know. All the tutorials I have read or seen
on youtube tell me I need a swap file, and that's the only reason I made one. And I don't have
enough knowledge to ski off-track.

Elodie

---

### Post by Dennis N on 2023-06-09
Assuming you show the old partitioning, you will need to select sda3, press the "change" button, and fill in (again) the details about sda3 for the new install. The installer wouldn't assume the old root location will be the new root location. The same is true for the separate home partition. sda1 would probably automatically be used again for the ESP if the boot and esp flags are set. You also need to specify the boot loader location at the bottom.

A swap partition is optional. Ubuntu automatically makes a swap file if there is no swap partition, and you don't need to specify it's size when installing. 32G is pretty large for swap if you have that much RAM available. If I need to make one, I only use 4G.

---

### Post by guiverc on 2023-06-09
> **m-elodie said:**
> Hello!

Thanks for your reply.
I'm using Ubuntu iso file downloaded directly from ubuntu.com
The filename is ubuntu-23.04-desktop-amd64.iso
As for using a swap file, let's state it frankly: I don't know. All the tutorials I have read or seen
on youtube tell me I need a swap file, and that's the only reason I made one. And I don't have
enough knowledge to ski off-track.

Elodie

Your ISO name tells me you're using Ubuntu 23.04 **Desktop**, and used the *`ubuntu-desktop-installer`* installer, if you want to use the installer you used for prior releases of Ubuntu Desktop, that is available too from [https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)   (*it's the LEGACY Desktop Installer download option*)

SWAP can be achieved in multiple ways; either via SWAP FILE, or as SWAP PARTITION.

When it's a FILE, it'll just use some of a disk partition that is used by other things (such as your actual install, your data files etc), and being a FILE its size can be readily adjusted (ie. increasing or decreasing size) even without a reboot too most of the time.

When it's a PARTITION, it's a reserved part of your disk that you've planned ahead of time as to what size is required & don't plan on adjusting it, as its not easily changed (*requiring you to shutdown, boot live media & modify partitions potentially impacting all OSes on the drive*).

Your initial post made the decision to use SDA2 or a SWAP PARTITION.  In contrast your last comment talked only about a SWAP FILE (which wouldn't be stored on SDA2 but a shared partition as a file), Swap files & partitions are different ways to achieve the same thing, ie. give your system SWAP capacity.

You can use both SWAP PARTITION & SWAP FILE, but unless you have reason to use swap partition, I'd recommend using only SWAP FILE as it's much easier to manage. 

Dennis N. has already suggested most of this.

---

### Post by m-elodie on 2023-06-09
Hello!

Thanks for your replies.

> 
[COLOR=#000000] 32G is pretty large for swap if you have that much RAM available.
[/COLOR][COLOR=#000000]

I have read somewhere that I need twice the RAM amount.

[/COLOR]> [COLOR=#000000]Assuming you show the old partitioning, you will need to select sda3, press the "change" button, and fill in (again) the details
about sda3 for the new install. The installer wouldn't assume the old root location will be the new root location. The same is true
for the separate home partition. sda1 would probably automatically be used again for the ESP if the boot and esp flags are set.
You also need to specify the boot loader location at the bottom.
[/COLOR][COLOR=#000000]

I did all what you say (button "change", etc) as documented on the net. What doesn't change is that the "next" button
stays gray.

Beside this, Ubuntu is supposed to be user friendly, and I don't understand why I should re-partition a disk that used
to work. I should just select the partition(s) I want to format (mostly the root partition), and let it go. I don't have this option.

By the way, I just downloaded [/COLOR]ubuntu-23.04-desktop-legacy-amd64.iso
[COLOR=#000000]What is it exactly? Is it a complete Ubuntu OS? The reason of this question is that its 1GB less than the other version.
I guess the legacy installer cannot be 1GB less than the new one, right?

Elodie.

[/COLOR]

---

### Post by guiverc on 2023-06-09
> **m-elodie said:**
> [COLOR=#000000]

By the way, I just downloaded [/COLOR]ubuntu-23.04-desktop-legacy-amd64.iso
[COLOR=#000000]What is it exactly? Is it a complete Ubuntu OS? The reason of this question is that its 1GB less than the other version.
I guess the legacy installer cannot be 1GB less than the new one, right?

Elodie.

[/COLOR]

The *alternate* or LEGACY Desktop installer is the same as the *primary* ISO except for installer.

The *legacy* installer cannot upgrade itself if fixes are made (*the primary installer can!*) so there is some sizable/notable differences between the installers (*they also use different type of instructions with regard seeing/autoinstall scripts*) but the two installs both install the same product, the difference being how they accomplish this.

FYI:  The new *flutter* installer requires extra infrastructure to operate when contrasted with the  older installer, which of course needs to exist on the ISO. I'm not aware of any features being removed from the `ubiquity` installer for this release over prior releases, but beyond well documented differences in the new install infrastructure & *like* changes, I'm not aware of any new features though either beyond the changed  *preseed* options of the newer installer (*though there is great potential for more to be added to the new installer which wasn't [easily] possible with the older installer*).

---

### Post by TheFu on 2023-06-10
> **m-elodie said:**
>  
I have read somewhere that I need twice the RAM amount.

Ignore that advice.  It was good advice in the 1990s, when we had 32MB of RAM and 80MB HDDs.  It hasn't applied in at least 2 decades.
Swap should be large enough to prevent OOM crashes and allow the user of a single user system to "feel" the system getting slow so they can close some programs.  Typically, just closing the browser will solve any tight memory issues, thanks to the bloat that is a modern browser today.

For a desktop, I think there's only 1 correct answer for swap size.  4.1GB.  Period.  This works for computers with just 2GB of RAM (I have a chromebook with that) and for systems with 32GB+ of RAM like 2 of my desktops.  For a server, the answer is for swap to be as small as possible, but still have some so the kernel optimizations that having some swap allows are enabled.  RAM is cheap.  Having a system using lots of RAM and very little swap is the ideal situation.

For example:
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           30Gi        23Gi       853Mi        93Mi       6.3Gi       6.6Gi
Swap:         4.1Gi       1.0Gi       3.1Gi
```

Here's an overview of that system's hardware:
```
$ inxi -bz
System:    Kernel: 5.15.0-73-generic x86_64 bits: 64 Desktop: FVWM2 2.6.8
           Distro: Ubuntu 20.04.6 LTS (Focal Fossa) 
Machine:   Type: Desktop Mobo: ASUSTeK model: ROG STRIX B450-F GAMING v: Rev 1.xx 
           serial: <filter> UEFI: American Megatrends v: 5003 date: 02/03/2023 
CPU:       6-Core: AMD Ryzen 5 5600G with Radeon Graphics type: MT MCP speed: 4199 MHz 
           min/max: 1400/4200 MHz 
Graphics:  Device-1: AMD driver: amdgpu v: kernel 
           Display: server: X.Org 1.20.13 driver: amdgpu resolution: 1920x1200~60Hz 
           OpenGL: renderer: llvmpipe (LLVM 12.0.0 256 bits) v: 4.5 Mesa 21.2.6 
Network:   Device-1: Intel I211 Gigabit Network driver: igb 
           Device-2: Intel 82575GB Gigabit Network driver: igb 
           Device-3: Intel 82575GB Gigabit Network driver: igb 
           Device-4: Intel 82575GB Gigabit Network driver: igb 
           Device-5: Intel 82575GB Gigabit Network driver: igb 
Drives:    Local Storage: total: 37.13 TiB used: 24.78 TiB (66.7%) 
Info:      Processes: 694 Uptime: 6d 23h 14m Memory: 30.72 GiB used: 25.83 GiB (84.1%) 
           Shell: bash inxi: 3.0.38 

```
It has 32GB of RAM, but the iGPU has stolen 2G for video needs.  Most of the RAM is used by virtual machines and linux containers that are running.

I would setup my system different from what you are attempting.  I certainly wouldn't make / be more than 35G.  Just because you have extra, unused storage, doesn't mean it should be allocated now.  In my nearly 30 yrs as a Unix/Linux admin, I've never, ever, not once, properly setup the storage for a computer that was correct a year later.  So, I've taken to setting up storage in a way that is easy to modify (i.e. increase) where that needs to happen.  A beginner isn't ready to use the methods I use, but you could use simple partitions, carefully placed on the HDD to allow easy expansion at the end without shifting any other partitions. Shifting partitions that contain data is a complex process, best avoided.

If I were you, trying to setup storage for an install, I'd do that in a "Try Ubuntu" ISO boot environment, using gparted on the target storage device.  Then it is pretty easy to leave unused areas between partitions to allow extensions.  BTW, set a label on each partition, so when you are in the installer, you'll know what is planned to be used for each purpose.
```
                          Whole Drive
+------------------------------------------------------------------------------------+
|                                                                                    |
|  +---+   +--------------+          +---------------------+                     +-+ |
|  |   |   |              |          |                     |                     | | |
|  |   |   |              |          |                     |                     |S| |
|  |   |   |              |          |                     |                     |w| |
|  | E |   |              |          |                     |                     |a| |
|  | F |   |    OS        |          |      Home           |                     |p| |
|  | I |   |              |          |                     |                     | | |
|  |   |   |              |          |                     |                     | | |
|  |   |   |              |          |                     |                     | | |
|  |   |   |              |          |                     |                     | | |
|  |   |   |              |          |                     |                     | | |
|  +---+   +--------------+          +---------------------+                     +-+ |
|                                                                                    |
+------------------------------------------------------------------------------------+

```
Areas that aren't inside boxes are empty. So between the OS and Home partitions would be 20G+ of unused, unallocated, space.  Haven't unallocated space provides flexibility in the future.  On an SSD, it can also extend the lifespan, since unused cells are available for wear leveling by the SSD controller.

Here's my actual storage setup:
```
NAME                              SIZE TYPE FSAVAIL FSUSE% FSTYPE      MOUNTPOINT
nvme0n1                         931.5G disk                            
&#9500;&#9472;nvme0n1p1                         1M part                ext2        
&#9500;&#9472;nvme0n1p2                        50M part   43.9M    12% vfat        /boot/efi
&#9500;&#9472;nvme0n1p3                       700M part  342.6M    42% ext4        /boot
&#9492;&#9472;nvme0n1p4                     930.8G part                LVM2_member 
  &#9500;&#9472;vg01-swap01                   4.1G lvm                 swap        [SWAP]
  &#9500;&#9472;vg01-root01                    35G lvm      26G    19% ext4        /
  &#9500;&#9472;vg01-var01                     20G lvm    16.6G    10% ext4        /var
  &#9500;&#9472;vg01-tmp01                      4G lvm     3.6G     1% ext4        /tmp
  &#9500;&#9472;vg01-home01                    10G lvm     4.2G    52% ext4        /home
  &#9500;&#9472;vg01-libvirt--01              137G lvm     2.8G    98% ext4        /var/lib/libvirt
  &#9492;&#9472;vg01-lxd--containers--01       30G lvm                           
```
The system has a 1TB SSD, but you can see only about 250G is allocated for use.  There's actually 690.68GB free of that 930.78GB partition.  My /var is larger than most people will need and I added some specific storage for a huge virtual machine directly to /var/lib/libvirt/.

---

