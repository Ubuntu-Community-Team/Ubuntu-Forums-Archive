---
title: "Partition problem"
date: 2016-01-07
forum: New to Ubuntu
---

### Post by miner2 on 2016-01-07
Hello all,

I've just moved to Ubuntu and all is working fine except one issue...my partition is too small and I don't know exactly how to fix it. I worked out how to load up gparted and I have looked at all sorts of methods, but my problem seems different. (So I know how to load up gparted on a live USB, etc.).

So in the attached picture we have all the usual jazz - here it is opened in Ubuntu as normal and not on a live CD - but whereas in all the tutorials my unallocated space would be next to my drive, which I assume to be ext4 (?) in this one the Lenovo drive is between them and so I don't know how to repartition here. 

Simple, newbie, grandmother instructions welcome :D

---

### Post by Bucky Ball on 2016-01-07
Welcome. Not exactly sure what it is you want to do here, but you need to boot to a live session (install media> Try Ubuntu> Gparted) if you want to resize the Ubuntu / partition (sda8). 

No idea if you had a plan prior to hitting go, but this all looks a little random. You have no /swap partition and you should have (2Gb) as the last partition on the drive (or somewhere).

Also, what you refer to as 'drive' is Windows speak. We call them partitions. You have there the drive sda with partitions on it: sda*, etc. In this case, sda8 is your root or OS partition: /. 

Maybe you can spell out exactly what it is you are wanting to do here and we can let you know what's possible.

PS: Don't know what the partition labelled 'Lenovo' is, but if that is the Win partition, DON'T resize that with Ubuntu tools. Always use Win disk management tools for them, Linux tools for EXT* partitions.

---

### Post by miner2 on 2016-01-07
Hello and thanks. The problem is I picked up this laptop from a charity store just to play with so I don't really know what is on it. It boots to Windows 10 (what looks like an upgrade). I assume Lenovo might be something like a recovery drive, but then there are all the weird other ones (I'm going to leave them be). 

Sorry for the vagueness, this is all totally new to me (Windows user for 15 years!), so my hope was to work out how I could use the unallocated 97GB that is unallocated as extra space for sda8. But I don't know how to do this on gparted. When I look at guides for how to partition they assume the free space and the root drive are beside each other. But in my case they are not. 

Again, sorry for not being so clear here, but this is all new to me though I do try to sort these things out myself usually (god help me).

---

### Post by Bucky Ball on 2016-01-07
Your options are clear. The only way you are going to get the / partition and the free space together is to remove the 'Lenovo' partition. That's it. 

Why not just install Ubuntu to the 97Gb free space in the first place?

As I said, when installing, particularly with a dual-boot, it pays to sit down with a pen, paper and a beverage and figure out what the end result is in the analogue prior to diving into the digital. Not a bad idea reinstalling anyway. You need to add a /swap partition somewhere. You can do that with what you've got, but ...

Your other option is to make the 97Gb free space an NTFS data partition which can be shared between Ubuntu and Win and keep all your personal data there. Are you intending to use Win on this machine in any case? Have you booted into the Win install and created the recovery disks? If you do that you could safely wipe that 'Lenovo' partition and all is right with the world.

---

### Post by miner2 on 2016-01-07
Actually that sounds like it would work perfectly. This was just a case where I needed another eye to see the wood from the trees. Thank you.

---

### Post by Bucky Ball on 2016-01-07
sda1 looks like the Win recovery partition, sda2 is your EFI boot partition (DON'T go near that), sda3 and sda7 no idea what they are, the rest are self-explanatory.

Lenovo, don't know what that's about, but make a plan, give it a go, see what you come up with and let us know. As you've just got this machine I presume you have no valuable data to lose if things go pear-shaped, so good time to experiment and learn. Make the Win recovery disks when booted to Win prior to executing whatever plan you come up with so if you need to get the machine back to square one factory default you can.

Basically, for Ubuntu, you would need:

/ = 20Gb (if you are keeping personal data on a larger data partition);
/swap = 2Gb

That is the bare minimum. You can create whatever partitions you like and call them what you like, but you will find the ones above as default mountpoints when using 'Something Else' during install. 

If you are not intending to use a separate data partition for your personal data, then make the / partition as big as you can as your /home directory, where your personal data goes, will be inside /. 

You can also create a separate /home partition instead of the default /home directory inside /. This is handy if things go pear-shaped and you need to install the OS. All your personal data is in the /home partition, not the / partition, if you follow me. Yet another option. 

Good luck.

---

### Post by yancek on 2016-01-07
I'd suggest you read the info at the Ubuntu site below on dual booting windows/Ubuntu using UEFI before you begin.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by miner2 on 2016-01-07
OK so here is an update. First, yes I bought the laptop precisely so I could enter Linux without fear of losing data so that's no worry. I keep everything backed up on USB sticks as a rule (I'm an academic, lots of files!).

So what I did was back up OneKey, Lenovo's Windows recovery disc basically, deleted D: Lenovo. Loaded up the live Ubuntu and used gparted to expand ext4 although I didn't make it big enough. I'll expand it more now. The machine still seems a tad slow so I presume that is the main issue? I just need to make it bigger again? The 100GB did not seem to alter. Not sure what that means to be frank.

Regarding sda3 and 7 I am curious to know what the hell they are. Is there a way to somehow analyse them for fun? I am hoping they are super secret disks, but likely not. 

