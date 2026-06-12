---
title: "What am I missing here? (c programming)"
date: 2011-08-27
forum: Programming Talk
---

### Post by kevinharper on 2011-08-27
I can't find where word and hint are messing up. Here's the code:
```

if (num_players != 0)
{
  word = get_word(num_players, player_turn);
  word_length = strlen(word);
  correct_guesses = (char *) malloc( word_length + 1 );

  hint = get_hint(num_players);
}
else
  exit(EXIT_SUCCESS);

/* erase correct_guesses & wrong_guesses */
for (int i = 0; i < word_length; i++ )
  correct_guesses[i] = '-';
correct_guesses[word_length] = '\0';

for (int i = 0; i < INCORRECT_TRIES; i++ )
  wrong_guesses[i] = ' ';
wrong_guesses[INCORRECT_TRIES] = '\0';

wg = wrong_guesses;

/* game... repeats until player has guessed word or has reached
	INCORRECT_TRIES - 7 incorrect tries completes hangman */
for(;;)
{
  clrscrn();
  draw_hangman(num_wrong_guesses);
  printf("HINT: %s\n", hint);
  printf("Word: %s\n", correct_guesses);
  printf("Incorrect Tries: %s\n", wrong_guesses);

```
If I printf("hint: %s", word); and do the same for hint immediately after word = get_word(num_players, player_turn); (same for hint), it prints just fine.

But lower, when I print it inside for(;;) it doesn't. word_length also gets set to 2. I'm guessing because word and hint are pointers, not actual word-arrays. Could someone please confirm that for me?

So... in a clearer fashion... two questions:
Is word_length set to two because word is a pointer?
Why do word and hint print out just fine after being initialized, but do not print out correctly inside the for(;;) loop?

---

### Post by Arndt on 2011-08-27
> **kevinharper said:**
> I can't find where word and hint are messing up. Here's the code:
```

if (num_players != 0)
{
  word = get_word(num_players, player_turn);
  word_length = strlen(word);
  correct_guesses = (char *) malloc( word_length + 1 );

  hint = get_hint(num_players);
}
else
  exit(EXIT_SUCCESS);

/* erase correct_guesses & wrong_guesses */
for (int i = 0; i < word_length; i++ )
  correct_guesses[i] = '-';
correct_guesses[word_length] = '\0';

for (int i = 0; i < INCORRECT_TRIES; i++ )
  wrong_guesses[i] = ' ';
wrong_guesses[INCORRECT_TRIES] = '\0';

wg = wrong_guesses;

/* game... repeats until player has guessed word or has reached
	INCORRECT_TRIES - 7 incorrect tries completes hangman */
for(;;)
{
  clrscrn();
  draw_hangman(num_wrong_guesses);
  printf("HINT: %s\n", hint);
  printf("Word: %s\n", correct_guesses);
  printf("Incorrect Tries: %s\n", wrong_guesses);

```
If I printf("hint: %s", word); and do the same for hint immediately after word = get_word(num_players, player_turn); (same for hint), it prints just fine.

But lower, when I print it inside for(;;) it doesn't. word_length also gets set to 2. I'm guessing because word and hint are pointers, not actual word-arrays. Could someone please confirm that for me?

So... in a clearer fashion... two questions:
Is word_length set to two because word is a pointer?
Why do word and hint print out just fine after being initialized, but do not print out correctly inside the for(;;) loop?

I think you have to supply the whole program.

---

### Post by Senesence on 2011-08-27
I don't think that dumping your program is such a good idea.

You should try to isolate the problem further.

---

### Post by Bachstelze on 2011-08-27
> **kevinharper said:**
> 
Is word_length set to two because word is a pointer?


Of course not, otherwise strlen would always return two because it always takes a pointer as its argument... Also what Arndt says.

---

### Post by kevinharper on 2011-08-27
Here's the whole thing:
```

/* Hangman III
   Kevin Harper :: August 25, 2011 */

#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>
#include <string.h>
#include <ctype.h>

/* constant declarations */
#define MAX 255
#define INCORRECT_TRIES 7

void	clrscrn(void);
void	clrstdin( void );
int	get_num_players(void);
char*	get_word(int, int);
char*	get_hint(int);
int	check_string(const char *, int);
void	draw_hangman(int);
char	get_guess(int);
int	is_dup_guess(const char, char *, char *);
int	is_correct_guess(const char, char *);
void	set_wrong_guess(const char, char *, int);
void	set_correct_guess(const char, char *, int, char *);

int main(void)
{
	int num_players; /* number of players (1 or 2) */
	int player_turn = 1;
	int num_wrong_guesses = 0;

	int unique_guess = 0, correct_guess;
	int word_length;
	char *word, *correct_guesses, guess, wrong_guesses[INCORRECT_TRIES + 1], *wg, *hint;

	clrscrn();

	num_players = get_num_players();

	for(;;)
	{
		clrscrn();

		if (num_players != 0)
		{
			word = get_word(num_players, player_turn);
			word_length = strlen(word);
			correct_guesses = (char *) malloc( word_length + 1 );

			hint = get_hint(num_players);
		}
		else
			exit(EXIT_SUCCESS);

		/* erase correct_guesses & wrong_guesses */
		for (int i = 0; i < word_length; i++ )
			correct_guesses[i] = '-';
		correct_guesses[word_length] = '\0';

		for (int i = 0; i < INCORRECT_TRIES; i++ )
			wrong_guesses[i] = ' ';
		wrong_guesses[INCORRECT_TRIES] = '\0';

		wg = wrong_guesses;

		/* game... repeats until player has guessed word or has reached
			INCORRECT_TRIES - 7 incorrect tries completes hangman */
		for(;;)
		{
			clrscrn();
			draw_hangman(num_wrong_guesses);
			printf("HINT: %s\n", hint);
			printf("Word: %s\n", correct_guesses);
			printf("Incorrect Tries: %s\n", wrong_guesses);
			while(!unique_guess)
			{
				guess = get_guess(player_turn);
				unique_guess = is_dup_guess(guess, correct_guesses, wg);
			}

			correct_guess = is_correct_guess(guess, word);

			if (!correct_guess)
			{
				set_wrong_guess(guess, wg, num_wrong_guesses);
				num_wrong_guesses++;
			}
			else
				set_correct_guess(guess, word, word_length, correct_guesses);
		}

		/* switch player turn */
		player_turn == 1 ? player_turn++ : player_turn--;
	}

/* check to see if word was guessed */

/* check to see if max num of incorrect guesses */

/* reset flags */

	return EXIT_SUCCESS;
}

/* clrscrn() clears terminal by inserting 30 blank lines */
void clrscrn(void)
{
	for (int x = 0; x < 30; x++ )
		printf("\n");
}

/* clrstdin() clears stdin stream */
void clrstdin(void)
{
	int ch = 0;

	while ((ch = getchar()) != '\n' && ch != EOF)
		;
}

/* get_num_players() sets the number of players.
   Function returns 0, 1, or 2 players */
int get_num_players(void)
{
	int val = 3;

	while (val > 2)
	{
		puts("Enter the number of players.");
		puts("Options: 1 or 2 players.");
		puts("Enter 0 to quit.");
		val = getchar() - 0x30;
		clrstdin();
		if (val > 2)
		{
			clrscrn();
			puts("This game can only be played by 1 or 2 players.");
		}
	}

	return val;
}

/* get_word() sets word to be guessed
   if 1 player, gets word from word_hint.txt 
   if 2 players, get word from a non-guesser
   word can only consist of letters */
char* get_word(int players, int pt)
{
	char word[MAX], *newline, *p_word;
	bool is_valid_string = false;

	if (players == 1)
		/* get word from word_hint.txt */
		puts("get word from word_hint.txt");
	else
	{
		while (!is_valid_string)
		{
			printf("Player %d, enter a word for your opponent to guess.\n", pt);
			fgets(word, sizeof(word), stdin);
			newline = strchr(word, '\n'); /* check for trailing newline char */

			if (newline)
				*newline = '\0';   /* replace newline with a null character */

			is_valid_string = check_string(word, 0);

			if (!is_valid_string)
				puts("Only letters are allowed.");
		}
	}

	p_word = word;

	return p_word;
}

/* get_hint() sets hint to help guesser narrow down options of poss words */
char* get_hint(int players)
{
	char hint[MAX], *newline, *p_hint;
	bool is_valid_string = false;

	if (players == 1)
		/* get hint from word_hint.txt */
		puts("get hint from word_hint.txt");
	else
	{
		while (!is_valid_string)
		{
			puts("Enter a short hint for your opponent.");
			fgets(hint, sizeof(hint), stdin);
			newline = strchr(hint, '\n'); /* check for trailing newline char */

			if (newline)
				*newline = '\0';   /* replace newline with a null character */

			is_valid_string = check_string(hint, 1);

			if (!is_valid_string)
				puts("Only letters, spaces, and periods are allowed.");
		}
	}

	p_hint = hint;

	return p_hint;
}

/* check_string() verifies that word and hint only containe letters
   word cannot have spaces, hint can */
int check_string(const char *s, int wh)
{
	for (const char *ptr = s; *ptr != '\0'; ptr++)
		if(!(isalpha(*ptr) || (wh && (*ptr == ' ' || *ptr == '.'))))
			return 0;

	return 1;
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

/* get_guess() asks guesser to submit a guess
   guess must be a letter */
char get_guess(int pt)
{
	char g;

	pt == 1 ? pt++ : pt--;
	printf("Player %d, enter a guess\n", pt);

	while(!isalpha(g))
	{
		puts("Your guess must be a letter.");
		g = getchar();
		clrstdin();
	}

	return g;	
}

/* check_duplicate() checks to see if guess had previously been guessed
   accepts guess from get_guess()
   returns 0 if duplicate guess, 1 if unique guess */
int is_dup_guess(const char g, char *cg, char *ig)
{
	for (const char *ptr = cg; *ptr != '\0'; ptr++)
		if (g == *ptr || g == *ptr - 32)
			return 0;

	for (const char *ptr = ig; *ptr != '\0'; ptr++)
		if (g == *ptr || g == *ptr - 32)
			return 0;

	return 1;
}

/* is_correct_guess() checks to see if guess is right or not 
   returns 0 if guess is not correct, 1 if correct*/
int is_correct_guess(char g, char *w)
{
	g = toupper(g);

	for (const char *ptr = w; *ptr != '\0'; ptr++)
		if (g == toupper(*ptr))
			return 1;

	return 0;
}

/* set_wrong_guess() keeps track of all incorrect guesses
   the function accepts the guess and a pointer to wrong_guess[],
   it adds the most current incorrect guess to wrong_guess[i] */
void set_wrong_guess(const char g, char *ig, int nwg)
{
	ig[nwg] = g;
}

/* set_correct_guess() looks through word and compares each element to guess
   if guess == word[i], guess get put into correct_guesses[i] */
void set_correct_guess(const char g, char *w, int wl, char *cg)
{
	for (int i = 0; i < wl; i++ )
		if (g == w[i])
			cg[i] = g;
}

```
Compiled as "gcc -std=c99 -pedantic -Wall -Werror -o hangman-III hangman-III,c"

