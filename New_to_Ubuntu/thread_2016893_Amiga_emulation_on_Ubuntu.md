---
title: "Amiga emulation on Ubuntu"
date: 2012-07-04
forum: New to Ubuntu
---

### Post by GeordieJedi on 2012-07-04
Hi there, I hope you're all well.

(Hope this is the right section, if not could you move it please).

A bit of background -
I currently dual boot between Win 7 and Ubuntu 11.04. I also own Amiga Forever.
I really want to get back to using my Amiga via Linux emulation, some gaming (esp UFO Enemy Unknown !)

I'm using UAE under Linux (and have the ROMs from Amiga Forever).
The UAE site seems a little bit bereft of help files or manuals.

(I know all the roms are on and I've copied them accross to my hdd.
I assumed that I'd also have Workbench OS on there too. But now I'm not certain)

Also, I seem to get a workbench window appear (but it's the ancient 1.3 version)
I keep requesting the amiga-os-310.rom

Like I said, I really want to play UFO. I've created my initial set up (A1200 plus extra ram etc).
Then when I start UAE I get the std Amiga floppy animation, (As I should).

Do I need to set up a virtual Amiga HDD? (How ?)
Do I need to format part of my Linux HDD partition to Amiga FS?
(Does it need to be less than 4GB ?)


I seem to be getting a tiny bit further each time.....



Thanks in advance for any help or advice.

---

### Post by rai4shu2 on 2012-07-04
I assume you've looked at AROS.

[http://aros.sourceforge.net/](http://aros.sourceforge.net/)

---

### Post by FrodeSolheim on 2012-09-02
I recommend you try FS-UAE. It is newer than the other UAE releases for Linux - with more accurate emulation (updated emulation code from WinUAE), works generally better on Linux, has better documentation and is actively maintained.

[http://fengestad.no/wp/fs-uae](http://fengestad.no/wp/fs-uae)

If you want to install UFO: Enemy Unknown to HD and play from there, you can:
* Configure a directory on your Linux box to be the HD for the Amiga (easy to set up, no formatting, and the files are also available on Linux, you can copy/backup individual files etc).
* Boot with Workbench installation floppies and install WB to this "HD".
* Lastly, install the game.

I can help with further instructions if you need help configuration FS-UAE.

(Disclaimer: I'm the author of FS-UAE)

---

### Post by s1baker on 2012-09-03
just curious....

I have some old Amiga games on 3-1/2" floppies that are over 25 years old.
Is it actually possible to run an Amiga emulator on Ubuntu whereby one could load the games from the floppy drive and actually play them?
I think this was an Amiga 1000.

---

### Post by Jakin on 2012-09-03
> **s1baker said:**
> just curious....

I have some old Amiga games on 3-1/2" floppies that are over 25 years old.
Is it actually possible to run an Amiga emulator on Ubuntu whereby one could load the games from the floppy drive and actually play them?
I think this was an Amiga 1000.

Nah, they are incompatible with PC floppy drives unfortunately, though you may be able to modify a drive- then i think it wouldn't read anything else. (in anycase probably still wouldn't allow the PC hardware to read it)

---

### Post by s1baker on 2012-09-03
:(
I was hoping that if there was an Amiga emulator, it would somehow be able to access the floppy drive in an "Amiga" way to do that.
Although, I think most of these games are so old, they might could be downloaded off the internet.

---

### Post by petran79 on 2012-09-25
some games have compatibility issues that it would be better to play then on  a real Amiga instead

Eg the game Mike the Magic Dragon, though it is publicly available, it has some copy protection issues since it is from Kingsoft. While the cracked version runs on an Amiga, the game freezes in the emulator after completing the first stage.

---

### Post by Swagman on 2012-09-25
I'd love to get "True-Brilliance" running 100% within Linux. <--- That means the anim brushes too !!

My fave all time proggie (Final Writer 2nd, Photgenics 3rd)

---

### Post by rai4shu2 on 2012-09-25
> **petran79 said:**
> some games have compatibility issues that it would be better to play then on  a real Amiga instead

Eg the game Mike the Magic Dragon, though it is publicly available, it has some copy protection issues since it is from Kingsoft. While the cracked version runs on an Amiga, the game freezes in the emulator after completing the first stage.

LOL

Crackers were lazy. Amiga copy protection is notorious for being some of the most amibtious designs for copy protection (see the Amiga version of Dragon's Lair if you want one of the most amibitious).

---

### Post by khelben1979 on 2012-09-25
> **s1baker said:**
> :(
I was hoping that if there was an Amiga emulator, it would somehow be able to access the floppy drive in an "Amiga" way to do that.
Although, I think most of these games are so old, they might could be downloaded off the internet.

That **is** possible. :) 

[Check this out!]("http://en.wikipedia.org/wiki/Individual_Computers_Catweasel")

---

### Post by Bashing-om on 2012-09-25
My first love also was an Amiga // I still have it and tons of software as well as the "white books" . It has been retired as of ubuntu (a bunch of years ago) . However, I sure learned a lot with that machine!

[INDENT]fond memories <==BDQ

[/INDENT]

---

### Post by aka-John99 on 2012-09-25
> **khelben1979 said:**
> That **is** possible. :) 

[Check this out!]("http://en.wikipedia.org/wiki/Individual_Computers_Catweasel")

This may have some relavance to your problem.
See for instance [http://en.wikipedia.org/wiki/Floppy_disk_variants#Commodore_Amiga](http://en.wikipedia.org/wiki/Floppy_disk_variants#Commodore_Amiga) 

I used PCs with DOS & Xenix & also an Atari in the days of floppies. I found it was quite possible to make floppies that could be cross compatible. Xenix could format floppies a PC could use. PC & Atari software was availible that allowed the number of sectors etc to be changed and if necessary some of the identification bits in the boot sector could be changed.

Whilst I was not attempting to beat copy protection, I had no problem transferring files between the three systems using floppy disks. I do not remember the exact details now but it seemed fairly easy at the time.  The item I linked to above may suggest there are methods of transfering data to Amiga emulators.

I still have some Atari floppies, and a pc with a floppy drive, I sometimes think I may try an Atari emulator before throwing out the floppies and FDD.

---

### Post by mips on 2013-04-24
If you wanna do Amiga emulation look at FS-UAE, it rocks! [http://fengestad.no/fs-uae/](http://fengestad.no/fs-uae/)
It also has a excellent gui called  FS-UAE Launcher which lets you configure everything with the click of the mouse, have not touched a config file.

Been playing with it for the last couple of days, Just tested UFOEU and it works right away.

---

### Post by Bashing-om on 2013-04-24
Thanks for the info mips, real nice to know !

---

