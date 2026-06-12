---
title: "cannot open a file stream in C++"
date: 2008-03-05
forum: Programming Talk
---

### Post by Hits on 2008-03-05
```
#include <fstream>
#include <iostream>
#include <cstdlib>


using namespace std;


int main ()
{

ifstream fin;


fin.open("numbers.dat");

if (fin.fail()) //file open failsafe
{
	cout << "numbers.dat couldn't be opened. \n";
	exit(1);


return 0;
}
```

after  > g++ default.cpp
         > ./a.out

this simple program cannot create a file stream and I don't know what is causing this.  help ?

---

### Post by aks44 on 2008-03-05
ifstream means "input file stream" (ie. "read file").


If your goal is to open a non-existing file, use ofstream ("output file stream", ie. "write file").
Otherwise, make sure the file you're trying to read ("numbers.dat") already exists. It may help to specify the full path.

---

### Post by Wybiral on 2008-03-05
Also (not sure if this is related) but you're missing a closing bracket on your condition (but it shouldn't compile if that were the problem).

---

### Post by Hits on 2008-03-05
thanks for pointing it out, il try not to make such dumb threads in the future, i guess i need sleep

---

### Post by t3hi3x on 2008-03-05
> **Hits said:**
> thanks for pointing it out, il try not to make such dumb threads in the future, i guess i need sleep

No such thing as a dumb thread. It helps sometimes to just get a 3rd party to look at it.

Good luck with C++. It's a blast!

---

