---
title: "Combine two numbers into one?"
date: 2012-11-04
forum: Programming Talk
---

### Post by Kdar on 2012-11-04
I want to combine two numbers into one, which can be of unknown length...

For example:
I have XXXXX and YYYYY and I want to creat XXXXXYYYYY

How could I do this?

Before.. when I was just combining single digits, it was easy, since I just multiply one by 10 and add, but here I do not know how long the second integer is (2, 3, 4, 5 digits?)

Also.. the reason I need this is that I want to monitor some events and I want to record a history of their order of execution. (I have three types of events which I indicate by digits 1,2,3)

---

### Post by KdotJ on 2012-11-04
You could convert the numbers into Strings, concatenate them and the convert the result back into an integer. 

Example in java:
```

int n1 = 12345;
int n2 = 67890;

String concat = Integer.toString(n1) + Integer.toString(n2);

int combined = Integer.parseInt(concat);

```

---

### Post by Vaphell on 2012-11-04
you didn't mention the language but in most you can
1. convert numbers to their string representations and glue these together and then convert back.
to_int( to_string(x)+to_string(y) )
2. find length using string methods 
x*10^( length( to_string(y) ) ) + y
3. find the proper power of 10 by going up from 1 and checking where number/10^n stops having value > 0
in C:
```
int glue( int a, int b )
{
  int d;
  for( d=1; b/d; d*=10 );
  return a*d + b;
}
```

---

### Post by Kdar on 2012-11-04
sorry, I am using C++.

---

### Post by Paari on 2012-11-04
Well in c++ it's going to be the same as Vaphel posted...  u'll get it this easy in Python :)

```

z = int(str(x) + str(y))

```

---

### Post by The Cog on 2012-11-04
I see a logical problem here - both "12"+"3" and "1"+"23" produce "123". How are you going to know which pair of inputs produced the output?

---

### Post by Kdar on 2012-11-04
Well, actually.. both XXXXX and YYYYY I produce by combining single digit at a time. They just signify a basic block. But there is a case when there is a dynamic block, thats where I want to combine XXXXX and YYYYY.

For basic block, I am just combining single digits as they come in..
1
12
123
1231
12313...
etc

---

### Post by Vaphell on 2012-11-04
edit:
before reading your reply

the cog is right, unless you won't get that problem with your numbers ever, you have to pad with 0s

1 333 -> 1333
1 33 -> 1033
1 3 -> 1003
actually that would make things easier, because you can do simple x*d+b where d is a constant


another potential problem - do your sequences have some upper bound on length? because if not, you shouldn't use numeric types to represent them - you risk overflow.

---

### Post by Kdar on 2012-11-04
oh yes.. I didn't thought of overflow. That can be a problem.. because some number of events are in ~50 range.

What would the best thing to use then? array?

---

### Post by trent.josephsen on 2012-11-04
By your own admission: > **Kdar said:**
> the reason I need this is that I want to monitor some events and I want to record a history of their order of execution.

Is there a problem with simply handling the events and assigning them integers in order? i.e. the first event is event 0, the second is event 1, etc. Or assigning them unambiguous digit strings according to the date and time of their occurrence, such as 20121104181505 (6:15.05 pm on November 4th)?

---

### Post by Kdar on 2012-11-04
Well, there are going to be many of those blocks. lets say about 2000. and for each block I want to have a string of characts that shows what type of events were executed.

I kind of want to have it all in one line for each individual block:
block address, block length, block trace/history

---

### Post by SuperCamel on 2012-11-04
Try using stringstream. No chance of buffer overflow.

```

#include <iostream>
#include <string>
#include <sstream>

using namespace std;

int main()
{
    int first_number = 1234;
    int second_number = 5678;
    stringstream i1;
    stringstream i2;
    string tmp_str;
    int result;
    i1 << first_number;
    i2 << second_number;
    tmp_str = i1.str() + i2.str();
    stringstream(tmp_str) >> result;
    cout << result << endl;
}

```

---

### Post by Vaphell on 2012-11-04
do you need the string for something else than visual purposes?
maybe put executed events in a list, at its end. That would be self documenting because traversing the list and producing the sequence when needed would be trivial with a simple for loop.

---

### Post by Kdar on 2012-11-04
well, its mostly for visual... I might try link list like you saying.. Since with some blocks I have overflow the way I do it now.

---

### Post by Vaphell on 2012-11-04
another benefit would be that while you seem to need only simple stuff, the list node class for executed events could be easily extended to provide other features, detailed info and what not, should the need arise.
Designing a program with not enough wiggle room more often than not proves painful in the long run, when the need to add unplanned functionality arises (featurecreepis be damned ;-) )

---

### Post by trent.josephsen on 2012-11-05
Forgive me, but if it's for visual purposes, why concatenate the two numbers in the first place? Why not separate them with a dash or a space or a tab or something?

---

