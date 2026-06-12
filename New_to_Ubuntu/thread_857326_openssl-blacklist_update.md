---
title: "openssl-blacklist update"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by movrshakr on 2008-07-12
Every so often, when I do updates that are offered, an openssl-blacklist update is part of the updates.  

When that is installed, is there anything else I need to do to "use it?"  Or, is it just a database of bad ssl hashes that is automatically used whenever ssl is used?

---

### Post by roquefilipe on 2008-07-13
there was a bug with the random generation of keys. 

You should update your system and generate new keys in every machine that you  admin.

---

### Post by movrshakr on 2008-07-13
That's somewhat inconvenient in that these blacklist updates have appeared several times.  So we have to go regenerate keys every time they come out?  Bummer--especially for the Windows machines, because you have to run them through the translator program in addition to the key generations.

---

### Post by achianese on 2008-07-13
As I understood it, the original update fixed the keygens, and at that point, all servers were required to generate new keys. The often-updated package openssl-blacklist is "to aid in detecting vulnerable certificates and keys."

Anyone who knows otherwise, please correct me.

see:
[http://www.linuxsecurity.com/content/view/138783](http://www.linuxsecurity.com/content/view/138783)

---

### Post by movrshakr on 2008-07-13
> **achianese said:**
> As I understood it, the original update fixed the keygens, and at that point, all servers were required to generate new keys. The often-updated package openssl-blacklist is "to aid in detecting vulnerable certificates and keys."
Anyone who knows otherwise, please correct me.
see:
[http://www.linuxsecurity.com/content/view/138783](http://www.linuxsecurity.com/content/view/138783)

I did generate new keys after the first update.

Second on the "Anyone who knows otherwise, please correct me."  I need to know whether to do it every time new ones come out.

---

