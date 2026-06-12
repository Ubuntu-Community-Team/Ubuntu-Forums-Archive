---
title: "Restricted access to specific folders"
date: 2012-11-20
forum: New to Ubuntu
---

### Post by ENigma885 on 2012-11-20
I need to restrict access to specific folders in my HDD to specific persons.

**Features I want:**
1- It should be independent of the OS used; folders cannot be accessed even when booting to another OS using LiveCD or Windows or if the HDD has been attached somewhere else.
2- I need an easy and quick access to the users who have the right to access the folders; using password for example.

**Notes**:
- The size of the folders vary from small to huge, so full encryption is not an option as far as I can tell as the encryption/decryption process with large files is very time-consuming. (correct me if I'm wrong)

---

### Post by TheFu on 2012-11-20
There is no solution for the vague requirements provided.
* which OSes do you care about? The complete list with specific versions is needed.
* if you don't need Windows to access it locally, that does simplify things, otherwise, you are stuck with NTFS as the starting point, which is extremely limited.
* If you don't need to support multi-boot, then the problem becomes much easier. 
* If all access can be over the network, then the issue becomes much easier again.

The best answer I can see is to use a network mount and encrypt the file system to prevent access from other systems or boot. Then share with NFS over Kerberos.  Using normal userid/groupids should provide the restrictions you want ... provided you don't need direct non-Linux access.

Full encryption of the file system is not time consuming in the way you think it is.

**Quick** **and easy** access is the enemy of **secure access **almost always.

For example, the remote access could be provided by WebDAV and keep the files stored on an encrypted file system. The end users over the network would not be able to tell anything about the encryption, since to their computers, it would appear as decrypted in the HTTPS webdav access.  OTOH, webDAV is known to have security issues under most operating systems.  It is quick and easy, but not as secure as you seem to want.

---

