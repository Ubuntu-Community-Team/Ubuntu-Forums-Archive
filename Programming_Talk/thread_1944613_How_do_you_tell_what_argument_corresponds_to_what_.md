---
title: "How do you tell what argument corresponds to what operand in C++ operator overloading"
date: 2012-03-21
forum: Programming Talk
---

### Post by venom104 on 2012-03-21
Here is an example assignment that I did for my C++ class.

[http://pastebin.com/XpKXKR9w](http://pastebin.com/XpKXKR9w)

I have a few questions on how stuff works

For example, in the function

friend String1 operator+(char * newStr, String1 &oldStr);

How can I tell what operand would be on what side of the + operator? It could be charstring + String1 or it could be String1 + charString. My function doesn't work for both cases, what the heck is the difference?

The same question in the function
  friend ostream &operator<<(ostream & output, const String1 & oStr);

How can I tell what operand correponds to the operator...

Obviously the code has to go like this cout << string1 object. So does operator overloading always follow a linear path (EG the first operand is the one on the LEFT hand side?)

Please advise me

---

### Post by cgroza on 2012-03-21
Are you getting error messages regarding the operators?
If so, please post them here in code tags.

---

### Post by CynicRus on 2012-03-22
[http://en.wikibooks.org/wiki/C++_Programming/Operators/Operator_Overloading](http://en.wikibooks.org/wiki/C++_Programming/Operators/Operator_Overloading)

---

