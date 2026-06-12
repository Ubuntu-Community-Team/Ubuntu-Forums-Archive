---
title: "Ubuntu Home Recording Studio... how do I get there..."
date: 2008-07-30
forum: New to Ubuntu
---

### Post by SideOfPotatoes on 2008-07-30
Howdy everybody!

I am a complete noob to Ubuntu (hence the post in the "Absolute Beginner Talk"). Here is my situation.

I have a computer with Ubuntu 8.04 (just the standard edition, not the studio edition), and I've only had about 30 minutes of experience with it. I would like to create a home recording studio (on a very basic level) with this computer as the centerpiece, and I have no clue as to how.

First of all, I've heard that ARDOUR is the way to go (because I'll be doing more "pro tools" type production work). How do I install it? From what I gather, Ubuntu is not too keen with the '.exe's, and I DO NOT HAVE INTERNET ACCESS WITH THE "DESTINATION" COMPUTER, so is there a way I can transfer everything via flashdrive or the like?

Do I need other softwares aside from ARDOUR?

Are there any suggested, linux-compatable guitar/bass/mic/keyboard to computer interfaces on the market?

Will a stock '02 or '03 Dell soundcard be good enough to do what I want (or is there some other software to download that will simulate a better one)???

I'm not going for pro sound quality on this one...just "respectable" quality would be fine!

All help is GREATLY appreciated!!!

Thanks!!!

-Jim

:guitar:

P.S. I'm sorry if this was already asked. I did some digging and I couldn't find it.

---

### Post by Thelasko on 2008-07-30
It will be much easier to hook up the machine to the internet and use synaptic/APT/Add and Remove software to install the software you desire.  Here is a [link]("http://packages.ubuntu.com/hardy/sound/ardour") to the Ardour file, you will see that it requires you to install many other software packages to work.  [Here is an instruction manual]("https://help.ubuntu.com/8.04/add-applications/C/offline.html") for installing software without an internet connection.

If this computer is going to be used solely as a studio computer I would install ubuntustudio.  I know it's a pain because it doesn't fit on a cd.  I suggest connecting your machine to the internet and just installing it by opening the terminal (applications>accessories>terminal) and entering the commands [found here:]("http://ubuntuforums.org/showthread.php?t=861455")
```
sudo apt-get update
sudo apt-get install ubuntustudio-audio ubuntustudio-audio-plugins linux-rt
```

I've never upgraded to Ubuntustudio personally, but I will offer you one important piece of advice.  NEVER, install software using a method other than APT, synaptic, or "Add & Remove Software" unless you are specifically told to do so by someone here on the forums or it says so on help.ubuntu.com.

Once you are done installing the software, you can disconnect it from the internet.  I suggest moving the computer to a location that has internet to install the software (maybe two hours if everything goes smooth) and then move it back to your studio when your are done.

---

### Post by BDNiner on 2008-07-30
You will have to install ubuntu studio. the main reason is studio uses a different kernel than the regular ubuntu OS. it uses the realtime kernel which priorities the processes running to prevent/reduce latency. If you install software that is part of the ubuntu studio package using APT or synaptic it will install the real time kernel.

Ubuntu studio comes with a lot of software for audio production. I run ubuntu studio at home but i still use my XP machine for audio production since my m-audio USB sound card is not compatible with ubuntu. Some of the m-audio PCI sound cards are compatible, i just don't know which ones off the top of my head. My m-audio USB midi keyboard is compatible, but i have not gotten my serial fatboy midi controller to work. I have an older machine with a Creative audigy 1, with the break out box, and the 1/4 inch jacks on the break out box do function in ubuntu, i tested that using a live CD. but i have read about creative's lack of support with linux and newer audigy card have issues.

---

### Post by SideOfPotatoes on 2008-07-30
Ok, I talked with a few people who have the interwebs, and I might be able to connect this puppy up within the next few days.

Should I uninstall 8.04 when I install the studio version (and, if so, how)?

So...my sound card may not work...and the interface may not work...

