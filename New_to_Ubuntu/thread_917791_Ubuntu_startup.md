---
title: "Ubuntu startup"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by bob74 on 2008-09-12
My system works fine and up to a week or so ago I would receive periodically on switch on the message checking file system which I could swallow. But now every time I switch on I get the message "/dev/sda1 contains a file system with errors, check forced"
Short of re-installing Ubuntu which means the rigmarole of backing etc., is there any way of identifying and correcting the errors?
Any help would be gratefully received. I should mention after the checking completes everything proceeds normally.
Any help would be appreciated.
bob74

---

### Post by ronnielsen1 on 2008-09-12
It's telling you to run fsck manually. If it's forcing this it should give you a command line. Type fsck 

If it doesn't boot into safe mode

It should list the errors and ask you if you want to fix them

---

### Post by WRDN on 2008-09-12
There is a guide [here]("http://www.gatzet.com/fixing-file-system-on-ubuntu.html") for repairing the filesystem.

---

### Post by bob74 on 2008-09-13
Thank you both for the quick replies
The guide did the trick although strangely enough after the last sudo command no request was made for the new password!
Anyway that minor irritating problem is out the way.
Thanks once again, and sorry for the delay in coming back
bob74

---

### Post by akiratheoni on 2008-09-13
> **bob74 said:**
> Thank you both for the quick replies
The guide did the trick although strangely enough after the last sudo command no request was made for the new password!
Anyway that minor irritating problem is out the way.
Thanks once again, and sorry for the delay in coming back
bob74


That's probably because if you use sudo, you don't need to type in your password for about 15 minutes. Saves you on typing your password every time if you're doing some heavy sudo work.

---

