---
title: "C++ Template Confusion"
date: 2009-04-05
forum: Programming Talk
---

### Post by tdrusk on 2009-04-05
I am working with [this]("http://pastebin.com/d3af640c2") program. When I subtract Person g from Person h I get a garbage number. I'm not sure what I'm doing wrong. Any ideas?

---

### Post by dwhitney67 on 2009-04-05
The main problem with the code is in the Person::operator-() method.  In the way you have defined it, it will have the capability to operate on the 'this' object.  I suspect from the code in the main() function this is not what you want; instead you want to operate on two unique objects.  This requires a friend function.

When passing objects in C++, always pass by reference unless you have a compelling reason not to.  Currently you are passing your object by value, and thus a copy of the object is being made when necessary.  This slows down performance, and can lead to errors should the object have allocated data members.  Also, if you have no plans to modify the object, then declare it as const.

So, with that in mind, here's how the Person::operator-() probably should be declared/implemented:
```

class Person
{
  ...
  friend Person operator-(const Person& p1, const Person& p2);
};

Person operator-(const Person& p1, const Person& p2)
{
   Person temp;

   temp.lastName  = "Difference";
   temp.firstName = "Age";
   temp.age       = std::abs(p1.age - p2.age);

   return temp;
}

```

P.S.  When you post code on a 3rd party website such as you have, it makes it difficult for anyone to copy the code into their own terminal to test your program.  Personally I did not have the luxury of time to enter your code by hand, or remove every # mark that shows up when I attempted to copy/paste it, so the code I posted above has not been tested/compiled.

---

### Post by tdrusk on 2009-04-05
> **dwhitney67 said:**
> The main problem with the code is in the Person::operator-() method.  In the way you have defined it, it will have the capability to operate on the 'this' object.  I suspect from the code in the main() function this is not what you want; instead you want to operate on two unique objects.  This requires a friend function.

When passing objects in C++, always pass by reference unless you have a compelling reason not to.  Currently you are passing your object by value, and thus a copy of the object is being made when necessary.  This slows down performance, and can lead to errors should the object have allocated data members.  Also, if you have no plans to modify the object, then declare it as const.

So, with that in mind, here's how the Person::operator-() probably should be declared/implemented:
```

class Person
{
  ...
  friend Person operator-(const Person& p1, const Person& p2);
};

Person operator-(const Person& p1, const Person& p2)
{
   Person temp;

   temp.lastName  = "Difference";
   temp.firstName = "Age";
   temp.age       = std::abs(p1.age - p2.age);

   return temp;
}

```P.S.  When you post code on a 3rd party website such as you have, it makes it difficult for anyone to copy the code into their own terminal to test your program.  Personally I did not have the luxury of time to enter your code by hand, or remove every # mark that shows up when I attempted to copy/paste it, so the code I posted above has not been tested/compiled.

Oh okay thanks. The only reason I did that was because I don't like the code to be displayed at all times, and pastebin deletes it after one day. I'll remember that though. 
Also, pastebin has a download link which allows you to download the code. I can understand how copy and paste is easier in some situations(such as this one)

---

