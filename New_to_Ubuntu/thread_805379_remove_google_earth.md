---
title: "remove google earth"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-05-23
I have been trying to remove google earth and have had no luck.

This is what I have tried.

sudo apt-get autoremove googleearth

and this is the response.

shawn@shawn-laptop:~$ sudo apt-get autoremove googleearth
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package googleearth
shawn@shawn-laptop:~$ 

Then I tried

sudo apt-get autoremove /opt/googleearth folder

and I got

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package

---

### Post by Maestro23 on 2008-05-23
Did you install it from the repositories or download it from the website?

---

### Post by unutbu on 2008-05-23
Since the apt-get command did not work, perhaps try
```

sudo /opt/google-earth/uninstall
```

---

### Post by saskatchewan on 2008-05-23
I just managed to get it to work!!

I had installed the 4.3 version of Google earth and it would not work so, I just installed the 4.2 and it seems to have replaced the 4.3 without me doing any removal.

Do you think that I have been successful or is there likely just more crap hiding on my hard drive?

---

### Post by vrangforestillinger on 2008-05-23
The command for removing packages in apt is
```
sudo apt-get remove googleearth
```

Autoremove is for removing old dependencies that are no longer needed. I usually run remove first, and then I run autoremove to delete libraries (lib-packages) that are no longer needed. 

How did you install google earth? 

It might be that you need to use dpkg instead of apt-get.

```
sudo dpkg --remove googleearth
```

Edit: Woops.. Didnt see those replies coming. :P Oh well

---

### Post by smilehoe on 2008-07-23
Hi, I tried all the commands listed above. Same here, resulting package not found. I downloaded the GoogleEarthLinux.bin file from google.com and moved to /home/'user' before running the command 

chmod +x GoogleEarthLinux.bin
./GoogleEarthLinux.bin

The google-earth folder is now in /home which I think shouldn't be there. Would like to remove it and reinstall in the correct directory. Also how should I install a bin file that I downloaded manually to be in the same folder as in if I used apt-get?

Thanks!

Hardy-Heron
Amd64

---

### Post by smilehoe on 2008-07-23
While I browse through the google-earth folder, I noticed an uninstall file. Clicked and ended up my problem solved. As I just came from xp, was wondering is there anything like registry/library that would leave any trace?

Thanks!

---

### Post by unutbu on 2008-07-23
In general, there is no registry/library that you need to worry about when uninstalling programs. 

Most of the time it is best to take advantage of Ubuntu's excellent package manager, APT (via Synaptic, or apt-get, etc), by installing programs through their associated packages.
There is a googleearth package for example.

When you use the package manager, uninstalling is made very easy and all the appropriate files are removed for you by the package manager. For example:
```

sudo apt-get purge PACKAGE
```

When you install a program by running a command like ./GoogleEarthLinux.bin you are at the script-writer's mercy. It can deposit files anywhere it likes (though most are pretty civilized about this). Some programs come with uninstall scripts, but not all. If there is no uninstall script, then removing the files manually is all you can do; I know of no sure way to do this properly.

To solve this problem, there is the excellent checkinstall package. Once installed (suda apt-get install checkinstall), you can easily turn the installation scripts of other programs into .deb packages.

For example, if a package is usually installed with 

```
sudo make install
```

you can instead type

```
sudo checkinstall -D make install 
```

This will create a .deb package with which you can do many useful things:

To view the files that will be installed

```
dpkg --contents *.deb
```

To install
```

dpkg -i *.deb
```

To uninstall

```
dpkg -r PACKAGE
```

where PACKAGE is the name of the package.

---

### Post by smilehoe on 2008-07-24
Thanks. That really did help

---

