---
title: "C Code Audit (Tic Tac Toe)"
date: 2011-08-09
forum: Programming Talk
---

### Post by kevinharper on 2011-08-09
I had an awesome experience w/ <a href="http://ubuntuforums.org/showthread.php?t=1821018">my last audit request</a>. I've decided to post another 'game' I wrote using C. I hope you guys can take a look at all (if not, bits and pieces) of the code and let me know what you would do differently. How can this code/game be improved? What noob-mistakes am I making? and so on.

Thank you all of your time. I appreciate your input.

Here is the source code:
```

/* Tic-Tac-Toe
   Kevin Harper :: Aug 08, 2011 */

#include <stdio.h>

/* array/string declarations */
char a1 = ' ',
     a2 = ' ',
     a3 = ' ',
     b1 = ' ',
     b2 = ' ',
     b3 = ' ',
     c1 = ' ',
     c2 = ' ',
     c3 = ' ';

/* function prototypes */
void clrscrn( void );
void top_coords( void );
void dashes( void );
int  check_position( int pos );
void place_mark( int pos, char mark );
int  check_winner( void );
int  check_tie( void );

main()
{
   /* variable declarations */
   char coordinates[3] = " "; /* where to place mark */
   char x_o            = 'X'; /* X goes first */

   int taken_flag   = 0, /* flag = 1 if spot already used */
       invalid_flag = 0, /* flag = 1 if user select spot outside of c3 range */
       position     = 0,
       winner       = 0,
       tie          = 0;

   do
   {
      /* display board */
      clrscrn();

      if( taken_flag == 1 )
      {
         printf( "That spot is already taken.\n\n" );
         taken_flag--;
      }

      if( invalid_flag == 1 )
      {
         printf( "Invalid entry.\n\n" );
         invalid_flag--;
      }

      top_coords();
      printf( "1  %c | %c | %c\n", a1, b1, c1 );
      dashes();
      printf( "2  %c | %c | %c\n", a2, b2, c2 );
      dashes();
      printf( "3  %c | %c | %c\n", a3, b3, c3 );

      printf( "Where would you like to the %c?\n", x_o );
      puts( "Type a letter-number combination (example: a1) and hit 'Enter'." );
      gets( coordinates );

      coordinates[2] = '\0';

      /* set position from coordinates */
      if( coordinates[0] == 'a' && coordinates[1] == '1' )
         position = 1;

      else if( coordinates[0] == 'b' && coordinates[1] == '1' )
         position = 2;

      else if( coordinates[0] == 'c' && coordinates[1] == '1' )
         position = 3;

      else if( coordinates[0] == 'a' && coordinates[1] == '2' )
         position = 4;

      else if( coordinates[0] == 'b' && coordinates[1] == '2' )
         position = 5;

      else if( coordinates[0] == 'c' && coordinates[1] == '2' )
         position = 6;

      else if( coordinates[0] == 'a' && coordinates[1] == '3' )
         position = 7;

      else if( coordinates[0] == 'b' && coordinates[1] == '3' )
         position = 8;

      else if( coordinates[0] == 'c' && coordinates[1] == '3' )
         position = 9;

      else
      {
         invalid_flag = 1;
         continue;
      }

      taken_flag = check_position( position );

      if( taken_flag == 0 )
         place_mark( position, x_o );

      else
         continue;

      winner = check_winner();

      if( winner == 1 )
      {
         clrscrn();
         printf( "CONGRATULATIONS! %c's have won!\n", x_o );

         top_coords();
         printf( "1  %c | %c | %c\n", a1, b1, c1 );
         dashes();
         printf( "2  %c | %c | %c\n", a2, b2, c2 );
         dashes();
         printf( "3  %c | %c | %c\n", a3, b3, c3 );

         break;
      }

      else
         tie = check_tie();

      if( tie == 1 )
      {
         clrscrn();
         puts( "IT'S A DRAW!" );

         top_coords();
         printf( "1  %c | %c | %c\n", a1, b1, c1 );
         dashes();
         printf( "2  %c | %c | %c\n", a2, b2, c2 );
         dashes();
         printf( "3  %c | %c | %c\n", a3, b3, c3 );

         break;
      }

      /* toggle between X and O */
      if( x_o == 'X' )
         x_o = 'O';

      else
         x_o = 'X';

   } while( 1 );

}

/* clrscrn() clears the screen */
void clrscrn( void )
{
   int x = 0;

   for( x = 0; x < 20; x++ )
      printf( "\n" );
}

/* ASCII Tic Tac Toe Grid

   a   b   c

1    |   |
  ---+---+---
2    |   |
  ---+---+---
3    |   |

*/

/* top_coords() displayes letters at the top.
   Lets players select column on which to place mark. */
void top_coords( void )
{
   int count = 0;

   for( count = 0; count < 13; count++ )
   {
      if( count == 3 )
         printf( "a" );
      else if( count == 7 )
         printf( "b" );
      else if( count == 11 )
         printf( "c" );
      else
         printf( " " );
   }

   printf( "\n\n" );
}

/* dashes() prints horizontal separators */
void dashes( void )
{
   /* variable declarations */
   int count = 0;

   printf( " " );

   for( count = 0; count < 13; count++ )
   {
      if( count % 4 == 0 && count != 0 && count != 12)
         printf( "+" );
      else if( count > 0 && count != 12 )
         printf( "-" );
      else
         printf( " " );
   }

   printf( "\n" );
}

/* check_position() checks slot indicated by user.
   Returns 0 if empty/1 if taken. */
int check_position( int pos )
{
   /* variable declarations */
   int taken = 0;

   switch ( pos )
   {
      case 1:
         if( a1 != ' ' )
            taken = 1;
         break;

      case 2:
         if( b1 != ' ' )
            taken = 1;
         break;

      case 3:
         if( c1 != ' ' )
            taken = 1;
         break;

      case 4:
         if( a2 != ' ' )
            taken = 1;
         break;

      case 5:
         if( b2 != ' ' )
            taken = 1;
         break;

      case 6:
         if( c2 != ' ' )
            taken = 1;
         break;

      case 7:
         if( a3 != ' ' )
            taken = 1;
         break;

      case 8:
         if( b3 != ' ' )
            taken = 1;
         break;

      default: /* if pos = 9 */
         if( c3 != ' ' )
            taken = 1;
         break;
   }

   return taken;
}

/* place_mark() places X or O into the slot indicated by user.
   Takes position and returns 0 if successful/1 if slot previously used. */
void  place_mark( int pos, char mark )
{
   switch( pos )
   {
      case 1:
         a1 = mark;
         break;

      case 2:
         b1 = mark;
         break;

      case 3:
         c1 = mark;
         break;

      case 4:
         a2 = mark;
         break;

      case 5:
         b2 = mark;
         break;

      case 6:
         c2 = mark;
         break;

      case 7:
         a3 = mark;
         break;

      case 8:
         b3 = mark;
         break;

      default: /* if pos = 9 */
         c3 = mark;
         break;
   }         
}

/* check_winner() checks to see if last turn won the game */
int check_winner( void )
{
   int win = 0;

   /* horizontal checks */
   if( a1 != ' ' && a1 == a2 && a1 == a3 )
      win = 1;

   else if( a2 != ' ' && a2 == b2 && a2 == c2 )
      win = 1;

   else if( a3 != ' ' && a3 == b3 && a3 == c3 )
      win = 1;

   /* vertical checks */
   else if( a1 != ' ' && a1 == b1 && a1 == c1 )
      win = 1;

   else if( a2 != ' ' && a2 == b2 && a2 == c2 )
      win = 1;

   else if( a3 != ' ' && a3 == b3 && a3 == c3 )
      win = 1;

   /* diagnal checks */
   else if( a1 != ' ' && a1 == b2 && a1 == c3 )
      win = 1;

   else if( a3 != ' ' && a3 == b2 && a3 == c1 )
      win = 1;

   /* no winner yet */
   else
      win = 0;

   return win;
}

/* check_tie() checks to see if game is a draw */
int check_tie( void )
{
   int tie = 0;

   if( a1 != ' ' && b1 != ' ' && c1 != ' '
       && a2 != ' ' && b2 != ' ' && c2 != ' '
       && a3 != ' ' && b3 != ' ' && c3 != ' ' )
      tie = 1;

   return tie;
}

```

