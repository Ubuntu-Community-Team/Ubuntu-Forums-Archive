---
title: "Help making a compile script"
date: 2008-01-02
forum: Packaging and Compiling Programs
---

### Post by MONODA on 2008-01-02
Hi I am pretty new to ubuntu and to writing scripts but I do know a bit. I decided that I would make a script to create a .deb package for tarballs using checkinstall. I have the following so far but it does not work. Most of it was just guessing and messing around so I need to improve it a lot.
```
title="Create .deb from tarball"
dialog="Enter the name of the tarball without the extension"
filename=`gdialog --title "$title" --inputbox "$dialog" 200 100 2>&1`

	tar -zxvf $filename.tar.gz
	cd $filename
	./configure
	make
	sudo checkinstall
	shift
done
```
When I run it from terminal it says that the command does not exist and if I try to compile a tarball normally (without the script) I get an error when running make, the error is:
> make: *** No targets specified and no makefile found.  Stop.

is there anway to fix this? If anyone could help with that or with my script it would be great, thanks in advance.

---

### Post by MONODA on 2008-01-02
Please I really need some help with this script, any help would be appreciated.

---

### Post by amingv on 2008-01-02
I am very illiterate when it comes to shell scripts (only know one or two things), But I felt tempted to try the script and it worked (at least until the make part, because I didn't let it do checkinstall.) The only thing that comes to my mind is, are you sure you typed the path right?

Try and run it this way: cd to the directory where the script is, and type './scriptname', if the tar file is in the same folder, just type in the filename. If not make sure you input the correct path.

Also take notice that not all packages have the configure file in their main directory, so check where it is in your package.
Also remember that to run a script you must give it execute permission, this you can do with:

```
cd <path_where_script_is>
chmod +x myscript
```

Finally, not all source files have the extension '.tar.gz', allowing different file extensions would greatly add to the script's usefulness.

Anyway I may know less than you do about shell scripts for that matter. Just hope it helps.

---

### Post by odiseo77 on 2008-01-03
I'm not very good with scripts either, but you say 'make' didn't find any makefile when trying to compile the source; the 'configure' command, did it run fine and clean? I mean, did you get a normal output when executing the 'configure' script (most of times the 'Makefile' is created by the 'configure' script).

Other thing, I don't understand quite well the first 3 lines of your script, but I suppose on the first 3 lines your script is asking the user for the name of the program? Oh, and something very important here: did you add the ***#!/bin/bash*** line to the script? If you haven't, then edit it and type the following line at the very beginning of it:

```
#!/bin/bash
```

I think your script could get very complex assuming most of times when compiling a program 'configure' fails the first times when dependencies are not met, so, in case you're trying do write a generic script for compiling different sources, you must keep it in mind in order to receive failed 'configure' outputs and automatically tell apt-get to download certain packages, etc. (not to discourage you; in fact, I think this is a very interesting idea; only I don't have the skills to accomplish such difficult things with scripts).

Greetings, and good luck!

---

### Post by MONODA on 2008-01-03
> Other thing, I don't understand quite well the first 3 lines of your script, but I suppose on the first 3 lines your script is asking the user for the name of the program? Oh, and something very important here: did you add the #!/bin/bash line to the script? If you haven't, then edit it and type the following line at the very beginning of it:
the first three lines are meant to create variables in the script so I can refer to their values later by writing $'the name of the variable'. an yes I have added that and some other comments but I did not include them in my post.
My purpose is to create a menu in the right click menu in nautilus (this can be done with nautilus action configuration) that when clicked runs my script. First I need the script to work however. When I run the script from terminal everything succeeds except for the make operation. Comiling from source has NEVER worked for me, i have tried it with many tarballs and i always get the same error with the make operation. Can anyone else help...

---

### Post by MONODA on 2008-01-03
ok i found out that ./configure was not working because i didnt have qmake so i installed it but when I tried to compile a different tarball, it said that no target or makefile was specified.

---

### Post by Vadi on 2008-01-03
This will be awesome when it works, please keep us updated.

---

