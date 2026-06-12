---
title: "code improvement?"
date: 2012-09-20
forum: Programming Talk
---

### Post by conradin on 2012-09-20
Hi all, 
I have a trivial C program which I wrote to make every combination of three letters followed by "0h". The program works fine, but I keep thinking that it could be simplified. If Anyone wants, I wouldn't mind pointers to simplify my code.
```

#include <stdio.h>
int main()
{
	int i;
	for (i = 97; i < 123; i++) //ascii lowercase
	{	
		char a=i;
		int j;
		for (j = 97; j < 123; j++)
		{	
			char b=j;
			int k;
			for (k = 97; k < 123; k++) 
			{
				char c=k;
				printf("%c%c%c%s\n",a,b,c, "0h" );
			}
		}
	}
return 0;
}

```

sample output:
```

.....
zzs0h
zzt0h
zzu0h
zzv0h
zzw0h
zzx0h
zzy0h
zzz0h


```

---

### Post by satsujinka on 2012-09-20
> **conradin said:**
> Hi all, 
I have a trivial C program which I wrote to make every combination of three letters followed by "0h". The program works fine, but I keep thinking that it could be simplified. If Anyone wants, I wouldn't mind pointers to simplify my code.
```

#include <stdio.h>
int main()
{
	int i;
	for (i = 97; i < 123; i++) //ascii lowercase
	{	
		char a=i;
		int j;
		for (j = 97; j < 123; j++)
		{	
			char b=j;
			int k;
			for (k = 97; k < 123; k++) 
			{
				char c=k;
				printf("%c%c%c%s\n",a,b,c, "0h" );
			}
		}
	}
return 0;
}

```

sample output:
```

.....
zzs0h
zzt0h
zzu0h
zzv0h
zzw0h
zzx0h
zzy0h
zzz0h


```
Algorithm wise, that's probably about as good as you're going to get. However, you could drop the chars a, b, and c and just use i, j, k to display the characters.

If you really want to loose lines, you could use C99 which would allow you to do this:
```
int main(void) {
    for(int i = 97; i < 123; i++) {
        for(int j = 97; j < 123; j++) {
            for(int k = 97; k < 123; k++) {
                printf("%c%c%c%s\n", i, j, k, "Oh");
            }
        }
    }
}

```
Then compile with:
gcc yourfile.c -o yourfile -include stdio.h -std=c99


Generally, your code's about as good as it's going to be for a toy problem like this.

---

### Post by steeldriver on 2012-09-20
I was going to suggest much the same - except iterating over the char type directly (which is legal - I think - and imo makes it clearer what the code is doing)

[ DISCLAIMER: I am not a professional programmer ]

Also you might want to  #define the start and stop values just so it's easy to modify the range. 

```
#include <stdio.h>

#define ASCII_START 'a'
#define ASCII_STOP 'z'

int main()
{
    char a, b, c;

    for (a = ASCII_START; a <= ASCII_STOP; a++) //ascii lowercase
    {    
        for (b = ASCII_START; b <= ASCII_STOP; b++)
        {    
            for (c = ASCII_START; c <= ASCII_STOP; c++)
            {
                printf("%c%c%c%s\n",a,b,c, "0h" );
            }
        }
    }
    return 0;
}
```These are just stylistic suggestions - they don't modify your algorithm, just make it a little easier to see what the code is doing.

---

### Post by satsujinka on 2012-09-20
For comparison, here's my version using chars (which I do agree makes it a bit clearer, though I don't think the #defines help.)
```
int main(void) {
    for(char a = 'a'; a <= 'z'; a++) {
        for(char b = 'a'; b <= 'z'; b++) {
            for(char c = 'a'; c <= 'z'; c++) {
                printf("%c%c%c%s\n", a, b, c, "Oh");
            }
        }
    }
}
```

---

### Post by dwhitney67 on 2012-09-20
Here's my version, which when measured with 'time', appears to outperform previous versions that have been posted.
```

#include <stdio.h>
#include <string.h>

int main(void) {
    char combo[17576 * 6 + 1];
    int i = 0;
    for(char a = 'a'; a <= 'z'; a++) {
        for(char b = 'a'; b <= 'z'; b++) {
            for(char c = 'a'; c <= 'z'; c++) {
                sprintf(combo + (6 * i++), "%c%c%c%s\n", a, b, c, "Oh");
            }
        }
    }
    printf("%s", combo);
    return 0;
}

```

