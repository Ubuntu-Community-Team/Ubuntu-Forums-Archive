---
title: "Learning Kernighan and Ritchie on Ubuntu/gcc"
date: 2011-11-06
forum: Programming Talk
---

### Post by ask_ on 2011-11-06
Hello , 

I was planning to start Kernighan and Ritchie's C programming - 2nd Ed. I am using Ubuntu 11.10 and have the following version of gcc :-
gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) 

I wanted to know if the examples given in K and R work well in general in the gcc and Linux environment.
(I am somewhat new to Linux/Ubuntu) .

---

### Post by haqking on 2011-11-06
> **ask_ said:**
> Hello , 

I was planning to start Kernighan and Ritchie's C programming - 2nd Ed. I am using Ubuntu 11.10 and have the following version of gcc :-
gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) 

I wanted to know if the examples given in K and R work well in general in the gcc and Linux environment.
(I am somewhat new to Linux/Ubuntu) .

yes should all work fine.

make sure you have the errata and you can also obtain the solutions also.

---

### Post by Bachstelze on 2011-11-06
They don't work in general, they work always, that's what standards are for. ;)

---

### Post by ask_ on 2011-11-06
From where can one know the necessary compiler commands that sometimes are needed for execution of some of the programs.

For example there is a file copy program in section 1.5
```
#include <stdio.h>

/*K and R, page 16 , copy input to output program ; 1st version*/

main()
{
    int c;
    while((c=getchar())!=EOF)
        putchar(c);
    

}
```Now to run this in compiler we can either present a file as an input or type the text via keyboard.

For the first option I searched the net and found out that the command

```
cat filename|./a.out

```will present the file "filename" as an input to the executable file ./a.out . Can you explain what the 'cat' command does . Since I am new to Linux/Ubuntu I couldn't figure out what exactly it does.

How to learn these extras related to Ubuntu commands alongside K and R.

---

### Post by haqking on 2011-11-06
> **ask_ said:**
> From where can one know the necessary compiler commands that sometimes are needed for execution of some of the programs.

For example there is a file copy program in section 1.5
```
#include <stdio.h>

/*K and R, page 16 , copy input to output program ; 1st version*/

main()
{
    int c;
    while((c=getchar())!=EOF)
        putchar(c);
    

}
```Now to run this in compiler we can either present a file as an input or type the text via keyboard.

For the first option I searched the net and found out that the command

```
cat filename|./a.out

```will present the file "filename" as an input to the executable file ./a.out . Can you explain what the 'cat' command does . Since I am new to Linux/Ubuntu I couldn't figure out what exactly it does.

How to learn these extras related to Ubuntu commands alongside K and R.

cat means concatenate.

for all commands in linux from command line(terminal)

```
man cat
```

```
man command
```

which will display the manual page

also look at [http://linuxcommand.org](http://linuxcommand.org)

---

### Post by ask_ on 2011-11-06
> **haqking said:**
> yes should all work fine.

make sure you have the errata and you can also obtain the solutions also.

I have the second edition  , does the errata help cope with any changes Ubuntu's environment has as compared to the UNIX with respect to which the book was written ?

---

### Post by haqking on 2011-11-06
> **ask_ said:**
> I have the second edition  , does the errata help cope with any changes Ubuntu's environment has as compared to the UNIX with respect to which the book was written ?

the errata is for the errors in the book.

none of it is relevant to Ubuntu or any other distro.

as mentioned above it is a standard.

---

### Post by Bachstelze on 2011-11-06
Hmm, isn't the second edition of K&R based on ANSI C? Because what you have

```
main()
```

is not ANSI C, it sould be

```
int main(void)
```

---

### Post by haqking on 2011-11-06
> **Bachstelze said:**
> Hmm, isn't the second edition of K&R based on ANSI C? Because what you have

```
main()
```

is not ANSI C, it sould be

```
int main(void)
```

ahh yeah good point.

yeah it is ANSI C

---

### Post by ask_ on 2011-11-06
> **haqking said:**
> cat means concatenate.

for all commands in linux from command line(terminal)

```
man cat
``````
man command
```which will display the manual page

also look at [http://linuxcommand.org](http://linuxcommand.org)

Could you explain how the concatenation of the executable with the file accomplished the job. I mean how is concatenating a file to an executable different from running the executable alone.

Thanks for the help.

---

### Post by haqking on 2011-11-06
> **ask_ said:**
> Could you explain how the concatenation of the executable with the file accomplished the job. I mean how is concatenating a file to an executable different from running the executable alone.

Thanks for the help.

you answered it yourself above in previous post.

It is using the file as input, piping it to the executable

---

### Post by ask_ on 2011-11-06
> **Bachstelze said:**
> Hmm, isn't the second edition of K&R based on ANSI C? Because what you have

```
main()
```is not ANSI C, it sould be

```
int main(void)
```

The authors say in preface that the book is based on ANSI C. But they have used main() everywhere.
I think 2nd edition is latest one, released in 1988.

---

### Post by haqking on 2011-11-06
> **ask_ said:**
> The authors say in preface that the book is based on ANSI C. But they have used main() everywhere.
I think 2nd edition is latest one, released in 1988.

main() is c89 standard

int main() is c99 standard

---

### Post by ask_ on 2011-11-06
> **haqking said:**
> you answered it yourself above in previous post.

It is using the file as input, piping it to the executable

:o. 

Can we concatenate more than 1 file with the executable? If yes, how to distinguish between the 2 files via the C program.

Sorry for the digression here. If this is too advanced for me,I will return to the i/o discussion later.:)

---

### Post by haqking on 2011-11-06
> **ask_ said:**
> :o. 

Can we concatenate more than 1 file with the executable? If yes, how to distinguish between the 2 files via the C program.

Sorry for the digression here. If this is too advanced for me,I will return to the i/o discussion later.:)

