---
title: "&quot;* winbind is not running&quot;"
date: 2011-10-20
forum: New to Ubuntu
---

### Post by dementech on 2011-10-20
Hi,

Need some help please.

I have built an ubuntu 10.10 64 server, and I'm trying to get samba/winbind integrated with my W2K3 AD.

The box will be used as a new backup server and will not be joined to the domain; the /etc/samba/smb.conf file from the old backup server has been copied over.

samba appears to be running:
mec@ubuntu:~$ sudo service smbd status
smbd start/running, process 1100

testparm -s /etc/samba/smb.conf reported the file was OK.

but winbind will not start.
mec@ubuntu:~$ service winbind status
 * winbind is not running

Of course I have tried stopping/restarting the services but that changes nothing.

I am new to this and would appreciate some good help; what the heck am I missing?

Thanks for your help.

---

### Post by dementech on 2011-10-20
SOLVED - I figured it out; some other poor newbie might run in to this so I want to let you know what the deal was.

We're using this backup server to rsync files from Windows Server shares, and my manager set the old one up; unfortunately, he doesn't have a penchant for sharing details.

I did not know that the Ubuntu box had to be joined to the domain (i thought samba took care of that), again, I am a newbie.

After I did "sudo net ads join -U administrator" and provided the domain administrators pwd, and rebooted the Ubuntu box, I was able to see winbind running and wbinfo -u gave AD user info.

---

### Post by 2F4U on 2011-10-20
Maybe this helps

[http://samba.org/samba/docs/man/Samba-HOWTO-Collection/winbind.html](http://samba.org/samba/docs/man/Samba-HOWTO-Collection/winbind.html)

---