---

### Post by unknownPoster on 2011-08-09
Follow the advice in that thread. Compile it with  the "-pedantic -Wall -Werror" flags and you'll find a good many things you need to fix. Just as a start, you should have "int main()" rather than just "main()" and it should also explicitly return an int. Look up EXIT_SUCCESS for this.

---

### Post by kevinharper on 2011-08-09
Which of the following do you guys suggest:

```

int main()
{
   /* some code */

   return 0;
}

```
or
```

void main( void )
{
   /* some code */
}

```

The book I am learning C from (bought back in 2000ish) usually just has
```

main()
{
   /* some code */

   return 0;
}

```
This is just how I have it in the tic-tac-toe code - picked up the habit from the book. But using certain options while compiling it generates warning or errors that "gcc -c" normally overlooks.

What is your guys' preference? Under what circumstances can I expect main()'s return value to mean something? Why not just use void main( void ) all the time?

---

### Post by kevinharper on 2011-08-09
Just compiled with those options plus "-std=c99"... 1 error - "int" before "main()" and not returning a value.

I also got a warning for using "gets()" when linking the program.

I was about done with tic-tac-toe yesterday when I posted the code for hangman yesterday. I opened up the book this morning to see where I was at and noticed that "fgets()" is explained in a couple more paragraphs. :)

