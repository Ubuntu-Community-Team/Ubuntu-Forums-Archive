---
title: "Update won't complete"
date: 2012-04-06
forum: New to Ubuntu
---

### Post by mogibb1 on 2012-04-06
I have been trying to update Ubuntu and it will d/l the updates and when it is processing them it gives me this after extracting the templates:

Reading database ... 70%%
 (Reading database ... 75%%dpkg: unrecoverable fatal error, aborting: 
 reading files list for package 'python-dbus': Input/output error 
Error in function:  
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)

I have to boot into recover mode each time because it will not load any other way and I have no idea why. (I did have to put this HD into another laptop, however, it is the same make and model as the other one, but Ubuntu is giving me fits.) Any help is appreciated, thanks.

---

### Post by sandyd on 2012-04-06
> **mogibb1 said:**
> I have been trying to update Ubuntu and it will d/l the updates and when it is processing them it gives me this after extracting the templates:

Reading database ... 70%%
 (Reading database ... 75%%dpkg: unrecoverable fatal error, aborting: 
 reading files list for package 'python-dbus': Input/output error 
Error in function:  
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)

I have to boot into recover mode each time because it will not load any other way and I have no idea why. (I did have to put this HD into another laptop, however, it is the same make and model as the other one, but Ubuntu is giving me fits.) Any help is appreciated, thanks.
Your file list for python-dbus is corrupt.


[LIST=1]
[*]```
sudo rm /var/lib/dpkg/info/python-dbus
```
[*]```
sudo apt-get install python-dbus --reinstall
```
[/LIST]
The first command removes the corrupt file list.
The second command reinstalls the correct file list.

---

### Post by mogibb1 on 2012-04-07
After entering the reinstall instruction, this is what I got:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libtelepathy-farstSream1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 860 not upgraded.
Need to get 100.0 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main python-dbus i386 1.0.0-1ubuntu1 [100.0 kB]
Fetched 100.0 kB in 1s (51.9 kB/s)                      
(Reading database ... 75%dpkg-preconfigure: unable to re-open stdin: No such file or directory
dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'python-dbus': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

