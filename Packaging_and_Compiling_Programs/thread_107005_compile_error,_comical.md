---
title: "compile error, comical"
date: 2005-12-22
forum: Packaging and Compiling Programs
---

### Post by Nrvnqsr on 2005-12-22
hi all, well I'm having this issue when compiling and gave me this error

> 
nrvnqsr@ALTROUGE2:~/comical-0.7$ sudo make
`wx-config --cxx` `wx-config --cxxflags` -O2 -Wall -pipe -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -DRARDLL -D_UNIX -Iunrar -c -o src/ComicBook.o src/ComicBook.cpp
/bin/sh: wx-config: command not found
/bin/sh: wx-config: command not found
/bin/sh: -O2: command not found
make: *** [src/ComicBook.o] Error 127
nrvnqsr@ALTROUGE2:~/comical-0.7$


pretty much I have build-essential from repos
don't know if I'm missing anything else
and also how do I make it compile into a *.deb package?

thanks again

---

### Post by amohanty on 2005-12-22
I think you need to install the libwxgtk and python-wxgtk packages. Search in synaptic for wx in name only.

> and also how do I make it compile into a *.deb package?

instead of
> sudo make install

use the checkinstall package ie:

> sudo checkinstall

That will automatically create a deb and install it for you. Removable using:
> dpkg -r <package_name>

HTH

---

### Post by Nrvnqsr on 2005-12-22
I checked for those 2 in synaptic and they were marked as installed

