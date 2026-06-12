---
title: "Ownership of files.  give all to www-data"
date: 2006-11-09
forum: Programming Talk
---

### Post by haaglin on 2006-11-09
Hi.

I'm developing a CMS system, and i had some problem with mixed permission between me and www-data. I know why, so thats not my problem. But is there a security risk if i give all the ownership to www-data, or nobody? I would like to make an "update" feature, but i cant do that unless apache owns the files. I also use pclzip to unpack during installation, wich saves me a lot of time, but again, these files belong to apache, and if it's a security risk, then i cant do it.

---

### Post by haaglin on 2006-11-09
crap! I just made a script i uploaded to another webuser on the same host, and i was able to read all my config files with mysql connection details and other sensitive stuff of my web. Does anyone know a solution to this, without needing the host to do some changes?

Wihout apache owning the files, i cant use the "zip" way of installing, and i cant offer an update feature. to bad.

---

### Post by haaglin on 2006-11-10
*bump*

---

