---
title: "Backing up"
date: 2013-03-09
forum: New to Ubuntu
---

### Post by pras8421 on 2013-03-09
Hi, . . 

I have installed Ubuntu 12.10 on my system using Wubi inside windows. 
Can I have a backup of the system image and install again separately so that I get the GRUB loader with every package I've,
possibly without the internet connection?
I don't want to lose any package I have . . .
Can I've a solution?

I'm sorry for my poor English . .

---

### Post by ikt on 2013-03-10
In the Ubuntu Software Centre go to "File > Sync between computers" and sign in with your ubuntu single sign on, and that should be able to transfer them across.

Remember to select a local mirror in "edit > software sources", as many local sources are faster and may be not counted towards your internet usage.

---

### Post by bcbc on 2013-03-10
> **pras8421 said:**
> Hi, . . 

I have installed Ubuntu 12.10 on my system using Wubi inside windows. 
Can I have a backup of the system image and install again separately so that I get the GRUB loader with every package I've,
possibly without the internet connection?
I don't want to lose any package I have . . .
Can I've a solution?

I'm sorry for my poor English . .
I don't really understand. You'd like to reinstall, but have all your packages that you downloaded in a previous install? What is the reason? If you want a straight complete duplicate of your current install see this: [https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk](https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk)
It's possible to [multiboot different Wubi installs]("http://ubuntu-with-wubi.blogspot.ca/2012/10/getting-ready-for-ringtail.html") but not straightforward.

If you really want to reinstall a fresh copy but not download all the packages again, there may be a way to save your package cache, but I haven't seen a guide on how to do this. Here's a link but not sure how current it is: [http://www.debianadmin.com/create-backup-of-all-packages-using-aptoncd-in-ubuntu.html](http://www.debianadmin.com/create-backup-of-all-packages-using-aptoncd-in-ubuntu.html)

Maybe explain more clearly what you are after.

---

### Post by pras8421 on 2013-03-12
In fact, the reason is simple, I am running out of space.
Secondly, I want to have grub as loader.

---

### Post by bcbc on 2013-03-12
Then this may be of interest: [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

Other wise refer to this askubuntu post which has the above link and alternatives: [http://askubuntu.com/questions/635/how-to-convert-wubi-install-into-regular-install]("http://askubuntu.com/q/635/14916")

---

### Post by midfingr on 2013-03-12
Just a shot in the dark...

Maybe take a look at Clonezilla ? [http://clonezilla.org/](http://clonezilla.org/) It's used for imaging partitions, then a complete restore if needed.

@ ikt -- that's very cool, didn't know that, thanks :)

---

### Post by tejpatel98 on 2013-03-12
Are you trying to re-install your Ubuntu partition?

---

