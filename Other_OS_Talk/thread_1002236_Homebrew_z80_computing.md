---
title: "Homebrew z80 computing"
date: 2008-12-04
forum: Other OS Talk
---

### Post by WaeV on 2008-12-04
This is a post from another forum.  I'm seriously considering doing this.  I want to expand further, however, and eventually get SymbOS running on it!  (See pictures below.)

> **"benryves"]I've posted about this on IRC and a little on here before switching host, but I thought I'd post a proper thread here as it seems to have got some GameDev members interested in Electronics. :) 

I'm currently working on a Z80 computer built from electronic components soldered to stripboard, so not very high tech stuff. It's running the Z80 BBC BASIC, and has simple hardware specs:

[list][*]10MHz Z80 CPU running at 2MHz.
[*]128KB Flash ROM to store the OS.
[*]32KB SRAM.
[*]128x64 graphical monochrome LCD.
[*]Two PS/2 ports (keyboard and mouse).
[*]I[sup]2[/sup]C bus to add further components.
[*]DS1307 real-time clock (I[sup]2[/sup]C) for time-keeping functions.[/list]

[center][img]http://www.benryves.com/bin/z180/2008.09.07.01.LookAroundYou.jpg[/img][/center]
I haven't worked out what I'm going to do for storage yet (I have some 32KB I[sup]2[/sup]C EEPROMs that may do the trick for removable storage, and they can be programmed externally for transferring files between a modern PC and this computer). The system only runs at 2MHz as the LCD requires at least 900nS when reading or writing data, and running the Z80 slowly seemed easier than designing a circuit that would force the Z80 to wait for a few extra clock cycles. I had planned on being able to switch between a 2MHz and a 10MHz clock by a multiplexer, but the changover from one signal to another is a bit noisy and generates several > 10MHz clock cycles which cause the system to crash.

