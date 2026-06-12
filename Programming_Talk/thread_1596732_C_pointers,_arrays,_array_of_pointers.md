---
title: "C: pointers, arrays, array of pointers"
date: 2010-10-14
forum: Programming Talk
---

### Post by Pithikos on 2010-10-14
I am really confused  about this concept and I have to be done with an exercise for university until tomorrow.
I got an understanding of what pointers and arrays are.
Pointers are "variables" containing the memory adress of some variable.
Arrays are just a bunch of variables that you can access easily by an index number.

Where it gets furstrating is when I have to make a program that takes parameters. An example:

```
#include <stdio.h>

int main(int argc, char *argv[]) {
 
         int i=0;
         printf("first string's adress: %p\n", argv[0]);
         printf("number of arguments: %d \n", argc);
         
         printf("first string %s\n", *argv[0]); /*HERE IS THE PROBLEM*/
         
         for (i=0; i<argc; i++){ /*this I saw from somewhere and it works although I don't understand it completely*/
                 printf("%s\n", *argv);
         }
         return 0;
}

```Isn't it so that "argv[]" is just an array with pointers inside? So to get to the information of the array's first element i should just go with "*argv[0]" as argv[0] holds the address for the first element/parameter. And that element is a string so using "%s" should be right :confused:

Where am I wrong? Please try to explain in simple words. I read a bunch of tutorials and everything but I just got more confused.

---

### Post by GeneralZod on 2010-10-14
argv[0] will be of type char*, which you can use with printf("%s", blahblah).

*argv[0] will be of type char - in fact, it will be the first character of the first argument (argv[0][0] would be another way of writing this :))

This:

```

for (i=0; i<argc; i++){ /*this I saw from somewhere and it works although I don't understand it completely*/
                 printf("%s\n", *argv);
         }

```

should be 

```

for (i=0; i<argc; i++){ 
                 printf("%s\n", argv[i]);
         }

```

Would it be clearer if you could see where the strings came from?

```

         const char *nice_foodstuffs[] = { "sausage", "bacon", "eggs" };
         for (int food_type = 0; food_type < 3; food_type++)
	 {
	   printf("Yum - I sure like %s!\n", nice_foodstuffs[food_type]);
	 };

```

A minor variation:

```

         const char* third_food_type = "eggs";
         const char *nice_foodstuffs[] = { "sausage", "bacon", third_food_type };
         for (int food_type = 0; food_type < 3; food_type++)
	 {
	   printf("Yum - I sure like %s!\n", nice_foodstuffs[food_type]);
	 };
	 printf("But I especially like the third food type: %s\n", third_food_type);

```

or

```

         const char* third_food_type = "eggs";
         const char *nice_foodstuffs[] = { "sausage", "bacon", third_food_type };
         for (int food_type = 0; food_type < 3; food_type++)
	 {
	   printf("Yum - I sure like %s! It begins with the letter '%c'\n", nice_foodstuffs[food_type], *nice_foodstuffs[food_type]);
	 };
	 printf("But I especially like the third food type: %s\n", third_food_type);

```

or 

```

         const char* third_food_type = "eggs";
         const char *nice_foodstuffs[] = { "sausage", "bacon", third_food_type };
         for (int food_type = 0; food_type < 3; food_type++)
	 {
	   printf("Yum - I sure like %s! It begins with the letter '%c'\n", nice_foodstuffs[food_type], nice_foodstuffs[food_type][0]);
	 };
	 printf("But I especially like the third food type: %s\n", third_food_type);

```

---

### Post by dwhitney67 on 2010-10-14
And yet another example...
```

#include <stdio.h>

void function(int argc, char** argv)
{
   for (int i = 0; i < argc; ++i)
   {
      printf("%s\n", *(argv+i));  // here, the pointer is incremented by i, then dereferenced.
   }
}

int main(int argc, char** argv)
{
   function(argc, argv);

   return 0;
}

```

---

### Post by pbrane on 2010-10-14
> **GeneralZod said:**
> argv[0] will be of type char*, which you can use with printf("%s", blahblah).

*argv[0] will be of type char - in fact, it will be the first character of the first argument (argv[0][0] would be another way of writing this :))

This:

```

for (i=0; i<argc; i++){ /*this I saw from somewhere **and it works** although I don't understand it completely*/
                 printf("%s\n", *argv);
         }

```


How does this work? It doesn't work for me:
```

$ ./argv test two three
./argv
./argv
./argv
./argv

```
it just prints the first element of argv, the program name, which in this case I called the test program **argv**

dwhitney67's example works, and I understand why it works.

