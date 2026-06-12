---
title: "fflush() or fpurge()? Neither work..."
date: 2009-01-27
forum: Programming Talk
---

### Post by myromance123 on 2009-01-27
warning: C programming problem up ahead!!

Heya, okeh heres the lowdown. Basically I have tried again and again with fflush(stdin) to get my C programs to stop accepting Enter as input but it doesnt work...

 So I thought I needed to use fpurge(stdin) but the terminal reports this back
```
/tmp/ccIUQo2Y.o: In function `main':
stocks.c:(.text+0x6a): undefined reference to `fpurge'
collect2: ld returned 1 exit status

```

How do I use fpurge? Is it even possible? Or am I misusing fflush()?
Is there another alternative altogether??

If you want to see the code I'll gladly put it up (pretty simple stuff)
 Thanks a heap~

---

### Post by nvteighen on 2009-01-27
Never do **fflush(stdin);**. In GNU/Linux it doesn't work, but in other systems it can lead to undefined behaivor.

fpurge is a BSD extension, according to its man page... if you use it, your code gets non-standard. fflush is standard.

What are you trying to do? I honestly don't understand your post... Are you trying to make your input "multiline"?

---

### Post by myromance123 on 2009-01-27
Okeh here is the code hopefully it will clear up what Im trying to accomplish (dont worry bout the unfilled functions at the bottom, will get to that later):

```
#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>

#define FALSE 0
#define TRUE !FALSE

struct stock_data {
	char name[20];
	float buy_price;
	float current_price;
};

void write_info(void);
void read_info(void);

int main()
{
	char c;
	int done=FALSE;
	
	while(!done)
	{
		puts("\nSTOCK PORTFOLIO THING\n");
		puts("A - Add new stock\n");
		puts("L - list stock(s)\n");
		puts("Q -Quit \n");
		printf("your choice:");
		
		c = getchar();
		fflush(stdin);
		c = toupper(c);
		switch(c)
		{
			case('A'):
				puts("Add new stock\n");
				write_info();
				break;
			case('L'):
				puts("List stock");
				read_info();
				break;
			case('Q'):
				puts("Quit\n");
				done = TRUE;
				break;
			default:
				puts("?");
				break;
		}
	}
	return(0);
}

void write_info(void)
{
}

void read_info(void)
{
}
```

Basically once a selection is input then it heads to the write and read functions but instead of just accepting the selection it also accepts the enter key causing it to run default as well...

I find this happens to all the programs that I need to use fflush() with...

---

### Post by nvteighen on 2009-01-27
Try commenting fflush() out and you'll notice your program will behaive exactly the same with or without it...

Ok, the "canonical" way to do this would be to use ncurses, which handles most of these terminal interface needs in a practical (but really messy) way. cbreak() mode + getch() and you'd be fine.

What I'd do without ncurses is to tell the program to accept a string with fgets() and the test the first character of that string... (because the second will be '\n' and the third '\0'... you need an array of size 3).

---

### Post by myromance123 on 2009-01-27
Im sorry but could you guide me through that "canonical" way or your way?

  I dont really get what you're getting at (Im still quite the beginner at C )

Thanks for the speedy replies

---

### Post by nvteighen on 2009-01-27
Hmm... ncurses is a library that allows you to do create better text interfaces. If you're a beginner, you better not touch it... yet.

What I mean is something like this (standard C):
```

#include <stdio.h>
#include <ctype.h>

int main(void)
{   
    int done = 1;

    while(done)
    {
        printf("What's your option? (y/n):");

        char input[3]; /* 3, because we want place for the character, the
                        * newline and the '\0' terminator. */
        fgets(input, 3, stdin);

        char test = tolower(input[0]); /* We get the input's first character in
                                        * lowercase. */

        switch(test)
        {
        case 'y':
            printf("\nYes!");
            done = 0;
            break;
        case 'n':
            printf("\nNo!");
            done = 0;
            break;
        default:
            printf("\nInvalid!");
            break;
        }

        printf("\n");
    }

    return 0;
}

```

EDIT: Is C your first programming language? If yes, be aware that C is a difficult language; it's meant to build systems up from ther ground and that's usually an obstacle unless you need to do that. A language like Python (among others, but that one specially) would teach much more about programming in less time... and after having learned the most basic programming techniques, you'll be ready to use that knowledge to learn C. Just a kind advice :)

---

### Post by Nemooo on 2009-01-27
You don't need an array of 3 chars, if you just want to get one char as input. The newline is only appended, if there's room for it. This works fine for reading and printing a character. And if you run it you'll see that the last character is 0:

```
#include <stdio.h>

int main(void)
{
	char arr[2];

	fgets(arr, 2, stdin);
	puts(arr);
	printf("%d", arr[1]);

	return 0;
}
```

Furthermore I often find this function useful when dealing with userinput:

```
/* Clears the buffer. Used after fgets, because fgets appends a '\n' if it
   doesn't exceed the length of the array (so there needs to be room for '\0').
   strchr returns a pointer to the occurence of '\n' and a NULL pointer if
   there's no '\n'. If there's not room for a newline the buffer contains
   letters we want erased. This is done by calling getchar until it reaches
   '\n'. If there is a '\n' it's replaced by a '\0', so the newline isn't
   printed later. */

void clear_buffer(char *input)
{
	char *i;

	i = strchr(input, '\n');

	if(i == NULL)
		while(getchar() != '\n');
	else
		*i = '\0';
}
```

---

### Post by geirha on 2009-01-27
If you do want to try ncurses, install the package, [libncurses5-dev](apt:libncurses5-dev), and read [http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/](http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/).

