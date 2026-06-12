---
title: "Best FILESYSTEM for Linux?"
date: 2008-08-20
forum: Recurring Discussions
---

### Post by Krupski on 2008-08-20
I'm probably opening a can 'o worms here... but...

Which FS is better for Linux? EXT3 or XFS (or other)?

And, please explain, technically, why.

Thank you!

-- Roger

---

### Post by meindian523 on 2008-08-20
Depends on what you want to use the partition you are formatting for.

---

### Post by forger on 2008-08-20
You need to mention the use to find a better file system
So, best for what use? :)
What do you do every day?

---

### Post by LUS93 on 2008-08-20
Google is your friend in this case. 

There is no one canned "this filesystem is the best for everything" answer. If there were, the other filesystems wouldn't exist.

I suggest a stack of whitepapers, a clear idea of what you need a filesystem to do (you surely have some idea since you're asking the question) and a lot of coffee.

---

### Post by forger on 2008-08-20
Nevertheless, people could provide their experience with the filesystem they use. That's why I asked for the purpose of the machine

---

### Post by LateNiteTV on 2008-08-20
the best file system is the one that suits your needs.

---

### Post by dexter.deepak on 2008-08-20
if you really need some good details have a look here :
[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)
for linux, it really depends on your usage style and preferences.
as far as i have experienced,ext3 for security and reiserfs for speed. but this is MY experience and opinions may vary.
you should rather study and use filesystems to know them better.

---

### Post by sandysandy on 2008-08-20
see these links

[http://linuxgazette.net/102/piszcz.html](http://linuxgazette.net/102/piszcz.html)

[http://wiki.novell.com/index.php/File_System_Primer](http://wiki.novell.com/index.php/File_System_Primer)

[http://fsbench.netnation.com/](http://fsbench.netnation.com/)

regards

---

### Post by LowSky on 2008-08-20
The best out there is probably ZFS, but it only runs on Solaris OSes. ext4should be becoming the newest Linux standard in the upcoming years.
But for now ext3 isn't that bad at all.

---

### Post by bodhi.zazen on 2008-08-20
This is an age old question.

[http://www.linux.com/feature/31939](http://www.linux.com/feature/31939)

[http://www.linux.com/articles/31966](http://www.linux.com/articles/31966)

Unless you have some specialized need, IMO, stay with ext3. I find the the web pages re: speed/performance of various file systems frankly a lot of hype and speed on so called performance tests is not a good reason to select a file system. In my experience, with day to day use, I do not find performance is affected much by the root file system.

Now if you are running a server or performing a specialized task you may benefit from changing your file system.

---

### Post by Krupski on 2008-08-20
Thank you! To all who posted.

The usage in my case for the filesystem is pure data storage (i.e. a Network Attached Storage box).

I tried XFS and found that it was faster than EXT3 and it also left quite a bit more freespace on my RAID drive.

So... thinking "It must be too good to be true", I got skeptical. What does XFS give up for it's performance?

Then I started reading all kinds of reviews and comparisons until my brain once again began hurting.

Then I got lazy and decided to just ask!  :)


(edit to add): Given a choice between SPEED and RELIABILITY (reliability being defined as corruption resistance, recovery from power failure, general data integrity), I want RELIABILITY.

XFS must give up something for it's speed and lack of disk space overhead... otherwise it would be used instead of EXT3.... yes?

---

### Post by Gamma746 on 2008-08-21
> **Krupski said:**
> What does XFS give up for it's performance?

XFS does *not* handle sudden power loss very well.  I wouldn't recommend using it unless you have a UPS.

If you want reliability above all else, use ext3.

---

### Post by Dremora on 2008-08-22
> **Gamma746 said:**
> XFS does *not* handle sudden power loss very well.  I wouldn't recommend using it unless you have a UPS.

If you want reliability above all else, use ext3.

It handles power outages a lot better lately, Linux 2.6.25 and .26 got rid on most remaining XFS issues.

I don't use anything but XFS.

At the risk of being flamed, XFS has a defragger called XFS_FSR that is provided in the xfsdump package.

(Yes ext3 frags, get over it) :P

---

### Post by billgoldberg on 2008-08-22
I use reiserfs now and don't notice any differences (good or bad) over ext3.

---

