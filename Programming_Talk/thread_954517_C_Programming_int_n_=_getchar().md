---
title: "C Programming: int n = getchar()"
date: 2008-10-21
forum: Programming Talk
---

### Post by nathanqh on 2008-10-21
I apologize if this is really really simple, but I was just wondering how I can use getchar() to get an integer value, and then use that as an integer, not a char.  This is what I wrote so far, but it's printing numbers completely different than what I input.  Is it giving me the memory address or something like that instead?
```
#include <stdio.h>

#include <stdlib.h>

int main () {
	int n;
	n = getchar();
	printf("%d\n", n);
	n += n+5;
	printf("%d\n", n);

	return EXIT_SUCCESS;
}
```

Thanks!!

---

### Post by slavik on 2008-10-21
you can't, getchar() returns a char or -1 on EOF.

if you want to read a number, read about scanf.

---

### Post by mike_g on 2008-10-21
You could do:
```
int n = getchar() - '0';
```
but this would work for getting a number from 0-9. You would be better off with scanf, or alternatively using fgets with strtol.

---

### Post by nathanqh on 2008-10-21
hmmm, ok

the reason i was trying to use getchar() is because i wanted to use ungetc(n, stdin) right after...is there such thing as a similar function that can be used with scanf()?

---

### Post by Canis familiaris on 2008-10-21
> **nathanqh said:**
> I apologize if this is really really simple, but I was just wondering how I can use getchar() to get an integer value, and then use that as an integer, not a char.  This is what I wrote so far, but it's printing numbers completely different than what I input.  Is it giving me the memory address or something like that instead?
```
#include <stdio.h>

#include <stdlib.h>

int main () {
	int n;
	n = getchar();
	printf("%d\n", n);
	n += n+5;
	printf("%d\n", n);

	return EXIT_SUCCESS;
}
```

Thanks!!
It is giving the ASCII of the first "number" or rather character you are intending to type.
For example if you type '8' it will output the ASCII value of 8 (if you print the char as number that is)

---

### Post by blackmail on 2008-10-21
#include <stdio.h>

#include <stdlib.h>

int main () {
	int n;
	scanf("%d", &n);
        printf("%d\n", n);
	n += n+5;  /*if this line should do n=n+5 then you can write n += 5*/
	printf("%d\n", n);

	return EXIT_SUCCESS;
}

---

### Post by blackmail on 2008-10-21
getchar is for chars and not for numbers, i mean use the thing for what they are intended for... :D

---

### Post by Majorix on 2008-10-21
You might want to convert your char to int:
[php]char c = getchar();
int n = atoi(c);
//do something with n[/php]

---

### Post by kknd on 2008-10-21
> **nathanqh said:**
> hmmm, ok

the reason i was trying to use getchar() is because i wanted to use ungetc(n, stdin) right after...is there such thing as a similar function that can be used with scanf()?

No (only ungetc for chars and ungetwc for wide chars).

If you want to read a bigger number like 523 with getchar, you can do something like this:

[PHP]
int acc = 0, buf;

while( (buf = getchar()) != EOF )
     acc = acc * 10 + buf - '0';


printf("Read %d\n", acc);
[/PHP]

---

### Post by lswb on 2008-10-21
Can't you just cast it to an int?

int n;

n=(int)getchar();

Also, this line is asking for trouble:

n += n+5;

It probably won't even compile unless you turn off warnings & errors.

---

### Post by estyles on 2008-10-21
> **lswb said:**
> 
Also, this line is asking for trouble:

n += n+5;

It probably won't even compile unless you turn off warnings & errors.

It seems like a perfectly valid statement that just happens to do something completely different from what the coder probably intended.  I believe that the new value of n will end up being equal to 2n+5.

---

### Post by Majorix on 2008-10-21
> **estyles said:**
> It seems like a perfectly valid statement that just happens to do something completely different from what the coder probably intended.  I believe that the new value of n will end up being equal to 2n+5.

That's correct, that statement won't cause any errors/warnings.

But yeah, I believe there is a logic error in that. The OP might have meant "n += 5" or "n = n+5" (both of which do the same of course).

