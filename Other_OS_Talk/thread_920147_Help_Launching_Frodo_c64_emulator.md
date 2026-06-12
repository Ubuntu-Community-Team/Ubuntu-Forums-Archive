---
title: "Help Launching Frodo c64 emulator"
date: 2008-09-15
forum: Other OS Talk
---

### Post by Laxton14 on 2008-09-15
I just installed DeliLinux.. a light linux distro on to a very old laptop of mine.. it is command-line only (the GUI will not work on it for some reason) and i wanna know how to use the c64 frodo emulator.. i've un zipped and untarred it allready and now i just need to know how to launch the game, thanks in advance

---

### Post by zmjjmz on 2008-09-15
Do you need to compile something?
Or is it a binary?

---

### Post by Laxton14 on 2008-09-15
im not really sure, im new to linux.. but i think that it has something to do with a file called TkGui.tcl or something.. thats the only file in the emulator that isnt just a directory or anything.. (sorry that im not much help).. but im not sure what kind of information i need to give

---

### Post by FranMichaels on 2008-09-15
What are the laptop specs (at least the chip, pentium class? pentium II?)

Have you tried another release? Is there a package manager? Installing things manually should be a choice in my opinion... If Ubuntu didn't work on your laptop, have you tried xubuntu? 

What format was what you unzipped and untarred? tar.gz, is there a binary or source, or an install? Does typing ./configure in the extracted directory cause something to happen? Does typing ./frodo work?

Are you working purely from a terminal? No X or anything, I don't think tcltk will work without X...

Lastly, I'd recommend [vice]("http://www.viceteam.org/")

Awesome c64 emulator (well other commodore systems too, but 64 is my fave!)

Also, if you like the c64 music, [audacious]("http://audacious-media-player.org/index.php?title=Main_Page") handles it nicely.

To reiterate, I recommend you get a simple distribution working on that laptop. Don't get me wrong, I love working from commandline and tweaking scripts and such. But, with a graphical environment and package management ala Add/Remove your Linux experience will be smooth as silk, and you can work from terminal (or terminals) seamlessly.

From what you've described, it's like a stone-age broken linux install, you will miss out on many modern apps and perks, and it may even be frustrating, dealing with issues that have long been solved...

EDIT: One other thing, if this machine is really old, damn small linux may be a good choice
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

I've used it years ago, it can use apt-get, making installs trivial. It doesn't have all the bells and whistles as a full fledged distros. But depending on your hardware and bandwidth, 50mb is a very decent size for an OS ;)

---

### Post by Laxton14 on 2008-09-15
its... extremely old... Pentium.. 166mhz...32mb ram..2gig hard drive.. floppy and cd drive... thats really all i know about it i cant get the X running.. when i run Startx... it comes up.. but its really buggy.. the screen is orange and there a few boxes up that just say "bsh 2.1" (or something, not exactly sure).. ive tried reconfiguring the X by choosing various drivers and what not (vesa and vga to name a few) but to no avail. I have tried many many distro's on this computer but i fear it is to old to run any of them, i dont see how though.. seeing as it ran windows 95. I will give vice a shot (basically all this laptop is for is to run an emulator). thanks again for the responses.

---

### Post by Bungo Pony on 2008-09-15
If you want a good c64 emulator to run on an old machine like that, you're probably best off installing DOS and using [CCS64]("http://www.computerbrains.com/ccs64/"). I run it on my DOS 486 laptop and it runs great.

Linux is great in some cases, but for older hardware (166 MHz and lower), you're almost better off using an older version of Windows or DOS.

---

