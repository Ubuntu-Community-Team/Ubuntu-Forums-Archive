---
title: "C Code Audit (Hangman II)"
date: 2011-08-25
forum: Programming Talk
---

### Post by kevinharper on 2011-08-25
Here's my second version of Hangman:
```

/* Hangman ver. II
   Kevin Harper :: August 22, 2011 */

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <stdbool.h>

/* constant declarations */
#define MAX             255
#define INC_GUESS_LIMIT   7 /* Limit of Incorrect Guesses
                                  7 wrong guesses completes hangman */

/* function prototypes */
void clrscrn( void );
void clrstdin( void );
int is_letter( char g );
void draw_hangman( int incorrect_tries );

int main( void )
{
   /* variable declarations */
   int num_players       = 0, /* # of players */
       player            = 1, /* determine turn */
       player1_pts       = 0,
       player2_pts       = 0,
       num_wrong_guesses = 0,
       word_length       = 0, /* length of word that is to be guessed */
       ltr               = 0; /* determines if guess is a letter */

   char guess = ' ';

   bool flag_correct_guess = false, /* guess is correct */
        flag_win           = false, /* word was guessed */
        flag_lose          = false, /* word was not guessed */
        flag_repeat        = false;  /* check duplicate guesses */

   /* string/array declarations */
   char word[MAX]                          = " ",
        hint[MAX]                          = " ",
        wrong_guesses[INC_GUESS_LIMIT + 1] = " "; /* holds wrong guesses */

   /* pointer declarations */
   char *correct_guesses , /* holds correct guesses */
        *newline,
        *ch;

   do
   {
      while( num_players != 1 && num_players != 2 )
      {
         clrscrn();

         printf( "Are there 1 or 2 players?\n" );
         printf( "Press any other key to quit.\n" );
         scanf( "%d", &num_players );

         clrstdin();

         if( num_players == 0 )
            exit( EXIT_SUCCESS );

         clrscrn();

      }

      if( num_players == 2 )
      {
         printf( "Player %d: Enter a word for your opponent to guess.\n", player );
         fgets( word, sizeof( word ), stdin );

         newline = strchr(word, '\n'); /* check for trailing newline char */

         if( newline )
            *newline = '\0';   /* replace newline with a null character */

         printf( "Enter a short hint.\n" );
         fgets( hint, MAX, stdin );

         newline = strchr(word, '\n'); /* check for trailing newline char */

         if( newline )
            *newline = '\0';   /* replace newline with a null character */

         /* define and initialize correct_guesses */
         word_length = strlen( word );
         correct_guesses = (char *) malloc( word_length + 1 );

         for(int i = 0; i < word_length; i++ )
            correct_guesses[i] = '-';

      }

      else
      {
         /* get random word & hint from another file */
      }

      while( flag_win == false && flag_lose == false )
      {
         clrscrn();

         /* display hangman and prompt for guesses */
         puts( "HANGMAN by Kevin Harper (http://www.kevinharper.com/)" );
         draw_hangman( num_wrong_guesses );
         printf( "HINT: %s\n", hint );
         printf( "\n" );
         printf( "WORD: %s\n", correct_guesses );
         printf( "Wrong Guesses: %s\n", wrong_guesses );
         puts( "Guess a letter." );
         scanf( "%c", &guess );

         clrstdin();

         ltr = is_letter( guess );

         /* check that guess is a letter */
         while( ltr == 0 )
         {
            puts( "You must enter a letter. Please try again." );
            puts( "Guess a letter." );
            guess = getchar();

            clrstdin();

            ltr = is_letter( guess );
         }

         /* check to see if duplicate guess */
         do
         {
            if( flag_repeat == true )
            {
               flag_repeat = false;

               puts( "You have already tried this character." );
               puts( "Try again. Guess another letter." );
               guess = getchar();

               clrstdin();

               ltr = is_letter( guess );
            }

            /* check that guess is a letter */
            while( ltr == 0 )
            {
               puts( "You must enter a letter. Please try again." );
               puts( "Guess a letter." );
               guess = getchar();

               clrstdin();

               ltr = is_letter( guess );
            }

            ch = strchr( correct_guesses, guess );

            if( ch )
               flag_repeat = true;

            ch = strchr( wrong_guesses, guess );

            if( ch )
               flag_repeat = true;

         } while( flag_repeat == true );

         /* look through word and compare to guess */
         for( int i = 0; i < word_length; i++ )
         {
            if( word[i] == guess || word[i] == guess - 32 )
            {
               correct_guesses[i] = guess;
               flag_correct_guess = true;
            }
         }

         /* check to see if word has been guessed */
         ch = strchr( correct_guesses, '-' );

         if( ch == NULL )
         {
            puts( "Congratulations! You guessed right!" );
            printf( "WORD: %s\n", word );
            flag_win = true;

            if( player == 1 )
               player2_pts++;

            if( player == 2 )
               player1_pts++;
            
         }

         if( flag_correct_guess == false )
         {
            wrong_guesses[num_wrong_guesses] = guess;
            num_wrong_guesses++;

            if( player == 1 )
               player1_pts++;

            if( player == 2 )
               player2_pts++;

         }

         /* check to see if failed to guess word */
         if( num_wrong_guesses == INC_GUESS_LIMIT )
         {
            draw_hangman( num_wrong_guesses );
            puts( "Too bad! You did not guess the word!" );
            printf( "WORD: %s\n", word );
            flag_lose = true;
         }

         /* reset flag_correct_guess */
         if( flag_correct_guess == true )
            flag_correct_guess = false;

      }

   printf( "\n" );
   printf( "Player 1 pts: %d\n", player1_pts );
   printf( "Player 2 pts: %d\n", player2_pts );

   /* reset flags and switch players */
   flag_win  = false;
   flag_lose = false;
   player == 1 ? player++ : player--;
   num_wrong_guesses = 0;
   ltr = 0;

   } while ( 1 );

   return EXIT_SUCCESS;
}

/* clrscrn() prints 30 newlines on console (clears screen) */
void clrscrn( void )
{
   for( int x = 0; x < 30; x++ )
      printf( "\n" );
}

/* clrstdin() clear any leftover chars tha may be in stdin stream */
void clrstdin( void )
{
   int ch = 0;

   while( ( ch = getchar() ) != '\n' && ch != EOF )
         ;
}

/* is_letter() verifies guess is a letter */
int is_letter( char g )
{
   int letter = 0;

   if( ( g >= 'a' && g <= 'z' ) || ( g >= 'A' && g <= 'Z' ) )
      letter = 1;

   return letter;
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
I just finished it, it took me a while to get some of the checks working... unlike my previous version ( [http://ubuntuforums.org/showthread.php?t=1821018](http://ubuntuforums.org/showthread.php?t=1821018) ), this new version allows two people to play against each other. The program knows whose turn it is and it even keeps score. I have not added the random grab of words/hints from a file for when there is only one player but I will throw that up on this thread as soon as I do it.

As I completed the program a few minutes ago I noticed that a lot of the code within main() is repeat and could very easily be turned into functions. This is a definite step for version III.

I am very open to critique. :) Please let me know what you think of the code itself - clean, or not? Too many comments? How would you develop this differently? How would you make this more efficient (faster, smaller)?

Thanks, everyone!

---

### Post by Smart Viking on 2011-08-25
(Compiled with gcc -o file file.c -std=c99)
Here's some bugs that needs to be fixed: 
1 player doesn't run at all, word = (null), and when guessing a characted it gets a segmention fault.
When you press a number higher than 2 when it asks for how many players, then you can't quit by entering any other character anymore.
You can have a number in the word, but you cannot guess a number.

:popcorn:

---

### Post by Bachstelze on 2011-08-25
Sanitize user input. The user will not always input what you tell him to.

```
         fgets( hint, MAX, stdin );

         newline = strchr(word, '\n'); /* check for trailing newline char */

         if( newline )
            *newline = '\0';   /* replace newline with a null character */

