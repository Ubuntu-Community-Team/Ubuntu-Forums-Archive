---
title: "CIFS mount permissions"
date: 2014-04-11
forum: New to Ubuntu
---

### Post by risk3715 on 2014-04-11
I have a windows machine with a share that I want to mount on my ubuntu machine temporarily.

I use this command to mount:
sudo mount -t cifs //192.168.1.202/Movies /media/Movies/ -o username=user,uid=1000,gid=1000,rw,dir_mode=0777,file_mode=0777

After putting in the above command, I put in my windows root password for 'sudo' and then the windows password for the user on the windows machine. (the user on the windows machine and the user on the ubuntu machine are the same)

It mounts the directory and all the directories and files in the mount show the correct permissions: -rwxrwxrwx and the owner is user and the group is user.
I can not make files in the mount, though. Example:
touch: cannot touch 'file': Permission denied

Even if I use sudo touch file I get the same response.

I can cp files from the mount to, say, my home directory. Even when I use smbclient to the share, I can 'get' files but I cannot 'put' files.

Any ideas?

---

### Post by risk3715 on 2014-04-11
Oops, I think I posted this in the wrong thread... maybe should be in Networking & Wireless

---

### Post by bab1 on 2014-04-11
> **risk3715 said:**
> I have a windows machine with a share that I want to mount on my ubuntu machine temporarily.

I use this command to mount:
sudo mount -t cifs //192.168.1.202/Movies /media/Movies/ -o username=user,uid=1000,gid=1000,rw,dir_mode=0777,file_mode=0777

After putting in the above command, I put in my windows root password for 'sudo' and then the windows password for the user on the windows machine. (the user on the windows machine and the user on the ubuntu machine are the same)

It mounts the directory and all the directories and files in the mount show the correct permissions: -rwxrwxrwx and the owner is user and the group is user.
I can not make files in the mount, though. Example:
touch: cannot touch 'file': Permission denied

Even if I use sudo touch file I get the same response.

I can cp files from the mount to, say, my home directory. Even when I use smbclient to the share, I can 'get' files but I cannot 'put' files.

Any ideas?

What is the output from the Ubuntu terminal of this command:```
ls -l /media/Movies
```

You will need to either: have console access (ptty) or you will need to ssh to the Ubuntu machine using PuTTY.  In any event we will need to see the Linux file ownership and permissions of the share directories.  Samba provides authentication (who are you) and Ubuntu provides the authorizations (are you allowed to do that).

[COLOR="#0000FF"]Edit:  I just realized you  have this as a CIFS share --> //192.168.1.202/Movies /media/Movies/ 

This should be //192.168.1.202/share_name.  You shouldn't use paths in the share description.  [/COLOR]

---

### Post by risk3715 on 2014-04-11
> **bab1 said:**
> What is the output from the Ubuntu terminal of this command:```
ls -l /media/Movies
```

You will need to either: have console access (ptty) or you will need to ssh to the Ubuntu machine using PuTTY.  In any event we will need to see the Linux file ownership and permissions of the share directories.  Samba provides authentication (who are you) and Ubuntu provides the authorizations (are you allowed to do that). 

Thanks for replying.
I thought I mentioned that the ownership of the mounted files and directory are my user. Lets assume that user is: george
Example:
george@ubuntu$ cd /media/Movies/
george@ubuntu:/media/Moves$ ls -l
drwxrwxrwx 0 george george 0 Apr 10 23:22 1-Horror
-rwxrwxrwx 0 george george 1234567 May 11 2010 Iron_Man.mp4
-rwxrwxrwx 0 george george 0 Sep 5 2-Chick_Flicks

Also note that the user on the Win 8.1 machine username is 'george' as well with the same password.

> 
[COLOR=#0000FF]Edit: I just realized you have this as a CIFS share --> //192.168.1.202/Movies /media/Movies/ 

This should be //192.168.1.202/share_name. You shouldn't use paths in the share description. [/COLOR]

Thanks for the tip. It was superfluous anyway. The actual share name is something else.

I just figured out my problem wasn't on the linux side, but on the Windows machine. I forgot to set permissions on the Windows machine to allow the user to do more than read. Thanks goes to bab1 for helping me remember that permissions need to be set on both machines.

---

