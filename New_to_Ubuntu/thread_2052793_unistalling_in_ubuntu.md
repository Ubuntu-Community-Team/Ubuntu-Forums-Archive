---
title: "unistalling in ubuntu"
date: 2012-09-04
forum: New to Ubuntu
---

### Post by iamrcube on 2012-09-04
I am new to ubuntu and would like to know the command that I need to enter in terminal to uninstall kile from my computer. Can anybody please help.

---

### Post by sanderj on 2012-09-04
> **iamrcube said:**
> I am new to ubuntu and would like to know the command that I need to enter in terminal to uninstall kile from my computer. Can anybody please help.


If you installed it via

```
sudo apt-get install blabla

```
then you can install via

```
sudo apt-get remove blabla

```

HTH

---

### Post by Ansowi on 2012-09-04
This should work:

```
sudo apt-get remove kile
```

I don't have this package installed but it seems to have a lot of dependencies, so after removing the package you may want to run this too:

```
sudo apt-get autoremove
```

If it says no packages were removed, that's fine.

---

### Post by taras.kuzyo on 2012-09-04
Also you can run 
```
sudo apt get purge <package>
```
to remove configuration files of that package.

---

### Post by robtygart on 2012-09-04
You might want to also look at the manual for apt-get it will give you more options and a discription of what it does. You will learn a lot.

For the manual type 
```
man apt-get
```

Do this for other commands too.

---

### Post by marlow59 on 2012-09-04
The best thing to do (as suggested) is : 
 ```
sudo apt-get autoremove kile
 sudo apt-get purge kile
```

If you have installed the application prom the Ubuntu software center it may be easier and more "user friendly" to uninstall it from the Ubuntu software center. (run the Ubuntu software center directly from the launcher or from the Dash).

Hope it helps.

---

### Post by newb85 on 2012-09-04
> **marlow59 said:**
> The best thing to do (as suggested) is : 
 ```
sudo apt-get autoremove kile
 sudo apt-get purge kile
```If you have installed the application prom the Ubuntu software center it may be easier and more "user friendly" to uninstall it from the Ubuntu software center. (run the Ubuntu software center directly from the launcher or from the Dash).

Hope it helps.

Unless you really *really* don't want to use the CLI, I suggest you not use the Software Center to uninstall kile.  The software center won't remove all those unnecessary dependencies mentioned earlier, or the configuration files for kile.

---

### Post by Paqman on 2012-09-04
> **newb85 said:**
> The software center won't remove all those unnecessary dependencies mentioned earlier, or the configuration files for kile.

Which can be a handy feature. If you ever want to reinstall it'll be fast and already configured.

---

### Post by newb85 on 2012-09-04
> **Paqman said:**
> Which can be a handy feature. If you ever want to reinstall it'll be fast and already configured.

Granted, provided you don't need that space for something else.  If someone that new to Ubuntu installed kile, it probably installed all the KDE libraries, which are comparatively large.  Of course, that could also be used as an argument for keeping them installed.

Actually, if you were switching to a different LaTex development environment (such as Lyx), it would probably be best to hold of on removing dependencies until after the new one was installed, as they probably have a lot of common dependencies.

---

### Post by Paqman on 2012-09-04
Sure. This being Absolute Beginners I just wanted to point out that that behaviour was a feature, rather than a bug! The onus does then fall on the user to do a bit of housekeeping once in a while.

---

### Post by newb85 on 2012-09-04
> **Paqman said:**
> Sure. This being Absolute Beginners I just wanted to point out that that behaviour was a feature, rather than a bug! The onus does then fall on the user to do a bit of housekeeping once in a while.

Agreed.

---

### Post by robtygart on 2012-09-05
> **Paqman said:**
> Which can be a handy feature. If you ever want to reinstall it'll be fast and already configured.

Does programs that are alike, Example: (Banshee & Amarok), use the same dependencies. and if another program does use any of the same, could it messup the other program?   

Also with todays Hard divres with so much space, does it hurt leaving these dependencies installed?

---

### Post by ramsharan065 on 2012-09-05
If your are new to ubuntu, I would suggest to use ubuntu software center to uninstall it.

---

### Post by mcduck on 2012-09-05
> **robtygart said:**
> Does programs that are alike, Example: (Banshee & Amarok), use the same dependencies. and if another program does use any of the same, could it messup the other program?   

Also with todays Hard divres with so much space, does it hurt leaving these dependencies installed?

they might, or they might not. Depends on the programs, and what libraries etc. the program's developer decided to use.

Anyway, any package will be installe donly onve, and shared with any other package that might depend on it. And no, different programs sharing things doesn't mess anything, that's actually one of the main benefits of having a working package management system like we have in Linux systems. :)

Leaving dependencies installed doesn't waste anything else than drive space, and quite likely not too much of that either. Of course if you install and uninstall tons of stuff you'll end wasting more space, so it pretty much depends on what you do, and how much extra space you have available. In general it's not something you should worry about all the time, but on the other hand it desn't make any sense to use gigabytes worth of space for something you aren't using, so cleaning up unused dependencies every now and then would still make sense. After all, it only takes one command in a terminal to do. ;)

What comes to configuration fels left behind, they are just small text files and absolutely meaningless when considering disc space usage. The main reason why you'd ever want to remove any of those is if you have somehow messed up a program and want to get a fresh start with it to fix the problems. And also keep in mind that any user-specific settings will be stored in your own home directory, and the package manager will never remove those. So purging a package like Firefox would still leave your own browser settings untouched.

---

### Post by houseworkshy on 2012-09-05
One of the most useful commands is "man", entering this in front of any command will take you to it's manual page;  so "man man" will tell you how to use it and "man apt-get" will tell you about apt-get.  This help is built in so always available, even offline.

---

