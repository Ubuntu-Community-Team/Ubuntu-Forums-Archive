---
title: "Add Drag and Drop capabilities to aMSN"
date: 2007-09-27
forum: Outdated Tutorials &amp; Tips
---

### Post by olskar on 2007-09-27
Hi!
Do this to enable Drag and Drop capabilities in aMSN.

You need the tkdnd binaries, you get them from TkDND developers cvs server with this commands:

```
cvs -z3 -d:pserver:anonymous@tkdnd.cvs.sourceforge.net:/cvsroot/tkdnd login
``` (Hit enter, no password neededr)

```
 cvs -z3 -d:pserver:anonymous@tkdnd.cvs.sourceforge.net:/cvsroot/tkdnd co -P tkdnd/lib

```

Then you need to make a tkdnd in the amsn directory using this command:
```
mkdir $AMSNDIR/utils/tkdnd
``` (mine was in /usr/share/amsn)

Finally you need to copy over the files from the cvsserver to the directory you just made using this command:

```
 cp tkdnd/lib/*tcl $AMSNDIR/utils/tkdnd/
```
and
```
 cp tkdnd/lib/Linux/libtkdnd1.0.so $AMSNDIR/utils/tkdnd/
```

Restart aMSN and you can enjoy dragging files to the conversationwindows to send them!

---

### Post by Klargodut on 2007-10-23
Thank You! One of the last pieces I was missing in aMsn!

---

### Post by VON_CAPO on 2007-10-23
Thanks. :)

---

### Post by kr0n1x on 2007-10-29
it doesn't work on my Gutsy 64 bit...
any idea?

---

### Post by hobbes_ba on 2007-10-30
> **kr0n1x said:**
> it doesn't work on my Gutsy 64 bit...
any idea?

I can also confirm that 

Do not work on Gutsy 64 bit!

Anyone?

---

### Post by Scimu on 2007-11-01
Thanks a lot for this. I was missing this feature.. Works on Gutsy 32bit!

---

### Post by adam0509 on 2007-11-01
Work for me !!!

thank you so much !!!


