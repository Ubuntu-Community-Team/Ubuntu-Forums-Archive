---
title: "Uninstalled a package but it is still running"
date: 2016-10-16
forum: New to Ubuntu
---

### Post by tonma on 2016-10-16
I installed netbeans via the sudo ./install.sh command (Downloaded the netbeans zip)..
Then it somehow installed on 2 places: on the /home/netbeans-8.2 and also on /usr/local/netbeans-8.2

I ran sudo ./uninstall.sh at the /usr/local location, but the icon is still on the Ubuntu launcher, and it launches! and the netbeans on /home/netbeans-8.2 did not uninstall! it's still there!

so I did sudo ./uninstall.sh at /home/netbeans-8.2, but I get an error message:
 > "The specified target component - nb-base/8.2.0.0.20134543
 was not found in the registry. The installer
 can continue as if the target component was not specified. 
Click Yes to continue, No to exit the installer

I click Yes, but it won't delete this! so how can I still remove this netbeans, and check if it didn't install itself on another place? (And how did that happen the first place?!)

---

### Post by kc1di on 2016-10-16
Hello Tonma and welcome to Ubuntu and Linux,

You can try this in a terminal enter this command ```
sudo apt-get purge netbeans
```
if it spits out any error messages post them here. 

Once you purge your installed netbeans, you can install them from the repositories by typing
```
sudo apt-get install netbeans
```

It's always better to install from the official repositories as those files have mostly been checked and ok'd by the developers and packagers. 
only reason you should install out side the official repositories is if you need a newer version than is available or a package you have to have
and it's not available. 

Good Luck

---

### Post by monkeybrain20122 on 2016-10-16
I think netbeans is installed in your home and the one in /usr/local/bin is just a symlink (symbolic link, it is created to put netbeans executable in your path, so that, for example, you can start it in  the terminal by just typing netbeans) so to uninstall it you must uninstall it in from your home. Instead of running the uninstall script you should be able to just delete the netbeans folder

If you don't know where it is

In the terminal type
 ```
sudo updatebd
locate --a netbeans
```

The option --a show the hidden files (those start with ".") as well and they are usually configuration files, you would want to delete those as well.

---

### Post by tonma on 2016-10-16
> **kc1di said:**
> Hello Tonma and welcome to Ubuntu and Linux,

You can try this in a terminal enter this command ```
sudo apt-get purge netbeans
```
if it spits out any error messages post them here. 

Once you purge your installed netbeans, you can install them from the repositories by typing
```
sudo apt-get install netbeans
```

It's always better to install from the official repositories as those files have mostly been checked and ok'd by the developers and packagers. 
only reason you should install out side the official repositories is if you need a newer version than is available or a package you have to have
and it's not available. 


Good Luck

Thank you, will take note for next time, just thought that following the website would be better, but now I know !

> **monkeybrain20122 said:**
> I think netbeans is installed in your home and the one in /usr/local/bin is just a symlink (symbolic link, it is created to put netbeans executable in your path, so that, for example, you can start it in  the terminal by just typing netbeans) so to uninstall it you must uninstall it in from your home. Instead of running the uninstall script you should be able to just delete the netbeans folder

If you don't know where it is

In the terminal type
 ```
sudo updatebd
locate --a netbeans
```

The option --a show the hidden files (those start with ".") as well and they are usually configuration files, you would want to delete those as well.
 
updatedb*:P, the problem was (I think) that, upon first installation, my computer got stuck, so the installation was broken, and then I installed it in a different location (because it wouldn't let me install in the same location as it was "not empty" so couldn't be overwritten from some reason, unlike installations in Windows, where you just reinstall in the same place). So it seems like I did have 2 installations: 1 broken and 1 where I specified at home/netbeans-8.2. What I did was to delete the folder without uninstall command (simply del button), and then I reinstalled it again to the same location (home/netbeans-8.2 using ./install.sh), and then uninstalled again using the sudo ./uninstall.sh - and this time it did find the nb-base thing. I also remembered that I may have accidentally ran a sudo rm to the entire .nbi folder previously, that's why it didn't find the nt-base.

I know it's a long story, but just in case someone else has that problem.

Ty!

---

