---
title: "A newbie is about to explode(c++)"
date: 2008-12-02
forum: Programming Talk
---

### Post by echo.whoami on 2008-12-02
I'm about to explode](*,)
this is the code. What should i put into the $$$$. I know is char something but WHAT...

```
#include<iostream>
#include<string>
using namespace std;

class employee
{
  private:
    char name[20];
    char id[5];
  public:
    employee($$$$$,$$$$$); //constructor
};

void main()
{
  employee em1($$$$$$,$$$$$$); //constructor
  .
  .
  .
}

employee::employee($$$$$$,$$$$$$$)
{
  strcpy(name,$$$$$$);
  strcpy(id,$$$$$$$);
}
```

i want just to use the overloaded constructor employee but how.

If you are really quit you'll be able to hear me (boom!!!)

---

### Post by dwhitney67 on 2008-12-02
Your member data (name and id) should be declared to be STL strings, not char arrays.  It's ironic that you declared the arrays, yet included <string>.

Your constructor should accept a string for each field.  The use of strcpy() is not needed.

---

### Post by jimi_hendrix on 2008-12-02
you would do

employee(int x, char* a,)
{
//stuff
}

then 

employee(char* a, char* b)
{
//stuff
}


thats how you overload stuff
(tell me if im crazy and wrong)

o ya and use strings...i was just lazy

---