### Post by meatpan on 2008-01-03
> **MONODA said:**
> ok i found out that ./configure was not working because i didnt have qmake so i installed it but when I tried to compile a different tarball, it said that no target or makefile was specified.

This error typically means that you tried to run the 'make' command in a directory that doesn't contain a file named 'makefile' (or 'Makefile').   

Try adding the '-v' flag after the #!/bin/bash command.  This is a  useful debugging technique that causes all commands to be echoed to standard output *before* they are executed.

Another idea is to try chaining together the most important/dependent commands.  

The code would be changed to look like this:
```

./configure && make && sudo checkinstall

```

This decreases readability, but provides the benefit that 'make' will not be run unless './configure' finishes successfully, and 'sudo checkinstall' will not be run unless both './configure' and 'make' finish successfully.

---

### Post by MONODA on 2008-01-03
Thanks for the help but everything succeeds except I get this one error at the end. I am not sure what it means.
> cd source/AuxiliaryLibraries && qmake AuxiliaryLibraries.pro -o Makefile
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
Project MESSAGE: Configuring AuxilliaryLibraries
Project MESSAGE: -------------------------------
cd source/AuxiliaryLibraries && make -f Makefile
make[1]: Entering directory `/home/dany/Downloads/Tarballs/jahshaka/source/AuxiliaryLibraries'
cd blur && qmake blur.pro -o Makefile
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
cd blur && make -f Makefile
make[2]: Entering directory `/home/dany/Downloads/Tarballs/jahshaka/source/AuxiliaryLibraries/blur'
g++ -c -pipe -Wall -W -g -D_REENTRANT  -DJAHPREFIX=\"/usr/local\" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -I/usr/X11R6/include -I/usr/X11R6/include -o blurlib.o blurlib.cpp
make[2]: g++: Command not found
make[2]: *** [blurlib.o] Error 127
make[2]: Leaving directory `/home/dany/Downloads/Tarballs/jahshaka/source/AuxiliaryLibraries/blur'
make[1]: *** [sub-blur] Error 2
make[1]: Leaving directory `/home/dany/Downloads/Tarballs/jahshaka/source/AuxiliaryLibraries'
make: *** [sub-source-AuxiliaryLibraries] Error 2


---

### Post by NullHead on 2008-01-03
> **MONODA said:**
> Thanks for the help but everything succeeds except I get this one error at the end. I am not sure what it means.

You need build-essential.```
sudo apt-get install build-essential
```

---

### Post by MONODA on 2008-01-03
ok i got build essential but I am getting this error:
```
make[2]: Entering directory `/home/dany/Downloads/Tarballs/jahshaka/source/AuxiliaryLibraries/FTGL'
g++ -c -pipe -w -g -D_REENTRANT  -DJAHPREFIX=\"/usr/local\" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/share/qt3/include -I/usr/X11R6/include -I/usr/X11R6/include -o FTBitmapGlyph.o FTBitmapGlyph.cpp
In file included from FTBitmapGlyph.cpp:3:
FTBitmapGlyph.h:5:22: error: ft2build.h: No such file or directory
FTBitmapGlyph.h:6:10: error: #include expects "FILENAME" or <FILENAME>
FTBitmapGlyph.h:7:10: error: #include expects "FILENAME" or <FILENAME>
In file included from FTBitmapGlyph.h:9,
                 from FTBitmapGlyph.cpp:3:
FTGL.h:44:31: error: GL/gl.h: No such file or directory
FTGL.h:45:32: error: GL/glu.h: No such file or directory
In file included from FTBitmapGlyph.h:10,
                 from FTBitmapGlyph.cpp:3:
FTGlyph.h:5:10: error: #include expects "FILENAME" or <FILENAME>
FTGlyph.h:6:10: error: #include expects "FILENAME" or <FILENAME>
In file included from FTGlyph.h:8,
                 from FTBitmapGlyph.h:10,
                 from FTBitmapGlyph.cpp:3:
