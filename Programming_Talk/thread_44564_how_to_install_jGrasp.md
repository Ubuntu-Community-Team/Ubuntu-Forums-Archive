---
title: "how to install jGrasp"
date: 2005-06-26
forum: Programming Talk
---

### Post by tlo on 2005-06-26
i've recently installed kubuntu on my system and i want to install a java editor. i found jGrasp to be my favorite on windows, but is it possible to install it on kubuntu? i have only had it for a week and im still not very familiar with apt-get. any help would be appreciated

---

### Post by SGC on 2005-06-26
- Download jGRASp zip file from [here](http://spider.eng.auburn.edu/user-cgi/grasp/grasp.pl?;dl=download_jgrasp.html) 

- extracte the zip file to any folder

- Jgrasp does not requires installation so to create a shortcut to it, right click on the desktop (or where you want to put the shortcut) and choose **Create new** then **Link to application**.

In the general tab enter **jGRASP** and then go to **application** tab, and enter this  in the command field:
~/jgrasp175/jgrasp/bin/jgrasp

Change ~ to where you extracted the file.

**Note: you need JRE in order to run this program, I'm sure you have it, but in case you don't, follow [this instructions](http://ubuntuguide.org/#jre)  to install it**

---

### Post by jerome bettis on 2005-06-26
> **SGC]- Download jGRASp zip file from [URL=http://spider.eng.auburn.edu/user-cgi/grasp/grasp.pl? said:**
> here[/URL] 

- extracte the zip file to any folder

- Jgrasp does not requires installation so to create a shortcut to it, right click on the desktop (or where you want to put the shortcut) and choose **Create new** then **Link to application**.

In the general tab enter **jGRASP** and then go to **application** tab, and enter this  in the command field:
~/jgrasp175/jgrasp/bin/jgrasp

Change ~ to where you extracted the file.

**Note: you need JRE in order to run this program, I'm sure you have it, but in case you don't, follow [this instructions](http://ubuntuguide.org/#jre)  to install it**
 IMO jgrasp is terrible.  take a look at eclipse or jedit.

---

### Post by tlo on 2005-06-27
[QUOTE=jerome bettis]IMO jgrasp is terrible.  take a look at eclipse or jedit.[/QUOTE]
 is this pretty much how to install any program that you dont apt-get? just download the zip, extract it, and link to the executable?

---

### Post by SGC on 2005-06-27
[QUOTE=tlo]is this pretty much how to install any program that you dont apt-get? just download the zip, extract it, and link to the executable?[/QUOTE]
 No, It differs from a program to another

---

### Post by tlo on 2005-06-27
ok, i did all that, but it wont open. do i need to have the jre somewhere in the jGrasp folder?

---

### Post by toosweetnitemare on 2006-09-05
ya that doesnt work for me either, but im not using kubuntu im using gnome does that matter?

---

### Post by loswr86 on 2008-03-26
thanks.

---

### Post by Joshua swordmaster on 2009-10-03
I have the same problem. It has to do with the way kubuntu sees .jar files as .zip files (at least, thats my system does). You can run jgrasp from the terminal by typing 
```
java -jar filename.jar
``` or by setting your system to see .jar files as executable, but I do not know how to do that. IF you run jgrasp from the terminal, you cannot use the debug tool, but otherwise it works just fine.

---

### Post by sean.bailey00 on 2011-01-31
This thread is now rather dated...  see [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1417703") for a more recent solution.

---

### Post by orttez on 2011-08-30
I'm using Ubuntu and all I did to use jGRASP was to download the zip file in my desired location. I double click the jgrasp directory, then double click the bin directory.
Once in the bin directory I saw a shell script entitled "jgrasp" which I double clicked. A small window pops up, and I clicked run in order to start using jGRASP.

---

