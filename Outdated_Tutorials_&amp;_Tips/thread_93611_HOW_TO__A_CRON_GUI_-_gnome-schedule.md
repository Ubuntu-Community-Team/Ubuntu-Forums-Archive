---
title: "HOW TO:  A CRON GUI - gnome-schedule :"
date: 2005-11-22
forum: Outdated Tutorials &amp; Tips
---

### Post by GrammatonCleric on 2005-11-22
[B]
HOW TO:  A CRON GUI - gnome-schedule :[/B]

Download and install:

```

    sudo apt-get install python-gtk2
    sudo apt-get install python-gtk2-dev

``` 

Download gnome-shedule source tarball:

[http://prdownloads.sourceforge.net/gnome-schedule/gnome-schedule-0.9.0.tar.bz2?download](http://prdownloads.sourceforge.net/gnome-schedule/gnome-schedule-0.9.0.tar.bz2?download)

[ ]("http://kent.dl.sourceforge.net/sourceforge/gnome-schedule/gnome-schedule-0.9.0.tar.bz2")
Extract the tared file:

```


    tar jxvf gnome-schedule-0.9.0.tar.bz2


``` 
Change into the extracted directory:

```


    cd gnome-schedule-0.9.0 


``` 
Configure the source:

```


    ./configure


``` 
Compile the source:

```

 
   make


``` 
Install the compiled source:

```


    sudo make install

``` 
From a terminal command line or from a launcher run...

```


    gnome-schedule


``` 
**NOTE: to use gnome-schedule to schedule jobs as root from the command line run....**

```

    
      sudo  gnome-schedule


``` 
GC

---

### Post by shof2k on 2005-11-29
Any chance of a screenshot?

---

### Post by Hyun on 2005-11-29
[source]("https://gaute.vetsj.com/~drzap/gnome-schedule/screenshots/2005-07-27-150249_1280x1024_scrot.png") ;)

---

### Post by artnay on 2005-11-29
Instead of making "sudo make install", you should build a .deb file using checkinstall. It's the easiest way to build a package. Just do "sudo apt-get install checkinstall" before anything else and replace "sudo make install" with "sudo checkinstall". That way it's easy to remove a program, you don't need make clean.

Please write HOWTOs to use checkinstall instead of make install! Mods, edit when needed! ;)

For creating packages with dependencies, you should check [http://www.us.debian.org/devel/]("http://www.us.debian.org/devel/")

---

### Post by Spudgun on 2005-11-29
Cheers, worked nicely apart from I had to install an XML parsing module for Perl.

---

### Post by Sionide on 2005-11-29
[QUOTE=Spudgun]Cheers, worked nicely apart from I had to install an XML parsing module for Perl.[/QUOTE]

Me too,

for newbies;

type

```
cpan
```

then

```
install XML::Parser
```

then

```
exit
```

then try ./configure again.

OR - do the checkinstall thing, that stuff is quality - I wish I'd remembered to do it BEFORE I compiled it the normal way. :mad:

Anyway, great HOWTO - perhaps someone can see about getting this included in Dapper??

---

### Post by ow50 on 2005-11-30
[QUOTE=Sionide]Me too,

for newbies;

type

```
cpan
```
...[/QUOTE]
Rather
```
sudo apt-get install libxml-parser-perl
```

---

### Post by phyzome on 2006-04-06
I used the checkinstall to build a .deb package, and uploaded it to my server.  I'm not vouching for it, but here's the [deb package for gnome-scheduler]("http://brainonfire.net/blog/main/wp-content/uploads/2006/05/gnome-schedule-0.9.0_0.9.0-1_i386.deb") (updated URL).

---

### Post by altonbr on 2007-05-12
It's now in the repositories for 7.04.

---

### Post by abhiroopb on 2008-06-06
Where is the "default UNIX mailbox" where all the outputs are sent? Can I change this? ideally I would like outputs to come to my home folder as log files (if possible).

---

### Post by altonbr on 2008-06-06
> **abhiroopb said:**
> Where is the "default UNIX mailbox" where all the outputs are sent? Can I change this? ideally I would like outputs to come to my home folder as log files (if possible).

Are you running one-liners or a script?

You can write to a file, either by erasing each time (>) or appending each time (>>).

Example after being ran three times:

ls > dir_listing.log
> foo/ bar/
ls >> dir_listing.log
> foo/ bar/
foo/ bar/
foo/ bar/

If you want to make a new log every single time it runs, you'll need to write a script to make a variable such as:
```
THEDATE=`date '+%Y%m%d-%s'` # 20071010-1192044000
```
so you then can append a Unix timestamp to your log like so:
```
ls > dir_listing-$THEDATE.log # dir_listing-20071010-1192044000.log
```

Does that make sense?

---

### Post by abhiroopb on 2008-06-06
I'm a little confused. Basically I have a bash script, for rsync backup, and it creates its own log file.  So it isn't so essential that a log file is created, however, I was just wondering where this magical "UNIX mailbox" was. I am using gnome-schedule 1.0.1 (from repo) and when I create a cron job underneat there is an option for "Output", which if I scroll over says it saves the outputs in the defualt UNIX mailbox.

---

### Post by altonbr on 2008-06-06
> **abhiroopb said:**
> I'm a little confused. Basically I have a bash script, for rsync backup, and it creates its own log file.  So it isn't so essential that a log file is created, however, I was just wondering where this magical "UNIX mailbox" was. I am using gnome-schedule 1.0.1 (from repo) and when I create a cron job underneat there is an option for "Output", which if I scroll over says it saves the outputs in the defualt UNIX mailbox.

The default UNIX mailbox can be accessed by typing  'mail' in the command line I believe. It is a little archic nowadays, but still used by system administrators. Instead of letting it create a log to UNIX mail, tell it to create a log at /home/<your username/logs/my_log.log

---

### Post by abhiroopb on 2008-06-06
> **altonbr said:**
> The default UNIX mailbox can be accessed by typing  'mail' in the command line I believe. It is a little archic nowadays, but still used by system administrators. Instead of letting it create a log to UNIX mail, tell it to create a log at /home/<your username/logs/my_log.log

How do I tell it to create a log in the home directory? Would that be using your command? If so, like I said I don't want to use such a complicated method.

---

### Post by abhiroopb on 2008-06-06
I think I see the problem: according to this  [https://sourceforge.net/mailarchive/forum.php?thread_name=5a5b14cf0802081037s2dcd398fkc0ed3e0a2e983daa%40mail.gmail.com&forum_name=gnome-schedule-devel](https://sourceforge.net/mailarchive/forum.php?thread_name=5a5b14cf0802081037s2dcd398fkc0ed3e0a2e983daa%40mail.gmail.com&forum_name=gnome-schedule-devel) gnome schedule creates its logfile in .gnome/gnome-schedule SINCE version 1.1.0. The version in the repo is 1.0.1 (a bit old). However, when I try to compile the latest version I get the following error:

```

abhiroop@Vanimo:~/MyDownloads/gnome-schedule-2.0.2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for python... /usr/bin/python
checking for python version... 2.5
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.5/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.5/site-packages
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PYGTK... yes
checking for pkg-config... /usr/bin/pkg-config
checking PYTHONPATH env variable for PyGTK... /usr/lib/python2.4/site-packages
checking for gtk.glade... found
checking for GNOMEPYTHON... configure: error: Package requirements (gnome-python-2.0 >= 2.12.0) were not met:

No package 'gnome-python-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GNOMEPYTHON_CFLAGS
and GNOMEPYTHON_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

Any thoughts?

---

