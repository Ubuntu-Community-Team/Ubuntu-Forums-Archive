---
title: "freeing a pointer passed to strtok_r"
date: 2009-09-11
forum: Programming Talk
---

### Post by ittiam on 2009-09-11
If I pass a pointer that was malloc-ed to strtok_r and free it later wouldn't it create a problem, a particular problem, "invalid free next size". 

The following sample program works fine,

```
#include<stdio.h>
#include<string.h>
#include<stdlib.h>

int main()
{
   char *a = NULL;
   char *token = NULL;
   char *lasts = NULL;

   a = (char *)malloc(64);
   memset(a, '\0', 64);
   strcpy(a, "You a parasite");
   token = strtok_r(a, " ", &lasts);
   while(token != NULL)
   {
      token = strtok_r(NULL, " ", &lasts);
   }
   printf("%s\n", a);
   free(a);
}

```

I am kind of confident this is not the right approach to free the memory. A strdup in this case will be redundant as all it does is malloc again from a malloc-ed string. 

Any other suggestions?

---

### Post by Arndt on 2009-09-11
> **ittiam said:**
> If I pass a pointer that was malloc-ed to strtok_r and free it later wouldn't it create a problem, a particular problem, "invalid free next size". 

The following sample program works fine,

```
#include<stdio.h>
#include<string.h>
#include<stdlib.h>

int main()
{
   char *a = NULL;
   char *token = NULL;
   char *lasts = NULL;

   a = (char *)malloc(64);
   memset(a, '\0', 64);
   strcpy(a, "You a parasite");
   token = strtok_r(a, " ", &lasts);
   while(token != NULL)
   {
      token = strtok_r(NULL, " ", &lasts);
   }
   printf("%s\n", a);
   free(a);
}

```

I am kind of confident this is not the right approach to free the memory. A strdup in this case will be redundant as all it does is malloc again from a malloc-ed string. 

Any other suggestions?

The strtok_r call inserts Nul characters in your original string, and returns pointers to the successive substrings. So if you don't make copies of the returned tokens, you shouldn't free the original string until you're done with all the tokens.

I don't see that this is apparent from the manual page.

The FreeBSD page is more explicit:

>  The strtok() function returns a pointer to the beginning of each subse-
     quent token in the string, after replacing the separator character itself
     with an ASCII NUL character.  When no more tokens remain, a null pointer
     is returned.

---

### Post by ittiam on 2009-09-11
Yes I understand that. I did not explain the problem statement properly. Assume I have tokenized the string (str) and stored the reference of each token in a separate pointer. Now I go ahead and execute the logic using those tokens. After executing the logic I want to free the string. But now the string contains only the first token and it won't free the complete memory that was allocated. 

If the above is kind of confusing, hope this clears it up
```

char *array[10];
str = (char *)malloc(len);
strcpy(str, "blah$blah$blah$blah");

token = strtok_r(str, "$", &lasts);
while(token != NULL)
{
    array[count++] = token;
    token = strtok_r(str, "$", &lasts);
}

/*.....use the array and execute appropriate logic ....*/

....
....
....

/* Now I want to free str - but str now only contains "blah". I want to free the complete string */
free(str);
```

---

### Post by Arndt on 2009-09-11
> **ittiam said:**
> Yes I understand that. I did not explain the problem statement properly. Assume I have tokenized the string (str) and stored the reference of each token in a separate pointer. Now I go ahead and execute the logic using those tokens. After executing the logic I want to free the string. But now the string contains only the first token and it won't free the complete memory that was allocated. 

If the above is kind of confusing, hope this clears it up
```

char *array[10];
str = (char *)malloc(len);
strcpy(str, "blah$blah$blah$blah");

token = strtok_r(str, "$", &lasts);
while(token != NULL)
{
    array[count++] = token;
    token = strtok_r(str, "$", &lasts);
}

/*.....use the array and execute appropriate logic ....*/

....
....
....

/* Now I want to free str - but str now only contains "blah". I want to free the complete string */
free(str);
```

I think I see what you're asking. Yes, it will free the whole string, or rather, it will free the memory that was allocated, because the memory allocation/deallocation doesn't care what's in the memory, whether there are Nul characters in the middle or not. Otherwise you couldn't use malloc for containing other data than strings.

The information about the size of the memory block is kept elsewhere, either in a header just before the block, or in some other way.

---

### Post by Habbit on 2009-09-11
I could bet that your problem is that your code handling the tokens tries to free the substrings separately, thus either corrupting the malloc arena or - magically - freeing the whole block. No matter what happens, when you try to free the original pointer (now the first token), you are assured some big nasty trouble.

---

