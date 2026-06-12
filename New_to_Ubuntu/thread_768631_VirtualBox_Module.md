---
title: "VirtualBox Module?"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by neoMAX on 2008-04-26
I'm trying to get VirtualBox running. At first, I used Add/Remove Applications for the installation, but it wouldn't load my virtual machine or iso. So I uninstalled it.

Now I'm in Terminal, and here's what I'm getting with aptitude:

```
Setting up virtualbox-ose (1.5.6-dfsg-6ubuntu1) ...
 * Starting VirtualBox host networking...                                [ OK ] 
 * Starting VirtualBox kernel module vboxdrv                                    
 [COLOR="Red"]*[/COLOR] No suitable module for running kernel found.

```

So clearly something has gone awry in the install. I've done a lot of googling but nothing's worked for me. Can someone help me out? Thanks!

---

### Post by neoMAX on 2008-04-26
Bump! I reinstalled from Add/Remove and rebooted and I still have the same problem.

---

### Post by neoMAX on 2008-04-26
Hourly bump train :P

---

### Post by _Stevie_ on 2008-04-26
you have to install module "virtualbox-ose-modules-2.6.24-16-generic".
then it should work. if "virtualbox-ose-modules-2.6.24-16-386" has been installed by the virtualbox install, purge it.

---

### Post by neoMAX on 2008-04-26
Okay, that's got me a step futher. Next is this new issue:

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..

I'm guessing I need to chmod that folder to a certain number :confused:

---

### Post by nquinnathome1 on 2008-04-26
Your user has to be a member of the vboxdrv group to use Virtualbox..

Go to Users and Groups (It's under 'Administration' on the System menu, unlock it, then hit 'Groups' and find the vboxdrv group. Click properties for that and tick your username under 'Group members', then log out and back in for it to take effect - you can now use VirtualBox.

---

### Post by _Stevie_ on 2008-04-26
not quite, have a look at this:
[http://ubuntuforums.org/showthread.php?t=593512](http://ubuntuforums.org/showthread.php?t=593512)

---

### Post by cabletie on 2009-08-26
Installed VirtualBox from the Ubuntu repository.

Got the "no suitable module for running kernel found" and "VirtualBox kernel driver not installed." errors.

Followed instructions to run "sudo /etc/init.d/vboxdrv setup" and the machine's response is that 'setup' isn't one of the commands that can be used with vboxdrv. Tried reinstalling, and a number of other cryptic commands that people have offered to try and fix it.

I finally uninstalled it and downloaded a .deb from the official Sun VirtualBox site:


[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

I grabbed the Ubuntu-appropriate one for my machine, and it installed cleanly.

Tried to start my VM, and lo and behold, it worked!
Thanks to all who have offered solutions, but I recommend downloading from the Sun site.

---

