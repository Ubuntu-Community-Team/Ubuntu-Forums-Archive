---
title: "Brutal Chess Mod"
date: 2009-12-12
forum: Programming Talk
---

### Post by HellionDarkLord on 2009-12-12
Hi all!

i am new to programming like this.  I have modded several games, but nothing I had to compile first.  Trying to compile Brutal Chess is giving me a headache. I wanted to try it out for the first time and then make a mod that I call Epic Chess. I made the board game version and everyone at the college wants me to bring it and play 5 games at the same time.  LOL!! I have had to make them put their names on a list to stop fights for who plays next.  Glass chess pieces were a really bad idea!

Everything looks great when running ./configure.  However when I run the make command I get errors that I have no idea what to do with.

```
brutalplayer.cpp:37: error: ‘INT_MAX’ was not declared in this scope
make[2]: *** [brutalplayer.o] Error 1
make[2]: Leaving directory `/home/gabriel/brutalchess-0.5.2/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/gabriel/brutalchess-0.5.2/src'
make: *** [all-recursive] Error 1

```

Perhaps there is a #include missing somewhere?  I'm running Ubuntu 9.10 with the gcc 4.4 it came with.  

Maybe I'm the only one who cares about this game.  I think it is the most beautiful start.  Why is it still alpha?

Thanks,

HD

---

### Post by dhillonv10 on 2009-12-26
Alright have you installed build-essential, may be the program needs g++ to compile c++ files. Other than that, check the dependencies, you might be missing something there :popcorn:

---

### Post by snova on 2009-12-26
> **HellionDarkLord said:**
> ```
brutalplayer.cpp:37: error: ‘INT_MAX’ was not declared in this scope
make[2]: *** [brutalplayer.o] Error 1
make[2]: Leaving directory `/home/gabriel/brutalchess-0.5.2/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/gabriel/brutalchess-0.5.2/src'
make: *** [all-recursive] Error 1

```

Perhaps there is a #include missing somewhere?  I'm running Ubuntu 9.10 with the gcc 4.4 it came with.

If you're still trying to fix this, that would appear to be the problem. INT_MAX is defined in limits.h, so add this to the top of src/brutalplayer.cpp:

[php]#include <limits.h>[/php]

---

### Post by HellionDarkLord on 2010-01-01
AWESOME!!! thanks I'll try it!

---

### Post by HellionDarkLord on 2010-01-01
SO now I'm back to this project once again.

I've gone and done a complete reinstall because of a hard drive failure.  So I had to reinstall all the dev packages, but I finally got a "yes" for EVERYTHING when running ./configure :P

now I can't get make install to run properly.

I had no idea what aclocal.m4 was or why it was causing an error.
```
 make install
cd . && aclocal-1.8 
/bin/bash: aclocal-1.8: command not found
make: *** [aclocal.m4] Error 127

```

No idea what that meant then found out that it was the version of automake.  So, checking automake version with synaptic I found that it was 1.11

So after poking around in the Makefile I found :
```
ACLOCAL = aclocal-1.8
```

That can't be right. so I changed it to 1.11

```
make install
cd . && aclocal-1.11 
acinclude.m4:28: warning: underquoted definition of AM_PATH_SDL
acinclude.m4:28:   run info '(automake)Extending aclocal'
acinclude.m4:28:   or see http://sources.redhat.com/automake/automake.html#Extending-aclocal
configure.ac:42: warning: AC_CACHE_VAL(mdl_cv_have_OpenGL, ...): suspicious presence of an AC_SUBST in the second argument, where no actions should be taken
../../lib/autoconf/general.m4:2018: AC_CACHE_VAL is expanded from...
../../lib/autoconf/general.m4:2039: AC_CACHE_CHECK is expanded from...
acinclude.m4:190: MDL_HAVE_OPENGL is expanded from...
configure.ac:42: the top level
 cd . && automake-1.8 --foreign 
/bin/bash: line 4: automake-1.8: command not found
make: *** [Makefile.in] Error 1

```


No success.

```
configure: WARNING: `missing' script is too old or missing

