---
title: "Disk Defragmentation"
date: 2011-12-02
forum: New to Ubuntu
---

### Post by arno48 on 2011-12-02
Hellow,
is Disk defragmentation necessary in Ubuntu?
If so is there an utility available?
Thanks

---

### Post by Lars Noodén on 2011-12-02
It's not needed unless you are using an outdated file system like NTFS.  The default file systems for Ubuntu (Ext4 or Ext3) do not need it.

---

### Post by lolpenguin on 2011-12-02
If you have an SSD do not attempt to defrag. It will reduce the life of your SSD, and it won't make a difference.

---

### Post by The Cog on 2011-12-03
> **arno48 said:**
> Hellow,
is Disk defragmentation necessary in Ubuntu?
As others have said, in general defragmentation is not needed.

If you use Linux to write to ntfs a lot, you might need to occasionally use windows to defrag that ntfs partition, but the linux filesystems don't tend to get themselves into such a state.
> If so is there an utility available?I don't think there is such a utility, which only goes to show that defrag really isn't needed.

The upcoming btrfs filesystem will have an online defrag utility, but that's because of the rather different way it handles disk updating.

---

### Post by mörgæs on 2011-12-03
If you don't fill your hard disk more than 3/4, there is no need for defragmentation. 

As many other topics discussed here, defragmentation is a Windows habit brought into Linux.

---

### Post by arno48 on 2011-12-04
Thank you, quite clear.
I can mark the thread as solved now.

---

### Post by *^kyfds( on 2011-12-04
very clear. 

about 10 responses saying pretty much the same thing.

nice.

---

### Post by Clearsup on 2012-05-25
> defragmentation is not needed in Linux

Everyone repeat this like a dogma.
So, how do you know it's not necessary?
How do you check your disc fragmentation?

What's important, how can i check mine?

---

### Post by zombifier25 on 2012-05-25
Post split into its own thread in 3... 2...
Anyway,
> **Clearsup said:**
> 
So, how do you know it's not necessary?

[ext4's wikipedia page](https://en.wikipedia.org/wiki/Ext4) describes some techniques it uses in order to keep fragmentation level to the minimum. [This page on defragmentation](https://en.wikipedia.org/wiki/Defragmentation) also states that ext4 generally does not need to be defragmentated.
> **Clearsup said:**
> 
How do you check your disc fragmentation?

What's important, how can i check mine?

I don't think a tool like so is available, since it's not really useful. Then again, I may be wrong.

---

### Post by Lars Noodén on 2012-05-25
> **zombifier25 said:**
> 
I don't think a tool like so is available, since it's not really useful. Then again, I may be wrong.

There was one for EXT2 but not updated since 1998 because the EXT file systems don't really get that fragmented:
[http://tldp.org/LDP/sag/html/filesystems.html#FRAGMENTATION](http://tldp.org/LDP/sag/html/filesystems.html#FRAGMENTATION)

Now that I check, it seems no longer available.  No loss.

---

### Post by oldos2er on 2012-05-25
Look up **e4defrag**: [http://manpages.ubuntu.com/manpages/precise/man8/e4defrag.8.html](http://manpages.ubuntu.com/manpages/precise/man8/e4defrag.8.html)

---

### Post by ubuntu27 on 2012-05-25
Read this: [Why doesn't Linux need defragmenting]("http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting")?

---

### Post by Guilden_NL on 2012-05-25
> **oldos2er said:**
> Look up **e4defrag**: [http://manpages.ubuntu.com/manpages/precise/man8/e4defrag.8.html](http://manpages.ubuntu.com/manpages/precise/man8/e4defrag.8.html)

Nice, thanks for the link.

And I am just getting up off of the floor from seeing your avatar.  Ohhhh the memories from 1993 and setting up an OS2 server.  It was only a couple of months after that when I started using Linux.  Maybe my subconscious was directing me in that direction.

---

### Post by 577 Jersey on 2012-11-15
Defragmentation,,
 Another reason I wont miss being held captive by windows :mad:

---

### Post by felixq78 on 2012-12-08
Yet Ubuntu Software Centre is selling HDD Ranger (a defrag app' for ext4 file system) for $7.99. If we don't need it why are they trying to sell us the app ?
I've been using Ubuntu since 8.04 and have never felt the need to defrag my drives, they've always worked well with no slowing down etc

---

### Post by zydecoman on 2012-12-08
Thanks for asking this question and for the answers. I was wondering about fragmentation too.

---

### Post by Bucky Ball on 2012-12-08
[I][B]Thread Closed
[/B][B]
Reason:[/B][/I] Old thread put to sleep. Original question was answered (many times) and solved many posts ago.

---

