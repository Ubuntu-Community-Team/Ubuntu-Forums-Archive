---
title: "gcc warning problem, strict aliasing"
date: 2009-10-25
forum: Programming Talk
---

### Post by MadCow108 on 2009-10-25
I'm currently trying to compile some foreign code on a newer gcc version (4.4.1)
I get following warning in code which reads a binary file:
```
tools/hist_draw.cc:128: error: dereferencing type-punned pointer will break strict-aliasing rules
```
in following code segment:
```
void
mystream::myget(float& f) { // mystream inherits from ifstream
  char c[4];
  get(c[0]);
  get(c[1]);
  get(c[2]);
  get(c[3]);
  f = *(float*)c; // line 128
}
```

I do not fully understand the error message yet, but changed the segment to this:
```
void
mystream::myget(float& f) {
  read(reinterpret_cast<char*>(&f),sizeof(float));
}
```
and the warning disappears.

The question is:
Have I fixed the problem or just outsmarted gcc's warning system?

(I could also remove the warning by introducing a temporary float pointer but that probably does not solve the reason but just takes gcc ability to detect the problem)

a yes no answer is enough, but an explanation or link to the reason of the problem would be nice too.

---

### Post by ibuclaw on 2009-10-25
Are you able to reproduce this on a small scale program example?

I can't seem to get the same message you are getting.

Regards
Iain

---

### Post by MadCow108 on 2009-10-25
here:
compile with -Wall -O2 in gcc 4.4.1 (I think it doesn't occur in gcc <= 4.3.3)
```
#include <iostream>
#include <fstream>

using namespace std;

void readfilewarning(ifstream & results, float &m)
{
//warning
  char c[4];
  results.get(c[0]);
  results.get(c[1]);
  results.get(c[2]);
  results.get(c[3]);
  m = *(float*)c;
  //nowarning
  //results.read(reinterpret_cast < char * > (&m), sizeof(m));
}

int main (int argc, char *argv[])
{
  ofstream file("numbers.dat",ios::binary);
  float x = 5.2342;
  file.write(reinterpret_cast<char *>(&x),sizeof(float));
  file.close();
  float m;
  ifstream results("numbers.dat",ios::binary);
  readfilewarning(results,m);
  std::cout << m << std::endl;
  return 0;
}
```

both versions seem to work, I just would like to make sure I really solved the warning issue

---

### Post by ibuclaw on 2009-10-25
Had a small look around, and it looks like that the reason you get that output is because the behaviour of how the line is interpreted at the optimisation stage of the compiler is generally undefined.

Adding **-fno-strict-aliasing** will hide the warning message.

Regards
Iain

---

### Post by MadCow108 on 2009-10-25
yes but it will also disable aliasing optimizations. Just disabling the warning with -Wno-strict-aliasing is also not wanted.

After some testing and reading I guess my solution is ok as the operation on type-punned pointers happen (if at all) in the (hopefully) safe standard library and not in my code.
If I'm wrong please say.

---

### Post by dribeas on 2009-10-25
For an interesting article on strict aliasing, follow this [link]("http://cellperformance.beyond3d.com/articles/2006/06/understanding-strict-aliasing.html"), it explains it and some of the consequences better than I could reproduce here.

At the end, the simplest solution to your particular problem is creating an union:

```

union binary_float
{
   char c[4];
   float f;
};

void readfilewarning(ifstream & results, float &m)
{
  union binary_float u;
  results.get(u.c[0]);
  results.get(u.c[1]);
  results.get(u.c[2]);
  results.get(u.c[3]);
  m = u.f;
}

```

---

### Post by MadCow108 on 2009-10-25
thanks for this nice article. It is very informative.

I don't actually need that char buffer, it was just some strange way it was implemented by someone else and in the article it says a cast to a char* is save so it should be fine.
So I'll stick with my solution.

Thank you for your help.

---

### Post by tmcg on 2009-12-11
If it is still of interest: If you'r strict even the union approach is not standard conforming since you write a char[] and read as float afterward.

On the other hand accessing any type as char (using a cast) is explicitly allowed. So your reinterpret_cast is the correct solution.

---