```

O.O

```
scanf( "%c", &guess );
```

Never Use scanf&#8482;. Here you can replace it with getchar (which you do  few lines later). However, never convert the return value of getchat to char until you are certain it is not EOF. Declare guess as an int.

That's all the major problems I see. I would have a lot to say about your style, though, if you are interested.

*EDIT:* And yes, since 1-player mode does not work, put an exit() there.

---

### Post by kevinharper on 2011-08-25
Yeah.. aware of the one player mode. It's supposed to play against words/hints provided by the computer. The program is supposed to retrieve that info from a separate text file. I haven't build this part yet.

2 quotes from "Smart Viking":
> When you press a number higher than 2 when it asks for how many players, then you can't quit by entering any other character anymore. Right... thanks. I overlooked that. It is supposed be with a 0 to exit. So 0 players -> exit() a few lines below that.

> You can have a number in the word, but you cannot guess a number. VEEEEEEEERY good observations. I hadn't given that a thought! I will have to make it so that there are no numbers in the word to be guessed.

> Sanitize user input. The user will not always input what you tell him to. Sanitize how? Alter what they put? I assume you're referring to word and hint... I checked "guess" at every point, I thought. I'm not asking for code to sanitize; want to know what you mean by it and if you could give me a few examples. :) Thanks.

Quotes from Bachstelze:
> Never Use scanf&#8482;. Here you can replace it with getchar (which you do few lines later) I replaced it in other places because I was having issues with newline just jumping past scanf. And I missed this one. I had intention of using getchar() on all single-character inputs. Promise.

> However, never convert the return value of getchat to char until you are certain it is not EOF Okay.. so, as you said, declare "int guess = 0;"... :S And then getchar(), only go if guess != EOF. Here's why the int declaration is important, right? Then "convert to char"? Do I just start using it as if it were a letter from this point on (like 'a')? Is that what you mean by that?

AND YES! VERY INTERESTED IN TELLING ME ABOUT MY STYLE. :)

EDIT:
> Never use scanf
Like neva-eva... or like never for a single character? I did read somewhere that a lot of veteran programmers don't like to use scanf(). And I'm almost certain it had to do with newlines or something like that... :S

---

### Post by ofnuts on 2011-08-25
> **kevinharper said:**
> Here's my second version of Hangman:
```