> nrvnqsr@ALTROUGE2:~/comical-0.7$ sudo make install
make: *** No rule to make target `install'.  Stop.
nrvnqsr@ALTROUGE2:~/comical-0.7$ ls -a
.          **Comical Icons**              COPYING   Makefile.mingw  **src**
..         Comical.kdevelop           **doc-pak**   Makefile.vc     TODO
AUTHORS    Comical.kdevelop.filelist  Doxyfile  NEWS            **unrar**
ChangeLog  **Comical.pbproj**             Makefile  README
nrvnqsr@ALTROUGE2:~/comical-0.7$


even with the make install is still a no go

**BIG EDIT**
I marked the newer wxGTK that are found in the repos and compiled the program, but failed to make a deb package

---

### Post by amohanty on 2005-12-22
> but failed to make a deb package


What do you mean ?

---

### Post by mo_x on 2005-12-22
Is there no ./configure script? Normal sequence of compiling a package is:
./configure
make
sudo make install

---

### Post by Nrvnqsr on 2005-12-22
I mean creating a *.deb so that I don't have to compile when I need to install it on another PC 

I did the "sudo checkinstall" command
and gave me this

> 
nrvnqsr@ALTROUGE2:~/comical-0.7$ sudo checkinstall
Password:

checkinstall 1.5.3, Copyright 2001 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist.
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

Installing with "make install"...

========================= Installation results ===========================

Copying documentation directory...
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Restoring overwritten files from backup...OK

Cleaning up...OK

Bye.


> 
Is there no ./configure script? Normal sequence of compiling a package is:
./configure
make
sudo make install


it doesn't have a ./configure script
> 
bash: ./configure: No such file or directory


---

### Post by amohanty on 2005-12-24
What does the README or INSTALL (usually there with the source say)

AM

---

### Post by Nrvnqsr on 2005-12-24
pretty much nothing, all that it has is only "what new", requirements, and copyrights.

here's the site if you want to check out the source
[http://comical.sourceforge.net/](http://comical.sourceforge.net/)

---

### Post by amohanty on 2005-12-24
Ok, I downloaded it:

do the following:
> tar xzf comical-0.7.tar.gz
cd comical-0.7
sudo apt-get install libwxgtk2.6-0 libwxgtk2.6-dev python-wxgtk2.6
make comical

This will create a binary in the same folder called > comical
Copy it over to /usr/bin via:
> sudo cp comical /usr/bin

Thats all you need to do. Since it outputs only a single file, you _dont_ need a deb, just copy the abovementioned file voer to whichever machine you want in /usr/bin

I have also attached the gzipped executable in case you want to use it directly. To run it just download the file, unzip it and double click on it.

NOTE: this was build on gnome and gtk, so might look wierd if you are using kubuntu.

HTH

[ATTACH]4812[/ATTACH]

---

### Post by Nrvnqsr on 2005-12-25
well, it can't be helped but I appreciated the help

---

### Post by amohanty on 2005-12-26
> well, it can't be helped ...

What do you mean.??

AM

---

### Post by Nrvnqsr on 2005-12-26
[QUOTE=amohanty]What do you mean.??

AM[/QUOTE]

I was just hoping to create a deb package for backup so that I don't need to compile it again.

---

### Post by amohanty on 2005-12-26
Its just one file, so you will not need to create a deb. Just backup that one file. If you really, really, really want to create a deb file, use your favorite editor to edit Makefile in the source. Change the **comical** target to **install** and make sure that you add a > cp comical /usr/bin within the **install** target. 

HTH
AM

---

### Post by Nrvnqsr on 2006-06-11
sorry bring a long dead thread, anyways

pretty much in Breezy, I can compile with no problem, but with Dapper it gives me this errors

> 
make -C src
make[1]: Entering directory `/home/danny/comical-0.8/src'
make[1]: Leaving directory `/home/danny/comical-0.8/src'
make[1]: Entering directory `/home/danny/comical-0.8/src'
Converting firstpage.png
Converting prevpage.png
Converting prev.png
Converting next.png
Converting nextpage.png
Converting lastpage.png
Converting rot_cw.png
Converting rot_ccw.png
Converting open.png
Converting fullscreen.png
Converting exit.png
make[1]: Leaving directory `/home/danny/comical-0.8/src'
make[1]: Entering directory `/home/danny/comical-0.8/src'
cc `wx-config --cxxflags` -O2 -Wall -pipe -D_UNIX -I../unrar -I../unzip -c -o ComicalApp.o ComicalApp.cpp
cc `wx-config --cxxflags` -O2 -Wall -pipe -D_UNIX -I../unrar -I../unzip -c -o ComicalBrowser.o ComicalBrowser.cpp
cc `wx-config --cxxflags` -O2 -Wall -pipe -D_UNIX -I../unrar -I../unzip -c -o ComicalCanvas.o ComicalCanvas.cpp
cc `wx-config --cxxflags` -O2 -Wall -pipe -D_UNIX -I../unrar -I../unzip -c -o ComicalFrame.o ComicalFrame.cpp
cc `wx-config --cxxflags` -O2 -Wall -pipe -D_UNIX -I../unrar -I../unzip -c -o ComicalManager.o ComicalManager.cpp
cc `wx-config --cxxflags` -O2 -Wall -pipe -D_UNIX -I../unrar -I../unzip -c -o ComicBook.o ComicBook.cpp
ComicBook.cpp: In member function &#8216;virtual void* ComicBook::Entry()&#8217;:
ComicBook.cpp:540: warning: operation on &#8216;target&#8217; may be undefined
cc `wx-config --cxxflags` -O2 -Wall -pipe -D_UNIX -I../unrar -I../unzip -c -o ComicBookDir.o ComicBookDir.cpp
cc `wx-config --cxxflags` -O2 -Wall -pipe -D_UNIX -I../unrar -I../unzip -c -o ComicBookRAR.o ComicBookRAR.cpp
make[1]: Leaving directory `/home/danny/comical-0.8/src'
make: *** [src/ComicalApp.o] Error 2


since I'm still a newb in compiling I have no idea what I miss, and son't know what "Error 2" means.
I compiled both version 0.7 and 0.8 still give this error any ideas?

---

### Post by Hikaru79 on 2006-06-11
If you are still having problems with this package, you might want to check out "Comix" from the Ubuntu repositories. It does the exact same things as comical, but it has the benefit of already being in the repos.

---

### Post by Nrvnqsr on 2006-06-12
yeah, but comical is somehow more resposive and resource friendly on my pc than comix, and the gui is easy for me on comical

---

### Post by simplyw00x on 2006-06-12
Nrvnqsr, check your PMs. I can make you a deb of this or show you how. Fairly simple, actually.

---

### Post by Nrvnqsr on 2006-06-13
I apreciate your help, I suspect that Dapper in default is missing some library packages to compile it.

and also making a deb is impossible since its doesn't have the instruction to make it into a deb file, it only makes the binary.

---

### Post by simplyw00x on 2006-06-14
Making a deb does not require make install rules or even a configure script. You can make a deb from just image files. And the whole point of debs is that it handles dependencies and automatically installs the right packages if you don't have them.

---

### Post by Mateo on 2006-07-01
Could I have some help?  I have tried to compile this.  I have libwxgtk2.6-0, libwxgtk2.6-dev, and python-wxgtk2.6.  I have version 0.8 of comical which is newer than the one in this thread.  this is what happens when i run make.

```
matthew@matthew-desktop:~/Desktop/comical-0.8$ make
make -C src
make[1]: Entering directory `/home/matthew/Desktop/comical-0.8/src'
make[1]: Leaving directory `/home/matthew/Desktop/comical-0.8/src'
make[1]: Entering directory `/home/matthew/Desktop/comical-0.8/src'
Converting firstpage.png
Converting prevpage.png
Converting prev.png
Converting next.png
Converting nextpage.png
Converting lastpage.png
Converting rot_cw.png
Converting rot_ccw.png
Converting open.png
Converting fullscreen.png
Converting exit.png
make[1]: Leaving directory `/home/matthew/Desktop/comical-0.8/src'
make[1]: Entering directory `/home/matthew/Desktop/comical-0.8/src'
cc `wx-config --cxxflags` -O2 -Wall -pipe -D_UNIX -I../unrar -I../unzip -c -o ComicalApp.o ComicalApp.cpp
cc `wx-config --cxxflags` -O2 -Wall -pipe -D_UNIX -I../unrar -I../unzip -c -o ComicalBrowser.o ComicalBrowser.cpp
cc `wx-config --cxxflags` -O2 -Wall -pipe -D_UNIX -I../unrar -I../unzip -c -o ComicalCanvas.o ComicalCanvas.cpp
cc `wx-config --cxxflags` -O2 -Wall -pipe -D_UNIX -I../unrar -I../unzip -c -o ComicalFrame.o ComicalFrame.cpp
cc `wx-config --cxxflags` -O2 -Wall -pipe -D_UNIX -I../unrar -I../unzip -c -o ComicalManager.o ComicalManager.cpp
cc `wx-config --cxxflags` -O2 -Wall -pipe -D_UNIX -I../unrar -I../unzip -c -o ComicBook.o ComicBook.cpp
ComicBook.cpp: In member function ‘virtual void* ComicBook::Entry()’:
ComicBook.cpp:540: warning: operation on ‘target’ may be undefined
cc `wx-config --cxxflags` -O2 -Wall -pipe -D_UNIX -I../unrar -I../unzip -c -o ComicBookDir.o ComicBookDir.cpp
cc `wx-config --cxxflags` -O2 -Wall -pipe -D_UNIX -I../unrar -I../unzip -c -o ComicBookRAR.o ComicBookRAR.cpp
make[1]: Leaving directory `/home/matthew/Desktop/comical-0.8/src'
make: *** [src/ComicalApp.o] Error 2

