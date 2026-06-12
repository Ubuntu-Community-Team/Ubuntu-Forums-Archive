---
title: "Fibbonaci Series"
date: 2007-08-02
forum: Programming Talk
---

### Post by ashvala on 2007-08-02
This Ain't my home work...

How many of you can write a program for Fibbanoci series in CPP?

---

### Post by LaRoza on 2007-08-02
> **ashvala said:**
> This Ain't my home work...

How many of you can write a program for Fibbanoci series in CPP?

Many can, actually, anyone who know what that series is can.

Are you asking for code?

([http://answers.yahoo.com/question/index?qid=20060807231437AADyZGU](http://answers.yahoo.com/question/index?qid=20060807231437AADyZGU))

---

### Post by mgoblue on 2007-08-02
Yeah it's pretty simple.  Try the "golden ratio" using recursion.

---

### Post by fazavon on 2007-08-02
using namespace std;

unsigned long fibo(unsigned long n, unsigned long x)
	{
	long sum;
	cout << x << " ";
	sum=n + x;
		if (n < 2147483647)
			{
			return sum + fibo(x,sum);
			}
		else
			{
			return x;
			}
	};

int main(int argc, char* argv[])
	{
	int y;
  fibo(0,1);
  cin >> y;
  return 0;
	}

---

### Post by Jessehk on 2007-08-02
> **ashvala said:**
> This Ain't my home work...


I don't believe you. :)

Here's a template metaprogramming one in D
```

import std.stdio;

template fib(uint n) {
    static if ( n < 2 )
        const uint fib = 1;
    else
        const uint fib = fib!(n - 2) + fib!(n - 1);
}

void main() {
    writefln( "%s", fib!(45) );
}

```

---

### Post by LaRoza on 2007-08-02
> **Jessehk said:**
> I don't believe you. :)

Here's a template metaprogramming one in D
```

import std.stdio;

template fib(uint n) {
    static if ( n < 2 )
        const uint fib = 1;
    else
        const uint fib = fib!(n - 2) + fib!(n - 1);
}

void main() {
    writefln( "%s", fib!(45) );
}

```
That is a good idea, can't copy and paste. (If it isn't homework)

If it IS homework, you get a faster result googling you question, "Program for Fibbonaci Series" will get you more. It will even fix your typo.

---

