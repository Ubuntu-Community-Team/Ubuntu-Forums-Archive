---
title: "mounting network drive like ftp://192.168....:21/ at boot"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by baybe1111 on 2008-10-11
Hi, I have an external drive which is connected to the network via a print/storage server. I can access it by typing [ftp://192.168](ftp://192.168) etc:21/ into nautilus. However I really want to mount it at boot up so I can use it more easily. What would be the easiest way to do this?

---

### Post by mejy on 2008-10-11
This feature is currently in flux a little due to architecture changes, but you can generally achieve what you want by chosing "Connect to Server" from the Places menu, filling in the server's details and checking "Add Bookmark".

---

### Post by airtonix on 2008-10-11
I'm digging up some links for you now.
the basics of fstab **: **[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

found this at : [http://ubuntuforums.org/showthread.php?t=203572](http://ubuntuforums.org/showthread.php?t=203572)
> 
what your looking for is curlftpfs. it is a FUSE extension, so you can mount ftp like any drive.
 some info on it here : [http://www.mypool.cn/develop/linux/mounting-ftp-host-to-local-directory-on-top-of-fuse/](http://www.mypool.cn/develop/linux/mounting-ftp-host-to-local-directory-on-top-of-fuse/)

a brief intro on usage in this guys post : [http://ubuntuforums.org/showpost.php?p=3821198&postcount=23](http://ubuntuforums.org/showpost.php?p=3821198&postcount=23)

---

### Post by iponeverything on 2008-10-11
Does it export the drive via NFS or SMB in addition to allowing ftp access?

You don't really "mount" drives via ftp.

---

