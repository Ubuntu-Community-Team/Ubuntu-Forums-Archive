---
title: "permission issue after installation packaged application"
date: 2010-03-26
forum: Packaging and Compiling Programs
---

### Post by brijith on 2010-03-26
Hi all,

I have created a deb package out of python source file. deb file is working fine I could install it with out any error. but the problem is,when I run the installed application it could not access its configuration file. says no permission to access the file. 

Is there any method to give necessary permission the installation folder by doing any special coding in **debian/rules** file

---

### Post by Cork87 on 2010-03-26
Hi , 

Just use the normal file permissions via the command line. 

Here is an explanation how to use it : 

[http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html)

P.S. you need to be root.

---

### Post by SevenMachines on 2010-03-28
it would really depend on your rules file, if you're using debhelper it might be fixing permissions of your installed files, you can avoid this using something like
DEB_FIXPERMS_EXCLUDE = /usr/bin/myfile-to-exclude

if your using something like the 'install' command you might want to add a '-m' mode option to set the permissions.

if your still having problems then the more code or files you can post will make it more clear... probably :)

---

### Post by brijith on 2010-04-20
> **SevenMachines said:**
> 
DEB_FIXPERMS_EXCLUDE = /usr/bin/myfile-to-exclude


Where to give this line? In side the RULES files ?

---

### Post by SevenMachines on 2010-04-23
sorry, i missed your reply! yes, that command would go in the debian/rules file but it really depends on how your program is packaged whether thats the way to do it or not. If you post your packaging or give a link it would be easier to see.

---

### Post by brijith on 2010-04-23
Can we give multiple files to exclude from it, Or can we exclude the a directory.

My problem is when I developed the program I have no idea about this packaging. While running the program I am creating some temporary files in the same folder. Also I have given provision to edit configuration files though the program. So what happened after I packaged it was,the program is not working because it has no permission to create the temp file I mentioned earlier. Also those configuration files lacks the permission to edit.

---

### Post by SevenMachines on 2010-04-23
what you're trying to doesn't really sound like a packaging problem. if your program needs to edit files in system directories, it needs administrator privileges, you'll see programs popping up a password window to get sudo access for exactly this reason, or needing to be run as root. You're program rightly shouldnt be able to do this unless the user running it has administrator access.

---

