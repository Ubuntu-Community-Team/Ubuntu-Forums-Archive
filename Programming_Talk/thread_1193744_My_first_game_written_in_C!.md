---
title: "My first game written in C!"
date: 2009-06-21
forum: Programming Talk
---

### Post by %hMa@?b&lt;C on 2009-06-21
I got my first game in C done today! I've written it in other languages, but I'm learning C now.  What do you think?
```
#include <stdio.h>
/* Rock, Paper Scissors by (jeff.crowell@gmail.com) 
If you have any questions/suggestions/help please email me!*/
int main (void)  {
	int computer, player;
	computer = rand ()%3; // generates the computer's choice of rock, paper, or scissor randomly
	printf ("type in your choice of 'rock'=1 'paper'=2 or 'scissor'=3'\n");
	scanf ( "%i", &player );  //receives the player's input
/*this is the compair computer with player*/		
	if (player == computer) {
		printf ("'\ntie games'\n");
		}
		if (player==1 && computer==2) {
		printf ("\nloss, paper covers rock\n");
		printf ("%i", computer);
		}
		if (player==1 && computer==3) {
		printf ("\nwin, rock breaks scissors\n");
		}
		if (player==2 && computer==1) {
		printf ("\nwin, paper covers rock\n");
		}
		if (player==2 && computer==3) {
		printf ("\nloss, scissors cut paper\n");
		}
		if (player==3 && computer==1) {
		printf ("\nloss, rock breaks scissors\n");
		}
		if (player==3 && computer==2) {
		printf ("\nwin, scissors cut paper\n");
		}
/*end compair*/
	return 0;
}	
	

```

---

### Post by jacensolo on 2009-06-21
This is mostly personal preference but most people use ```
if ()
{
}
```

instead of the "java style" when writing C. Other than that, good luck with C. It's a very nice language.

---

### Post by Can+~ on 2009-06-21
> **jacensolo said:**
> This is mostly personal preference but most people use ```
if ()
{
}
```

Syntax:
Yeah, I was thinking the same, the indentation blocks are kinda funky. And change if's for elseif's, as you're doing extra comparisons for nothing.