FTBBox.h:5:10: error: #include expects "FILENAME" or <FILENAME>
FTBBox.h:7:10: error: #include expects "FILENAME" or <FILENAME>
In file included from FTBBox.h:10,
                 from FTGlyph.h:8,
                 from FTBitmapGlyph.h:10,
                 from FTBitmapGlyph.cpp:3:
FTPoint.h:5:10: error: #include expects "FILENAME" or <FILENAME>
FTPoint.h:6:10: error: #include expects "FILENAME" or <FILENAME>
FTPoint.h:39: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;&&#8217; token
FTPoint.h:39: error: ISO C++ forbids declaration of &#8216;FT_Vector&#8217; with no type
FTPoint.h: In constructor &#8216;FTPoint::FTPoint(int)&#8217;:
FTPoint.h:40: error: &#8216;ft_vector&#8217; was not declared in this scope
FTBBox.h: At global scope:
FTBBox.h:49: error: expected `)' before &#8216;glyph&#8217;
FTGlyph.h:31: error: expected `)' before &#8216;glyph&#8217;
FTGlyph.h:65: error: &#8216;FT_Error&#8217; does not name a type
FTGlyph.h:81: error: &#8216;FT_Error&#8217; does not name a type
FTBitmapGlyph.h:31: error: expected `)' before &#8216;glyph&#8217;
FTBitmapGlyph.cpp:5: error: expected `)' before &#8216;glyph&#8217;
FTBitmapGlyph.cpp: In member function &#8216;virtual float FTBitmapGlyph::Render(const FTPoint&)&#8217;:
FTBitmapGlyph.cpp:57: error: ISO C++ forbids declaration of &#8216;type name&#8217; with no type
FTBitmapGlyph.cpp:57: error: ISO C++ forbids declaration of &#8216;type name&#8217; with no type
FTBitmapGlyph.cpp:57: error: expected primary-expression before &#8216;const&#8217;
FTBitmapGlyph.cpp:57: error: expected `)' before &#8216;const&#8217;
FTBitmapGlyph.cpp:59: error: &#8216;GL_UNPACK_ROW_LENGTH&#8217; was not declared in this scope
FTBitmapGlyph.cpp:59: error: &#8216;glPixelStorei&#8217; was not declared in this scope
FTBitmapGlyph.cpp:60: error: ISO C++ forbids declaration of &#8216;type name&#8217; with no type
FTBitmapGlyph.cpp:60: error: ISO C++ forbids declaration of &#8216;type name&#8217; with no type
FTBitmapGlyph.cpp:60: error: expected primary-expression before &#8216;const&#8217;
FTBitmapGlyph.cpp:60: error: expected `)' before &#8216;const&#8217;
FTBitmapGlyph.cpp:62: error: ISO C++ forbids declaration of &#8216;type name&#8217; with no type
FTBitmapGlyph.cpp:62: error: ISO C++ forbids declaration of &#8216;type name&#8217; with no type
FTBitmapGlyph.cpp:62: error: expected primary-expression before &#8216;const&#8217;
FTBitmapGlyph.cpp:62: error: expected `)' before &#8216;const&#8217;
make[2]: *** [FTBitmapGlyph.o] Error 1
make[2]: Leaving directory `/home/dany/Downloads/Tarballs/jahshaka/source/AuxiliaryLibraries/FTGL'
make[1]: *** [sub-FTGL] Error 2
make[1]: Leaving directory `/home/dany/Downloads/Tarballs/jahshaka/source/AuxiliaryLibraries'
make: *** [sub-source-AuxiliaryLibraries] Error 2
        shift
done
/home/dany/Documents/Install from Source: line 17: syntax error near unexpected token `done'
/home/dany/Documents/Install from Source: line 17: `done'

```
my script looks like this:
[CODE]#!/bin/bash -v

---

### Post by NullHead on 2008-01-03
remove you're working folder and then re extract you're tarball.

---

### Post by MONODA on 2008-01-04
Alright I finished the script it works but you have to manually install the dependencies. If anyone could tell me a way to automatically install the dependencies for a package it would be great. Thanks I have attached the script.

---

### Post by MONODA on 2008-01-04
oops sorry here it is:

---

