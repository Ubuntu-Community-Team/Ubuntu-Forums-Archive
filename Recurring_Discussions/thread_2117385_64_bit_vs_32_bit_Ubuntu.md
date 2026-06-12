---
title: "64 bit vs 32 bit Ubuntu"
date: 2013-02-18
forum: Recurring Discussions
---

### Post by n4pgw on 2013-02-18
I just wanted to share a little something I learned about the difference between 32 bit and 64 bit Ubuntu.

The most commonly known issue is RAM addressing.  If a computer uses more than 4GB of RAM, it is possible that only part of it can be used with 32 bit Ubuntu.  

However, I discovered something else.  With 32 bit Ubuntu, I found my self limited to moving and copying files under 4GB in size.  I had an 8GB file on a drive that I was unable to move before I installed the 64 bit Ubuntu.  

I was using Ubuntu 10.04 LTS when I discovered these differences.

---

### Post by albandy on 2013-02-18
> **n4pgw said:**
> I just wanted to share a little something I learned about the difference between 32 bit and 64 bit Ubuntu.

The most commonly known issue is RAM addressing.  If a computer uses more than 4GB of RAM, it is possible that only part of it can be used with 32 bit Ubuntu.  

However, I discovered something else.  With 32 bit Ubuntu, I found my self limited to moving and copying files under 4GB in size.  I had an 8GB file on a drive that I was unable to move before I installed the 64 bit Ubuntu.  

I was using Ubuntu 10.04 LTS when I discovered these differences.

32 bit versions of ubuntu can map more than 4GB of RAM using the pae extension (simply ensure you're using a pae kernel).

I've no problems to move or copy files greater than 20GB in my 32 bit systems, maybe you're problem was a filesystem problem.

Were you triying to copy these files to a Fat32 partition?

---

### Post by 3rdalbum on 2013-02-18
> **n4pgw said:**
> I just wanted to share a little something I learned about the difference between 32 bit and 64 bit Ubuntu.

The most commonly known issue is RAM addressing.  If a computer uses more than 4GB of RAM, it is possible that only part of it can be used with 32 bit Ubuntu.  

True, but 32-bit Ubuntu can be extended with the PAE kernel. Technically, this gives you a 36-bit kernel running 32-bit programs. In fact, doesn't this run by default these days?

> However, I discovered something else.  With 32 bit Ubuntu, I found my self limited to moving and copying files under 4GB in size.  I had an 8GB file on a drive that I was unable to move before I installed the 64 bit Ubuntu. 

This isn't actually true. 32-bit Ubuntu has no problems addressing files up to their maximum size allowed by the filesystem, regardless of whether this can be addressed by 32-bit numbers or not. That's why you can copy DVD ISOs on 32-bit Ubuntu; these are typically over 4 GiB in size.

Sounds like you were trying to copy your 8 GB file to a Fat32-formatted drive; the copy will conk out after 4GB because of limitations in the filesystem itself. Even 64-bit Ubuntu won't copy more than 4 GB in a single file to a Fat32 disk.

---

### Post by Paqman on 2013-02-18
> **3rdalbum said:**
> In fact, doesn't this run by default these days?


Yup.

---

### Post by codemaniac on 2013-02-18
Thread moved to "Recurring Discussions".

---

