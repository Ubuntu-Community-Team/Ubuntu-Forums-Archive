---
title: "Partiton Restriction Access (plugdev?)"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by moshazat on 2008-05-06
Hello,

My machine is dual boot of Wndows XP and ubuntu 7.10..
When im using ubuntu, on the desktop it will appear the other volume that have in the hd, and for my machine is partiton "Windows XP" which is located at hda1...

My question is ;
Can i restricted an access or permission to this other volume, so that when i use for example guest account in ubuntu it will restrict me from changing or create or copy any file from or to the windows xp volume? i dun want to unmount it, i just want to restrict on how certain account i created can do with this "Windows XP" volume..

hurm

---

### Post by subzero316 on 2008-05-06
Use the  commands according to your preferneces

chmod
and
chown

you can configure that

---

### Post by moshazat on 2008-05-06
i never heard of that, and sory im not mention that im new with ubuntu..
how to use that? 

thanx for quick reply

---

### Post by subzero316 on 2008-05-07
chmod sets the permissions

400 read by owner
040 read by group
004 read by anybody (other)
200 write by owner
020 write by group
002 write by anybody
100 execute by owner
010 execute by group
001 execute by anybody

eg:

```
chmod 644 file.htm
```

This gives the file read/write by the owner and only read by everyone else (-rw-r--r--).

---

### Post by subzero316 on 2008-05-07
To know about the command see the Community docs or google it 
or man <command>

eg:
```
man chmod
```
```
man chown
```

---

### Post by MaindotC on 2008-05-07
Can you check out the manual page and tell us if you have any questions after that?  You can view the manual page by typing in a command prompt:

```

man chmod

```

to change the read, write, and execution permissions or

```


man chown


```

to change who has ownership of the partition.

---

### Post by moshazat on 2008-05-07
owh, i get the idea ;)

but what about the numbers? how do i choose which number i can use so that for example "windows xp" volume which located at /media/sda1 can onle be read only in guest account.. i have 3 account now which is root,Admin and guest.. so how suppose the chmod command look like... and how to choose the number?

---

### Post by subzero316 on 2008-05-07
> **moshazat said:**
> owh, i get the idea ;)

but what about the numbers? how do i choose which number i can use so that for example "windows xp" volume which located at /media/sda1 can onle be read only in guest account.. i have 3 account now which is root,Admin and guest.. so how suppose the chmod command look like... and how to choose the number?

```
sudo chmod 744 /media/sda1
```

This gives the file read/write by the owner and only read by everyone else (-rw-r--r--).




you dont have to mention thanks jus click the medal on right :-)

---

### Post by subzero316 on 2008-05-07
the numbers work like this

400 read by owner
040 read by group
004 read by anybody (other)
200 write by owner
020 write by group
002 write by anybody
100 execute by owner
010 execute by group
001 execute by anybody


so 4+2+1=7 (will give all read write n execute permissions)

chmod XYZ file

x is permisson for owener thats u
so x=7
y is for group y=4
z is for anybody z=4

---

### Post by moshazat on 2008-05-07
> **subzero316 said:**
> the numbers work like this

400 read by owner
040 read by group
004 read by anybody (other)
200 write by owner
020 write by group
002 write by anybody
100 execute by owner
010 execute by group
001 execute by anybody


so 4+2+1=7 (will give all read write n execute permissions)

chmod XYZ file

x is permisson for owener thats u
so x=7
y is for group y=4
z is for anybody z=4

Owhhh, thats how the numbers work eyy, hurm i thing i get the idea, i will try it now.. i will be back

---

### Post by moshazat on 2008-05-07
hurm, still no change..

i still can create and change any document in the volume...

about the XYZ... the x is the owner.. .and y is for group,which group it means?... how to make for example group "xubuntu" are the group that only can read which is the Y for exmple

---

### Post by subzero316 on 2008-05-07
If you can do that from a guest account then you have made a mistake in the command.

for creating a group:

```
groupadd somegroup
useradd -g somegroup -<other_options> username
```


or

```
groupadd -g SOMEGID somegroup
```

---

### Post by subzero316 on 2008-05-07
> **moshazat said:**
> hurm, still no change..

i still can create and change any document in the volume...

about the XYZ... the x is the owner.. .and y is for group,which group it means?... how to make for example group "xubuntu" are the group that only can read which is the Y for exmple

```
groupadd xubuntu
```

then add users to it like i stated b4
eg:
```
useradd -g xubuntu username
```

---

### Post by subzero316 on 2008-05-07
For a file name `samplefile`

```
sudo chown username1:xubuntu sample file 
sudo chmod 755 samplefile
```

---

### Post by moshazat on 2008-05-07
actually i already set that the Guest account is in "xubuntu" group using "users and groups" at administration...

i already login to root account try to change the group permission to the /media/sda1 as read only for "xubuntu" group, but it will change back to group called "plugdev" and the permission is read and write... what i want to do is to remove Guest account from plugdev OR set that the group that belong to "xubuntu" only have permission to READ ONLY... how can i do that?

or there is other way?
i already read the man chown and chmod, but im afraid to just trial and error since maybe will cause the whole system are in error, i dun want to make this thing bigger;)

---

### Post by MaindotC on 2008-05-07
Follow the instructions of subzero above but create a test file in your hda1 partition.  If you perform the operations he suggested then you should be able to test accessing it without the possibility of ruining your whole file system.

---

### Post by moshazat on 2008-05-07
huhu dont be so cold...:p
anyway i already use my solution, where i change the Guest account privilege selection,at Administration>Users and Groups. where i uncheck the first option... the automatic access to removable storage or something like that...

I did what the subzero told, but i want to make the whole volume to be read only, or cannot be change by user who access using Guest account,not only a single file :)

anyway thank you so much for telling me about this chmod and chown, maybe i can use it on other thing next time

---

### Post by MaindotC on 2008-05-07
I'm not being cold.  I'm saying that if you follow his directions on a TEST FILE then you don't have to worry about the integrity of your whole file system.  You can chmod, chown, and chgrp that file all you want and it won't affect your system.  Once you master this skill, then you can apply it to the whole hda1 folder and restrict permissions as you wish.

---

