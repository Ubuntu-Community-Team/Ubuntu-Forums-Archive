---
title: "canon pixma  mp470"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by simonvdavis on 2008-04-29
hi there any body out there could help with installing this printer 
                 it would be music to my ears 


                              thanks sim

---

### Post by mikeyphi on 2008-04-29
In a previous thread - it was reported that the MP610 driver gave a good function. It's worth a try - or you have to buy Turboprint!

Look here for the procedure: 
[http://mp610.blogspot.com/2007/11/setup-canon-pixma-mp600-or-mp610.html](http://mp610.blogspot.com/2007/11/setup-canon-pixma-mp600-or-mp610.html)

---

### Post by Eric Qel-Droma on 2008-07-01
I, too, have an MP470.  I tried the 610 drivers, but color was all wonky.  The 150 drivers seem to be doing a decent basic job of printing, but I haven't tried scanning yet.

Eric

---

### Post by Eric Qel-Droma on 2009-04-25
For what it's worth (I know this thread is old), but I just scanned with my Pixma MP470 in Jaunty (using the MP150 driver for the printer--I don't know if that matters for the scanning program).  I used the XSane program that came with Jaunty.  

Everything was quick and easy and seemed to work fine.  I wasn't doing anything complicated; it was just so I could email a document.  However, I started and was done within two minutes.

Eric

---

### Post by spinwheel on 2009-05-25
Thanks, that worked for me. 

Thanks for replying even the old post :) sometimes it comes into help for somebody.
like me :)

---

### Post by regx on 2009-12-06
I have had great success with this printer by installing sane and guttenprint from cvs. It sounds like the scanner is working fine for everyone, so here is a simple how to for installing the print drivers.

To build the drivers you will need to have build-essential installed
```
sudo apt-get install build-essential
```

1. Download the latest version of the drivers from [http://gutenprint.sourceforge.net/p_Download.php](http://gutenprint.sourceforge.net/p_Download.php)

I recommend checking out from cvs so you can easily do updates of course to do this you need cvs installed
```
sudo apt-get install cvs
```

then checkout from cvs. First cd into the directory where you want the source code to be downloaded then type
```
cvs -d:pserver:anonymous@gimp-print.cvs.sourceforge.net:/cvsroot/gimp-print login

cvs -z3 -d:pserver:anonymous@gimp-print.cvs.sourceforge.net:/cvsroot gimp-print co -P print
```

Then Build the package
Note: If you already have guttenprint installed you should uninstall it first. If you have installed it previously from cvs just do make clean
cvs up and you are ready to re-install.
```
automake
./configure --prefix="/usr" --enable-cups-ppds
make
sudo make install
```

Note: I used the Canon MP160 driver which seems to work great.

---

