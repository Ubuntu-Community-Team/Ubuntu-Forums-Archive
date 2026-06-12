---
title: "Errors on startup"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by the_wordsmith on 2008-07-28
I loaded up Ubuntu 8.04LTS LiveCD (desktop edition onto a computer I've just finished building from scrapped parts, and I got as far as (I guess) the Ubuntu BIOS screen (4-5 options displayed vertically, as far as memory serves the commands included stuff like "run on system as it is" "install Ubuntu on Hard Drive" etc).

I clicked through and it is going through the CD at the moment, stating all the problems. As the same lines keep occuring, I'm assuming it's because one thing is wrong.

example of errors coming up:

[3587.360352] buffer I/O error on device sr0, logical block 57661
[3758.523903] SQUASHFS error: sb_breadfailed reading block 0x1b9fe
[3818.496260] SQUASHFS error: unable to read page, block 6e7ad5f, size 4b82
[3660.001394] SQUASHFS error: unable to read fragment cache block [6e7ad5f]

and it repeats the cycle of 

Buffer error
Buffer error
Buffer error
SQUASHFS error sb_bread
SQUASHFS error fragment cache
SQUASHFS error unable to read page
SQUASHFS error sb_bread
SQUASHFS error fragment cache
SQUASHFS error unable to read page
Buffer error etc.

Any ideas as to what I've done? And also, anyone know if I'm ok to turn it off and on again to restart the launcher? Many thanks

---

### Post by wolfen69 on 2008-07-28
> **the_wordsmith said:**
>  anyone know if I'm ok to turn it off and on again to restart the launcher? Many thanks

go ahead and kill it. what could happen?

---

### Post by t0p on 2008-07-28
Sounds to me like your CD is bad... maybe you need to burn another one?

---

### Post by stevoo on 2008-07-28
Most probably the cd is bad. Bad copy bad download. 
I reccon trush that and re-download one and burn again as slow speed.

---

### Post by the_wordsmith on 2008-07-28
Can anyone recommend a link to download from? I got my version/installation advice from  [here:]("http://www.ubuntu.com/getubuntu/download")

and when you click download it leads you to a load of links about how to install it. If anyone can provide a reliable mirror?

edit: I ran the "check for errors" option, it turns up 1 error really early on (only one bar orange).

---

### Post by t0p on 2008-07-28
> **the_wordsmith said:**
> Can anyone recommend a link to download from? I got my version/installation advice from  [here:]("http://www.ubuntu.com/getubuntu/download")

and when you click download it leads you to a load of links about how to install it. If anyone can provide a reliable mirror?

That link is the one I would point you toward.  It should be fine to use. Just cos you got a bad download off it once, doesn't mean it's a bad link.  Bad downloads/burns happen.

---

### Post by the_wordsmith on 2008-07-29
I've re-downloaded, and as per the instructions in my last link, I'm using Infra-Recorder to burn the image onto a blank CD-RW (700mb, 80 mins as is recommended). I went through the steps on the website, and clicked Burn Image. Both times (last time when it failed and now) it came up with the following errors [IMG]http://i6.photobucket.com/albums/y237/chimpyacee/BurnerImage.jpg[/IMG]

(that's a screeny of the problem, I don't know if the forum accepts pics so [link]("http://i6.photobucket.com/albums/y237/chimpyacee/BurnerImage.jpg")

I know this isn't technically Ubuntu, but hopefully there's a guru out there somewhere?

---

### Post by the_wordsmith on 2008-07-30
*bump*

---

### Post by scorp123 on 2008-07-30
> **the_wordsmith said:**
>  I'm using Infra-Recorder to burn the image onto a blank CD-RW (700mb, 80 mins as is recommended). Try a CD-R disk and burn it at 4x speed max. CD-RW disks get broken very fast, e.g. those "survives 1000 rewrites" which they claim in the advertisements are achieved waaaaay faster than you think. The other thing is this: CD-RW disks have a fainter reflection than CD-R disks. This has to do with the layers and materials CD-RW disks are made of. So it could be --in a bizarre way-- that your CD-burner can burn the CD-RW disk but then fails to read it. I have seen this happen before. It simply boils down to the fact that not all CD-R and CD-RW disks will work in every CD-burner drive regardless what vendors etc. claim.

As I said ... try with a 80 min. / 700 MB CD-R disk from a "good" brand (e.g. Emtec, Imation, TDK, Sony, Samsung, ...). If that fails too .... can't you ask a friend to burn the CD for you?

---

### Post by the_wordsmith on 2008-07-31
I've tried it with several Imitation 700mb 80min, loads of TDK CD-R80's (700/80 again) and a few Samsung CD-R's, all set to x4 to ensure they burn properly... no dice. Can anyone suggest an alternative ISO burner?

---

### Post by nbayiha on 2008-07-31
Alternative ISO burner Brasero you got it , give it a try and wont be disappointed .

---

### Post by eightmillion on 2008-07-31
I've always used [CDburnerxp]("http://cdburnerxp.se/"). It's free and easy to use.

---

### Post by scorp123 on 2008-07-31
> **nbayiha said:**
> Alternative ISO burner Brasero you got it , give it a try and wont be disappointed . There is a version of Brasero for Windows?? 

Or else ... chances are you did not understand that OP is still on Windows and trying to burn an Ubuntu CD .... ;)

---

### Post by nbayiha on 2008-07-31
I didnt read it well.
use Cdburner as @eightmillion said , i used it's free and good .

---

### Post by Ptero-4 on 2008-07-31
It could also be that you got a picky drive (The 500MHz iBook that I used to have, came with a POS CD burner drive that gave me no end of problems to get good CD's out of iso images.

---

