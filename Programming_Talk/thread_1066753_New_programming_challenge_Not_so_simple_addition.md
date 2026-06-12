---
title: "New programming challenge: Not so simple addition"
date: 2009-02-11
forum: Programming Talk
---

### Post by maximinus_uk on 2009-02-11
This was a task I was given many years ago when a young student. It's quite fun, and since there was another thread requesting a programming challenge, well, here we are:

**TASK:**

Your program must get 2 integer values from the user. The first of these integers is used to define the end point of a list of integers starting with 1. I.e. if the value is 7, then you should generate the list 1234567.
Your task is to place either +'s (plus signs) or -'s (minus signs) in this list in such a way as to produce a sum that is equal to the value of the second number given. **You must generate all such possible lists.**

As an example, given the inputs 5 and 41, one possible answer would be this:

*12+34-5 (= 41, the second input)*

So you may place either a plus sign (+) or a minus sign (-) in-between each digit, or leave it unchanged.

You may start the whole sequence with a minus sign, if you wish:

Input: 9 and 6
*-123+45+67+8+9 (= 6, the second integer input)*

**OUTPUT:**

Output each given answer on it's own line as:

```
12+34-5 = 41
1 answer only
```

Or, if there are no possibilities.

```
No answers for 2 and 7
```

Bonus points if your code either A) scales up really well, B) can cope with optional hex digits, or C) Can cope with integer values bigger then 2^64


Good luck :)

---

### Post by s1ightcrazed on 2009-02-11
OK - I thought on this one for a while, and now my head hurts.

---

### Post by stevescripts on 2009-02-11
Interesting ...

Maybe I can find some time soon.

Steve

---

### Post by nvteighen on 2009-02-11
Hmm... really good one. Though I fear functional programming here has a clear advantage over imperative.

---

### Post by s1ightcrazed on 2009-02-11
OK - I have a few thoughts on this one.... the problem is that none of them will scale worth a damn. Of course that is not a requirement, but still, it would be nice. 

I'll try to post a solution later if I can. I guarantee it will be amateurish and probably slow as a drunk sloth, but it will work (I hope). 

Damn, I hate getting sucked into these things.

---

### Post by achron on 2009-02-11
Are you sure you aren't my old CS professor? He gave us a similar problem. It's a shame that I threw away all that homework some 30 years ago...  "Bah, I'll never need this again."

---

### Post by JK3mp on 2009-02-11
Hmm...interesting enough if i get some time i'll have to try this. Is there any particular language you want it in? Perl,Python,C++,Ruby etc

---

### Post by badperson on 2009-02-11
I'm taking a stab at this in perl...cool problem. I think my way will work, but like was mentioned above, it won't be fast when you get into big numbers. 
bp

---

### Post by jimi_hendrix on 2009-02-11
i hate math challenges...ill check it out sooner or later though

---

### Post by johnl on 2009-02-11
Here is a one-off C program that attempts to generate a solution using a greedy algorithm.  I haven't put a lot of thought into whether or not it is unable to solve some inputs that are actually solvable, but I wouldn't bet against it :).

