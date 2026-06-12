---
title: "Laptop Harddrive damaged but can i at least recover some word documents using ubuntu?"
date: 2013-09-10
forum: New to Ubuntu
---

### Post by Ryan_Barham on 2013-09-10
my laptop froze while i was using it, i restarted and it appear to be  slow then a blue screen came up with the error "unmountable boot  volume." 
i checked the BIOS test for the memory and everything was ok but for the hard drive this came up "hard disk 1 quick 303" 
i have lost alot of data on there but all i want to recover is about 5  word documents in the same folder, they're the only word documents on my  laptop and i really need them.
i installed ubuntu onto my USB and was able to use it, i tried to force mount the hard drive that had been damaged but no luck
has anyone got any ideas where i could recover just those word documents some how?
any answers will be much appreciated!

---

### Post by Mark Phelps on 2013-09-10
Linux will refuse to mount a Windows filesystem that is damaged -- to prevent further damage.  So, in this case, using Linux utilities is likely not to work.

However, if you can connect the drive to a Windows PC, there are Windows data recovery apps that can search the drive for files, without relying on the integrity of the filesystem to do so.  If you want to go that route, then read on ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from Runtime Software in MS Windows.
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to the website below, you can compare the features and (at least for me) the extra cost wasn't worth it:

[http://www.recovermyfiles.com/data-recovery-software-purchase.php](http://www.recovermyfiles.com/data-recovery-software-purchase.php)

Your data ... your money ... your choice.

---

### Post by Ryan_Barham on 2013-09-10
hey thanks for the reply i will try find someone with PC i can borrow, also i have an hp laptop and it has its own tests for the system i recently did a test on the hardrive and this came up.
Testing Drive 1
SMART check: PASSED
Short DST: FAILED
Do you know what that means by the way?

---

### Post by erasmusp on 2013-09-10
Hi Ryan,

I have used a bootable live Linux CD many times in a situation like this. Just boot up from the CD and you should be able to access the data on your hard drive. Then copy the files you need off onto a flash disk.

---

### Post by Ryan_Barham on 2013-09-10
where can i download live linux CD? i'm abit confused where to download it.
after do i then just burn it on to a cd and hope for the best

---

### Post by whitesmith on 2013-09-10
See answer from **Mark Phelps**: Ubuntu won't read a damaged hdd. Even if you could get it to, it would probably cause more damage. If I were you  I would drop $65 on *SpinRite* and hope for the best. [Edit: I'm not affiliated with Steve Gibson or his company that makes *SpinRite*.]

---

