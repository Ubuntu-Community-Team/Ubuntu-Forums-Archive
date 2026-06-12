---
title: "Need permission to save file"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by drrwhistle3 on 2008-04-30
I have been instructed to save the following script as and in load_ata_piix in /usr/share/initramfs-tools/scripts/init-top/  .  I open gedit and copy and pated the following: 

#!/bin/sh
 PREREQ=""
 prereqs()
 {
        echo "$PREREQ"
 }
 case $1 in
 # get pre-requisites
 prereqs)
        prereqs
        exit 0
        ;;
 esac
 modprobe -Qb ata_piix


Then I tried to save as and it tells me I don't have permission.  How do I get permission?

---

### Post by Stabilityonitsown on 2008-04-30
to open a file with root use this
```
gksu gedit /your/directory/here/
```
Or if you want to have full permission when browsing through files use
```
sudo nautilus
```
I would love a [IMG]http://i197.photobucket.com/albums/aa37/Shoot3r101/post_thanksgif.png[/IMG] :)

---

### Post by master5o1 on 2008-04-30
```
gksu gedit /path/file
```

use this in Terminal to gain permissions for editing in gedit.

---

### Post by drrwhistle3 on 2008-04-30
ok that has worked the next instruction says to Execute the script:

$ sudo /usr/share/initramfs-tools/scripts/init-top/load_ata_piix

Next, rebuild the initrd so that the kernel will probe for the SATA driver before the USB driver:

$ sudo update-initramfs -u -k all

When I try to extecute the script it says: 
sudo: /usr/share/initramfs-tools/scripts/init-top/load_ata_piix: command not found

I know I saved the file.  What I think is that I am running in User@ubuntu-desktop:~$  shouldn't I do something different?  Maybe in root.  As you can tell this is my first experience at this

---

### Post by PeterJS on 2008-04-30
Does the file */usr/share/initramfs-tools/scripts/init-top/load_ata_piix* exist? does it have execute permission?

If it doesn't have execute permission, you can give it permissions with:
```

sudo chmod +x /usr/share/initramfs-tools/scripts/init-top/load_ata_piix

```

---

### Post by drrwhistle3 on 2008-05-01
I appreciate the help.  

Can someone explain the script, however?  I am trying to have an understanding of what I am doing (or what I am supposed to do).  Thanks

sudo chmod +x /usr/share/initramfs-tools/scripts/init-top/load_ata_piix

---

### Post by gerben1 on 2008-05-01
In Linux every file has some attributes that detrmine wheter you can Read, Write and Eexcute the file. You could call these the R, W and X attributes, if the R attribute is set you are allowed to read the file, if the W attribute is set you are allowed to write to the file and if the X attribute is set you can execute it. Now each file has three sets of these attributes, one determines what the "super user", often called root, is allowed to do with the file, a second that determines what the owner of the file can do with it and a third that determines what all others can do with it.

As an example, if you list the files in some directory with the command
```
ls -l 
```
you will see all the files in that directory and some details about the files, like how the read, write and execute permissions are set:
```

gerben@CC1184274-A:~/example$ ls -l
total 8
-rw-r--r-- 1 root   root   8 2008-05-01 14:41 fileA
-rwxrw-rw- 1 gerben gerben 8 2008-05-01 14:41 fileB

```
so you can see in this directory there are 2 file, fileA and fileB, and the permissions for those files are set different. Take a look at fileA, it's permissions are set as:
-rw-r--r--
which means that:
- super user (or root) is allowed to read the file and write to the file but not to execute the file
- the owner of the file is only allowed to read it
- all others are also only allowed to read it

now look at fileB, it's permisssions are set as:
-rwxrw-rw-
which means that:
- super user (or root) is allowed to read the file, write to it and to execute the file
- the owner of the file is only allowed to read it and to write to it
- all others are also only allowed to read it and to write to it.

Now, chmod is a program you can use to change the permissions of a file. This command
```
chmod +x /usr/share/initramfs-tools/scripts/init-top/load_ata_pi
```
means add the execute permission to this file (if you do the command as above execute permissions for root, owner and other will all be turned on)

often you have to do things in linux that require certain permissions because a bunch of files$ need to be written to and others need to be executed etc. what often happens when you just go ahead and try to do it, is that you get some message that the action could not be completed because something somewhere was not permitted. This is ussualy becasue you tried to do things that only the super user (root) is allowed to do, that is why you need to do it as Super user (which is what the sudo command does).

for example a normal user is not allowed to change the file permissions as in your case, so you need to do it as super user:
```
sudo chmod +x /usr/share/initramfs-tools/scripts/init-top/load_ata_piix
```
 "super user DO change permissions of load_ata_piix so that it can be executed"

---

