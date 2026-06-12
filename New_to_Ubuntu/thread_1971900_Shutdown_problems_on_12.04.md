---
title: "Shutdown problems on 12.04"
date: 2012-05-03
forum: New to Ubuntu
---

### Post by johnlm on 2012-05-03
I have installed 12.04 on my notebook (Advent 4211c) which shows problems with shutdown.
The shutdown button on the top-right corner of the screen is missing. (I notice that it is present before I have logged in.) I have to resort to pressing the power button to close it down.
When I experimented with Mint I use to be able to install a seperate work around but I'm not sure if this is possible with Ubuntu 12.04. 
Any help appreciated
John
PS Apart from this 12.04 is great!!

---

### Post by anewguy on 2012-05-03
You could always do sudo shutdown -h now in a terminal window.  In the mean time, I'll look for a way to add it back in to the options.

Dave

---

### Post by gilgamesh.from.uruk on 2012-05-05
Same problem here.
sudo shutdown -h now
does not solve it.

---

### Post by anewguy on 2012-05-08
Does "sudo shutdown -P now" work?  The -h  from the previous is for halt, and works on some systems to also power them down.  The -P option should power down after shutdown.

---

### Post by CharlesA on 2012-05-08
> **anewguy said:**
> Does "sudo shutdown -P now" work?  The -h  from the previous is for halt, and works on some systems to also power them down.  The -P option should power down after shutdown.
That will probably fix it.

Precise broke the way I do shutdowns via "halt" with no arguments.

```
sudo halt -p
```

Should work too.

---

