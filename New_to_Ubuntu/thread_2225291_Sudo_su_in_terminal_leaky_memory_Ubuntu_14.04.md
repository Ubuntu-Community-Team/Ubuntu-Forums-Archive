---
title: "Sudo su in terminal leaky memory Ubuntu 14.04"
date: 2014-05-20
forum: New to Ubuntu
---

### Post by johan-t on 2014-05-20
Hi, I had a problem where if I put in a sudo command it come's up saying this
```

no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
```

so, I looked around on the web and ended up with this website: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1311353](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1311353)
it's solution was to put this command into terminal: ```
sudo apt-get remove libpam-smbpass
```
That fixed my problem but I was curious, what was it that I uninstalled?, and was it important?


Thanks, Johan

---

### Post by ian-weisser on 2014-05-23
```
$ apt-cache show libpam-smbpass
...
Description-en: pluggable authentication module for Samba
 This is a module for PAM that enables a system administrator to migrate
 user passwords from the Unix password database to the SMB password
 database as used by Samba, and to subsequently keep the two databases in
 sync.  Unlike other solutions, it does this without needing users to log
 in to Samba using cleartext passwords, or requiring them to change their
 existing passwords.
...

```
It's the package the synchronizes your samba network-file-sharing password to your normal everyday login password.
If you don't run a samba server, or if you don't use samba to share files across the network, then you may likely never miss it.

---

### Post by johan-t on 2014-05-25
Thanks for the reply :D

---

### Post by claracc on 2014-05-25
If you have got a satisfactory answer, please, mark the thread as solved with thread tools menu in the upper right part of the page.

Thanks

---

### Post by nquare on 2014-06-09
Hi,
I have a HP Microserver N40L and on a fresh installation of Ubuntu Server 14.04 LTS i get the same Leaking Memory Problem.
Because im new using Ubuntu Server, can please someone please help me on this and respond to 3 simple questions i have:
1- Besides removing "libpam-smbpass" is there any other solution for this problem?
2- Until Ubuntu team releases a fix / update for this, can i still use Ubuntu Server 14.04 LTS, without problems? How does this memory leaking problem affects my system?
3- On the installation process i choose to install Samba. If i don't install Samba will the Leaking Memory problem still happen?
Thanks

---

### Post by samrishah on 2015-03-11
Hi,

The recommendation on AskUbuntu works for me.  Give it a try.

[http://askubuntu.com/questions/477002/loadparm-c4864-leaking-memory](http://askubuntu.com/questions/477002/loadparm-c4864-leaking-memory)

---

### Post by capscrew on 2015-03-12
> **samrishah said:**
> Hi,

The recommendation on AskUbuntu works for me.  Give it a try.

[http://askubuntu.com/questions/477002/loadparm-c4864-leaking-memory](http://askubuntu.com/questions/477002/loadparm-c4864-leaking-memory)

The problem is really not addressed properly with that answer.

How did you install Samba?  By that I mean did you install by selecting **[*] Samba** on the server install menu or did you install the package *samba* from the command line with APT (sudo apt-get install samba).

How are you using Samba?  Are you using Samba as a "standalone" file server?  Or are you using Samba as a Domain Controller (DC) and managing users and groups and machines.?  You should not use a Samba v4 install to do both file serving and user management at this time.

---