/* is_letter() verifies guess is a letter */
int is_letter( char g )
{
   int letter = 0;

   if( ( g >= 'a' && g <= 'z' ) || ( g >= 'A' && g <= 'Z' ) )
      letter = 1;

   return letter;
}


```!
There is a built-in isalpha()  macro/function that does just that. You'll find other function to check for lowercase/uppercase and convert to uppercase (useful in some countries)

Your names for variables are reasonably chosen so the comment tends to state the obvious. But you never tell how you use them. Somewhere one expects a hight level explanation of how the program works (usage of correct_guesses is not obvious, for instance).

You should declare the type for each variable ie:
```
int x;
int y;
```instead of 
```
int x;
    y;

```Your style makes your code hard to follow, because you tend to group together variables that are only related by their common type. You should group them by usage, for instance: a char array, a char* that points in the array, and an int that keeps the array length. For me the only correct use of a common type is when the variables are strongly related:
```
float x0,y0,z0;  /* origin coordinates */
```This code is strange because it documents nothingness:
```
      else
      {
         /* get random word & hint from another file */
      }

```This:
```
         /* reset flag_correct_guess */
         if( flag_correct_guess == true )
            flag_correct_guess = false;

```can be replaced by:
```
flag_correct_guess = false;
```

Your main() is too long. You can break it up in pieces (get a valid input,check,print result).

---

### Post by Smart Viking on 2011-08-25
New bug:
When a new round is started, the wrong guesses are not deleted, so you can't use them.
:popcorn:

---

### Post by Bachstelze on 2011-08-25
> **kevinharper said:**
> 
 Sanitize how? Alter what they put? I assume you're referring to word and hint... I checked "guess" at every point, I thought. I'm not asking for code to sanitize; want to know what you mean by it and if you could give me a few examples. :) Thanks.

Basically what Smart Viking said above: your program expects the number of players to be 0, 1 or 2, so you must do something to handle the case in which the user enters another number, or anything that is not even a number. Likewise, your program expects the word to be all letters, so you must handle the case in which the user enters other characters in the word.

> Okay.. so, as you said, declare "int guess = 0;"... :S And then getchar(), only go if guess != EOF. Here's why the int declaration is important, right? Then "convert to char"? Do I just start using it as if it were a letter from this point on (like 'a')? Is that what you mean by that?

Basically, so something like this: first make your is_letter function take an int as argument, not a char (or even better, use isalpha()). Then :

```
int guess;
guess = getchar();
ltr = is_letter(guess);
```

If ltr is true, then you are sure that the character is not EOF and you can convert it to char. Otherwise treat it as invalid input (there should be no need to distinguish between invalid input and no input at all).

> AND YES! VERY INTERESTED IN TELLING ME ABOUT MY STYLE. :)

A few things then. Note that as all style matters, this is just my opinion. It is shared by a number of people and projects, but that does not mean you should blindly apply it. Use what works for you.

* Indentation is eight spaces.
* In general, groups of spaces are only used before a line, for indentation. Do not use several consecutive spaces in the middle of a line in variable declarations or in the middle of your code:

```
       player1_pts       = 0,
   char word[MAX]                          = " ",

