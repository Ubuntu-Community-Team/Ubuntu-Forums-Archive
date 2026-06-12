---
title: "Permissions problems"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by Toco on 2008-05-18
When i download something to desktop it downloads fine but doesn't show up on my desktop and i have to use the command 'gksudo nautilus' and go to the /home/toco/desktop in order to see the files and then change the permissions on them.  I also have to move them from nautilus to my desktop to get them to show up.  I've tried changing the default download folder to a different folder in my /home/toco/ and it works fine.  i've also tried to change the permissions on 'desktop' to toco instead of root and that didn't help either

also with wine.  i installed a program and the link did the same as downloaded files from firefox.

how do i fix this so it doesn't do this anymore

---

### Post by jimbren on 2008-05-18
your Desktop folder is ownded by root?  

From a terminal, try this within your home directory:
```
sudo chown yourusername:yourusername *.*
```

That will give you ownership of all files in your home directory.  Once you've done that, let's see what happens when you download files again.  You shouldn't have to open nautilus as root, that's for sure.

jimbo

---

### Post by mikewhatever on 2008-05-18
Do you use XFCE/Xubuntu? Could it be that you run Firefox as root? Can you post the output of ,ls -l /home/toco/Desktop. Permissions should not be the problem, because by default you have full rights in your home directory.

---

### Post by Toco on 2008-05-18
to jimbren i tried that cmd and it said invalid usergroup.

To mikewhatever:

toco@toco-desktop:~$ ls -l /home/toco/Desktop
total 28
drwxrwxrwx 1 root root     0 2008-05-18 11:24 files
-rw------- 1 root root 28204 2008-05-18 14:31 ubuntu-8.04-desktop-i386.iso.torrent

the files folder is a network folder (smb) on a different computer.

the torrent is something i just downloaded.

when i did the 'gksudo nautilus' cmd i went in and changed permissions of desktop from root to 'toco'.


edit:  also there is a drive (same symbol as when you plug in a usb thumb drive) labeled as desktop that i can't get rid of and i don't see in nautilus

---

### Post by spiderbatdad on 2008-05-18
> **Toco said:**
> to jimbren i tried that cmd and it said invalid usergroup.

Of course this post author did not literally mean "yourusername." You would substitute your actual user name in the command like :```
sudo chown toco:toco *.*
``` if your login name is "toco." If your login name is Toco, then you would substitute like: ```
sudo chown Toco:Toco *.*
```

---

### Post by Toco on 2008-05-18
> **spiderbatdad said:**
> Of course this post author did not literally mean "yourusername." You would substitute your actual user name in the command like :```
sudo chown toco:toco *.*
``` if your login name is "toco." If your login name is Toco, then you would substitute like: ```
sudo chown Toco:Toco *.*
```

i changed it but i did ```
 sudo chown toco:(password) *.*
```

