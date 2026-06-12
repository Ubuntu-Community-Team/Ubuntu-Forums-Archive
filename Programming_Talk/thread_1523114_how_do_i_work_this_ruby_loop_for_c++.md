---
title: "how do i work this ruby loop for c++??"
date: 2010-07-03
forum: Programming Talk
---

### Post by unter on 2010-07-03
i have this not understanding for a c++ version of this ruby method.
it does execution a method/function a variable number of times like this:

```
n = 8

def a_method
puts "bla bla bla\n"
end

n.times do
    a_method
end
```i understand to know for c++???

```
#include <iostream>
using namespace std;

int n = 8;
a_function();

int main ()
 {       
   << do a_function n times here >>
   return 0; 
 }

void a_function(void)
 {
    cout << "blah blah blah\n" << endl; 
 }
```

---

### Post by Some Penguin on 2010-07-03
```

for (int i=0; i < 8; i++) {
   a_function();
}

```

Have a look at the the sticky threads.  Among other content, there's sure to be multiple links to C++ guides.

---

### Post by nvteighen on 2010-07-03
You need a **for** loop, a construct very common in many programming languages: C, C++, Python, Java, Javascript, etc.

```

#include <iostream>

void a_function(int);

int main(void)
{
    int n = 8;
    int counter;

    /* for(do something at start; loop condition; do after each iteration) { }
     *
     * There are other ways to do the same, but this is by far the most common
     * you'll see in C and C++. The idea is to set a counter that's incremented
     * (++) after each iteration and keep looping till the condition is no
     * longer true. In the code below, counter will take values from 0 to 7,
     * enough to have your loop executed 8 times.
     */
    for(counter = 0; counter < n; counter++)
    {
        a_function(counter);
    }

    return 0;
}

void a_function(int number)
{
    std::cout << "Blah! Counter is: " << number << std::endl;
}

```

Please, review some C++ reference.

---

### Post by unter on 2010-07-03
> **Some Penguin said:**
> ```

for (int i=0; i < 8; i++) {
   a_function();
}

```Have a look at the the sticky threads.  Among other content, there's sure to be multiple links to C++ guides.

where you have "< 8" there in for loop, can replace with my variable 'n'? as for the code I want for the loop to still work if value of n changes.  what is there tests for < 8 but not for value of n?

---

### Post by unter on 2010-07-03
> **nvteighen said:**
> You need a **for** loop, a construct very common in many programming languages: C, C++, Python, Java, Javascript, etc.

```

#include <iostream>

void a_function(int);

int main(void)
{
    int n = 8;
    int counter;

    /* for(do something at start; loop condition; do after each iteration) { }
     *
     * There are other ways to do the same, but this is by far the most common
     * you'll see in C and C++. The idea is to set a counter that's incremented
     * (++) after each iteration and keep looping till the condition is no
     * longer true. In the code below, counter will take values from 0 to 7,
     * enough to have your loop executed 8 times.
     */
    for(counter = 0; counter < n; counter++)
    {
        a_function(counter);
    }

    return 0;
}

void a_function(int number)
{
    std::cout << "Blah! Counter is: " << number << std::endl;
}

```Please, review some C++ reference.

ok yes i understand from your example. thank you.

---

### Post by unter on 2010-07-03
is nothing "built in" for c++ to do a repetition variable times or is always done to comparing with counter?

---

### Post by schauerlich on 2010-07-03
> **unter said:**
> is nothing "built in" for c++ to do a repetition variable times or is always done to comparing with counter?

Inside the for loop, you have can have any expression that can somehow be evaluated to true or false in the middle section. For instance, you could have a function that decides whether something is true or not, and the loop will only be entered if that function evaluates to true. Take this example:

```


#include <iostream>
 using namespace std;

bool isLessThanTwenty(int number) {
  if (number < 20)
    return true;
  else
    return false;
}

int main(void) {
  int max = 34;
  int i;

  for (i = 0; isLessThanTwenty(i); ++i)
    cout << i << " is less than 20" << endl;

  return 0;
}
```

This is obviously a fairly simple example. You could have /any/ function in there that can evaluate to true or false. You could even have a void function, as long as the entire expression evaluates to true or false.

---

### Post by nvteighen on 2010-07-04
> **unter said:**
> is nothing "built in" for c++ to do a repetition variable times or is always done to comparing with counter?

Hm... there are iterators for std::vector... that means, std::vector is able to do the loop on its own, but that's a bit beyond the scope of this thread I guess.

But yes, usually you use a counter because of the usual low-levelness of C and C++ programming. You're no longer in Ruby, where a lot was done for you behind the scenes :)

---

