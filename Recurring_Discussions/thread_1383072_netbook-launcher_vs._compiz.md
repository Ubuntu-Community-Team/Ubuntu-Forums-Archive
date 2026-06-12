---
title: "netbook-launcher vs. compiz"
date: 2010-01-16
forum: Recurring Discussions
---

### Post by warfacegod on 2010-01-16
I am running a dual boot of 9.10 and 9.10 UNR. When using UNR the netbook-launcher process with, compiz running either Extra or custom effects, will about half the time, use virtually all of my processor bringing my desktop environment to its knees. It may or may not do this if I boot with effects on but always will if I turn them on after boot up. Any help is most appreciated.


Specs:
Intel Pentium 4 2.8 Ghz Hyper Thread
2 GB Crucial DDR RAM
nVidia Geforce FX Go5200 64 MB w/ 173 Driver
9.10 UNR 32 Bit
2.6.31-17 Kernel

---

### Post by warfacegod on 2010-01-18
What? No takers on this one?

---

### Post by warfacegod on 2010-01-18
Starting to feel like a pariah.

---

### Post by warfacegod on 2010-01-23
This is a cold and lonely place.

---

### Post by willowave on 2010-01-25
I'm just replying so you don't feel so alone :D
I've noticed that with effects on even UNR slows down my Eee pc. As purty as it is, I keep it turned off cuz I only have 1 gig of RAM in it so far. (But it slowed down on my regular Ubuntu too. So like I said...I'm no help. I' just felt sorry for you. )

---

### Post by warfacegod on 2010-01-25
A reply! I'd thank god but that would be a bit self serving. It's good to hear a voice. Any voice.

---

