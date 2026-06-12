---
title: "Commodore 486sx-25 - boot from hard drive"
date: 2008-03-21
forum: Other OS Talk
---

### Post by Kulgan on 2008-03-21
Hi all!

Got myself some new hardware... a nice old Commodore... 

Now, I've seen them before, but never actually used one myself. And this one isn't doing what I want it to. I have everything set up - I have a keyboard with the pre-PS/2 connectors, a serial port mouse, if I ever need it, and it works with my monitor.

The problem is this: It boots from the floppy. Only the floppy. I have tried looking in the BIOS/CMOS/whatever the hell it's actually called, but there is nothing there related to boot order. The hard drive is set up (as far as I know) properly (it's an IDE, thank goodness...): [http://www.computerhope.com/hdquantu.htm](http://www.computerhope.com/hdquantu.htm) [bottom of page, Quantum ProDrive ELS 85]. I'm not getting any errors (wish I were), but it just will not try the hard drive (tries floppy, fails, tells me to insert media). Lame.

So if anyone knows what might be going wrong here, I would appreciate knowing :D

-K

---

### Post by Bungo Pony on 2008-03-22
Is the hd set to "master"? 

The hd may also be shot. Try swapping it out with another old IDE drive and see if that works.

---

### Post by JonUK76 on 2008-03-22
Does the hard drive have anything on it? I.e an operating system?

If you Google for boot disks you will find various boot floppies you can download to get you started. What OS did you intend to run on it?

---

### Post by Kulgan on 2008-03-22
Just got home again - replaced the hard drive, set it to master, and the thing now goes into an infinite loop of trying and failing to boot netBSD. Success!

I had tried replacing the hard drive before, but since the original didn't even have jumpers (O.o), I didn't think about checking that. 

Some floppy distro of linux, perhaps, or a (very) minimal install of netBSD. Or perhaps freeDOS. Any recommendations?

Thanks!
-K

---

### Post by Bungo Pony on 2008-03-22
A 486 *should* play MP3s. You could put some version of DOS on it, get a DOS MP3 player, and play music on it. You can also put a bigger hd in it if you use drive overlay software.

Lately, I've been trying to get DOS to read from USB flash drives. So far, I can get it to find the device, but I cannot access the files. You could probably get a USB DVD drive to work on it. Fill a DVD full of MP3s and you've got a nice little jukebox. The trick is getting the drive to work.

Or you could use it to play old DOS games.

---

### Post by Kulgan on 2008-03-22
Yeh, I'm thinking games. And freedos seems to have a decent interest in the gaming area, so I guess I'll try that first.

---

### Post by init1 on 2008-03-22
I recommend FreeDOS, it'll play games and do word processing just fine. You could do Linux, but I'm not sure if you have enough RAM for it.

---

### Post by Kulgan on 2008-03-22
I think there should be floppy distros that can handle 4MB of ram. But I'll go with freedos for now. I'm having to burn an 8mb CD... crazy...
It wil also require installing a cd drive... which should be interesting... this thing probably doesn't even know what a CD drive is...

Edit:
I think I may have found the - or at least a - problem. The mobo battery is dead, so every time the power cable is removed (rather often, since I only have four of them), the bios is reset - along with all the hard drive settings. Sucks.

Edit 2: 
What am I supposed to put for cylinder, heads and sectors for a CD??

---

### Post by JonUK76 on 2008-03-22
From memory the PC's from that sort of era didn't know what a CD drive exactly - not like today anyway where you plug it in and go. To use a CD drive you had to connect it through a sound card - which would have a proprietary interface on it ( Sony or Panasonic interfaces for example) or alternatively you could use SCSI drives.  IDE (ATAPI) CD drives came along a bit later. The original IDE standard supported a maximum drive size of 528mb IIRC, and didn't support CD-Rom drives.

---

### Post by Kulgan on 2008-03-22
So basically I need to find something that will install from floppies. It's having a hard time just duplicating what it did earlier (booting from hard drive) so I think a CD drive is out of the question. 
Sound card? Seriously? This is making me feel very young indeed...

---

### Post by JonUK76 on 2008-03-22
> **Kulgan said:**
> 
Sound card? Seriously? This is making me feel very young indeed...

:lolflag:

Yep cards like this for example with a Creative/Panasonic interface - [http://cgi.ebay.com/Soundblaster-16-CT2230-16-Bit-ISA-Sound-Card-w-Panasoni_W0QQitemZ350037585338QQihZ022QQcategoryZ3701QQrdZ1QQssPageNameZWD1VQQ_trksidZp1638.m118.l1247QQcmdZViewItem](http://cgi.ebay.com/Soundblaster-16-CT2230-16-Bit-ISA-Sound-Card-w-Panasoni_W0QQitemZ350037585338QQihZ022QQcategoryZ3701QQrdZ1QQssPageNameZWD1VQQ_trksidZp1638.m118.l1247QQcmdZViewItem)

---

### Post by Kulgan on 2008-03-22
Hmm... I have a similar looking card in this thing. It's not a sound card, it's the card for the com, joystick and lpt ports, but it seems to do the same thing - at least, that's where the IDE and floppy connectors stem from. 

So you're saying I would need an extra card on top of that to get the CD drive working... I suddenly like nice ATX standards-compliant PCI card rather more than before... 

I'll see what I can do by way of floppy OS tomorrow. freeDOS seems to have abandoned floppies (you can make a floppy that will force the machine to boot off the CD drive... big deal... ) I have quite a bit of work due on Tuesday, though, which I should probably get started on, so we'll see how it goes. Distrowatch has a section on floppy distros, I seem to remember.

Thanks all!
-K

---

### Post by K.Mandla on 2008-03-22
> **JonUK76 said:**
> :lolflag:

Yep cards like this for example with a Creative/Panasonic interface - [http://cgi.ebay.com/Soundblaster-16-CT2230-16-Bit-ISA-Sound-Card-w-Panasoni_W0QQitemZ350037585338QQihZ022QQcategoryZ3701QQrdZ1QQssPageNameZWD1VQQ_trksidZp1638.m118.l1247QQcmdZViewItem](http://cgi.ebay.com/Soundblaster-16-CT2230-16-Bit-ISA-Sound-Card-w-Panasoni_W0QQitemZ350037585338QQihZ022QQcategoryZ3701QQrdZ1QQssPageNameZWD1VQQ_trksidZp1638.m118.l1247QQcmdZViewItem)
Ack, I remember those. Things have definitely gotten better since then.

---

### Post by Bungo Pony on 2008-03-23
> I think I may have found the - or at least a - problem. The mobo battery is dead, so every time the power cable is removed (rather often, since I only have four of them), the bios is reset - along with all the hard drive settings. Sucks.

Most PCs take the same mobo battery. It's usually a circular, silver 3v battery that you can get at almost any store that sells batteries. There's a place in my city that sells a 5pk for $3.99. There's two types of this battery (I can't remember the type numbers) but get the thick type, not the slim type. Better yet, pull the battery out of the mobo and take it with you to the store.

Unfortunately, some mobos from that era take special types of batteries, and if you don't find a silver round 3v battery, you may find a rectangular battery (or even something else). You won't be able to do much about this unless you devise a hardware hack.


> To use a CD drive you had to connect it through a sound card

You do NOT have to connect your CD drive to a sound card. You also don't need to configure your CD drive in the BIOS. If you have only one hard drive set to master, you can connect your CD drive as a slave on the same IDE cable. However, you will not be able to boot from CD. You will have to configure DOS to see your CD ROM drive.

You'll either need to install DOS by putting the hard drive in a PC that CAN boot from a CD, or install DOS from the floppy drive. You can move the hard drive from PC to PC since DOS (normally) doesn't automatically install drivers - you usually have to configure them manually.

After your OS is installed, you'll have to make sure you have two files in C:\ to make your CD Drive work:

[b]mscdex.exe
ibmidecd.sys[/b] (this is a somewhat universal CD-ROM driver, search for it on google)

edit the autoexec.bat file to include the following line:

```
C:\MSCDEX /D:MSCD001 /M:15 /V /L:D
```

Then, edit your config.sys file to include the following lines:

```
DEVICE=C:\IBMIDECD.SYS /D:MSCD001
LASTDRIVE=Z
```

Reboot, and your CD-ROM drive *should* work in DOS. If it doesn't, you may need to find a DOS driver that will support your CD-ROM drive

Oh, and if you have a sound blaster card installed, put this line in your autoexec.bat file:

```
SET BLASTER=A220 I5 D1 T4 
```

Reboot, and your sound card should work.

---

### Post by Kulgan on 2008-03-23
Thanks for the info, all of you :D

I'm getting a set of DOS floppies next week, so I should be able to test it out then. 

Bungo Pony:
I know what you mean - and the two other comps I have open at the moment have one. But I can't find anything similar to on the Commodore. Unless it's under the motherboard... 
If I knew what the mobo was, I could find something here: [http://artofhacking.com/th99/](http://artofhacking.com/th99/)
Shouldn't it say that somewhere? The BIOS chip says 486DX (it's an AMI) but beyond that I have no idea.

I randomly read on-line about certain boards not having replacable batteries, and therefore providing a socket for an external one, but I can't seem to find that, either, so it doesn't really hep much. 
Here's something else about that:
> With some older motherboards, the battery was soldered on. This is especially true with the 386 and early 486 motherboards.
- [http://www.errorforum.com/hardware-tutorials/303-how-replace-cmos-battery.html](http://www.errorforum.com/hardware-tutorials/303-how-replace-cmos-battery.html)
I can't see anything that looks like a battery soldered on to the board, either :(

---

### Post by Bungo Pony on 2008-03-23
I might be able to locate it if I could see the boards. But it's possible that there may have been an 'external' battery that someone may have removed when they had the case apart. Thank god the batteries are all standardized now.

I was tempted to pick up one of those old Commodore PCs a while back. Maybe I should have :)

---

### Post by Kulgan on 2008-03-23
Not very good pics. They are taken with my phone, so what can you expect.

I think it may be on the pic numbered 64 (boxed in in red). There are two of them, and they read 
```
Kyocera
KX0-01-1
```
 for the first two lines, then:
```
14.31818MHz
9248 JAPAN
```
for the first one and
```
50.0000MHz
9225 JAPAN
```
for the second. 

Don't know if that means anything. It doesn't to me :D

---

### Post by Bungo Pony on 2008-03-23
I don't see any pics...

But from what you've described, it seems you've identified two crystals, and I don't know what the other part is.

Also, if that computer isn't Y2K compatible, there would be no point in using the clock anyway :)

Did you try doing a google search on the model number of that computer? The last one that I can tell was released was the PC-60: 80386 25 MHz system with a tower case and a 60MB to 200MB hard disk.

Also, how are you making the floppies that you're going to use?

---

### Post by Bungo Pony on 2008-03-23
I found a pic of a PC-10 Motherboard (gotta love the zoom feature in Compiz!). I've circled what is probably the battery, but I can't clearly see the value on it. I do believe it's a 3.6v battery.

I'm not sure if you can buy those batteries anymore. A hardware hack may be able to fix that, such as a 9v battery going through a zener diode, or even sodering three AA batteries together. Either way, you need to be handy with a soldering iron.

---

### Post by JonUK76 on 2008-03-23
> **Bungo Pony said:**
> You do NOT have to connect your CD drive to a sound card. You also don't need to configure your CD drive in the BIOS. If you have only one hard drive set to master, you can connect your CD drive as a slave on the same IDE cable. However, you will not be able to boot from CD. You will have to configure DOS to see your CD ROM drive.


Fair enough then. My recollection was that early versions of IDE, like I guess might be on this PC, did not support CD Rom drives. ATAPI CD-Roms seemed to come about when the E-IDE interface (and drives larger than 528mb) became available.

EDIT - [http://www.pcguide.com/ref/hdd/if/ide/std.htm](http://www.pcguide.com/ref/hdd/if/ide/std.htm)

---

### Post by Kulgan on 2008-03-23
Hehe, forgot to attach pics. Do it all the time :/

You're probably right that what I am thinking is not the battery. I have nothing against throwing together a few parts when I know where to stick the end result. But without that... well.. yeh... 

I would write the .img files with dd on another old comp I have, but I have a teacher who should have the installation disks around - which I can always duplicate if i need to. 

I have set the date to past 2000 before, but that's not really the problem. It's the hard drive settings. They are erased every time the mobo runs out of power, and it then resorts to the defaults - at least, that's my theory, based on booting and checking the setting many, many times. 

Google gives mentions of the same machine, without actually presenting any useful information (Closest matches are "Commodore C486SX-20" and "Commodore C486-25C" on [http://support.microsoft.com/kb/83210/en-us](http://support.microsoft.com/kb/83210/en-us) ). 

Also:
> DT 486SX-25   80486SX @ 25 MHz, SVGA, 4MB RAM, 80 MB HD.
* DT 486SX-25   80486SX @ 25 MHz, SVGA, 4MB RAM, 120 MB HD. 
 - [http://www.zimmers.net/commie/docs/cbm-products.txt](http://www.zimmers.net/commie/docs/cbm-products.txt) (about half way down)

So this thing was produced. I don't have some sort of imaginary box sitting here. But it can't have been very popular. 
List of Commodore machines:
[http://www.xs4all.nl/~lagendr/Menu/COMP.htm](http://www.xs4all.nl/~lagendr/Menu/COMP.htm)

What I have is close to this one:
[http://www.xs4all.nl/~lagendr/Pagina/COMP-PC486-25.htm](http://www.xs4all.nl/~lagendr/Pagina/COMP-PC486-25.htm)

However, my "Intel Inside" sticker is red, not blue (O.o), and the on/off swith is to the right of the floppy drive. (The two on the left are reset and turbo - whatever turbo does.)

I'm trying to find better documentation for it, but I don't think Wikipedia so much as mentions it, so I don't think I have much chance on the rest of the web either.

---

### Post by mips on 2008-03-23
Those silver rectangular things with the ? are what provides the PC with it's clocking signals as in how fast the cpu or bus operates at.

You might want to check for a battery somewhere inside the actual case, I have seen batteries that are seperate from the motherboard before.

---

### Post by Bungo Pony on 2008-03-23
JonUK76, I recall the soundblasters with the IDE connector on them. In fact, I think I have one around here somewhere. As far as I know, it was just a regular IDE controller. Older PCs had their IDE controllers on ISA cards instead of on the motherboard which it looks like is the case with this computer.

I don't see anything that resembles a battery on the motherboard either, unless it's beside the RAM (which I cannot see from the pics). And it definately could be a battery mounted in the case (usually with velcro) that connects to the motherboard, but I don't see a connector anywhere for it.

Those items that you circled are crystals.

I also seem to recall seeing the silver 3v battery on some ISA cards in the past, but don't quote me on that one as my memory is a bit foggy on that issue.

> (The two on the left are reset and turbo - whatever turbo does.)
From what I recall, the turbo button cuts down your CPU speed which I believe was to help with compatibility for older software that ran too fast on 'modern' equipment. Most PCs back then had turbo buttons.

That's probably the last PC that Commodore manufactured before they went TU. Definately an interesting PC!

> I have set the date to past 2000 before, but that's not really the problem. It's the hard drive settings. They are erased every time the mobo runs out of power, and it then resorts to the defaults - at least, that's my theory, based on booting and checking the setting many, many times.

I'd forgotten about that. I don't blame you for wanting to get that problem fixed, but unfortunately I can't see anything in your pics indicating the location of the battery, or a connector for the battery. If I knew the pinout, you could probably solder a battery directly to the processor, but you REALLY need to be careful that you solder the right pins!

---

### Post by Kulgan on 2008-03-23
Ok, so I knew this would happen. I was poking around in the area around the RAM, looking for something even vaguely resembling a battery, when I see BATTERY on the board. Couldn't have been more obvious.

It is indeed an external battery, in a little plastic box, tucked under the bar that holds the PSU in place.  I'm not sure I want to open it, so I havent. It weighs less than a standard AA battery, and the label says it's 3.6V. 

The connectors aren't soldered on - they have their own little connectors. This makes things one hell of a lot easier :D

Battery reads:
> 
3.6V High energy lithium battery warning:
Fire, Explosion And Severe Burn Hazard.
Do Not Recharge, Disassemble, Heat Above 100C
Incinerate Or Expose Contents To Water

(no, ucwords was not done by me... ) and the same in German. Yay. 

As I said, I'm hesitant to open the plastic encasing, even if it looks like there's one section of it that's "meant" to come off.

Edit:
Took it apart. Wasn't as interesting as I could have hoped. Looks like an old camera battery. Gives between 0.07 and 0.08V - looks like it was (part of) the problem?
I guess the next step is finding something to replace it with. Would it be OK to just use two AAs? 0.06V shouldn't make a difference anyway, so long as it's 0.06 less... I think?

---

### Post by Bungo Pony on 2008-03-23
Excellent!

It looks like it's basically the same battery that I pointed out on that other circuit board.

You'll probably want to solder three AA batteries together (1.5 v each). The extra .9 volts shouldn't hurt anything, but the lack of the .6 volts might cause problems as your batteries lose charge over time.

When connecting the batteries, connect plus to minus, just like you were putting them into a ghetto blaster, but use wire to connect them together.

Before soldering each end of the battery, take a knife or sand paper and scratch each end to make it a bit rough. The solder will stick much better. After, put the batteries into a case (or wrap them in electrical tape) preferably away from the motherboard, just in case they end up leaking from leaving them in for a long period of time. Use the connector on the old battery to connect the new ones. Connect the red wire to the + end of your battery 'circuit', and the black wire to the - end. Double check the voltage with a meter; it should be a bit higher than 4.5v. Connect, and away you go!

---

### Post by Kulgan on 2008-03-24
Awesome. Thanks!

So it should be a series rather than parallel circuit, then. Time to see if I can actually find the soldering iron. Haven't used it ages :D

update:
Got it working, though it's probably the messiest job ever done. The batteries weren't quite 1.5V, so it gives out pretty much exactly 3.7 
Testing...

It's working. At least, it booted twice in a row without having to enter in the settings again, and it's still 2008. Very good indeed. 

Thanks for all the help! I'm just waiting for the DOS disks before I can install. Now I've got that warm fuzzy feeling you get when you fix something broken :D
Just hope DOS installs OK, and I'll see what I can do with those drivers mentioned earlier. Thanks all!

---

### Post by Bungo Pony on 2008-03-24
Great stuff! Hope your install goes well and getting all the drivers you need working. That's probably the most difficult part.

---

### Post by Wobedraggled on 2008-03-24
Commodore made filing cabinets too, I would kill for one of those.

Cool stuff.

---

