---
title: "installing tar.gz problem"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by T2manner on 2008-05-06
no matter what i do, installing never works

i'v extracted the archive to my desktop
chaned the directory to the folder
then did the sudo ./configure and it did its thing
then when i try to do sudo make i get this```
relyt@relyt-desktop:~/Desktop/eboard-1.1.1$ sudo make
make: *** No targets specified and no makefile found.  Stop.

```

and when i do sudo make install i get this [```
relyt@relyt-desktop:~/Desktop/eboard-1.1.1$ sudo make install
make: *** No rule to make target `install'.  Stop.

```

and if i try to do checkinstall i get this ```
relyt@relyt-desktop:~/Desktop/eboard-1.1.1$ sudo checkinstall

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>> 

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@relyt-desktop ]
1 -  Summary: [ Package created with checkinstall 1.6.1 ]
2 -  Name:    [ eboard ]
3 -  Version: [ 1.1.1 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ eboard-1.1.1 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

relyt@relyt-desktop:~/Desktop/eboard-1.1.1$ 


```





there's got to be something i'm doing wrong because installing from source never works for me

---

### Post by PeterJS on 2008-05-06
Did the configure complete successfully? Your problem is that you don't have a makefile, which is why make isn't working. The makefile is supposed to be written by the configure script when it successfully completes. The odds of a configure script succedding the first time are nearly astronomical, so try running it again and seeing if there are any errors when it quits.

---

### Post by T2manner on 2008-05-06
well this is what i got
```
relyt@relyt-desktop:~/Desktop/eboard-1.1.1$ sudo ./configure
configuring eboard 1.1.1...
checking sanity of install... ok
testing C++ compiler...
  trying g++ ... it works
header verification:
  all headers found.                    
header verification:
  sys/audioio.h       : no              
checking for IPPROTO_TCP in netinet/in.h... yes
checking for TCP_NODELAY in netinet/in.h... no
checking for SOL_TCP in netinet/in.h... no
checking for IPPROTO_TCP in netinet/tcp.h... no
checking for TCP_NODELAY in netinet/tcp.h... yes
checking for SOL_TCP in netinet/tcp.h... yes
  net options: netinet/tcp.h required, IPPROTO_TCP present.
looking for pkg-config... /usr/bin/pkg-config
looking for GTK+ version... Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
NOT FOUND, WILL NOT DO (must be >= 2.0.0 and < 2.99.9)
** The currently installed GTK+ version cannot be used to
** compile eboard, it is recommended you get the latest one.
** GTK+'s site: http://www.gtk.org
relyt@relyt-desktop:~/Desktop/eboard-
```

---

### Post by Monicker on 2008-05-06
Trying installing this package:

```
sudo apt-get install libgtk2.0-dev
```


Also, eboard is in the repositories, albeit a slightly older version, if you don't want to manually compile it.

```
sudo apt-get install eboard
```


I don't what feature differences there are.  Its been a while since I've used eboard.  I've always been more partial to xboard.

---

### Post by T2manner on 2008-05-06
thanks
i'll try xboard too, i just want to know how to install from source.

---

### Post by Monicker on 2008-05-06
> **T2manner said:**
> thanks
i'll try xboard too, i just want to know how to install from source.

You should be able to install eboard from source once you have the gtk dev libraries; I would stick with the Ubuntu packages for those.

The more you mix external source packages with a system based on a package manager, the more risk you have of problems later.

I use source packages too sometimes, but they are pretty self-contained, and I know they won't overwrite a bunch of other system files.

---

### Post by T2manner on 2008-05-06
okay i installed it
now how do i remove it?

---

### Post by PeterJS on 2008-05-06
Did you install it with checkinstall or make install?

For check install search synaptic for the name you gave the package and uninstall it like you would anything else. If you used make install, consider it a learning expernice, try sudo make uninstall, and hope for the best.

---

### Post by T2manner on 2008-05-06
checkinstall

---

