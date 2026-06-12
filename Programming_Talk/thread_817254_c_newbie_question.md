---
title: "c newbie question"
date: 2008-06-03
forum: Programming Talk
---

### Post by cmay on 2008-06-03
hi.
i am currently following the gnu c tutorial found link in the sticky treadh. i have problems whit getting this code accepted.
it says implicit declariton of builtin function exit 
i was up all night drinking lots of coffe and reading trough this tutorial 
but i went to bed at 4 night time since i could not compile the examples using the exit funktion. what did i miss? 

thanks for reading this. 
```


/* ************************************************************************
 * aha.c                                                                  *
 * license : restricted by means of impossible usage                      *                                           * 
 * purpose : unknown                                                      *
 *  author : completly unknown and absolute unreachable by phone or email * 
 * *************************************************************************/

#include <stdio.h>
int main(int argc, char** argv)
{
if(argc != 2)
{
printf(" usage : makes [filename][type] default .txt unless else specified  \n");
return 1; /* why implicit declaretion of exit(1); ? */
}
else
printf("MESSAGE:look for the file you made in the ./ directory\n");
FILE *file_ptr=fopen(argv[1],"w");
fprintf(file_ptr,"the file is saved as %s \n is that not cool or what :)\n",argv[1]);
fclose(file_ptr); /* how to print to printer ? */
return 0;
}
```
ps
it was very late and i was very tired. i just posted the last code in question whit the problems i had commented out.

---

### Post by LaRoza on 2008-06-03
Add:

```

#include <stdlib.h>

```

(At the top with stdio.h)

---

### Post by cmay on 2008-06-03
thanks for the reply.
i dont seem to renember the stdlib was included in the exmples that i found in the tutorial. 
i have printed the whole thing out
page by page i could have missed one or two.
anyway thank you.

---

### Post by Martin Witte on 2008-06-03
How do you compile? I saved your code as test.cpp, then ran 'gcc test.c' in a terminal without problems. The created program (it is by default named 'a.out') runs fine

---

### Post by cmay on 2008-06-03
i use geany since i know that its supposed to give the -wall option. else if i use nano i use gcc  -o myfile ./myfile.c
i wrote this littel testprogram to see if i could begin understand the terminal programs structure 
and as well the file part of the tutorial is where  i am most focused right now.

---

### Post by LaRoza on 2008-06-03
> **Martin Witte said:**
> How do you compile? I saved your code as test.cpp, then ran 'gcc test.c' in a terminal without problems. The created program (it is by default named 'a.out') runs fine

That shouldn't compile.

---

### Post by Martin Witte on 2008-06-03
> **LaRoza said:**
> That shouldn't compile.
here you are
```
martin@toshibap200:~$ cat test.c
/* ************************************************************************
 * aha.c                                                                  *
 * license : restricted by means of impossible usage                      *                                           * 
 * purpose : unknown                                                      *
 *  author : completly unknown and absolute unreachable by phone or email * 
 * *************************************************************************/

#include <stdio.h>
int main(int argc, char** argv)
{
if(argc != 2)
{
printf(" usage : makes [filename][type] default .txt unless else specified  \n");
return 1; /* why implicit declaretion of exit(1); ? */
}
else
printf("MESSAGE:look for the file you made in the ./ directory\n");
FILE *file_ptr=fopen(argv[1],"w");
fprintf(file_ptr,"the file is saved as %s \n is that not cool or what :)\n",argv[1]);
fclose(file_ptr); /* how to print to printer ? */
return 0;
}
martin@toshibap200:~$ gcc test.c -Wall
martin@toshibap200:~$ ls -l a.out
-rwxr-xr-x 1 martin martin 6935 2008-06-03 20:15 a.out
martin@toshibap200:~$ date
Tue Jun  3 20:15:26 CEST 2008
martin@toshibap200:~$ 

```

---

### Post by nvteighen on 2008-06-03
> **LaRoza said:**
> That shouldn't compile.
Yes, it will compile because in the code he's giving he is **not using** exit(1) but replaced it with "return 1" in main().

