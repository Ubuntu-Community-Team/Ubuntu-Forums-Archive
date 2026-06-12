---
title: "Weekly Programming Challenge: February 2, 2007"
date: 2007-02-01
forum: Programming Talk
---

### Post by meng on 2007-02-01
Okay so once again I have the honor of setting this week's problem. As regular followers will be aware, the preceding challenges have covered a broad range of tasks and skill levels, and this week's challenge will be aimed at the more elementary level:

A common task in board games or role-playing games is to roll a number of dice and do one of the following:
(a) take the total of all dice rolled.
(b) take the total of the highest *n* dice rolled.
(c) note how many of the dice rolled achieved a target number *t* or higher.

for example, if I rolled 4 six-sided dice and got [1, 2, 5, 5]
(a) the total is 13
(b) taking the highest three, the total is 12
(c) if I was aiming for a target of 5 or higher, I would score 2 "hits"

Your task is to write a program which will roll any required number of dice and process the result with parameters passed at runtime. If you wish to limit yourself to six-sided dice, that's fine. For "bonus marks" (yeah, right, believe me I am NOT marking this!) you could write your program to accept any number and combination of n-sided dice (numbered from 1 to n, of course).

For those who feel this task is too trivial, I have another challenge (although I rather suspect there's a library/module out there that will achieve this one easily):
Given a list of n items [1, 2, 3, ..., n], generate combinations and/or permutations of r objects selected from the list,  i.e. spell out P(n,r) and C(n,r)

Good luck.

---

### Post by Tomosaur on 2007-02-02
> **meng said:**
> Okay so once again I have the honor of setting this week's problem. As regular followers will be aware, the preceding challenges have covered a broad range of tasks and skill levels, and this week's challenge will be aimed at the more elementary level:

A common task in board games or role-playing games is to roll a number of dice and do one of the following:
(a) take the total of all dice rolled.
(b) take the total of the highest *n* dice rolled.
(c) note how many of the dice rolled achieved a target number *t* or higher.

for example, if I rolled 4 six-sided dice and got [1, 2, 5, 5]
(a) the total is 13
(b) taking the highest three, the total is 12
(c) if I was aiming for a target of 5 or higher, I would score 2 "hits"

Your task is to write a program which will roll any required number of dice and process the result with parameters passed at runtime. If you wish to limit yourself to six-sided dice, that's fine. For "bonus marks" (yeah, right, believe me I am NOT marking this!) you could write your program to accept any number and combination of n-sided dice (numbered from 1 to n, of course).

For those who feel this task is too trivial, I have another challenge (although I rather suspect there's a library/module out there that will achieve this one easily):
Given a list of n items [1, 2, 3, ..., n], generate combinations and/or permutations of r objects selected from the list,  i.e. spell out P(n,r) and C(n,r)

Good luck.

Are we allowed to use random number generator functions, or should we just write one of our own, to add a little more complexity?

---

### Post by pmasiar on 2007-02-02
> **Tomosaur said:**
> Are we allowed to use random number generator functions, or should we just write one of our own, to add a little more complexity?

Knuth has really good story about "homemade" random numbers generators (and why numbers they generate are not random) - I know I would not trust any random :-) quick-and-dirty hobby random number generator. IMHO, YMMV.

It might be separate task - to write really good random number generator, and write program comparing it to the one from library.

---

### Post by meng on 2007-02-02
> **Tomosaur said:**
> Are we allowed to use random number generator functions, or should we just write one of our own, to add a little more complexity?
Your choice! I assumed most would use an already available randomizing module. But if that's too simple, feel free to add complexity.

---

### Post by kpatz on 2007-02-02
Ok, here's my first go at it.  Written in C.  Compile with gcc.

To emulate the example: > for example, if I rolled 4 six-sided dice and got [1, 2, 5, 5]
(a) the total is 13
(b) taking the highest three, the total is 12
(c) if I was aiming for a target of 5 or higher, I would score 2 "hits"

run it with the following parameters:  -s 6 -n 4 -p 3 -t 5

Parameters are:

-n NUMDICE (specifies number of dice to roll, no default, parameter must be specified)
-s SIDES  (specifies number of sides on the dice, default 6)
-s and -n can be repeated, to roll dice of different sizes.  Make sure to specify -s before -n, since -s sets the number of sides for dice specified in later -n options.
-t TARGET (counts number of dice rolled with at least TARGET value)
-p N (totals values of top N dice.  Obviously N must be <= the total number of dice rolled)

Since I used a fixed allocation, there is a maximum of 100 dice that can be rolled per invocation.  I figured that pre-calculating the number of dice and then allocating the array dynamically was outside the scope of this exercise. ;)

