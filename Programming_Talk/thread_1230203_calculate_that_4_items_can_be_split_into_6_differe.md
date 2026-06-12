---
title: "calculate that 4 items can be split into 6 different groups of 2."
date: 2009-08-03
forum: Programming Talk
---

### Post by PetePete on 2009-08-03
hi,
Could someone help me with this, (psyudo code or c#/java/c++ would be great).

If you have 4 different items, lets call them, coat, socks, pants, hat. this group of 4 items can be split into 6 different pairs. (coat & socks) (coat&pants) (coat&hat) (pants&socks) (socks&hat) (hat&pants), .. the order of the pair does not matter ((pants&socks) == (socks&pants))

how would I turn this into an alogorthm to compute N items into upto N-1 groups.

so with 6 items, caclulate groups of 2, 3, 4, 5 and 6. 

Even if someone can think of a way just to calculate the number of combinations there should be that'd be great.

cheers

---

### Post by nvteighen on 2009-08-03
Er... Have you learned about combinations in Maths?

When creating groups of n elements in a set of m, the amount of resulting groups is defined by:
```

C(n, m) = n!/((n - m)! * m!)

```

Where x! is the factorial of x.

---

### Post by PetePete on 2009-08-03
ok well i've found out this problem is called Binomial coefficients, and found some code to calculate the total number of different groups.



```

public static int Binom(int n, int m)
    {
	int[] b = new int[n + 1];
	b[0] = 1;
	for (int i = 1; i <= n; ++i)
	{
	    b[i] = 1;
	    for (int j = i - 1; j > 0; --j)
		b[j] += b[j - 1];
	}
	return b[m];
    }


```


any ideas how i might create these groups?

Binom(4,2) == 6... but how can i create the 6 differnt groups?

---

### Post by Habbit on 2009-08-03
This is just off the top of my head, but *I think* it should work to compute all possible pairings of two elements: it takes each element and pairs it with all others to the right.
```

std::vector<std::pair<int, int> > pairings;
std::vector<int> elements;

typename std::vector<int>::iterator cur_head, cur_tail;

for (cur_head = elements.begin(); cur_head != elements.end(); ++cur_head)
    for (cur_tail = cur_head; cur_tail != elements.end(); ++cur_tail)
        pairings.push_back(std::make_pair(*cur_head, *cur_tail));

```

---

### Post by PetePete on 2009-08-03
cheers, looking at that it should work for pairing, but I also need groups of 3, 4 ,5 (well n-1). n = number of elements.

---

### Post by Arndt on 2009-08-03
> **PetePete said:**
> cheers, looking at that it should work for pairing, but I also need groups of 3, 4 ,5 (well n-1). n = number of elements.

Knuth probably has something about it in The Art of Programming.

---

### Post by Tony Flury on 2009-08-03
Well if you have a function that takes each element and forms groups of two ... adapt that funtion to create groups of 3, and groups of 4 etc 

learn about recursion and loops.

This whole things stinks of homework to me.

---

### Post by PetePete on 2009-08-03
i can't believe that attitude of some of the people on these boards.
i come here with a problem ,which as a software dev does happen from time to time that you can't for whatever reason come up with the solution and need another pair of eyes. and i get accused of being a schoolchild and cheating on my homework and told to read a book!
yeah thanks alot.


but a sincere thanks to those which did offer their time to help me out.

---

### Post by Tony Flury on 2009-08-03
I did give you some help - i told you to research loops and recursion - even gave you idea how to proceed.

If you had some code that did not work - but it was obvious what it was meant to do, then you would get a load of help. What you did was came and asked for a solution - with no obvious evidence of your own effort to solve the problem.

it does still sound a lot like homework (it is the sort of problem that i was set when i was a student) - if it isn't then I apologise.

you have been given two code snippets that solve the "combination of 2 items" problem - see if you can work out how to adapt that code so it does combinations of "n" items - and then place that function in a loop so that n goes from 2 to 5.

---

### Post by veda87 on 2009-08-04
This also works... check this out.... 

```
((factorial(items))/((factorial(items-group))*(factorial(group))));

int factorial(int n)
{
        if (n == 1 | n == 0) {
                return 1;
        } else {
                return (n*factorial(n-1));
        }
}

```
Here items--> no of items
     group --> no of elements to be in a group
....

---

### Post by NovaAesa on 2009-08-04
Here's some Java/C++ style pseudocode:
```

Item[] itemArray = {coat, socks, pants, hat};
for (int i = 0; i < itemArray.length; i++) {
    for (int j = i + 1; j < itemArray.length; j++) {
        print itemArray[i] + "," + itemArray[j];
    }
}

```

I hope that helps. I haven't tested the pseudocode and threw it up in a hurry, but it should work! (or will work with a little bit of modification).

---

