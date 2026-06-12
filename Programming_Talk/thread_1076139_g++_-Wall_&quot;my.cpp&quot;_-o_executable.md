---
title: "g++ -Wall &quot;my.cpp&quot; -o executable ?"
date: 2009-02-21
forum: Programming Talk
---

### Post by Leo Dragonheart on 2009-02-21
Could someone answer a couple of questions for me? I have for the last few days now been using g++ -Wall "my.cpp" -o executable, chmod u+x executable, ./executable, and I don't even know what it is. I know what is does but not what it is. 

1. What is the -Wall and -o, and what do they do?

2. Does the W in -Wall have to be capitalised?

3. I know chmod is change mode but what is the u+x?

4. Do I have to use chmod every time I run a file or once it's changed does it stay changed?

5. Once I have the file compiled and chmod-ed, can I jus use ./filename to execute it?

6. If anyone can show me some shortcuts for not having to type this out every time I want to compile and run a file since I am studing C++ and am doing this about a hundred times a day. I would greatly appreciate it thx.
( I already know the cut & paste method...:D ).

---

### Post by monkeyking on 2009-02-21
When you compile your program you might have missed some stuff,
when using -Wall the compiler will spit out  stuff it things you have  messed up. -Wall is short for Warning all.
If you want a list of stuff it checks for, you should read the man gcc part called Warning Options

-o just renames you executable from the std ./a.out to your -o arg.

chmod u+x file makes the file executable for the current user.
You shouldn't have to type chmod u+x anytime when using gcc.

If your project depends on multiple files or strange linking.
Consider using makefiles.
When I test my prog, I type in

```
make
./myprog

```

---

### Post by Leo Dragonheart on 2009-02-21
> **monkeyking said:**
> When you compile your program you might have missed some stuff,
when using -Wall the compiler will spit out  stuff it things you have  messed up. -Wall is short for Warning all.
If you want a list of stuff it checks for, you should read the man gcc part called Warning Options

-o just renames you executable from the std ./a.out to your -o arg.

chmod u+x file makes the file executable for the current user.
You shouldn't have to type chmod u+x anytime when using gcc.

If your project depends on multiple files or strange linking.
Consider using makefiles.
When I test my prog, I type in

```
make
./myprog

```

Thank you for the information. I have not tried the make thing yet so I will give that a try, thanx again..:D

---

### Post by nvteighen on 2009-02-21
> **Leo Dragonheart said:**
> Thank you for the information. I have not tried the make thing yet so I will give that a try, thanx again..:D
FYI: This is the best introduction to make I found. It's in a C tutorial, but easily translatable.