NOTE: Program is not complete and only 2 players plays. 0 players does quit, 1 simply prints that a word and hint need to be retrieved from a text file.

---

### Post by Bachstelze on 2011-08-27
```
char* get_word(int players, int pt)
{
	char word[MAX], *newline, *p_word;
        /* ... */
	p_word = word;
	return p_word;
}
```

This is wrong, because you allocate the array word on the stack, and then return a pointer to it. Since the memory that actually holds the data is in the stack frame of get_word, it will be freed when get_word returns, and overwritten when you call another function. As a result, the data pointed by p_word may be different when you try to access it later.

Possible fix: allocate word on the heap with malloc(), or declare it in main.

---

### Post by kevinharper on 2011-08-27
> Possible fix: allocate word on the heap with malloc(), or declare it in main.
Will look into that.

@Bachstelze How's it looking so far? Much cleaner, yes? And much easier to follow, right? BTW, you can officially start calling me "Grasshopper".

---

### Post by gnometorule on 2011-08-27
Same problem with hint obviously. Make heap variable (better), or static in function.

---

### Post by Arndt on 2011-08-27
> **Bachstelze said:**
> ```
char* get_word(int players, int pt)
{
	char word[MAX], *newline, *p_word;
        /* ... */
	p_word = word;
	return p_word;
}
```

This is wrong, because you allocate the array word on the stack, and then return a pointer to it. Since the memory that actually holds the data is in the stack frame of get_word, it will be freed when get_word returns, and overwritten when you call another function. As a result, the data pointed by p_word may be different when you try to access it later.

Possible fix: allocate word on the heap with malloc(), or declare it in main.

Another possible fix is to declare 'word' static. Then it won't disappear when the function returns. But it's not a good solution if you find yourself dealing with the result of several calls to get_word at the same time (which I guess you don't, here).

Generally, the best interface may be that get_word takes two additional arguments: a buffer and its length. Then the caller is responsible for allocating the buffer.

---

### Post by Bachstelze on 2011-08-27
Looks good. This time, though, you might have too many functions. ;) Especially your last three ones. When you have a function call, you should be able to instantly tell what it does. For example:

```
unique_guess = is_dup_guess(guess, correct_guesses, wrong_guesses);
```

(Modified for clarity, your wg variable is unnecessary.)

No problem, it checks whether the guess is a dulicate. However

```
set_correct_guess(guess, word, word_length, correct_guesses);
```

What does it do? I have to go see the code to find out. And since the code is not long, I would put it in main with a comment at the top explaining what it does:

```
else {
        /*
         * The guess is correct, replace all dashes that correspond to this
         * letter with the letter itself.
         */
        for (int i=0; i<word_length; i++) {
                if (word[i] == guess) {
                        correct_guess[i] = guess;
                }
        }
}
```

Same with set_wrong_guess, don't you think it's a bit absurd to have a function call that takes more characters than the body of the function?

---

### Post by kevinharper on 2011-08-27
>  don't you think it's a bit absurd to have a function call that takes more characters than the body of the function?LMAO!

I can't stop laughing.

Will post Hangman-III code when finished. Thanks, everyone!

---

### Post by kevinharper on 2011-08-27
Perfect... seems to be getting word and hint just fine now. :P

Was about to do something Bachstelze told me not to do on the last post on this page [http://ubuntuforums.org/showthread.php?t=1831669&highlight=malloc+don%27t](http://ubuntuforums.org/showthread.php?t=1831669&highlight=malloc+don%27t)

Instead, I strcpy(p_word, word);

EDIT: I also eliminated set_correct_guess() and set_wrong_guess().

---

### Post by Bachstelze on 2011-08-27
> **kevinharper said:**
> 
Instead, I strcpy(p_word, word);


But are you sure it won't overflow?

---

### Post by kevinharper on 2011-08-27
I set p_word = (char *) malloc(word_legth + 1); So, pretty sure it won't overflow.

Why does was_guessed get incremented
```

for (int i = 0; i < word_length; i++)
{
 if (correct_guesses[i] == '-')
  break;

 was_guessed++;
}

```
So... if a dash is detected, the for loop should end, right? Never incrementing was_guessed.

Here's that whole segment:
```

/* check to see if word has been guessed
   or if max num of allowed incorrect guesses has
   been reached (INCORRECT_TRIES) */
for (int i = 0; i < word_length; i++)
{
	if (correct_guesses[i] == '-')
		break;

	was_guessed++;
}

if (num_wrong_guesses == INCORRECT_TRIES - 1)
	was_not_guessed++;

/* player has not guessed word and has not reached
   incorrect guess limit */
if (!was_guessed && !was_not_guessed)
	continue;
/* player has guessed word
   player (guesser) gets a point */
else if(was_guessed)
{
	draw_hangman(num_wrong_guesses);
	printf("Congratulations player %d!\n", player_turn);
	/* award pt for guessing right */
	player_turn == 1 ? p1_pts++ : p2_pts++;
	puts("You've guessed right and have earned a point!");

	break;
}
else
/* player was not able to guess word - has reached
   allowed incorrect tries limit */
{
	draw_hangman(num_wrong_guesses);
	printf("Whoops! Looks like you were unable to guess the word: %s", word);
	/* award pt to non-guessing player */
	player_turn == 1 ? p2_pts++ : p1_pts++;
	puts("Your opponent has earned a point");

	break;
}

```

---

### Post by Bachstelze on 2011-08-27
What do you think the loop does?

---

### Post by kevinharper on 2011-08-27
Looks through correct_guesses (which was initilized to all dashes). If it finds a dash, it exits the loop and never makes was_guessed true.

was_guessed enters loop w/ a value of 0/false.

---

### Post by Bachstelze on 2011-08-27
But what if the dash is the second character in the string. ;)

