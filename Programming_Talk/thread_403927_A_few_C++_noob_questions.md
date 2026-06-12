---
title: "A few C++ noob questions"
date: 2007-04-07
forum: Programming Talk
---

### Post by khedron on 2007-04-07
Hi everyone,

I am just learning C++. I have learnt C already, so this has not been too much of a shock to me.

However, I have a few questions that don't seem to be answered from looking at  cplusplus.com or the tutorials I have found on the internet.

1. When I return a complex object from a function (i.e. not just an int, char or float) is it passed by value? I.e. could I write ```
#include <iostream>
std::string HWText () 
{
std::string s ("Hello World!");
return s;
}

int main (void)
{
std::cout << HWText() <<endl;
return 0;
}
```This should print the Hello World text and exit. I'm not on my dev machine atm, but I seem to remember getting reference to local variable warnings when I used such a construct. Maybe it's just because I declared my function as std::string& (I know this would be wrong), but I'd like to be sure on such an important concept.

2. Is there a way of quickly defining a nameless object? For example, would the function below be equivalent to the one shown in question 1?```
std::string HWText ()
{
return std::string ("Hello World!");
}
```When I type this (not for a string actually, but for my own class) I get an error. Again, I'm not on my dev machine atm, so if you need to know the actual error and code, please ask.

3.  If I have a derivative of a class, how can I declare this << operator overload for both of them? Could I do something like```
class Error;
class InputError : public Error;
virtual std::ostream& operator << ( std::ostream&, Error& );
std::ostream& operator << ( std::ostream&, InputError& );

```Thanks for your time.

---

### Post by DoubleQuadword on 2007-04-07
Hi, in response to your questions:

1. Indeed, the function HWNext is returning an 'std::string' object as value.
2. Yes you can do that, and - by the way - you can do this too:
```

return "a string";

```

Since std::string has a constructor defined which takes a const char * as an argument.

3. A. The operators '<<' and '>>' cannot have two arguments.
    B. There's no need to declare them as virtual but if you need do so.

Regards.

---

### Post by khedron on 2007-04-07
Thanks for the help. So how should I declare the operator << overload?

Also, wouldn't there be ambiguity if I removed the **virtual** keyword and then did```
std::cout << InputError ("Error");
``` since there are two different functions that the InputError could use - the general Error one and the InputError one?

---

### Post by DoubleQuadword on 2007-04-07
Keeping or removing the virtual keyword would not help at all, the concept of 'virtual' is different. What are you doing is called 'operator overloading', and actually you can have more than one overload for any kind of function (including constructors).

I recommend you to ensure both declarations contain only one argument.

I.E:

```

std::ostream& operator << (std::ostream&);

```

Another thing, when you call InputError you're calling the class constructor, and there's no one defined which takes a void */char */const char */, etc; value; therefore, you're providing an InputError object to std::cout, which's not a supported value for the overloaded operator '<<' in cout.

And finally, if you want to call your operator do this:

```

InputError ie;
ie << (object of the type you specified or one that can be casted to it);

```

Regards.

---

### Post by khedron on 2007-04-07
But what if I want to define how my Error is written on the console, so I can do something like ```
ostream& operator << (ostream&, Error&) { /* define how to write an Error to stdout */ }
//....
try 
{
readSomething();
}
catch ( Error & err ) 
{
cout << err;
}

```I would have to define operator << including the Error type somewhere, wouldn't I?

---

### Post by DoubleQuadword on 2007-04-07
As I said in the previous posts, the declaration regarding the left shift operator ('<<') cannot contain two arguments.

It does not matter how you declare/define your operator '<<', you're not applying it at all to your 'Error' object. Instead, you're providing an 'Error' object to the std::cout which's not a supported type.

For example:

```

class myclass 
{ myclass(const char *); virtual ~myclass(); void operator << (const char *); };

// Now in your main...

myclass m("Hi.");
m << "Hi there!";

```

In this case you're calling the operator '<<' of 'm' which is of the type 'myclass', and you should define in the operator << definition how you want/need that string to be printed.

Regards.

---

### Post by khedron on 2007-04-07
Ok, thanks for the help.

---

### Post by wtruong on 2007-04-07
you don't gotta put std:: in if you write

using namespace std;

above main

---