Remember to link against the ncurses library with -lncurses.
```

$ gcc -c prog.c
$ gcc -lncurses -o prog prog.o
$ ./prog

```

---

### Post by myromance123 on 2009-01-28
To nvteighen, thank you for your advice and help :) (yes C is my first~)
  I just want to know a bit about why you used *fgets()* instead of *gets()*, is it because you can fit the required arguments in *fgets()* which you cant with the *gets()*?
 
  Plus, from my understanding I thought that fgets() only gets strings from a file written to disk, I did not know it could be used to obtain input from the keyboard. Everything else in your code I understand.

Thank you Nemoo but I dont understand your second code :-k
 Im working on figuring it out now, sorry mate.

Thanks geirha but I think I'll stay away from ncurses for abit until I wrap my head around C better.

 I study C because I want to professionalize in it and be prepared for the foundation and degree courses Im going to take soon :)

---

### Post by nvteighen on 2009-01-28
> **myromance123 said:**
> 
  I just want to know a bit about why you used *fgets()* instead of *gets()*, is it because you can fit the required arguments in *fgets()* which you cant with the *gets()*?

Because gets() can lead to security risk. If you use it and the user happens to write more characters than the variable can hold, the buffer will overflow and you may overwrite whatever is next in memory (another variable, the return address, etc.).
 
> 
  Plus, from my understanding I thought that fgets() only gets strings from a file written to disk, I did not know it could be used to obtain input from the keyboard. Everything else in your code I understand.


C was designed with UNIX in mind... actually, both are two sides of the same project and were developed side by side vby the same people. I'm sure you know about fopen() and such, that return a (FILE *) variable and that in UNIX everything is a file. Well, stdin and stdout are declared as (FILE *) so you can use them as they were text files, one for input and the other for output. More: printf() and scanf() are just calls to fprintf(stdout, ...) or fscanf(stdin, ...).

> I study C because I want to professionalize in it and be prepared for the foundation and degree courses Im going to take soon :)

OK, I see. But anyway, I advice you to have a look (when you got some time, of course) to Python and such. It will clarify you a lot of stuff, specially to see what is just C-specific and what's not. And also, having more languages in the pocket is always better and keeps your mind open.

Good luck! ;)

---

### Post by sujoy on 2009-01-28
will not a simple

char chr;
scanf("%c",&chr);

suffice for this?

---

### Post by myromance123 on 2009-01-28
Thanks very much nvteighen :)
  Helped me a lot~

Sujoy, not too sure how Im gonna use that idea(to me i imagine it to be very long but maybe thats because Im a newbie :P )
 Anyhow Im using nvteighen's method now to fix my fflush() problems hehe

Thanks all for the quick and helpful replies :D

---

### Post by nvteighen on 2009-01-28
> **sujoy said:**
> will not a simple

char chr;
scanf("%c",&chr);

suffice for this?
No, because you may also overflow.

Look at this:
```

#include <stdio.h>
#include <ctype.h>

int main(void)
{
    int done = 1;

    while(done)
    {
        printf("What's your option? (y/n):");

        char input;
        scanf("%c", &input);

        char test = tolower(input);

        switch(test)
        {
        case 'y':
            printf("\nYes!");
            done = 0;
            break;
        case 'n':
            printf("\nNo!");
            done = 0;
            break;
        default:
            printf("\nInvalid!");
            break;
        }

        printf("\n");
    }

    return 0;
}

```

Look what happens:
```

ugi@UGI:~/Desktop$ ./over
What's your option? (y/n):e

Invalid!
What's your option? (y/n):
Invalid!
What's your option? (y/n):y

Yes!
ugi@UGI:~/Desktop$ 

```

What happened there? The first "invalid" is because of the 'e', but the second one? Because of the newline. And if the program continued after having received a valid input and asked for another prompt, the newline would get into that second prompt.

There are different possible solutions. Mine is the simplest. Another one would be to check stdin's contents after each prompt (by using a buffer)... Using ncurses's getch() solves the whole thing in one function call.

These are the cases where Perl's chomp() function makes a lot of sense :)

---

### Post by Nemooo on 2009-01-28
> **myromance123 said:**
> Thank you Nemoo but I dont understand your second code :-k
 Im working on figuring it out now, sorry mate.

strchr() returns a pointer to the first occurence of '\n' in the string (char array). If strchr find no occurence of '\n' it means that there was no room for it, so the user must have entered something that was longer than our array. Therefore there are characters in stdin, which will be read next time we call fgets. Therefore getchar() is "catching" all that extra input, so we get the desired input next time.

Hope that makes more sense.

```
void clear_buffer(char *input)
{
	char *i;

	/* i is the pointer to the occurence of '\n'. */
	i = strchr(input, '\n');

	/* If there is no '\n' get the remaining input left in stdin, so it 
	isn't taken as input later on- */
	if(i == NULL)
		while(getchar() != '\n');
	/* If there is a '\n' replace it with a '\0' because we lateron don't 
	want the '\n' printed. */
	else
		*i = '\0';
}
```

---

### Post by sujoy on 2009-01-28
@nvteighen

thanks for clearing that up. :)

---

### Post by myromance123 on 2009-01-28
Hey Nemoo I finally understand what you're saying :D
 I just had to read it back to myself  and remember what I've learnt so far~

I like that function a lot! I'am really starting to like how we can pick and choose bits and pieces of input that we want and dont want and do what we want to them in C.

Thanks mate, you made me think harder and more like a programmer :D
 You rocketh!!

Hehehe sujoy, we both learnin ;)  

  Thanks guys~

Next time I have a problem I know who to turn to :)

---