I would also use more separation between the variable definition and the working code, like (also notice I'm not a big fan of inline comments):

```

#include <stdio.h>

int main (void)
{
	int computer, player;
	
	// generates the computer's choice of rock, paper, or scissor randomly
	computer = rand ()%3;
	printf ("type in your choice of 'rock'=1 'paper'=2 or 'scissor'=3'\n");

	//receives the player's input
	scanf ( "%i", &player );
	
	/*this is the compare computer with player*/		
	if (player == computer) 
	{
		printf ("'\ntie games'\n");
	}
	else if (player==1 && computer==2) 
	{
		printf ("\nloss, paper covers rock\n");
		printf ("%i", computer);
	}
	else if (player==1 && computer==3) 
	{
		printf ("\nwin, rock breaks scissors\n");
	}
	else if (player==2 && computer==1) 
	{
		printf ("\nwin, paper covers rock\n");
	}
	else if (player==2 && computer==3) 
	{
		printf ("\nloss, scissors cut paper\n");
	}
	else if (player==3 && computer==1) 
	{
		printf ("\nloss, rock breaks scissors\n");
	}
	else if (player==3 && computer==2) 
	{
		printf ("\nwin, scissors cut paper\n");
	}
	/*end compare*/
	
	return 0;
}

```

---

### Post by jacensolo on 2009-06-21
> **Can+~ said:**
> Syntax:
Yeah, I was thinking the same, the indentation blocks are kinda funky. And change if's for elseif's, as you're doing extra comparisons for nothing.

I would also use more separation between the variable definition and the working code, like:



I agree with this. I didn't look at the code to see what it was doing, I just looked over it.

---

### Post by %hMa@?b&lt;C on 2009-06-21
thanks for the tips.
I agree that my formatting is a bit... strange?  Can anyone please tell me why a elseif is better than an if?  Thanks!

---

### Post by Can+~ on 2009-06-21
> **jeffc313 said:**
> thanks for the tips.
I agree that my formatting is a bit... strange?  Can anyone please tell me why a elseif is better than an if?  Thanks!

Because the execution goes this way:

```

> if (...)   check condition, nope.
.     ........
.
> if (...)   check condition, nope.
.     ........
.
> if (...)   check condition, yes!
    > ...... do stuff
.
> if (...)   check condition, nope.
.
.
.

```

Once it found the matching condition, it continues searching the rest of the if's.

With else if


```

> if (...)        check condition, nope.
.     ........
.
> else if (...)   check condition, nope.
.     ........
.
> else if (...)   check condition, yes!
    > ...... do stuff
.
. else if         no need to check condition, jump to the end of the if/else block
```

When the condition is found, the execution of the if-else block ends.

---

### Post by soltanis on 2009-06-22
I disagree with the braces style -- I prefer coding similar to the Linux kernel format, which is like

```


int function_call(type_t arguments)
{
        /* some comments */
        /* Here's a multi-
         * liner comment */
        
        if (condition) {
                do_stuff();
        }
}


```

Indentation 8 spaces, spaces between conditionals/loops and (), and no space between functions and ().

But what's important is that you pick a style (preferably with more whitespace) and stick to it.

Otherwise you look good. There might be a more elegant way to do the branching conditional, and most people use #define for numeric constants that stand for conceptual information, but you got it.

---

### Post by hessiess on 2009-06-22
> **Can+~ said:**
> Because the execution goes this way:

```

> if (...)   check condition, nope.
.     ........
.
> if (...)   check condition, nope.
.     ........
.
> if (...)   check condition, yes!
    > ...... do stuff
.
> if (...)   check condition, nope.
.
.
.

```

Once it found the matching condition, it continues searching the rest of the if's.

With else if


```

> if (...)        check condition, nope.
.     ........
.
> else if (...)   check condition, nope.
.     ........
.
> else if (...)   check condition, yes!
    > ...... do stuff
.
. else if         no need to check condition, jump to the end of the if/else block
```

When the condition is found, the execution of the if-else block ends.

And if possible, use a switch instead. They are more easily optimised by the compiler.

---

### Post by credobyte on 2009-06-22
```
int main()
{
     if ( ... ) {
          // do something here
     }
}
```If you create a function, open/close it in a new like, but, don't do the same for "if/else" or any other "local" operation ( tough, that's what I prefer and you shouldn't use it as the "best" style of coding ).

---

### Post by darthmob on 2009-06-22
personally I would say that you should not mind the nitpicking about the brackets style or efficiency too much. even more if you have just started with programming. here are my thoughts on your program / game:

[list]
[*] if you have got a program with user input (eg. the choice in your program) you always have to check for a valid response. as a basic approach keep in mind that the average computer user is stupid. your program simply ends if a different number than expected is entered - it should at least tell the user that it was wrong. or make a loop that keeps asking for a correct choice (hint: do while loop).

[*] else if or a switch case with breaks would be better (see Can+~'s explanation)

[*] don't use /* */ for single line comments. in my experience it won't compile if you have one or more /* */ in a /* */ (for example when you want to comment out a larger chunk of code for testing purposes). 

[*] try to keep the code easy to read. it does not hurt to have lines without text!

[*] the next step for your program would be to accept strings as a choice. eg. to let the user enter 'paper' if he wants to select paper. you would have to work with string compares there. strings can be a bit tricky in C but sooner or later you will have to deal with them. :)
[/list]

---

### Post by %hMa@?b&lt;C on 2009-06-23
well, after a bit of thinking, I added a "sanity check" to make sure that input is 1, 2, or 3.  
One error that i get is that even though rand()%3; is run every single time the program is run, the computer always gets the same output.

```
#include <stdio.h>
int main (void)
{
	int computer, player;
	
	// generates the computer's choice of rock, paper, or scissor randomly
	computer = rand ()%3;
	printf ("type in your choice of 'rock'=1 'paper'=2 or 'scissor'=3'\n");

	//receives the player's input
	scanf ( "%i", &player );
	
	//check sanity of the input
	while(player!=1 && player!=2 && player!=3)
	{
		printf("\ninput _MUST_ be either 1, 2, or 3\n");
		printf("try again: 'rock'=1 'paper'=2 or 'scissor'=3'\n");
		scanf( "%i", &player);
	}
		
	/*this is the compare computer with player*/		
	if (player == computer) 
	{
		printf ("'\ntie games'\n");
	}
	else if (player==1 && computer==2) 
	{
		printf ("\nloss, paper covers rock\n");
		printf ("%i", computer);
	}
	else if (player==1 && computer==3) 
	{
		printf ("\nwin, rock breaks scissors\n");
		printf ("%i", computer);
	}
	else if (player==2 && computer==1) 
	{
		printf ("\nwin, paper covers rock\n");
	}
	else if (player==2 && computer==3) 
	{
		printf ("\nloss, scissors cut paper\n");
		printf ("%i", computer);
	}
	else if (player==3 && computer==1) 
	{
		printf ("\nloss, rock breaks scissors\n");
		printf ("%i", computer);
	}
	else if (player==3 && computer==2) 
	{
		printf ("\nwin, scissors cut paper\n");
		printf ("%i", computer);
	}
	/*end compare*/
	
	return 0;
}
```

---

### Post by Mirge on 2009-06-23
> **jeffc313 said:**
> well, after a bit of thinking, I added a "sanity check" to make sure that input is 1, 2, or 3.  
One error that i get is that even though rand()%3; is run every single time the program is run, the computer always gets the same output.

```
#include <stdio.h>
[B]#include <time.h>
#include <stdlib.h>[/B]

int main (void)
{
**    srand(time(NULL));**
    int computer, player;
    
    // generates the computer's choice of rock, paper, or scissor randomly
    computer = rand ()%3;
    printf ("type in your choice of 'rock'=1 'paper'=2 or 'scissor'=3'\n");

    //receives the player's input
    scanf ( "%i", &player );
    
    //check sanity of the input
    while(player!=1 && player!=2 && player!=3)
    {
        printf("\ninput _MUST_ be either 1, 2, or 3\n");
        printf("try again: 'rock'=1 'paper'=2 or 'scissor'=3'\n");
        scanf( "%i", &player);
    }
        
    /*this is the compare computer with player*/        
    if (player == computer) 
    {
        printf ("'\ntie games'\n");
    }
    else if (player==1 && computer==2) 
    {
        printf ("\nloss, paper covers rock\n");
        printf ("%i", computer);
    }
    else if (player==1 && computer==3) 
    {
        printf ("\nwin, rock breaks scissors\n");
        printf ("%i", computer);
    }
    else if (player==2 && computer==1) 
    {
        printf ("\nwin, paper covers rock\n");
    }
    else if (player==2 && computer==3) 
    {
        printf ("\nloss, scissors cut paper\n");
        printf ("%i", computer);
    }
    else if (player==3 && computer==1) 
    {
        printf ("\nloss, rock breaks scissors\n");
        printf ("%i", computer);
    }
    else if (player==3 && computer==2) 
    {
        printf ("\nwin, scissors cut paper\n");
        printf ("%i", computer);
    }
    /*end compare*/
    
    return 0;
}
```

See bold above. See if that changes the random selection.

---

### Post by shadylookin on 2009-06-23
computer = rand ()%3;

will give you either 0, 1, or 2 you should change it to 

computer = (rand() % 3) + 1;

---

### Post by meditatingfrog on 2009-06-23
I found this thread because I want to improve my coding skills.  How do I compile your code?  I tried saving the code to a file called rps in gedit, then typed make rps but that didn't work.  I won't tell you the other silly things I tried that also didn't work.  :confused:

---

### Post by %hMa@?b&lt;C on 2009-06-23
> **meditatingfrog said:**
> I found this thread because I want to improve my coding skills.  How do I compile your code?  I tried saving the code to a file called rps in gedit, then typed make rps but that didn't work.  I won't tell you the other silly things I tried that also didn't work.  :confused:

save it as rps.c to make it 
gcc rps.c -o rps

EDIT: Mirge, your additions worked. can you please explain to me as to why?  Thanks!

---

### Post by meditatingfrog on 2009-06-23
Dear Jeffc313:

gcc rps.c -o rps did the trick.  I was able to then execute it by ./rps.  When I play it, I can always tie the computer by choosing rock, well, I suppose I shouldn't say always, I only ran it like twenty times.  Have you gotten anything besides a tie when you play rock?

---

### Post by %hMa@?b&lt;C on 2009-06-23
> **meditatingfrog said:**
> Dear Jeffc313:

gcc rps.c -o rps did the trick.  I was able to then execute it by ./rps.  When I play it, I can always tie the computer by choosing rock, well, I suppose I shouldn't say always, I only ran it like twenty times.  Have you gotten anything besides a tie when you play rock?

mirge's additions make it work.  I am not sure exactly what it does.  Also shadylookin got it right about rand()%3 needing the +1

here is the code that is working as of now.
```
#include <stdio.h>
#include <time.h>
#include <stdlib.h>

int main (void)
{
    srand(time(NULL));
    int computer, player;
    
    // generates the computer's choice of rock, paper, or scissor randomly
    computer = (rand ()%3) + 1;
    printf ("type in your choice of 'rock'=1 'paper'=2 or 'scissor'=3'\n");

    //receives the player's input
    scanf ( "%i", &player );
    
    //check sanity of the input
    while(player!=1 && player!=2 && player!=3)
    {
        printf("\ninput _MUST_ be either 1, 2, or 3\n");
        printf("try again: 'rock'=1 'paper'=2 or 'scissor'=3'\n");
        scanf( "%i", &player);
    }
        
    /*this is the compare computer with player*/        
    if (player == computer) 
    {
        printf ("'\ntie games'\n");
    }
    else if (player==1 && computer==2) 
    {
        printf ("\nloss, paper covers rock\n");
        printf ("%i", computer);
    }
    else if (player==1 && computer==3) 
    {
        printf ("\nwin, rock breaks scissors\n");
        printf ("%i", computer);
    }
    else if (player==2 && computer==1) 
    {
        printf ("\nwin, paper covers rock\n");
    }
    else if (player==2 && computer==3) 
    {
        printf ("\nloss, scissors cut paper\n");
        printf ("%i", computer);
    }
    else if (player==3 && computer==1) 
    {
        printf ("\nloss, rock breaks scissors\n");
        printf ("%i", computer);
    }
    else if (player==3 && computer==2) 
    {
        printf ("\nwin, scissors cut paper\n");
        printf ("%i", computer);
    }
    /*end compare*/
    
    return 0;
}
```

---

### Post by meditatingfrog on 2009-06-23
I added shadylookin's +1 to computer = rand()%3 and now I lose when I choose rock.  Haven't won on rock yet.

---

### Post by meditatingfrog on 2009-06-23
It does work better now.  The trials appear to be more random.

---

### Post by Mirge on 2009-06-23
srand() seeds rand... specifying time(NULL) seeds with changing data (ie: timestamp). Seeding with the same value will cause the same "random" numbers.

Always seed before using rand() in your programs.. only need to do it once though.

---

### Post by Can+~ on 2009-06-23
C's random in reality is a "pseudo-random". It's a f(n) function that can return a wide variety of numbers, but for a known n it returns the exact same number. Each time you call the function, this n increases.

srand displaces this n, and using time(NULL) as it's input makes it time dependant, making it "more random" as it depends when you execute your application, but still is pseudo-random.

It's good enough for games, bad for cryptography.

---

### Post by meditatingfrog on 2009-06-23
I think this is cool.  I'm going to see if I can figure out how to watch the output of the computer variable.

---

### Post by %hMa@?b&lt;C on 2009-06-23
> **meditatingfrog said:**
> I think this is cool.  I'm going to see if I can figure out how to watch the output of the computer variable.

a simple printf command will do that

printf ("%i", computer);

prints the integer assigned to computer.

---

### Post by meditatingfrog on 2009-06-23
Isn't computer the name for the variable that stores the integer?  Why doesn't just prinf(computer) work, or printf("'This is the computer:  '", computer) work?  I just tried it.  Doesn't work quite the way I would like it to.

I added this code to the if and else if blocks:  	

printf ("'Computer is:  '", computer);

---

### Post by noerrorsfound on 2009-06-23
> **meditatingfrog said:**
> Why doesn't just prinf(computer) work, or printf("'This is the computer: '", computer) work?
I'm not an experienced programmer so anyone can correct me if it's necessary.

There are more ways than one to print the value held in the variable. For example, taken from [this example on cplusplus.com]("http://www.cplusplus.com/reference/clibrary/cstdio/printf/"):
```
printf ("Some different radixes: %d %x %o %#x %#o \n", 100, 100, 100, 100, 100);
```It's being given the integer 100 each time yet it's being printed in different ways.

Regarding the second example you gave, you never told it where to print the value of computer. You could want it printed anywhere within that text, so the computer's not going to just assume you wanted it at the end and print it. You can also put more than one variable, and if they were both printed at the end, how would the computer know what way you want them separated? Maybe you want spaces in between, or commas.

Have you read any books or tutorials about C?

---

### Post by meditatingfrog on 2009-06-23
I haven't even touched a book on C since college, which was like 8 years ago.  I've done more reading and have more experience with SQL.  I'll keep trying, thanks for the tip.

---

### Post by meditatingfrog on 2009-06-23
> **noerrorsfound said:**
> I'm not an experienced programmer so anyone can correct me if it's necessary.

There are more ways than one to print the value held in the variable. For example, taken from [this example on cplusplus.com]("http://www.cplusplus.com/reference/clibrary/cstdio/printf/"):
```
printf ("Some different radixes: %d %x %o %#x %#o \n", 100, 100, 100, 100, 100);
```It's being given the integer 100 each time yet it's being printed in different ways.

Regarding the second example you gave, you never told it where to print the value of computer. You could want it printed anywhere within that text, so the computer's not going to just assume you wanted it at the end and print it. You can also put more than one variable, and if they were both printed at the end, how would the computer know what way you want them separated? Maybe you want spaces in between, or commas.

Have you read any books or tutorials about C?

I did just read the man page for printf.  I'll read the website you linked.  I appreciate your help, but your explanation appears to be over my head.  I understand that you are saying I need to tell the printf (function?) where to print the computer integer, I'm just not sure how to do that yet.  I think I'm going to have to practice editing and compiling, and yes, reading the website you linked.  

I hope you don't find my stupidity too frustrating.

---

### Post by cmay on 2009-06-23
```
/* simple formats example */

#include <stdio.h>

int main(int argc, char** argv)
{
    int i=22;
    float f = 1.25;
    char c= 'a';
    char string[]="hello world";
    
    printf("%d \n %s \t %1.2f \n %c\n",i,string,f,c);
    
    return 0;
}
```the int is printed using a %d and the float is printed using a %1.2f that also sets the format on the print.  

same as the \t that adds a tab to the output and the \n newline is added by \n
the char can be printed using both %c or %d as they are close to each other in type but 
to print a char its %c and to print a int its still %d. 

the string is a array of chars in c so therefor its declared as a char array but printed out as a string using the %s symbol. 

i am not sure if that was the question but feel free to ignore if i posted out of context.

---

