---
title: "Questions about users management"
date: 2021-02-15
forum: New to Ubuntu
---

### Post by nanoemp on 2021-02-15
Hi,
So I'm very new to Ubuntu, I have bene tasked with a installing and configuring a 20.04 Ubuntu. 
So everything is fine, but I would need to have 2 users, both with administrations rights (and different passwords), but independent. So they could not see/manipulate each others home/folder/files, the software that each one installs is not applied nor accessible from the other... etc

Is this possible at all? I have been doing some tests in the Ubuntu settings, but I have not been able to do it

Any advice would appreciated, thanks

---

### Post by Impavidus on 2021-02-15
Every user can set permissions on his own home directory and all files therein to grand or deny read, write and execute access of other users to those files and directories. However, an admin user (i.e., a user who can use sudo for arbitrary commands) can always override those permissions.

Software installed in your home directory may be accessible to you only, if you wish so. Software installed system wide may be executable only for specific users, but this is messy. Software installed in the normal way is executable for all users. And again, any admin user can override this.

Read this: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by Holger_Gehrke on 2021-02-15
No, this isn't possible. There's actually only one account with full administrative permissions ('root', the user with id 0). Other users with administrative rights are allowed to act as root temporarily through use of the 'sudo' (or 'pkexec') command. Since being root means having full access to everything on the system, it isn't possible to block one user who can act as root from accessing the files of another user. 

Also the normal ways of installing programs (through .deb or .snap packages) install programs for all users on the system. The only way of installing programs in such a way that only one user can access this software would be to install from source into subdirectories of the $HOME of the user, which would make them inaccessible to other users which don't have administrative rights.

The only way I can imagine doing something somewhat like that is two have to separate Ubuntus on the machine and select which one to boot using grub.

Holger

---

