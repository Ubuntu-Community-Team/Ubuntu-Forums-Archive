---
title: "c program problem"
date: 2007-02-02
forum: Programming Talk
---

### Post by sauravbhaumik on 2007-02-02
I have installed Ajunta IDE for c++ for gnome. And I have written a program of which the source code :
```
#include<stdio.h>
void main (void)
{int i,j;
printf("\ni=?");scanf(%d,&i);
printf("\nj=?");scanf(%d,&j);
printf("\nsum is %d",i+j);
getch();
}
```

And I save the file with the name ```
test.c
```
Then I go to the terminal and then, to the location where I saved the file and type 
```
gcc test.c
```

It gives
```
test.c: In function ‘main’:
test.c:4: error: expected expression before ‘%’ token
test.c:5: error: expected expression before ‘%’ token
test.c:3: warning: return type of ‘main’ is not ‘int’

```

But I remember I have compiled successfully such programs in windows XP turbo C++ compiler. Kindly tell me what happened in ubuntu.

---

### Post by LostShootingStar on 2007-02-02
%d needs to be in quotes.

---

### Post by sauravbhaumik on 2007-02-02
> **LostShootingStar said:**
> %d needs to be in quotes.

Sorry, a careless mistake. I corrected and it gives, then :
```
test.c: In function ‘main’:
test.c:3: warning: return type of ‘main’ is not ‘int’
/tmp/ccWeUTYf.o: In function `main':
test.c:(.text+0x69): undefined reference to `getch'
collect2: ld returned 1 exit status

```
Would you kindly explain?

---

### Post by LostShootingStar on 2007-02-02
I think the function is getc() not getch (that might be c++? i forget). and the warning about main not returning an int is a warning. main should always be int main().

anyway...fgetc() would probably be better than getc() anyway

---

### Post by sauravbhaumik on 2007-02-02
> **LostShootingStar said:**
> I think the function is getc() not getch (that might be c++? i forget). and the warning about main not returning an int is a warning. main should always be int main().

anyway...fgetc() would probably be better than getc() anyway
neither getc() nor fgetc() worked. It says ```
too few arguments to function 'fgetc'
```

---

### Post by sauravbhaumik on 2007-02-02
Would you kindly compile it in your machine:
```
#include <stdio.h>

int main()
{
 int i,j;
 i=7;j=9;
  printf("%d",i+j);
  getch();
} 
```

---

### Post by LostShootingStar on 2007-02-02
maybe it will help if you explain what your trying to do....fgetc() requires a file handle as input

i assume your just trying to pause the program or something until a user hits a button?

---

### Post by sauravbhaumik on 2007-02-02
I've installed c++ in linux and I try to ensure that it has been installed properly and it runs c programs. So, I want to run a very very simple c program in it. This is what I want.
Now, kindly explain me what to do.

---

### Post by lnostdal on 2007-02-02
```

#include <stdio.h>


int main(int argc, char **argv)
{
  int a, b;
  printf("a: "); scanf("%d", &a); getchar();
  printf("b: "); scanf("%d", &b); getchar();
  printf("%d + %d = %d\n", a, b, a + b);
  getchar();
  return(0);
}


/*
 lars@ibmr52:~/programming/c$ gcc -Wall -g test.c -o test
 lars@ibmr52:~/programming/c$ ./test
 a: 1234
 b: 4321
 1234 + 4321 = 5555
*/

```

edit:
scanf does not read the newline from the input-buffer .. i've therefore added the getchars to "dump" them

also note that getch isn't part of "standard C" .. you'll find it in external libraries such as ncurses for instance .. i also think i remember an getch from the old borland compilers under DOS

---

### Post by sauravbhaumik on 2007-02-03
but the matter is, when i use the gcc command, the terminal gives nothing.
I first type ```
saurav@saurav-desktop:~$ gcc test.c

```
then it gives```
saurav@saurav-desktop:~$ 

```

---

### Post by lnostdal on 2007-02-03
> **sauravbhaumik said:**
> but the matter is, when i use the gcc command, the terminal gives nothing.
I first type ```
saurav@saurav-desktop:~$ gcc test.c

```
then it gives```
saurav@saurav-desktop:~$ 

```

yes? that means all is well .. it has created a file a.out with the compiled object file for you to execute .. you specify the name of the output file with -o as i've done in my example above ..    just try out what i have pasted above ....

---

