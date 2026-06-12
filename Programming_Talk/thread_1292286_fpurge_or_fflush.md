---
title: "fpurge or fflush?"
date: 2009-10-15
forum: Programming Talk
---

### Post by jessiebrownjr on 2009-10-15
Im playing with C for dummies and he gave me the two options... fpurge, or flush. He said that fpurge is required for unix/linux/mac.  I compiled my source at first with the fflush option as so..

It compile without error, but it didn't do what it was intended to do.  This code is for training only as you can see im sure hehe.. Now I have to questions.. why is fpurge (what he said i needed to use for Linux) not working, and what is (stdin)... is it part of stdio.h?

```
#include <stdio.h>
#include <stdlib.h>
int main()

{
char a,b;

printf("Enter a char!");
a=getchar();
fflush(stdin);
printf("Enter a nudder...");
b=getchar();


if(a > b)

{
    printf("'%c' is greater than '%c'",a,b);
}

else if (a < b)
{
    printf("'%c is less then '%c'",a,b);
}

else 
{
printf("Yo dog, same key brah.");
}

return(0);
}
```


This is the error I get when I try to use fpurge.
I have tried it as fpurge(); as well as fpurge(stdin); to no avail.
```
elmo@Elmo:~$ gcc char.c -o char
/tmp/ccgUyvdX.o: In function `main':
char.c:(.text+0x2c): undefined reference to `fpurge'
collect2: ld returned 1 exit status
```

---

### Post by MadCow108 on 2009-10-15
don't flush stdin! flush on an input stream is not defined in standard C
[http://www.cprogramming.com/faq/cgi-bin/smartfaq.cgi?id=1043284351&answer=1052863818](http://www.cprogramming.com/faq/cgi-bin/smartfaq.cgi?id=1043284351&answer=1052863818)

fpurge is so far I know a BSD function and does not exist in GNU/Linuxx. But I may be wrong.

Your book seems very outdated. Consider using a newer one.

---

### Post by jessiebrownjr on 2009-10-15
> **MadCow108 said:**
> don't flush stdin! flush on an input stream is not defined in standard C
[http://www.cprogramming.com/faq/cgi-bin/smartfaq.cgi?id=1043284351&answer=1052863818](http://www.cprogramming.com/faq/cgi-bin/smartfaq.cgi?id=1043284351&answer=1052863818)

fpurge is so far I know a BSD function and does not exist in GNU/Linuxx. But I may be wrong.

Your book seems very outdated. Consider using a newer one.

Yeah im using C for dummies to start, its very limited I can tell, im 1/2 way through it and barely into if/else statements.

Ok ill ask you this then, the program right there is I guess an attempt to teach me how to make a single char menu system basically.. If you do it without that, the only way to get the program to work properly is after the first character you input, you hit ctrl+D instead of hitting enter.. if you hit enter, it puts that as a single character as well and inputs it into the second getchar. Whats the way around that?

Thanks!

Edit. I read that site you gave me, I'm guessing that code is a bit higher level then what I have learned so far and maybe I should just keep reading my terrible book :-)

---

### Post by dwhitney67 on 2009-10-15
Use scanf() in lieu of the getchar().

```

#include <stdio.h>

int main()
{
  char ch1;
  char ch2;

  printf("Input one character: ");
  scanf("%c%*c", &ch1);

  printf("Input another character: ");
  scanf("%c%*c", &ch2);

  printf("\n\nYou entered a %c and a %c.\n", ch1, ch2);
  return 0;
}

```

---

### Post by MadCow108 on 2009-10-15
Not sure if there is a better way in C but this would work inserted after a getchar:
```

while (1) {
	char c = getchar();
	if (c == '\n' || c == EOF)
		break;
}

```

---

### Post by jessiebrownjr on 2009-10-15
> **dwhitney67 said:**
> Use scanf() in lieu of the getchar().

```

#include <stdio.h>

int main()
{
  char ch1;
  char ch2;

  printf("Input one character: ");
  scanf("%c%*c", &ch1);

  printf("Input another character: ");
  scanf("%c%*c", &ch2);

  printf("\n\nYou entered a %c and a %c.\n", ch1, ch2);
  return 0;
}

```

Can this be used to compare the two inputs via if statements? I haven't read a reason to not use scanf,gets(i know gets is bad i dont know how to use fgets yet) or getchar etc.

---

### Post by dwhitney67 on 2009-10-15
Your app is reading single characters; getchar(), fgetc(), or even scanf() are fine for this.  I chose scanf() so that it would gobble, and ignore, any number of characters on the input stream following the first character (ie the one I'm interested in).

Use fgets(), and no other function, when attempting to read a string from the input stream.  It is considered safer to use because it allows the programmer to guard against buffer overruns when accepting data from an malicious user.

P.S.  In the example I provided, there is nothing to prevent you from comparing ch1 and ch2.  Think of these as char values, or signed 8-bit integers.  Up 2 you.

---

### Post by jessiebrownjr on 2009-10-15
> **dwhitney67 said:**
> Use scanf() in lieu of the getchar().

```

#include <stdio.h>

int main()
{
  char ch1;
  char ch2;

  printf("Input one character: ");
  scanf("%c%*c", &ch1);

  printf("Input another character: ");
  scanf("%c%*c", &ch2);

  printf("\n\nYou entered a %c and a %c.\n", ch1, ch2);
  return 0;
}

```

Ok I hate to ask this but it seems I forgot... I see you put &ch1 there, what is the difference between that and me typing ("%c",ch1) ? I remember seeing that character symbol used but forgot WHAT it was used for, and also, why does your code have all the extra stuff besides just "%c" ? Thanks :-)

---

### Post by jessiebrownjr on 2009-10-15
```
#include <stdio.h>

int main()

{

char nam;

printf("What is your name?");
scanf("%c",&nam);
printf("You entered %c",nam);

return (0);
}
```I feel like I forget everything I have read... I tried this to test out, it works.. only puts the first character of whatever I enter, now if I try to change %c %s it doesn't work.. Sighhhhh :-)

I changed it to a string instead of just a single char... THIS following code works right.

#include <stdio.h>

int main()

{

char nam[10];

printf("What is your name?");
scanf("%s",nam);
printf("You entered %s",nam);

return (0);
}

now if I change it to scanf.....&nam, it compiles, still works, but gives me an error.. is this only for assigning single chars?

---

### Post by dwhitney67 on 2009-10-15
> **jessiebrownjr said:**
> Ok I hate to ask this but it seems I forgot... I see you put &ch1 there, what is the difference between that and me typing ("%c",ch1) ? I remember seeing that character symbol used but forgot WHAT it was used for, and also, why does your code have all the extra stuff besides just "%c" ? Thanks :-)
Copy the code I presented, and test it with different permutations.  See which meets your requirements.

I wager that if you take out the "%*c" from the scanf() format statement, you will be no better off than if you had used getchar() to read the user's input.

---

### Post by jessiebrownjr on 2009-10-15
> **dwhitney67 said:**
> Copy the code I presented, and test it with different permutations.  See which meets your requirements.

I wager that if you take out the "%*c" from the scanf() format statement, you will be no better off than if you had used getchar() to read the user's input.


Not being a jokerster here because I'm still learning but I think I did that up there without the %*c, look up a post or two and see if thats the same thing.  What does %*c do? I'm trying to iron out this blasted books bad teaching.. the smug little *()^#$ keeps telling me to refer to his 2nd all in one reference book...

---

### Post by dwhitney67 on 2009-10-15
> **jessiebrownjr said:**
> ...
now if I change it to scanf.....&nam, it compiles, still works, but gives me an error.. is this only for assigning single chars?

It is for specifying the address of the variable where you want to store data.  When you are using an array (of chars), you do not need to specify the address since the address is implied.

These are equivalent:
```

scanf("%s", nam);

scanf("%s", &nam[0]);

```

Nevertheless, as I stated earlier, one should NEVER use scanf() to read a string; fgets() is the best/better option.

---

### Post by jessiebrownjr on 2009-10-15
> **dwhitney67 said:**
> ]Nevertheless, as I stated earlier, one should NEVER use scanf() to read a string; fgets() is the best/better option.

