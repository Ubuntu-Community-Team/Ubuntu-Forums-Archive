---
title: "How do I get to system admin?"
date: 2013-02-17
forum: New to Ubuntu
---

### Post by Jonathan47 on 2013-02-17
Hi,
I just upgraded to Ubuntu 12.04, and I can not see how to get to system admin. I have tried all the buttons I now have down the left of my screen, + the menus on top, so I feel a bit silly
What I want to do when I get there is to set one of my user accounts to not need a password, and give that account access to (some) files and programs created/downloaded when I was logged in as administrator.
The system info I know how to access (because someone told me in response to a prior request) is below if that helps. Thanks

```
theboss@Ubuntu-desktop:~$ lsb_release -rcd ; uname -rm
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise
3.2.0-37-generic-pae i686
theboss@Ubuntu-desktop:~$ echo $DESKTOP_SESSION
ubuntu
theboss@Ubuntu-desktop:~$ lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF106 [GeForce GTS 450] [10de:0dc4] (rev a1)
    Subsystem: Giga-byte Technology Device [1458:34fe]
    Kernel driver in use: nouveau
theboss@Ubuntu-desktop:~$ 

```

---

### Post by gifford on 2013-02-17
Go to system settings in the launcher(left side) and then under system go to user accounts.

---

### Post by Jonathan47 on 2013-02-18
Thanks gifford

Sorry, I was not clear on what I was asking. (to be expected given my current level of ignorance :))

I did find what you told me, but could not see how I can actually DO anything.

 I can now lock and unlock the popup,  add and delete accounts, and enable/disable automatic log in. 
But I still do not know how to share files between users.

What am I missing?

---

### Post by WhipLash365 on 2013-02-18
if you want to be able to work with files created as root type in terminal:```
sudo nautilus
```
It will start file browsing as root giving full access to all files (beware! Deleted files in this mode are immediately removed from disk. Also pay attention not to delete important system files)

---

### Post by schragge on 2013-02-18
It sounds like all you want is to change ownership of some files
```

sudo chown $USER:$USER file1 file2 ...

```

However, if you want to permanently share some files between two users then you can add both users to the same group
```

sudo adduser theboss users
sudo adduser anotheruser users

```
Then adjust file permissions for the files you want to share
```

sudo chgrp users shared_file
sudo chown g+rw shared_file

```

---

### Post by Warren Hill on 2013-02-18
If you were the first user on the system then you should have administrator privileges. To find out open a terminal (CTRL+ALT+T) and enter

```
id
```If this lists **sudo** as one of the groups you belong to then you are.  However you need to tell the computer when you need the admin privileges

For graphical applications press Alt-F2 and in the window that opens type

```
gksu *command*
```Replace *command* with the name of the program you want to run for example

```
gksu nautilus
```Runs the file manager as root

```
gksu gedit
```Create text file as root

For command line applications prefix the command with **sudo**.  For example
```
sudo fdisk -l
```Lists the drives on your computer

More information here

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

**_Edit:_** You will also see **gksudo** used in place of **gksu** in some places. **gksudo** is just a link to **gksu** so both commands are equivalent,

---

### Post by slickymaster on 2013-02-18
> **WhipLash365 said:**
> if you want to be able to work with files created as root type in terminal:```
sudo nautilus
```


You should never use sudo with graphical applications. Use **gksudo** instead.

Take a look at this: [Running Sudo Graphically]("http://www.psychocats.net/ubuntu/graphicalsudo"), it explains it very succinctly.

---

### Post by squakie on 2013-02-18
the first thing I would do is manually add a folder to \home name something like "shared". I would then change the permissions on that folder to only be accessable from a certain group (create a new one specifically for this), then add the users who are allowed to access that folder to that group. I *think* that any files/sub folders the users create within that new folder would still be accessable by that group. Keeping the sharing in a separate folder off \home means you don't have to worry about messing something up with the system files nor with any single users files not in the "shared" folder. Move the files created by you as administrator to that new folder, check the permissions and modify as needed to be accessable by the new group.

---

