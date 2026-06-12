---
title: "[SOLVED] HDD Making More Noise Than Usual in Ubuntu 8.04"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by Jack Bonner on 2008-07-23
Well I installed Ubuntu yesterday and i'm extremely happy with it so far, pretty much everything works, and what doesn't work was fixable. There's one thing that slightly worries me though, the hard drive seems to make a lot more noise in Ubuntu than it did in Vista, it's just the normal slight grinding sound that you get when it's accessing the HDD, but it happens a lot more often. I just wondered if it should be doing this

---

### Post by northern lights on 2008-07-23
This is most likely cause Ubuntu frequently checks for the drives presence and thus it never spins down.

Installing PowerTop should tell you what's happening:

```
sudo apt-get install powertop
```

Most likely you can fix this by increasing the dirty_writeback time

```
echo 2000 > /proc/sys/vm/dirty_writeback_centisecs
```

This would set it to 20 seconds, for instance.

---

### Post by sdennie on 2008-07-23
A default Ubuntu install will write the disk more often than Windows however, it's not generally anything to worry about on a desktop machine.  If you find the noise of the increased disk activity annoying or it just makes you nervous, you could use the following guide to reduce activity: [http://ubuntuforums.org/showthread.php?t=839998](http://ubuntuforums.org/showthread.php?t=839998)

Edit:
Wrong guide!

---

### Post by Jack Bonner on 2008-07-23
> **vor said:**
> A default Ubuntu install will write the disk more often than Windows however, it's not generally anything to worry about on a desktop machine.  If you find the noise of the increased disk activity annoying or it just makes you nervous, you could use the following guide to reduce activity: [http://ubuntuforums.org/showthread.php?t=839998](http://ubuntuforums.org/showthread.php?t=839998)

Edit:
Wrong guide!

Thanks muchly, the guide sorted everything out and eased my worrying a little.

Many thanks :)

---

