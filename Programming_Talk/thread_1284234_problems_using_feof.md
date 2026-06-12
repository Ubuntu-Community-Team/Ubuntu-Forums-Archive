---
title: "problems using feof"
date: 2009-10-06
forum: Programming Talk
---

### Post by BoilerEE on 2009-10-06
```

#include <stdio.h>
#include <string.h>
#include <stdlib.h>

#define MAXLENGTH 50

typedef enum {soups, salads, entrees, desserts} category;
typedef enum {ADD, FIND, PRINT_ALL, RATE, END} func;

struct dish{
  char *dish_name;
  char *category;
  int recipe_num;
  int rating[3];
};

int main()
{
  //Initialization
  struct dish   tmp, menu[100];
  char input[100], dish_name[150];
  int i = 0,c,* pnt_dish_name;
  
  //Program start
  [COLOR=Red]while(!feof((pnt_dish_name = dish_name[i])))[/COLOR]
  {
    scanf("%s", input);
    c = getchar(); 
    dish_name[i++] = c;
  }
  
  printf(input, dish_name);
  return(0);
}

```
I keep getting an error with the line in red, I am trying to assert that the value in dish_name[] is the EOF, but keep getting an error about 
 [COLOR=Red]warning: assignment makes pointer from integer without a cast
warning: passing argument 1 of &#8216;feof&#8217; from incompatible pointer type[/COLOR]

when I try to de-reference dish_name[] I get a  [COLOR=Red]invalid type argument of &#8216;unary *&#8217; [COLOR=Black]error I de-reference dish_name[] by puting *(dish_name[i]) instead of dish_name[i]

please halp THANKS [/COLOR]
[/COLOR]

---

### Post by MadCow108 on 2009-10-06
your assigning a char to a pointer, of course that won't work ( the [] operator is already a dereferencing operator, it does just transform ar[i] to *(ar+i) )
also feof checks if the eof indicator of a FILE* stream is set and does not work on arbitrary pointers.

scanf does not return EOF in its format arguments but in its return value.
so do something like this:
```

int read=0;
while ((read = scanf(...)) != EOF) {
//dostuff
}

```

---

### Post by BoilerEE on 2009-10-06
I changed that while to 
```

 while((c = scanf("%c")) != "EOF");
  {
    scanf("%s %c", input, &dish_name[i++]);
  }

```but am still getting 
warning: comparison between pointer and integer

is it saying that the "EOF" is a pointer? I defined c as a char, and as an int still get the same warning. 

Thanks for your help

---

