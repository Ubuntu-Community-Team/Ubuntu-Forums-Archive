---
title: "Every combination of letters"
date: 2009-12-20
forum: Programming Talk
---

### Post by bamsanks on 2009-12-20
Hi peeps.
I have been trying to write a function to output every combination of a string but can't seem to get my head round the logic of it.
For example, if I input the word "ABC", the output should look like:
ABC
ACB
BAC
BCA
CAB
CBA
I've looked around for functions to take or translate into c, but can't find the right one.
I know that I have to use recursion but that's all I seem to know.
If anyone can help, it would be greatly appreciated.
Sam.

---

### Post by grayrainbow on 2009-12-20
Try searching for permutations.

---

### Post by CptPicard on 2009-12-20
What you are looking to produce are more properly called "permutations" of the string. Here's a discussion from Google...

[http://bytes.com/topic/c/answers/514194-print-all-permutations-string](http://bytes.com/topic/c/answers/514194-print-all-permutations-string)

EDIT:

```

#include <stdio.h>


void swap(char *a, char *b) {
  char tmp = *a;
  *a = *b;
  *b = tmp;
}

void permutations(char *str, int i, int n) {

  int j;
  
  if (i >= n)
    printf("%s\n",str);
  else {
    
    permutations(str, i+1, n);
    
    for (j = i+1; j < n; j++) {
      swap(&str[i], &str[j]);
      permutations(str, i+1, n);
      swap(&str[i], &str[j]);
    }
    
  }
  
}


int main(int argc, char **argv) {

  char foo[] = "ABC";
  
  permutations(foo, 0, 3);
  
}
```

---

### Post by Can+~ on 2009-12-20
[PHP]#!/usr/bin/env python

from itertools import permutations

for perm in permutations("ABC", 3):
	print perm[/PHP]

Output: 
```
('A', 'B', 'C')
('A', 'C', 'B')
('B', 'A', 'C')
('B', 'C', 'A')
('C', 'A', 'B')
('C', 'B', 'A')
```

edit: whoops, I just read the "C" part.

---

### Post by grayrainbow on 2009-12-20
> **Can+~ said:**
> [PHP]#!/usr/bin/env python

from itertools import permutations

for perm in permutations("ABC", 3):
	print perm[/PHP]

Output: 
```
('A', 'B', 'C')
('A', 'C', 'B')
('B', 'A', 'C')
('B', 'C', 'A')
('C', 'A', 'B')
('C', 'B', 'A')
```

edit: whoops, I just read the "C" part.
That's exactly why I'm on opinion that python can not teach you anything except importing and calling cod written by somebody else, which is not bad for automation stuff btw.

---

### Post by Barriehie on 2009-12-20
In regards to the logic think of it as the input string becomes an array, or a list.  For each position in the string length you've got to cycle through all elements in the list; i.e. input string is 'ABC' so:

A A **A**
A A **B**
A A **C**
A B A
A B B
A B C
B A A
...

There are, as indicated prior, functions to do this but those don't help to understand what's happening.  I use a method like this to generate random filenames where my 'list' is upper and lower case letters and the numbers 0 - 9.  For a 20 character filename I end up with:
62^20 = 704,423,425,546,998,022,968,330,264,616,370,176 combinations.  I don't know what that number is but I've yet to generate a duplicate name! :)

HTH
Barrie

---

### Post by Can+~ on 2009-12-20
> **grayrainbow said:**
> That's exactly why I'm on opinion that python can not teach you anything except importing and calling cod written by somebody else

Let me tell you something. I'm a teacher's assistant, in charge of creating homeworks for the students, I have to correct around 60 projects each time. The course: Data Structures and Algorithms.

My teachers think that homeworks should be done in C, and I'm ok with that. I correct homeworks, and slowly realize, that even though we ask tasks that require creating and specifying the data structures and algorithms (without any external library) and then achieving something with that, in the end of the day, you realize that they just replicated the exact algorithm from wikipedia, changed things for pointers when it's due and that's it.

