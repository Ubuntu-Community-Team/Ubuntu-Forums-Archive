---
title: "How-to install Monotheka"
date: 2005-05-24
forum: Outdated Tutorials &amp; Tips
---

### Post by A-star on 2005-05-24
How-to install Monotheka

Monotheka is a (yet!) simple application to organize and keep track of your movie catalogue. It runs on Linux platform using the GTK toolkit. It's designed to be simple and GNOME / HIG compliant. It's written in Mono. It's free.

Dowload Monotheka from the following url in a directory of your choice
wget [http://forge.novell.com/modules/xfcontent/private.php/monotheka/0.1-ALPHA/monotheka-0.0.5.tar.gz](http://forge.novell.com/modules/xfcontent/private.php/monotheka/0.1-ALPHA/monotheka-0.0.5.tar.gz)

Add the backport repo to your list of repositories
sudo gedit /etc/apt/sources.list
and add at the end of file

deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted

Then type :
sudo apt-get update

then open a terminal and install Mono:
sudo apt-get install libmono0 libmono-dev mono mono-assemblies-arch mono-common mono-devel mono-gac mono-jay mono-jit mono-mcs mono-utils

Install sqlite
sudo apt-get install sqlite libsqlite0 libsqlite0-dev sqlite-doc

Install gtk-sharp
sudo apt-get gtk-sharp-gapi gtk-sharp-examples

Now onto installing Monotheka
tar -zxvf monotheka-0.0.5.tar.gz
cd monotheka-0.0.5
./configure
make
sudo make install

there should now be a menu-item called monotheka in the applications/sound & video menu.

I wrote down what I remembered, so there could be a mistake in it somewhere.
Let me know and I will correct it.

---

### Post by Sniffer on 2005-05-24
Thks for letting me know of this app.

It seems good, long live Gnome. \\:D/

---

### Post by darksides on 2005-05-24
I'v got an error about mono version.....

```
* Running monoBOIL                                 ;,'
  Auto-configure tool for mono stuff       _o_    ;:;'
  GPL Licence, 0.1.0                   ,-.'---`.__ ;
  Copyright MDK <mdk@mdk.org.pl>      ((j`=====',-'
                                       `-\     /
                                          `-=-'

Checking for sanity...
      * make [OK]
      * pkg-config [OK]
      * sed [OK]
      * awk [OK]
      * mcs [OK]
      * fold [OK]
      * install [OK]

Configuring: Monotheka [0.0.5 "Use me, I'm yours"] ...

Parsing commandline parameters...

Configuring install paths...
   PREFIX: /usr [auto]
   BINDIR: /usr/bin [auto]
   LIBDIR: /usr/lib [auto]
   DATADIR: /usr/share [auto]
   PKGCONFIG: /usr/lib/pkgconfig [auto]

Sleeping to let you see...5 4 3 2 1

Checking for required components...
   Checking for pkg dependencies...
      * mono-1.0.6 [NOT FOUND!] (1.0.5)


   |--- ERROR ---
   | The required package could not be found in your
   | system! Make sure it's installed and pkg-config'ed
   |
   |     This software was NOT configured! If you
   | think this is a script error please report it to
   | bugzilla (NovelForge, project Monotheka). You can
   | obatin some more information how monoBOIL works
   | by typing './configure --help' . A
   | 'configure.log' file was created during the
   | process, please attach it.

```

---

### Post by Majlo on 2005-05-24
Hi ..
You must add backport repo in /etc/apt/sources.list

*sudo gedit /etc/apt/sources.list*

and add at the end of file 

[I]deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted[/I]

Then type :
*sudo apt-get update*

---

### Post by A-star on 2005-05-25
[QUOTE=Majlo]Hi ..
You must add backport repo in /etc/apt/sources.list

*sudo gedit /etc/apt/sources.list*

and add at the end of file 

[I]deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted[/I]

Then type :
*sudo apt-get update*[/QUOTE]
 added this to the the how-to

---

### Post by nehalem on 2005-06-21
Hmmm, I'm a little nervous about changing to the backport version of mono.  Does it break any problems, seems like some people complained that it did at one time.

---

### Post by thechitowncubs on 2005-06-21
Cool Program!

---

### Post by A-star on 2005-06-21
[QUOTE=nehalem]Hmmm, I'm a little nervous about changing to the backport version of mono.  Does it break any problems, seems like some people complained that it did at one time.[/QUOTE]
 I have experienced no problems at all.
But I'm only using monotheka and no other mono programs that I know off.

---

### Post by nehalem on 2005-06-21
Ok I installed it and this app reminds me of the other nice mono apps like f-spot.  Has everything I wanted and is easy enough to pick up and use in minutes.  

Nice How to.

---

### Post by xalphas on 2005-06-21
Got the latest mono. Compiled with success and installed. Later ;

```
xalphas@ubuntu:~/getto/monotheka-0.0.5$ monotheka

Unhandled Exception: System.InvalidOperationException: Invalid connection string: no URI
in <0x0032d> Mono.Data.SqliteClient.SqliteConnection:SetConnectionString (System.String connstring)
in <0x00010> Mono.Data.SqliteClient.SqliteConnection:set_ConnectionString (System.String value)
in <0x00019> Mono.Data.SqliteClient.SqliteConnection:.ctor (System.String connstring)
in <0x00091> MovieDatabase.MovieDB:InitDB (System.String filename)
in <0x0011b> Global:Main (System.String[] args)
``` 

Any ideas?

---

### Post by A-star on 2005-06-22
> **xalphas]Got the latest mono. Compiled with success and installed. Later  said:**
>  args)
``` 

Any ideas?
 I would say a problem with sqlite.
Did you install sqlite?

---

### Post by xalphas on 2005-06-22
Yep it looks like Sqlite but i followed the steps and installed Sqlite package . Not Sqlite3 package. But i think this is an error about whole mono thing. Cause Beagle, F-spot also gives errors. I wrote about that in other applications forum. 

Anyway thx.

---

### Post by Swoop on 2005-06-25
works great.. thanks alot for the howto ;)

btw a little mistype (or letout) on the howto:

original text:  sudo apt-get gtk-sharp-gapi gtk-sharp-examples

correct text:  sudo apt-get **install** gtk-sharp-gapi gtk-sharp-examples

---