Does anyone know of interfaces that do work?

Is there a way to get around a sound card that doesn't work? (I thought someone had mentioned to me some freeware that emulated a sound card pretty well...?)

Thanks again!!!
:guitar:

---

### Post by cariboo on 2008-07-30
if you could open up a Applications-->Accessories-->Terminal and type:

```
lspci >hardware.txt
```

This will create a text file called hardware.txt, it will be located in your home directory. You will have to sneakernet it to the computer you are using for posting here. Include it in your next post, this way we can help you with any hardware problems.

Jim

---

### Post by Thelasko on 2008-07-31
> Should I uninstall 8.04 when I install the studio version (and, if so, how)?

No, The instructions I posted before will install the audio part of Ubuntu Studio on top of your regular Hardy Heron (8.04) install.  To install the whole thing (audio, video, graphics) without removing regular Ubuntu, [read this page.]("https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromHardy")

Ubuntu Studio appears to have some pretty good [help pages]("https://help.ubuntu.com/community/UbuntuStudio"), they're just hard to find.

---

### Post by Thelasko on 2008-07-31
> So...my sound card may not work...and the interface may not work...
Does the soundcard in question work right now?  If it does, I don't think you will have any problems getting it to work with Ubuntu Studio, but you might not have the quality you desire.  I suggest you try it, and if you don't like it, buy a better one.

Unfortunately, you can't buy soundcards designed for studio recording off the shelf at Best Buy.  You want something that has some good inputs.  I found [this thing]("http://www.markertek.com/Product.asp?baseItem=LX-LAMBDA&cat=COMPUTER&subcat=&prodClass=COMPAUDIO&mfg=&search=0&off=") on markertek.  It's cheap and looks like it's good quality ([XLR]("http://en.wikipedia.org/wiki/XLR") and [1/4"]("http://en.wikipedia.org/wiki/Jack_plug") inputs), I just don't know if it works with Linux.  Sam Ash and Guitar Center probably have something too, but I suspect they are expensive.  I haven't messed with that kinda stuff in a few years, although a friend of mine works in television.  He only uses Windows.

---

### Post by Thelasko on 2008-07-31
[Read this]("https://help.ubuntu.com/community/UbuntuStudio/HardwareOptimization") before buying a soundcard.

---

### Post by Technoviking on 2008-07-31
Tony of the Ubuntu UK podcast has done a screencast series on podcasting in Audour, it maybe some help.

[http://screencasts.ubuntu.com/Mixing_A_Podcast_In_Ardour_-_Part_1](http://screencasts.ubuntu.com/Mixing_A_Podcast_In_Ardour_-_Part_1)

---

### Post by Brightbelt on 2008-08-01
I've had some experience configuring Ardour. You'll need to use the JACK programs, which are the behind-the-scenes configuration for your audio driver and plugins etc.

Installing Ardour includes Jackd by dependency, but the main program through which you should use to run Ardour is 'Qjackctl'...I recommend installing that through your Synaptic Package Manager.

In Qjackctl, you choose your audio driver, and the Alsa driver is the default setting. And Alsa usually works fine right out of the box. When you want to use Ardour, you really start the Qjackctl program first and click start, then you can run Ardour.

I have tried long and hard to configure the Freebob driver and/or the FFado driver (it's still in beta) in order to use a Mackie firewire console, but so far no luck. After visiting the Ardour forums, I can assure you, I'm not alone there.  

But since your aim is not really pro audio quality, the alsa driver should be fine for you. 

Good Luck !

Frank B.

---

### Post by Thelasko on 2008-08-01
JACK should be automatically installed with Ubuntu Studio, if you go that route.

---

### Post by SideOfPotatoes on 2008-08-01
Wow...

Well, first off...thanks to everyone for your responses...

I'm a little confused, but I'm starting to make sense of it all.

I'll do the hardware.txt thing tonight or tomorrow, and I'll post that up so you can better advise me, and, yes, my current soundcard makes all kinds of annoying beeps, so it will probably be ok.

I think, at this rate, I'm just going to dump everything and put on studio (I haven't really even saved a document on the computer, so I don't really care about wiping it clean again).

Thanks again guys!

I really appreciate all your help (and I can't flippin' wait until I can start recording!!!!!!!!!!!!!)

-Jim

---

### Post by SideOfPotatoes on 2008-08-02
GOOD NEWS!!!

I was explaining to a friend that I was trying to set up a recording studio, and he wanted me to record his band when I get it set up...so to help he's **giving** me a Dell 490 precision workstation (way better than the dimension that I've been screwing around with)!!!

UBER SCORE!

Anyhow, I'll have to wait until I get that to get the hardware.txt, but, rest assured, I should have it done soon!!!

Thanks for your patience!

-Jim

:guitar:

---

### Post by SideOfPotatoes on 2008-08-05
Ok, not as good of news...the guy said "450" not "490", but it's still an upgrade.

Anyway, here's the hardware list (Please don't laugh too hard). **[SIZE="5"]If anyone could recommend a good linux-compatable instrument/computer interface, it would be GREATLY appreciated!!![/SIZE]**

