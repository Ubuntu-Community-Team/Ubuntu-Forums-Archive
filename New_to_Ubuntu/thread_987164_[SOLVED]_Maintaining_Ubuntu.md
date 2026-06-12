---
title: "[SOLVED] Maintaining Ubuntu"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by sharkbite1414 on 2008-11-19
I know there are many things you need to do to maintain windows e.g. defraging the HDD, cleaning the registry, deleting those little bits of web pages IE saves etc. So is there any thing I need to do to maintain Ubuntu?

thanks!

Ubuntu Rules!!!:guitar:Windows Drools!](*,)

---

### Post by Titan8990 on 2008-11-19
I don't have to do anything to maintain my system like I do in Windows....

Defragging and cleaning the registry does not apply in Ubuntu. You can clear your firefox cache regularly, but I usually don't bother.

---

### Post by Idefix82 on 2008-11-19
You will almost never have to worry about defragmenting, since Ext3 doesn't become fragmented as long as your partitions have about 15% free space.

You will probably want to delete the cache of your web browser sometimes. Also, Synaptic usually keeps the downloaded files that it needs to install packages unless you tell it to delete them. You can do it by running
```
sudo apt-get clean
```
Personally, I have a separate partition for /var, where these temporary files are kept and Synaptic seems to delete the older ones automatically as soon as the partition becomes too full.

Also, if a package is installed automatically as a dependency of something and then later you uninstall this something, the dependencies are kept. To clear those out you can run
```
sudo apt-get autoremove
```
or follow this link to set up a filter in Synaptic that will show you the packages that are not needed any more:
[http://ubuntuforums.org/showthread.php?t=140920]("http://ubuntuforums.org/showthread.php?t=140920")
I prefer the filter since you are less likely to remove something that you do need after all if you get to have a look at it before removing it.

That's all the maintenance I can think of.

---

### Post by starcannon on 2008-11-19
I backup my /home folder to another Hard Drive once in awhile, not because Ubuntu requires it, but because hard drive failure happens, and I don't wanna be caught with my pants down. Thats about it though, keep the updates current, do clean upgrade installs (requires a seperate /home partition for that to be an easy operation). Thats about it though, I'm not pestered by a machine bogging down under the wieght of its operating system like I was back when I was using the other OS.

GL and Keep it Fun :)

---

