---
title: "Toshiba Satellite A50, 512 MB memory"
date: 2015-01-25
forum: New to Ubuntu
---

### Post by kate315 on 2015-01-25
I'm new to the forum but not completely new to Linux and last year I was pleased to revive a very old (2003?)Toshiba laptop by installing Ubuntu 10.10.  It appears to access the internet quite well but I worry that I might pick up something or other that I might transfer to a newer computer. 

My questions are:

Should I stay off the net with it?

Is there any more recent version of Linux that might run equally well on such an old laptop?  It has 512mb of RAM - the maximum possible.

---

### Post by mörgæs on 2015-01-25
Hi, welcome to the fora.

It's a classic question and the classic answer is install Lubuntu 14.04.1 or 14.10. If you want to know more about the matter please see the link in my signature.

---

### Post by coffeecat on 2015-01-25
> **kate315 said:**
> Should I stay off the net with it?

Unequivocally, yes.

Ubuntu 10.10 went end-of life in April 2012 and there have been no updates, including security patches, since then. You are running a vulnerable system.

> **kate315 said:**
> Is there any more recent version of Linux that might run equally well on such an old laptop?  It has 512mb of RAM - the maximum possible.

I would agree with  mörgæs about installing Lubuntu.

[http://lubuntu.net/](http://lubuntu.net/)

You have the choice of the LTS 14.04 (now 14.04.1) supported until April 2017, or the newer release 14.10 which is only supported for 9 months, that is until July 2015. If you do go for 14.10, be mindful that you would need to upgrade or re-install in about 6 months time. The 14.04.1 point release is now available. There was a bug in 14.04 which meant that the network manager icon often didn't appear. This was easily fixed but was an inconvenience. I don't know whether this was fixed in the 14.04.1 point release, but something to be aware of.

---

### Post by yancek on 2015-01-25
Other non-Ubuntu Linux systems which should work on your hardware are AntiX and the different variations of Puppy Linux.  They are both very different from Ubuntu however.

---

### Post by mörgæs on 2015-01-25
> **coffeecat said:**
> I don't know whether this was fixed in the 14.04.1 point release

Yes, it's fixed in 14.04.1.

---

### Post by kate315 on 2015-01-27
Thanks to all who replied.  I've printed out the suggestions and I'll work my way through them.  I'm not particularly hopeful because I tried installing Mint and other versions of Ubuntu before I found something that actually worked.  One (possibly Mint?) seemed okay but the screen was split.

Maybe I'll just have to keep the laptop isolated and enjoy the novelty of it working at all.  The keyboard stopped working with XP years ago.

---

### Post by Bucky Ball on 2015-01-27
Try the recent 14.04 Lubuntu release, as suggested. Run it from the Live install disk/USB and see how you go. Sounds like you tried the other flavours of Ubuntu some time ago. Things change and you might find Lubuntu now works.

---

### Post by kc1di on 2015-01-27
I have successfully run Lubuntu on a machine as old as that , but it will depend alot on the hardware present.  
10.10 has not been supported for a long time and will be vunerable to security flaws. 

though it's not ubuntu by any means Puppy Linux usually will run quite well on an older machine and you don't even have to install it to the hard drive. 
just a thought :)

---

### Post by mörgæs on 2015-01-27
Puppy is a fine little distro but maybe less user friendly than Lubuntu.

Kate315, if you want a more precise answer please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags. You can do it from the old 10.10 install.

---

### Post by kate315 on 2015-01-27
**Satellite A50-105**

**Part number: PSA50E-06S02HEN**


[LIST]
[*]Windows® XP Home Edition
[*]Mobile [Intel® Celeron® M Processor]("http://www.intel.com/products/processor/celeron/index.htm") 340
[*]14.1 ", TFT colour display
[*]Hard disk 40 GB
[*]256 MB, DDR RAM
[*]maximum life : up to 4.0 (Mobile Mark&#8482;) hours
[*]weight : 2.6 kg
[*]W x D x H : 338 x 274 x 27 (front) / 38 (back) mm
[/LIST]

Hardware as above other than RAM which is now 512mb.

---

### Post by kate315 on 2015-01-27
I'll try that but I'm not so great with the command line.

---

### Post by sudodus on 2015-01-27
I think this Celeron M processor has PAE capability but lacks PAE flag.

1. You can run distros and re-spins based on Ubuntu 14.04.1 LTS, if you use the boot option **forcepae**. Try **Lubuntu 14.04.1 LTS** as the first alternative. See this link

[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M)

2. You can run distros and re-spins based on Ubuntu 12.04 LTS, if  you use a system based on the original 12.04 LTS non-pae kernel for  example ***Bodhi*** linux or ***LXLE***.

3. You can try some really light-weight linux alternatives, ***Wary Puppy***, ***TahrPup*** or ***Tiny Core***. These are different from Ubuntu based distros, but might work better in such an old computer, with only 512 MB RAM. Try live, and after trying install, if you find a system that works well for you :-)
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

