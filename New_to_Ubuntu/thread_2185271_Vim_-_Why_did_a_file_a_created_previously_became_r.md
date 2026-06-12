---
title: "Vim - Why did a file a created previously became readonly when I open it now?"
date: 2013-11-01
forum: New to Ubuntu
---

### Post by zeynel2 on 2013-11-01
I have a file named euclid.txt. I open vim without sudo and the file is readonly. If I open vim as sudo vim, I can write to the file? Why is this? Is there a reference I can read to understand file organization and permissions?

---

### Post by Impavidus on 2013-11-01
All files (including directories, which are a special kind of file) have an owner, a group (which on Ubuntu usually is the personal group of the owner) and a set of permissions.These permissions specify what the owner, members of the group and other users can do. In your case you don't have permission to write to the file euclid.txt, but the root user has. The root user is the omnipotent user who has to be very careful to maintain the system. To make sure you don't have to be very careful at all times you usually don't log in as the root user. In fact, in Ubuntu the root account has been locked by default.

Your file is owned by root (I think) and ordinary users don't have permission to write to it. If it's not some system file (which won't be the case if it's in your home directory) it should not be owned by root. Files can become owned by root when you use the chown command or when you edit the file with a program running as root, as when running **sudo vim filename**. You can change ownership back to yourself with ```
sudo chown yourusername:yourusername filename
```But don't do that if it's a system file.

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by whitesmith on 2013-11-01
You are limited to read permission. You also need write. Open a terminal and type```
sudo chmod a+w euclid.txt
```Try searching for "ubuntupocketguide-v1-1.pdf" for a quick guide to the basics, or try Wikipedia.

---

### Post by Impavidus on 2013-11-01
Yes, it is either not owned by you or it lacks the write permission bit. Run **ls -l euclid.txt** in the directory with the file to find the exact cause.

---

### Post by zeynel2 on 2013-11-01
Thanks, whitesmith and impavidus. That's what I needed to know. I'll read the references. I changed the permissions with [COLOR=#000000][FONT=Ubuntu Mono]sudo chown yourusername:yourusername filename[/FONT][/COLOR] but I am still curious why a file that I created and edited before became owned by the root? Is it because I may have edited it while using vim as sudo?

---

### Post by Impavidus on 2013-11-02
Simply editing a file shouldn't change ownership, but copying, saving under a new name will. Just don't use sudo unless you need it and keep a clean separation between user files (in your home directory) and system files (outside of it).

---

### Post by BrunoLotse on 2013-11-02
Hi:) find files in your home directory owned by root ```
find ~/ -type f -user root
```Should you find any - change them ALL to be owned by yourself. root-owned files should not be in your home.

UNIX / Linux: Beginners Guide to File and Directory Permissions ( umask, chmod, read, write, execute )[http://www.thegeekstuff.com/2010/04/unix-file-and-directory-permissions/](http://www.thegeekstuff.com/2010/04/unix-file-and-directory-permissions/)
7 Chmod Command Examples for Beginners [http://www.thegeekstuff.com/2010/06/chmod-command-examples/](http://www.thegeekstuff.com/2010/06/chmod-command-examples/) 
12 Linux Chown Command Examples to Change Owner and Group [http://www.thegeekstuff.com/2012/06/chown-examples/](http://www.thegeekstuff.com/2012/06/chown-examples/)

You'll find lots interesting subjects on this site

Cheers,
Bruno

---

### Post by oldos2er on 2013-11-02
> **zeynel2 said:**
> Thanks, whitesmith and impavidus. That's what I needed to know. I'll read the references. I changed the permissions with [COLOR=#000000][FONT=Ubuntu Mono]sudo chown yourusername:yourusername filename[/FONT][/COLOR] but I am still curious why a file that I created and edited before became owned by the root? Is it because I may have edited it while using vim as sudo?

That could be. You haven't told us where in the file system this file is located. Normally any file outside of your home folder will have a different owner than your user, so you would need 'sudo' to edit it.

Please note what Impavidus said, because it's very important: [COLOR=#ff0000]But don't do that [i.e. run sudo chown yourusername:yourusername filename] if it's a system file[/COLOR].

---