### Post by willowave on 2010-01-26
Since I've got your attention and I see you are on here quite a bit, I might as well ask you. Do you know if there is a way to edit the netbook launcher? I'd like to minimize it maybe, so I don't have a menu sitting on my desktop the WHOLE time, and maybe edit the left hand panel/menu thingy. I don't need ALL those seperate tabs. I'd like to stick the tabs I don't use into one tab maybe labeled "stuff"  or something fancy like that. I saw you like to break things....this might be a good opportunity if you are interested. I like to break things too...but with a baby at home (I'm a stay at home mom) I just don't have time to fix them. lol

---

### Post by warfacegod on 2010-01-26
So you want me to try and break my stuff so you won't break yours.:twisted: Okay, I'll do it. Just as soon as I can get my laptop up and running. GRUB decided to commit suicide and I don't have the proper hardware on my other computer to make a new installUSB. In the mean time some light reading while you wait:

[http://ubuntuforums.org/showthread.php?t=878695&highlight=customize+netbook+remix]("http://ubuntuforums.org/showthread.php?t=878695&highlight=customize+netbook+remix")

---

### Post by willowave on 2010-01-27
LOL It sounds so selfish when you put it like that but yeah pretty much. :D Are you sure GRUB decided to commit suicide or did you murder it? I wish I had more time to mess with stuff. I try but someone is always harrassing me for something. 
Thanks for the link but I was hoping for more tweaking than that. I don't want something open on my desktop all the time. It bugs the crap out of me. and so....if I edit .gtk-bookmarks and if I delete tabs then would the only way I am able to open the apps I want, that I need only once in awhile would be thru command line? I'm getting the feeling I'm going to break something. :D cross your fingers...
EDIT: You know I just realized (I had this installed one other time before when it was 9.04) I don't HAVE the right side panel. Which is fine I don't want it. But if I did want it...WHERE is it?

---

### Post by scottuss on 2010-01-27
Just a quick comment: I'm using Gnome Shell on my eee 701 and it's really great! (Use the PPA version)

---

### Post by Leppie on 2010-01-27
you may actually want to take a look at this post: [http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8233155&postcount=6](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8233155&postcount=6)

---

### Post by warfacegod on 2010-01-27
> **willowave said:**
> LOL It sounds so selfish when you put it like that but yeah pretty much. :D Are you sure GRUB decided to commit suicide or did you murder it? I wish I had more time to mess with stuff. I try but someone is always harrassing me for something. 
Thanks for the link but I was hoping for more tweaking than that. I don't want something open on my desktop all the time. It bugs the crap out of me. and so....if I edit .gtk-bookmarks and if I delete tabs then would the only way I am able to open the apps I want, that I need only once in awhile would be thru command line? I'm getting the feeling I'm going to break something. :D cross your fingers...
EDIT: You know I just realized (I had this installed one other time before when it was 9.04) I don't HAVE the right side panel. Which is fine I don't want it. But if I did want it...WHERE is it?

Trust me, no murder involved. GRUB is the one thing I won't mess with so that I can always boot ubuntu at least. That theory worked out well, didn't it?!

Why not disable the netbook interface entirely? I think if you wanted the *right* pane you would have to install the 9.04 version of netbook-launcher, "I think".

I'm working on a crazy scheme to get my laptop back up so I'll be able to tell you more then. Stay posted! Same Bat time! Same Bat channel!

---

### Post by willowave on 2010-01-28
> **Leppie said:**
> you may actually want to take a look at this post: [http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8233155&postcount=6](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8233155&postcount=6)

Yeah I did see that post. Thanks Leppie. But really I like the launcher. I don't want to completely remove it, I'd just like to edit it and was hoping that there was a way to make it so the panel wasn't sitting with a tab open ALL of the time on the desktop. It actually is pretty handy for netbooks because you can utilize the whole screen then.
I am going to check out the Gnome shell too tho.

---

### Post by Leppie on 2010-01-28
i'm sorry it's not exactly what you were looking for...
i'd install unr myself, but just discovered i've got a x64 system, so will do a re-install of my main system first...

---

### Post by willowave on 2010-01-29
Well I don't have much to worry about now. I forgot to enable the desktop when I killed off the launcher. Yeah I know it sounds stupid but I had two kids climbing on me when I did it. Don't work on linux while being distracted, at least I can't. So when I rebooted the system, I had nothing. I couldnt get in to restart the launcher (not enough command line experience) so I end up reinstalling which isnt a big deal cuz I didnt really have it on there very long in the first place. So I reinstall, and it wont start the wireless. I also noticed it brought in my previous settings after I told it not to. So. After trying to restart, disabling the wireless and re-enabling it several times, checking ifconfig and only seeing the l0, loopback, I gave up for the time being. I am talking to you thru a usb kubuntu and not really sure what to try next. Let me know if anyone has any suggestions.
On top of all this my main system died today, and I was using this as my main til I rebuild my main computer. Go figure.

And I just have to say how very frustrating it is to have it work fine the first time its installed and then to reinstall and have it NOT work, not even show up. Kinda pisses me off. It's one thing with all the different hardware to not have it work right out of the box. But to have it work then just NOT work?

---

### Post by warfacegod on 2010-01-29
> **willowave said:**
> Well I don't have much to worry about now. I forgot to enable the desktop when I killed off the launcher. Yeah I know it sounds stupid but I had two kids climbing on me when I did it. Don't work on linux while being distracted, at least I can't. So when I rebooted the system, I had nothing. I couldnt get in to restart the launcher (not enough command line experience) so I end up reinstalling which isnt a big deal cuz I didnt really have it on there very long in the first place. So I reinstall, and it wont start the wireless. I also noticed it brought in my previous settings after I told it not to. So. After trying to restart, disabling the wireless and re-enabling it several times, checking ifconfig and only seeing the l0, loopback, I gave up for the time being. I am talking to you thru a usb kubuntu and not really sure what to try next. Let me know if anyone has any suggestions.
On top of all this my main system died today, and I was using this as my main til I rebuild my main computer. Go figure.

And I just have to say how very frustrating it is to have it work fine the first time its installed and then to reinstall and have it NOT work, not even show up. Kinda pisses me off. It's one thing with all the different hardware to not have it work right out of the box. But to have it work then just NOT work?

Go to: System> Admin.> Hardware Drivers> and activate the recommended wireless driver, if one is there. Might want to activate your video driver while your there too.

---

### Post by willowave on 2010-01-29
Did that and got "No propritary drivers are in use on this system" and there is nothing listed in the box. 
I am now using my sons Dell laptop as I have no other working computers in the house. Nice.

---

### Post by warfacegod on 2010-01-29
> **willowave said:**
> Did that and got "No propritary drivers are in use on this system" and there is nothing listed in the box. 
I am now using my sons Dell laptop as I have no other working computers in the house. Nice.

Enable restricted extras in Software Sources. You'll need to give internet access. Your netbook should have an ethernet port so use a cabled connection.

---

### Post by willowave on 2010-01-29
Already was enabled...hooking her up now. Should I try to just update when I get it hardwired? And do you have an idea of why all this happened?

---

### Post by warfacegod on 2010-01-29
> **willowave said:**
> Already was enabled...hooking her up now. Should I try to just update when I get it hardwired? And do you have an idea of why all this happened?

Yea, hook it up and update. Probably happened because it didn't have internet during the install or after.

---

### Post by willowave on 2010-01-29
HA...your gonna love this. So I had it hooked up to a usb wireless kb/mouse and a larger monitor. I unhooked it, took it in to the router. Hooked it up. Nothing happened. Touchpad is frozen. Hook it up thinking maybe it'll push something to get going....nope...unhook it from the router, hook it back up to the kb/mouse (differnt room as the router)...after restarting it 3 times. Nothing. It wont move. 
Keyboard does work because it asks me for the keyring passwrd. So ....restarted again....complete shutdown. Sit for a few minutes, make sure RAM is clear. 
Touchpad still wont work. 
I'M THINKIN I'm done with this crap for now unless you have some good ideas. I'm about ready to stick Windows back on it. 
I love Linux but this is why it isn't more mainstream.

---

### Post by warfacegod on 2010-01-29
Your xorg file almost certainly got messed up by disconnecting the Monitor. The easiest fix, considering the other issues, is to reinstall with the ethernet connected.

Remember, Windows installs are *never* the same either. I used to have to reinstall Windows countless times on the same machine with the same XP disc. Every time, Windows was always installed differently, nothing ever worked the same way.

I don't blame you, though, if this is becoming too much of a hassle. It almost was for me at first.

---

### Post by willowave on 2010-01-29
I'm going to reinstall Ubuntu for now since I will be using it for my main system for awhile til I get my other computer rebuilt. I think I'll have more flexibilty ...maybe? when using the other monitor? Desktop wise I will anyways.  I guess I'll see what happens. Yeah I know I've been messing with Linux on and off since Red Hat 5.1 I just never have the time to stick with it thru the crap like this. 
I'm not impressed with my install so far....window showing progress won't open. 
At least I know how to check my drivers now. lol
Why do I get the feeling I'll be back here with more problems? (cuz I like to break things.....)

---

### Post by willowave on 2010-01-30
working ubuntu, I'm not breaking this one til I get another computer built. Sorry I hijacked your thread lol
EDIT: Wrong. I already broke it. looks like xorg is screwed again. I'm trying to change screen res thru command line and it keeps telling me cant open display. I think I may have to reinstall. Bah.

---

### Post by Leppie on 2010-01-30
> **willowave said:**
> working ubuntu, I'm not breaking this one til I get another computer built. Sorry I hijacked your thread lol
EDIT: Wrong. I already broke it. looks like xorg is screwed again. I'm trying to change screen res thru command line and it keeps telling me cant open display. I think I may have to reinstall. Bah.
if this is a karmic install, you can just delete the xorg.conf (karmic doesn't have a xorg.conf by default, it's only needed for customization of the graphics module), or rename it.

---

### Post by willowave on 2010-01-30
yur awesome. thank you so much. so how do I do that? I'm sitting at the root command line right now.
EDIT: got it. but now it's still not giving me a display.

---

### Post by Leppie on 2010-01-30
> **willowave said:**
> yur awesome. thank you so much. so how do I do that? I'm sitting at the root command line right now.
something like:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
then launch x

---

### Post by warfacegod on 2010-01-30
> **willowave said:**
> working ubuntu, I'm not breaking this one til I get another computer built. Sorry I hijacked your thread lol
EDIT: Wrong. I already broke it. looks like xorg is screwed again. I'm trying to change screen res thru command line and it keeps telling me cant open display. I think I may have to reinstall. Bah.

Changing the Res. doesn't work in the Display Manager or Your driver utility? I'm not sure about UNR but in normal 9.10, the xorg files are shipping blank. nVidia is the only one using it now. Try deleting the contents in the file (not the file itself).

---

### Post by Leppie on 2010-01-30
> **warfacegod said:**
> Changing the Res. doesn't work in the Display Manager or Your driver utility? I'm not sure about UNR but in normal 9.10, the xorg files are shipping blank. nVidia is the only one using it now. Try deleting the contents in the file (not the file itself).
you can delete the xorg.conf. i just did a clean install of karmic and i don't have the xorg.conf on my system, it's only an optional.

---

### Post by warfacegod on 2010-01-30
Boosting beans in my thread I :Psee.

---

### Post by willowave on 2010-01-30
OK...so too late. I deleted the file. It actually booted up better this time after I did that. I got proper display on the splash screen but when it tried to boot up into the desktop it gives me a very black screen. I was able to use Fn? or Alt? 4 to open up a terminal, but I can't get that to open now either. When I go to the recovery console its still telling me "can't open display"....
I was just trying to make both monitors work. This is killin me.
EDIT: I'll be gone for half an hour...I expect you guys to have this fixed when I get back. hee hee
Seriously, thanks for your help. I expect I botched it up enough to do another install this afternoon. I think we should do a sticky post to see who has had to reinstall linux the most times. I wonder if I would win.

---

### Post by Leppie on 2010-01-30
> **warfacegod said:**
> Boosting beans in my thread I :Psee.
course i do... what'd you expect? :P

---

### Post by warfacegod on 2010-01-30
> **willowave said:**
> OK...so too late. I deleted the file. It actually booted up better this time after I did that. I got proper display on the splash screen but when it tried to boot up into the desktop it gives me a very black screen. I was able to use Fn? or Alt? 4 to open up a terminal, but I can't get that to open now either. When I go to the recovery console its still telling me "can't open display"....
I was just trying to make both monitors work. This is killin me.

Sorry if you answered this already. What graphics card do you have? Better yet, post the output of:

```
sudo lshw
```

---

### Post by Leppie on 2010-01-30
> **willowave said:**
> OK...so too late. I deleted the file. It actually booted up better this time after I did that. I got proper display on the splash screen but when it tried to boot up into the desktop it gives me a very black screen. I was able to use Fn? or Alt? 4 to open up a terminal, but I can't get that to open now either. When I go to the recovery console its still telling me "can't open display"....
I was just trying to make both monitors work. This is killin me.
are both monitors attached now? if so, try disconnecting the 2nd.

---

### Post by warfacegod on 2010-01-30
I should have thought of that first. Can't post what you can't see.

---

### Post by willowave on 2010-01-30
heh, actually i can get into the recovery console so I can go type that in and see what I get. Let me go check. And I did already unplug the second monitor and restarted. No luck. So I'm back to recovery console.
EDIT: Did that and everything scrolls by too fast...whats the command to page?

---

### Post by warfacegod on 2010-01-30
> **willowave said:**
> heh, actually i can get into the recovery console so I can go type that in and see what I get. Let me go check. And I did already unplug the second monitor and restarted. No luck. So I'm back to recovery console.
EDIT: Did that and everything scrolls by too fast...whats the command to page?

It will look like this:

>     description: Computer
    vendor: Gateway
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal
  *-core
       description: Motherboard
       product: MS-6330
       vendor: MicroStar
       physical id: 0
       version: 2.1
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0AAVWP13 (06/26/2001)
          size: 64KiB
          capacity: 192KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp i2oboot ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.4.2
          slot: F2
          size: 1100MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pat pse36 mmx fxsr syscall mmxext 3dnowext 3dnow up
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             clock: 25MHz (40.0ns)
             capabilities: pipeline-burst synchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-cache
             size: 256KiB
             capacity: 512KiB
             clock: 25MHz (40.0ns)
             capabilities: pipeline-burst synchronous internal write-back unified
     *-memory
          description: System Memory
          physical id: 22
          slot: System board or motherboard
          size: 1GiB
          capacity: 1536MiB
        *-bank:0
             description: DIMM SDRAM Synchronous 100 MHz (10.0 ns)
             physical id: 0
             slot: DIMM 1
             size: 512MiB
             width: 64 bits
             clock: 100MHz (10.0ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 100 MHz (10.0 ns)
             physical id: 1
             slot: DIMM 2
             size: 256MiB
             width: 64 bits
             clock: 100MHz (10.0ns)
        *-bank:2
             description: DIMM SDRAM Synchronous 100 MHz (10.0 ns)
             physical id: 2
             slot: DIMM 3
             size: 256MiB
             width: 64 bits
             clock: 100MHz (10.0ns)
     *-pci
          description: Host bridge
          product: VT8363/8365 [KT133/KM133]
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via
          resources: irq:0 memory:e0000000-efffffff(prefetchable)
        *-pci
             description: PCI bridge
             product: VT8363/8365 [KT133/KM133 AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm bus_master cap_list
             resources: ioport:d000(size=4096) memory:faa00000-feafffff memory:bfe00000-dfefffff(prefetchable)
           *-display
                description: VGA compatible controller
                product: NV44A [GeForce 6200]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 bus_master cap_list rom
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
                resources: irq:11 memory:fd000000-fdffffff memory:c0000000-cfffffff(prefetchable) memory:fc000000-fcffffff memory:feae0000-feafffff(prefetchable)
        *-isa
             description: ISA bridge
             product: VT82C686 [Apollo Super South]
             vendor: VIA Technologies, Inc.
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=parport_pc latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 7.1
             bus info: pci@0000:00:07.1
             logical name: scsi0
             logical name: scsi1
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
           *-disk:0
                description: ATA Disk
                product: WDC WD200BB-60CJ
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 16.0
                serial: WD-WMAAF1297218
                size: 18GiB (20GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=689e689e
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 56f6c95a-4c80-4451-9799-0d1a8fafb2ee
                   size: 17GiB
                   capacity: 17GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2009-11-29 14:15:53 filesystem=ext4 lastmountpoint=/&#65533;&#65533;J&#65533;&#65533;&#65533;&#65533;)&#65533;S&#65533;&#63290;&#65533;IZ&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;\&#65533;&#65533;&#65533;&#65533;&#65533;%&#65533; modified=2010-01-27 21:17:08 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-01-30 09:33:01 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 839MiB
                   capacity: 839MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 839MiB
                      capabilities: nofs
           *-disk:1
                description: ATA Disk
                product: WDC WD400BB-53AU
                vendor: Western Digital
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: 18.2
                serial: WD-WMA6R1351001
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=06300630
              *-volume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   version: 1.0
                   serial: e26a9fe8-81de-4e4d-a194-d198a676f0c8
                   size: 37GiB
                   capacity: 37GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2010-01-27 18:01:10 filesystem=ext4 modified=2010-01-27 21:17:08 mounted=2010-01-27 19:56:06 state=clean
           *-cdrom
                description: DVD reader
                product: CDRW/DVD SM-308B
                vendor: SAMSUNG
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: M002
                serial: [SAMSUNG CDRW/DVD SM-308BM0020
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.2
             bus info: pci@0000:00:07.2
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:10 ioport:e800(size=32)
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.3
             bus info: pci@0000:00:07.3
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:10 ioport:e880(size=32)
        *-serial UNCLAIMED
             description: SMBus
             product: VT82C686 [Apollo Super ACPI]
             vendor: VIA Technologies, Inc.
             physical id: 7.4
             bus info: pci@0000:00:07.4
             version: 30
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: SB Live! EMU10k1
             vendor: Creative Labs
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=EMU10K1_Audigy latency=64 maxlatency=20 mingnt=2
             resources: irq:9 ioport:e480(size=32)
        *-input
             description: Input device controller
             product: SB Live! Game Port
             vendor: Creative Labs
             physical id: 9.1
             bus info: pci@0000:00:09.1
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Emu10k1_gameport latency=64
             resources: irq:0 ioport:ec00(size=8)
        *-network:0
             description: Ethernet interface
             product: VT86C100A [Rhine]
             vendor: VIA Technologies, Inc.
             physical id: a
             bus info: pci@0000:00:0a.0
             logical name: eth0
             version: 06
             serial: 00:50:ba:06:e8:7d
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half ip=192.168.2.2 latency=64 link=no maxlatency=152 mingnt=118 multicast=yes port=MII speed=10MB/s
             resources: irq:10 ioport:e400(size=128) memory:febffc00-febffc7f memory:febe0000-febeffff(prefetchable)
        *-network:1
             description: Wireless interface
             product: Belkin
             vendor: Belkin
             physical id: c
             bus info: pci@0000:00:0c.0
             logical name: wmaster0
             version: 20
             serial: 00:17:3f:2d:24:07
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list logical ethernet physical wireless
             configuration: broadcast=yes driver=rtl8180 ip=192.168.1.105 latency=64 maxlatency=64 mingnt=32 multicast=yes wireless=IEEE 802.11bg
             resources: irq:5 ioport:e000(size=256) memory:febff800-febff9ff


Scroll to the top of the Terminal, highlighting everything applicable, hit Shift+Ctrl+C. Open browser, click Reply, hit the code button, hit Ctrl+V, Submit Reply.

---

### Post by willowave on 2010-01-30
lol...can't open brower remember? I'm running back and forth between computers here. You give me commands and I run in the other room, go try them and run back here. Using my sons computer again. 
I'm running these commands in the recovery console....no scroll...no arrow up...true terminal. I need the command that makes it run page by page instread of the full output. And if I remember right...dont I have to pipe the output to read it? I'll go look for options to the command while waiting for you to reply. Maybe I'll find what I'm looking for.
EDIT:Gonna try lshw -short might give me enough

---

### Post by willowave on 2010-01-30
wow lshw -short is nice. 
I have a Mobile 945GME Express Intergrated video card. So its Intel.

---

### Post by Leppie on 2010-01-30
my machine has intel graphics as well and it doesn't require the xorg.conf.
are you sure you didn't change any other settings?

try creating a new account and see if you can login normally.
to change between runlevels (recovery console is runlevel 1, normal everyday use is runlevel 2):
[code]telinit 2[/quote]
if you're in runlevel 2, you'll obviously need sudo

---

### Post by Leppie on 2010-01-30
> **willowave said:**
> heh, actually i can get into the recovery console so I can go type that in and see what I get. Let me go check. And I did already unplug the second monitor and restarted. No luck. So I'm back to recovery console.
EDIT: Did that and everything scrolls by too fast...whats the command to page?
to make it more readable:
```
lshw | less
```

---

### Post by willowave on 2010-01-30
You are not going to believe this. So I got it working...I found a page on the forum that talked about my vid card...ect ect, did X -configure, it made a new xorg.conf file and now AT LEAST my netbook is working. However when I go to hook it up to the monitor it goes black again. So I can deal with no monitor. 
NOW it's DUMPED MY WIRELESS again. WTF?? It says wireless disabled. And I'm going to bet that when I go and do ifconfig its not going to show anything just like it did before. 
This would all be amusing and wonderful if I had another computer to work with. But my main system died just a day or two ago. This is giving me a headache and my daughter has had enough cuz I keep messing with the computer and not playing with her. 
Going to pull hair out now. 
I'm going to put in the link that I used to help with my vid card in case someone else runs into this. 
[http://ubuntuforums.org/showthread.php?t=1324239&page=3](http://ubuntuforums.org/showthread.php?t=1324239&page=3)

---

### Post by warfacegod on 2010-01-30
I don't suppose I could talk you into *not* trying to use your second monitor?

---

### Post by Leppie on 2010-01-30
> **warfacegod said:**
> I don't suppose I could talk you into *not* trying to use your second monitor?
lol - that would be sooooo microsoft like... :P

---

### Post by willowave on 2010-01-30
lol its looking like I don't have much of a choice. Either I want a working computer, or I can NOT have one and keep Ef'n around with this. But now I'm not going to have a working computer if I don't get the wireless working again. SO....what happened...did it dump the wireless drivers? 
Where'd they go and how much work am I going to have to do to get them back?
I smell another reinstall and this one isn't going to be linux I don't think. Not until I get another working desktop.

---

### Post by warfacegod on 2010-01-30
> **Leppie said:**
> lol - that would be sooooo microsoft like... :P

Hey! this is *my* thread, I can suggest anything I want.:P

Maybe a better response would have been; SSSHHHHHH!!!!!!!! don't tell her!:rolleyes:

---

### Post by warfacegod on 2010-01-30
> **willowave said:**
> lol its looking like I don't have much of a choice. Either I want a working computer, or I can NOT have one and keep Ef'n around with this. But now I'm not going to have a working computer if I don't get the wireless working again. SO....what happened...did it dump the wireless drivers? 
Where'd they go and how much work am I going to have to do to get them back?
I smell another reinstall and this one isn't going to be linux I don't think. Not until I get another working desktop.

System> Adimin.> Hardware Drivers

---

### Post by Leppie on 2010-01-30
depending on what wifi card you got, check the kernel drivers:
```
lsmod
```

intel wifi uses the kernel modules, so i can refine like this (and since you've got the 945gme integrated card, i think you've got intel wireless as well):
```
lsmod | grep iwl
```

---

### Post by Leppie on 2010-01-30
> **warfacegod said:**
> Hey! this is *my* thread, I can suggest anything I want.:P

Maybe a better response would have been; SSSHHHHHH!!!!!!!! don't tell her!:rolleyes:
oki sowwy...
SSSSSSSHHHHH!!! don't tell her... ;)

---

### Post by warfacegod on 2010-01-30
Try using:```
sudo iwlist scanning
``` to see if you are picking up any signals.

---

### Post by willowave on 2010-01-30
ok so lsmod gives me a nice list, lsmod with grep gives me nothing (I cant remembe rwhat grep does..output to something?)....iwlist scanning says none of the interfaces support scanning (one says network is down but its not the wireless)
and my wireless is the AR9285 Atheros
gotta get my daughter to take a nap bbl

---

### Post by Leppie on 2010-01-30
> **willowave said:**
> ok so lsmod gives me a nice list, lsmod with grep gives me nothing (I cant remembe rwhat grep does..output to something?)....
from man:
> GREP(1)                          User Commands                         GREP(1)

NAME
       grep, egrep, fgrep, rgrep - print lines matching a pattern


> **willowave said:**
> and my wireless is the AR9285 Atheros
are you using the madwifi drivers?

> **willowave said:**
> iwlist scanning says none of the interfaces support scanning (one says  network is down but its not the wireless)
well, iwlist wouldn't do much if your card is atheros

---

### Post by warfacegod on 2010-01-30
Plug it into the net. Enable restricted-extras. Enable installable from CD-ROM. Get updates. Check wireless.

---

### Post by warfacegod on 2010-01-30
jkhjghnmhjzdbnZAe]0-thiq \4op
ah;LZBC>?V< ]z 
HKas'gnmXC<>?:z
Cvo

EDIT: warfacegod shall, in the future, refrain from pounding his fist into the keyboard because of the unbelievable slowness of his wife's computer.

---

### Post by warfacegod on 2010-01-30
> are you using the madwifi drivers?

Shouldn't have to. Atheros is generally well supported.

---

### Post by Leppie on 2010-01-30
> **warfacegod said:**
> jkhjghnmhjzdbnZAe]0-thiq \4op
ah;LZBC>?V< ]z 
HKas'gnmXC<>?:z
Cvo

EDIT: warfacegod shall, in the future, refrain from pounding his fist into the keyboard because of the unbelievable slowness of his wife's computer.
haha... he shouldn't have fragged his own lappie before getting the new one in the first place ;)

---

### Post by Leppie on 2010-01-30
> **warfacegod said:**
> Shouldn't have to. Atheros is generally well supported.
sorry, didn't know that. i'm using intel :(
coming across a lot of madwifi articles though (even in combination with karmic).

---

### Post by warfacegod on 2010-01-30
What happened, no more Zeitgeist links?



(Totally and completely ignoring fallacious comment about warfacegod's laptop.)

---

### Post by Leppie on 2010-01-30
> **warfacegod said:**
> What happened, no more Zeitgeist links?

(Totally and completely ignoring fallacious comment about warfacegod's laptop.)
the op's bugged me about it... how about that?
ignorance is highly esteemed my friend. i'm sure they don't know what it really is, nor do they understand the implications of the films... so much for "open source"...

don't worry, i will remind you of your own laptop every time you get upset with your wife's system... ;)

---

### Post by warfacegod on 2010-01-30
> **Leppie said:**
> the op's bugged me about it... how about that?
ignorance is highly esteemed my friend. i'm sure they don't know what it really is, nor do they understand the implications of the films... so much for "open source"...

don't worry, i will remind you of your own laptop every time you get upset with your wife's system... ;)

That's what friends are for. To turn the screwdriver just when it's needed most.

---

### Post by Leppie on 2010-01-30
and willowave fled the battle fields...

---

### Post by warfacegod on 2010-01-30
...and the battle lines have been drawn.

[http://money.cnn.com/magazines/fortune/fortune_archive/2007/05/28/100033867/index.htm]("http://money.cnn.com/magazines/fortune/fortune_archive/2007/05/28/100033867/index.htm")

---

### Post by Leppie on 2010-01-30
> **warfacegod said:**
> ...and the battle lines have been drawn.

[http://money.cnn.com/magazines/fortune/fortune_archive/2007/05/28/100033867/index.htm](http://money.cnn.com/magazines/fortune/fortune_archive/2007/05/28/100033867/index.htm)
it's always the same rubbish...
linux has been challenged several times (one of the biggest originating from SCO) which should've eredicated the linux world, yet nothing ever really proven to be "stolen". the big thing is that even if these giants pump lots of money into these things, they will make massive profits from the "free publicity". so even if microsoft loses, it still wins...

---

### Post by warfacegod on 2010-01-30
> **Leppie said:**
> it's always the same rubbish...
linux has been challenged several times (one of the biggest originating from SCO) which should've eredicated the linux world, yet nothing ever really proven to be "stolen". the big thing is that even if these giants pump lots of money into these things, they will make massive profits from the "free publicity". so even if microsoft loses, it still wins...

When Big Business turns its head, the losers in the Endgame are always people like us.

---

### Post by willowave on 2010-01-30
Don't get yur panites in a bundle. :D I fell asleep with my daughter. Cuddle time is awesome. I'll go plug the silly POS in to the router now...do the update thingy...blah blah...
[EMAIL="heh@using"]heh@using[/EMAIL] the wifes computer. Nice job. :D

---

### Post by Leppie on 2010-01-30
fingers crossed... ;)

---

### Post by warfacegod on 2010-01-30
> **willowave said:**
> Don't get yur panites in a bundle. :D I fell asleep with my daughter. Cuddle time is awesome. I'll go plug the silly POS in to the router now...do the update thingy...blah blah...
[EMAIL="heh@using"]heh@using[/EMAIL] the wifes computer. Nice job. :D

Every bodies a critic. Go ahead, give me a jab about how "*I* "broke" my laptop".:roll::twisted:

---

### Post by willowave on 2010-01-30
I got nothin. And no it says my system is up to date. So theres nothing to update. AT least this time the eth0 is there and connected. Last time it dumped everything. Unfortunatly I can't stay connected to the router. The only place to put the computer is on top of the TV.

---

### Post by Leppie on 2010-01-30
> **warfacegod said:**
> Every bodies a critic. Go ahead, give me a jab about how "*I* "broke" my laptop".:roll::twisted:
you deserve it... :P
always posting about how you're going to frag your sysem... but the last time you did it properly...

---

### Post by willowave on 2010-01-30
So boys....whats next? Flyin the white flag hmmm?
Oh and enabling the cdrom doesnt work cuz there isnt one. I wish there was a way to pull the original drivers off the usb.

---

### Post by Leppie on 2010-01-30
try the latest test drivers:
```
sudo apt-get install linux-backports-modules-karmic-generic
sudo apt-get install linux-backports-modules-wireless-karmic-generic
```

---

### Post by willowave on 2010-01-30
Still nothing. No wmaster0 showing up in ifconfig. What do you want to bet I can get my old computer up and running before this thing works? lol

---

### Post by Leppie on 2010-01-30
have you checked your /etc/NetworkManager/nm-system-settings.conf?
and can you see the atheros drivers in lsmod?
if those are kernel modules you will have to load them...
[code]sudo modprobe <moduletoload>[/quote]
or reboot...

---

### Post by willowave on 2010-01-30
when I type in NetworkManager I get no such file or directory. (sorry I did cd to etc and then cd to NetworkManager so let me know if that is wrong)
And how do I tell if I have the Atheros drivers in there...can you give me more of a hint of what I am looking for...I'll tell you what I have that looks relevant
I see these three entries...
ath9k - that has a 0 on it
mac80211 - that has a 1 and then says athk9 after the 1
ath - that has a 1 and ath9k
 
I am going to take a guess and that ath9k is the wireless and the 0 means I don't have it/driver?
 
Whoops found two more...
led_class - 1 and the ath9k after it
cfg80211 - that has a 3 and then has the ath9k,mac80211, and ath after it

---

### Post by Leppie on 2010-01-30
> **willowave said:**
> I see these three entries...
ath9k - that has a 0 on it
mac80211 - that has a 1 and then says athk9 after the 1
ath - that has a 1 and ath9k
 
I am going to take a guess and that ath9k is the wireless and the 0 means I don't have it/driver?
ath9k is the atheros module, 0 means it's not being used by any other module
the mac80211 has a 1 because it's being used by the atheros module (since it's a wireless device) and the ath9k is the module that is using the mac80211 module

you may want to try to reboot...

---

### Post by willowave on 2010-01-30
I did already because apparently you can't unplug the damn hardwired connection without this freezing up. Not impressed. I'll try again tho.
EDIT: Nope nothin. *sigh*
Give up yet?

---

### Post by willowave on 2010-01-30
You guys have given up on me haven't you? I don't blame ya. I'm going to go maybe try a few different things n then probably reinstall. 
On the upside I got my main system working. lol

---

### Post by Leppie on 2010-01-30
wish i could help any further, but i don't use unr and none of my wifi adapters is atheros...

---

### Post by willowave on 2010-01-30
thats ok. Thanks anyways. I learned a few things along the way. That counts for something. It's why I mess with it in the first place. I don't learn anything unless it breaks anyways. :)

---

### Post by Leppie on 2010-01-30
> **willowave said:**
> thats ok. Thanks anyways. I learned a few things along the way. That counts for something. It's why I mess with it in the first place. I don't learn anything unless it breaks anyways. :)
that doesn't necessarily have to be true... :P
i've learned a lot about linux since my first encounter. a lot i learned because i broke things. but i learned a lot as well browsing forums and all trying to help others ;)

---

### Post by willowave on 2010-01-30
I reinstalled. It's not working again. All the other times I reinstalled it worked on install it was after I messed with the video that it quit working. But at least I have another working computer so I can mess with it. Even if I have to balence it on the TV while its hooked to the router. lol

---

### Post by warfacegod on 2010-01-30
Looks like you kids have been busy. Cats away and all that.






I got my laptop back up!

---

### Post by willowave on 2010-01-31
Well I certianly hope you don't have the wireless card I do. lol
I keep hoping I'll shut it down and it will magically work, kind of like it magically seems to not work.

---

### Post by warfacegod on 2010-01-31
> **willowave said:**
> Well I certianly hope you don't have the wireless card I do. lol
I keep hoping I'll shut it down and it will magically work, kind of like it magically seems to not work.

I've got the AR5211 a/b (yep, Atheros) and haven't had an issue with it since 9.04 came out. (Except encryption but that was really Network Managers fault.)

---

### Post by Leppie on 2010-01-31
> **warfacegod said:**
> I got my laptop back up!
kewl :D

what did you do to get it working again? did you order a cheap usb pci controller?

---

### Post by Leppie on 2010-01-31
> **willowave said:**
> Well I certianly hope you don't have the wireless card I do. lol
I keep hoping I'll shut it down and it will magically work, kind of like it magically seems to not work.
is there by any change some hardware or bios switch that has been altered yesterday?

---

### Post by warfacegod on 2010-01-31
> **Leppie said:**
> kewl :D

what did you do to get it working again? did you order a cheap usb pci controller?

I drove like 15 miles to a Mom n' Pop computer store and bought their last USB card.

---

### Post by Leppie on 2010-01-31
> **warfacegod said:**
> I drove like 15 miles to a Mom n' Pop computer store and bought their last USB card.
good thing those stores still exist ;)

---

### Post by warfacegod on 2010-01-31
> **Leppie said:**
> good thing those stores still exist ;)

