---
title: "How would you solve this?(4 lines code)"
date: 2011-02-06
forum: Programming Talk
---

### Post by Pithikos on 2011-02-06
I take discrete mathematic at university and I came across some interesting code and was wondering how many programmers out there are actually good in math or even using math in their implementations. Here is the code:

```

for i=1 to 20 do
for j=1 to i do
for k=1 to j do
print(i*j+k)

```How many times do you think you would get something printed on the screen? Try to do this without modifying the code(like using a counter).

---

### Post by slavik on 2011-02-06
O(i^3)

---

### Post by Pithikos on 2011-02-06
> **slavik said:**
> O(i^3)
What stands "O" for?

---

### Post by MadCow108 on 2011-02-06
i*(i+1)*(i+2)/3! times

or more general:
1/d! \prod_{n=0}^d (i+n)
with i range and d dimension

---

### Post by sanderj on 2011-02-06
> **Pithikos said:**
> What stands "O" for?

It defines how a function goes to a value or infinity expressed in a simple fuction. So in this case it behaves like the function like i^3, so a third order function.

See [http://en.wikipedia.org/wiki/Big_O_notation](http://en.wikipedia.org/wiki/Big_O_notation)

---

### Post by cprofitt on 2011-02-07
> **Pithikos said:**
> I take discrete mathematic at university and I came across some interesting code and was wondering how many programmers out there are actually good in math or even using math in their implementations. Here is the code:

```

for i=1 to 20 do
for j=1 to i do
for k=1 to j do
print(i*j+k)

```How many times do you think you would get something printed on the screen? Try to do this without modifying the code(like using a counter).

I am unfamiliar with the language so I am not sure where your loops end.

---

### Post by Pithikos on 2011-02-07
> **cprofitt said:**
> I am unfamiliar with the language so I am not sure where your loops end.

It's not a specific language. It's pseudocode. Maybe this clarifies it a bit more:

```

for i=1 to 20 do
  for j=1 to i do
   for k=1 to j do
    print(i*j+k)
   end
  end
end

```

---

### Post by Pithikos on 2011-02-07
> **MadCow108 said:**
> i*(i+1)*(i+2)/3! times


But i is undefined. That doesn't give anything..

---

### Post by sanderj on 2011-02-07
> **Pithikos said:**
> But i is undefined. That doesn't give anything..

... Madcow108 already said "with i range", so fill out i=20, and you get your answer.


To understand Madcow108's formula: try an easier, 2-dimensional step: 1 + 2 + 3 + ... + n = (n^2)/2 + n/2 = 1/2*n*(n-1). Easy to check: it's a triangle, with little triangles on top of each column. You can calculate the area of that triangle and the small triangles, can't you?

Madcow108 describes the three-dimensional variant ... so think triangular cube. You already know it's volume is something with i^3 ...


Is this enough for your homework? ;-)

If not, you can also define your problem's answer recursively:
f(n)=number of lines, with:
f(1)=1
f(n)=f(n-1) + 1/2*n*(n+1)

Or as a serie:

n*1 + (n-1)*2 + (n-2)*3 + ... + 2*(n-1) + 1*n

---

### Post by InspiredIndividual on 2011-02-07
There is a slight mistake in MadCow108's general formula. It is obvious when you try and substitute some numbers for d and i. It should evidently be

1/d! \prod_{n=0}^(d-1) (i+n)
with i range and d dimension.

As your original question was how others would solve it: I would use generating functions. The problem is equivalent with the distribution of [depth] identical objects among [range] people. My probability-and-statistics oriented brain was immediately triggered by the analogy, although I surmise that MadCow108 solved the problem in a much easier way...

I do agree with sanderj, though. First post your own solution, or at least a good try, then I'll post mine ;-)

---

### Post by Pithikos on 2011-02-08
> **InspiredIndividual said:**
> There is a slight mistake in MadCow108's general formula. It is obvious when you try and substitute some numbers for d and i. It should evidently be

1/d! \prod_{n=0}^(d-1) (i+n)
with i range and d dimension.

As your original question was how others would solve it: I would use generating functions. The problem is equivalent with the distribution of [depth] identical objects among [range] people. My probability-and-statistics oriented brain was immediately triggered by the analogy, although I surmise that MadCow108 solved the problem in a much easier way...

