---
title: "PIC Device, Programmer, and Software advice needed"
date: 2007-11-11
forum: Programming Talk
---

### Post by Hopworks on 2007-11-11
Greetings!
This post is a little off the wall, but it's a neat project and I'm going to have to get my ahead around a lot of things to make it work. I'm way beyond making LED's blink now. :shock:

I am going to work on building a little project using a PIC18F4455 USB mcu that sends keyboard presses via USB to my Explorer 3250 cable box via the USB port on the front. I plugged a keyboard into it and was able to do channel changing with the numeric keypad, much to my surprise.

Why do it this way? I have a Vista-Only remote and IR Blaster MCE kit, where the remote is supported, but using the IR Blaster to change set top box channels is not. I could build a cheap serial interface, but this idea came along and just seemed more difficult but interesting to me. I'd rather send the keystrokes instead of fooling a parted USB keyboard or numeric keypad into doing it for me via a PIC. Just seems like a waste of hardware when the PIC can do at least USB 2.0 off the chip.

I'm sure I have a ton of things to get my head around so to get started, I looked at my bench and found the 18F4455 just sitting there waiting for a programmer. I decided to dump my K182 from Kitsrus because of lack of support for newer PIC's, and decided on the Pickit2 Debug Express bundle from Microchip. While waiting for my order to arrive, I started looking on how I can program it via Linux and I have some ideas.

What I want to ask is; is there a good forum I could go look at where people are programming PIC's via a Linux machine? I need to learn a lot about USB bootloaders, using the 4455 as a HID, communicating with two USB connections, writing code other than assembler and programming via tools under Linux. I installed sdcc this morning, but see that MPLAB doesn't support Linux, which I find very surprising.

I could use a Windows machine to get the boot loader into the chip though, then the door is wide open to use it with Linux without a programmer, or so I read.

Once I find a good forum on another site other than here that can help me in these areas, I'll probably post an edited version of this post over there, if you see it again don't be surprised.

Any advice on this project would be very much appreciated. I'd like to meet a few here that are doing some things with PIC's and Linux so I hope this thread brings a few out.

Thanks for your time!
Hop

---

### Post by rekahsoft on 2007-11-11
I have used SDCC for a computer engineering project last year in school...it tured out ok but getting the code onto the PIC was a pain...a bootloader would have been nice :P...although i don;t know much about then so i can't really help u there :S...i can wish u the best of luck tho :D

---

### Post by Hopworks on 2007-11-11
> **rekahsoft said:**
> I have used SDCC for a computer engineering project last year in school...it tured out ok but getting the code onto the PIC was a pain...a bootloader would have been nice :P...although i don;t know much about then so i can't really help u there :S...i can wish u the best of luck tho :D
Thank you! I need all the luck I can get!

I found a site that has a line of tutorials concerning setting up the PIC to act like a HID. Using a boot loader to program the chip, or 'update' the firmware is how I see it happening from Linux. That will probably involve me writing an application that runs in Linux, something I have never done. What would I use? Perl? C? Who knows. I love the options there though. Lots to learn.

By the time I get this project working for me on my PVR machine, there will be wireless interfacing with cable boxes probably, and a public-use standard that works. I don't care, it's a learning experience.

---

### Post by samjh on 2007-11-11
I've done two projects on PIC microcontrollers (both PIC16F series), but the programming was done on Windows, not Linux.  Bugger.

Take a look at these:

PIC16F bootloader: [http://mdubuc.freeshell.org/Jolt/](http://mdubuc.freeshell.org/Jolt/)

Lots of Pickit2 stuff for Linux: [http://mcuee.blogspot.com/](http://mcuee.blogspot.com/)

---

### Post by evymetal on 2007-11-11
I **think** that if you use gcc you should be able to compile C/C++ for the PIC (you may need to grab some extra libraries), though haven't done it for a long time (and never on Linux). No idea on the rest, though. My PIC programming only got as far as driving a set of DJ lights in various psudo-random patterns from simple on/of inputs, never did any serial work.

I guess that you should be able to use FORTRAN / whatever native-compiling language you want, gcc will probably support it, but last time I used PICs the memory was the largest problem, so you may have to resort to ASM.

(sorry if this is wrong, it's been a long time since i did any embedded stuff)

---

### Post by samjh on 2007-11-12
> **evymetal said:**
> I **think** that if you use gcc you should be able to compile C/C++ for the PIC (you may need to grab some extra libraries)

Negative.  Microchip PIC isn't one of GCC's supported platforms, and I haven't read anything unofficial otherwise.

The best open-source bet is SDCC ([http://sdcc.sourceforge.net/](http://sdcc.sourceforge.net/)), which does have official PIC16 and PIC18 support.

MPLAB works under Wine: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=2709](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2709) (Boy it's gotten a lot more user friendly.  When I used it the user interface was in ASCII graphics without mouse support!)

[quote=Hopworks]What I want to ask is; is there a good forum I could go look at where people are programming PIC's via a Linux machine? I need to learn a lot about USB bootloaders, using the 4455 as a HID, communicating with two USB connections, writing code other than assembler and programming via tools under Linux. I installed sdcc this morning, but see that MPLAB doesn't support Linux, which I find very surprising.[/quote]Microchip has official developer forum on its website:
[http://forum.microchip.com/default.aspx](http://forum.microchip.com/default.aspx)

---

### Post by Hopworks on 2007-11-12
> **samjh said:**
> I've done two projects on PIC microcontrollers (both PIC16F series), but the programming was done on Windows, not Linux.  Bugger.

Take a look at these:

PIC16F bootloader: [http://mdubuc.freeshell.org/Jolt/](http://mdubuc.freeshell.org/Jolt/)

Lots of Pickit2 stuff for Linux: [http://mcuee.blogspot.com/](http://mcuee.blogspot.com/)

Thanks for the links samjh, and they both look very useful, especially that first one, but shouldn't it be PIC18F series? Anyway, just read about that boot loader and that is exactly what I'm looking for! I just checked and my Pickit2 has shipped. woot. I can't wait to play with boot loaders this weekend.

---

### Post by Hopworks on 2007-11-12
> **samjh said:**
> The best open-source bet is SDCC ([http://sdcc.sourceforge.net/](http://sdcc.sourceforge.net/)), which does have official PIC16 and PIC18 support.I wondered about that, because I updated my SDCC to the latest snapshot but couldn't find a parameter to list supported devices, and sdcc -v yields the line...

[FONT="Courier New"][COLOR="DimGray"]SDCC : mcs51/gbz80/z80/avr/ds390/pic16/pic14/TININative/xa51/ds400/hc08 2.7.4 #4958 (Nov 11 2007) (UNIX)[/COLOR][/FONT]

and I see pic16 and pic14, but not pic18.

> **samjh said:**
> MPLAB works under Wine: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=2709](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2709) (Boy it's gotten a lot more user friendly.  When I used it the user interface was in ASCII graphics without mouse support!)
hehehe YUK!

---

### Post by samjh on 2007-11-12
> **Hopworks said:**
> I wondered about that, because I updated my SDCC to the latest snapshot but couldn't find a parameter to list supported devices, and sdcc -v yields the line...

[FONT="Courier New"][COLOR="DimGray"]SDCC : mcs51/gbz80/z80/avr/ds390/pic16/pic14/TININative/xa51/ds400/hc08 2.7.4 #4958 (Nov 11 2007) (UNIX)[/COLOR][/FONT]

and I see pic16 and pic14, but not pic18.

It's good to read the manual: [http://sdcc.sourceforge.net/doc/sdccman.html/node46.html](http://sdcc.sourceforge.net/doc/sdccman.html/node46.html)

They've made it a bit confusing but pic16 = 16-bit PIC, not PIC16.  It seems support isn't complete, though.

Otherwise, just use MPLAB on Wine.  It won't give you itchy bites or anything! :)

---

### Post by Hopworks on 2007-11-12
> **samjh said:**
> It's good to read the manual: [http://sdcc.sourceforge.net/doc/sdccman.html/node46.html](http://sdcc.sourceforge.net/doc/sdccman.html/node46.html)

They've made it a bit confusing but pic16 = 16-bit PIC, not PIC16.  It seems support isn't complete, though.

Otherwise, just use MPLAB on Wine.  It won't give you itchy bites or anything! :)
I didn't even think of that! The 16-bit, 14-bit PIC's.

I don't know wine yet, although I have it installed. "Install into wine" I read a lot, but I don't see an interface to do that, so I may get a bug bite or two. I'll get my can of 'OFF'. :shock: It's just little wine things I'll get my head around the next couple of days. Part of the reason I moved towards Linux.

---

### Post by samjh on 2007-11-12
Wine's easy to use.  At least, as easy to use as Cygwin on Windows.

Have you used Cygwin?  If you have, then Wine should be a piece of cake.

If you've got Wine installed, you just have to set it up.  Run: ```
winecfg
``` and choose the appropriate options.  The defaults are usually OK.

It will create a .wine directory in your home directory.  In .wine, there will be a drive_c directory, which is like a fake C drive.

Download MPLAB, and run the installer by prefixing it with wine.  So if the installer is setup.exe, you can run it with: ```
wine setup.exe
```

I haven't used MPLAB with Wine - Wine isn't even installed on my computer at the moment - but judging by the entry in WineDB, there shouldn't be too many problems.  MPLAB is free, anyway.

You might also be interested in [http://en.wikipedia.org/wiki/PIC_microcontroller](http://en.wikipedia.org/wiki/PIC_microcontroller).  Take a look near the bottom of the page, there are links to heaps of FOSS development resources for PIC chips.

But wait, there is more!  [http://www.gnupic.org/](http://www.gnupic.org/)  Old, but lots of stuff.

---

### Post by Hopworks on 2007-11-14
Thanks again samjh and others for the help and advice. I'll have my programmer by Thursday, and my18f4550 chips from Microchip on Friday. I ordered a couple of PIC18F4431 devices to test them with fan speed control, and those are on the supported list for the Pickit2 as well.

Doing MPLAB under wine after I post this. I don't need the programmer to play with it. I can't remember if it has a simulator, but if it doesn't, can you recommend one or at least some you heard of? Also, I can't wait to learn C! Always wanted to, now I have to. My first PIC projects were all in assembly. They did what I wanted, actually used PWM to dim LED's in an array, but because I had to do multiplex scanning, the desired brightness wasn't there. 

Hey, that leads me to a question I should have asked at the beginning of the thread, but forgot to. C optimization. I noticed that the compiler version from Microchip that does that costs a lot of money. Is SDCC a suitable answer to that? In your opinion I mean.

Take care!

Hop

---

### Post by chrisccoulson on 2007-11-14
For a development environment for PICs, have you considered Piklab? [http://piklab.sourceforge.net/]("http://piklab.sourceforge.net/")

I've not tried it personally, but looks fairly feature complete, with support for a variety of programmers and compilers.

---

### Post by Hopworks on 2007-11-15
> **chrisccoulson said:**
> For a development environment for PICs, have you considered Piklab? [http://piklab.sourceforge.net/]("http://piklab.sourceforge.net/")

I've not tried it personally, but looks fairly feature complete, with support for a variety of programmers and compilers.

Thanks for recommending that again. I saw that somewhere, in another thread perhaps. It definitely looks like something I need to try out, and I had forgot about it.

Problem I have with this, and any other application that isn't in the repositories is how to install it. It's one of those things I've been meaning to address, just never got around to it.

I'm using GNOME but the _[COLOR="Navy"][site]("http://piklab.sourceforge.net/download.php") [/COLOR]_offers KDE and QT libraries. And the list at the top shows...

    * Sources + Mandriva + Windows: Download piklab
    * Mandriva: older versions or lastest for cooker from here.
    * Fedora 5 and 6: available from Fedora Extras.
    * Slackware: available from here.
    * OpenSuse 10.x: available from here.
    * Debian: see availability from here.

*I figured Debian, but the stability for those packages doesn't look good...*

    *  lenny (testing) (electronics): IDE for PIC-microcontroller development
      0.14.5-1: alpha amd64 arm hppa i386 ia64 mips mipsel powerpc s390
    * sid (unstable) (electronics): IDE for PIC-microcontroller development
      0.15.0-1: amd64 i386 ia64 sparc
      0.14.5-1: alpha arm armel hppa m68k mips mipsel powerpc s390

sorry, but 'what?' hehehe.

I don't mind going right after this issue since it is something I want to understand. Could you suggest some reading on how to build executables the hard but exciting way?
**EDIT**: I found a thread here related to piklab and ubuntu [HERE]("http://ubuntuforums.org/showthread.php?t=123481") so maybe I'll pick up some parallel info about installing non-repository apps from that.

Thanks again for reminding me about piklab!

**AFTERTHOUGHT**: I never mentioned it before, and it is a little off the wall, but I'm real pleased at how UbuntuForums handles vB Code, especially the LINK control. I highlight text, and all I have to do is click that control icon, put the address in, and it does the rest with the selected text. I only wish it offered the option to color the text different and underline it to show it as a link without a mouse-over. First rate forum programming though. Just wanted to mention that.

Hop

---

### Post by chrisccoulson on 2007-11-15
> **Hopworks said:**
> Thanks for recommending that again. I saw that somewhere, in another thread perhaps. It definitely looks like something I need to try out, and I had forgot about it.

Problem I have with this, and any other application that isn't in the repositories is how to install it. It's one of those things I've been meaning to address, just never got around to it.

I'm using GNOME but the _[COLOR="Navy"][site]("http://piklab.sourceforge.net/download.php") [/COLOR]_offers KDE and QT libraries. And the list at the top shows...

    * Sources + Mandriva + Windows: Download piklab
    * Mandriva: older versions or lastest for cooker from here.
    * Fedora 5 and 6: available from Fedora Extras.
    * Slackware: available from here.
    * OpenSuse 10.x: available from here.
    * Debian: see availability from here.

*I figured Debian, but the stability for those packages doesn't look good...*

    *  lenny (testing) (electronics): IDE for PIC-microcontroller development
      0.14.5-1: alpha amd64 arm hppa i386 ia64 mips mipsel powerpc s390
    * sid (unstable) (electronics): IDE for PIC-microcontroller development
      0.15.0-1: amd64 i386 ia64 sparc
      0.14.5-1: alpha arm armel hppa m68k mips mipsel powerpc s390

sorry, but 'what?' hehehe.

I don't mind going right after this issue since it is something I want to understand. Could you suggest some reading on how to build executables the hard but exciting way?
**EDIT**: I found a thread here related to piklab and ubuntu [HERE]("http://ubuntuforums.org/showthread.php?t=123481") so maybe I'll pick up some parallel info about installing non-repository apps from that.

Thanks again for reminding me about piklab!

**AFTERTHOUGHT**: I never mentioned it before, and it is a little off the wall, but I'm real pleased at how UbuntuForums handles vB Code, especially the LINK control. I highlight text, and all I have to do is click that control icon, put the address in, and it does the rest with the selected text. I only wish it offered the option to color the text different and underline it to show it as a link without a mouse-over. First rate forum programming though. Just wanted to mention that.

Hop

I have a deb for piklab, but it's Gutsy 64-bit, just in case thats any use.

---

### Post by samjh on 2007-11-15
> **Hopworks said:**
>     *  lenny (testing) (electronics): IDE for PIC-microcontroller development
      0.14.5-1: alpha amd64 arm hppa i386 ia64 mips mipsel powerpc s390
    * sid (unstable) (electronics): IDE for PIC-microcontroller development
      0.15.0-1: amd64 i386 ia64 sparc
      0.14.5-1: alpha arm armel hppa m68k mips mipsel powerpc s390

sorry, but 'what?' hehehe.

Lenny (the testing branch) has a reputation for being pretty stable.  Expect Ubuntu-like stability from Lenny packages.

Sid is cutting-edge, so you should probably stay away from that.

Or you could compile it from source. ;)

---

### Post by Hopworks on 2007-11-16
> **samjh said:**
> Lenny (the testing branch) has a reputation for being pretty stable.  Expect Ubuntu-like stability from Lenny packages.

Sid is cutting-edge, so you should probably stay away from that.

Or you could compile it from source. ;)
I need to learn to compile it from source, but after all I've been through learning XFS and getting MythTV to behave, I think I'll be able to handle it. And thanks, I didn't know that about Lenny and Sid. :D

I have my Pickit2 from Microchip, and my new devices, but I ran into a little bug while testing it on my Windows laptop. It seems that the Pickit2 option in Programmers (MPLAB) is disabled. Do you or anyone else have experience with this programmer? I wonder if it is a firmware issue. I guess I should have researched that first before asking, but thought maybe you had a quick answer, as always. :)

The debugger package is pretty sweet. The demo board that came with the Pickit2 has a PIC16F887 (44 pin TQFP package) routed out to termination points all around the chip. and a SMD prototyping area for expansion. There are also 8 SMD LED's on the board for experimenting I imagine, and a potentiometer for testing the ADC functions. The decoupling capacitors are tiny, telling me that I really need to get into surface mount technology! I don't see a crystal, so I'm guessing it uses the internal 8MHz clock, but after looking closely, there is an area for installing an external clock to enjoy the 32MHz the chip is capable of. I would really love to get my hands on a 44 pin TQFP prototyping board like this, set up for the 16F and 18F devices. I'm sure they are out there. Then I can play with the big stuff with nothing more needed than a steady hand and a SMD soldiering iron. Maybe better eyes too. :D

Why they picked the 16F887 for the demo board is beyond me since the programmer is USB. I would think that the device would be a USB capable device, but then they do have other demo boards that plug into the Pickit2. I haven't looked but I'll bet they have a much more expensive USB demo board that is compatible. 

<after checking> OK, sure enough, there is a board for just that, that uses the 18F4550. It's the [DM163025]("http://www.microchip.com/stellent/idcplg?IdcService=SS_GET_PAGE&nodeId=1406&dDocName=en021940&part=DM163025"), and WOW! It's [$60 from Mouser]("http://www.mouser.com/search/ProductDetail.aspx?R=DM163025virtualkey57940000virtualkey579-DM163025"). When I last looked at these they were hundreds of dollars and untouchable! It appears to have termination points for every pin like the demo board I got, and other termination points as well. This might actually be my USB test prototyping board for my project!!! I'd have to install 11 pin inline connectors to route to a breadboard for design, and not sure how the breakout will affect the design, being routed away from the chip, you know, signal loss, voltage drop-off, that sort of thing. Maybe a high quality ribbon cable going to a 44 pin dip connector, if they make such a thing. :shock:

Sorry for the spew of text, but I'm real happy about this combo kit I got. If I were searching forums for this subject, all this info is something I would want to see. I try to always think about the mate that will want to follow the same path I am taking.

Hop

---

### Post by samjh on 2007-11-17
Unforunately I haven't used Pickit2.

However, a bit of Google ogling has revealed this:
[http://groups.google.gm/group/sci.electronics.design/browse_thread/thread/dc1d86231e91b810](http://groups.google.gm/group/sci.electronics.design/browse_thread/thread/dc1d86231e91b810)

Looks like that fellow has the same Pickit2 programmer & MPLAB problem as you.

---

### Post by RudolfMDLT on 2007-11-17
:) Sorry.

---

### Post by samjh on 2007-11-17
We're talking about MPLAB, not Matlab.  There are no native Linux binaries for MPLAB.

---

### Post by Hopworks on 2007-11-17
> **samjh said:**
> Unforunately I haven't used Pickit2.

However, a bit of Google ogling has revealed this:
[http://groups.google.gm/group/sci.electronics.design/browse_thread/thread/dc1d86231e91b810](http://groups.google.gm/group/sci.electronics.design/browse_thread/thread/dc1d86231e91b810)

Looks like that fellow has the same Pickit2 programmer & MPLAB problem as you.
Yes sir! That was a great link,and solved my problem. I installed MPLAB 8.0 and now I can use my programmer. Interestingly enough, my demo board sprang to life and the LED's are scrolling. Must be the default program to cycle those LED's. I got an error about the device ID being zero, but it might be a programmer firmware issue still. I'll look at that and make sure I'm clear on what to do, because I certainly don't want to hose my programmer. lol

Hey samjh, is it inappropriate to keep this thread running? It IS about my USB interface project, and mostly everything contained in this thread is related. Just asking because I bump it daily with a response to info I get from you guys. It's been a real valuable tool to help me into the development phase of this project.

Thanks again!

Hop

EDIT[clarification]: I mention the use of windows, but that's just to make sure my programmer I'm using is tip-top shape. The software supporting the Pickit2 is windows only, so I'm using my Windows laptop to test and familiarize myself with the programmer hardware, and the demo board that is paired with it. Once I know all is working well, I'll move that functionality to the Linux platform and continue.

---

### Post by samjh on 2007-11-17
> **Hopworks said:**
> Hey samjh, is it inappropriate to keep this thread running? It IS about my USB interface project, and mostly everything contained in this thread is related. Just asking because I bump it daily with a response to info I get from you guys. It's been a real valuable tool to help me into the development phase of this project.

As long as the moderators do not object to it, I think it's OK to continue this thread.  It is about programming, after all.  And I'm sure you won't be the last person in this forum to try PIC programming, other people may find this thread useful.

---

### Post by dwf_starband on 2007-11-20
I am wanting to start learning about microcontrolers.  I got an Asix Presto programmer and a PVK40 development board which has a PIC16F877A chip.  I have spent some time searching but havent found how to use the programer in linux.  I am interested in your thread here and will be watching to see what you do.  I would appreciate any help from anyone that knows about the Presto programmer or any insite they may have on my situation.

thanks,

dennis

---

### Post by dwf_starband on 2007-11-21
I installed the linux driver found [here.]("http://www.ftdichip.com/Drivers/D2XX.htm")
I was then able to use vmware server with a windows xp instalation and installed the windows drivers and software and was able to access the Asix Presto programer.  So far I have been able to transfer sample programs to the chip and they have worked!

dennis

---

### Post by Hopworks on 2007-11-21
> **dwf_starband said:**
> I installed the linux driver found [here.]("http://www.ftdichip.com/Drivers/D2XX.htm")
I was then able to use vmware server with a windows xp instalation and installed the windows drivers and software and was able to access the Asix Presto programer.  So far I have been able to transfer sample programs to the chip and they have worked!

dennis

Grats Dennis! That's a plus for sure, although I don't have any experience with vmware. Because of the holidays, I haven't had time to dive any further into the linux side at this time. As a matter of fact, I don't know that programmer you are using. I got so fed up with my kitsrus DIY K182 and the lack of support for that programmer, that I went to the Microchip PICKit2. The development board I got has a 16f887 on it, with lots of prototyping ability. fyi.

Just experimenting or do you have a specific task for your embedded project?

Hop

---

### Post by dwf_starband on 2007-11-21
The board I have(PVK40) also has the PIC16F877A.  Im just wanting to learn and experiment.

It sounds like you have more experience, I would be interested in how you did/are start(ing) your learning process, and any educational sites you may know or frequent.

vmware is amazing, it allows you to install any operating system inside your Ubuntu(or any OS really) computer  and run it in a window while still able to use and access your normal operating system.  And its free!!

dennis

---

### Post by Hopworks on 2007-11-22
How I got started with Microchip's MCU's is rather funny really. I've always been a breadboard tinker'r, but shelved it because most of the devices these days are surface mount, flat packs. Hard to breadboard.

Anyway, one year, one of the kids brought home a little toy their mom bought them that had flashing high output LED's, and they faded into each other, obviously running a program pattern of some kind.

So I started researching, because I wanted my pumpkins for halloween to use something more special than just a candle for illumination. That's when the pandora's box got opened.

I build my first programmer, don't remember the model, but it was a kitsrus DIY thing. Later on, it was buggy, using the serial port to communicate. Being a glutten for punishment, I bought another of their models, this time the K182. A USB model, and much smaller. It served its purpose, but the author past away, and the site was taken over by another entity. Their support for newer Microchip devices were slow coming, or not at all. Linux support looked like it was never gonna happen.

Now, doing amazing patterns of light from within a pumpkin head via high-output LED's seems like nothing compared to what I REALLY want to do with these wonderful devices from Microchip. Right now, I want to emulate a HID via the microcontroller. But there are other things I want to do. Control fan speed in a system, lighting, temperature reporting, all via the USB interface. Maybe even emulate a floppy device so I can easily install my raid drivers via solid state device. It's been done, but I want to do it from scratch.

There are toys out there that do all that, but I want something I can update the firmware via the USB connection, have total control over that device.

I haven't even touched on ethernet. I see other MCU platforms that deal with that. All my experience has been with PIC devices though so I'm reluctant to move to something else. Plus, programmers are expensive. I'll wait until I've reached my limit with Microchip's offerings.

HAPPY THANKSGIVING!

Hop

AFTERTHOUGHT: I'm no expert on compiling C with these devices. Don't wanna mislead you. Most of what I have done has been in assembly. I'm growing with it, much like you are. =)

---

### Post by half_monkey on 2009-03-03
I've been using piklab from the testing (Lenny) branch of debian with SDCC for some time now, and it's never let me down - i'd highly recommend it - seems stable, well polished and easy to use.
The only couple of caveats are that you need the programmer firmware from an install of MPLAB, and to use with SDCC there are a few library-related options that piklab doesn't have sensible defaults for.

---