---

### Post by kevinharper on 2011-08-27
ah! So... GOT IT! XD if first isn't dash, increment value anyways... duh!

Thanks.. brb after I get this done.. I think it's my last piece.

---

### Post by Bachstelze on 2011-08-27
Also I don't like how you use ++ and -- for integers that represent a bolean value. This is bad because setting a truth value to a variable requires knowledge of its current value. Also if you ++ a variable that is true, it might become false (and vice versa), or it might stay true but not become false when you -- it afterwards.

Use var = 1 and var = 0 please. Or better yet, use bool for booleans.

---

### Post by kevinharper on 2011-08-27
This is what it looks like so far:
```

/* Hangman III
   Kevin Harper :: August 25, 2011 */

#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>
#include <string.h>
#include <ctype.h>

/* constant declarations */
#define MAX 255
#define INCORRECT_TRIES 7

void	clrscrn(void);
void	clrstdin( void );
int	get_num_players(void);
char*	get_word(int, int);
char*	get_hint(int);
int	check_string(const char *, int);
void	draw_hangman(int);
char	get_guess(int);
int	is_dup_guess(const char, char *, char *);
int	is_correct_guess(const char, char *);

int main(void)
{
	int num_players; /* number of players (1 or 2) */
	int player_turn = 1;
	int num_wrong_guesses = 0;

	int unique_guess    = 0,
	    correct_guess   = 0,
            was_guessed     = 0,
            was_not_guessed = 0;

	int word_length;

	char *word,
             *correct_guesses,
             guess,
             wrong_guesses[INCORRECT_TRIES + 1],
             *wg,
             *hint;

	int p1_pts = 0,
            p2_pts = 0;

	clrscrn();

	num_players = get_num_players();

	for(;;)
	{
		clrscrn();

		if (num_players != 0)
		{
			puts("Hanman v3 by Kevin Harper");
			printf("Player 1 pts: %d\t", p1_pts);
			printf("Player 2 pts: %d\n", p2_pts);
			word = get_word(num_players, player_turn);
			word_length = strlen(word);
			correct_guesses = (char *) malloc( word_length + 1 );

			hint = get_hint(num_players);
		}
		else
			exit(EXIT_SUCCESS);

		/* erase letters in correct_guesses & wrong_guesses */
		for (int i = 0; i < word_length; i++ )
			correct_guesses[i] = '-';
		correct_guesses[word_length] = '\0';

		for (int i = 0; i < INCORRECT_TRIES; i++ )
			wrong_guesses[i] = ' ';
		wrong_guesses[INCORRECT_TRIES] = '\0';

		wg = wrong_guesses;

		/* game... repeats until player has guessed word or has reached
			INCORRECT_TRIES - 7 incorrect tries completes hangman */
		for(;;)
		{
			clrscrn();
			draw_hangman(num_wrong_guesses);
			printf("HINT: %s\n", hint);
			printf("Word: %s\n", correct_guesses);
			printf("Incorrect Tries: %s\n", wrong_guesses);
			while(!unique_guess)
			{
				guess = get_guess(player_turn);
				unique_guess = is_dup_guess(guess, correct_guesses, wg);
			}

			correct_guess = is_correct_guess(guess, word);

			/* guess is wrong
			   add guess character to wrong_guesses so it can
			   be displayed when next guess is requested */
			if (!correct_guess)
			{
				wrong_guesses[num_wrong_guesses] = guess;
				num_wrong_guesses++;
			}
			/* guess is right
			   add guess into correct_guesses
			   replaces all dashes occupying spaces where letter
			   guessed should be. */
			else
				for (int i = 0; i < word_length; i++ )
					if (word[i] == guess)
						correct_guesses[i] = guess;

			/* check to see if word has been guessed
			   or if max num of allowed incorrect guesses has
			   been reached (INCORRECT_TRIES) */
			for (int i = 0; i < word_length; i++)
			{
				if (correct_guesses[i] == '-')
					break;

				if (i == word_length - 1)
					was_guessed = 1;
			}

			if (num_wrong_guesses == INCORRECT_TRIES - 1)
				was_not_guessed++;

			/* player has not guessed word and has not reached
			   incorrect guess limit */
			if (!was_guessed && !was_not_guessed)
			{
				unique_guess  = 0;
				correct_guess = 0;
				continue;
			}
			/* player has guessed word
			   player (guesser) gets a point */
			else if(was_guessed)
			{
				draw_hangman(num_wrong_guesses);
				printf("Congratulations player %d!\n", player_turn);
				/* award pt for guessing right */
				player_turn == 1 ? p1_pts++ : p2_pts++;
				puts("You've guessed right and have earned a point!");

				break;
			}
			else
			/* player was not able to guess word - has reached
			   allowed incorrect tries limit */
			{
				draw_hangman(num_wrong_guesses);
				printf("Whoops! Looks like you were unable to guess the word: %s\n", word);
				/* award pt to non-guessing player */
				player_turn == 1 ? p2_pts++ : p1_pts++;
				puts("Your opponent has earned a point");

				break;
			}
		}

		/* switch player turn */
		player_turn == 1 ? player_turn++ : player_turn--;

		/* reset vars */
		num_wrong_guesses = 0;
		was_guessed = 0;
		was_not_guessed = 0;
	}

	return EXIT_SUCCESS;
}

/* clrscrn() clears terminal by inserting 30 blank lines */
void clrscrn(void)
{
	for (int x = 0; x < 30; x++ )
		printf("\n");
}

/* clrstdin() clears stdin stream */
void clrstdin(void)
{
	int ch = 0;

	while ((ch = getchar()) != '\n' && ch != EOF)
		;
}

/* get_num_players() sets the number of players.
   Function returns 0, 1, or 2 players */
int get_num_players(void)
{
	int val = 3;

	while (val > 2)
	{
		puts("Enter the number of players.");
		puts("Options: 1 or 2 players.");
		puts("Enter 0 to quit.");
		val = getchar() - 0x30;
		clrstdin();
		if (val > 2)
		{
			clrscrn();
			puts("This game can only be played by 1 or 2 players.");
		}
	}

	return val;
}

/* get_word() sets word to be guessed
   if 1 player, gets word from word_hint.txt 
   if 2 players, get word from a non-guesser
   word can only consist of letters */
char* get_word(int players, int pt)
{
	char word[MAX], *newline, *p_word;
	int word_length;
	bool is_valid_string = false;

	if (players == 1)
		/* get word from word_hint.txt */
		puts("get word from word_hint.txt");
	else
	{
		while (!is_valid_string)
		{
			printf("Player %d, enter a word for your opponent to guess.\n", pt);
			fgets(word, sizeof(word), stdin);
			newline = strchr(word, '\n'); /* check for trailing newline char */

			if (newline)
				*newline = '\0';   /* replace newline with a null character */

			word_length = strlen(word);
			p_word = (char *) malloc( word_length + 1 );
			strcpy(p_word, word);

			is_valid_string = check_string(word, 0);

			if (!is_valid_string)
				puts("Only letters are allowed.");
		}
	}

	return p_word;
}

/* get_hint() sets hint to help guesser narrow down options of poss words */
char* get_hint(int players)
{
	char hint[MAX], *newline, *p_hint;
	int hint_length;
	bool is_valid_string = false;

	if (players == 1)
		/* get hint from word_hint.txt */
		puts("get hint from word_hint.txt");
	else
	{
		while (!is_valid_string)
		{
			puts("Enter a short hint for your opponent.");
			fgets(hint, sizeof(hint), stdin);
			newline = strchr(hint, '\n'); /* check for trailing newline char */

			if (newline)
				*newline = '\0';   /* replace newline with a null character */

			hint_length = strlen(hint);
			p_hint = (char *) malloc( hint_length + 1 );
			strcpy(p_hint, hint);

			is_valid_string = check_string(hint, 1);

			if (!is_valid_string)
				puts("Only letters, spaces, and periods are allowed.");
		}
	}

	return p_hint;
}

/* check_string() verifies that word and hint only containe letters
   word cannot have spaces, hint can */
int check_string(const char *s, int wh)
{
	for (const char *ptr = s; *ptr != '\0'; ptr++)
		if(!(isalpha(*ptr) || (wh && (*ptr == ' ' || *ptr == '.'))))
			return 0;

	return 1;
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

/* get_guess() asks guesser to submit a guess
   guess must be a letter */
char get_guess(int pt)
{
	char g;

	pt == 1 ? pt++ : pt--;
	printf("Player %d, enter a guess\n", pt);

	while(!isalpha(g))
	{
		puts("Your guess must be a letter.");
		g = getchar();
		clrstdin();
	}

	return g;
}

/* check_duplicate() checks to see if guess had previously been guessed
   accepts guess from get_guess()
   returns 0 if duplicate guess, 1 if unique guess */
int is_dup_guess(const char g, char *cg, char *ig)
{
	for (const char *ptr = cg; *ptr != '\0'; ptr++)
		if (g == *ptr || g == *ptr - 32)
			return 0;

	for (const char *ptr = ig; *ptr != '\0'; ptr++)
		if (g == *ptr || g == *ptr - 32)
			return 0;

	return 1;
}

/* is_correct_guess() checks to see if guess is right or not 
   returns 0 if guess is not correct, 1 if correct*/
int is_correct_guess(char g, char *w)
{
	g = toupper(g);

	for (const char *ptr = w; *ptr != '\0'; ptr++)
		if (g == toupper(*ptr))
			return 1;

	return 0;
}

```

