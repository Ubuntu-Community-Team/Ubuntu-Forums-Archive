---
title: "realloc does not approve of 32-bytes as the new size?"
date: 2010-01-24
forum: Programming Talk
---

### Post by ownaginatious on 2010-01-24
Hello,

Right now in my program I'm having a problem every time I try to realloc from 24 to 32 bytes of data in my program.

Here is what's causing problems:

```

char** variables = malloc(sizeof(char*));

*variables = malloc(2 * sizeof(char));
variables[0][0] = 65;
variables[0][1] = '\0';

...

variables = realloc(variables, ++var_count * sizeof(char*));

variables[var_count] = malloc((var_name_size + 1)* sizeof(char));
               
variables[var_count][var_name_size + 1] = '\0';

...


```

The purpose of this segment of the program is to increase the size of the array of char pointers so I can add another string. Everything works fine until it tries to realloc from 24-Bytes (3 pointers) to 32-bytes (4 pointers).

This is the error I get followed by a trace:

```
*** glibc detected *** /home/.../Desktop/test: realloc(): invalid next size: 0x0000000000602400 ***

```

Any ideas what's going on here?

Thanks

---

### Post by LKjell on 2010-01-24
Should be something like this. My memory in C is getting dull.

```
char **variables = malloc(sizeof(char*));
variables[0] = "Hello";
variables = realloc(variables, 2 *sizeof(char*));
variables[1] = "World";
```

---

### Post by ownaginatious on 2010-01-24
> **LKjell said:**
> Should be something like this. My memory in C is getting dull.

```
char **variables = malloc(sizeof(char*));
variables[0] = "Hello";
variables = realloc(variables, 2 *sizeof(char*));
variables[1] = "World";
```

Well ya, that's pretty much what it does (I left a lot of stuff out to prevent confusion). Due to its application though; I have to fill it character by character; rather than just a whole string.

The problem is basically when I get to what would equate to in your example: 

```
variables = realloc(variables, 4 *sizeof(char*));
```

The thing gives me this error:

```
*** glibc detected *** /home/.../Desktop/test: realloc(): invalid next size: 0x0000000000602400 ***
```

---

### Post by MadCow108 on 2010-01-24
crashes in re/malloc are almost always due to you overwriting some memory malloc uses internally

check it with valgrind

one thing in the code you posted is this:
variables[var_count] = malloc((var_name_size + 1)* sizeof(char));
variables[var_count][var_name_size + 1] = '\0';

this writes one past the end of the allocated space in _both_ levels of the array (indices begin with 0!)

variables[var_count - 1][var_name_size] = '\0';
should be correct

---

### Post by ownaginatious on 2010-01-24
> **MadCow108 said:**
> crashes in re/malloc are almost always due to you overwriting some memory malloc uses internally

check it with valgrind

one thing in the code you posted is this:
variables[var_count] = malloc((var_name_size + 1)* sizeof(char));
variables[var_count][var_name_size + 1] = '\0';

this writes one past the end of the allocated space in _both_ levels of the array (indices begin with 0!)

variables[var_count - 1][var_name_size] = '\0';
should be correct

Thanks, I actually caught that too only a few minutes before I read your post. Unfortunately though, I'm still experiencing the same problem :(.

I think I'll try the valgrind tool you've suggested.

---

### Post by dwhitney67 on 2010-01-24
This here is your problem...
```

variables[var_count] = malloc((var_name_size + 1)* sizeof(char));
               
variables[var_count][var_name_size + 1] = '\0';

```
It may not be the only problem, but at least it is a starting point for you to look at.  Hopefully, what you intended to do above is use "var_count - 1" as your index.


P.S.  Ponder this... Say you allocate 10 items; legal indices for the array are 0 through 9.  In your case, your using whatever the result of ++var_count is.  Say it is 10 after the pre-increment.  Once again, the legal range of indices is 0 through 9, yet var_count is equal to 10.  Now do you see the issue with accessing your array above?

---

### Post by ownaginatious on 2010-01-24
> **dwhitney67 said:**
> This here is your problem...
```

variables[var_count] = malloc((var_name_size + 1)* sizeof(char));
               
variables[var_count][var_name_size + 1] = '\0';

```
It may not be the only problem, but at least it is a starting point for you to look at.  Hopefully, what you intended to do above is use "var_count - 1" as your index.


P.S.  Ponder this... Say you allocate 10 items; legal indices for the array are 0 through 9.  In your case, your using whatever the result of ++var_count is.  Say it is 10 after the pre-increment.  Once again, the legal range of indices is 0 through 9, yet var_count is equal to 10.  Now do you see the issue with accessing your array above?

Thanks, but I'm still having the same problem after correcting that error. Interestingly enough, I tried running valgrind, and I receive this error several times:

