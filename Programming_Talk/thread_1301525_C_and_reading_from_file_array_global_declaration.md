---
title: "C and reading from file/ array global declaration"
date: 2009-10-26
forum: Programming Talk
---

### Post by rbaleksandar on 2009-10-26
Hi, guys.


  I'm writing a program to read from a file and display the number of times all letters (Latin alphabet) appear in it. For now I do the **toupper()**, so that the program doesn't make difference between upper- and lowercase (later I'll modify it). Now my code is working. But before I got it up and running, a thing happened that made me wonder "why?".
Here's the code (not perfect, I know :)):

**NOTE: The file's content is "This a file system test.".**

```

#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>

int count[26];

int main(int argc, char *argv[]){
	FILE *fp;
	char ch;
	int i;
	
		
	if(argc!=2){
		puts("Name of file is missing.");
		exit(1);
	}
		
	if((fp = fopen(argv[1], "r")) == NULL){
		printf("Cannot open file %s. Please specify  an existing file.", argv[1]);
		exit(1);
	}
	
	while((ch = fgetc(fp)) != EOF){
		putchar(ch);		//Display content of file
		ch = toupper(ch);
		if(ch>='A' && ch<='Z') count[ch - 'A']++;
	}
		
	for(i=0; i<26; i++)
		printf("%c occured %d time(s).\n", (i+'A'), count[i] );
	
	fclose(fp);
	return 0;
}


```

  Didn't put comments (except one :D) since it's small and I think it's clear what each section does.

  About the problem: first I have declared ```
int count[26]
``` inside the main-function (since I need it only there and nowhere else). But this caused a strange problem an explanation for which I really don't have. If you put it inside main(), when displaying all things inside the console, this appears:
```

A occured 1 time(s).
B occured 2293564 time(s).
C occured 2089871648 time(s).
D occured 2089877600 time(s).
E occured 1094795588 time(s).
F occured 1094795586 time(s).
G occured 2293480 time(s).
H occured 1094795586 time(s).
I occured 2293582 time(s).
J occured 2009291924 time(s).
K occured 2009310510 time(s).
L occured 2009471721 time(s).
M occured 2293597 time(s).
N occured 2009308512 time(s).
O occured 8 time(s).
P occured 2009288239 time(s).
Q occured 2009288233 time(s).
R occured 52 time(s).
S occured 4 time(s).
T occured 4 time(s).
U occured 4199456 time(s).
V occured 2293556 time(s).
W occured -1 time(s).
X occured 2293728 time(s).
Y occured 2009291925 time(s).
Z occured 2009147472 time(s).

```
  Which needless to say is wrong. :P If I put the ```
int count[26]
``` outside main() (that is - declare it as a global variable), I get it all correct:

- 1 time 'A'
- 3 times 'E'
- 1 time 'F'
- 1 time 'H'
- 2 time 'I'
etc.

 So my question is - why do I have to declare my array outside the function although I need it only there and nowhere else? And why are some of the numbers correct? (like 'S' which occurs 4 times)

Thanks in advance!

---

### Post by Arndt on 2009-10-26
> **rbaleksandar said:**
> Hi, guys.


  I'm writing a program to read from a file and display the number of times all letters (Latin alphabet) appear in it. For now I do the **toupper()**, so that the program doesn't make difference between upper- and lowercase (later I'll modify it). Now my code is working. But before I got it up and running, a thing happened that made me wonder "why?".
Here's the code (not perfect, I know :)):

**NOTE: The file's content is "This a file system test.".**

```

#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>

int count[26];

int main(int argc, char *argv[]){
	FILE *fp;
	char ch;
	int i;
	
		
	if(argc!=2){
		puts("Name of file is missing.");
		exit(1);
	}
		
	if((fp = fopen(argv[1], "r")) == NULL){
		printf("Cannot open file %s. Please specify  an existing file.", argv[1]);
		exit(1);
	}
	
	while((ch = fgetc(fp)) != EOF){
		putchar(ch);		//Display content of file
		ch = toupper(ch);
		if(ch>='A' && ch<='Z') count[ch - 'A']++;
	}
		
	for(i=0; i<26; i++)
		printf("%c occured %d time(s).\n", (i+'A'), count[i] );
	
	fclose(fp);
	return 0;
}


```

  Didn't put comments (except one :D) since it's small and I think it's clear what each section does.

  About the problem: first I have declared ```
int count[26]
``` inside the main-function (since I need it only there and nowhere else). But this caused a strange problem an explanation for which I really don't have. If you put it inside main(), when displaying all things inside the console, this appears:
```

A occured 1 time(s).
B occured 2293564 time(s).
C occured 2089871648 time(s).
D occured 2089877600 time(s).
E occured 1094795588 time(s).
F occured 1094795586 time(s).
G occured 2293480 time(s).
H occured 1094795586 time(s).
I occured 2293582 time(s).
J occured 2009291924 time(s).
K occured 2009310510 time(s).
L occured 2009471721 time(s).
M occured 2293597 time(s).
N occured 2009308512 time(s).
O occured 8 time(s).
P occured 2009288239 time(s).
Q occured 2009288233 time(s).
R occured 52 time(s).
S occured 4 time(s).
T occured 4 time(s).
U occured 4199456 time(s).
V occured 2293556 time(s).
W occured -1 time(s).
X occured 2293728 time(s).
Y occured 2009291925 time(s).
Z occured 2009147472 time(s).

```
  Which needless to say is wrong. :P If I put the ```
int count[26]
``` outside main() (that is - declare it as a global variable), I get it all correct:

- 1 time 'A'
- 3 times 'E'
- 1 time 'F'
- 1 time 'H'
- 2 time 'I'
etc.

 So my question is - why do I have to declare my array outside the function although I need it only there and nowhere else? And why are some of the numbers correct? (like 'S' which occurs 4 times)

Thanks in advance!

The reason is that global variables are initialized to zero, while stack variables are not. This is because the initialization of global variables is done at compile/link time, while for stack variables it would have to be done every time a function is entered.

---

### Post by aJayRoo on 2009-10-26
You are adding one to the value of count[...] but you have not initialized the array to zero. When you declare count outside of main it is getting initialized to zero (I believe this is a requirement of ANSI-C). You should always initialize variables yourself, it is less likely to introduce subtle bugs, and your intent will be clearer to others reading your code.

---

### Post by dwhitney67 on 2009-10-26
You need to initialize your variables; many newbie, and unfortunately experienced, programmers neglect to do this.

Btw, in your particular application, the global variable is not needed whatsoever.  Declare it within main().

```

   FILE*        fp = 0;
   char         ch = EOF;
   unsigned int i = 0;
   unsigned int count[26] = {0};

```

---

### Post by rbaleksandar on 2009-10-26
> **dwhitney67 said:**
> You need to initialize your variables; many newbie, and unfortunately experienced, programmers neglect to do this.

Btw, in your particular application, the global variable is not needed whatsoever.  Declare it within main().

```

   FILE*        fp = 0;
   char         ch = EOF;
   unsigned int i = 0;
   unsigned int count[26] = {0};

```



Thank you, guys, for all the explanations! I usually do initialize them. :P
  So a global variable can be left uninitialized (bad style, I know) and not cause any problem later when called, but a stack variable has to be initialized...Always. Cool. :guitar:

---

### Post by Arndt on 2009-10-26
> **rbaleksandar said:**
> Thanks you, guys, for all the explanations! I usually do initialize them. :P
  So a global variable can be left uninitialized (bad style, I know) and not cause any problem later when called, but a stack variable has to be initialized...Always. Cool. :guitar:

Of course you don't have to initialize anything if you don't read it before you write it the first time. In this case you do, but in other cases, the array may be a queue of something, for example, and some other variable will keep track of how much of it is valid.

(Just for completeness: you can have variables local to a function but not on the stack, by using the 'static' keyword in their declaration. It's a bad idea to have really large items on the stack, since the stack is not guaranteed to be very large.)

---

### Post by rbaleksandar on 2009-10-26
Thanks, Arndt. Good to know that. :)

---

