---
title: "Help with simple &quot;password&quot; program - absolute beginner"
date: 2008-06-15
forum: Programming Talk
---

### Post by jmmL on 2008-06-15
As the title says, I'm completely new to programming - but i'm really enjoying the little i've done so far. I've chosen to try to learn C as my first language.

I've written the obligatory "Hello World!" and one other one that's essentially a guessing game with numbers - guess the number 7 and the program congratulates you; guess anything else and it prompts you to try again.

What I'd like to be able to do is to have a similar "guessing game" program, but with a word (is a "string" the right term here?). Here's my code for the program:

```

#include <stdio.h>

int main()
{
	char pwd;
	
	printf( "Enter a password here to login: " );
	scanf( "%c", &pwd );

if (pwd == hello) {
	printf("You entered the correct password, welcome in!\n" );
}

else {
	printf("The password you entered was not correct. The program will now abort.\n" );
}

	getchar();
	return 0;
}

```

It's just a modification of my number program really. Here are the errors i get when i compile with gcc:

```

jamie@minty-alien ~ $ gcc ~/password.c -o password -Wall
/home/jamie/password.c: In function ‘main’:
/home/jamie/password.c:10: error: ‘hello’ undeclared (first use in this function)
/home/jamie/password.c:10: error: (Each undeclared identifier is reported only once
/home/jamie/password.c:10: error: for each function it appears in.)

```

What would i have to change to get it to work? Is it possible in C? The [guide]("http://www.cprogramming.com/tutorial.html#ctutorial") I'm using doesn't seem to mention taking words as an input...

It's possible I've dived in too quickly, but any help with this would be greatly appreciated!

---

### Post by Yes on 2008-06-15
[php]#include <stdio.h>
#include <string.h>

int main {
    char[100] pwd; /* Declares the password user gives.  
It's a character array with room for up to 100 characters */

    printf ("Enter the password: ");
    fgets (pwd, sizeOf(pwd), stdin); /* Gets user input from stdin (standard input), 
and puts it into pwd.  It only gets up to sizeOf(pwd) characters, ensuring that the 
user doesn't give more input than pwd can hold. */
    
    if (strcmp(pwd, "hello") == 0) /* Compares two strings, returns 0 if they're the same */
        printf ("Password correct.\n");
    else
        printf ("Password incorrect.\n");

    return(0);
}[/php]

String is the right term.  I tried to explain everything in my comments, just ask if you don't understand anything.  Here's the page on strings from the guide you've been using: [http://www.cprogramming.com/tutorial/c/lesson9.html](http://www.cprogramming.com/tutorial/c/lesson9.html)

---

### Post by cmay on 2008-06-15
this seems to work on my machine.
```
#include <stdio.h>
#include <string.h>

int main ()
{
char pwd[100]; /* Declares the password user gives.  It's a character array with room for up to 100 characters */

printf ("Enter the password: ");
fgets (pwd, sizeof(pwd), stdin); /* Gets user input from stdin (standard input), and puts it into pwd.  It only gets up to sizeOf(pwd) characters, ensuring that the user doesn't give more input than pwd can hold. */
    
if (strcmp(pwd, "hello") == 1){ /* Compares two strings, returns 0 if they're the same */
printf ("Password correct.\n");
}
else
{

printf ("Password incorrect.\n");
}

return(0);
} 
```

---

### Post by nvteighen on 2008-06-15
Dear OP: some things I'd like you to see.
1. strcmp(), printf(), scanf(), fgets(), etc. are Standard Library functions. This means they aren't part of the language like "char" or "if", but have been created afterwards and put together into a library; there are lots of other libraries intended for almost any task you want (so you focus on your job and don't have to rewrite what someone else has already done!). Those are learned when you actually need them. But the Standard Library is anavoidable! You must master it and know it.

What I really want you to see is that C is a structured programming language. This means that it relies in functions, no matter if your own or a library's. main() is a function, for example (which has to be in all C programs), and the idea is that "1 function does 1 task"... your main() is actually doing everything... Now, at the beginning, it isn't that important as getting used to the language, but you should keep at least this concept in mind for the future, when your programs get a bit more complex.

