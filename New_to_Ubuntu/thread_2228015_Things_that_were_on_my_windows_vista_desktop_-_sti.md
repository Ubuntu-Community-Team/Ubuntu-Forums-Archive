---
title: "Things that were on my windows vista desktop - still able to find them?"
date: 2014-06-05
forum: New to Ubuntu
---

### Post by gary38 on 2014-06-05
When I installed Ubuntu my original plan was to overwrite Pinguy on my SSD and leave Vista on my HDD, but somehow I managed to overwrite both :redface:, so I was just wondering, as my files and things are still there fortunately, will things that were on my desktop still be there? and if so how do I find them?

Many thanks in advance.

---

### Post by Mark Phelps on 2014-06-05
First of all, things weren't "on" your desktop; instead, they were in your Desktop folder.  They could have been files, folders, or shortcuts to the same.

When you overwrote Vista, you overwrote some files and folders.  Whether or not those include the ones in the Desktop folder, no one really knows.

You would need to run a data recovery app that allows you to look at the contents of the Desktop folder.  

Since this was a Windows filesystem, you would do better using Windows apps -- and Recuva is one that is free.

ALSO -- and this is IMPORTANT -- every time you use the HDD on the PC, you overwrite more files and folders, so the sooner you stop using it, the better the chances of getting anything back.

---

### Post by gary38 on 2014-06-05
So there's no way of just locating the desktop folder and looking in it?  Can you explain the important part please, why would I be overwriting more files and folders on my HDD just by using the PC?

Thanks.

---

### Post by QIII on 2014-06-05
Hello!

From the user perspective, write operations on the disk are non-deterministic.  The machine has a rhyme and reason for where it writes, but you don't get to chose.  If the machine chooses to write over an old file in a partition it has been told is free game, the original file will be destroyed.  At this point, Ubuntu has been told it can write where it wants in the newly created partitions, and it has no record of anything that was there before.  It will only be concerned with files it writes from now on.

You need to recover your files before using the machine further to avoid that eventuality.

---

### Post by gary38 on 2014-06-07
QIII Thanks for explaining that.

OK I don't have windows on my PC anymore so I thought I would look for a tool that I could use on Ubuntu and I came across this - Partition Scanner & Disk Recovery Tool - now I feel like a total newbie here, but I have downloaded it from the Ubuntu Software Center and I can't for the life of me find it.  I thought it would just appear in 'Show Applications' but I don't see it.   argh.  Help anyone?

---

### Post by gary38 on 2014-06-09
Can anyone please advise me, how do I install and run testdisk - partition scanner & disk recovery tool - I can find it in the software center, but beyond that I'm struggling, when I click to install it I don't find it anywhere....?

---

### Post by stalkingwolf on 2014-06-09
it looks like testdisk is a commandline tool.  open terminal and type testdisk.
  depending on how you formatted the hdd it might not work.  the description doesnt mention ext4.  ive never used it.

---