@OP: By the way, if you want to print to printer (as you've placed in a comment), you'll get some problems. Either you write your own driver or you better use something external...

---

### Post by Bichromat on 2008-06-03
LaRoza is just pointing to an error in Martin Witte's post. He says he saved the file as test**.cpp** and then compiled test**.c**

---

### Post by LaRoza on 2008-06-03
> **Bichromat said:**
> LaRoza is just pointing to an error in Martin Witte's post. He says he saved the file as test**.cpp** and then compiled test**.c**

Yes, I think I should have pointed that out in my post (was doing something else at the time of writing it)

---

### Post by Martin Witte on 2008-06-03
> **Bichromat said:**
> LaRoza is just pointing to an error in Martin Witte's post. He says he saved the file as test**.cpp** and then compiled test**.c**
Touche, I usually write C++ ....

---

### Post by LaRoza on 2008-06-03
> **Martin Witte said:**
> Touche, I usually write C++ ....

For such situations on the internet, I have my home full of files ready to use:
```

~$ls p*
p.asm  p.bf  p.c  p.ch  p.cpp  p.cs  p.d  p.exe  p.f  p.hi  p.hs  p.js  p.o  p.php  p.pl  p.py  p.sh  p.text
```

---

### Post by cmay on 2008-06-03
> @OP: By the way, if you want to print to printer (as you've placed in a comment), you'll get some problems. Either you write your own driver or you better use something external...
thanks for the info that may come in handy some day.

i did a littel introduktion to programmering in turbo pascal 7 two years ago. 
from the top of my head it was something like writeln(lpt1,'print to serial com');
so i must ask the difference in c and pascal on both linux and windows to understand.
 i dont need to use the printer right now as you may already have sort of guessed but nice to know anyway
 since it seems a bit different working on linux whit files.
i forgot all about pascal as of this moment i was just using it as a stepping stone to learn c.

---

### Post by Joeb454 on 2008-06-03
That's a lot of p's ;)

Though I guess it's better than really long filenames

---

### Post by LaRoza on 2008-06-03
> **Joeb454 said:**
> That's a lot of p's ;)

Though I guess it's better than really long filenames

It stands for "practice". They are just temp programs and are used for testing and samples.

---

### Post by nvteighen on 2008-06-03
> **cmay said:**
> thanks for the info that may come in handy some day.

i did a littel introduktion to programmering in turbo pascal 7 two years ago. 
from the top of my head it was something like writeln(lpt1,'print to serial com');
so i must ask the difference in c and pascal on both linux and windows to understand.
 i dont need to use the printer right now as you may already have sort of guessed but nice to know anyway
 since it seems a bit different working on linux whit files.
i forgot all about pascal as of this moment i was just using it as a stepping stone to learn c.
The easiest way would be to make your program call the "lpr" command, which prints some text to your default printer. There's an example in the same GNU C tutorial (though in the ["Building a library"]("http://crasseux.com/books/ctutorial/Building-a-library.html#Building%20a%20library") section...!).

More flexible, more interesting and that has introduced me in the world of third-party libraries (and learning how to read some API documentation) is to implement printing using CUPS. Maybe you don't want to learn that now, but at least know that it exists.

---

### Post by cmay on 2008-06-03
> The easiest way would be to make your program call the "lpr" command, which prints some text to your default printer. There's an example in the same GNU C tutorial (though in the "Building a library" section...!).

More flexible, more interesting and that has introduced me in the world of third-party libraries (and learning how to read some API documentation) is to implement printing using CUPS. Maybe you don't want to learn that now, but at least know that it exists.

thank you .
this sounds very interesting .
i will wanna look at the cups when i get more the feel of c programmering.
i also thought about yeasterday writing the 
aha.c program that i could maybe do something like system("lpr1");
but it was 4 a clock in the morning and the 
missing stdlib left me too many questions towards the exit(1); function.
right now i just play around whit it to get  to learn the language .
however this information you gave me is really worth something. 
thank you.

---

