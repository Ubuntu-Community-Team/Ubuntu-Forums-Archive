---
title: "c - simple number squaring  program"
date: 2010-01-25
forum: Programming Talk
---

### Post by jasperyate on 2010-01-25
I'm just starting out with c and i'm trying to write a simple input/output number squaring program.

Here's what I have

```
#include <stdio.h>
#include <math.h>

main()
{
    int c;

    c = getchar();

    while((c = getchar()) !=EOF)
        {
        int i;
        i = c * 2;

        printf("i\n", i);
        }
    return 0;
}
```The output i get seems to be the ASCII designation for the input i give. eg, for and input of '4' i get
```

4             /*this is the input i typed not an output*/
104
20

```
 im sure im missing something pretty basic, so any solutions with explanation of where im going wrong would be appreciated. cheers.

---

### Post by doas777 on 2010-01-25
watch your getchar lines. looks like you are ignoring the first char retrieved. 
also you should probably check to make sure that the chars are numeric before you operate on them (unless plan to square the numeric representation of those chars).

---

### Post by Can+~ on 2010-01-25
Read on [atoi]("http://www.cplusplus.com/reference/clibrary/cstdlib/atoi/").

---

### Post by lisati on 2010-01-25
> **doas777 said:**
> watch your getchar lines. looks like you are ignoring the first char retrieved. 

I agree. The value stored just before your loop will be lost as soon as the conditional is evaluated. Two options come to mind: (1) drop the first getchar, - or - (2) move the conditional to the end of the loop
> **doas777 said:**
> 
also you should probably check to make sure that the chars are numeric before you operate on them (unless plan to square the numeric representation of those chars).
> **Can+~ said:**
> Read on [atoi]("http://www.cplusplus.com/reference/clibrary/cstdlib/atoi/").
+1 to both the above. Stuff typed in at the keyboard is stored in a form that's good for displaying, which isn't always so useful for use in calculations.

---

### Post by Xyro on 2010-01-25
Also, you are not squaring that input, you're doubling it ;)

ASCII '4' = decimal 54, 54*2 = 104.
ASCII '\n' = decimal 10, 10*2 = 20

So, when you input "4<CR>", you have two inputs and get two outputs. As was said earlier, atoi() will fix that for you.

---

### Post by lisati on 2010-01-25
> **Xyro said:**
> Also, you are not squaring that input, you're doubling it ;) ASCII '4' = decimal 54, 54*2 = 104.

Good call. I'd noticed but forgot to mention it in my replies earlier.

---

### Post by doas777 on 2010-01-25
> **Xyro said:**
> Also, you are not squaring that input, you're doubling it ;)

ASCII '4' = decimal 54, 54*2 = 104.
ASCII '\n' = decimal 10, 10*2 = 20

So, when you input "4<CR>", you have two inputs and get two outputs. As was said earlier, atoi() will fix that for you.

i figured that was the problem but didn't feel like digging out my old ascii table.... lol.

---

### Post by Xyro on 2010-01-25
> **doas777 said:**
> i figured that was the problem but didn't feel like digging out my old ascii table.... lol.

Digging it out! Google is your friend here :) Did you get your code sorted out then?

---

### Post by dwhitney67 on 2010-01-25
> **Xyro said:**
> Digging it out! Google is your friend here :) Did you get your code sorted out then?

Or the ASCII table can be viewed locally.
```

man ascii

```

---

### Post by jasperyate on 2010-01-25
alright well it all sounds well enough but i have no idea how to implement this atoi() command youre all so fond of. this is what ive come up with:

```

#include <stdio.h>
#include <math.h>
#include <stdlib.h>

main()
{
    int c;
    printf("Enter a number: ");
    c = getchar();

    while((c = getchar()) !=EOF)
        {
        int i, j;
        i = c^2;
        j = atoi (i);
     
        printf("%d\n", i);
        }
    return 0;
}
```

Which gives me a Segmentation fault every time...and yea im an idiot i was doubling before sorry.

---

### Post by dwhitney67 on 2010-01-25
Sigh...
```

#include <iostream>

int main(void)
{
   int num = 0;

   while (1)
   {
      printf("Enter a number, or 0 to quit: ");
      scanf("%d", &num);

      if (num == 0) break;

      printf("%d x %d = %d\n", num, num, (num*num));
   }

   return 0;
}

```

If you want to read a string, just so you can become familiar with atoi(), then try this:
```

#include <stdlib.h>
#include <iostream>

int main(void)
{
   char strnum[8] = {0};

   while (1)
   {
      printf("Enter a number, or 0 to quit: ");
      fgets(strnum, sizeof(strnum), stdin);

      int num = atoi(strnum);

      if (num == 0) break;

      printf("%d x %d = %d\n", num, num, (num*num));
   }

   return 0;
}

```
You may need to use the GCC compiler option -std=gnu99 to compile the latter program.

Use only getchar() when you need to acquire a single character.  Beware that the trailing newline character will be gobbled up by the next call to getchar().  You need to "flush" the stdin stream, and I can assure you fflush() will not work.

P.S.  You will need to subtract 0x30 (or 48 ) from the result returned by getchar() to yield an int digit between 0 and 9, inclusive.

---

### Post by gnometorule on 2010-01-25
Well, I think it's encouraging when you start to fix closer to what you already had, so I'm trying to chip in with that. While the errors have been pointed out, starting with your version, here is how it should run (sitting in cafe so might not remember correctly everything, but here we go):

(1) Remove the first c = getchar() as you effectively discard the first read with it
(2) Make c *2 into c * c
(3) Now, the ascii issue. There are two easy fixes; only one i think was mentioned:

(3a) include another standard library called stdlib.h on top:

#include <stdlib.h>

then use 

atoi(c),

which is a mnemonic for 'ascii to integer.' The stdlib library contains functions that perform transormations from one C-data type to another; you'll use it and a couple of others so often that they'll become second nature.

(3b) Another pretty classical way of addressing the 'problem' that you read a character, but need an integer, **and assuming you enter only single digit integers**,  is to change

c * c

into (c - '0') * (c - '0')

Why does this work? In all character sets that you'll work with for a while, and certainly ascii, integers 0-9 and letters a-z and A-Z correspond to subsequent ascii codes. So if c is a character equal to 3, then the ascii value of 3 is 3 greater than that of 0 in ascii; and hence c - '0' = 3 ('0' is the C idiom to refer to the single character '0').

Just meant as a pet on the back. Wasn't that much off and typical issues at start. :)

---

### Post by Tony Flury on 2010-01-26
you need to atoi your input - before you do the calculation.

Also man is your friend - 

```

man atoi

```

---

### Post by nmccrina on 2010-01-26
> **dwhitney67 said:**
> Or the ASCII table can be viewed locally.
```

man ascii

```

Wow, that is amazingly cool! I never knew about that. [-o<

---

