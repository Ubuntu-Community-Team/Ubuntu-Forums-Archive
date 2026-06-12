---
title: "'Ubuntu Restricted Extras' Issue."
date: 2008-11-15
forum: New to Ubuntu
---

### Post by Obero on 2008-11-15
So, obviously restricted extras is a valuable sudo input. It installs many essential utilities and software that can ease the computation process. And so, I decided to do it. I input this little gem:

```
sudo apt-get install ubuntu-restricted-extras
```

And I got this output:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

```

I'm a complete beginner at Ubuntu, and this is really bugging me. How do I fix this and go back on the right track?

---

### Post by taurus on 2008-11-15
Just run

```
sudo dpkg --configure -a
sudo apt-get update
```

Now, install whatever you want.

---

### Post by alexcckll on 2008-11-15
I think you need to add "sudo" to the command it offers... you run as a basic user then elevate your privs...

Re my new thread... while I wouldn't know at a really low-level what is going on - I do admin XP and Lotus Notes at work - so I understand what goes on from a *systems support* perspective... but not from a "guru's" perspective.

---

### Post by arpanaut on 2008-11-15
In a terminal run:

```
sudo dpkg --configure -a
```

 that should fix you up

---

### Post by Obero on 2008-11-15
> **arpanaut said:**
> In a terminal run:

```
sudo dpkg --configure -a
```

 that should fix you up

So I tried this, and did the update again but I'm not sure if it worked. I think something messed up?

```
Setting up java-common (0.30ubuntu3) ...

Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 23 changed, 2 added doc-base file(s)...
Registering documents with scrollkeeper...
guy@familyreeths-desktop:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-jre: Depends: sun-java6-bin (= 6-10-0ubuntu2) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-10-0ubuntu2) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by taurus on 2008-11-15
```
sudo apt-get -f install
```

---

### Post by Obero on 2008-11-15
> **taurus said:**
> ```
sudo apt-get -f install
```

This is wierd, a message came up saying sudo warning: java package not installed or something.

Then this came up.

[http://img83.imageshack.us/my.php?image=screenshotsusilaarumainbv8.png](http://img83.imageshack.us/my.php?image=screenshotsusilaarumainbv8.png)

How do I continue?

---

### Post by MasterSander on 2008-11-15
Read the output extensively, because a lot of the time ubuntu just tells you what to do in these cases

---

### Post by MasterSander on 2008-11-15
Click ok and install java from there on

---

### Post by taurus on 2008-11-15
It's asking you if you want to except the license.  Just press the Tab key to highlight the <OK> and then Return to except it.  Then, you should be all good to go.

---

### Post by Obero on 2008-11-15
> **MasterSander said:**
> Read the output extensively, because a lot of the time ubuntu just tells you what to do in these cases

There doesn't seem to be a continuation, just ends with this:

```
 &#9474; For inquiries please contact: Sun Microsystems, Inc., 4150 Network Circle, Santa Clara,   &#9618; 
 &#9474; California 95054, U.S.A.                                                                  &#9618; 
 &#9474;                                                                                           &#9646; 
 &#9474; DLJ v1.1                                                  27APR2006ANS      
```

There's < OK > at the end as well, but I can't click it or anything.

---

### Post by Obero on 2008-11-15
> **taurus said:**
> It's asking you if you want to except the license.  Just press the Tab key to highlight the <OK> and then Return to except it.  Then, you should be all good to go.

That seemed to do it. Let's hope this goes well...

Okay, this was the output:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-jre: Depends: sun-java6-bin (= 6-10-0ubuntu2) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-10-0ubuntu2) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
susila@arumainayagam-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  gsfonts-x11 odbcinst1debian1 sun-java6-bin sun-java6-jre unixodbc xutils-dev
Suggested packages:
  sun-java6-plugin ia32-sun-java6-plugin sun-java6-fonts libmyodbc odbc-postgresql libct1
The following NEW packages will be installed:
  gsfonts-x11 odbcinst1debian1 sun-java6-bin unixodbc xutils-dev
The following packages will be upgraded:
  sun-java6-jre
1 upgraded, 5 newly installed, 0 to remove and 75 not upgraded.
1 not fully installed or removed.
Need to get 0B/35.2MB of archives.
After this operation, 102MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package odbcinst1debian1.
(Reading database ... 
dpkg: serious warning: files list file for package `sun-java6-jre' missing, assuming package has no files currently installed.
100107 files and directories currently installed.)
Unpacking odbcinst1debian1 (from .../odbcinst1debian1_2.2.11-16build2_i386.deb) ...
Selecting previously deselected package unixodbc.
Unpacking unixodbc (from .../unixodbc_2.2.11-16build2_i386.deb) ...
Selecting previously deselected package sun-java6-bin.
Unpacking sun-java6-bin (from .../sun-java6-bin_6-10-0ubuntu2_i386.deb) ...
Preparing to replace sun-java6-jre 6-10-0ubuntu2 (using .../sun-java6-jre_6-10-0ubuntu2_all.deb) ...
sun-dlj-v1-1 license has already been accepted
Unpacking replacement sun-java6-jre ...
Selecting previously deselected package xutils-dev.
Unpacking xutils-dev (from .../xutils-dev_1%3a7.4+3_i386.deb) ...
Selecting previously deselected package gsfonts-x11.
Unpacking gsfonts-x11 (from .../gsfonts-x11_0.20ubuntu1_all.deb) ...
Processing triggers for man-db ...
Setting up odbcinst1debian1 (2.2.11-16build2) ...

Setting up unixodbc (2.2.11-16build2) ...

Setting up xutils-dev (1:7.4+3) ...
Setting up gsfonts-x11 (0.20ubuntu1) ...

Setting up sun-java6-jre (6-10-0ubuntu2) ...

Setting up sun-java6-bin (6-10-0ubuntu2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```

Did the restricted extras work?

---

### Post by handydan918 on 2008-11-15
> **Obero said:**
> There doesn't seem to be a continuation, just ends with this:

```
 &#9474; For inquiries please contact: Sun Microsystems, Inc., 4150 Network Circle, Santa Clara,   &#9618; 
 &#9474; California 95054, U.S.A.                                                                  &#9618; 
 &#9474;                                                                                           &#9646; 
 &#9474; DLJ v1.1                                                  27APR2006ANS      
```

There's < OK > at the end as well, but I can't click it or anything.
Yeah, you are looking at an ncurses interface, I think, which doesn't respond to mouse input. Try using the TAB to highlight the OK button, and then either ENTER or SPACE to select.

---

### Post by landrand on 2008-11-21
I just installed 8.10 and ubuntu-restricted-extras.  I too received the Java license screen.  I spent about an hour trying to figure out what I do with the Java license agreement. The bad thing is ...I've been using Linux for 7 years.  Maybe a little note should be added to the screen indicating that you need to use the tab key.  Just a thought...

---

### Post by frankleeee on 2008-11-21
> **landrand said:**
> I just installed 8.10 and ubuntu-restricted-extras.  I too received the Java license screen.  I spent about an hour trying to figure out what I do with the Java license agreement. The bad thing is ...I've been using Linux for 7 years.  Maybe a little note should be added to the screen indicating that you need to use the tab key.  Just a thought...

If you just install from add remove you get a java gui to accept the package,  the terminal is good for a lot of things but I avoid it for installing stuff that needs a confirmation of contract.

---

### Post by LowSky on 2008-11-21
lol, you guys got stuck on <ok> sorry not wanting to laugh, but it is funny.

TAB is your friend.

Or install Extras from synaptic or Add/remove , that way you get a rather nice looking GUI that your mouse can point and click on.

---

