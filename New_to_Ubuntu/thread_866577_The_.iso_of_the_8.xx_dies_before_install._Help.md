---
title: "The .iso of the 8.xx dies before install. Help"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by whrd on 2008-07-21
I made about 15 CDs, DVDs of various drives off of various machines.
I've downloaded the .iso off of the site, off of various mirrors. I've used: Win 2k, OpenSolaris, Mac OSX, and SUSE. Each time the .iso downloads, each time the install starts, then goes to a buffer overflow error fd0, #0.

I'm given to believe that I'm supposed to download the image which is an iso, but then create an iso in linux.

I actually went out and bought the distro (7.04) in The Ubuntu Book, Prentice Hall, and that crashed the exact same way on 3 different machines. 

What am I doing wrong?

Thanks, 

Will Davis.

---

### Post by Mister.Vash on 2008-07-22
The basic message that you listed - it was also mentioned in this thread:
[http://ubuntuforums.org/archive/index.php/t-530739.html](http://ubuntuforums.org/archive/index.php/t-530739.html)

What was said was 'system complained about "buffer overflow on device fd0". in BIOS, had to set "drive A" to "none."'

Can you try disabling your floppy drive in the bios prior to doing an install?

---

### Post by whrd on 2008-07-22
Well, after I got up off the floor from smacking myself in the forehead, I disabled fd0 (oh, let's just call that the floppy drive, since 1982),  and the install went smoothly. 

I have video resolution questions, of course, as to why my NEC P1150 is only correct, proportionally, at 1024x768. and only goes to 60hz, but I'll keep hunting the forum for that. 

Thanks. 

==Will

ps
Your emotocon artist is crying for help.

---

