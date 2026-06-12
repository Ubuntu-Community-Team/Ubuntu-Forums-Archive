---
title: "'Strange' message at end of using terminal"
date: 2013-01-05
forum: New to Ubuntu
---

### Post by kabukiM0n0 on 2013-01-05
Hi!

Whenever I install something through the terminal, once it is has completed this message appears 
```
Error: "/var/tmp/kdecache-km" is owned by uid 1000 instead of uid 0.
kbuildsycoca4(7694) KConfigGroup::readXdgListEntry: List entry text/html in "/home/km/.local/share/applications/mimeapps.list" is not compliant with XDG standard (missing trailing semicolon). 

```

It doesn't seem to affect anything I am installing, but am curious as to what it is.

Thanks.

K.m

---

### Post by llamabr on 2013-01-05
Hard to say, since you don't put your input, but only your output.  But probably you're doing a sudo konsole or something.  Open your terminal normally, and then sudo the app, such as apt-get or whatever.

In any case, you can probably ignore it.

---

### Post by kabukiM0n0 on 2013-01-05
```
sudo apt-get install 
sudo apt-get purge
sudo aptitude
sudo apt-get update
sudo apt-get upgrade

```

For now I've only noticed it with them commands. Once the terminal finishes updating/installing/etc.. the message appears.

---

### Post by Bashing-om on 2013-01-05
kabukiM0n0; Hi !

What results if you edit in that semi-colon in the referenced file ?
And, I would take a look at the file permissions for the file :
> /var/tmp/kdecache-kmmaybe investigate why that file expects uid 0 to have access.
[INDENT][INDENT]hth <== BDQ

[/INDENT][/INDENT]

---

### Post by kabukiM0n0 on 2013-01-06
Is there a command see the file permissions? 

No idea what happens if I do add the semicolon - I don't know how to do it.

---

### Post by Bashing-om on 2013-01-06
kabukiM0n0;

To see the file permissions list the file with the "long" option:
```
ls -l /var/tmp/kdecache-km
```Probably pay to look at the permissions of the directories that hold the file too.
This tutorial explains the concept:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

To look at and edit a file use the default editor gedit.
First, though, make a back-up of the file - for whatever might happen.
```
cp /home/km/.local/share/applications/mimeapps.list  /home/km/.local/share/applications/mimeapps.list-bak  
```
Edit the file:
```
 gedit  /home/km/.local/share/applications/mimeapps.list
```Looking to see that each line ends with the same character (a semicolon).[INDENT][INDENT]clear(er) than mud ? <== BDQ

[/INDENT][/INDENT]

---

### Post by iMac71 on 2013-01-06
you might try to change the ownership of /var/tmp/kdecache-km by typing the following command in a Terminal window:```
sudo chown 0 /var/tmp/kdecache-km
```

---

### Post by kabukiM0n0 on 2013-01-07
> **Bashing-om said:**
> kabukiM0n0;

To see the file permissions list the file with the "long" option:
```
ls -l /var/tmp/kdecache-km
```Probably pay to look at the permissions of the directories that hold the file too.
This tutorial explains the concept:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

To look at and edit a file use the default editor gedit.
First, though, make a back-up of the file - for whatever might happen.
```
cp /home/km/.local/share/applications/mimeapps.list  /home/km/.local/share/applications/mimeapps.list-bak  
```
Edit the file:
```
 gedit  /home/km/.local/share/applications/mimeapps.list
```Looking to see that each line ends with the same character (a semicolon).[INDENT][INDENT]clear(er) than mud ? <== BDQ

