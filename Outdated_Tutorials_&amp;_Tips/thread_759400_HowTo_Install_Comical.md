---
title: "HowTo: Install Comical"
date: 2008-04-19
forum: Outdated Tutorials &amp; Tips
---

### Post by ACLBandit on 2008-04-19
So for everyone who's having some SERIOUS issues either A) finding a Comical .deb that works (I sure couldn't-- all the links seem to be down or B) making Comical compile from source, this is my attempt at assisting those who went through the same silliness I did.

According to the Comical website, Comical is an easy-to-use, featureful GUI comic book viewer, written in C++ using wxWidgets. 

It's also my personal favorite; sure, there are easy alternatives available in the software channel like QComicBook (A KDE app which, in gnome, is extremely buggy) as well as Comix, but I just like Comical, and I couldn't make it install for many many hours. Finally, I've got it.

I could not make version .8 compile no matter what. So, if you want this program, you have to go with the .7 version available [here]("http://sourceforge.net/project/downloading.php?groupname=comical&filename=comical-0.7.tar.gz&use_mirror=superb-east").

After downloading it, right-click it and extract it to the your home folder.

Open your command terminal.

Type the following: 
```

sudo apt-get install build-essential libwxgtk2.6-0 libwxgtk2.6-dev python-wxgtk2.6 zlib1g zlib1g-dev rar zip wx-common wx2.6-headers libwxbase2.6-dev python-wxversion libwxbase2.6-0 unrar-free unrar

```

To be honest, I don't know if ALL of those packages are necessary. 

Now, navigate to the comical source folder and then compile it with 

```
cd comical-0.7
make comical
```

If everything goes through without an error, you're good to go (finally!).

Type 

```
./comical
```

And enjoy your comics! ^_^


EDIT 5/2/08: Changed the extraction location to home folder instead of desktop so that the "cd" command would make sense for  someone unfamiliar with the command line.

---

### Post by mmcmonster on 2008-08-05
Thanks.

Unfortunately, this doesn't work for comical 0.8. :-(

---

### Post by ACLBandit on 2008-09-16
> **mmcmonster said:**
> Thanks.

Unfortunately, this doesn't work for comical 0.8. :-(

I know. Sorry...

...however, better than nothing, right? ^_^;

---

### Post by rockclimber112358 on 2010-01-29
Hey, I'm not sure if you guys are still following this thread, but I could use some help if you are.  I've loaded all the packages, but when I run "make comical" I get alot of errors:

```

`wx-config --cxx` `wx-config --cxxflags` -O2 -Wall -pipe -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -DRARDLL -D_UNIX -Iunrar -c -o src/ComicBook.o src/ComicBook.cpp

```

and

```

src/../Comical Icons/comical.xpm:210: warning: deprecated conversion from string constant to ‘char*’

```

Then, after several hundred of the second errors, I get the following errors:

```

src/ComicalApp.cpp: In member function ‘virtual bool ComicalApp::OnInit()’:
src/ComicalApp.cpp:65: error: invalid use of incomplete type ‘struct wxIcon’
/usr/include/wx-2.8/wx/gdicmn.h:35: error: forward declaration of ‘struct wxIcon’
src/ComicalApp.cpp: In member function ‘void ComicalFrame::OnGoTo(wxCommandEvent&)’:
src/ComicalApp.cpp:401: error: ‘wxGetNumberFromUser’ was not declared in this scope
src/ComicalApp.cpp: In member function ‘void ComicalFrame::OnBuffer(wxCommandEvent&)’:
src/ComicalApp.cpp:414: error: ‘wxGetNumberFromUser’ was not declared in this scope
make: *** [src/ComicalApp.o] Error 1

```

Any ideas about why I'm getting these errors, or what to do to fix it?  Thanks so much!

---

### Post by MysticOdin on 2010-11-30
I'm having the same problem too, my best guess is that this statement is allowed on microsoft's compiler and not by gcc

---

### Post by doperus on 2011-07-28
Thanks a lot it worked fine for me!

---

