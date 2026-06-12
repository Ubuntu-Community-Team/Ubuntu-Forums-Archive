---
title: "Home folder owned by &quot;nobody&quot;. Change owner or permitions."
date: 2008-07-05
forum: New to Ubuntu
---

### Post by osc1882 on 2008-07-05
I shared my home folder on one of my computers a cross the network and now the folders I created across the network say they are owned by nobody. And I can not change or remove or add to those folders from that computer its self. What command can I use to change the owner of everything in that home folder so that the computer it is on change make changes to the folder? I am no longer using the network. ( Router fried, bit torrent) and will soon be adding all files to that computer with with a portable hard drive.

---

### Post by Teber on 2008-07-05
i read about a command chown somewhere. try that in search and you should find useful info.

---

### Post by Fass on 2008-07-05
To flesh out the answer a bit, you may want to look at chown's man file before you do anything, but to change the owner of all files in /home/user, you'd do:

```
chown -hvR user /home/user
```

where "user" is the name of the owner you want to change it to.

---

### Post by bodhi.zazen on 2008-07-05
You should not share your home directory, rather share a directory within $HOME such as :

~/share

---

### Post by Teber on 2008-07-05
> **bodhi.zazen said:**
> You should not share your home directory, rather share a directory within $HOME such as :

~/share

as i recall sharing your home dir will shut you out? you would log in and be logged out in about 15 seconds? this is one of the reasons why i recommended searching the treasure trove of info this forum is. my own knowledge on permissions and ownership is very limited. and i'm aware now of the dangers being rash.

---

### Post by zzatz on 2008-07-05
Sharing a folder within a home directory is good for simple situations. You can handle more general cases if you understand how Unix permissions work.

Every user has a user ID (uid) and group ID (gid). You should never share a user ID, share a login, or anything like that. That login and user ID should always be limited to one and only one person.

But users belong to groups. And you can set up the group permissions on files and folders to allow members of a group to share the files.

Ubuntu creates a separate group for each user, with the group name the same as the user name. But you can belong to more than one group.

Say you wanted to share music with another user. Add a user named 'music' to the system, which will also add a group named 'music'. Then you can add the other users to that group. Change the permissions on /home/music to allow members of the group access, and you have a shared folder where you can control exactly who has access and who doesn't - by controlling membership in the group. By the way, you would never log in as 'music'; this just an easy way to add the group and the shared folder in a standard location.

Most projects can be handled this way. You can belong to as many groups as you need. If a file or folder has group permissions, and you belong to that group, you have those permissions.

Assume 'andy' and 'bob' already exist. Then:

sudo adduser music
sudo adduser andy music
sudo adduser bob music
sudo chmod g+rws /home/music

The chmod command adds read, write, and execute permission for the music group. Using 's' instead of 'x' means that anything added to that folder will get those same permissions, instead of your default permissions.

It's a little trouble to set up, but worth it to have a folder for a project that more than one person, but not everyone, has access to.

---

