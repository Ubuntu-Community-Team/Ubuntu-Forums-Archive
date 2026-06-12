---
title: "What's the Linux equivalent of Program Files?"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by 1337yit on 2008-10-29
In Windows, as most of you probably know, Programs generally install all of their data into Program Files. If I install a program from a .deb archive, or from synaptic, where do these files go, and where are they installed to?

In other words, what is the Linux equivalent of Program Files?

---

### Post by nothingspecial on 2008-10-29
usually /usr/bin but not always.

---

### Post by Nepherte on 2008-10-29
It's a little more complicated in Linux. The launcher of the program typically resides in /usr/bin, the main program mostly in /usr/share, /usr/local/share or /opt and libraries in /usr/lib. User preferences in a hidden map in their home directory /home/username/.applicationname. And in some cases, it might even be something else.

In general you don't really have to know where they're installed to as you are likely not going to mess with the installed files.

---

### Post by Cypher on 2008-10-29
Applications will put executables in /bin, /sbin, /usr/bin and /usr/sbin. Manually compiled applications usually go in /usr/local/bin.

If you installed a DEB file, then you can list the files in that package and see where all the files are by doing
```

dpkg -L <package name>

```
The package name is what you installed, if you don't know what the package name is, you can find it with
```

dpkg -l | grep <part of the package name>

```
This will list all the packages in the system and search for part of the name.

---

### Post by nothingspecial on 2008-10-29
Sorry speedy reply. Most of the config files ie how you set the app up to your needs will be in a hidden folder in your home directory. Hidden folders start with a .
 To view them press Ctrl + H or in Terminal
```

ls -a
```

---

### Post by igknighted on 2008-10-29
The actual binary (or the .exe, if you will) typically goes in /usr/bin, but might also end up in myriad other places.  The libraries (think .dll's, roughly) usually end up in /usr/lib.  Any system-wide configuration files (if you need sudo to run it, typically config files are here) involved typically go in /etc, while and user-specific configuration files (most desktop apps) go in your home folder as hidden folders (firefox config data goes in your home folder as .firefox, for example).

Linux groups files by what they do, rather than what application dumped them there.  That way libraries and other files can easily be shared, so there isn't a need for multiple versions of the same thing.

---

### Post by random turnip on 2008-10-29
I'm not 100% sure what you mean by Program Files in Windows, but I think I get what you're talking about.

The easiest way to see a list of you programs is to go to Applications > Add/Remove and then change the filter to show all categorys but only apps that you have already installed.  Here you will see everything that is installed on your ubuntu partition and be able to remove them as well.

---

### Post by Sarmacid on 2008-10-29
> **Cypher said:**
> Applications will put executables in /bin, /sbin, /usr/bin and /usr/sbin. Manually compiled applications usually go in /usr/local/bin.

If you installed a DEB file, then you can list the files in that package and see where all the files are by doing
```

dpkg -L <package name>

```
The package name is what you installed, if you don't know what the package name is, you can find it with
```

dpkg -l | grep <part of the package name>

```
This will list all the packages in the system and search for part of the name.

There's another way to see the files that a package has installed. Go to system->administration->synaptic package manager, there you can search for what you have installed, right click, properties and there should be a tab for installed files. Not sure if this works on things you haven't installed showing you where the files would go.

---

### Post by chrisod on 2008-10-29
I think an important point here is to work on getting yourself out of the Windows mindset. Linux is not like Windows, and trying to equate the two will just frustrate you in the long run by slowing down the learning process.

---

### Post by Kellemora on 2008-10-29
Hi 1337

In the DOZE, only a part of your Programs are stored in Program files, except for a few stand alone .exe programs that are self-contained.
There are files scattered all over your hard drive even to the Registry.

Linux tries to keep the files in Logical places for all programs, depending upon what that file in the program is designed to do.

Now if you meant where do you find a newly installed program, it should appear under Applications in one of the sub-categories there.  A Game would be in Applications Games, instead of Programs Games like in the Doze.

If the installer didn't state where to put it, it may end up under Applications Other.

Edited to add:  
I forgot to mention that you can Add your Own Names to the Applications drop down list as well.  I have one named Accounting for my various accounting and inventory, payroll, accounts handling programs, etc.
This is done by Right Clicking on Applications and selecting Edit Menu's!

TTUL
Gary

---

### Post by SunnyRabbiera on 2008-10-29
This is how I learned the linux directory structure:

Home= My Doccuments
Computer= My computer
usr/bin= Program Files (usually)


This might help too:
[http://slashmedia.wordpress.com/2007/12/23/linux-directory-structure/](http://slashmedia.wordpress.com/2007/12/23/linux-directory-structure/)

---

