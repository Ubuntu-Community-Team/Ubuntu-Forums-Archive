---
title: "Any Linux install I try does not work"
date: 2013-03-27
forum: New to Ubuntu
---

### Post by monkspeed on 2013-03-27
Something really weird is going on with this rig, it does not seem to start the installation of any Linux DVD I try to use.

Although I did just about install Ubuntu the other day, but it really took loads of tries, and thinking about it now, it really was random why it started working..

So far I've tried Ubuntu 12.10, Ubuntu 12.04 LTS, Manjaro open box, Linux Mint...

Every single one, the DVD will boot and get to the very first menu but after I select install or begin it goes to a black screen with a blinking cursor and that's it...

The iso's I've all burnt using power iso onto a dvd + r and all verified OK afterwards as well.

Do you think the DVD drive is incompatible or something?? Or maybe the MB is just **** and causing all the problems?

SPEC:
Abit AN7 MB with latest bios 19
OCZ Platinum DDR 400 512mb x 2
AMD XP 2800+
Samsung 40GB hard drive
LG DVD ROM drive
Geforce 2 MX400 64mb

that's about all I can think of for now...

Any ideas??

---

### Post by ManamiVixen on 2013-03-27
That AMD XP 1800+ does not support Ubuntu 12.04 and newer and that also goes for all Ubuntu based Distros based on 12.04 or newer. You could use Lubuntu 12.04 and newer though, while it is based on Ubuntu, it was desigend with old hardware in mind and has support for that CPU. There is also Puppy Linux and Debian as other alternatives.

Oh, as for the reason, Ubuntu by default install the PAE kernel for 32bit hardware. The PAE kernel allows a 32bit CPU and OS to address more than 4GB of ram. The Athlon XP 1800+ does not support PAE.

---

### Post by monkspeed on 2013-03-28
> **ManamiVixen said:**
> That AMD XP 1800+ does not support Ubuntu 12.04 and newer and that also goes for all Ubuntu based Distros based on 12.04 or newer. You could use Lubuntu 12.04 and newer though, while it is based on Ubuntu, it was desigend with old hardware in mind and has support for that CPU. There is also Puppy Linux and Debian as other alternatives.

Oh, as for the reason, Ubuntu by default install the PAE kernel for 32bit hardware. The PAE kernel allows a 32bit CPU and OS to address more than 4GB of ram. The Athlon XP 1800+ does not support PAE.

Hi there, thanks for writing back!
I made a total mistake in my post, the CPU is an XP 2800+ not 1800, sorry for the mistake!! Whether that changes things or not I don't know...
But somehow out of the blue I did manage Ubuntu 12.04 to install the other day after trying many times, but was not very stable...

Thanks.

---

### Post by sudodus on 2013-03-28
> **monkspeed said:**
> Hi there, thanks for writing back!
I made a total mistake in my post, the CPU is an XP 2800+ not 1800, sorry for the mistake!! Whether that changes things or not I don't know...
But somehow out of the blue I did manage Ubuntu 12.04 to install the other day after trying many times, but was not very stable...

Thanks.

Your cpu specs, 2800+, is good enough for running Xubuntu with the light-weight desktop environment XFCE and Lubuntu with the ultra  light-weight desktop environment LXDE. So even with this information, I support *ManamiVixen*'s suggestion to install Lubuntu. It will give you a good user experience. It is also possible to run Ubuntu (at least after some tweaking), but try a lighter desktop environment :-)

Maybe your system will work better with some boot options, for example nomodeset. See this link

