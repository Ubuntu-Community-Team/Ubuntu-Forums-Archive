---
title: "Passing a variable to a shell script"
date: 2008-07-10
forum: Programming Talk
---

### Post by blooddrunk on 2008-07-10
Hi! I am writing a C program, but I need to pass the value of a variable from that C program to a shell script. How can I do that? 10x in advance

---

### Post by ghostdog74 on 2008-07-10
> **blooddrunk said:**
> Hi! I am writing a C program, but I need to pass the value of a variable from that C program to a shell script. How can I do that? 10x in advance

generally, the pass something to a script, 
```

myscript.sh arg1 arg2

```
however, i would advise you not to do this unless necessary. Using C libraries, i  am sure you can code everything in C

---

### Post by blooddrunk on 2008-07-10
Yes, but in C to start s script you need the function system() as far as I know. For example: system("./my_script"). When one puts variable from C in the brackets in system, it doesn't work. You can't do :
 system("./my_script variable") or system ("./myscript",variable). 
SO what should I do to pass the variable?

---

### Post by ghostdog74 on 2008-07-10
don't just say it doesn't work. In C, print some debug information and show it here.

---

### Post by Martin Witte on 2008-07-10
> **blooddrunk said:**
> Yes, but in C to start s script you need the function system() as far as I know. For example: system("./my_script"). When one puts variable from C in the brackets in system, it doesn't work. You can't do :
 system("./my_script variable") or system ("./myscript",variable). 
SO what should I do to pass the variable?

it does work with system:
```
martin@toshibap200:~$ cat test.sh
#!/bin/sh
echo $*
martin@toshibap200:~$ cat test.c
int main(int argc, char** argv)
{
	system("/bin/sh test.sh 1 2 3");
	return 0;
}
martin@toshibap200:~$ gcc test.c
martin@toshibap200:~$ ./a.out
1 2 3
martin@toshibap200:~$ 
```

---

### Post by odyniec on 2008-07-10
I suppose what you're trying to do is pass the value of some specific C variable. If that's the case, then you need to put that value in a string (you can use snprintf() for this purpose), then pass that string to system(), eg.:
```
int foo = 31337;
char s[100];

snprintf(s, 100, "echo %d", foo);
system(s);
```

---

### Post by blooddrunk on 2008-07-11
odyniec, thanks a lot

---

### Post by 2015 on 2010-01-06
i m making a server program for implementing telnet protocol to talk to clients. In the server program i m receiving the commands typed at client's terminal in a char[] buffer. now i want this command to be executed at server's terminal by running a shell script which receives buffer as its arguments.the script executes:
`echo $1`

but its not working.script does not takes value of buffer string rather the variable name itself.
either snprintf() didn't worked or if odyniec can tell to pass a string!!!!!! 

Please help!!!

---

### Post by Hellkeepa on 2010-01-06
HELLo!

Please post the code where you create the command line, and call it, for this shell script.

Happy codin'!

---

### Post by 2015 on 2010-01-09
in the server program i m receiving commands from telnet clients in char [] buffer and want to run this command in the server terminal.

i'm calling the script as:

system("/home/krsna/Desktop/hello.sh $buffer");

the snprintf() didn't worked.
first i made a char[] s n used function as:

snprintf(s,len(s),"echo %s",buffer);
system(s);

---