---

### Post by r-senior on 2010-10-14
No it doesn't work. If you look back at GeneralZod's post, it says that the piece of code you list should be something else, i.e. it should use argv[i].

---

### Post by dwhitney67 on 2010-10-14
> **r-senior said:**
> No it doesn't work. If you look back at GeneralZod's post, it says that the piece of code you list should be something else, i.e. it should use argv[i].

Or use *(argv + i).

Note for the OP:

*argv is the same as *(argv + 0)

---

### Post by Pithikos on 2010-10-14
Sorry, I posted the code after I edited it to test things. So ```
for (i=0; i<argc; i++){                 
  printf("%s\n", *argv); }
```

Should be:

```
for (i=0; i<argc; i++){                 
  printf("%s\n", *argv++); } 
```

---

### Post by Pithikos on 2010-10-14
By the way can someone explain me this?: ```
char *food[] = { "sausage", "bacon", "eggs" };
```Does this mean we have an array "food" that has pointers and each pointer points to a string(sausage, bacon, eggs)?
so food[0] has the adress of string "sausage"
so food[1] has the adress of string "bacon"
so food[2] has the adress of string "eggs"
Is my assumption right?
And if it is then shouldnt "printf("%s", *food[1])" print "bacon" on the screen? As food[1] has the adress of string "bacon" and adding the asterisk infront of it should get the value where it's pointing?
I am really confused :S

---

### Post by dwhitney67 on 2010-10-14
> **Pithikos said:**
> 
I am really confused :S
Why don't you develop a small little program and test your questions?  You learn much more by doing, than merely by reading.

---

### Post by lloyd_b on 2010-10-14
> **Pithikos said:**
> By the way can someone explain me this?: ```
char *food[] = { "sausage", "bacon", "eggs" };
```Does this mean we have an array "food" that has pointers and each pointer points to a string(sausage, bacon, eggs)?
so food[0] has the adress of string "sausage"
so food[1] has the adress of string "bacon"
so food[2] has the adress of string "eggs"
Is my assumption right?
And if it is then shouldnt "printf("%s", *food[1])" print "bacon" on the screen? As food[1] has the adress of string "bacon" and adding the asterisk infront of it should get the value where it's pointing?
I am really confused :S

Pointers and arrays (which are basically the same thing, expressed in two different ways) are generally pretty confusing to newcomers.  But they are *very* powerful, so it's necessary to learn them.

First tip - you need to realize there's no such thing as a "pointer to a string" in C.  Or a "pointer to an array" for that matter.  What you are pointing to is to the ***first element*** of that array.  "food[1]" is exactly the same thing as "&food[1][0]", a pointer to the character at the start of the food[1] array. Calling something a "pointer to an array" is just easier than saying "pointer to the first element of an array" :)

For printf(), the "%s" format expects a ***character pointer***, which is expected to be the a pointer to the first element of a zero-terminated string.  'printf("%s\n", food[1])' fulfills this requirement, while 'printf("%s\n", *food[1])' does not, as *food[1] is not a pointer, but the ***contents of*** the memory pointed to by food[1], the letter 'b'.

Hope I didn't confuse you further :)

Lloyd B.

---

### Post by Pithikos on 2010-10-14
No in fact that last post helped me a lot :P
I tested a lot following what you said and it seems to make some sense now. I just had a hard time understanding that a pointer points only to the first character of a word. Noone ever mentions it in any book or tutorial so clearly out as you did.
Secondly from some assumption I understood that ```
printf("%s", x)
``` requires an address in the place of x, something that is totally different for the other cases that don't deal with arrays.
Then I found written somewhere that according to ANSI standard ```
ptr=&array[0]
``` is the same thing as ```
ptr=array
``` So that also explains why in the hell you can print a string with just giving the array name.
Well I guess I will be able to finish that exercise now after fighting with pointers and arrays for hours :rolleyes:

---

### Post by Pithikos on 2010-10-20
btw I found this cool program in Ubuntu repository called "cdecl". You can run it and type any declaration of variables, arrays etc and it outputs the declaration in plain english.

example:
```
cdecl> explain int (*arr)[3];
declare arr as pointer to array 3 of int
cdecl> explain int **arr[3];
declare arr as array 3 of pointer to pointer to int

```Cheers

---

### Post by Zymus on 2010-10-20
```

int main(int argc, char** argv)
{
    printf("Number of arguments: %d\n", argc);
    for(int i = 0; i < argc; i++)
    {
        printf("argv[%d]: %s\n", i, argv[i]);
    }
}
```

---

