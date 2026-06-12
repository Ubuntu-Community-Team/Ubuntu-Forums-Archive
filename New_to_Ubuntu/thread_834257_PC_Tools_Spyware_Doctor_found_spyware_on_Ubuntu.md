---
title: "PC Tools Spyware Doctor found spyware on Ubuntu ?"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by JBA2337 on 2008-06-19
According to everything that I have read and heard, spyware and adware is not a problem with Ubuntu.

I installed a program on my PC so that when I am running Windows XP (on an NTFS partition), I can also see and work with files that are in my Ubuntu installation (on an ext3 partition). A few days ago, I ran several spyware/adware scanners on my Windows XP installation, as I customarily do about once a week. While the scanners were running, I noticed that they were also scanning my Linux Ubuntu installation. 

I ran several spyware/adware scanners, and here are the results:

Spybot....no infections found
Windows Defender...no infections found 
AVG Anti-Spyware...no infections found
Norton Security Scan...no infections found

PC Tools Spyware Doctor
1,182 infections found on my computer!
All of the "infections" except 4 were in my Ubuntu installation.

Here are a few examples of what Spyware Doctor is calling an infection in my Ubuntu installation:

/tmp/orbit-jim/linc-lc01-0499fa135
/tmp/tracker-jim.6337/cache.db
/usr/src/linux-headers-2.6.24-16-generic/scripts/basic/fixdep.c
/usr/src/linux-headers-2.6.24-16-include/asm-mips/ip32/crime.h
/usr/src/linux-headers-2.6.24-16-generic/include/asm.sh
/usr/src/linux-headers-2.6.24-16-generic/scripts/kconfig/expr.h

Spyware Doctor listed 16 infected files in the /tmp folder, and 1162 files in the /usr folder.

Are these files really spyware or adware?
Or is this just a quirk of the Spyware Doctor program?


JBA2337

---

### Post by Nepherte on 2008-06-19
I'd seriously question the results of PC Tools Spyware Doctor if the others didn't find a single infection.

---

### Post by Tomatz on 2008-06-19
> **JBA2337 said:**
> According to everything that I have read and heard, spyware and adware is not a problem with Ubuntu.

I installed a program on my PC so that when I am running Windows XP (on an NTFS partition), I can also see and work with files that are in my Ubuntu installation (on an ext3 partition). A few days ago, I ran several spyware/adware scanners on my Windows XP installation, as I customarily do about once a week. While the scanners were running, I noticed that they were also scanning my Linux Ubuntu installation. 

I ran several spyware/adware scanners, and here are the results:

Spybot....no infections found
Windows Defender...no infections found 
AVG Anti-Spyware...no infections found
Norton Security Scan...no infections found

PC Tools Spyware Doctor
1,182 infections found on my computer!
All of the "infections" except 4 were in my Ubuntu installation.

Here are a few examples of what Spyware Doctor is calling an infection in my Ubuntu installation:

/tmp/orbit-jim/linc-lc01-0499fa135
/tmp/tracker-jim.6337/cache.db
/usr/src/linux-headers-2.6.24-16-generic/scripts/basic/fixdep.c
/usr/src/linux-headers-2.6.24-16-include/asm-mips/ip32/crime.h
/usr/src/linux-headers-2.6.24-16-generic/include/asm.sh
/usr/src/linux-headers-2.6.24-16-generic/scripts/kconfig/expr.h

Spyware Doctor listed 16 infected files in the /tmp folder, and 1162 files in the /usr folder.

Are these files really spyware or adware?
Or is this just a quirk of the Spyware Doctor program?


JBA2337

Well fixdep.c, crime.h, asm.sh and expr.h are all system components. I just googled them to double check.


Its probably the heuristics in the anti-spyware picking up something potentially suspicious as you have to remember that it is designed to run in a windows only environment.You could email them and see if they can fix the bug in future definition updates.

;)

---

### Post by Dan_Dranath999 on 2008-06-19
i don't think those files could be spyware. Do a web search with some of the names, and you probably get their function within the system.

---

### Post by Pjotr123 on 2008-06-19
You can safely ignore those false positives from PC Tools. 

