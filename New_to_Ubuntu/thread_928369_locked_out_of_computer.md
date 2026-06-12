---
title: "locked out of computer"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by estanton on 2008-09-23
Today i noticed that I have lost administrative privileges for both logins on my system. In the login I frequently I use I can't access synaptic, when I click unlock in users-admin I get a message stating that the password can't be authenticated.
With the other login I can use sudo still but again I cannot unlock anything. Any way to edit one of these users back to having admin privileges?

---

### Post by jemate18 on 2008-09-23
> **estanton said:**
> Today i noticed that I have lost administrative privileges for both logins on my system. In the login I frequently I use I can't access synaptic, when I click unlock in users-admin I get a message stating that the password can't be authenticated.
With the other login I can use sudo still but again I cannot unlock anything. Any way to edit one of these users back to having admin privileges?

what is the output of

```
users
```

in the terminal?

---

### Post by Crafty Kisses on 2008-09-23
Try the following:
```
sudo -i
```
Enter your password, then see if you become root.

---

### Post by estanton on 2008-09-23
> **jemate18 said:**
> what is the output of

```
users
```

in the terminal?

```
eliot@ShuttleX:~$ users
eliot eliot
eliot@ShuttleX:~$ 
```

eliot is the login, my other login is admin

---

### Post by estanton on 2008-09-23
> **Codename said:**
> Try the following:
```
sudo -i
```
Enter your password, then see if you become root.

```
eliot@ShuttleX:~$ sudo -i
[sudo] password for eliot: 
eliot is not in the sudoers file.  This incident will be reported.

```

However with the other login I can get into root. What now? :P

---

### Post by nowshining on 2008-09-24
my guess is that u need to go into the account u can get root/sudo in and add urself ie: user elliot to the admin group.....i just forgot the exact sequence on howtwo..

---

### Post by Orange_and_Green on 2008-09-24
Hello Estanton,

logging in as admin, can you go to System->Administration->Users and Groups and unlock that? 'Cause if you can, it's easy: select eliot, click on Properties, select the "User Privileges" tab and enable "Administer the system".

Good luck:KS

---

### Post by estanton on 2008-09-24
> **Orange_and_Green said:**
> Hello Estanton,

logging in as admin, can you go to System->Administration->Users and Groups and unlock that? 'Cause if you can, it's easy: select eliot, click on Properties, select the "User Privileges" tab and enable "Administer the system".

Good luck:KS

No I can't unlock anything with either account, I just keep getting the same error. If I run users-admin from the terminal I get.
```
** (users-admin:11362): CRITICAL **: Did not receive a reply. Possible causes include: 
the remote application did not send a reply, the message bus security policy blocked the reply, 
the reply timeout expired, or the network connection was broken.
```

Any help guys? Since I'm locked out of my own system the only option I see at the moment is to scrub the system and start all over again. yech.

---

### Post by Orange_and_Green on 2008-09-24
I see...

Does it give you the same error if you do ```
gksudo users-admin
```?

If so, you could try reinstalling gnome-system-tools from synaptic and see if that changes anything. Do you have any, say, "non standard" security applications like Bastille or SELinux installed?

---

### Post by estanton on 2008-09-24
```

** (users-admin:11612): CRITICAL **: Unable to lookup session information for process '11612'
```
i don't have access to synaptic because I don't have admin privileges.
However it is up to date, rave a sudo apt from the terminal.
I'm running a pretty standard configuration nothing odd on the security side at all.

---

### Post by Orange_and_Green on 2008-09-24
> **estanton said:**
> i don't have access to synaptic because I don't have admin privileges.

you mean ```
gksu /usr/sbin/synaptic
```

won't work? (From your "admin" account, I mean.)

---

### Post by estanton on 2008-09-24
No difference, is there a way to edit those privileges manually?

---

### Post by Orange_and_Green on 2008-09-24
Well, yes, there is...

You could use the command "adduser" to add eliot to the admin group (or perhaps to add a new admin2 user that might just luckily enough be created with things working normally). See "man adduser" or [this link]("http://www.techotopia.com/index.php/Managing_Ubuntu_Linux_Users_and_Groups") for details.

If you want to edit the sudoers file you can do so with visudo but please be EXTREMELY careful if you do, and make a backup of any files you are about to edit...

[Visudo tutorial]("http://www.unixtutorial.org/2007/12/visudo-tutorial/")

It's hard to give you a good advice... Personally, I would likely try adding a new admin (possibly, if things are still ugly, even temporarily adding him to root group) and see if you can straighten things out from that account... But that's  only what I would do....

---

### Post by estanton on 2008-09-24
No dice, :(
This apparently creeps up in systems from time to time. I wonder what causes it. There's a few other reports in the forums about it.

---