added to french wiki : [http://doc.ubuntu-fr.org/amsn#fonction_drag_n_drop](http://doc.ubuntu-fr.org/amsn#fonction_drag_n_drop)

---

### Post by kr0n1x on 2007-11-01
nobody was able to do it working in 64 bit version? :confused:

---

### Post by CyberAngel on 2007-12-02
Also doesn`t work on 64bit gutsy :(

Have you found anything?

---

### Post by CyberAngel on 2007-12-02
Fixed that but I had to compile tkdnd on my own :)

---

### Post by kr0n1x on 2007-12-02
> **CyberAngel said:**
> Fixed that but I had to compile tkdnd on my own :)

where you got sources? i'll try to compile it too, thanks

---

### Post by CyberAngel on 2007-12-02
> **kr0n1x said:**
> where you got sources? i'll try to compile it too, thanks

I posted a how to for the hole installation of amsn from svn with tcl/tk 8.5 and tkdnd but it is pending moderation approval.

I am pasting the same post here until it will be approved (if approved anyway :) )

> Hello!
I know that many similar threads exists (also a script to do automatically all of the following exists), but because I was trying to compile aMSN today and I found myself in front of many errors that finally solved, I decided to sum up everything on this thread.

All of the following has been tested on a kubuntu amd64 installation!
Yes, and the drag n drop support is here! 

Just copy paste the commands in order, and finally you should have a working aMSN installation as the thread title describes :)

Let`s start..

First of all download all the dependencies..

```
sudo apt-get install build-essential libx11-dev libc6-dev imagemagick libjpeg-dev libpng12-dev tcltls libxft-dev msttcorefonts checkinstall subversion cvs libssl-dev openssl xorg-dev

sudo apt-get build-dep amsn tcl8.4 tk8.4

```

Then download and compile tcl/tk/tkdnd from the cvs repositories..
```

mkdir ~/Desktop/amsn
mkdir ~/Desktop/amsn/tcltk8.5

cd ~/Desktop/amsn/tcltk8.5
cvs -d:pserver:anonymous@tcl.cvs.sourceforge.net:/cvsroot/tcl login
```

When it will ask for a password just press enter

```
cvs -z3 -d:pserver:anonymous@tcl.cvs.sourceforge.net:/cvsroot/tcl co -P tcl

cvs -d:pserver:anonymous@tktoolkit.cvs.sourceforge.net:/cvsroot/tktoolkit login
```

Again the password is nothing. Just hit enter.

```
cvs -z3 -d:pserver:anonymous@tktoolkit.cvs.sourceforge.net:/cvsroot/tktoolkit co -P tk

cvs -z3 -d:pserver:anonymous@tkdnd.cvs.sourceforge.net:/cvsroot/tkdnd login
```

Just hit enter for the password.

```
cvs -z3 -d:pserver:anonymous@tkdnd.cvs.sourceforge.net:/cvsroot/tkdnd co -P tkdnd

cd tcl/unix

./configure --prefix=/usr/local --includedir=/usr/local/include/tcl8.5 --enable-shared --enable-threads --enable-64bit \
  --mandir=/usr/local/share/man --enable-man-symlinks --enable-man-compression=gzip && make CFLAGS="-g -O2 -D_REENTRANT"

sudo make install


cd ../../tk/unix

./configure --prefix=/usr/local --includedir=/usr/local/include/tcl8.5 --with-tcl=/usr/local/lib --enable-shared --enable-threads \
  --enable-64bit --enable-man-symlinks --enable-man-compression=gzip --enable-xft && make CFLAGS="-g -O2 -D_REENTRANT"

sudo make install


cd ../../tkdnd

./configure  --prefix=/usr/local --includedir=/usr/local/include/tcl8.5 --with-tcl=/usr/local/lib --with-tk=/usr/local/lib --enable-threads \
&& make CFLAGS="-g -O2 -D_REENTRANT"

sudo make install
```

!!!!!!!!!!!NOTE FROM aMSN wiki!!!!!!!!!!!
Note: this way you're enabling threads. This may cause hangs under kernel of the 2.6 series. If you experience such a problem, please recompile Tcl/Tk without threads (just remove --enable-threads from the command line).


Now we have to download and compile amsn from the svn repository..
```

cd ~/Desktop/amsn

svn co https://amsn.svn.sourceforge.net/svnroot/amsn/trunk/amsn amsn

cd amsn

./configure --with-tcl=/usr/local/lib --with-tk=/usr/local/lib

make

sudo make install

```

Now just change the amsn startup script to use tcl8.5 and not 8.4!
```
kdesu kate /usr/share/amsn/amsn
```
or
```
gksudo gedit /usr/share/amsn/amsn
```

depending the ubuntu flavor that you have (Ubuntu/Kubuntu)

and change the third line from: ```
exec wish $0 $@
```
to: ```
exec wish8.5 $0 $@
```


The following two are because of two problems I encountered when starting amsn...
```
sudo cp -r ~/Desktop/amsn/tcltk8.5/tcl/library/msgcat /usr/local/lib/
```

Now start once your amsn and close again (this is just for amsn to create the ~/.amsn dir)

```
cd ~/.amsn/plugins

ln -s /usr/lib/tls1.50 .
```

That`s it!
Finished :)

---

### Post by kr0n1x on 2007-12-02
but i'm not interested to new version of tcl/tk :( i think them aren't stable.
anyway i found sources (i hope it is XD):
[http://sourceforge.net/project/showfiles.php?group_id=13167&package_id=21487&release_id=412413](http://sourceforge.net/project/showfiles.php?group_id=13167&package_id=21487&release_id=412413)

edit: i don't know how to use them .-. i "cd" to *unix* folder but "make" give me some errors...

---

### Post by CyberAngel on 2007-12-02
> **kr0n1x said:**
> but i'm not interested to new version of tcl/tk :( i think them aren't stable.
anyway i found sources (i hope it is XD):
[http://sourceforge.net/project/showfiles.php?group_id=13167&package_id=21487&release_id=412413](http://sourceforge.net/project/showfiles.php?group_id=13167&package_id=21487&release_id=412413)

edit: i don't know how to use them .-. i "cd" to *unix* folder but "make" give me some errors...

I am using amsn and tcl/tk from svn/cvs for a year now, and I am not encountering any problems :)
I think it is very stable.

So I would recommend to you just a try ;)
It looks much more better with the font antialiasing.

Especially to the Greek characters I am using (and I think also for other non latin characters) that I can`t even read/write them with tcl/tk 8.4!

---

### Post by CyberAngel on 2007-12-02
you don`t need to "cd" to the unix folder.
You need to run make on the general folder (the one that also contains unix)

---

### Post by kr0n1x on 2007-12-02
> **CyberAngel said:**
> you don`t need to "cd" to the unix folder.
You need to run make on the general folder (the one that also contains unix)

```
make: *** No targets specified and no makefile found.  Stop.
```

anyway i had (in past) some problems like 100% cpu sucking by amsn :( then for now i prefer to stay in the stable version.

what's wrong with my "make"? :( i tried it in "general" folder.

---

### Post by CyberAngel on 2007-12-02
First of all you need some dependencies so first run the following:

```
sudo apt-get install libx11-dev
```

then

```
./configure && make && sudo make install
```

---

### Post by kr0n1x on 2007-12-02
> **CyberAngel said:**
> First of all you need some dependencies so first run the following:

```
sudo apt-get install libx11-dev
```

then

```
./configure && make && sudo make install
```

have you looked the sources archive? there isn't a configure script... i'm talking about the archive that you can download byt this link:
[http://sourceforge.net/project/showfiles.php?group_id=13167&package_id=21487&release_id=412413](http://sourceforge.net/project/showfiles.php?group_id=13167&package_id=21487&release_id=412413)

---

### Post by CyberAngel on 2007-12-02
> **kr0n1x said:**
> have you looked the sources archive? there isn't a configure script... i'm talking about the archive that you can download byt this link:
[http://sourceforge.net/project/showfiles.php?group_id=13167&package_id=21487&release_id=412413](http://sourceforge.net/project/showfiles.php?group_id=13167&package_id=21487&release_id=412413)

yeap...

You are right...

I just did this also from the cvs repository...

Just try the same too..

```
cvs -z3 -d:pserver:anonymous@tkdnd.cvs.sourceforge.net:/cvsroot/tkdnd login

```
Just hit enter for the password.
```

cvs -z3 -d:pserver:anonymous@tkdnd.cvs.sourceforge.net:/cvsroot/tkdnd co -P tkdnd
```

then 

```
cd tkdnd
```

and run the configure and make

---

### Post by kr0n1x on 2007-12-02
```
pasquale@pasquale-desktop:~/tkdnd$ ./configure
checking for correct TEA configuration... ok
checking for Tcl configuration... configure: WARNING: "Cannot find Tcl configuration definitions"
pasquale@pasquale-desktop:~/tkdnd$ 

```

O_o

can you help me?

---

### Post by CyberAngel on 2007-12-02
I think that you also need the tcl/tk dev.....

I ran the configure like this:

```
./configure  --prefix=/usr/local --includedir=/usr/local/include/tcl8.5 --with-tcl=/usr/local/lib --with-tk=/usr/local/lib
```

But first I installed tcl/tk from source to the above folders...

So what I suggest is to try download the dev packages of tcl/tk and find where they are installed to set the --includedir and --with-tcl, --with-tk parameters..

---

### Post by kr0n1x on 2007-12-02
for dependencies:
```
sudo apt-get build-dep amsn
```

then i do:
```
pasquale@pasquale-desktop:~/tkdnd$ ./configure --prefix=/usr --includedir=/usr/include/tcl8.4 --with-tcl=/usr/lib/tcl8.4 --with-tk=/usr/lib/tk8.4
checking for correct TEA configuration... ok
checking for Tcl configuration... found /usr/lib/tcl8.4/tclConfig.sh
checking for existence of /usr/lib/tcl8.4/tclConfig.sh... loading
checking for Tk configuration... found /usr/lib/tk8.4/tkConfig.sh
checking for existence of /usr/lib/tk8.4/tkConfig.sh... loading
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... yes
checking for ranlib... ranlib
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking if the compiler understands -pipe... yes
checking for required early compiler flags...  _LARGEFILE64_SOURCE
checking for 64-bit integer type... using long
checking whether byte ordering is bigendian... no
checking for sin... no
checking for main in -lieee... yes
checking for main in -linet... no
checking net/errno.h usability... no
checking net/errno.h presence... no
checking for net/errno.h... no
checking for connect... yes
checking for gethostbyname... yes
checking dirent.h... yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking float.h usability... yes
checking float.h presence... yes
checking for float.h... yes
checking values.h usability... yes
checking values.h presence... yes
checking for values.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/wait.h usability... yes
checking sys/wait.h presence... yes
checking for sys/wait.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for unistd.h... (cached) yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking for Tcl public headers... /usr/include/tcl8.4
checking for Tk public headers... /usr/include/tcl8.4
checking for X... libraries , headers 
checking for X11 header files... checking for building with threads... no (default)
configure: WARNING:
    Building tkdnd without threads enabled, but building against a Tcl
    that IS thread-enabled.
checking how to build libraries... shared
checking if 64bit support is enabled... no
checking if 64bit Sparc VIS support is requested... no
checking system version (for dynamic loading)... Linux-2.6.22-14-generic
checking for dlopen in -ldl... yes
checking for ar... ar
checking for build with symbols... no
checking for tclsh... /usr/bin/tclsh8.4
checking for wish... /usr/bin/wish8.4
configure: creating ./config.status
config.status: creating Makefile
pasquale@pasquale-desktop:~/tkdnd$
```
can you check the WARNING voice? if is important or not...
thanks

---

### Post by kr0n1x on 2007-12-02
anyway "make" results was good!
```
*** tkdnd built successfully ***
```

---

### Post by CyberAngel on 2007-12-02
is it working now???

To get rid of this WARNING just use the ./configure with --enable-threads ;)

---

### Post by kr0n1x on 2007-12-02
> **CyberAngel said:**
> is it working now???

To get rid of this WARNING just use the ./configure with --enable-threads ;)

yes now works.

what is "threads" function? i need to recompile?

---

### Post by CyberAngel on 2007-12-02
> **kr0n1x said:**
> yes now works.

what is "threads" function? i need to recompile?

First of all I`m glad that it works :D

And second, if you need the thread support (Also your tcl/tk is compiled with the threads options.. That`s why you had that warning) of course you need to recompile it with this option.

Read more about threads here :
[http://en.wikipedia.org/wiki/Thread_%28computer_science%29](http://en.wikipedia.org/wiki/Thread_%28computer_science%29)

---

### Post by kr0n1x on 2007-12-02
> **CyberAngel said:**
> First of all I`m glad that it works :D

And second, if you need the thread support (Also your tcl/tk is compiled with the threads options.. That`s why you had that warning) of course you need to recompile it with this option.

Read more about threads here :
[http://en.wikipedia.org/wiki/Thread_%28computer_science%29](http://en.wikipedia.org/wiki/Thread_%28computer_science%29)

then i need to do "make" and "sudo checkinstall" again?

thanks for support, bye! (i use checkinstall, not make install)

---

### Post by CyberAngel on 2007-12-02
> **kr0n1x said:**
> then i need to do "make" and "sudo checkinstall" again?

thanks for support, bye! (i use checkinstall, not make install)

You`re welcome!

I use checkinstall too to be able to keep track of my installed software ;)

---

### Post by kr0n1x on 2007-12-02
ok i recompiled it and works! good luck with the how-to! bye

---

### Post by eyemean on 2007-12-29
Hi, im new to ubuntu, so sorry for the question, but should i of uninstalled amsn 0.97 first, because i cant really see much of a difference apart from the larger characters, lol.

Thank you in advance.

---

### Post by lordmess on 2011-03-09
> **olskar said:**
> Hi!
Do this to enable Drag and Drop capabilities in aMSN.

You need the tkdnd binaries, you get them from TkDND developers cvs server with this commands:

```
cvs -z3 -d:pserver:anonymous@tkdnd.cvs.sourceforge.net:/cvsroot/tkdnd login
``` (Hit enter, no password neededr)

```
 cvs -z3 -d:pserver:anonymous@tkdnd.cvs.sourceforge.net:/cvsroot/tkdnd co -P tkdnd/lib

```Then you need to make a tkdnd in the amsn directory using this command:
```
mkdir $AMSNDIR/utils/tkdnd
``` (mine was in /usr/share/amsn)

Finally you need to copy over the files from the cvsserver to the directory you just made using this command:

```
 cp tkdnd/lib/*tcl $AMSNDIR/utils/tkdnd/
```and
```
 cp tkdnd/lib/Linux/libtkdnd1.0.so $AMSNDIR/utils/tkdnd/
```Restart aMSN and you can enjoy dragging files to the conversationwindows to send them!





When I enter the mkdir command this message shows up

mkdir: cannot create directory `/usr/share/amsn/utils/tkdnd': Permission denied

I entered the code like this mkdir /usr/share/amsn/utils/tkdnd

Have I done something wrong?

---

### Post by kr0n1x on 2011-03-09
> **lordmess said:**
> When I enter the mkdir command this message shows up

mkdir: cannot create directory `/usr/share/amsn/utils/tkdnd': Permission denied

I entered the code like this mkdir /usr/share/amsn/utils/tkdnd

Have I done something wrong?

You're trying to make a new folder in a directory which needs administration privileges.

Add *sudo* before the command.
```
sudo mkdir /usr/share/amsn/utils/tkdnd
```
Pay attention when you work in important directories like */usr*

---

### Post by lordmess on 2011-03-09
> **kr0n1x said:**
> You're trying to make a new folder in a directory which needs administration privileges.

Add *sudo* before the command.
```
sudo mkdir /usr/share/amsn/utils/tkdnd
```Pay attention when you work in important directories like */usr*



I did everything you said I added sudo in the start of the command all filles where transfered. I checked them but I still cant drag and drop files on amsn. sorry to bother you I am a new user. Its the first time I work under linux.

---

### Post by kr0n1x on 2011-03-09
> **lordmess said:**
> I did everything you said I added sudo in the start of the command all filles where transfered. I checked them but I still cant drag and drop files on amsn. sorry to bother you I am a new user. Its the first time I work under linux.

Just to be sure that you've done the command correctly, try:
```
ls /usr/share/amsn/utils/tkdnd
```
and check that you've got all the needed files.

Restart aMSN and check if it works.

If it still doesn't work, maybe you can try tkdnd 2.2:
[http://sourceforge.net/projects/tkdnd/](http://sourceforge.net/projects/tkdnd/)

I haven't tried it and I don't even have an Ubuntu installation at the moment, so I can't help you better.

Try finding a solution in aMSN forum, probably also other people had your problem.

---

### Post by lordmess on 2011-03-09
> **kr0n1x said:**
> Just to be sure that you've done the command correctly, try:
```
ls /usr/share/amsn/utils/tkdnd
```and check that you've got all the needed files.

Restart aMSN and check if it works.

If it still doesn't work, maybe you can try tkdnd 2.2:
[http://sourceforge.net/projects/tkdnd/](http://sourceforge.net/projects/tkdnd/)

I haven't tried it and I don't even have an Ubuntu installation at the moment, so I can't help you better.

Try finding a solution in aMSN forum, probably also other people had your problem.
 

well the new tkdnd.tlc didnt work. 

Thanks you for your help anyway. the only solution I found is installing an other version of amsn from amsn forums.

---

