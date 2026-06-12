---
title: "Swap function using pointers"
date: 2010-05-15
forum: Programming Talk
---

### Post by spaz886 on 2010-05-15
Hi people.

Need some help creating a function in C that swaps between the values of two variables.
The function should look like:
```
void swap( void* p, void* q, int n&#8236;&#8236;);
```for this code for example:
```
int main ()
{
    int a=1, b=4;
    double w=3.14, e=2.71;
    swap(&a, &b, sizeof(int));
    swap(&w, &e, sizeof(double));
    // This should print 4, 1, 2.71, 3.14 : 
    printf ("%d, %d, %lf, %lf\n", a, b, w, e);
    return 0;
}

```and this should be done WITHOUT using malloc()..

any ideas?
appreciate your help!

---

### Post by MadCow108 on 2010-05-15
no homework questions allowed here.
but a little hint, to swap arbitrary non aliasing data without temporary storage you can utilize a one of the basic binary logic functions.

---

### Post by Can+~ on 2010-05-15
Agreed, no homeworks here.

[COLOR="Silver"]But, I'll consider that you have reached a road-block that is familiar to all newbie C programmers.

Pointers are also "integers", and therefore, are also local to the scope of the function, even if passed as arguments, there's no magic to them. In other words, you need to "change the direction where the pointers points to", ergo, arguments should be void **p, void **q.[/COLOR]

Disregard that, I re-read and realized that you had a different problem.

---

### Post by lisati on 2010-05-16
> **MadCow108 said:**
> no homework questions allowed here.
but a little hint, to swap arbitrary non aliasing data without temporary storage you can utilize a one of the basic binary logic functions.

+1: We won't actually *do* the homework for you, but can give hints (such as the above one, which is good and easily overlooked if you're not expecting it) and guidance if you get stuck.

---

### Post by pokebirdd on 2010-05-16
> **MadCow108 said:**
> no homework questions allowed here.
but a little hint, to swap arbitrary non aliasing data without temporary storage you can utilize a one of the basic binary logic functions.

Can we also use that to swap structures? Or is that a type of aliasing data? Actually, what is aliasing data anyways? :confused:

---

### Post by MadCow108 on 2010-05-16
you can use it for structures but you need a loop over struct size/register size 

aliasing is when two pointers point to the same (or partly the same) memory location.
In that case the mentioned operation does not work anymore.

---

### Post by Serious George on 2010-05-16
[http://en.wikipedia.org/wiki/XOR_swap_algorithm](http://en.wikipedia.org/wiki/XOR_swap_algorithm) 
Take a read through that. Although for some reason, some people say it is just faster to create a temp variable and swap that way, i'm not sure why, maybe someone could explain this.

---

### Post by MadCow108 on 2010-05-16
its explained in the same article you quoted.

---

### Post by Serious George on 2010-05-16
> **MadCow108 said:**
> its explained in the same article you quoted.
Woops, missed that. Thanks for pointing it out.

---

### Post by trent.josephsen on 2010-05-16
I find it interesting that the restriction is "without using malloc", not "without using temporary storage".  It might be better to step through it one byte at a time and copy it via a temporary (but automatic) variable, which is easier to code and avoids using malloc.  In any case, you'll need to be doing operations on unsigned char, which is the only way to handle arbitrary memory data in a standards-compliant manner (and I think you're on shaky ground even then).

---

### Post by rnerwein on 2010-05-16
hi spaz886
hint for homework:

void foo(int *pi, int *px)
{

        *pi ^= *px;
        *px ^= *pi;
        *pi ^= *px;
}

ciao  :-)

---

