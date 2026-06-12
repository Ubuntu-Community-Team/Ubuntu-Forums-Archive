---
title: "[SOLVED] Why is always the same string returned?"
date: 2008-01-05
forum: Programming Talk
---

### Post by quandary on 2008-01-05
Hi!

Question in C++: Why does my program (see below) malfunction when the content of main is put in a function in a class?
It does always output:  
```

name "..NAME.."

```

instead of: 
```

name "{Any number of dots between 0 and 3 here}NAME{Any number of dots between 0 and 3 here}"

```

But when i put it in a seperate program (as seen below) it works perfectly.
Why???

```

#include <iostream>

inline int FuncRandomNumberInRange( int intMinInRange, int intMaxInRange )
{
	// srand( std::clock() ); // fast, only for Microbosoft
	// srand(time(NULL));  // slow, only for Microbosoft
	return ( rand() % (intMaxInRange - intMinInRange + 1) ) + intMinInRange ;
}

int main()
{
	
	for(int C=0; C < 100; C++)
	{
	std::string myname ="name \"";
	int intRandomNumber = FuncRandomNumberInRange(0,4);
	int i;
	for(i=0;i<intRandomNumber;++i)
		myname+= "." ;
	myname+= "NAME";
	intRandomNumber = FuncRandomNumberInRange(0,4);
	
	for(i=0;i<intRandomNumber;++i)
		myname+= ".";
	myname+= "\"" ;
	
	std::cout << myname << "\n" ;
	// usleep(100000);
	}
	
	return 0;
}

```

---

### Post by quandary on 2008-01-05
bump.

---

### Post by Majorix on 2008-01-05
Why is the randomizing srand() function commented out? Without it you will always produce the same set of numbers in a function.

---

### Post by quandary on 2008-01-05
> **Majorix said:**
> 
Why is the randomizing srand() function commented out? 
Without it you will always produce the same set of numbers in a function.


No, it only produces always the same set of numbers if srand() IS initialized.
ONLY on WINDOWS you need to initialize srand().

At least that's what i figured out that works with g++.

---

### Post by Lster on 2008-01-05
Look at the LibC manuals:

[QUOTE=LibC Manual]&#8212; Function: int rand (void)

    The rand function returns the next pseudo-random number in the series. The value ranges from 0 to RAND_MAX. 

&#8212; Function: void srand (unsigned int seed)

    This function establishes seed as the seed for a new series of pseudo-random numbers. If you call rand before a seed has been established with srand, it uses the value 1 as a default seed.

    **To produce a different pseudo-random series each time your program is run, do srand (time (0)).** [/QUOTE]

I highlighted the most important bit. ;)

Here is the link if you want more information:

[http://www.gnu.org/software/libc/manual/html_node/ISO-Random.html#ISO-Random](http://www.gnu.org/software/libc/manual/html_node/ISO-Random.html#ISO-Random)

---

### Post by Martin Witte on 2008-01-05
if you change to something like this, you get what the other repliers also say (done this on MS-Windows, but that is irrelevant for this example)
[PHP]
#include <iostream>

using namespace std;
class Random
{
public:
      Random(int min, int max):intMinInRange(min), intMaxInRange(max)
                 { srand(time(NULL)); }
      int FuncRandomNumberInRange()
      {	return ( rand() % (intMaxInRange - intMinInRange + 1) ) + intMinInRange ; }
private:
        int intMinInRange, intMaxInRange;               
};

int main()
{
	Random rand(0, 4);
	for(int C=0; C < 100; C++)
	{
	string myname ="name \"";
	int intRandomNumber = rand.FuncRandomNumberInRange();
	int i;
	for(i=0;i<intRandomNumber;++i)
		myname+= "." ;
	myname+= "NAME";
	intRandomNumber = rand.FuncRandomNumberInRange();
	
	for(i=0;i<intRandomNumber;++i)
		myname+= ".";
	myname+= "\"" ;
	
	cout << myname << "\n" ;
	}
    
    return 0;
}[/PHP]

---

### Post by quandary on 2008-01-05
> **Lster said:**
> 
I highlighted the most important bit. ;)


I repeat: srand(time(0)) or srand(time(NULL)) will make the program BREAK !

Look: Output of program without seed srand(time(0)):
```

name "...NAME."
name "..NAME"
name "...NAME"
name ".NAME.."
name "....NAME."
name "..NAME.."
name "NAME...."
name "...NAME."
name "NAME."
name "..NAME."
name ".NAME..."
name "..NAME...."
name "..NAME"
name "..NAME..."
name "..NAME"
name "....NAME.."
name "..NAME..."
name "....NAME.."
name "...NAME."

```
which is perfectly the output i wanted.