Having a few issues... last guess passes through as the next player's first guess. And a few endless loops in get_guess();

Will have to look at it later.... too much code for now. Thanks. This is seriously a lot of fun.

---

### Post by Arndt on 2011-08-27
> **kevinharper said:**
> This is what it looks like so far:
```

/* Hangman III
   Kevin Harper :: August 25, 2011 */

#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>
#include <string.h>
#include <ctype.h>

/* constant declarations */
#define MAX 255
#define INCORRECT_TRIES 7

void	clrscrn(void);
void	clrstdin( void );
int	get_num_players(void);
char*	get_word(int, int);
char*	get_hint(int);
int	check_string(const char *, int);
void	draw_hangman(int);
char	get_guess(int);
int	is_dup_guess(const char, char *, char *);
int	is_correct_guess(const char, char *);

int main(void)
{
	int num_players; /* number of players (1 or 2) */
	int player_turn = 1;
	int num_wrong_guesses = 0;

	int unique_guess    = 0,
	    correct_guess   = 0,
            was_guessed     = 0,
            was_not_guessed = 0;

	int word_length;

	char *word,
             *correct_guesses,
             guess,
             wrong_guesses[INCORRECT_TRIES + 1],
             *wg,
             *hint;

	int p1_pts = 0,
            p2_pts = 0;

	clrscrn();

	num_players = get_num_players();

	for(;;)
	{
		clrscrn();

		if (num_players != 0)
		{
			puts("Hanman v3 by Kevin Harper");
			printf("Player 1 pts: %d\t", p1_pts);
			printf("Player 2 pts: %d\n", p2_pts);
			word = get_word(num_players, player_turn);
			word_length = strlen(word);
			correct_guesses = (char *) malloc( word_length + 1 );

			hint = get_hint(num_players);
		}
		else
			exit(EXIT_SUCCESS);

		/* erase letters in correct_guesses & wrong_guesses */
		for (int i = 0; i < word_length; i++ )
			correct_guesses[i] = '-';
		correct_guesses[word_length] = '\0';

		for (int i = 0; i < INCORRECT_TRIES; i++ )
			wrong_guesses[i] = ' ';
		wrong_guesses[INCORRECT_TRIES] = '\0';

		wg = wrong_guesses;

		/* game... repeats until player has guessed word or has reached
			INCORRECT_TRIES - 7 incorrect tries completes hangman */
		for(;;)
		{
			clrscrn();
			draw_hangman(num_wrong_guesses);
			printf("HINT: %s\n", hint);
			printf("Word: %s\n", correct_guesses);
			printf("Incorrect Tries: %s\n", wrong_guesses);
			while(!unique_guess)
			{
				guess = get_guess(player_turn);
				unique_guess = is_dup_guess(guess, correct_guesses, wg);
			}

			correct_guess = is_correct_guess(guess, word);

			/* guess is wrong
			   add guess character to wrong_guesses so it can
			   be displayed when next guess is requested */
			if (!correct_guess)
			{
				wrong_guesses[num_wrong_guesses] = guess;
				num_wrong_guesses++;
			}
			/* guess is right
			   add guess into correct_guesses
			   replaces all dashes occupying spaces where letter
			   guessed should be. */
			else
				for (int i = 0; i < word_length; i++ )
					if (word[i] == guess)
						correct_guesses[i] = guess;

			/* check to see if word has been guessed
			   or if max num of allowed incorrect guesses has
			   been reached (INCORRECT_TRIES) */
			for (int i = 0; i < word_length; i++)
			{
				if (correct_guesses[i] == '-')
					break;

				if (i == word_length - 1)
					was_guessed = 1;
			}

			if (num_wrong_guesses == INCORRECT_TRIES - 1)
				was_not_guessed++;

			/* player has not guessed word and has not reached
			   incorrect guess limit */
			if (!was_guessed && !was_not_guessed)
			{
				unique_guess  = 0;
				correct_guess = 0;
				continue;
			}
			/* player has guessed word
			   player (guesser) gets a point */
			else if(was_guessed)
			{
				draw_hangman(num_wrong_guesses);
				printf("Congratulations player %d!\n", player_turn);
				/* award pt for guessing right */
				player_turn == 1 ? p1_pts++ : p2_pts++;
				puts("You've guessed right and have earned a point!");

				break;
			}
			else
			/* player was not able to guess word - has reached
			   allowed incorrect tries limit */
			{
				draw_hangman(num_wrong_guesses);
				printf("Whoops! Looks like you were unable to guess the word: %s\n", word);
				/* award pt to non-guessing player */
				player_turn == 1 ? p2_pts++ : p1_pts++;
				puts("Your opponent has earned a point");

				break;
			}
		}

		/* switch player turn */
		player_turn == 1 ? player_turn++ : player_turn--;

		/* reset vars */
		num_wrong_guesses = 0;
		was_guessed = 0;
		was_not_guessed = 0;
	}

	return EXIT_SUCCESS;
}

/* clrscrn() clears terminal by inserting 30 blank lines */
void clrscrn(void)
{
	for (int x = 0; x < 30; x++ )
		printf("\n");
}

/* clrstdin() clears stdin stream */
void clrstdin(void)
{
	int ch = 0;

	while ((ch = getchar()) != '\n' && ch != EOF)
		;
}

/* get_num_players() sets the number of players.
   Function returns 0, 1, or 2 players */
int get_num_players(void)
{
	int val = 3;

	while (val > 2)
	{
		puts("Enter the number of players.");
		puts("Options: 1 or 2 players.");
		puts("Enter 0 to quit.");
		val = getchar() - 0x30;
		clrstdin();
		if (val > 2)
		{
			clrscrn();
			puts("This game can only be played by 1 or 2 players.");
		}
	}

	return val;
}

/* get_word() sets word to be guessed
   if 1 player, gets word from word_hint.txt 
   if 2 players, get word from a non-guesser
   word can only consist of letters */
char* get_word(int players, int pt)
{
	char word[MAX], *newline, *p_word;
	int word_length;
	bool is_valid_string = false;

	if (players == 1)
		/* get word from word_hint.txt */
		puts("get word from word_hint.txt");
	else
	{
		while (!is_valid_string)
		{
			printf("Player %d, enter a word for your opponent to guess.\n", pt);
			fgets(word, sizeof(word), stdin);
			newline = strchr(word, '\n'); /* check for trailing newline char */

			if (newline)
				*newline = '\0';   /* replace newline with a null character */

			word_length = strlen(word);
			p_word = (char *) malloc( word_length + 1 );
			strcpy(p_word, word);

			is_valid_string = check_string(word, 0);

			if (!is_valid_string)
				puts("Only letters are allowed.");
		}
	}

	return p_word;
}

/* get_hint() sets hint to help guesser narrow down options of poss words */
char* get_hint(int players)
{
	char hint[MAX], *newline, *p_hint;
	int hint_length;
	bool is_valid_string = false;

	if (players == 1)
		/* get hint from word_hint.txt */
		puts("get hint from word_hint.txt");
	else
	{
		while (!is_valid_string)
		{
			puts("Enter a short hint for your opponent.");
			fgets(hint, sizeof(hint), stdin);
			newline = strchr(hint, '\n'); /* check for trailing newline char */

			if (newline)
				*newline = '\0';   /* replace newline with a null character */

			hint_length = strlen(hint);
			p_hint = (char *) malloc( hint_length + 1 );
			strcpy(p_hint, hint);

			is_valid_string = check_string(hint, 1);

			if (!is_valid_string)
				puts("Only letters, spaces, and periods are allowed.");
		}
	}

	return p_hint;
}

/* check_string() verifies that word and hint only containe letters
   word cannot have spaces, hint can */
int check_string(const char *s, int wh)
{
	for (const char *ptr = s; *ptr != '\0'; ptr++)
		if(!(isalpha(*ptr) || (wh && (*ptr == ' ' || *ptr == '.'))))
			return 0;

	return 1;
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

/* get_guess() asks guesser to submit a guess
   guess must be a letter */
char get_guess(int pt)
{
	char g;

	pt == 1 ? pt++ : pt--;
	printf("Player %d, enter a guess\n", pt);

	while(!isalpha(g))
	{
		puts("Your guess must be a letter.");
		g = getchar();
		clrstdin();
	}

	return g;
}

/* check_duplicate() checks to see if guess had previously been guessed
   accepts guess from get_guess()
   returns 0 if duplicate guess, 1 if unique guess */
int is_dup_guess(const char g, char *cg, char *ig)
{
	for (const char *ptr = cg; *ptr != '\0'; ptr++)
		if (g == *ptr || g == *ptr - 32)
			return 0;

	for (const char *ptr = ig; *ptr != '\0'; ptr++)
		if (g == *ptr || g == *ptr - 32)
			return 0;

	return 1;
}

/* is_correct_guess() checks to see if guess is right or not 
   returns 0 if guess is not correct, 1 if correct*/
int is_correct_guess(char g, char *w)
{
	g = toupper(g);

	for (const char *ptr = w; *ptr != '\0'; ptr++)
		if (g == toupper(*ptr))
			return 1;

	return 0;
}

```

