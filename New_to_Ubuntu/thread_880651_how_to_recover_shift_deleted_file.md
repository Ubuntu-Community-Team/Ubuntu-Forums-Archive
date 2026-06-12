---
title: "how to recover shift deleted file?"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by sxytrillian on 2008-08-05
I have Accidentally deleted (Shift + delete) an important project file in ubuntu 7.10 and my file system is ext3.

Is there any steps to recover the file?

SO guys please help me out to recover the file.

---

### Post by sharks on 2008-08-05
i think u cant

---

### Post by fiddledd on 2008-08-05
For your sake I hope I'm wrong, but I think on ext3 the data is wiped on deletion.

---

### Post by Grone1985 on 2008-08-05
According to my past experience with some other important projects you can't recover files after shift+del elimination... anyone with more knowledge and a reason for why this happens could back me up???

---

### Post by Vishal Agarwal on 2008-08-05
If you get them, Pls let me know how. B'cos I am also facing the same problem for some files.

---

### Post by WRDN on 2008-08-05
You could try using [Disk Internals Data Recovery]("http://www.diskinternals.com/linux-recovery/") Freeware.

---

### Post by fiddledd on 2008-08-05
Here's a couple of links, I've no idea if they will help:

[http://www.cyberciti.biz/tips/linuxunix-recover-deleted-files.html](http://www.cyberciti.biz/tips/linuxunix-recover-deleted-files.html)

[http://e2undel.sourceforge.net/recovery-howto.html](http://e2undel.sourceforge.net/recovery-howto.html)

But, here's the bad news from one of the developers, Andreas Dilger:

"In order to ensure that ext3 can safely resume an unlink after a crash, it actually zeros out the block pointers in the inode, whereas
ext2 just marks these blocks as unused in the block bitmaps and marks the inode as "deleted" and leaves the block pointers alone.

Your only hope is to "grep" for parts of your files that have been deleted and hope for the best."

---

### Post by sharks on 2008-08-05
i think for using that app u need window$. sxytrillian: if u dont have window$ , u r gng to be an unlucky guy.

---

### Post by AdamWood on 2008-08-05
I don't know an easy way to recover the files but I have had great success myself using **scalpel** and I've heard **ext3grep** can work too.

---

### Post by sxytrillian on 2008-08-05
thanks guys.. let me try out..

---

### Post by Sarmacid on 2008-08-05
I've used the [Sleuth Kit]("http://www.sleuthkit.org/") to do forensics, but never on ext3. Maybe you can give them a try, or try Autopsy, wich is the same but not command line.

---

### Post by hyper_ch on 2008-08-05
get the project file from one of your backups.

---

### Post by jemate18 on 2008-09-06
> **sxytrillian said:**
> I have Accidentally deleted (Shift + delete) an important project file in ubuntu 7.10 and my file system is ext3.

Is there any steps to recover the file?

SO guys please help me out to recover the file.

Also facing the same problem.. cant find a solution.. Oh well, just have to type the document again (due to an accidental SHIFT DELETE)...

:)

---

### Post by hyper_ch on 2008-09-06
as said 4 weeks ago: recover the files from your backups

---

### Post by indeed on 2008-10-16
Here's what worked for me when a rogue rm -rf ate half of my ext3 partition:

Immediately shutdown affected machine and reboot into live cd.
Get network up, download architecture-appropriate ext3grep package from
[here]("http://debian.cs.binghamton.edu/debian/pool/main/e/ext3grep/"),  and install it.
Mount a non-affected local partition with plenty of room, or a network mount if necessary, and cd into it. Do not mount the affected partition.
Run ```
sudo ext3grep /dev/sda1 --dump-names
``` replacing sda1 with the partition having the deleted files. This will take a long time.
While you're waiting convert a convenient date and time just before the deletion into a timestamp. I used [this online tool]("http://www.unixtimestamp.com/").
Run ```
sudo ext3grep /dev/sda1 --restore-all --after=1223960400
``` using your generated timestamp.
This will create a directory 'RESTORED_FILES' containing all ... erm ... restored files.

I am immensely indebted to Carlo Wood's package and explanation [here]("http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html").

---

### Post by jkll on 2008-10-21
ext3grep 

[http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html]("http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html")

---

### Post by Kikuta on 2008-11-16
I keep on getting this error:
```
$ sudo ext3grep /dev/sda1 --dump-names
Running ext3grep version 0.9.0
ext3grep: init_consts.cc:44: void init_consts(): Assertion `super_block.s_magic == 0xEF53' failed.
Aborted

```

---

### Post by raja.genupula on 2011-07-04
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