```

maybe that's the culprit?

can't Find anything so

maybe I need to regenerate the build system entirely?  

How do I do that?

Am I completely going in the wrong direction here?

Thanks in advance for any help!

HD

---

### Post by HellionDarkLord on 2010-01-01
oopse!! I changed the wrong line.

```
ACLOCAL = aclocal-1.8
```

stays the same!

```
AUTOMAKE = automake-1.8
```
is now
```
AUTOMAKE = automake-1.11
```

and that seems to work... yeesh!

---

### Post by HellionDarkLord on 2010-01-02
YAY!!! I fixed it!!  Now the game runs and looks beautiful!

I noticed that the game available in the repositories doesn't have the green marble look to the board like the one I just complied and built.  Interesting to say the least!!

So what I had to do to make this build nicely was to comment out all instances of glvoid

Objview.cpp```
int initGL( GLvoid );
```

became
```
int initGL(/* GLvoid*/ );
```

and also in md3view

```
int initGL(/* GLvoid*/ )
```

I did this for each time GLvoid appears in the code.

This is beautiful chess game!

HD

---

### Post by HellionDarkLord on 2010-01-02
this is what it looks like:

[IMG]http://c3.ac-images.myspacecdn.com/images02/129/l_50df38a1814249b59eef4ec872fca342.png[/IMG]

---

### Post by aviedw on 2010-01-02
What you did with that chess games seems impossible.

---

### Post by aviedw on 2010-01-02
wow, thats beautiful. Is there any way i cant get a copy of that game?

---

### Post by HellionDarkLord on 2010-01-02
Now I've modified the marble board. Looks better no?

[IMG]http://img709.imageshack.us/img709/2201/screenshot2im.png[/IMG]

---

### Post by 10nitro on 2010-01-02
> **aviedw said:**
> wow, thats beautiful. Is there any way i cant get a copy of that game?

sudo apt-get install brutalchess

all he did was change the bitmaps--it still looks really good.

---

### Post by HellionDarkLord on 2010-01-02
The bitmaps aren't the only difference between what I have and the game that's available in the repositories.

I don't know how to make the source code do what it needs to do:

#1. It tries to build with automake1.8 and the system has automake 1.11 so it won't build.  something wrong with the ./configure
#2.  "GLvoid" in the needs to be deleted or commented-out in both Objview.cpp and also in md3view.cpp before it will build properly.

Then I don't know how to make it into a binary package.

However, this is the new PNG for the green marble:

[http://img199.imageshack.us/img199/8238/marblehugeblack.png](http://img199.imageshack.us/img199/8238/marblehugeblack.png)

And this is the white:

[http://img23.imageshack.us/img23/1747/marblehugewhite.png](http://img23.imageshack.us/img23/1747/marblehugewhite.png)

Make install has to be run with all the proper dev packages and build packages required.

I'm totally brand new to this.  So for most of it you are on your own.

This is a side by side comparison of the screen shots.  The original is on the left.

[IMG]http://img15.imageshack.us/img15/7697/screenshot3go.png[/IMG]

---

### Post by HellionDarkLord on 2010-01-02
okay I will show you how to configure and build everything from source.

packages needed in Ubuntu 9.10:

Automake1.11
Autoconf
build-essential
gawk
FreeType 2.1.9
libxmu-dev 
libxi-dev

I don't remember them all right now but when ./configure errors then you need the dev package for anything that has "no" at the end of the line. (except for cross compile)

Download the src:[***Here***]("http://sourceforge.net/projects/brutalchess/")

extract to a new folder and open gnome terminal in that folder

run "./configure" in terminal in the directory you just extracted it to, and get the dev packages for whatever errors show up.  That's how I did it.

Don't run "make install" yet. 

Edit the Makefile in brutalchess-0.5.2 folder
```
AUTOMAKE = automake-1.8
```

Should instead be:
```
AUTOMAKE = automake-1.11
```

or whatever automake version you have. (look in synaptic or apt for the version number.)

Then

Do a search in gedit in the md3view.cpp file in the game's src folder (Ctrl+f) for GLvoid and either erase the words GLvoid leaving the parenthesis there, or put /* */ on either side of it to comment it out. Do this for every Glvoid in the file. (Why I said to search for it.)

Edit md3view.cpp looking for line 75.
```
int initGL( GLvoid );
```
This is wrong and I have no idea what it means. Change it to:
```
int initGL(/* GLvoid*/ );
```

Then Edit objview.cpp the same way this time deleting each GLvoid and just leaving the parenthesis.

Don't know why that is but it will error if you just comment it out.

Next you will want to replace the png's in the Art folder. Copy them from imageshack making sure they are 1024x1024 in size and paste the new png's into the Art folder making sure they are named marblehugeblack.png and marblehugewhite.png thus rewriting the files.

Then in terminal in the brutalchess-0.5.2 directory type in
```
sudo make install
``` 

hit enter, and then your password and hit enter again to build/install the game.  If it builds without any errors, type
```
brutalchess
```
in the terminal and hit enter.  

To get to the game menu hit Esc. I want to next add a menu you can get to from the mouse, but I don't know how yet.  

Hope you have lots of fun.

HD

---