Thanks a lot. Where else did I go wrong?

---

### Post by Bachstelze on 2011-08-09
> **kevinharper said:**
> 
The book I am learning C from (bought back in 2000ish) usually just has
```

main()
{
   /* some code */

   return 0;
}

```
This is just how I have it in the tic-tac-toe code - picked up the habit from the book.

That's a bad habit and you should get rid of it. The correct form is

```
int main(void)
```

or

```
int main(int argc, char **argv)
```

if you want to use the commad-line arguments. It's not a matter of "preference", it's required by the standard. The return value is passed to the caller process (usually a shell) as the return error code of the program. An error code of 0 usually means the program ran successfully, and anything else means there was some kind of error.

Also for heaven's sake don't use gets! I'm not helping you further until you fix that.

---

### Post by kevinharper on 2011-08-09
Awesome.. Thanks for the thorough explanations about why I must declare main() just like any other function.

And I promise you never to use gets(), ever again. As stated above, I had already written this code yesterday when I posted the hangman code. I will never use gets() in the future - I promise.

I will also use
```

#include <stdio.h>
#include <stdlib.h> /* for exit constant */

int main( void )
{
   /* some code */

   return( EXIT_SUCCESS ); /* or EXIT_FAILURE */
}

```
I read somewhere that these phrases (as opposed to 0 or 1) are for portability. Something about how most read 0 as successful but some may be looking for 1 as successful.

Once again, guys... thanks a lot.

---

### Post by JupiterV2 on 2011-08-09
I didn't really look past the first couple of lines but I have a few observations over and above what others have already said.

1) You could simplify your play area a bit using the following:
```
char game_board[3][3] = {
  {' ', ' ', ' '},
  {' ', ' ', ' '},
  {' ', ' ', ' '}};
```

Or you could use memset, since the memory would be contiguous:

```
#include <string.h>

char game_board[3][3];
memset(game_board, ' ', 9);
```

Also, you could use a struct, or even a bit-field, for your flags:

