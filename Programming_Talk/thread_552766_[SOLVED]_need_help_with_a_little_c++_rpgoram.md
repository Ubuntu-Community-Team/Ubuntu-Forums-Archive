---
title: "[SOLVED] need help with a little c++ rpgoram"
date: 2007-09-16
forum: Programming Talk
---

### Post by rbprogrammer on 2007-09-16
ok, so this is my code:
```

#include <iostream>
#include <time.h>
using namespace std;
int main(int argc, char *argv[])
{
    const int N=5;
    int a[N];
    int randomInt;
    srand ( time(NULL) );
    bool newNumber = false;
    for (int i=0; i<N; i++)
    {
        do
        {
            randomInt = (rand() % 10 + 1);
            newNumber = true;
            for(int ct=0; ct<i; ct++)
            {
                if(a[i] == randomInt)
                {
                    newNumber = false;
                    break;
                }
            }
        }while( newNumber );
        a[i] = randomInt;
    }
    for (int i=0; i<N; i++)
    {
        cout << "[" << a[i] << "]" << endl;
    }
    return 0;
}

```
all it needs to do is create an array of N elements and insert NON-REPEATING numbers...

i know this is probably some easy solution, but i'm just not seeing it... i suspect it is something with the srand().. i'm not that familiar with it..

---

### Post by rbprogrammer on 2007-09-16
oh, i guess i should probably report on what the error is....

the program just hangs up and nothing is ever outputted to the screen.... :confused:

---

### Post by dwhitney67 on 2007-09-16
newNumber is never set to false if the secondary for-loop fails to find a repeating number.

---

### Post by rbprogrammer on 2007-09-16
ok, with a little tweeking, i got:
```

#include <iostream>
#include <ctime>    // For time()
#include <cstdlib>  // For srand() and rand()
using namespace std;
int main(int argc, char *argv[])
{
    const unsigned int N = 5;
    int a[ N ];
    int randomInt = 0;
    srand( (unsigned)time(0) );
    bool newNumber = true;
    for (int i=0; i<N; i++)
    {
        newNumber = false;
        while( !newNumber )
        {
            randomInt = rand() % N + 1;
            newNumber = true;
            for(int ct=0; ct<i; ct++)
            {
                if( randomInt == a[i])
                {
                    newNumber = false;
                    break;
                }
            }
        }
        a[ i ] = randomInt;
    }
    for (int i=0; i<N; i++)
    {
        cout << "a[ " << i << " ] == " << a[ i ] << endl;
    }
    return 0;
}

```
*but now it repeats random numbers...* :confused: :confused: 

to be more specific with what i need, i need an array with N elements to have the range of 1 through N+1 randomly placed in the array.

---

### Post by dwhitney67 on 2007-09-17
Here's a working program that is slightly different from yours.  I only tested it a few times, but I believe it works.

This program allows you to set N to whatever you want, and will fill up the array 'a' with unique, random, numbers.

Enjoy!

[PHP]#include <iostream>
#include <stdlib.h>   // for srand()
#include <time.h>     // for time()

using namespace std;


int main( int argc, char** argv )
{
  static const unsigned int N = 20;

  int a[N] = {0};         // initialize array to all zeroes

  srand( time(0) );       // seed random number generator

  // Obtain N unique numbers ranging from 1 to N
  for ( int i = 0; i < N; ++i )
  {
    int randomNumber = (rand() % (N)) + 1;

    // search list for duplicate; if one found, get another random number
    // and then search again, until a unique number is found.
    for ( int j = 0; j < i; ++j )
    {
      if ( randomNumber == a[j] )
      {
        // get new random number
        randomNumber = (rand() % (N)) + 1;

        // search from the beginning of the list (note j is set to -1
        // so that when the for-loop expression increments j, it is
        // set back to zero.)
        j = -1;
      }
    }
    a[i] = randomNumber;
  }

  // output results
  for ( int i = 0; i < N; ++i )
  {
    cout << "a[" << i << "] = " << a[i] << endl;
  }
}[/PHP]

---

### Post by gnusci on 2007-09-17
your code is ok just mind some corrections.

[PHP]
#include <iostream>
#include <ctime>    // For time()
#include <cstdlib>  // For srand() and rand()
using namespace std;
int main(int argc, char *argv[])
{
    const unsigned int N = 5;
    int a[ N ], ct;
    int randomInt = 0;
    srand( (unsigned)time(0) );
    bool newNumber = false;
    for (int i=0; i<N; i++)
    {
        newNumber = false;
        while( !newNumber )
        {
            randomInt = rand() % N + 1;
            newNumber = true;
            for(ct=0; ct<i; ct++)
            {
                if( randomInt == a[i])
                {
                    newNumber = false;
                    //break; //<--- don't use break here
                    ct = i;
                }
            }
        }
		a[ i ] = randomInt;
    }
    for (int i=0; i<N; i++)
    {
        cout << "a[ " << i << " ] == " << a[ i ] << endl;
    }
    return 0;
}

[/PHP]

---

### Post by dwhitney67 on 2007-09-17
gnusci -

That fix you suggested will not work.  The code I provided earlier did not come out of thin air, but only after a few attempts to solve the problem myself.

Initially I tried variations of the OP's code, only to find that it had unnecessary complexities.  I recall trying what you have suggested, and I know it does not work.

---

### Post by gnusci on 2007-09-17
I found the correct bug in the code, here just the snip:

[PHP]
if( randomInt == a[ct]) //<-------- here must be "ct"
{
       newNumber = false;
       break; //<---- this is right
} 
[/PHP]

---