THANKS!!!

-Jim

Hw:

00:00.0 Host bridge: Intel Corporation E7505 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation E7505/E7205 PCI-to-AGP Bridge (rev 03)
00:02.0 PCI bridge: Intel Corporation E7505 Hub Interface B PCI-to-PCI Bridge (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R200 QH [Radeon 8500] (rev 80)
02:1c.0 PIC: Intel Corporation 82870P2 P64H2 I/OxAPIC (rev 03)
02:1d.0 PCI bridge: Intel Corporation 82870P2 P64H2 Hub PCI Bridge (rev 03)
02:1e.0 PIC: Intel Corporation 82870P2 P64H2 I/OxAPIC (rev 03)
02:1f.0 PCI bridge: Intel Corporation 82870P2 P64H2 Hub PCI Bridge (rev 03)
03:0e.0 Ethernet controller: Intel Corporation 82545EM Gigabit Ethernet Controller (Copper) (rev 01)

---

### Post by SideOfPotatoes on 2008-08-05
I'm thinking of using this:

[http://www.guitarcenter.com/M-Audio-Delta-44-Digital-Recording-System-100883404-i1154072.gc](http://www.guitarcenter.com/M-Audio-Delta-44-Digital-Recording-System-100883404-i1154072.gc)

It says it's compatable...opinions?

---

### Post by djxcon on 2008-08-05
I have been using the M-Audio Audiophile 2496 for years in Linux (Fedora, Ubuntu, Studio64) and could not be happier.  This card has 2 RCA inputs (L, R), 2 RCA outputs (L,R) and MIDI capability.  Once you install the ubuntustudio packages, you will have a comprehensive software selection covering editing tools, production, software synths, etc.  Become familiar with Ardour 2 as this will most likely be your primary multitrack solution.  This tutorial is also pretty helpful: [www.out-of-order.ca/tutorials/ardour/]("www.out-of-order.ca/tutorials/ardour/")

---

### Post by ibuclaw on 2008-08-05
RME Support Linux in almost all their PCI and Cardbus products.
[http://www.rme-audio.de/forum/viewtopic.php?pid=15085](http://www.rme-audio.de/forum/viewtopic.php?pid=15085)

As for me, my SoundCard is an RME HDSP 9632
[As seen here.]("http://www.dv247.com/invt/20060/")

Although, my personal preferences actually deny UbuntuStudio. It is far too heavy and bloated for me.
Have a look at [64Studio]("http://64studio.com/"), their kernel patches feels far better tuned for realtime/low latency than any others I've used. (At least, on my low budget M/B|CPU hardware)

Regards
Iain

---

### Post by SideOfPotatoes on 2008-08-05
> **djxcon said:**
> I have been using the M-Audio Audiophile 2496 for years in Linux (Fedora, Ubuntu, Studio64) and could not be happier.  This card has 2 RCA inputs (L, R), 2 RCA outputs (L,R) and MIDI capability.  Once you install the ubuntustudio packages, you will have a comprehensive software selection covering editing tools, production, software synths, etc.  Become familiar with Ardour 2 as this will most likely be your primary multitrack solution.  This tutorial is also pretty helpful: [www.out-of-order.ca/tutorials/ardour/]("www.out-of-order.ca/tutorials/ardour/")

Wow...

That one even says that it is not linux compatable...

I kind of like the pricer one, even for just the fact that it has a breakout box (more accessable...).

I'll keep looking though!

-Jim

---

### Post by djxcon on 2008-08-05
tinivole: That is a nice looking sound card!

---

### Post by ZootHornRollo on 2008-08-05
> **djxcon said:**
> I have been using the M-Audio Audiophile 2496 for years in Linux (Fedora, Ubuntu, Studio64) and could not be happier.  This card has 2 RCA inputs (L, R), 2 RCA outputs (L,R) and MIDI capability.  Once you install the ubuntustudio packages, you will have a comprehensive software selection covering editing tools, production, software synths, etc.  Become familiar with Ardour 2 as this will most likely be your primary multitrack solution.  This tutorial is also pretty helpful: [www.out-of-order.ca/tutorials/ardour/]("www.out-of-order.ca/tutorials/ardour/")

i also have an Audiophile 2496 but have as yet been unable to get it to function in Hardy.  The alsa mixer diplays a sound output but i get zero sound out of the outputs. 

I went back to 7.10 where it worked straight away.

It is however a fantastic card for the money and provides lots of connectivity for recording.

---

### Post by djxcon on 2008-08-05
ZootHornRollo: I am running this card on Hardy no problem...we can probably work through the issue that you had if you decide to upgrade. The only real customization that I do is disable onboard sound which may also apply to the computer that SideOfPotatoes is going to receive.

---

### Post by Thelasko on 2008-08-05
I like something with at least one 3-pin XLR input for microphones.  Otherwise you will have to neck it down to 1/4" TRS.  Not that 1/4" is bad, it's just a matter of preference.

---

### Post by Thelasko on 2008-08-05
oooh! M-Audio is owned by [Avid]("http://www.avid.com/") *drooling* they make good stuff.  Look on their website to find [retailers]("http://www.m-audio.com/index.php?do=store.locator&name=&zipcode=&kind=webstore&image.x=10&image.y=6").  Maybe you can find a good deal if you shop around.  

I've personally had good luck with [B&H]("http://www.bhphotovideo.com/").  A friend of mine in the industry recommends [Full Compass]("http://www.fullcompass.com/").

---

### Post by SideOfPotatoes on 2008-08-05
> **Thelasko said:**
> I like something with at least one 3-pin XLR input for microphones.  Otherwise you will have to neck it down to 1/4" TRS.  Not that 1/4" is bad, it's just a matter of preference.

I thought about it, but I have some 1/4" mics, so that's not a HUGE deal.

Vocals kinda take the back seat in my line of work though (I'm mostly messing around with instrumental/jazz).

---

### Post by djxcon on 2008-08-05
What type of inputs are you looking to capture?  If the band is sending all of their instruments to a mixer, you could capture the output from that mixer (record out).  In this scenario, you really only need one R/L input on the sound card.

---

### Post by ByteJuggler on 2008-08-05
> **SideOfPotatoes said:**
> I thought about it, but I have some 1/4" mics, so that's not a HUGE deal.

Vocals kinda take the back seat in my line of work though (I'm mostly messing around with instrumental/jazz).

I recently bought M-Audio's Mobile Pre, [here]("http://www.dolphinmusic.co.uk/shop/flypage/product_id/3015").

For the money it's unbeatable, and as it's "class compliant" it worked out of the box with my Ubuntu Hardy laptop (even though Linux is not mentioned anywhere on the box or manuals.)  I literally took it out the box, plugged it in, and it was there instantly showing up as recording source/playback device.  It supports several input types (XLR mics, stereo 3.5mm stereo jack etc.) and several outputs as well as a headphone monitoring jack.  It also provides phantom power should you need it, and it all runs only off of your USB, so no extra power adapter needed.  It only records 16-bit 44/48khz, so if you need more resolution you might spend slightly more money and get something better, perhaps looking at the E-MU TrackerPre USB (or an internal PCI solution.)

---

### Post by SideOfPotatoes on 2008-08-05
> **ByteJuggler said:**
> I recently bought M-Audio's Mobile Pre, [here]("http://www.dolphinmusic.co.uk/shop/flypage/product_id/3015").

For the money it's unbeatable, and as it's "class compliant" it worked out of the box with my Ubuntu Hardy laptop (even though Linux is not mentioned anywhere on the box or manuals.)  I literally took it out the box, plugged it in, and it was there instantly showing up as recording source/playback device.  It supports several input types (XLR mics, stereo 3.5mm stereo jack etc.) and several outputs as well as a headphone monitoring jack.  It also provides phantom power should you need it, and it all runs only off of your USB, so no extra power adapter needed.  It only records 16-bit 44/48khz, so if you need more resolution you might spend slightly more money and get something better, perhaps looking at the E-MU TrackerPre USB (or an internal PCI solution.)

Hmmmmmm....

That's pretty nice...

---

### Post by SideOfPotatoes on 2008-08-05
I just bought the card with the breakout box (4 - 1/4" inputs).

GuitarCenter.com had a refurbed one for $99.99, so I picked it up. (This will only be a temp. solution for the next year or two anyway.)

Anywho, I'm sure I'll be writing back with issues as soon as I try to hook everything up!

Thanks everyone for your help!!!

:guitar:

-Jim

---

### Post by SideOfPotatoes on 2008-08-07
...and we're back!

I tried installing Ubuntu Studio last night, and it didn't go so well.

My friend burned it on DVD, and I was able to use my DVD drive to run it. It booted off of the disc just fine and ran through all of the usual prompts (keyboard, system clock, etc...).

Everything was done and it attempted to reboot, and I got this message:


[Crappy_Error_Message:]
Intel (R) Boot Agent GE v1.1.09
Copyright (C) 1997-2002, Intel Corporation
PXE-E61: Media Test Faailure, Check Cable
PXE-MOF: Exiting Intel Boot Agent

GRUB Loading Stage 1.5
GRUB Loading, Please Wait...

ERROR 2
[/Crappy_Error_Message]

...and it won't boot up after that...

What cable? I didn't touch anything...

What's "Error 2"? Any ideas?

Thanks for your help!!!

---

### Post by ByteJuggler on 2008-08-07
Hmmm.  Well, PXE is a standard for booting from Network.  It would suggest your boot-order in the BIOS has possibly been changed and that "Network boot" is now before the hard disk in the boot order. Which if it happened (for whatever reason) might also explain the GRUB error. (Obviously you're not using network boot, which is why it's complaining about the network cable etc. so that's understandable given that the computer is trying to boot off network initially.) 

Anyway, I would go into the BIOS, load setup defaults, then ensure the boot order is:
```
1. CD/DVD
2. HDD
```

Disable any other boot options (floppy, network etc.)

GRUB Error 2 (see the list [here]("http://www.uruk.org/orig-grub/errors.html#stage2")) means "Selected disk doesn't exist", which I have a hunch has to do with the above mixup somehow, so lets just try to sort out your boot order first and see if that affects/fixes the error or not.

---

### Post by SideOfPotatoes on 2008-08-07
> **ByteJuggler said:**
> Hmmm.  Well, PXE is a standard for booting from Network.  It would suggest your boot-order in the BIOS has possibly been changed and that "Network boot" is now before the hard disk in the boot order. Which if it happened (for whatever reason) might also explain the GRUB error. (Obviously you're not using network boot, which is why it's complaining about the network cable etc. so that's understandable given that the computer is trying to boot off network initially.) 

Anyway, I would go into the BIOS, load setup defaults, then ensure the boot order is:
```
1. CD/DVD
2. HDD
```

Disable any other boot options (floppy, network etc.)

GRUB Error 2 (see the list [here]("http://www.uruk.org/orig-grub/errors.html#stage2")) means "Selected disk doesn't exist", which I have a hunch has to do with the above mixup somehow, so lets just try to sort out your boot order first and see if that affects/fixes the error or not.

Ya' know...That just may do it... (I won't get to test it until tonight because it's at the fiance's house).

I declined setting up the network (because I am not currently connected to a network), and I had to mess with the boot order and hardware configurations to get it to see my DVD drive (and not my CD drive) as my primary drive to boot off of.

Sweet. That sounds like it will do it (I'm just happy that it may be as easy of a fix as that!!!).

Thank you Thank you Thank you (and, if it works, I'll thank you! :lolflag: )


:guitar:

---

### Post by Thelasko on 2008-08-07
There might be a "factory settings" in the boot order menu.  Using that option might save you some work.

I hear you on the "crappy error message" comment.  I haven't used ubuntustudio personally, but everyone I have talked to comments on how un-user-friendly it is.  I created an [Ubuntu brainstorm page]("http://brainstorm.ubuntu.com/idea/11864/") to try to get that fixed.

---

### Post by SideOfPotatoes on 2008-08-09
Ok...I think I broke it...

I swiched the boot order, and I still received an "error 2" from the GRUB Boot Agent. 

I got adventurous and went to the 'repair a broken system'. I reinstalled the GRUB Boot Agent into 'HD0' location. Still nothing.

I tried putting regular ol' 8.04 on it again, and I got this error:

(249.216529) Buffer I/O error on device FD0, logical block 0.

( there were square brackets, but I can't find them on my phone). Then, 30 seconds later, the same message pops up, but with the number: (287.313894).

Thanks again everyone!!!!!!!!!!!!!!!!!!

-Jim

---

### Post by ByteJuggler on 2008-08-09
Hmmm. FD0 is usually the first floppy drive.... What the *heck* is going on?

---

### Post by SideOfPotatoes on 2008-08-10
I tried unplugging the floppy drive...no luck.

:(

I just wanna jam...Is that so much to ask?!?!?!

:(

---

### Post by ByteJuggler on 2008-08-11
> **BDNiner said:**
> ... my m-audio USB sound card is not compatible with ubuntu...

Which one is that out of interest?

---

### Post by ByteJuggler on 2008-08-11
> **SideOfPotatoes said:**
> I tried unplugging the floppy drive...no luck.

:(

I just wanna jam...Is that so much to ask?!?!?!

:(

No it's not too much to ask.  I'll download Ubuntu studio and familiarize myself with its installation and try to help you.  

I would probably start over and firstly wipe the machine and do a stock 8.04 install again first, to ensure that works, and then maybe again try the Ubuntu studio install.  You seem to be having some strange problems though, and it's kind of hard to guess at what might be going wrong at the minute...

What happens if you reboot with the 8.04.1 CD and install using the "use whole disk" option?

---

### Post by SideOfPotatoes on 2008-08-11
> **ByteJuggler said:**
> No it's not too much to ask.  I'll download Ubuntu studio and familiarize myself with its installation and try to help you.  

I would probably start over and firstly wipe the machine and do a stock 8.04 install again first, to ensure that works, and then maybe again try the Ubuntu studio install.  You seem to be having some strange problems though, and it's kind of hard to guess at what might be going wrong at the minute...

What happens if you reboot with the 8.04.1 CD and install using the "use whole disk" option?

I was having the FD0 error with the "use whole disk" option, as a matter of fact, I've only been using the "use whole disk" option because I'm not attempting a dual-boot or anything similar.

I will try the stock 8.04.1 install again, and, if this does not work yet again, I may try to pull the harddrive and the DVD/CD drive and dump them in another spare computer and see if it's a computer-specific problem.

Thanks!!!

---

### Post by SideOfPotatoes on 2008-08-13
> **ByteJuggler said:**
> No it's not too much to ask.  I'll download Ubuntu studio and familiarize myself with its installation and try to help you.

Did you have a chance to try this yet???

:popcorn:

---

### Post by ByteJuggler on 2008-08-13
> **SideOfPotatoes said:**
> Did you have a chance to try this yet???

:popcorn:

I'm sorry no -- just kicked off the download... :( Thanks for reminding me... :)  Edit: Which version did you try btw?  32bit?  (Ah stuffit, I'll get both...)

---

### Post by ByteJuggler on 2008-08-14
OK, both downloaded when I woke up this morning, will have a look when I get home from work tonight.  BTW, I downloaded the 8.04.1 release, is this what you used, or did you use the 8.04 release?

---

### Post by SideOfPotatoes on 2008-08-14
> **ByteJuggler said:**
> OK, both downloaded when I woke up this morning, will have a look when I get home from work tonight.  BTW, I downloaded the 8.04.1 release, is this what you used, or did you use the 8.04 release?

The 8.04 version, and it was the 32.

Let me know if it works for you, because, then I'll just try to get my hands on the 8.04.1...

---

### Post by ByteJuggler on 2008-08-15
> **SideOfPotatoes said:**
> The 8.04 version, and it was the 32.

Let me know if it works for you, because, then I'll just try to get my hands on the 8.04.1...

Sorry life got in the way last night and we only got home very late so I didn't have time to look into this, will definitely do so tonight.  Apologies this is taking so long.  (I suggest you get the 8.0.4.1 release anyway in the meantime, if you can easily do so.)

---

### Post by SideOfPotatoes on 2008-08-15
> **ByteJuggler said:**
> Sorry life got in the way last night and we only got home very late so I didn't have time to look into this, will definitely do so tonight.  Apologies this is taking so long.  (I suggest you get the 8.0.4.1 release anyway in the meantime, if you can easily do so.)

Hey, there is absolutely no need to appologize! You are doing me a giant favor by doing this! (And I got caught biking 40 miles in the rain last night, so I didn't feel like fiddling with the computer much...)

Thanks again for your help, and I'll try to get a handle on 8.04.1!

-Jim

---

### Post by ByteJuggler on 2008-08-17
Right, well to make a long story short:  The install went fine, once I sorted out some space to put it, what to install, and solved some GRUB/boot issues (none of which was UbuntuStudio's fault -- I have a slightly convoluted setup with RAID-0 array and single disks, but didn't have room to put the new install so connected another disk, which threw my GRUB out of whack etc etc etc etc... eventually sorted it all out.)  

Anyway, looks rather slick I might say.  A word of warning, it can install shedloads of stuff, I dug up a 2.4GB partition which I thought would be plenty, but it all but filled it even though I installed *only* the audio production loadout and Ubuntu desktop (Don't forget that, othewise you end up with text only install lol.)  Over 20 sound production apps (having scanned the menu's), possibly more.

Anyway, Get 8.04.1 and see if tha works for you.  I've now got it as well so can try to assist...

---

### Post by SideOfPotatoes on 2008-08-18
I have someone getting 8.04.1 for me now (hopefully), so I'll give that a shot as soon as I have it.

Since your GRUB issue was not a studio problem, is it possible that my issue is also not with Ubuntu Studio? (The only thing I've done to the computer is switched out the hard drive.)

---

### Post by ByteJuggler on 2008-08-18
Hmmm.  Can you do me a favour and just describe exactly what your current HDD setup/config is.  I've just scanned the whole thread again as I've begun to forget all the salient details but am still unclear about what exactly your current config/setup is.  It is quite possible that you're having a GRUB issue rather than an Ubuntu studio issue.  

Ideally if you have a single HDD which is dedicated to your new install, I'll be tempted to walk you through nuking the existing partition table on the disk from orbit to make sure there's no pre-existant partitions that could cause trouble during installation, and then only trying the install.

---

