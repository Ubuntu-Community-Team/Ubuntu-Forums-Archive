---
title: "Problems with mounted items"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by fballem on 2008-05-18
I currently have the following code in /etc/fstab:

```
//[ipaddress]/media /home/[username]/Media-NAS cifs userid=[nasusername],password=[naspassword],uid=[username],iocharset=utf8,user 0 0
//[ipaddress]/[userprivatedrive] /home/[username]/Private-NAS cifs userid=[nasusername],password=[naspassword],uid=[username],iocharset=utf8,user 0 0

```

where:
[INDENT][ipaddress] is a numeric ip address (apparently a named server is not supported). The NAS device uses a small form of Windows Server (additional information may be found at: [http://www.lacie.com/ca/products/product.htm?pid=10843](http://www.lacie.com/ca/products/product.htm?pid=10843))
[username] is the username that is used on ubuntu
[nasusername] is the user name that is used on the NAS
[naspassword] is the password for the the user to access the NAS
[userprivatedrive] is the NAS share for the user's private files[/INDENT]

This code correctly mounts the two NAS shares and I have the access that I need (create, delete files, read-write access).

When I use the following:

```
//[ipaddress]/media /home/[username]/Media-NAS cifs credentials=/home/[username]/.NASPassword,uid=[username],iocharset=utf8,user 0 0
//[ipaddress]/[userprivatedrive] /home/[username]/Private-NAS cifs credentials=/home/[username]/.NASPassword,uid=[username],iocharset=utf8,user 0 0

```

.NASPassword is a two-line file containing the [nasusername] and [naspassword].

I get an error code 13 (Permission denied) when attempts are made to mount the device. I think the key is who owns .NASPassword file and what permission is given to users. For obvious reasons, I would like to get this solution working, so:

[LIST]
[*]Who should create the .NASPassword file (root, using gksudo gedit, or [username] using gedit)?
[*]What permissions need to be applied to the .NASPassword file?
[/LIST]

A second problem occurs when I shutdown/restart. As the system is shutting down, there are two messages produced:

[INDENT]CIFS VFS: Server not responding
CIF VFS: No response for CMD 50 MID 117[/INDENT]

I have been ignoring these and the system has been shutting down, but they are displayed for quite some time and do slow down the shutdown/restart.

Any help on either of these two problems would be much appreciated.

Many thanks,

---

### Post by EXCiD3 on 2008-05-18
I saw this in a configuration for samba shares in fstab:
```

//192.168.2.185/SVN /home/harris/SVN/ cifs nounix,uid=harris,gid=harris,file_mode=0777,dir_mode=0777 0 0
//192.168.2.185/MUSIC /home/harris/Music/ cifs nounix,uid=harris,gid=harris,file_mode=0777,dir_mode=0777 0 0
```
Do you think the dir_mode and file_mode would help?

No idea about those error messages so i can't help with your second problem.

---

### Post by fballem on 2008-05-27
thanks for the fixes, but I think the problem is with:

1) who (me or the superuser) sets up the NAScredentials file
2) the permissions that need to be in place for the NAScredentials file.

---