Note that output to the screen is awfully slow.  That's why the version above is slightly faster.

P.S.  About the "magic" numbers:  17576 = 26 * 26 * 26
Each combination consists of 6 characters (e.g. "abc0h\n").  An extra space is added for null-character at the end of the string.

---

### Post by satsujinka on 2012-09-20
> **dwhitney67 said:**
> Here's my version, which when measured with 'time', appears to outperform previous versions that have been posted.
```

#include <stdio.h>
#include <string.h>

int main(void) {
    char combo[17576 * 6 + 1];
    int i = 0;
    for(char a = 'a'; a <= 'z'; a++) {
        for(char b = 'a'; b <= 'z'; b++) {
            for(char c = 'a'; c <= 'z'; c++) {
                sprintf(combo + (6 * i++), "%c%c%c%s\n", a, b, c, "Oh");
            }
        }
    }
    printf("%s", combo);
    return 0;
}

```

Note that output to the screen is awfully slow.  That's why the version above is slightly faster.

P.S.  About the "magic" numbers:  17576 = 26 * 26 * 26
Each combination consists of 6 characters (e.g. "abc0h\n").  An extra space is added for null-character at the end of the string.

I'd imagine that it uses sizeof(combo) more memory though ;)
(~400 KiB)

While we're on the optimization train, here's one that the compiler will probably do for you.
```
int main(void) {
    char combo[409657]; //compiler will calc. this for you
    int i = 0;
    for(char a = 'a'; a <= 'z'; a++) {
        for(char b = 'a'; b <= 'z'; b++) {
            for(char c = 'a'; c <= 'z'; c++) {
                sprintf(combo + i, "%c%c%c%s\n", a, b, c, "Oh");
                i += 6; //addition is faster than multiplication
            }
        }
    }
    printf("%s", combo);
    return 0;
}

```

EDIT: forgot the command
gcc yourfile.c -o yourfile -include stdio.h -include string.h -std=c99

---

### Post by Some Penguin on 2012-09-21
It could also be restructured to be more easily generalized to different N.

pseudocode:
```

print_helper:  (string so far, # chars left)
  if # of chars left is less than 1, roll eyes and explode
  for (each possible char)
       compute string so far + that char
       if # of chars left is 1, just print that string, the 0h suffix, and a newline;
       else, recurse w/ print_helper (new buffer, # chars left - 1)

```

to avoid massive allocation:  you can allocate a single buffer set up to hold n characters, pass along the index as well as an additional argument, and just change characters within that buffer.  Might as well pass the suffix as a parameter, too.

If you wanted to support massive N, enough to explode the call stack... you could do it with e.g. a bignum library, just converting each number to mod 26, just iterating over all possible values.  Or, painstakingly, do the math yourself and 'increment' the final character in the array, carrying over 'z' -> 'a' and incrementing the preceding column, if you wanted to do it w/o a bignum library.  Those aren't really simpler, but they generalize better than using N nested loops.

---

### Post by satsujinka on 2012-09-21
> **Some Penguin said:**
> It could also be restructured to be more easily generalized to different N.

pseudocode:
```

print_helper:  (string so far, # chars left)
  if # of chars left is less than 1, roll eyes and explode
  for (each possible char)
       compute string so far + that char
       if # of chars left is 1, just print that string, the 0h suffix, and a newline;
       else, recurse w/ print_helper (new buffer, # chars left - 1)

```to avoid massive allocation:  you can allocate a single buffer set up to hold n characters, pass along the index as well as an additional argument, and just change characters within that buffer.  Might as well pass the suffix as a parameter, too.

If you wanted to support massive N, enough to explode the call stack... you could do it with e.g. a bignum library, just converting each number to mod 26, just iterating over all possible values.  Or, painstakingly, do the math yourself and 'increment' the final character in the array, carrying over 'z' -> 'a' and incrementing the preceding column, if you wanted to do it w/o a bignum library.  Those aren't really simpler, but they generalize better than using N nested loops.

It's probably best to simulate a stack. Though wrapping 'z'->'a' sounds like it might be easiest (though I doubt it performs well.) Of course, if tail call elimination was optimized for we wouldn't even have to do that.

