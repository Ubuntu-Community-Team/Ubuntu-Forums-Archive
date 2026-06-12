---
title: "A folder in /home for a group?"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by powerpleb on 2008-06-12
I want to create a directory in /home that several users can access so I can put shared files in there (Music, Photos, Videos, etc)
I was thinking I could create a group called 'share' and a directory called /home/share and set it up so members of the group have full access to this directory.
So my questions are...
Do all directories in /home have to be user accounts, ie if I create /home/share will Linux want to create a user called 'share'?
Can groups have /home folders? 
Is /home a good place to be storing shared files?

I ask this because I have /home on a large partition and it would be nice to have users' files and shared files kept on the same partition. It will make backing up easier and it will mean if I change distro, or do a clean install everything will work the same.

---

### Post by ibutho on 2008-06-12
The directories in /home do not have to be owned by a user and Linux will not try to create a user called "share" just because there is a folder called "share" in /home. /home is ok for sharing files between users and groups.

---

### Post by ibuclaw on 2008-06-12
As long as you don't try to make a user with the same name as the folder your creating, it should be alright.

Although, it can be safer to make it a hidden folder.

```

sudo mkdir -m 775 /home/.share
sudo chgrp users /home/.share

```
And then add all users who you want to give write access to the "**users**" group (gid 100).

This can be done with the app "**Users and Groups**" in the Gnome menu.
Or you can add them one by one with this command
```
sudo usermod -a -G users **FRED**
```

And then just create symlinks in the user accounts pointing to that directory, you know how to do that, right?
```
ln -s /home/.share **/PATH/TO/TARGET**
```

Regards
Iain

---

### Post by Cypher on 2008-06-12
What you want to do is create a new group and then create ANY directory in /home as Root, ensure to give RWX GROUP permissions to that directory with
```

sudo chmod 775 <dir>

```
Now which ever user should have access to that newly created directory should be part of the newly created group. These users can now create/delete files in that directory..

---

### Post by powerpleb on 2008-06-12
Thanks a lot guys.

---

### Post by powerpleb on 2008-06-12
Hmmm, I added all users to the group 'users' but when I type 'id' in console the group users doesn't show up.

---

### Post by powerpleb on 2008-06-12
Furthermore:
```
user1@host:/home$ echo 'hello' >> ~/share/hello.txt
bash: /home/user1/share/hello.txt: Permission denied

```

---

### Post by ibuclaw on 2008-06-12
What is the output of these commands?

```
ls -ld ~/share
```
and
```
cat /etc/group | grep ":100:"
```

Regards
Iain

---

### Post by powerpleb on 2008-06-12
```
andrew@andrew-laptop:/home$ ls -l ~/share
lrwxrwxrwx 1 andrew andrew 12 2008-06-12 22:16 /home/andrew/share -> /home/.share

andrew@andrew-laptop:/home$ cat /etc/group | grep ":100:"
users:x:100:andrew,gemma,root

```
andrew and gemma are the two users I added to the 'users' group

---

### Post by Najand on 2008-06-12
Change the group owner of the directory to users:
```
 sudo chgrp -R users /home/.share 
```
and then if you give any of these permissions then members of users group can use that feature:
```

For read permission: sudo chmod -R g+r /home/.share
For write permission: sudo chmod -R g+w /home/.share
For Execute Permission: sudo chmod -R g+x /home/.share
For all permissions: sudo chmod -R g+rwx /home/.share

```
If you want other users don't access it, remove their permissions:
```

sudo chmod -R o-rwx /home/.share

```

---

### Post by ibuclaw on 2008-06-12
1) You can remove root from the group.
Root has write access to everything, regardless of the chmod permissions.

2) Type in this
```
ls -ld /home/.share
```
:) Sorry, I wasn't aware that you put it where I suggested.

To make sure it is right, though.
```
sudo chmod 775 /home/.share
sudo chgrp users /home/.share

```
Also, you have to logout/login for the new group changes to take affect.

Regards
Iain

---

### Post by powerpleb on 2008-06-12
I tried that and it still doesn't work.

---

### Post by Najand on 2008-06-12
What is the output of:
```
 ls -lda /home/.share
```

---

### Post by powerpleb on 2008-06-12
> Also, you have to logout/login for the new group changes to take affect.

Thanks, i logged out and in again and it works well.

---