@lswb:
If you look at my post above yours, you would have noticed I already suggested a conversion :)

---

### Post by lswb on 2008-10-21
> **Majorix said:**
> That's correct, that statement won't cause any errors/warnings.

But yeah, I believe there is a logic error in that. The OP might have meant "n += 5" or "n = n+5" (both of which do the same of course).

@lswb:
If you look at my post above yours, you would have noticed I already suggested a conversion :)

Yes, I see you are right about the n+=n+5 statement, it just _looks_ confusing. 

Doesn't atoi take a char *, not a char ?

---

### Post by boz on 2008-10-22
> **lswb said:**
> Can't you just cast it to an int?

int n;

n=(int)getchar();


The characters '0' through '9' are are ASCII 30h (48) through 39h (57).  Therefore, if you really want to use getchar(), you'd have to do something like this:

```

int n = (int)getchar();
if (n < 0x30 || n > 0x39)
{
    n = -1;
}
else
{
    n -= 0x30;
    // You can alternatively do n -= 48 if you're not comfortable with hex
}

```

---

### Post by lswb on 2008-10-22
I thought the OP just wanted to do something with the actual integer value of the character, not the value that the character is used to represent. Now I'm not sure what he wanted!

---

### Post by dribeas on 2008-10-22
> **lswb said:**
> Also, this line is asking for trouble:

n += n+5;

It probably won't even compile unless you turn off warnings & errors.

> **estyles said:**
> It seems like a perfectly valid statement that just happens to do something completely different from what the coder probably intended.  I believe that the new value of n will end up being equal to 2n+5.

I cannot check against the C standard, but the C++ is quite clear to that point:

> 
Section 5 - Expressions, paragraph 4
Except where noted, the order of evaluation of operands of individual operators and subexpressions of individual expressions, and the order in which side effects take place, is unspecified. Between the previous and next sequence point a scalar object shall have its stored value modified at most once by the evaluation of an expressions. [...] [Example:
```

i = v[ i++ ]; // the behavior is unspecified
i = ++i + 1; // the behavior is unspecified

```
]


Your code should not do it, and if you do it the compiler has the right (maybe even the obligation) of complaint through a warning.

---

### Post by estyles on 2008-10-22
> **dribeas said:**
> I cannot check against the C standard, but the C++ is quite clear to that point:
```

Section 5 - Expressions, paragraph 4
Except where noted, the order of evaluation of operands of individual operators and subexpressions of individual expressions, and the order in which side effects take place, is unspecified. Between the previous and next sequence point a scalar object shall have its stored value modified at most once by the evaluation of an expressions. [...] [Example:
Code:

i = v[ i++ ]; // the behavior is unspecified
i = ++i + 1; // the behavior is unspecified

] 
```

Your code should not do it, and if you do it the compiler has the right (maybe even the obligation) of complaint through a warning.

I won't argue that your code shouldn't do it.  Even if it's valid c code, it's confusing and silly.  It's unlikely to do what you intended and if you intended to set n = 2n + 5, then why write it all confusing-style?

I don't think it's a warnable offense, though.  I may be wrong, and if so, please feel free to correct me, but n += n+5 doesn't change the value of n more than once, nor does it rely on order of operations, except for the fact that the right side is evaluated before assigning it to the variable.  n += n+5 should expand to n = n+n+5, which is perfectly valid, or just be interpreted as "add n n+5; mov ax n" (excuse my ASM, rusty is too kind a word, so the syntax may be wrong, but you get what I'm saying).  You're not using an increment or decrement operator, so order of operations shouldn't factor into it.  Am I wrong?

---

### Post by loneowais on 2008-10-24
> **Anurag_panda said:**
> It is giving the ASCII of the first "number" or rather character you are intending to type.
For example if you type '8' it will output the ASCII value of 8 (if you print the char as number that is)

Char means just a Shape...Characters are just like Smilies. Each smiley has it's own unique identification number. It varies between implementations, the most commonly used system is ASCII.

Whenever we input a character to the computer, it is stored as a number, a number which is unique to the character(see ASCII table).

0-9 are digits & also chars()
ASCII codes for char 0-9 are