Even a task about compressing a file using a Huffman's Tree formation algorithm is easy. Where do they fail mostly? When doing the importing/parsing of the files, ironically, the algorithm is just about moving pseudocode to code, and it's the easiest part. They failed mostly on parsing the end result.

There isn't anything particularly attractive about it. If you care about learning how things work, you study the algorithm, not the implementation. Python won't teach you algorithms, nor will C, it's the desire of learning that pushes you to learn how things actually work, pointers? mallocs? Those are implementation details.

But I agree with you in a certain aspect, that having to actually write the algorithm, is a good enough excuse to learn it, you don't do that with python or any other pre-baked algorithms, because you're probably too lazy and just call it done.

That's why I recommend people interested in actual programming, to go learn higher level, and buy a book relating to algorithms for the details, those details that are implementation-dependant. (btw, I just bought [Algorithm Design by Éva Tardos and Jon Kleinberg]("http://www.amazon.com/Algorithm-Design-Jon-Kleinberg/dp/0321295358"), great book).

---

### Post by LKjell on 2009-12-20
When you copy and paste from pseudo code to C code is a way to study.
But whether you understand the algorithm is a different part. And even if you understand how an algorithm works it is not the same as know how to implement it and write it in C code. Well look at the heapsort code below which is taken from the Linux kernel source and pseudo code from wikipeadia [http://en.wikipedia.org/wiki/Heapsort#Pseudocode](http://en.wikipedia.org/wiki/Heapsort#Pseudocode)

```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <time.h>

static void swap(void *a, void *b, size_t size)
{
	char t;

	do {
		t = *(char *)a;
		*(char *)a++ = *(char *)b;
		*(char *)b++ = t;
	} while (--size > 0);
}

int cmp_int(const void *a, const void *b)
{
	if(*(int *)a >= *(int *)b)
		return 0;
	else
		return -1;
}

/*
 * sort - sort an array of elements
 * @base: pointer to data to sort
 * @num: number of elements
 * @size: size of each element
 * @cmp_func: pointer to comparison function
 * @swap_func: pointer to swap function or NULL
 */
 
void sort(void *base, size_t num, size_t size, 
		int (*cmp_func)(const void *, const void *),
		void (*swap_func)(void *, void *, size_t size))
{
	/* pre-scale counters for performance */
	int i = (num/2 - 1) * size, n = num * size, c, r;

	/* heapify */
	for ( ; i >= 0; i -= size) {
		for (r = i; r * 2 + size < n; r  = c) {
			c = r * 2 + size;
			if (c < n - size &&
					cmp_func(base + c, base + c + size) < 0)
				c += size;
			if (cmp_func(base + r, base + c) >= 0)
				break;
			swap_func(base + r, base + c, size);
		}
	}

	/* sort */
	for (i = n - size; i > 0; i -= size) {
		swap_func(base, base + i, size);
		for (r = 0; r * 2 + size < i; r = c) {
			c = r * 2 + size;
			if (c < i - size &&
					cmp_func(base + c, base + c + size) < 0)
				c += size;
			if (cmp_func(base + r, base + c) >= 0)
				break;
			swap_func(base + r, base + c, size);
		}
	}
}

int main()
{
	srand(time(NULL));
	int *k = malloc(1000 * sizeof(int));
	
	for (int i = 0; i < 1000; i++) {
		k[i] = rand() % 1000;
	}

	sort(k, 1000, sizeof(int), cmp_int, swap);

	for (int i = 0; i < 1000; i++)
		printf("%d\n", k[i]);
        free(k);
}
```

---

### Post by kwyto on 2009-12-21
the solution given CptPicard works fine, but when encounter with large numbers it sucks dry the memory. maybe a solution without recursion would be better. 
 about whether people learn or not when all the have to do is import libraries is irrelevant. if you know your [EMAIL="!@#$(stuff"]!@#$(stuff[/EMAIL])  then you know, it will come a time when you'll have to proof your knowledge without anyone's help. that's when programmers are separated from men.

---

### Post by CptPicard on 2009-12-21
> **LKjell said:**
> 
But whether you understand the algorithm is a different part. And even if you understand how an algorithm works it is not the same as know how to implement it and write it in C code.

True, algorithm and implementation are two (at least mostly) separate things. Although everything starts from actually understanding the algorithm -- it would be crazy to suggest that you could meaningfully implement anything without understanding what you're doing in the general case.

> Well look at the heapsort code below which is taken from the Linux kernel source and pseudo code from wikipeadia

IMO the kernel implementation is a great example of something that has lost all readable meaning as a heapsort. If you gave that code to someone without telling them what it is and asked them to name the algorithm, it's likely they would fail.

When you have a higher-level language, it becomes much easier and readable to express, in particular, structurally different variants of the same algorithm.

It should also be noted that nothing stops one from writing a heapsort like that in Python, but you just probably wouldn't, as there are other alternatives to construct the implementation (and no, I do not mean just by calling a library function).

> **kwyto said:**
> the solution given CptPicard works fine, but when encounter with large numbers it sucks dry the memory.

The max stack usage is linear in the length of input, so yes, in that sense it is a rather inefficient version. However, considering that these are permutations, **n!** is such a rapidly growing number that you will run out of time to enumerate all of them much, much faster than you're going to run out of stack (unless you mean that the algorithm pushes and pops quite a bit of stack frames in total). 

In that sense I don't understand what you mean by it sucking memory unless the solution has a bug somewhere -- there is no way you'll ever get through an output large enough to cause any memory issues :)

