---
title: "HowTo: bring dead dvd/cr-rw back to life"
date: 2010-07-15
forum: Outdated Tutorials &amp; Tips
---

### Post by Hugo Alvarado on 2010-07-15
I had a brand new dvd-rw, and while burning some stuff on it the burn process failed. After that the dvd was unusable. It would not mount. XP did not see it. Ubuntu did not see it. It was gone. 5 months later I found how to fix it! (here: [http://txt.binnyva.com/2008/01/linux-command-to-erase-rewritable-cd/](http://txt.binnyva.com/2008/01/linux-command-to-erase-rewritable-cd/))

This is what I did:

1. unmount cd/dvd (mine did not mount so this was not needed) 
2. list the available drives with:
	cdrecord -scanbus

this shows something like:
scsibus0:
0,0,0 0) ‘HL-DT-ST’ ‘RW/DVD GCC-4481B’ ‘1.05&#8242; Removable CD-ROM
0,1,0 1) ‘TSSTcorp’ ‘CDDVDW SH-S202J ‘ ‘SB01&#8242; Removable CD-ROM
0,2,0 2) *

note the first 3 numbers (0,0,0 for the first dvd drive)

3. begin erasing:
cdrecord dev=0,0,0 blank=all
OR
cdrecord dev=0,0,0 blank=fast

4. wait...and wait.. 

After this I was able to mount the dvd again, I did a test burn on it and it was all good.

---