Not for much longer.

---

### Post by Leppie on 2010-01-31
> **warfacegod said:**
> Not for much longer.
they going out of business?

---

### Post by warfacegod on 2010-01-31
> **Leppie said:**
> they going out of business?

Places like Walmart and Bestbuy are putting lots of them out of business. Just like Home Depot puts little guy hardware stores out of business.

---

### Post by willowave on 2010-01-31
We have a place here that does pretty good. Now that you mention it, I have a dlink that I am using on my main home computer...I wonder if I could use that to maybe kick start it?
Either you guys know anymore about modprobe? I'm trying to find out exactly where to start with all the "solutions" I keep finding on the forums. There are so many problems with wireless on the forums I don't even know where to start.
Nope. dlink not working either.

---

### Post by warfacegod on 2010-01-31
There aren't nearly as many problems with wireless as you'd think. Most of those people are just too lazy to do a proper search and end up posting instead.

---

### Post by willowave on 2010-01-31
> **warfacegod said:**
> There aren't nearly as many problems with wireless as you'd think. Most of those people are just too lazy to do a proper search and end up posting instead.
 lol Where do I fall in that catagory?
Is it time for me to do a post?Everything I try is not working but there has to be SOMEthing that will get this thing working. 
I tried some directions to install madwifi...no luck there either.

