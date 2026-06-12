---
title: "Maintance"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by Oliver.BS on 2008-11-19
What can I do to keep my system running perfect like on XP I would Defrag,disk Check etc etc

---

### Post by wolfen69 on 2008-11-19
there is no need to defrag in linux. as far as diskcheck, every 25 boots or so it will automatically do a file system check at boot. relax and enjoy. you can also clean up any unused files and dependencies by: ```
sudo apt-get clean
``` and ```
sudo apt-get autoremove
```

---

### Post by Crafty Kisses on 2008-11-19
To be honest you don't really have to defrag in Linux, the file system is organized and stored more efficiently than a Windows box. If you really want to then I can suggest you go to something like Google and search "Linux defrag" or something and grab a utility, they do exist, but unnecessary.

---

### Post by Oliver.BS on 2008-11-19
I keep getting this error I can never get my Terminal to work I get Command not found all the time

```
oli@Olis-laptop:~$ apt-get clean
E: Could not open lock file /var/cache/apt/archives/lock - open (13 Permission denied)
E: Unable to lock the download directory
oli@Olis-laptop:~$ 

```

---

### Post by Crafty Kisses on 2008-11-19
Try putting "sudo" in front of that command, so it would look like this:
```
sudo apt-get clean
```

---

### Post by philinux on 2008-11-19
sudo apt-get clean

---

### Post by Oliver.BS on 2008-11-19
I am sure my Terminal doesnt work I now get this

```
oli@Olis-laptop:~$ sudo apt-get clean
[sudo] password for oli: 
oli@Olis-laptop:~$ 


```

Should I use Root Terminal or Just Terminal

---

### Post by Crafty Kisses on 2008-11-19
That's normal when you run the command "clean".

---

### Post by Oliver.BS on 2008-11-19
But nothing happens.I dont even get a report to say its done.

---

### Post by MasterSander on 2008-11-19
yeah that's normal :P

---

### Post by cariboo on 2008-11-19
THe only time a terminal will report anything back is when you do something wrong. To check if the apt-clean command worked you can cd to /var/cache/apt/archives. the only thing in that directory should be a sub-directory called partial.

Jim

---

### Post by Oliver.BS on 2008-11-19
Aww bless it not wanting any thanks lol cheers so if I go back to 

```

oli@Olis-laptop:~$ 


```

After a command it has worked ?

---

### Post by LowSky on 2008-11-19
yes

---

### Post by SunnyRabbiera on 2008-11-19
for administration commands always put sudo in, in your case sudo apt-get clean
and then enter YOUR password.
sudo is sort of like super user mode but you use your password instead of an admin password.

As for defrag it is not needed, ext3 (the linux filesystem) does not fragment nearly as much as NTFS

---

### Post by Oliver.BS on 2008-11-19
Cool thanks every one

---

### Post by SunnyRabbiera on 2008-11-19
Yeh sorry you got thrown off, if you need to learn basics just ask as for us they are second nature :D
just keep in mind a few things:
When using some guides on the web if someone prompts you to put in the su command substitute it with sudo
also the root account is disabled by default, this is done as a safety measure and is for the best :D

---

