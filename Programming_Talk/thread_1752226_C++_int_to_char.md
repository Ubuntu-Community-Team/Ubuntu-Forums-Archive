---
title: "C++ int to char*"
date: 2011-05-07
forum: Programming Talk
---

### Post by 23Andrew on 2011-05-07
The title says it all really.

I've searched about, and all I can find are
[LIST]
[*]itoa. Which is windows only I think
[*]int to string. But I need char*
[*]Incomplete bit of code, without explaining what needs to be added to it.
[/LIST]

Ubuntu 10.10

---

### Post by cgroza on 2011-05-07
> **23Andrew said:**
> The title says it all really.

I've searched about, and all I can find are
[LIST]
[*]itoa. Which is windows only I think
[*]int to string. But I need char*
[*]Incomplete bit of code, without explaining what needs to be added to it.
[/LIST]

Ubuntu 10.10
Warning, bad code ahead!

```

char c(12);
char* c2 = &c;

```itoa is not Windows specific. it is included in stdlib.h.
[http://www.cplusplus.com/reference/clibrary/cstdlib/itoa/](http://www.cplusplus.com/reference/clibrary/cstdlib/itoa/)

---

### Post by simeon87 on 2011-05-07
```
#include <stdio.h>

int main (void)
{
    int c = 65;
    char d = (char) c;
    char *e = &d;
    // gives A:
    //printf("%s\n", e);
}
```

---

### Post by SledgeHammer_999 on 2011-05-07
And a C++ approach would be:

```

#include <iostream>
#include <sstream>

int main(int argc, char *argv[])
{
	const char *my_string = "45646";
	int my_int=0;
	
	std::stringstream ss;
	
	//Push the string into the stream.
	ss << my_string;
	
	//Extract the number from the string.
	ss >> my_int;
	
	/*You should do some error checking on the stream to see if the 
	 * conversion went well*/
	 	
	std::cout << "The number is: " << my_int << std::endl;
	return 0;
}


```

---

### Post by SledgeHammer_999 on 2011-05-07
Documentation on stringstream -> [http://www.cplusplus.com/reference/iostream/](http://www.cplusplus.com/reference/iostream/)

---

### Post by 23Andrew on 2011-05-07
Thanks for the help guys. I'm just reading through all the documentation on these things to see which is the most efficient.

---

### Post by james_mcl on 2011-05-07
If you're interested in another approach to this, I in turn would be interested to know how the combination of these two functions compares in terms of efficiency to the previous suggestions.

T should be an integer data type, such as int, size_t, or unsigned long int.

```

/*
If T is an integer data type, the number of digits of T are returned, with the minus sign counted as a digit in the case of a negative number.

If T is a floating point type, the number of digits of the integer part of the number are returned.
Again, the minus sign is counted as a digit in the case of a negative number.
The decimal point is not counted.
*/
template <typename T> unsigned int digits_of(T t)
{
	unsigned int i=0;
	if (t<=0)
	{
		t*=-1;
		i++;
	}

	/*
	However, the above won't treat 0 as a
	digit for numbers of the form \pm 0.x,
	unless x=0.
	*/
	if ((t < 1)&&(t > 0))
	{
		i++;
	}

	while (t >= 1)
	{
		t/=10;
		i++;
	}

	return i;
}

template <typename T> void int2str(T i, char *buf)
{
	if (i==0)
	{
		buf[0]='0';
		buf[1]='\0';
		return;
	}
	
	int x, l, base=10;

	if (i<0)
	{
		char *buf2=new char[digits_of(-i)+1];
		buf[0]='-';
		buf[1]='\0';
		int2str(-i, buf2);

		x=0;

		while(buf2[x])
		{
			buf[x+1]=buf2[x];
			x++;
		}
		buf[x+1]='\0';
		delete[] buf2;
		return;
	}

	l=digits_of(i)-1;
	buf[l+1]='\0';

	for (x=l; x>=0; x--)
	{
		buf[x] = '0' + (i % base);
		i/=base;
	}
}

```

---

### Post by ziekfiguur on 2011-05-08
@james_mcl if you just want to return the number of digits, wouldnt it be a lot more efficient to just do something like this:
```
#include <iostream>
#include <cmath>

size_t ndigits(ssize_t x)
{
    if (x == 0)
        return 1;
    if (x < 0)
        return static_cast<size_t>(log10(-x) + 2);
    return static_cast<size_t>(log10(x) + 1);
}

int main()
{
    std::cout << ndigits(948) << '\n'
              << ndigits(-948) << '\n'
              << ndigits(-1) << '\n'
              << ndigits(0) << '\n'
              << ndigits(1) << '\n'
              << ndigits(static_cast<ssize_t>(1.134)) << '\n'
              << ndigits(static_cast<ssize_t>(11424.123)) << '\n'
              << ndigits(static_cast<ssize_t>(-11424.123)) << '\n'
              << ndigits(234482932) << '\n';
    return 0;
}
```

---

### Post by dwhitney67 on 2011-05-08
> **23Andrew said:**
> The title says it all really.

I've searched about, and all I can find are
[LIST]
[*]itoa. Which is windows only I think
[*]int to string. But I need char*
[*]Incomplete bit of code, without explaining what needs to be added to it.
[/LIST]

Ubuntu 10.10

Why the need for a char*?  The others that have posted here have attempted to offer solutions; I would rather figure why you need a particular feature, than propose a solution that you may not need.

Btw, the STL string class offers a const char*, and a string object is available via the STL stringstream class.

---