---

### Post by warfacegod on 2010-01-31
> **willowave said:**
> lol Where do I fall in that catagory?
Is it time for me to do a post?Everything I try is not working but there has to be SOMEthing that will get this thing working. 
I tried some directions to install madwifi...no luck there either.

Give me a few minutes. I'll be back.

---

### Post by willowave on 2010-01-31
> **warfacegod said:**
> Give me a few minutes. I'll be back.
 I will actually be gone for a few hours. I'll check back here in a little while tho.

---

### Post by warfacegod on 2010-01-31
> **willowave said:**
> So boys....whats next? Flyin the white flag hmmm?
Oh and enabling the cdrom doesnt work cuz there isnt one. I wish there was a way to pull the original drivers off the usb.

It's the same thing with a USB installer if I'm not mistaken. Plug it in, it should get read as the CD.

---

### Post by willowave on 2010-01-31
> **warfacegod said:**
> It's the same thing with a USB installer if I'm not mistaken. Plug it in, it should get read as the CD.
I'll try that next, tho the flash drive I use is a multiboot with  9 os's.

---

### Post by warfacegod on 2010-01-31
Never mind. I just spent the last 45 minutes trying to get it to work.

---

### Post by warfacegod on 2010-01-31
This comes directly from the ath9k site:

If you want to get the latest ath9k driver you can get it by using the wireless-testing git tree. Read our git-guide for that. Alternatively you can download and compile ath9k and its dependencies alone by using compat-wireless. After downloading you can run:

./scripts/driver-select ath9k
make
sudo make install

Enabling ath9k

To enable ath9k, you must first enable mac80211:

Networking  --->
  Wireless  --->
    <M> Improved wireless configuration API
    <M> Generic IEEE 802.11 Networking Stack (mac80211)

You can then enable ath9k in the kernel configuration under

Device Drivers  --->
  [*] Network device support  --->
        Wireless LAN  --->
          <M>   Atheros 802.11n wireless cards support

---

### Post by Leppie on 2010-01-31
> **willowave said:**
> Either you guys know anymore about modprobe? I'm trying to find out exactly where to start with all the "solutions" I keep finding on the forums.
what would yo like to know about modprobe? i have to admit that i'm no expert either on this.

---

### Post by warfacegod on 2010-01-31
I admit nothing.

---

### Post by Leppie on 2010-01-31
> **warfacegod said:**
> I admit nothing.
that's ok, coz we already know... :P

---

### Post by willowave on 2010-01-31
> **warfacegod said:**
> This comes directly from the ath9k site:
 
If you want to get the latest ath9k driver you can get it by using the wireless-testing git tree. Read our git-guide for that. Alternatively you can download and compile ath9k and its dependencies alone by using compat-wireless. After downloading you can run:
 
./scripts/driver-select ath9k
make
sudo make install
 
Enabling ath9k
 
To enable ath9k, you must first enable mac80211:
 
Networking --->
Wireless --->
<M> Improved wireless configuration API
<M> Generic IEEE 802.11 Networking Stack (mac80211)
 
You can then enable ath9k in the kernel configuration under
 
Device Drivers --->
[*] Network device support --->
Wireless LAN --->
<M> Atheros 802.11n wireless cards support
 I know, I read that but honestly I've never compiled anything. 
I'm confused, where it says "networking>wireless>etc" where is that....cuz thats not in the GUI right?  Or does that show up after you do the make install? I started reading that git-guide then I had to leave so I was just going to look into that some more. 
What the hell is a git-guide? lol

---

### Post by willowave on 2010-01-31
ok. I just read all of that about compling the drivers. Theres no way I can do all that. I have ADD and 2 kids. Between the 3 I can't even concentrate long enough to READ enough let alone compile it. 
I guess I'll just keep installing it over and over til it works. lol

---

### Post by Leppie on 2010-01-31
> **willowave said:**
> ok. I just read all of that about compling the drivers. Theres no way I can do all that. I have ADD and 2 kids. Between the 3 I can't even concentrate long enough to READ enough let alone compile it. 
I guess I'll just keep installing it over and over til it works. lol
compiling really isn't that hard. what have you got to lose? if you mess it up, you were going to reinstall anyways ;)

just remember that for compiling there's a couple of essential pachages you need to install. what comes to mind is: build-eseential automake

---

### Post by willowave on 2010-01-31
> **Leppie said:**
> compiling really isn't that hard. what have you got to lose? if you mess it up, you were going to reinstall anyways ;)
 
just remember that for compiling there's a couple of essential pachages you need to install. what comes to mind is: build-eseential automake
 yeah thats part of the problem. I don't have the slightest idea where to start. Sounds like more research.

---

### Post by willowave on 2010-01-31
maybe I'll just try Moblin.

---

### Post by warfacegod on 2010-01-31
```
sudo apt-get install build-essential automake
```

Please excuse Leppie's horrid, mangling of our dear native language.

---

### Post by Leppie on 2010-01-31
> **willowave said:**
> yeah thats part of the problem. I don't have the slightest idea where to start. Sounds like more research.
usually they put a short introduction to compiling on the site (or in the readme).
very often compiling comes down to this:
- installing dependencies
- compiling:
```
./configure
make
sudo make install
```and that's it ;)

---

### Post by warfacegod on 2010-01-31
Try compiling Amarok 1.4 without a script. Try it with one that has packages in it that don't exist.

---

### Post by willowave on 2010-01-31
> **warfacegod said:**
> ```
sudo apt-get install build-essential automake
```
 
Please excuse Leppie's horrid, mangling of our dear native language.
ok...so If I download this essential automake...then (and I already have) downloaded the driver file...and the other three things that it says to download on that page (iw, crda...somethin else) then I should have everything I need and be able to compile it?

---

### Post by warfacegod on 2010-01-31
Ask Leppie, I got lost about 3 pages ago. I'm just being pretend mod right now.

---

### Post by Leppie on 2010-01-31
> **willowave said:**
> ok...so If I download this essential automake...then (and I already have) downloaded the driver file...and the other three things that it says to download on that page (iw, crda...somethin else) then I should have everything I need and be able to compile it?
i guess so, if something goes wrong and you don't know what to do, just post the error ;)

---

### Post by Leppie on 2010-01-31
> **warfacegod said:**
> Ask Leppie, I got lost about 3 pages ago. I'm just being pretend mod right now.
you got demoted??? :P

---

### Post by willowave on 2010-01-31
> **warfacegod said:**
> Ask Leppie, I got lost about 3 pages ago. I'm just being pretend mod right now.
 lol jerk :P
well I have moblin downloading right now. gonna play with that if I cant get this working. this all might have to wait until the kids are sleeping.

---

### Post by warfacegod on 2010-01-31
> **Leppie said:**
> you got demoted??? :P

