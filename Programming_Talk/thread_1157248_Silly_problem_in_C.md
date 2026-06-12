---
title: "Silly problem in C"
date: 2009-05-12
forum: Programming Talk
---

### Post by loneowais on 2009-05-12
So here I am trying to print 1 for a, 2 for b, 3 for c etc...

here is the code


> #include<stdio.h>
#include<stdlib.h>

int main()
{
char a;

while(1)
{
fflush(stdin);
scanf("%c",&a);
fflush(stdin);
printf("%d\n",a-96);
}
return 0;
}

It works fine but prints 10 - 96 after every iteration.
I also tried flushing the input stream but no gain.

Actually it prints 10 but since I'm subtracting 96, it prints 10-96.

And the most important thing. This happens only when I put it inside a loop. Without a loop it works fine.

---

### Post by bigboy_pdb on 2009-05-12
I'm pretty certain that the 'a-96' isn't legitimate c.

You can convert a character to an integer (which is the character's ascii value). To do this use "(int)c".

Also, characters can be subtracted from one another (ie. 'a' - 'a' would be the 0th character).

I don't want to say more because I don't know if your a student working on an assignment or not. Besides, working with a programming language is the only way to get better at using it.

---

### Post by loneowais on 2009-05-12
I'm a student but this is not my assignment. My brother asked me to do it. 
I never take help on my assignments.

---

### Post by loneowais on 2009-05-12
*I've already tried type casting or whatever it is called but no help*

> **bigboy_pdb said:**
> I'm pretty certain that the 'a-96' isn't legitimate c.

You can convert a character to an integer (which is the character's ascii value). To do this use "(int)c".

Also, characters can be subtracted from one another (ie. 'a' - 'a' would be the 0th character).

I don't want to say more because I don't know if your a student working on an assignment or not. Besides, working with a programming language is the only way to get better at using it.

---

### Post by bigboy_pdb on 2009-05-12
Sorry, with respect to the a-96. I was thinking of the dash as being a dash and not a minus sign. Using that format converted the character for me.

Also, you should specify what isn't working or any error messages you're getting. It will help other people to help you.

When you're writing a program, it's important to test the individual program components.

What I mentioned will work.
```

char c = 'd'; // Change the letter to see the different values
              // (only works with lowercase characters)
printf("%i\n", (int)(c - 'a' + 1));

```

You can try that piece of code on its own. It should work (I've tested it).

You can use getchar and putchar to read/write characters.

I also [read that fflush can discard terminal input]("http://www.thinkage.ca/english/gcos/expl/c/lib/fflush.html").

---

### Post by loneowais on 2009-05-13
I've found a workaround,

here is the modified code

#include<stdio.h>

int main()
{
char a;

while(1)
{
scanf("%c",&a);

if(a!='\n')
printf("%d\n",a-96);

}
return 0;
}

The problem here is that 'return' ascii value 10 remains in the input
buffer stream. So in the next iteration the loop just skips scanf() as
it takes input from the stream.
So the user get to input again in the third iteration. Sound good at
the face of it but it doesn't work if I use fflush(stdin);
On Turbo C back in college I had similar issues with getche(); and
flushall(); did the trick there. But I can't seem to get rid of it in
GCC.

---

### Post by k2t0f12d on 2009-05-13
```

#include<stdio.h>
#include<stdlib.h>

int main()
{
char a;

while(1)
{
fflush(stdin);
scanf("%c",&a);
fflush(stdin);
[s]printf("%d\n",a-96);[/s]
a=a-96;
printf("%d\n",a);
}
return 0;
}

```

---