[http://crasseux.com/books/ctutorial/Writing-a-makefile.html#Writing%20a%20makefile](http://crasseux.com/books/ctutorial/Writing-a-makefile.html#Writing%20a%20makefile)

---

### Post by jimi_hendrix on 2009-02-21
makefiles are somewhat confusing for new programmers though (or they were for me...)

you wont need them for a while

---

### Post by snova on 2009-02-21
> **Leo Dragonheart said:**
> 1. What is the -Wall and -o, and what do they do?

**-Wall** enables a large set of warnings. -Wextra will enable more, if you like.

> 2. Does the W in -Wall have to be capitalised?

Yes.

> 3. I know chmod is change mode but what is the u+x?

User + eXecute. Makes it executable for your user, but nobody else.

> 4. Do I have to use chmod every time I run a file or once it's changed does it stay changed?

Yes, it's permanent. You're changing permissions, after all...

Though, you don't need to do that at all- GCC will make its output files executable for you.

> 5. Once I have the file compiled and chmod-ed, can I jus use ./filename to execute it?

Assuming it's in the current directory, yes.

> 6. If anyone can show me some shortcuts for not having to type this out every time I want to compile and run a file since I am studing C++ and am doing this about a hundred times a day. I would greatly appreciate it thx.
( I already know the cut & paste method...:D ).

An IDE?

make, formerly mentioned, is not a complicated tool. It simply determines, by looking at timestamps, which files need to be recompiled. A simple Makefile to compile one source file to an executable might look like this:

```

program: source.cpp
        g++ -o program source.cpp -Wall

```

On the left is the filename that will be generated, on the right the files it depends on. Then the sequence of commands to generate it, indented with tabs. (Note that this is a requirement, spaces are invalid for some reason.)

---

### Post by slavik on 2009-02-21
```

destination_file1 destination_file2 : source_file1 source_file2 source_filen
  command1 -o destination_file1
  command2 -o destination_file2

```

the indents are tabs, not spaces.

---

### Post by Krupski on 2009-02-21
> **Leo Dragonheart said:**
> Could someone answer a couple of questions for me? I have for the last few days now been using g++ -Wall "my.cpp" -o executable, chmod u+x executable, ./executable, and I don't even know what it is. I know what is does but not what it is. 

1. What is the -Wall and -o, and what do they do?

2. Does the W in -Wall have to be capitalised?

3. I know chmod is change mode but what is the u+x?

4. Do I have to use chmod every time I run a file or once it's changed does it stay changed?

5. Once I have the file compiled and chmod-ed, can I jus use ./filename to execute it?

6. If anyone can show me some shortcuts for not having to type this out every time I want to compile and run a file since I am studing C++ and am doing this about a hundred times a day. I would greatly appreciate it thx.
( I already know the cut & paste method...:D ).


(1) -Wall means "Warnings, all"
(2) That's the way the GCC was written. :)
(3a) In chmod, "u" means "user who owns the file" (i.e. YOU).
(3b) "x" means the file is executable (i.e. a program, not a plain file).
(4) The executable generated by the compiler already has the proper bits set and you do not have to chmod (or re-chmod) it.
(5) Yes.
(6) Here's what I use... feel free to copy it and modify it to your liking:


```

#!/bin/bash
#####################################################
# script to run the gcc compiler
#####################################################

FNAME=$@
FNAME=${FNAME%%.*} # isolate filename w/o extension

# test if file exists
/usr/bin/test -e [COLOR="Red"]**$FNAME.c**[/COLOR]

if [ ${?} -ne 0 ]; then
{
  /bin/echo [COLOR="Red"]**$FNAME.c**[/COLOR] not found
  exit 1
}
fi

# compile the source
# assumes "filename.c", also accepts "filename"
# outputs "filename" with executable bits set (chmod 0755)
/usr/bin/gcc -Wextra -lm -o $FNAME [COLOR="Red"]**$FNAME.c**[/COLOR]

if [ ${?} -eq 0 ]; then
{
  /bin/echo "SUCCESS!!!"
  exit 0
}
else
{
  /bin/echo "FAILED!!!!"
  exit 2
}
fi

```

Copy and paste the above into a file. Make the file "executable" by typing "chmod 0755 filename". Then, copy it to a directory in your path (such as "/usr/local/sbin").

You can find out which directories are in your path like this:

```

root@michael:/# [COLOR="Blue"]**set | grep -i path**[/COLOR]

```

Note in the script above the parts highlighted in red... they assume your source has a ".c" extension. Change it to ".cpp" or whatever you use if ".c" is not your default. 

Note also that the "-Wextra" option shows even more warnings than "-Wall".

Note the "-lm" option links math functions such as "sin" and "cos" etc... if your code uses them. It DOES NOT make your code larger if math functions are not used, so you can leave that option in place - it won't alter your code.

Good luck.

-- Roger

---

### Post by Leo Dragonheart on 2009-02-21
> **snova said:**
> **-Wall** enables a large set of warnings. -Wextra will enable more, if you like.



Yes.



User + eXecute. Makes it executable for your user, but nobody else.



Yes, it's permanent. You're changing permissions, after all...

Though, you don't need to do that at all- GCC will make its output files executable for you.



Assuming it's in the current directory, yes.



An IDE?

make, formerly mentioned, is not a complicated tool. It simply determines, by looking at timestamps, which files need to be recompiled. A simple Makefile to compile one source file to an executable might look like this:

```

program: source.cpp
        g++ -o program source.cpp -Wall

```

(Note that make requires you use tabs, not spaces)

On the left is the filename that will be generated, on the right the files it depends on. Then the sequence of commands to generate it, indented with tabs. (Note that this is a requirement, spaces are invalid for some reason.)

I just want to say that I give you 10 kudos, and an A+++ for this response....Now that is one Awesome response....Thanx...:D

---

### Post by Leo Dragonheart on 2009-02-21
> **Krupski said:**
> (1) -Wall means "Warnings, all"
(2) That's the way the GCC was written. :)
(3a) In chmod, "u" means "user who owns the file" (i.e. YOU).
(3b) "x" means the file is executable (i.e. a program, not a plain file).
(4) The executable generated by the compiler already has the proper bits set and you do not have to chmod (or re-chmod) it.
(5) Yes.
(6) Here's what I use... feel free to copy it and modify it to your liking:


```

#!/bin/bash
#####################################################
# script to run the gcc compiler
#####################################################

FNAME=$@
FNAME=${FNAME%%.*} # isolate filename w/o extension

# test if file exists
/usr/bin/test -e [COLOR="Red"]**$FNAME.c**[/COLOR]

if [ ${?} -ne 0 ]; then
{
  /bin/echo [COLOR="Red"]**$FNAME.c**[/COLOR] not found
  exit 1
}
fi

# compile the source
# assumes "filename.c", also accepts "filename"
# outputs "filename" with executable bits set (chmod 0755)
/usr/bin/gcc -Wextra -lm -o $FNAME [COLOR="Red"]**$FNAME.c**[/COLOR]

if [ ${?} -eq 0 ]; then
{
  /bin/echo "SUCCESS!!!"
  exit 0
}
else
{
  /bin/echo "FAILED!!!!"
  exit 2
}
fi

```

Copy and paste the above into a file. Make the file "executable" by typing "chmod 0755 filename". Then, copy it to a directory in your path (such as "/usr/local/sbin").

You can find out which directories are in your path like this:

```

root@michael:/# [COLOR="Blue"]**set | grep -i path**[/COLOR]

```

Note in the script above the parts highlighted in red... they assume your source has a ".c" extension. Change it to ".cpp" or whatever you use if ".c" is not your default. 

Note also that the "-Wextra" option shows even more warnings than "-Wall".

Note the "-lm" option links math functions such as "sin" and "cos" etc... if your code uses them. It DOES NOT make your code larger if math functions are not used, so you can leave that option in place - it won't alter your code.

Good luck.

-- Roger

Now here is another Awesome response A++ and 10 kudos to you also thanx for the info...

---

### Post by Leo Dragonheart on 2009-02-21
I also want to say thank you to everyone else. All the info was good and useful...

---

### Post by Krupski on 2009-02-21
> **Leo Dragonheart said:**
> Now here is another Awesome response A++ and 10 kudos to you also thanx for the info...

You are quite welcomed. Hope it's of help to you!

-- Roger

---

### Post by MadMan2k on 2009-02-21
> **Krupski said:**
> 
(6) Here's what I use... feel free to copy it and modify it to your liking:

for gods sake, don't use shell scripts for building. And dont use make either. Both are broken, since they require way too much input and dont scale well, as your application grows.
Use [scons]("http://www.scons.org/") instead.

here is the SConstruct file which was sufficient for most of my projects:
```

env = Environment()
env["CXXFLAGS"] = "-Wall -std=c++0x -O3"
# for c programs use
# env["CFLAGS"] = "-Wall"
# env["LINKFLAGS"] = "" # optional
env.Program("exe_name", Glob("*.cpp"))
# alternatively
# env.Program("exe_name", ["source1.c", "source2.c"])

```
the compile order and compiler calls are figured out by scons automatically :)

