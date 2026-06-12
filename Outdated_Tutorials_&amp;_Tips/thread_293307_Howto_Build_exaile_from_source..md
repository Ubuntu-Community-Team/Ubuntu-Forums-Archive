---
title: "Howto: Build exaile from source."
date: 2006-11-05
forum: Outdated Tutorials &amp; Tips
---

### Post by cborga1985 on 2006-11-05
[SIZE="5"][COLOR="Magenta"]**Howto: Building exaile from source.**[/COLOR][/SIZE]
[SIZE="3"][COLOR="DarkGreen"]***Update: All Dependencies should be fixed now.***[/COLOR][/SIZE]
**First**
*ALT+F2 **gnome-terminal**, click run then*
```
wget http://www.exaile.org/files/exaile_0.2.9b.tar.gz
```

**Second**
*Extract from tarball*
```
tar xvfz exaile_0.2.9b.tar.gz
```

**Third**
*Grab the dependencies*
```
sudo apt-get install build-essential dpkg-dev debhelper libgstreamer0.10-0 gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly python-gst0.10 gstreamer0.10-esd gstreamer0.10-alsa python2.4 python2.4-dev python2.4-gtk2 python-gtk2-dev python-glade2 python2.4-dbus python-pyvorbis python-mutagen python-pysqlite2 python-elementtree python2.4-gnome2-extras python-cddb streamripper

```

**Forth**
*Go to the **exaile** folder*
```
cd exaile_0.2.*
```

**Fifth**
*Compile program*
```
make
```

**Sixth**
*Compile a debian package*
```
sudo dpkg-buildpackage
```
wait for it to build

**Seventh**
*Go to previous directory where the debian package generates*
```
cd ..
```

**Eighth**
*Install the package*
```
sudo dpkg -i exaile*.deb
```

If it does not work when you go to run it. Do this but I didn't seperate everything. Just follow line by line.
```

cd ~/Desktop
wget http://janvitus.interfree.it/ubuntu/pool/dapper-upure64/main-amd64/python-mutagen_1.6-0ubuntu1~janvitus_all.deb
sudo dpkg -i python-mutagen_1.6-0ubuntu1~janvitus_all.deb
rm python-mutagen_1.6-0ubuntu1~janvitus_all.deb
```

**[COLOR="Red"][SIZE="3"]Steps for building bleeding edge [here]("http://www.ubuntuforums.org/showpost.php?p=1863663&postcount=16").[/SIZE][/COLOR]**
*by **bionnaki***

---

