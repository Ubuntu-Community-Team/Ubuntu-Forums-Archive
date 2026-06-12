---
title: "How to burn a backup on CD preserving all tweaks ?"
date: 2014-11-19
forum: New to Ubuntu
---

### Post by Innernet on 2014-11-19
Hi.
My installation has been tweaked, setup and tailored to my exact needs and taste;  
Will a backup preserve everything and be capable of replicate exactly the same for a new hard drive ?  
How is it done - both in creating the CD and later restoring it ?  Do not care about data; just for the operative system, browser, desktop, drivers, foreign keyboard...

---

### Post by yancek on 2014-11-19
There is a program called remastersys which did exactly this and also included an installer.  It had options to preserve personal data in the /home/user folder or not to preserve them.  It is no longer being developed but may still work.  I used it on 12.04 and have read at least one post of someone who got it to work on 14.04.  Another option to clone your install is clonezilla.  Clonezilla should work if it is to be used to restore on the same computer.

---

### Post by monkeybrain20122 on 2014-11-19
Why do you need to burn it to a CD? Just clone it with clonezilla or fsarchiver and save the image. fsarchiver is better IMO as it clones just the file system, but works only wth mbr.

---

### Post by Mark Phelps on 2014-11-20
The best way, in my experience, to preserve everything to to make an "image backup" of your install, which I do routinely using Clonezilla. 

The problem with YOU doing that, is that the image is going to be way too big to fit on a "CD".  Maybe, it would fit on a DVD, but USB sticks are so cheap these days, if the purpose of doing a backup is to be able to restore later, it's better to use USB sticks.  They're larger than DVDs, and they are faster both writing and reading.

---

