---
title: "Need help with c"
date: 2006-11-21
forum: Programming Talk
---

### Post by janfsd on 2006-11-21
Hi, I am still a newbie in programming, and need actually help doing an exercise, it is actually like this:

I need to write a program that finds all the possible combinations of a number (actually it's money) and prints them, just using bills of 20, 50 and 100... for instance:
for 120$ :
120 = 1*100 + 0*50 + 1*20
120 = 0*100 + 2*50 + 1*20
120 = 0*100 + 0*50 + 6*20

Even the algorithm to make it would be helpful, so please can you help me with this?

EDIT: oh, i forgot, I cannot use more than 2 loops.

---

### Post by hod139 on 2006-11-21
As many people have said before in the forum, no we will not do your homework for you.  Make an honest attempt at solving the problem first, and ask questions about specific problems.  You will learn and retain more information if you struggle through it first.

---

### Post by loell on 2006-11-21
i'd notice some of the programming exercises from the book had an answer sheet usually at the end of the book, perhaps check it out

---

### Post by janfsd on 2006-11-22
Well, I have already being trying for a long time, the thing is that I know how to make it with 3 loops (in a recursive way), but with 2 I have no idea. I was asking because maybe there is some kind of algorithm that can be used. Maybe some kind of hint to make it? Well I am still trying to find a solution. But any kind of help would be appreciated.

---

### Post by hod139 on 2006-11-22
This was wrong.

**EDIT:**  Oops, I should have read the original post more closely, you can ignore what I just wrote.

**EDIT2**: Why don't you post your thoughts (even if it is the 3 loop version) and then maybe some people can give nudges in the right direction.  Again, implementing an algorithm someone else tells you is not hard, coming up with the algorithm is the important part.  Write it in English (or whatever your native language is), then write it in code.

---

### Post by Lord Illidan on 2006-11-22
Let me give you a hint.

What I would have done was :

Let's say you have x dollars to convert to notes.

First, I'd divide the x dollars by 100. I'd take the integer part (ignore everything after the decimal point) and store the answer in a variable y.

Then i'd divide (x-y) by 50. And repeat the step of taking the integer part, etc. 

Then repeat for the 20, 10, and 5 dollar bills. It's quite easy.

---

### Post by hod139 on 2006-11-22
Lord Illidan,
This was also my first impression of the problem, however, upon further reading I don't think that is quite right.  The problem is not how to make change (of which you just presented the greedy algorithm), the problem is this:
Given a set of denominations, find all possible combinations of change.

---

### Post by yaaarrrgg on 2006-11-22
I'm not sure why the number of loops matters though in the exercise, since you can always take a three loop problem:

```

for( int i = 0 ...){
    for( int j = 0 ...){
        for( int k = 0 ...){
        ....
        }
    }
}

```

and refactor it as one loop:

```

int i,j,k = 0;
int sum = 0;
while( increment(i,j,k) ){
...
}

```

a simple solution: you could always just run through all possible sums of i*20 + j*50 + k*100, and store the ones that add up to the target sum.  Aso you can optimize this somewhat by jumping some groups of indexes when the sum is reached/exceeded. 

for a fancy solution, there is a branch of math that deals specifically with these problems (see "generating functions" in combinatorics and diophantine analysis) but i'm a little rusty on these.

---

### Post by janfsd on 2006-11-22
Thanks for all the answers. :) 

> **yaaarrrgg said:**
> I'm not sure why the number of loops matters though in the exercise, since you can always take a three loop problem:

```

for( int i = 0 ...){
    for( int j = 0 ...){
        for( int k = 0 ...){
        ....
        }
    }
}

```

and refactor it as one loop:

```

int i,j,k = 0;
int sum = 0;
while( increment(i,j,k) ){
...
}

```

What do you mean with "refactor it as one loop"? Is increment(i,j,k) a function of the loops you wrote before? or is it something else?

And about this:
> a simple solution: you could always just run through all possible sums of i*20 + j*50 + k*100, and store the ones that add up to the target sum. Aso you can optimize this somewhat by jumping some groups of indexes when the sum is reached/exceeded.
I was thinking on something like this, just the only problem is that i can only make it with 3 loops...
Still, I am going to check on these "generating fuctions" you mentioned.

---

### Post by scourge on 2006-11-22
Here you go, with only one loop:

```

#include <stdio.h>

static void combinations(int sum, int b20, int b50, int b100)
{
	if (sum == 0) {
		printf("%d*100 + %d*50 + %d*20\n", b100, b50, b20);
	} else if (sum > 0) {
		combinations(sum - 20, b20 + 1, b50, b100);
		combinations(sum - 50, b20, b50 + 1, b100);
		combinations(sum - 100, b20, b50, b100 + 1);
	}
}

int main(void)
{
	int sum;

	printf("Enter sum: ");
	scanf("%d", &sum);
	combinations(sum, 0, 0, 0);
	
	return 0;
}

```


The above code will list ALL the possible combinations, I'll leave it to you to figure out how to remove duplicates.

---

### Post by yaaarrrgg on 2006-11-22
> **janfsd said:**
> What do you mean with "refactor it as one loop"? Is increment(i,j,k) a function of the loops you wrote before? or is it something else?

generally, you can take three nested loops, and rewrite them as one loop.  The only thing that changes is you must manually increment the loop indices, and test the loop condition.

The "increment" function was just something I made up as an example.  It would increment the i,j,k variables and return 1 or 0.    Course there are other ways to do it (actually don't really even need to pass the i,j,k if they are global).

Actually though the solution using the recursive function might be the simplest... but here is an example of rewriting the loops ( totally untested :) ):

```


int target = 120; //whatever your amount is;
int i,j,k,sum= 0;

int max_i = target / 20;
int max_j = target / 50;
int max_z = target / 100;

while(true){
    sum = i * 20 + j * 50 + k * 100;

    //look for match
    if ( sum == target ){
        // found one
    }

    //manually increment
    i++;

    if( i > max_i ){
        i = 0;
        j++;
    }

    if( j > max_j ){
        j = 0;
        z++;
    }

    if( z > max_z ){
        break;
    }

}

```

---

### Post by janfsd on 2006-11-23
First of all, thanks to all for your help.

Ok then, yaaarrrgg I followed your example and this will be the code:
```
#include <stdio.h>
int main() {

	int target ;
	int i,j,k,sum= 0;
	scanf("%d",&target);

	int max_i = (int) target / 20;
	int max_j = (int) target / 50;
	int max_k = (int) target / 100;

	
	while(1){
		sum = i * 20 + j * 50 + k * 100;

		//look for match
		if ( sum == target ){
			printf("\n%d * 100 + %d * 50 + %d * 20\n",k,j,i); // found one
		}

		//manually increment
		i++;

		if( i > max_i ){
			i = 0;
			j++;
		}

		if( j > max_j ){
			j = 0;
			k++;
		}

		if( k > max_k ){
			break;
		}
	
	}
	int n;
	scanf("\n%d",&n);
	return 0;
}
```
This works perfectly,but notice before the end, the scanf... without it i get one possibility less, for instance for 120 you should get something like this:
```

0 * 100 + 0 * 50 + 6 * 20
0 * 100 + 2 * 50 + 1 * 20
1 * 100 + 0 * 50 + 1 * 20

```
However without that scanf, you dont get the 1st answer:
```

0 * 100 + 2 * 50 + 1 * 20
1 * 100 + 0 * 50 + 1 * 20
```
I tried several things to fix it, but nothing worked, so could you please explain me why this happens, and how to fix this?

Oh and about the recursive way that scourge posted before, well that works, my only problem is that I still can't find a way to remove the duplicate entries, any hint on how to make it?
By the way, I have already found another way to make it, but it's longer and I am looking for the most optimal way to resolve the problem.
Thanks again for your help.

---

### Post by scourge on 2006-11-24
> This works perfectly

Not on my system. You absolutely have to initialize the variables i, j and k to zero, or else you'll get undefined behavior. If you do that you won't need the scanf at the end.


> Oh and about the recursive way that scourge posted before, well that works, my only problem is that I still can't find a way to remove the duplicate entries, any hint on how to make it?

There are several ways. You could have a 3-dimensional array where you store the numbers for each bill every time a correct combination is found. But I think yaaarrrgg's example is more efficient so I would go with that.

---

### Post by janfsd on 2006-11-24
> **scourge said:**
> Not on my system. You absolutely have to initialize the variables i, j and k to zero, or else you'll get undefined behavior. If you do that you won't need the scanf at the end. 

Thanks for that, this worked!! I am just wondering why this happens?

---

### Post by amo-ej1 on 2006-11-24
it is logical to me, you allocate space to store anything in it. At that point you only want some space this is wat your get. If you want contents you should add it yourself ;)

---

### Post by scourge on 2006-11-25
> **janfsd said:**
> Thanks for that, this worked!! I am just wondering why this happens?

[http://c-faq.com/decl/initval.html](http://c-faq.com/decl/initval.html)

---

### Post by janfsd on 2006-11-25
Thx for the explanation, now I understand better ;)

---

