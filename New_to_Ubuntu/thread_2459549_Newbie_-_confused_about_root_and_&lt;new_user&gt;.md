---
title: "Newbie - confused about /root and /&lt;new user&gt;"
date: 2021-03-21
forum: New to Ubuntu
---

### Post by netrix-g on 2021-03-21
Hi folks,

I'm new to Ubuntu, I have a new install of 20.04 LTS on my server.

At install I was prompted to create a user (I thought the term was root user, but maybe mistaken). - this is User 1
Post install - on reading much but absorbing little - I read that logging in as, or using the /root user is not advisable, so I created a new user with sudo privileges. - this is User  2

A little bit further along the line, I "think" that User 1 and User 2 are alike, in that they are both users created with sudo privileges - is that correct ?

If it is I would like to remove User 1 and all it's associated folders/files - I have only logged in once as User 1 at which point I created User 2. From then on, all setup and app installs have been via the User 2 profile.

It is no big deal to leave both user's on the server, but I would like to keep things tidy, I don't understand the filesystem structure yet and don't want to be confused from the get-go !

Thanks in advance, regards

Netrix

---

### Post by sotiris2 on 2021-03-21
The root user has the actual username 'root', that is you will see the command prompt have a form similar to root@myserver . If you put in a username for user1 during install user1 is not the root user.  If user2 is able to use sudo to install apps or edit root owned files you can delete user1.

---

### Post by CatKiller on 2021-03-21
> **netrix-g said:**
> At install I was prompted to create a user (I thought the term was root user, but maybe mistaken). - this is User 1
Post install - on reading much but absorbing little - I read that logging in as, or using the /root user is not advisable, so I created a new user with sudo privileges. - this is User  2 

/root isn't a user. root is the (theoretical) user with all the privileges. /root is that user's home directory. It's separate from all the other user home directories, which are in /home, because it needs to be available if things have gone really pear-shaped and you're booting up into an emergency root session and /home wouldn't necessarily be available under those circumstances; /home could be on another disk or another machine entirely. 

root isn't an account that you use on Ubuntu. By default it doesn't have a password and you can't log in with it, locally or remotely. You have to go out of your way to do those things. On Ubuntu you use sudo, or other mechanisms, to temporarily elevate a user's privileges for those times when you need to do system-wide maintenance tasks. 

Other distros might do things differently. 

> A little bit further along the line, I "think" that User 1 and User 2 are alike, in that they are both users created with sudo privileges - is that correct ? 

User 2 wouldn't necessarily have sudo privileges, but you said that you gave them to User 2, so yeah. 

> If it is I would like to remove User 1 and all it's associated folders/files - I have only logged in once as User 1 at which point I created User 2. From then on, all setup and app installs have been via the User 2 profile.

It is no big deal to leave both user's on the server, but I would like to keep things tidy, I don't understand the filesystem structure yet and don't want to be confused from the get-go !

I wouldn't bother, personally. If things get broken (and they will for an inexperienced user trying things out to see how they work; there's no shame in it, we've all done it), having a second user account available is a useful troubleshooting step to see if it's broken broken, or just broken for the one account. Things that are just broken for one account means that the fix is a config file in that user's home directory, and things that are broken broken need a fix elsewhere.

If things get so broken that a 20-minute reinstall is a better choice than a lengthy troubleshooting period  (and they might for an inexperienced user trying things out to see how they work; there's no shame in it, we've all done it) you can revisit whether you want two users then.

---

### Post by TheFu on 2021-03-21
+1 for what CatKiller wrote.

I usually create a backup user, so if some settings get munged with the first user (that which was created during the OS install), then it is easy to correct without going through a full reboot using a Try-Ubuntu Flash drive or Advanced Grub menu.

root --> /root ---> root's HOME directory (mandatory location)
bob --> /home/bob --> Bob's HOME directory (typical location, but there is no requirement for /home/ to be used for any or all user-account HOMEs).  

A fresh install is my first step in restoring backup data if there is any file corruption or disk failure or if I've mucked up the OS settings too much.

---

### Post by yancek on 2021-03-21
I would suggest you read the through the information at the link below which discusses root privileges and sudo used on Ubuntu with advantages/disadvantages explained.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

The standard install of Ubuntu requires that at least one user be created to successfully complete the install.  That first user always has root/sudo privileges.  If you created a second user and granted that user root privileges, it wasn't necessary as you already had a user with those privileges.  As stated in above posts, this should not really be a problem.

---

### Post by netrix-g on 2021-03-21
Thanks for all the info guys, much appreciated, I will mark this one as solved.

Onwards and upwards !!

Regards

Netrix

---