```

if you can help, thanks.

---

### Post by Mateo on 2006-07-01
never mind, i found a .deb and seem to like comix better anyways.

---

### Post by Kilz on 2006-07-15
> **Mateo said:**
> never mind, i found a .deb and seem to like comix better anyways.

If you or anyone else wants Comica. 0.8 [I have .deb's on my site.]("http://www.tghc.org/staticpages/index.php/comicalcbrandcbzreaderforubuntudapper")

---

### Post by mmcmonster on 2006-08-20
I would like to know how to compile this, for future reference.  Every time I build/rebuild a system, this is the one stumbling block. :-(

```

$ sudo apt-get install build-essential libwxgtk2.6-0 libwxgtk2.6-dev python-wxgtk2.6 zlib1g zlib1g-dev

``` 
After the above line, I get the same error at exactly the same place as the other people above.  Can someone please try compiling this on a clean Dapper install and help me figure out what else is needed?  This is starting to bug me. :-(

(I know, there's a .deb available, but now it's a matter of satisfaction...)
```

$ sudo make
make -C src
make[1]: Entering directory `/usr/local/src/comical/comical-0.8/src'
Converting firstpage.png
Converting prevpage.png
Converting prev.png
Converting next.png
Converting nextpage.png
Converting lastpage.png
Converting rot_cw.png
Converting rot_ccw.png
Converting open.png
Converting fullscreen.png
Converting exit.png
make[1]: Leaving directory `/usr/local/src/comical/comical-0.8/src'
make[1]: Entering directory `/usr/local/src/comical/comical-0.8/src'
cc `wx-config --cxxflags` -O2 -Wall -pipe -D_UNIX -I../unrar -I../unzip -c -o ComicalApp.o ComicalApp.cpp
cc `wx-config --cxxflags` -O2 -Wall -pipe -D_UNIX -I../unrar -I../unzip -c -o ComicalBrowser.o ComicalBrowser.cpp
cc `wx-config --cxxflags` -O2 -Wall -pipe -D_UNIX -I../unrar -I../unzip -c -o ComicalCanvas.o ComicalCanvas.cpp
cc `wx-config --cxxflags` -O2 -Wall -pipe -D_UNIX -I../unrar -I../unzip -c -o ComicalFrame.o ComicalFrame.cpp
cc `wx-config --cxxflags` -O2 -Wall -pipe -D_UNIX -I../unrar -I../unzip -c -o ComicalManager.o ComicalManager.cpp
cc `wx-config --cxxflags` -O2 -Wall -pipe -D_UNIX -I../unrar -I../unzip -c -o ComicBook.o ComicBook.cpp
ComicBook.cpp: In member function ‘virtual void* ComicBook::Entry()’:
ComicBook.cpp:540: warning: operation on ‘target’ may be undefined
cc `wx-config --cxxflags` -O2 -Wall -pipe -D_UNIX -I../unrar -I../unzip -c -o ComicBookDir.o ComicBookDir.cpp
cc `wx-config --cxxflags` -O2 -Wall -pipe -D_UNIX -I../unrar -I../unzip -c -o ComicBookRAR.o ComicBookRAR.cpp
make[1]: Leaving directory `/usr/local/src/comical/comical-0.8/src'
make: *** [src/ComicalApp.o] Error 2
$