> whether people learn or not when all the have to do is import libraries is irrelevant. if you know your [EMAIL="!@#$(stuff"]!@#$(stuff[/EMAIL])  then you know, it will come a time when you'll have to proof your knowledge without anyone's help. that's when programmers are separated from men.

The "they're just importing libraries" is the common straw man in the high level/low level language discussion. The important point to realize that HLLs do not implement specifically a library call for each imaginable specific problem (there would be an infinite amount of them), but implement a theoretically based, generic, abstract operator set that can be flexibly recombined with sufficient understanding of the problem structure. This is what I always try to tell the "pointer crowd", but in the end, it boils down to [having to have the exposure yourself]("http://www.paulgraham.com/avg.html"), to for example, functional programming concepts. Until they bother to learn, they will just dismiss offhand what they do not understand.

A really great example of this is the Python itertools and functools modules. From itertools docs:

> 
The module standardizes a core set of fast, memory efficient tools that are useful by themselves or **in combination**. Together, they form an **“iterator algebra”** making it possible to construct specialized tools succinctly and efficiently in pure Python.


Unless one understands why such an iterator algebra is a useful abstraction for implementing many programming concepts, one simply does not have the competence to have an opinion of whether one is or is not learning anything from them by learning how to structure solutions using such an algebra. And the only way to gain that competence is to... learn how it works and use it instead of complaining about the non-existence of pointers in the solution.

---

### Post by nvteighen on 2009-12-21
May I ask something?

Is this about **permutations** or **combinations**? Those are totally different mathematical concepts. A permutation is just about swapping elements; a combination also takes account about identity, such that BAC is the same combination that ABC but not that ABD (the usual combinations example is about dancing couples).

While permutation uses the formula:
```

          n!
nPm = ----------
       (n - m)!

```

Combination uses:
```

           n!
nCm = ------------
       m!(n - m)!

```

---

### Post by kwyto on 2009-12-21
yeah, that's what i meant. basically, like you said CptPicard the algorithm is very inefficient. by the way thank you for the link, very enlightening

---

### Post by CptPicard on 2009-12-21
> **kwyto said:**
> yeah, that's what i meant. basically, like you said CptPicard the algorithm is very inefficient.

