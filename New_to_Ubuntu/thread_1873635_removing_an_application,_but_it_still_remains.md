---
title: "removing an application, but it still remains?"
date: 2011-11-01
forum: New to Ubuntu
---

### Post by dtay on 2011-11-01
hi all i'm trying to remove ruby and gems so that i can reinstall with rvm, but i'm having a hard time. 

i recently updated to the new distro (11.10), maybe that's pertinent. 

i gave the command 
$ sudo apt-get autoremove gem 

and it said it was removed, but then if i ask for:

$ gem -v
it remains 1.3.7

and if i ask for 

$ which gem

it returns /usr/bin/gem


why is this happening and how can i completely remove the application (the same thing is happening with ruby, but not rails).

---

### Post by Yayestechlab on 2011-11-01
Try running ```
sudo apt-get remove ruby && sudo apt-get autoremove 
``` and that should remove ruby.

---

### Post by dtay on 2011-11-01
> **Yayestechlab said:**
> Try running ```
sudo apt-get remove ruby && sudo apt-get autoremove 
``` and that should remove ruby.

yes i tried that before as well, didn't work with ruby or gems

---

### Post by 3rdalbum on 2011-11-01
If you installed those programs manually, i.e. not using Deb packages or Ubuntu's package manager, then you can't remove them using the package manager. You would need to consult the documentation that comes with the thing you downloaded.

Also:

```
chris@chris-desktop:~$ gem
The program 'gem' can be found in the following packages:
 * ruby1.9.1
 * rubygems

```

Check that it's not one of those two packages that you have installed.

---

### Post by dtay on 2011-11-02
> **3rdalbum said:**
> If you installed those programs manually, i.e. not using Deb packages or Ubuntu's package manager, then you can't remove them using the package manager. You would need to consult the documentation that comes with the thing you downloaded.

Also:

```
chris@chris-desktop:~$ gem
The program 'gem' can be found in the following packages:
 * ruby1.9.1
 * rubygems

```

Check that it's not one of those two packages that you have installed.

yes i installed them manually, and so am trying to remove them via the terminal. 

i checked and neither of those packages are installed.

it says i have gems version 1.3.7 and ruby 1.8.7, which are both old, making this problem even odder

---

### Post by dtay on 2011-11-02
> **3rdalbum said:**
> If you installed those programs manually, i.e. not using Deb packages or Ubuntu's package manager, then you can't remove them using the package manager. You would need to consult the documentation that comes with the thing you downloaded.

Also:

```
chris@chris-desktop:~$ gem
The program 'gem' can be found in the following packages:
 * ruby1.9.1
 * rubygems

```

Check that it's not one of those two packages that you have installed.

and any idea where that documentation might be? i'm guessing in a readme, but i can't find where these apps actually are on my hd, making finding a readme impossible...

---

### Post by dtay on 2011-11-02
removed gem with the purge command, ruby remains...any ideas?

---

### Post by 3rdalbum on 2011-11-02
Take a look on the Ruby website for removal instructions, maybe? Or just install a newer version over the top using Synaptic?

---

### Post by DapperMe17 on 2011-11-02
Have you tried to install deborphan-gtk, then look for those files and remove?

It's worth a try as maybe you still have remnants left in your system.

---

