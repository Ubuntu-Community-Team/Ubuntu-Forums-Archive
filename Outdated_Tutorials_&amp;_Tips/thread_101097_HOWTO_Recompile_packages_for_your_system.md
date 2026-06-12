---
title: "HOWTO: Recompile packages for your system"
date: 2005-12-09
forum: Outdated Tutorials &amp; Tips
---

### Post by GoldBuggie on 2005-12-09
This howto is for ppl who want to recompile ubuntu packages and keep the ubuntu settings(so that it is more stable) PLUS add some of your own compiling flags(maybe for your cpu type).

Make sure you have the *deb-src* lines uncommented in */etc/sources.list*.

Make a directory where you will do your work. This way you can easily see what has been downloaded and easy remove it later.
```
mkdir recompileUbuntuPackages
cd recompileUbuntuPackages
```[LIST=1]
[*][SIZE=3][COLOR=Indigo]Download needed header-files etc for **<package-name>**[/COLOR][/SIZE]
```
sudo apt-get build-dep <package-name>
```
[*][SIZE=3][COLOR=Indigo]Add your own compiling flags[/COLOR][/SIZE]
This is the only thing that will change the build. If you do not have this step you will build an exact duplicate of the original package.
You can pass flags(options) to the compiler using CXXFLAGS and CFLAGS. For which options you can add have a look at [http://gcc.gnu.org/onlinedocs/gcc-4.0.2/gcc/i386-and-x86_002d64-Options.html#i386-and-x86_002d64-Options]("http://gcc.gnu.org/onlinedocs/gcc-4.0.2/gcc/i386-and-x86_002d64-Options.html#i386-and-x86_002d64-Options")
    
Add these flags to your environment file.
```
sudo kate /etc/environment
```
and add for example*(note that this is a pentium3; change for your own cpu type.) *
```
CFLAGS="-O2 -march=pentium3 -funroll-loops -ffast-math -fomit-frame-pointer -fno-exceptions"
CXXFLAGS="-O2 -march=pentium3 -funroll-loops -ffast-math -fomit-frame-pointer -fno-exceptions"
```
Restart computer to get the variables into the system or do an *export CFLAGS CXXFLAGS* after you have typed the above into konsole.
[*][SIZE=3][COLOR=Indigo]Download **<package-name>** and compile it to a deb-package[/COLOR][/SIZE]
```
sudo apt-get -b source **<package-name>**
```
[COLOR=Purple] 3.1[/COLOR] [COLOR=Purple]Download & Compile with a seperate command[/COLOR]
If you want to download the source and do a compile after maybe twinkling with some files do the above but **remove** the *-b* option then to compile and build a .deb```
sudo dpkg-buildpackage -rfakeroot -uc -b
```
[*][SIZE=3][COLOR=Indigo]Install
    [/COLOR][/SIZE]```
sudo dpkg -i *.deb
```[/LIST]The **<package-name>** will have everything similar to the original except the change when compiling. So after you have installed the package you will still be able to see when new packages have arrived from ubuntu. In fact since you have changed the original package and installed it you will see them as available for update. But if you check the version you will see that they are the same. 

[SIZE=3][COLOR=Indigo]How to revert back to the original **<package-name>**[/COLOR][/SIZE]
```
sudo apt-get install --reinstall <package-name>
``` 
[SIZE=3][COLOR=DarkSlateGray]Packages that might improve your system[/COLOR][/SIZE][INDENT]**[COLOR=Blue]KDE[/COLOR]**
kdebase
kdelibs
libqt3-mt*(These libraries use qmake which uses QMAKE_CFLAGS. Please use option 3.1 and then add your build options to ./qt-x11-free-3.3.4/mkspecs/linux-g++**/qmake.conf)*
  
  **[COLOR=Olive]Gnome[/COLOR]**
(Don't know sorry; Anyone know which the important base packages are?)

[/INDENT][SIZE=3][COLOR=Indigo]**Problems**[/COLOR][/SIZE]**[SIZE=3][COLOR=Indigo] with this method[/COLOR][/SIZE]**
The above howto will not work on all packages since it depends on how they were packaged. If the package doesn't take the systems CFLAGS into account the it won't change a thing. Also packages using qmake won't work.
To provide you with a solution to the first problem I will give you this script which I myself use. It solves the above problem by scanning the directoy and replacing occurances of -O2 with $CFLAG (not pretty but it works).
```
 #!/bin/bash
if [ -n "$1" ]
then
    echo ":: fetching necessary packages for build"
    apt-get build-dep "$@"
    echo ":: fetching source"
    apt-get source "$@"
fi

ourflags=$CFLAGS
echo :: using $ourflags
for directory in `ls -Al | awk '/^d/ {print $8}'`;
do
    echo :: entering directory $directory ...
    cd $directory
    sed -e 's/-O2/'"${ourflags}"'/g' -i `ls -Al | awk '/^-/ {print $8}'`
    cd debian
    sed -e 's/-O2/'"${ourflags}"'/g' -i `ls -Al | awk '/^-/ {print $8}'`
    cd ..
    dpkg-buildpackage -rfakeroot -uc -b
    echo :: leaving directory $directory ...
    cd ..
done 
``` Copy the script to a file; I named mine *recompile*.

Make it executable. ```
sudo chmod +x ./recompile
``` 
 Use it as either **sudo ./recompile <package(s)>**. This will fetch dependencies and source before building. You can also use if for more then one package which is nice.
 Or just do a **sudo ./recompile**. This will assume you already have the source and it will only build.
 
 **Note**...use this within a new directory otherwise it will span thrue your other directories and files.
 


Please note that this is not a discussion about if or not other packages should be available. This is for those who like to have fun with their computer and change it to their own taste. This provides a safe way to do that since reverting back is so easy.

---

### Post by funkyou on 2005-12-12
Hello, nice howto but...

ich have done it as described, but when iam compiling
a package, it does not use my specified cflags at all...

look here:

g++ -c -pipe -I/usr/include/mysql -I/usr/include/freetype2 -I/usr/include/postgresql -I/usr/include/postgresql/8.0 -fno-exceptions -Wall -W -g -D_REENTRANT -fPIC -DQT_SHARED -DQT_TABLET_SUPPORT -DQT_THREAD_SUPPORT -DQT_THREAD_SUPPORT -D_LARGEFILE_SOURCE -D_LARGE_FILES -D_FILE_OFFSET_BITS=64 -DQT_NAS_SUPPORT -DQT_DLOPEN_OPENGL -DQT_NO_IMAGEIO_MNG -DQT_BUILTIN_GIF_READER=1 -DQT_NO_STYLE_MAC -DQT_NO_STYLE_AQUA -DQT_NO_STYLE_CDE -DQT_NO_STYLE_MOTIFPLUS -DQT_NO_STYLE_INTERLACE -DQT_NO_STYLE_PLATINUM -DQT_NO_STYLE_WINDOWSXP -DQT_NO_STYLE_SGI -DQT_NO_STYLE_COMPACT -DQT_NO_STYLE_POCKETPC -DQT_NO_STYLE_WINDOWS -DQT_NO_STYLE_MOTIF -I/home/jan/Work/qt-x11-free-3.3.4/mkspecs/linux-g++ -I. -I/usr/include/freetype2 -I3rdparty/opentype -I../include -I/usr/X11R6/include -I.moc/debug-shared-mt/ -o .obj/debug-shared-mt/qbitmap.o kernel/qbitmap.cpp

...but my flags are: 
CFLAGS="-march=athlon-xp -O2 -fomit-frame-pointer -pipe -fvisibility-inlines-hidden"
CXXFLAGS="-march=athlon-xp -O2 -fomit-frame-pointer -pipe -fvisibility-inlines-hidden"

so, what can i do?

---

### Post by tseliot on 2005-12-12
XXFLAGS and CFLAGS? They remind me of my previous Gentoo installation. I didn't know it could be done in Ubuntu. 
Thanks for the guide

---

### Post by Rob2687 on 2005-12-12
Nice guide

---

### Post by GoldBuggie on 2005-12-12
*Updated the howto to include a 3.1* section which first downloads the package then you can look at the files etc maybe change something then start the compile and build of .deb.
[B]

funkyou[/B]
Well I've not come across a package that does not include those options. Would be wrong if they aren't included I think. Anyhow...the flag options should be in the configure file. Do a
```
cat ./configure | grep FLAGS
```
If they are there then you please look if you have exported your variables correctly. Just type **echo $CFLAGS** to do so.

Which package are you building...maybe I can take a look.

Must run now..I'm almost late for a appointment.

---

### Post by funkyou on 2005-12-12
Hello,

at first, thank you for your help and support, its very appreciated.


I tried to rebuild libqt3-mt and libqt3-mt-dev.

this are my cflags and cxxflags:
[B]jan@agentj:~$ echo $CFLAGS
-mtune=athlon-xp -O2 -fomit-frame-pointer -pipe -fvisibility-inlines-hidden
jan@agentj:~$ echo $CXXFLAGS
-mtune=athlon-xp -O2 -fomit-frame-pointer -pipe -fvisibility-inlines-hidden
jan@agentj:~$[/B]


The first way (before your section 3.1) does not work on my machine, as
gcc does not use my flags. So i tried it the other way, first downloading
the sources with apt, and then modifying the whole thing.

Well, when i search through the configure script, i find many build options
with the name cflags... so i tried something different... i looked through the
qt-source-folder and found this file

[B]~/Work/qt-x11-free-3.3.4/mkspecs/linux-g++/qmake.conf
[/B]
in which one can place the flags for the compiler on linux/gcc...
i have modified the following line to:

[B]QMAKE_CFLAGS = -mtune=athlon-xp -O2 -fomit-frame-pointer -pipe -fvisibility-inlines-hidden
[/B]

I think this should work, but when i try to use the command from section
3.1 of your howto, i get this error message:

[B]jan@agentj:~/Work$ sudo dpkg-buildpackage -rfakeroot -uc -b
Password:
dpkg-parsechangelog: error: cannot open debian/changelog to find format: Datei oder Verzeichnis nicht gefunden
dpkg-buildpackage: unable to determine source package is[/B]

I tried this in both my work-folder and in the qt-folder itself, but its not working.
it claims to not find the debian changelog...

---

### Post by GoldBuggie on 2005-12-12
the **sudo dpkg-buildpackage -rfakeroot -uc -b **command should be run in the same folder as you did the apt-get source. Have you installed fakeroot? sudo apt-get install fakeroot. As for not recoqnizing the cflags option that is just strange to my ears. I even compiled the libqt3-mt package and it worked as a charm. hmmmm...*must think*

but doing it the search important files and chang is also an option. But it can just be to much sometimes so using the flags option is an easy way out.

---

### Post by GoldBuggie on 2005-12-13
Ok added a line about QMAKE_C(XX)FLAGS in the KDE section but I haven't made any tests yet. Will do tomorrow!

But thanks funkyou for pointing it out. I looked thrue the package and noticed that some things are compiled using regular made makefiles and those include CFLAGS etc but since trolltech wants to make things their way(using qmake instead of make) you will have to use the above or change qmake.conf.

---

### Post by funkyou on 2005-12-14
Tried it again, but no succes...

Didn't had the fakeroot package installed, but when i now try to
invoke the **sudo dpkg-buildpackage -rfakeroot -uc -b** command
at the work-folder (where i downloaded the packages), it gives
me the same error message as posted below:

[B]jan@agentj:~/Work$ sudo dpkg-buildpackage -rfakeroot -uc -b
Password:
dpkg-parsechangelog: error: cannot open debian/changelog to find format: Datei oder Verzeichnis nicht gefunden
dpkg-buildpackage: unable to determine source package is[/B]

---

### Post by GoldBuggie on 2005-12-14
I think you are missing some package. Don't know which it is but I have the following installed
[SIZE=1]ii  automake1.4 1.4-p6-9   A tool for generating GNU Standards-complian
ii  automake1.6   1.6.3-12  A tool for generating GNU Standards-complian
ii  automake1.7   1.7.9-7       A tool for generating GNU Standards-complian
ii  automake1.8     1.8.5-3      A tool for generating GNU Standards-complian
ii  automake1.9        1.9.5-1       A tool for generating GNU Standards-complian
ii  dpkg   1.13.10ubuntu4    Package maintenance system for Debian
ii  dpkg-dev        1.13.10ubuntu4     Package building tools for Debian
ii  make   3.80-9    The GNU version of the "make" utility[/SIZE]

I think it might have something to do with automake.

---

### Post by hornett on 2005-12-19
Firstly, thanks for this excellent howto!

Does anybody know how to stop the package manager trying to use the official versions in favour of the recompiled ones? 

I'm using the 3 rather than 3.1 method, and even pinning my recompiled packages doesn't help.

Cheers

---

### Post by GoldBuggie on 2005-12-19
> Firstly, thanks for this excellent howto!Thank you very much. Makes me happy that some find it useful. I would like to expand the howto to be more complete since the flags won't get used on some specific packages. But it might be to much I think. Better to give ppl the bigger idea. The rest is something they can find out maybe.

>  Does anybody know how to stop the package manager trying to use the official versions in favour of the recompiled ones
I'm sorry but I don't seem to understand your question. Use which version of what? Please explain in some further detail

---

### Post by GoldBuggie on 2005-12-19
Aaaah wait I'm way to slow today...must be becaus I'm listening to some ambiant music. It messes with your mind a tell ya.

Well..the recompiled version should be the one that is in use. The older package should be upgraded to your version.

How do you know it is the old package? They way to know that it is the new package is to look what updates you can download. Do a ```
sudo apt-get update
``` Then look which packages you can update. The one you replaces should show up. They have the same number version but it is the new one that is used.

After going thrue step 3 you install it thrue sudo dpkg -i <package name>. You didn't forget that did you?

*edit*
Which package you trying to recompile?

---

### Post by ow50 on 2005-12-19
[QUOTE=hornett]Does anybody know how to stop the package manager trying to use the official versions in favour of the recompiled ones?[/QUOTE]
When recompiling you could add something to the version number, e.g. ".1" or "bob1" if your name is Bob.

That way the replacing order by the package manager would be
0.1.0-0ubuntu1 (breezy version)
0.1.0-0ubuntu1bob1 (your first recompiled version)
0.1.0-0ubuntu1bob2 (your second recompiled version)
0.1.0-0ubuntu2 (breezy security update)
0.1.0-0ubuntu2bob1 (your first recompile after security update)
...

This way you would revert back to the official version with
```
sudo apt-get install <package name>/breezy
```

---

### Post by hornett on 2005-12-19
Thanks for all your help.

I think what I want is something like ow50 suggested. I have definitely installed the packages as I compiled them on another machine, and used dpkg over my samba mount. 

What I'd really like is to be able to add that extra string to the package version, but from within or by adding a command before the **sudo apt-get -b source** command.

Again, any help much appreciated! :D

---

### Post by ow50 on 2005-12-19
[QUOTE=hornett]What I'd really like is to be able to add that extra string to the package version, but from within or by adding a command before the **sudo apt-get -b source** command.[/QUOTE]
To change the version number you need to edit the topmost entry in the file debian/changelog in the source directory after dowloading the source with "apt-get source".

To automate that install package "devscripts" and use command "debchange". For example
```
debchange --nmu --preserve --distribution breezy "Recompiled with optimizations."
```
would add a new changelog entry with ".1" appended to the version number.

---

### Post by One Quick Question on 2005-12-20
EDIT:  Sorry, this post is a complete lie.  Turns out I didn't bother to add *deb-src [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main* in my sources.list

---

### Post by One Quick Question on 2005-12-20
The *sudo dpkg-buildpackage -rfakeroot -uc -b* command has to be done within the subdirectory that contains all the source stuff, **not** the directory where *sudo apt-get source <package name>* was issued.  Or at least that's what works for me.

---

### Post by One Quick Question on 2005-12-20
[QUOTE=ow50]To change the version number you need to edit the topmost entry in the file debian/changelog in the source directory after dowloading the source with "apt-get source".[/QUOTE]Whoa, when you do this, make sure it's in the EXACT format as the other changelog entries or the compiler gets really confused.
for example,
[i]qt-x11-free (3:3.3.4-8ubuntu_OQQ) breezy; urgency=low
[blank line]
  * Compiled with optimizations
[blank line]
 -- OQQ <me>  Tue, 20 Dec 2005 02:00:00 +0500
[TWO spaces between <me> and the required date...][/i]
Kind of crazy!

---

### Post by One Quick Question on 2005-12-20
I think I have the same problem as funkyou but with kdelibs.
```
if test ""; then cd ""; else cd "obj-i486-linux-gnu"; fi && CC="cc"
 CXX="g++" CFLAGS="-g -Wall -O2 -DDEBIAN_VERSION=4:3.5.0-0ubuntu0breezy1"
 CXXFLAGS="-g -Wall -O2 -DDEBIAN_VERSION=4:3.5.0-0ubuntu0breezy1"
[etc...; and I added my own carriage returns for readability]
``` 
but
```
$ echo $CFLAGS
-O2 -march=pentium4 -pipe
$ echo $CXXFLAGS
-O2 -march=pentium4 -pipe
```

even though
```
$ cat ./configure | grep cflags
      LIBART_CFLAGS="`$LIBART_CONFIG --cflags`"
kde_save_cflags="$CFLAGS"
CFLAGS="$kde_save_cflags"
kde_save_cflags="$CFLAGS"
CFLAGS="$kde_save_cflags" [etc...]
```

The INSTALL file doesn't say anything useful even though there are words under the "Compilers and Options" section.

This is so confusing...

---

### Post by One Quick Question on 2005-12-20
Yet another thing...  should I be concerned when the output of the qtlib3-mt build says *dpkg-buildpackage: host architecture i386* when in fact I have a i686?

---

### Post by GoldBuggie on 2005-12-20
nope

We are changing how things are compiled but not named. So that you use the -march= or -mtune= option is the thing that matters . It should show up when the compiler starts building; g++ ... -O2 -march= ... etc.

---

### Post by GoldBuggie on 2005-12-20
> I think I have the same problem as funkyou but with kdelibs. 
Ok...i will be adding this weekend some new info to the how to since i see that it is necessary. been recompiling things for 2 weeks now. mainly to learn to see what difference different packages & settings make. But there are 2 exceptions to the howto. one is with qmake. One must change the qmake.conf file. The other is when the CFLAG option is written not to include your CFLAG(which makes no sense to me). Many(probably all) libx* packages are written in this way. I wrote a little script which takes care of this so that things become more automated. You qill basically only have to use that script then. 

I'll add that script to the howto in the weekend(want to make sure it looks nice first).


Then after that the only thing,that I know of, that won't work without manually tinkering is qmake.

---

### Post by GoldBuggie on 2005-12-20
Ok i'll add the script i use for here so long...need to write some things before adding it to the 1st page...still not sure if i should do it or not thou.

```
#!/bin/bash
if [ -n "$1" ]
then
    echo ":: fetching necessary packages for build"
    apt-get build-dep "$@"
    echo ":: fetching source"
    apt-get source "$@"
fi

ourflags=$CFLAGS
echo :: using $ourflags
for directory in `ls -Al | awk '/^d/ {print $8}'`;
do
    echo :: entering directory $directory ...
    cd $directory
    sed -e 's/-O2/'"${ourflags}"'/g' -i `ls -Al | awk '/^-/ {print $8}'`
    cd debian
    sed -e 's/-O2/'"${ourflags}"'/g' -i `ls -Al | awk '/^-/ {print $8}'`
    cd ..
    dpkg-buildpackage -rfakeroot -uc -b
    echo :: leaving directory $directory ...
    cd ..
done
``` 
Save this as a file; for example: [I]recompile
[/I]Then do a ```
sudo chmod +x recompile
``` to make it executable.

Use it as either **sudo ./recompile kdelibs**. This will fetch dependencies and source before building. You can also use if for more then one package which is nice. I wanted to compile 8 packages over night so I used this.
Or just do a **sudo ./recompile**. This will assume you already have the source and it will only build.

**Note**...use this within a new directory otherwise it will span thrue your other directories and files.

This is not a pretty script since it basically assumes packages are built with -O2 and replaces the occurences of -O2 with your FLAGS. But hey..it works.

---

### Post by One Quick Question on 2005-12-20
Hmm.  Is this safe?  Do you think the hardcoded CFLAGS are there for a reason?

---

### Post by GoldBuggie on 2005-12-20
> Hmm. Is this safe?It is as safe as compiling them with your own flags. > Do you think the hardcoded CFLAGS are there for a reason? They are there cause someone put them there. Not meaning to be silly here just stating that the person who managed the package didn't put the ability to easy recompile. And we are only changing "-O2" to "-O2 XXXXX" and that feels pretty safe to me.

Besides if you run into some trouble. Let's say kdm doesn't start(this won't happen; but for the sake of the argument let's say it will). You will come to the console and to repair what you install all you have to do is sudo apt-get install XXXX. rebooot and woops kdm starts.

I've tried kdelibs, kdebase, libx* some other things etc and I haven't seen anything broken. I've seen some packages doens't make a difference(then I just reinstall the old one), but that is a whole other matter.

---

### Post by snelo on 2007-05-02
I'm confused.... way confused....
What I'm trying to do is recompile squid with --enable-follow-x-forwarded-for
(I'm using DansGuardian and want to give different rights to different PCs on my network - like one particular PC can only surf during certain hours - DansGuardian forces squid to see requests from localhost and so all my filtering is busted)

OK .... I managed to follow the above steps minus the CFLAGS stuff and was able to recompile my squid packages - but that just makes them the same as the binaries ??? Correct???

I edited the environment file and now when I echo CFLAGS or CXXFLAGS I get
--enable-follow-x-forwarded-for

Looking at the error file it is trying to run gcc with the code - and it is dumping out... 
error code 77 ... in config.log there is an entry
gcc --enable-follow-x-forwarded-for 
and that's where the errors start
so what do I need to do so I can recompile squid with that option?  Should I modify one of the other files?
Looking in the configure.in file there is lines that start with 
AC_ARG_ENABLE(follow-x-forwarded-for

Obviously I'm missing something which will be really obvious to someone.

---

### Post by snelo on 2007-05-04
bump

---

### Post by TrinitronX on 2008-12-20
I need to pass a special flag to the configure script to get a package to compile on ubuntu.  The build works with this flag, but when attempting to package it with dpkg-buildpackage, it looks like autoconf is passing the following command line (according to config.log after a failed build):

```
It was created by configure, which was
generated by GNU Autoconf 2.59.  Invocation command line was

  $ ./configure --prefix=/usr --mandir=${prefix}/share/man --build=x86_64-linux-gnu CFLAGS=-g -O2 -g

```

I need to pass a flag: "--with-xv-path=/usr/lib"

What is the correct way to do this with the debian tools?

---