```

#include <stdlib.h>
#include <stdio.h>
#include <inttypes.h>

typedef struct numset_s
{
    size_t count;
    int8_t* sign;
} numset_t;

#define numset_ispos(set, i) (((numset_t*)set)->sign[((int)i)] ==  1 ? 1 : 0)
#define numset_isneg(set, i) (((numset_t*)set)->sign[((int)i)] == -1 ? 1 : 0)

#define numset_setpos(set, i) (((numset_t*)set)->sign[((int)i)] =  1)
#define numset_setneg(set, i) (((numset_t*)set)->sign[((int)i)] = -1)

#define MIN(a,b) ((a)<(b)?(a):(b))


numset_t* numset_create (int range);
void      numset_delete (numset_t* set);
int       numset_sum    (numset_t* set);

int  solve  (numset_t* set, int target);
void report (numset_t* set, int target);


int main(int argc, char* argv[])
{
    int range, target;

    do {
        printf("input: ");
    }while(scanf("%d %d", &range, &target) != 2 || range < 0);

    numset_t* set = numset_create(range);

    int rc = solve(set, target);
    if (!rc) {
        report(set, target);
    } else if (rc == -1) {
        printf("impossible: sum(range) < target\n");
    } else if (rc == -2) {
        printf("can't solve this one :(\n");
    }

    numset_delete(set);

    return 0;
}


int solve(numset_t* set, int target)
{
    int s = numset_sum(set);
    int diff;

    if (s < abs(target)) {
        return -1;
    }

    while(s != target) {
        diff = s - target;

        if (diff == 1 || diff < 0) {
            return -2;
        }

        int i;
        for(i = MIN(diff/2, set->count - 1); i > 0; i--) {
            if (numset_ispos(set, i)) {
                numset_setneg(set, i);
                break;
            }
        }
        s = numset_sum(set);
    }
    return 0;
}

numset_t* numset_create(int range)
{
    numset_t* result = (numset_t*)malloc(sizeof(numset_t));
    result->sign = (int8_t*)malloc(sizeof(int8_t) * (range+1));
    result->count = range + 1;
    int i;
    for(i = 0; i < result->count; ++i) {
        result->sign[i] = 1;
    }

    return result;
}

void numset_delete(numset_t* set)
{
    free(set->sign);
    free(set);
}

int numset_sum(numset_t* set)
{
    int i;
    int result = 0;
    for(i = 1; i < set->count; ++i) {
        result += (i * set->sign[i]);
    }

    return result;
}

void report(numset_t* set, int target)
{
    int i;
    printf("0");
    for(i = 1; i < set->count; ++i) {
        printf("%c%d", numset_isneg(set, i) ? '-' : '+', i);
    }
    printf("=%d\n", target);
}

```

---

### Post by CptPicard on 2009-02-11
Some ideas for more competent Haskellers than I am... I still suck at it but I have a feel that Haskell would put all else to shame -- I would try code it myself if I weren't working a lot for rest of week...

Essentially, you have two lists ... the [1..n] list that contains digits, and then functions `+`, `-` and let's say "cons" : for putting together two digits into a number, so that 1 : 2 = 12. So what you want to do is that you want to produce a list of length n that contains all combinations of these operators. Think of each member of n as being one position "in between" the digits (and the first one is the possible initial - sign, or an insignificant : or +). Producing this all-combinations-list is not hard, and there is probably a function for it somewhere already.

Now, we either interleave the two lists or keep them separate (or zip them into a list of pairs)... the evaluation of this kind of structure should be doable as a fold (think how you evaluate infix using two stacks, for example). After that, it's just a question of a mapping and filtering for the equality condition.

---

### Post by s1ightcrazed on 2009-02-11
This is the best I could do (using python). 