```
#include <stdio.h>
#include <stdlib.h>
#include <malloc.h>
#include <time.h>

#define NUM_DICE 1
#define NUM_SIDES 2
#define NUM_TARGET 3
#define NUM_TOP 4
#define MAXDICE 100

struct s_die {
  int sides;
  int value;
};

static int dice_compare(const void *d1, const void *d2);
void usage(void);
void createAndRollDie(struct s_die *d, int sides);

main(int argc, char **argv)
{
  int i, j, target = 0, work, numDice = 0, nextParm = 0, topNumToTotal = 0;
  int hits = 0, total = 0, topTotal = 0, lastSides = 0;
  time_t t;
  struct s_die *dice, *p, **sortarray, **s;
  int numCurrSides = 6, numCurrDice = 2;

  /* Allocate space for up to 100 dice (for simplicity's sake) */
  if ((dice = (struct s_die *)malloc(sizeof(struct s_die) * MAXDICE)) == NULL)
  {
    fprintf(stderr, "Unable to allocate space for dice structures\n");
    exit(1);
  }
  p = dice;
  /* Seed random number generator */
  time(&t);
  srand(t);
  /* Parse arguments */
  for (i = 1; i < argc; i++)
  {
    if (*argv[i] == '-')
    {
       switch(*(argv[i] + 1))
       {
         case 'n':   /* Number of dice */
           nextParm = NUM_DICE;
           break;
         case 's':   /* Number of sides */
           nextParm = NUM_SIDES;
           break;
         case 't':   /* Target number */
           nextParm = NUM_TARGET;
           break;
         case 'p':   /* Total top p dice  */
           nextParm = NUM_TOP;
           break;
         default:
           fprintf(stderr, "Invalid parameter: %s\n", argv[i]);
           usage();
       }
    }
    else
    {
       switch(nextParm)
       {
         case NUM_DICE:
           numCurrDice = atoi(argv[i]);
           numDice += numCurrDice;
           if (numDice > MAXDICE)
           {
             fprintf(stderr, "Maximum of %d dice allowed\n", MAXDICE);
             exit(1);
           }
           for (j = 0; j < numCurrDice; j++)
             createAndRollDie(p++, numCurrSides);
           break;
         case NUM_SIDES:
           numCurrSides = atoi(argv[i]); break;
         case NUM_TARGET:
           target = atoi(argv[i]); break;
         case NUM_TOP:
           topNumToTotal = atoi(argv[i]); break;
         default:
           usage();
       }
    }
  }
  if (numDice < 1) usage();
  /*  Allocate array of pointers to sort dice */
  if ((sortarray = (struct s_die **)malloc(sizeof(struct s_die *) * numDice)) == NULL)
  {
    fprintf(stderr, "Unable to allocate space for sort array structures\n");
    exit(1);
  }
  /*  Print value of dice and build array for sorting, and calculate target hits */
  for (i = 0, p = dice, s = sortarray; i < numDice; i++, p++, s++)
  {
    *s = p;
    if (target > 0 && p->value >= target) hits++;
    if (p->sides == lastSides)
      printf(", ");
    else
    {
      printf("\nRoll %d-sided dice: ", p->sides);
      lastSides = p->sides;
    }
    printf("%d", p->value);
    total += p->value;
  }
  /*  Sort array */
  qsort(sortarray, numDice, sizeof(struct s_die *), dice_compare);
  /* Get total of top N dice */
  if (topNumToTotal > numDice) topNumToTotal = numDice;
  for (i = 0, s = sortarray; i < topNumToTotal; i++, s++)
    topTotal += (*s)->value;
  /* Print totals */
  printf("\nTotal of all dice = %d\n", total);
  if (topNumToTotal) printf("Total of top %d dice = %d\n", topNumToTotal, topTotal);
  if (target) printf("Total dice > %d = %d\n", target, hits);
  /* Clean up */
  free(sortarray);
  free(dice);
  return 0;
}

/* Compare function for qsort.  Returns are reversed so that sort is in descending order */
static int dice_compare(const void *d1, const void *d2)
{
   int v1 = (*(const struct s_die **)d1)->value;
   int v2 = (*(const struct s_die **)d2)->value;
   if (v1 < v2)
     return 1;
   else if (v1 > v2)
     return -1;
   else
     return 0;
}

/*  Initializes a die structure, and "rolls" the dice using rand() */
void createAndRollDie(struct s_die *d, int sides)
{
  d->sides = sides;
  d->value = rand() % sides + 1;
}

/* A little help blurb */
void usage()
{
  fprintf(stderr, "Usage: dice [-t target] [-p toptotal] [ [-s sides] [-n numdice] ] ...\n\n \
Rolls numdice dice of s sides.  Returns number of dice with value at least\n\
target, and total for toptotal dice.\n\
-s and -n can be repeated to roll multiple dice of different sizes.\n\
When -s and -n are used together, put -s first.\n");
  exit(1);
}

```

