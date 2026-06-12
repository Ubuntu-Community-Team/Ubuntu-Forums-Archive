---
title: "How to format a drive Correctly"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by janes604 on 2008-11-01
HI all 

SO i have a spare Hard drive and  i used Gparted(live cd) to format it and installed a ext3files system on i. Now when i mount it in Ubuntu 8.1  and try to copy a file/folder etc to it it say: 

The folder " Stuff" cannot be copied because you do not have permissions to create it in the destination.


What did i do wrong , you help will be greatly appreciated.

Ubuntu FTW !
 Thanks in advance !

---

### Post by Cypher on 2008-11-01
How did you mount your newly partitioned "stuff" partition? If you use the normal "sudo mount <partition> <destination directory>" scheme, then the destination directory is owned by root and only root can do anything there.

You'll want to use the "-o umask=0777" or something to give everyone access to the directory..

---

### Post by taurus on 2008-11-01
Since it's an ext3 filesystem, you can just change the ownership of directory Stuff to your login name so you can write to it anytime you want.  Assuming your login name is janes and you mount that spare harddrive to /media/Stuff, run

Applications -> Accessories -> Terminal
```
sudo chown -R janes:janes /media/Stuff
ls -la /media/Stuff
```

---

### Post by janes604 on 2008-11-01
HI thanks for the replies 
Im pretty new to the command line stuff and typically i just use the graphical interface to do stuff i.e mount the drive by  going to My computer and right clicking the drive fyi the drive name/label is  ¨Back up¨ 

the folder i was trying to copy to the drive was called ¨Stuff¨ and when i tried to move that file to the drive it says:

*{ The folder " Stuff" cannot be copied because you do not have permissions to create it in the destination. }*

The destination being &#7831;he ¨back up" drive

So im not really sure where how to proceed here....

Thanks again

---

### Post by janes604 on 2008-11-02
> **taurus said:**
> Since it's an ext3 filesystem, you can just change the ownership of directory Stuff to your login name so you can write to it anytime you want.  Assuming your login name is janes and you mount that spare harddrive to /media/Stuff, run

Applications -> Accessories -> Terminal
```
sudo chown -R janes:janes /media/Stuff
ls -la /media/Stuff
```



So I tried this with the necessary changes for my user name etc and no success  
it give me this message 

chown: cannot access `/media/backup': No such file or directory


your help is much appreciated

---

### Post by vrhahaha on 2008-11-02
this is how i normally do it :

- Alt-F2 , type in "gksu nautilus", enter your password
- browse to the harddisk that u want to change the permission
- right click and go to Properties
- go to Permissions tab
- change Owner: your username, Folder access: Create and delete files
- change Group: your username, Folder access: Create and delete files
- change Folder access: create and delete files
- unmount the volume
- log out then log in

does it help?

---

### Post by janes604 on 2008-11-02
> **vrhahaha said:**
> this is how i normally do it :

- Alt-F2 , type in "gksu nautilus", enter your password
- browse to the harddisk that u want to change the permission
- right click and go to Properties
- go to Permissions tab
- change Owner: your username, Folder access: Create and delete files
- change Group: your username, Folder access: Create and delete files
- change Folder access: create and delete files
- unmount the volume
- log out then log in

does it help?


YES, this was perfect thank you very much.
:KS:KS:KS:KS:KS

---

