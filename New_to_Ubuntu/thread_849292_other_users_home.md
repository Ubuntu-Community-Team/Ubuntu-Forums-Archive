---
title: "other users /home"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by rusty4r on 2008-07-04
I just did a fresh install of 8.04 with /home partition still intact. But when I try to add my wife and point to her /home/misty it tells me that /home/misty already exists and won't let me proceed. Any ideas how to get around that?

---

### Post by Pumalite on 2008-07-04
This might help:
[http://www.reallylinux.com/docs/usersubuntu.shtml](http://www.reallylinux.com/docs/usersubuntu.shtml)

---

### Post by rusty4r on 2008-07-04
Sorry pumalite, I didn't see anything there that refered to adding a user that alredy has a /home folder. It did say that you could remove a user and add them back later but then the user would still be in the list and I'm assuming it would be like just turning their account back on. But after my new install it's like my wife never existed even though her /home/misty is still there.

---

### Post by bumanie on 2008-07-04
Not sure whether this will help, but maybe you can reset her account from scratch and it will work properly again. Have a look and see what you think. [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Archmage on 2008-07-04
Did you try the commando line and use "adduser"? And later you need to give her the rights on the folder.

---

### Post by rusty4r on 2008-07-04
bumanie I just tried that and when I typed "ls /home" she was there but when I typed "passwd misty" it said unknown user.


Archmage, I'm not sure what you mean. I didn't use command line I tried the gui way under system-admin-users and groups.

---

### Post by bumanie on 2008-07-04
Try going into users and groups and use the gui to see what is there for "misty". System --> Administration --> Users and Groups.

---

### Post by rusty4r on 2008-07-04
nothing at all. only me "rusty"

---

### Post by sayakb on 2008-07-04
```
sudo rm -rf /home/misty 
```
Now  make the user account again..

---

### Post by rusty4r on 2008-07-04
if I remove /home/misty what is the point of having a seperate /home partition? all files and settings will be lost. although it's not like mine are working all my /home/rusty is there but still lost all my email and address book somehow

---

### Post by bumanie on 2008-07-04
I think what linuxisinnovation means is that if you remove the errant /home/misty, you should then be able to create a new one via adduser (or user and groups gui). Getting rid of /home/misty should not affect /home/rusty. Basically get rid of the one that's not working and recreate it.

---

### Post by rusty4r on 2008-07-04
I realize that it wont affect rusty but isn't there suppose to be some advantage to keeping your /home

---

### Post by sayakb on 2008-07-04
Keeping /home on separate or the same partition does not make any difference. It helps only when you re-install Linux, and hence, you don't lose your data.. If you have files in /home/misty, simply backup them somewhere. Even config files and database files would work if you copy them beck to the new /home/misty after creating the account again.

---

### Post by txcrackers on 2008-07-04
Don't delete the directory.

Use the command-line or a file manager to determine what the UserID and GroupID are for the directory/files. Since "misty" isn't a valid user at this point, they should show up as numeric values (e.g. 1002/1002). Then, in the "add user" dialogs, create the "misty" group first and specify the GID explicity. Then add the "misty" user and specify the UID and GID explicitly. There *should* also be an option to create the directory, which you need to un-check.

This is how having a separate partition saves you work in backing up and restoring. My current home partition has survived, intact, across 3 different hard-drives and seven years and four different distributions - Mandrake, RedHat, Fedora, Kubuntu. (Of course, at this point, it's also got so much cruft in it that it may be time to start from scratch... :wink:)

---

### Post by jerome1232 on 2008-07-04
Why don't you just rename her /home directory ie /home/misty-bck create her user and copy the files back over?

---

### Post by rusty4r on 2008-07-04
well I actually have another partition /data that I keep all my data on and an external that I plug in every now and then to backup the data. 

So what I'm still losing is my email account from thunderbird. and I also thought that my cursor selection, bacckground themes and other user settings would remain if I kept the /home folder.

when I used evolution I did copy the evolution folder over once before but now Im using thunderbird and the folder appears to be empty.

---

### Post by rusty4r on 2008-07-04
Ok what happened here what did I do wrong?

```
rusty@rusty-laptop:~$ sudo rename /home/misty /home/misty_old
[sudo] password for rusty: 
Bareword found where operator expected at (eval 1) line 1, near "/home/misty"
	(Missing operator before ty?)
syntax error at (eval 1) line 2, near "/home/misty
"
rusty@rusty-laptop:~$ 
```

---

### Post by jerome1232 on 2008-07-04
I would've done
```
 sudo mv /home/misty /home/misty_old 
```

for the difference between the two commands check out
```
 man mv
man rename 
```

---

### Post by bab1 on 2008-07-04
I believe rename works on files. You need to name which files you want renamed.  I believe you can use the command mv.  to rename the directory.  Check the man pages```
man move
```


Yes jerome1232

Just saw your post

---