```

Bad. Do it for prototypes and structures, though.
* I know I've told you that excessive initialization was not a crime, but avoid it if you can anyway.
* You put spaces in the wrong places. No space after ( and [ and before ) and ]. One space between keywords like if, for or while and the (, no space after function calls. Bad:

```
while( num_players != 1 && num_players != 2 )
printf( "Are there 1 or 2 players?\n" );

```

Good:

```
while (num_players != 1 && num_players != 2)
printf("Are there 1 or 2 players?\n");

```

* Don't compare bool variables to true or false, it's redundant. Bad:

```
if( flag_repeat == true )
if( flag_correct_guess == false )

```

Good:

```
if (flag_repeat)
if (!flag_correct_guess)

```

* Be consistent. Do not use bool-style tests for some variables and explicit comparison to 0 for others. Choose one or the other but make up your mind. For example you have [font=monospace]if( ch )[/font] and a few lines later [font=monospace]if( ch == NULL )[/font]. My recommendation is use bool-style tests for bool variables and integer variables that semantically represent a boolean value, and explicit comparison to 0 for everything else.
* do..while loops are to be avoided unless strictly needed.
* The kosher way to do an infinite loop is [font=monospace]for (;;)[/font].
* For prototypes, no variable names, and put a tab between the type of the function and everything else:

```
/* function prototypes */
void    clrscrn(void);
void    clrstdin(void);
int     is_letter(char);
void    draw_hangman(int);
```


> Like neva-eva... or like never for a single character? I did read somewhere that a lot of veteran programmers don't like to use scanf(). And I'm almost certain it had to do with newlines or something like that... :S

Never ever. Unless you are playing with C and don't know anything else, for example a lot of beginner exercises in C involve inputting values and mainpulating them, like "input two integers and print the largest one". scanf works as an uncomplicated way to do that, but once you get serious, you should forget about it.

[http://c-faq.com/stdio/scanfprobs.html](http://c-faq.com/stdio/scanfprobs.html)

```
         correct_guesses = (char *) malloc( word_length + 1 );

```

Never cast the return value of malloc (or any other function that returns void*). It is unnecesary and can cause problems in some cases.

[http://stackoverflow.com/questions/605845/do-i-cast-the-result-of-malloc](http://stackoverflow.com/questions/605845/do-i-cast-the-result-of-malloc)

---

### Post by Bachstelze on 2011-08-25
And yes, as ofnuts says, your main is too long and complicated with all its nested loops, which is why I mostly only made formal remarks, your logic is way too convoluted so I didn't bother analyzing it.

---

### Post by kevinharper on 2011-08-25
@Smart Viking: Thanks for the bug report. Will blank array when players switch.

@ofnuts: Thanks for the function suggestions. isalpha() is definitely worth looking into although I don't think the low-to-cap function is really needed here.

> Somewhere one expects a hight level explanation of how the program works (usage of correct_guesses is not obvious, for instance).Okay... so something like:
```

char *correct_gueses;

/* correct_guesses is the same size as word and displays characters that have been correctly guessed. */

```

You are right in how I declared my vars... they are by type, not by function. And there is no other reason for doing it other than to have int x, y, z. Thanks for that tip, now I understand why I have seen these var types split up in code snippets I've looked at online.

> This code is strange because it documents nothingness:
LOL Indeed... Just mental note for me to remember to add that missing functionality.

I can't believe I hadn't seen that about the flag... You're right... why even check? Just set it and forget it. And yes.. main() is really long for what this program does. I am aware that many things can be broken down into functions and just insert the function calls within main(). I hadn't realized it until I finished and I was about to post it here, though.

I tried HARD to do your "input > check > print"... Getting there. Just have to get used to people input, looks like.

@Bachstelze
> Don't compare bool variables to true or false, it's redundant. This is so obvious... how could I have missed it. Thanks for pointing it out!

> your logic is way too convoluted so I didn't bother anayzing it. I have no logic.. ;)

Okay... will take all of this in and brew it in my head for the next few days. Then... on to version 3. Expect a much smaller main(), w/ a few more functions.

You guys are awesome! Thank you! :) I never though Hangman could be so educational.

---

### Post by ofnuts on 2011-08-25
> **kevinharper said:**
> 
@ofnuts: Thanks for the function suggestions. isalpha() is definitely worth looking into although I don't think the low-to-cap function is really needed here.
Only if 'hangman' isn't ans answer for "HanGmAn"
> **kevinharper said:**
> 
Okay... so something like:
```