And now: Output with srand(time(0))
```

name "....NAME...."
name "....NAME...."
name "....NAME...."
name "....NAME...."
name "....NAME...."
name "....NAME...."
name "....NAME...."
name "....NAME...."
name "....NAME...."
name "...NAME..."
name "...NAME..."
name "...NAME..."
name "...NAME..."
name "...NAME..."
name "...NAME..."
name "...NAME..."
name "...NAME..."
name "...NAME..."
name "...NAME..."
name "....NAME...."
name "....NAME...."
name "....NAME...."
name "....NAME...."
name "....NAME...."
name "....NAME...."
name "....NAME...."
name "....NAME...."
name "....NAME...."
name "....NAME...."
name ".NAME."
name ".NAME."
name ".NAME."
name ".NAME."
name ".NAME."
name ".NAME."
name ".NAME."
name ".NAME."
name ".NAME."
name ".NAME."
name "NAME"
name "NAME"
name "NAME"
name "NAME"
name "NAME"
name "NAME"
name "NAME"
name "NAME"
name "NAME"
name "NAME"
name ".NAME."
name ".NAME."
name ".NAME."
name ".NAME."
name ".NAME."
name ".NAME."
name ".NAME."
name ".NAME."
name ".NAME."
name ".NAME."
name "....NAME...."
name "....NAME...."
name "....NAME...."
name "....NAME...."
name "....NAME...."
name "....NAME...."
name "....NAME...."
name "....NAME...."
name "....NAME...."
name "....NAME...."
name "..NAME.."
name "..NAME.."
name "..NAME.."
name "..NAME.."
name "..NAME.."
name "..NAME.."
name "..NAME.."
name "..NAME.."
name "..NAME.."
name "..NAME.."
name "..NAME.."
name "..NAME.."
name "..NAME.."
name "..NAME.."
name "..NAME.."
name "..NAME.."

```
This is exactly what i don't want...


And the output of the program when part of a class, with or without srand(time(0)) is:
```

name "..NAME.."
name "..NAME.."
name "..NAME.."
name "..NAME.."
name "..NAME.."
name "..NAME.."
name "..NAME.."
name "..NAME.."
name "..NAME.."
name "..NAME.."
name "..NAME.."
name "..NAME.."
name "..NAME.."
name "..NAME.."
name "..NAME.."
name "..NAME.."
name "..NAME.."
name "..NAME.."
name "..NAME.."
name "..NAME.."
name "..NAME.."
name "..NAME.."
name "..NAME.."
name "..NAME.."
name "..NAME.."
.
. (= etc.)
.
name "..NAME.."
name "..NAME.."
name "..NAME.."
name "..NAME.."
name "..NAME.."
name "..NAME.."

```
And this is the last thing i want...

---

### Post by Lster on 2008-01-05
How does it break? What happens? That text I quoted was from the official GNU C Library Manual, they must know what they're talking about.

Martin Witte's code looked good to me - have you tried it?

---

### Post by Jessehk on 2008-01-05
> **quandary said:**
> 
i've to loop much, and that gives quite a lot of time for each key. 
Imagine, 16 seconds for each key at least... for 100 keys 
that's 26+ minutes; i am faster if i do it by hand myselfs...

That's why i have to use clock as seed.
 But unforunately, clock doesn't work very well, and i know that problem. 
Still, i remember having once solved that problem by not seeding, but unforunately I don't have that sourcecode handy right now...

