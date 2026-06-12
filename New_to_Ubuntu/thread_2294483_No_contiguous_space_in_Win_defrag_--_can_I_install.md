---
title: "No contiguous space in Win defrag -- can I install anyway?"
date: 2015-09-11
forum: New to Ubuntu
---

### Post by dave194 on 2015-09-11
Booting now from a live USB, I'm considering installing side-by-side with the existing OS, so I cleaned up the disc and ran Windows defragment a couple of times, but the defrag GUI still shows "files that can't be moved" all across the disc, with space between them -- not enough contiguous space to install Ubuntu 14.04.

If I try to install anyway, will the installer be able to move those files, to give me half the disc for Ubuntu?   I do need to retain the ability to use Windows, too.  Will installation under these circumstances entail greater risk of messing up the Windows partition?  (I don't have a way of backing up and restoring the Windows system.)

Thanks,
Dave

---

### Post by Topsiho on 2015-09-11
I don't think you should let the [COLOR="#FF0000"]Ubuntu[/COLOR] install do the repartitioning of your [COLOR="#008000"]Windows[/COLOR] disk. That should be done by Windows itself, otherwise on reboot of Windows it is confronted with a new unknown situation, and will check the hard disk first, which is, or appears to be as, not booting at all.
So if Windows is not capable of creating enough contiguous space, and you need Windows, and you even can't backup your files properly, I guess you are stuck :(

How much contiguous space do you think you need for your the Ubuntu install? For the system you need at least 5 or 6 GiB, preferably some more, for swap you need 2 x your RAM, and then you need some space for your personal files, which can be anything. 

Topsiho

---

### Post by grahammechanical on 2015-09-11
How much free space is there on that disk? As I understand the defrag process, it moves fragments  of a file to empty space and collects all the fragements of the same file together and then it clears space for the now unfragemented file by moving other files out of the way so that the unfragmented file can be moved up against the other files that have already been defragmented.

If Windows is saying that there is not enoungh contiguous space left to move the remaining defragmented files around, then it seems to me that your hard disk maybe close to being full. The fragments of the remaining files could too large to fit into the remaining contiguous space. Moving those fragments would fragment them. 

To install Ubuntu you would need to resize at least one windows partition to create unallocated space for Ubuntu. Does that disk have enough unused space so that you can resize a Windows partition to create space for Ubuntu? I would guess that if you run the Ubuntu installer it would only offer you the option to Erase disk and install Ubuntu. And that will delete everything at present of the hard disk.

Regards.

---

### Post by dave194 on 2015-09-11
> **Topsiho said:**
> I don't think you should let the [COLOR=#FF0000]Ubuntu[/COLOR] install do the repartitioning of your [COLOR=#008000]Windows[/COLOR] disk. That should be done by Windows itself, otherwise on reboot of Windows it is confronted with a new unknown situation, and will check the hard disk first, which is, or appears to be as, not booting at all.
So if Windows is not capable of creating enough contiguous space, and you need Windows, and you even can't backup your files properly, I guess you are stuck :(

How much contiguous space do you think you need for your the Ubuntu install? For the system you need at least 5 or 6 GiB, preferably some more, for swap you need 2 x your RAM, and then you need some space for your personal files, which can be anything. 

Topsiho
There is plenty of free space -- around half the disk -- which is plenty of room for Linux.  It's just that the free space is broken up by many green bars, which the defrag utility identifies as files that "can't be moved."  Thanks for your interest and help!

---

### Post by dave194 on 2015-09-11
> **grahammechanical said:**
> How much free space is there on that disk? As I understand the defrag process, it moves fragments  of a file to empty space and collects all the fragements of the same file together and then it clears space for the now unfragemented file by moving other files out of the way so that the unfragmented file can be moved up against the other files that have already been defragmented.

If Windows is saying that there is not enoungh contiguous space left to move the remaining defragmented files around, then it seems to me that your hard disk maybe close to being full. The fragments of the remaining files could too large to fit into the remaining contiguous space. Moving those fragments would fragment them. 

To install Ubuntu you would need to resize at least one windows partition to create unallocated space for Ubuntu. Does that disk have enough unused space so that you can resize a Windows partition to create space for Ubuntu? I would guess that if you run the Ubuntu installer it would only offer you the option to Erase disk and install Ubuntu. And that will delete everything at present of the hard disk.

Regards.
Windows is not saying why the remaining defragmented files "can't be moved" -- just that they can't.  I don't think it is a space issue, since the GUI shows empty spaces that are larger than the green bars representing files that "can't be moved."  Yes, there is enough unused space, but it is broken up rather than contiguous.  

Thank you for taking the time to discuss this with me.

---

### Post by oldos2er on 2015-09-11
> **dave194 said:**
> If I try to install anyway, will the installer be able to move those files, to give me half the disc for Ubuntu? 

It could do that easily, but it would break Windows. Since you say you need Windows and currently have no way to backup, you should consider getting another hard drive.

---

### Post by Mark Phelps on 2015-09-11
Contiguous space exist only INSIDE an existing Windows filesystem partition -- and it you're planning to install THERE, do not.  You need space OUTSIDE of the windows filesystem to install Linux.  

If the problem is that you're trying to shrink the Windows filesystem partition, and the unmoveable files are preventing that, then read the material in the link -- that may help: [http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")  The link is for Vista, but the problems are the same in newer versions of Windows.

---

### Post by dave194 on 2015-09-11
Thank you Mark, oldoz2er, grahammechanical and Topsiho.  Your comments and suggestions are much appreciated.  After reviewing the complexity and risks of trying to partition the drive while safeguarding an irreplaceable Windows OS, I have decided to keep using Ubuntu 14.04 from the live USB, rather than installing it at this time.

It works fine with good response time using the USB drive, and I am very happy using it that way.  Someday, once I have verified that I can do everything I need to do in Ubuntu, and no longer need legacy Windows apps and files, I will almost certainly wipe the laptop's drive clean and install Ubuntu as the installed OS.

Thank you, all, again!!!

---

### Post by Bucky Ball on 2015-09-11
That's probably a good idea. Also, if you end up with another drive and have backed up your install you could have a go at dual-booting, as suggeseted.

Have you got a persistence install on the USB, as in, it remembers your files and settings on reboot?

Please see the first link in my signature. Cheers.

PS: Rule of thumb is resize Win partition with Win software, Ubuntu with Ubuntu. :)

---

### Post by dave194 on 2015-09-13
> **Bucky Ball said:**
> That's probably a good idea. Also, if you end up with another drive and have backed up your install you could have a go at dual-booting, as suggeseted.

Have you got a persistence install on the USB, as in, it remembers your files and settings on reboot?

Please see the first link in my signature. Cheers.

PS: Rule of thumb is resize Win partition with Win software, Ubuntu with Ubuntu. :)
Thanks, Bucky.  Actually, I've found some small external drives for under $50, so I'm going to obtain one of those and do a full install on the external drive.

Thank you!

---

### Post by Bucky Ball on 2015-09-13
Good plan. Please see the first link in my signature and mark the thread as solved. Post a new one for any further questions/problems. Good luck. :)

---

