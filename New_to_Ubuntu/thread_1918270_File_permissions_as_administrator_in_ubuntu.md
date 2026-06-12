---
title: "File permissions as administrator in ubuntu"
date: 2012-01-31
forum: New to Ubuntu
---

### Post by davidc60 on 2012-01-31
Hi,  
 I am presently running Ubuntu 11.10 (from a USB). I routinely get messages on the screen saying that I do not have 'permission' to view or open a particular file, or rename files, delete files or even copy and paste between folders etc. allegedly because I am not the 'owner'. The fact is that I am using the system as the Administrator, they are all my files, I created them and no-one else is authorised to use the system. Can anyone please enlighten me as to how I can completely and permanently change the 'permissions' so that I can access and change everything and anything on the system at any time? (I have tried the Properties-Permissions tab but this is greyed-out and simply refers to 'root' (which is me, as Administrator, anyway). Many thanks,

---

### Post by Morbius1 on 2012-01-31
> (I have tried the Properties-Permissions tab but this is greyed-out and  simply refers to 'root' (which is me, as Administrator, anyway).You are not root. As Administrator you have been endowed by root to have certain privileges but only after you provide credentials. To change permissions on a file you can use the terminal and precede the appropriate command with **sudo** or you can do it graphically by launching nautilus with privileges:
```
gksu nautilus
```

---

### Post by Dngrsone on 2012-01-31
Ubuntu is designed to protect people from themselves as much as from others.

With that in mind, even thought you are the only user on your machine, your username and permissions are distinctly different from the superuser known as root.

Root pretty much has all permissions to do anything on the machine, but it can be pretty easy to trash your OS if you don't know what you are doing, which is why you aren't allowed to log in as root and why system files are protected from manipulation from non-root users.

With that said, if you want to dig around in the system files unimpeded, then open up a terminal and enter in the following:

```
gksu nautilus
```

You will be asked for your password and then a nautilus file browser will open up with root permissions.

Again, I warn you that you be absolutely certain you know what you are doing when moving, changing, or deleting any system files while acting as root.

---

### Post by cavh on 2012-01-31
Linux (and other *nixes) come at permissions from the opposite end that Windows does. That's what helps these operating system stay secure (compared to Windows). In Windows, the door (or should that be window?) is wide open, and viruses and malware come floating in. In Ubuntu (as with other *nixes), the door is closed and you have to explicitly open it using sudo and gksudo. 

Suggest you read this: [http://help.ubuntu.com/community/FilePermissions]("http://help.ubuntu.com/community/FilePermissions")

Then read the man pages for sudo and gksudo:
[http://manpages.ubuntu.com/manpages/oneiric/en/man8/sudo.8.html]("http://manpages.ubuntu.com/manpages/oneiric/en/man8/sudo.8.html")
[http://manpages.ubuntu.com/manpages/oneiric/en/man1/gksudo.1.html](http://manpages.ubuntu.com/manpages/oneiric/en/man1/gksudo.1.html)

gksudo is used when you want to run a graphical interface to a command. For example, typing gksudo nautilus in a terminal window (which is like the DOS command line) will bring up the nautilus file manager (like Windows Explorer) in sudo mode.

sudo is used to run commands in a terminal window which do not require a graphical interface.

---

### Post by Morbius1 on 2012-01-31
And just in case there is any confusion over **gksu** vs **gksudo**:
> ls -l /usr/bin/gksudo
lrwxrwxrwx 1 root root 4 2010-05-18 07:19 /usr/bin/gksudo -> gksu                      
In Ubuntu one is a symlink to the other.

---

### Post by davidc60 on 2012-01-31
Thanks for your prompt and helpful replies. Remarkably, my system has apparently started misbehaving just shortly before I posted my message about 'file permissions' so I cannot run the nautilus command.  All of a sudden the terminal has chosen not to accept my usual administrator password - this happened immediately after I had deleted my Standard user account (which I only created yesterday) leaving just the Administrator account on the system. I have no idea why this has happened. It is not just the terminal that won't accept my usual Administrator password - I cannot even try to set things straight in the User Accounts program because that will not accept my usual password either. The net effect of this is that I can no longer 'change' anything in Ubuntu! I have tried restarts, shutdowns etc. all to no avail. 
davidc

---

### Post by Dngrsone on 2012-01-31
By deleting your user account, you pretty much locked yourself out.

---

