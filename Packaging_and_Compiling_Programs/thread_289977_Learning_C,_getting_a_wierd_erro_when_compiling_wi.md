---
title: "Learning C, getting a wierd erro when compiling with gcc"
date: 2006-10-31
forum: Packaging and Compiling Programs
---

### Post by xboxbman on 2006-10-31
I'm just learning C.  I made a simple prog called test.C, here it is:

#include <stdio.h>
int main(int argc, char** argv)
{
	printf("Hello test\n");
	return 0;
}

this is the error I get

bman@wherewulf:~$ gcc test.C
/tmp/ccKH5JHY.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

my friend is a programmer, and says he has no clue about this.  Any help would be appreciated for this future 733t programmer (yes, I'm a big geek!)

---

### Post by Jussi Kukkonen on 2006-10-31
Well, that error usually means you tried to link C++ code with gcc (a C compiler). I'm a little baffled why that would happen with your code... 

Have you installed the *build-essential* package?

---

### Post by xboxbman on 2006-10-31
yes I have

---

### Post by jhaitas on 2006-10-31
just out of curiosity... why the capital 'C' in the source code file extension?

i tried it out and this is your problem... you named the source file 'test.C'  and not 'test.c' - emphasis being on the capital 'C'... if you simply rename the file to 'test.c' with a lower-case c your problem will be resolved...

```
mv test.C test.c
```

now your code will compile...

---

### Post by po0f on 2006-10-31
xboxbman,

Just to elaborate on the previous post, older C++ programs were suffixed with .C as opposed to .c.  I'm guessing that's the cause of the __gxx_personality_v0 error (gxx meaning g++).

---

### Post by jhaitas on 2006-10-31
and that explains why this error occurs...

i guess the capital 'C' extension for C++ files was before my time... i've always named my C++ with the '.cpp' extension...

---

### Post by xboxbman on 2006-10-31
no more error, but nothing happens.  The learning C book I have is assuming you're working on a windows machine, so it have no info on running these in linux.  I type "gcc test.c", I hear the hardrive spin for a second, then nothing.  I get the same effect just hitting enter.  sorry to hassle you guys with these low level, questions, but I gotta start somewhere.

---

### Post by jhaitas on 2006-10-31
that means it compiled with no problems...
in that same directory you should now have a file called 'a.out'....
to execute the file issue this command at the terminal:
```
./a.out
```
the most important part of that being the './'
don't forget it... that tells the shell where the file is located...

to be clear this is what you need to do assuming you are at the directory containing your source code

```
gcc test.c
./a.out
```

let us know how it goes

---

### Post by xboxbman on 2006-10-31
hurray! my first program, lame as it is, works.  Next stop, world domination! Mwahahahaha!!!  But seriously, thanks for the help.  I know it was silly little questions, but one thing I've learned is that a moment of stupidity is better than a lifetime of ignorance.

Thanks again jhaitas

---

### Post by jhaitas on 2006-10-31
i remember when i was in the same place as you...

let me know if you have any more issues...

one side note... if you want to give your executable a meaningful name - use the '-o' argument in the gcc command:

```
gcc test.c -o test.out
./test.out
```

see how that works for you...
fyi: one of the best resources are the manpages...
to read up on gcc you can issue the command:
```
man gcc
```

you will get a lot of useful information there... furthermore the man command can be used for other commands like 'ls' or 'lsof'... any command you use at the terminal should have associated manpages... ('man' being short for 'manual')

---

### Post by rahaman on 2006-11-21
> **jhaitas said:**
> and that explains why this error occurs...

i guess the capital 'C' extension for C++ files was before my time... i've always named my C++ with the '.cpp' extension...
[Mr.jhaitas]("http://ubuntuforums.org/member.php?u=152865") . there is no difference between C and c in the extensions of the c file. if you give the C as extension it will compile with out error.

---

### Post by po0f on 2006-11-21
rahaman,

You're [wrong](http://en.wikibooks.org/wiki/C++_Programming/Source_File), please look it up before posting.

---

### Post by hod139 on 2006-11-21
PoOf, you are correct but shouldn't cite wikipedia.  You should cite [gcc:]("http://gcc.gnu.org/onlinedocs/gcc-4.1.1/gcc/Overall-Options.html#Overall-Options")


For those that don't want to read the link, here are the relavant extensions, my emphasis added:
> 
**file.c**
--> C source code which must be preprocessed.       
file.i
-->     C source code which should not be preprocessed.       
file.ii
-->     C++ source code which should not be preprocessed.       
file.h
-->     C, C++, Objective-C or Objective-C++ header file to be turned into a precompiled header.       
file.cc
file.cp
file.cxx
file.cpp
file.CPP
file.c++[B]
file.C
       [/B] --> C++ source code which must be preprocessed.  Note that in `.cxx', the last two letters must both be literally `x'.  Likewise, `.C' refers to a literal capital C.

---

### Post by po0f on 2006-11-21
hod139,

I know, I was being lazy and didn't feel like searching through the man page though.  ;)

---