```
#include <stdio.h>

#define OFF 0
#define ON  1

typedef struct _Flags {
    int flag1 : 2;
    int flag2 : 2;
    int flag3 : 2;
} Flags;

int main (void)
{
    Flags f = {OFF, ON, OFF}; /* set default values */
    
    f.flag1 = ON;
    f.flag2 = OFF;
    f.flag3 = ON;
    
    printf ("sizeof (f) = %d\n", sizeof (f));
    printf ("flag 1 set? %s\n", f.flag1 == ON ? "yes" : "no");
    printf ("flag 2 set? %s\n", f.flag2 == ON ? "yes" : "no");
    printf ("flag 3 set? %s\n", f.flag3 == ON ? "yes" : "no");

    return 0;
```

The last example might be a little advanced but something to look to in the future.

---

### Post by kevinharper on 2011-08-09
@JupiterV2 VERY COOL! THanks!

I thought about a multidimensional array but I haven't really done anything with 'em yet so I decided to stay away from them. But it would be a nice thing to incorporate in v2.0. :)

I REALLY like how you defined ON/OFF.

Your example is indeed advanced but very helpful. I'll do my best to dissect it until I can digest it. Thanks a lot.

---

### Post by Bachstelze on 2011-08-09
The ON/OFF thing seems a bit redundant. Just include stdbool.h and use true/false.

---

### Post by kevinharper on 2011-08-10
Nice, Bachstelze! Will use those instead.

---

### Post by kevinharper on 2011-08-10
So this book has just given me yet ANOTHER cool way to use gets()... Flush out stdin! :D

Of course, I'm joking. Sort of.. it does suggest this use but talks about fflush() a couple of paragraphs later.

Seriously guys... thanks for all of your input. Learned a ton.

---

### Post by Bachstelze on 2011-08-10
This book is terrible, you should throw it in the recycle bin where it belongs.

---

### Post by kevinharper on 2011-08-10
LOL.. just thought of that, actually!

So I finish reading about fflush() and how I can use it to clear stdin, I compile the program without any warnings or errors. I run it and it doesn't clear the stream. I read up on fflush() and find that "One frequently suggested way of doing this is by using fflush(stdin). This is incorrect, and should be avoided" (faq.cprogramming.com).

It basically says there's no standard way to clear stdin stream.

What to do? No prob, right? fgets( var_name, MAX, stdin) limits size of var_name to MAX-1 and everything else is basically thrown out, right?

The cool thing about this book is that I'm almost done with it (about 3/4s of the way through it). I have a few others that are more specific (data structures, problem solving techniques, etc). This has really been a pretty good intro book.

---

### Post by unknownPoster on 2011-08-10
> **kevinharper said:**
>  This has really been a pretty good intro book.

No offense but if the code you've posted is indicative of the quality of the book then it most definitely is not a good book...

---

### Post by Bachstelze on 2011-08-10
> **kevinharper said:**
> 
What to do? No prob, right? fgets( var_name, MAX, stdin) limits size of var_name to MAX-1 and everything else is basically thrown out, right?


No, it will stay in the input buffer. See this program:

```
firas@aoba ~ % cat test.c                                        
#include <stdio.h>

int main(void)
{
        char foo[5];
        char bar[5];
        char baz[256];
        printf("foo? ");
        fgets(foo, 5, stdin);
        printf("bar? ");
        fgets(bar, 5, stdin);
        printf("baz? ");
        fgets(baz, 256, stdin);
        printf("foo: %s\nbar: %s\nbaz: %s\n", foo, bar, baz);
        return 0;
}

firas@aoba ~ % cc -std=c99 -pedantic -Wall -Werror -o test test.c
firas@aoba ~ % ./test                                            
foo? supercalifragilisticexpialidocious
bar? baz? foo: supe
bar: rcal
baz: ifragilisticexpialidocious

```

Since the first call to fgets only reads 4 characters, all the other characters have not been read, and when I make another call to fgets (or any other function that reads from stdin) later, it will read those characters, and if enough characters are available, it will not let me input anything. An almost-standard way to discard the input is to call getchar repeatedly until you reach the last character, which when you read from stdin is a newline (when you read from a file it would be EOF):

