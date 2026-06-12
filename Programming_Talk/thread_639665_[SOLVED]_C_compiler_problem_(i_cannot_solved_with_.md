---
title: "[SOLVED] C compiler problem (i cannot solved with &amp;quot;sudo apt-get install build-essenti"
date: 2007-12-13
forum: Programming Talk
---

### Post by eerraayyss on 2007-12-13
hi everyone..
this year i began my education in computer engineering;we study c language and i'm an absolute rookie.
I heard that linux is great for programmers and i just installed ubuntu.

but i cannot compile my basic programs..? i installed KDevelop..took all the packages.. "build-essentials","G++","GCC" etc...But when i wrote a hello world application it gives error;

it says there is no Makefile in the directory and than gives error;
cd '/home/eray/eee' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -f Makefile.cvs && mkdir '/home/eray/eee/debug' && cd '/home/eray/eee/debug' && CFLAGS="-O0 -g3 " "/home/eray/eee/configure" --enable-debug=full && cd '/home/eray/eee/debug/src' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -k eee.lo
aclocal
make: aclocal: Komut bulunamad&#305;
make: *** [all] Hata 127
*** Exited with status: 2 ***


i took snapshots;

[[IMG]http://img91.imageshack.us/img91/813/ekrangrntsyo7.png[/IMG]](http://imageshack.us)
[[IMG]http://img519.imageshack.us/img519/6034/ekrangrnts1xz0.png[/IMG]](http://imageshack.us)
[[IMG]http://img519.imageshack.us/img519/6034/ekrangrnts1xz0.1ba1644386.jpg[/IMG]](http://g.imageshack.us/g.php?h=519&i=ekrangrnts1xz0.png)

can you suggest another compiler for c? some people say vim is a good compiler;i installed it but dont know how to open it;i couldnt find it:(

i hope you guys help me and find me a solution.

---

### Post by meatpan on 2007-12-13
> **eerraayyss said:**
>  installed KDevelop..took all the packages.. "build-essentials"

Assuming this is a typo, and you meant 'build-essential',

> 
can you suggest another compiler for c? some people say vim is a good compiler;i installed it but dont know how to open it;i couldnt find it:(


This is not a compiler problem.  Also, vim is not a compiler.

The following is a personal opinion derived from my own particular experiences, so this might not apply to you:
As a novice programmer writing C code for linux, you should learn how compilation works.  IDE's such as KDevelop and eclipse can abstract this process to a button-press,  but until you learn what the IDE is running on your behalf, I suggest compiling tools manually.  This will require a lot of reading, patience, and practice, but in the end these efforts will make you a considerably more knowledgeable developer.   

Try opening a terminal, and compiling the source code manually.
```

> cd home/eray/eee
> gcc -Wall eee.c
> ./a.out

```

This will change your current working directory to the same directory as the source code, compile the source code (printing warnings), and running the program.   I am happy to help if you have any questions about the make/compilation progress, and there is also a useful forum on these boards that is devoted specifically to this process:  [http://ubuntuforums.org/forumdisplay.php?f=44](http://ubuntuforums.org/forumdisplay.php?f=44)

---

### Post by eerraayyss on 2007-12-13
thanks for your help,i know i have a lot to do..
manually compiling..that sounds fantastic for me..i just start to realize what linux really means..

but can you tell me how i can write my projects and compile them until i become good at linux..i really dont want to turn back to windows and visual c++..i still dont know what is wrong with my KDevelop and cant find that kind a problem in forums..there must be a way right?:)

---

### Post by eerraayyss on 2007-12-13
come on guys i really need your help..
i got homeworks to do...:)
i just cant figure out what is wrong with my ubuntu:(

---

### Post by samjh on 2007-12-13
Firstly, why are you using a complex IDE for a very simple Hello World program?  You'll probably be much better served by using a code editor like Gedit (go to Applications menu -> Accessories -> Text Editor) and compiling using the command line.

Let's get the basics right.

Put this command into your terminal:
```
sudo apt-get install build-essential
```

Navigate to the directory containing your eee.c source file.

Enter this command:
```
gcc -o eee eee.c
```
That command will compile your eee.c source into an executable program called, eee.

The -o switch allows you to specify the output file of the compilation.  In this case, that's eee.  The eee.c at the end of the command is the input file to compile.

You can also create a make file to do compilation for you.

Create a file called, Makefile, in the same directory as your eee.c file.

Enter these into Makefile (IMPORTANT: the indentations are real tabs, not spaces):
```
eee: eee.c
    gcc -o eee eee.c
```
The line eee: eee.c tells Make that the output file eee, needs eee.c.  The line underneath is the command to create eee.

Let's say you have eee which needs eee.c and fff.c to be compiled first into object files (they end with the *.o suffix).  Your makefile may look like this:
```
eee: eee.o fff.o

eee.o: eee.c
    gcc -c eee.c

fff.o: fff.c
    gcc -c fff.c
```This tells Make that eee depends on eee.o and fff.o object files.  The second block of commands eee: eee.c and gcc -c eee.c tells Make how to create the eee.o object file.  The third block gives similar instruction for the fff.o object file.

To run the Makefile, just type ```
make
```into terminal while in the same directory as the Makefile.

---

### Post by doubl00 on 2007-12-14
Hi eerraayyss
following your lead, I did the same thing.  same error.  
FAQ-KDevelop says:
[http://www.kdevelop.org/mediawiki/index.php/FAQ#How_do_I_create_New_Files_in_a_Project.3F](http://www.kdevelop.org/mediawiki/index.php/FAQ#How_do_I_create_New_Files_in_a_Project.3F)
What to do when automake & friends fails with strange error messages?
Open a console window in your project root directory and type: 
libtoolize --copy --force
It should solve the problem of conflicting autotools versions between KDevelop and your installed system. 
so I tried: "libtoolize --copy --force
[http://www.kdevelop.org/mediawiki/index.php/FAQ#How_do_I_create_New_Files_in_a_Project.3FThe](http://www.kdevelop.org/mediawiki/index.php/FAQ#How_do_I_create_New_Files_in_a_Project.3FThe) program 'libtoolize' is currently not installed.  You can install it by typing:
sudo apt-get install libtool
So i did. 
 donald@eMachine:~/Lessons/HelloWorld$ libtoolize --copy --force
You should add the contents of `/usr/share/aclocal/libtool.m4' to `aclocal.m4'.
donald@eMachine:~/Lessons/HelloWorld$ cd /usr/share/aclocal
donald@eMachine:/usr/share/aclocal$ ls
fontutil.m4  gsl.m4  libtool.m4  xorg-macros.m4  xorgversion.m4
donald@eMachine:/usr/share/aclocal$

That's where I am now.  Looks like I need to add teh contents of libtool,m4 to aclocal.m4   But that file does not exist so I am  not sure what to do next.

---

### Post by eerraayyss on 2007-12-14
@doubl00
you cant figure out the problem,can you?i did wahat you did,and took same result..i think the problem is at "aclocal"..we should find or create an "aclocal.m4" and put the contents of libtool.m4 in it,but where???where is aclocal.m4??

@samjh thanks for your professional help..
i used to press compile button in Visual C++ and it was doing all the process and show me the result..I havent know the scenes behind the compile process,that will help me a lot..but i got a few questions

Firstly;what exactly a Makefile??why doesnt compiler create one automaticly..should i create a make file for all my projects?
Secondly;
> Create a file called, Makefile
what is the type of this file?should i create it in text editor and write inside of this file ;
"eee: eee.c
    gcc -o eee eee.c"??

Lastly;> 
Navigate to the directory containing your eee.c source file.
Enter this command:
gcc -o eee eee.c


with this method i compiled my program it was created in the same directory of my eee.c file..it say it is an executable file..but i couldnt open it when i double-clicked it?:)
i'm absolute beginner at terminal..how can open it in terminal..?
(i wrote executable file's name and it says command not found,there must be an openning command first,i think:))

sorry for my easy questions..it would help me a lot if you guys show me how to handle with terminal..i realized you do all of your work in terminal..but there is alot of code i should learn:(

---

### Post by samjh on 2007-12-14
It's great to see you're enthusiastic about your learning, eerrayyss. :)

A Makefile is just a normal text file with a script to tell the compiler how to build your project.  The script looks like this:
```
myexecutable: myprogram.c
    gcc -o myexecutable myprogram.c
```

The Makefile is used used by a program called "make", which runs the script within it.  When you invoke the "make" command in a directory, make will always search for a file named Makefile and run it.

The file name of a Makefile is always "Makefile". :)  There is no file extension like .txt.  You can create it using a text editor.

The reason why you can't run the compiled eee executable is because you need to be in the command-line terminal to run it.  Go to Applications -> Accessories -> Terminal to open up your command-line terminal window.

Run your executable by typing:```
./eee
```Notice the ./ in front of the executable file name.  The ./ means the file is in the current directory.

(See my signature to look up useful Linux commands you can use in the terminal. :) )

A bit more info about make.  As I said before, make is a program that runs the Makefile script.  Make will be installed when you install the build-essential package.  KDevelop and some other IDEs use Automake and Autoconf to automatically generate Makefile and other files used for building.  However, Automake and Autoconf are VERY complicated to set up and use.  For small projects, you'd be better off just using a hand-made Makefile.

At this stage of your learning, stick to command-line compilation and a Makefile.

After you're familiar with those, you can try IDEs.  I recommend Eclipse with the CDT plug-in (available on Ubuntu via Synaptic).

---

### Post by pedro_orange on 2007-12-14
> **eerraayyss said:**
> 
with this method i compiled my program it was created in the same directory of my eee.c file..it say it is an executable file..but i couldnt open it when i double-clicked it?:)


This is because your program will have no breaks in. So when the program is run, it opens does its job, and then closes. Hence why you can't see anything. 
Especially if it's a hello world app - it's going to take less than a second to open run and close. Unless you've got super sight/reactions I doubt you're going to see anything going on!

./executable_name will run it if you're in the directory its located!

Keep the faith!

---

### Post by doubl00 on 2007-12-14
My KDevelop now compiles and runs through the IDE.  I used 

      sudo aptitude install kde-devel build-essential

---

### Post by ameba on 2007-12-14
h

---

### Post by samjh on 2007-12-15
You need to make sure build-essential is installed first.  Do this in terminal:
```
sudo apt-get install build-essential
```

If that doesn't allow you to compile, post the first few lines of your source code here.  It looks like there might be a problem with your #include directives.

Make sure your #include directives are in this format:
```
#include <stdio.h>
```

---

### Post by ameba on 2007-12-15
[

---

### Post by chips24 on 2007-12-15
run some updates...

---

### Post by eerraayyss on 2007-12-16
ok guys I solved my problem;I installed some packages called "Makefile" from Synaptic..I dont which one solved my problem but now I can compile my programs with KDevelop:)

but unfortunately I cant use it,because my computer does not turn on..
I post a thread  about it;
[http://ubuntuforums.org/showthread.php?t=642047](http://ubuntuforums.org/showthread.php?t=642047)
if you guys check out,it would be great

---

