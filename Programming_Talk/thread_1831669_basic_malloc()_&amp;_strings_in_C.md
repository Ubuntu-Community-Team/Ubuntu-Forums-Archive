---
title: "basic malloc() &amp; strings in C"
date: 2011-08-23
forum: Programming Talk
---

### Post by kevinharper on 2011-08-23
Fist question:
Is this the proper way to use malloc()?
```

#include <stdio.h>
#include <stdlib.h>

#define MAX 255

int main( void )
{
   /* string/array declarations */
   char word[MAX] = " ";

   /* pointer declarations */
   char *p_word;

   puts( "Enter some text." );
   p_word = fgets( word, sizeof( word ) + 1, stdin );

   return EXIT_SUCCESS;
}

```
The reason I ask is that later, if I printf both word and p_word I get the same thing.

This leads to my second question...
Do I essentially now have two memory locations with the same value (one for word[strnlen+1] & another for p_word) - one array, one pointer/block?

---

### Post by Bachstelze on 2011-08-23
You have forgotten something. Maybe to use malloc() at all. ;)

---

### Post by kevinharper on 2011-08-23
weak... I was so excited didn't even notice!

I'm rewriting the hangman program (v2.0, if you will).

I want malloc() to allocate exactly amount of mem necessary for a string a user enters (word to be guessed).

All malloc() examples that I see have a set value (ie: malloc( 100 ) ). I have also seen malloc( strlen( word ) + 1 ).

Am I correct in that I have to ask for word and save it as char array[MAX]. AND THEN rely on malloc? This is why it seems like I would have two memory locations with the same value/size.

I understand now why my code prints the same thing for word and p_word... word is the actual mem location where pointer p_word points.. :S right?

---

### Post by Bachstelze on 2011-08-23
> **kevinharper said:**
> 
Am I correct in that I have to ask for word and save it as char array[MAX]. AND THEN rely on malloc?

Yes, this is correct. The buffer in which you store the data entered by the user must exist before you call fgets, and therefore you can't calculate its size based on the length of the input.

> I understand now why my code prints the same thing for word and p_word... word is the actual mem location where pointer p_word points.. :S right?

This is also correct. word is a memory area allocated on the stack. Since fgets return the address of the buffer on success, and you store that value into p_word, p_word will point to the first byte of word. (If fgets fails, p_word will be NULL, but word will not change.)

---

### Post by kevinharper on 2011-08-23
Oh man.. this sounds like I'm soon to get "RTFM" pretty shortly... But here goes...

How's this:
```

#include <stdio.h>
#include <stdlib.h>

#define MAX 255

int main( void )
{
   /* string/array declarations */
   char word[MAX] = " ";

   /* pointer declarations */
   char *p_word;

   puts( "Enter some text." );
   fgets( word, sizeof( word ) + 1, stdin );

   p_word = (char *) malloc( sizeof word );

   return EXIT_SUCCESS;
}

```
Soooo? I'm guessing there is a way to clear word[] and I just need to RTFM-it, right? This way there won't be a dup mem-allocation w/ the same value.

EDIT: Of course, none of this is taking into account that malloc wasn't successful in allocating space. Which, at the moment, is the least of my concerns/inquiries.

---

### Post by Bachstelze on 2011-08-23
> **kevinharper said:**
> Oh man.. this sounds like I'm soon to get "RTFM" pretty shortly... But here goes...

How's this:
```

#include <stdio.h>
#include <stdlib.h>

#define MAX 255

int main( void )
{
   /* string/array declarations */
   char word[MAX] = " ";

   /* pointer declarations */
   char *p_word;

   puts( "Enter some text." );
   fgets( word, sizeof( word ) + 1, stdin );

   p_word = (char *) malloc( sizeof word );

   return EXIT_SUCCESS;
}
```


How about you tell us what you want to do here? This is probably not it. ;)

> Soooo? I'm guessing there is a way to clear word[] and I just need to RTFM-it, right? This way there won't be a dup mem-allocation w/ the same value.

There was never double memory allocation. In your first code, the data resided in word, and p_word was just a pointer to it. A pointer only takes 4 bytes (on a 32-bit machine), it does not duplicate the data.

---

### Post by kevinharper on 2011-08-23
Okay... Then malloc() is probably not needed at all.

> How about you tell us what you want to do here?

