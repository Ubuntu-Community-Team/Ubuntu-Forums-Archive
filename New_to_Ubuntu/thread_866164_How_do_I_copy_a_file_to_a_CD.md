---
title: "How do I copy a file to a CD?"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by tc101 on 2008-07-21
How do I copy a file to a CD?  It seems like I used to be able to do this.  Either something has changed or I have forgotten something.  

I put a CD in the CD read write drive, which I call drive 1.  I copy a file to it.  The file seems to be there.  However, when I move the CD to drive 2 it is blank.  I have checked with other CDs and there is nothing wrong with drive 2.  When I move the CD back to the original drive a message box opens and says "You have inserted a blank CD.  What would you like to do?"  

If I push the "ignore" button or the "create data CD" button I am able to see the file.

Is the file really there or not?  What is going on?

---

### Post by damis648 on 2008-07-21
After you drag it in, you have to click "Write CD" at the top. That is just the temporary writing folder.

---

### Post by Het Irv on 2008-07-21
When you put the file into the CD's folder, you are placing it in a list of files to be burned.  You will actually have to burn the CD for the files to be there.

---

### Post by tc101 on 2008-07-21
I pushed the write button and it said it had done a write.  However, when I put the CD in drive 2, it says "Unable to mount media".  I put another CD in drive 2 and it reads it just fine.

Could there be a problem with the blank CD I used?  If so, how do I figure this out?

---

### Post by Het Irv on 2008-07-21
Can the first drive read the CD now?  If not it was a bad burn, try burning at a lower speed.

---

### Post by tc101 on 2008-07-21
The first drive reads the CD, but if I try to drag a new file to that CD I get a message saying "Error, you do not have permission to write to this folder.  How do I wipe the CD clean and start from scratch?  Also, how do I set the burn speed?

---

### Post by damis648 on 2008-07-21
> **tc101 said:**
> The first drive reads the CD, but if I try to drag a new file to that CD I get a message saying "Error, you do not have permission to write to this folder.  How do I wipe the CD clean and start from scratch?  Also, how do I set the burn speed?

You would have to use gnomebaker for setting the burn speed, it is an advanced feature. And the permissions problem is because the CD has already been written and is a CD-R. It cannot be erased. Sorry. If you have no use for it, its garbage.

---

### Post by tc101 on 2008-07-21
It is a rewitable CD.  On the cover it says:  TDK CD-RW, 1-4x, 80 min, 700 mb

---

### Post by damis648 on 2008-07-21
> **tc101 said:**
> It is a rewitable CD.  On the cover it says:  TDK CD-RW, 1-4x, 80 min, 700 mb

Use Applications>Sound & Video>Brasero to erase it.

---

### Post by t0p on 2008-07-21
> **tc101 said:**
> The first drive reads the CD, but if I try to drag a new file to that CD I get a message saying "Error, you do not have permission to write to this folder.  How do I wipe the CD clean and start from scratch?  Also, how do I set the burn speed?

I have found it best to use Brasero to wipe clean a CD and write new files to it. I think Brasero is installed by default in Hardy.

---

### Post by NikoC on 2008-07-21
Just in case if KDE is your desktop environment, go for k3b to burn discs.

Cheers.

---

### Post by m_ad on 2008-07-21
I bet your drive is like mine :lolflag:

sometimes it doesn't read -rw's. reads them as blank discs.

---

### Post by tc101 on 2008-07-21
I am still on Gutsy, but I installed Brasero.  I am now blanking the CD.  How long should this take?  It has been going for about 3 minutes.

---

### Post by tc101 on 2008-07-21
I got tired of waiting for Brasero to blank the CD, stopped the process, and started over with Fast Blanking checked.  That has been running for 7 minutes, so there must be some problem, either with the CD or the drive.  I will try to isolate the error.  First thing I will do is try a new CD.

Thanks for your help.

---

### Post by tc101 on 2008-07-21
Now the CD drive won't eject the CD.  I closed Brasero.  I tried pushing the eject button.  I tried right clicking the drive and hitting "Eject".  A light is flashing on the CD drive.  Any ideas?

Ignore this.  The drive just ejected.  Don't know what is going on.  Will start with a new CD.

So everyone agrees that Brasero is the best thing to use now?

---