[/INDENT][/INDENT]
```
km@km:~$ ls -l /var/tmp/kdecache-km
total 588284
drwx------ 3 km km     4096 Jan  5 05:10 akregator
drwx------ 2 km km     4096 Jan  5 15:14 favicons
drwx------ 2 km km     4096 Jan  5 07:53 help
drwx------ 2 km km   151552 Jan  6 13:36 http
-rw-rw-r-- 1 km km 10526816 Jan  7 11:40 icon-cache.kcache
drwx------ 3 km km     4096 Jan  5 04:48 kio_help
drwx------ 2 km km     4096 Jan  5 07:24 ksplashx
-rw-rw-r-- 1 km km  1497069 Jan  7 01:19 ksycoca4
-rw-rw-r-- 1 km km      504 Jan  7 01:19 ksycoca4stamp
-rw------- 1 km km       48 Jan  5 03:59 Personal Calendarrc
-rw------- 1 km km     2819 Jan  7 03:23 plasma-svgelements-DarkenCarbon
-rw-rw-r-- 1 km km 84213856 Jan  5 16:19 plasma_theme_air-netbook.kcache
-rw-rw-r-- 1 km km 84213856 Jan  7 11:40 plasma_theme_DarkenCarbon.kcache
-rw-rw-r-- 1 km km 84213856 Jan  6 13:15 plasma_theme_Elegance.kcache
-rw-rw-r-- 1 km km 84213856 Jan  6 13:11 plasma_theme_Ghost.kcache
-rw-rw-r-- 1 km km 84213856 Jan  7 10:55 plasma_theme_internal-system-colors.kcache
-rw-rw-r-- 1 km km 84213856 Jan  6 13:07 plasma_theme_oxygen.kcache
-rw-rw-r-- 1 km km 84213856 Jan  6 13:15 plasma_theme_PerlaNegra.kcache
drwx------ 4 km km     4096 Jan  5 05:38 plasma-wallpapers
drwx------ 2 km km     4096 Jan  6 00:31 thumbs
```

> **iMac71 said:**
> you might try to change the ownership of /var/tmp/kdecache-km by typing the following command in a Terminal window:```
sudo chown 0 /var/tmp/kdecache-km
```
Should the terminal answer in anyway? 
```
km@km:~$ sudo chown 0 /var/tmp/kdecache-km
[sudo] password for km: 
km@km:~$ 

```

---

### Post by fdrake on 2013-01-07
did you edite the file as suggested by Bashing-om by adding a ; at the end of the line?

---

### Post by iMac71 on 2013-01-07
> **kabukiM0n0 said:**
> Should the terminal answer in anyway? 
```
km@km:~$ sudo chown 0 /var/tmp/kdecache-km
[sudo] password for km: 
km@km:~$ 

```for a "verbose" output, modify the command as follows:```
sudo chown -v 0 /var/tmp/kdecache-km
```

---

### Post by Bashing-om on 2013-01-07
kabukiM0n0;

How are you looking ?
In respect to the file /var/tmp/kdecache-km: As the file is located in a "tmp" (tempoary ??) directory, I am going to "assume" -yeah we know what is said about that attitude- that upon shut-down of the system any files in that directory are no longer in existence. That is easy enough to test by making a "test"file in that directory and seeing that it does not survive a reboot. 
I am mystified on no output from the chown command; I would expect in this case to have seen "No such file or directory" However if the file existed, upon successful completion of the command, there would be no output . [INDENT][INDENT]hth <== BDQ

[/INDENT][/INDENT]

---

### Post by kabukiM0n0 on 2013-01-08
> **Bashing-om said:**
> kabukiM0n0;

How are you looking ?
In respect to the file /var/tmp/kdecache-km: As the file is located in a "tmp" (tempoary ??) directory, I am going to "assume" -yeah we know what is said about that attitude- that upon shut-down of the system any files in that directory are no longer in existence. That is easy enough to test by making a "test"file in that directory and seeing that it does not survive a reboot. 
I am mystified on no output from the chown command; I would expect in this case to have seen "No such file or directory" However if the file existed, upon successful completion of the command, there would be no output . [INDENT][INDENT]hth <== BDQ

[/INDENT][/INDENT]


It doesn't say anything anymore ... the terminal acts just fine. 
Maybe ```
sudo chown 0 /var/tmp/kdecache-km
```sorted it?
I'll give it a few days to see if anything iffy starts up again. 

Cheers mate.

K.m

---

### Post by iMac71 on 2013-01-08
> **kabukiM0n0 said:**
> It doesn't say anything anymore ... the terminal acts just fine. 
Maybe ```
sudo chown 0 /var/tmp/kdecache-km
```sorted it?
I'll give it a few days to see if anything iffy starts up again. 

Cheers mate.

K.mhaving given that command, you changed the uid from 1000 (which generated the error message) to 0.

---