On a different note, for the varying N version storing everything in an array and outputting that array doesn't work well. This is because the array's memory size is  O(26^N) (for comparison's sake, N=3 takes up ~400kiB and at N=6 takes up ~2GiB.)

---

### Post by Tony Flury on 2012-09-21
you could also implement it as a single loop from 0 to 17576 - and then use mod and integer div operators to work out the character strings from aaa to zzz. No need to store anything


It would only be one loop - but it would be less easy to read i think - and possibly slower.

```

for (int i = 0 ; i <=17576 ; i++)
{
  char a,b,c;
  a = 'a' + i % 25;
  b = 'a' + (i / 26) % 25;
  c = 'a' + (i / (26 * 26) );
  printf("%c%c%c0h\n",c,b,a);
}

Not tested but it should work

```

---

### Post by GeneralZod on 2012-09-21
Needs some refinements, and prints them in a strange order, but here we go :)

```


#include <stdio.h>
#include <stdbool.h>

int main(void)
{
    char combination[] = "aaa";
    const int numberCharacters = sizeof(combination) - 1;
    
    bool foundAllCombinations = false;
    while (!foundAllCombinations)
    {
        int characterIndex = numberCharacters - 1;
        bool computedNextCombination = false;
        
        while (!computedNextCombination && !foundAllCombinations)
        {
            combination[characterIndex]++;
            if (combination[characterIndex] == 'z' + 1)
            {
                combination[characterIndex] = 'a';
                characterIndex--;
                if (characterIndex < 0)
                {
                    foundAllCombinations = true;
                }
            }
            else 
            {
                computedNextCombination = true;
            }
        }
        printf("%s\n", combination);
    }
        
   return 0;
}


```

---

### Post by satsujinka on 2012-09-21
Here's an arbitrary N implementation. main not included :)
```
static void perm(char* current, int depth) {
    if(depth < 1) {
        puts(current);
        return;
    }
    int len = strlen(current);
    char *temp = malloc((2+len)*sizeof(char));
    strncpy(temp, current, len);
    temp[len+1] = '\0';
    for(char a = 'a'; a <= 'z'; a++ ) {
        temp[len] = a;
        perm(temp, depth-1);
    }
    free(temp);
}
void print_perm(int depth) {
    if(depth < 1) return;
    perm("", depth);
}

```

EDIT: @Tony Flury
Slightly off, here's one that works correctly.
```
for (int i = 0 ; i < 17576 ; i++) {
    char a,b,c;
    a = 'a' + i % 26;
    b = 'a' + (i / 26) % 26;
    c = 'a' + (i / (26 * 26) );
    printf("%c%c%c0h\n",c,b,a);
}
```

---

### Post by ofnuts on 2012-09-22
> **dwhitney67 said:**
> Here's my version, which when measured with 'time', appears to outperform previous versions that have been posted.
```

#include <stdio.h>
#include <string.h>

int main(void) {
    char combo[17576 * 6 + 1];
    int i = 0;
    for(char a = 'a'; a <= 'z'; a++) {
        for(char b = 'a'; b <= 'z'; b++) {
            for(char c = 'a'; c <= 'z'; c++) {
                sprintf(combo + (6 * i++), "%c%c%c%s\n", a, b, c, "Oh");
            }
        }
    }
    printf("%s", combo);
    return 0;
}

```Note that output to the screen is awfully slow.  That's why the version above is slightly faster.

P.S.  About the "magic" numbers:  17576 = 26 * 26 * 26
Each combination consists of 6 characters (e.g. "abc0h\n").  An extra space is added for null-character at the end of the string.
It doesn't cost anything in execution time to use:
```

    char combo[26*26*26*6+ 1];

``` and it explains better how the size is computed.

Speaking of execution time, the main optimization is to remove the sprintf() call (10x improvement...)
```

    char combo[26*26*26*6+ 1];
    char *out=combo;
    for(char a = 'a'; a <= 'z'; a++) {
        for(char b = 'a'; b <= 'z'; b++) {
            for(char c = 'a'; c <= 'z'; c++) {
        *out++=a;
        *out++=b;
        *out++=c;
        *out++='0';
        *out++='h';
        *out++='\n';
            }
        }
    }
    *out++=0;
    printf("%s", combo);

```

---

### Post by conradin on 2012-09-23
Hey Thanks Everyone! 
I know the code is trivial but that's part of what I like about it. Seeing what other people would do is very interesting. I really enjoy this type of discussion. I am aware that I have some very slow coding styles. 
I liked satsujinka's code a lot for neatness, and steeldrivers {} placement is something I find to be very readable.


I think Ill leave this open a little while longer. :D

---

