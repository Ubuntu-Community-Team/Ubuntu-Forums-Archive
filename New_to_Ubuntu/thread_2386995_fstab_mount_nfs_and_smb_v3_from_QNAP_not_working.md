---
title: "fstab mount nfs and smb v3 from QNAP not working"
date: 2018-03-13
forum: New to Ubuntu
---

### Post by Wojciech_Marusiak on 2018-03-13
Hi guys, 

I have latest Ubuntu [B]Linux ubuntu 4.13.0-36-generic #40-Ubuntu SMP Fri Feb 16 20:07:48 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

[/B]I have QNAP NAS where I have several shares via SMB v3 and NFS. I would like to mount those shares during boot time so they are always accessible.
SMB mount attempt
```
//192.168.255.117/Seriale /media/seriale cifs username=wojcieh,password=password,iocharset=utf8,sec=ntlm 0 0
//192.168.255.117/Movies /media/movies cifs username=wojcieh,password=password,iocharset=utf8,sec=ntlm 0 0
```

When I try to mount via sudo mount -a I receive following error.

```

Mar 13 11:38:55 ubuntu kernel: [942160.880516] CIFS VFS: Unable to select appropriate authentication method!
Mar 13 11:38:55 ubuntu kernel: [942160.880522] CIFS VFS: Send error in SessSetup = -22
Mar 13 11:38:55 ubuntu kernel: [942160.880845] CIFS VFS: cifs_mount failed w/return code = -22
Mar 13 11:38:55 ubuntu kernel: [942160.905738] CIFS VFS: Unable to select appropriate authentication method!
Mar 13 11:38:55 ubuntu kernel: [942160.905745] CIFS VFS: Send error in SessSetup = -22
Mar 13 11:38:55 ubuntu kernel: [942160.916577] CIFS VFS: cifs_mount failed w/return code = -22

```


When i try to mount via nfs, after mount -a it times out without error.

```

192.168.255.117:Seriale /media/seriale nfs username=wojcieh,password=password
192.168.255.117:Movies /media/movies nfs username=wojcieh,password=password

```

```

wojcieh@ubuntu:~$ sudo mount -a
/etc/host.conf: line 4: bad command `nospoof on'
mount.nfs: Connection timed out
mount.nfs: Connection timed out

```

What am I doing wrong?

---

### Post by Morbius1 on 2018-03-13
> CIFS VFS: Unable to select appropriate authentication method!
The 4.13 Linux kernel changed the default smb dialect for cifs from smb1 to smb3 which may be the issue here. Force it to the old default by adding **vers=1.0** to your list of options:
> //192.168.255.117/Seriale /media/seriale cifs username=wojcieh,password=password,iocharset=utf8,sec=ntlm[COLOR=#0000cd]**,vers=1.0**[/COLOR] 0 0

---

### Post by Wojciech_Marusiak on 2018-03-13
Hi Morbius1, 

QNAP serves SMB in v3.0.

---

### Post by #&amp;thj^% on 2018-03-13
Is QNAP listed in your /etc/fstab file?
Mounting an NFS share on Ubuntu: [https://wiki.qnap.com/wiki/Mounting_an_NFS_share_on_Ubuntu](https://wiki.qnap.com/wiki/Mounting_an_NFS_share_on_Ubuntu) Just for basics
And this is the method i used: [https://qnapsupport.net/qnap-uygulamalari/qnapi-kurdum-peki-nasil-qnapa-dosya-atacagim/linux-bilgisayarimdan-nasil-qnapa-ulasacagim/](https://qnapsupport.net/qnap-uygulamalari/qnapi-kurdum-peki-nasil-qnapa-dosya-atacagim/linux-bilgisayarimdan-nasil-qnapa-ulasacagim/)

---

### Post by Wojciech_Marusiak on 2018-03-13
This is what I get when I try to mount from command line.

```

wojcieh@ubuntu:~$ sudo mount -t nfs -o username=wojcieh,password=password 192.168.255.117:Seriale /media/seriale/
/etc/host.conf: line 4: bad command `nospoof on'
mount.nfs: an incorrect mount option was specified

```

---

### Post by #&amp;thj^% on 2018-03-13
So how dose your  /etc/host/ file now read?
"/etc/host.conf: line 4: bad command `nospoof on'" gives us a clue to look at.

---

### Post by Wojciech_Marusiak on 2018-03-14
Hello, 

Here is the /etc/host.conf file

```

# The "order" line is only used by old versions of the C library.
order hosts,bind
multi on
nospoof on

```

I commented out the nospoof on section but error is the same.

```
wojcieh@ubuntu:~$ sudo mount -t nfs -o username=wojcieh,password=password 192.168.255.117:Seriale /media/seriale/
mount.nfs: an incorrect mount option was specified
```

I tried as well without nfs as mount type.

```
wojcieh@ubuntu:~$ sudo mount -v -o username=wojcieh,password=password 192.168.255.117:Seriale /media/seriale/
mount.nfs: timeout set for Wed Mar 14 10:09:21 2018
mount.nfs: trying text-based options 'username=wojcieh,password=password ,vers=4.2,addr=192.168.255.117,clientaddr=192.168.255.125'
mount.nfs: mount(2): Invalid argument
mount.nfs: trying text-based options 'username=wojcieh,password=password =4.1,addr=192.168.255.117,clientaddr=192.168.255.125'
mount.nfs: mount(2): Invalid argument
mount.nfs: trying text-based options 'username=wojcieh,password=password ,vers=4.0,addr=192.168.255.117,clientaddr=192.168.255.125'
mount.nfs: mount(2): Invalid argument
mount.nfs: trying text-based options 'username=wojcieh,password=password ,addr=192.168.255.117'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: trying 192.168.255.117 prog 100003 vers 3 prot TCP port 2049
mount.nfs: prog 100005, trying vers=3, prot=17
mount.nfs: trying 192.168.255.117 prog 100005 vers 3 prot UDP port 30000
mount.nfs: mount(2): Invalid argument
mount.nfs: an incorrect mount option was specified
```

---

### Post by Morbius1 on 2018-03-14
> **Wojciech_Marusiak said:**
> Hi Morbius1, 

QNAP serves SMB in v3.0.
Then sec=ntlm makes no sense. Try removing it:
```
//192.168.255.117/Seriale /media/seriale cifs username=wojcieh,password=password,iocharset=utf8 0 0  
```

---

### Post by Wojciech_Marusiak on 2018-03-14
> **Morbius1 said:**
> Then sec=ntlm makes no sense. Try removing it:
```
//192.168.255.117/Seriale /media/seriale cifs username=wojcieh,password=password,iocharset=utf8 0 0  
```
It worked!

---

