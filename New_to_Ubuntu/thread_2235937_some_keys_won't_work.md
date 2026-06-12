---
title: "some keys won't work"
date: 2014-07-23
forum: New to Ubuntu
---

### Post by lawlerj on 2014-07-23
Hi - total linux newby here. Also not overly technically skilled. So if this is a dumb question, my apologies in advance. 

I am running Ubuntu 12.04 on an ASUS 1015e. In the last few days, when I am using the laptop keyboard, the 1, 3, 5, 6, 8 and 9 keys have stopped working. In addition to this, the left shift and tab keys do not work. However, when I plug in an external wireless keyboard, there are no issues. I have run all updates, and have attempted to create another user profile - got the same result. 

Any ideas on how to fix this? Thanks!

---

### Post by Mark Phelps on 2014-07-23
It's either a hardware failure (contacts failing on the laptop keyboard) or it's a problem with the Linux kernel seeing the key presses.

To test out the first, I would burn a DVD or USB of a different Linux distro (you can get them from distrowatch.com for free), boot into that and see if the keys are still failing.

I would also try some older Ubuntu releases from the link (to get different kernel versions): [http://old-releases.ubuntu.com/releases/]("http://old-releases.ubuntu.com/releases/")

If the keys still fail across the different Linux versions, it's most likely a hardware failure -- and only replacing the keyboard would fix that.

---

### Post by ajgreeny on 2014-07-23
Also try running a live system of 12.04 (the one you probably used when installing?) to see if the problem still shows.

---

### Post by csuggs4 on 2014-08-05
I had a similar problem after waking my laptop from suspend.  I'm running Ubuntu 12.04, all up to date, on a System76 Gazelle Professional.  At least the following keys stopped working as expected: 1, s, -.  In fact, the 1 would toggle the cooling fan from high to silent.  

Simply restarting did not fix it.  I put the laptop back into suspend, woke it back up, and then the keyboard was working normally again.

---