The problem is that it scales like old people screw (i.e. it's slow and not all that satisfying) but it works and was relatively painless to code. 

BTW, I'm using the itertools that come with python 2.6.....this code WILL NOT WORK on <= 2.5.

[php]import itertools
import string

x=input('Enter first number: ')
y=input('Enter second number: ')

sign_list=['','+','-']
number_list=[]
solution_list=[]
sign_permutator_list=[]

for i in range(1,x+1):
	number_list.append(str(i))
	
for i in range(x):
	sign_permutator_list.append(sign_list)
	
for permutations in itertools.product(*sign_permutator_list):
	number_and_sign_list=[]
	for i in range(len(permutations)):
		number_and_sign_list.append(permutations[i])
		number_and_sign_list.append(number_list[i])
	potential_solution_string=string.join(number_and_sign_list)
	potential_solution=string.join(potential_solution_string.split(), "")
	if potential_solution[0] != '+':
		if eval(potential_solution) == y:
			solution_list.append(potential_solution)
if len(solution_list) > 0:
	for i in solution_list:
		print i+' is a possible solution'
else:
	print 'No solutions found'[/PHP]

Basically I am creating a string that is the length of the first number * 2. I do this by 'filling' spaces between the numbers with one of three possible signs, either '' (nothing), '+' or '-'. The way I do this is to take a list of those three 'signs' ( sign_list=['','+','-'] ) and then create a nested list of sign_list * the first number....so we now have a list that looks like [['','+','-'], ['','+','-'], ['','+','-'], ['','+','-']].... using itertools.product we generate all possible permutations of that new list, and then interleave these with the numbers. We turn this into a string, hit it with eval, and compare the result to the second number. 

Simple run:

```

randall@randall-laptop:~/projects/python$ ~/python-2.6.1/bin/python find_solution.py
Enter first number: 5
Enter second number: 5
1+2+3+4-5 is a possible solution
1-2-3+4+5 is a possible solution
-1+2+3-4+5 is a possible solution


```

phew!

---

### Post by Reiger on 2009-02-11
Haskell with IO and stuff:```

module Challenge where
import Data.Char
import Data.List

cases lim = foldl' (\os ps ->  [ o++p | o<-os, p<-ps]) ["1","-1"] blocks
	    where
	    blocks= map (\int -> [ op++int | op<- ["","-","+"] ]) $ map show [2..lim]

check expr val = (val ==) $ sum $ parseExpr expr 1

parseExpr [] f = []
parseExpr ('+':xs) f= parseExpr xs 1
parseExpr ('-':xs) f= parseExpr xs (-1)
parseExpr ls f = unpack $ span isDigit ls
	      where
	      unpack (a,b) =  [f * (read a :: Integer)] ++ (parseExpr b f)

prompt str = putStrLn str >> putStr ">>> " >> ((\x -> do str<-x; return ( read str :: Integer)) getLine)

solve lim val = filter (\e -> check e val) $ cases lim 

main =do 
      lim <- prompt "If I'm to find solutions, what is the largest digit I should work with?"
      val <- prompt "If I'm to find solutions, what is the value my expression should equate to?"
      let x = (solve lim val) in
	  if(x == [] )
	    then putStrLn "Sorry, I could not find any solutions!"
	    else (mapM (\s -> putStrLn $ "I found: "++s) x) >> putStrLn "Done!"
```

---

### Post by dmm1285 on 2009-02-11
sounds like a job for amb

---

### Post by maximinus_uk on 2009-02-11
When I solved this a few years ago I used a similar solution to s1ightcrazed.

I did think about saying 'no' to using something like an eval function if your language of choice had it, but that seems to be just a cheap way of making it a bit harder.

I got tested on this in C, and the metric they used for good coding skills (once you had actually solved the problem) was, believe it or , LINES OF CODE!!!

---

### Post by PythonPower on 2009-02-12
Quick hack in Python 2.5 (haven't got 3 on this computer):

[PHP]

def poss(n, first=False):
	if n == 0:
		yield []
		return
	
	q = ['', '-']
	if not first: q.append('+')
	
	for i in q:
		for j in poss(n-1):
			yield [i]+j


length = int(input('Length = '))
target = int(input('Target = '))

k = [str(a) for a in range(1, length+1)]

for x in poss(length, True):
	expr = ''.join(reduce(lambda x, y: x+y, (s for s in zip(x, k))))
	if eval(expr) == target: print(expr)

[/PHP]

Edit: sped things up just a little.

---

### Post by CptPicard on 2009-02-12
Yay, your code is looking a lot more "pythonic" than last time :P

---

### Post by s1ightcrazed on 2009-02-12
> **PythonPower said:**
> Quick hack in Python 2.5 (haven't got 3 on this computer):

[PHP]

def poss(n, first=False):
	if n == 0:
		yield []
		return
	
	q = ['', '-']
	if not first: q.append('+')
	
	for i in q:
		for j in poss(n-1):
			yield [i]+j


length = int(input('Length = '))
target = int(input('Target = '))

k = [str(a) for a in range(1, length+1)]

for x in poss(length, True):
	expr = ''.join(reduce(lambda x, y: x+y, (s for s in zip(x, k))))
	if eval(expr) == target: print(expr)

[/PHP]

Edit: sped things up just a little.

I was afraid of using recursion in this one, given the need to scale... I know it's hard to get away from when doing a permutations calc, but running this against larger numbers seems like it would hit the recursion limit. 

Then again, I could be wrong.

---

### Post by PythonPower on 2009-02-12
[QUOTE=s1ightcrazed]I was afraid of using recursion in this one, given the need to scale... I know it's hard to get away from when doing a permutations calc, but running this against larger numbers seems like it would hit the recursion limit.[/QUOTE]

I could incorporate the use of [this]("http://docs.python.org/library/sys.html#sys.setrecursionlimit") if it needed to scale. Algorithmically the algorithm is quite poor being a member of O(3^n) so scaling will be poor; kudos to anyone who can reduce this to polynomial complexity. :P

---

### Post by Reiger on 2009-02-12
I've improved mine somewhat, it runs a good bit faster now.

As for the recursion; that's why I use foldl' (which together with span makes for the import Data.List) -- that is a strict version of foldl.
Foldl can (and the ghci does that IIRC) be optimised to a loop, meaning that foldl' which doesn't have the weight of lazyness to bear (I'm going to evaluate everything anyway) should be able to handle *a very large* list without problems.

EDIT: A good way to test if the recursion holds is the case 12 67; 197 solutions according to my program out of 354294 cases to test.

---

### Post by PythonPower on 2009-02-12
Indeed, I get 197 solutions too. Your algorithm is O(3^n) too and checks all 2*3^11 = 354294 possibilities too. In addition, my algorithm has a memory complexity which is a member of O(n); I'm guessing your's is also.

---

### Post by s1ightcrazed on 2009-02-12
Anyone think we can get a performance benefit out of multi-threading somehow? I'm just wondering if its possible to break out the permutations calc into a bunch of smaller jobs, each one handled by a thread....

Just a thought.

---

### Post by orochibayot on 2009-02-12
very Interesting, i love this skills!:KS

---

### Post by CptPicard on 2009-02-12
> **PythonPower said:**
> kudos to anyone who can reduce this to polynomial complexity. :P

I am quite sure it can't be done -- this problem is very close to a number of well known NP-complete problems such as the [subset sum problem]("http://en.wikipedia.org/wiki/Subset_sum_problem"). Another similar problem is the [partition problem]("http://en.wikipedia.org/wiki/Partition_problem") ("can you select from the list so that +es compensate the -es?" -- the actual value of the right side of the equation is probably meaningless and can be thought of as 0). All of these are related essentially to the knapsack problem.

Now, you *might* be able to do some sort of search pruning by simplifying the equation as you "fix into place" parts of the expression, but then again you're just still left with just a constant on the right side to match the rest against... I am not sure it is really useful.

---

### Post by PythonPower on 2009-02-12
[QUOTE=CptPicard]I am quite sure it can't be done -- this problem is very close to a number of well known NP-complete problems such as the subset sum problem. Another similar problem is the partition problem ("can you select from the list so that +es compensate the -es?" -- the actual value of the right side of the equation is probably meaningless and can be thought of as 0). All of these are related essentially to the knapsack problem.

Now, you *might* be able to do some sort of search pruning by simplifying the equation as you "fix into place" parts of the expression, but then again you're just still left with just a constant on the right side to match the rest against... I am not sure it is really useful.[/QUOTE]

I think it may well be possible given the amount of information given but not used by many of the algorithms. In that sense the problem seems similar to [Project Euler 152]("http://projecteuler.net/index.php?section=problems&id=152") which has a very nice solution that requires checking far less than 2^79-1 = 604,462,909,807,314,587,353,087 states.

At the very least we should be able to reduce the complexity to O(k^n) (or similar) with k<3.

---

### Post by nvteighen on 2009-02-12
> **CptPicard said:**
> Some ideas for more competent Haskellers than I am... I still suck at it but I have a feel that Haskell would put all else to shame -- I would try code it myself if I weren't working a lot for rest of week...

Essentially, you have two lists ... the [1..n] list that contains digits, and then functions `+`, `-` and let's say "cons" : for putting together two digits into a number, so that 1 : 2 = 12. So what you want to do is that you want to produce a list of length n that contains all combinations of these operators. Think of each member of n as being one position "in between" the digits (and the first one is the possible initial - sign, or an insignificant : or +). Producing this all-combinations-list is not hard, and there is probably a function for it somewhere already.

Now, we either interleave the two lists or keep them separate (or zip them into a list of pairs)... the evaluation of this kind of structure should be doable as a fold (think how you evaluate infix using two stacks, for example). After that, it's just a question of a mapping and filtering for the equality condition.

OK, I'm not a Haskeller, as you know. But I implemented the first part (the "consing") in Scheme. Stupidly enough, I deleted the code but it's pretty much doable. After that, it shouldn't be difficult.

---

### Post by CptPicard on 2009-02-12
> In that sense the problem seems similar to [Project Euler 152]("http://projecteuler.net/index.php?section=problems&id=152") which has a very nice solution that requires checking far less than 2^79-1 = 604,462,909,807,314,587,353,087 states.

That's interesting. The usual approach to solving these sorts of subset-selection problems efficiently usually hinges on the ability to deduce something from the required property, based on what has been selected so far, to prune impossible future selections (branch-and-bound).

The first difference that jumps to mind here is that the Euler problem seems like it has two styles of useful monotonousness built into it -- you're just using addition which "makes stuff bigger" and when you increase the k in 1/k^2, you're making the term smaller. Cutoffs resulting from this (having to maintain the invariant of the equation) is what seems like will produce a result to this problem...

Using both + and - complicates stuff though because you really have much less of an idea how slapping a - somewhere is going to correctly compensate away what you've +'ed, if you catch my drift... you just don't know before you've placed all the signs (I suspect).

I guess the important structure is the following... 

```

We have equation 

a = b  where a is the expression and b is the other given constant

We form some number c from a part of the list that a is composed of

now, the problem reduces to dealing with the rest of the expression d, similarly, with the equation being

d = b - c

```

I am afraid the remaining subproblem is just equally bad although we do have the saving grace of not having to go through "all possible subsets" or something...

---

### Post by PythonPower on 2009-02-12
Branch cutting methods seemed to work quite poorly (but working at all is a huge improvement on the naive algorithm!).

Myself, I analyzed denominators so I could reduce the set down to containing only 34 elements. Then using the O(n*2^[n/2]) algorithm [Wikipedia]("http://en.wikipedia.org/wiki/Subset_sum_problem#Exponential_time_algorithm") describes I find how many solutions there are. In total it takes about 31 seconds in Python 3.

---

### Post by CptPicard on 2009-02-12
I've been trying to come up with a reduction between subset sum or something similar and this one, but haven't managed... at least that's a positive. :)

And on second thought regarding the euler problem, not surprising that branch-cutting is weak despite it not being an integer-problem (rationals are, after all, enumerable)...

---

### Post by s1ightcrazed on 2009-02-12
I had a (potentially stupid) thought....

Can we break up the list into, lets say 2 number 'blocks', calc all of the possible outcomes from those 2 numbers (8 possibilities, I believe), and then add/sub those against the calcs for the next 2 numbers, and keep going to the end? 

Again, it's the end of the day and the coffee has run out. This may be a dumb suggestion... I'll try to throw together some code to see if it makes sense.

---

### Post by howlingmadhowie on 2009-02-17
> **s1ightcrazed said:**
> I had a (potentially stupid) thought....

Can we break up the list into, lets say 2 number 'blocks', calc all of the possible outcomes from those 2 numbers (8 possibilities, I believe), and then add/sub those against the calcs for the next 2 numbers, and keep going to the end? 

Again, it's the end of the day and the coffee has run out. This may be a dumb suggestion... I'll try to throw together some code to see if it makes sense.

that would help with multi-threading. but it won't move the problem into P.

it may however move it below 3^n

---

