---
title: "Replacing Windows 8.1 on UEFI with Ubuntu"
date: 2014-04-21
forum: New to Ubuntu
---

### Post by keithcleaver2010 on 2014-04-21
Hi.

I'm returning to Ubuntu, and looking to install it on my PC, which currently has a Windows 8.1 UEFI partition, but I want to replace it with Ubuntu. Are there any special steps I need to go through before installing Ubuntu over it, or can I just do a straight installation?

---

### Post by WoodenWalker on 2014-04-21
If you plan to wipe the system, I would change to legacy boot (for sake of simplicity). Other than that, just make sure fast boot is off. Secure boot shouldn't be an issue, but you can turn it off anyways (if you like. After that, just format the system and install like normal. I personally setup my own layout when doing an install. I tend to do 3 primary partitions and one extended. 1 primary for /boot (I set at 1G of memory). I setup a partition for swap (mine is 6G but yours doesn't have to be). I setup a 10G partition for /tmp. Then the rest I allocate for /. But you can just do a normal install too. It's kinda up to what you want to do with your system.

---

### Post by keithcleaver2010 on 2014-04-21
Thanks for quick reply. The legacy boot settings are in the UEFI settings I assume, yes?

---

### Post by WoodenWalker on 2014-04-21
No problem, and yes. That is correct. The option will be UEFI/Legacy boot. Just switch it to legacy (this is the older boot option that most users are accustomed to). It will just make the install a bit less complicated. Lol

---

### Post by keithcleaver2010 on 2014-04-21
Ok, I'll try that. Thanks!

---

### Post by WoodenWalker on 2014-04-21
No problem. If it all works out for you, just mark this thread as [Solved]. If not, just post back or send me a PM and I will try my best to help with whatever issues you encounter.

---

### Post by keithcleaver2010 on 2014-04-21
I've marked it as solved as the query I had has been answered. I'm going to give it a try tomorrow, and if I encounter any issues, I'll PM you. Thanks again.

---

### Post by mörgæs on 2014-04-21
The SOLVED flag is set using Thread Tools.
Please keep troubleshooting in the open and not in PM's. It helps other people with the same problem.

---

### Post by WoodenWalker on 2014-04-21
Oh okay. And sorry, I was just telling him to PM me if he needed more help because it's easier than checking back on threads. I haven't figured out a way to setup notifications on here yet. Just joined the forums today.

---

### Post by oldfred on 2014-04-21
@WoodenWalker
I find it easier just to go to advance search and plug in oldfred. It gives the last 250 posts, but the one's with new posts are bolded.

       Guide to Forum features:
[http://ubuntuforums.org/showthread.php?t=2054969](http://ubuntuforums.org/showthread.php?t=2054969)
[http://ubuntuforums.org/showthread.php?t=1006656](http://ubuntuforums.org/showthread.php?t=1006656)
Forum do & don't
[http://ubuntuforums.org/showthread.php?t=885580](http://ubuntuforums.org/showthread.php?t=885580)

---

### Post by WoodenWalker on 2014-04-21
Thank you for the advice. I'll keep that in mind. :)

---

