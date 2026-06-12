---
title: "Creating .deb packages"
date: 2008-06-23
forum: Packaging and Compiling Programs
---

### Post by L0tU5 on 2008-06-23
Hi, I belong to an internet cafe and I am tired of having to copy the games directory (eg. Quake4, Quake3, Doom3, Enemy Territory...) and all its components every time it needs to be reinstalled. So I got thinking about creating a .deb package that would do all the work (i.e. placing the game, creating the icons and menu entries)..
I found 2 methods on the net but no success due to the lack of step by step instructions..

If anyone could help me on the matter, it would be greatly appreciated.

---

### Post by Arlanthir on 2008-06-23
I'm no PRO, but I'll give it a shot!

Create a folder on your home called *PACKAGENAME*.
Inside, you're going to have 2 folders: *DEBIAN* and *usr*.

On *usr*, you recreate the files and folders you want your file system to have after install.
Meaning, if you want to have an application in /usr/share/myprogram
you would create a folder named *share* in *usr* and then another named *myprogram* in *share*. Something like this:

/home/you/PACKAGENAME
[INDENT]|
       |--- DEBIAN
       |--- usr
[INDENT]|
        |--- share
[INDENT]       |
               |--- myprogram
[/INDENT][/INDENT][/INDENT]


That's it for the data files. On to the DEBIAN folder.
The DEBIAN folder is used to provide package information.

Inside, it will only have a single textfile named *control*

Here is a template *control* file for you to work on:

```

Package: myprogram
Priority: optional
Section: games
Installed-Size: 91.3
Maintainer: L0tU5
Architecture: i386
Version: 0:0.5
Depends: libgtk2.0-0, python-gtk2
Description: A super program.

```


After all that, you're ready to build the package!
Fire up a terminal and issue the following command:

```

dpkg-deb -b PACKAGENAME

```

So, there you go, I hope I was clear =)
I think it's slightly handcrafted and there are probably more automatic ways, but this is the only one I know :P

**Notes:** Don't forget to change PACKAGENAME and myprogram to names of your choosing! About the menu entries, you'll have to create the .desktop files you want and place them in /usr/share/applications. Check that folder for some examples (open them with gedit!)

---

### Post by L0tU5 on 2008-06-23
Thanks for the reply... I will try this out.. This is the exact method as I have used before but it didnt work... ```
jared@jared-desktop:~/Documents/My_Programming/Debian/Quake4/Quake4$ sudo dpkg -i ./quake4_0.1-1_all.deb
(Reading database ... 240435 files and directories currently installed.)
Unpacking quake4-game (from ./quake4_0.1-1_all.deb) ...
dpkg-deb: file `./quake4_0.1-1_all.deb' is corrupt - bad magic at end of first header
dpkg: error processing ./quake4_0.1-1_all.deb (--install):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Errors were encountered while processing:
 ./quake4_0.1-1_all.deb
```

---

### Post by Keith Hedger on 2008-06-23
Arlanthir - Great I've just been looking for a quick explanation as to how to build a deb package so i can transfer some homebrew apps Thanks:):)

---

### Post by Arlanthir on 2008-06-23
> **L0tU5 said:**
> Thanks for the reply... I will try this out.. This is the exact method as I have used before but it didnt work... 

I never encountered a problem like that before... If you double-click the file to see the information, does it display it correctly?
Could it be that the archive was not compressed correctly!?
After running dpkg-build have you done something with the file?

---

### Post by L0tU5 on 2008-06-24
Well I have all the source in the correct order and I have changed it several times to try get it working but no luck. When I double-click it, it says "The package might be corrupted or you are not allowed to open the file. Check the permissions of the file." and exactly the same when I run in a root nautilus.

---

### Post by madjr on 2008-06-24
you could look into **debcreator**

[http://ubuntuforums.org/showthread.php?t=787209](http://ubuntuforums.org/showthread.php?t=787209)

---

### Post by L0tU5 on 2008-06-24
I want to create a debian package that makes the files of Quake4 copy into /usr/share/games/quake4 and icons and menu entries and so on. I want to do this for several other games too... Now how do I go about doing that?

---

### Post by Arlanthir on 2008-06-24
Could you try it with some simpler application? 
I'm really not seeing where it would not work :S

---

### Post by Johnsie on 2008-07-02
I tried this method and it worked great. Thanks.

---

### Post by pjwhite on 2008-08-01
I am looking through this and it all makes sense but all the other documents I have read on this mention that a rules file is important and does the actual installing?

I like this example am only trying to build a binary deb package from binaries, instead of from source (custom built things for a bunch of computers I maintain). 

To extend from this if I also add the cron.d file to PACKAGENAME/debian/ then that gets added to the crontab automatically? And similarily for the postinst script?

---

### Post by Arlanthir on 2008-08-01
I'm sorry, but I really can't help you there, what I posted is all I know and all I do with deb packages.
If you try and it works, post here so others with the same doubt will see the result ;)

---

