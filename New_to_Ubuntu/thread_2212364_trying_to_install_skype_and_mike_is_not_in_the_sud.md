---
title: "trying to install skype and mike is not in the sudoers file.  This incident will be r"
date: 2014-03-20
forum: New to Ubuntu
---

### Post by bostoncab2 on 2014-03-20
mike is not in the sudoers file.  This incident will be reported.


mike is my username

---

### Post by deadflowr on 2014-03-20
You don't have any other users, do you?
Typically, first user made during install gets admin(sudo) rights automatically, but any made after won't and you have to give them the rights.

But you didn't add a new user, then the easiest way to add a user to the admin group, when no user has admin rights, is to reboot the system into the recovery mode(option).
[When you reboot, select the recovery mode in the grub menu]

In here go to root shell(or session;whatever it's called)
It's loaded as read-only so you need to change it to read-write
run
```
mount -o rw,remount /
```
this will reload the root shell read/write.
now simply run
adduser mike sudo
this will add mike to the sudo group, giving mike sudo(admin) rights.
the type exit and take whatever option says go to desktop or whatever it says.

---

### Post by bostoncab2 on 2014-03-20
Is there a way to list all users?

---

### Post by deadflowr on 2014-03-20
```
ls /home
```
is usually a simple and quick way, since it's most likely the users have a home folder.
more verbose would be
```
cat /etc/passwd | grep 100[0-9]
```
this should list all users with uid's from 1000 to 1009.
The typical default is 1000, and each subsequent user added goes higher, unless you set it, which I doubt you have or would.

I'm sure there is an easier way, but can't remember or think of it.

Someone else might though.

Edit: steeldriver reminded me, sudo not needed for passwd file.:p

---

### Post by steeldriver on 2014-03-20
Not really easier, but a similar way using getent

```
getent passwd uid 100{0..9}
```

Another tack (possibly more relevant to the case at hand?)

```
getent group sudo
```

to list the members of the sudo group

---

### Post by deadflowr on 2014-03-20
Yep, go with the getent approach.
Limits the use of sudo.
If you don't need to run as root, don't.

I'll leave my earlier post as is, as an option.
But I think it's better to use the getent.

---

### Post by steeldriver on 2014-03-20
^^^ bit of an aside, but you normally shouldn't need sudo to cat /etc/passwd (it's only the shadow files that are only root-readable by default)

```
$ ls -l /etc/{group,gshadow,passwd,shadow}
-rw-r--r-- 1 root root   1159 Mar 17 14:29 /etc/group
-rw-r----- 1 root shadow  975 Mar 17 14:29 /etc/gshadow
-rw-r--r-- 1 root root   2181 Mar 13 09:29 /etc/passwd
-rw-r----- 1 root shadow 1530 Mar 13 09:29 /etc/shadow

```

---

### Post by deadflowr on 2014-03-20
Thanks.
I edited my earlier post and removed the sudo.

I think I was mixing passwd and shadow.
Probably because they seemingly go hand in hand.

Also: alternatively, older installs might have the admin users in the group admin.
FWIW.
(But that would have been from like 10.04 and older, I think)
Someone who upgrades rather than does a fresh install might still be in the admin group.
(Instead of sudo)

---

### Post by bostoncab2 on 2014-03-21
ok so mike is the only user I have. Back to that pathway I guess.. weird this isnt my first buntu install and I have already had more issues with this one install than with all other previous installs combined... I am wondering if I should have donated the $2. 

Looking back at the instructions to give user mike sudo access so I can get skype installed.. you lost me...

Again I just want to use skype. I would prefer to use skype as this user and not install another user unless of course that gets me using my computer at optimum desired level faster?

How do I get skype installed again?

---

### Post by steeldriver on 2014-03-21
You're going to need to add user 'mike' back to the sudo group. Try

```
pkexec gpasswd --add mike sudo
```

If that doesn't work, follow the instructions here --> [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

