---
title: "[SOLVED] error trying to install Music Applet 2.4.0 for Rhythmbox"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by gbrad901 on 2008-07-18
i get this error after i do the ./configure command. It goes for a while then this:



checking for a Python interpreter with version >= 2.4... python
checking for python... /usr/bin/python
checking for python version... 2.5
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.5/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.5/site-packages
checking for headers required to compile python extensions... not found
configure: error: could not find Python headers

any suggestions?

---

### Post by mgranet on 2008-07-18
Do you have the python2.5-dev package installed?

---

### Post by gbrad901 on 2008-07-18
how do I check, i searched for files with python and see folders with multiple versions. 2.3, 2.4, and 2.5

---

### Post by mgranet on 2008-07-18
> **gbrad901 said:**
> how do I check, i searched for files with python and see folders with multiple versions. 2.3, 2.4, and 2.5

```
 sudo apt-get install python2.5-dev 
```

---

### Post by gbrad901 on 2008-07-18
that get me this 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by mgranet on 2008-07-18
> **gbrad901 said:**
> that get me this 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

A package database error occured (likely due to a crash or dependency error of your package manager), and the db was locked. To unlock it, run ```
 sudo dpkg --configure -a
```

---

### Post by gbrad901 on 2008-07-18
that got me 


gbrad901@gbrad901-laptop:~$ sudo dpkg --configure -a
Setting up java-common (0.28ubuntu3) ...

Setting up odbcinst1debian1 (2.2.11-16build1) ...

Setting up unixodbc (2.2.11-16build1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
gbrad901@gbrad901-laptop:~$  sudo apt-get install python2.5-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-bin: Depends: sun-java6-jre (= 6-06-0ubuntu1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
gbrad901@gbrad901-laptop:~$

---

### Post by gbrad901 on 2008-07-18
that good or bad?

---

### Post by gbrad901 on 2008-07-18
also, after i did that i went back to the music applet andthe ./configure command no longer works

---

### Post by mgranet on 2008-07-18
> **gbrad901 said:**
> that got me 


gbrad901@gbrad901-laptop:~$ sudo dpkg --configure -a
Setting up java-common (0.28ubuntu3) ...

Setting up odbcinst1debian1 (2.2.11-16build1) ...

Setting up unixodbc (2.2.11-16build1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
gbrad901@gbrad901-laptop:~$  sudo apt-get install python2.5-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-bin: Depends: sun-java6-jre (= 6-06-0ubuntu1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
gbrad901@gbrad901-laptop:~$

```
 sudo apt-get install sun-java6-jre
```

---

### Post by mgranet on 2008-07-18
> **gbrad901 said:**
> also, after i did that i went back to the music applet andthe ./configure command no longer works

You've already configured it. That is normal operation.

---

### Post by gbrad901 on 2008-07-18
how do dependencies get broken? installation of other apps? only been on linux for a short time. sorry for the complete noob questions

---

### Post by mgranet on 2008-07-18
> **gbrad901 said:**
> how do dependencies get broken? installation of other apps? only been on linux for a short time. sorry for the complete noob questions

That's a big question. Sometimes, a package outside of the repositories might depend on a newer or older version of an installed library. Or your package manager might crash halfway through an install. I'm sure there's more ways than that, but those are the only ways I've broken dependencies on a debian based system. (RPM based systems, on the other hand...)

The only stupid question is one that isn't asked.

---

### Post by gbrad901 on 2008-07-18
after i do the java gimmick i get this(look at attached pic) and cant get out of it

---

### Post by gbrad901 on 2008-07-18
Anybody around that can help?

---

### Post by cariboo on 2008-07-18
That is just the Sun EULA just scroll all the way to the bottom and agree to the licensing terms then when the OK is highlighted hit enter.
You can use the up and down arrows or the space bar to scroll to the bottom of the EULA.

Jim

---

### Post by gbrad901 on 2008-07-18
this is where it's stuck art now

checking for a Python interpreter with version >= 2.4... python
checking for python... /usr/bin/python
checking for python version... 2.5
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.5/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.5/site-packages
checking for headers required to compile python extensions... found
checking for pygtk-codegen-2.0... no
configure: error: could not find pygtk-codegen-2.0 script

---

### Post by gbrad901 on 2008-07-18
now i'm here

checking for MUSICAPPLET_DEPS... configure: error: Package requirements (
	gtk+-2.0
	libpanelapplet-2.0
	pango >= 1.6
	pygtk-2.0
	gnome-python-2.0
) were not met:

No package 'libpanelapplet-2.0' found
No package 'gnome-python-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables MUSICAPPLET_DEPS_CFLAGS
and MUSICAPPLET_DEPS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

### Post by mgranet on 2008-07-18
It sounds to me like you are starting to wind up in dependency hell(where dependencies just depend on more files in a seemingly never ending loop). 

That is why it is advised to only install software from the repos until you get used to the way software in Linux works. Music Applet 2.3.1.1 is available in the repos. 

If you install the version in the repos your package manager will then do all the hard work for you, including installing of dependencies.

```
sudo apt-get install music-applet
```

Or search for 'music-applet' in your package manager and install it the graphical way.

---