### Post by MONODA on 2008-01-14
Ok you guys I have worked on the script a bit more since I last posted and here is what I got:

My previous version worked but you had to manually get the packages so i tried to make it easier to do that. Please read the comments in my script, it has questions commented out.

---

### Post by MONODA on 2008-01-14
One more thing. In the script, I want to be able to install the packages that are checked, how can I do this?
Thanks I cant wait until this completely works its gonna be awesome :)

---

### Post by NullHead on 2008-01-15
> **MONODA said:**
> One more thing. In the script, I want to be able to install the packages that are checked, how can I do this?
Thanks I cant wait until this completely works its gonna be awesome :)

Checked as in checkinstalled? or the .deb produced after the script? You could always use a sudo dpkg -i *.deb on the end of it to install a .deb after the scrip.

---

### Post by MONODA on 2008-01-15
no check as in checkbox because the new script will ask you for the dependencies for the package you want to install then it will run ```
sudo apt-cache search [whatever you searched for]
```. I want the output to be outputed into a checklist so that the person using the script can check the ones they want and after that the ones that have been checked(as in checkbox) will be installed

---

### Post by MONODA on 2008-01-28
Can anyone help? I havent gotten any work done since my last post becuase I really dont know what to do next.

---

### Post by MONODA on 2008-02-23
Ok here is the lastest version, I have attached it

---

### Post by Vadi on 2008-02-23
It was executable right away, so that's a good start. But.. can we get a 'browse' button?

Or maybe make it a nautilus script, such that when we run the script on whatever file we have selected, it'll use that file?

---

### Post by MONODA on 2008-02-23
I thought of that but then I there is no way for the script to know which directory to cd to once the tarball has been extracted. Basically this script has almost no use untill I can get it to search apt and install the dependencies from within the script. do u know of anyway to do that?

---

### Post by Vadi on 2008-02-23
I think someone made a program that find what dependencies do you need... PM "Artifical Intelligence" about this and mention the "getlibs" program. That's what I think it's called.

---

### Post by NullHead on 2008-02-23
Getlibs was made by my friend Cappy. He is the person you need to PM.

EDIT: here is his thread on his project: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by Cappy on 2008-02-24
What you want is dpkg-checkbuilddeps
Look at this:
> 
~/Desktop/gaim-xfire-0.6.1~20071109$dpkg-checkbuilddeps 
dpkg-checkbuilddeps: Unmet build dependencies: debhelper (>= 4.0.0) autotools-dev gaim-dev | pidgin-dev (<= 1:2.1.1-1) | libpurple-dev gaim-dev | pidgin-dev (<= 2.1.1-1) | pidgin-dev (> 1:2) | libpurple-dev gaim-dev | imagemagick libglib2.0-dev automake1.9


You should also look at dpkg-buildpackage. Use existing tools. Read the man pages. Read the Ubuntu MOTU pages. They will all help.

Something along these lines
> 
dpkg-checkbuilddeps 2>&1 | sed -e 's/([^(]*)//g' -e 's/| //g' -e 's/dpkg-checkbuilddeps: Unmet build dependencies://g'

which will print out a nice list like 
>  debhelper  autotools-dev gaim-dev pidgin-dev  libpurple-dev gaim-dev pidgin-dev  pidgin-dev  libpurple-dev gaim-dev imagemagick libglib2.0-dev automake1.9

which you may be able to put straight into apt-get. First though, you should check with apt-cache show packagename (or apt-cache policy packagename ^_^) because a bad package name such as gaim-dev will ruin the apt-get. Apt-cache search is useless for this kind of stuff. It is slow and brings back TONS of unrelated results.

---

### Post by MONODA on 2008-02-24
wow thanks  a lot I think ill check that out.

---

### Post by MONODA on 2008-02-24
whenever I run dpkg-buildpackage i get 
> dpkg-parsechangelog: error: cannot open debian/changelog to find format: No such file or directory
dpkg-buildpackage: unable to determine source package is

and when I run dpkg-checkbuilddeps i get
> dpkg-checkbuilddeps: error: cannot read control file debian/control: No such file or directory

whats going on? how can I fix this

---