### Post by MadCow108 on 2009-10-06
not "EOF" (which is a const char* so a pointer)
just EOF without the quotes which is some (by the stdio library) predefined integer value
and you shouldn't define c as a char because scanf returns an int!
your truncating the value (although it probably won't matter as long as your not reading more than 256 values)

I'm also not quite sure if your splitting in two scanf's will work.
Whats the format of the file your reading?

---

### Post by BoilerEE on 2009-10-06
I need to input a command then a name of object... i.e.

ADD pasta

adds the menu item pasta to a struct menu and prompts for other info about pasta.

---

### Post by MadCow108 on 2009-10-06
if it are always pairs of words then its as simple as this:
```

int read=0;
int counter=0;
char cmd[100],menu[100];
while ((read = scanf("%s %s",cmd,menu)) != EOF) {
  if (read != 2)
   printf("error: no even number of arguments\n");

  if (strcmp(cmd,"ADD") == 0) {
    // add menu to struct
  }
}

```
here some scanf reference:
[http://www.cplusplus.com/reference/clibrary/cstdio/scanf/](http://www.cplusplus.com/reference/clibrary/cstdio/scanf/)

---

### Post by dwhitney67 on 2009-10-06
It is better/safer to use fgets() to read variable length strings than it is to use scanf().

Here's an example of fgets() obtaining input from standard-in.  When the use enters ctrl-D, the fgets() interprets this as an EOF condition, and returns NULL.  When an input is given, strtok() is used to dissect the given input into hopefully two valid tokens: a command and menu item.
```

#include <stdio.h>
#include <string.h>

int main()
{
   char str[100] = {0};

   while (fgets(str, sizeof(str), stdin) != 0)
   {
      char* cmd  = strtok(str,  " ");
      char* menu = strtok(NULL, "\n");

      if (cmd && menu)
      {
         // do something with 'cmd' and 'menu'
      }
   }

   return 0;
}

```

---

### Post by MadCow108 on 2009-10-06
you can also use the max length identifier in the format string (e.g. %100s for a char str[100] buffer) or use the %as flag(non-portable!) which also makes scanf (and all other format based functions) save.

fgets has the advantage that you can read in whitespace separated strings into a single buffer unlike scanf, so it may be worth looking at for your problem.

---

### Post by dwhitney67 on 2009-10-07
> **MadCow108 said:**
> you can also use the max length identifier in the format string (e.g. %100s for a char str[100] buffer)...
Actually, for a char str[100], the format should be "%99s".  You don't want to consume the last space of the string, which generally should be reserved for the null-character that terminates the string.

Anyhow, this is yet another reason why scanf() is not desirable for the reading of strings.  Its usage is prone to user-error.

---

### Post by BoilerEE on 2009-10-08
Alright so I got the input worked out and I thank everyone for their help, I got the program written but am getting a segmentation error.
it is very long and complicated but I could use the help. 

SORRY but the curly brackets got messed up in transfer... but they are correct in the program
```

#include <stdio.h>
#include <string.h>
#include <stdlib.h>

#define MAXLENGTH 50

struct dish{
  char *dish_name;
  char *category;
  int recipe_num;
  float rating[3];
}menu[100];

int main()
{
  //Initialization
  char input[70], *tmp, *command, *dish_name, *category;
  int i = 0, a, b, c, end = 0, find = 0, recipe_num;
  float rating, rating_hold;    

  //Program start
  while(end != 1)
  {
    gets(input);
    command = strtok(input, " ");
    
    if(strncmp(command, "ADD", 3))
    {
      dish_name = strtok(NULL, "\0");
      for(a = 0; a < 3; a++)
      {
        menu[i].rating[a] = 0;
      }
      menu[i].dish_name = dish_name;
      i++;
      
      printf("Enter category (Soups, Salads, Entrees, Desserts) \n");
      gets(category); 
      
      printf("Enter recipe number: ");
      scanf("%d", &recipe_num);
    } 
    else if(strncmp(command, "FIND", 4))
    {
      dish_name = strtok(NULL, "\0");
      
      for(find = 0; find < i; ++find)
      {
        if(menu[i].dish_name == dish_name)
    {
      printf("%s %i", menu[i].dish_name, menu[i].recipe_num);
    }
        else
    {
      printf("your dish '%s' was not found\n", dish_name);
    }     
      }
    }  
    else if(strncmp(command, "PRINT_ALL", 9))
    {
      category = strtok(NULL, "\0");
     
      for(find = 0; find < i; ++find)
      {
        if(menu[i].category == category)
    {
      printf("%s %d", menu[i].dish_name, menu[i].recipe_num);
          
          for(a = 0; a < 3; a++)
      {
        printf("%f", menu[i].rating[a]);
      }  
        }
        else
    {
      printf("no dishes of the category '%s' in menu \n", category);
    }  
      }
    } 
    else if(strncmp(command, "RATE", 4))
    {
      dish_name = strtok(NULL, "\0");
      scanf("%2.1f", rating);
      
      for(find = 0; find < i; ++find)
      {
    if(menu[i].dish_name == dish_name)
    {
      menu[i].rating[3] = rating;

      for(b = 0; b < 2; b++)
      {
        if(menu[i].rating[b] < menu[i].rating[b+1])
            {
          rating_hold = menu[i].rating[b];
          menu[i].rating[b] = menu[i].rating[b+1];
          menu[i].rating[b+1] = rating_hold;
        }
      }
    }
        else
        {
      printf("your dish '%s' was not found please try again \n", dish_name);
    }
      }
    }
    else if(strncmp(command, "END", 3))
    {
      end = 1;
    }
    else
    {
      printf("your command '%s' was not found please renter \n", command);
    }  
  }

  return(0);
}

```I have been trying to figure out the darn fault forever now...  An example input / out put is 
```

ADD chocolate cake
your command 'ADD' was not found please renter 
FIND chocolate cake
Enter category (Soups, Salads, Entrees, Desserts) 
Soups
Segmentation fault
$ a.out
FIND chocolate cake
Enter category (Soups, Salads, Entrees, Desserts) 
Salads
Segmentation fault
$ a.out
END
Enter category (Soups, Salads, Entrees, Desserts) 
Entrees
Segmentation fault
$ a.out
PRINT_ALL Soups
Enter category (Soups, Salads, Entrees, Desserts) 
Salads
Segmentation fault


```I know its alot to figure out but any help is well appreciated.

---

### Post by dwhitney67 on 2009-10-08
When you save a string, for instance the dish_name, into your structure, you need to make a duplicate of that string.  Otherwise the memory location of the original string will be overwritten by the next iteration of the while loop.

You have realize that 'dish_name' is a pointer to a subset of the string originally referenced by 'input', and where there was a space-character, strtok() slapped in a null-termination-character.

Consider using strdup() for copying and allocating space for the strings you want to save.

You also need to realize that strtok() could potentially return NULL (if it fails to parse the input).  You should consider that possibility in your code.

Don't forget... 1) read the man-page on strdup(), and 2) de-allocate the memory allocated by strdup() just before your program completes.

P.S.  If possible, you should consider programming in the ISO-1999 standard of C.  GCC supports the standard, although not 100%.

It would allow for you to declare variables closest to where they are first used, and even permit you to declare temporary variables in a for-loop initialization section.

The other recommendation is that you initialize all of your variables when they are declared.  Avoid bunching up the declaration of similar type variables onto one line of code.  It makes the code harder to read, and on occasion, harder to maintain.

P.S. #2

Don't use gets() to read in a string!  You do not have the means to convey to the application what size string you are interested in reading when you use this function.  Thus from an IA (Information Assurance) perspective, usage of gets() is a security risk because the operator could potentially enter more data than is expected, thus causing the application to crash or perform other unintended actions.  Use fgets() instead.

---

### Post by MadCow108 on 2009-10-08
and don't post 2 threads concerning the same problem!
[http://ubuntuforums.org/showthread.php?t=1285645](http://ubuntuforums.org/showthread.php?t=1285645)

---