i get this now: ```
toco@toco-desktop:~$ sudo chown toco:toco *.*
chown: cannot access `*.*': No such file or directory
```

---

### Post by spiderbatdad on 2008-05-18
take a look at```
ls -l
```to see the owner of the files in your home directory

---

### Post by Toco on 2008-05-18
```
toco@toco-desktop:~$ ls -l
total 36
drwxrwxrwx 1 toco toco    0 2008-05-18 14:31 Desktop
drwxr-xr-x 2 toco toco 4096 2008-05-17 22:33 Documents
lrwxrwxrwx 1 toco toco   26 2008-05-17 22:29 Examples -> /usr/share/example-content
drwxr-xr-x 4 toco toco 4096 2008-05-18 00:55 here
drwxr-xr-x 2 toco toco 4096 2008-05-18 13:26 internet Downloads
drwxr-xr-x 5 toco toco 4096 2008-05-18 02:50 Music
drwxr-xr-x 2 toco toco 4096 2008-05-18 01:35 Pictures
drwxr-xr-x 2 toco toco 4096 2008-05-17 22:33 Public
drwxr-xr-x 2 toco toco 4096 2008-05-17 22:33 Templates
drwxr-xr-x 2 toco toco 4096 2008-05-17 22:33 Videos
drwxr-xr-x 2 toco toco 4096 2008-05-18 02:37 vmware
```

i honestly think firefox is running as root. instead of toco

---

### Post by spiderbatdad on 2008-05-18
ah...you can add the -a flag to show "all" folders, incliding those hidden:
```
ls -al
``` Or navigate to Home Folder and select View>>Show Hidden Files. The go to .mozilla/firefox and right click on the folder Properties>>Permissions will show you the Owner.

---

### Post by Toco on 2008-05-18
> **spiderbatdad said:**
> ah...you can add the -a flag to show "all" folders, incliding those hidden:
```
ls -al
``` Or navigate to Home Folder and select View>>Show Hidden Files. The go to .mozilla/firefox and right click on the folder Properties>>Permissions will show you the Owner.

did that and i was the owner so i didn't bother changing it.

its showing the files now (donno why).  but it has a lock in the upper right corner and an x in the bottom right corner.  when i right click the file it says the owner is 'root'

---

### Post by spiderbatdad on 2008-05-18
so which folder is owned by root, .mozilla or firefox?

To change owner of firefox: ```
sudo chown -R toco:toco /home/toco/.mozilla/firefox
```

Edit: make sure -R flag is used, not -r

---

### Post by drubin on 2008-05-18
The reason that the command 
```
sudo chown toco:toco *.*
```
wasnt working was because that looks for files/folders that have a "." in them. 

try this
```
sudo chown toco:toco *
```

---

### Post by spiderbatdad on 2008-05-18
> **rubinboy said:**
> The reason that the command 
```
sudo chmod toco:toco *.*
```
wasnt working was because that looks for files/folders that have a "." in them. 

try this
```
sudo chmod toco:toco *
```

WHAT? why don't you try that yourself?

---

### Post by drubin on 2008-05-18
> WHAT? why don't you try that yourself?

You must have read it before i changed it. I noticed my stupidity....

---

### Post by spiderbatdad on 2008-05-18
> **rubinboy said:**
> You must have read it before i changed it. I noticed my stupidity....

I do that myself all the time :)
I believe his problem is only with the firefox directory, so to change that directory and all the files recursively, chown should be run with the -R flag. you can't just * on directories. And the command need a path:
```
sudo chown toco:toco -R /home/toco/.mozilla/firefox
```

---

### Post by drubin on 2008-05-18
Firstly is it not  
> sudo chown **-R ** toco:toco /home/.mozilla/firefox
The option before the owner
> chown --help
Usage: chown [OPTION]... [OWNER][:[GROUP]] FILE...

But if there is an owner issue with his home directory should he not just do 
```
sudo chown -R toco:toco /home/toco/
```

And re-owner his home directory??

---

### Post by spiderbatdad on 2008-05-18
> **rubinboy said:**
> Firstly is it not  

The option before the owner


But if there is an owner issue with his home directory should he not just do 
```
sudo chown -R toco:toco /home/toco/
```

And re-owner his home directory??

This would work:```
sudo chown -R toco:toco /home/toco/*
```

---

### Post by Toco on 2008-05-18
alright.  i used  ```
sudo chown -R toco:toco /home/toco/*
```

and it changed the existing files from root to me.  but when i tried downloading a new file it is owned by root again.

the mozilla directory is owned by me and i didn't change that it was like that to begin with.  also tried even though i alraedy owned it ```
sudo chown toco:toco -R /home/toco/.mozilla/firefox
```

and restarted firefox with no luck

---

### Post by spiderbatdad on 2008-05-18
> **Toco said:**
> alright.  i used  ```
sudo chown -R toco:toco /home/toco/*
```

and it changed the existing files from root to me.  but when i tried downloading a new file it is owned by root again.

the mozilla directory is owned by me and i didn't change that it was like that to begin with.  also tried even though i alraedy owned it ```
sudo chown toco:toco -R /home/toco/.mozilla/firefox
```

and restarted firefox with no luck
It is possible the package you are downloading was archived in such a way that it specifies root as owner. Does this happen with all downloads or just a particular file you are getting somewhere?

---

### Post by Toco on 2008-05-18
> **spiderbatdad said:**
> It is possible the package you are downloading was archived in such a way that it specifies root as owner. Does this happen with all downloads or just a particular file you are getting somewhere?

across the board multiple ubuntu torrent files, .zip files, .rar files even when i extract a zip/rar file instead of saving it and copy the file onto the desktop it's owner is 'root'

---

### Post by spiderbatdad on 2008-05-18
can you post output:```
id toco
```

---

### Post by Toco on 2008-05-18
```
toco@toco-desktop:~$ id toco
uid=1000(toco) gid=1000(toco) groups=1000(toco),4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),29(audio),30(dip),44(video),46(plugdev),105(scanner),107(fuse),109(lpadmin),115(admin),124(sambashare)
```

---

### Post by spiderbatdad on 2008-05-18
just don't know. If you have changed the ownership of all the folders in your home directory to toco, I can't think of any reason ownership of downloads is root, unless you are running firefox from the terminal with sudo.

---

### Post by Toco on 2008-05-18
i tried to use sudo firefox and when i dled a file it's owner was still 'root' but it didn't have the x in the bottom left (donno what that is) like when i downloaded it without running sudo.

also installed ff 2 and it still did it.   i have ubuntu 8.04 btw.

when i download to other folders besides my desktop it works fine and i'm the owner.

---

### Post by Toco on 2008-05-20
just wanted to post that i found the problem for this.  I have a windows machine which has a shared folder that i connect to and since the 'connect to server' under places wasn't working right i googled it and found this guide.  [http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)

when i unmounted the volume i could have full control of my firefox downloads. (also a note i messed up my install of ubuntu and reinstalled it.  during the process i could download files to desktop before i mounted the windows shared folder but not afterwords. guess it pays not to do things the same way every time)

---

