---
title: "getchar() question"
date: 2008-01-11
forum: Programming Talk
---

### Post by Will B-R on 2008-01-11
I have the book The C Programming Language second edition.

I was given the following code in the book.
[PHP]
#include <stdio.h>

main ()
{
	int c;
	
	while ((c = getchar()) != EOF)
		putchar(c);
} 
[/PHP]

The book seems to imply that it will print each char one at a time; which it does, however it also prints it out a second time on a new line once I hit enter or C-d.

I have no idea why this is happening.

I can also use backspace when entering the first line; this also seems unexpected.

The following is the output.
[PHP]will@will-desktop:~/Programming/C/getchar$ ./a.out 
this is a test
this is a test
will@will-desktop:~/Programming/C/getchar$ [/PHP]

---

### Post by LaRoza on 2008-01-11
I don't understand what you mean. It does exactly what it is supposed to do.

Could you clarify what is unexpected?

If you don't understand that code, I suggest brushing up on C from something other than K&R.
[php]
#include <stdio.h> 

int main (int args,char ** argv) 
{ 
    int c; 
    while ((c = getchar()) != EOF) 
        putchar(c); 
} [/php]

It is a loop that gets a char (getchar()) until it reaches the EOF (end of file, or Ctrl + D). When you type a line in the program then press "enter", the it loops through the input, putting each char (putchar()) to the screen, then loops again (where it waits for more characters).

---

### Post by stroyan on 2008-01-11
You are seeing the effects of the 'termio' terminal driver interface in 'cooked' or 'canonical' mode.  Characters that you type are echoed back by the kernel device driver before your program ever sees them.  Only typing return or <ctrl>D will cause the characters to become readable by the program.

You can control what processing is done by the kernel using the termios functions or the stty command.  See 'man termios' and 'man stty' for details.  See [http://tldp.org/HOWTO/Serial-Programming-HOWTO/](http://tldp.org/HOWTO/Serial-Programming-HOWTO/) for digestible details. ;-)
The term 'serial' is a bit deceptive.  Almost all of the interface applies to any terminal type such as a pty used by gnome-terminal.

---

### Post by popch on 2008-01-11
I think the OP is somewhat surprised that the text entered appears twice on the console.

IOW, the OP 
- expected the output **abcdef**
- got the output **abcdefabcdef**

To be honest, I would have expected **aabbccddeeff**

---

### Post by YourSurrogateGod on 2008-01-11
> **Will B-R said:**
> I have the book The C Programming Language second edition.

I was given the following code in the book.
[PHP]
#include <stdio.h>

main ()
{
	int c;
	
	while ((c = getchar()) != EOF)
		putchar(c);
} 
[/PHP]

The book seems to imply that it will print each char one at a time; which it does, however it also prints it out a second time on a new line once I hit enter or C-d.

I have no idea why this is happening.

I can also use backspace when entering the first line; this also seems unexpected.

The following is the output.
[PHP]will@will-desktop:~/Programming/C/getchar$ ./a.out 
this is a test
this is a test
will@will-desktop:~/Programming/C/getchar$ [/PHP]

I think I understand why you're confused.

I got the same result:
```
ysg@ysger:~/Desktop/My Documents/Programming/C/test$ ./main
foo
foo
bar
bar
foobar
foobar
ysg@ysger:~/Desktop/My Documents/Programming/C/test$
```

My guess that it's when you start it and when it begins to execute and you begin typing, you think that it's reading what you type (the very moment, or close to it, that you hit a key on your keyboard) and then as soon as possible spitting it out on the screen, yes? When you enter something on the console, the program is in a state where it's waiting for input, it's not reading your input at the same time that you're typing :) .

Similar to when you get to a point with a function like scanf, it waits for you to input something before executing.

Here is some info on getchar:
[http://www-ccs.ucsd.edu/c/stdio.html#getchar](http://www-ccs.ucsd.edu/c/stdio.html#getchar)

---

### Post by wolfbone on 2008-01-11
It's because of a combination of stream buffering and terminal I/O behaviour (cf stroyan's comment). To get what I think you were expecting, you could do something like this:

[PHP]
     #include <unistd.h>
     #include <stdio.h>
     #include <stdlib.h>
     #include <termios.h>

     /* Use this variable to remember original terminal attributes. */

     struct termios saved_attributes;

     void
     reset_input_mode (void)
     {
       tcsetattr (STDIN_FILENO, TCSANOW, &saved_attributes);
     }

     void
     set_input_mode (void)
     {
       struct termios tattr;
       char *name;

       /* Make sure stdin is a terminal. */
       if (!isatty (STDIN_FILENO))
         {
           fprintf (stderr, "Not a terminal.\n");
           exit (EXIT_FAILURE);
         }

       /* Save the terminal attributes so we can restore them later. */
       tcgetattr (STDIN_FILENO, &saved_attributes);
       atexit (reset_input_mode);

       /* Set the funny terminal modes. */
       tcgetattr (STDIN_FILENO, &tattr);
       tattr.c_lflag &= ~(ICANON|ECHO); /* Clear ICANON and ECHO. */
       tattr.c_cc[VMIN] = 1;
       tattr.c_cc[VTIME] = 0;
       tcsetattr (STDIN_FILENO, TCSAFLUSH, &tattr);
     }

     int
     main (void)
     {
       char c;

       set_input_mode ();

       setvbuf(stdout,NULL,_IONBF,1);

       while (1)
         {
           read (STDIN_FILENO, &c, 1);
           if (c == '\004')          /* `C-d' */
             break;
           else 
             putchar (c);
         }

       return EXIT_SUCCESS;
     }

[/PHP]

The bulk of that - all except the setvbuf(..) - is an example in the primary reference for GNU libc - the info pages.

It's a shame so few people seem to know where the right documentation is these days. No wonder code quality seems to be dropping. </rant>

---

### Post by Will B-R on 2008-01-12
Ok, I'll have a read through that once I get home from work tonight.

I guess this happened because the C implementation in GCC is different to my old book? I seems to happen on both windows and in linux.

Wolf your code works just like it was implied in the book. Thanks.

---

