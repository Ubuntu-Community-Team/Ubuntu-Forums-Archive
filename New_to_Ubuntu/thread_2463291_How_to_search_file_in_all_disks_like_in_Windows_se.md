---
title: "How to search file in all disks like in Windows search"
date: 2021-06-08
forum: New to Ubuntu
---

### Post by joydipto on 2021-06-08
[COLOR=#222222][FONT=Verdana][SIZE=2]I am new to Ubuntu and I want to know how to search in all the disks for a file like in the windows (as shown in the pic) [ATTACH=CONFIG]288628[/ATTACH][/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2]I have a ssd which is partitioned and both Windows and Ubuntu boots from the ssd. I have an internal hdd where all my other files are stored and can be accessed using windows search.[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2]When I have to search for a document, let's say a book pdf located in Local Disk D:, I could have easily searched it in Windows by using the windows search. But in ubuntu I have to open [/SIZE][/FONT][/COLOR]**[COLOR=#222222][FONT=Verdana][SIZE=2]Files[/SIZE][/FONT][/COLOR]**[COLOR=#222222][FONT=Verdana][SIZE=2]and go to the individual partition of my hdd and then to that folder where that book's pdf is saved and then search for it.[/SIZE][/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana][SIZE=2]So is there any way to search for a file stored anywhere in my laptop(I prefer not to use the terminal for searching files).[/SIZE][/FONT][/COLOR]

---

### Post by ActionParsnip on 2021-06-08
If you mount the NTFS partition, you can then run:
```

sudo updatedb; locate -i *.pdf

```
This is how I do it...

---

### Post by Impavidus on 2021-06-08
You can limit your search to any directory. If you limit it to the root directory, you will search all mounted filesystems. So just make sure that the filesystems you want to search are mounted, then search.

In Windows, all NTFS filesystems are automatically mounted. This is not the case on Ubuntu.

---

### Post by TheFu on 2021-06-08
I use updatedb/locate all the time.  **sudo apt install locate** to install.  Locate only knows about filenames. It doesn't look inside.  It updates the filename DB daily, automatically using the updatedb command.  In my setup, it will not index portable/usb media, so I think if that is desired, the modifying the /etc/updatedb/config file will be needed.  OTOH, to get search results is instantaneous.  locate honors access permissions, so no result will be provided to any userid that doesn't have read permissions on the file to be provided in the results list.

Also use **recoll**, for looking inside files and file metadata for stuff.  This index takes much longer and is dependent on helper applications to access the internals for all the different types of files that aren't plain text.

I know that Mate has a file search tool included.  For me, the shell/cli is 1000x faster.

If you want a non-indexed solution, which will have to scan the entire directory tree for all disks connect, then 'find' is the only tool I know.  Compared to pre-indexed files, it is very slow as it traverses all the directory trees looking for patterns.  'find' isn't intuitive - to understand how it can be used, probably best to google for "top 50 find commands" or something like that.  Find can search for almost anything known about a file.  The name, type (file or directory or link), size, owner, group, permissions, creation, modification or access times and a bunch of other things.  When you have a 'find' command, plug it into **explainshell.com** to see what it really will do.  ExplainShell accepts commands, then looks up the command and the options in the manpages to show what each means. 

**find** is very powerful, but can be unwieldy.  The results can be passed onto other commands for processing, deletion or just saved to a file for later.

I use **find** to create an index of music files to build a playlist every week, then feed list into a player for background music while I work.

---

### Post by monkeybrain20122 on 2021-06-08
> **TheFu said:**
> I use updatedb/locate all the time.  **sudo apt install locate** to install.

.

Actually the package name is mlocate

It used to be installed by default but since 18.04(?)  I have to install it myself.

---

### Post by TheFu on 2021-06-08
```
apt search locate 
...
locate/focal 4.7.0-1ubuntu1 amd64
  maintain and query an index of a directory tree
...
mlocate/focal,now 0.26-3ubuntu3 amd64 [installed]
  quickly find files on the filesystem based on their name
...
```

Could have swore I checked the name. Over the years the name has been locate, updatedb, and mlocate.  Hummmm.  That's odd.
```
$ which locate
/usr/bin/locate
$ dpkg -S /usr/bin/locate
dpkg-query: no path found matching pattern /usr/bin/locate

```
Hummmm. Something is fishy.

---

### Post by fyfe54 on 2021-06-08
I have been using FSearch, currently in beta.

[https://github.com/cboxdoerfer/fsearch](https://github.com/cboxdoerfer/fsearch)

---

### Post by vanadium on 2021-06-09
The Ubuntu desktop includes an indexed search powered by tracker. That is configured to index and find files in your home folder. To use an external drive, you should mount it automatically during startup (instead of only when you click on it in files) and then add the mounted folder to "Search locations" in "Settings" - "Search". That "Search" works from the Application Overview as well.

Alternatively, you can search quite quickly by name in Files. This is a recursive search, i.e., search is from the current folder into all subfolders. If is sufficient to be in the root of the mounted drive to search it completely.

Obviously, because of how this works, the search will be faster if you are more closely to the target. So if you know the folder under which the file exist, it is best to first go there, then search the file. Once the file is found, you can open the folder where it resides with the shortcut key Ctrl+Alt+O (and of course also from the right-click menu).

---

### Post by Holger_Gehrke on 2021-06-09
@TheFu

> **TheFu said:**
> 
```
$ which locate
/usr/bin/locate
$ dpkg -S /usr/bin/locate
dpkg-query: no path found matching pattern /usr/bin/locate

```
Hummmm. Something is fishy.

Nope, that's as expected for a program which is under the control of the Debian alternatives system. /usr/bin/locate is a symbolic link to /etc/alternatives/locate which is a symbolic link to /usr/bin/mlocate. Those links are probably created in the post-install script so they are not part of any package ....

Holger

---

### Post by him610 on 2021-06-10
You might want to consider ***Catfish File Search***
I use it several times weekly. It may or may not be installed with your distribution, but it is in the ubuntu repository. It is one of the applications that are installed with Xubuntu.

---