---

### Post by Tomosaur on 2007-02-02
> **pmasiar said:**
> Knuth has really good story about "homemade" random numbers generators (and why numbers they generate are not random) - I know I would not trust any random :-) quick-and-dirty hobby random number generator. IMHO, YMMV.

It might be separate task - to write really good random number generator, and write program comparing it to the one from library.

I know all that, but past challenges have mostly been 'wary' of using libraries, just wanted to clarify the situation :P

---

### Post by &lt;mawe&gt; on 2007-02-02
In Python:
```
import random

dices = int(raw_input("How many dices? "))
sides = int(raw_input("How many sides? "))
target = int(raw_input("Target: "))

eyes = [ random.randint(1,sides) for dice in range(dices) ]
top_3 = sorted(eyes)[-3:]
hits = len( [ i for i in eyes if i == target ] )

print "Rolled dices: ", eyes
print "Total: %s" % sum(eyes)
print "Top 3: %s" % top_3
print "Hits: %s" % hits
```

---

### Post by jblebrun on 2007-02-02
Generating permutations and combinations is a great way to show off the power of Python's generators. A generator, if you're not familiar with them, is a very useful construct that allows a function to return a value, but maintain state, and continue from the return (or yield) point on the next call. The most basic example I can think of is a generator which mimics the behavior of range for a step value of 1:

```

def range_generator(start, stop):
   while start < stop:
       yield start
       start += 1

```

By creating recursive generators, you can *easily* generate all permutations of combination of a list:

```

def perm(l):
    if len(l)==1: yield l
    else: for item in l:
            sl=list(tuple(l))
            sl.remove(item)
            for subperm in perm(sl): yield [item]+subperm

def comb(l):
    if len(l)==1: yield l
    else:
        sl=list(tuple(l))
        for item in l:
            yield [item]
            sl.remove(item)
            for subcomb in comb(sl): yield [item]+subcomb

```

These examples simply return all permutations of full size, and all combinations in the same rank order as the list passed in. It should be a simple exercise to extend these functions to return all permutations of a given size, or all combinations of a given size. I leave these exercises to the readers who have just discovered generators and want to play around with them a bit more.

---

### Post by &lt;mawe&gt; on 2007-02-04
I'm currently trying to learn Haskell (2 days now), so I thought this challenge would be an easy exercise. I was so wrong. The function *getrand* allone took 3 headaches.
```
module Main where

import IO
import List
import Random
import Text.Printf

getrand :: Int -> Int -> IO [Int]
getrand num sides = do
  g <- newStdGen
  let dices = randomRs (1::Int, sides) g
  return (take num dices)

prettifyDices :: (Show a) => [a] -> String
prettifyDices lst = concat $ intersperse "-" $ map (show) lst

main = do
  hSetBuffering stdin LineBuffering
  putStrLn "How many dices? "
  num <- getLine
  putStrLn "How many sides? "
  sides <- getLine
  putStrLn "Target: "
  target <- getLine
  rands <- getrand (read num) (read sides)
  let sorted = sort rands
  printf "Dices: %s\n" $ prettifyDices rands
  printf "Sum: %s\n"   $ show $ sum sorted
  printf "Top 3: %s\n" $ prettifyDices $ take 3 (reverse sorted)
  printf "Hits: %s\n"  $ show $ length $ filter (== (read target)) sorted
```
Any Haskell hackers out there who can show me how to *really* do this in Haskell?

Regards, mawe

---

### Post by sdrubolo on 2007-02-04
```

permutation l = h id l [1..l] 
  where
    h g 0 _ = [g[]]    
    h g len_1 list = f g list len_1 
      where 
        f _ _ 0 = []
        f g b@(y:ys) len_2 = (h (g . (y:)) (len_1 -1) ys) ++ (f g (swap b) (len_2-1))  
        swap [] = []
        swap (x:xs) = xs ++ [x]

```

Hi, this is my solution, even if I haven't understood very well what you meant by 
> 
Given a list of n items [1, 2, 3, ..., n], generate combinations and/or permutations of r objects selected from the list, i.e. spell out P(n,r) and C(n,r)


Especially for the r parameter. Anyway, this piece of function computes all the possible permutation of a given list  from 1 to n, which it is chosen by the user...
I hope it is quite close to what you meant.
Bye.

---

### Post by meng on 2007-02-04
I mean permutations and combinations according to the strict mathematical definition.

P(n,r) refers to the number of distinct selections of r objects from n choices, where order is important. For example, P(3,3), the number of orderings of 3 objects, is 3!=6.
C(n,r) refers to the number of distinct selections of r objects from n choices, where order is irrelevant. For example, P(3,2), the number of selections of 2 objects from 3 choices, is 3.

The exercise is not to calculate the NUMBER of possibilities, but to list all the possibilities.

