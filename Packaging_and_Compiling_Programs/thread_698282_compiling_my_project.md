---
title: "compiling my project"
date: 2008-02-16
forum: Packaging and Compiling Programs
---

### Post by mouse5hi7 on 2008-02-16
How would i build my binomial program?
________________________________
binomial.h

#ifndef BINOMIAL_H
#define BINOMIAL_H

void init(binomial & B);
void init(binomial & B, int C1, int C2);
void input(istream & ins, binomial & B);
void output(ostream & outs, const binomial & B);
binomial sum(const binomial & B1, const binomial & B2);
binomial difference(const binomial & B1, const binomial & B2);

struct binomial
{
  int c1;        //coefficient of x
  int c2;        //constant coefficient
};

void init(binomial & B)
{
  B.c1 = 0;
  B.c2 = 0;
}

void init(binomial & B, int C1, int C2)
{
  B.c1 = C1;
  B.c2 = C2;
}

void input(istream & ins, binomial & B)
{
  cin >> B.c1;
  cin >> B.c2;
}

void output(ostream & outs, const binomial & B)
{
  cout << B.c1 << "x +" << B.c2;
}

binomial sum(const binomial & B1, const binomial & B2)
{
  binomial s;
  s.c1 = B1.c1 + B2.c1;
  s.c2 = B1.c2 + B2.c2;
  return(s);
}

binomial difference(const binomial & B1, const binomial & B2)
{
  binomial d;
  d.c1 = B1.c1 - B2.c1;
  d.c2 = B1.c2 - B2.c2;
  return(d);
}
#endif
_______________________

binomial.cpp

#include <iostream>
#include "binomial.h"
using namespace std;

int main()
{
  binomial b1, b2, b3;
  init(b1);
  init(b2);
  init(b3, 1, 2);
  output(cout, b3);
  cout << endl;
  input(cin, b1);
  input(cin, b2);
  b3 = sum(b1, b2);
  output(cout, b3);
  cout << endl;
  b3 = difference(b1, b2);
  output(cout, b3);
  cout << endl;
}
____________________
would it be  g++ binomial.cpp    or do i have to have the .h file in there?  NOTE:  My teacher told us to have the functions in our .h instead of a separate file for some reason.
 Thanks for your help.

---

### Post by hod139 on 2008-02-16
When posting code, you should put it inside
[ code ] code here [ /code ] 
(without the spaces inside the brackets)

To compile
```

g++ -Wall -obinomial binomial.cpp

```
THe -Wall flag will enable all warnings, and the -obinomial flag will name the executable binomial.  As for putting all the code inside of the header, that is rather strange.

---

### Post by mouse5hi7 on 2008-02-18
got my program to build w/ no errors, but it wont read in numbers from a file.  heres my input function

```

void input(istream & ins, binomial & B)
{
  char x;
  char sign;

  ins >> B.c1;
  ins >> x;
  ins >> sign;
  ins >> B.c2;
}

```

the char are to skip the "x+" in the binomial read in, so it will say something like 4x+10, and this function has to be able to get the 4 into the B.c1 struct and the 10 into the B.c2 struct.   I have to use these parameters too.  Plz help

---

