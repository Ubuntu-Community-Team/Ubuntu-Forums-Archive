---
title: "Homework related..."
date: 2009-04-06
forum: Programming Talk
---

### Post by Mezillious on 2009-04-06
Hey guys, I'm currently doing a graduate certificate in IT and as part of that course i'm doing a unit on UNIX/LINUX programming.

I am trying to come to grips with not only the linux programming environment itself, but also some specific commands. My assignment asks me to write a program which takes input from a file and outputs only the lower case letters from that file. I think I know how to do it, it's just that the syntax is driving me mad.

Every example i find, i cant get to work. I'm using the getchar command to read the character then an if loop to determine the case of teh character and a simple printf to output the result.

My problem is, that i cant get the getchar command to work at all, and im not even sure that im executing the command the right way.

My course is by distance and my lecturer doesn't give much information away, which is why i'm trolling the internet for help.

This is the code i have written to test the getchar command which i have written in a text document and saved as test.c

[B]#include <stdio.h>

int main (void)
{
int c;

printf("EOF has value: %d\n", EOF);

while((c = getchar()) != EOF)
putchar(c);

return 0;
}[/B]

When I type source test.c into the terminal i get

**bash: test.c: line 3: syntax error near unexpected token `('**
**bash: test.c: line 3: `int main (void)**

My question is, should this program run in this way from the terminal or is there something else i need to do? Once i can get this to work, i'll be able to answer the question, i just can't figure out the getchar syntax and how it is supposed to be run.

Thanks,

Craig

---

### Post by cabalas on 2009-04-06
Programs written in C need to be compiled before you can run them to compile something you need gcc installed which you can do by running the following command with sudo 

```
apt-get install build-essential
```

To compile code you need to run a command similar to this

```
gcc -o <output_name> <input_files>
```

where <output_name> is the name of the program you wish to produce and <input_files> is the one or more c source files.

---

### Post by overdrank on 2009-04-06
From the [Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")
> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums should not be thought of as a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued. 

---