```

---

### Post by Kilz on 2006-09-06
> **mmcmonster said:**
> I would like to know how to compile this, for future reference.  Every time I build/rebuild a system, this is the one stumbling block. :-(

```

$ sudo apt-get install build-essential libwxgtk2.6-0 libwxgtk2.6-dev python-wxgtk2.6 zlib1g zlib1g-dev

``` 
After the above line, I get the same error at exactly the same place as the other people above.  Can someone please try compiling this on a clean Dapper install and help me figure out what else is needed?  This is starting to bug me. :-(

(I know, there's a .deb available, but now it's a matter of satisfaction...)
```

$ sudo make
make -C src
make[1]: Entering directory `/usr/local/src/comical/comical-0.8/src'
Converting firstpage.png
Converting prevpage.png
Converting prev.png
Converting next.png
Converting nextpage.png
Converting lastpage.png
Converting rot_cw.png
Converting rot_ccw.png
Converting open.png
Converting fullscreen.png
Converting exit.png
make[1]: Leaving directory `/usr/local/src/comical/comical-0.8/src'
make[1]: Entering directory `/usr/local/src/comical/comical-0.8/src'
cc `wx-config --cxxflags` -O2 -Wall -pipe -D_UNIX -I../unrar -I../unzip -c -o ComicalApp.o ComicalApp.cpp
cc `wx-config --cxxflags` -O2 -Wall -pipe -D_UNIX -I../unrar -I../unzip -c -o ComicalBrowser.o ComicalBrowser.cpp
cc `wx-config --cxxflags` -O2 -Wall -pipe -D_UNIX -I../unrar -I../unzip -c -o ComicalCanvas.o ComicalCanvas.cpp
cc `wx-config --cxxflags` -O2 -Wall -pipe -D_UNIX -I../unrar -I../unzip -c -o ComicalFrame.o ComicalFrame.cpp
cc `wx-config --cxxflags` -O2 -Wall -pipe -D_UNIX -I../unrar -I../unzip -c -o ComicalManager.o ComicalManager.cpp
cc `wx-config --cxxflags` -O2 -Wall -pipe -D_UNIX -I../unrar -I../unzip -c -o ComicBook.o ComicBook.cpp
ComicBook.cpp: In member function ‘virtual void* ComicBook::Entry()’:
ComicBook.cpp:540: warning: operation on ‘target’ may be undefined
cc `wx-config --cxxflags` -O2 -Wall -pipe -D_UNIX -I../unrar -I../unzip -c -o ComicBookDir.o ComicBookDir.cpp
cc `wx-config --cxxflags` -O2 -Wall -pipe -D_UNIX -I../unrar -I../unzip -c -o ComicBookRAR.o ComicBookRAR.cpp
make[1]: Leaving directory `/usr/local/src/comical/comical-0.8/src'
make: *** [src/ComicalApp.o] Error 2
$