char *correct_gueses;

/* correct_guesses is the same size as word and displays characters that have been correctly guessed. */

```
Better. actually you'll find how to comment code when you put your code aside, forget it for 6 months, and try to work again on it. Commenting the obvious won't help. It's where things get complicated (take in account a special case you didn't desgn for...) that comments are useful.
> **kevinharper said:**
> I can't believe I hadn't seen that about the flag... You're right... why even check? Just set it and forget it. And yes.. main() is really long for what this program does. I am aware that many things can be broken down into functions and just insert the function calls within main(). I hadn't realized it until I finished and I was about to post it here, though.

I tried HARD to do your "input > check > print"... Getting there. Just have to get used to people input, looks like.
Splitting your code in simple pieces that you can define, code and test independently and thoroughly is an habit that you should acquire as quickly as possible. Ideally, your brain should never have to scroll to check you code. All you functional units should be under a screenful.
> **kevinharper said:**
> You guys are awesome! Thank you! :) I never though Hangman could be so educational.Hangman or any other program.. there are two ways to learn, lots of self-criticism, or accepting other people's critics (which is more efficient but may require thick skin).
Your Hangman V6 or V7 may be close to OK :)

---

### Post by kevinharper on 2011-08-25
> there are two ways to learn, lots of self-criticism, or accepting other people's critics (which is more efficient but may require thick skin).

I've posted a few "code audit" requests already. :( Was once told that "No offense, but if your code is indicative of what the book teaches, it most definitely is not a good book." (or something VERY similar to that).

I'm very humble and always looking to improve. :D What better way to do so than to consult with experts, right?

I really, really hope that I can do a good job with this next version that I will start on in a few minutes. I started version 2 from scratch... Will do the same with version 3.

Quick question, though. What did you mean by
>  All you functional units should be under a screenful.

Are you saying that main() should be that small? I was thinking something like this for ver3:
```

main()
{
   get_num_players();
   if (num_players == 1)
      get_word_hint_user();
   else if (num_players == 2 )
      get_word_hint_file();
   else
      exit(EXIT_SUCCESS); /* 0 players */

   get_word();
   get_hint();

   return EXIT_SUCCESS;
}

get_num_players()
/* ask for number of players, check 0, 1, 2... return value
   repeat if input > 2, and display msg like "max of 2 players can play" */

get_word()
/* ask a player to enter a word to be guessed
   loop until string = 100% letters */

```
I plan on checking input with functions also... :S I really hope this is what you meant.

EDIT: I am aware that the above is not proper code... It is a form of pseudocode - :S I hope. Just used it as an example to quickly get the point across.

---

### Post by Smart Viking on 2011-08-25
Just to throw it out there:

If should not be possible to crash/halt a program, not even intentionally, unless it's ment to quit the program or is a part of the design of the operative system(like CTRL-C in bash). Expect the user to return ridiculous inputs, because the user will expect a nice informative error, anything else would be very terrifying for them.

---

### Post by kevinharper on 2011-08-25
>  anything else would be very terrifying for them.
I cannot stop laughing. XD

I really hope no one loses sleep from fight caused by my programs. :( LOL.

Believe me... I understand what you said. Will include those nice little error messages.

---

### Post by Bachstelze on 2011-08-25
> **kevinharper said:**
> 
Are you saying that main() should be that small? I was thinking something like this for ver3:
```

main()
{
   get_num_players();
   if (num_players == 1)
      get_word_hint_user();
   else if (num_players == 2 )
      get_word_hint_file();
   else
      exit(EXIT_SUCCESS); /* 0 players */

   get_word();
   get_hint();

   return EXIT_SUCCESS;
}

get_num_players()
/* ask for number of players, check 0, 1, 2... return value
   repeat if input > 2, and display msg like "max of 2 players can play" */

get_word()
/* ask a player to enter a word to be guessed
   loop until string = 100% letters */

