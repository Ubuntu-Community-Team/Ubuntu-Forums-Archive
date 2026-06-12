---
title: "C - generate random string, can you check it please"
date: 2012-05-13
forum: Programming Talk
---

### Post by buffay on 2012-05-13
Is the following function to generate a random string correct? I saw many implementation where a string was returned, but not when an empty string was taken as an argument and was filled with characters. I have some concerns about a terminating NULL character. Now user has to pass an array that has one more element that the required random string just to make sure it's correctly terminated at the end. Does it make sense?

```

#include <time.h>
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
 
void random_string(char * string, unsigned length)
{
  /* Seed number for rand() */
  srand((unsigned int) time(0) + getpid());
   
  /* ASCII characters 33 to 126 */
  int i;  
  for (i = 0; i < length; ++i)
    {
      string[i] = rand() % 94 + 33;
    }
 
  string[i] = '\0';  
}
 
int main(void)
{
  char s[31];
  random_string(s, 30);
  printf("%s\n", s);  
  return 0;
}

```

---

### Post by dwhitney67 on 2012-05-13
Your code is functional.  However I would suggest that you avoid using "magic" numbers in the code.  For instance, the number 94; it would be clearer if you used (126 - 33 + 1).  The compiler will reduce that to 94, so you do not have to worry about the operation slowing down the execution time.

The other thing I see in the code that perhaps could be done better is the function interface.  If a function accepts a buffer (char*) and a length (unsigned int or size_t), typically one would pass the length of the buffer.  In your code, you passed one byte less than the size of the buffer.  Other than having intimate knowledge of the inner workings of random_string(), no one would have known to do that.

My suggestion is that within random_string(), to alter the code so that only length - 1 characters are randomly chosen, and then you can safely slap the terminating null-character at the end of the buffer.  For example:
```

void random_string(char * string, unsigned length)
{
  /* Seed number for rand() */
  srand((unsigned int) time(0) + getpid());
   
  /* ASCII characters 33 to 126 */
  unsigned int num_chars = length - 1;
  unsigned int i;
  for (i = 0; i < num_chars; ++i)
    {
      string[i] = rand() % (126 - 33 + 1) + 33;
    }
 
  string[num_chars] = '\0';  
}

```
Lastly, the use of getpid() will probably be insignificant when seeding the random number generator.  The pid is relatively small number compared to the number of seconds since the epoch.

---

### Post by buffay on 2012-05-13
Thank you, indeed it makes this function easier to use now. However, number of random characters will be less than the number passed as the second argument to the function and also strlen() will return value lower that the number of characters in the array. Still a bit confusing for user, but maybe there is nothing that could be done about this because this is how C works. I changed 'unsigned' to 'size_t' and removed getpid() when seeding. Now my program looks like this:

```

#include <time.h>
#include <stdio.h>
#include <stdlib.h>

void random_string(char * string, size_t length)
{
  /* Seed number for rand() */
  srand((unsigned int) time(0));  
   
  /* ASCII characters 33 to 126 */
  unsigned int num_chars = length - 1;
  unsigned int i;
  for (i = 0; i < num_chars; ++i)
    {
      string[i] = rand() % (126 - 33 + 1) + 33;
    }
 
  string[num_chars] = '\0';  
}

int main(void)
{
  char s[30];
  random_string(s, 30);  
  printf("%s\n", s);  
  return 0;
}

```

---

### Post by PeterP24 on 2012-05-13
> **dwhitney67 said:**
> Lastly, the use of getpid() will probably be insignificant when seeding the random number generator.  The pid is relatively small number compared to the number of seconds since the epoch.

+1

I don't know for sure if by using unistd.h, you achieve portability of your code and it would be a shame to loose it if all you need from unistd.h is getpid(). It doesn't appear to be portable to a MSWindows environment (correct me if I am wrong) although you can probably write your own version for it. You may want to include time.h and seed your srand() function with something like:

```
srand((unsigned)time (NULL));
```

Later Edit: Oh - I see you already took @dwhitney67 advice!

---

### Post by dwhitney67 on 2012-05-13
> **buffay said:**
> ... number of random characters will be less than the number passed as the second argument to the function and also strlen() will return value lower that the number of characters in the array.

I wouldn't think of it like that.  In C, strings are null terminated.  If you want to generate an array of random characters, then that is one thing; however generating a string with random characters still implies that the last character will be a null.  That's just the nature of a string.

---

### Post by Some Penguin on 2012-05-13
(1) I wouldn't use srand() every time that the method is called.  srand() initializes the PRNG, and should be called once before all uses, instead of once before each.

(2) If you had stipulated that what gets passed in must already be a proper C string (i.e. null-terminated char*), then you wouldn't need the length because you can check for the ((char) 0).  That doesn't work for what you've written here, however, since the initial contents of the array are undefined.

---

