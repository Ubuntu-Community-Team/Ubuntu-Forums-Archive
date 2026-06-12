---
title: "Problem in running C Programs"
date: 2012-01-25
forum: Programming Talk
---

### Post by uabhi12 on 2012-01-25
I had previously used c programs in windows xp on my desktop. Now I have installed Ubuntu 11.10 on my laptop and run certain downloaded programs with 'make' and related commands like './filename.exe' etc. But now I tried to run a simple summing of two numbers program from the proper directory by the above method. It is not running. The message is that 'there is no destination file.' Can't figure out the problem. Please help. One more thing when I post threads or replies a message comes 'Click a Quick Reply icon in above.'But I can't find any such icon - all I find are smilies.

---

### Post by imagecko on 2012-01-25
You cant windows-files, which have an ending of ".exe" in Linux. To do that you must have like Wine installed. If its not an exe-file, you just start them with: ./filename in the terminal. Be sure that you are in the same folder as  the file.

---

### Post by oldos2er on 2012-01-25
> **uabhi12 said:**
> I had previously used c programs in windows xp on my desktop. Now I have installed Ubuntu 11.10 on my laptop and run certain downloaded programs with 'make' and related commands like './filename.exe' etc. But now I tried to run a simple summing of two numbers program from the proper directory by the above method. It is not running. The message is that 'there is no destination file.' 

Can you please copy and paste the full terminal output of the command you're running?

Also please stick to the default forum font, per the CoC's posting tips.

---

### Post by uabhi12 on 2012-01-25
I have installed Wine1.3-gecko 1.40+1 and checked that it is installed.I am trying to run a program 'SUM' which is a c program and which had successfully run in Windows, in a directory 'Test" with the command ./SUM in Ubuntu. The message that I am getting is 
bash:./SUM:Permission denied.
 But previously I have run a very lengthy c Program which has a make file with the 'make' command. I understand Wine is a windows interface for Ubuntu. But think if Wine can run the SUM program as mentioned by imagecko the problem is with my not being able to open the Wine application.Please help.

---

### Post by 9072997 on 2012-01-25
you are running up against a security feature of linux. linux has a exicutible bit. all exicutible code must have it set (though i think make is supposed to do it automatically). to make a file exicutible do "chmod +x FILENAME"

---

### Post by uabhi12 on 2012-01-26
Hello 9072997,
 Now  the SUM program is compiling with "chmod +x SUM".But I am getting lots of error messages like:

```

abhijit@abhijit:~/Test$ ./SUM
./SUM: line 1: /*Program: No such file or directory - The /* Program is a comment line which the program doesn't read in Windows as can be seen below!
./SUM: line 4: syntax error near unexpected token `('
./SUM: line 4: `void main()'
abhijit@abhijit:~/Test$ 

```
Test is the folder under which the file SUM is.

My program is

```
/*Program to sum two numbers*/
#include <stdio.h>
#include <conio.h>
void main()
{
int a,b,c;
clrscr();
printf("\nGive the values of a and b")
scanf("%d%d",&a,&b);
c=a+b;
printf("The Sum is =%d",c);
getch ();
}

```

---

### Post by fct on 2012-01-26
> Hello 9072997,
Now the SUM program is compiling with "chmod +x SUM".But I am getting lots of error messages like:


abhijit@abhijit:~/Test$ ./SUM
./SUM: line 1: /*Program: No such file or directory - The /* Program is a comment line which the program doesn't read in Windows as can be seen below!
./SUM: line 4: syntax error near unexpected token `('
./SUM: line 4: `void main()'
abhijit@abhijit:~/Test$


Compile it. Rename SUM to SUM.c and:

```
$ gcc -o SUM SUM.c
```

Then you can run it with ./SUM

---

### Post by Tony Flury on 2012-01-26
> **fct said:**
> Compile it. Rename SUM to SUM.c and:

```
$ gcc -o SUM SUM.c
```

Then you can run it with ./SUM

Also - The code includes conio.h - which is windows specific and does not exist in Ubuntu. I would be very surprised if the compiler does not complain about that.

---

### Post by bouncingwilf on 2012-01-26
Looking at your source, you appear to be missing a semicolon after the printf statement

Bouncingwilf

---

### Post by Tony Flury on 2012-01-26
> **uabhi12 said:**
> Hello 9072997,
 Now  the SUM program is compiling with "chmod +x SUM".But I am getting lots of error messages like:



chmod +x does NOT compile anything - all it does it change the permissions on the file so that Linux knows it can execute it. The errors that you get are due to linix tryig to run the file as a shell script - which is the default fo executable text files.

the command 
```

gcc -o SUM SUM.c

```
actually compiles the text file which is SUM.c and coverts it into a binary executable file called SUM - if this compilation works you should be able to use 
```

./SUM

```
to execute your now binary file (which should be executable by default as the compiler will set the "x" permission on the file), but as I and others have pointed out - it is unlikely that the code you have given here will compile due to errors.

Although the C language is a standard, it does not mean that a C program which compiles and runs on Windows will compile and run (without modification) on Linux - often code will use libraries that only exist on one platform for instance - in your code, conio.h and getch() are examples of that I believe.

---

### Post by uabhi12 on 2012-01-26
[FONT=Times New Roman][SIZE=3]The Problem is solved.[/SIZE][/FONT]

---

### Post by cgroza on 2012-01-26
> **uabhi12 said:**
> [FONT=Times New Roman][SIZE=3]The Problem is solved.[/SIZE][/FONT]
Then mark it so. :D

---

