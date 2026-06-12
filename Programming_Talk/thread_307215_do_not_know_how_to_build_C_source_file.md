---
title: "do not know how to build C source file"
date: 2006-11-26
forum: Programming Talk
---

### Post by evgininanir on 2006-11-26
hello everybody i am a new user of ubuntu...
and i am trying to learn c language.
i installed ubuntu 6.10 and then kDevelopment 

THERE WAS SOME PROBLEMS AND i solve it with these people's answers........
------>shining and red_Marvin...thank you guys again...

i want to learn C programming language.
but as in Windows we write a hello.c program and we can build it with something like "run" or "build " or something else.....

but in ubuntu with Kdevelopment ide i could not compile and could not see the hello.c program's result...

my question is how can i compile and see the result of my simple hell.c program's result like has been it MS-Dos.....thanks...
this is the code of my simple hello.c 
#include<iostream.h>
main()
{
printf("Hello Evgin !");

return 0;
}


help i am going crazy and i want learn using ubuntu .....

---

### Post by meng on 2006-11-26
Make sure you have gcc and associated files installed by doing this:
sudo aptitude install build-essential

Subsequently, you can compile a program by doing this:
gcc hello.c
(the file will be a.out, there are other options with gcc such as specifying another output file name)

---

### Post by evgininanir on 2006-11-26
okey but if you excuse me ....
my source file is at /home/oem/desktop/new folder/hello.c

how can i use gcc ?

thank you meng

---

### Post by meng on 2006-11-26
Open a terminal:
cd desktop/new\ folder/
gcc hello.c

This assumes you have installed build-essential as stated in my earlier post.

---

### Post by evgininanir on 2006-11-26
thank you again meng....
i did and it worked..
now i have another problem.
when i make this ------>gcc hello.c it produced a.out as you said.

and now how can i see what a.out do like has been at ms-dos 
or what i have to do to see what this a.out does?.....

---

### Post by rbalfour on 2006-11-26
> **evgininanir said:**
> hello everybody i am a new user of ubuntu...
#include<iostream.h>
main()
{
printf("Hello Evgin !");

return 0;
}



iostream is for windows.

Here is a proper Hello.c test for you.

```

#include <stdio.h>

int
main (void)
{
        printf ("Hello, Ubuntu\n");
        return 0;
}


```

then 

# gcc -Wall hello.c -o hello

Should compile a file called hello for you to run.

Enjoy.

A good eBook to better understand gcc
"An Intro to GCC" by Brian Gough ([http://www.network-theory.co.uk/docs/gccintro/](http://www.network-theory.co.uk/docs/gccintro/))

---

### Post by meng on 2006-11-26
Or alternatively, just type
./a.out
(I can't remember if you explicitly need to make the file executable, if you do need to do this:
chmod a+x a.out

)


Ultimately, you'll want to use the -o option, then
./hello2
(or whatever the filename is)

---

### Post by evgininanir on 2006-11-26
thanks both of you....

i have another question.....
i want to use kdevelopment envoirement to write and to compile  and run all c program but how can i do that i do not know....

for e.g.
i have a file named hello.c 
the code in this file 

#include <stdio.h>
main()
{
printf("HELlo..\n");
return 0;
}

how can i do that in KDevelop:C\C++ ....thanks

---

### Post by pstreck on 2006-11-26
> **rbalfour said:**
> iostream is for windows.

Here is a proper Hello.c test for you.

```

#include <stdio.h>

int
main (void)
{
        printf ("Hello, Ubuntu\n");
        return 0;
}


```

then 

# gcc -Wall hello.c -o hello

Should compile a file called hello for you to run.

Enjoy.

A good eBook to better understand gcc
"An Intro to GCC" by Brian Gough ([http://www.network-theory.co.uk/docs/gccintro/](http://www.network-theory.co.uk/docs/gccintro/))

Just wanted to clarify something here, iostream.h is part of the C++ language standard, and stdio.h is part of the C programming language. If you really want to dig into C then I would recommend you get the book "The Programming Language" by Brian Kernighan & Dennis Ritchie. (Those are the guys who invented C btw)

---

### Post by rbalfour on 2006-11-26
> **pstreck said:**
> Just wanted to clarify something here, iostream.h is part of the C++ language standard, and stdio.h is part of the C programming language. If you really want to dig into C then I would recommend you get the book "The Programming Language" by Brian Kernighan & Dennis Ritchie. (Those are the guys who invented C btw)

The C Programming Language -> [http://cm.bell-labs.com/cm/cs/cbook/](http://cm.bell-labs.com/cm/cs/cbook/)

Just to also add.
Usually filename.c are C language and filename.cpp are C++ language.

---

### Post by evgininanir on 2006-11-26
i do understand you but my problem is is there a way to buid the simple hello.c source file and see what it produces ,using KDevelop:C/C++ platform ?

---

### Post by po0f on 2006-11-26
evgininanir,

Just use Gedit and the command-line for all of your early development.  Kdevelop will just be another thing to learn on top of C.

---

### Post by junglepeanut on 2006-11-27
I agree with the others, that you should just work in a command line environment for now, but I also know some instructors are specific in how they are doing things or some people are stuck in microsofts point and click method. So I will point in a direction and then say check more with google like I did as I prefer creating my own makefile and the like. A nice syntax highlighter is very helpful though. 

kile, gedit, vim, emacs many many many more out there, eclipse etc etc

Here is the most relevant thing I thought to start your reading (from google) if you have to use kdevelop

[http://www.kdevelop.org/mediawiki/index.php/FAQ](http://www.kdevelop.org/mediawiki/index.php/FAQ)

---