Having a few issues... last guess passes through as the next player's first guess. And a few endless loops in get_guess();

Will have to look at it later.... too much code for now. Thanks. This is seriously a lot of fun.

The different cases in the function which draws the picture have a lot in common. If it was my program, I would try to make that more compact. That would have two benefits: the source code would become smaller, and changing the picture would probably need a change in only one place instead of half a dozen. Drawbacks, of course, are that it works now, and the change takes time to do and may introduce errors.

---

### Post by Bachstelze on 2011-08-27
Still a lot of issues...

get_num_players: what happens if I enter, say, '#'?
get_word and get_hint: if 1 player, you will return an uninitialized pointer. At least return NULL. No "but it's just until I implement it", that's no excuse and you don't know when you will implement it.
get_guess: how many times will I have to tell you that getchar returns an int? Before converting it to a char, you must make sure that the value is not EOF and can be represented as a char. isalpha() works, but you have to test *before* you convert to char, not after.

Also you should initialize your "game variables" at the beginning of each game intead of the end of the loop. That way, you won't forget one. ;)

---

### Post by kevinharper on 2011-08-27
@Arndt
>  I would try to make that more compact.
I tried looking into that while creating the first version and I couldn't get it. Definitely hoping to get that solved on ver4. :(

@Bachstelze
>  what happens if I enter, say, '#'?
I should just
```
system("shutdown -r 0");
```
and make it boot into login prompt. User most definitely doesn't understand how to use a computer. XD ... of course I'm kidding. I hadn't considered non-numeric input.

> get_word and get_hint: if 1 player, you will return an uninitialized pointer. At least return NULL. No "but it's just until I implement it", that's no excuse and you don't know when you will implement it.
I know it's not excuse. I was 'forced' to put up the whole source code. I was really hoping to get that on there before disclosing the whole thing. But yes... this version WILL have it (finally).

