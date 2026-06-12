---
title: "DrScheme in repo is broken..."
date: 2006-08-21
forum: Programming Talk
---

### Post by deepspring on 2006-08-21
Hi guys,

Just lettin everyone know that the drscheme and mzscheme packages in the universe repositories seem to be broken. They appear to fail to fully install  and apt will constantly spit errors at you telling you so, even when you are trying to install a package that has nothing to do with either of these packages.

I recommend grabbing the latest "Ubuntu (Dapper)" versions directly from the mzscheme and drscheme sites here:
[list]
[*][http://www.plt-scheme.org/software/mzscheme/](http://www.plt-scheme.org/software/mzscheme/)
[*][http://www.drscheme.org/](http://www.drscheme.org/)
[/list]

Install instructions are provided on the download pages.

I've spent the last two and a bit hours trying to fix the issue on my system, in the end this worked:
```
sudo rm -rf /var/lib/dpkg/info/mzscheme*
sudo rm -rf /var/lib/dpkg/info/drscheme*
sudo apt-get install <some installed package name>

```

Hope this helps...

---

### Post by LordHunter317 on 2006-08-21
Without posting the errors, no one can verify what you said as true or not.

It's somewhat specious to make such claims and offer a workaround without some proof.

---

### Post by deepspring on 2006-08-21
Ok..

```

[scott@lazerus: ~ ]$ sudo apt-get install drscheme
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  mzscheme
Suggested packages:
  menu
The following NEW packages will be installed:
  drscheme mzscheme
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/13.7MB of archives.
After unpacking 68.3MB of additional disk space will be used.
Do you want to continue [Y/n]?
Preconfiguring packages ...
Selecting previously deselected package mzscheme.
(Reading database ... 120289 files and directories currently installed.)
Unpacking mzscheme (from .../mzscheme_1%3a209-9ubuntu2_i386.deb) ...
Selecting previously deselected package drscheme.
Unpacking drscheme (from .../drscheme_1%3a209-9ubuntu2_i386.deb) ...
Setting up mzscheme (209-9ubuntu2) ...
Completing install...Running setup...
setup-plt: Setup version is 209
setup-plt: PLT home directory is /usr/lib/plt
setup-plt: Collection paths are
setup-plt:   /usr/lib/plt/collects
setup-plt: Installing MrEd launcher /usr/lib/plt/bin/drscheme
setup-plt: Installing MrEd launcher /usr/lib/plt/bin/games
setup-plt: Installing MrEd launcher /usr/lib/plt/bin/help-desk
setup-plt: Installing MzScheme launcher /usr/lib/plt/bin/mzc
setup-plt: Installing MzScheme launcher /usr/lib/plt/bin/mzpp
setup-plt: Installing MzScheme launcher /usr/lib/plt/bin/mztext
setup-plt: Installing MzScheme launcher /usr/lib/plt/bin/setup-plt
setup-plt: Installing MzScheme launcher /usr/lib/plt/bin/slatex
setup-plt: Installing MzScheme launcher /usr/lib/plt/bin/pdf-slatex
setup-plt: Installing MrEd launcher /usr/lib/plt/bin/slideshow
setup-plt: Installing MzScheme launcher /usr/lib/plt/bin/swindle
setup-plt: Installing MrEd launcher /usr/lib/plt/bin/framework-test-engine
setup-plt: Installing MzScheme launcher /usr/lib/plt/bin/framework-test
setup-plt: Installing MzScheme launcher /usr/lib/plt/bin/tex2page
setup-plt: Installing MrEd launcher /usr/lib/plt/bin/web-server
setup-plt: Installing MzScheme launcher /usr/lib/plt/bin/web-server-text
setup-plt: Installing MzScheme launcher /usr/lib/plt/bin/web-server-monitor
setup-plt: Post-Installing MrEd
setup-plt: Done setting up
PLT installation done.
finished
Building MzScheme zo files:  This can take a LONG time (10 minutes in some cases!)
finished.
Cataloging SLIB routines...
reference to undefined identifier: with-load-pathname
dpkg: error processing mzscheme (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of drscheme:
 drscheme depends on mzscheme (= 1:209-9ubuntu2); however:
  Package mzscheme is not configured yet.
dpkg: error processing drscheme (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mzscheme
 drscheme
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Unfortunately, because all the crap I've done to rid my self of the previous errors, I can't seem to get it to replicate the exact same error messages.

The previous error messages were pointing to pair of files in "/var/lib/dpkg/info" called "drscheme.postinst" and "mzscheme.postinst*".

The errors looked like a combination of the the above errors with lines like this:
```
Completing install.../var/lib/dpkg/info/drscheme.postinst: 51: /usr/lib/plt/install: not found
```

---

### Post by deepspring on 2006-08-21
Anyone want to install mzscheme and drscheme to help verify the errors?

---

### Post by LordHunter317 on 2006-08-21
There's a packaging bug.  Fixing the postinst scripts and running 'dpkg --configure -a' would fix the problem.

Anyway, when I get a chance, I'll make a fresh dapper install and report it.

---

### Post by deepspring on 2006-08-21
Thank you LordHunter317.

---

### Post by rubliwdrahcir on 2006-08-24
I selected DrScheme from Applications->Add/Remove and was greeted with similar results.  I am running Dapper on an iBook 14" PPC G4 and tried to install DrScheme development environment so I could try my hand at learning the language.  DrScheme depends on MzScheme which has a problem installing.  Log follows:

Setting up mzscheme (209-9ubuntu2) ...
Completing install...This program should be used again only when the PLT tree was moved.
You should use bin/setup-plt instead.
finished
Building MzScheme zo files:  This can take a LONG time (10 minutes in some cases!)
finished.
Cataloging SLIB routines...
reference to undefined identifier: with-load-pathname
dpkg: error processing mzscheme (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of drscheme:
 drscheme depends on mzscheme (= 1:209-9ubuntu2); however:
  Package mzscheme is not configured yet.
dpkg: error processing drscheme (--configure):
 dependency problems - leaving unconfigured


Any ideas?  I haven't seen any update available for MzScheme.

---

### Post by deepspring on 2006-08-25
LordHunter317's advice is probably safer than doing the following, but I have no idea what I need to fix, so here it goes...

NOTE: this worked for me, but I'm not sure if it will work for you.

Do this...
```

sudo rm -rf /var/lib/dpkg/info/mzscheme*
sudo rm -rf /var/lib/dpkg/info/drscheme*

```

Then this...
```

sudo apt-get install mzscheme drscheme

```

Then this...
```

sudo apt-get remove --purge drscheme mzscheme
sudo rm -rf /usr/lib/plt

```

And this...
```

wget -c http://download.plt-scheme.org/bundles/352/plt/plt-352-bin-i386-linux-ubuntu-dapper.sh
wget -c http://download.plt-scheme.org/bundles/352/mz/mz-352-bin-i386-linux-debian-unstable.sh
sudo chmod +x ./plt-352* 
sudo chmod +x ./mz-352*
sudo ./plt-352-bin-i386-linux-ubuntu-dapper.sh
sudo ./mz-352-bin-i386-linux-debian-unstable.sh

```

Both installation scripts will prompt you for stuff, just do the following for both of them:
Q1. [enter]
Q2. [enter]
Q3. [y], [enter]

If you get prompted to overwrite something, just say: [y], [enter].

Now create a menu entry...

Do this...
```

sudo ln -s /usr/plt/collects/icons/PLT-206.png /usr/share/pixmaps/PLT-206.png
sudo gedit /usr/share/applications/drscheme.desktop

```

And finally paste this into the file...
```

[Desktop Entry]
Name=DrScheme
Comment=Scheme Programming Environment
Exec=/usr/bin/drscheme
Icon=/usr/share/pixmaps/PLT-206.png
Terminal=false
MultipleArgs=false
Type=Application
Categories=Application;Development;
StartupNotify=true

```

Save the file, close it. If all went well, you should be able to run DrScheme... Applications -> Development -> DrScheme


Edit: found the icon, updated the above.

---

### Post by shat on 2007-01-09
This Edgy package is still broken.  Same bug.  Same fix at least 8) 

Just popping in to report!

---

### Post by razzmataz on 2007-01-13
I don't know if any one has looked into this again, but it looks like line 56 of the postinst script for mzscheme is trying to creat a new catalog for slib, which is borking with the error message:

reference to undefined identifier: with-load-pathname

Looks like this is the offending command:
/usr/bin/mzscheme -vm -L load.ss slibinit -e "(require 'new-catalog)"

I'd send a patch if I knew more scheme than I do know...

---

### Post by fractal13 on 2007-02-14
Edit /var/lib/dpkg/info/mzscheme.postinst

After export PLTHOME

Add 

export SCHEME_LIBRARY_PATH=/usr/share/slib 

Run dpkg --configure -a

---

