---
title: "Could not startup kstartupconfig error at login - partition problem?"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by TMcKSmith on 2008-04-27
I just installed Hardy Heron via a fresh install from a disc.  My previous setup had a 10GB partition for the OS, and an 80GB partition for my files, which was mounted at my home directory.  I thought that if I just kept the 80GB partition and formatted/installed Hardy on the 10GB, things would go smoothly - guess I was wrong.  I mounted the new 10GB partition on "/" - was that wrong?  It seemed to create a whole new home directory on the 10GB parition, and my old files are now in media/disk/thomas.  

So then I got the idea to just set my "HOME" directory as media/disk/thomas (is this a good thought?).  So I did that, restarted and now when I go to login it says:

"Could not startup kstartupconfig.  Check your installation" and then takes me back to the login screen.

Please help!  Thank you.

---

### Post by TMcKSmith on 2008-04-27
bump

Okay, so to fix my first problem I had to edit the /etc/passwd file and remove the /media/disk/thomas reference and changed it back to /home/thomas.  

Now I can login.

However, now I'm looking for a solution to fix my partition confusion.  Is there an easy way to fix this?  Clearly I just set it up incorrectly when I installed - should I re-install?  What should I do to set this up correctly?  Thank you

---

### Post by TMcKSmith on 2008-04-27
edit:  topic title updated

---