```
firas@aoba ~ % cat test.c 
#include <stdio.h>
#include <string.h>

int main(void)
{
        char foo[5];
        char bar[5];
        printf("foo? ");
        fgets(foo, 5, stdin);
        /* 
         * If the last character of the string is not newline,
         * it means there are unread characters, so we call getchar
         * to get rid of them until we reach the newline.
         */
        if (foo[strlen(foo)-1] != '\n') {
                while (getchar() != '\n')
                        ;
        }
        printf("bar? ");
        fgets(bar, 5, stdin);
        printf("foo: %s\nbar: %s\n", foo, bar);
        return 0;
}

firas@aoba ~ % cc -std=c99 -pedantic -Wall -Werror -o test test.c
firas@aoba ~ % ./test                                            
foo? supercalifragilisticexpialidocious
bar? bar  
foo: supe
bar: bar


```

*EDIT:* So you could have a function like this:

```
/*
 * Equivalent to fgets, except that it will read from stdin and
 * discard all leftover input characters.
 */
char *my_fgets(char *s, int size)
{
        char *res = fgets(s, size, stdin);
        if (res == NULL) {
                return NULL;
        }
        if (s[strlen(s)-1] != '\n') {
                while (getchar() != '\n')
                        ;
        }
        return res;
}

```

---

### Post by kevinharper on 2011-08-10
@unknownPoster My problem is a lack of practice... and yes, most of my habits come from continually seeing them in the book's examples.

It's one of those "learn in 21 days" ones and it's a couple of editions old. But I learn quick... By looking at others' code and reading online threads I'll start to get a pretty good idea of what to do (and not do). I appreciate your help a lot. Thank you.

@Bachstelze Awesome. I was just about to let you know that I was wrong (as you pointed out). I was then going to look for a way to flush the stream.

Here's an example that is similar to the one you posted: [http://faq.cprogramming.com/cgi-bin/smartfaq.cgi?answer=1044873249&id=1043284392](http://faq.cprogramming.com/cgi-bin/smartfaq.cgi?answer=1044873249&id=1043284392).

They have:
```

while ((ch = getchar()) != '\n' && ch != EOF);

```

I like that they check for EOF.

Maybe this will work:
```

if( foo[strlen( foo ) - 1] != '\n')
{
   while( ( ch = getchar() ) != '\n' && ch != EOF )
      ;
}

```
I'll stick it in a "clear_stream()" function and use it that way.

Thanks a lot.

---

### Post by kevinharper on 2011-08-10
Just saw your edit/update... Very cool function.

---

### Post by Bachstelze on 2011-08-10
> They have:
```

while ((ch = getchar()) != '\n' && ch != EOF);

```

Be careful if you do that, ch must be declared as an int, not as a char!

*EDIT:* Also note that "if last character is not newline, it means we have unread characters" works only if you're reading from stdin. If you're reading from a file, it is perfectly possible that the last character of the file is not a newline. Also even if you're reading from stdin, it is possible that the input stream will be "cut" (making fgets read EOF, not a newline)... Interactive input is probably the most problematic thing in C.

---

### Post by kevinharper on 2011-08-10
> **Bachstelze said:**
> Be careful if you do that, ch must be declared as an int, not as a char!
Okay... Just checked getchar()'s prototype and it returns an int - hence your recommendation.

> **Bachstelze said:**
> Interactive input is probably the most problematic thing in C.
I'm beginning to see that.

---

### Post by Bachstelze on 2011-08-11
> **kevinharper said:**
> Okay... Just checked getchar()'s prototype and it returns an int - hence your recommendation.


And it returns an int for a reason, so it's not just a "recommendation". If you declare it as a char, your program will not work correctly in some cases.

---

### Post by Odexios on 2011-08-11
> **Bachstelze said:**
> And it returns an int for a reason, so it's  not just a "recommendation". If you declare it as a char, your program  will not work correctly in some cases.What cases?

I've always been told I could just cast getchar's return value to char without consequences. What can go wrong?

---

### Post by Bachstelze on 2011-08-11
> **Odexios said:**
> What cases?

