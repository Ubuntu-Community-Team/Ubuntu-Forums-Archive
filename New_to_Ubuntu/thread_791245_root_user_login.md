---
title: "root user login"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Unewbeginner on 2008-05-12
hello, I want to know how to log in as root user.
I just installed Ubuntu on my personal computer and i'm the only person using this system. 

Now I need to install some software as root user, but when I login with the user name "root" and the password for "root",  the system message is: "the system administrator is not allowed to login from this screen".

How could I fix it?
thanks

---

### Post by SunnyRabbiera on 2008-05-12
actually if a software tells you to enter as root, dont, and use sudo instead...
what were you trying to install?

---

### Post by angry_johnnie on 2008-05-12
type **sudo** before any command to execute it as root.

for instance, if your told to install package-a by doing

```
apt-get install package-a
```

as root

what you do is

```
sudo apt-get install package-a
```

When it asks you for a password, it will be **your** password.

---

### Post by dfreer on 2008-05-12
Ubuntu ships with the root account locked by default. To unlock it, all you need to do is to create a password for it. Open up the terminal and type:
```

```
It should ask for your *sudo* password first (this should be your normal user's password, the one you use when you log in). It will then ask you to enter the new root password twice.

EDIT: This is the simple answer to why the system administrator is not allowed to login by default in Ubuntu. As mentioned above, it's better just to use sudo when you need root access.

FINAL EDIT: Evidently it is against forum policy to disclose this information, so I've removed the command.

---

### Post by tamoneya on 2008-05-12
> **dfreer said:**
> Ubuntu ships with the root account locked by default. To unlock it, all you need to do is to create a password for it. Open up the terminal and type:
```
sudo passwd root
```
It should ask for your *sudo* password first (this should be your normal user's password, the one you use when you log in). It will then ask you to enter the new root password twice.

While this is true it is strongly discouraged.  There is a reason why they did that and you are circumventing what canonical has tried to put in place.  There are very very few situations where sudo will not work as shown in the above post.

---

### Post by dfreer on 2008-05-12
> **tamoneya said:**
> While this is true it is strongly discouraged.  There is a reason why they did that and you are circumventing what canonical has tried to put in place.  There are very very few situations where sudo will not work as shown in the above post.

True, I have the root account locked on my debian system even (it's not by default). No reason to keep the information hidden from users though, and if the OP simply would rather log in as root I'd rather not have this end up being a "Ubuntu doesn't allow root logins at all" thread. :D

---

### Post by tamoneya on 2008-05-12
> **dfreer said:**
> True, I have the root account locked on my debian system even (it's not by default). No reason to keep the information hidden from users though, and if the OP simply would rather log in as root I'd rather not have this end up being a "Ubuntu doesn't allow root logins at all" thread. :D

I fully realize this and I honestly agree with you but I recently got in a little trouble with some of the mods for this myself and instead of letting you make the same mistake.  Take a look at this thread: [http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414).  While it says only graphical and automatic logins I posted almost the exact thing and got a infraction for it.  Its best to just abide by the rules of the forum.

---

### Post by Unewbeginner on 2008-05-12
> **SunnyRabbiera said:**
> actually if a software tells you to enter as root, dont, and use sudo instead...
what were you trying to install?

I'm going to install a 3D package called Houdini. It must be installed as the root user because the License Server files are written to /usr/lib/sesi.

I got the setup file called houdini.install, but I don't know how to run it as the root user in terminal (sorry I'm a new guy to linux).

Could anyone let me know how to make it?
thanks

---

### Post by tamoneya on 2008-05-12
```
sudo ./houdini.install
```

---

### Post by Unewbeginner on 2008-05-12
as root

what you do is

```
sudo apt-get install package-a
```

When it asks you for a password, it will be **your** password.[/QUOTE]

i run 
```
 sudo apt-get install houdini.install 
```

but it said couldn't find package houdini.install
where i'm wrong?

PS: i run this command under the directory of the package.

---

### Post by tamoneya on 2008-05-12
sudo apt-get install is used for packages in the repositories.  houdini install is not in the repositories (that is why the package is not found) you however have already downloaded the source and that is where you currently are (the directory from the tar.gz file).  Run the command I listed earlier.

---

### Post by SunnyRabbiera on 2008-05-12
you dont use apt-get for this one, the command should be sudo sh houdini.install or something along those lines

---

### Post by Unewbeginner on 2008-05-12
> **tamoneya said:**
> ```
sudo ./houdini.install
```

thanks. it works.

---

### Post by SunnyRabbiera on 2008-05-12
> **Unewbeginner said:**
> thanks. it works.

ah, I knew it might have been one of them, there are many ways to install binary packages like this so no wonder why I am garbled :D

---

### Post by dfreer on 2008-05-12
> **tamoneya said:**
> I fully realize this and I honestly agree with you but I recently got in a little trouble with some of the mods for this myself and instead of letting you make the same mistake.  Take a look at this thread: [http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414).  While it says only graphical and automatic logins I posted almost the exact thing and got a infraction for it.  Its best to just abide by the rules of the forum.

Thanks for the heads up. I was not aware about this rule. My original post has been edited.

---