Ok, I think this right here will be very helpfup to know, mr dan gookin hasn't said that yet.. lol.

I find it annoying how he tells me how to do a program, i type it compile it.. but it errors out... instead of keeping on reading, i try to debug the program, only to give up, read further, and hes like "LOL GOT YA"....

---

### Post by dwhitney67 on 2009-10-15
> **jessiebrownjr said:**
> Not being a jokerster here because I'm still learning but I think I did that up there without the %*c, look up a post or two and see if thats the same thing.  What does %*c do? I'm trying to iron out this blasted books bad teaching.. the smug little *()^#$ keeps telling me to refer to his 2nd all in one reference book...

I'm a competent s/w developer, and I admit, many times I gloss over the details of a language.  So forgive me if what I state here is incorrect or incomplete...

The "%*c", as I understand it, instructs scanf() to gobble all remaining characters in the input stream until an EOF or newline is reached.  If I had specified the number 5 in lieu of '*', then only up to 5 characters would have been read.

I hope this meager information provides you with enlightenment.

---

### Post by jessiebrownjr on 2009-10-15
> **dwhitney67 said:**
> I'm a competent s/w developer, and I admit, many times I gloss over the details of a language.  So forgive me if what I state here is incorrect or incomplete...

The "%*c", as I understand it, instructs scanf() to gobble all remaining characters in the input stream until an EOF or newline is reached.  If I had specified the number 5 in lieu of '*', then only up to 5 characters would have been read.

I hope this meager information provides you with enlightenment.
indeed, ill play with this knowledge later and try to start teaching myself :-) thanks!

---

