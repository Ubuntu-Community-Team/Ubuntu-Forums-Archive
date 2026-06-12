---
title: "Software Center and Update Manager not working"
date: 2013-08-19
forum: New to Ubuntu
---

### Post by volchanetskiy on 2013-08-19
Yesterday I tried to install some Python app on my system (13.04) by executing *setup.py install*. I did not succeed in installing it but then I found that I can't install/view/check updates with update-manager and install/delete packages though software-center. I found [this]("http://ubuntuforums.org/showthread.php?t=2050736") thread with similar output. I can still use apt-get and Synaptic so I tried to reinstall packages mentioned in that thread but it didn't help. Here is some lines from the output:
```
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.debian.apt': no such name
```
```
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 1
```

---

### Post by ian-weisser on 2013-08-19
That other thread seemed to be caused by a dying hard drive.
Are you saying you think you have a hardware fault?
If so, have you run a filesystem check (fsck) on your hard drive?

If it's not a filesystem error, then are you quite sure that apt-get had no errors at all?
Those error messages can be very helpful.

What new python application are you trying to install? Link, please. Does it have any dependencies?
If you uninstall the application, do Network Manager and Software Center work again?
If you reinstall the python3-dbus and python3-aptdaemon packages, do Network Manager and Software Center work again?

---

### Post by philinux on 2013-08-19
Yes apt-get errors needed.

Please run this in a terminal and post back if any errors.

```
sudo apt-get update; sudo apt-get upgrade
```

---

### Post by volchanetskiy on 2013-08-19
Thank you for reply. :D
> **ian-weisser said:**
> Are you saying you think you have a hardware fault?
If so, have you run a filesystem check (fsck) on your hard drive?
I don't think something is wrong there. But I run *touch /forcefsck* anyway. It was checking partition at boot but [*/var/log/fsck* still contains empty files]("http://askubuntu.com/questions/112907/where-are-fsck-results-logged-at-boot-time-after-forcefsck").
> **ian-weisser said:**
> What new python application are you trying to install? Link, please. Does it have any dependencies?
[http://code.google.com/p/please/wiki/Install](http://code.google.com/p/please/wiki/Install)
> **ian-weisser said:**
> If you uninstall the application, do Network Manager and Software Center work again?
*setup.py* with *install* or *uninstall* option fails. Nothing changed.
> **ian-weisser said:**
> If you reinstall the python3-dbus and python3-aptdaemon packages, do Network Manager and Software Center work again?
No... The same output again.
> **philinux said:**
> Please run this in a terminal and post back if any errors.
```
sudo apt-get update; sudo apt-get upgrade
```
There was no errors but no updates was found. I can install and delete packages with apt-get.

---

### Post by ian-weisser on 2013-08-19
Please show us *all* output that includes a failure message or error.
Those messages are very helpful.

---

### Post by volchanetskiy on 2013-08-19
Most output is in the attached text files.

---

### Post by sandyd on 2013-08-19
can you post the output of
```

sudo smartctl --test=short /dev/sda
#Wait a few minutes before running
sudo smartctl -a /dev/sda
```

thanks.

---

### Post by volchanetskiy on 2013-08-19
My HDD is pretty new...

---

### Post by volchanetskiy on 2013-09-13
Thanks everyone for help. Finally I figured out that problem was in AptDaemon. Executing *sudo aptd* gave me this error:

 ```
Traceback (most recent call last): 

   File "/usr/sbin/aptd", line 28, in <module> 
     import aptdaemon.core 
   File "/usr/lib/python3/dist-packages/aptdaemon/core.py", line 66, in <module> 
     from .worker import ( 

   File "/usr/lib/python3/dist-packages/aptdaemon/worker.py", line 56, in <module> 
     import pkg_resources 
   File "/usr/local/lib/python3.3/dist-packages/pkg_resources.py", line 621 
     except ResolutionError,v: 

                           ^ 
 SyntaxError: invalid syntax
```
Then I manually applied some changes to *pkg_resources.py* file from [this patch]("https://bitbucket.org/tarek/distribute/pull-request/7/fixes-for-python-3-compatibility/diff"). Now I'm able to use Software Center and install updates but I'm afraid that it will break again after any update affecting this file... I don't understand why it stopped working and what changes I made trying to install these apps.

---

