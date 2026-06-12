---
title: "Setting up Kubuntu Hardy for Development"
date: 2008-07-31
forum: Programming Talk
---

### Post by bigj2632 on 2008-07-31
I was wondering is there a way to set up kubuntu to develop kde 4 apps or do i need to follow kde's guide to setting it up which requires me to compile kde from source.

---

### Post by mssever on 2008-07-31
> **bigj2632 said:**
> I was wondering is there a way to set up kubuntu to develop kde 4 apps or do i need to follow kde's guide to setting it up which requires me to compile kde from source.
I don't use KDE, but I doubt it's that complicated. Probably it's just a matter of installing build-essential and the Qt development packages for whatever language you'll be using. All the basics should already be in the repos.

---

### Post by bigj2632 on 2008-08-01
I installed all the dev versions of pretty much all the kde4 files i could find also cmake, automake, build essential and what not. i know that if i install all that stuff in gnome it pretty much is set up to develop but when i try the kde tutorial off the website i get an error that it cannot find the some of the functions i am calling out wich means i think that it cannot find the dev files.  Is there something i need to edit to make my computer find those files and allow me to compile successfully.

---

### Post by mssever on 2008-08-01
> **bigj2632 said:**
> I installed all the dev versions of pretty much all the kde4 files i could find also cmake, automake, build essential and what not. i know that if i install all that stuff in gnome it pretty much is set up to develop but when i try the kde tutorial off the website i get an error that it cannot find the some of the functions i am calling out wich means i think that it cannot find the dev files.  Is there something i need to edit to make my computer find those files and allow me to compile successfully.
If you post the specific errors, someone might be able to recognize the problem. I've never tried KDE development, so I probably can't help you, but if you post error messages, someone else probably can.

---

### Post by bigj2632 on 2008-08-01
Here is the error message:

james@james-laptop:~$ g++ main.cpp -o tutorial1 \                                                                                  
> -I$QTDIR/include/Qt \                                                                                                            
> -I$QTDIR/include/QtCore \                                                                                                        
> -I$QTDIR/include \                                                                                                               
> -I$KDEDIR/include/KDE \                                                                                                          
> -I$KDEDIR/include \                                                                                                              
> -L$KDEDIR/lib \                                                                                                                  
> -L$QTDIR/lib -lQtCore -lQtGui -lkdeui -lkdecore                                                                                  
main.cpp:1:24: error: KApplication: No such file or directory                                                                      
main.cpp:2:22: error: KAboutData: No such file or directory
main.cpp:3:24: error: KCmdLineArgs: No such file or directory
main.cpp:4:23: error: KMessageBox: No such file or directory
main.cpp:39:2: warning: no newline at end of file
main.cpp: In function &#8216;int main(int, char**)&#8217;:
main.cpp:8: error: &#8216;KAboutData&#8217; was not declared in this scope
main.cpp:8: error: expected `;' before &#8216;aboutData&#8217;
main.cpp:32: error: &#8216;KCmdLineArgs&#8217; has not been declared
main.cpp:32: error: &#8216;aboutData&#8217; was not declared in this scope
main.cpp:33: error: &#8216;KApplication&#8217; was not declared in this scope
main.cpp:33: error: expected `;' before &#8216;app&#8217;
main.cpp:34: error: &#8216;KGuiItem&#8217; was not declared in this scope
main.cpp:34: error: expected `;' before &#8216;yesButton&#8217;
main.cpp:37: error: &#8216;KMessageBox&#8217; has not been declared
main.cpp:37: error: &#8216;i18n&#8217; was not declared in this scope
main.cpp:38: error: &#8216;yesButton&#8217; was not declared in this scope

I used the code from this page which is a basic hello world for kde4.
[http://techbase.kde.org/Development/Tutorials/First_program](http://techbase.kde.org/Development/Tutorials/First_program)

Thanks msserver for the try.

---

### Post by Hayrola on 2008-08-24
Save this to a file: (like "kde4dev.sh" for example)
```

#!/bin/bash

#this is shamelessly stolen by hayer form http://techbase.kde.org/Getting_Started/Increased_Productivity_in_KDE4_with_Scripts/.bashrc

prepend() { [ -d "$2" ] && eval $1=\"$2\$\{$1:+':'\$$1\}\" && export $1 ; }

# Qt
# only set Qt related variables if you compiled Qt on your own
# (which is discouraged). if you use the distro provided Qt, skip
# this section. Comment it if necessary.
export QTDIR=/usr/share/qt4
prepend PATH $QTDIR/bin
prepend LD_LIBRARY_PATH $QTDIR/lib
prepend PKG_CONFIG_PATH $QTDIR/lib/pkgconfig


# KDE
export KDEDIR=/usr/lib/kde4
export KDEHOME=$HOME/.kde4
export KDETMP=/tmp/kde4-$USER
mkdir -p $KDETMP
export KDEDIRS=$KDEDIR
prepend PATH $KDEDIR/bin
prepend LD_LIBRARY_PATH $KDEDIR/lib
prepend PKG_CONFIG_PATH $KDEDIR/lib/pkgconfig
prepend QT_PLUGIN_PATH $KDEDIR/lib/kde4/plugins

```

then open a console and type:
```

source kde4dev.sh

```

in this console the build command should now work!
(if it don't work anyway, assert that you have "kde4-devel" installed)

---

### Post by bigj2632 on 2008-09-19
Thanks alot for your help you guys, Hayrola i tried that script you gave me and after a few modifications i got it working.  FIrst off I just commented out the qt stuff, then change some of the kde variables

export KDEDIR=/usr/
export KDEHOME=/.kde

I tested this and it worked on intrepid so im not entirely sure on Hardy although i dont see why it would not work.

---