### Post by #&amp;thj^% on 2021-02-15
A quick look at possibles: [https://www.answertopia.com/ubuntu/managing-ubuntu-users-and-groups/](https://www.answertopia.com/ubuntu/managing-ubuntu-users-and-groups/)

---

### Post by grahammechanical on 2021-02-15
The first user installed during the install process has administrator privileges, That user can install other users and give them administrator privileges or not. Every user who has administrator privileges can administer the operating system. All of it. That is the privilege an administrator is given.

Perhaps you should think about having three users. One who is administrator and the other two who are standard users. Every installed operating system needs at least one administrator. Increase the number of users who have administrator privileges and the risk of malware being installed and viruses infecting the machine increases. A person does not need much skill to wreck a computer operating system even without administrator privileges. Fixing things is much more difficult. Some of us have learnt from experience that the easy fix is to reinstall.

I suggest that there be a partition for data with each user having their own data folder that only they can access. Or even their own partition. Then you can reinstall without touching the data partitions. Of course, the administrator will have access to those user data partitions/folders. 

Regards.

---

### Post by ActionParsnip on 2021-02-15
Use the sudo group to give full admin access. Users with the ability to use sudo have full access so will be able to "see" the other user's data and access the files. This is exactly the same in Windows where administrators over a system can access everything on the system.

---

### Post by nanoemp on 2021-02-16
Thank you all. All replies have been extremely useful.

Best regards

---

### Post by TheFu on 2021-02-16
> **nanoemp said:**
> Thank you all. All replies have been extremely useful.

Best regards

I think you need an OS that supports role-based administration to accomplish your needs. That is NOT Ubuntu.
If you can specifically limit the things that the 2nd admin user can do, say to 20 things, you may be able to restrict the admin elevated access to exactly those 20 things and nothing else.  Depending on those 20 things, a number of back doors which could provide full admin permissions could be possible, as many programs allow "shelling out". If the current userid has elevated to root privilege, then can open a shell from within that other tool, they can easily see other people's stuff and create a program to gain full admin access at any time in the future without using sudo.

Let's just say that when I only had 5 yrs of Unix admin experience, I doubt I could have secured a setup as described above.  I have done if for less than 5 specific needs and that did work out.  We ended up controlling exactly all programs, all options, all access for those users, however.

---

### Post by chrischang2021 on 2021-02-16
When I manage the group, user and permission at UNIX and Linux OP.


I use those command as below : You need to as superuser. You can study it how to use.
You need to carefully use it when you as superuser you can do anything include kill yourself system.


chgrp
chown
chmod

---

### Post by nanoemp on 2021-02-17
Thank you for the advice! At the end I think we'll just have an admin account and a local standard one. And maybe manage the permissions of particular folders individually. 

Thanks

---

### Post by TheFu on 2021-02-17
> **chrischang2021 said:**
> When I manage the group, user and permission at UNIX and Linux OP.


I use those command as below : You need to as superuser. You can study it how to use.
You need to carefully use it when you as superuser you can do anything include kill yourself system.

chgrp
chown
chmod

Most of the time, chown and chmod do NOT require sudo/admin access. chown does, always.  The owner of any file or directory is the only userid who can modify the group or change permissions ... except if we use sudo.  But sudo-abuse is all to prevalent these days and people really to bad things to their systems by not understanding Unix permissions.  There are thousands of Unix permissions how-tos/guides. Those all apply 100% to any Linux system. It is the same.

If anyone anywhere suggests using *chmod 777*, it is because they either don't understand permissions or they are careless with permissions. If you see that in an installation guide for anything, consider the author's other suggestions as suspect too.  Every system has 1 directory that is setup with permissions that look to be 777, but are subtly different:
```
drwxrwxrw**t** 21 root root   16384 Feb 17 09:57 ./
```
That 't' at the end changes everything. It forces the files inside to be deletable only by the userid who created them, not anyone in general. Still, it is best to avoid 777 permissions until you fully, completely, understand, what this really means. By then, you'll know there are better methods.

---

### Post by chrischang2021 on 2021-02-17
**TheFu Thanks you more detail and clearly to explain it, I agree it "avoid 777 permissions ", Why Linux system is safe ,because you only allow to do, superuser allow you do level.**

---

### Post by rsteinmetz70112 on 2021-02-17
You might be able to come close accomplishing what you want if you create at least 3 users and only allow one to sudo, then arrange groups so that one user can access certain programs and the other can access other programs. 

Or place each application in a group of its own then add those users you want to have access to to those groups. But if you give those users sudo access there are about a gazillion ways to get around it. 

Might it is also worth considering separate VMs for the different roles and restricting access to the VMs to those who need those things.

None of this would be simple.

---

### Post by TheFu on 2021-02-17
Let's break this down.

> So I'm very new to Ubuntu, I have bene tasked with a installing and configuring a 20.04 Ubuntu.
Installs aren't THAT hard. Configuring doesn't need much, but it depends on all sorts of things. Mainly what you want the system to be used for.  Ubuntu systems can do 50,000 things - actually, more.

> So everything is fine, but I would need to have 2 users, both with administrations rights (and different passwords), but independent.
2 users. Easy
2 users with sudo. Easy.  Different passwords. That is expected. Independent.  Not sure what you mean by that.  Unix systems can support 64K users, perhaps more. That includes your desktop Ubuntu. They share system resources, storage, RAM, CPU, so they aren't independent, but Unix does keep their process data separate unless they want to share. Groups of users commonly choose to share storage, for example.

> So they could not see/manipulate each others home/folder/files, the software that each one installs is not applied nor accessible from the other... etc
Well, if they aren't administrators, then users have control over the access to their HOME directory.  They can install programs separately, but that is not the Ubuntu way.  In general, software gets installed across the entire system by the administrator and anyone with an account can run it. The data files for that software is separate - per user. This is Unix.
However, if a user has admin rights, then they can elevate their current access and do almost anything to the system and other users and any data located on the system, if that is their desire.  But the admin needs to request this access and be authorized. Every time that happens, it is logged. There are easy ways for an admin user to change to a different userid - the change will be logged but commands after that are not.

> Is this possible at all? I have been doing some tests in the Ubuntu settings, but I have not been able to do it
At all? Sure. In the way you posted, no.
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) has more about this stuff. You say you are new, which is why I provided that link. It has lots of background along with commands, so you don't see what to type, but why and when.  Unix isn't about entering 20 commands to accomplish something. It is about understanding the underlying ways that things work, so you can accomplish brilliant things that were not expected.

As  rsteinmetz70112 says, you might be able to accomplish what you want using virtual machines.  However, the admin who controls running each VM on the host would be able to see everything in each guest VM unless there was full encryption and the hostOS admin didn't know the encryption keys.  I've not tried this, but I could see where that would work.  Have the VM host provide block storage to each guest VM and let your "users" have admin on their machine only. Don't allow any other users on each VM.  When the machine is running, the storage would be unlocked for the VM, but not for the host, so the host Admin wouldn't have access.  If you do this, you'll have many other challenges - like how to backup the systems and data efficiently.  I don't have a good idea for that, but I use "pull" backups from a network backup server to prevent malware/cryptoware from harming the backup storage.

If this is for some school assignment, I seriously doubt the intent is nearly as difficult as your posted question.

---

### Post by nanoemp on 2021-02-18
Hi all and thank you very much for taking the time for such comprehensive answers. I really appreciate that. It could be, but this is not school assignment. We do not have proper IT service but I like informatics, and I've been tasked to do this by my boss. Apart from the fairness of that, it is how it is, and I thank you for your help! Great community. I agree with you all that I should start learning from the bottom. All the links and comments are appreciated and I'm on it. My current thoughts now are an administrator account+standard account. Then from the admin account, limit the permissions of some folder, I'd say:
```
sudo chmod 0700 /home/username
```
And maybe the same over some folders in external hard disks. 