---

### Post by kate315 on 2015-01-27
I'm not getting a reply to:

sudo lshw -sanitize > lshw.txt

I think I'm logged in as root.  I think it's asking me what format I want the text in.

---

### Post by sudodus on 2015-01-27
try like this:

```
sudo -s
lshw -sanitize > lshw.txt
exit  # exit from the superuser shell
```

And then you can attach the file **lshw.txt** to a reply post: Go Advanced, click on Manage Attachments ...

---

### Post by Mike_Walsh on 2015-01-27
> **kc1di said:**
> I have successfully run Lubuntu on a machine as old as that , but it will depend alot on the hardware present.  
10.10 has not been supported for a long time and will be vunerable to security flaws. 

though it's not ubuntu by any means Puppy Linux usually will run quite well on an older machine and you don't even have to install it to the hard drive. 
just a thought :)

+1 to that!

@Kate; I have for the last 3 months been running the newest version of Puppy Linux, Tahrpup 6.0, on an even older machine than yours, and it runs very sweetly.

My old Dell lappie is 2002 vintage, has an older Celeron than yours, same size hard drive, but twice the RAM (1 GB).

As others have said, Puppy IS somewhat different to the main 'buntu flavours....but for some years now, all the Puppy releases have been based on their current Ubuntu counterparts.....so they have access to all the Ubuntu & Debian repositories.

And as kc1di has pointed out, with the Puppies, you don't even have to install to your hard drive. You can install them to a flash drive (anywhere from 4-8 GB is plenty big enough), because with Puppy, the whole thing is SO small that it sits completely in RAM memory.....and the O/S periodically saves everything to your personal 'save-file' on the flash drive (about every half hour or so, usually). This is to prolong the life of the flash drive.

Tahrpup has a feature called 'Quickpet', which allows you to install a range of popular apps & programs with a single click; makes installation and set-up a doddle. In fact, Tahrpup runs SO well on the old Dell that I have it set-up for file-sharing and network printing, too!

If you're interested, you can find the .iso file on [this page]("http://distro.ibiblio.org/puppylinux/puppy-tahr/iso/tahrpup%20-6.0-CE/"):-

You want the 4th entry from the bottom; tahr-6.0-CE_PAE.iso. According to[ this page]("http://ark.intel.com/products/27141/Intel-Celeron-M-Processor-340-512K-Cache-1_50-GHz-400-MHz-FSB"), from Intel themselves, PAE is enabled for 32-bit extensions, which your CPU certainly has. If not, go for the NoPAE version; both are available.

Download, burn, and run from CD just like an Ubuntu LiveCD.

If you need help. visit the Puppy Forums:-

