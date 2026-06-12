---
title: "comparing the value of scanf in a conditional"
date: 2009-12-07
forum: Programming Talk
---

### Post by Lyon on 2009-12-07
How do I compare the value of scanf in a conditional statement in C?

For example, in Perl, it would be 

```
if ($input eq 'quit')
{
}
```

or in PHP it would be

```
if ($input == 'quit')
{
}
```

This is what I have so far in C

```
#include <stdio.h>
#include <string.h>

int main()
{
	int game;
	char input[10];
	
	printf("Starting the game... \n");
	
	game = 1;
	
	while(game)
	{
		scanf("", &input);
	
		if (strcmp(input, "quit"))
		{
			char quit[1];
			scanf("Are you sure you want to quit? [Y/N] ", &quit);
			
			if (strcmp(quit, "y"))
			{
				printf("Goodbye...\n");
				return 0;
			}else{
				printf("Continuing game...");		
			}
		}	
	}
	
	
}
```

But this quits the game if I type anything in the output.

Is this less of a problem with my string comparison, or more of a problem with my logic?

---

### Post by lloyd_b on 2009-12-07
It's an error with your understanding of strcmp().

From the man page:```
RETURN VALUE
       The strcmp() and strncmp() functions return an integer less than, equal
       to, or greater than zero if s1 (or the first n bytes thereof) is found,
       respectively, to be less than, to match, or be greater than s2.
```.

In other words, strcmp returns 0 **if the two strings are equal**, a negative number of the first string is "less than" the second, and a positive number if the first string is "greater than" the second.  As a result, your if condition is executing on everything *except* "quit".

Try:```
if (!strcmp(input, "quit"))
``` to only trigger that block of code when the two strings are equal.

Lloyd B.

---

### Post by Lyon on 2009-12-07
Ah thank you, that makes a lot more sense now.

For future reference, how do I access the man pages for C functions? I already tried just "man strcmp" in bash, but of course, nothing.

EDIT:

I've compiled it and now nothing is happening when I type quit. I even tried adding a "\n" to the string comparison to account for the enter key. I suspect I misunderstood the strcmp() function AND my logic is flawed.

---

### Post by dwhitney67 on 2009-12-07
See this statement:
```

scanf("", &input);

```
Not only is it missing a purposeful format statement (eg. "%s"), it implies that you are attempting to read in a string.

Never use scanf() to read in a string; use fgets() instead.
```

/* initialize variables */
char input[10] = {0};

...

/* get the input */
fgets(input, sizeof(input), stdin);

/* remove the trailing newline, if any */
char* nl = strchr(input, '\n');
if (nl) *nl = '\0';

if (strcmp(input, "quit") == 0)
{
   /* the word 'quit' was entered */
}

```

---

### Post by PandaGoat on 2009-12-07
I think you should explicitly use 

```

strcmp(input, "quit") == 0

```

This won't solve the problem, but it is better style in my opinion.

The problem is with
```

char quit[1];
scanf("Are you sure you want to quit? [Y/N] ", &quit);
			
if (strcmp(quit, "y"))
{
    printf("Goodbye...\n");
    return 0;
}
else
{
    printf("Continuing game...");		
}

```

This is erroneous since in C you must represent the end of a string with the '\0' character.  I will not go into the details of this since it will take a while to fully explain, but you clearly should look it up before continuing.

strcmp is unable to compare two strings unless they are properly formatted.  Static strings like "y" have an implied null-terminating-character so you do not explicitly need it there.  However, QUIT only has one character, the user's input and does not end with a null-terminating-character.  Furthermore, you should not even use a string for that AND you do not use scanf correctly--there is not even a %-code in the format string:

```

char quit;
scanf("Are you sure you want to quit? [Y/N] %c", &quit);
			
if (quite == 'y')
{
    printf("Goodbye...\n");
    return 0;
}
else
{
    printf("Continuing game...");		
}

```

All in all, the problem is not your understanding of this specific concept or a logic error.  It is your understanding of C.  Go through some tutorials again. Sorry if I sound mean, but the code is laden with errors.

---

### Post by lloyd_b on 2009-12-07
To get the man pages for man(2) (system calls) and man(3) (standard library functions), you need to install the "manpages-dev" package.

(I was going to write a longer post, detailing the problems with scanf() in this instance, but others beat me to it :) )

Lloyd B.

---

### Post by Lyon on 2009-12-07
> 

All in all, the problem is not your understanding of this specific concept or a logic error.  It is your understanding of C.  Go through some tutorials again. Sorry if I sound mean, but the code is laden with errors.

No, you don't sound mean, I understand completely. While I do have experience with other languages, C is something completely new to me, so it's important people tell me what I'm doing wrong so I can learn.

I have to get used to how C works and break from the habits I had with other languages.

---

### Post by PandaGoat on 2009-12-07
Haha, good.  You took it exactly how I wanted to express it (which I usually sound mean expressing).

As most people have expressed, you should get used to the man pages.  If you want to use a function, in terminal type "man 3 function_name". The 3 represents the programming chapter of the manual.  Read the function's man page and try to understand how to use the function; if you don't then you need to look further back to why you don't understand how to use it or ask others about it specifically, like on the forums here.

The first task is to grasp general concepts which you've seem to done except for using char quit[1] but that is due to inexperience with C. As you said, you have experience with other language so this won't be of any concern.

Good luck to you!

Resources:
[http://www.cprogramming.com/tutorial.html#ctutorial](http://www.cprogramming.com/tutorial.html#ctutorial) This site in general has some decent tutorials but a lot of it is for specific topics. I linked directly to the general c tutorial though. Warning: it unfortunately has pop-ups.

---

