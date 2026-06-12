---
title: "compile C programs, Kdevelop &amp; terminal"
date: 2008-10-13
forum: Programming Talk
---

### Post by gian748 on 2008-10-13
Dear all,

I’m a C user. I “was born” with borland c interface (1998-96). It was simple. :)

Now I have started with LINUX and I have found enormous problems to use my C old programs and make new ones.

First. I have installed K develop but today, to compile and run a common C-language program I have to make a project.  So I do it, and I start to build it. But all the times a windows opens:” …there is no make file in this directory and no configure script fror this project. Run automake a& friends and configure first?” 

If I press “run them” the systems says “ there is neither a Makefile.cvs nor an autogen.sh.script in the project directory.

If I press “Do not run” it obviously do nothing.

Thus I’m not able to run hello.c program, neither!

What I have to do? :confused:

I have tried to compile online from terminal. Thus I have searched for a list with a brief explanation of the principals options to compile, link, make and run c programs. I have found the manual at the link : [http://www.gnu.org/software/gcc/onlinedocs/](http://www.gnu.org/software/gcc/onlinedocs/)


But…..it’s just a list without any explanation. ](*,)

Has someone a list WITH short explanation of the most commons options to compile, link, make and run c programs from terminal?

Many thanks 

gian

---

### Post by dwhitney67 on 2008-10-13
> **gian748 said:**
> ... to compile and run a common C-language program I have to make a project.
...

Only if you are using an IDE (e.g. Kdevelop).  Why not simplify your life and use the command-line to compile/link your programs?  I hope you haven't avoided this option because of fear of changing to something more hands-on.  It is actually quite simple, and eliminates a lot of the grief of developing simple applications.

Btw, if you have not already done so, ensure to install the development tools on your system.
```
sudo apt-get install build-essential
```
(note, it might be "essentials", not "essential".)

This may be what is causing Kdevelop its problems.

To compile a C program from the terminal:
```
gcc -Wall -pedantic -std=gnu99 Hello.c -o Hello
```

-Wall forces all warnings to be displayed
-pedantic displays warnings when code is not ISO C compliant
-std=gnu99 instructs the compiler to use the 1999 C standards (although GNU has not fully implemented them.)  The compiler, by default, uses the ancient 1989 standards.
-o is used to instruct the GCC linker what to name the resulting executable

When done, run the program:
```
./Hello
```


P.S.  Typing "gcc -Wall -pedantic -std=gnu99" everytime you want to compile a program can become tedious.  I suggest you add an alias to your ~/.bashrc file (using kedit or other editing application):
```
alias gcc='gcc -Wall -pedantic -std=gnu99'
```
then source the file when it has been saved.
```
source ~/.bashrc
```

---

### Post by gian748 on 2008-10-13
thank you very much!!! :)


I try and I let you know the result

gian

---

### Post by gian748 on 2008-10-13
...I have installed the develop tools with "sudo apt-get install build-essential" but Kdevelop still do exactly the same errors....

:confused:

then I tried the terminal possibility and this is , unfortunately, the result:

gianrico@Gianrico:~/Documents/BORLANDC$ ls
BORLANDCv  esempi  Input  invers  invers_V  MR_CNT.doc  Output  prova
gianrico@Gianrico:~/Documents/BORLANDC$ cd esempi
gianrico@Gianrico:~/Documents/BORLANDC/esempi$ ls
AND2.C      CARAT.C     COS.C      GENOP2.C   MIO7.C    OPMMU2.C    QUADRA.C
AND3.C      CICCA2.C    CUBICA.C   GENOP3.C   MIO8.C    OPMMU.C     SBLM9.C
AND.C       CICCA3.C    DIV.C      GENOP5.C   MIO9.C    OR.C        STAMPY.C
ASSFILE.C   CICCA4.C    EXTERN1.C  GENOP.C    MIO.C     PARAM.DAT   SUONO.C
ASSFILK1.C  CICCA7.C    EXTERN2.C  GOTOP.C    MUCCA.C   PRINEX.C    SWITCH.C
ASSFILK3.C  CICCA8.C    FEEDB.C    MARIA.BAK  NRUTIL.C  PROVA1.C    TEMPO.C
ASSFILK.C   CICCA.C     FILEOP.C   MARIA.C    OCA2.C    PROVA2.C    TESTFF.C
barza2.c    COMP1.C     FOPEN2.C   MENTRE.C   OCA3.C    PROVA34.C   UTIL.C
BEPPO.C     COMP2.C     FOPEN33.C  MIO10.C    OCA4.C    PROVA3.C    WFM1.C
BOZZA2.C    CONICO17.C  FOPEN3.C   MIO11.C    OCA5.C    PROVA4.C    WVFMOUT.C
BOZZA.C     CONTRO1.C   FOPEN4.C   MIO12.C    OCA6.C    PULISCI2.C  ZERI.C
CALC2.C     CONTRO2.C   FOPEN5.C   MIO4.C     OCA7.C    PULISCI.C
CALC.C      CONTRO3.C   FUN.C      MIO6.C     OCA.C     PUNTI.C
gianrico@Gianrico:~/Documents/BORLANDC/esempi$ gcc -Wall -pedantic -std=gnu99 and.c
gcc: and.c: No such file or directory
gcc: no input files
gianrico@Gianrico:~/Documents/BORLANDC/esempi$ gcc -Wall -pedantic -std=gnu99 and.c -o and
gcc: and.c: No such file or directory
gcc: no input files
gianrico@Gianrico:~/Documents/BORLANDC/esempi$ 


:(

...

---

### Post by gian748 on 2008-10-14
...ok, I'm happy to say that I'm stupid!!!!

A friend of mine has remembered me that Linux is case sensitive, I have forgotten that point. 

So I was succesfull in compiling c-code by terminal with your dwhitney67 suggestions!!!!

thanks again!!!

---

