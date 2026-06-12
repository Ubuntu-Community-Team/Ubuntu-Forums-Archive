---
title: "Read Only File System Error Ubuntu 11.10"
date: 2012-04-29
forum: New to Ubuntu
---

### Post by Jugurtha on 2012-04-29
Hello everyone,

This is a solved issue, and this thread is just to record how it was ..

I think it was after an update. I tried to compile a C program, and I had this error. Everything I did, basically triggered this error.

I've looked different fora, I searched a lot.. and each solution proposed involved changing something that would trigger this error. (Goes the same for changing permissions, etc)

Tinkering with ```
fstab
```, would trigger this error.

sudo command would trigger it, etc...

So, I tried to boot in recovery mode and chose "drop root" and I basically got the same error.

Then, from the grub menu .. I tried "Previous Linux versions" and chose the oldest release in recovery mode .. Then drop root.. Then :

```
**fsck -As**
```The rest is basically just hitting "Y" to let it "repair" the file system.

Then rebooting and voilà :)

The rest is just updating and upgrading:

```
**sudo apt-get update**
```
```
**sudo apt-get upgrade**
```Maybe cleaning , etc..

That's it.

---

### Post by murtulasi on 2012-07-31
Hi,

Thanks for the steps. IT helped me today to solve the issue with oneiric.

Cheers

---

