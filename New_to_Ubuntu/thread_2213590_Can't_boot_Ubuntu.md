---
title: "Can't boot Ubuntu"
date: 2014-03-27
forum: New to Ubuntu
---

### Post by Arascophi on 2014-03-27
I had Ubuntu 13.10 installed and running well.  I ran package manager, and was in the process of updating programs, and the computer froze, then shut down.  When I tried to start it up again, it would not do so.  It gave a message about a missing kernel, I am sorry, I did not write the message down, and no longer have it.  I tried to recover by running the live CD, and was not given the option to recover.  Since then, I have installed a clean copy of 13.10 alongside the old one, ran bootrepair and still no luck.  In running Gparted, I can see that I have:

dev/sda2 is the original Ubuntu that has all my stuff.
This is what shows up on fdisk:


Is there anything I can do?
  Thanks for all your help!

---

### Post by kc1di on 2014-03-27
did boot repair find the original install and make and entry for it?

---

### Post by Arascophi on 2014-03-27
No, boot repair did not find anything

---

### Post by kc1di on 2014-03-27
At this point then you should be able to see the partition from the old install with the file manager in the new one. copy what you can from the old to the new.

---

