---
title: "external network hardrive"
date: 2012-03-13
forum: New to Ubuntu
---

### Post by goodgriefpenfold on 2012-03-13
Good morning,

I have recently transfered from windows and i'm loving Ubuntu. Starting to get my teeth stuck into command line etc...

I operated a network hardrive whilst on windows which is a mybookworld nas. I can find it on my network but only have limited accessability to it even when i enter my passwords. I can play things from it but can not save onto it. Something about it not being mounted?

Any help would be greatly appreciated.

Regards

Ryan

---

### Post by aeiah on 2012-03-13
have you mounted it? try mounting it from the command line. it looks like NFS is disabled on that kind of nas for some weird reason, so i presume you're going in through samba

---

### Post by goodgriefpenfold on 2012-03-13
Hello [aeiah,]("http://ubuntuforums.org/member.php?u=71962")

Thanks for taking the time.

The drive is on my network from when i used it on windows.

Now that i am on ubuntu i can go into my folder, look at network and i can then see it. When i click on it it lets me open it and play music from it etc... but iw will not let me store anything new on it from ubuntu.

my questions are...what is mounting? How do I do it? and lastly what is samba and what do you mean going in throuh it?

Thanks

---

### Post by goodgriefpenfold on 2012-03-13
Ahhhhh,

If anybody is having the same problem. Problem solved. just folow this thread

[http://ubuntuforums.org/showthread.php?t=1527793](http://ubuntuforums.org/showthread.php?t=1527793)

---

### Post by Paqman on 2012-03-13
> **goodgriefpenfold said:**
> Ahhhhh,

If anybody is having the same problem. Problem solved. just folow this thread

[http://ubuntuforums.org/showthread.php?t=1527793](http://ubuntuforums.org/showthread.php?t=1527793)

I would go a bit further than that. You can have it mount automatically at boot by adding an entry to /etc/fstab:

[Mount SMB shares permanently](http://ubuntuforums.org/showthread.php?t=288534)

---

