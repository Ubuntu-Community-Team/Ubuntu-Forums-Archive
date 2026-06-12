---
title: "Problem with flash on 8.10"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by chirpilittle on 2008-11-11
I recently upgraded to ubuntu 8.10 and tried it out for the first time. Then I realised I needed to install flash player again.

I went to the synaptic package manager and uninstalled the old version of flash. Downloaded the new flash player ( .tar.gz ) from the Adobe site, but when I tried to install it gave me this error:

```
ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.
```

any ideas on how to fix it?

---

### Post by mapes12 on 2008-11-11
Downloading binaries can be hit and miss. I had a similar issue. I solved it by pointing Firefox to a site where I knew Flash would be required then let Firefox handle the package management. Close down then restart Firefox and it worked.

I would recommend abandoning the tar file you have downloaded until you have tried other automated options.

---

### Post by MasterSander on 2008-11-11
You probably downloaded the wrong file, you need a 64 bit version and not a 32 bit version

---

### Post by chirpilittle on 2008-11-11
> **mapes12 said:**
> Downloading binaries can be hit and miss. I had a similar issue. I solved it by pointing Firefox to a site where I knew Flash would be required then let Firefox handle the package management. Close down then restart Firefox and it worked.

I would recommend abandoning the tar file you have downloaded until you have tried other automated options.

I actually tried that, but it always directs me to the adobe site and instructs me to install flash manually

---

### Post by chirpilittle on 2008-11-11
> **MasterSander said:**
> You probably downloaded the wrong file, you need a 64 bit version and not a 32 bit version

Hmm... there isn't an option to download a 32 or 64 bit version. It's the same file for both

---

