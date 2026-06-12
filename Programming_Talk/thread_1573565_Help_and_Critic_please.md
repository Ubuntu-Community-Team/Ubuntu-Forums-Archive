---
title: "Help and Critic please"
date: 2010-09-12
forum: Programming Talk
---

### Post by zully602 on 2010-09-12
I took an intro C++ class in college over 10 years ago, other than what little I remember I am pretty much brand new to this.  I am trying to teach myself C and I decided to try to make a simple program that would generate lotto numbers for Powerball.  Five of the numbers should be between 1 and 54 and different from each other, printed in sequence to the screen.  The powerball number should be between 1 and 54 and may be the same as one of the others.  Favor #1.  My bubble sort is not working if someone could please help me with that.  Favor #2.  If I went about something the long way, even if it works the way i did it, i would appreciate an explanation of the easier method.  Thanks in advance.

Code follows:

```

/* This program displays lotto numbers for the standard powerball */

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main ()
{
    srand ( time(NULL) ); // seed randomness with system time
    /* Define variables */
    int myarray[4], pb, i, tmpvalue, foundsort = 1;

    /* Get random values for variables */
    for (i = 0; i <= 4; i++)
        myarray[i] = getrand();
    pb = getrand();

    printf ("Your Powerball Numbers\n\n");

    /* Make sure none of the numbers are the same, except for the Powerball */
    while (myarray[1]==myarray[0])
        myarray[1] = getrand();
    while (myarray[2]==myarray[0] || myarray[2]==myarray[1])
        myarray[2] = getrand();
    while (myarray[3]==myarray[0] || myarray[3]==myarray[1] || myarray[3]==myarray[2]);
        myarray[3] = getrand();
    while (myarray[4]==myarray[0] || myarray[4]==myarray[1] || myarray[4]==myarray[2] || myarray[4]==myarray[3]);
        myarray[4] = getrand();

    /* Put the numbers in order */

    //Pre sort check for debugging only
    printf ("%d, %d, %d, %d, %d PB: %d\n\n", myarray[0], myarray[1], myarray[2], myarray[3], myarray[4], pb);


    /* Bubble sort array */
    while (foundsort == 1)
    {
        foundsort = 0;
        for (i = 0; i <= 4; i++)
        {
            if (myarray[i] <= myarray[i+1])
            {
                foundsort = 1;
                tmpvalue = myarray[i];
                myarray[i] = myarray[i+1];
                myarray[i+1] = tmpvalue;
            }
        }
    }

    //Print output to the screen
    printf ("%d, %d, %d, %d, %d  Powerball: %d\n\n\n", myarray[0], myarray[1], myarray[2], myarray[3], myarray[4], pb);
    return 0;
}

int getrand(void) // returns random number in range of 1 to 54
{
   int n;
   n = random() %53 + 1;  //n is random number in range of 1 - 54
   return(n);
}

```

---

### Post by Some Penguin on 2010-09-12
One thing that grabs me immediately:

You're trying to put five items into an array of size four.

---

### Post by Some Penguin on 2010-09-12
And the next bit:  your sort will check whether the fifth item comes before a non-existent sixth item.

---

### Post by ghostdog74 on 2010-09-12
while C/C++ still has its uses, you can do pretty much the same thing using interpreted languages like Python/Perl. eg Python
```

>>> import random
>>> random.seed()
>>> random.sample( range(1,55), 6)
[36, 34, 4, 46, 24, 14]

```

Eg [Perl ]("http://docstore.mik.ua/orelly/perl/cookbook/ch02_08.htm")


no need to meddle with pointers or taking care of memory. You take less time to develop your code as well.

---

### Post by nvteighen on 2010-09-13
> **ghostdog74 said:**
> while C/C++ still has its uses, you can do pretty much the same thing using interpreted languages like Python/Perl. eg Python


Ok, I've seen "C/C++" before... but "Python/Perl"! LOL, I guess you'll be soon bitten by Python- and Perl-fanboys altogether, perhaps paving the way to common understanding between both communities! (Just kidding!)

@OP:
Seriously, ghostdog74 is right. C is not precisely the best language to do this, but well, I can understand that you do this for learning the language, but also take this as a chance to learn the limitations of a language like C, by comparing your code with ghostdog74's Python version.

---

### Post by r-senior on 2010-09-13
I think there are two reasons your bubble sort doesn't work:

(a) Your comparison is the wrong way round. For an ascending sort, you want to check if element * is [I]greater* than element [i + 1] and swap them if it is.

(b) Once you've corrected the array size to 5 elements as pointed out by Some Penguin, you don't want to check the fifth element against the sixth because the sixth is beyond bounds. So you need i < 4 rather than i <= 4 in your for loop.

Further to that, given that "foundsort" is a flag to indicate if the array is sorted, I'd call it "sorted" and use 0 as false, 1 as true accordingly. Makes it easier to read the algorithm.

I'd also put the sort into a function sort(int array[]) {...} so that it reads more naturally in the main function. You also get to isolate local variables, e.g. tmp in that function.

```

void sort(int array[]) 
{
    int i, tmp, sorted = 0;

    while (!sorted) {
        sorted = 1;
        for (i = 0; [COLOR="Red"]i < 4[/COLOR]; i++) {
            if (array[i] [COLOR="Red"]>[/COLOR] array[i+1]) {
                sorted = 0;
                tmp = array[i];
                array[i] = array[i+1];
                array[i+1] = tmp;
            }
        }
    }
}
```

Then you have:

```

    sort(myarray);

```

which is clear without a comment and a block of sorting code.

I've not picked through it, but I also think your algorithm for checking duplicates is missing something (I've seen duplicates coming out when I've run it). Personally I'd write a function that checks if the array contains a number and deal with duplicates before you add new numbers. Something like this:

```

    /* Choose random balls, no duplicates */
    int ball;
    for (i = 0; i <= 4; i++) {
        do {
            ball = random_ball();
        } while (contains(ball, balls));
        balls[i] = ball;
    }

```

Your "contains" function (you can probably think of a better name) is simple and could deal with a change in array size more easily than the hard-coded ORs:

```

int contains(int n, int array[]) 
{
    int i;
    for (i = 0; i < 5; i++) {
        if (array[i] == n) {
            return 1;
        }
    }
    return 0;
}

```

I guess you'd need to initialise the elements of the array to invalid ball numbers for that to work properly.

I've not compiled or tested some of this, but you get the idea.

---

### Post by spjackson on 2010-09-13
There are other ways to do this (different language, use qsort(), etc). However, as this is a learning exercise, I'll just comment on the bugs, of which there are quite a few. Some have been pointed out by others, but I've included them here anyway.

1. Your array needs to be declared as 
```
int myarray[5]
```2. Infinite looping
```

while (myarray[3]==myarray[0] || myarray[3]==myarray[1] || myarray[3]==myarray[2]);
        myarray[3] = getrand();
    while (myarray[4]==myarray[0] || myarray[4]==myarray[1] || myarray[4]==myarray[2] || myarray[4]==myarray[3]);
        myarray[4] = getrand();

```Both of these loops have an extraneous semi-colon at the end of the line containing  the while. If the conditions ever fire, you will loop forever. (The earlier while loops are OK.)

3. Bounds in array sorting
```
for (i = 0; i <= 4; i++)
```This should be ```
for (i = 0; i < 4; i++)
```You are comparing each item with the next one. For the fifth item (i==4) there is no next item.

4. Swap condition
```

            if (myarray[i] <= myarray[i+1])

```You must not swap if 2 items are equal, because once you have 2 adjacent equal items, you will swap them forever. Arguably, this is irrelevant since you ensure uniqueness before sorting, but if you are taking it as a general sorting algorithm then it's a bug.

If you are sorting in descending order then
```

            if (myarray[i] < myarray[i+1])

```For ascending order then
```

             if (myarray[i] > myarray[i+1])
 
```5. Random number generation
```

   n = random() %53 + 1;  //n is random number in range of 1 - 54

```This expression generates numbers in the range 1 - 53 inclusive. It can never generate 54.

Here's your complete code with all the above corrections.
```


/* This program displays lotto numbers for the standard powerball */

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int getrand(void); // returns random number in range of 1 to 54

int main ()
{
    srand ( time(NULL) ); // seed randomness with system time
    /* Define variables */
    int myarray[5], pb, i, tmpvalue, foundsort = 1;

    /* Get random values for variables */
    for (i = 0; i <= 4; i++)
        myarray[i] = getrand();
    pb = getrand();

    printf ("Your Powerball Numbers\n\n");

    /* Make sure none of the numbers are the same, except for the Powerball */
    while (myarray[1]==myarray[0])
        myarray[1] = getrand();
    while (myarray[2]==myarray[0] || myarray[2]==myarray[1])
        myarray[2] = getrand();
    while (myarray[3]==myarray[0] || myarray[3]==myarray[1] || myarray[3]==myarray[2])
        myarray[3] = getrand();
    while (myarray[4]==myarray[0] || myarray[4]==myarray[1] || myarray[4]==myarray[2] || myarray[4]==myarray[3])
        myarray[4] = getrand();

    /* Put the numbers in order */

    //Pre sort check for debugging only
    printf ("%d, %d, %d, %d, %d PB: %d\n\n", myarray[0], myarray[1], myarray[2], myarray[3], myarray[4], pb);


    /* Bubble sort array */
    while (foundsort == 1)
    {
        foundsort = 0;
        for (i = 0; i < 4; i++)
        {
            if (myarray[i] > myarray[i+1])
            {
                foundsort = 1;
                tmpvalue = myarray[i];
                myarray[i] = myarray[i+1];
                myarray[i+1] = tmpvalue;
            }
        }
    }

    //Print output to the screen
    printf ("%d, %d, %d, %d, %d  Powerball: %d\n\n\n", myarray[0], myarray[1], myarray[2], myarray[3], myarray[4], pb);
    return 0;
}

int getrand(void) // returns random number in range of 1 to 54
{
   int n;
   n = random() %54 + 1;  //n is random number in range of 1 - 54
   return(n);
}

```

---

### Post by dwhitney67 on 2010-09-13
EDIT:  Sorry; I just realized the OP wanted a solution in C.

-------------

Forget the array; IIRC, for Power-Ball, the ordering of the first 5 numbers is irrelevant.  Thus all one has to do is "select" 5 unique numbers, and then another final number as the Power-Ball number.  The latter does not need to be unique.

Here's a simple way to accomplish the app without the use of an array:
```

#include <set>
#include <vector>
#include <iostream>
#include <iterator>
#include <ctime>     // for time()
#include <cstdlib>   // for srand(), rand()

int main()
{
   const int MAX_NUM = 54;

   // seed random number generator
   srand(time(0));

   // container for storing first 5 unique numbers
   std::set<int> regNums;

   // obtain 5 unique numbers
   while (regNums.size() < 5)
   {
      regNums.insert((rand() % MAX_NUM) + 1);
   }

   // container for storing 5 unique numbers AND the Power Ball number
   std::vector<int> allNums(regNums.begin(), regNums.end());

   // obtain the Power Ball number
   allNums.push_back((rand() % MAX_NUM) + 1);

   // display results
   std::copy(allNums.begin(), allNums.end(), std::ostream_iterator<int>(std::cout, " "));
   std::cout << std::endl;

   return 0;
}

```

---

