---
title: "sound converter uninstall problem"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by Falc7 on 2008-04-22
I have been having trouble installing and using programs through the add/remove programs menu recently, giving me an error about sound converter, a program i have downloaded.
So i thought i would uninstall and reinstall sound converter, but when i try to uninstall it i get this error message
E: soundconverter: subprocess post-removal script returned error exit status 139
And it says it has failed to uninstall.

edit: i tried to software update, but it says my program index is broken and to run a console command, but this gives me an error when i do it

wer@wer-laptop:~$ sudo apt-get install -f
[sudo] password for wer:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  soundconverter
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
2 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

---

### Post by Michael.Godawski on 2008-04-22
Close all other update and installation applications like add/remove or synaptic or the update manager. Now try again these commands.
```

sudo apt-get install -f
sudo dpkg --configure -a
```

---

### Post by Falc7 on 2008-04-22
wer@wer-laptop:~$ sudo apt-get install -f
[sudo] password for wer:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  soundconverter
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 438kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 112644 files and directories currently installed.)
Removing soundconverter ...

(update-desktop-database:7383): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing soundconverter (--remove):
 subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
 soundconverter
E: Sub-process /usr/bin/dpkg returned an error code (1)
wer@wer-laptop:~$ sudo dpkg --configure -a
Setting up avg75fld (7.5.51_a1243) ...
Installing 'avgd' service initscripts...
ln: creating symbolic link `/etc/init.d/avgd' to `/opt/grisoft/avg7/etc/init.d/avgd.all': File exists
dpkg: error processing avg75fld (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 avg75fld

---

### Post by Falc7 on 2008-04-22
If i try to remove sound converter through synpatic
E: soundconverter: subprocess post-installation script returned error exit status 139
E: avg75fld: subprocess post-installation script returned error exit status 1

---