48='0'
49='1'
50='2'
.
.
.
.
.
.
57='9'


So even if you enter a valid integer in the program, getchar() will take it as the character(smiley) & forward it's ASCII value to an integer variable.


An Example

int an=2,bn=2,cn;
char ac='2',bc='2;

cn=an+bn;// as an &  bn are int, an+bn==2
printf("%d\n",cn);


cn=ac+bc;
printf("%d\n",cn);//as ac & bc are char and ASCII value of '2' is 50, ac+bc=100..%d will print 50

printf("%c\n",cn);//as ac & bc are char and ASCII value of '2' is 50, ac+bc=100..%c will print the smiley represented by number in cn, i.e, d



Oputput will be
4
100
d

---

### Post by dribeas on 2008-10-24
> **estyles said:**
> I don't think it's a warnable offense, though.  [...] n += n+5 doesn't change the value of n more than once

Completely right, my bad. That is what I get from reading too fast :) To clear things up the code above has not problems whatsoever. The problem would be with code like 'n = n++ +5' where n is meant to be changed twice.

My apologies

---

### Post by estyles on 2008-10-24
> **dribeas said:**
> Completely right, my bad. That is what I get from reading too fast :) To clear things up the code above has not problems whatsoever. The problem would be with code like 'n = n++ +5' where n is meant to be changed twice.

My apologies

You mean I'm right for once?  Hooray!  :guitar:

---

### Post by blackmail on 2009-04-30
Yes sorry, i was a bit sleepy writing, in the comment i wrote it ok, but in the actual code it was messed up, i am just human (that's why i use ubuntu )

---

### Post by blackmail on 2009-04-30
and i don't see any way why it should give error or warnings, it is just an addition, so if my small C knowledge dosen't make me look stupid, it is an ok code!

---

### Post by Krupski on 2009-04-30
> **nathanqh said:**
> I apologize if this is really really simple, but I was just wondering how I can use getchar() to get an integer value, and then use that as an integer, not a char.  This is what I wrote so far, but it's printing numbers completely different than what I input.  Is it giving me the memory address or something like that instead?
```
#include <stdio.h>

#include <stdlib.h>

int main () {
	int n;
	n = getchar();
	printf("%d\n", n);
	n += n+5;
	printf("%d\n", n);

	return EXIT_SUCCESS;
}
```

Thanks!!

Try this:

[PHP]
#include <stdio.h>
#include <math.h>

int readint(FILE*); // prototype

int main(void)
{
    int number; // declare variable

    printf("Enter a number: "); // prompt
    number = readint(stdin); // get integer number from console (stdin)
    printf("You entered %d\n", number); // display it

    return 0;
}

int readint(FILE *fp)
{
    char buf[256];
    int inum;
    double dnum;

    buf[0] = 0;
    fgets(buf, 256, fp); // read from "fp"

    dnum = atof(buf); // get floating point version of number
    inum = (int)(dnum < 0 ? dnum - 0.5 : dnum + 0.5); // do symmetric round

    return inum; // return rounded integer to caller
}
[/PHP]

Note... the funky line "inum = (int)(dnum < 0 ? dnum - 0.5 : dnum + 0.5);" does a symmetric rounding of the number. For example, if you enter "123.5", you will get 124. If you enter "-123.5", you get "-124".

If you don't need rounding, then just do away with the "dnum" variable and use "atoi" to get the number into "inum".

Hope this helps!

-- Roger

---

### Post by dwhitney67 on 2009-04-30
getchar() returns the ASCII value (in integer format) for a _single_ character.

If you examine the ASCII table, the character '0' is 0x30, '1' is a 0x31, etc.

To get the integer value of a numeral character that is read by getchar():
```

#include <stdio.h>

int main()
{
  int num = getchar() - 0x30;

  printf("num = %d\n", num);
}

```

---

### Post by dwhitney67 on 2009-04-30
> **blackmail said:**
> Yes sorry, i was a bit sleepy writing, in the comment i wrote it ok, but in the actual code it was messed up, i am just human (that's why i use ubuntu )

You opened a 6-month old thread.... for what purpose?????????

---

