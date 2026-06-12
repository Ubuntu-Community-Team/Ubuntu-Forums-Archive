---
title: "Where do programs install by default and how do I change that location?"
date: 2012-12-03
forum: New to Ubuntu
---

### Post by Yelnoc on 2012-12-03
I just downloaded Skype, my first time downloading a program which was not included with the Ubuntu package.  Once downloaded I was taken to the Software Center, which prompted me to press Install.  I did so.  It installs.  It works.  And I have no idea where it is.  I cannot find it under the Home folder nor in my perusal through the drive.  I also apparently cannot right-click to access Properties like in windows (do things have properties in Ubuntu?).

Any and all help would be appreciated.  If you can't tell, I'm very much a noob; I just installed Ubuntu about an hour ago.  So if there's some sort of intro primer that covers this, feel free to point me me to it.

Thanks,
Yelnoc

---

### Post by deadflowr on 2012-12-03
Hi again, 

If using the default Ubuntu desktop, which should have a panel on the left-side with a couple of icons on it. Look at the top of the panel and you will see an icon with the Ubuntu logo, click it.
This is the dash. It is the ubuntu menu system. You can find your applications either by searching for them, or by navigating to the apps section.
To navigate the dash, look for the icons at the bottom of the dash screen, one looks like a house, another looks like a sheet with numbers and so on. The first is the dash home icon, the second is the application icon, the third is the files and folders icon and so on. Click on the app icon and it will list three sections, recently used, installed and download. Click the arrow next to download and it will alphabetically list all the installed apps.

A good first place to get basic help on Ubuntu is in the help section. You can find it easily by typing Help in the search bar in the dash.Or here:

[https://help.ubuntu.com/]("https://help.ubuntu.com/") 

Pick the version you're running and select desktop. This will be the exact same as is in your system.

---

### Post by Yelnoc on 2012-12-03
Thanks for the response again and the link to the documentation.  I'm afraid my question was phrased poorly.  I can find Skype to use it, what I want to know is where it was installed.  That's to say, what is the install path on the drive (the equivalent on Windows would for example would be C:\Users\Skype).

---

### Post by MadmanRB on 2012-12-03
Usually applications are stored in usr/bin
Sometimes /opt
I am not sure where skype would install to though, I dont use it.
And technically applications in linux dont just install in one place.
Usually binaries (the actual program) will go into user/bin, but other parts of the app go in other places such as usr/lib or something of that sort.

---

### Post by Yelnoc on 2012-12-03
> **MadmanRB said:**
> Usually applications are stored in usr/bin
Sometimes /opt
I am not sure where skype would install to though, I dont use it.
And technically applications in linux dont just install in one place.
Usually binaries (the actual program) will go into user/bin, but other parts of the app go in other places such as usr/lib or something of that sort.

Ok, that makes sense.  Of course Ubuntu works differently, it is a different operating system after all. 

I suppose there isn't an equivalent to the "properties" dialog box accessible by right-clicking an icon in Windows?  Is there a way, for instance, to change the picture/icon of a program in the tray thing with all the icons on the left of my screen?

---

### Post by deadflowr on 2012-12-03
> **Yelnoc said:**
> Ok, that makes sense.  Of course Ubuntu works differently, it is a different operating system after all. 

I suppose there isn't an equivalent to the "properties" dialog box accessible by right-clicking an icon in Windows?  Is there a way, for instance, to change the picture/icon of a program in the tray thing with all the icons on the left of my screen?

System files can only be changed by a root/superuser.

To change an applications launcher icon open a terminal
(ctrl = T):

```
gksudo nautilus /usr/share/applications
```

Right click on the application, drop down to properties and click on the icon in the properties, and find the icon you'd like to use.

Please note, the changes you make most likely will get wiped out if the program gets an update/upgrade, as this will overwrite the old file with a replacement.

The files in the /usr/share/applications are known as .desktop files.

gksudo is the version of sudo used to run root for graphical applications.


More reading enjoy:
[http://ubuntu-manual.org/]("http://ubuntu-manual.org/")

---

### Post by mamamia88 on 2012-12-03
> **deadflowr said:**
> System files can only be changed by a root/superuser.

To change an applications launcher icon open a terminal
(ctrl = T):

```
gksudo nautilus /usr/share/applications
```

Right click on the application, drop down to properties and click on the icon in the properties, and find the icon you'd like to use.

Please note, the changes you make most likely will get wiped out if the program gets an update/upgrade, as this will overwrite the old file with a replacement.

The files in the /usr/share/applications are known as .desktop files.

gksudo is the version of sudo used to run root for graphical applications.


More reading enjoy:
[http://ubuntu-manual.org/]("http://ubuntu-manual.org/")

or use a program called menulibre [https://launchpad.net/~menulibre-dev/+archive/devel](https://launchpad.net/~menulibre-dev/+archive/devel) then edit the .desktop entry.  click the app you want then go to the editor tab and type the path to the image file where it says icon= and then save

---

### Post by MadmanRB on 2012-12-03
or just use the standard menu editor (not included, but it does come in handy, its called alacarte)

---

### Post by agillator on 2012-12-04
There is a File Hierarchy Standard that you might take a look at: [https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard). Then realize it is not necessarily followed.

The short answer to your where question is 'wherever it wants to'. It also partially depends on your method of installation. If you use a package manager to install, then it is going to be installed wherever the person who built the package wants it to be installed. On the other hand, if you install by using the tar program to install a tarball ( tar.gz or tar.bz2, etc) you have some control - maybe. See the man page for tar.

Generally when you install a 'program' you are really setting up multiple files in multiple directories. You may be able to get a list from the home page of the program if there is one. The find command can also help if you know or can guess a part common to all the files. Looking at the manual page may help ( man xxxx). Near the end there may be a list of files. If you installed the program by a package manager, the package manager may have a command to show you the list of files it installed. For example, if you install a deb package using apt, apt-get, dpkg, etc. you can use the command 'dpkg-query -L <package-name> to see a list of files. For example, dpkg-query -L xterm will give you the list of files installed by the xterm package (if you have xterm installed, of course). 

So there is no simple answer to your question. I hope the above helps, though. Practically speaking I find the dpkg commands (and dpkg-query) and the find command are the most useful.

Now, why would you want to change the installation location? I ask because there may be another option. If you know where a file is located and just want to access it from a different location for whatever reason, you don't have to move the file. Put a link to it (ln command) in the new location. You can seem to have a copy of a file in a thousand places when actually you only have one copy to the file on the computer, just a thousand links or pointers to the file. Would that help you?

---

### Post by DuckHook on 2012-12-04
Installation locations on Linux systems are a bit of a mess. There are some conventions, as previous posters have pointed out, but packages can basically install themselves anywhere they want. One of the most difficult learning curves for me when I first started using Linux was the location of app files. I found the following very helpful:

In the graphical environment, use *catfish*. This is a graphical front end for the command line commands: *find* and *locate*. The latest version allows you to choose which command to use.

However, as so often happens in Linux, the most powerful methods involve the command line. My favourite is:

```
locate -b '\file_name'
```Substitute the file name of your app for "file_name". This will return a (usually) reasonably short list of results for the app or file. From there it's not too hard to figure out where the binary resides, usually through a short process of reduction and elimination.

---

### Post by mcduck on 2012-12-04
> **DuckHook said:**
> 
However, as so often happens in Linux, the most powerful methods involve the command line. My favourite is:

```
locate -b '\file_name'
```Substitute the file name of your app for "file_name". This will return a (usually) reasonably short list of results for the app or file. From there it's not too hard to figure out where the binary resides, usually through a short process of reduction and elimination.
It's even easier than that...
Find the executable file of a program:
```

which packagename
```

find where a program has installed files:
```
whereis packagename
```

...and, in case of desktop apps, you can of course always just open /usr/share/applications, which contains the launchers for all system-wide installed graphical applications.

---

### Post by DuckHook on 2012-12-04
*which* and *whereis* only work for well-behaved programs that install themselves through the repositories. For example, neither works for *google earth* that, if downloaded and installed from the google website, won't play nicely with *which* (actually, it was exactly this stupid ornery app that forced me to research and learn to use *locate*). I do agree, though, that you may wish to try *which* first before resorting to the more convoluted *locate*. Even *locate* might fail because it looks for the file name under a database, in which case, we would have to resort to *find*. Don't even want to go there for a new user.

---

### Post by monkeybrain2012 on 2012-12-04
> **deadflowr said:**
> System files can only be changed by a root/superuser.

To change an applications launcher icon open a terminal
(ctrl = T):

```
gksudo nautilus /usr/share/applications
```Right click on the application, drop down to properties and click on the icon in the properties, and find the icon you'd like to use.

Please note, the changes you make most likely will get wiped out if the program gets an update/upgrade, as this will overwrite the old file with a replacement.

The files in the /usr/share/applications are known as .desktop files.

gksudo is the version of sudo used to run root for graphical applications.


More reading enjoy:
[http://ubuntu-manual.org/](http://ubuntu-manual.org/)

You can copy the .desktop file to .local/share/applications in the home directory (and chown to username) then changes will not be wiped out when software get updated, catch is that now you have two launchers instead of one. You can delete the original one in /usr/share/applications but it will regenerate when program gets updated

@OP,

You can install programs in different directories if you compile from source and use the prefix= options, but this doesn't work with proprietary software such as Skype of course.

---

### Post by Yelnoc on 2012-12-04
Thanks to everyone for the excellent responses.  I have a lot of reading to do.   I have accepted that Linux is just different, and I don't really need to know *where *everything is so long as I know how to find my programs and files.  One thing I evidently need to learn is how to use (and even how to open up!) a/the terminal.

---

### Post by fyfe54 on 2012-12-05
From what I see, you want to be able to find and run Skype.

Click on the Ubuntu logo in the top left corner then start typing Skype.  When the Skype logo appears, click it to launch Skype.  While running, Skype will appear in the launcher - to keep it there for future use, right click on it and select "lock to launcher".

---

