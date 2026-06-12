---
title: "Hardy Heron install problems"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by jacquelinec on 2008-06-12
I installed the new release and the darned thing shuts down during boot up. It refuses to cooperate and I'm resorting to wild pounding of F12 then random changes. 

I don't know how to replicate the problem or the "fix" but it even shuts OFF when I've tried to leave it on. 

also bookmarks fail.

Thanks in advance.
Jacqueline

---

### Post by gr4nf on 2008-06-12
When it boots, does it give you an error message? What is the message?

---

### Post by billgoldberg on 2008-06-12
The download might have gotten corrupted.

Download the iso again, [check the md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") after you downloaded it, then burn at a low speed (2x or 4x speed).

Reinstall.

---

### Post by impert on 2008-06-12
Are you using an AMD 64 machine by any chance?
If so, booting with pci=nomsi in the boot options is supposed to work.

---

