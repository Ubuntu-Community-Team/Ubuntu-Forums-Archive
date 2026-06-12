---
title: "mv command line between directories"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by mlotfi on 2008-11-12
Hi,

I am still a newbie working with command line, I had a folder called admin in a flash drive, I was trying to move it to usr/local/tomcat/webapps/

1) how to do it with the move command ?

2)this is what I did, the folder admin is not anymore in the flash drive, but I don't know where is it now :
 

mlotfi@majid:/$ ls
bin   cdrom  etc   initrd.img  lost+found  mnt  proc  sbin  sys  usr  vmlinuz
boot  dev    home  lib         media       opt  root  srv   tmp  var
mlotfi@majid:/$ cd media
mlotfi@majid:/media$ cd KINGSTON/
mlotfi@majid:/media/KINGSTON$ sudo mv admin/ ./usr/


Thanks.

---

### Post by fwojciec on 2008-11-12
> **mlotfi said:**
> Hi,

I am still a newbie working with command line, I had a folder called admin in a flash drive, I was trying to move it to usr/local/tomcat/webapps/

1) how to do it with the move command ?

2)this is what I did, the folder admin is not anymore in the flash drive, but I don't know where is it now :
 

mlotfi@majid:/$ ls
bin   cdrom  etc   initrd.img  lost+found  mnt  proc  sbin  sys  usr  vmlinuz
boot  dev    home  lib         media       opt  root  srv   tmp  var
mlotfi@majid:/$ cd media
mlotfi@majid:/media$ cd KINGSTON/
mlotfi@majid:/media/KINGSTON$ sudo mv admin/ ./usr/


Thanks.

My guess that what used to be called /media/KINGSTON/admin is currently called /media/KINGSTON/usr.

If you use full stop (.) in path that means "the current directory" -- so ./usr/ means current_directory/usr/

What you wanted was:

sudo mv /media/KINGSTON/admin /usr/local/tomcat/webapps

---

### Post by mlotfi on 2008-11-12
Thank you very match, you are right, it works now.
my question now why move using graphical user interface with cut aand paste does not work ?

thanks.

---

### Post by Joeb454 on 2008-11-12
Because you won't have sufficient privileges, you would need to run nautilus as root.

If you wanted to do it graphically, you could run ```
gksu nautilus
``` from a terminal or Alt+F2.

Though be aware you have access to any file on your system this way, and yes - I've broken my system doing that once ;)

---

### Post by taurus on 2008-11-12
Because your graphical interface doens't have root permission as default.  If you want to do cut and paste with nautilus, you have to start it with

```
**gksudo** nautilus
```

---

### Post by Idefix82 on 2008-11-12
Probably because you need root privileges. Start your file browser with
```
gksudo nautilus
```
if you want to move things of which you are not the owner (ie normally everything outside your home directory).

I must warn you that this is the less secure way compared to command line, since you now have the file browser open with full permissions. So nothing will stop you from deleting the whole file system by accidentally pressing the wrong button. Besides, it's slower, once you are comfortable with the command line.

---

### Post by mlotfi on 2008-11-12
Thanks lot for all your helps,

I just added the admin web application to tomcat, all the other examples are working fine except admin, is this has to do with permissions ? if so how to change it ?

Here is what I have :

mlotfi@majid:/usr/local/apache-tomcat-5.5.27/webapps$ ls -l
total 28
drwx------ 13 mlotfi mlotfi 4096 2008-11-12 10:56 admin
drwxr-xr-x  5 mlotfi mlotfi 4096 2008-08-28 23:10 balancer
drwxr-xr-x 21 mlotfi mlotfi 4096 2008-11-12 10:25 jsp-examples
drwxr-xr-x  4 mlotfi mlotfi 4096 2008-11-12 10:25 ROOT
drwxr-xr-x  4 mlotfi mlotfi 4096 2008-11-12 10:25 servlets-examples
drwxr-xr-x 12 mlotfi mlotfi 4096 2008-11-12 10:25 tomcat-docs
drwxr-xr-x  3 mlotfi mlotfi 4096 2008-11-12 10:25 webdav
mlotfi@majid:/usr/local/apache-tomcat-5.5.27/webapps$ 
mlotfi@majid:/usr/local/apache-tomcat-5.5.27/webapps$ 

thanks

---

### Post by bodhi.zazen on 2008-11-12
You change permissions with chown and chmod.

[uhelp]community/FilePermissions[/uhelp]

---

### Post by mlotfi on 2008-11-12
I am the administrator here in ubuntu, should this folder admin a problem when accessing it from the browser :
[http://localhost:8080/admin/](http://localhost:8080/admin/)


drwx------ 13 mlotfi mlotfi 4096 2008-11-12 10:56 admin
drwxr-xr-x 5 mlotfi mlotfi 4096 2008-08-28 23:10 balancer


how to use chown  and chmod to folder admin so I will have access to it from the web application ?

Thanks

---

### Post by bodhi.zazen on 2008-11-12
In ubuntu apache is run as the user www-data

So, 

chown root.www-data foo

or give the directory world readable permissions (so it can be read by apache, or www-data).

---