[[COLOR=#ff0000]https://help.ubuntu.com/community/BootOptions[/COLOR]]("https://help.ubuntu.com/community/BootOptions")

---

### Post by monkspeed on 2013-03-28
> **sudodus said:**
> Your cpu specs, 2800+, is good enough for running Xubuntu with the light-weight desktop environment XFCE and Lubuntu with the ultra  light-weight desktop environment LXDE. So even with this information, I support *ManamiVixen*'s suggestion to install Lubuntu. It will give you a good user experience. It is also possible to run Ubuntu (at least after some tweaking), but try a lighter desktop environment :-)

Maybe your system will work better with some boot options, for example nomodeset. See this link

[[COLOR=#ff0000]https://help.ubuntu.com/community/BootOptions[/COLOR]]("https://help.ubuntu.com/community/BootOptions")

I just tried Manjaro net install version burnt onto a rewritable CD and still the same, get to menu, start Manjaro, black screen... Sometimes it will write 'starting kernel' but will still hang. 

I will try some codes out as you suggest but I really got a sneaky feeling the DVD drive is kaput, I will try swapping it from my decent rig. 

Thanks!
:-)

---

### Post by sudodus on 2013-03-28
Please try with some boot options too :-)

Start with ***nomodeset***. It is often the key thing with your kind of graphics.

---

### Post by monkspeed on 2013-03-28
> **sudodus said:**
> Please try with some boot options too :-)

Start with ***nomodeset***. It is often the key thing with your kind of graphics.

OK will do, thanks!! :-D

---

### Post by monkspeed on 2013-03-28
So I've come to the conclusion that the AN-7 is pure rubbish. I swapped DVD drives and the same **** happens. I even tried a windows xp CD and that made an error also on motherboard.inf.

I did manage a couple of times to get a little further by select safe install and options nomodeset and edd=off. Lots of writing on the console but then it hung again when it got to welcome to manjaro.

Honestly I downloaded xubuntu default and alternative but I really don't want to waste DVDs, I know it still won't work.

I've had problems with the AN7 since day one when the ps2 keyb connector was screwed somehow and I had to use a USB keyb since, and the mob struggles to hit 180fsb... That's ridiculous, I've read people hitting 220 easily with this board so I think I just received a duff one, my luck...

Thanks anyway.

---

### Post by sudodus on 2013-03-28
Have you checked if your RAM is OK? You can run memtest (from the boot menu of the install CD) overnight. Not one single memory error should occur during a whole night.

---

### Post by monkspeed on 2013-03-28
> **sudodus said:**
> Have you checked if your RAM is OK? You can run memtest (from the boot menu of the install CD) overnight. Not one single memory error should occur during a whole night.

Can't, as soon as I select memtest the PC reboots immediately, but the ram is OK as I've had it in another rig and done lots of memtest and prime...

Definitely sounds fishy that the PC reboots though... :-/

---

### Post by sudodus on 2013-03-28
Yes, something is wrong. Maybe the motherboard and ram are not co-operating as they should. Or there is something wrong with the motherboard.

---

### Post by monkspeed on 2013-03-29
So I managed to install Aros without a hitch! Its not Linux but at least its breathed some life into an old rig and I get to re-live my good ol' Amiga 500 days! :-D

---

### Post by Zill on 2013-03-29
monkspeed:  Most, if not all, Linux distros can be run as a "Live" session *directly* from a DVD or USB - no installation to HDD required.  This is an excellent way to test compatibility with your hardware and, IMHO, should always be done *prior* to trying to install a new distro.  If the live session runs OK "out of the box" then this should show that an installation should work without any problems.  However, if the live session does *not* run properly then this will indicate that you may need to add some boot parameters to get things working *or* that there are hardware problems that need further investigation.

In order to avoid wasting DVDs, I suggest you use rewriteable DVDs (RW) rather than the single-use (R) versions.  Alternatively, you can use a USB stick for the ISO - just make sure your PC BIOS is correctly configured to boot from USB.

The spec you have posted may be rather limiting for some modern Linux distros but it should certainly work with distros having lower system requirements.  I suggest trying out [CrunchBang Linux]("http://crunchbang.org/"), first as a Live USB and then, if successful, installing the system. My recommendation is to try the [32-bit Waldorf for Older PCs (non PAE) version]("http://crunchbang.org/download") as this should have the best chance of working well on your system.

---

### Post by mörgæs on 2013-03-29
> **ManamiVixen said:**
> The Athlon XP 1800+ does not support PAE.

Do you have a link for this, please? 
(I know it's not the CPU which original poster is using).

---

### Post by matt_symes on 2013-03-29
Hi

> **mörgæs said:**
> Do you have a link for this, please? 
(I know it's not the CPU which original poster is using).

If the OP can boot into a Linux Live CD/USB then

```
grep pae /proc/cpuinfo
```

should show pae if it has it.

I'm also interested whether the chip older is non pae capable. 

Incidentally, you can check with the non pae netboot 12.04 iso.

Kind regards

---

### Post by monkspeed on 2013-03-29
The live CD's don't work, soon as I select 'start' it hangs... I'm sure this MB has problems with booting from a cd, or possibly some hardware fault. Maybe even the harddrive is a dud. Maybe it don't like the DVD +r discs... Once in thirty tries it might boot a bit further with the DVD but then... You guessed it, it hangs again. I managed to install Ubuntu 12.04 a few days ago after a couple of attempts, used it for a day, installed the nvidia driver, the I started getting random system errors and then the next thing I know it wouldn't load past grub...

So that's when I began trying other distro's and then discovered nothing works any more :-/

I'm burning crunchbang waldorf now as per Zill's instructions, see if that works..

:-)

---

### Post by monkspeed on 2013-03-29
I burned crunchbang at 4x and verified OK.
Selecting install or live CD just hangs, memtest instantly restarts the PC.

I figured out tab allows me to type some options so I wrote 'nomodeset' and 'edd=off' to no avail.
This is so unbelievably frustrating...

---

### Post by sudodus on 2013-03-29
1. Maybe you should check out the memtest problem: Try with one memory card (test each of them separately). Then swap the position of the cards (when both are connected).

Can you check if the motherboard supports the specs of the memory cards and vice versa? Do you have other memory cards with similar specs (for example sitting in another computer)?

2. Maybe you can take the internal HDD out of the computer and connect it to another computer. Then you can install some linux distro to it [an Ubuntu flavour ;-)] Install no proprietary driver! Then move it back into this Abit computer and try running it.

---

### Post by mörgæs on 2013-03-29
+1 to the suggestions above.

Also, for comparison how does a boot from USB work (provided your BIOS supports it)?

---

### Post by Zill on 2013-03-29
> **monkspeed said:**
> The live CD's don't work, soon as I select 'start' it hangs... I'm sure this MB has problems with booting from a cd, or possibly some hardware fault. Maybe even the harddrive is a dud...
A live [COLOR="#D3D3D3"]CD[/COLOR] DVD should ignore the harddrive and so a live session *should* run irrespective of the harddrive's condition or even its presence!  If a live CD will not load then this is probably down to either the motherboard or to RAM and so it would be useful to check the RAM as suggested by sudodus.  However, as mörgæs suggests, it will also be useful to boot from USB in order to eliminate your DVD drive as the culprit.

Please post back exactly what your PC shows when it freezes while loading a live distro.  CrunchBang Waldorf should be helpful in this regard as it does normally show some terminal output while booting and it will be useful to see what was last loaded.

---

### Post by Zill on 2013-03-29
One further thought...  Just to make sure an ISO file is not corrupt it is always good practice to run an "md5sum" on the downloaded file.  The value returned should then correspond *exactly* to the md5sum published for the particular release.  See [HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") for more details.

---

### Post by monkspeed on 2013-03-29
> **sudodus said:**
> 1. Maybe you should check out the memtest problem: Try with one memory card (test each of them separately). Then swap the position of the cards (when both are connected).

Can you check if the motherboard supports the specs of the memory cards and vice versa? Do you have other memory cards with similar specs (for example sitting in another computer)?

2. Maybe you can take the internal HDD out of the computer and connect it to another computer. Then you can install some linux distro to it [an Ubuntu flavour ;-)] Install no proprietary driver! Then move it back into this Abit computer and try running it.

Tried lots of things tonight...

1. swapped PSU.
2. Swapped memory (tried every single slot with one stick, tried very relaxed timings within bios) - memtest still crashes immediately upon selecting from grub menu.
3. swapped gfx card.
4. removed cables from hard drive so it was only dvd drive.

I got a tiny tiny bit further when selecting Live crunchbang, screen goes a funny colour of grey with blinking cursor instead of just crashing on grub menu immediately upon selection. tried with 'nomodeset' and 'edd=off' params as well.

> **mörgæs said:**
> +1 to the suggestions above.

Also, for comparison how does a boot from USB work (provided your BIOS supports it)?
tried to put crunchbang on a usb stick with unetbootin, but got no option for booting from usb-stick in bios :-/

> **Zill said:**
> A live [COLOR="#D3D3D3"]CD[/COLOR] DVD should ignore the harddrive and so a live session *should* run irrespective of the harddrive's condition or even its presence!  If a live CD will not load then this is probably down to either the motherboard or to RAM and so it would be useful to check the RAM as suggested by sudodus.  However, as mörgæs suggests, it will also be useful to boot from USB in order to eliminate your DVD drive as the culprit.

Please post back exactly what your PC shows when it freezes while loading a live distro.  CrunchBang Waldorf should be helpful in this regard as it does normally show some terminal output while booting and it will be useful to see what was last loaded.
No terminal output occurs, it either crashes on grub screen when selecting option 1 or 2, or will proceed past grub to funny grey colour and then hang. option 3 memtest restarts computer immediately upon selection. this has been the same for every linux distro i've tried so far :-/

> **Zill said:**
> One further thought...  Just to make sure an ISO file is not corrupt it is always good practice to run an "md5sum" on the downloaded file.  The value returned should then correspond *exactly* to the md5sum published for the particular release.  See [HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") for more details.

Thanks for the link, that is a great app! I always wondered what I was suppose to do with those md5 numbers!
It would have been great if they were found to be corrupt because this would have given me something to go on, but alas they all check out fine (well crunchbang and manjaro do, didnt check the others but i'm sure they are not at fault).

I think I'm pinning the blame on MB, I will try when I have time to put together another rig with even older parts and try that... or take hard drive, put it in decent computer, install then put it back...


Thanks all for the help everybody! :D

---

### Post by Zill on 2013-03-29
monkspeed:  Thanks for the update.  In view of these tests I must agree that the motherboard seems most likely to be the problem.

Out of interest, has this system actually worked before or have you just built it from "spare" parts?  If it did work previously then which OS ran on it?

---

### Post by monkspeed on 2013-03-29
> **Zill said:**
> monkspeed:  Thanks for the update.  In view of these tests I must agree that the motherboard seems most likely to be the problem.

Out of interest, has this system actually worked before or have you just built it from "spare" parts?  If it did work previously then which OS ran on it?

It was my old Winblows XP rig. Everything was the same apart from dvd drive and hard drive. I also had a different PSU Tagan 480Watt PSU at that time, but that is powering a different rig which is around my bro-in-laws at the moment. I'm not to sure but from memory I was running board, CPU and same OZC memory at about 196 FSB daily. I remember this rig did pop a PSU hence why I bought the Tagan in the first place, maybe it did some kind of damage that didn't rear it's head till now?

Hmm, the bios-battery is not so great in the board, it doesn't hold charge for very long, maybe it messed with the bios in some way? I could try re-flashing it and see what happens...

---

### Post by AndyOpie150 on 2013-03-30
Also:
Try Plop Boot Manager to manipulate where to boot from (allowed me to boot from the USB on my ten year old machine when even the BIOS setting wouldn't). Pick the "Windows boot" script instaler. When you restart you will have two options in the grub menu. Windows and Plop

Download Puppy Slacko 5.4-Opera-4g.iso. Super fast on older machines and can stay on USB flash drive. It also has the easiest wireless driver install of all the distro's with many older drivers supported and ndiswrapper module already compiled and configured in case you end up having to use your Windows wireless driver. Took me less than 5 minutes to get wireless working with my Windows wireless driver folder for my wireless adapter card pasted to the network folder.
To install .iso to a flash drive try either LiLi USB Creator or Universal USB Installer.

If that works let me know. I can help you select a distro with a password protected login screen that should install from USB drive.

For more info go here: [URL="https://www.linuxdistrocommunity.com/forums/showthread.php?tid=524"]https://www.linuxdistrocommunity.com/forums/showthread.php?tid=524

PS: Try "Free Download Manager" to accelerate your download speeds, and.........check the MD5 sum.
[/URL]

---

### Post by sudodus on 2013-03-30
> **monkspeed said:**
> Tried lots of things tonight...


Yes indeed :-)
> 
I think I'm pinning the blame on MB, I will try when I have time to put together another rig with even older parts and try that... or take hard drive, put it in decent computer, install then put it back...


Thanks all for the help everybody! :D

Yes, I think we have more evidence against the MB. But if the damage is near the connection to the CD/DVD drive, it might work to take the hard drive, put it in decent computer, install then put it back...

But you are running Aros successfully ... So maybe there is some hardware that these new linux systems cannot cope with. Just for fun, you can try some mini OS, that might work, although maybe won't be really useful for everyday usage: DSL, kolibri or some very old Ubuntu version, for example Ubuntu 8.04 (the desktop version won't receive any security update, but the server will for a few weeks more).

---

### Post by Zill on 2013-03-30
> **monkspeed said:**
> ...Hmm, the bios-battery is not so great in the board, it doesn't hold charge for very long, maybe it messed with the bios in some way? I could try re-flashing it and see what happens...
Thanks for the additional info.  Re the BIOS battery I would simply replace the battery with a new one.  Re-flashing the BIOS should *not* be necessary just because of a flat battery and, IMHO, could generate more problems than it solves. ;-)  Of course, after changing the battery it is a good idea to reset the BIOS to defaults and then enter your preferred settings as required.

---

### Post by Zill on 2013-03-30
> **monkspeed said:**
> It was my old Winblows XP rig. Everything was the same apart from dvd drive and hard drive. I also had a different PSU Tagan 480Watt PSU at that time...
So did the current configuration (including DVD drive, HDD and PSU) actually run Windows XP without *any* problems?

---

### Post by monkspeed on 2013-03-30
> **Zill said:**
> So did the current configuration (including DVD drive, HDD and PSU) actually run Windows XP without *any* problems?

It use to run windows fine when conservatively clocked but I use to enjoy pushing it while trying to get to the elusive 200fsb! (Never could do, 198 was as far as it would go, and that was rather flakey)

the MB and CPU have been in storage, but I was using the memory for a few more years afterwards.

It was only recently that I fancied trying out the latest Linux, that I started rooting through all my old junk and found it and rebuilt it...

I do have a nice spare machine I'm dying to use for Manjaro but my in-laws are using it to watch Turkish television on it through the internet, if I take it my wife will probably kill me :-P

---

### Post by Zill on 2013-03-30
monkspeed:  The problems with running Linux *may* be down to the "surgery" done by dismantling and later reassembling the PC.  It may simply be that a cable is broken or a connector is not mating properly.  Alternatively, the CPU could have been damaged by the overclocking. :-(

---

### Post by monkspeed on 2013-03-30
> **Zill said:**
> monkspeed:  The problems with running Linux *may* be down to the "surgery" done by dismantling and later reassembling the PC.  It may simply be that a cable is broken or a connector is not mating properly.  Alternatively, the CPU could have been damaged by the overclocking. :-(

I had to run the CPU with a high voltage to keep it stable so it may now be suffering from electromigration?

I'll build another old rig based on a 1ghz Thunderbird and see if I get any problems with that, but I think I'll try installing to the hard drive on my working rig as well just out of curiosity.

Thanks everyone for your help!
:-D

---

### Post by sudodus on 2013-03-30
But you are running ***Aros*** successfully ... So maybe there is some  hardware that these new linux systems cannot cope with. Just for fun,  you can try some mini OS, that might work, although maybe won't be  really useful for everyday usage:

- DSL [[COLOR=#ff0000]http://www.damnsmalllinux.org/download.html[/COLOR]]("http://www.damnsmalllinux.org/download.html")

- kolibri [[COLOR=#ff0000]http://kolibrios.org/en/[/COLOR]]("http://kolibrios.org/en/")

or

- some very old Ubuntu  version, for example Ubuntu 8.04 [[COLOR=#ff0000]http://releases.ubuntu.com/8.04/[/COLOR]]("http://releases.ubuntu.com/8.04/")
(the desktop version won't receive any  security update, but the server will for a few weeks more), or

- an old version of Knoppix, for example Knoppix 5, that can be found at [[COLOR=#ff0000]http://mirror.cs.utah.edu/pub/knoppix/[/COLOR]]("http://mirror.cs.utah.edu/pub/knoppix/") while a modern version will be found via [[COLOR=#ff0000]http://www.knoppix.org/[/COLOR]]("http://www.knoppix.org/")
  
*Edit*: I have tried all of these distros

---

### Post by monkspeed on 2013-03-31
Well I'm at my bro-in-laws house now and am posting this from my spare rig with the Manjaro Openbox live cd. It's so nice and slick! Makes me want it even more!!

---

### Post by starlyte2 on 2013-03-31
Try Puppy Linux Precise or Lucid. They work really well on the "older" PC's, no insult meant, but when you see the 4 & 6 cores, and more I think. You can install all the Ubuntu programs for those releases, and it has a really small foot print, about 120mb's. Which leaves the place for other things on your HDD. It won't hang, as it doesn't need tonnes of memory. I've been using it for years, with old PIII's, and now a x4 core Athlon. It is very versatile. I use Openbox as desktop, but you have lots of choice, not only with that. Once you get going it can be as small or big as you like.[http://www.murga-linux.com](http://www.murga-linux.com) is a great place to begin. ;)
 Good luck.

---

### Post by ally_uk on 2013-03-31
Try Debian net install :)

---

### Post by monkspeed on 2013-04-02
Guess what!? Well I'll be a monkeys uncle!

Following my hunch I decided to re-flash the bios, but the original 1.9 bios from what's left of Abit's website would not run on my 64bit Windows rig so I was a bit stumped for a while! But I managed to find a modded bios by some guy called 'artbios' flashed it successfully and now I am actually posting this from the live install disc!

At my bro-in-law's yesterday I installed Manjaro onto a spare hard drive and put that in this rig today, and that boots up as well but does not show the desktop, i just get a console, so I am going to try to re-install from the live cd and see what happens.

Wish me luck!!!
:D

---

### Post by sudodus on 2013-04-02
You are making progress. Continue with that alias Good Luck :-D

---

