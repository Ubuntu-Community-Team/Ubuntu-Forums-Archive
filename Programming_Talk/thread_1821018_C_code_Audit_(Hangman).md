---
title: "C code Audit (Hangman)"
date: 2011-08-08
forum: Programming Talk
---

### Post by kevinharper on 2011-08-08
Up until about a month ago, I had gone quite a few years without doing any programming at all!

Very glad to have the time to pick it back up. I started to get reacquainted with C using a few books that I had from way back in the day (2000ish, I think).

Now that I've regained some working knowledge of C, I have started to write small programs. This is the code for Hangman.

```

/* Program: Hangman
   By: Kevin Harper     Date: Aug 05, 2011 */

#include <stdio.h>
#include <string.h>

/* contant declarations */
#define NUM_TRIES_ALLOWED 7

/* function prototypes */
void clrscrn( void );
void draw_hangman( int incorrect_tries );

main()
{
   /* variable declarations */
   int num_letters       = 0, /* length of word char array */
       count             = 0, /* for word char array       */
       tries             = 0, /* total tries user has used */
       num_vis_chars     = 0, /* # of visible characters   */
       correct_guesses   = 0, /* # of correct guesses      */
       correct_flag      = 0, /* was guess correct?        */
       repeat_flag       = 0; /* was guess a repeat?       */

   char guess;

   /* array declarations */
   char word[255]              = " ";
   char hint[255]              = " ";
   char incorrect_letters[255] = " ";

   /* get word */
   puts( "Enter a word for player to guess." );
   gets( word );

   puts( "Give the player a very short hint." );
   gets( hint );

   num_letters = strlen( word );
   char visible_word[num_letters]; /* displays correct guesses */

   /* initialize visble_word */
   for( count = 0; count < num_letters; count++ )
      visible_word[count] = '-';

   visible_word[num_letters] = '\0';

   clrscrn();
   puts( "\nHANGMAN" );
   printf( "HINT: %s", hint );
   draw_hangman( tries );

   while( tries < NUM_TRIES_ALLOWED )
   {
      printf( "WORD: %s\n", visible_word );
      printf( "Incorrect Guesses: %s\n", incorrect_letters );
      printf( "\nGuess a letter (and press 'Enter'): " );
      scanf( " %c", &guess );

      /* match guess against previous guesses */
      for( count = 0; count < num_letters; count++ )
         if( guess == visible_word[count] || guess == incorrect_letters[count] )
         {
            repeat_flag  = 1;
            correct_flag = 1;
            break;
         }

      if( repeat_flag == 0 )
         /* check for matches in string */
         for( count = 0; count < num_letters; count++ )
         {
            if( guess == word[count] )
            {
               visible_word[count] = guess;
               correct_guesses++;

               if( correct_guesses == num_letters )
               {
                  puts( "\n\nCONGRATULATIONS! You guessed the word!" );
                  printf( "WORD: %s\n\n", visible_word );
                  exit( 0 );
               }

               correct_flag = 1;
            }
         }

      if( correct_flag == 0 )
      {
         incorrect_letters[tries] = guess;
         tries++;
      }

      /* reset flags */
      repeat_flag  = 0;
      correct_flag = 0;

      clrscrn();
      puts( "\nHANGMAN" );
      printf( "HINT: %s", hint );
      draw_hangman( tries );
   }

   puts( "You did not guess the word." );
   printf( "WORD: %s\n\n", visible_word );

   return 0;
}

/* clrscrn() clears the screen */
void clrscrn( void )
{
   int x = 0;

   for( x = 0; x < 20; x++ )
      printf( "\n" );
}

/* draw_hangman() displays the hangman */
void draw_hangman( int incorrect_tries )
{
/*
 ___
 |  &
 |  O
 | /|\
 | / \
 |
---
*/

   switch( incorrect_tries )
   {
      default:
      {
         puts( "\n  ___" );
         puts( " |" );
         puts( " |" );
         puts( " |" );
         puts( " |" );
         puts( " |" );
         puts( "---" );
         break;
      }

      case 1:
      {
         puts( "\n  ___" );
         puts( " |  &" );
         puts( " |" );
         puts( " |" );
         puts( " |" );
         puts( " |" );
         puts( "---" );
         break;
      }

      case 2:
      {
         puts( "\n  ___" );
         puts( " |  &" );
         puts( " |  O" );
         puts( " |" );
         puts( " |" );
         puts( " |" );
         puts( "---" );
         break;
      }

      case 3:
      {
         puts( "\n  ___" );
         puts( " |  &" );
         puts( " |  O" );
         puts( " | /" );
         puts( " |" );
         puts( " |" );
         puts( "---" );
         break;
      }

      case 4:
      {
         puts( "\n  ___" );
         puts( " |  &" );
         puts( " |  O" );
         puts( " | /|" );
         puts( " |" );
         puts( " |" );
         puts( "---" );
         break;
      }

      case 5:
      {
         puts( "\n  ___" );
         puts( " |  &" );
         puts( " |  O" );
         puts( " | /|\\" );
         puts( " |" );
         puts( " |" );
         puts( "---" );
         break;
      }

      case 6:
      {
         puts( "\n  ___" );
         puts( " |  &" );
         puts( " |  O" );
         puts( " | /|\\" );
         puts( " | /" );
         puts( " |" );
         puts( "---" );
         break;
      }

      case 7:
      {
         puts( "\n  ___" );
         puts( " |  &" );
         puts( " |  O" );
         puts( " | /|\\" );
         puts( " | / \\" );
         puts( " |" );
         puts( "---" );
         break;
      }
   }
}

```