rather than continue with a never ending lesson i would refer you to the book and the following as resources.

[http://www.cprogramming.com/tutorial.html](http://www.cprogramming.com/tutorial.html)

[http://www.youtube.com/user/thenewboston#grid/user/78280D6BE6F05D34](http://www.youtube.com/user/thenewboston#grid/user/78280D6BE6F05D34)

---

### Post by ask_ on 2011-11-06
Thanks for the help. I was looking for something like this.

---

### Post by haqking on 2011-11-06
> **ask_ said:**
> Thanks for the help. I was looking for something like this.

you are welcome.

The newboston series are pretty good, enjoy.

Good luck and welcome to the forums

---

### Post by Bachstelze on 2011-11-06
> **ask_ said:**
> The authors say in preface that the book is based on ANSI C. But they have used main() everywhere.
I think 2nd edition is latest one, released in 1988.

Which one is it ?

[img]http://1.bp.blogspot.com/-8ezll0vIqhI/TZGtQlQdrbI/AAAAAAAAAAM/NTxT9qK2Hg8/s1600/41jZJq0HMcL._bL160_.jpg[/img] [img]http://filedanstachambre.org/central/wp-content/uploads/2011/04/200px-Kr_c_prog_lang.jpg[/img]

You should get the first one, the second one is based on a pre-version of ANSI C and has some gotchas, main being one of them. There aren't a lot of them, and gcc can warn you when you do things that are not standard, so for one thing, always do

```
int main(void)
```

> **haqking said:**
> main() is c89 standard

int main() is c99 standard

Wrong, main returns int in both C89 and C99. If you omit it, gcc will make it default to int, but you should really make it return int explicitly if you want your code to be portable.

---

### Post by haqking on 2011-11-06
> **Bachstelze said:**
> 


Wrong, main returns int in both C89 and C99. If you omit it, gcc will make it default to int, but you should really make it return int explicitly if you want your code to be portable.

ahh ok, yeah im no C guru by any stretch ;-)

Cheers for the pointer.

edit: i guess i was confused with what i had read here [http://faq.cprogramming.com/cgi-bin/smartfaq.cgi?id=1043284376&answer=1044841143](http://faq.cprogramming.com/cgi-bin/smartfaq.cgi?id=1043284376&answer=1044841143)

---

### Post by ask_ on 2011-11-06
> **Bachstelze said:**
> Which one is it ?

[IMG]http://1.bp.blogspot.com/-8ezll0vIqhI/TZGtQlQdrbI/AAAAAAAAAAM/NTxT9qK2Hg8/s1600/41jZJq0HMcL._bL160_.jpg[/IMG] [IMG]http://filedanstachambre.org/central/wp-content/uploads/2011/04/200px-Kr_c_prog_lang.jpg[/IMG]

You should get the first one, the second one is based on a pre-version of ANSI C and has some gotchas, main being one of them. There aren't a lot of them, and gcc can warn you when you do things that are not standard, so for one thing, always do

```
int main(void)
```.

Oops. My book is Indian edition and has 272 pages . It is all blue in color. And it doesn't have ANSI C stamped on it as such.
But I checked a few pages of it from amazon's preview and it does seem to be the one after ANSI was released.

But in my book everywhere they have used main() and not int main(void). What's more my gcc is also not giving any warnings for main() . 

My gcc version is
```
Using built-in specs.
COLLECT_GCC=gcc
COLLECT_LTO_WRAPPER=/usr/lib/gcc/i686-linux-gnu/4.6.1/lto-wrapper
Target: i686-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.6.1-9ubuntu3' --with-bugurl=file:///usr/share/doc/gcc-4.6/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++,go --prefix=/usr --program-suffix=-4.6 --enable-shared --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.6 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-plugin --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=i686-linux-gnu --host=i686-linux-gnu --target=i686-linux-gnu
Thread model: posix
gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) 
```

---

### Post by Bachstelze on 2011-11-06
Oh well, never mind that either way. Just proceed with the book and compile your programs like that:

```
gcc -ansi -pedantic -Wall -Wextra -o output source.c
```

It will compile [font="monospace"]source.c[/font], yielding executable [font=monospace]output[/font], which you can run with

```
./output
```

of course you can change the name of the input and output files. With options -pedantic -Wall -Wextra, you will sometimes see a lot of warnings. They are here for a reason, so you should pay attention to them, and try to write code that compiles without warnings. Don't hesitate to ask here if you have questions.

---

### Post by ask_ on 2011-11-07
Thanks to both of you - haqking and Bachstelze. 

:D

---

### Post by Arndt on 2011-11-07
> **ask_ said:**
> :o. 

Can we concatenate more than 1 file with the executable? If yes, how to distinguish between the 2 files via the C program.

Sorry for the digression here. If this is too advanced for me,I will return to the i/o discussion later.:)

There is a crucial character in the command, namely the vertical bar |.

In Unix, it is used for "piping" data from one program to another, in this case from the input file to your program. It is one of the fundamental building blocks in Unix. If you google for something like "Unix tutorial pipe", you ought to find something useful.

Someone else mentioned the "man cat" command for looking at the documentation for the program 'cat'. For programs, this is often the best way. For general concepts, this doesn't always work so well. "man pipe" exists, but will get you the details of the system call which creates a pipe, which is no use at all for a beginner. This manual page refers to "man 7 pipe", which is better, but still very terse. "man bash" has the info about pipes somewhere in there, but is quite large, and assumes you know what a pipe is already.

---

### Post by ask_ on 2011-11-07
> **Arndt said:**
> There is a crucial character in the command, namely the vertical bar |.

In Unix, it is used for "piping" data from one program to another, in this case from the input file to your program. It is one of the fundamental building blocks in Unix. If you google for something like "Unix tutorial pipe", you ought to find something useful.



Thanks, Arndt . I found one website after googling , [http://www.ee.surrey.ac.uk/Teaching/Unix/](http://www.ee.surrey.ac.uk/Teaching/Unix/) . It seems good .

You addressed one of my problems when you said 'man cat' command does not explain the concept of piping .  I will look into the UNIX tutorials for the concepts for sure. 


I have one query though .Do , the UNIX commands work in Ubuntu ? I found that most of the commands of the UNIX tutorial work in Ubuntu as well. 

K and R says that to execute a program file 'a.out' we type 'a.out' in UNIX  terminal.In Ubuntu we have to type './a.out'  to run it. This was one difference I found.

---

### Post by haqking on 2011-11-07
> **ask_ said:**
> Thanks, Arndt . I found one website after googling , [http://www.ee.surrey.ac.uk/Teaching/Unix/](http://www.ee.surrey.ac.uk/Teaching/Unix/) . It seems good .

You addressed one of my problems when you said 'man cat' command does not explain the concept of piping .  I will look into the UNIX tutorials for the concepts for sure. 


I have one query though .Do , the UNIX commands work in Ubuntu ? I found that most of the commands of the UNIX tutorial work in Ubuntu as well. 

K and R says that to execute a program file 'a.out' we type 'a.out' in UNIX  terminal.In Ubuntu we have to type './a.out'  to run it. This was one difference I found.

yes most commands work across Unix/Linux.  There will be some differences here and there, hence the use of man, --info, --help etc.

Also

apropos

which allows you to search for a command without knowing what it is called, example

apropos copy

will bring a list of commands that may do or involve copying leading to the copy command (cp)

---

### Post by Arndt on 2011-11-07
> **ask_ said:**
> Thanks, Arndt . I found one website after googling , [http://www.ee.surrey.ac.uk/Teaching/Unix/](http://www.ee.surrey.ac.uk/Teaching/Unix/) . It seems good .

You addressed one of my problems when you said 'man cat' command does not explain the concept of piping .  I will look into the UNIX tutorials for the concepts for sure. 


I have one query though .Do , the UNIX commands work in Ubuntu ? I found that most of the commands of the UNIX tutorial work in Ubuntu as well. 

K and R says that to execute a program file 'a.out' we type 'a.out' in UNIX  terminal.In Ubuntu we have to type './a.out'  to run it. This was one difference I found.

If you have the current directory in your PATH variable (i.e., a period "."), then you don't need to prefix programs with "./". This was common practice once, but nowadays, people are advised to avoid practices that can compromise security, and doing this carries certain risks (if you cd to someone else's directory and enter a command that is not otherwise recognized, you may inadvertently run something that for example erases your files or copies your mailbox).

---

### Post by gnometorule on 2011-11-07
Back to the original question, do they all compile...

The answer is: almost all. You seem to just begin, but the code in the last chapter will not always compile. In particular, the last chapter implements a directory walk where K/R present a then-good solution which defines structures that have after been made part of the kernel, and use certain commands in ways they should no longer be used in this context. So that example you should read ( still interesting), but skip the implementation (you'll see dirent structures). I forgot if the other unix examples worked, but remember some did. I also think there is a minor logic error in the very last .c file, but it will compile as is. Just to keep in mind when you begin with that chapter. It's still the best book to learn C from.

---

### Post by ask_ on 2011-11-07
Thanks, gnometorule . I tried to run a version of the file-copy program given in the last chapter just out of curiosity. And like you said it didn't run.  I will keep in mind what you said about the chapter 8 when I reach it.

Thanks again to everyone for taking time out for this discussion.All your tips were & will be helpful . :cheers:

---