### Post by IusedTObeSOMEONEelse on 2006-11-10
I just want to say **THANK YOU** for the HowTo. I am using Feisty Fawn on this Machine and it installed perfectly for me following all the steps. If only alot more things (I'll catch hell for saying this) were explained in those terms to make it easier for New Members to install various things. :-k  Sally :cool:

---

### Post by ryu kun on 2006-11-19
I've got this error after the install:

```
ryu@rua:~/src/exaile_0.2.6$ exaile
Traceback (most recent call last):
  File "/usr/bin/exaile", line 67, in ?
    from xl import *
  File "/usr/share/exaile/xl/tracks.py", line 18, in ?
    import common, media, db, config, trackslist
  File "/usr/share/exaile/xl/media.py", line 18, in ?
    import mutagen, mutagen.id3, mutagen.flac, mutagen.oggvorbis
ImportError: No module named oggvorbis

```

what should I do?

---

### Post by cborga1985 on 2006-11-21
> **ryu kun said:**
> I've got this error after the install:

```
ryu@rua:~/src/exaile_0.2.6$ exaile
Traceback (most recent call last):
  File "/usr/bin/exaile", line 67, in ?
    from xl import *
  File "/usr/share/exaile/xl/tracks.py", line 18, in ?
    import common, media, db, config, trackslist
  File "/usr/share/exaile/xl/media.py", line 18, in ?
    import mutagen, mutagen.id3, mutagen.flac, mutagen.oggvorbis
ImportError: No module named oggvorbis

```

what should I do?
Get lastest python-mutagen. Follow instructions above I just added.

---

### Post by ryu kun on 2006-11-23
Thank you. It works now.

---

### Post by cborga1985 on 2006-11-23
> **ryu kun said:**
> Thank you. It works now.

no problem

---

### Post by stucky on 2006-11-24
You kick ***.

---

### Post by bionnaki on 2006-11-25
what is the advantage of building from source rather than using the .deb from exaile.org ?

---

### Post by Fsngruv on 2006-11-26
The install was going well until I had to compile on step 5.  It keep telling me command not found heres what it looks like, did I miss a step somewhere?

owenby@owenby-desktop:~$ sudo apt-get install build-essential dpkg-dev debhelper libgstreamer0.10-0 gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly python-gst0.10 gstreamer0.10-esd gstreamer0.10-alsa python2.4 python2.4-dev python2.4-gtk2 python-gtk2-dev python-glade2 python2.4-dbus python-pyvorbis python-mutagen python-pysqlite2 python-elementtree python2.4-gnome2-extras python-cddb streamrippe
Reading package lists... Done
Building dependency tree... Done
libgstreamer0.10-0 is already the newest version.
gstreamer0.10-plugins-base is already the newest version.
gstreamer0.10-plugins-good is already the newest version.
python-gst0.10 is already the newest version.
gstreamer0.10-esd is already the newest version.
gstreamer0.10-alsa is already the newest version.
python2.4 is already the newest version.
python2.4-gtk2 is already the newest version.
python-glade2 is already the newest version.
python2.4-dbus is already the newest version.
python-pyvorbis is already the newest version.
python2.4-gnome2-extras is already the newest version.
python-cddb is already the newest version.
E: Couldn't find package streamrippe
owenby@owenby-desktop:~$ cd exaile*
owenby@owenby-desktop:~/exaile_0.2.6$ make
bash: make: command not found
owenby@owenby-desktop:~$ sudo apt-get install streamripper
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  kstreamripper streamtuner
The following NEW packages will be installed:
  streamripper
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 60.9kB of archives.
After unpacking 176kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe streamripper 1.61.17-1 [60.9kB]
Fetched 60.9kB in 0s (79.4kB/s)
Selecting previously deselected package streamripper.
(Reading database ... 76166 files and directories currently installed.)
Unpacking streamripper (from .../streamripper_1.61.17-1_i386.deb) ...
Setting up streamripper (1.61.17-1) ...
owenby@owenby-desktop:~$ cd exaile*

---

### Post by bionnaki on 2006-11-27
what's the point in creating a .deb? why not just *sudo make install* after *make* ? seems like making a .deb is an unnecessary step.

---

### Post by birdmun on 2006-11-30
The nice thing about creating a .deb is that when you install it that way its easily removed via synaptic.

---

### Post by terminatorkobold on 2006-12-02
Hello cborga1985,

I get stuck when grabbing the dependencies.
The problem is with the python-gtk2-dev package, and I get the following error message from apt-get:
python-gtk2-dev: Depends on: libgtk2.0-dev (>= 2.8 ) but wont be installed
E: defect packages

What should I dou

Thanks

---

### Post by cborga1985 on 2006-12-07
> **bionnaki said:**
> what is the advantage of building from source rather than using the .deb from exaile.org ?
none really but some people had problems with the deb

---

### Post by cborga1985 on 2006-12-07
> **Fsngruv said:**
> The install was going well until I had to compile on step 5.  It keep telling me command not found heres what it looks like, did I miss a step somewhere?

owenby@owenby-desktop:~$ sudo apt-get install build-essential dpkg-dev debhelper libgstreamer0.10-0 gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly python-gst0.10 gstreamer0.10-esd gstreamer0.10-alsa python2.4 python2.4-dev python2.4-gtk2 python-gtk2-dev python-glade2 python2.4-dbus python-pyvorbis python-mutagen python-pysqlite2 python-elementtree python2.4-gnome2-extras python-cddb streamrippe
Reading package lists... Done
Building dependency tree... Done
libgstreamer0.10-0 is already the newest version.
gstreamer0.10-plugins-base is already the newest version.
gstreamer0.10-plugins-good is already the newest version.
python-gst0.10 is already the newest version.
gstreamer0.10-esd is already the newest version.
gstreamer0.10-alsa is already the newest version.
python2.4 is already the newest version.
python2.4-gtk2 is already the newest version.
python-glade2 is already the newest version.
python2.4-dbus is already the newest version.
python-pyvorbis is already the newest version.
python2.4-gnome2-extras is already the newest version.
python-cddb is already the newest version.
E: Couldn't find package streamrippe
owenby@owenby-desktop:~$ cd exaile*
owenby@owenby-desktop:~/exaile_0.2.6$ make
bash: make: command not found
owenby@owenby-desktop:~$ sudo apt-get install streamripper
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  kstreamripper streamtuner
The following NEW packages will be installed:
  streamripper
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 60.9kB of archives.
After unpacking 176kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe streamripper 1.61.17-1 [60.9kB]
Fetched 60.9kB in 0s (79.4kB/s)
Selecting previously deselected package streamripper.
(Reading database ... 76166 files and directories currently installed.)
Unpacking streamripper (from .../streamripper_1.61.17-1_i386.deb) ...
Setting up streamripper (1.61.17-1) ...
owenby@owenby-desktop:~$ cd exaile*
the code was not copy and pasted quite right
it should have been

sudo apt-get install build-essential dpkg-dev debhelper libgstreamer0.10-0 gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly python-gst0.10 gstreamer0.10-esd gstreamer0.10-alsa python2.4 python2.4-dev python2.4-gtk2 python-gtk2-dev python-glade2 python2.4-dbus python-pyvorbis python-mutagen python-pysqlite2 python-elementtree python2.4-gnome2-extras python-cddb [COLOR="Orange"]streamripper[/COLOR]

The end of the command said streamrippe instead of streamripper. Do ```
ls
``` amd that should show a list of file like this.
```

[FONT="Courier New"]boston@boston:~/Downloads/exaile_0.2.6$ ls
build-stamp      debian          exaile.glade   license.txt  mmkeys.so   sql
changelog        exaile          exaile.gladep  Makefile     package.py  TODO
checklist        exaile.1        exaile.py      merge        po          xl
configure-stamp  exaile.desktop  images         mmkeys       scripts[/FONT]

```
If you see another folder cd to it by typing ```
cd *foldername*
```. Where *foldername* is what the folder inside the exaile folder was called. P.S. If you are try to use svn then you have to do ```
cd trunk
``` before doing make.

---

### Post by cborga1985 on 2006-12-07
> **birdmun said:**
> The nice thing about creating a .deb is that when you install it that way its easily removed via synaptic.

thanks, you took the words right out of my mouth. much better to make the deb so later on you can purge all the data using sudo dpkg -P filename.deb

---

### Post by bionnaki on 2006-12-09
you can also build the bleeding edge (currently 0.2.7b)

sudo apt-get install subversion

svn checkout svn://jbother.org/usr/local/svn/exaile/trunk

sudo apt-get install build-essential dpkg-dev debhelper libgstreamer0.10-0 gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly python-gst0.10 gstreamer0.10-esd gstreamer0.10-alsa python2.4 python2.4-dev python2.4-gtk2 python-gtk2-dev python-glade2 python2.4-dbus python-pyvorbis python-mutagen python-pysqlite2 python-elementtree python2.4-gnome2-extras python-cddb streamripper

rename trunk directory in home directory to exaile_svn

cd exaile_svn

make

sudo dpkg-buildpackage

cd ..

sudo dpkg -i exaile*.deb

---

### Post by cborga1985 on 2006-12-09
> **terminatorkobold said:**
> Hello cborga1985,

I get stuck when grabbing the dependencies.
The problem is with the python-gtk2-dev package, and I get the following error message from apt-get:
python-gtk2-dev: Depends on: libgtk2.0-dev (>= 2.8 ) but wont be installed
E: defect packages

What should I dou

Thanks
Sounds like you haven't enabled all the repositories. A quick guide to do that [here]("http://ubuntuguide.org/wiki/Dapper#Repositories").

---

### Post by foxy123 on 2006-12-14
AFter building the package I have the following error:
```
$ exaile
Traceback (most recent call last):
  File "/usr/bin/exaile", line 2291, in ?
    main()
  File "/usr/bin/exaile", line 2281, in main
    exaile = ExaileWindow(options, fr)
  File "/usr/bin/exaile", line 96, in __init__
    self.database_connect()
  File "/usr/bin/exaile", line 869, in database_connect
    self.db.check_version("sql")
  File "/usr/share/exaile/xl/db.py", line 134, in check_version
    row = self.read_one("db_version", "version", "1=1", tuple())
  File "/usr/share/exaile/xl/db.py", line 265, in read_one
    cur.execute(query, args)
OperationalError: no such table: db_version

```

I am on Dapper, btw.

---

### Post by golem3 on 2006-12-14
> **cborga1985 said:**
> none really but some people had problems with the deb

Yep, even after I did the sudo apt-get install (boat load of dependencies here) 

the .deb fails to load for a libatk1.1 or something, a dependency that I cannot find via Synaptic to download. 

Oh well.

---

### Post by terminatorkobold on 2006-12-15
> **cborga1985 said:**
> Sounds like you haven't enabled all the repositories. A quick guide to do that [here]("http://ubuntuguide.org/wiki/Dapper#Repositories").

Hello cborga,

I modified my sources.list file following the guide bu I still get the same error message when trying to get the python-gtk2-dev package. Do you have another sugestion?

Thanks

Christophe

---

### Post by ihavenoname on 2006-12-21
> **cborga1985 said:**
> 

**Fifth**
*Compile program*
```
make
```

**Sixth**
*Compile a debian package*
```
sudo dpkg-buildpackage
```
wait for it to build


is that how you build most debian packages? Or must it already have the debian folder inside? I am just learning the art (some may say the dark art) of Debian packaging.

---

### Post by cborga1985 on 2006-12-28
> **ihavenoname said:**
> is that how you build most debian packages? Or must it already have the debian folder inside? I am just learning the art (some may say the dark art) of Debian packaging.
yeah once it has a control file which is in the debian folder of the source package. if it does not already have that you have to make your own control, and other things. i don't know that much about that. usually i patch stuff with premade control files from older versions or just use checkinstall sometimes.

---

### Post by cborga1985 on 2006-12-28
> **foxy123 said:**
> AFter building the package I have the following error:
```
$ exaile
Traceback (most recent call last):
  File "/usr/bin/exaile", line 2291, in ?
    main()
  File "/usr/bin/exaile", line 2281, in main
    exaile = ExaileWindow(options, fr)
  File "/usr/bin/exaile", line 96, in __init__
    self.database_connect()
  File "/usr/bin/exaile", line 869, in database_connect
    self.db.check_version("sql")
  File "/usr/share/exaile/xl/db.py", line 134, in check_version
    row = self.read_one("db_version", "version", "1=1", tuple())
  File "/usr/share/exaile/xl/db.py", line 265, in read_one
    cur.execute(query, args)
OperationalError: no such table: db_version

```

I am on Dapper, btw.
Delete the .exaile folder in your home directory.
```
cd ~
rm -r .exaile
```

> **golem3 said:**
> Yep, even after I did the sudo apt-get install (boat load of dependencies here) 

the .deb fails to load for a libatk1.1 or something, a dependency that I cannot find via Synaptic to download. 

Oh well.
never had that happen

> **terminatorkobold said:**
> Hello cborga,

I modified my sources.list file following the guide bu I still get the same error message when trying to get the python-gtk2-dev package. Do you have another sugestion?

Thanks

Christophe
did you run this
```
sudo apt-get update
``` to update the package lists?

---

### Post by ihavenoname on 2006-12-28
> **cborga1985 said:**
> yeah once it has a control file which is in the debian folder of the source package. if it does not already have that you have to make your own control, and other things. i don't know that much about that. usually i patch stuff with premade control files from older versions or just use checkinstall sometimes.

ah, thanx!

---

### Post by ufugu on 2006-12-30
thanks so much for the straightforward instructions.  it took just a couple minutes to get this done and its running well on my ppc.  exaile is a great player.

---

