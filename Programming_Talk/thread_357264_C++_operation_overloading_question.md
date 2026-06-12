---
title: "C++ operation overloading question"
date: 2007-02-09
forum: Programming Talk
---

### Post by rekahsoft on 2007-02-09
Hi all i have been haviung an issue with operating overloading. I have been reading my C++ book and have came accross code that does not work. Here is an example:```
//test.h
#ifndef __TEST_H
#include <string>
class Test {
     friend bool operator==(const Test&, const Test&);
     public:
          bool operator==(const Test&, const Test&);
     protected:
          std::string test;
};
#endif

//test.cc
#include "test.h"
bool Test::operator==(const Test& a, const Test& b) {
     return a.test == b.test;
}
```When i try to compile this with g++ i get the following error:```
bool Test::operator==(const Test&, const Test&) must take exactly one argument
```Then when i define the example like so:```
//test.h
#ifndef __TEST_H
#include <string>
class Test {
     friend bool operator==(const Test&);
     public:
          bool operator==(const Test&);
     protected:
          std::string test;
};
#endif

//test.cc
#include "test.h"
bool Test::operator==(const Test& a) {
     return this->test == b.test;
}
``` i get the following error:```
bool Test::operator==(const Test&) must take exaclty two argument
```Then when i define the class without the friend declaration it compiles. Can anybody explane what is happening here? This has thoroughly confused me. Thanks

---

### Post by WW on 2007-02-09
It appears that you have not copied your example and error message
correctly in the second case.  In test.cc, change b.test to a.test.
When test.cc is compiled, the error is
```
bool Test::operater==(const Test&) must take exactly two arguments
```

I think you are putting in the friend declaration unnecessarily.
Since operator== is a member function, it should not be declared a
friend.  In fact, this line
```
friend bool operator==(cont Test&);
```
seems to be telling the compiler that you will also define (somewhere
else) a different, non-member operator== function.  And, apparently,
a non-member operator== function must take exactly two arguments
(which makes sense).

So your code should really be
```

//test.h
#ifndef __TEST_H
#include <string>
class Test {
     public:
          bool operator==(const Test&);
     protected:
          std::string test;
};
#endif

//test.cc
#include "test.h"
bool Test::operator==(const Test& a) {
     return this->test == a.test;
}

```
with no friends declared.

---

### Post by rekahsoft on 2007-02-09
Thanks for the explanation, i had been using the the way that works (shown by your example) but just did not understand why, it makes more sence now but i do still not tottaly understand. I have fixed my original post so that it makes sence. Thanks

---

### Post by kvorion on 2007-02-10
Boy its been a long time since I used C++. In your  case you are trying to overload the == operator in two ways:

1) As a member function
```
public:
          bool operator==(const Test&, const Test&);
```

and

2) As a friend function

```
friend bool operator==(const Test&, const Test&);
```

I reckon that the first definition is what is causing you the error. See, the == operator is a binary operator, and therefore it takes only ONE object as an argument IF it is defined as a member function

So your first definition must be like this:

```
bool Test:: operator==(const Test& a)
{
return (a.test == this.test)
}

```

My advice is that avoid using a friend function for overloading if you can achieve the same using a member function. In case you must use the friend function to do you job, remember that a friend function takes TWO arguments for a binary operator.

So you can have this:

```

bool operator == (const Test& a, Test &b)
{
return (a.test == b.test)
}

```


BOTH of these will work, but I don know if you should use both of them in the same program cos I dont know if the compiler will be able to identify which one it wants to use.
One more thing, make sure that your == operator can actually compare two strings if this program should work :)

---

### Post by rekahsoft on 2007-02-11
Thanks :D i understand now :)

---