---

### Post by the_unforgiven on 2009-02-22
> **MadMan2k said:**
> for gods sake, don't use shell scripts for building. And dont use make either. Both are broken, since they require way too much input and dont scale well, as your application grows.
Use [scons]("http://www.scons.org/") instead.

Not really..
Generally, custom build scripts and make works out pretty nicely - it gives you ultimate control over how to compile things - even for small one-file projects. And they're definitely not broken.

You found it to be tedious doesn't mean others also feel the same.

---

### Post by Leo Dragonheart on 2009-02-22
Ok I have the file that Krupski suggested created, edited, pasted into /user/local/sbin. now how do I use it?

---

### Post by Krupski on 2009-02-22
> **MadMan2k said:**
> for gods sake, don't use shell scripts for building.

I don't really "build" C programs. I write tiny little utilities for my own use. Most times the SOURCE is only 2 or 3 pages long.

I don't use makefiles... I just compile the one little "source.c" file into an executable.

My script is certainly inadequate for major build projects, but for me it just simplifies the task of typing the whole command line out each time (and it saves me when I accidentally make the OUTPUT file name "source.c" and trash everything!).

For the tiny programs I do, the simple script is good enough.

And since the OP said he was typing the same command line "hundreds of time a day" I figured a script was just what he needed.

-- Roger

---

### Post by Krupski on 2009-02-22
> **Leo Dragonheart said:**
> Ok I have the file that Krupski suggested created, edited, pasted into /user/local/sbin. now how do I use it?

