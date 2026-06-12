---
title: "Is there a need for ext2, ext3, or ext4 anymore?"
date: 2015-11-16
forum: New to Ubuntu
---

### Post by bob-briggs on 2015-11-16
Really, my problem may be a definition. Since I upgraded to 15.10 I have been seeing new “errors” I did not see in 15.04. The one that befuddles me most right now is the report that I am missing ext3.mod. I looked, I am indeed missing ext3.mod, but on researching the issue I find that the use and definition of the exts is more flexible than I like. Some say that ext2 can recognize all 3 of them, others say that ext4 can do the same thing; yet others say you don’t need any to boot. If any of them are true, why am I being advised that ext3.mod is missing?

---

### Post by bab1 on 2015-11-16
> **bob-briggs said:**
> Really, my problem may be a definition. Since I upgraded to 15.10 I have been seeing new “errors” I did not see in 15.04. The one that befuddles me most right now is the report that I am missing ext3.mod.

Where do you see this "report".  Can you post this here?  There is no ext3.mod you should be using ext.mod in the grub file for any ext file system that you are using to boot from.
> 
 I looked, I am indeed missing ext3.mod, but on researching the issue I find that the use and definition of the exts is more flexible than I like. Some say that ext2 can recognize all 3 of them, others say that ext4 can do the same thing; yet others say you don’t need any to boot. If any of them are true, why am I being advised that ext3.mod is missing?
The ext file system was originally released as ext2.  The ext3 and ext4 file systems are just extensions of ext2.  The most important part is the addition of journaling to both 3 and 4.  The boot parameters are the same.  Once again; where are you advised that ext3.mod is missing?  Post that exact text information here so we may see it.

---

### Post by bob-briggs on 2015-11-18
BAB1 - really appreciate your comment, it made me look at my problem again to see....

Yes, I am still getting "file missing" report as I am booting up my only 15.10 and the only one I have on an ext3 partition.

And yes as I was researching this problem I had to dig through quite a few arguments for and against each of our exts. Research continues.

---

### Post by bab1 on 2015-11-18
> **bob-briggs said:**
> BAB1 - really appreciate your comment, it made me look at my problem again to see....

Yes, I am still getting "file missing" report as I am booting up my only 15.10 and the only one I have on an ext3 partition.

And yes as I was researching this problem I had to dig through quite a few arguments for and against each of our exts. Research continues.
Post that **_[SIZE=3]exact text information[/SIZE]_** here so we may see it.   This is NOT a matter of which ext file system you use.  It is a grub booting issue.

---

### Post by bob-briggs on 2015-11-18
You know I didn't have these problems (there are a few intermittent) with 15.04, this is just one of them.

ah, to the exact message:

When I select to boot to 15.10 I get...

error: file &#8216;/boot/grub/i386-pc/ext3.mod&#8217; not found
Press any key to continue...

Then in about 10-15 seconds it boots

Someone said to me that Linux is the way to wisdom...this sure is.  I&#8217;m still stumped.  Wisdom could be telling me reload 15.04, but this problem would haunt me.

---

### Post by bab1 on 2015-11-19
> **bob-briggs said:**
> You know I didn't have these problems (there are a few intermittent) with 15.04, this is just one of them.

ah, to the exact message:

When I select to boot to 15.10 I get...

```
error: file ‘/boot/grub/i386-pc/ext3.mod’ not found
Press any key to continue...
```

Then in about 10-15 seconds it boots

Someone said to me that Linux is the way to wisdom...this sure is.  I’m still stumped.  Wisdom could be telling me reload 15.04, but this problem would haunt me.
I don't use any releases except the LTS versions.  I find the releases between them to be experimental.  Problems are solved during the time that they are current.  The knowledge gained is incorporated into the next LTS version.  Ubuntu 15.10 is the last version before the LTS version 16.04.  That being said, about as close an answer I can give you is this:  You choice of of using ext3 as the file system format may have caused problems with the creation of the grub2 boot loader.  There is no advantage using ext3 over ext4, but there are some disadvantages.  One of them is that ext4 file system clears up some file syncing problems that can cause file corruption.  I don't use ext3 at all anymore.

I would either: a) reinstall 15.10 using ext4 as the file system format, or b) revert to 15.04.  

I would file a bug report with your observations re: grub2.

---

### Post by grahammechanical on 2015-11-19
I have never seen an error message like that and I have run every development version of Ubuntu over the last three years or more. I am now running Xenial Xerus and there are 271 items in /boot/grub/i386-pc/ and one of them is ext2.mod but there is no ext3.mod and I still do not get that error message.

Perhaps an examination of grub.cfg might throw some light on this matter. This is a line that seems to be part of the boot parameters of every kernel,

> insmod ext2

Perhaps that has been changed to insmod ext3 in your grub.cfg? 

Just a thought.

---

