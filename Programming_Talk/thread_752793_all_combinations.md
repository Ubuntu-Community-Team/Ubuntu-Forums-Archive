---
title: "all combinations"
date: 2008-04-12
forum: Programming Talk
---

### Post by slavik on 2008-04-12
just thought I'd post the most efficient way of getting all combinations of a set in C.

[SIZE="7"]notice the bit shifts[/SIZE]

[php]
/*
 *      combinations.c
 *      
 *      Copyright 2008 Vyacheslav Goltser <slavikg@gmail.com>
 *      
 *      This program is free software: you can redistribute it and/or modify
 *      it under the terms of the GNU General Public License as published by
 *      the Free Software Foundation, either version 3 of the License, or
 *      (at your option) any later version.
 *      
 *      This program is distributed in the hope that it will be useful,
 *      but WITHOUT ANY WARRANTY; without even the implied warranty of
 *      MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 *      GNU General Public License for more details.
 *      
 *      You should have received a copy of the GNU General Public License
 *      along with this program.  If not, see <http://www.gnu.org/licenses/>.
 *      
 */

#include <stdio.h>

#define ITEMS 5

unsigned long long int po2 (unsigned int p) {
	unsigned long long int ret = 1;
	while (p-- > 0) ret <<= 1;
	return ret;
}

int main(int argc, char** argv)
{
	int items[ITEMS] = {'A','B','C','D','E'};
	unsigned long long int max = po2(ITEMS) - 1;
	unsigned long long int counter = 0;
	unsigned long long int tmpcounter;
	unsigned long long int c;

	while (counter <= max) {
		tmpcounter = counter;
		c = 0;
		while (tmpcounter > 0) {
			// changed the if condition according to mike_g's suggestion, now there isn't a single mul/div instruction in the code
			if (tmpcounter & 1) { printf("%c,", items[c]); }
			tmpcounter >>= 1;
			c++;
		}
		counter++;
		printf("\b.\n");
	}
	return 0;
}
[/php]

---

### Post by keratos on 2008-04-12
Why?

---

### Post by slavik on 2008-04-12
> **keratos said:**
> Why?
why what?

---

### Post by keratos on 2008-04-14
why as in ... whats the point!

never mind.

---

### Post by mike_g on 2008-04-14
It would be even more efficient to do:
```
if(tmpcounter & 1)
     printf("%c", items[c]); 
```
Instead of:
```
if ((tmpcounter % 2) != 0) { printf("%c,", items[c]); } 
```

---

### Post by Lster on 2008-04-14
I hadn't seen this algorithm before - thanks. Is the algorithm well-known?

---

### Post by slavik on 2008-04-14
I think so, and mike_g, you are totally right (going to change it right now).

edit: it should be well known because one of my professors pushed me towards it, I am simply spreading knowledge here :)

edit2: the reason for bit shifts is to get a cheap multiplication/division by 2 (bit shift takes 1 clock cycle whereas using the multiplication/division circuits could be longer)
the reason mike_g's suggestion is nicer than modulo division is that bitwise and is also much faster than division (1 clock cycle, maybe 2) since we only care about the least significant bit (if it's set, the number is odd, if not, it is even).

---

### Post by Lster on 2008-04-14
[QUOTE=slavik]I think so, and mike_g, you are totally right (going to change it right now).

edit: it should be well known because one of my professors pushed me towards it, I am simply spreading knowledge here :)[/QUOTE]

I'm glad you did - algorithms interest me greatly (especially ones likes this), and although conceptually quite easy, I like the idea behind this. Thanks again. :)

---

### Post by slavik on 2008-04-14
this is why I am into parallel programming, you can write simple algorithms which can be 'embarrassingly parallel' (very easy to make parallel)

---

### Post by keratos on 2008-04-16
> **slavik said:**
> this is why I am into parallel programming, you can write simple algorithms which can be 'embarrassingly parallel' (very easy to make parallel)

parallel execution requires implementing hardware, i.e. transputers.

---

### Post by lnostdal on 2008-04-16
> **keratos said:**
> parallel execution requires implementing hardware, i.e. transputers.

this [http://paste.lisp.org/display/56483#1](http://paste.lisp.org/display/56483#1) looks pretty parallel to me .. running on my old standard boring laptop type hardware right here ...

---

### Post by slavik on 2008-04-16
> **keratos said:**
> parallel execution requires implementing hardware, i.e. transputers.
SMP will work, too ;)

