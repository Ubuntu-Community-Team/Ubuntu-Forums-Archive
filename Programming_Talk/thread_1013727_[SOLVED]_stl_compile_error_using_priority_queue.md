---
title: "[SOLVED] stl compile error using priority_queue"
date: 2008-12-17
forum: Programming Talk
---

### Post by Cygnus on 2008-12-17
At [http://www.cplusplus.com/reference/stl/priority_queue/priority_queue.html](http://www.cplusplus.com/reference/stl/priority_queue/priority_queue.html) you can find the following example code for creating some priority_queues:

[PHP]
// constructing priority queues
#include <iostream>
#include <queue>
using namespace std;

class mycomparison
{
  bool reverse;
public:
  mycomparison(const bool& revparam=false)
    {reverse=revparam;}
  bool operator() (const int& lhs, const int&rhs) const
  {
    if (reverse) return (lhs>rhs);
    else return (lhs<rhs);
  }
};

int main ()
{
  int myints[]= {10,60,50,20};

  priority_queue<int> first;
  priority_queue<int> second (myints,myints+3);
  priority_queue< int, vector<int>, greater<int> > third (myints,myints+3);

  // using mycomparison:
  priority_queue< int, vector<int>, mycomparison > fourth;

  typedef priority_queue<int,vector<int>,mycomparison> mypq_type;
  mypq_type fifth (mycomparison());
  mypq_type sixth (mycomparison(true));

  return 0;
}
[/PHP]

However if I try to use the queue with the name fifth I get a compile error. For example just try to add fifth.push(5) before the return statement.

The error is:

[PHP]
error: request for member 'push' in 'fifth', which is of non-class type 'main()::mypq_type ()(mycomparison (*)())'
[/PHP]

I have the same problem in my code and it was after that I found this example code at cplusplus.com that seem to have the same problem. It seem to think that it is a function declaration and not a new variable on the stack, is the syntax incorrect, or is the compiler confused ?

---

### Post by Zugzwang on 2008-12-17
Compiles fine here (when changing the line in which you define fifth to "mypq_type fifth (mycomparison(false));". Don't use empty braces as these have some special meaning (However, I don't know which).

---

### Post by Cygnus on 2008-12-17
> **Zugzwang said:**
> Compiles fine here (when changing the line in which you define fifth to "mypq_type fifth (mycomparison(false));". Don't use empty braces as these have some special meaning (However, I don't know which).

I have tried g++ 4.2, 4.1 and 3.4 on kubuntu and debian with the same result.

And yes it is fine if you use false and not the empty braces, but it does not work either if you use a variable. For example bool b = false, and then put b inside the braces.

---

### Post by dribeas on 2008-12-17
The simple solution is enclosing the parameter in parenthesis:

```

   mypq_type fifth ((mycomparison()));

```

And now the problem you had: the parser is mistakenly assuming that fifth is the declaration of a function and not a variable. In fact it is assuming that mycomparison() is the declaration of an unnamed function taking no arguments and returning a mycomparison object. That is used as parameter type for the declaration of a second function that returns a mypq_type and is called fifth.

Adding the extra parenthesis breaks the ambiguity for the compiler, as parameters cannot be defined inside the extra parenthesis, so that fifth cannot be a function declaration.

This is why C++ is not for the faint of heart :)

(See the explanation in [C++Faq lite 10.19]("http://www.parashift.com/c++-faq-lite/ctors.html#faq-10.19"))

---

### Post by Cygnus on 2008-12-17
> **dribeas said:**
> The simple solution is enclosing the parameter in parenthesis:

Ah thanks, I had a feeling that was the problem as I now recall to have read about this ages ago. I did not remember that parantheses was the solution. Thanks alot :)

---

