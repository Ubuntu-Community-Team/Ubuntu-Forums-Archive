---
title: "What are these files?"
date: 2012-05-05
forum: New to Ubuntu
---

### Post by vasa1 on 2012-05-05
I'm seeing```
-rw-------  1 user user       0 Apr 29 23:09 .goutputstream-1M84CW
-rw-------  1 user user       0 May  5 13:09 .goutputstream-2DJZDW
-rw-------  1 user user       0 May  4 23:59 .goutputstream-6AMPDW
-rw-------  1 user user       0 May  3 13:28 .goutputstream-HN3PDW
-rw-------  1 user user       0 May  1 08:32 .goutputstream-PT56CW
-rw-------  1 user user       0 May  2 12:58 .goutputstream-SQLZDW
-rw-------  1 user user       0 May  1 13:03 .goutputstream-USQADW

```in my home folder. I don't recall seeing them in 11.04 or 11.10.

---

### Post by PaulW2U on 2012-05-05
It was discussed here - [http://ubuntuforums.org/showthread.php?t=1938825&page=1](http://ubuntuforums.org/showthread.php?t=1938825&page=1) - a quick Google search suggests that they're temporary files which should have been deleted.

---

### Post by vasa1 on 2012-05-05
> **PaulW2U said:**
> It was discussed here - [http://ubuntuforums.org/showthread.php?t=1938825&page=1](http://ubuntuforums.org/showthread.php?t=1938825&page=1) - a quick Google search suggests that they're temporary files which should have been deleted.

Oops! Thanks for the link. I'll request that this thread be deleted.

---

### Post by CharlesA on 2012-05-05
> **vasa1 said:**
> Oops! Thanks for the link. I'll request that this thread be deleted.
Marked it as solved as we don't delete threads.

---

### Post by alr1969 on 2012-05-06
Regarding all those .goutputstream-XXXXX showing up in the home folder as per this thread [http://ubuntuforums.org/showthread.p...utstream+files]("http://ubuntuforums.org/showthread.php?t=1938825&highlight=goutputstream+files") 

In my case those files stopped accumulating when I started logging out before shutting down or restarting. Seems like there is a process running that doesn't like being unceremoniously shut down :)

This is just guessing on my part.  I'm not very experienced in this stuff.

Hope this helps.

---

### Post by DGINSD on 2012-05-20
I've just been researching this on my machine and was pointed to this thread from this bug report [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/984785]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/984785")

Some posts there suggest that removing ubuntuone eliminates the issue, this combined with the above post #5 would kind of lead me to belive shutdown isn't handling U1 correctly, just a guess.

Shouldn't "shutdowns" first order of business be to log you out?

---

