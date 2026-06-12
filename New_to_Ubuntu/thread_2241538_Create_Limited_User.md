---
title: "Create Limited User"
date: 2014-08-26
forum: New to Ubuntu
---

### Post by ben5 on 2014-08-26
I want to set up a bunch of Xubuntu Desktops where the main user is "limited".  Much like a windows "limited" user.  They have no way to install new programs, etc.   And preferably only be able to run putty or firefox... though that part is a little less important. 

What is the easiest way?

---

### Post by deadflowr on 2014-08-26
I don't run xubuntu, but this might help
[http://docs.xubuntu.org/1304/administrative-tasks.html](http://docs.xubuntu.org/1304/administrative-tasks.html)
Most *bunutu's allow you to add users either as an admin or normal user.
An admin can install and change the system. A normal user cannot.
Typically a normal user is called something like standard, desktop or simply normal use.
Admins are almost always called admin, or administrator.

Hopes this helps to get you started.

---

### Post by JKyleOKC on 2014-08-27
> **ben5 said:**
> I want to set up a bunch of Xubuntu Desktops where the main user is "limited".  Much like a windows "limited" user.  They have no way to install new programs, etc.   And preferably only be able to run putty or firefox... though that part is a little less important. 

What is the easiest way?The simplest way to do this is to not enter the main user's name when you install Xubuntu. Instead, enter a cryptic name known only to you -- definitely NOT the Windows standard of "Administrator" although that will be its purpose. Then after the installation is complete, log in using that name and its password, and from the system menu select "Users and Groups" to create the main user. It will automatically be a limited user unless you explicitly set it to have administrative privileges.

They will still be able to install new programs, but only in their own very limited home directory. They will not be able to make any kind of system changes. Note that programs requiring system-wide configuration usually simply refuse to install under these conditions, but that will depend on the individual program, not on the Xubuntu system.

In all flavors of Ubuntu, the very first user created at install time becomes a member of a special "group" that is able to modify system settings and install new programs. Users added later do not automatically gain access to that group. Even the first user has to jump through special hoops to make changes, much like Windows' "Run as..." feature. Nobody has the ability to make immediate system changes; many other flavors of Linux require that one be logged in as the super user "root" and once that's done, any system-wide change can take immediate effect. Thus you may see many web postings referring to "root" -- but Ubuntu has put a bit more of a barrier in place.

Restricting the "limited" user to only a few programs can be done using AppArmor, but I can't help much there since I've never used it and the documentation makes it look rather tedious to set up.

Hope this helps!

---

