---
title: "HDD space"
date: 2012-10-16
forum: New to Ubuntu
---

### Post by 3dmatrix on 2012-10-16
I was recently facing shortage of space on my home partition and so shifted about 60 Gb of files to another partition.

I copied the files to the other partition and then deleted the original and finally emptied the trash.

But it was strange to find that even after repeated booting and emptying the trash i was still receiving low space messages.

Even system monitor and disk analyser all reported the same problem, but there were hardly that many files (including hidden files).

I finally booted through Puppy Cd and found that a .thrash folder had all those original files still blocking the space in that partition. Though i finally deleted that folder but i found it strange why we could not do the same from Ubuntu. Or did i go wrong anywhere ?


.

---

### Post by audiomick on 2012-10-16
> **3dmatrix said:**
> Though i finally deleted that folder but i found it strange why we could not do the same from Ubuntu. 

Do you mean "emptied", or did you really delete that folder? If you deleted it, I think you will find it has turned up again, albeit empty now.

If you open your file manager, you should see an icon for the trash folder on the left in the pane there. You do have to empty it periodically. It may be possible to set it to empty automatically at regular intervals. I am not sure.

While you are in the file manager, look in the "view" menu for the option "view hidden files". The keyboard shortcut is ctrl+H . When you have that switched on, you can see the files like .trash that have a dot at the start of their name and are normally not visible.

---

### Post by Bashing-om on 2012-10-16
What pops into my mind is roots' trash folder ????

[INDENT]just think'n <==BDQ


[/INDENT]

---

### Post by audiomick on 2012-10-16
Yeah, there is one of them too, I as far as I know. I haven't tried, but I expect you could look at it with an instance of the file manager with root privileges. You need to start the file manager, Nautilus, like this

```
gksudo nautilus
```

---

### Post by 3dmatrix on 2012-10-16
> **Bashing-om said:**
> What pops into my mind is roots' trash folder ????

[INDENT]just think'n <==BDQ


[/INDENT]

Oh ! YES that could be the reason and so i could not find any way to do that from my user area and had to finally boot through Puppy to do so.

Yes it could have been done through sudo nautilus also !

Thanx

---

### Post by 3dmatrix on 2012-10-16
> **audiomick said:**
> Do you mean "emptied", or did you really delete that folder? If you deleted it, I think you will find it has turned up again, albeit empty now.

If you open your file manager, you should see an icon for the trash folder on the left in the pane there. You do have to empty it periodically. It may be possible to set it to empty automatically at regular intervals. I am not sure.

While you are in the file manager, look in the "view" menu for the option "view hidden files". The keyboard shortcut is ctrl+H . When you have that switched on, you can see the files like .trash that have a dot at the start of their name and are normally not visible.

Perhaps you did not read my first post very well !

---

### Post by NikTh on 2012-10-17
Hi , 

can you open a terminal and give the results of these commands ```
df -Th
mount
```

Thanks

---

### Post by audiomick on 2012-10-17
> **3dmatrix said:**
> Perhaps you did not read my first post very well !

Hmmm, posting too late at night again.:-\"

When you want a root nautilus, do use "gksudo" and not just "sudo". It is not reccomended to use plain "sudo" to start graphical applications.

---

### Post by 3dmatrix on 2012-10-17
> **audiomick said:**
> Hmmm, posting too late at night again.:-\"

When you want a root nautilus, do use "gksudo" and not just "sudo". It is not reccomended to use plain "sudo" to start graphical applications.

Thanx and how does gksudo, sudo and sudo -i differ in terms of usage ?

Moreover can any one kindly tell me how can i make other partitions on my HDD accisible only through password ? In some versions of ubuntu it is there by default and in others it is not.

---

### Post by audiomick on 2012-10-17
> **3dmatrix said:**
> Thanx and how does gksudo, sudo and sudo -i differ in terms of usage ?

here is a good explanation of the reason for gksuo
[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

As far as sudo -i goes, I have never used that, but here is what the man page for sudo says about the -i option.

> -i [command]
                   The -i (simulate initial login) option runs the shell specified in the passwd(5) entry of the target user as a login shell.  This means that login-specific resource files such as .profile or .login will be read by the shell.  If a command is specified, it is passed to the shell for execution.  Otherwise, an interactive shell is executed.  sudo attempts to change to that user's home directory before running the shell.  It also initializes the environment, leaving DISPLAY and TERM unchanged, setting HOME, SHELL, USER, LOGNAME, and PATH, as well as the contents of /etc/environment on Linux and AIX systems.  All other environment variables are removed.

As far as the password access goes, I can't say much about that.I just don't know enough about that side of things.

---

### Post by 3dmatrix on 2012-10-21
Can any one tell me : I want my system to ask for password every time i try to access any other partition on my HDD (ofcourse except my home partition).
How can i do that ?

---