Yes, I demoted myself to demiwarfacegod for the remainder of this thread or the next post, whichever comes first.

---

### Post by Leppie on 2010-01-31
> **willowave said:**
> lol jerk :P
what'd you expect from the warfacegod??? :P

---

### Post by willowave on 2010-01-31
[http://liquidweather.net/howto/index.php?id=82](http://liquidweather.net/howto/index.php?id=82)
handy link for linux stuff...gives good info on compiling

---

### Post by Leppie on 2010-01-31
> **willowave said:**
> [http://liquidweather.net/howto/index.php?id=82](http://liquidweather.net/howto/index.php?id=82)
handy link for linux stuff...gives good info on compiling
that's the long version of what i told you :P

---

### Post by willowave on 2010-01-31
lol I know but I need to understand the process. I'm not good at just following directions. In fact, I stink. lol

---

### Post by willowave on 2010-01-31
> **warfacegod said:**
> Yes, I demoted myself to demiwarfacegod for the remainder of this thread or the next post, whichever comes first.
 Are you back to warfacegod yet? Or still demoted?

---

### Post by Leppie on 2010-01-31
> **willowave said:**
> lol I know but I need to understand the process.
to understand the process you will have to know a lot about programming and shell scripting... that would require a significant amount of reading and testing...

---

### Post by warfacegod on 2010-01-31
> **willowave said:**
> Are you back to warfacegod yet? Or still demoted?

Full divinity has been attained again.

---

### Post by warfacegod on 2010-01-31
> **willowave said:**
> lol I know but I need to understand the process. I'm not good at just following directions. In fact, I stink. lol

Is *that* why we're still here?:shock::biggrin:](*,)

---

### Post by Leppie on 2010-01-31
> **warfacegod said:**
> Is *that* why we're still here?:shock::biggrin:](*,)
i guess so... :lolflag:

---

### Post by warfacegod on 2010-01-31
13 pages later and I've almost completely forgotten why I started this thread in the first place.

---

### Post by Leppie on 2010-01-31
> **warfacegod said:**
> 13 pages later and I've almost completely forgotten why I started this thread in the first place.
to get some more beanses... :P

---

### Post by willowave on 2010-01-31
well Moblins not gonna work. It's too foofy for me. 
I guess I'll just work on tryin to get these drivers to work. It's gonna take all week. lol I'll be lucky to get one command a day done.

---

### Post by warfacegod on 2010-01-31
AAaaaarRRRGGGghhhGHHHHRRRAaaaAAAA!!!!!!!

(warfacegod, having repeated slammed his warface into the tempered glass of his desk, realizes that the digital bloody mess he was staring at on his laptop has now, literally, become a bloody mess)

---

### Post by willowave on 2010-01-31
> **warfacegod said:**
> AAaaaarRRRGGGghhhGHHHHRRRAaaaAAAA!!!!!!!
 
(warfacegod, having repeated slammed his warface into the tempered glass of his desk, realizes that the digital bloody mess he was staring at on his laptop has now, literally, become a bloody mess)
 LOL I thought it was all fixed? What happened? Er...what happened to it in the first place?

---

### Post by warfacegod on 2010-01-31
> **willowave said:**
> LOL I thought it was all fixed? What happened? Er...what happened to it in the first place?

This thread.:P

Have a :KS for not giving up.

---

### Post by Leppie on 2010-02-01
and we're back to the normal level... :P

---

### Post by willowave on 2010-02-01
so boys...I tried to install the build-essential automake....won't go.
any suggestions?

---

### Post by Leppie on 2010-02-01
> **willowave said:**
> so boys...I tried to install the build-essential automake....won't go.
any suggestions?
sorry, what was the output of that?

---

### Post by willowave on 2010-02-01
right was just looking that up when you asked. says "couldn't find package build"
actually when I tried to do the madwifi installation it seemed to give me that a few times too.

---

### Post by willowave on 2010-02-01
> **warfacegod said:**
> This thread.:P
 
Have a :KS for not giving up.
 and yes I am stubborn as hell. I don't like losing. Especially to a damn computer. 
Let me know if you'd like me to start my own thread so you can have yours back. lol
As long as you boys promise to come visit. lol

---

### Post by Leppie on 2010-02-01
> **willowave said:**
> right was just looking that up when you asked. says "couldn't find package build"
actually when I tried to do the madwifi installation it seemed to give me that a few times too.
did you put the dash in between build and essential? the package name is "build-essential"... lol

---

### Post by Leppie on 2010-02-01
> **willowave said:**
> and yes I am stubborn as hell. I don't like losing. Especially to a damn computer.
who's more stubborn... computer or man (in this case woman ;))... :P

---

### Post by warfacegod on 2010-02-01
> **willowave said:**
> and yes I am stubborn as hell. I don't like losing. Especially to a damn computer. 
Let me know if you'd like me to start my own thread so you can have yours back. lol
As long as you boys promise to come visit. lol

Little late for that.


(warfacegod goes off to sulk in the corner.)

---

### Post by warfacegod on 2010-02-01
> **willowave said:**
> right was just looking that up when you asked. says "couldn't find package build"
actually when I tried to do the madwifi installation it seemed to give me that a few times too.

Have you considered witchcraft?

---

### Post by Leppie on 2010-02-01
> **warfacegod said:**
> (warfacegod goes off to sulk in the corner.)
these are tough times... first gets demoted, then thread hijacked...

---

### Post by warfacegod on 2010-02-01
> **Leppie said:**
> these are tough times... first gets demoted, then thread hijacked...

Feel like Rodney Dangerfield....:cry:

---

### Post by willowave on 2010-02-01
> **Leppie said:**
> did you put the dash in between build and essential? the package name is "build-essential"... lol
 *blush*
ok. yeah I forgot the -.
layer 8. :D
ok. marching on...

---

### Post by willowave on 2010-02-01
Seriously let me know if you'd like me to just start a thread. My feelings won't be hurt. lol

---

### Post by audiomick on 2010-02-01
> **willowave said:**
> Seriously let me know if you'd like me to just start a thread. My feelings won't be hurt. lol

I think they are having fun...

---

### Post by Leppie on 2010-02-01
> **warfacegod said:**
> Feel like Rodney Dangerfield....:cry:
there there...

---

### Post by Leppie on 2010-02-01
> **willowave said:**
> *blush*
ok. yeah I forgot the -.
layer 8. :D
ok. marching on...
don't worry, you should know the mistakes i made when trying to compile the first time... :lolflag:

---

### Post by willowave on 2010-02-01
> **audiomick said:**
> I think they are having fun...
 I dunno...warfacegod is all bloody, and I barely have any hair left.
Leppies hanging in there ok tho. lol 
I'm impressed I didn't get more crap from them for forgetting the dash. lol

---

### Post by audiomick on 2010-02-01
> **willowave said:**
> 
I'm impressed I didn't get more crap from them for forgetting the dash. lol
Take heed: they never let you forget anything...

---

### Post by warfacegod on 2010-02-01
> **willowave said:**
> Seriously let me know if you'd like me to just start a thread. My feelings won't be hurt. lol

No. No. Carry on... (sniff!)



I've long since installed Mythbuntu over the UNR partition and then UNR over that. At this point, I'm more interested in giving UNR surgery. 



(Liposuction Leppie, *NOT!* a lobotomy.)

---

### Post by Leppie on 2010-02-01
> **willowave said:**
> I'm impressed I didn't get more crap from them for forgetting the dash. lol
we all are novices at something...

---

### Post by Leppie on 2010-02-01
> **warfacegod said:**
> Liposuction Leppie, *NOT!* a lobotomy.)
why? lobotomy is far more interesting than liposuction... though liposuction can be a lot more messy...

---

### Post by warfacegod on 2010-02-01
> **willowave said:**
> I dunno...warfacegod is all bloody, and I barely have any hair left.
Leppies hanging in there ok tho. lol 
I'm impressed I didn't get more crap from them for forgetting the dash. lol

If you like, I can mail you some!

---

### Post by Leppie on 2010-02-01
> **warfacegod said:**
> If you like, I can mail you some!
yeah, send me some ;)

---

### Post by willowave on 2010-02-01
What is a good network manager besides the default one that comes with Ubuntu?
I'd like to experiment with something from a post I just tried. Any suggestions?

---

### Post by willowave on 2010-02-01
> **warfacegod said:**
> If you like, I can mail you some!
 Mail me crap, blood or hair?

---

### Post by Leppie on 2010-02-01
dunno, i jus tuse the XFCE network manager...
you could try wicd:
```
sudo apt-get install wicd
```

---

### Post by willowave on 2010-02-01
I've got half of what I need to do the madwifi...(wth is madwifi anyways?)
I'm getting down to not many more options to try. I've tried a new network manager. I've tried erasing network interfaces. I've tried the updating backports. Uninstalling and reinstalling gnome network manager. I don't have a wireless switch so I know its not turned off. I'm going to try the madwifi in a bit, and then I'M STARTING MY OWN THREAD and ITS ON like DONKEY KONG

---

### Post by warfacegod on 2010-02-01
Fair Warning: It is not recommended that Network Manager be removed.

Having said that and eased my conscience, I say do it.

---

### Post by warfacegod on 2010-02-01
> **willowave said:**
> I've got half of what I need to do the madwifi...(wth is madwifi anyways?)
I'm getting down to not many more options to try. I've tried a new network manager. I've tried erasing network interfaces. I've tried the updating backports. Uninstalling and reinstalling gnome network manager. I don't have a wireless switch so I know its not turned off. I'm going to try the madwifi in a bit, and then I'M STARTING MY OWN THREAD and ITS ON like DONKEY KONG

What? You mean we can't milk this for more beanses?

---

### Post by Leppie on 2010-02-01
> **willowave said:**
> I've got half of what I need to do the madwifi...(wth is madwifi anyways?)
maybe because this wifi makes you go mad? :lolflag:

---

### Post by Leppie on 2010-02-01
> **warfacegod said:**
> What? You mean we can't milk this for more beanses?
yes we can, just in another thread afaiu...

---

### Post by warfacegod on 2010-02-01
> @Warfacegod, I dunno if/how it can be done through the GUI, but you could edit the /etc/apt/sources.list file and add deb file://<location> /. Where the location would be your flash drive. In my installation CD i saw the release file in /dists/karmic, so try putting deb file:///media/(flash drive name)/dists/karmic / in sources.list

I just got this from another thread. This might be the way to use the Usb installer to get the wireless driver.

---

### Post by willowave on 2010-02-01
> **warfacegod said:**
> I just got this from another thread. This might be the way to use the Usb installer to get the wireless driver.
 I think if  I do that option I'll do that last cuz then I'd end up breaking my sources.list somehow and then never be able to update. 
So then why if the correct drivers are on the USB key/install files (which they must be, because this USB has worked more than once on install) why the hell arent they on my computer/working??
THAT would be a bug I'd say.

---

### Post by warfacegod on 2010-02-01
> **willowave said:**
> So then why if the correct drivers are on the USB key/install files (which they must be, because this USB has worked more than once on install) why the hell arent they on my computer/working??
THAT would be a bug I'd say.

Please refer to post #130 on page 13.

---

### Post by audiomick on 2010-02-01
> **warfacegod said:**
> Please refer to post #130 on page 13.

eloquent.

---

