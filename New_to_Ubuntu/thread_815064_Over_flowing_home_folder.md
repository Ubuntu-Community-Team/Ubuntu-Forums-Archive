---
title: "Over flowing /home folder"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by Horomancer on 2008-06-01
Hello there! New ubuntu user here.
My problem is that my /home folder is maxed out and i'm in need of more space. I have 2 hard drives in my computer, one 50gb the other 100gb, and when i first installed ubuntu I set the 50gb has the /home partition. I would have set the 100gb has /home and the other as everything else, but this gave me troubles when i tried to boot my system up.
Now when i use Disk Usage Analyzer I see that my /home is at 98% capacity and I still have 90+gb free on my other hard drive.
I've tried just saving things into another folder outside of /home or making a /home2 folder in root, but I guess i don't have write access and am not totaly sure this would be the best way to handle my situation.
Would i need to make another /home partition using fdisk or simular tool?

---

### Post by HalPomeranz on 2008-06-01
It's difficult to give you complete advice without knowing exactly how your system's disks are partitioned, but I think you were on the right track when trying to create the /home2 directory.  The trick is that you need root access to create the folder:

```

sudo mkdir /home2
sudu chown <yourusername> /home2

```

When sudo prompts you for a password, enter the password you use when you log into the system.  Substitute the username of your account for "<yourusername>" on the second line.

These commands should create a /home2 directory and make it owned by your regular user account.  That should allow you to save files in the /home2 directory in the future, without needing root privs.

---

### Post by Horomancer on 2008-06-01
That did it.
Thanks

---

