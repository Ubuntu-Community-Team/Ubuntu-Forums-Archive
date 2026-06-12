---
title: "A simple bash script question"
date: 2008-05-15
forum: Programming Talk
---

### Post by R0b on 2008-05-15
Hi, recently i created a new user un my box, using the command "useradd"

I noticed that the newly created user was present only in one group (himself), so i wanted to copy the groups of another user, which had more privileges.

Old user with a lot of groups :
```
root@ambulatorio:/home# groups robby
robby adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin

```

New user : 
```
root@ambulatorio:/home# groups ambulatorio
ambulatorio

```

I used the command "**usermod -G <group> <user>"** 
to add the new user to some groups.

doing this operation for every single group is a repetitive action, and the idea is to create a simple script that takes the the groups of one user (from a file) and copies to another.

I dumped to a file the groups of the first user 
```
#groups robby > groupList
```

but i don't know how to parse the elements of that file, and pass them directly to "**usermod -G <group> <user>**"

I know that there are a lot of ways for this problem, the one and the obvious (and the most stupid one) is to do it by hand

---

### Post by Majorix on 2008-05-15
If I were you I would backup the new user's files and then do a little more automated
[php]adduser #NOT useradd[/php]
It will ask you where you want your user to be a part of.

---

### Post by amingv on 2008-05-15
For the sake of learning, you could do

```
for i in $(cat groupList); do usermod -G -a $i <username>; done 
```

---

### Post by R0b on 2008-05-15
Thank you very much guys,
@amingv that's exactly what i searched for

many thanks again

---

