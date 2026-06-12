---
title: "Errors installing Ubuntu - a cautionary tale"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by Paddy Landau on 2008-06-02
This post is really a cautionary tale to newbies (like myself!) who have troubles with installing Ubuntu or variants from a downloaded CD.

I was having problems installing Ubuntu. (I had tried WUBI, successfully, and now was doing a native installation.)

On searching through this forum, I noticed frequent admonitions to check the MD5 and the CD integrity. And most of the newbies that I read either ignored or argued with that.

Here is what happened to me (as I found out when I went back to follow the instructions):


[LIST=1]
[*]The mirror closest to me had a faulty download, which although a valid ISO file, failed the MD5 check sum. I wouldn't have known otherwise that it had a problem. I downloaded from a different mirror, and it was valid.
[*]I created the disk on a CD RW (twice), and once on a CD-R. All three times the CDs failed the CD Integrity Check. "Check finished: errors found in 1 files!" That's when I realised that both my CDs were faulty.
[*]Finally, I used a new CD-RW, and it worked. Phew!
[/LIST]

So. If I had left out either the [MD5 check]("https://help.ubuntu.com/community/HowToMD5SUM") or the [CD Integrity Check]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck"), I would still be sitting here scratching my head.

---

### Post by Paqman on 2008-06-02
Good tip. Sometimes a few extra minutes of prep can save you a lot of time later.

We used to have a saying in the military: "Proper Prior Preparation Prevents P!$$ Poor Performance"

---

