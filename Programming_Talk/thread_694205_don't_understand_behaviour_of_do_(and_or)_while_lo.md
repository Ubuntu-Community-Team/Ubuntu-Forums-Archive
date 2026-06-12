---
title: "don't understand behaviour of do (and or) while loop + redirecting text file?"
date: 2008-02-11
forum: Programming Talk
---

### Post by S15_88 on 2008-02-11
ok so i'm trying to write a program that instead of taking input from stdin it takes a text file and reads it in word by word as stdin.

this is what i've got:
```


char *string;
int words;

string = malloc(sizeof(char)*200);

while(string != EOF)
{       
    fscanf(stdin, "%s", string);
    words++; 
}
printf("%d\n", words);

```

then compile with:
```

gcc fun.c < testfile.txt -ansi -Wall -o tester

```

What I want to accomplish is read in a file word by word from a file as stdin then print them out one by one and count the words up then print the total amount of words.

my guess is that it's with the while loop condition: (string != EOF) 
as i'm getting a warning: comparison between pointer and integer

all warnings aside when i run it it doesn't take the textfile, it sits there waiting for input on command line.  if you type stuff it works fine but doesn't exit the loop! ie. prints out each word you typed on a new line.

if someone could clarify what is going on it would be greatly appreciated.

Thanks, Alain

---

### Post by lloyd_b on 2008-02-11
1.  "string" is NEVER going to equal EOF.  "string" contains a pointer to the memory you're allocating (an address such as 0x4000000).  It is NOT affected in ANY way by the fscanf function.  The values in memory that is being pointed to is changed, but the pointer itself isn't affected.

Resolution (and a little better coding style):
```
while (fscanf(stdin, "%s", string) != EOF)
     words++;
```

2. I have no clue what the "< testfile.txt" is doing in your compile command.  The redirection should be done when you execute the compiled program:
```
gcc -ansi -Wall -o tester fun.c
./tester < testfile.txt
```

Lloyd B.

Edit: Forgot something - you need to initialize "words" to zero somewhere.  By default, gcc does NOT do this for you, so if you run without initializing it, you get some random value (whatever happened to be in that chunk of memory before).
```
int words = 0;
```
will take care of it.

---

### Post by S15_88 on 2008-02-11
thanks alot you've cleared things up for me and i thank you for taking the time to explain to me why things weren't working as opposed to just fixing it, in your three quick explanations i've realized alot haha i just wasn't thinking hard enough into it.  i'm still new to C programming and i thank you for explaining things!

thanks, Alain

---