I've always been told I could just cast getchar's return value to char without consequences. What can go wrong?

There are 257 possible return values for getchar: all 256 char's plus EOF. A char can only have 256 different values, so when EOF is cast to a char, it will always have the same value as one of the 256 char's. If you read a character that has this value, it will be mistaken for EOF.

For example on an x86 Linux system, EOF is -1, i.e. 0xFFFFFFFF. If you cast it to a char, it will be 0xFF. Now if the character 0xFF is read from the input, getchar will return 0x000000FF. Cast it to a char, it will be 0xFF. So if you cast the return value of getchar to a char and get 0xFF, you have no way to know if EOF or the 0xFF character was read.

You can cast the return value of getchar to a char only after you make sure it is not EOF.

---

### Post by kevinharper on 2011-08-11
Thanks for your explanation Bachstelze... The following made some sense, but I admit I didn't fully get it:

> "If the integer value returned by getchar() is stored into a variable of type char and then compared against the integer constant EOF, the comparison may never succeed, because sign-extension of a variable of type char on widening to integer is implementation-defined."
From: [http://pubs.opengroup.org/onlinepubs/009695399/functions/getchar.html](http://pubs.opengroup.org/onlinepubs/009695399/functions/getchar.html)

---

### Post by Bachstelze on 2011-08-11
Hmm....

> 6.3.1.3 Signed and unsigned integers

1. When a value with integer type is converted to another integer type other than _Bool, **if the value can be represented by the new type, it is unchanged**.

Any char value can also be represented as an int, so the result of the conversion is that the int will have the same value as the char, this is not implementation defined...

*EDIT: However, the result of casting any int greater than 127 or smaller than -128 to a char is implementation-defined, maybe that's what was meant here.*

*EDIT 2: So actually it's a bad idea to cast the return value of getchar to a char at all, you should cast it to an unsigned char instead (after ensuring that it is not EOF).*

It is true, however, that the comparison may never succeed. If EOF is defined as -129, when you convert it to a char and then back to an int, it will not compare equal to the original value, because -129 cannot be represented as a char.

---

### Post by Bachstelze on 2011-08-11
A real-life example of what can happen (on Linux x86): let's say I have this input file:

```
firas@wakaba ~ % cat test.txt                                      
supercalifragilistic&#65533;expialidocious

```

The "diamond" is a 0xFF character, you can see it for example by printing the file in hexadecimal with od:

```
firas@wakaba ~ % cat test.txt | od -t x1
0000000 73 75 70 65 72 63 61 6c 69 66 72 61 67 69 6c 69
0000020 73 74 69 63 ff 65 78 70 69 61 6c 69 64 6f 63 69
0000040 6f 75 73 0a
0000044

```

If I have this program to count the number of characters in the file, it will mistake the 0xFF character for EOF:

```
firas@wakaba ~ % cat test.c                                        
#include <stdio.h>

int main(void)
{
    char ch;
    int n = 0;
    while ((ch = getchar()) != EOF) {
        n++;
    }
    printf("%d characters were read.\n", n);
    return 0;
}
firas@wakaba ~ % cc -std=c99 -pedantic -Wall -Werror -o test test.c
firas@wakaba ~ % cat test.txt| ./test 
20 characters were read.

```

While this one will behave correctly:

```
firas@wakaba ~ % cat test.c                                        
#include <stdio.h>

int main(void)
{
    int ch;
    int n = 0;
    while ((ch = getchar()) != EOF) {
        n++;
    }
    printf("%d characters were read.\n", n);
    return 0;
}
firas@wakaba ~ % cc -std=c99 -pedantic -Wall -Werror -o test test.c
firas@wakaba ~ % cat test.txt| ./test                              
36 characters were read.

```

An attacker could exploit the wrong behaviour of the first one: let's say you use a similar function to get the number of characters in the file, then allocate a buffer to read the file data into. An attacker could trick your program into believing the file is smaller than it actually is, then your buffer would be too small to hold the contents of the actual file, and you would have a buffer overflow when you read the file data into it.

---