Try Boost.Random [http://www.boost.org/libs/random/index.html](http://www.boost.org/libs/random/index.html)

For example (you don't actually have to write the wrapper class like I did):
```

#include <iostream>
#include <cstdlib>

#include <boost/random.hpp>
#include <boost/static_assert.hpp>

template <int LOWER, int UPPER>
class RandIntGen {
BOOST_STATIC_ASSERT( LOWER <= UPPER );
private:
    boost::mt19937 rng_;
    boost::uniform_int<> range_;
public:
    explicit RandIntGen() :
        rng_( std::time( 0 ) ),
        range_( LOWER, UPPER ) {}

    inline int operator()() {
        return range_( rng_ );
    }
};

int main() {
    RandIntGen<0, 10> randint;
    
    for ( int x( 0 ); x != 10; ++x )
        std::cout << randint() << std::endl;
}

```

```

9
8
1
7
2
4
1
4
7
9

```

---

### Post by Lster on 2008-01-05
Perhaps if you post your whole program we can help figure out what isn't working?

---

### Post by quandary on 2008-01-05
> **Lster said:**
> 
How does it break? What happens? 
That text I quoted was from the official GNU C Library Manual, they must know what they're talking about.

Martin Witte's code looked good to me - have you tried it?


No, Martin Witte's code is not good, because:
1. I did not wanted to have it as a class, i said i use it as content of a function in a class (i mentioned it because i suspect that a call from inside a class to a function outside that class might be different from calling the very same function from outside that class - that could explain the difference in program behaviour...)
2. if someone would write a class for random numbers in a range, it wouldn't be wise to limit the range to [0,4] instead i would call: rand.FuncRandomNumberInRange(0,4);
3. a class for this alone is crazy, that's like breaking a butterfly on the wheel...

---

### Post by quandary on 2008-01-05
> **Lster said:**
> 
Perhaps if you post your whole program we can help figure out what isn't working?


The whole program is quite big.

---

### Post by stroyan on 2008-01-05
Your problem as described should not be happening.  WIthout the actual code to look at we are all reduced to guessing about what is not as you understand it to be.  I will take a couple of guesses.

  My first question would be whether rand.FuncRandomNumberInRange(); is actually being called every time you write to cout.  I notice in you example that you are setting intRandomNumber both when you declare it and before counting out the trailing '.'s.   Is it possible that you translated that to a case by making intRandomNumber into a class variable that is initialized and assigned a random value exactly once?

The next question is whether rand.FuncRandomNumberInRange(); is actually being called many times and producing the same value every time.  If it is producing the same value we can concentrate on the result of rand().  If it is not, then we can look elsewhere.

You can answer both those questions by adding a write to cout or cerr of the FuncRandomNumberInRange function result before returning it.

Or you could just single step through your class with a debugger and watch for something unexpected to happen.

---

### Post by dwhitney67 on 2008-01-05
The code below works.  Maybe you shouldn't have initialized (seeded) the random generator each time you called your function.

[PHP]#include <stdlib.h>
#include <iostream>
#include <string>

using namespace std;


int getRandomNumberInRange( int min = 0, int max = 1000 )
{
  static bool first = true;

  if ( first )
  {
    first = false;
    srand( time(0) );
  }

  return (rand() % (max - min + 1)) + min;
}


int main( int argc, char **argv )
{
  int userMin = (argc > 1) ? atoi(argv[1]) : 1;
  int userMax = (argc > 2) ? atoi(argv[2]) : 10;

  string str( "name \"" );

  int randVal = getRandomNumberInRange( userMin, userMax );
  for ( int i = 0; i < randVal; ++i )
  {
    str += ".";
  }

  str += "NAME";

  randVal = getRandomNumberInRange( userMin, userMax );
  for ( int i = 0; i < randVal; ++i )
  {
    str += ".";
  }

  str += "\"";

  cout << "str = " << str << endl;

  return 0;
}[/PHP]

---

### Post by Wybiral on 2008-01-06
As dwhitney67 said, you should NOT seed the random number each time! Just seed it at the start of your program and it will continue to spit out "random" numbers. If you seed it to the time each loop, the time isn't changing fast enough to reset the random number generator to different seed each call.

---

### Post by quandary on 2008-01-06
Arrrgh, always the semicolons, problem solved. 

Non of the above was right.
I shouldn't have placed semicolons after for(...) in my function...

:lolflag:

What a stupid error... And by the way so obvious when you look at the code and think about what could produce this error!

And btw, no, there is no need to seed. If at all, it must be before the loop, or it brakes.

---

### Post by Wybiral on 2008-01-06
> **quandary said:**
> Arrrgh, always the semicolons, problem solved.

Non of the above was right.

What? The problem with the lack of randomness (which I perceived as being THE problem) was because you were seeding it EVERY iteration. The "srand" function seeds the random generator (tells it where to start). If you do this before each call to "rand" with the same seed, it will always return the same result. Since you're using "time" as a seed, the seed will only change each second (if you seed before each call to "rand").

Notice how this changes ever two calls (provided your computer is fast enough):
```

#include <time.h>
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int main(int argc, char *argv[])
{
    int i;
    for(i = 0; i < 10; ++i)
    {
        srand(time(NULL));
        printf("%i\n", rand());
        usleep(500000);
    }
    return 0;
}

```

This changes every call:
```

#include <time.h>
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int main(int argc, char *argv[])
{
    int i;
    for(i = 0; i < 10; ++i)
    {
        srand(time(NULL));
        printf("%i\n", rand());
        usleep(1000000);
    }
    return 0;
}

```

And this doesn't change at all (unless your computer takes an entire second to process all of these):
```

#include <time.h>
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int main(int argc, char *argv[])
{
    int i;
    for(i = 0; i < 10; ++i)
    {
        srand(time(NULL));
        printf("%i\n", rand());
/*
        usleep(1000000);
*/
    }
    return 0;
}

```

---

