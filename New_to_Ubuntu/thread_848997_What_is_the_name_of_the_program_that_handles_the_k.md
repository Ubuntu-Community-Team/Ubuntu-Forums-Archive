---
title: "What is the name of the program that handles the kde widgets?"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by 4t0m1c_w07f on 2008-07-04
Just as the title asks...

---

### Post by bhadotia on 2008-07-04
In KDE4 I think its called plasma dashboard- though can't recall properly.

---

### Post by 4t0m1c_w07f on 2008-07-04
> **bhadotia said:**
> In KDE4 I think its called plasma dashboard- though can't recall properly.

Thanks so how will I launch a widget? I have the kde base files installed under my gnome...

---

### Post by bhadotia on 2008-07-04
Don't know how to do it under GNOM exactly. 
Still, let me guess :
First launch plasma through CLI or alt+f2 then point the mouse cursor to the top right corner of the screen , you shpuld be able to see the menu.

---

### Post by 4t0m1c_w07f on 2008-07-04
Right, so what I did was try install the kde4 base but says this when I try to apply:
```
kde4base:
 Depends: libldap2 (>=2.1.17-1) but it is not installable
 Depends: libopenexr2c2a (>=1.2.2) but it is not installable
 Depends: kde4base-data but it is not going to be installed

```

---

### Post by bhadotia on 2008-07-04
I cannot find the kde4base package in synaptic. There is kde4-core ofcourse and it can be installed ; then may be you can run plasma.

---

### Post by 4t0m1c_w07f on 2008-07-04
And doing this wont stuff up my gnome?

---

### Post by bhadotia on 2008-07-04
I checked the total download size of these packages is 80.5 MB , which after installation will take up 174 MB . So if you have disk space thetre is no problem at all ( I've tried full KDE4 with GNOME once and even then there was not much of a problem).

---

### Post by 4t0m1c_w07f on 2008-07-04
AWESOME!!! So that means I will be able to run OpenKiosk in gnome basically!

---

### Post by bhadotia on 2008-07-04
I forgot to tell after installing this you also be able to access KDE4 from login screen . But before you do that ensure that in the previous session you run:
```
sudo dpkg-reconfigure kdm-kde4
``` 
or,
```
sudo dpkg-reconfigure gdm
```
Just follow the prompts. This will configure the Display Manager according to the session you intend to log in the next time.
If you forget to do this you might experience strange behavior in GNOME  if the DM is kdm-kde4.. KDE4 will run (though not smoothly) even  with gdm as the DM.

---

### Post by ChameleonDave on 2008-07-04
> **4t0m1c_w07f said:**
> Right, so what I did was try install the kde4 base but says this when I try to apply:
```
kde4base:
 Depends: libldap2 (>=2.1.17-1) but it is not installable
 Depends: libopenexr2c2a (>=1.2.2) but it is not installable
 Depends: kde4base-data but it is not going to be installed

```

There may be problems with your /etc/apt/source.list.  You might also want to wait a while, then refresh the database in Synaptic, and try again.

---

### Post by bhadotia on 2008-07-04
> **ChameleonDave said:**
> There may be problems with your /etc/apt/source.list.  You might also want to wait a while, then refresh the database in Synaptic, and try again.
Well I did not find kde4base package in my synaptic . Is it there in yours?

---

### Post by ChameleonDave on 2008-07-04
> **bhadotia said:**
> Well I did not find kde4base package in my synaptic . Is it there in yours?

```

$ sudo apt-get install kde4base
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package kde4base is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  kdelibs5
E: Package kde4base has no installation candidate

```
I do have kdebase-kde4 and kdelibs5 installed on my system.  My only desktop environment is KDE 4.

---

### Post by bhadotia on 2008-07-04
> **ChameleonDave said:**
> ```

$ sudo apt-get install kde4base
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package kde4base is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  kdelibs5
E: Package kde4base has no installation candidate

```I do have kdebase-kde4 and kdelibs5 installed on my system.  My only desktop environment is KDE 4.
See, told you its not there.

---

### Post by 4t0m1c_w07f on 2008-07-04
Ok kewl well I'm installing kde4 core now

---

### Post by bhadotia on 2008-07-04
Heehee, Well you can install anything you want as long as you have the patience to troubleshoot when something goes wrong. I certainly don't have that quality- whenever something goes wrong I simply do reinstall. Thats why my seperate /home, /data partitions and APTonCD DVD always come in handy.


Good Luck. :)

---

### Post by ChameleonDave on 2008-07-04
> **bhadotia said:**
> See, told you its not there.

Told who?  Me?  I never said it was there.  I was just responding to that error message, which indicated that there were unmet dependencies.

---

