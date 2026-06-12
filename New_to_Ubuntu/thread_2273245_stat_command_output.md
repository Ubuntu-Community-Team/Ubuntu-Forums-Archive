---
title: "stat command output"
date: 2015-04-11
forum: New to Ubuntu
---

### Post by aliak-93 on 2015-04-11
hello everybody. 
I'm looking for an explanation to all the data that I get as output to the stat command in the shell. I'd really like to understand it!
I'm really gratefull for your helping and patience with us newbies!

---

### Post by TheFu on 2015-04-11
**stat --help ** explains
or there is **man stat**.

I've never used stat from the shell before today.  I have used it from C/C++ and perl programs. There are manpages for those specific uses too - just in different manpage sections.

```
$ /usr/bin/stat /etc/hosts
  File: &#8216;/etc/hosts&#8217;
  Size: 427837          Blocks: 840        IO Block: 4096   regular file
Device: fc00h/64512d    Inode: 928000      Links: 1
Access: (0644/-rw-r--r--)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2015-04-11 09:32:00.223224764 -0400
Modify: 2015-02-12 05:45:19.741221795 -0500
Change: 2015-02-12 05:45:20.133204226 -0500
 Birth: -
``` 

Someone else wrote this: [http://bencane.com/2012/05/24/stat-detailed-information-about-a-file/](http://bencane.com/2012/05/24/stat-detailed-information-about-a-file/)

Specific question?

---- Update ----
So - I was reading the manpage and it appears that your/my shell may override the /usr/bin/stat command. They say to check the specific shell manpage for details.

---

