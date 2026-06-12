---
title: "Permissions problem: can't log in as root"
date: 2012-04-02
forum: New to Ubuntu
---

### Post by jps2012 on 2012-04-02
I was getting "permission denied" error messages while trying to run a script, so I (foolishly) tried to remove all permissions on my home folder. 

Here's the command I ran: 

          **sudo chmod -R 777 / **

Terminal responded with a long status list, most of which looked like this:    
           *chmod: changing permissions of `/proc/19049/io': Operation not permitted * 
 Then I ran this command:     **$ sudo apt-get update**
 and got a message noting that I was not logged in as root: 
          *sudo: must be setuid root*  
 However, if I attempt to login as as root, I'm NOT asked for my password. I'm just reminded again that "must be setuid root." _It's an endless loop.  _
 Does anyone know a way out of that loop? How to set permissions back for root?

---

### Post by jps2012 on 2012-04-02
Just in case someone asks what the permissions are on "/sudo"

I ran this command (and Terminal returned the following):

  	 	 	 	 	 	             **$ ls -l /usr/bin/sudo**
 *-rwxrwxrwx 2 root root 144508 2011-05-29 22:51 /usr/bin/sudo*

---

### Post by coffeecat on 2012-04-02
This command:

> **jps2012 said:**
> 
Here's the command I ran: 

          **sudo chmod -R 777 / **

Has given 777 permissions to every single file in your system (except those for which you saw errors). This means that you have broken your system. In theory you could reassign correct permissions to every file in the system (thousands of them) using a live CD, but this would take months.

I suggest you backup your personal files and reinstall.

---

### Post by oldos2er on 2012-04-02
> **jps2012 said:**
> I was getting "permission denied" error messages while trying to run a script, so I (foolishly) tried to remove all permissions on my home folder. 

Here's the command I ran: 

          **sudo chmod -R 777 / **

Terminal responded with a long status list, most of which looked like this:    
           *chmod: changing permissions of `/proc/19049/io': Operation not permitted * 
 Then I ran this command:     **$ sudo apt-get update**
 and got a message noting that I was not logged in as root: 
          *sudo: must be setuid root*  
 However, if I attempt to login as as root, I'm NOT asked for my password. I'm just reminded again that "must be setuid root." _It's an endless loop.  _
 Does anyone know a way out of that loop? 

Backup any needed files and reinstall Ubuntu.

---

### Post by JKyleOKC on 2012-04-02
When you ran that first command, you effectively destroyed your system. By far the simplest way to correct things will be to use a Live CD to access your home directory (at /home/yourusername), copy it and all of its subdirectories onto an external drive, reformat the hard disk and reinstall from scratch, losing all data and installed software, then copy your data back from the external drive.

The problem you created is that many of the system maintenance tools, including sudo itself and its configuration files, must have limited permissions. By changing everything that you could to effectively unlimited permission for all, you triggered the internal self protection capabilities.

It's possible, of course, to undo all the damage, but you would have to do it for each and every critical file -- and I know of no exhaustive list of the files with such requirements.

Incidentally, your original command wasn't limited to just your home folder. It clobbered the permissions on almost every directory and file in your system. Frankly, I'm amazed that the system will even boot up in that condition!

---

### Post by jps2012 on 2012-04-02
Thanks, everyone. Wow. I've learned my lesson the hard way (to not attempt to change permissions on EVERYTHING). 

Is there some way to backup files that are separate from the operating system? I imagine that even if I knew how to sort them out in the GUI, if I did it file by file it would take ... a lonnnnnng time. 

In other words, is there a command for "backup everything that isn't the operating system itself"?

---

### Post by coffeecat on 2012-04-02
> **jps2012 said:**
> 
In other words, is there a command for "backup everything that isn't the operating system itself"?

No - your application files are pretty much well mixed in with the core operating system files. Besides, your application files will now have 777 permissions, which may cause problems with some or all of them.

If you are concerned by download bandwidth when applying upgrades and installing apps to the freshly installed system, you can backup and re-use the cached package files. Have a look in /var/cache/apt/archives/. All the *.deb files are your downloaded and cached package files for applications and updates. Back those up, transfer them to /var/cache/apt/archives/ in your new system and you will save some bandwidth. The new system will probably still need to download something but it will help.

---

### Post by jps2012 on 2012-04-03
Thanks, Coffeecat. I reinstalled 11.04 and I'm a little "wiser" now. The truth is that I'd rather keep working with the command line--which means taking some risks, occassionally--than go back to the purely safe (and passive) point-and-click administration. I've been very happy learning a new skill set, and I've never seen a better place than this forum when it comes to 'communal help.'

---