```

Do you have rar installed?

---

### Post by mmcmonster on 2006-10-23
I am trying this again with Ubuntu 6.10:

```
$ sudo apt-get install build-essential libwxgtk2.6-0 libwxgtk2.6-dev python-wxgtk2.6 zlib1g zlib1g-dev rar unrar zip

```Now it seems that things are worse. :-(

Can anyone try to confirm this and tell me what else I have to install?

```

$ sudo make
make -C src
make[1]: Entering directory `/usr/local/src/comical/comical-0.8/src'
`wx-config --cxx` `wx-config --cxxflags` -O2 -Wall -pipe -D_UNIX -I../unrar -I../unzip -c -o ComicalApp.o ComicalApp.cpp
In file included from ComicalFrame.h:43,
                 from ComicalManager.h:32,
                 from ComicalApp.h:32,
                 from ComicalApp.cpp:28:
firstpage.h:2: error: stray ‘#’ in program
In file included from ComicalFrame.h:44,
                 from ComicalManager.h:32,
                 from ComicalApp.h:32,
                 from ComicalApp.cpp:28:
prevpage.h:2: error: stray ‘#’ in program
In file included from ComicalFrame.h:45,
                 from ComicalManager.h:32,
                 from ComicalApp.h:32,
                 from ComicalApp.cpp:28:
prev.h:2: error: stray ‘#’ in program
In file included from ComicalFrame.h:46,
                 from ComicalManager.h:32,
                 from ComicalApp.h:32,
                 from ComicalApp.cpp:28:
next.h:2: error: stray ‘#’ in program
In file included from ComicalFrame.h:47,
                 from ComicalManager.h:32,
                 from ComicalApp.h:32,
                 from ComicalApp.cpp:28:
nextpage.h:2: error: stray ‘#’ in program
In file included from ComicalFrame.h:48,
                 from ComicalManager.h:32,
                 from ComicalApp.h:32,
                 from ComicalApp.cpp:28:
lastpage.h:2: error: stray ‘#’ in program
In file included from ComicalFrame.h:49,
                 from ComicalManager.h:32,
                 from ComicalApp.h:32,
                 from ComicalApp.cpp:28:
rot_cw.h:2: error: stray ‘#’ in program
In file included from ComicalFrame.h:50,
                 from ComicalManager.h:32,
                 from ComicalApp.h:32,
                 from ComicalApp.cpp:28:
rot_ccw.h:2: error: stray ‘#’ in program
In file included from ComicalFrame.h:51,
                 from ComicalManager.h:32,
                 from ComicalApp.h:32,
                 from ComicalApp.cpp:28:
open.h:2: error: stray ‘#’ in program
In file included from ComicalFrame.h:52,
                 from ComicalManager.h:32,
                 from ComicalApp.h:32,
                 from ComicalApp.cpp:28:
fullscreen.h:2: error: stray ‘#’ in program
In file included from ComicalFrame.h:53,
                 from ComicalManager.h:32,
                 from ComicalApp.h:32,
                 from ComicalApp.cpp:28:
exit.h:2: error: stray ‘#’ in program
/usr/include/wx-2.6/wx/hashmap.h: In member function ‘wxLongToLongHashMap_wxImplementation_HashTable::Node** wxLongToLongHashMap_wxImplementation_HashTable::GetNodePtr(const long int&) const’:
/usr/include/wx-2.6/wx/hashmap.h:705: warning: dereferencing type-punned pointer will break strict-aliasing rules
/usr/include/wx-2.6/wx/clntdata.h: In member function ‘wxShadowObjectMethods_wxImplementation_HashTable::Node** wxShadowObjectMethods_wxImplementation_HashTable::GetNodePtr(const wxString&) const’:
/usr/include/wx-2.6/wx/clntdata.h:26: warning: dereferencing type-punned pointer will break strict-aliasing rules
/usr/include/wx-2.6/wx/clntdata.h: In member function ‘wxShadowObjectFields_wxImplementation_HashTable::Node** wxShadowObjectFields_wxImplementation_HashTable::GetNodePtr(const wxString&) const’:
/usr/include/wx-2.6/wx/clntdata.h:31: warning: dereferencing type-punned pointer will break strict-aliasing rules
/usr/include/wx-2.6/wx/gdicmn.h: In member function ‘wxStringToColourHashMap_wxImplementation_HashTable::Node** wxStringToColourHashMap_wxImplementation_HashTable::GetNodePtr(const wxString&) const’:
/usr/include/wx-2.6/wx/gdicmn.h:476: warning: dereferencing type-punned pointer will break strict-aliasing rules
/usr/include/wx-2.6/wx/image.h: In member function ‘wxImageHistogramBase_wxImplementation_HashTable::Node** wxImageHistogramBase_wxImplementation_HashTable::GetNodePtr(const long unsigned int&) const’:
/usr/include/wx-2.6/wx/image.h:123: warning: dereferencing type-punned pointer will break strict-aliasing rules
firstpage.h: At global scope:
firstpage.h:2: error: expected unqualified-id before ‘-’ token
prevpage.h:2: error: expected unqualified-id before ‘-’ token
prev.h:2: error: expected unqualified-id before ‘-’ token
next.h:2: error: expected unqualified-id before ‘-’ token
nextpage.h:2: error: expected unqualified-id before ‘-’ token
lastpage.h:2: error: expected unqualified-id before ‘-’ token
rot_cw.h:2: error: expected unqualified-id before ‘-’ token
rot_ccw.h:2: error: expected unqualified-id before ‘-’ token
open.h:2: error: expected unqualified-id before ‘-’ token
fullscreen.h:2: error: expected unqualified-id before ‘-’ token
exit.h:2: error: expected unqualified-id before ‘-’ token
make[1]: *** [ComicalApp.o] Error 1
make[1]: Leaving directory `/usr/local/src/comical/comical-0.8/src'
make: *** [src/ComicalApp.o] Error 2
$ 

```

---

### Post by mmcmonster on 2006-11-10
Okay.  I got it to work this time. :-)
On a fresh dapper installation, install the following packages:
```

sudo apt-get install build-essential libwxgtk2.6-0 libwxgtk2.6-dev python-wxgtk2.6 zlib1g zlib1g-dev rar unrar-nonfree zip wx-common wx2.6-headers libwxbase2.6-dev python-wxversion libwxbase2.6-0

```
On my system, it says it will install some extra packages as well.  Allow it to install everything, and then just make comical like you would anything else.

Nothing else was needed (except the comical source, of course) :-)

---

