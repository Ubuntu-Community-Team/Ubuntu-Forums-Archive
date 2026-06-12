---
title: "xbmc - Update librtmp"
date: 2014-03-15
forum: New to Ubuntu
---

### Post by miguelmalheiro17 on 2014-03-15
Hello, how can I update xbmc's librtmp? I already downloaded the file, and searched for it in explorer but the only librtmp I found was in a steam folder.

[http://wiki.xbmc.org/index.php?title=HOW-TO:Update_librtmp](http://wiki.xbmc.org/index.php?title=HOW-TO:Update_librtmp)

I'm using ubuntu 13.10 64-bit

Thanks in advance

---

### Post by matt_symes on 2014-03-15
Hi

Welcome to the forums :)

> **miguelmalheiro17 said:**
> Hello, how can I update xbmc's librtmp? I already downloaded the file, and searched for it in explorer but the only librtmp I found was in a steam folder.

[http://wiki.xbmc.org/index.php?title=HOW-TO:Update_librtmp](http://wiki.xbmc.org/index.php?title=HOW-TO:Update_librtmp)

I'm using ubuntu 13.10 64-bit

Thanks in advance

Can i ask, why do you want to update librtmp ?

On my 64 bit install, i have a copy of librtmp here.

```
matthew-S206:/home/matthew % ls -l $(locate librtmp.so.0)
-rw-r--r-- 1 root root 105696 May  2  2013 **/usr/lib/x86_64-linux-gnu/librtmp.so.0**
matthew-S206:/home/matthew %
```

Do you not have the same file ?

You should just be able to update this file and (i assume) xbmc will use it.

Did you install it from the PPA or from the repository ?

Kind regards

---

### Post by miguelmalheiro17 on 2014-03-15
Thank you for the warm welcome and answer.
I installed xbmc from the stable build ppa.
I'm trying to update librmtp because a video addon reported that it had to be updated.

Yes thank you very much, I think this is the directory to file. I've backed up the original, just in case. And for now the addon is working properly.

King regards, and again, thank you very much.

---

### Post by njr2 on 2015-02-12
Hello miguelmalheiro17,

I am new on Ubuntu, and I would like to update my 
librtmp.so.0

on Kodi but I don`t know how.

If you can help me, would be great.

My Ubuntu version is 14.10 x64.

Thank you "obrigado"

---

