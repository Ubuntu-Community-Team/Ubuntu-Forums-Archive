---
title: "Help with web server and localhost"
date: 2013-10-05
forum: New to Ubuntu
---

### Post by jlsmi3th on 2013-10-05
Hello all, I am a retired mainframe programmer with 40 years experience in the business world. COBOL and many other languages. IBM, DEC, NCR, Prime, and a host of other large platforms; CP/M 2.2; MS-DOS; OASIS, and now Ubuntu. I would like your advice and help.

I am in the process of switching from Windows (version 7 most recently) to a pure Ubuntu life and I have much to learn. I have been putting up basic web pages using HTML, CSS and PHP since 2005. I hand-code all my work, I guess old habits die hard, but I am quite willing to learn new ways.

I am running Precise Pangolin on an old Dell Inspiron 1501, Ubuntu only, no dual-boot. No issues running on that platform. I have installed LAMP and it is working just fine. The issue I have is that I cannot seem to find how to or where to post my code so the "localhost" finds the code. I maintain a few websites so I need to keep their elements separate but still be able to direct the server to go to each one as needed. I do not have permission to create folders or files on "/var/www/" as it tells me I am not the owner.

I am reluctant to change the permissions to "/var/www/" as that seems to be an incorrect (or at least inelegant) solution and possibly dangerous. I have installed Bluefish but it, too, cannot write in that directory.

I eagerly await your thoughts and recommendations.

---

### Post by Kevin_Arnold on 2013-10-05
Just use sudo to create a directory inside /var/www and then you can change the permissions on that.
```

sudo mkdir /var/www/mydirectory

```

Then you can change permissions so you can write to it, just make sure www-data still has read access as well. You'll access it from [http://localhost/mydirectory](http://localhost/mydirectory).

Technically, another option is to create a new Apache virtual host and have it look somewhere else for the data, but I wouldn't suggest that.

---

### Post by grahammechanical on 2013-10-06
Do not take me a an expert on this but I think that you can create folders in that folder without changing the folder's permissions. We do it by becoming the owner. In fact we are the owner or the administrator. It is just that in Ubuntu we work as an ordinary user and only use our administrative privileges when we need to. When we are asked to authenticate an action as administrator.

If you run this code you will be running the File Manager with administrative privileges

```
gksudo nautilus
```

You can browse to the folder and I think that you will find that you can now create a folder inside it and also paste files into it. This can also be done on the command line. I think that we need to prepend the commands with "sudo." In both methods we will be asked to authenticate by giving a password. I think that the folder will still retain its original permissions. But as I said I am not an expert.

This explains the how and why of doing things this way in Ubuntu.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Regards.

---

### Post by JKyleOKC on 2013-10-06
And there's a third way to get to your goal: use "group" membership and permissions. The "group" concept is there specifically to solve such problems, by allowing additional permissions to a small group of users and permitting the super user (system administrator) to control membership in the group. All files and directories have three levels of permission: owner, group, and others. Within each level, separate permission flags for reading, writing, and execution exist. Normally, each defined user (such as "www-data") has a corresponding group defined, in the file /etc/group, and each file or directory owned by that user duplicates its owner's permissions in the "group" level. Thus any member of the "www-data" group would be able to write to places owned by "www-data."

You can add yourself to any group by using the "sudo" prefix to the command, or via the GUI's system maintenance dialogs. Once that is done (and you log out and back in one time to get the internal system flags synchronized with your permanent settings) you will be able to work in those previously-restricted areas just as if you were the owner -- and with no need to change anything except your own user attributes.

It's also possible (using sudo) to modify group permissions on any file or directory, so that group members can read but not write while "others" cannot even read it much less write. The "group" concept is quite powerful, and all too often overlooked. With your background, though, it should seem quite natural...

EDIT: There's essentially no limit to the number of groups to which you may belong, or the number of members in a group. Here's a listing of my current groups (my user id is "jk" and "testu" is another user id I created to help recover from a login problem):```
jk@mehitabel:~$ cat /etc/group|grep jk
adm:x:4:jk
dialout:x:20:jk
cdrom:x:24:jk,testu
audio:x:29:pulse,jk
plugdev:x:46:jk,testu
fuse:x:104:jk
lpadmin:x:105:jk
netdev:x:112:jk,testu
admin:x:118:jk,testu
jk:x:1000:
sambashare:x:121:jk,testu
vboxusers:x:122:jk
wireshark:x:127:jk
dovecot:x:135:jk

```

---

### Post by jlsmi3th on 2013-10-06
> **Kevin_Arnold said:**
> Just use sudo to create a directory inside /var/www and then you can change the permissions on that.
```

sudo mkdir /var/www/mydirectory

```

Then you can change permissions so you can write to it, just make sure www-data still has read access as well. You'll access it from [http://localhost/mydirectory](http://localhost/mydirectory).

Technically, another option is to create a new Apache virtual host and have it look somewhere else for the data, but I wouldn't suggest that.

Thank you all for the help. I chose to go the route of adding a new group and adding myself to that group and creating the new directory and changing its ownership. Seems to be working perfectly. Again, thank you all for the good help.

---

### Post by Kevin_Arnold on 2013-10-07
No problem, the group idea is definitely the best bet, I just wasn't sure how much work you wanted to put in to it :P

Happy coding!

---

### Post by sffvba[e0rt on 2013-10-07
*Thread moved to **Absolute Beginners Section**.*


404

---