### Post by willowave on 2010-02-01
> **warfacegod said:**
> AAaaaarRRRGGGghhhGHHHHRRRAaaaAAAA!!!!!!!
 
(warfacegod, having repeated slammed his warface into the tempered glass of his desk, realizes that the digital bloody mess he was staring at on his laptop has now, literally, become a bloody mess)
This pretty face does not look good bloody. I prefer to throw things. And break them permanently. None of this intermittent not working crap. Just good ol broken.

---

### Post by willowave on 2010-02-01
installing madwifi...don't hold your breath...

---

### Post by willowave on 2010-02-01
This is seriously gettin ridiculious. So. Nothing. Give me some commands to test it or that will give me some new information. I'm about ready to install windows just to see if it works. And then I can tell you I wont be working with linux again til they fix this.
EDIT:nevermind. I just did ifconfig and it still doesnt show a wireless.

---

### Post by Leppie on 2010-02-01
> **willowave said:**
> This is seriously gettin ridiculious. So. Nothing. Give me some commands to test it or that will give me some new information. I'm about ready to install windows just to see if it works. And then I can tell you I wont be working with linux again til they fix this.
EDIT:nevermind. I just did ifconfig and it still doesnt show a wireless.
isn't there any .deb package around to install the madwifi stuff with?

have you tried the following command:
```
sudo apt-get install -f linux-restricted-modules-$(uname -r)
```

---

### Post by willowave on 2010-02-01
Too late. It's deleted. BUT. When I went to reinstall windows...which is supposed to be wonderfully easy on the Eee PC, and why I was working with linux on this thing cuz of the easy reinstall...it seems that it cant see the ghosted partition there anymore. I know it's there. it's just that F9 isn't working now. It worked not too long ago, but when I tried to use it, it wont install with linux on it cuz it says theres no room to install. So I need to delete linux to install windows. But if I do that then it wont boot up the ghosted partition. For petes sake. BAHHHHHHHHHHH!!!! More work.

---

### Post by willowave on 2010-02-01
> **Leppie said:**
> isn't there any .deb package around to install the madwifi stuff with?
 
have you tried the following command:
```
sudo apt-get install -f linux-restricted-modules-$(uname -r)
```
 There might be but I'm pretty sure I installed it all ok. When I did lshw this time it showed the wireless as wlan0 this time instead of wmaster0. But still wont work.

---

### Post by warfacegod on 2010-02-01
> **willowave said:**
> Too late. It's deleted. BUT. When I went to reinstall windows...which is supposed to be wonderfully easy on the Eee PC, and why I was working with linux on this thing cuz of the easy reinstall...it seems that it cant see the ghosted partition there anymore. I know it's there. it's just that F9 isn't working now. It worked not too long ago, but when I tried to use it, it wont install with linux on it cuz it says theres no room to install. So I need to delete linux to install windows. But if I do that then it wont boot up the ghosted partition. For petes sake. BAHHHHHHHHHHH!!!! More work.

Please refer to post #130 on page 13.

---

### Post by willowave on 2010-02-01
> **warfacegod said:**
> Please refer to post #130 on page 13.
 mmmmyeah. I'm there.

---

### Post by willowave on 2010-02-01
so have any luck with mythbuntu? I've got a box with it sitting right here, but I can't get rid of the 160. ip address. 
What linux distro should I try next?
Since we obviously need a new topic for this thread.

---

### Post by warfacegod on 2010-02-01
Synchronized head=desktop smashing.

---

### Post by warfacegod on 2010-02-01
If Windows is acting dodgy then I'm wondering if this might be hardware.

(warfacegod laughs up his sleeve at mentioning Windows acting in anyway.)








Chocolate Ubuntu Mocha Blend: I ***HATE!!!!*** chocolate!

---

### Post by willowave on 2010-02-01
no I'm pretty sure it wouldnt be because I erased the partition. And let it unallocated. Which means no grub. And the windows partition is nortons ghost...which isn't intuitive enough to ask if I want to delete the partition that linux is on ect ect. it just says "oh you dont have enough room piss on you"
So I either have grub and linux and no room to install windows. Or I cant install windows from the img partition. I'm sure there is a way around it I just havent decided how much work I want to put into it. And I might have a rescue disk for my Eee...but no cd-rom to use it with. More research needed...because I assume that there would be some way to put the rescue disk on a usb since there is no cd-rom on the netbook. 
You hate chocolate? WTH is wrong with you? lol I have a cup of M&M's I munch on all day. Who needs food.

---

### Post by Leppie on 2010-02-01
so is your atheros card working now? :P

---

### Post by willowave on 2010-02-01
> **Leppie said:**
> so is your atheros card working now? :P
***. lol
EDIT:***** lol
OMG LOL I called you a donkey and it stars it? wow. child safe area huh?
 
wait ...does it star "****"?
LMAO...yep. the "english version"

---

### Post by willowave on 2010-02-01
I'm trying to decide what to install next. I figured I'd try something that I haven't tried since nothing seems to work anyways.

---

### Post by warfacegod on 2010-02-01
> **warfacegod said:**
> If Windows is acting dodgy then I'm wondering if this might be hardware.

(warfacegod laughs up his sleeve at mentioning Windows acting in anyway.)








Chocolate Ubuntu Mocha Blend: I ***HATE!!!!*** chocolate!


If warfacegod is acting dodgy then I'm wondering if this might be hardware.


(warfacegod laughs up his sleeve at mentio..... circles go round, go round, go round, go round, go round, go round, go round, go round........

_

---

### Post by willowave on 2010-02-01
> **warfacegod said:**
> If warfacegod is acting dodgy then I'm wondering if this might be hardware.
 
 
(warfacegod laughs up his sleeve at mentio..... circles go round, go round, go round, go round, go round, go round, go round, go round........
 
_
LOL nice. Losing it are we?

---

### Post by Leppie on 2010-02-01
> **willowave said:**
> ***. lol
EDIT:***** lol
OMG LOL I called you a donkey and it stars it? wow. child safe area huh?
 
wait ...does it star "****"?
LMAO...yep. the "english version"
that's for calling me names... :P

---

### Post by warfacegod on 2010-02-01
> **willowave said:**
> LOL nice. Losing it are we?

Many years ago. If my writing is any indicator, I'm the most monstrously insane human being the Earth has ever known.

---

### Post by Leppie on 2010-02-01
> **willowave said:**
> I'm trying to decide what to install next. I figured I'd try something that I haven't tried since nothing seems to work anyways.
try dream linux?

---

### Post by Leppie on 2010-02-01
> **warfacegod said:**
> Many years ago. If my writing is any indicator, I'm the most monstrously insane human being the Earth has ever known.
isn't that "used to be"? not sure it's possible to be human and a deity at the same time...

---

### Post by warfacegod on 2010-02-01
> **Leppie said:**
> isn't that "used to be"? not sure it's possible to be human and a deity at the same time...

Of course it is. Ishtar, Jesus, Vishnu, Julius Caesar, Lemmy Kilmister....

---

### Post by Leppie on 2010-02-01
> **warfacegod said:**
> Of course it is. Ishtar, Jesus, Vishnu, Julius Caesar, Lemmy Kilmister....
those are not even real gods... :P

---

### Post by warfacegod on 2010-02-01
> **Leppie said:**
> those are not even real gods... :P

Do not disparage The Lemmy.

---

### Post by Leppie on 2010-02-01
> **warfacegod said:**
> Do not disparage The Lemmy.
well, him i'll reconsider... ;)
but all those other wanna-be deities...

---

### Post by willowave on 2010-02-01
> **Leppie said:**
> try dream linux?
never heard of it...I'm going to try that and PC-BSD next.

---

### Post by Leppie on 2010-02-01
poor lil netbook... :P

---

### Post by warfacegod on 2010-02-01
> **Leppie said:**
> well, him i'll reconsider... ;)
but all those other wanna-be deities...

Not Vishnu? Destroyer god and all that?

---

### Post by warfacegod on 2010-02-01
> **willowave said:**
> never heard of it...I'm going to try that and PC-BSD next.

Might be wise to check your hard drive for errors.

```
sudo apt-get install gsmartcontrol
```

Use the longest test.

---

### Post by Leppie on 2010-02-01
> **warfacegod said:**
> Not Vishnu? Destroyer god and all that?
destroyer of what? silly pictures?

---

### Post by warfacegod on 2010-02-01
> **Leppie said:**
> destroyer of what? silly pictures?

Hairbands at the very least. Although, the destroying part doesn't seem to have been all that great. They're all doing reunion tours now. ...Stupid Destroyer god.

---

### Post by Leppie on 2010-02-01
> **warfacegod said:**
> Hairbands at the very least. Although, the destroying part doesn't seem to have been all that great. They're all doing reunion tours now. ...Stupid Destroyer god.
see, there you go... just wanna-be deities....

---

### Post by warfacegod on 2010-02-01
> **Leppie said:**
> see, there you go... just wanna-be deities....

Didn't the Ramones write a song about that?

---

### Post by Leppie on 2010-02-01
> **warfacegod said:**
> Didn't the Ramones write a song about that?
could be, don't remember... never really was that much into the ramones...

---

### Post by willowave on 2010-02-02
you guys are showing your age. lol

---

### Post by warfacegod on 2010-02-02
> **willowave said:**
> you guys are showing your age. lol

I'm only 30.


(In this embodiment.)

---

### Post by audiomick on 2010-02-02
> **warfacegod said:**
> I'm only 30.


(In this embodiment.)

Oh, to be young again!

---

### Post by warfacegod on 2010-02-02
> **audiomick said:**
> Oh, to be young again!

Try working in Construction and Remodeling 11 years. See how young you feel at 30.

Carpal Tunnel
Twisted L4 & L5 vertebrate
Several mildly arthritic joints
Weak rotator cuff
Bad knee
Slight tinnitus from being young and stupid about ear protection that mysteriously gets worse whenever my wife walks in the room

---

### Post by audiomick on 2010-02-02
> **warfacegod said:**
> Try working in Construction and Remodeling 11 years. See how young you feel at 30.

Carpal Tunnel
Twisted L4 & L5 vertebrate
Several mildly arthritic joints
Weak rotator cuff
Bad knee
Slight tinnitus from being young and stupid about ear protection that mysteriously gets worse whenever my wife walks in the room

OUCH!
I haven't noticed a connection between my tinnitus (same cause...) and my girlfriend. I will have to observe that closely....

---

### Post by warfacegod on 2010-02-02
> **audiomick said:**
> OUCH!
I haven't noticed a connection between my tinnitus (same cause...) and my girlfriend. I will have to observe that closely....

Observing closely would involve not paying attention, in this case.

---

### Post by Leppie on 2010-02-02
> **willowave said:**
> you guys are showing your age. lol
lol - how "young" are you? :P

---

### Post by Leppie on 2010-02-02
> **warfacegod said:**
> Observing closely would involve not paying attention, in this case.
the oldest human paradigm...

---

### Post by audiomick on 2010-02-02
> **Leppie said:**
> lol - how "young" are you? :P

45. A few grey hairs, but not doing too bad...

---

### Post by warfacegod on 2010-02-02
> **audiomick said:**
> 45. A few grey hairs, but not doing too bad...

I've got a few in my beard. I want more. I'm gonna be a cranky old man. I'll rig up a slant six engine to my wheelchair.

---

### Post by audiomick on 2010-02-02
> **warfacegod said:**
> I'll rig up a slant six engine to my wheelchair.

With a blower and nitrous injection, I hope...

---

### Post by Leppie on 2010-02-02
> **audiomick said:**
> With a blower and nitrous injection, I hope...
what fun is it without these? :P

---

### Post by warfacegod on 2010-02-02
> **audiomick said:**
> With a blower and nitrous injection, I hope...

...and a small thermonuclear reactor cannon.

---

### Post by willowave on 2010-02-02
*intentionally ignoring the age question*
Guess what? The damn wireless was disabled in the BIOS!!? How does THAT happen????
I installed windows and it still woiuldn't work. So I called Asus, and they had me reset the defaults in the bios. 
And now its working. 
WTH???

---

### Post by Leppie on 2010-02-02
> **willowave said:**
> *intentionally ignoring the age question*
that's what all women do...


> **willowave said:**
> Guess what? The damn wireless was disabled in the BIOS!!? How does THAT happen????
that's what i was suggesting a while ago...

> **willowave said:**
> I installed windows and it still woiuldn't work. So I called Asus, and they had me reset the defaults in the bios. 
And now its working. 
WTH???
well, at least your unr will run properly again as well...
they didn't tell you by any change which option to change specifically? resetting all the bios is a bit radical just to get wireless back... could be you personally haven't made any changes there, but still....

---

### Post by willowave on 2010-02-02
> **Leppie said:**
> 
that's what i was suggesting a while ago...
 
well, at least your unr will run properly again as well...
they didn't tell you by any change which option to change specifically? resetting all the bios is a bit radical just to get wireless back... could be you personally haven't made any changes there, but still....
 
well I guess I figured if _ I _ didn't go into the BIOS and mess with anything then it wasn't really something I needed to worry about. So I didn't give it a second thought. 
I think I might go and poke into the BIOS a bit more so I know exactly WHAT the default settings are, so if next time I see that not working, I might notice something different if I go look at it. I've only had the netbook 4 months so I haven't really poked around a whole lot. 
 
Hmmm...so now what to do...

---

### Post by Leppie on 2010-02-02
> **willowave said:**
> well I guess I figured if _ I _ didn't go into  the BIOS and mess with anything then it wasn't really something I needed  to worry about. So I didn't give it a second thought.
most systems nowadays can access the bios or parts of it.

> **willowave said:**
> Hmmm...so now what to do...
tell us your age... :P

---

### Post by warfacegod on 2010-02-02
> **Leppie said:**
> most systems nowadays can access the bios or parts of it.


tell us your age... :P

She'll just give us a window of 23 - 45.

---

### Post by warfacegod on 2010-02-02
What kind of netbook do you have?

---

### Post by willowave on 2010-02-02
> **Leppie said:**
> most systems nowadays can access the bios or parts of it.
tell us your age... :P
 
apparently I'm old enough to not know that systems these days can do that. I'm 39. 
Yuck. I don't like saying that outloud. Or seeing it in text for that matter.

---

### Post by Leppie on 2010-02-02
> **willowave said:**
> apparently I'm old enough to not know that systems these days can do that. I'm 39. 
Yuck. I don't like saying that outloud. Or seeing it in text for that matter.
is that so bad? i'm actually 37...

---

### Post by warfacegod on 2010-02-02
Ack! Geezers everywhere!

---

### Post by Leppie on 2010-02-02
> **warfacegod said:**
> Ack! Geezers everywhere!
where??? where/??

---

### Post by warfacegod on 2010-02-02
> **Leppie said:**
> where??? where/??

Over there!!!! Quick! You hide behind me and I'll hide behind you and nobody will see us!

---

### Post by Leppie on 2010-02-02
> **warfacegod said:**
> Over there!!!! Quick! You hide behind me and I'll hide behind you and nobody will see us!
kewl, sounds like a plan :)
thanks for your help :D

---

### Post by warfacegod on 2010-02-02
> **Leppie said:**
> kewl, sounds like a plan :)
thanks for your help :D