---

### Post by jblebrun on 2007-02-04
> **meng said:**
> I mean permutations and combinations according to the strict mathematical definition.

P(n,r) refers to the number of distinct selections of r objects from n choices, where order is important. For example, P(3,3), the number of orderings of 3 objects, is 3!=6.
C(n,r) refers to the number of distinct selections of r objects from n choices, where order is irrelevant. For example, P(3,2), the number of selections of 2 objects from 3 choices, is 3.

The exercise is not to calculate the NUMBER of possibilities, but to list all the possibilities.

That's what my generator examples do. However, they only list all permutations of a set equal to the size of the input set, or all combinations in the same lexical order as the input set. It's trivial, though to extend them to meet your specifications. I just thought it was a good opportunity to introduce python's generators to those who aren't familiar with them.

---

### Post by meng on 2007-02-04
> **jblebrun said:**
> That's what my generator examples do. However, they only list all permutations of a set equal to the size of the input set, or all combinations in the same lexical order as the input set. It's trivial, though to extend them to meet your specifications. I just thought it was a good opportunity to introduce python's generators to those who aren't familiar with them.
Just to be clear: I'm not criticising your solution, but answering sdrubolo's "question". The generator approach is exactly what I'm interested in, it's perfect for passing each permutation/combination singly into another "test" function.

---

### Post by jblebrun on 2007-02-05
> **meng said:**
> Just to be clear: I'm not criticising your solution, but answering sdrubolo's "question". The generator approach is exactly what I'm interested in, it's perfect for passing each permutation/combination singly into another "test" function.

Ok, sorry! You didn't address anyone in particular in your response, so I was just covering my own bases ;-)

---

### Post by sdrubolo on 2007-02-05
```

c n r = p id [1..n] r
  where
    p g list r | r == 0 = g[]:[]
                   | (length list) < r = [] --to stop useless calculation
                   | otherwise = f g list r
      where   
        f _ [] _ = []
        f g (y:ys) r = (p (g . (y:)) ys (r-1)) ++ (f g ys r) 

```

This is the output...
> 
c 3 2 = [[1,2],[1,3],[2,3]]


It's been a pleasure, I did really enjoy this programming challenge. it is a good idea.
):P

---

### Post by Lux Perpetua on 2007-02-10
sdrubolo, what language is that? It looks like something based on ML, but it's been a while since I've written anything in ML. 

Combinatorial algorithms are fun. Here's a pretty basic C implementation: ```
#include <stdio.h>
#include <stdlib.h>

void show_strings(char **s) {
    for ( ; *s; ++s) {
        fputs(*s, stdout);
        fputc(' ', stdout);
    }
    putc('\n', stdout);
}

void show_permutations(char **begin, char **end, int r) {
    if (r == 0) {
        show_strings(end);
    } else {
        char *t = end[-1];
        char **s;
        for (s = end - 1; s >= begin; --s) {
            end[-1] = *s;
            *s = t;
            show_permutations(begin, end - 1, r - 1);
            *s = end[-1];
        }
        end[-1] = t;
    }
}

void show_combinations(char **begin, char **mid, char **end, int r) {
    if (r == 0) {
        show_strings(end);
    } else {
        char *t = end[-1];
        char **s;
        for (s = mid - 1; s - r + 1 >= begin; --s) {
            end[-1] = *s;
            show_combinations(begin, s, end - 1, r - 1);
        }
        end[-1] = t;
    }
}

int main(int argc, char **argv) {
    int n;
    if (argc < 3) {
        fprintf(stderr, "Usage: %s P|C size [args]\n", argv[0]);
        exit(EXIT_FAILURE);
    }
    n = atoi(argv[2]);
    if (n >= 0) {
        switch(argv[1][0]) {
        case 'C':
            show_combinations(argv + 3, argv + argc, argv + argc, n);
            break;
        case 'P':
            show_permutations(argv + 3, argv + argc, n);
            break;
        default:
            fprintf(stderr, "Usage: %s P|C size [args]\n", argv[0]);
            exit(EXIT_FAILURE);
        }
    }
    exit(EXIT_SUCCESS);
}
```

**Edit:** Or, for permutations also in (most-significant-element-last) lexicographic order: ```
void show_permutations(char **begin, char **end, int r) {
    if (r == 0) {
        show_strings(end);
    } else {
        char **s = end - 1;
        char *t = *s;

        for ( ; s >= begin; --s) {
            end[-1] = *s;
            *s = t;
            t = end[-1];

            show_permutations(begin, end - 1, r - 1);
        }

        for (s = end - 1; s > begin; --s) {
            *s = s[-1];
        }
        *begin = t;
    }
}
```

---

### Post by sdrubolo on 2007-02-10
Hi Lux Perpetua, this is Haskell.

---

