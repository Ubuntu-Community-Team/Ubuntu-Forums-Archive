---
title: "How to evaluate space on boot USB"
date: 2011-09-23
forum: New to Ubuntu
---

### Post by Denver Dave on 2011-09-23
I have a 16 GB USB drive where installed ubuntu.  I attempted to install kontact

sudo aptitude install kontact
gave aptitude: command not found

sudo apt-get install kontact
lots of messages, the last being:
Need to get 83.6 MB of archives.
After this operation, 267 MB of additional disk space will be used.
Do you want to continue
I choose not to.

The Disk Utility identifies 10 GB ext4 - Extended 5.9 GB (21.9 GB Swap Space and 2.9 GB Swap Space),  Even though there is a line for available, it does not contain a value.  

With the Disk Usage analyzer it defaults to my main hard drive not the USB drive and also allows remote drives, but does not seem to allow the boot USB to be analyzed.

Seems strange that I'm out out space on the 16 GB drive, but maybe.  Last time I continued installation on a smaller USB seemed like it might have goofed a few things up (not sure).

How do I evaluate available space on boot USB drive?

Thanks.

= = = = = = = = 
In disk Usage Analyzer clicked on Scan Home
- Total filesystem capacity 228.4 GB (used 34.6 GB available 193.8 GB) - is this total of all drives??

Looking down the folders, see:
denverdave usage 100% Size 142 MB with most of the space in .mozilla 125.6 MB

---

### Post by Rubi1200 on 2011-09-24
Try this in the terminal:

```
df -H
```

Here are some tips for cleaning up space on Ubuntu:
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by Denver Dave on 2011-09-25
Thanks.  The terminal command  df -H does give free space on my USB stick

16 GB stick
/dev/sdb1  10G  Used 3.66
none 1.56 used 709
none 1.56 used 1.4M
none 1.56 used 95K
none 1.56 used none

It would appear that there is plenty of space on the USB stick, although perhaps not where it is needed.   

Which brings me back to the mystery of asking if can get space from Archives.  Not sure of the ramifications of this.

The GUI System Monitor under the File systems tabs gives similar info for the USB boot stick (interesting doesn't mention the main HD)

So if I have 6 GB or so free on the Boot USB, why is more space from archives (whatever that is) needed?

Thanks.

---

### Post by mcduck on 2011-09-25
> **Denver Dave said:**
> 

So if I have 6 GB or so free on the Boot USB, why is more space from archives (whatever that is) needed?

Thanks.
You want to install a new program, so of course you'll need to download it. And that takes some space.

The message is telling you that to install that program it will need to download 83.6MB worth of files, and once installed they will take 267MB of disc space.

So it's not telling you that you'd need more disc space, but simply that installing new software will use some of the space you have. :)

---