More information and links to journal posts [here](http://www.benryves.com/?module=projects&product=z80computer).

I'm hoping that maybe some other people may have an interest in building computers said:**
> Electronics Explained[/url]* by M. W. Brimicombe. (You can preview the book on [Google Books](http://books.google.com/books?id=i7ar1oHyxtsC)).





Screenshots of SymbOS.  What I find really interesting about SymbOS is that it is a multitasking OS that runs on the z80 processor.  This is intersting because the z80 is the same processor in the ti-83 and ti-84+ calculators, among others.  Imaghine getting this to run on your calculator!  Of course, it would need a new screen, more RAM, better battery life...  But still!

[img]http://www.symbos.de/gfx/shots/cpc/symbos-cpc-desktop1.gif[/img]


[img]http://www.symbos.de/gfx/shots/cpc/symbos-cpc-desktop2.gif[/img]


[img]http://www.symbos.de/gfx/shots/apps/symbos-apps-symplay2.gif[/img]

---

### Post by jason.b.c on 2008-12-04
i so want to try this as well....

---

### Post by WaeV on 2008-12-04
It would be neat to have this on the go, but it seems to be difficult to find a screen that would support color / resolutions like that.

Hmm...

---

### Post by maybeway36 on 2008-12-04
The Sega Master System/Game Gear use the Z80 as the main processor, and the Megadrive had it too (usually used to control the music.) I wonder if you could use that somehow?

---

### Post by WaeV on 2008-12-04
Ooh! Potential lead on a color LCD screen!  [http://www.lcd-modules.com/color-LCD.htm](http://www.lcd-modules.com/color-LCD.htm)

Yeah, tons of things use a z80, whether made by Zilog or cloned by another company.  I think part of the z80's success was that the design was open-source, so anyone could make them.  Because everyone was using a z80 whether by Zilog or others, the demand went up and Zilog sold more.  I think.

---

### Post by zmjjmz on 2008-12-04
This is pretty awesome. I could see it being used in ultra-low power systems that could run for weeks on end with a standard laptop battery.

---

### Post by WaeV on 2008-12-04
That would be awesome.  How would one go about getting a laptop battery?

---

### Post by LateNiteTV on 2008-12-05
if i were you, i would check out netbsd and learn some z80 asm.

---

### Post by WaeV on 2008-12-05
Actually, the original quote is from [http://www.junemann.nl/maxcoderz/](http://www.junemann.nl/maxcoderz/) , a site dedicated to z80 assembly programming for ti-calculators.

I found it too confusing, and I moved on to newer projects, but the bit I did learn taught me a lot about programming, like how ridiculously slow if statements are.  Now that I know that, I've optimized all my intensive Ti-basic programs to run at least 10x faster.

I made a factoring program a while ago, the optimized it.  According to benchmarks I made using the school clock, it took about 4 minutes to determine that 8675309 is a prime number, the original would have taken over 3 days. :o



Why NetBSD?


I've been looking for a good screen with the resolution of an amstrad CPC, but it's so hard to find.  I think it's the smnallest resolution ever made: 320x200.  If anyone finds a "color CGA TFT LCD module" let me know. :)

Do you think a larger resolution screen could work, like if the extra pixels just stayed off or summat?

---

### Post by jason.b.c on 2008-12-05
> **WaeV said:**
> That would be awesome.  How would one go about getting a laptop battery?

LOL i'll sell you a dell lap batt... it works...?!;)

---

### Post by WaeV on 2008-12-05
Hopefully not one of the exploding variety? ;)


Video of SymbOS in action.  As you watch this, keep in mind that the processor is clocked at a mere 10 MHz!  (That's a full 5MHz less than the Ti-84+)  Now that's what I call efficient design.
[http://www.symbos.de/videos/trexsymbos1.zip](http://www.symbos.de/videos/trexsymbos1.zip)

---

### Post by mips on 2008-12-05
Why not run this in an emulator, seems much easier than sourcing & building hardware.

---

### Post by 3rdalbum on 2008-12-05
> **WaeV said:**
> Video of SymbOS in action.  As you watch this, keep in mind that the processor is clocked at a mere 10 MHz!  (That's a full 5MHz less than the Ti-84+)  Now that's what I call efficient design.
[http://www.symbos.de/videos/trexsymbos1.zip](http://www.symbos.de/videos/trexsymbos1.zip)

Downloading right now. But can you play the video on SymbOS?

I actually had a hard time believing that you can play digital videos on a 10Mhz z80; until I remembered that you could play 256-colour digital videos on a 20Mhz 68030 running System 6.

---

### Post by Sorivenul on 2008-12-05
> **mips said:**
> Why not run this in an emulator, seems much easier than sourcing & building hardware.

Might be easier, but it takes away the fun and experience...

After reading this thread, I think this would be a fun Holiday break project.

---

### Post by WaeV on 2008-12-05
I'm building this for fun, not necessity.  Plus an emulator isn't portable.

---

### Post by BlueSkyNIS on 2008-12-05
Where can you guys buy parts for this? I searched everywhere for Z80 CPU, PIO, SIO...but nothing. Are these parts still being manufactured by Zilog?

---

### Post by LateNiteTV on 2008-12-05
> **WaeV said:**
> Actually, the original quote is from [http://www.junemann.nl/maxcoderz/](http://www.junemann.nl/maxcoderz/) , a site dedicated to z80 assembly programming for ti-calculators.
 
I found it too confusing, and I moved on to newer projects, but the bit I did learn taught me a lot about programming, like how ridiculously slow if statements are. Now that I know that, I've optimized all my intensive Ti-basic programs to run at least 10x faster.
 
I made a factoring program a while ago, the optimized it. According to benchmarks I made using the school clock, it took about 4 minutes to determine that 8675309 is a prime number, the original would have taken over 3 days. :o
 
 
 
Why NetBSD?
 
 
I've been looking for a good screen with the resolution of an amstrad CPC, but it's so hard to find. I think it's the smnallest resolution ever made: 320x200. If anyone finds a "color CGA TFT LCD module" let me know. :)
 
Do you think a larger resolution screen could work, like if the extra pixels just stayed off or summat?
 
sorry, i was drunk when i posted that. netbsd doesnt run on z80.

---

### Post by init1 on 2008-12-05
> **mips said:**
> Why not run this in an emulator, seems much easier than sourcing & building hardware.
But that's a lot less fun ;)

---

### Post by WaeV on 2008-12-05
> **BlueSkyNIS said:**
> Where can you guys buy parts for this? I searched everywhere for Z80 CPU, PIO, SIO...but nothing. Are these parts still being manufactured by Zilog?

30 second search:
[http://www.google.com/products?hl=en&q=z80%20zilog%20processor&um=1&ie=UTF-8&sa=N&tab=wf](http://www.google.com/products?hl=en&q=z80%20zilog%20processor&um=1&ie=UTF-8&sa=N&tab=wf)

---

### Post by BlueSkyNIS on 2008-12-06
> **WaeV said:**
> 30 second search:
[http://www.google.com/products?hl=en&q=z80%20zilog%20processor&um=1&ie=UTF-8&sa=N&tab=wf](http://www.google.com/products?hl=en&q=z80%20zilog%20processor&um=1&ie=UTF-8&sa=N&tab=wf)

The only problem is they do not ship parts to my country... :(

---

### Post by mips on 2008-12-06
> **Sorivenul said:**
> Might be easier, but it takes away the fun and experience...



True there is a fun factor involved if you are kinda new to it. For me I have build enough singleboard computers/microcontrollers in my lifetime.

---

### Post by WaeV on 2008-12-06
> **BlueSkyNIS said:**
> The only problem is they do not ship parts to my country... :(

The first result might not, but look around, you may get luck with the second, or third etc.  The guy who wrote the original quote used the following sources (he's from the UK):

[http://uk.farnell.com/1081891/semiconductors-integrated-circuits/product.us0?sku=zilog-z84c0010peg](http://uk.farnell.com/1081891/semiconductors-integrated-circuits/product.us0?sku=zilog-z84c0010peg)
[http://uk.rs-online.com/web/](http://uk.rs-online.com/web/)
[http://www.rapidonline.com/Electronic-Components/Optoelectronics/LCDs-And-Accessories/Backlit-graphic-LCD-modules/72887/kw/57-1084](http://www.rapidonline.com/Electronic-Components/Optoelectronics/LCDs-And-Accessories/Backlit-graphic-LCD-modules/72887/kw/57-1084)

---

### Post by mips on 2008-12-06
> **BlueSkyNIS said:**
> Where can you guys buy parts for this? I searched everywhere for Z80 CPU, PIO, SIO...but nothing. Are these parts still being manufactured by Zilog?

You should be able to buy them from electronics stores that stock this type of stuff.

---

### Post by WaeV on 2008-12-06
I still can't find a website that offers the purchase of one 320x200 lcd module with multiple colors.

I think I want "TFT" based on what comes up when I include that in a search but I don't really know what that is.

Edit:  According to this site [http://www.glyn.co.nz/Displays_EDT.htm](http://www.glyn.co.nz/Displays_EDT.htm) I could use TFT or STN.

---

### Post by stream303 on 2008-12-08
Don't forget the 8080 based Imsai.  Looks like you can still get them, and even run modern hardware inside as:

[http://www.imsai.net/](http://www.imsai.net/)

Imagine running Intrepid one moment, and then classic 8080 stuff the next. :)

---

### Post by cardinals_fan on 2008-12-08
> **LateNiteTV said:**
> if i were you, i would check out netbsd and learn some z80 asm.
> **WaeV said:**
> 
Why NetBSD?

While NetBSD doesn't run on z80 (as noted above), it does run on some fairly cool stuff...

[http://www.embeddedarm.com/software/arm-netbsd-toaster.php](http://www.embeddedarm.com/software/arm-netbsd-toaster.php)
[IMG]http://www.embeddedarm.com/images/misc/netbsd-toaster-pc.jpg[/IMG]

---

### Post by WaeV on 2008-12-08
:)

[IMG]http://imgs.xkcd.com/comics/rtfm.png[/IMG]

---

### Post by GoS_ on 2008-12-09
It's too bad there aren't monitors that can be easily mapped to RAM (like the TI-86's).  Then again, it would also probably be a lot harder to connect a memory mapped display. It seems like most monitor options for these types of projects have their own RAM.  Anyway, what you have looks really cool.  Z80 assembly is, in my opinion, the most fun programming language, so I'd be very interested in trying something like this too.

Good luck with your future Z80 endeavors.

---

### Post by WaeV on 2008-12-09
Ben suggested a display with a controller already set up, so all that I have to do is map the image to RAM for it to display.  The problem is that every 320x240 or 320x200 TFT LCD module either has no controller, doesn't mention a controller, or is only sold in bulk to corporations.

---

### Post by mips on 2008-12-10
> **WaeV said:**
> The problem is that every 320x240 or 320x200 TFT LCD module either has no controller, doesn't mention a controller, or is only sold in bulk to corporations.

Have you had a look at the Farnell catalogue?

Would something like this do (see data sheet), [http://www.futureelectronics.com/en/technologies/semiconductors/lcd-display-solutions/active-matrix-displays/Pages/9930355-LQ050Q5DR01.aspx?CrossPart=](http://www.futureelectronics.com/en/technologies/semiconductors/lcd-display-solutions/active-matrix-displays/Pages/9930355-LQ050Q5DR01.aspx?CrossPart=)

---

### Post by WaeV on 2008-12-10
I hadn't I probably should.

$250?  Errr...

The size and quality is right, but I couldn't find any data on the LCD controller.

I've been looking around on eBay as well, but it's mostly PSP replacement screens.  I might be able to get that to work...

---

### Post by mips on 2008-12-10
> **WaeV said:**
> I hadn't I probably should.

$250?  Errr...

The size and quality is right, but I couldn't find any data on the LCD controller.

I've been looking around on eBay as well, but it's mostly PSP replacement screens.  I might be able to get that to work...

Have you considered a higher resolution lcd as it seems there are a lot more options for them. This obviously would require more ram I think.

Anyway, good luck in finding a display.

---

### Post by WaeV on 2008-12-10
Thanks for your help!

I hadn't considered a higher resolution display because SymbOS runs at a resolution of 320x200 (CGA).

---

### Post by WaeV on 2008-12-11
Well, it looks like the idea to get SymbOS running on a homebuilt PC is falling through - it's closed source and needs to be recompiled even for close relatives of the CPC.  I'm looking at getting something running, however.  I was pointed to contiki by Ben.  I think I'll attempt to get a text OS running as Ben did first, though.

[http://www.sics.se/contiki/](http://www.sics.se/contiki/)

[IMG]http://www.protovision-online.de/hardw/gfx/contiki.png[/IMG]

---

### Post by frenchn00b on 2008-12-27
I installed : 

1/ libdsk-1.3.0.tar.gz 
2/ xjoyce  [http://www.seasip.demon.co.uk/Unix/Joyce/index.html](http://www.seasip.demon.co.uk/Unix/Joyce/index.html)
and tried:
 
3/
```
/tmp/pcw$ xjoyce -a Sym-PCW.DSK
JOYCE PCW Emulator v2.2.0
JOYCE will emulate a PCW 82048 (or 92048)
^[^[^[
```

and got white death screen ... is it normal?
:(

---

