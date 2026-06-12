---
title: "Fdupes"
date: 2017-10-08
forum: New to Ubuntu
---

### Post by mac187 on 2017-10-08
Hi, never used fdupes before, is it safe to run it on my system ? Just to clean up everything ? Like clean up all duplicates files and more.. ? 

Thanx

---

### Post by oldfred on 2017-10-08
I have run this, but it can take a while to scan entire system. 
It shows me many duplicates.

But I find I end up wanting to house clean an old folder as I had copied data to new location.
But fsdupes shows each file, and I sometimes select to delete wrong copy and still have old folder with a few files that then are not in new location.

---

### Post by mac187 on 2017-10-08
so the fdupes can possible delete imprtant files ??

---

### Post by oldfred on 2017-10-08
It shows you duplicates and you select which to delete. So unless you delete the wrong file, it is safe.

But of course you fully update your normal backup so you have all the old copies anyway.
       Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2368992](https://ubuntuforums.org/showthread.php?t=2368992)

---

### Post by HermanAB on 2017-10-09
I think it is best to convert duplicates into hard links.  That way, you dedup the filesystem without losing anything.

I use fslint to do that, but there are other tools available that do the same.

---

