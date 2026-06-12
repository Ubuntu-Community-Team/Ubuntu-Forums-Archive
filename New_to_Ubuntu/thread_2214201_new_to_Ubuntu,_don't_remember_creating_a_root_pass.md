---
title: "new to Ubuntu, don't remember creating a root password."
date: 2014-03-30
forum: New to Ubuntu
---

### Post by daniel134 on 2014-03-30
Hello all, my name is Daniel and I am super new to Linux. I am taking a Linux class in college and Ubuntu is one of the distrobutions we are learning on, mostly command line stuff, it is part of Networking and Systems Admin. We are working on "Changing Identities" and "Special Permissions" in general. I have installed it on a box at home as a VM along with 6 other OS's. As I work through one of the problems in the book, I am instructed to "Log in three times using three virtual terminals: once as root, once as user1, and once as user2." (Users 1 and 2 have to be in different groups - that's a different question all-together.) When I attempt to "**su -**", it asks for my password. I tried my user password, but it says "authentication failure". As I already stated, this copy of Ubuntu is on my box at home and I don't remember creating a root password. Any help or suggestions?

---

### Post by QIII on 2014-03-30
By default there is no root password (in effect disabling the root account) in Ubuntu, and you elevate your privileges to accomplish tasks "as root" by using ```
sudo
```, not ```
su -
``` as you might in Fedora, for instance.

For graphical applications, you should use ```
gksudo
``` in Ubuntu or ```
kdesudo
``` in Kubuntu to avoid some potential problems with changing permissions on some files inadvertantly.

So Ubuntu is probably not the best to "log in as root" and we won't even allow discussions about how to log in to the graphical user interface at root in Ubuntu on the forums.

If you have something like Fedora in one of your VMs, that would be a good one to practice on.  But remember:  When you are logged in as root you are in danger if anyone happens to hack your machine while you are root.  Also, what you tell the machine to do it will do without question.  It will assume you know exactly what you are doing.

Cheers.

---

### Post by daniel134 on 2014-03-30
I tried the "sudo" command, but what I am trying to do is start a second terminal and switch to another account. Any account I have on my box - I have created for practice. The chapter is covering permissions, and the "su" command and "sudo" command are two of the commands we are working on. "Sudo" does not start a new shell, but "su" is supposed to. When I type "su -" or "su -l" I am asked for my password, I type my password and it says "Authentication failed". My book doesn't say anything about this, I guess they figure it will just work.

---

### Post by coldcritter64 on 2014-03-30
> **daniel134 said:**
> I tried the "sudo" command, but what I am trying to do is start a second terminal and switch to another account. Any account I have on my box - I have created for practice. The chapter is covering permissions, and the "su" command and "sudo" command are two of the commands we are working on. "Sudo" does not start a new shell, but "su" is supposed to. When I type "su -" or "su -l" I am asked for my password, I type my password and it says "Authentication failed". My book doesn't say anything about this, I guess they figure it will just work.

"Authentication failed" when using "su -" or "su -l" is because of the locked root account in Ubuntu. To use su (**s**ubstitute **u**ser, where if no user is defined substitute root user, hence it asking for a root password, which doesn't exist in Ubuntu's set up)  you need to do "sudo su" to get it to work and input your normal sudo password.

To get a root shell, using root's environment variables (the preferred way in Ubuntu, using sudo) is to do ```
sudo -i
``` you will then have a full root shell to work from after you input your user's sudo password.

---

### Post by QIII on 2014-03-31
Again:

If you want to use ```
su -
``` as your course materials suggest, I recommend using Fedora.  Fedora 20 is really solid and I use it as much as Ubuntu.

If one of the distros you are using in your course is Ubuntu, your instructors should know about the disabled root account by default in Ubuntu.

---

### Post by daniel134 on 2014-03-31
it turns out that I did need to use "sudo", the syntax was "sudo su -l". Thank you for your help.

---

### Post by su:bhatta on 2014-03-31
Great, you got that sorted out .

Please mark the thread as 'Solved' using the 'Thread Tools' at top right of this page.

---

