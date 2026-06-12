---
title: "why do root folder permissions..."
date: 2008-08-19
forum: New to Ubuntu
---

### Post by csu1 on 2008-08-19
...every group permission to access all folders in :/ ?

By default of installation of hardy 8.04[Kernel Linux 2.6.24-19-generic, GNOME 2.22.2]

in folder properties permissions, the are three categories; **owner, group** and **others** 

who are or what is the others category?   

Why are there so many groups? and is the mail group for example able to interactively create an unwanted session(which has instant access to :/)? 

after installation of software it is treated as a new group and instantly has access to any file in :/ 

If the root is the owner of all files on :/, why does it allow write/read permissions too it's home folder!:/root) to all other groups and users? 

to protect the owner of all,(roots files(:/)i must first select all folder permissions to deny the unprivileged user's group, why? should this deny permission to :/ not be applied upon creation of unprivileged user? I guess unprivileged user's needs to read/write some system files to run a session, but is it necessary to allow access to all of the operating system's important files?

...or maybe i just misunderstand groups:roll:

---

### Post by t0p on 2008-08-19
Very confusing question.  I can't explain the reason for the existence of groups to you.  As for permissions to the root directory: on my computer, the permissions to root directory are as follows:

Owner (root) has write access: ie can create and delete files

Group (root) and Others have read access: ie can read files only.

But maybe that isn't the directory you're talking about.  I just noticed you wrote **/ directory**.  The / directory is at the root (haha) of the entire file structure.  It is not the same as the directory called "root".

---

### Post by nicedude on 2008-08-19
I don't think you are at all correct in the way you think this works, here is just one thing you said that I can easily see is incorrect. I am sure others here might explain some of the other things you asked about.

YOU SAY
to protect the owner of all,(roots files(:/)i must first select all folder permissions to deny the unprivileged user's group, why? should this deny permission to :/ not be applied upon creation of unprivileged user? I guess unprivileged user's needs to read/write some system files to run a session, but is it necessary to allow access to all of the operating system's important files? 

Unprivileged users have no read/write access to / I don't know how you deduced that. By default you have to use sudo in conjunction with knowing the system password to modify any important things. Even your first user you create when you install who is basically the admin account has no access to / files without first using sudo or logging in as root. The Ubuntu system is pretty secure the way it comes and unless you go compiling source code from unknown people then you are safe. Can you get say a rootkit infection? YUP but only if you are downloading unknown code from bad people and installing it yourself. So stick to the stuff in the repositories or on reputable sites like sourceforge and you should be plenty safe.

---

### Post by pauper on 2008-08-19
"Groups" limit access to system resources to only those services/devices/users
who are the part of that group. Instead of manually assigning permissions to
every user, you could use groups--far quicker. "Others" are neither the owner
of the file/directory nor the group assigned to it.

[http://www.debian.org/doc/debian-policy/ch-opersys.html#s9.2](http://www.debian.org/doc/debian-policy/ch-opersys.html#s9.2)

> **csu1 said:**
> I guess unprivileged user's needs to read/write some system files to run a
session, but is it necessary to allow access to all of the operating system's
important files?

Try reading/accessing, let alone modifying, the majority of hidden files/directories
in /root as regular user, for example. *Important files* have zero permissions
for "Group" and "Others" by default.

Segregate user and system data (keep /home, /var, /tmp on separate partitions).

For paranoid people, look into "man chattr" and ACL:

[http://www.securityfocus.com/infocus/1407](http://www.securityfocus.com/infocus/1407)
[http://www.securityfocus.com/infocus/1400](http://www.securityfocus.com/infocus/1400) (probably outdated).

Read about file permissions:

[http://www.hackinglinuxexposed.com/articles/20030417.html](http://www.hackinglinuxexposed.com/articles/20030417.html)
[http://www.hackinglinuxexposed.com/articles/20030424.html](http://www.hackinglinuxexposed.com/articles/20030424.html)

---

### Post by meanburrito920 on 2008-08-19
Groups exist for multiple reasons. Lets say for example, you want to share a folder between several users. However, you dont want some other user to access that folder. You cant have all the users 'own' the folder, so instead you put them all in a group that 'owns' the folder. so therefore, they all can have equal access to the folder. Groups is just a way of saying 'lots of users with the same permissions on certain files'. Others are anyone not in that group. and owner, is of course, whoever the one user that owns that file is.

---

