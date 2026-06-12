---
title: "Stumped: C++ vector element scope issue"
date: 2010-06-27
forum: Programming Talk
---

### Post by fallingcow on 2010-06-27
I'm new to C++, but not to programming in general.  I'm working on an exercise that involves printing a list of perfect numbers and their factors in a range, and decided that a vector would be the most convenient way to keep track of the factors.  I've put all the factor-finding and determining-if-it's-perfect stuff in a single function (isPerfect(int)), since they're highly related (and since the exercise calls for it to be done that way)

My first effort involved a global-scope vector in which I stored the factors, so I could simply return a bool from my isPerfect() function, print the number I'd passed to it, then for-loop over the vector to print the factors.  The program found the perfect numbers just fine, but when it came time to print the factors it displayed... odd behavior.

It printed the appropriate *count* of factors (e.g. three of them for 6) but the *values* of the factors are bizarre, large numbers.  All three for 6 would be the same large number, but (say) 28's factors would be a different large number, and so on.

Since it was correctly locating the perfect numbers, I tried taking a peek at the values of the global vector as they appeared in my isPerfect() function--sure enough, they're fine.

I'm guessing it's a scope issue, and that the numbers I'm seeing are addresses (or something) rather than regular values, or else gibberish resulting from (from main()'s perspective) un-initialized ints.  My guess is that vector's push_back(), when used inside a function, ignores the scope of the vector it's acting on, creating an element in the global vector but giving the element itself a local scope.

I've tried a couple of solutions:

1. declaring the vector in main() rather than making it global, then passing-by-reference to isPerfect().  Same problem.

2. creating a struct, putting isPerfect()'s usual bool result *and* the vector inside it, and making isPerfect() return the whole thing.  Same problem.

I'm using MingW's Windows port of gcc (g++) to compile, if it matters.

I can work around this problem, but the result is less elegant, and I feel that I *should* be able to do this (certainly I could in just about any other language I've used)

A couple hours of Googling has not helped.  What's the correct way to modify a global-scope vector from a function, or else to return a vector (without it becoming mangled, as mine do)?

I can include source if necessary, but a general answer to that last question should get me where I need to be.

---

### Post by dribeas on 2010-06-27
Without actual code there is not much that can be done, but take into account that the std::vector keeps copies, so the scope of the variable where they are copied from does not have any effect. That is, unless you are using a vector of pointers and having the pointers refer to local variables...

---

### Post by fallingcow on 2010-06-27
OK, here's the code from the version where I just use a global vector:

```
# include <iostream>
# include <vector>

using namespace std;

int max = 28;        // Highest number we'll investigate; keeping it low for testing purposes
vector<int> factors; // Factors for each number go here.

bool isPerfect(int number);

int main()
{
  cout << "The perfect numbers up to " << ::max << endl << endl;
  
  int i;
  for(i=3; i<=::max; i++)
  {
    if(isPerfect(i))
	{
	  cout << i << ": ";

	  int fi;  // Another iterator; stands for Factors Iterator
	  for(fi=0; fi<factors.size(); fi++)
	  {
	    cout << factors[i] << " ";
	  }

	  cout << endl;	
	}
	factors.clear();
  }

  return 0;
}

bool isPerfect(int number)
{
  int i;
  int factorsSum = 0;
  
  for(i=1; i<number; i++)
  {
    if((number % i) == 0)
	{
	  factors.push_back(i);
	}
  }
  
  for(i=0; i<factors.size(); i++)
  {
    factorsSum += factors[i];
  }

  if(factorsSum == number)
  {
    return true;
  }
  else
  {
    return false;
  }
}

```

Sample output:

```
6: 3023408 3023408 3023408
28: 842231141 842231141 842231141 842231141 842231141
```

(note that the numbers don't always stay the same)

I will be so very happy if someone finds that I've merely made some sort of simple, dumb error rather than stumbling on a Deep Mystery of C++ that will require a significant re-working of the code to accommodate; I eagerly await my embarrassment :)

---

### Post by Sub101 on 2010-06-27
I think;

```
	  int fi;  // Another iterator; stands for Factors Iterator
	  for(fi=0; fi<factors.size(); fi++)
	  {
	    cout << factors[[COLOR="Red"]i[/COLOR]] << " "; 
	  }


```

This is trying to access the vector at "i" which is defined as between 3 and 28.

Where as in the perfect method you have;

```
    if((number % i) == 0)
	{
	  factors.push_back([COLOR="Red"]i[/COLOR]);
	}

```

This places the number i in the next space. The next space may not be between 3 and 28.

I think your problem may be that the i in 

```
	    cout << factors[i] << " ";

```

should be "fi"

---

### Post by schauerlich on 2010-06-27
That doesn't even compile for me.

i686-apple-darwin10-gcc-4.2.1 (GCC) 4.2.1 (Apple Inc. build 5659)

---

### Post by croto on 2010-06-27
the line:

cout << factors[i] << " ";

should read 

cout << factors[fi] << " ";

---

### Post by Sub101 on 2010-06-27
> **croto said:**
> the line:

cout << factors[i] << " ";

should read 

cout << factors[fi] << " ";

Agreed. Be sure to name variables so they are not easily mistaken.

---

