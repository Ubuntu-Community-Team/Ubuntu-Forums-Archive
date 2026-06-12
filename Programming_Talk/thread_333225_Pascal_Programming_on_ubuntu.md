---
title: "Pascal Programming on ubuntu"
date: 2007-01-07
forum: Programming Talk
---

### Post by fasoulas on 2007-01-07
I would like to now if there is any way so i can program with pascal on ubuntu i am learning pascal in school so i have it install it on my windows xp installation to practice amd i am wondering there is anyway so i can do that on ubuntu (i searched synaptic ,it comes up with a lot of packages but i don't now which to choose)

---

### Post by moma on 2007-01-07
You can try the Lazarus Pascal IDE.
o--> [http://www.lazarus.freepascal.org/](http://www.lazarus.freepascal.org/)

I think you must install both FreePascal compiler and the Lazarus IDE.

1) Download "fp_all_deb.tar" and "lazarus_0.9.20-0_i386.deb" from 
[http://sourceforge.net/project/showfiles.php?group_id=89339&package_id=204004](http://sourceforge.net/project/showfiles.php?group_id=89339&package_id=204004)

Install FreePascal compiler (fp_all_deb.tar) first. Unpack the tar file into an empty directory and run 
$ [COLOR="SeaGreen"]sudo dpkg -i *deb [/COLOR]

Download the "lazarus_0.9.20-0_i386.deb" and install it 
$ [COLOR="SeaGreen"]sudo dpkg -i lazarus_0.9.20-0_i386.deb[/COLOR]

You may need to install several dependencies which Lazarus requires. 
Eg. you will need to install
$ [COLOR="SeaGreen"]sudo apt-get install libgdk-pixbuf-dev[/COLOR]

Search for any missing package like this
$ [COLOR="SeaGreen"]apt-cache search pixbuf[/COLOR]
-----

Start Lazarus IDE:  (the package ha some errors and it puts some bad sym-links to /usr/bin )
$ [COLOR="SeaGreen"]/usr/share/lazarus/lazarus[/COLOR]

Good luck.  Tell us how it is :-k 
-----

See also: 
[http://www.ubuntuforums.org/showthread.php?p=1962696#post1962696](http://www.ubuntuforums.org/showthread.php?p=1962696#post1962696)


Note that you can use the FreePascal IDE (text based ~ turbo pascal 4) and compiler directly. Test
$ [COLOR="SeaGreen"]fp[/COLOR]
and
$ [COLOR="SeaGreen"]fpc [/COLOR]

---

### Post by fasoulas on 2007-01-07
ok thnx a lot for the links and the info i will try them.
Sorry i couldn't reply earlier i wasn't home.
Thnx again

---

### Post by fasoulas on 2007-01-07
> **moma said:**
> 

You may need to install several dependencies which Lazarus requires. 
Eg. you will need to install
$ [COLOR="SeaGreen"]sudo apt-get install libgdk-pixbuf-dev[/COLOR]

Search for any missing package like this
$ [COLOR="SeaGreen"]apt-cache search pixbuf[/COLOR]
-----

Start Lazarus IDE:  (the package ha some errors and it puts some bad sym-links to /usr/bin )
$ [COLOR="SeaGreen"]/usr/share/lazarus/lazarus[/COLOR]



From that point and after i couldn't understand very well what do u mean.
What do u mean by saying i have to install several dependencies which Lazarus requires  OR how to search for missing package and what kind of errors do the lazurus IDE package has ???

Could u pls answer to my questions because i am new to linux

---

### Post by moma on 2007-01-12
Lazarus requires some additional software pieces to run properly. You can find these packages in the Ubuntu's package system (Synaptic).  Start Synaptic package manager from the System -> Administration menu or use "apt-cache search  ...." to find those missing packages.

Lazarus will tell you what it is missing.  
libgdk-pixbuf-dev package is the one (if not the only one) you must install. 


The Lazarus-package (.deb) ha some errors and it puts some bad sym-links to /usr/bin directory, therefore you must start it like this:
$ [COLOR="SeaGreen"]/usr/share/lazarus/lazarus[/COLOR]
(On the command line. Or create a startup icon for it)

---

### Post by Lord Illidan on 2007-01-12
Are you using Turbo Pascal at school? If so, we are in the same boat.

I found Free Pascal to be a good substitute for console programs, but for graphical programs, I needed to use a protected mode mouse unit, which would only work with Turbo Pascal 7.

So I downloaded Dosbox, and set to work.

```
sudo apt-get install dosbox
```

Once it is installed, running dosbox from the terminal will give you a dos-like window, and you can mount a folder as a virtual harddrive from there and run Turbo Pascal from it.

---

### Post by angustia on 2007-01-12
> **Lord Illidan said:**
> Are you using Turbo Pascal at school? If so, we are in the same boat.

I found Free Pascal to be a good substitute for console programs, but for graphical programs, I needed to use a protected mode mouse unit, which would only work with Turbo Pascal 7.

So I downloaded Dosbox, and set to work.

```
sudo apt-get install dosbox
```

Once it is installed, running dosbox from the terminal will give you a dos-like window, and you can mount a folder as a virtual harddrive from there and run Turbo Pascal from it.

freepascal comes with sdl and opengl units...

---

### Post by sudenaz on 2007-01-12
1.- try with pthread_detach at the end of mythread()

2.- look in /proc/sys/kernel/threads-max (max number of threads for the whole system)

3- with ps -eLf you can see processes with their threads (under LWP (light weight process))
[www.unreadedpost.com](www.unreadedpost.com)

---

### Post by Lord Illidan on 2007-01-12
> **angustia said:**
> freepascal comes with sdl and opengl units...

I know, but I cannot use them at school.

---