```
I plan on checking input with functions also... :S I really hope this is what you meant.

EDIT: I am aware that the above is not proper code... It is a form of pseudocode - :S I hope. Just used it as an example to quickly get the point across.

To me the problem is not really the length of main, but all the nested loops. You should be able to do the same thing with one big main loop that says "keep the program running until the game is over", and second-level loops that should only be about a dozen lines each at a maximum. No third-level loops. Try to do it like that, and it should be a lot clearer.

---

### Post by ofnuts on 2011-08-25
> **kevinharper said:**
> I
Quick question, though. What did you mean by
[quote]All you functional units should be under a screenful. 			 		

Are you saying that main() should be that small? I was thinking something like this for ver3:
```

main()
{
   get_num_players();
   if (num_players == 1)
      get_word_hint_user();
   else if (num_players == 2 )
      get_word_hint_file();
   else
      exit(EXIT_SUCCESS); /* 0 players */

   get_word();
   get_hint();

   return EXIT_SUCCESS;
}

get_num_players()
/* ask for number of players, check 0, 1, 2... return value
   repeat if input > 2, and display msg like "max of 2 players can play" */

get_word()
/* ask a player to enter a word to be guessed
   loop until string = 100% letters */

```
I mean that you should be able to have all the relevant code on one screen, and so be able to read it without scrolling. This often means a function, but I said functional units because in some cases it's difficult to make a function. But this still means that for instance the code in sight isn't using variables that are set elsewhere (except of  course proper initialization ). And ideally it is well delimited in the code by a block of comments on entry (that describe/explain what it does)

---

### Post by kevinharper on 2011-08-25
Got it.. thanks guys.

One more question.. I want to NOT use scanf to get the number of players. Do I getchar and then atoi? Didn't quite understand what atoi does.. I ASSUME alpha to integer. But the int value entered by player will not be the same after conversion. Lost.

---

### Post by Bachstelze on 2011-08-25
> **kevinharper said:**
> Got it.. thanks guys.

One more question.. I want to NOT use scanf to get the number of players. Do I getchar and then atoi? Didn't quite understand what atoi does.. I ASSUME alpha to integer. But the int value entered by player will not be the same after conversion. Lost.

Don't use atoi() (or at least, don't use it alone), because it does not detect errors. Use fgets to get the input in a buffer, and then strtol or sscanf to parse it. Alternatively, use getchar() and isdigit(), and decrement the value.

---

### Post by kevinharper on 2011-08-25
My brain's done for the day. I'm getting some weird values returned by isdigit() and not sure what you mean by decrement the value.

Don't answer just yet. I think I need to not stare at code or read about C until tomorrow. I'll let you know when I get it working. :)

---

### Post by kevinharper on 2011-08-26
Alright... so I found out what you meant by "decrement the value".

Mr. dwhitney27 answered this same question a little over a couple of years here: [http://ubuntuforums.org/showthread.php?t=954517&page=3](http://ubuntuforums.org/showthread.php?t=954517&page=3)

So that works and the game looks much, MUCH cleaner and easier to follow than what I vomited on this thread when I created it. But I can't seem to understand why the following function isn't working:
```

/* check_string() verifies that word and hint only letters
   word cannot have spaces, hint can */
int check_string(char *s, int wh)
{
	int s_length;
	char *is_space;
	bool is_letter = false;
	int val = 1;

	s_length = strlen(s);

	for (int i=0; i < s_length; i++)
	{
		is_letter = isalpha(s[i]);

		if (!is_letter && wh == 1)
			is_space = strchr(s, ' ');

		if (!is_letter && !is_space)
		{
			val = 0;
			break;
		}
		else
			continue;
	}

	return val;
}

```
I use this function to check that everything entered in word and hint are letters. But I want hint to be able to allow spaces.

So I call this function w/ a hw=0 value from word and w/ a hw=1 value from hint.

My logic:
if
s[i]
is not a letter, then
isalpha(s[i])
returns null and is_letter has null value. This should make the first part of
if (!is_letter && wh == 1)
true. The second part of this should be true ONLY when I'm calling function to check hint. function that sets word should just continue to ask for word if a non-alpha char or space is detected.

This code, however, allows spaces in both, word and hint. Before I added the space check, I was not allowed to put spaces in hint and the program would just keep asking for hint. This is the exact behavior I expect from word when a space is encountered.

---

### Post by kevinharper on 2011-08-26
okay... just saw something weird in functions that call this one.

Essentially, what I think is going on is that val doesn't get set to 0 for word because is_space never got set to null.

This is the function that calls it for word (hint is identical, just has 1 instead of 0 as second argument to check_string()):
```

