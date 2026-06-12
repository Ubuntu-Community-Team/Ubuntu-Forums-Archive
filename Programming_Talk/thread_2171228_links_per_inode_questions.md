---
title: "links per inode questions"
date: 2013-08-29
forum: Programming Talk
---

### Post by mark allyn on 2013-08-29
Hello everyone, 

I have been trying to come to grips with ext3/ext4, in particular, with respect to the maximum number of subdirectories per directory that are permissable.  Wikipedia indicates that for ext3 the number is 32000 (technically, 31998 + 2 for the "." and ".." subdirs).  According to Wikipedia ext4 increases this number to 64,000.  These two figures are fixed by the number of links per inode.

Could someone explain to me what exactly is going on here?  What constrains the number of links per inode?  That is question 1.

Question 2 is related to how one (me, that is) might be able to back into this number by examining dump commands (e.g. dump2efs and similar) for the filesystem?  Using dump2efs on a specific /dev/sdb2 produces a lot of documentation, but nowhere do I see a specific reference to "links per inode".

Thanks to all,

Mark Allyn

---

### Post by trent.josephsen on 2013-09-02
I tried to answer your question 1 some time ago in connection with [this thread](https://bbs.archlinux.org/viewtopic.php?id=164655), but got nowhere. I'm guessing you'll have to go source diving to figure that one out.

You may already understand this, but just to be clear on something: the .. entry in directory /foo/bar/ does not directly increase the link count on bar; it links to, and increases the link count on, foo. foo, in turn, has an entry called "bar", which increases bar's link count (since if it didn't, bar wouldn't be accessible through the hierarchy at all). ext? doesn't permit [multiple hard links to a directory](http://xkcd.com/981/), but if it did, every name under which a directory was accessible would increment the link count by one, just like regular files.

I hope you find the answers you're looking for.

---

### Post by mark allyn on 2013-09-11
Hi Trent.Josephson,

Thanks for the .. info.  It's an interesting point.  

I have gotten absolutely nowhere with this one.  I'm thinking about trying to contact Theordore Ts'o (who has contributed extensively to ext*).  He might know.  But, I think he's a pretty busy guy and may not have the time to explain it to me.

BTW, the link you sent had problems.  Is there another means to get the info to me,.

Regards,
Mark

---

### Post by trent.josephsen on 2013-09-11
My mistake -- that thread isn't accessible to the public. It makes no difference, I think -- there's very little technical content and you probably know it anyway; I won't copy the whole discussion. (If you're really burning with curiosity, you could just create a free account, which would permit you to view it.)

If and when you do figure out the origin of that limitation, I'd be interested to know. 2^15 - 1 is 32,767, so 32,000 is consistent with the link count being stored as a signed 16-bit integer, but that doesn't explain why the designers would have chosen to omit the extra 767 rather than just increasing the limit. Perhaps a round number maximum has performance implications.

---

