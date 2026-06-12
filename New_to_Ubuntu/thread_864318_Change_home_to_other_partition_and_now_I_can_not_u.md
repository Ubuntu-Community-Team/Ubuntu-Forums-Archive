---
title: "Change /home to other partition and now I can not use Evolution and other programs"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by jontxu01 on 2008-07-19
Hy, 
I'm new to Ubuntu and I have a problem with the permissions of /home directory.
I change the home directory from the main partition to a new one and now I can not open or use the information on home because every time I try to open a program the system tell me that I don't have permission to modify the /home folder.
For example every time I try to open evolution the software tell me "The application "Evolution" attempted to change an aspect of your configuration that your system administrator or operating system vendor does not allow you to change. Some of the settings you have selected may not take effect, or may not be restored next time you use the application."
After that evolution close.

Please help, I have all mi mails in evolution and I don't know what to do.

Thanks

---

### Post by JillSwift on 2008-07-19
Probably you need to change the ownership of your files back to you. In a terminal window, type:```
sudo chown -R <username>:<group> /home/<username>/*
```<username> is your login name, and <group> is going to be the same name.

You may also need to do this as well:```
sudo chown -R <username>:<group> /home/<username>/.*
```to get your "invisible" setup files. I can't remember right now >.>;

---

### Post by jontxu01 on 2008-07-19
Thanks for the quick replay, I've done what you tell me but Evolution continue to give me th same problem, there is something more I can do to solve it?

---

### Post by jontxu01 on 2008-07-19
Ok, seems that everything is working now, I forget to put the second line you give me, Evolution works, the problem now is in the beginning of the sesion after I put the user and the password it give me the next message:

User's $HOME/.dmrc file is being ignored. This prevent the default session and lenguage from being saved. Files should be owned by user and have 644 permissions. User's $HOME directory must be owned by usr and not writable by other users.

Do you know what it is about and how I can fix it?

---

### Post by linfidel on 2008-07-19
> **jontxu01 said:**
> Hy, 
I'm new to Ubuntu and I have a problem with the permissions of /home directory.
I change the home directory from the main partition to a new one and now I can not open or use the information on home because every time I try to open a program the system tell me that I don't have permission to modify the /home folder.
For example every time I try to open evolution the software tell me "The application "Evolution" attempted to change an aspect of your configuration that your system administrator or operating system vendor does not allow you to change. Some of the settings you have selected may not take effect, or may not be restored next time you use the application."
After that evolution close.

Please help, I have all mi mails in evolution and I don't know what to do.

ThanksWhat method did you use to change the partition?  

644 permissions refer to the command "chmod", where 644 represents the permissions for owner, group, and world, in that order.  For each number, it is an octal representation, where you add up three "flags" for Read, Write, Execute permission.  Sounds complicated, maybe, if you're not a programmer.  But here's the formula (R = Read, W = write, and X = execute).  Binary octal numbers from 0 to 7 are 000, 001, 010, 011, 100, 101, 110, 111.
Useful examples:    111 (7) = RWX;      101 (5) = RX (read-only);  etc.
644 means 
RW, but not execute for your files.  Script files will not run with this.
R, but no WX for group and world.  This means Read-only, no execute.

The thing is, you can't mark every file this way, or no scripts will run, like .bashrc.  But to mark some of them, use the command "chmod 644 *filename*".

The best way would have been to copy the permissions along with the files using the "p" switch with cp, something like:
*cp -pr /mnt/home/joe /home/username*

Or use "dd" or tar.

---