The program compiles and runs exactly like I want it to. Can you guys audit my code? I would love to see your feedback, especially if you know of some way to make this code more compact and efficient. Was I right in using flags?

Thanks guys!

---

### Post by dwhitney67 on 2011-08-08
works?

This part of the code has a buffer overrun...
```

...
   char visible_word[num_letters]; /* displays correct guesses */

   /* initialize visble_word */
   for( count = 0; count < num_letters; count++ )
      visible_word[count] = '-';

   **visible_word[num_letters] = '\0';**
...

```
Perhaps you meant to define visible_word as an array with num_letters + 1 characters?

---

### Post by Bachstelze on 2011-08-08
First steps: compile with -std=c99 -pedantic -Wall -Werror, and when it finally compiles, run it in valgrind. That will spot the most obvious errors.

Also, for the love of everything cute and cuddly, **never** use gets! [http://en.wikipedia.org/wiki/Gets](http://en.wikipedia.org/wiki/Gets)

---

### Post by ve4cib on 2011-08-08
My first comment, after having briefly skimmed the code, is to get rid of all those "[255]" array definitions, and use a #define so that you can change the length of your arrays more easily if you ever need/want to.

And as someone mentioned above, never, ever use gets unless you have a very, very good reason.  It's prone to buffer-overflow errors if your input is too long.  fgets would be a better option.

---

### Post by kevinharper on 2011-08-08
Awesome catch, dwhitney67. And yes.. it does compile and run. So strlen doesn't include the NULL character? Will update code to declare array as "num_letters + 1".
[UPDATE]
As I was making the update on my code, I realized that it's right.

Let's say the word is "Kevin" (no quotes). num_letters = 5.
for loop stars count at 0. so it inputs "-" for 0, 1, 2, 3, 4. Five places.
I then close array off with NULL character @ visible_word[num_letters] (visible_word[5]) gets the NULL character ('\0').

So... now that I defended it... Is the code difficult to read?
[/UPDATE]

@Bachstelze: Thanks for the reply. I had never done C in linux before and I honestly have no clue what all those tags/compilation options mean. Just checked gcc man page... Yep... lots of reading for me today. Thanks a lot.

@ve4cib: I set the length to 255 because for some crazy reason I think that's the maximum amount. Is it? Whats the best way to declare the length of an array when length is uncertain and depends on user input? When should I use malloc()?

@Bachstelze & @ve4cib: Yes... I know that gets() can be dangerous... I'm reminded of that by gcc every time I compile and it generates a warning msg. I thought fgets() was for reading from a file. I'll have to look into using it to read from keyboard/stdin.

---

### Post by unknownPoster on 2011-08-08
> **kevinharper said:**
>  I thought fgets() was for reading from a file. I'll have to look into using it to read from keyboard/stdin.

stdin is a FILE pointer defined in stdio.h, there is also stdout and stderr. For your purpose you can treat them as standard files.

---

### Post by dwhitney67 on 2011-08-08
> **kevinharper said:**
> Awesome catch, dwhitney67. And yes.. it does compile and run. So strlen doesn't include the NULL character? Will update code to declare array as "num_letters + 1".
[UPDATE]
As I was making the update on my code, I realized that it's right.

Let's say the word is "Kevin" (no quotes). num_letters = 5.
for loop stars count at 0. so it inputs "-" for 0, 1, 2, 3, 4. Five places.
I then close array off with NULL character @ visible_word[num_letters] (visible_word[5]) gets the NULL character ('\0').

So... now that I defended it... Is the code difficult to read?
[/UPDATE]


Please check your response above...

Say for a 5-character word:
```

visible_word[0] = '-';   /* one */
visible_word[1] = '-';   /* two */
visible_word[2] = '-';   /* three */
visible_word[3] = '-';   /* four */
visible_word[4] = '-';   /* five */

visible_word[5] = '\0';   /* OOPS!  Buffer overrun! */

```
visible_word is declared as an array of 5 characters, indexed using values 0-4.


P.S.  Here, play with this code:
```

#include <assert.h>
int main()
{
   char array[5];
   char temp = 'a';

   array[0] = '1';
   array[1] = '2';
   array[2] = '3';
   array[3] = '4';
   array[4] = '5';

   array[5] = '\0';

   assert(temp == 'a');
   return 0;
}

```

---

### Post by Bachstelze on 2011-08-08
> **kevinharper said:**
> 
As I was making the update on my code, I realized that it's right.

Let's say the word is "Kevin" (no quotes). num_letters = 5.
for loop stars count at 0. so it inputs "-" for 0, 1, 2, 3, 4. Five places.
I then close array off with NULL character @ visible_word[num_letters] (visible_word[5]) gets the NULL character ('\0').

So... now that I defended it... Is the code difficult to read?
[/UPDATE]

No it's not right. Your array has 5 elements. You are trying to write to the 6th element. Since there is no 6th element, your program will overwrite whatever byte is stored just after the array in memory.

> @ve4cib: I set the length to 255 because for some crazy reason I think that's the maximum amount. Is it? Whats the best way to declare the length of an array when length is uncertain and depends on user input? When should I use malloc()?

255 is entirely reasonable to use as a maximum, there is no word in English that has more than 255 characters. Your problem is what happens if the user enters more than 255 characters? Personally, I'll just say "hey dude what the hell do you think you're doing here?" and just discard the extra characters.

> @Bachstelze & @ve4cib: Yes... I know that gets() can be dangerous... I'm reminded of that by gcc every time I compile and it generates a warning msg. I thought fgets() was for reading from a file. I'll have to look into using it to read from keyboard/stdin.

When there is a warning, you should deal with it before proceeding. No exceptions.

---

### Post by kevinharper on 2011-08-08
Kudos dwhitney67 for highlighting my flaw. Thanks (cc Bachstelze).

@Bachstelze: Will make sure to deal w/ the warnings just as I deal w/ the errors. I'll start using more compilation options (as Bachstelze suggested).

@unknownPoster Thanks for your response about std's and fgets(). Will definitely suspend the use of gets().

Thanks for the input guys. It's greatly appreciated.

---