No problem my friend. Avoiding geezers is an ever vigilant duty. Except Geezer Butler.

---

### Post by audiomick on 2010-02-02
here, I have drawn up some construction plans[ATTACH]145775[/ATTACH]

---

### Post by warfacegod on 2010-02-02
> **audiomick said:**
> here, I have drawn up some construction plans

Crap! audiomick saw us!

---

### Post by audiomick on 2010-02-02
> **warfacegod said:**
> Crap! audiomick saw us!

no I didn't, I couldn't see you past each other....

---

### Post by warfacegod on 2010-02-02
> **audiomick said:**
> here, I have drawn up some construction plans[ATTACH]145775[/ATTACH]

I'm noticing a complete and utter *lack* of a steering wheel. I suppose the helmet is compensation for that?

---

### Post by audiomick on 2010-02-02
> **warfacegod said:**
> I'm noticing a complete and utter *lack* of a steering wheel. I suppose the helmet is compensation for that?

You steer a wheel chair by braking the wheel on the inside of the corner.
The helmet is just for intimidating other drivers.

---

### Post by warfacegod on 2010-02-02
> **audiomick said:**
> You steer a wheel chair by braking the wheel on the inside of the corner.
The helmet is just for intimidating other drivers.

I was thinking that a bald man with long white hair would be intimidating enough. Besides, smacking their hovercars with my cane aught to do the job as well.

---

### Post by audiomick on 2010-02-02
> **warfacegod said:**
> ... a bald man with long white hair... 

I'd be scared. I'd be thinking "that guy is bald, so whose hair has he got?"

 > Besides, smacking their hovercars with my cane aught to do the job as well.

You could be right there. Riding a motorbike has taught me that people really don't want to scratch their nice shiny cars. They get out of your way if you push the point...

---

### Post by willowave on 2010-02-02
> **audiomick said:**
> I'd be scared. I'd be thinking "that guy is bald, so whose hair has he got?"
 
 
You could be right there. Riding a motorbike has taught me that people really don't want to scratch their nice shiny cars. They get out of your way if you push the point...
 Typically I'm more concerned I'd kill the guy on the motorcycle if I'm not careful. Not so concerned about my car. lol Motorcycle riders are easily sqiushable if they end up on the ground.

---

### Post by Leppie on 2010-02-02
> **audiomick said:**
> no I didn't, I couldn't see you past each other....
so how did you found us?
was i sneezing too loudly?

---

### Post by warfacegod on 2010-02-02
> **Leppie said:**
> so how did you found us?
was i sneezing too loudly?

It must be me. I haven't laundered my mana for a few days.

---

### Post by audiomick on 2010-02-02
> **warfacegod said:**
> It must be me. I haven't laundered my mana for a few days.

That's what that is. I've been wondering. I thought it was the cat....

---

### Post by warfacegod on 2010-02-02
> **audiomick said:**
> I'd be scared. I'd be thinking "that guy is bald, so whose hair has he got?"

 
You could be right there. Riding a motorbike has taught me that people really don't want to scratch their nice shiny cars. They get out of your way if you push the point...

Bald on top. Bald as a coot. Codger bald.

---

### Post by Leppie on 2010-02-02
> **warfacegod said:**
> Bald on top. Bald as a coot. Codger bald.
man, scary crap indeed...

---

### Post by audiomick on 2010-02-02
> **Leppie said:**
> man, scary crap indeed...

what, going bald?

---

### Post by Leppie on 2010-02-02
> **audiomick said:**
> what, going bald?
going bald with long white hair...

---

### Post by audiomick on 2010-02-02
> **Leppie said:**
> going bald with long white hair...

hair dye? Then it wont be white at least....

---

### Post by warfacegod on 2010-02-02
I want it white. Probably some gray too.

---

### Post by audiomick on 2010-02-02
> **warfacegod said:**
> I want it white. Probably some gray too.

peroxide.

---

### Post by warfacegod on 2010-02-02
> **audiomick said:**
> peroxide.

The only "body altering/adornment" I have (or will do) is a pierced leg. Bullet went in and back out the other side. Buddy of mine said I should put a turkey leg bone in it.

---

### Post by willowave on 2010-02-02
> **warfacegod said:**
> The only "body altering/adornment" I have (or will do) is a pierced leg. Bullet went in and back out the other side. Buddy of mine said I should put a turkey leg bone in it.
did you shoot back?

---

### Post by warfacegod on 2010-02-02
> **willowave said:**
> did you shoot back?

I'm the one that *did* the shooting.

---

### Post by Leppie on 2010-02-03
> **warfacegod said:**
> I'm the one that *did* the shooting.
you're a real einstein... :P

---

### Post by willowave on 2010-02-03
> **warfacegod said:**
> I'm the one that *did* the shooting.
LMAO...how'd you shoot yourself in the leg?

---

### Post by Leppie on 2010-02-03
> **willowave said:**
> LMAO...how'd you shoot yourself in the leg?
a redneck has illimitate ways of shooting himself in the any body part... ;)

---

### Post by audiomick on 2010-02-03
> **Leppie said:**
> a redneck has illimitate ways of shooting himself in the any body part... ;)
you know the saying: If it  moves, shoot it, if it isn't moving, push it so it moves....

---

### Post by warfacegod on 2010-02-03
> **audiomick said:**
> you know the saying: If it  moves, shoot it, if it isn't moving, push it so it moves....

Murphy's Law #23:

> Body count math is: two guerrillas plus three chickens plus two pigs = 37 enemy killed.

---

### Post by willowave on 2010-02-03
> **audiomick said:**
> you know the saying: If it moves, shoot it, if it isn't moving, push it so it moves....
LOL I've never heard that saying but being from South Dakota...or just the US in general, it's very relevant to like 90% of the male population.
*lives in hickville*

---

### Post by audiomick on 2010-02-03
> **willowave said:**
> LOL I've never heard that saying but being from South Dakota...or just the US in general, it's very relevant to like 90% of the male population.
*lives in hickville*
It used to apply to a lot of the country areas in Australia too, or the variation "If it moves, shoot it, if it doesn't, cut it down".

---

### Post by warfacegod on 2010-02-03
Yeeeeehhhaaaaaa!


Over hill and over dale,
We're always on the Redneck trail,
Hunting rocks and needing bail,
And a double shot of whiskey!

---

### Post by audiomick on 2010-02-03
> **warfacegod said:**
> Yeeeeehhhaaaaaa!


Over hill and over dale,
We're always on the Redneck trail,
Hunting rocks and needing bail,
And a double shot of whiskey!
I guess that's probably not a manowar song?

---

### Post by warfacegod on 2010-02-03
> **audiomick said:**
> I guess that's probably not a manowar song?

Only in so far as that I am a man o' war.

---

### Post by willowave on 2010-02-04
21 hours without a post on this thread? We aren't going to let it go dead are we?

---

### Post by willowave on 2010-02-04
You never mentioned your mythbuntu thingy and how that worked out. I have a system sitting here waiting for me to make it work lol

---

### Post by audiomick on 2010-02-04
> **willowave said:**
> 21 hours without a post on this thread? We aren't going to let it go dead are we?
was wondering the same thing myself....
as for the mythubuntu thingy: As far as I know, the laptop was revived, but wfg hasn't said much about it the last few days. He's probably broken it again...;)

---

