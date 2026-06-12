---
title: "[SOLVED] What is the difference between ext2 and ext3 and does ext3 require defrag?"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2008-07-18
I have two questions:

1. What is the difference between ext2 and ext3.  Is one really supperior to the other?

2. Does an ext3 partition require defrag?

---

### Post by bodhi.zazen on 2008-07-18
> **pi.boy.travis said:**
> I have two questions:

1. What is the difference between ext2 and ext3.  Is one really supperior to the other?

ext3 is ext2 with a journal.

[http://www.linux.com/feature/31939](http://www.linux.com/feature/31939)

[http://www.linux.com/articles/31966](http://www.linux.com/articles/31966)

> 2. Does an ext3 partition require defrag?With the exception of rare circumstances, such as a very full disk, no.

[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by SunnyRabbiera on 2008-07-18
Use ext3 as ext2 is a bit archaic now...

---

### Post by someonestolemyname on 2008-07-18
Not sure if anyone directly answered...
Ext3 is better than Ext2. Use it always.

Daniel

---

### Post by hyper_ch on 2008-07-18
> **someonestolemyname said:**
> Ext3 is better than Ext2.

in what ways?

---

### Post by nikgare on 2008-07-18
Ever heard of google?
[http://www.google.com/search?q=ext2+vs+ext3&ie=utf-8&oe=utf-8&aq=t&rls=FlockInc.:en-US:unofficial&client=firefox](http://www.google.com/search?q=ext2+vs+ext3&ie=utf-8&oe=utf-8&aq=t&rls=FlockInc.:en-US:unofficial&client=firefox)

---

### Post by hyper_ch on 2008-07-18
> **nikgare said:**
> Ever heard of google?
[http://www.google.com/search?q=ext2+vs+ext3&ie=utf-8&oe=utf-8&aq=t&rls=FlockInc.:en-US:unofficial&client=firefox](http://www.google.com/search?q=ext2+vs+ext3&ie=utf-8&oe=utf-8&aq=t&rls=FlockInc.:en-US:unofficial&client=firefox)

Well, I've never heard of google before ;)

However, in case you haven't noticed, someonestolemyname just said ext3 is better without giving any explanation why that is so and I challenged that ;)

---

### Post by someonestolemyname on 2008-07-18
I was just trying to clarify what bodhi.zazen wa saying in the first reply. I don't blame you for your evidence question. For my evidence, see here: [http://ubuntuforums.org/showpost.php?p=5408511&postcount=2](http://ubuntuforums.org/showpost.php?p=5408511&postcount=2)

=P

---

### Post by hyper_ch on 2008-07-19
> **someonestolemyname said:**
> I was just trying to clarify what bodhi.zazen wa saying in the first reply.
Ah :)

---

### Post by pi.boy.travis on 2008-07-19
Thanks for all the good info and links to additional information!

---

### Post by avatarmonkeykirby on 2011-03-13
> **someonestolemyname said:**
> Not sure if anyone directly answered...
Ext3 is better than Ext2. Use it always.

Daniel

In the case of using a Solid-State Drive or a USB storage device it's actually recommended that you use EXT2 over EXT3+ because the journal will use up the limited life of write-erase cycles of the flash devices.

---

### Post by Paqman on 2011-03-13
> **avatarmonkeykirby said:**
> In the case of using a Solid-State Drive or a USB storage device it's actually recommended that you use EXT2 over EXT3+ because the journal will use up the limited life of write-erase cycles of the flash devices.

That's excessively conservative IMO. Most SSDs have wear-levelling algorithms that make the limited write count a non-issue. The only SSDs this was an issue on was the very early, very cheap ones, such as those fitted to the Eee PC 701s. Even then it was more of a theoretical limit than a practical one.

On a modern SSD I would suggest using EXT4. Using EXT2 would mean your filesystem is not journalled, which is a bad idea. For USB sticks it doesn't particularly matter as they aren't normally doing loads of writes anyway. Use FAT32 for compatibility with other OSes unless you need to store files larger than 4GB on the stick.

---

