---
title: "Where are the programs?"
date: 2012-12-15
forum: New to Ubuntu
---

### Post by Troooppo stefano on 2012-12-15
Hello.

In xubuntu, in which folder will i find all the applications? In Windows they were in Programs...

And wich extension is equivalent to Windows'  .exe ?

Thank you!

---

### Post by ibjsb4 on 2012-12-15
Look in /usr/share/applications

---

### Post by JRV on 2012-12-15
/usr/share/applications holds the launchers for programs, not the actual programs. 
The launchers are .desktop files.
In linux a program does not need a file extension.
Use the "which" command to find the location of a program.
```

which bash

``` 
returns "/bin/bash"
```

which firefox

```
returns "/usr/bin/firefox"

---

### Post by Cheesemill on 2012-12-15
> **Troooppo stefano said:**
> In xubuntu, in which folder will i find all the applications? In Windows they were in Programs...
Linux isn't the same as Windows.
Instead of programs living in a single directory the files that make up an applications are spread over the hard drive depending on their purpose. Program binaries are usually in /usr/bin, program icons are in /usr/share/icons, documentation is in /usr/share/docs etc...

For some background on this concept take a read of these:

[http://www.thegeekstuff.com/2010/09/...tem-structure/]("http://www.thegeekstuff.com/2010/09/linux-file-system-structure/")
[http://www.tuxradar.com/content/take...ilesystem-tour]("http://www.tuxradar.com/content/take-linux-filesystem-tour")
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

> And wich extension is equivalent to Windows'  .exe ?
There isn't one.
Instead of using a files extension to find out what type of file it is Linux looks at the actual information inside the file. For example if you look at what I've done below, the system still knows that the 'Desktop' file in my example is an image, even though I've removed the extension.
```
rob@arch:~/Pictures$ ls D*
-rw-r--r-- 1 rob users 1.1M Dec  8 19:17 Desktop.jpg
rob@arch:~/Pictures$ file Desktop.jpg 
Desktop.jpg: JPEG image data, JFIF standard 1.01
rob@arch:~/Pictures$ mv Desktop.jpg Desktop
rob@arch:~/Pictures$ ls D*
-rw-r--r-- 1 rob users 1.1M Dec  8 19:17 Desktop
rob@arch:~/Pictures$ file Desktop
Desktop: JPEG image data, JFIF standard 1.01
rob@arch:~/Pictures$ 
```

---

### Post by ibjsb4 on 2012-12-15
> In which folder will i find all the applications

/usr/share/applications

---

### Post by Cheesemill on 2012-12-15
> **ibjsb4 said:**
> /usr/share/applications
No.

They are just the application launchers, not the actual applications.

---

### Post by Frogs Hair on 2012-12-15
Unlike Windows the is no program and features or C program files equivalent.  The following command will generate a list in the form of a text document in your home folder.```
sudo dpkg --get-selections > installed-software
```

---

### Post by ibjsb4 on 2012-12-15
> **Cheesemill said:**
> No.

They are just the application launchers, not the actual applications.

I never said they were not.  You WILL find all GUI app's there.

---

### Post by Impavidus on 2012-12-15
The programs themselves are typically located in /usr/bin, program data in /usr/share, but exceptions are common.

File name extensions have no meaning to linux (but they do to some programs running on linux). Script executables often (but not always) have an extension indicating the scripting language (.sh, .py, .pl), binary executables usually don't have an extension. Extensions on linux are mostly a convention to aid users, not a necessity.

---

### Post by MG&amp;TL on 2012-12-15
> **ibjsb4 said:**
> I never said they were not.  You WILL find all GUI app's there.

All GUI apps *with a launcher*. But yes, fine, whatever. ;)

---

### Post by Rockstarever on 2012-12-15
ok if u need to see where are the files that run the program try open the explorer. and press ctrl+h this will show all the hidden files and many of them contains the related files to the programs. hope this helps. 

-----------------
Ubuntu rocks.

---

### Post by monkeybrain2012 on 2012-12-15
> **Rockstarever said:**
> ok if u need to see where are the files that run the program try open the explorer. and press ctrl+h this will show all the hidden files and many of them contains the related files to the programs. hope this helps. 

-----------------
Ubuntu rocks.
No,  those are configuration files for the programs' settings. The actual executables are actually in /usr/bin  as pointed out before (or /usr/local/bin or sometimes /opt/programname depending on how the program was installed)

@OP,
In Linux files are grouped by functionalities  and many programs may share the same libraries. Once you get used to it it is actually more logical and efficient than the Windows way (one reason why Linux is so lean comparing to windows. Since many programs share the same system libraries they don't have to be duplicated for each program like in Windows)

---

### Post by Merrattic on 2012-12-15
No-one has asked why or what you need to know for?

The Applications  Menu (default top panel, top left, Xubuntu icon)will provide a link to all gui installed apps, otherwise dpkg -l on the cli will show all apps installed

---

