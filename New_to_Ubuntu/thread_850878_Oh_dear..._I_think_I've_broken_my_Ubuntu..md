---
title: "Oh dear... I think I've broken my Ubuntu."
date: 2008-07-06
forum: New to Ubuntu
---

### Post by Dionikon on 2008-07-06
Ok, so I've spent the last 2 days messing with my Ubuntu box trying to get Asterisk working.  Frustrating experience thus far but I'm getting my head around it.

So...  how did I break my Ubuntu I hear you ask?

Well, while giving FreePBX a go I discovered that the www folder for my apache was unreadable through a browser on a different machine.  So I changed the permissions, recursively.... for my etc directory, so that everyone could read it (775).

So now I can't use sudo, and I can't get ssh working... I'm sure there's more that doesn't work but that's all I've found for now.

Is there a way I can easily fix this?  Or am I doomed?

ssh says: "Read from socket failed: Connection reset by peer"

and sudo says something about the mode not being correct, I can't remember now because I haven't checked it on the box itself.

---

### Post by sdennie on 2008-07-06
This is a fairly dire problem.  There are a number of things in /etc that really like to have (and should have) permissions set a certain way (as you've discovered with /etc/sudoers).  You might be able to set the important things back to original permissions but, the integrity of your system will always be in doubt unless you re-install.

---

### Post by brian_p on 2008-07-06
> **Dionikon said:**
> 
Is there a way I can easily fix this?  Or am I doomed?

A possible route:

Restore correct permissions to /etc/sudoers
Have the Ubuntu disk in /etc/apt/sources.list
Use sudo apt-get install --reinstall

---

### Post by Dionikon on 2008-07-06
I thought as much.

I'd like to try getting it fixed before reinstalling though, the box is my MythTV setup and is running perfectly, starting again from scratch would be a little annoying.

So I need to fix the sudo issue.  What permissions should be set on /etc/sudoers?

I'm guessing that my ssh issue is going to be caused by incorrect permissions aswell, any idea what I need to change to get that back aswell?  It's my main way of doing anything with this box other than watching television on it.  It's only display is a CRT TV so using it as a computer isn't very user friendly.

---

### Post by brian_p on 2008-07-06
> **Dionikon said:**
> So I need to fix the sudo issue.  What permissions should be set on /etc/sudoers?

```
-r--r----- 1 root root 325 2007-08-28 23:38 /etc/sudoers
```


[I'm guessing that my ssh issue is going to be caused by incorrect permissions aswell, any idea what I need to change to get that back aswell?  It's my main way of doing anything with this box other than watching television on it.  It's only display is a CRT TV so using it as a computer isn't very user friendly.[/QUOTE]

```
-rw-r--r-- 1 root root  132777 2007-03-05 16:38 moduli
-rw-r--r-- 1 root root    1424 2007-03-05 16:38 ssh_config
-rw-r--r-- 1 root root    1874 2008-02-15 22:36 sshd_config
-rw------- 1 root root     672 2008-05-15 00:06 ssh_host_dsa_key
-rw-r--r-- 1 root root     601 2008-05-15 00:06 ssh_host_dsa_key.pub
-rw------- 1 root root    1675 2008-05-15 00:06 ssh_host_rsa_key
-rw-r--r-- 1 root root     393 2008-05-15 00:06 ssh_host_rsa_key.pub

```

I'd back up /etc first to preserve any customisations you have made.

---

### Post by Dionikon on 2008-07-06
All working!

w00t!

Thanks guys!

---

### Post by Dionikon on 2008-07-08
Ok, I've discovered another directory that looks like it's causing issues.

mysql is being a bit strange.

could someone please do an ls -l on their /etc/mysql and /etc/mysql/conf.d and post the results?

looks like fixing this could be a long process of discovering issues one thing at a time.

Currently mysql is like this:
drwxrwxr-x 2 root root 4096 2008-06-23 23:40 conf.d
-rwxrwxr-x 1 root root  312 2008-05-14 21:48 debian.cnf
-rwxrwxr-x 1 root root 1198 2008-03-28 15:16 debian-start
-rwxrwxr-x 1 root root 3897 2008-03-28 15:16 my.cnf

and conf.d is:

-rwxrwxr-x 1 root root 31 2008-06-23 23:40 mythtv.cnf


Thanks. :)

---

