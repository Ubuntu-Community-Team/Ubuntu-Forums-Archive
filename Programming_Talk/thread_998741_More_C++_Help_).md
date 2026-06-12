---
title: "More C++ Help :)"
date: 2008-12-01
forum: Programming Talk
---

### Post by feedmeh8 on 2008-12-01
Im stumped :confused: 

Question : Write a C program to accept a value from the user and determine if the number is odd or even. Do not use the modulus operator.

would appreciate any help on this one ty :D

---

### Post by tjandracom on 2008-12-01
[QUOTE="feedmeh8"]Do not use the modulus operator.
[/QUOTE]

then use fmod() function. modulus operator works only on integers. fmod() function works on float/double numbers. :)

---

### Post by dribeas on 2008-12-01
You can check whether the least significant bit is set (odd number) [This assumes we are talking about integer numbers]

---

### Post by feedmeh8 on 2008-12-01
I am pretty much an absolute beginner and have no idea what those are :p

---

### Post by sambita on 2008-12-01
I believe something like this should work:

#include <iostream>

using namespace std;

int main()
{
	float arg;
	cout<<"Please enter number: ";
	cin>>arg;
	float aux = arg/2;	
	int x = (int)aux;	
	if(aux == x)
		cout<<"It's even"<<endl;
	else	
		cout<<"It's odd"<<endl;
}

The other solutions posted here should work as well, but maybe this is more whats intended in an absolute beginners course. Hope it helps! :)

---

### Post by Zugzwang on 2008-12-01
> **sambita said:**
> I believe something like this should work:

[...]


That doesn't need to work (hint: "==" on floating point numbers does not make much sense due to rounding errors). 

@OP: So you have given a task you are unable to solve right now. Maybe the goal of this excercise is to get you started with reading into programming on your own. Normally, if you are given a task and you have no clue how to do it, then something went wrong. You might want to discuss this with the person who gave you this task.

Note that we're having a policy on homework here!

---

### Post by sambita on 2008-12-01
> **Zugzwang said:**
> That doesn't need to work (hint: "==" on floating point numbers does not make much sense due to rounding errors). 


My bad, i did not know that, ive only had one c++ course so far, still learning. 


Luckily you corected me before any harm was done heh.

---

### Post by dribeas on 2008-12-01
> **sambita said:**
> My bad, i did not know that, ive only had one c++ course so far, still learning. 

Luckily you corected me before any harm was done heh.

I am not a native speaker, but I have always thought that even numbers were those integers divisible by 2, while odd numbers where the rest of the integers. My understanding is that the app should ask for a number (integer), read it and if it is divisible by 2 answer 'even' while if it is not answer 'odd'. Not using modulus operator just makes the test a little more complex, as with the modulus operator the check would be:

```
int x; // read from the user
if ( x % 2 ) {
   printf( "The number %d is odd\n", x );
} else {
   printf( "The number %d is even\n", x );
}
```

---

### Post by dwhitney67 on 2008-12-01
> **dribeas said:**
> I am not a native speaker, but I have always thought that even numbers were those integers divisible by 2, while odd numbers where the rest of the integers.
...

The beauty about mathematics is that it is a universal language.  Your interpretation of even and odd numbers is correct.

It is my understanding that if the least significant bit of a value is set (to a one), then the number is odd; even otherwise.

Because this appears to be a homework exercise, I will not provide the details on how to check if a particular bit is set; I will leave that for the OP to figure out.

Edit --

Dribeas, it looks like you beat me to the hint about the least-significant bit.

---

### Post by WitchCraft on 2008-12-01
I had this problem once one on a calculator who didn't had mod and round...

the solution is:
```

a = gcd(x,2)

if(a==1)
{
//odd
}
else
{
//even
}

```

Now, the trick is of course that gcd uses modulus division, but you don't see that ;-)
:lolflag:


So the goal is to write a gcd implementation that doesn't use modulus:

See here:
```

int fastGCD( register int ECX, register int EDX )
	//register int ECX ; // only in C, not C++
	//register int EDX ; // only in C, not C++
{
	register int EAX = EDX ;
	WHILE:
		if (ECX == 0)
			goto END_WHILE;

		EAX = EAX - ECX;

		if (ECX <= EDX) //JNS
				goto END_IF;
			EAX = ECX ;
			ECX = EDX ;
		END_IF:
	
		EDX = EAX ;
		goto WHILE;	
	END_WHILE:
	return EDX;
}

```
:lolflag:

---

### Post by jrupes on 2008-12-02
> **dribeas said:**
> You can check whether the least significant bit is set (odd number) [This assumes we are talking about integer numbers]

In code...

```

bool isOdd(int x)
{
  return (x & 1) ? true : false;
}

```

While the other responses are accurate, they are all much less clean/much more overkill than what you are looking for.

(I leave the user input part up to you...)

---

### Post by dwhitney67 on 2008-12-02
Congratulations!  You just answered the OP's homework assignment.

---

### Post by WitchCraft on 2008-12-05
> **dwhitney67 said:**
> 
Congratulations!  You just answered the OP's homework assignment.

lol
and what a trivial method :lolflag:
If you must give him a solution, give him an interesting one, like mine, which demands more thinking than doing it on your own *lol*

---

### Post by pp. on 2008-12-05
> **jrupes said:**
> While the other responses are accurate, they are all much less clean/much more overkill than what you are looking for.

If you're after a clean solution, you should eliminate that ugly and unnecessary ternary operator.

---

### Post by dribeas on 2008-12-06
> **pp. said:**
> If you're after a clean solution, you should eliminate that ugly and unnecessary ternary operator.

Yes, it is kind of funny how many times you find that kind of return statements:

```

   if ( condition ) return true; else return false;
// or more concisely:
   return ( condition ? true : false );

```

People just does not seem to notice that the condition (either for an if or a ternary operator) is already a boolean. Both of the statements above are precisely equivalent to:

```

   return condition;

```

which is even more concise and also simpler.

---

