---
title: "There's no need to set a password for root in Ubuntu"
date: 2008-08-15
forum: Recurring Discussions
---

### Post by Uchiha_madara on 2008-08-15
> **newnews said:**
> Hi, All:

I just installed ubuntu 8 in my PC. I want to set default OS to WinXP when booting. I try to edit "menu.lst", but I have no permission to save it,only user root can do. So, what is the default password for user "root"?

Thanks
you need to change the password of root

by using "passwd" command 

passwd root

then change the password , to Log in as root type 
su root 
and the new password

enjoy it

---

### Post by aysiu on 2008-08-15
> **Uchiha_madara said:**
> you need to change the password of root No, you really don't.

The supported security method for Ubuntu and the forums is *sudo* not a root login. If you want something resembling a root login, you can use ```
sudo -i
``` No new user and very few old users *need* to set a root password.

---

### Post by BarryMaccaukner on 2008-08-15
you need to change the password of root

by using "passwd" command

passwd root

then change the password , to Log in as root type
**su root**
and the new password
Aren't you actually supposed to type sudo su and the new password?

---

### Post by snowpine on 2008-08-15
> **BarryMaccaukner said:**
> you need to change the password of root

by using "passwd" command

passwd root

then change the password , to Log in as root type
**su root**
and the new password
Aren't you actually supposed to type sudo su and the new password?

No.

---

### Post by aysiu on 2008-08-15
> **BarryMaccaukner said:**
> you need to change the password of root

by using "passwd" command

passwd root

then change the password , to Log in as root type
**su root**
and the new password
Aren't you actually supposed to type sudo su and the new password?
You are not correct here.

You do not need to set or change the password of root at all.

You should not run the *passwd root* command, and even if you wanted to, you would still need to preface it with *sudo* to get it to work.

And, no, you don't *su root* either.

To get a persistent root prompt in Ubuntu, you don't need a new password. You just do ```
sudo -i
``` and then enter your normal password (no new password, no root password).

But, the OP is asking about editing the /boot/grub/menu.lst file, a task which definitely does not even require a persistent root prompt, so ```
gksudo gedit /boot/grub/menu.lst
``` should suffice.

For more information, please read [Forum policy on log-in-as-root tutorials](http://ubuntuforums.org/showthread.php?t=765414)

---

### Post by colobix on 2008-08-15
OK so the command to set password for root is passwd root?
I tried cso but it won't let me do that.
It told me that it couldn't see or change password information for root.

---

### Post by aysiu on 2008-08-15
> **colobix said:**
> OK so the command to set password for root is passwd root?
I tried cso but it won't let me do that.
It told me that it couldn't see or change password information for root. You shouldn't be setting a root password. Why do you think you need one?

Please read [Forum policy on log-in-as-root tutorials](http://ubuntuforums.org/showthread.php?t=765414) and [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by colobix on 2008-08-15
Oh nvm. I didnt see the msg where u said we shouldnt do so.

sudo -i works fine.

---

### Post by picpak on 2008-08-15
> **aysiu said:**
> You are not correct here.

You do not need to set or change the password of root at all.

Actually, there are a few (read: very few) files that can't be edited as a normal user or sudo, and needs su. I believe they were under /proc; this may have changed since then. Of course, the average user never needs to touch them anyway, so it doesn't matter.

---

### Post by aysiu on 2008-08-15
> **picpak said:**
> Actually, there are a few (read: very few) files that can't be edited as a normal user or sudo, and needs su. I believe they were under /proc; this may have changed since then. Of course, the average user never needs to touch them anyway, so it doesn't matter.
I'm of the opinion, and this is in line with what the staff has agreed upon, that anyone who needs a root-enabled account already can figure out how to enable it, and anyone who needs to be told how to enable a root account doesn't need to enable it.

---

### Post by lukjad on 2008-08-15
Good point that.

---

### Post by snowpine on 2008-08-15
Just to add my thoughts on the matter: There is certainly nothing wrong with logging in as root; I can understand why someone might want to do it. Hey, I even did it myself when I first started with Ubuntu (coming from a different distro)!

But the thing is, ubuntuforums is (in my opinion) the best resource of its kind on the internet. People come to this site in different ways, for example, googling a problem they're having. My concern is that if we allowed "logging in as root" posts, someone navigating to this site might just read that one post out of context and never learn about sudo. So, while I am sympathetic to the "free speech" argument, I really have to agree with the mods' decision to maintain a consistent "message" on the root vs. sudo debate throughout the forums. :)

---

### Post by grs on 2008-09-08
If a password is set for root, how can you set it back to not having one?

I think I need to set a password so I can use WinSCP fully.

---

