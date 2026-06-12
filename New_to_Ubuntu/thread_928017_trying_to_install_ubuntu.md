---
title: "trying to install ubuntu"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by klambert on 2008-09-23
i put the disk in my computer (which is a home built computer and that may be my problem) but anyway when i tell it to boot from the disk...it starts itself and like suddenly after it loads the kernel it starts saying [some numbers. some more numbers] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
cmd a0/00:00:00:24:00/00:00:00:00:00/a0 tag 0 pio 36 in
status: { DRDY }

now i know like some c++ program and very little java, so i'm not by any means good with programming or anything and i have no frieking clue what all this means...those numbers in the [] just keep getting larger and larger and the error is always the same...i dont know what to do, but i really really really want to put linux on my computer and get away from windows if anyone knows how to help me plzzzz help.

---

### Post by Tatty on 2008-09-23
A few questions:

1. What version of Ubuntu are you trying to install?

2. What is the exact error message you are getting?  It can be helpful to have the exact error message so it can be googled.

3.  Did you check the integrity of your disk?  Boot to the first menu then select "check integrity".

EDIT:
4. What are the specs of your machine?

---

### Post by Kain000 on 2008-09-23
Whats your system memory look like?    And is linux in dual boot or is this the first os your installing on your system?       

Does it ever get to the ubuntu menu where you can use memtest?  or as soon as your BIOS hands it over to the Ubuntu cd it goes downhill?

The first thing I would try is to (if you have access to another computer) re-download the Ubuntu kernal and install cd from 
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
and (again if you have another computer) while you are at it download and burn the ISO disk image of memtest 3.3 from 
[http://www.memtest86.com/](http://www.memtest86.com/)
and i'd try 

1: try again with the new cd and see if you get the same problem.
           ---if you do then try booting from the memtest cd and runing a test on your RAM to see if there is fault in your memory.  

hope it helps, 
let me know how it goes.
-sean

---

### Post by klambert on 2008-09-23
ok the version is the newest stable one (i cant find the actual version anywhere, i dont know, i installed t successfully on my roommates last top last week though.)
and man what i wrote is what i get it just keeps repeating it over and over. i've tryed to google it but i cant find anything on what its doing.
and when i check the integrity of the machine it starts doing the same thing, same message and everything.

my specs are an amd athlon 1700
vid card is radeon 8xx i cant rembember for sure
1 gig ram (dont ask brand i dont know)
and asus mother board
i'm sorry i cant provide a lot of info, i built this computer 5 1/2 years ago and cant remember all the detailed specs.

---

### Post by NewJack on 2008-09-23
It may be a problem with your downloaded Ubuntu image.  

The first thing you should do is check the Hash value of the file you downloaded against the official Ubuntu Hash list.

Found here: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Just find your version and compare. 

Anytime you download a disc image, you should check the hash value against the distributor's hash list.

Hope that helped.

Joe

---

### Post by klambert on 2008-09-23
here's my thing though, i used this exact cd, to put ubuntu on my roommates laptop so it should be fine as far as that goes

---

### Post by Tatty on 2008-09-23
Even though you used this CD to install to another PC recetly, it may be worth following NewJack's above post to eliminate a bad CD as a possibility - cds can pick up scratches, etc.

If it is not the disk then it seems to be having a problem with your hard disk, I have been googling and I have found a few similar issues, but none of them with booting.

Do you have any other OS's on the computer?  Do they function correctly?

---

### Post by mrtomcef on 2008-09-23
I would download and try another linux live cd ([Knoppix]("http://knopper.net/knoppix-mirrors/index-en.html")) and see if your computer still gives you the funky readout.

---

### Post by klambert on 2008-09-23
ok so here is what i have found, completely different subject and i may need to go somewhere else to get this fixed...but at one point a while back i tryed to dual boot linux with my xp, and i must have done something because now i cannot even boot xp up without both hard disks and one set as master and the other as slave (i tryed putting one os on one disk and the other on another disk, but that apparently messed somehting up) and now i cannot access my bios or anything like that, so i may have some reinstalling to do or something...thanks for the timely responses guys and all the help

---

### Post by Tatty on 2008-09-23
> **klambert said:**
> ok so here is what i have found, completely different subject and i may need to go somewhere else to get this fixed...but at one point a while back i tryed to dual boot linux with my xp, and i must have done something because now i cannot even boot xp up without both hard disks and one set as master and the other as slave (i tryed putting one os on one disk and the other on another disk, but that apparently messed somehting up) and now i cannot access my bios or anything like that, so i may have some reinstalling to do or something...thanks for the timely responses guys and all the help

You cannot acces your bios?  That sounds like a motherboard issue.

Unplug both your hard drives then try accessing your bios.  If you still cant get to the bios then the problem is almost certainly your motherboard.

---

### Post by klambert on 2008-09-23
yup thats what ive been trying to do, i cant access the bios with everything unplugged...something got messed up when i was messing around with all that so thats what im working on...i just dont know what i really need to do to get it back accessible, ive never messed with this stuff...im more of a hardware kinda guy...not too software oriented

---