> get_guess: how many times will I have to tell you that getchar returns an int? Before converting it to a char, you must make sure that the value is not EOF
Apparently this one last time. :(
I'll get on that right away.

As for
> should initialize your "game variables" at the beginning of each game intead of the end of the loop. That way, you won't forget one.
You've identified a major problem I ran into when "reseting vars" at the end of the loop. It would get stuck in endless loop and I'd have to run back through and see which ones were causing the prob. Will switch that up right away.

---

### Post by kevinharper on 2011-08-27
Okay... here's what is there so far:
```

/* Hangman III
   Kevin Harper :: August 25, 2011 */

#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>
#include <string.h>
#include <ctype.h>

/* constant declarations */
#define MAX 255
#define INCORRECT_TRIES 7

void	clrscrn(void);
void	clrstdin( void );
int	get_num_players(void);
char*	get_word(int, int);
char*	get_hint(int);
int	check_string(const char *, int);
void	draw_hangman(int);
char	get_guess(int);
int	is_dup_guess(const char, char *, char *);
int	is_correct_guess(const char, char *);

int main(void)
{
	int num_players; /* number of players (1 or 2) */
	int player_turn = 1;
	int num_wrong_guesses = 0;

	int unique_guess    = 0,
	    correct_guess   = 0,
            was_guessed     = 0,
            was_not_guessed = 0;

	int word_length;

	char *word,
             *correct_guesses,
             guess,
             wrong_guesses[INCORRECT_TRIES + 1],
             *wg,
             *hint;

	int p1_pts = 0,
            p2_pts = 0;

	clrscrn();

	num_players = get_num_players();

	for(;;)
	{
		clrscrn();

		if (num_players != 0)
		{
			/* set vars for new player */
			num_wrong_guesses = 0;
			was_guessed = 0;
			was_not_guessed = 0;

			puts("Hangman v3 by Kevin Harper");
			printf("Player 1 pts: %d\t", p1_pts);
			printf("Player 2 pts: %d\n", p2_pts);
			word = get_word(num_players, player_turn);
			word_length = strlen(word);
			correct_guesses = (char *) malloc( word_length + 1 );

			hint = get_hint(num_players);
		}
		else
			exit(EXIT_SUCCESS);

		/* erase letters in correct_guesses & wrong_guesses */
		for (int i = 0; i < word_length; i++ )
			correct_guesses[i] = '-';
		correct_guesses[word_length] = '\0';

		for (int i = 0; i < INCORRECT_TRIES; i++ )
			wrong_guesses[i] = ' ';
		wrong_guesses[INCORRECT_TRIES] = '\0';

		wg = wrong_guesses;

		/* game... repeats until player has guessed word or has reached
			INCORRECT_TRIES - 7 incorrect tries completes hangman */
		for(;;)
		{
			/* set vars for new guess */
			unique_guess  = 0;
			correct_guess = 0;

			clrscrn();
			draw_hangman(num_wrong_guesses);
			printf("HINT: %s\n", hint);
			printf("Word: %s\n", correct_guesses);
			printf("Incorrect Tries: %s\n", wrong_guesses);
			while(!unique_guess)
			{
				guess = get_guess(player_turn);
				unique_guess = is_dup_guess(guess, correct_guesses, wg);
			}

			correct_guess = is_correct_guess(guess, word);

			/* guess is wrong
			   add guess character to wrong_guesses so it can
			   be displayed when next guess is requested */
			if (!correct_guess)
			{
				wrong_guesses[num_wrong_guesses] = guess;
				num_wrong_guesses++;
			}
			/* guess is right
			   add guess into correct_guesses
			   replaces all dashes occupying spaces where letter
			   guessed should be. */
			else
				for (int i = 0; i < word_length; i++ )
					if (word[i] == guess)
						correct_guesses[i] = guess;

			/* check to see if word has been guessed
			   or if max num of allowed incorrect guesses has
			   been reached (INCORRECT_TRIES) */
			for (int i = 0; i < word_length; i++)
			{
				if (correct_guesses[i] == '-')
					break;

				if (i == word_length - 1)
					was_guessed = 1;
			}

			if (num_wrong_guesses == INCORRECT_TRIES)
				was_not_guessed++;

			/* player has not guessed word and has not reached
			   incorrect guess limit */
			if (!was_guessed && !was_not_guessed)
			{
				continue;
			}
			/* player has guessed word
			   player (guesser) gets a point */
			else if(was_guessed)
			{
				draw_hangman(num_wrong_guesses);
				printf("Congratulations player %d!\n", player_turn);
				/* award pt for guessing right */
				player_turn == 1 ? p1_pts++ : p2_pts++;
				puts("You've guessed right and have earned a point!");

				break;
			}
			else
			/* player was not able to guess word - has reached
			   allowed incorrect tries limit */
			{
				draw_hangman(num_wrong_guesses);
				printf("Whoops! Looks like you were unable to guess the word: %s\n", word);
				/* award pt to non-guessing player */
				player_turn == 1 ? p2_pts++ : p1_pts++;
				puts("Your opponent has earned a point");

				break;
			}
		}

		/* switch player turn */
		player_turn == 1 ? player_turn++ : player_turn--;
	}

	return EXIT_SUCCESS;
}

/* clrscrn() clears terminal by inserting 30 blank lines */
void clrscrn(void)
{
	for (int x = 0; x < 30; x++ )
		printf("\n");
}

/* clrstdin() clears stdin stream */
void clrstdin(void)
{
	int ch = 0;

	while ((ch = getchar()) != '\n' && ch != EOF)
		;
}

/* get_num_players() sets the number of players.
   Function returns 0, 1, or 2 players */
int get_num_players(void)
{
	int val = 3;

	while (val > 2)
	{
		puts("Enter the number of players.");
		puts("Options: 1 or 2 players.");
		puts("Enter 0 to quit.");
		val = getchar() - 0x30;
		
		clrstdin();
		if (val > 2)
		{
			clrscrn();
			puts("This game can only be played by 1 or 2 players.");
		}
	}

	return val;
}

/* get_word() sets word to be guessed
   if 1 player, gets word from word_hint.txt 
   if 2 players, get word from a non-guesser
   word can only consist of letters */
char* get_word(int players, int pt)
{
	char word[MAX], *newline, *p_word;
	int word_length;
	bool is_valid_string = false;

	if (players == 1)
		/* get word from word_hint.txt */
		puts("get word from word_hint.txt");
	else
	{
		while (!is_valid_string)
		{
			printf("Player %d, enter a word for your opponent to guess.\n", pt);
			fgets(word, sizeof(word), stdin);
			newline = strchr(word, '\n'); /* check for trailing newline char */

			if (newline)
				*newline = '\0';   /* replace newline with a null character */

			word_length = strlen(word);
			p_word = (char *) malloc( word_length + 1 );
			strcpy(p_word, word);

			is_valid_string = check_string(word, 0);

			if (!is_valid_string)
				puts("Only letters are allowed.");
		}
	}

	return p_word;
}

/* get_hint() sets hint to help guesser narrow down options of poss words */
char* get_hint(int players)
{
	char hint[MAX], *newline, *p_hint;
	int hint_length;
	bool is_valid_string = false;

	if (players == 1)
		/* get hint from word_hint.txt */
		puts("get hint from word_hint.txt");
	else
	{
		while (!is_valid_string)
		{
			puts("Enter a short hint for your opponent.");
			fgets(hint, sizeof(hint), stdin);
			newline = strchr(hint, '\n'); /* check for trailing newline char */

			if (newline)
				*newline = '\0';   /* replace newline with a null character */

			hint_length = strlen(hint);
			p_hint = (char *) malloc( hint_length + 1 );
			strcpy(p_hint, hint);

			is_valid_string = check_string(hint, 1);

			if (!is_valid_string)
				puts("Only letters, spaces, and periods are allowed.");
		}
	}

	return p_hint;
}

/* check_string() verifies that word and hint only containe letters
   word cannot have spaces, hint can */
int check_string(const char *s, int wh)
{
	for (const char *ptr = s; *ptr != '\0'; ptr++)
		if(!(isalpha(*ptr) || (wh && (*ptr == ' ' || *ptr == '.'))))
			return 0;

	return 1;
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

/* get_guess() asks guesser to submit a guess
   guess must be a letter */
char get_guess(int pt)
{
	int ch;
	char g;

	pt == 1 ? pt++ : pt--;
	printf("Player %d, enter a guess\n", pt);

	while(!isalpha(g))
	{
		puts("Your guess must be a letter.");
		ch = getchar();

		if (ch != EOF)
		{
			g = ch;
			clrstdin();
		}
		else
			continue;
	}

	return g;
}

/* check_duplicate() checks to see if guess had previously been guessed
   accepts guess from get_guess()
   returns 0 if duplicate guess, 1 if unique guess */
int is_dup_guess(const char g, char *cg, char *ig)
{
	for (const char *ptr = cg; *ptr != '\0'; ptr++)
		if (g == *ptr || g == *ptr - 32)
			return 0;

	for (const char *ptr = ig; *ptr != '\0'; ptr++)
		if (g == *ptr || g == *ptr - 32)
			return 0;

	return 1;
}

/* is_correct_guess() checks to see if guess is right or not 
   returns 0 if guess is not correct, 1 if correct*/
int is_correct_guess(char g, char *w)
{
	g = toupper(g);

	for (const char *ptr = w; *ptr != '\0'; ptr++)
		if (g == toupper(*ptr))
			return 1;

	return 0;
}

```
Is that a fair way to determine if EOF inside get_guess() before making it a char?

At the moment the only problem this program seems to have is that it goes into an endless loop of "Player %d, enter a guess\n". This is what get_guess() prints out.

EDIT: I got rid of the looping issue by initializing g to ' ' at the beginning of get_guess. Now I can't seem to alert user that guess was duplicate. No matter where I put the alert, it only displays the "Your guess must be a letter" msg.

I've tried placing the dup alert ("You've previously guessed this letter. Please try another") inside main() and everywhere inside get_guess() but it won't display. I'm using the condition that g = ' ', thinking that if it's dup, it gets set to this and never enters the while loop within the get_guess() func. Typing that out makes me think I'm wrong, though.

Having issues rejecting non-numeric values for get_num_players().

I've tried adding isdigit(), and if values are below 0, etc. But when I add a second condition in that loop, I run the program and it skips this section altogether. It just goes straight into 2 player mode and asks player 1 for a word.

---

### Post by kevinharper on 2011-08-27
@Arndt And I'm very interested in seeing how you would cut that draw_hangman() func down in size. As I mentioned, I tried doing something like what you suggested in my first version. But being that the output goes to the terminal, I'm not sure how to "just add" an extra char to the current hangman.

---

### Post by kevinharper on 2011-08-27
Found this online.... is this it?
```

theCharacter = atoi(string[i]);
  if (isdigit(theCharacter)) {
    ...
  }

```
Is this how I can get around a user entering $ instead of an integer? :( I don't like just grabbing other people's code, though.

---

### Post by Longinus00 on 2011-08-27
I think a lot of your errors/confusion could be helped if you take a slower approach. Step through the code by yourself without compiling and running it and try to reason why things are happening. One way to force yourself to slow down is to diagram the logic on paper before attempting to write the code. This way you can be sure the error is solely in your implementation rather than your design.

Have you used malloc before? Your program has memory leaks.

---

### Post by Arndt on 2011-08-28
> **kevinharper said:**
> Found this online.... is this it?
```

theCharacter = atoi(string[i]);
  if (isdigit(theCharacter)) {
    ...
  }

```
Is this how I can get around a user entering $ instead of an integer? :( I don't like just grabbing other people's code, though.

atoi takes a string and returns a number. isdigit takes a character and returns a boolean. What connection do you see there?

What does the above code do if you enter a '$'?

When I need to be sure that a piece of input really is a number, I usually use 'sscanf'.

---

### Post by Arndt on 2011-08-28
> **kevinharper said:**
> @Arndt And I'm very interested in seeing how you would cut that draw_hangman() func down in size. As I mentioned, I tried doing something like what you suggested in my first version. But being that the output goes to the terminal, I'm not sure how to "just add" an extra char to the current hangman.

To begin with, we can put all the common code outside the switch. Three printed lines are always the same.

```
void draw_hangman( int incorrect_tries )
{
  puts( "\n  ___" );
   switch( incorrect_tries )
   {
      default:
      {
         puts( " |" );
         puts( " |" );
         puts( " |" );
         puts( " |" );
         break;
      }
      case 1:
      {
         puts( " |  &" );
         puts( " |" );
         puts( " |" );
         puts( " |" );
         break;
      }
      case 2:
      {
         puts( " |  &" );
         puts( " |  O" );
         puts( " |" );
         puts( " |" );
         break;
      }
      case 3:
      {
         puts( " |  &" );
         puts( " |  O" );
         puts( " | /" );
         puts( " |" );
         break;
      }
      case 4:
      {
         puts( " |  &" );
         puts( " |  O" );
         puts( " | /|" );
         puts( " |" );
         break;
      }
      case 5:
      {
         puts( " |  &" );
         puts( " |  O" );
         puts( " | /|\\" );
         puts( " |" );
         break;
      }
      case 6:
      {
         puts( " |  &" );
         puts( " |  O" );
         puts( " | /|\\" );
         puts( " | /" );
         break;
      }
      case 7:
      {
         puts( " |  &" );
         puts( " |  O" );
         puts( " | /|\\" );
         puts( " | / \\" );
         break;
      }
   }
   puts( " |" );
   puts( "---" );
}

```

Now it may have become easier to see what further things they have in common.

I didn't mean reusing the already drawn picture on the terminal, although that is also not a bad idea. I think ncurses or libraries built on top of that do things like that. As an optimization, this was mostly useful when the speed of the line between the computer and the screen was very slow, as it was in the 70's/80's. If you want a picture that changes very rapidly, it may still be a useful idea.

---

### Post by Bachstelze on 2011-08-28
Once again, you're making it too complicated. As I said, using isalpha is perfectly fine, but you have to do it while the input is sill an int:

```
char get_guess(int pt)
{
	int g = 0;

	pt == 1 ? pt++ : pt--;
	printf("Player %d, enter a guess\n", pt);

	while(!isalpha(g))
	{
		puts("Your guess must be a letter.");
		g = getchar();
                clrstdin();
	}

	return g;
}
```

If isalpha returns true, it means the character will be representable as a char, so nothing will be lost in the conversion.

---

### Post by Arndt on 2011-08-28
> **Bachstelze said:**
> 
```
pt == 1 ? pt++ : pt--;
```



This does what it should, but two compact alternatives that some may find more appealing are

```
pt = 3-pt;
```

```
pt = (pt%2)+1;
```

One advantage with the last one is that if you have more than two players, you simply replace the '2'.

---

### Post by ofnuts on 2011-08-28
> **Arndt said:**
> This does what it should, but two compact alternatives that some may find more appealing are

```
pt = 3-pt;
``````
pt = (pt%2)+1;
```One advantage with the last one is that if you have more than two players, you simply replace the '2'.
Actually if you want to cycle a number between 0 and MAX (inclusive), that would be:
```

pt=(pt+1)%(MAX+1)

```[ie, apply remainder **after** incrementing). And of course, if you have N players that you number from 0 to N-1, (MAX+1) is N.

---

### Post by Bachstelze on 2011-08-28
> **ofnuts said:**
> Actually if you want to cycle a number between 0 and MAX (inclusive), that would be:
```

pt=(pt+1)%(MAX+1)

```[ie, apply remainder **after** incrementing). And of course, if you have N players that you number from 0 to N-1, (MAX+1) is N.

That's nice and all but that's not what we want to do here, sorry. What sense would it make to have 0 players?

---

### Post by ofnuts on 2011-08-28
> **Bachstelze said:**
> That's nice and all but that's not what we want to do here, sorry. What sense would it make to have 0 players?If you have N players, then you index them from 0 to N-1

---

### Post by Bachstelze on 2011-08-28
You can't be serious...

"Player 0, enter a guess"

That's how every game does it!

*EDIT:* Besides, it's totally pointless to speculate about what would happen if we had more than two players. The game would be completely different.

---

### Post by kevinharper on 2011-08-28
@Longinus00
> Have you used malloc before? Your program has memory leaks. A couple of times, but just to set up simple arrays like I do here. I will look into leaks. Thanks for pointing that out. An example would be greatly appreciated.

BTW... thanks for your suggestion to step through this program on paper. Will definitely do that before I continue. There are a few issues that I need to get rid of and this may help.

@Arndt
> atoi takes a string and returns a number. isdigit takes a character and returns a boolean. What connection do you see there?
[http://www.codecogs.com/reference/c/stdlib.h/atoi.php](http://www.codecogs.com/reference/c/stdlib.h/atoi.php) basically shows that atoi() will return all ints within a string. isdigit returns true if char is a digit. Connection I guess is to use atoi() and return an int, pass it to isdigit to determine if int is indeed a number.

> What does the above code do if you enter a '$'?
Honestly? I have no clue. Haven't even been able to test that piece of code. Was curious about it so I posted it here.

> When I need to be sure that a piece of input really is a number, I usually use 'sscanf'.
This was a second suggested option. I don't know much about sscanf() but will get acquainted with it in the next few days.

And thanks for the draw_hangman() breakdown. Helps me see this in segments and I think I can do something with it to make it noticeably shorter.

@Bachstelze
> If isalpha returns true, it means the character will be representable as a char, so nothing will be lost in the conversion.
Give me about a day to digest that.

EDIT: @Arndt & @ofnuts
I appreciate the suggestions to make the game accommodate more players. But that, as Bachstelze has pointed out, is not the plan. If 0 is entered for players, the game quits. The game can only be played w/ one or two players.
> if we had more than two players. The game would be completely different.
Yes... but the game itself was never designed for players > 2.

This brings me to another realization... game quitting after # of players has been set. Maybe the user types quitquitquit for the word, and three consecutive "q" for the guess. I definitely have to add this.

---

### Post by Longinus00 on 2011-08-29
> **kevinharper said:**
> @Longinus00
 A couple of times, but just to set up simple arrays like I do here. I will look into leaks. Thanks for pointing that out. An example would be greatly appreciated.

BTW... thanks for your suggestion to step through this program on paper. Will definitely do that before I continue. There are a few issues that I need to get rid of and this may help.


There should be plenty of examples of how to use malloc online (hell, even wikipedia gives well commented examples) but it's just one in a list of things that worries me. It seems like you are using these things because you've been told to use them or you've seen it in an example somewhere without really understanding what's going on. This goes back to my previous comment about rushing too quickly.

How are you learning C? Are you following a book/online guide or enrolled in a class? If you are using a book then its probably got a section devoted to dynamic memory allocation and pointers, ditto with a class. If it doesn't then it's time to get a different book. Also, what background do you have related to programming? Is C your first language or do you have previous experience in other languages?

---

### Post by ofnuts on 2011-08-29
> **Bachstelze said:**
> You can't be serious...

"Player 0, enter a guess"

That's how every game does it!

*EDIT:* Besides, it's totally pointless to speculate about what would happen if we had more than two players. The game would be completely different.The internal index and the displayed one don't need to be the same... In a real game you would display the players names anyway.

Besides I was just answering to that tiny part:
> 
```
pt = (pt%2)+1;
```One advantage with the last one is that if you have more than two players, you simply replace the '2'.
'Nuf said.

---

### Post by Arndt on 2011-08-29
> **kevinharper said:**
> 
@Arndt

[http://www.codecogs.com/reference/c/stdlib.h/atoi.php](http://www.codecogs.com/reference/c/stdlib.h/atoi.php) basically shows that atoi() will return all ints within a string. isdigit returns true if char is a digit. Connection I guess is to use atoi() and return an int, pass it to isdigit to determine if int is indeed a number.



"All ints"? It recognizes at most one int.

A stricter language type-wise would not accept what you try to do, and might point in the right direction of correcting the code, but C does so many things with ints.

atoi("97") returns 97.
isdigit(97) is a completely valid call, but here it is absurd - 97 is not meant to be a character, it's the number we just extracted from the string. isdigit(97) is the same as isdigit('a') and will return 0.

Make sure you are clear about the different values and types of 9, "9" and '9' in C.

The page you quote suggests 'strtol', which can be better than my suggestion 'sscanf' (which still is worth knowing).

> 

[about what inputting '$' would do]

I have no clue. Haven't even been able to test that piece of code. Was curious about it so I posted it here.



There is something wrong here. If you put together a piece of code, you have to have some idea what the code will do for any input. Otherwise, it's pure luck if something works.

The functions you are using are very well-documented, which is not always the case with published interfaces.

---

### Post by kevinharper on 2011-08-29
@ofnuts I apologize if I said something that offended you. I am grateful that you have stopped by this thread to help. I really, really appreciate your time and help.

@Longinus00
> How are you learning C? Are you following a book/online guide or enrolled in a class?
I started with a book. The book has been very faulty, however. It's old and hasn't really been much help in explaining things as they are introduced. malloc(), for example... It is introduced in the book. But there is very little text dedicated to it. I guess I was more or less looking to see what exactly "memory leaks" meant as far as malloc() is concerned.

I decided to code a hangman game for the sole purpose of getting acquainted w/ programming in general and the C language specifically.

>  Also, what background do you have related to programming? Is C your first language or do you have previous experience in other languages?
I started to program back in the late 90s. I took a computer-science "intro to programming" class that taught basic. I went the second semester of this "intro to programming" course and it was taught in pascal. The third class in the series was a beginner's programming class and that was in C. I took an intermediate class after that, 1 semester of assembly and a couple of Java. I have dabbled with PHP and JavaScript. Nothing more than for dynamically generating HTML content.

The PHP and JavaScript is a little more recent. But again, it is very superficial. I haven't taken a formal programming class since 2001. I picked it up again, trying to get back into it because I really, REALLY enjoy it. I just hadn't had time. Now I'm making time for it.

So... although C is technically not my first language... This is the first time I have really attempted to soak it into my brain. But I've worked with some excellent programmers and I know they think differently. Their algorithms are very different from what I would have done. THIS IS WHAT I'M AFTER.

And your previous suggestion to put this all on paper is great. I need to learn to first develop a logical algorithm. Maybe I should scrap this third version and, literally, "go back to the drawing board" (on paper). Then I can look at all input possibilities, and whatnot. AND THEN worry about what functions I should use, etc.

I feel that a lot of the issues I'm having have to do with lack of experience.... it's been a while.

---

### Post by kevinharper on 2011-08-29
I'm marking this thread "solved" because my initial question about what was going on that caused values for word and hint to be different have been answered.

I have gotten a lot of good feedback and really think that, as Longinus00, it would be best for me to sit down and really go through all possible scenarios on paper first... I mean, there is a reason flowcharts exist, right?

Thanks guys. As always, you've provided very valuable information. My next post will be an algorithm of the game. That way we can go through issues presented by user input BEFORE the code is developed.

---

### Post by Bachstelze on 2011-08-29
There's really not a lot to change, I don't think it's necessary to start all over again. Avoiding memory leaks is simple: when you malloc() some meory, free() it after you don't need it anymore. The only thing you need to work on is handling user input, but this is language-dependent so going through it on paper won't be of much use.

As Arndt said, what you need to work on right now is understand how data is represented in C. For example undestrand why you have to make sure the value returned by getchar() is valid *before* converting it to a char.

---

### Post by kevinharper on 2011-08-29
> There's really not a lot to change
This is what I saw as I was going through this on paper. :S

I basically sketched this program out and used the same logic as I do in the code that I posted.

> when you malloc() some meory, free() it after you don't need it anymore I completely forgot about freeing up memory. I guess though, as far as this game goes, the proper time to free up the memory is when I switch players - before initializing buffers for word and hint.

And yes....
> As Arndt said, what you need to work on right now is understand how data is represented in C. For example undestrand why you have to make sure the value returned by getchar() is valid before converting it to a char.
You have no clue how frustrating this is! grr..! I remember someone (maybe it was you) telling me that this was probably one of the hardest things about C.

And although you're right... handling user input is language-specific, I think these exercises are helping me understand it to a level where I will be able to deal with user input across the board (as languages are concerned).

---

### Post by Bachstelze on 2011-08-29
> **kevinharper said:**
> 
You have no clue how frustrating this is! grr..! I remember someone (maybe it was you) telling me that this was probably one of the hardest things about C.

And although you're right... handling user input is language-specific, I think these exercises are helping me understand it to a level where I will be able to deal with user input across the board (as languages are concerned).

Those are two separate problems, though in this case they are related. First there's the problem of handling input, and then there's the problem of the representation of data. Indeed, if you decide to go the getchar() route, you will need to know about data representation in order to validate the input, but there are a lot of other instances where you need to know about it.

For the problem at hand: getchar() returns an int, which is the value (between 0 and 255) of the character read, or EOF, which is an unspecified negative value. char is either signed or unsigned, and you don't know which one it is, so let's assume the worst case: char is signed and thus can take values between -128 and 127. When you convert a value from an integer type T1 to a signed integer type T2, two things can happen: either the value can be represented in type T2, and then there is no problem, the value will not be changed in the conversion, or the value cannot be represented in type T2, and then the result is undefined.

It is therefore critical that you make sure the value returned by getchar() is in the range of acceptable values for signed char before you convert it. Since in addition you require that it be a letter, it's easy: just call isalpha() on it, and if it returns true, it means the value is in the range 65-90 or 97-122, which are both acceptable.

If char is unsigned, different rules apply (basically on a two's complement machine the value will be truncated and the result of the conversion will be its lower byte), but if you make sure the value is not EOF (which will be the case if isalpha() returns true), the conversion will also work as intended.

---

### Post by Longinus00 on 2011-08-29
> **kevinharper said:**
> 
I started with a book. The book has been very faulty, however. It's old and hasn't really been much help in explaining things as they are introduced. malloc(), for example... It is introduced in the book. But there is very little text dedicated to it. I guess I was more or less looking to see what exactly "memory leaks" meant as far as malloc() is concerned.


I highly recommend you get a better book and just go through it from front to back. The beginning sections should be so easy you'll finish them in an hour and when it starts introducing things like malloc and getchar (maybe they'll even make you write your own versions of those functions so you *really* get an idea of what they do) it will clear up all your misunderstandings. If you go to your local public library I'm sure you'll find C programming books. There's also many free books online so just get your hands on a bunch of them and see which one seems to work out best for you.

Looking at your code I think your logic is okay but you're getting lost in the actual implementation. It's obvious that the C reference you're using is woefully insufficient. Knowing you need to free after malloc isn't good enough (it isn't always true anyway, you can malloc without freeing and not have memory leaks), you need to know why you should be doing these things. This is why I recommend learning via a book/class rather than just attempting to fill in the gaps as you go along. Getting anywhere in C will require you to learn pointer gymnastics and casting and I don't think you'll be able to just happen upon that knowledge.

I think the problems others have pointed out in your input checking is just a symptom of your lack of a good reference while learning. Once you get that sorted out and get a more robust understanding you'll be able to deal with that problem easily.

---

### Post by Bachstelze on 2011-08-29
> **Longinus00 said:**
> things like malloc and getchar (maybe they'll even make you write your own versions of those functions so you *really* get an idea of what they do) 

Writing your own malloc and getchar, really? It's true that rewriting some functions of the standard library is common beginner practice, but not those two. ;)

---

### Post by Longinus00 on 2011-08-29
> **Bachstelze said:**
> Writing your own malloc and getchar, really? It's true that rewriting some functions of the standard library is common beginner practice, but not those two. ;)

Yea, you're write. They might include an example implementation for how they could be written like in Dennis Ritchies book though! ;)

Oh, here's a challenge for kevinharper. Try rewriting your program so you don't need to call malloc and just use predefined buffers (char arrays).

One last thing kevin, while you've taken my advice to get your logic down on paper, you still need to go through your program line by line and think do a run through of what it does in your head (feel free to use scratch paper to write down variable states). I think a few of your bugs crop up because you have a disconnect between what you think the code does and what it's actually doing. Relying on the compiler/interpreter to tell you what your code does will build bad habits.

---

### Post by kevinharper on 2011-08-30
>  Try rewriting your program so you don't need to call malloc and just use predefined buffers (char arrays).
This is how it was in earlier version, and how this one started.

I made the mistake of defining the arrays within the functions and not inside main(), however.

I could just declare arrays for word hint. I would pass pointers to the arrays to get_word() and get_hint(), have the functions initialize word and hint (following specific input rules of what word allows, etc). These functions would then return nothing (void).

I guess that would be a very easy solution to the memory issue.

Now... is the memory issue the following:
Every time I ask for a new word and hint, I REALLOCATE memory? So I'm not really reusing the space I was using - instead, I just keep asking for more memory? And at some point, I could have no more mem available? I thought of that this morning.... is this the issue?

---

### Post by kevinharper on 2011-08-30
> rewriting some functions of the standard library is common beginner practice
I've done that... A previous version had me looking comparing guess against 'a' - 'z' and 'A' through 'Z'

This reminds me of something I forgot to address earlier.

Arndt said:
> Make sure you are clear about the different values and types of 9, "9" and '9' in C.
9 is literal int value - the number 9.
"9" is a string value like if I wanted to put "9 cats" into a string array.
'9' is the decimal value of char 9... which, according to my "wicked" teach-yourself C book is 057.

---

### Post by Bachstelze on 2011-08-30
> **kevinharper said:**
> 
'9' is the decimal value of char 9... which, according to my "wicked" teach-yourself C book is 057.

Yes and no. In C, a number with a leading 0 is interpreted as octal, so 057 would be the decimal 47, whch is '/'. What you mean is 57. Also you should get the habit of using manual pages: to get the ASCII code of a character, [font=monospace]man ascii[/font].

---

