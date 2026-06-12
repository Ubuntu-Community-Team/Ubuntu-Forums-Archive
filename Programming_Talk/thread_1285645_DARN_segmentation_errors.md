---
title: "DARN segmentation errors"
date: 2009-10-08
forum: Programming Talk
---

### Post by BoilerEE on 2009-10-08
Ok so I am creating a menu. Using an array of structs the program must accept the commands:
ADD, FIND, PRINT_ALL, etc the rest are in the code. So I first tried a switch for the commands but remembered you cannot use switch with strings, so I decided I would have to do a very long if else if set up :/. If any one could explain an easier way of doing the commands it would be great but mainly I am just trying to get the code I have to stop having a segmentation fault. 

it is very long and complicated but I could use the help. For some reason I can't get the program to compare the command to the desired string, I found this by using the highlighted code in[COLOR=Red] red.


[/COLOR] ```

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
[COLOR=Red]    
    [/COLOR][COLOR=Red]printf("%s %s test \n", command, dish_name);  [/COLOR]  
  }

  return(0);
}

```

I have been trying to figure out the darn fault forever now...  An example input / out put is 

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

```

I know its alot to wade through but any help is well appreciated.

---

### Post by geirha on 2009-10-08
```
gets(category);
```
You have not allocated any memory for category! so you are trying to write a string of text into a random memory location. The operating system does not like that.

You really need to learn how pointers work, and how to use malloc.

Also, gets() is unsafe to use. Use fgets() instead.

Bad:
```

#include <stdio.h>
#include <stdlib.h>

int main()
{
    char *category;

    puts("Type category:");
    fgets(category,10,stdin);  // segfaults
    puts(category);

    return 0;
}

```

Good:
```

#include <stdio.h>
#include <stdlib.h>

int main()
{
    char *category;
    
    // allocate 10 bytes of memory, and have category point to it
    category= malloc(sizeof(char) * 10);
    
    puts("Type category:");
    fgets(category,10,stdin);
    puts(category);

    //free the 10 bytes of memory
    free(category);
    category= NULL;
    return 0;
}

```

---

### Post by nvteighen on 2009-10-08
A kind advice: learn to use the gdb debugger... It will help you a lot in this (and other) kind of errors much better than using "debugging output".

---

### Post by BoilerEE on 2009-10-08
So I changed the code to include the advised mallocs, but I am still getting a segmentation error after I try to add the recipe number, I believe it is exiting at the highlighted line.

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
  int i = 0, a, b, c, end = 0, find = 0, recipe_num = 0;
  float rating, rating_hold;

  //Program start
  command = malloc(sizeof(char) * 10);
  dish_name = malloc(sizeof(char) * 50);
  category = malloc(sizeof(char) * 9);

  while(end != 1)
  {
    gets(input);
    command = strtok(input, " ");

    if((strncmp(command, "ADD", 4)) == 0)
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
      [COLOR="Red"]scanf("%d", &recipe_num);[/COLOR]
    }
    else if((strncmp(command, "FIND", 5)) == 0)
    {
      dish_name = strtok(NULL, "\0");

      for(find = 0; find <= i; find++)
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
    else if((strncmp(command, "PRINT_ALL", 10)) == 0)
    {
      category = strtok(NULL, "\0");

      for(find = 0; find <= i; find++)
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
    else if((strncmp(command, "RATE", 5)) == 0)
    {
      dish_name = strtok(NULL, "\0");
      scanf("%2.1f", rating);

      for(find = 0; find <= i; find++)
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
    else if((strncmp(command, "END", 4)) == 0)
    {
      printf("have a nice day \n");
      end = 1;
    }
    else
    {
      printf("your command '%s' was not found please re-enter \n", command);
    }
  }

  return(0);
}

```

It will read the ADD command and will ask for the category and recipe number but when input the recipe number it segmentation error.

THANKS!!!

---

### Post by Arndt on 2009-10-09
> **BoilerEE said:**
> So I changed the code to include the advised mallocs, but I am still getting a segmentation error after I try to add the recipe number, I believe it is exiting at the highlighted line.

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
  int i = 0, a, b, c, end = 0, find = 0, recipe_num = 0;
  float rating, rating_hold;

  //Program start
  command = malloc(sizeof(char) * 10);
  dish_name = malloc(sizeof(char) * 50);
  category = malloc(sizeof(char) * 9);

  while(end != 1)
  {
    gets(input);
    command = strtok(input, " ");

    if((strncmp(command, "ADD", 4)) == 0)
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
      [COLOR="Red"]scanf("%d", &recipe_num);[/COLOR]
    }
    else if((strncmp(command, "FIND", 5)) == 0)
    {
      dish_name = strtok(NULL, "\0");

      for(find = 0; find <= i; find++)
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
    else if((strncmp(command, "PRINT_ALL", 10)) == 0)
    {
      category = strtok(NULL, "\0");

      for(find = 0; find <= i; find++)
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
    else if((strncmp(command, "RATE", 5)) == 0)
    {
      dish_name = strtok(NULL, "\0");
      scanf("%2.1f", rating);

      for(find = 0; find <= i; find++)
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
    else if((strncmp(command, "END", 4)) == 0)
    {
      printf("have a nice day \n");
      end = 1;
    }
    else
    {
      printf("your command '%s' was not found please re-enter \n", command);
    }
  }

  return(0);
}

```

It will read the ADD command and will ask for the category and recipe number but when input the recipe number it segmentation error.

THANKS!!!

What I get is a segmentation fault on the line

```
if((strncmp(command, "ADD", 4)) == 0)
```

because 'command' is NULL at that point. Do use gdb for debugging. I think one of the problems is that you read a number with scanf, but not the newline which is also entered, so it will make the next gets return an empty line. Don't use scanf; use fgets and then sscanf or similar, that way you have control over the input.

---

### Post by fct on 2009-10-09
GDB is good for detecting segfaults, a backtrace will help a lot.

Valgrind is another tool which will also detect some other memory-related errors, it's my favorite to detect memleaks:

[http://valgrind.org/](http://valgrind.org/)

---

### Post by dwhitney67 on 2009-10-09
```

  while(end != 1)
  {
    fgets(input, sizeof(input), stdin);
    command = strtok(input, " ");

    if(command && (strncmp(command, "ADD", 4)) == 0)
    {
      dish_name = strtok(NULL, "\n");

      if (dish_name)
      {
        ...
      }

      ...
    }
  }

```
Do _NOT_ use gets() for reading strings; use fgets().  The function fgets() will store the newline character, so you need to account for this in your strtok() calls and/or when using the input string elsewhere.  If needed, you can remove a newline character, if it is present, using:
```

char* nl = strchr(input, '\n');
if (nl) *nl = '\0';

```

_READ_ the freakin' man-pages for fgets() and strtok() so you understand how they process the data given to them.

---

