---
title: "setting the user and groupid of a mounted drive via sshfs"
date: 2015-07-07
forum: New to Ubuntu
---

### Post by Raner on 2015-07-07
I am trying to mount a drive using sshfs and give access to another user and group (think something like apache). I use this command:

```
sudo sshfs -o allow_other server@xxx.xxx.xxx.xx:/folder/to/mount ~/mount/point
```

and it works due to "-o allow_other". But this seems like overkill and I am worried that it is potentially dangerous since it allows access to other users. (The files being stored on the drive are somewhat sensitive backups.)

Using the user's uid and gid, I tried:

```
sudo sshfs -o gid=<gid>,uid=<uid> server@xxx.xxx.xxx.xx:/folder/to/mount ~/mount/point
```

But this actually didn't work, even though the mounted folder, using "ls -l", shows the owner and group as the intended user, as expected. The intended user still cannot create files in the mounted directory.

I have trouble understanding the man page, but I think some options there may help me ([http://linux.die.net/man/1/sshfs](http://linux.die.net/man/1/sshfs))

```
**-o** idmap=TYPE 
user/group ID mapping, possible types are: none  no translation of the ID space (default)  
user  
only translate UID of connecting user  
file  
translate UIDs/GIDs based upon the contents of **uidfile** and **gidfile** 
**-o** uidfile=FILE file containing username:uid mappings for **idmap=file** **-o** gidfile=FILE file containing groupname:gid mappings for **idmap=file** 

```


I don't understand what file it wants me to point to and, if I create the file myself, what the syntax of the file should be. This was only a guess on how to proceed, and I am not sure that any of this even matters. I want to re-create the "-o allow_others" option for a particular user/group without any potential security holes.

---

### Post by sandyd on 2015-07-08
Try the following:
```

sshfs -o idmap=user server@xxx.xxx.xxx.xx:/folder/to/mount ~/mount/point
```

Seems to work with root on external server + normal user on local computer.

Sudo is missing as it maps the user (server) to the user you are running the command as.

---

### Post by Raner on 2015-07-11
Thanks sandyd. I think I understand what I am missing now.

I tried idmap=user and thought it meant for me to put the intended user's name in for "user", but instead it maps to the current user. So I need to login as the intended user and run the command you gave. 

I did a bit of searching to find out how to do this and found this:

```
sudo -i
su -<username>
```

Which I tried with my intended user. But after running the command, I received no update and remain as root@my_machine, so I am not sure anything changed or the command even worked. If I tried it with my normal login user, I switched to normal_user@my_machine. If I tried it with a non-existent user, I received an error. So I don't know what is happening with my intended user after running this command. I do not seem to be logged in as that user.

What might be happening here? Is there another command I could use to login as the intended user? Or perhaps this is normal and indicative of something about the type of user I am trying logging in as? (I dont know if there are different types of users on linux. The intended user is one that is autocreated by a program (like apache) and not a real live person.)

---

### Post by sandyd on 2015-07-12
Sometimes, a user may not have a shell defined (or have a shell linked to /bin/true, etc)

Check the user shell in /etc/passwd and adjust with usermod if necessary.

```

su - *username*
#Specify shell when using su
su - *username* -s /bin/bash
```

---