Oh... OK here's what you do... I'll assume you named the script "c" (yes, just the letter c... that's what mine is):

Make sure the script is executable:
```

# go to the directory your script is in
chdir /usr/local/sbin

# make it executable
chmod 0755 c

```

Now, let's say you have a C source code file names "project.c" and you want to compile it. Just type this:

```

c project.c

# -or-

c project

```

Either one is OK since the ".c" extension is assumed.

If it all worked you should see this:

```

root@michael:~/c-progs# c project.c
SUCCESS!!!
root@michael:~/c-progs# ls -laF
-rwxr-xr-x  1 root root  11298 2009-02-22 20:34 project*
-rw-r--r--  1 root root   2529 2009-02-22 14:41 project.c

```

Line by line, this is what you are seeing:

(1) Compile "project.c" using the script named "c".
(2) The source is compiled and the message "SUCCESS!!!" is returned.
(3) View the contents of your working directory.
(4) The executable file "project" is shown with a star after it (meaning it's executable).
(5) The source file "project.c" is shown.

To test or run your compiled executable, type this:

```

./project

```

The "./" is necessary to tell Linux where the executable is located. If you just type "project" it will say "command not found" (unless your working directory is in your path).

Hope this makes sense... let me know if you need any more info.

-- Roger

---

### Post by Leo Dragonheart on 2009-02-22
Ok I think I have it going but I am getting this output:

```
leo@Illuzionz:~$ cd cplusplus.com/
leo@Illuzionz:~/cplusplus.com$ com test.cpp
/tmp/ccm85Jy2.o: In function `__static_initialization_and_destruction_0(int, int)':
test.cpp:(.text+0x1d): undefined reference to `std::ios_base::Init::Init()'
test.cpp:(.text+0x22): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccm85Jy2.o: In function `main':
test.cpp:(.text+0x78): undefined reference to `std::cout'
test.cpp:(.text+0x7d): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
test.cpp:(.text+0x8b): undefined reference to `std::cin'
test.cpp:(.text+0x90): undefined reference to `std::basic_istream<char, std::char_traits<char> >::operator>>(int&)'
test.cpp:(.text+0x97): undefined reference to `std::cin'
test.cpp:(.text+0x9c): undefined reference to `std::basic_istream<char, std::char_traits<char> >::get()'
/tmp/ccm85Jy2.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status
FAILED!!!!
leo@Illuzionz:~/cplusplus.com$ 

```

---

### Post by snova on 2009-02-22
Because the script uses GCC, not G++.

Replace this line:

```
/usr/bin/gcc -Wextra -lm -o $FNAME $FNAME.c
```

With:

```
/usr/bin/g++ -Wextra -lm -o $FNAME $FNAME.c
```

G++ will link in the necessary C++ libraries automatically.

---

### Post by Leo Dragonheart on 2009-02-22
Works great thanx snova for the correction...:D

---

### Post by Krupski on 2009-02-22
> **Leo Dragonheart said:**
> Works great thanx snova for the correction...:D

Oops... sorry I didn't know you were using C++, else I would have put the proper compiler name in the script. I only use GCC.

Anyway, glad you're up and running now!

-- Roger

---

### Post by winch on 2009-02-23
The make equivalent to that build script is only two lines.

```

CXXFLAGS = -Wextra -lm

test:


```

A build system that encourages you to keep everything in a single file is doing you no favours. I have a ~250 line program split into 4 .c files. Even tiny programs can benefit from being split into multiple files.

---

### Post by monkeyking on 2009-02-23
> **MadMan2k said:**
> for gods sake, don't use shell scripts for building. And dont use make either. Both are broken, since they require way too much input and dont scale well, as your application grows.

:o
Thats quite a quite a statement,
can you elaborate?

scons uses anachronistic python syntax and api, waf was forked from scons because of the lack of scalability from scons. kde tried to do the transition to scons but ended up using cmake.


The make/shell scripting has been used for building projects for more than 30 years.

[http://www.scons.org/wiki/SconsVsOtherBuildTools#head-91cf190ca6ee2a85173873f5558889468b26e433](http://www.scons.org/wiki/SconsVsOtherBuildTools#head-91cf190ca6ee2a85173873f5558889468b26e433)
[http://markmail.org/message/jzcga3lc5srst32w](http://markmail.org/message/jzcga3lc5srst32w)
[http://lwn.net/Articles/188693/](http://lwn.net/Articles/188693/)

---

