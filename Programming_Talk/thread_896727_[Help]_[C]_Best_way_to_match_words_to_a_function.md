---
title: "[Help] [C] Best way to match words to a function"
date: 2008-08-21
forum: Programming Talk
---

### Post by loganwm on 2008-08-21
I have a string from input thats reads this example:

```
[B] [a] [s] [h] [ ] [t] [e] [s] [t]
```

And it adds a pointer in the array "STRING_KEY[index]" to the first letter of each word, and then replaces the spaces {Ex: Position 4} with a Null terminating char.

```
so if I were to call printf("%s",STRING_KEY[0]) then "Bash" is printed. {and using index 2 gives "test"}
```

I need to check STRING_KEY[index] against a command, and then match up syntax and the following words.

right now I have a multilayer sequence of:

```
if (strcasecmp(STRING_KEY[index],"bash") == 0) {
  **pseudo code to put all the words after index 0 into a string to be passed on as args**
  system(string of args)
}
```

but to check matches between a large number of words, I have a whole lot of "ifs"

I found that switch() doesn't work for me, and I'm interested in finding what will.

Help is appreciated.

---

### Post by nvteighen on 2008-08-21
Maybe what you want is an array of strings (in other words, a char **)? But that would possibly imply using dynamic allocation.

Then, you can use a for-loop to iterate through the array, and check the condition for all strings until the correct one is found.

---

### Post by loganwm on 2008-08-21
> **nvteighen said:**
> Maybe what you want is an array of strings (in other words, a char **)? But that would possibly imply using dynamic allocation.

Then, you can use a for-loop to iterate through the array, and check the condition for all strings until the correct one is found.

I have no issues obtaining my strings, its the checking them against the command list that uses a large number of if statements that looks bulky to me.

BTW: Out of curiousity, a char ** IS a string array?
can you give me an example, I might find it interesting!

---

### Post by dwhitney67 on 2008-08-21
I don't know if you have much experience issuing command-line arguments to a program that is written in C (or C++), but the 'argv' is an array of string(s).

Here's a simple little program that I wrote per **nvteighen** suggestion; let me know if you have any questions.
[PHP]#include <string.h>
#include <stdlib.h>
#include <stdio.h>


int main( int argc, char **argv )
{
  const char *cmds[4] = { "bash", "ls", "ifconfig", "etc" };

  if ( argc < 2 )
  {
    printf( "Usage:  %s <cmd [options]>\n", argv[0] );
    return 1;
  }

  // build string from command line args...
  //
  char *str = 0;

  for ( size_t i = 1; i < argc; ++i )
  {
    str = realloc( str, strlen(argv[i])+1+1 );

    sprintf( str+strlen(str), "%s ", argv[i] );
  }

  if ( str == 0 )
  {
    return 1;
  }

  str[strlen(str)-1] = '\0';  // remove trailing white-space

  
  #ifdef DEBUG
  printf( "str = %s\n", str );
  #endif

  size_t i = 0;
  for ( ; i < sizeof(cmds)/sizeof(char*); ++i )
  {
    if ( strncmp( cmds[i], str, strlen(cmds[i]) ) == 0 )
    {
      // issue command
      //
      system( str );
      break;
    }
  }

  if ( i == sizeof(cmds)/sizeof(char*) )
  {
    printf( "Error:  Command '%s' not recognized.\n", str );
  }

  free( str );

  return 0;
}[/PHP]

---

### Post by nvteighen on 2008-08-21
> **loganwm said:**
> I have no issues obtaining my strings, its the checking them against the command list that uses a large number of if statements that looks bulky to me.

Ah... they're command line arguments! Have you seen unistd.h's getopt()? It's a way to parse long lists of command line arguments.

> BTW: Out of curiousity, a char ** IS a string array?
can you give me an example, I might find it interesting!

Of course! Think of it: it's a pointer to a pointer to a char. As arrays are pointers, we can say it's a pointer to an array of chars. An array of chars is a string, so it's a pointer to a string. And again, as pointers are arrays, finally char ** is an array of strings :) 

[PHP]
#include <stdio.h>
#include <malloc.h> /* For malloc() and friends */

int main(void)
{
    /* I'll skip error checks after allocating memory to save space in 
     * the post. You shouldn't skip them in your program. */

    /* Allocate an array of 4 strings. I use calloc() instead of malloc()
     * because it automatically initializes memory to 0. */
    char **strarray = (char **)calloc(4, sizeof(char *));

    /* Now, allocate space for the strings in the array. To simplify
     * things, I'll allocate 80 bytes for all. But they can be of any 
     * size you need and all different. I use a loop just to make the 
     * code a bit nicer. */
    int i;
    for(i = 0; i < 4; i++)
        strarray[i] = (char *)calloc(80, sizeof(char));

    /* Here you're able to do what you want with your strings. You access
     * them by their index. strarray[i][j] will access the j-th character
     * in the i-th string, as expected. */

    /* At the end, as we have allocated memory through calloc(), we have 
     * to free() it. First, we deallocate the strings; then, the list.
     * Otherwise, we have a leak. */
    for(i = 0; i < 4; i++) /* Recycling 'i' from the last loop. */
        free(strarray[i]);

    free(strarray); /* And finally, we wipe the list. */

    return 0;
}
[/PHP]

But be careful, after you have allocated a string, the only way to change its contents without corrupting memory is assigning each character by one. The best way to do that is using strcpy(), otherwise, you get a dissaster! (try it :))

---