2. Let's see some code from you and see why it didn't work:
[php]
int main()
{
	char pwd;
	
	printf( "Enter a password here to login: " );
	scanf( "%c", &pwd );
(...)
[/php]

What you do there is to declare one-character-long variable. I mean: just a letter 'a', 'b' but never "hello"... just the 'h' would get into there. You need a string, which in C is an array of char's: As cmay pointed out, **char pwd[100];** will declare a 100-characters-long variable.

OK, the "issue" is that an array (any) is equivalent to a pointer, which I suppose you haven't learned yet. So, if you had used scanf() to read the string, you would have written: **scanf("%s", pwd);**, with no ampersand (&) and the "%s", which means "read a string"... just believe me that's the way, you'll understand it when you learn to use pointers. But, if you look carefully cmay's code, you'll see he doesn't use scanf(), but fgets(). Both make essentially the same, just that scanf() has serious security flaws (which you shouldn't care at least for now).

3. **if(pwd == hello)**. There you are telling to compare two **variables**, pwd and hello... but hello doesn't exist, you haven't declared it (that's why gcc complains)! String contents are always embodied between "..."; character use '...'. For example, in **printf("Hello");**.

There's a problem in C (which, again, is related to pointers). Yes, you can do **if(a == 'a')** (see if variable a contains an 'a'), but you can't do **if(a == "hello")**. You need the function strcmp() (=STRing CoMPare), which spits out some numbers depending on whether the strings are the same or not (1 if equal). So, we need to pass both strings to that function and see what that function tells us as result.

3. There's a very handy package in the repos that will make your life very much easier: manpages-dev. Install it and you'll get manual pages for all Standard Library's functions! After installing it, if you need to know what e.g. scanf() is and does, you do:
```

man scanf

```

And don't give up! :) (And don't stop to ask questions!)

---

### Post by jmmL on 2008-06-15
Brilliant!
Thank you, all 3 of you!
I've compiled it and it works fine!

[EDIT] Or at least, it /seemed/ to work fine. I just tried a few phrases through it and (as expected) "hello" works as expected, and incorrect ones like "asdf" don't. However, I tried a few more and ones like "jamie" or simply "a" seem to make the program think i entered the right password. :S
Here's the code I'm using:

[PHP]#include <stdio.h>
#include <string.h>

int main()
{
	char pwd[30];
	
	printf( "Enter a password here to login: " );
	fgets (pwd, sizeof(pwd), stdin);

if (strcmp(pwd, "hello") == 1 ) {
	printf("You entered the correct password, welcome in!\n" );
}

else {
	printf("The password you entered was not correct. The program will now abort.\n" );
}

	getchar();
	return 0;
}[/PHP]

What could be causing this? (I hope i haven't missed anything stupid) [/EDIT]

I'm now going to try some "else if" stuff with usernames and passwords. I'll let you know if i run into any more trouble, but I'll try the man pages first :)

I know this is going slightly off-topic, but what kind of programs are written in C? I heard that the Linux kernel is mostly C, is that right?
The reason i ask is that one of my main motivations for learning to "code" is that I'm just about to start a chemistry degree, and I'm hoping that in 4 or 5 years i might have enough programming knowledge to be able to write code for a quantum-scale simulation, or perhaps something more simple, like just capturing data from equipment etc..
Do you think this is feasible over 5 or so years? Bear in mind that anything i do will have to be done in my spare time, and i doubt that we'll get taught any as part of the course.

Thank you once again!

jmmL

---

### Post by mike_g on 2008-06-15
Well strcmp returns 0 if the strings are a match. So if the password needs to match "hello" then you want to be doing:
```
if (strcmp(pwd, "hello") == 0 )
```

---

### Post by Can+~ on 2008-06-15
[FONT="Courier New"]strcmp[/FONT] returns 0 if both strings are equal

---

### Post by cmay on 2008-06-15
i did not have my morning coffe yet.
also just a beginner anyway but it seems to work on my machine.
did not test it so much as i am drinking my morning coffe right now. 
all i did in the above code was to fix the pwd[30] and ad brackets.
try many things to fool proof it. just play around whit it to learn.
 and i think the adwise given by nvteighen is very good and worth a lot . 
as i think whats hardest to learn in c is not the simple language as such but for beginners the functions and how to use them. 
i have just used c in a monht so i am no expert on this subjekt

to answer your question as what c are used for its mostly in generel small projekt like as example texteditors .
windows applications are often written in c.
and c is good for compiler construction and drivers and such and created to write the unix operative system

---

### Post by nvteighen on 2008-06-16
> **mike_g said:**
> Well strcmp returns 0 if the strings are a match. So if the password needs to match "hello" then you want to be doing:
```
if (strcmp(pwd, "hello") == 0 )
```
Oops, my mistake there! Yes, it returns 0 if equal, 1 if not.

@OP: There's another problem we all missed: When you enter the string, you also add a newline character ('\n') because hitting the enter key. Well, yes: C keeps track of everything!

So, if you compare that to "hello", the test will fail because "hello\n" != "hello". **if(strcmp(pwd, "hello\n") == 0)** will work instead. Try it out!

---

