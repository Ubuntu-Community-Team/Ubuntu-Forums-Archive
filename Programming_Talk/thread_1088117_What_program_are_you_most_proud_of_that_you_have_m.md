---
title: "What program are you most proud of that you have made?"
date: 2009-03-05
forum: Programming Talk
---

### Post by jimi_hendrix on 2009-03-05
title says it all

mine is a 2d mario clone (i even ripped the sprites) that i made with c# and XNA...it allowed for you to make your own maps by editing a text file

---

### Post by namegame on 2009-03-05
So far,

A very rudimentary Web Crawler/Spider.

Essentially, given enough time and storage, you could download your own personal copy of the internet. :P

---

### Post by vandorjw on 2009-03-05
Lol, I hope someone tries to download the internet :)

So far my most impressive program is one that guides a robot through a maze of obstacles and picks up eggs along the way. :)

---

### Post by jimi_hendrix on 2009-03-05
> **cc7gir said:**
> Lol, I hope someone tries to download the internet :)


google has it 3 times over

---

### Post by kavon89 on 2009-03-05
My current project, [Cosis]("http://cosis.googlecode.com").

The cool features aren't there yet (system tray, backups, idle timeout) but they're simple to implement, I just need a good window of free time.

If anyone wants to test my program/report bugs (especially just some GUI irregularities or comments!) I would appreciate it.

---

### Post by slavik on 2009-03-05
autoit3 + lamp

every time at my old job we re-ghosted computers (updates, new licensing, etc.) we used autoit3 to run through the program's first run wizards. the problem was managing the miriad of different autoit scripts for each different area (since each area of the lab would have different set of software).

idea was simple: MAC address doesn't change. using this, I stored the system name, MAC address and some other info that would tell this program where the system was, it would apply the proper settings (change computer name, set up auto login using tweakui, etc). then there was a second step which had the combined functionality of every area and would download the config file from the lamp server (it would tell things to the lamp server via GET) and the php would spit out the text file, then step2 would run it's course ...

it might still be in use.

---

### Post by loganwm on 2009-03-05
I wrote a Chip8 emulator, and then I decided that I could use the same principles to write my own emulator for a fictional PC.

I'm in the process of creating a very rudimentary fictional 16-bit PC with an assembler, disassembler, and its own unique set of opcodes and io devices.

All I have working is basic graphics emulation and register arithmetic, but its really neat and it gives you a really cool understanding of a PC.

I'm hoping to complete it with a home-made BIOS, a rudimentary Operating System, and some simple applications created in it's own assembly language.

---

### Post by Gordon Bennett on 2009-03-06
I get the same feeling about all that I write - although if I had to pick, it would have to be the scribbles-on-back-of-the-envelope working out of a surface generator in PowerPC assembler that I did some time ago to prove how well a RISC-based algorithm can work in certain situations:

[Biquadratic surface patch generator]("http://mil-tdd-41p.net/archives/AsmQuadBezPatch/PPCAsmInterpolateBezPatch_U.s")

I was particularly proud of the 12-instruction inner loop (I'm a bit of a stickler for efficiency :P).

(BTW all the source code on my site there is public domain)


However, that was a while ago!  Recently I am very keen on two apps I have been coding within Linux - my first time writing serious code on the platform too - and I get a warm fuzzy feeling every time I boot up Ubuntu ;)  A graphics processing app and a server daemon - they are currently the ones I am most proud of in overall design and code - when they are done :)

---

### Post by munishvit on 2009-03-06
Two year ago I wrote a program in C that could solve all 'good' SUDOKU puzzles. Here, by 'good' I mean that the one in which you don't have to make guess. For the bad ones, it gives partial output and shows all the possibilities for the rest cells. \\:D/

---

### Post by Tony Flury on 2009-03-06
A Program entirely written in Python and uses pyGTK to provide a GUI to the PyFlickrAPI, includes thumbnails view of the images, automatically added Tags and Groups (including abiltity to add tags based on Folder names), change titles, descriptions, tags and groups on individual pictures or on many pictures, set default permissions, defaults folders etc. All preferences stored per user account, so that you can maintain multiple flickr accounts easily. In theory the design is such that the GUI is a discrete class with a few simple methods and signals - which means i can easily develop a command line interface, when i get round to it.

---

### Post by stevescripts on 2009-03-06
Software to control/monitor production line special machinery ...

---

### Post by namegame on 2009-03-06
Oh I forgot. I also have a few raytracers laying around. Those were a pain in the neck.

For those of you that don't know what raytracing is: [http://en.wikipedia.org/wiki/Ray_tracing_(graphics](http://en.wikipedia.org/wiki/Ray_tracing_(graphics))

---

### Post by imdano on 2009-03-06
[wicd](http://wicd.net), though I didn't do it by myself.

---

### Post by nvteighen on 2009-03-06
Not sure. Maybe my unpublished Restore utility written in Perl. At least, it's the only functioning program I have that makes something useful.

But, for theorical enjoyment, no doubt: FreeTruco. See my sig.

---

### Post by CptPicard on 2009-03-06
No contest -- my sports betting analysis toolkit, which I have mentioned here sometimes. As far as I know, nobody else is capable of providing a mathematically rigorous treatment -- in the kelly-betting sense -- of the games it is is used for, and *to be actually capable of computing it*. In the past 5 years, some €30 million have gone through it, and the bankroll is just steadily increasing...

---

### Post by DocForbin on 2009-03-06
I developed the internet. Seems to have caught on.

---

### Post by Cracauer on 2009-03-06
I wrote an OCR package in a /bin/sh (not bash) script. Using ImageMagick's "convert". You could teach it new fonts etc. quickly. Does hard pixel fonts (not scans) only.

---

### Post by HotCupOfJava on 2009-03-06
Wrote a program to read a BrainForest PDB backup file from my palm into plain text in outline form. It even keeps track of which items are "checked" correctly. I use it to email lists of things back to the business I work for while I'm on the road. I never paid for the desktop companion software for BrainForest (it runs on Windows, anyway), and the PDB structure is proprietary. I've been patting myself on the back for cracking it. I even had to use some bitwise operators to get the info correctly from the file (It uses unsigned integers, which Java doesn't support). I know it isn't much, but I'm hardly a "professional" programmer, so I feel pretty good about it.

---

### Post by Greyed on 2009-03-07
Wrote a simple utility for my previous job which tied together several different source text files and provided a decent way of looking up information or searching through wildly different sources for information.  In and of itself not too special.

What makes me proud was that I ensured that someone was able to maintain the code.  Introduced him to Python (he had a background w/c++ in college) and after leaving the company having him email me one day with the newest version he was working on.  He had dropped the console-based interface for a tabbed GUI interface w/far more efficient filtering on searches and other bells and whistles I never got around to implementing.

---

### Post by slavik on 2009-03-07
> **CptPicard said:**
> No contest -- my sports betting analysis toolkit, which I have mentioned here sometimes. As far as I know, nobody else is capable of providing a mathematically rigorous treatment -- in the kelly-betting sense -- of the games it is is used for, and *to be actually capable of computing it*. In the past 5 years, some €30 million have gone through it, and the bankroll is just steadily increasing...
and I still haven't seen a penny from it :(

---

### Post by PythonPower on 2009-03-07
Various algorithms for [Project Euler]("http://projecteuler.net/") have been my highlights; I would rate them higher than [my forum]("http://silicon.appspot.com/") although that is coming along nicely. I'm also in the middle of developing a 2D platform game (with some twists) and a 3D game-engine.

---