### Post by lnostdal on 2007-02-03
also see [http://www.network-theory.co.uk/docs/gccintro/](http://www.network-theory.co.uk/docs/gccintro/) and [http://gcc.gnu.org/onlinedocs/gcc/](http://gcc.gnu.org/onlinedocs/gcc/)

---

### Post by sauravbhaumik on 2007-02-03
great it worked!
but what is the meaning of -Wall, the -o, and at last, of the "./<filename>"?
Would you kindly explain?

---

### Post by lnostdal on 2007-02-03
[http://gcc.gnu.org/onlinedocs/gcc/Warning-Options.html#Warning-Options](http://gcc.gnu.org/onlinedocs/gcc/Warning-Options.html#Warning-Options)

[http://gcc.gnu.org/onlinedocs/gcc/Overall-Options.html#Overall-Options](http://gcc.gnu.org/onlinedocs/gcc/Overall-Options.html#Overall-Options)
> 
-o file
    Place output in file file. This applies regardless to whatever sort of output is being produced, whether it be an executable file, an object file, an assembler file or preprocessed C code.

    If -o is not specified, the default is to put an executable file in a.out, the object file for source.suffix in source.o, its assembler file in source.s, a precompiled header file in source.suffix.gch, and all preprocessed C source on standard output. 

./test means something like "execute the file test in the current directory"

---

### Post by ghandi69_ on 2007-02-03
Ok, so to summarize here. First things, install the c 'compliler'... by typing..
 
 sudo apt-get install build-essential 

this will give you 'gcc' and 'g++' gcc being the c compiler, and g++ being a c++ compiler. Note there are no graphical user interfaces for these, you don't open and run them.. you just send them code. So, lets practice....
 
 sudo nano HelloWorld.c
 
 (Enter you c program competely into this file, save it and exit)
 
 then to use to gcc to compile the code type
 
 gcc -o Helloworld.exe Helloworld.c 

"HelloWorld.exe", can be anything you want. It is what your are naming the executable file gcc creates... It could have been written "gcc -o RandomCrap Helloworld.c" and still work. The 2nd part. HelloWorld.c has to be the same as the .c file is named.
 
 Then to run your porgram using the first example.. you would type
 
 ./Helloworld.exe
 

 
 I hope this helps!!

---

### Post by ghandi69_ on 2007-02-03
Sorry about the the generic post, I just copied from a post I used a couple days ago.

---

### Post by burmanabhay88 on 2007-02-03
hi.. i'm new to ubuntu too. and i face the same problem as u. I use Ajunta IDE for editing C files, and then GCC for compiling. You were using Turbo C compiler in Win Xp, weren't u? Well the thing is GCC does not have the same standard libraries as Turbo C. It does not have Stdio.h, conio.h, stdlib.h, etc. I have a suggestion. Copy the include files from Turbo C compiler(all header files(.h extensions)) into any folder in Linux. And then instead of typing #include<stdio.h>, include the file, by giving the entire location of the file. This should do the job. If it works, please do tell me, and post the new c program for other people's reference
Regards.

---

### Post by sauravbhaumik on 2007-02-03
> **burmanabhay88 said:**
> hi.. i'm new to ubuntu too. and i face the same problem as u. I use Ajunta IDE for editing C files, and then GCC for compiling. You were using Turbo C compiler in Win Xp, weren't u? Well the thing is GCC does not have the same standard libraries as Turbo C. It does not have Stdio.h, conio.h, stdlib.h, etc. I have a suggestion. Copy the include files from Turbo C compiler(all header files(.h extensions)) into any folder in Linux. And then instead of typing #include<stdio.h>, include the file, by giving the entire location of the file. This should do the job. If it works, please do tell me, and post the new c program for other people's reference
Regards.

No. The command is not GCC, but it is gcc.
And you need to save the file with an extension .c, not .C, if you want to use stdio.h
The header file is stdio.h, be cautious about case.
I give you the simple program I am testing now:```
#include<stdio.h>
int main()
{int i;
printf("give an integer");scanf("%d",&i);getchar();
printf("\nthe next number is %d",i+1);
getchar();
return(0);
}
```

Save it in your home folder with the name ```
next.c
```
Open up terminal and go to the location where you saved it; make sure that it is there with the help of ls command.
Type```
gcc -Wall -g next.c -o next
```
Actually, if you saved it, instead with the name xxx.c, then the command would have been```
gcc -Wall -g xxx.c -o xxx
```
Press enter.
It would give nothing great, and then understand that you are almost done.
Then type```
./next
```
and press enter.
If it were xxx.c, the command would have been```
./xxx
```
Understand: the command is, dot slash filename(without extension)

**************************************
Am I wrong anywhere? Experts, please correct me where I am wrong.

---

### Post by lnostdal on 2007-02-03
burmanabhay88:
err .. stdio.h and stdlib.h is part of standard C and thus part of gcc in any linux distro .. and conio.h is replaced by the far superior ncurses library..

copying headers in any way is _not_ a solution.. not even if you're copying them from a similar system using the exact same compiler..  not even between two ubuntu systems.. and especially not when it "happens to work"

headers belong in companionship with the libraries which they describe and you get these properly downloaded, installed and configured by using apt-get or synaptic the same way you install any software on ubuntu

please try to learn to do things the proper way..  read the links i posted above about how to use the gcc compiler and get a book about C .. "The C Programming Language" is a good book ..   trying to work around this stuff in this manner will lead to a lot of problems and a lot of wasted time for everyone

instead, ask if you have any problems adjusting to the "linux way" of doing things -- people are usually willing to help if you work with them and the tools instead of against them

---

### Post by burmanabhay88 on 2007-02-03
wait.....I'm not able to include conio.h,etc. in my gcc compilation.
will u please tell me which files do i need to include for the following functions to work.. 
clrscr(),rand(),srand(),pow(),exp, etc.

u were saying something about the ncurses library. I'm sorry, but could you help me out in figuring things in Linux.
I was using Turbo C compiler in Win Xp.

If possible can you please tell me if there is some place where i can get some kind of info on the various library functions(not part of standard C compilation) available in GCC...
thanks...

---

### Post by runningwithscissors on 2007-02-03
> **burmanabhay88 said:**
> wait.....I'm not able to include conio.h,etc. in my gcc compilation.
will u please tell me which files do i need to include for the following functions to work.. 
> clrscr(),
dunno. Possibly ncurses.h, but the equivalent function won't be called clrscr(). Try clear().

> rand(),srand(),
stdlib.h

> pow(),exp,
math.h

> If possible can you please tell me if there is some place where i can get some kind of info on the various library functions(not part of standard C compilation) available in GCC...
thanks...
man pages.
Whatever function or header you want info on, just type:
$ man <keyword>
and you'll get it.

---

### Post by lnostdal on 2007-02-03
> **burmanabhay88 said:**
> wait.....I'm not able to include conio.h,etc. in my gcc compilation.
will u please tell me which files do i need to include for the following functions to work.. 
clrscr(),rand(),srand(),pow(),exp, etc.

u were saying something about the ncurses library. I'm sorry, but could you help me out in figuring things in Linux.
I was using Turbo C compiler in Win Xp.

If possible can you please tell me if there is some place where i can get some kind of info on the various library functions(not part of standard C compilation) available in GCC...
thanks...

see:
[http://www.gnu.org/software/libc/manual/html_node/index.html](http://www.gnu.org/software/libc/manual/html_node/index.html)
..and..
[http://www.cppreference.com/](http://www.cppreference.com/)

linux also has man-pages for these things .. to download and install them under ubuntu type:

```
sudo aptitude install manpages-dev glibc-doc
```

if i now type:

```
apropos rand
```

i get a list of man-pages with the title "rand" in them .. one of the mentioned ones are:

```
rand (3)             - pseudo-random number generator
```

..which means i can type:

```
man 3 rand
```

..to see the man-page about rand .. you'll also find srand(),pow(),exp() .. the man-pages mention which header you are to include for all of these

now, about clrscr() and such.. to do that kind of work under linux you want a library called ncurses:

```
sudo aptitude search ncurses
```
```
sudo aptitude install libncurses5-dev
```

..and you can now type man ncurses and read up on that .. for instance; you can type "apropos clear" ..  then type "man 3ncurses clear" and you'll find something similar to clrscr() .. also check [http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/](http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/)

---

### Post by sauravbhaumik on 2007-02-03
> err .. stdio.h and stdlib.h is part of standard C and thus part of gcc in any linux distro .. and conio.h is replaced by the far superior ncurses library..

Would you kindly tell me where I can get the ncurses library? I have checked and there is no **libncurses.a** in my /usr/lib
Kindly tell me wherefrom I can get them downloaded.
Regards

---

### Post by lnostdal on 2007-02-03
this is mentioned at the bottom in the post above :)

---

### Post by Elrohir on 2007-02-08
in conio.h there's a function called strrev(); is it in ncurses?

---

### Post by lnostdal on 2007-02-08
`strrev' reverses a string?

```

/*
  gcc -Wall -g -std=c99 reverse-string.c -o reverse-string
 */

#include <stdio.h>
#include <string.h>

typedef unsigned int uint;



void reverseString(char* str) {
  char tmp;   
  for(uint i = 0, j = strlen(str)-1; i < j; j--, i++) {
    tmp = str[i]; str[i] = str[j]; str[j] = tmp;
  }
}



int main() {
  char text[] = "abcd";
  reverseString(text);
  printf("%s\n", text);
    
  return 0;
}

```

edit: uhm, and well -- i don't know if ncurses has something like strrev

---

### Post by Elrohir on 2007-02-08
works great... but for one word... I'm trying to make it work with a whole phrase... can spaces be stripped out? how?

yes, strrev reverses a string...

---

### Post by runningwithscissors on 2007-02-08
.

---

### Post by Elrohir on 2007-02-08
> **runningwithscissors said:**
> .
yeah, I was going to point out that the if snippet you posted didn't work... ideas?

---

### Post by runningwithscissors on 2007-02-08
> **Elrohir said:**
> yeah, I was going to point out that the if snippet you posted didn't work... ideas?

The easiest way would be to reverse the string and then strip the spaces out.
Like a :
```

do {
        str = strchr(str, ' ');
        if(str != NULL) {
              memcpy(str, str+1, strlen(str+1));
              memcpy(str+strlen(str+1), "\0", 1);
        }
} while(str != NULL);
```

after the for loop has finished in Inostdal's example.
EDIT: Forgot to add the string terminator

---

### Post by Elrohir on 2007-02-08
> **runningwithscissors said:**
> The easiest way would be to reverse the string and then strip the spaces out.
Like a :
```

do {
        str = strchr(str, ' ');
        if(str != NULL) {
              memcpy(str, str+1, strlen(str+1));
              memcpy(str+strlen(str+1), "\0", 1);
        }
} while(str != NULL);
```after the for loop has finished in Inostdal's example.
EDIT: Forgot to add the string terminator
let me get this straight... this snippet here reverses and strips or just strips? becaus I want to strip the spaces before reversing it...

---

### Post by runningwithscissors on 2007-02-08
> **Elrohir said:**
> let me get this straight... this snippet here reverses and strips or just strips? becaus I want to strip the spaces before reversing it...

That snippet only strips spaces after the string reversal.

If you want to strip the spaces before, just declare a pointer and initialise it to the beginning of the string, and use that to strip spaces out.
Like so:
```
char* char_ptr;
char_ptr = str;
do {
        char_ptr = strchr(char_ptr, ' ');
        if(char_ptr != NULL) {
              memcpy(char_ptr, char_ptr+1, strlen(char_ptr+1));
              memcpy(char_ptr+strlen(char_ptr+1), "\0", 1);
        }
} while(char_ptr != NULL);

```
And move the snippet above the for loop that does the reversal.

---

### Post by LordHunter317 on 2007-02-08
The snippet there doesn't work, because it uses memcpy on overlapping strings.  Bad.  Use memmove instead.

---

### Post by lnostdal on 2007-02-08
> **Elrohir said:**
> works great... but for one word... I'm trying to make it work with a whole phrase... can spaces be stripped out? how?

ok, you want something that strips all space-characters from a character-array (string)?

```

/*
  gcc -Wall -g -std=c99 reverse-string.c -o reverse-string
 */

#include <stdio.h>
#include <string.h>

typedef unsigned int uint;


void reverseString(char* str) {
  // Reverse `str'. Destructively modifies `str'.
  char tmp;   
  for(uint i = 0, j = strlen(str)-1; i < j; j--, i++) {
    tmp = str[i]; str[i] = str[j]; str[j] = tmp;
  }
}


void stripChar(char c, char* str) {
  // Strip `c' from `str'. Destructively modifies `str'.
  char* t;
  for(t = str; *str; (*str - c) ? *t++ = *str++ : *str++);
  *t = '\0';
}


int main() {
  char text[] = "Hello World!";
  printf("%s\n", text);
  
  reverseString(text);
  printf("%s\n", text);

  stripChar(' ', text);
  printf("%s\n", text);
    
  return 0;
}

```

(note that this strips _all_ spaces .. not just trailing for instance)

---

### Post by runningwithscissors on 2007-02-08
> **LordHunter317 said:**
> The snippet there doesn't work, because it uses memcpy on overlapping strings.  Bad.  Use memmove instead.
It works. I agree that memove is the better and correct solution (I am forgetful, even though I've been programming C for quite some time). But the snippet works.
Besides, it wasn't tested or anything. I'm sure there will be some cases where it chokes.
 :)

---