---

### Post by keratos on 2008-04-18
> **lnostdal said:**
> this [http://paste.lisp.org/display/56483#1](http://paste.lisp.org/display/56483#1) looks pretty parallel to me .. running on my old standard boring laptop type hardware right here ...

oh dear, are you suggesting, really suggesting that a high level language with threading on a non supporting transputing platform is really parallel computing.

Oh dear me.

---

### Post by keratos on 2008-04-18
> **slavik said:**
> SMP will work, too ;)
concurr!

[http://en.wikipedia.org/wiki/Symmetric_multiprocessing](http://en.wikipedia.org/wiki/Symmetric_multiprocessing)

---

### Post by lnostdal on 2008-04-18
> **keratos said:**
> oh dear, are you suggesting, really suggesting that a high level language with threading on a non supporting transputing platform is really parallel computing.

Oh dear me.

here, need more beer?

edit:
this is why i hate people 99% of the time by the way .. not because they are wrong .. but because they are wrong _and_ stupid _and_ behave in a disgusting manner (about it) at the same time

i've found that i've got to assume that people will be wrong a lot of the time, and that most of them will be extremely stupid and disgusting about it .. so in "real life" i will sometimes have to prepare mentally, take a deep breath, then hold my tongue and knit my fists(#1) .. i do this _a lot_ to "fit in" with the rest of you assholes, but i'm just playing this game -- it isn't me .. life is grand, isn't it -- one disgusting insult and disappointment (mostly in you guys) after the other .. in short; get lost, you're not getting any information or answers from me -- my fists are tied and my tongue is too

#1: another option is to go in with all guns blazing .. this sometimes shuts people up, but i've found that it doesn't last long -- so why even bother .. you guys, or we, are screwed anyway

---

### Post by Wybiral on 2008-04-18
> **keratos said:**
> oh dear, are you suggesting, really suggesting that a high level language with threading ...

[quote=http://en.wikipedia.org/wiki/Parallel_computing]
Parallel computing is a form of computing in which many instructions are carried out simultaneously.
[/quote]

Yes, if you run it on multiple processors at once, it is.

---

### Post by keratos on 2008-04-19
> **lnostdal said:**
> here, need more beer?

edit:
this is why i hate people 99% of the time by the way .. not because they are wrong .. but because they are wrong _and_ stupid _and_ behave in a disgusting manner (about it) at the same time

i've found that i've got to assume that people will be wrong a lot of the time, and that most of them will be extremely stupid and disgusting about it .. so in "real life" i will sometimes have to prepare mentally, take a deep breath, then hold my tongue and knit my fists(#1) .. i do this _a lot_ to "fit in" with the rest of you assholes, but i'm just playing this game -- it isn't me .. life is grand, isn't it -- one disgusting insult and disappointment (mostly in you guys) after the other .. in short; get lost, you're not getting any information or answers from me -- my fists are tied and my tongue is too

#1: another option is to go in with all guns blazing .. this sometimes shuts people up, but i've found that it doesn't last long -- so why even bother .. you guys, or we, are screwed anyway

interesting, if a little weird - but that could be the language barrier - nevertheless, it doesnt change the fact that you are in error.

---

### Post by Wybiral on 2008-04-19
> **keratos said:**
> interesting, if a little weird - but that could be the language barrier - nevertheless, it doesnt change the fact that you are in error.

I think his point was just to show how easy threading is in Lisp... But, running on a multicore processor, the example he posted would be "parallel computing" by the very definition of the term. So, he may be drunk (which I'm 80% sure he is), but it's you, who is "in error".

I don't see what it being a high level language has anything to do with parallel computing. You also seem to think that threads don't count as parallel computing, so on the off-chance that you have no idea what threads are, let me inform you:

[quote=http://en.wikipedia.org/wiki/Parallel_computing]
Subtasks in a parallel program are often called threads. Some parallel computer architectures use smaller, lightweight versions of threads known as fibers, while others use bigger versions known as processes. However, "threads" is generally accepted as a generic term for subtasks.[/quote]

[quote=http://en.wikipedia.org/wiki/Thread_(computer_science)]
On a multiprocessor or multi-core system, threading can be achieved via multiprocessing, wherein different threads and processes can run literally simultaneously on different processors or cores.[/quote]

[quote=http://en.wikipedia.org/wiki/Parallel_computing]
Parallel computing is a form of computing in which many instructions are carried out simultaneously.
[/quote]

---

