---
title: "Installing perforce server (and client) on the same computer"
date: 2011-08-07
forum: Programming Talk
---

### Post by anche on 2011-08-07
Hello gurus

I'd like to use Perforce so I've followed this manual: [http://affy.blogspot.com/2007/09/setting-up-ubuntu-perforce-server.html](http://affy.blogspot.com/2007/09/setting-up-ubuntu-perforce-server.html)

I do not quite understand how I can manually start **p4d -d** as another user (**p4user** in my case). I am logged on as myself (an account that is a member of the **admin** group). I am supposed to start **p4d** as **p4user**, that is to say an account I have created that is not a member of the **admin** group.

There is no info about that in the manual mentioned above so I try **sudo -u p4user -g p4admin p4d -d**. There error I get is:[B]
Perforce server error:
    open for write: journal: Permission denied[/B]

Here is the output of **ls -al** **/var/log**
drwxr-xr-x  2 p4user            p4admin    4096 2011-08-07 12:49 p4logs

and **ls -al /var/log/p4logs/**

drwxr-xr-x  2 p4user p4admin 4096 2011-08-07 12:49 .
drwxr-xr-x 15 root   root    4096 2011-08-07 13:10 ..
-rw-r--r--  1 p4user p4admin 1508 2011-08-07 12:59 journal
-rw-r--r--  1 p4user p4admin  460 2011-08-07 12:59 p4err

What am I doing wrong?

Thanks in advance,
Anatoly.

---