Just couple of questions provided that this approach is acceptable:
* How could I restore the permissions the way they were, if needed? "sudo chmod 0755" from the admin account?
* I could affirm that the "privacy" of the admin user is guarenteed this way, right? And that the "private things", including files and folders with changed permissions, and passwords, mails, of the admin user are not accessible with the standard. I realize now some of the questions may be against how Ubuntu works. My apologies and thanks again for your helpful advice, will keep reading and learning

---

### Post by TheFu on 2021-02-18
> **nanoemp said:**
> Hi all and thank you very much for taking the time for such comprehensive answers. I really appreciate that. It could be, but this is not school assignment. We do not have proper IT service but I like informatics, and I've been tasked to do this by my boss. Apart from the fairness of that, it is how it is, and I thank you for your help! Great community. I agree with you all that I should start learning from the bottom. All the links and comments are appreciated and I'm on it. My current thoughts now are an administrator account+standard account. Then from the admin account, limit the permissions of some folder, I'd say:
```
sudo chmod 0700 /home/username
```
And maybe the same over some folders in external hard disks. 

Just couple of questions provided that this approach is acceptable:
* How could I restore the permissions the way they were, if needed? "sudo chmod 0755" from the admin account?
* I could affirm that the "privacy" of the admin user is guarenteed this way, right? And that the "private things", including files and folders with changed permissions, and passwords, mails, of the admin user are not accessible with the standard. I realize now some of the questions may be against how Ubuntu works. My apologies and thanks again for your helpful advice, will keep reading and learning

Ubuntu user accounts automatically create a unique group that matches the username. This can be confusing.  The group name and the username do not have to be related, but they are completely different things.

Don't use **sudo** so much.  
The owner of any file/directory can change the permissions of that file/directory. So {username} can run this:
```
chmod 0700 /home/{username}
```
no sudo needed.
BTW, /home/{username} is only convention. It is not mandated or even hard-coded anywhere.  The password entry for every userid specifies the HOME directory for that user.  /home/ is nothing special.
```
drwxr-x--- 194 thefu   thefu   20480 Feb 17 19:46 thefu/
```
The first "thefu" is the owner.
The second "thefu" is the group.  
```
$ id thefu
uid=1000(thefu) gid=1000(thefu) groups=1000(thefu),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),120(lpadmin),132(lxd),133(sambashare),126(docker)

```
To get a list of the members to a group, use:  
```
getent group {name-of-group}
```
The getent tool understands local file-based users and whatever remote user store *has been configured* on the system, like LDAP or other directory services.  Most home users don't know about getent and would use something like 
```
grep {name-of-group} /etc/group
```

Anyways, TLCL book should be clear about users, uids, usernames, groups, gids, and groupnames before heading off into permissions.

If you want to put things back, the best way is to have automatic, daily, versioned, backups. There are at least 1000 reasons to have those.

All computers have a flaw when it comes to security.  If physical access is allowed, then someone else can always pull the HDD/SSD and connect it to another computer they control, then access anything they like on the disk. There's only one solution to mitigate that.  Whole drive encryption.  Heck, if I have 90 seconds alone with most Linux computers, I can force a reboot using a flash drive I carry with me, copy off any data I like (I'm root on my flash drive), and reboot the system back into the normal OS.  What's worse is that flash drive to accomplish this is distributed world-wide by 20+ Linux distros.  We call them "Installer ISOs".  Using an Installer ISO in a "Try Ubuntu" mode, provides all the tools and access we need, usually.

But if the storage inside the computer is encrypted using LUKs, then someone booting from a "Try Ubuntu" or any other distro flash environment can't gain access unless one of the passphrases used to unlock the storage is trivial. LUKS has 8 slots for holding passphrases, so 8 different people can use the same computer, but not share the disk unlock passphrase. I use 4 different unlock methods with my laptop.  One is a really long passphrase that I probably couldn't actually type manually. It is a backup for the others.  I have 2 yubikeys.  One is setup in a challenge-response way. I'm prompted by the yubikey with a challenge. If the correct entry is made, then the yubikey enters a response into LUKS to unlock the storage.  And the last 2 use other features of a yubikey along with a shorter passphrase that I know to create a long, 2-part, password entry that unlocks the storage.

Without encryption, all storage is open to anyone with minimal skills.  Just boot from your Ubuntu Installer ISO, choose "Try Ubuntu" from the menu and see what you can see.  BTW, this is a method commonly used to fix some startup and storage problems across all Linux systems, so you'll want to have a flash drive with the same release of Ubuntu as you run on your servers and workstations handy.

---

### Post by nanoemp on 2021-02-19
Thank you for all the helpful information.

Regards

---