```

==2088== Invalid write of size 8
==2088==    at 0x400877: find_variables (in /home/.../Desktop/test)
==2088==    by 0x40064A: main (in /home/.../Desktop/test)
==2088==  Address 0x517a520 is 14 bytes after a block of size 2 alloc'd
==2088==    at 0x4C222A8: realloc (vg_replace_malloc.c:476)
==2088==    by 0x40083F: find_variables (in /home/.../Desktop/test)
==2088==    by 0x40064A: main (in /home/.../Desktop/test)

```

Any ideas on what that could mean?

---

### Post by dwhitney67 on 2010-01-24
Did you fix the problem with this statement?
```

variables[var_count][var_name_size + 1] = '\0';

```
Examine the value of var_name_size.  This is a similar problem that I discussed moments ago.

For any other issues, I would need to see more code.

---

### Post by ownaginatious on 2010-01-24
Yes, I fixed that mistake, but it didn't fix the problem. Anyway, here is the entire method. Maybe someone can see whatever is causing it to crash:

```

char** find_variables(char* expression){

   int count = 0, extract_count = 0;
   int exp_length = str_length(expression);

   int var_name_size = 0;
   int var_count = 1;

   char** variables = malloc(sizeof(char*));

   *variables = malloc(2 * sizeof(char));
   variables[0][0] = 65;
   variables[0][1] = '\0';

   for(count = 0; count < exp_length; count++)
      if(is_english_letter(expression[count]) && count != exp_length - 1)
         var_name_size++;
      else{
         if(expression[count] != '(')
            if(var_name_size > 0){

               variables = realloc(variables, ++var_count * sizeof(char*));

               variables[var_count] = malloc((var_name_size + 1) * sizeof(char));

               variables[var_count][var_name_size] = '\0';

               for(extract_count = 0; extract_count < var_name_size; extract_count++)
                  variables[var_count][extract_count] = expression[extract_count + count - var_name_size];

               printf("Congratulations! You stored the variable %s\n", variables[var_count]);
            }

         var_name_size = 0;
      }

   *(variables[0]) = var_count + 1;

   return variables;
}


```

---

### Post by dwhitney67 on 2010-01-24
EDIT:  Ignore this comment; I jumped to conclusions a little prematurely...  A minor thing; the second part of this condition will always be true:
```

if(is_english_letter(expression[count]) && count != exp_length - 1)

```
And as far as the code you just posted, it appears that you did not fix squat.  Change the following as appropriate:
```

               variables[var_count** - 1**] = malloc((var_name_size + 1) * sizeof(char));

               variables[var_count** - 1**][var_name_size] = '\0';

               for(extract_count = 0; extract_count < var_name_size; extract_count++)
                  variables[var_count** - 1**][extract_count] = expression[extract_count + count - var_name_size];

               printf("Congratulations! You stored the variable %s\n", variables[var_count** - 1**]);

```
I'm not sure what your other home-made functions are doing, so for instance, for str_length() or is_english_letter(), use the equivalent C library calls if possible (ie. strlen() and isalpha()).

---

### Post by ownaginatious on 2010-01-24
> And as far as the code you just posted, it appears that you did not fix squat.

Sorry, I just realized I misread some of what you had posted earlier. Correcting the index fixed the issue. Thank you for your help.

Thanks to the others that helped too :).

---

### Post by MadCow108 on 2010-01-24
> **ownaginatious said:**
> Thanks, but I'm still having the same problem after correcting that error. Interestingly enough, I tried running valgrind, and I receive this error several times:

```

==2088== Invalid write of size 8
==2088==    at 0x400877: find_variables (in /home/.../Desktop/test)
==2088==    by 0x40064A: main (in /home/.../Desktop/test)
==2088==  Address 0x517a520 is 14 bytes after a block of size 2 alloc'd
==2088==    at 0x4C222A8: realloc (vg_replace_malloc.c:476)
==2088==    by 0x40083F: find_variables (in /home/.../Desktop/test)
==2088==    by 0x40064A: main (in /home/.../Desktop/test)

```

Any ideas on what that could mean?

it means your writing to memory that you shouldn't write to, e.g. space not allocated by your program.

compile with -g flag (debugging information)
then valgrind will give you the line number

---

### Post by dwhitney67 on 2010-01-24
> **ownaginatious said:**
> Sorry, I just realized I misread some of what you had posted earlier. Correcting the index fixed the issue. Thank you for your help.

Thanks to the others that helped too :).

This may enlighten you as well:
```

#ifdef HARD_WAY
variables[var_count - 1][var_name_size] = '\0';

for(int extract_count = 0; extract_count < var_name_size; ++extract_count)
{
   variables[var_count - 1][extract_count] = expression[extract_count + count - var_name_size];
}
#else
strncpy(variables[var_count - 1], &expression[count - var_name_size], var_name_size);
#endif

```

---

