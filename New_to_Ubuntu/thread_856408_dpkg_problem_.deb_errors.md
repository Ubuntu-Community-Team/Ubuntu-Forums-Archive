---
title: "dpkg problem .deb errors?"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by Barnetto on 2008-07-11
Finally got my internet to work on laptop and desktop after months of trying! 

Now have another problem. Anytihng I try to install (.deb packages) I get this error message:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: Couldn't rebuild package cache

```

and this error massage in update manger, add/remove and synaptic:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.



Anyone know how to fix this? Something to do with Debian? Possible to reinstall the debian?


And on another note now that I have finally got onto ubuntu with internet I am never gonig back to XP. New happy member of the Ubuntu Community! 



Barnetto

---

### Post by avtolle on 2008-07-11
From the CLI (Terminal, accessed by Applications>>Accessories>>Terminal) enter the following```
sudo dpkg --configure -a
```type in your password (you will have no visual feedback of it) press Enter, and let it do its thing. Any error messages, post them here for review.

---

### Post by damis648 on 2008-07-11
> **Barnetto said:**
> Finally got my internet to work on laptop and desktop after months of trying! 

Now have another problem. Anytihng I try to install (.deb packages) I get this error message:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: Couldn't rebuild package cache

```

and this error massage in update manger, add/remove and synaptic:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.



Anyone know how to fix this? Something to do with Debian? Possible to reinstall the debian?


And on another note now that I have finally got onto ubuntu with internet I am never gonig back to XP. New happy member of the Ubuntu Community! 



Barnetto

Debian is the base of Ubuntu... it is not just a reinstallable package. To solve this, do as the error message tells you: in terminal,
```
dpkg --configure -a
```
and if that does not work,
```
sudo dpkg --configure -a
```
PS. Welcome to the community!

---

### Post by Barnetto on 2008-07-11
ah noobish mistake?
I take it that dpkg is the package installer?

Barnetto

---

### Post by damis648 on 2008-07-11
> **Barnetto said:**
> ah noobish mistake?
I take it that dpkg is the package installer?

Barnetto

Yep. Apt and synaptic are frontends.

---