I am curious what kind of results you're getting from it and what kind of a context you are using it in. I am able to enumerate and count all 12! permutations of a 12-character string in under 15 seconds on an Asus Aspire One here (not a particularly strong machine, that), and memory consumption is completely negligible -- max. 12 times the stack frame size.

For all practical purposes, this is the solution I'd use... as I said, n! grows so fast that you will not have enough time in the universe to do anything with the generated result on large enough n that will create memory problems.

EDIT: Interesting, there appears to be a non-recursive approach that gives you the kth permutation...

[http://en.wikipedia.org/wiki/Permutation#In_computing](http://en.wikipedia.org/wiki/Permutation#In_computing)

Anyway, the big problem with permutations is always the n! complexity factor it introduces for the rest of your algorithm -- the generation is not the bottleneck, the handling of the results is.

---

### Post by kwyto on 2009-12-21
i'm talking about a similar problem someone had earlier, where he needed to do the same for a matrix of 175,000 X 175,000. now that's number like your mama just to make back in the day. so you see my point, otherwise for small numbers is a very elegant and clean solution.

---

### Post by CptPicard on 2009-12-21
Yeah, but what I am trying to ask here, is your n! really realistically manageable even after generation, no matter how one does it? I mean, if we're talking permutations of 175k^2 or something items, the whole deal is just computationally too demanding anyway and will "forever". But if you can get by just creating *specific* permutations, you may want to check out the Wikipedia algorithm on generating the kth permutation in a sequence, either with order or not.

---

### Post by kwyto on 2009-12-21
i understand what are you coming from. we are talking of number reaaaaally large, i was just trying to help the guy, even though he wasn't being very specific and definitely unclear in his explanations.

---

### Post by grayrainbow on 2009-12-21
> **CptPicard]IMO the kernel implementation is a great example of something that has lost all readable meaning as a heapsort. If you gave that code to someone without telling them what it is and asked them to name the algorithm, it's likely they would fail.[/QUOTE]
I assume you are not aware of the term 'reverse engineering'? You know, there are some people who kinda understand programs by having access only to programs machine code. I won't say is it good or bad, that's just a fact.

[QUOTE=kwyto said:**
> i understand what are you coming from. we are talking of number reaaaaally large, i was just trying to help the guy, even though he wasn't being very specific and definitely unclear in his explanations.
Apart from some not so common occasions, biggest problem with solutions with noticeble overhead is that most programs in the world do 'a little more' then just performing one tiny algorithm. Drop, by drop, by drop...ocean is form.

Anyway, it looks a lot like homework question, so I hope OP have it done and learn something.

---

### Post by bamsanks on 2009-12-21
It definitely was permutations I was looking for, I didn't realise there was a difference between combinations and permutations before posting this.
Thankyou to everyone for your feedback.

---

### Post by s1ightcrazed on 2009-12-21
> **Barriehie said:**
> In regards to the logic think of it as the input string becomes an array, or a list.  For each position in the string length you've got to cycle through all elements in the list; i.e. input string is 'ABC' so:

A A **A**
A A **B**
A A **C**
A B A
A B B
A B C
B A A
...

There are, as indicated prior, functions to do this but those don't help to understand what's happening.  I use a method like this to generate random filenames where my 'list' is upper and lower case letters and the numbers 0 - 9.  For a 20 character filename I end up with:
62^20 = 704,423,425,546,998,022,968,330,264,616,370,176 combinations.  I don't know what that number is but I've yet to generate a duplicate name! :)

HTH
Barrie

That would be 704 decillion, 423 nonillion, 425 octillion, 546 septillion, 998 sextillion, 22 quintillion, 968 quadrillion, 330 trillion, 264 billion, 616 million, 370 thousand, 1 hundred and seventy six.

---

### Post by Barriehie on 2009-12-21
> **s1ightcrazed said:**
> That would be 704 decillion, 423 nonillion, 425 octillion, 546 septillion, 998 sextillion, 22 quintillion, 968 quadrillion, 330 trillion, 264 billion, 616 million, 370 thousand, 1 hundred and seventy six.

:)

---

