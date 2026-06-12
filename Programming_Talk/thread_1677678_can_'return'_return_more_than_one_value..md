---
title: "can 'return' return more than one value."
date: 2011-01-29
forum: Programming Talk
---

### Post by c2tarun on 2011-01-29
I found this program while reading a book.
Till now I knew that return statement can return only one value.
```

#include<stdio.h>

int addmult(int,int);
int main()
{
   int i=3,j=4,k,l;
   k=addmult(i,j);
   l=addmult(i,j);
   printf("%d %d\n",k,l);
   return 0;
}

int addmult(int ii,int jj)
{
   int kk,ll;
   kk=ii+jj;
   ll=ii*jj;
   return(kk,ll);
}

```

I executed the code and found the output is 12,12.
Guys this is not my homework, I just want to clear my concepts.
Can anyone please explain.

---

### Post by worksofcraft on 2011-01-29
> **c2tarun said:**
> I found this program while reading a book.
Till now I knew that return statement can return only one value.
```

#include<stdio.h>

int addmult(int,int);
int main()
{
   int i=3,j=4,k,l;
   k=addmult(i,j);
   l=addmult(i,j);
   printf("%d %d\n",k,l);
   return 0;
}

int addmult(int ii,int jj)
{
   int kk,ll;
   kk=ii+jj;
   ll=ii*jj;
   return(kk,ll);
}

```

I executed the code and found the output is 12,12.
Guys this is not my homework, I just want to clear my concepts.
Can anyone please explain.

This time you really have me stumped :shock:
AFIK the comma operator just takes the result of the last expression. OTOH return only returns one thing... so I will be eagerly reading any other replies here and I'll probably learn something else I never knew :)

---

### Post by lisati on 2011-01-29
> **worksofcraft said:**
> OTOH return only returns one thing... so I will be eagerly reading any other replies here and I'll probably learn something else I never knew :)
That's what I thought too, that return normally returns one item. Unless I'm missing something here and there's some kind of structure thingummy going on that I haven't spotted.

---

### Post by nvteighen on 2011-01-29
> **c2tarun said:**
> I found this program while reading a book.
Till now I knew that return statement can return only one value.
```

#include<stdio.h>

int addmult(int,int);
int main()
{
   int i=3,j=4,k,l;
   k=addmult(i,j);
   l=addmult(i,j);
   printf("%d %d\n",k,l);
   return 0;
}

int addmult(int ii,int jj)
{
   int kk,ll;
   kk=ii+jj;
   ll=ii*jj;
   return(kk,ll);
}

```

I executed the code and found the output is 12,12.
Guys this is not my homework, I just want to clear my concepts.
Can anyone please explain.

And it only returns one. It just returns ll, but you see it twice because addmult is called twice. 

Look at what gcc says when compiling with all warnings on:
```

ugi@UGI:~/Escritorio$ gcc -o z z.c -Wall -Wextra -pedantic
z.c: In function ‘addmult’:
z.c:18: warning: left-hand operand of comma expression has no effect
ugi@UGI:~/Escritorio$ ./z
12 12

```

That warning means that what's on th left-hand of the comma is simply ignored (in this case, kk).

If you want to return two values, what you have to do in C is to return a data structure that wraps that data into one single "object".

Hope this helps.

---

### Post by Rany Albeg on 2011-01-29
The answer is simple.
You are using the comma operator which evaluates its first operand and discard result, then evaluate the second one and returns.

Normally the comma sign acts as a separator like in functions and variable declarations so its a bit confusing.

For example in your code 

```
return (kk+1,ll);
```

will increase kk by one and return ll.
Of course that it is useless since kk is local, but still you can think of using pointers to change something and return a value.

You'll see it more in for loops where you want to set a variable in each iteration, like:
```
for(somehting;something;foo++,bar++)
```


Have a nice day ;)

---

### Post by The Cog on 2011-01-29
Oops. Posted a load of bunkum.

---

### Post by Praveen30 on 2011-01-29
> **c2tarun said:**
> I found this program while reading a book.
Till now I knew that return statement can return only one value.
```

#include<stdio.h>

int addmult(int,int);
int main()
{
   int i=3,j=4,k,l;
   k=addmult(i,j);
   l=addmult(i,j);
   printf("%d %d\n",k,l);
   return 0;
}

int addmult(int ii,int jj)
{
   int kk,ll;
   kk=ii+jj;
   ll=ii*jj;
   return(kk,ll);
}

```I executed the code and found the output is 12,12.
Guys this is not my homework, I just want to clear my concepts.
Can anyone please explain.

[nvteighen]("http://ubuntuforums.org/member.php?u=273037") is right . I have already done this question and i got the same explanation from the indiabix site...(u know from which section)

---

### Post by c2tarun on 2011-01-29
> **Praveen30 said:**
> [nvteighen]("http://ubuntuforums.org/member.php?u=273037") is right . I have already done this question and i got the same explanation from the indiabix site...(u know from which section)

I got this question from a book not any website. 
anyway thanks to everyone who replied, thanks a lot :D

---

### Post by Rany Albeg on 2011-01-29
You welocme.
Please mark this thread as solved.

---

### Post by c2tarun on 2011-01-29
> **Rany Albeg said:**
> You welocme.
Please mark this thread as solved.
Done :)

---

### Post by unknownPoster on 2011-01-29
Just as an fyi/addition, some programming languages such as Python support multiple return values.

---