### Post by 4t0m1c_w07f on 2008-07-04
After compiling successfully I run make and get this:```
root@dozer:~/Desktop/opkdekiosk-2.0.6# make
make  all-recursive
make[1]: Entering directory `/root/Desktop/opkdekiosk-2.0.6'
Making all in doc
make[2]: Entering directory `/root/Desktop/opkdekiosk-2.0.6/doc'
Making all in .
make[3]: Entering directory `/root/Desktop/opkdekiosk-2.0.6/doc'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/root/Desktop/opkdekiosk-2.0.6/doc'
Making all in en
make[3]: Entering directory `/root/Desktop/opkdekiosk-2.0.6/doc/en'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/root/Desktop/opkdekiosk-2.0.6/doc/en'
make[2]: Leaving directory `/root/Desktop/opkdekiosk-2.0.6/doc'
Making all in opkdekiosk
make[2]: Entering directory `/root/Desktop/opkdekiosk-2.0.6/opkdekiosk'
Making all in xmlrpc++
make[3]: Entering directory `/root/Desktop/opkdekiosk-2.0.6/opkdekiosk/xmlrpc++'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/root/Desktop/opkdekiosk-2.0.6/opkdekiosk/xmlrpc++'
Making all in applet
make[3]: Entering directory `/root/Desktop/opkdekiosk-2.0.6/opkdekiosk/applet'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/root/Desktop/opkdekiosk-2.0.6/opkdekiosk/applet'
Making all in kiosksetup
make[3]: Entering directory `/root/Desktop/opkdekiosk-2.0.6/opkdekiosk/kiosksetup'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/root/Desktop/opkdekiosk-2.0.6/opkdekiosk/kiosksetup'
Making all in pixmaps
make[3]: Entering directory `/root/Desktop/opkdekiosk-2.0.6/opkdekiosk/pixmaps'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/root/Desktop/opkdekiosk-2.0.6/opkdekiosk/pixmaps'
make[3]: Entering directory `/root/Desktop/opkdekiosk-2.0.6/opkdekiosk'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/root/Desktop/opkdekiosk-2.0.6/opkdekiosk'
make[2]: Leaving directory `/root/Desktop/opkdekiosk-2.0.6/opkdekiosk'
Making all in po
make[2]: Entering directory `/root/Desktop/opkdekiosk-2.0.6/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/root/Desktop/opkdekiosk-2.0.6/po'
make[2]: Entering directory `/root/Desktop/opkdekiosk-2.0.6'
make[2]: Leaving directory `/root/Desktop/opkdekiosk-2.0.6'
make[1]: Leaving directory `/root/Desktop/opkdekiosk-2.0.6'
```

Then I run make install and get this:

```
root@dozer:~/Desktop/opkdekiosk-2.0.6# make install
Making install in doc
make[1]: Entering directory `/root/Desktop/opkdekiosk-2.0.6/doc'
Making install in .
make[2]: Entering directory `/root/Desktop/opkdekiosk-2.0.6/doc'
make[3]: Entering directory `/root/Desktop/opkdekiosk-2.0.6/doc'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/root/Desktop/opkdekiosk-2.0.6/doc'
make[2]: Leaving directory `/root/Desktop/opkdekiosk-2.0.6/doc'
Making install in en
make[2]: Entering directory `/root/Desktop/opkdekiosk-2.0.6/doc/en'
make[3]: Entering directory `/root/Desktop/opkdekiosk-2.0.6/doc/en'
make[3]: Nothing to be done for `install-exec-am'.
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/doc/HTML/en/opkdekiosk
/usr/bin/install -c -p -m 644 index.docbook /usr/local/kde/share/doc/HTML/en/opkdekiosk/index.docbook
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/doc/HTML/en/opkdekiosk
/usr/bin/install -c -p -m 644 index.cache.bz2 /usr/local/kde/share/doc/HTML/en/opkdekiosk/
rm -f /usr/local/kde/share/doc/HTML/en/opkdekiosk/common
ln -s /usr/share/doc/kde/HTML/en/common /usr/local/kde/share/doc/HTML/en/opkdekiosk/common
make[3]: Leaving directory `/root/Desktop/opkdekiosk-2.0.6/doc/en'
make[2]: Leaving directory `/root/Desktop/opkdekiosk-2.0.6/doc/en'
make[1]: Leaving directory `/root/Desktop/opkdekiosk-2.0.6/doc'
Making install in opkdekiosk
make[1]: Entering directory `/root/Desktop/opkdekiosk-2.0.6/opkdekiosk'
Making install in xmlrpc++
make[2]: Entering directory `/root/Desktop/opkdekiosk-2.0.6/opkdekiosk/xmlrpc++'
make[3]: Entering directory `/root/Desktop/opkdekiosk-2.0.6/opkdekiosk/xmlrpc++'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/root/Desktop/opkdekiosk-2.0.6/opkdekiosk/xmlrpc++'
make[2]: Leaving directory `/root/Desktop/opkdekiosk-2.0.6/opkdekiosk/xmlrpc++'
Making install in applet
make[2]: Entering directory `/root/Desktop/opkdekiosk-2.0.6/opkdekiosk/applet'
make[3]: Entering directory `/root/Desktop/opkdekiosk-2.0.6/opkdekiosk/applet'
test -z "/usr/local/kde/lib" || mkdir -p -- "/usr/local/kde/lib"
 /bin/bash ../../libtool --silent --mode=install /usr/bin/install -c -p  'libopkdekiosk.la' '/usr/local/kde/lib/libopkdekiosk.la'
PATH="$PATH:/sbin" ldconfig -n /usr/local/kde/lib
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kicker/applets/
/usr/bin/install -c -p -m 644 ./opkdekiosk.desktop \
	/usr/local/kde/share/apps/kicker/applets/opkdekiosk.desktop
make[3]: Leaving directory `/root/Desktop/opkdekiosk-2.0.6/opkdekiosk/applet'
make[2]: Leaving directory `/root/Desktop/opkdekiosk-2.0.6/opkdekiosk/applet'
Making install in kiosksetup
make[2]: Entering directory `/root/Desktop/opkdekiosk-2.0.6/opkdekiosk/kiosksetup'
make[3]: Entering directory `/root/Desktop/opkdekiosk-2.0.6/opkdekiosk/kiosksetup'
test -z "/usr/local/kde/bin" || mkdir -p -- "/usr/local/kde/bin"
  /bin/bash ../../libtool --silent --mode=install /usr/bin/install -c -p  'kiosksetup' '/usr/local/kde/bin/kiosksetup'
/usr/bin/install -c -p -m 644 ./kioskclientrc /usr/local/kde/share/config/kioskclientrc
/usr/bin/install: cannot create regular file `/usr/local/kde/share/config/kioskclientrc': No such file or directory
make[3]: *** [install-data-local] Error 1
make[3]: Leaving directory `/root/Desktop/opkdekiosk-2.0.6/opkdekiosk/kiosksetup'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/root/Desktop/opkdekiosk-2.0.6/opkdekiosk/kiosksetup'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/root/Desktop/opkdekiosk-2.0.6/opkdekiosk'
make: *** [install-recursive] Error 1
```

Any idea whats going on?

---

### Post by ChameleonDave on 2008-07-04
Well, it fails because it cannot create /usr/local/kde/share/config/kioskclientrc.  It explains this as there being a missing file or directory.

Looking at my system, I can see that there is no such directory as /usr/local/kde/share/config/, so I can see that trying to create a file called "kioskclientrc" within that non-existent directory would cause an error.

The person who made that script assumed that such a directory would be present.  I don't know why.  Perhaps you have an unmet dependency that is not being properly flagged.  It's something to take up with them.  You can't do much in the mean time.

Well, I suppose you could try the following hack:

```

sudo mkdir  /usr/local/kde/  /usr/local/kde/share/  /usr/local/kde/share/config/

```

That might trick the script into working.  However, there are almost certainly other such discrepancies that will screw up the installation.

---

### Post by txcrackers on 2008-07-04
If you're talking about KDE 3.5, then the program is "superkaramba" and it *might* work in a Gnome session. The KDE 4 plasma widgets aren't quite fully baked yet and still have some issues...

---

### Post by zachthejones on 2008-08-16
The plasma widgets are for KDE 4, which you can install if you have this repo added to your sources list:

*deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main*

after reloading, just use this command in terminal to install:

```
sudo apt-get install kde4-core
```

Then, when you next boot up, choose KDE 4 in the session menu. You should be good to go then.

---

### Post by 4t0m1c_w07f on 2008-08-17
My problem is that the customers prefer the gnome desktop... We want to keep the gnome desktop environment but be able to run this:

> 
The Openkiosk system is basically composed of two parts. The first program is called NodeView. It acts as the OpenKiosk central server containing the client information database. It is responsible for administering all the clients on the network either automatically or manually. Monitoring and controlling the workstations can be done locally via the graphical user interfaces or remotely from a Java Applet in a browser.

The second part is simply called "The Client". It is the actual program that sits between the customer and the operating system interface on the workstations. It is the software which physically limits the user's access to the Internet, network resources, the local programs on the workstation itself. For automatic usage, it can take in membership card login. It is also possible to interface to much more advanced hardware readers such as smart card readers. The client is also capable of simple but important tasks such as remote shutdown, and instant messaging.

Presently, there are two versions of clients. The X11 Unix version, which is an applet that sits on top of the KDE panel (requires at least KDE 3.X) and the Windows version (Windows 95,98,NT,2000,XP).


This is the description of how OpenKiosk works and it says that I need KDE not gnome.

---