[http://www.murga-linux.com/puppy/index.php](http://www.murga-linux.com/puppy/index.php)

There's nothing these lads and lasses DON'T know about Puppy...and they are EXTREMELY helpful. There's a current thread running which explains to new users EXACTLY how to install Tahrpup to a flash drive.....in nice, plain English..!

Just my suggestion! Hope it helps you to decide what you want to do.


Regards,

Mike.

BTW; DO take note of sudodus's suggestions.....he knows what he's talking about.

---

### Post by monkeybrain20122 on 2015-01-27
I had a laptop which was that old (with 512 M of ram) Couldn't run anything on it newer than lubuntu 12.04. You may want to check out lxle [http://lxle.net/](http://lxle.net/) which is a community maintained 'LTS' spin of lubuntu 12.04, or Debian stable which is also old. 


But puppy Linux is probably best for weak hardware like that.

---

### Post by kate315 on 2015-01-27
After a bit of a struggle I've got the hardware text.  It's rather long.   I've also downloaded Lubuntu 14.04 LTS but I'm starting to think that something lighter might be better.  Thanks for the replies.

---

### Post by kate315 on 2015-01-28
The Lubuntu 14.04 LTS attempted install resulted in a message saying roughly:

"PAE disabled 'force pae' is unsupported, may cause unknown problems and will taint the kernel.  Please use a kernel appropriate to CPU."

I was somewhat discouraged by that especially as I managed to crash the laptop rather badly when trying to exit from the install.  It took 3 attempts to make a CD that was readable by the laptop.  (A possible CD drive reading fault??  Sometimes music CDs skip on it although they play okay elsewhere.  I didn't have any success making bootable flash drives when I tried some time ago.)

I'm prepared to persist with this and maybe try something else but a quick look through the other suggestions doesn't inspire me much.  They seem to have too many features for me.  I'm happy with the basic features of the Ubuntu 10.10 that I have.  My previous experience of Linux in the late '90s was of RedHat, Caldera and KDE on some sort of low powered Pentium.  I abandoned them mostly because the fonts in those days were too hard on my eyes.

Apologies for rambling but most of it is relevant.  How much of the hardware text would it be appropriate to post?  (Assuming I can get the CODE tag to work.)

---

### Post by Bucky Ball on 2015-01-28
If you're happy with 10.10, by all means stick with it. Just keep it offline and be aware that very few of us here can give you much help with it. 

Did I already mention the mini.iso? You could try that (you need to be online with a cable) and just install a lightweight desktop environment (lxde? xfce?) and the apps you want. That way you can get it very pared back, especially if all you do is surf the net and listen to music with the dinky old beast. 

Here's some links for the mini.iso. It can take awhile to install, depending on your connection, but just installs the Ubuntu kernel, nothing else. You add the rest via 'sudo apt-get install' (as at the end of the install you only have a CLI), and in your case, that wouldn't be a lot. ;)

Minimal Install page:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Older, but info still relevant while screenshots might be a bit different now:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

Good luck if you go that way. I've resurrected a number of decrepit old things using that method. ;)

---

### Post by sudodus on 2015-01-28
> **kate315 said:**
> The Lubuntu 14.04 LTS attempted install resulted in a message saying roughly:

"PAE disabled 'force pae' is unsupported, may cause unknown problems and will taint the kernel.  Please use a kernel appropriate to CPU."

I was somewhat discouraged by that especially as I managed to crash the laptop rather badly when trying to exit from the install  ...


We are many people who run or have run Lubuntu and in some cases Xubuntu with forcepae (14.04 LTS) and fakepae (previous versions) in Pentium M and Celeron M processors. See this link

[https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)

I have an IBM Thinkpad T42 with a Pentium M CPU of 1.7 GHz, I run it and I have done a lot of testing, so I'm not worried using a PAE kernel with Pentium M and Celeron M. It is really too bad if that warning will keep you away from using a modern version of Lubuntu (14.04.1). But if that is the case I recommend that you try a community re-spin based on Ubuntu 12.04 LTS with a ***non-pae*** kernel: ***Bento***, ***Bodhi*** or ***LXLE***. Those re-spins promise support until April 2017.

---

### Post by kate315 on 2015-01-28
I'm not sure what is relevant from the hardware text.  "Decrepit old thing" as mentioned above probably summarises it.  I can supply more text if necessary.  It reads as if I might in theory be able to upgrade the memory.

```

description: Notebook
    product: Satellite A50
    vendor: TOSHIBA
    version: PSA50E-06S02HEN
    serial: Z4030317P
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: administrator_password=disabled boot=normal chassis=notebook frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled uuid=97AFA200-4825-11D9-8050-B05DA4030317
  *-core
       description: Motherboard
       product: Portable PC
       vendor: TOSHIBA
       physical id: 0
       version: Version A0
       serial: $$T04Z21G2
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: Version 1.30 (10/25/2004)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing vesa cdboot bootselect pcmciaboot edd int13floppytoshiba int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) M processor         1500MHz
          vendor: Intel Corp.
          physical id: 4
          bus info: [EMAIL="cpu@0"]cpu@0[/EMAIL]
          version: 6.9.5
          slot: uFC-PGA Socket
          size: 1500MHz
          capacity: 1500MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 tm pbe up bts
        *-cache:0
             description: L1 cache
             physical id: 12
             slot: CPU Internal
             size: 64KiB
             capacity: 64KiB
             clock: 1GHz (1.0ns)
             capabilities: internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 13
             slot: CPU Internal
             size: 512KiB
             capacity: 512KiB
             clock: 1GHz (1.0ns)
             capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: 81
          slot: System board or motherboard
          size: 512MiB
          capacity: 1GiB
        *-bank:0
             description: SODIMM SDRAM Synchronous
             physical id: 0
             slot: DIMM 0
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: SODIMM SDRAM Synchronous [empty]
             physical id: 1
             slot: DIMM 1
             width: 64 bits


```

---

### Post by kate315 on 2015-01-28
It wasn't just the warning that put me off.  It was the fact that the laptop was getting hot and bothered about the whole thing.  (As was I by that stage.)

If I want to try again do I need something like this specifically for Lubuntu 14.04 LTS?

```

[TABLE]
[TR]
[TD][IMG]http://phillw.net/icons/compressed.gif[/IMG]
[/TD]
[TD][bento-ubuntu-remix-RC-linux-3.8-fake-pae-i386-2012.04.3.grub-n-iso.img.gz]("http://phillw.net/isos/lubuntu-fake-pae/raring/grub-n-iso/bento-ubuntu-remix-RC-linux-3.8-fake-pae-i386-2012.04.3.grub-n-iso.img.gz")
[/TD]
[TD="align: right"]30-Nov-2013 13:34
[/TD]
[TD="align: right"]700M
[/TD]
[TD][/TD]
[/TR]
[/TABLE]

```

Can someone point me towards the file I need to download?

---

### Post by sudodus on 2015-01-28
For Lubuntu 14.04.1 LTS you can use the what you have already (the iso file you downloaded and a CD/DVD/USB drive), and use **forcepae**.

If you don't like that, or if the computer gets too hot (a problem not related to PAE), you can try for example Bento. I'll check if there is some newer version of Bento to try, a version with a non-pae kernel.

---

### Post by sudodus on 2015-01-28
I'm waiting for an answer from the developer of Bento.

-o-

That Bento img.gz file is to be installed from USB, and if that is a problem in your computer, we should look for other alternatives.

- Can you burn and use a DVD disk? Or must the iso file be within CD size (703 MibiBytes for an '80 min CD disk')?

It seems the iso file at the following link is interesting, but slightly oversized for a CD disk

[http://phillw.net/isos/bento-ubuntu-remix/bento-i686-non-pae/](http://phillw.net/isos/bento-ubuntu-remix/bento-i686-non-pae/)

- An alternative is to start from the OBI-9w non-pae iso file, that you read about at this link

[https://help.ubuntu.com/community/9w](https://help.ubuntu.com/community/9w)

and download from this link

[http://phillw.net/isos/linux-tools/9w/obi_Trusty-nonpae-txt5-9w.iso](http://phillw.net/isos/linux-tools/9w/obi_Trusty-nonpae-txt5-9w.iso)

This way you can get Lubuntu 14.04 LTS with a non-pae kernel, which might be exactly what you want (to try as the second alternative)

---

### Post by sudodus on 2015-01-29
Here is the reply

> Here is non pae last Bento:
[http://downloads.linuxvillage.org/bento-i686-non-pae/](http://downloads.linuxvillage.org/bento-i686-non-pae/)

It is 711 MB. It can fit on a 700 MB CD with the overburn option. Also some 800 MB sized
CD do exist.

however, I consider 512 MB not enough, especially when the memory is shared with the
graphics.

I'd say ToriOS, if available, would be a good choice. If not available, then the person
should do a netinstall. She can start installing all the base meta packages, then a few
more, then any light environment she feels she can handle. IceWM, the choice of ToriOS,
is a full light one, quite ugly.

Of course, you probably won't suggest another distribution, but it could be relevant
(antiX, and other super light ones).


The Bento version referred to is the one I found at phillw.net and linked to in the previous post (an alternative web-site, I checked the md5sums, they are the same). So you might try to burn a CD disk with the overburn option. But the developer herself does not think 512 MB RAM is enough (she recommends 768 MB at the Bento web-site). The same can be said about Lubuntu, Bodhi and LXLE. These operating systems work with 512 MB RAM, but work better with more RAM.

[ToriOS]("http://torios.org/iso.html") is not yet released and in an intensive development phase, so maybe not a good option unless you are prepared to help testing it. It may break a few times, and will not be stable until the official release.

She also suggests netinstall alias the Ubuntu mini.iso and antiX. May I again suggest Wary Puppy and TahrPup.

Good luck, whatever you try :-)

---

### Post by kate315 on 2015-01-29
Thanks for the replies and the research.

Firstly I'm wondering if I should invest in some more memory.  It seems that I could upgrade the laptop to 1GB.  I thought it was a risk trying to upgrade it to 500MB so I'll have to think about that.

To answer the other questions.  I'm downloading on Windows 8.  (Hence the revival of interest in Linux!) 

 I have a rather erratic broadband connection which drops out a lot.  The files all take around 30 minutes to download.  The dropouts might  be the reason for some of the CDs not working.  I'm writing to CD on Windows 8.  I did try DVDs a year ago and I think perhaps the laptop didn't like them because I reverted to CDs.  The laptop should play DVDs but doesn't write them.

I don't mind collecting a few CDs and DVDs.  I assume I could try them on something else at a later date.  (I have an old Vista desktop that I could play with at some point.)

I suppose I could help out testing but with the proviso that nothing much works on the old laptop.

I need to go away, re-read the thread thoroughly and think about this.  Thanks again for all the help thus far.

---

### Post by Ashley_Bailey on 2015-01-29
You may also try debian!! The lower version works good itseems. Since your RAM is very small, you have to go with older version of Linux systems.

---

### Post by mörgæs on 2015-01-29
What do you mean by overheating? While the computer is sitting idle or when a particular application is running? 

Did you try to clean the fan and heat sink? There could be some dust bunnies nesting here.

Please post the entire lshw.txt.

---

### Post by kate315 on 2015-01-29
```


What do you mean by overheating? While the computer is sitting idle or when a particular application is running? 


```

The left side of it gets very hot to touch and there's a faint smell of burning. (Dust?)  It is okay idle.  It gets warm when asked to do anything complicated.  It runs best with lots of ventilation (hanging over the side of a table).  By complicated I mean accessing websites on Windows in around 2011 and booting from CD the other evening.

```


Did you try to clean the fan and heat sink? There could be some dust bunnies nesting here.


```

Not yet.  But if I can get the entire back off it I could try with the vacuum cleaner and a dust removing spray.

I can access the RAM and probably the hard disk quite easily.  Removing the entire back might be beyond my capabilities.

```


description: Notebook
    product: Satellite A50
    vendor: TOSHIBA
    version: PSA50E-06S02HEN
    serial: Z4030317P
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: administrator_password=disabled boot=normal chassis=notebook frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled uuid=97AFA200-4825-11D9-8050-B05DA4030317
  *-core
       description: Motherboard
       product: Portable PC
       vendor: TOSHIBA
       physical id: 0
       version: Version A0
       serial: $$T04Z21G2
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: Version 1.30 (10/25/2004)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing vesa cdboot bootselect pcmciaboot edd int13floppytoshiba int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) M processor         1500MHz
          vendor: Intel Corp.
          physical id: 4
          bus info: [EMAIL="cpu@0"]cpu@0[/EMAIL]
          version: 6.9.5
          slot: uFC-PGA Socket
          size: 1500MHz
          capacity: 1500MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 tm pbe up bts
        *-cache:0
             description: L1 cache
             physical id: 12
             slot: CPU Internal
             size: 64KiB
             capacity: 64KiB
             clock: 1GHz (1.0ns)
             capabilities: internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 13
             slot: CPU Internal
             size: 512KiB
             capacity: 512KiB
             clock: 1GHz (1.0ns)
             capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: 81
          slot: System board or motherboard
          size: 512MiB
          capacity: 1GiB
        *-bank:0
             description: SODIMM SDRAM Synchronous
             physical id: 0
             slot: DIMM 0
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: SODIMM SDRAM Synchronous [empty]
             physical id: 1
             slot: DIMM 1
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-generic:0 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-display:0
             description: VGA compatible controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:10 memory:d8000000-dfffffff memory:d0000000-d007ffff ioport:eff8(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:20000000-27ffffff memory:2c000000-2c07ffff
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:10 ioport:18c0(size=32)
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:18e0(size=32)
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:1c00(size=32)
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:11 memory:2c080000-2c0803ff
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 83
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:c000(size=4096) memory:cff00000-cfffffff memory:28000000-2bffffff
           *-network:0 DISABLED
                description: Wireless interface
                product: PRO/Wireless 2200BG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 5
                bus info: pci@0000:01:05.0
                logical name: eth1
                version: 05
                serial: 00:0e:35:a9:56:93
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
                resources: irq:11 memory:cffff000-cfffffff
           *-network:1
                description: Ethernet interface
                product: 82801DB PRO/100 VE (MOB) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:01:08.0
                logical name: eth0
                version: 83
                serial: 00:0e:7b:39:d5:2c
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
                resources: irq:11 memory:cfffe000-cfffefff ioport:cf00(size=64)
           *-pcmcia
                description: CardBus bridge
                product: ToPIC100 PCI to Cardbus Bridge with ZV Support
                vendor: Toshiba America Info Systems
                physical id: b
                bus info: pci@0000:01:0b.0
                version: 33
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=0 maxlatency=5 mingnt=128
                resources: irq:11 memory:cff00000-cff00fff ioport:c000(size=256) ioport:c400(size=256) memory:28000000-2bffffff memory:30000000-33ffffff
        *-isa
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:11 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:bfa0(size=16) memory:2c080400-2c0807ff
           *-disk
                description: ATA Disk
                product: TOSHIBA MK4025GA
                vendor: Toshiba
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: KA10
                serial: Z4314533T
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000e2b9a
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: fd67edd6-fd9b-44fb-80d0-6164fcd103fc
                   size: 35GiB
                   capacity: 35GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2014-04-30 14:01:14 filesystem=ext4 lastmountpoint=/ï¿½ï¿½ïï¿½ï¿½ï¿½hï¿½Ö’ï¿½ï¿½Pï¿½1ï¿½ï¿½l!ï¿½hï¿½ï¿½@ï¿½1ï¿½ï¿½ÜŒï¿½ï¿½ÜŒï¿½ï¿½ïï¿½ï¿½hï¿½1ï¿½yo!ï¿½ï¿½d modified=2015-01-25 12:36:09 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2015-01-27 12:43:39 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1450MiB
                   capacity: 1450MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1450MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: DVD-ROM SD-R2512
                vendor: TOSHIBA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1320
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:11 ioport:1000(size=256) ioport:1880(size=64) memory:2c080800-2c0809ff memory:2c080a00-2c080aff
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=0
             resources: ioport:1400(size=256) ioport:1800(size=128)
  *-battery
       description: Lithium Ion Battery
       product: LP660E
       vendor: TOSHIBA
       physical id: 1
       version: 11/10/04
       serial: 0100145438
       slot: 1st Battery
       configuration: voltage=10.8V


```

---

### Post by sudodus on 2015-01-29
> **kate315 said:**
> Thanks for the replies and the research.

Firstly I'm wondering if I should invest in some more memory.  It seems that I could upgrade the laptop to 1GB.  I thought it was a risk trying to upgrade it to 500MB so I'll have to think about that.

To answer the other questions.  I'm downloading on Windows 8.  (Hence the revival of interest in Linux!) 

 I have a rather erratic broadband connection which drops out a lot.  The files all take around 30 minutes to download.  The dropouts might  be the reason for some of the CDs not working.  I'm writing to CD on Windows 8.  I did try DVDs a year ago and I think perhaps the laptop didn't like them because I reverted to CDs.  The laptop should play DVDs but doesn't write them.

Check with ***md5sum***, that the download was good.
> 
I don't mind collecting a few CDs and DVDs.  I assume I could try them on something else at a later date.  (I have an old Vista desktop that I could play with at some point.)

I suppose I could help out testing but with the proviso that nothing much works on the old laptop.

[COLOR=#006400]I need to go away, re-read the thread thoroughly and think about this[/COLOR].  Thanks again for all the help thus far.

This is a very good idea ^^^ Take a pause and think before doing anything :KS

---

### Post by mörgæs on 2015-01-29
Cleaning is recommended. You don't necessarily have to take the computer apart. 

Your graphics is old Intel. Please see the Old Hardware guide for a possible tweak (and see post 3 i that thread for general recommendations). A light browser could also help.

Adding more memory will help but do it only if you get it cheap. This is very weak hardware so don't put too much money into it. 

The warning you saw about PAE has no significance. Just forget it. 

Old software is probably not going to make things better. If you should make a reinstall I would consider 14.10 but you could also just let it run as it is.

Base line: You have to accept a low performance for this old fella. Just be happy that you get some kind of use out of it.

---

### Post by Mike_Walsh on 2015-01-29
> **kate315 said:**
> 

Not yet.  But if I can get the entire back off it I could try with the vacuum cleaner and a dust removing spray.

I can access the RAM and probably the hard disk quite easily.  Removing the entire back might be beyond my capabilities.



A word of advice, Kate! Vacuum cleaners generate static electric; delicate electronics and static don't mix...

If you can get hold of it, a can of compressed air would work rather better. But if, as morgaes says, there are dust bunnies in there, then really, the back needs to come off to remove them.

I stripped my 13-yr old Dell down about 2 months ago, for the first time; the heatsink was clogged almost solid with dust bunnies. I ended up using a pair of tweezers to pull most of the solid stuff out, and then used the compressed air to blow the loose stuff out. My old girl  is now running a good 25-30 degrees cooler, so the effort IS worth it. It's one of those things you should only need to do once.

I guess, at the end of the day, it all boils down to one thing; how badly do you want to keep this senior citizen going? :p Some of us here on the forums do enjoy the challenge; it's why, in my case, I run 'Puppy' on this old girl.....because it really does make it run as well as, if not better than, it did when it was new. But not everybody wants to go to all that trouble, so.....the decision really has to be yours.

There's no getting away from the fact that the vast majority of people simply want to switch their machines on, and just use them; they don't have any interest in what 'makes them tick'...

I think, sometimes, though, that the 'urge' to tinker with things to make them work is hard-wired into guys' genetic make up..!:lol: I know what started my fascination with electronics; it was fixing the old man's ancient reel-to-reel tape recorder back in the mid 1970's. I got a pocket-money 'pay-rise' after that...!!

Good luck with whatever you decide to do.


Regards,

Mike. :)

---

### Post by Bucky Ball on 2015-01-29
Yes, you can upgrade to 1Gb. Yes, cleaning is a good idea. Blast it out with a can of compressed air. Blow out the vents.

---

### Post by kate315 on 2015-01-29
I'm typing this on the 'old thing' having installed Lubuntu!  There are a couple of minor irritations and the laptop is getting very warm otherwise it seems like it might be a success.  

I have some compressed air and I'll be cautious with the vacuum cleaner.  Thanks again for the help.

---

### Post by sudodus on 2015-01-30
Congratulations to running Lubuntu :KS

Which version is it? I think you tried Lubuntu 14.04.1 LTS before. Are you running the same version now?

Please share with us the result of cleaning the computer :-)

And finally, when you are happy with the computer, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by mörgæs on 2015-01-30
[http://www.irisvista.com/tech/](http://www.irisvista.com/tech/)

---

### Post by kate315 on 2015-01-30
Thanks for the irisvista link.  That looks very promising.  I was going to search out my manual but I don't think that tells me what I need to know.

It is Lubuntu 14.04.1 LTS and I'm very pleased with it.  It seems to do everything I need it to do.

The most difficult thing was getting the forcepae command to take.  I found some detailed instructions on another thread that eventually worked.  I'll paste them here if I ever find them again.

The installer offered me a dual boot with Ubuntu 10.10 so, rather nervously, I took it.  It halves the already minimal disk space.  Both boots seem to work okay.

I'm having difficulty getting a UK keyboard to take but that's only a minor irritation.  I may have had that problem before with this particular laptop.

It's getting generally warm after an hour's use so I'll rest it for a while.  It's no worse than it was on XP five years ago.  This gave up on XP long before the support ended!  I will try to remove the dust though as there must be some after using it for so long.

Thanks again for all the help.

---

### Post by Bucky Ball on 2015-01-30
DO NOT use a vaccuum cleaner!!! That is a no go, for several reasons. Can of compressed air, please. ;)

Just blow through the vents and blow out any dust around the hard drive/cards that you can see when you take the covers off the back (there should be an easily accessible hard drive and card area underneath).

Vaccuum cleaners can cause problems, not least of which is static electricity and sucking cables and other things out of place. You want to avoid that, and vaccuum cleaners, for getting rid of built up dust, lint and other unwanted flotsam.

---

### Post by Mike_Walsh on 2015-01-30
> **kate315 said:**
> 

I'm having difficulty getting a UK keyboard to take but that's only a minor irritation.  I may have had that problem before with this particular laptop.



@Kate:-

With regard to the UK keyboard layout, it IS a known 'bug' in Lubuntu 14.04 (&14.04.1). I got rid of the Lubuntu 14.04 I was using a couple of months ago, so can't remember exactly how I did it.....but I've changed it quite a few times, on various re-installs. There are a couple of different ways to approach the problem, one of which is detailed here:-

[http://www.everydaylinuxuser.com/2014/06/5-things-to-do-after-installing-lubuntu.html](http://www.everydaylinuxuser.com/2014/06/5-things-to-do-after-installing-lubuntu.html)

Look down toward the bottom of the page, and it'll tell you how to approach it.

Hope that helps.


Regards,

Mike. :)

---

### Post by Bucky Ball on 2015-01-30
If you want to tackle the keyboard issue specifically, best to post a new thread. ;)

---

### Post by mörgæs on 2015-01-31
I would like to add that I vacuum every old computer that I get for repair and have never had any bad experience. All my computers at home are also vacuumed on a regular basis to prevent problems. Just don't do it with too much force.

---

### Post by kate315 on 2015-01-31
I have carefully vacuumed desktops without ill effect.  I haven't as yet vacuumed a laptop.  (I once vacuumed a motherboard.  Again without ill-effect.)  I know about taking precautions for static but it never occurred to me that a vacuum cleaner might be a problem in that way.

I think the overheating is a hard disk problem.  I don't think it's failing yet but I think it's somewhat overworked.  On occasion the BIOS hasn't found it which, so far, has been solved with a reset.  (Is a dual boot harder work for the disk?)

I'm pleased with the Lubuntu 14.04.1 LTS  install.  The laptop is running well.  I would be interested in a separate thread on the UK keyboard topic.  I seem to remember that there was a problem with one particular key on the US version.  Something crucial while typing at the command line - possibly a slash or something similar??

I'm tempted to mark the thread solved but I'd prefer to leave it a couple of days to make sure that the install is stable if that's okay?

Thanks again for all the help.  I couldn't have done this without the input.  Ubuntu 10.10 was the best I could do on my own.

---

### Post by sudodus on 2015-01-31
It is fine to wait a couple of days to make sure that the install is stable :-)

... and then mark it as solved

---

### Post by kate315 on 2015-01-31
[http://zo0ok.com/techfindings/archives/1546](http://zo0ok.com/techfindings/archives/1546)

Despite much Googling I can't find the exact solution I found to the forcepae problem.  The above is a similar solution but I think I may have also pressed another key - perhaps tab.

The solution may have been from this forum - it involved a Toshiba user who was given at least four options to get forcepae to work.  The person found that the fourth option worked.

I didn't try it.  I went directly to installing it.

---

### Post by sudodus on 2015-01-31
More **forcepae** instructions:

I wrote the instructions in this link (and I know it has helped people to install Lubuntu and Xubuntu)

[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M)

*mörgæs* wrote the instructions in the following link (updated today, 2015-01-31, and I know that [a previous version of] this text has helped people to install Lubuntu and Xubuntu)

[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

---

### Post by Bucky Ball on 2015-01-31
> **sudodus said:**
> It is fine to wait a couple of days to make sure that the install is stable :-)

... and then mark it as solved

^^^
This> and then post a new thread regarding any other issues you have. You will have a much better chance of getting support rather than buried here on a thread with a title not related to the new issues. Good luck. ;)

Great to hear that the fully supported Lubuntu 14.04 LTS is working for you. ;)

---

### Post by Irihapeti on 2015-01-31
From the comments about UK keyboard, I suppose that the OP is based in the UK....

Which is a pity, because I have a 512MB stick of RAM that would almost certainly work in that machine but it would probably cost more to get it to the OP than it's worth. :(

---

### Post by kate315 on 2015-02-01
Thanks for the thought anyway Irihapeti.  I suppose it adds a whole new angle to the idea of distant memory!

As I have booted the laptop around 10 times and it has performed well and 'we' have even installed an update I'll mark the thread solved.  It seems to be running very nicely unless I overtax it.  I'm impressed with Lubuntu.

---

### Post by Bucky Ball on 2015-02-01
Try these:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

This will get everything completely up to date (take note: the last command will NOT upgrade you to the newest release, just upgrade anything in your current install that needs to be or can be). Good luck. ;)

---

