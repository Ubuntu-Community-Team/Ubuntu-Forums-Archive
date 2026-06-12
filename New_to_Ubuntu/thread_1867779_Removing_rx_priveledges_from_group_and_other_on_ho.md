---
title: "Removing rx priveledges from group and other on home directory"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by DrVladimirtzu on 2011-10-23
If I get rid of read and execute priveledges for group and other on my home directory, would there be any negative reprocussions?

---

### Post by cavh on 2011-10-23
I wouldn't do that. The permissions have been set that way for a reason, and things will break if you change them - just what will break I cannot say. See [https://help.ubuntu.com/community/FilePermissions]("https://help.ubuntu.com/community/FilePermissions"). 

Seriously, there's no reason to do this.

---

### Post by DrVladimirtzu on 2011-10-23
Aye, I had a feeling I should ask.  Especially after I noticed a lot of virtual users on /etc/passwd.  

I'd be curious to know exactly what it'd break and why, though.  And why /etc/passwd is like it is if anyone knows.

---

