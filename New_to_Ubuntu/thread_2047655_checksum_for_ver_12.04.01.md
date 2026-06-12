---
title: "checksum for ver 12.04.01"
date: 2012-08-25
forum: New to Ubuntu
---

### Post by Sudan on 2012-08-25
Hi, I'm a complete newbie.

I downloaded ubuntu desktop "ubuntu-12.04.1-desktop-i386.iso" 32 bit.  Please note this is a .1 "update" to 12.04.

Where can I find the checksum for this file?  I looked on page 

[https://help.ubuntu.com/community/UbuntuHashes#A12.04_LTS]("https://help.ubuntu.com/community/UbuntuHashes#A12.04_LTS")

But this web page does not contain an entry for file.  And this web page was last updated: UbuntuHashes (last edited 2012-05-04 01:38:57 by rocket2dmn). 

The 12.04.01 file was released 8-23-2012 
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule?action=show&redir%20ect=PreciseReleaseSchedule]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule?action=show&redir%20ect=PreciseReleaseSchedule")

Of course, does it really matter if I skip a hash check?  This is my first use of Ubuntu.  Help is appreciated.
Kelvin

---

### Post by Frogs Hair on 2012-08-25
I think you will have to wait until the hash page has been updated . I have had no problems with the eight Ubuntu ISOs I have burned and all were made at default speed using Windows or Ubuntu.

---

### Post by Krytarik on 2012-08-25
Please see the answer to the same question on AskUbuntu earlier today:

[http://askubuntu.com/questions/180228/where-can-i-get-the-hash-for-12-04-1-iso](http://askubuntu.com/questions/180228/where-can-i-get-the-hash-for-12-04-1-iso)

Regards.

---

### Post by Sudan on 2012-08-25
> **Krytarik said:**
> Please see the answer to the same question on AskUbuntu earlier today:

[http://askubuntu.com/questions/180228/where-can-i-get-the-hash-for-12-04-1-iso](http://askubuntu.com/questions/180228/where-can-i-get-the-hash-for-12-04-1-iso)

Regards.

Thanks.  I did go there, but the hash sum there does not match the one I calculated for downloaded file.  Per Frogs Hair, I'm just going to install it.

---

### Post by kansasnoob on 2012-08-25
[http://releases.ubuntu.com/12.04.1/MD5SUMS](http://releases.ubuntu.com/12.04.1/MD5SUMS)

```
682b0388d2a15bf9f38480b0eb4653f6 *ubuntu-12.04.1-alternate-amd64.iso
b4512076d85a1056f8a35f91702d81f9 *ubuntu-12.04.1-alternate-i386.iso
06472ddf11382c8da1f32e9487435c3d *ubuntu-12.04.1-desktop-amd64.iso
e235b63c02644e219b7bf3668f479c9e *ubuntu-12.04.1-desktop-i386.iso
a8c667e871f48f3a662f3fbf1c3ddb17 *ubuntu-12.04.1-server-amd64.iso
3daaa312833a7da1e85e2a02787e4b66 *ubuntu-12.04.1-server-i386.iso
1f2d0974eee10c54db4359ae85cdcc6c *ubuntu-12.04.1-wubi-amd64.tar.xz
a35494968d478f6bb9fe3349390b806c *ubuntu-12.04.1-wubi-i386.tar.xz
0cff2ad1e2092658eee8df589d56dfea *wubi.exe
```

---

### Post by Elfy on 2012-08-25
Bug on [https://help.ubuntu.com/community/UbuntuHashes#A12.04_LTS](https://help.ubuntu.com/community/UbuntuHashes#A12.04_LTS) to add 12.04.1 hashes confirmed. 

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/1041516](https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/1041516)

---

### Post by Sudan on 2012-08-26
> **kansasnoob said:**
> [http://releases.ubuntu.com/12.04.1/MD5SUMS](http://releases.ubuntu.com/12.04.1/MD5SUMS)

```
682b0388d2a15bf9f38480b0eb4653f6 *ubuntu-12.04.1-alternate-amd64.iso
b4512076d85a1056f8a35f91702d81f9 *ubuntu-12.04.1-alternate-i386.iso
06472ddf11382c8da1f32e9487435c3d *ubuntu-12.04.1-desktop-amd64.iso
e235b63c02644e219b7bf3668f479c9e *ubuntu-12.04.1-desktop-i386.iso
a8c667e871f48f3a662f3fbf1c3ddb17 *ubuntu-12.04.1-server-amd64.iso
3daaa312833a7da1e85e2a02787e4b66 *ubuntu-12.04.1-server-i386.iso
1f2d0974eee10c54db4359ae85cdcc6c *ubuntu-12.04.1-wubi-amd64.tar.xz
a35494968d478f6bb9fe3349390b806c *ubuntu-12.04.1-wubi-i386.tar.xz
0cff2ad1e2092658eee8df589d56dfea *wubi.exe
```

Thanks, my hash matched the one in your list.

---

