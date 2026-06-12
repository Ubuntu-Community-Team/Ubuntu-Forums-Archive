---
title: "[SOLVED] accidentally deleted my administrator user!"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by macvr on 2008-08-17
hi, i'm a noob

when i was trying to remove another user account i accidentally deleted my main administrator account, which i'm using now.

when i closed the users and groups window and re opened it again my administrator user name is present in the list along with root.

now if i log out will my administrator account be deleted?

 how do i recover my user account?

---

### Post by DGortze380 on 2008-08-17
> **macvr said:**
> hi, i'm a noob

when i was trying to remove another user account i accidentally deleted my main administrator account, which i'm using now.

when i closed the users and groups window and re opened it again my administrator user name is present in the list along with root.

now if i log out will my administrator account be deleted?

 how do i recover my user account?

The 'official' recommendation would be to create a new user account with full sudo privileges so you still gain access to the system to fix it. There is another way I would do it, but I can't express it here.  I would also backup your home directory while you still can.

---

### Post by macvr on 2008-08-18
anyone has a solution to _recover my account..._

i'm scared to even shutdown, wondering if ill be able to log in again!!!

---

### Post by hyper_ch on 2008-08-18
ok, calm down... if you have a second computer it's fairly easy (you can look things up). If you don't have a second computer print this out

First of all, we need to know if the user still exists. Run
```

cat /etc/passwd | grep USER

```
where USER is your username.
you should get something like this:
```

USER:x:1000:1000:USERNAME:/home/USER:/bin/bash

```

If you get that, then your user is still there. If not, then you need to add it.

if the user is there, check in what groups the user is:
```

cat /etc/group | grep USER

```
You should get this:
```

adm:x:4:USER
dialout:x:20:USER
cdrom:x:24:USER
floppy:x:25:USER
audio:x:29:USER
dip:x:30:USER
video:x:44:USER
plugdev:x:46:USER
lpadmin:x:109:USER
admin:x:114:USER
USER:x:1000:

```

If you get that, you are ok.

If not, then we either need to add the new user and/or add groups.

Add new user:

(1) Reboot and select recovery mode
--> this will start the computer in the command line and you will be root

(2) Add your user (again)
```

adduser USER

```
where USER is your desired username

(3) To set permissions right we set again the user to UID 1000
```

nano /etc/passwd

```
and alter
```

USER:x:YYYY:ZZZZ:USERNAME:/home/USER:/bin/bash

```
to
```

USER:x:1000:1000:USERNAME:/home/USER:/bin/bash

```
So UID and (primary) GID are 1000.

Adding the user to the (normal) groups:
(1) Boot into recovery mode (if you are not there yet)

(2) Run:
```

useradd -G adm,dialout,cdrom,floppy,audio,dip,video,plugdev,lpadmin,admin USER

```

Now you can reboot into normal mode and you should be "admin" again who can use sudo.

Before you alter the groups and stuff through command line, check if you are already in those groups and if the user still exists.

---

### Post by macvr on 2008-08-18
> **hyper_ch said:**
> 
First of all, we need to know if the user still exists. Run
```

cat /etc/passwd | grep USER

```
where USER is your username.
you should get something like this:
```

USER:x:1000:1000:USERNAME:/home/USER:/bin/bash

```

If you get that, then your user is still there. If not, then you need to add it.
i got this

```
_USER_:x:1000:1000:_USER_,,,,:/home/_USER_:/bin/bash
```

i have the extra ",,,," 
is that ok?

EDIT: i just checked the users and groups menu> when i'm asked to unlock my i'm displayed as USERNAME_,,,,_(USER)
so i guess the ",,,," would be ok?

> **hyper_ch said:**
> if the user is there, check in what groups the user is:
```

cat group | grep USER

```

```
cat: group: No such file or directory
```

this is what i got for the group check, so i guess the group is missing?


i should just start with this? no need the previous step, right?

> **hyper_ch said:**
> Adding the user to the (normal) groups:
(1) Boot into recovery mode (if you are not there yet)

(2) Run:
```

useradd -G adm,dialout,cdrom,floppy,audio,dip,video,plugdev,lpadmin,admin USER

```

Now you can reboot into normal mode and you should be "admin" again who can use sudo.

Before you alter the groups and stuff through command line, check if you are already in those groups and if the user still exists.

this check u mention in the last line, is the one i have done above enough, or do i have to check some where else also?

[i know u have given a very well explained procedure, but i just wanted to make sure i dont mess up further!]

so my doubts are just
1-if the extra ",,,," is a problem
2-i just have to do the_ Adding the user to the (normal) groups:_ part
3-will my old password work?

---

### Post by Elfy on 2008-08-18
Change  cat group | grep USER to
cat /etc/group | grep USER

---

### Post by macvr on 2008-08-18
> **forestpixie said:**
> Change  cat group | grep USER to
cat /etc/group | grep USER

ok when i do this i get the 
```

adm:x:4:USER
dialout:x:20:USER
cdrom:x:24:USER
floppy:x:25:USER
audio:x:29:_pulse,_USER
dip:x:30:USER
video:x:44:USER
plugdev:x:46:USER
lpadmin:x:109:USER
admin:x:_115_:USER
USER:x:1000:_user_
```

i have underlined the difference between mine and what Hyper_ch has given

now since i have got this does it mean i dont have to make any changes and my user account is safe?
do those differences matter?

---

### Post by hyper_ch on 2008-08-18
your USER exists and he's a member of the admin (and several other groups). So you're safe. No need to change.

---

### Post by macvr on 2008-08-18
> **hyper_ch said:**
> your USER exists and he's a member of the admin (and several other groups). So you're safe. No need to change.
oh thank goodness!!! thank you hyper_ch and forestpixie

@hyper_ch> thank u , that post was was written brilliantly, maybe u could just copy paste the post and leave it in the tutorials & tricks section,was a really good impressive one

---

### Post by macvr on 2008-08-18
finally braved a log out[after taking backups]
>>> and no probs, everything works fine

---