Furthermore, you don't need that sad, horrible application in Linux. Nor any other of it's kind. Read this:
[http://ubuntutip.googlepages.com/security](http://ubuntutip.googlepages.com/security)

---

### Post by jrusso2 on 2008-06-19
You can't run a scanner for Windows on Linux files and expect it to know what the files are it was not designed to be used on Linux.

Spyware Doctor is fairly reliable when run on Windows, but Linux?

---

### Post by fiddledd on 2008-06-19
I've just looked on PCtools website and can find no mention of Linux anywhere. So I'd guess that it doesn't scan linux files at all, it assumes they are windows files, which they are not. So it seems the other tools you used are accurate and this one messed up.
If there is such a thing as a Spyware checker for linux and that tells you you got spyware then maybe start to worry.

---

### Post by fatality_uk on 2008-06-19
I like it. Reports .h files as viruses :s
You gotta love AV vendors.

Ignore this. AV apps, unless stated will only match against profiles for Windows viruses. While it is technically possible to run Windows viruses in WINE for instance, they do little or no harm

---

### Post by jaw99 on 2008-11-10
> **JBA2337 said:**
> According to everything that I have read and heard, spyware and adware is not a problem with Ubuntu.

I installed a program on my PC so that when I am running Windows XP (on an NTFS partition), I can also see and work with files that are in my Ubuntu installation (on an ext3 partition). A few days ago, I ran several spyware/adware scanners on my Windows XP installation, as I customarily do about once a week. While the scanners were running, I noticed that they were also scanning my Linux Ubuntu installation. 

I ran several spyware/adware scanners, and here are the results:

Spybot....no infections found
Windows Defender...no infections found 
AVG Anti-Spyware...no infections found
Norton Security Scan...no infections found

PC Tools Spyware Doctor
1,182 infections found on my computer!
All of the "infections" except 4 were in my Ubuntu installation.

Here are a few examples of what Spyware Doctor is calling an infection in my Ubuntu installation:

/tmp/orbit-jim/linc-lc01-0499fa135
/tmp/tracker-jim.6337/cache.db
/usr/src/linux-headers-2.6.24-16-generic/scripts/basic/fixdep.c
/usr/src/linux-headers-2.6.24-16-include/asm-mips/ip32/crime.h
/usr/src/linux-headers-2.6.24-16-generic/include/asm.sh
/usr/src/linux-headers-2.6.24-16-generic/scripts/kconfig/expr.h

Spyware Doctor listed 16 infected files in the /tmp folder, and 1162 files in the /usr folder.

Are these files really spyware or adware?
Or is this just a quirk of the Spyware Doctor program?


JBA2337

i did it but not on linux but it found trojen av
i found it crazy spybot never found anything.:confused::confused:

---

### Post by Keen101 on 2008-11-10
well, you either have a fake virus scanner. Or, it just detected potentially suspicious code.


...try Clamwin ... it's an open source virus scanner.

and... clamav is a linux scanner based on the clamwin code, but can track down windows viruses, so you don''t become a carrier. Viruses really can't afect you in ubuntu, but you really don't want to accidentally pass on viruses to your windows friends.

---

### Post by Tomatz on 2008-11-10
Copy and paste the code in the link below in a text file and name it "fixdep.c" (without quotes).

[http://www.gelato.unsw.edu.au/lxr/source/scripts/basic/fixdep.c](http://www.gelato.unsw.edu.au/lxr/source/scripts/basic/fixdep.c)

Then scan it with your spyware scanner, i bet it will pick it up as spyware.


If you are still worried, post the contents of the aforementioned files (encrypted) in the programing forums so someone can take a closer look. Just to put your mind at ease ;)

I'm sure its just that crappy antispyware app. If spybot didn't pick it up you should have no worries.

;)

---

### Post by Kellemora on 2008-11-10
Hi Gang

I have to join in the phun here!

I had three files
One was a photograph I took myself
Second was a message I wrote in simple Doze Notepad, plain text.
Third was sound file used by a game.

Almost all of the free spyware and virus programs picked these three files up every single time I ran the programs, even though I had them marked IGNORE.
Took me the longest time to get them to quit doing that.
The Photograph I converted from jpg to a tif file, so it was no longer picked up anymore.
The textfile I just renamed, I think it was named VikingII.txt I changed it to NorseWarrior.txt, so it was no longer picked up anymore.
There wasn't a whole lot I could do with the sound file, since it was part of a game that the program looked for, so I couldn't rename it or it wouldn't work.  But, I made a copy of it, deleted the original, then copied the copy back to the game folder.  Voila, no spyware detected it anymore.

Then, just to have more phun, I made a bunch of small text files and gave them names of viruses, trojans, etc.  The spyware nailed every single one of them based solely on their file names.
If any of you are familiar with the screensaver like executable named Yiggart.exe, every spyware or virus program ever written picks that simple little program up as a virus, no matter WHAT you name it.

TTUL
Gary

---