I do agree with sanderj, though. First post your own solution, or at least a good try, then I'll post mine ;-)

Well it's not really homework. It's an example from my book(Discrete Math and Combinatorics pg32 example 1.47). The way the author solves it is combinations and he states:
> Any selection a,b,c [a=<b=<c] of size 3, with repetitions allowed, from the list 1,2,3, ..., 20 results in one of the correct selections here, k=a, j=b, i=c. Consequently the print statement is executed:
(20+3-1 choose 3)=(22 choose 3)So the thing really is that I can't understand his reasoning. So far I have been trying to have a visual way of combinations. For example if we have x+y+w=30 and we want to find the number of solutions to that equation, my thinking would be:

> We have 30 coins on the table on a row and they are devided in 3 groups. For that reason we have 2 pieces of papers as seperators. What we want is to arrange those pieces of papers among the 30 coins to get all possible answers. As I want all coins to be always on the table and I also want my pieces on the table I would assume that 30 coins + 2 pieces of paper make the 32 spots possible to put a coin or a paper. So to solve the problem I just have to find in how many ways I can arrange the pieces of paper and that gives me (32 choose 2)So as I have been following this concrete way to solve most of the problems I have a hard time understanding how someone can visualize the problem mentioned in the first post. That's why I posted the question in the first place. I just wanted to see if someone would give a more logic solution than the author but that proved just fatal :p

If it was up to me I would just make a table with the resulting values, find the pattern and try to make a Summation formula for it.

---

### Post by sanderj on 2011-02-08
This is how I visualize it:

Use a heap of lego cubes. I hope you can enjoy your neighbour country's invention.

First the 2-dimensional case:

Take 1 cube, and put it down. Content: 1 cube.

Take 2 more cubes, a lay them down in a horizontal 'row' next the one existing cube. 
Total area: 1 + 2 = 3

Take more lego cubs to create horizontal row #3. Total area: 1 + 2 + 3 = 6.

And so forth.
I already gave you the formula for the number of cubes. And you should be able to calculate it yourself.


Now the 3-dimensional case:

Use the stuff you already built with lego, and now make a triangle of columns on each horizontal row.

And because I'm such a nice guy, I've done it for you ... see pictures!

There, that's your visualization!

---

### Post by InspiredIndividual on 2011-02-08
I think I finally understand sanderj's reasoning. It evaded me before, but the triangle visualisation only works in the three dimensional case, isn't it? In, say, 18 dimensions it wouldn't help you any further. (Nice lego, by the way ;-) )

Regarding the explanation of the author of Pithikos' book: his answer is equivalent MadCow108's corrected formula.

The visualisation you use with the coins can be adapted to cover this particular problem. We have 20 numbered coins on the table in a row and we want to add 3 indicator coins to point out the index numbers of the loop. If, say, we place indicator coins before coins 4, 9 and 17, this means that index of the first loop is 17, the index of the second is 9 and the index of the third is 4. Hence, every line corresponds with a distinct way of placing the indicator coins. The position of the last numbered coin is fixed, because in our chosen visualisation the indicator coins point to the next numbered coin and no indicator coin can point to nowhere. Thus the indicator coins can be arranged in (20+3-1 choose 3) ways.

I think the coin visualisation is preferable to the one with lego, because it is easier to apply in higher dimensional cases. Lego is more fun, though :-D

---

### Post by MadCow108 on 2011-02-08
you might want to look up figurate numbers.
the two dimensional case are triangle numbers (or gauß sums)
the three dimensional case are tetrahedal numbers.

---

### Post by Vaphell on 2011-02-08
this problem is quite similar to calculating the d-th integral of 1 given the constraints on variables, which is obvious when you look at the lego example (area for d=2, volume for d=3). It's easy to come up with the general idea about the number without knowing much about discrete math and combinatorics.

int(**1** dz) = z
z in [0,y] -> **y**

int(**y** dy) = 1/2 y^2
y in [0,x] -> **1/2 x^2**

int(**1/2 x^2** dx) = 1/(2*3) x^3
x in [0,n] -> **1/(2*3) n^3**

it's easy to notice that the result of dth degree will be in form of **1/d! n^d** which is quite similar to the solution of the discrete problem. Difference stems from the 'blockiness' of the original that is not covered by the simplified integrals.

---

