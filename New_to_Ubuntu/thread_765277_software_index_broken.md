---
title: "software index broken"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by Falc7 on 2008-04-24
I have fairly major problems it seems at the moment. It seems the add new software and install updates parts of my system are broken. When i installed some security and program updates i get error messages. 
When i download programs i get this error message:

E: soundconverter: subprocess post-installation script returned error exit status 139
E: avg75fld: subprocess post-installation script returned error exit status 1

The program i downloaded was the .ace file archive opener. After i get this error, it says the program was sucessfully installed, but when i try to unarchive something it says an error occured. When i click command line output it says nothing.

When i try and remove sound converter, it won't let me saying an error occured. 

When i click update manager it says

Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

So this happens:
wer@wer-laptop:~$ sudo apt-get install -f
[sudo] password for wer:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  soundconverter
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 438kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 112652 files and directories currently installed.)
Removing soundconverter ...

(update-desktop-database:7353): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing soundconverter (--remove):
 subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
 soundconverter
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by tamoneya on 2008-04-24
```
sudo apt-get clean
```

---

### Post by Falc7 on 2008-04-24
hm, nothing seems to happen in the terminal
wer@wer-laptop:~$ sudo apt-get clean
wer@wer-laptop:~$

---

### Post by tamoneya on 2008-04-24
it doesnt typically have any output i think.  What happens when you try the install now?

---

### Post by Falc7 on 2008-04-24
I still get this message when running update manager

Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

---

### Post by jmagsho on 2008-04-24
Have you tried uninstalling the .ace archive program, and then running the *sudo apt-get -f* command?  It sounds like you either have a missing dependency or something got stepped on or installed incorrectly...

---

### Post by Falc7 on 2008-04-24
yep, it makes no difference whether i have the ace program installed or not, i think that is a symptom rather than a cause. I am pretty sure it has something to do with soundconverter, when i look at the package in package manager it is highlighted red. But it won't let me uninstall it

---

### Post by spiderbatdad on 2008-04-24
```
sudo dpkg-configure -a
sudo apt-get install -f
```

---

### Post by Falc7 on 2008-04-24
wer@wer-laptop:~$ sudo dpkg-configure -a
[sudo] password for wer:
sudo: dpkg-configure: command not found

---

### Post by Oldsoldier2003 on 2008-04-24
> **Falc7 said:**
> wer@wer-laptop:~$ sudo dpkg-configure -a
[sudo] password for wer:
sudo: dpkg-configure: command not found

```
sudo dpkg --configure -a
sudo apt-get install -f
```

---

### Post by spiderbatdad on 2008-04-24
> **Oldsoldier2003 said:**
> ```
sudo dpkg --configure -a
sudo apt-get install -f
```

:oops:

---

### Post by Falc7 on 2008-04-24
wer@wer-laptop:~$ sudo dpkg --configure -a
wer@wer-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  soundconverter
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 438kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 112468 files and directories currently installed.)
Removing soundconverter ...

(update-desktop-database:7162): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing soundconverter (--remove):
 subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
 soundconverter
E: Sub-process /usr/bin/dpkg returned an error code (1)
wer@wer-laptop:~$

---

### Post by spiderbatdad on 2008-04-24
looks like you need to ```
sudo apt-get remove soundconverter
```based on the error message.

---

### Post by Falc7 on 2008-04-24
wer@wer-laptop:~$ sudo apt-get remove soundconverter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  soundconverter
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 438kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 112468 files and directories currently installed.)
Removing soundconverter ...

(update-desktop-database:7244): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing soundconverter (--remove):
 subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
 soundconverter
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by spiderbatdad on 2008-04-24
sorry about that. I see that was your first post. Maybe try with --purge option instead of remove. ```
sudo apt-get --purge soundconverter
```

Was soundconverter installed as part of another package? Is there another package that needs to be uninstalled?

---

### Post by Falc7 on 2008-04-24
Nope sound converter was just installed the normal way through add/remove applications. thanks for your time trying to help me with this :)

wer@wer-laptop:~$ sudo apt-get --purge soundconverter
E: Invalid operation soundconverter

---

### Post by Oldsoldier2003 on 2008-04-24
well here is something you can try:
first clear your apt cache
```
sudo apt-get clean
```

the go to /var/lib/dpkg/info and remove anything thats got soundconverter in its name
```
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
```

and if all your errors are cleared up you can move on to business.

---

### Post by Falc7 on 2008-04-24
I found 4 files with sound converter in the name, but i get this message when trying to delete them

"/var/lib/dpk...rter.postrm" cannot be moved because you do not have permissions to change it or its parent folder.

---

### Post by Oldsoldier2003 on 2008-04-24
> **Falc7 said:**
> I found 4 files with sound converter in the name, but i get this message when trying to delete them

"/var/lib/dpk...rter.postrm" cannot be moved because you do not have permissions to change it or its parent folder.

sorry i should have been more explicit. If you would rather use the Gui to delete the files and are using Ubuntu type ```
gksu nautilus
``` to launch nautilus as root/superuser. you will then be able to delete the files.

If you are doing it by command line just 

```
cd /var/lib/dpkg/info
sudo rm <filename>
```
inserting the correct filename in place of <filename>

---

### Post by spiderbatdad on 2008-04-24
You need to be superuser. You can use ```
gksu nautilus
``` to graphically move files in the root file system, but be very careful. You can break your system removing the wrong files.

---

### Post by Falc7 on 2008-04-24
thanks very much! All fixed 
Am i okay to install soundconvertner again later?

When looking updates like just then, is 'hit' a good thing?

---

### Post by Oldsoldier2003 on 2008-04-24
> **Falc7 said:**
> thanks very much! All fixed 
Am i okay to install soundconvertner again later?

When looking updates like just then, is 'hit' a good thing?

you can try again the servers are under high load right now, if it botches up again you now know how to fix it .

---

