---
title: "Simple C program help =)"
date: 2009-10-19
forum: Programming Talk
---

### Post by mickmouse13 on 2009-10-19
Just a simple ZOMBIE! program... I want it to ask "are you a zombie" and be able to putt in yes or no. yes giving the long drawn out zombie attack and no giving a string saying "noooooooope" this is what i have so far i am having trouble with the "yes/no" thing.
```

 #include <stdio.h>

int main()
{
    int zombie;
    printf ( "are you a zombie?\n" );
    scanf ( "%d", &zombie );
        if ("%d" == "yes" ){
        /*zombie texxxxxxts*/
            printf( "i am alive! Beware.\n" "oh no what ya gonna do?\n" "yer all gonna die!\n" "rawr\n");
            printf( "mmmMMMRRRRRRREEEAAGHHHHH\n" );
        }
    else {
    printf ( "nooooooope\n" );
    }
    getchar();
        return 0;
}
```
the idea is to make a container (cant think of the name right now) to hold zombie.. then have the input asked and save the answer to "zombie" after that i want it to check for "yes" or "no", then print the respective phrases. 
PS. someone mentioned stating my ints. im not sure what he meant. Im pretty new to this but quick help is appreciated =) 
This program runs and compiles fine but no matter what i do it says "NOOOOOOPE" i have been playing with it for a while so idk.

---

### Post by jpmelos on 2009-10-19
OK, you are declaring an **int** (stands for integer)... Why are you expecting an "yes" as answer? The most correct would be to declare a **char** (stands for character) and ask for an **'y'** or **'n'** as answer:

```
#include <stdio.h>

int main()
{
    char zombie;
    printf ( "are you a zombie? (y/n)\n" ); /*asks for y or n as answer*/
    scanf ( "%c", &zombie );
    if (zombie == 'y' ){ /*compares char to char, see?*/
    /*zombie texxxxxxts*/
        printf( "i am alive! Beware.\noh no what ya gonna do?\nyer all gonna die!\nrawr\n"); /*no need to separate strings here*/
        printf( "mmmMMMRRRRRRREEEAAGHHHHH\n" );
    } else {
        printf ( "nooooooope\n" );
    }
    getchar();
    return 0;
}
```

You should pay more attention to indentation as well. It makes reading your code easier... My changes are not the only possibility... There are other options.

---

### Post by mickmouse13 on 2009-10-19
Thanks that works great. But for future things is there a way to input whole words?

---

### Post by jpmelos on 2009-10-19
Yes, you can declare an array of chars, and that makes a string. But, before dealing with strings, you should have a complete understanding of pointers and arrays... That's highly recommended. To declare an array, read it and print it, it would be like this:

```
char name[TAM];
scanf("%s", name);
gets(name);
printf("%s", name);
```

These commands do this, in order of appearance:

[LIST]
[*]Declares an array with space to TAM-1 characters (when you study strings, you'll find out that the last character is reserved to the '\0' char, that signs the end of the string);
[*]Reads a string until the first whitespace is found (whitespace must be understood as space, tab or newline). Notice, the second argument has no '&' before the variable name. That's because the name of an array is actually a pointer to the first element of it. I reinforce: study pointers and arrays before using strings;
[*]Reads a string until the first newline or tab is found (you can type spaces);
[*]Prints a string until it finds a '\0' character (it indicates the end of the string).
[/LIST]

---

### Post by jessiebrownjr on 2009-10-19
You can also change 
```
if (zombie == 'y' )
```
to
```
if (zombie == 'y' || zombie=='Y' )
```

This will cover capslock being on...
another good thing to do I think if you want is isolate ONLY being able to input Y/y or N/n inputs. You can do a nested loop for that I think is what its called.. Im learning C currently too, and it went over that as well.

---

### Post by jpmelos on 2009-10-19
Yea, you can do this:

```
#include <stdio.h>
#include <ctype.h>

int main()
{

    char zombie;
    printf("Are you a zombie? (y/n) ");
    scanf("%c", &zombie);
    zombie = toupper(zombie);
    while (zombie != 'Y' && zombie != 'N') {
        printf("Incorrect input. Are you a zombie? (y/n) ");
        scanf("%c", &zombie);
        zombie = toupper(zombie);
    }
    if (zombie == 'Y') {
        printf("I am alive! Beware.\nOh no what ya gonna do?\nYer all gonna die!\nRawr!\nmmmMMMRRRRRRREEEAAGHHHHH\n");
    } else {
        printf ("Nooooooope!\n");
    }
    getchar();
    return 0;
}
```

The function **toupper(char c)** returns the uppercase char version of c, or c itself if there's no uppercase. This function is in the ctype.h header.

---

