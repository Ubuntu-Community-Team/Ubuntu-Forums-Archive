---
title: "[SOLVED] Got a problem while creating a deb with deb creator."
date: 2008-07-29
forum: New to Ubuntu
---

### Post by cristo-father on 2008-07-29
Hi.
The file is [http://www.teeworlds.com/files/teeworlds-0.4.2-linux_x86_64.tar.gz]("http://www.teeworlds.com/files/teeworlds-0.4.2-linux_x86_64.tar.gz").
While in the process i get this error:
```
Unable to detect top source directory in the archive.
This should be something like <name>-<version>.
```
Any suggestions?
Thanks.

---

### Post by eightmillion on 2008-07-29
That archive contains no source. Perhaps you downloaded the wrong one.

Edit: That's the prebuilt x86_64 binary. The source is available [here.]("http://www.teeworlds.com/files/teeworlds-0.4.2-src.tar.gz")

---

### Post by cristo-father on 2008-07-29
Downloaded the source from here([http://www.teeworlds.com/?page=downloads&id=1137](http://www.teeworlds.com/?page=downloads&id=1137)) and i still have the same problem.

---

### Post by eightmillion on 2008-07-29
It looks like this program has specific build instructions and the source tar ball contains no build scripts. The instructions are [here.]("http://www.teeworlds.com/?page=docs&wiki=CompilingEverything")

---

### Post by cristo-father on 2008-07-29
Thanks. But i am still curious can i create a deb from the source? How?
Can i use deb creator or do i have to use another app?

---

### Post by eightmillion on 2008-07-29
I don't see any easy, automated way of creating a deb of teeworlds, but if you're determined you can always do it manually.

[Here]("http://thedarkmaster.wordpress.com/2008/05/24/how-to-create-manipulate-a-deb-file-of-a-compiled-application/") is a tutorial.

---

### Post by cristo-father on 2008-07-29
Thanks.

---