Again, I'm more playing with the machine, but I am very grateful for the help. I was a little worried I'd be crucified by hardcore Linux people.

---

### Post by Bucky Ball on 2016-01-07
Do you know the specs of the machine? It might be Ubuntu itself that's making it slow. How much RAM does it have? You could try a lighter flavour like Xubuntu or Lubuntu.

The size of the partition would have nothing to do with the speed of the install. Ubuntu has 75% headroom on that partition (you've only used a bit less than 5Gb of an 18Gb partition).

---

### Post by oldfred on 2016-01-07
These are the standard Windows partitions with UEFI.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

The standard partitions with Linux are / (root) and swap, but many add /home as a separate partition and/or add data partitions.

Vendors then have their own recovery partition(s) and Lenovo adds a hidden FAT32 with more efi boot files. It does not have the boot flag, so not really the ESP - efi system partition required for UEFI boot, but they somehow access those files from UEFI to boot Lenovo specific recovery, repair or updates. Only one FAT32 partition can have boot flag or make it the ESP per device or hard drive.

Your gparted screen shots show error or warning icons. That is normal for the Windows system reserved as it is unformatted.  But it may on main Windows install indicate that you still have Windows fast start up or always on hibernation set. That will cause issues dual booting, but turning it off will slow down boot, but not any other use of system.

If newer UEFI system, it should not be slow. What are specs? CPU, RAM, video card/chip?

 Fast Startup off
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

---

### Post by miner2 on 2016-01-07
Thanks for the info guys. It is likely just RAM, but here are the core specs:
[TABLE]
[TR]
[TD]Processor[/TD]
 [TD]Dual-core 1.86GHz Intel Celeron N2815[/TD]
 [/TR]
[TR]
[TD]RAM[/TD]
 [TD]4GB[/TD]
 [/TR]
[TR]
[TD]Memory slots (free)[/TD]
 [TD]2 (1)[/TD]
 [/TR]
[TR]
[TD]Max memory[/TD]
 [TD]8GB[/TD]
 [/TR]
[TR]
[TD]Size[/TD]
 [TD]380x262x24.7mm[/TD]
 [/TR]
[TR]
[TD]Weight[/TD]
 [TD]2.15kg[/TD]
 [/TR]
[TR]
[TD]Sound[/TD]
 [TD]Realtek HD Audio (3.5mm headset port)[/TD]
 [/TR]
[TR]
[TD]Pointing device[/TD]
 [TD]Touchpad[/TD]
[/TR]
[/TABLE]

According to reviews 'sluggish performance is normal' and it has even gotten 2/5 in some reviews!

I should add it's working pretty fine. You can hear it struggling a tad, but no crashes.

---

### Post by Bucky Ball on 2016-01-07
Well, that amount of RAM should run any flavour, but the processor is a little limp (although well above the stated minimum system requirements). Try [Xubuntu]("http://xubuntu.org/") in a live session and see if that runs faster (and it would be faster again when installed to HD). [Lubuntu]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu") would be a tad faster than that.

You may also need to install a graphics driver for that machine. If you do an update and check in 'Additional Drivers', what do you see? Anything related to graphics?

Open a terminal and:

```
sudo lshw -C video
```

Post the output here between code tags, please (see last link in my sig).

---

### Post by miner2 on 2016-01-07
I'll try those distros. I like the idea of a leaner distro. 

Graphics:

```

*-display               
       description: VGA compatible controller
       product: ValleyView Gen7
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0e
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:95 memory:90000000-903fffff memory:80000000-8fffffff ioport:3050(size=8)

```

---

### Post by Bucky Ball on 2016-01-07
Yea, a [minimal install]("https://help.ubuntu.com/community/Installation/MinimalCD") with xfce4 (as used by Xubuntu) is my main squeeze and has been for quite some time. On an i3 machine with 4Gb of RAM and an SSD so flies along. :)

I don't need bells and whistles.

---

### Post by oldfred on 2016-01-07
I install full Ubuntu but then install gnome-panel which has been called flashback or fallback.
That is the old menu system with gnome2, but using gnome3. And it is lighter weight.
My 2006 laptop with 1.5GB of RAM will not run Unity, but runs gnome-panel with metacity or 2d without issue.
You can try it easily just by adding gnome-panel and choosing it on reboot or even a logout & login.
       [http://ubuntuforums.org/showthread.php?t=2090021&p=12859103#post12859103](http://ubuntuforums.org/showthread.php?t=2090021&p=12859103#post12859103)
[https://mail.gnome.org/archives/gnome-announce-list/2013-September/msg00093.html](https://mail.gnome.org/archives/gnome-announce-list/2013-September/msg00093.html)
[http://packages.ubuntu.com/saucy/gnome-session-flashback](http://packages.ubuntu.com/saucy/gnome-session-flashback)
sudo apt-get install gnome-panel
On login screen click on logo/cog-wheel/star and choose 
[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)


 Both Unity and standard Gnome classic use Compiz as a WM, whereas Unity-2D and Gnome classic (no effects) use Metacity. 
Gnome shell and Cinnamon (which is a gnome-shell extension) use Mutter as a WM.
Gnome fallback Compiz vs Metacity, what's the diff?
[http://ubuntuforums.org/showthread.php?t=2250933](http://ubuntuforums.org/showthread.php?t=2250933)

---

### Post by miner2 on 2016-01-07
It's been running smooth all day. Thanks guys :)

---

