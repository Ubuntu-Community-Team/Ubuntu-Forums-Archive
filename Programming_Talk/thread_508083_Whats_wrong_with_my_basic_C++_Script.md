---
title: "Whats wrong with my basic C++ Script"
date: 2007-07-23
forum: Programming Talk
---

### Post by eldara5 on 2007-07-23
Well just for a little fun i make a simple C++ script and it has gone wrong i get the following errors:-
```

c.cpp:18: error: ISO C++ forbids comparison between pointer and integer
c.cpp:24: error: statement cannot resolve address of overloaded function

```

I cannot understand what they mean so i cannot fix them? Here is the code

```

#include <iostream>

using namespace std;

int main()
{ 
 int a;
  cout<<"Starting Program/n";
  sleep(10);
  cout<<"Running Program.....";
  cout<<"Press Enter to Begin";
  cin.get();
  cout<<"would you like to Add a user or login?";
  cin>> a;
  cin.ignore();
 
 
 if ( a == "add" )
  {
   cout<<"Starting add user";
   cin.get();
   cout<<"Program is still under construction, we apologise for this";
   cout<<"ERROR: CANNOT PROCEED, CLICK ENTER TO TERMINATE";
   cin.get;
  }


 else 
  {
   cout<<"Starting Login Server, please wait";
   sleep(10);
   cout<<"Sorry this program is under construction";
   cout<<"ERROR: CANNOT PROCEED, CLICK ENTER TO TERMINATE";
  return 1;
  }
}

```

Now im a n00b at C++ so ive no idea whats gone wrong, and if somone could give any help ill be greatful (and please explain whats wrong and why its wrong rather than posting the soluton so ill know for next time)

Thanks in advance,
Eldara

---

### Post by xtacocorex on 2007-07-23
From just looking at the code, you're trying to set a string to an int. 

a == "add" when you declare a as an int, not a string.

I would change:
```
int a;
```
with
```
string a;
```

---

### Post by eldara5 on 2007-07-23
See im a n00b I didnt even see it, Thanks

Anyone know why im getting

```

error: statement cannot resolve address of overloaded function

```

Eldara

---

### Post by Wybiral on 2007-07-23
> **eldara5 said:**
> See im a n00b I didnt even see it, Thanks

Anyone know why im getting

```

error: statement cannot resolve address of overloaded function

```

Eldara

Yes, it's line 24... You don't have parenthesis on your call to the last cin.get() function.

You should always take note of the line number that the compiler gives you with errors and warnings.

BTW, C++ is compiled. It's not usually called a script, it's just source code.

---