/* get_word() sets word to be guessed
   if 1 player, gets word from word_hint.txt 
   if 2 players, get word from a non-guesser */
void get_word(int players)
{
	char word[MAX], *newline;
	bool is_valid_string = false;

	if (players == 1)
		/* get word from word_hint.txt */
		puts("get word from word_hint.txt");
	else
	{
		while (!is_valid_string)
		{
			puts("Enter a word for your opponent to guess.");
			fgets(word, sizeof(word), stdin);
			newline = strchr(word, '\n'); /* check for trailing newline char */

			if( newline )
				*newline = '\0';   /* replace newline with a null character */
			is_valid_string = check_string(word, 0);
		}
	}
}

```
So because val doesn't get set to 0, it returns one. This, in turn, makes is_valid_string == true and loop exits.

---

### Post by Bachstelze on 2011-08-26
Once again, way too convoluted. Much better:

```
int test_string(const char *s, int wh) 
{
        for (const char *p = s; *p != '\0'; p++) {
                if (!(isalpha(*p) || (wh && *p == ' '))) {
                        return 0;
                }   
        }   
        return 1;
}

```

In general, when you want to search for an element x in an array t you do:

```
for (i=0; i<lt; i++) {
    if (t[i] == x) {
        return true;
    }
}
return false;
```

The thing is that "search" in this sense can mean a lot of things, not only "whether this element is in the array". You can test for any condition in the if block, so when you want to check whether there exists an element in an array that satisfies a given condition, 99% of the time, you do it like that.

---

### Post by kevinharper on 2011-08-26
Wow... Okay... so the pointer position moves up to the next array element on each iteration. And the end char of the string array is null so as long as it isn't that, continue. INSANE... I get it... :( Wouldn't have thought of it, though.

Same goes for the evaluations within the if statement. They make PERFECT sense... Maybe would have thought of them after hours and hours of tweaking the function.

Question: In all cases,
```

int var = 0;

if (!var)
   /* execute */

```
/* execute */ will execute, right? meaning that if int var != 0 then it is treated as if it existed, and when it var = 0 it is treated as if it doesn't exist?

When do I use "const char *ptr" as opposed to "char *ptr"?

> In general, when you want to search for an element x in an array t you do:
I used to do this... then dwhitney27 gave me an example with strchr() and been using that ever since. When is it appropriate to use strchr()? When I absolutely KNOW that the char I'm looking for exists?

---

### Post by Bachstelze on 2011-08-26
> **kevinharper said:**
> 
Question: In all cases,
```

int var = 0;

if (!var)
   /* execute */

```
/* execute */ will execute, right? meaning that if int var != 0 then it is treated as if it existed, and when it var = 0 it is treated as if it doesn't exist?

What do you mean by "exists"? When you do [font=monospace]if (var)[/font], the compiler interprets it as [font=monospace]if (var != 0)[/font] (and [font=monospace]if (!var)[/font] as [font=monospace]if (var == 0)[/font]). 

> When do I use "const char *ptr" as opposed to "char *ptr"?

With const it means that you cannot modify the memory pointed (but you can modify the pointer itself). Here, you don't modify the string, so it's good habit to use const so that the compiler will complain if you end up modifying the memory.

> I used to do this... then dwhitney27 gave me an example with strchr() and been using that ever since. When is it appropriate to use strchr()? When I absolutely KNOW that the char I'm looking for exists?

strchr() is very specific, it only checks whether a given character exists in a string. This template however is much more versatile, because it works on any kind of array, and lets you check for more sophisticated conditions than just equality. On the other hand, of course strchr() is much more concise since it only takes one line, but it probably does something similar behind the scenes.

---

### Post by kevinharper on 2011-08-26
> **Bachstelze said:**
> What do you mean by "exists"?
Exactly what you said in your explanation.

> With const it means that you cannot modify the memory pointed (but you can modify the pointer itself). Here, you don't modify the string, so it's good habit to use const so that the compiler will complain if you end up modifying the memory.Nice... thanks.



> strchr() is much more concise since it only takes one line, but it probably does something similar behind the scenes.Thought same thing as far it doing something very similar. Don't mind either way, really... just, as you said, a lot more concise and easier to write.

I'm about half-way done with this new version. I'm sure you'll agree it is MUCH easier to follow.

---

