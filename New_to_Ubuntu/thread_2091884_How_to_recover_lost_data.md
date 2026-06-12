---
title: "How to recover lost data"
date: 2012-12-06
forum: New to Ubuntu
---

### Post by AlphaQ on 2012-12-06
i recently installed lubuntu by overwriting over windows 7.
to make it clearer, i have lubuntu as my operatins system no dual boot...only a single OS.
Now , as far as i have heard,when you install a new os over your current os, only the partition in which the os is installed is formatted. but i dont know how, but my entire hard disk was formatted !! the entire 160 gb !! Among the formatted data were many movies and photos clicked over 6 years :'(.. how do i recover them , or atleast most of them?? :(
please help...they are really sentimental..

---

### Post by Frogs Hair on 2012-12-06
If you used option 2 in the  screen shot I think you are out of luck.

---

### Post by Grenage on 2012-12-06
> **AlphaQ said:**
> i recently installed lubuntu by overwriting over windows 7.
to make it clearer, i have lubuntu as my operatins system no dual boot...only a single OS.
Now , as far as i have heard,when you install a new os over your current os, only the partition in which the os is installed is formatted. but i dont know how, but my entire hard disk was formatted !! the entire 160 gb !! Among the formatted data were many movies and photos clicked over 6 years :'(.. how do i recover them , or atleast most of them?? :(
please help...they are really sentimental..

First things first, stop using the drive; do not boot from it, do not write to it.

There are programs such as photorec, which are quite good, but in my opinion *getdataback for ntfs* is the best software for recovering data from NTFS partitions.  You won't recover data that's been over-written, but you'll probably be able to get back the rest of it.

It's not free, but I believe there is a trial, so you can at least find out if it would recover any data.

---

### Post by Mark Phelps on 2012-12-06
The same company that sells GetDataBack sells RecoverMyFiles -- and like the former, you can download a trial version, install it to a Windows PC, connect your drive, run it against that drive -- and see what it finds.

IF it finds your files, you will have to go online to purchase a license to do the actual recovery.

Last time I checked, the license was around $80 USD.

---

### Post by AlphaQ on 2012-12-06
I used the second option and erased disk..any luck??

---

### Post by Frogs Hair on 2012-12-06
The above posts are your best chance. I have a program that can find deleted files but it only works in a Windows installation. Once the free space is wiped or the disk is formated it's useless.

---

### Post by AlphaQ on 2012-12-07
> The same company that sells GetDataBack sells RecoverMyFiles -- and like the former, you can download a trial version, install it to a Windows PC, connect your drive, run it against that drive -- and see what it finds.

IF it finds your files, you will have to go online to purchase a license to do the actual recovery.

Last time I checked, the license was around $80 USD.

You mean I remove my HDD from my PC, and connect it to another PC running windows and then run the program??

---

### Post by Anderson233 on 2012-12-07
As you have installed new OS so some of your files are overwritten now and can't be recovered with the help of any software. For maximum chances of recovery stop using the PC and uninstall the drive and connect that drive as an external drive to some other system running Windows. Now download and install a software called Kernel for Windows Data Recovery and then scan the drive for recovery options available. I had good experience with this tool in the past and recovered almost 100 GB of data.

---

### Post by AlphaQ on 2012-12-07
This gives me hope :)
will try on Tuesday ....

---

### Post by Toriku on 2012-12-07
to my knowledge linux writes randomly around the disk, while windows writes sequentually... if you've not used it much since re-installing maybe it randomly selected areas with no files or unimportant files, the more you use that computer, the more likely it is a file you want will be written over.

You should take the hard disk out and recover your files from another PC

---

### Post by Mark Phelps on 2012-12-07
> **AlphaQ said:**
> You mean I remove my HDD from my PC, and connect it to another PC running windows and then run the program??

Yes -- you HAVE to do this because you can't recover lost data back to the same drive; instead, you have to write it to a different drive.

---

### Post by AlphaQ on 2012-12-10
But my problem is the only other windows device at home is a laptop.. how do i connect an HDD to a laptop??:confused:

---

### Post by NightsShadeQueen on 2012-12-10
There are hard-drive to USB connector devices. What hard drive do you have?

---

### Post by AlphaQ on 2012-12-11
I dont get that.. what do mean by type of harddrive??
the brand,hdd/ssd or interface??

---

### Post by Grenage on 2012-12-11
Yes, SATA/IDE drive.  You can get USB adapters, or external caddies.  It's hellishly slow by comparison, but they work.

---

### Post by AlphaQ on 2012-12-11
i guess its SATA..
i am hesitant to do all this 'coz i feel i will mess it all up,BIG TIME.
Should i just call in a pro??

---

### Post by Grenage on 2012-12-11
As long as you don't use the drive (install the software on the laptop, then plug in the drive), then there's no reason you should have too many problems.  The software previously mentioned is quite user-friendly.

Professional firms are rather expensive, although in your case probably not *quite* as expensive as they can be.

---

### Post by memilanuk on 2012-12-11
> **AlphaQ said:**
> i guess its SATA..
i am hesitant to do all this 'coz i feel i will mess it all up,BIG TIME.
Should i just call in a pro??

You SHOULD have made a BACKUP before messing with stuff you didn't understand.  Its not like there aren't multiple FREE easy to use system backup and imaging utilities and live CDs available out there.

Now you get to pay the price.  

Honestly... I'd say you're screwed.  Consider the data lost, chalk it up to experience, and move on.

---