### Post by willowave on 2010-02-04
I at least can report that whole goal from the start of MY post anyways...I have ubuntu running on my eee pc. Wireless and all. 
Going to try really hard to NOT muck it up. Definitely won't be plugging a second monitor into it. Since that was really when the problems started.

---

### Post by willowave on 2010-02-04
What exactly does adding backports to the updater give a person? Anything needed?

---

### Post by willowave on 2010-02-04
> **audiomick said:**
> was wondering the same thing myself....
as for the mythubuntu thingy: As far as I know, the laptop was revived, but wfg hasn't said much about it the last few days. He's probably broken it again...;)
so do you know if he has mythbuntu ON the laptop? is that what he's been working on? I have mine on an old HP. But I keep running into a weird issue where it shows it has a 192 IP but when I try to update/get guides it's trying to pull it with a 160. addy. I know there is a frontend and a backend on it. 
I've been too busy tryin to fix the Eee PC to mess with it.

---

### Post by Leppie on 2010-02-04
> **willowave said:**
> What exactly does adding backports to the updater give a person? Anything needed?
it adds the testing repository... all kinds of unstable packages... ideal for breaking a system ;)

---

### Post by Leppie on 2010-02-04
> **willowave said:**
> so do you know if he has mythbuntu ON the laptop? is that what he's been working on? I have mine on an old HP. But I keep running into a weird issue where it shows it has a 192 IP but when I try to update/get guides it's trying to pull it with a 160. addy. I know there is a frontend and a backend on it. 
I've been too busy tryin to fix the Eee PC to mess with it.
i believe he installed mythbuntu over unr to then install moblin over it...
so it would be a unmmr... :lolflag:

---

### Post by warfacegod on 2010-02-04
> **willowave said:**
> You never mentioned your mythbuntu thingy and how that worked out. I have a system sitting here waiting for me to make it work lol

No, nothing shall die, unless it is killed. I scraped Mythbuntu. Details at 11!

---

### Post by willowave on 2010-02-04
> **Leppie said:**
> it adds the testing repository... all kinds of unstable packages... ideal for breaking a system ;)
 mmmm, think I will stay away from that for awhile. Give my poor netbook a break. Tho...if I was going to kill it I should do it while it's still under warrenty.

---

### Post by willowave on 2010-02-04
You know, this is a nice lookin distro. I might try this one out too. On the USB only for now. lol [http://chakra-project.org/](http://chakra-project.org/)
Anybody know anything about setting up a home media center/streaming content from a PC? Specially to a PS3.
Yeah that would be another thread but I figured I'd ask you guys first. lol

---

### Post by warfacegod on 2010-02-04
> **willowave said:**
> You know, this is a nice lookin distro. I might try this one out too. On the USB only for now. lol [http://chakra-project.org/](http://chakra-project.org/)
Anybody know anything about setting up a home media center/streaming content from a PC? Specially to a PS3.
Yeah that would be another thread but I figured I'd ask you guys first. lol

Why stream to the PS3? Last time I looked, Sony wasn't voiding the warrantees on the PS3 if you install Ubuntu directly onto it.

---

### Post by Leppie on 2010-02-04
why does everybody want to stream to a  ps3???
did you buy a console, or just a degraded pc?

---

### Post by warfacegod on 2010-02-04
> **audiomick said:**
> was wondering the same thing myself....
as for the mythubuntu thingy: As far as I know, the laptop was revived, but wfg hasn't said much about it the last few days. He's probably broken it again...;)

I have not!

---

### Post by Leppie on 2010-02-04
> **warfacegod said:**
> I have not!
well, i for one am glad you haven't broken it (again and yet). ;)

---

### Post by warfacegod on 2010-02-04
> **Leppie said:**
> well, i for one am glad you haven't broken it (again and yet). ;)

To you mean to say that you wouldn't derive immense pleasure from jabbing me for breaking my laptop again?

---

### Post by audiomick on 2010-02-04
> **warfacegod said:**
> To you mean to say that you wouldn't derive immense pleasure from jabbing me for breaking my laptop again?
Come on, we're not like that....
Or, as a mate of mine is fond of saying "I resemble that comment!"

---

### Post by willowave on 2010-02-04
> **warfacegod said:**
> Why stream to the PS3? Last time I looked, Sony wasn't voiding the warrantees on the PS3 if you install Ubuntu directly onto it.
 HA...my husband would KILL me if I did that. Thats why I have the Eee, so I can break my own stuff. I also have a PSP that I was thinking about hacking. But the E is more functional. 
Altho he is the one that brought up the other day that you could put linux on it. I was surprised he'd even tell me that. lol But I wouldn't mess with it, cuz we stream netflix from it and use it several times a day. I don't have time to fix something that we deem "neccesary" in our household. lol

---

### Post by Leppie on 2010-02-04
> **willowave said:**
> I don't have time to fix something that we deem "neccesary" in our household. lol
so the ps3 is something you would mess up? :P

---

### Post by willowave on 2010-02-04
> **Leppie said:**
> why does everybody want to stream to a ps3???
did you buy a console, or just a degraded pc?
I actually wanted to stream the movies that I have on my main PC to the PS3. 
See we have a nice big TV, and a PS3. We also have Netflix, which you can stream only the dvds that they say you can (instant movies)
But I rip movies when I get them and send them back.  
I want to be able to sit on the couch and watch movies on the big TV instead of sitting in the computer chair at the monitor. Hard for us all to watch movies crowded around the computer, too.
And just so I can say I can do it. :D

---

### Post by willowave on 2010-02-04
> **Leppie said:**
> so the ps3 is something you would mess up? :P
LOL pfft yeah, I mess everything up. If I am workin on the computer or something is unhooked from where it usually is at, the first thing my husband asks is "So what did you break now?"
Hence lots of spare computers in the house. I cleaned most of them out and tossed em tho.

---

### Post by Leppie on 2010-02-04
and netflix cannot stream images from disk?

---

### Post by Leppie on 2010-02-04
> **willowave said:**
> LOL pfft yeah, I mess everything up. If I am workin on the computer or something is unhooked from where it usually is at, the first thing my husband asks is "So what did you break now?"
Hence lots of spare computers in the house. I cleaned most of them out and tossed em tho.
if you have too many spare parts, send some to wfg and me :D

---

### Post by warfacegod on 2010-02-04
So that's where all the spare parts have been disappearing to,..your house!

---

### Post by warfacegod on 2010-02-04
Leppie's not kidding. We need parts. (No pun intended.)

---

### Post by Leppie on 2010-02-04
> **warfacegod said:**
> So that's where all the spare parts have been disappearing to,..your house!
maybe we should organize a raid to reclaim what's ours... :biggrin:

---

### Post by willowave on 2010-02-04
> **Leppie said:**
> if you have too many spare parts, send some to wfg and me :D
 Let me know what you need...they are all pretty old but I have a big bin of parts I stripped out of old computer. Tell me what you are looking for and I'll see if I have it. 
Old ram, vid cards, sound cards...hard drives not so much tho.

---

### Post by willowave on 2010-02-04
> **warfacegod said:**
> Leppie's not kidding. We need parts. (No pun intended.)
 Yeah well you will when you go around shooting them. :P lol

---

### Post by warfacegod on 2010-02-04
I shot my leg not my parts.

---

### Post by Leppie on 2010-02-04
> **willowave said:**
> Yeah well you will when you go around shooting them. :P lol
i'm sure he'd miss his parts... :P

---

### Post by warfacegod on 2010-02-04
> **Leppie said:**
> i'm sure he'd miss his parts... :P

I wood! I wood!

---

### Post by Leppie on 2010-02-04
> **warfacegod said:**
> I wood! I wood!
that's because of all the heavy-metal... :P

---

### Post by audiomick on 2010-02-04
> **warfacegod said:**
> Leppie's not kidding. We need parts. (No pun intended.)
I can see it now: In secret workshops using harmless seeming  discarded computer parts. Building the machine in seperate parts so it wont be recognised if it is discovered, commucating using coded threads on the Ubuntu forums, till finally they come together and unite in the last[SIZE=2] step to [SIZE=3]total world[SIZE=5] domination!!! MWAHAAHAHAHAHAHA!!!!!
[SIZE=1]wait a minute, what am I laughing for?[/SIZE]
[/SIZE][/SIZE][/SIZE]

---

### Post by willowave on 2010-02-04
LOL!! nice

---

### Post by Leppie on 2010-02-04
> **audiomick said:**
> I can see it now: In secret workshops using harmless seeming  discarded computer parts. Building the machine in seperate parts so it wont be recognised if it is discovered, commucating using coded threads on the Ubuntu forums, till finally they come together and unite in the last[SIZE=2] step to [SIZE=3]total world[SIZE=5] domination!!! MWAHAAHAHAHAHAHA!!!!!
[SIZE=1]wait a minute, what am I laughing for?[/SIZE]
[/SIZE][/SIZE][/SIZE]
shoot... he unveiled our cunning plan...

---

### Post by warfacegod on 2010-02-04
> **Leppie said:**
> shoot... he unveiled our cunning plan...

Look at his Avatar. He's blatantly announcing to the world his vile scheme to kill me.

---

### Post by warfacegod on 2010-02-04
> **Leppie said:**
> that's because of all the heavy-metal... :P

Remember the Gospel according to Manowar.

The Gods made heavy metal,
And they saw that it was good,
They said to play it louder than Hell,
And we promised that we would,

---

### Post by Leppie on 2010-02-04
> **warfacegod said:**
> Remember the Gospel according to Manowar.

The Gods made heavy metal,
And they saw that it was good,
They said to play it louder than Hell,
And we promised that we would,
:guitar:

---

### Post by warfacegod on 2010-02-04
](*,) <<<Headbanging mayhem action!

---

### Post by Leppie on 2010-02-04
we're creeping towards 2k!!! :D

---

### Post by audiomick on 2010-02-04
I can see I have got some catching up to do... :(

---

### Post by Leppie on 2010-02-04
> **audiomick said:**
> I can see I have got some catching up to do... :(
that's cos you're always trying to reproduce other peoples troubles... :P

---

### Post by warfacegod on 2010-02-04
Race you there!

---

### Post by audiomick on 2010-02-04
> **warfacegod said:**
> Race you there!
Easy to say when you're ahead!

---

### Post by Leppie on 2010-02-04
> **audiomick said:**
> Easy to say when you're ahead!
i'll race you there as well :P

---

### Post by audiomick on 2010-02-04
> **Leppie said:**
> i'll race you there as well :P
I wont make it tonight, anyway. Goodnight...
(one more ;) )

---

### Post by warfacegod on 2010-02-04
Nobody likes a quiter.:-({|=:tongue:

---

### Post by Leppie on 2010-02-04
> **audiomick said:**
> I wont make it tonight, anyway. Goodnight...
(one more ;) )
bad loser... :P

---

### Post by warfacegod on 2010-02-04
You think we should quit for a day (week) or two to let him catch up?

---

### Post by Leppie on 2010-02-04
> **warfacegod said:**
> You think we should quit for a day (week) or two to let him catch up?
you think it would be enough?
i remember when i saw his post count the first time, he was like 1000 ahead of me... :lolflag:

---

### Post by overdrank on 2010-02-04
Thread has drifted way off topic. Thread closed.

---