Really simple... Ask player 1 to enter string that player 2 should guess. An array could EASILY do. I don't have any other reason to user malloc() other than for practice. But it really, really seems like overkill.

EDIT: In other words, I could just declare array[255], initialize it to " ", and fgets( array, 256, stdin ). Everything after '\0' is freed anyways, right? In other words, array[] won't keep 255 locations open until program exists... :S or will it?

If it does, then it seems that malloc() would allow me to ONLY hold memory for strlen+1 - which would use up less memory than the array method described above.

---

### Post by Bachstelze on 2011-08-23
Yes, malloc is really overkill here, but to give you an idea, if you want to allocate the buffer dynamically, you would replace

```
char word[MAX]:
```

with

```
char *word = malloc(MAX);
```

And don't forget to free() it when you're done! (And memset() it to 0 if it contains sensitive data.)

In general you use malloc in two cases: when the buffer is very large and could cause a stack overflow if you store it on the stack, or when you want to pass the buffer up the calling stack (i.e. if you want to allocate a buffer in a function and return it, if you allocate it in the stack frame of the function, it will be lost when that function returns, and possibly overwritten when you call another function).

> EDIT: In other words, I could just declare array[255], initialize it to " ", and fgets( array, 256, stdin ). Everything after '\0' is freed anyways, right? In other words, array[] won't keep 255 locations open until program exists... :S or will it?

No. Your buffer will always be 255-byte long. What if first you store a 10-character string in it, and then a 20-character one? If the array is automatically shrunk to fit the first one, the second one will overflow.

> If it does, then it seems that malloc() would allow me to ONLY hold memory for strlen+1 - which would use up less memory than the array method described above.

Yes, so you can do that for example if you want to save the string for later use, and then ask the user for another string.

---

### Post by kevinharper on 2011-08-23
> No. Your buffer will always be 255-byte long. What if first you store a 10-character string in it, and then a 20-character one? If the array is automatically shrunk to fit the first one, the second one will overflow.
I can't believe I missed this... I initialize ALL of my arrays to " " when I declare them. Duh!

> Yes, so you can do that for example if you want to save the string for later use, and then ask the user for another string.
PERFECT! I will use malloc, after all! I ask user for two strings 1) word_to_be_guessed; 2) a_short_hint.

I was declaring one array for each one, this way I can declare just one named buffer. And no.. no sensitive data. :) Just a word that will be used in hangman.

Thanks for your helps. Cheers!

---

### Post by Bachstelze on 2011-08-23
> **kevinharper said:**
> 
PERFECT! I will use malloc, after all! I ask user for two strings 1) word_to_be_guessed; 2) a_short_hint.

I was declaring one array for each one, this way I can declare just one named buffer. And no.. no sensitive data. :) Just a word that will be used in hangman.

Thanks for your helps. Cheers!

Don't do this, though. ;)

```
char buf[255];
/* input... */
char *s1 = malloc(strlen(buf)+1);
s1 = buf;
```

---

### Post by dwhitney67 on 2011-08-23
A couple of notes...

If you provide fgets() with a buffer whose size is (2+ bytes) greater than the string that is inputted by the user, then the terminating newline (which the user entered) will be stored within the buffer.  Consider this when dealing with a string inputted by the user.

To remove the newline, consider the following:
```

...
char buf[13];

printf("Enter common phrase: ");
fgets(buf, sizeof(buf), stdin);    /* user enters Hello World */

char* newline = strchr(buf, '\n');

if (newline)
{
   *newline = '\0';   /* replace newline in buf with a null character */
}
...

```

The second thing to consider, if you want to allocate and clear a buffer (to zero, or null characters), you can use calloc()... which is a "cousin" to malloc().
```

...
char* buf = calloc(13, sizeof(char));

printf("Enter common phrase: ");
fgets(buf, 13, stdin);   /* cannot use sizeof() here! */
...
free(buf);

```

As for your "Hangman" game, you do not require the need to allocate memory from the heap; just assume the user will input a "small" amount of data, and govern how much is accepted by using fgets().

---

### Post by kevinharper on 2011-08-24
Awesome! Thanks!

I know that malloc() is overkill for this simple program, I just wanted to get some practice with it. But I have decided to stay away from it right now. I am making a similar game to what I made before but with more player interactivity, like scores and quiting the game.

I REALLY like your suggestion on how to replace '\n' with '\0'. Very clean and compact.

Thanks.

---

