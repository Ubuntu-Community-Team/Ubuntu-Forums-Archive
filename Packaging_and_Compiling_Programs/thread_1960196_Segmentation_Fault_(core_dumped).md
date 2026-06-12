---
title: "Segmentation Fault (core dumped)"
date: 2012-04-16
forum: Packaging and Compiling Programs
---

### Post by bjustice54 on 2012-04-16
Okay well I'm not to advanced at C++, its only my 2 quarter in college  taking Computer Science so please don't say anything that will go  straight over my head haha.  Well the code I have compiles just fine but  when I got to run it I'm getting this seg fault error and I'm pretty  sure it has something to do with the pointers in my code, if someone  could just look at it and help me out id appropriate it. I dont know how to use a debugger at all either and I dont really have the time to learn at the moment.   Thanks
So what this code is trying to do is read a .dat file that has 3 columns  the first two are numbers that represent cities and the third is the  cost of a cable that is connected between them.  It will read the file  and then find the cheapest cost that has all cities connected some way  or form.
My Code:


```
#include <iostream>
#include <time.h>
#include <string>
#include <fstream>
#include <stdlib.h>
#include <stdio.h>
using namespace std;

class Cable{ public: int city1, city2, cost; bool solution; };

int costcompare(const void *x, const void *y) {
  if ((**(Cable **)x).cost < (**(Cable**)y).cost) return -1;
  if ((**(Cable **)x).cost > (**(Cable**)y).cost) return 1;
  return 0;
}

class Solver {
  Cable **cables;
  int ncables;
  int ncities;
  int *group;
  Cable **argv;
  int sum;
  int dummy;
  string buffer;
  fstream *fin;

public:
  //constructor
  Solver() {
    this->ncables = ncables;
    this->ncities = ncities;
    this->sum = sum;
    this->dummy = dummy;
    this->buffer = buffer;
    this->cables = cables;
    this->group = group;
    this->fin = fin;
    this->argv = argv;
    }

  //reads the file from main
  void readFile(char **argv) {
    fstream *fin = new fstream(argv[1], ios::in);
    if (fin->fail()) {
      cerr << "Cannot open file " << argv[1] << "\n";
      exit(0);
    } 

    while (getline(*fin, buffer)) ncables++;
    fin->close();
    fin->clear();

    Cable **cables = new Cable*[ncables];

    int sum = 0;
    fin->open(argv[1], ios::in);
    for (int i = 0; i < ncables; i++) {
      cables[i] = new Cable();
      *fin >> cables[i]->city1>> cables[i]->city2 >> cables[i]->cost;
      sum += cables[i]->cost;
    }
    fin->close();
    fin->clear();
  }

  // Finds the number of cities
  void  findNcity () {
    int ncities = 0;
    for (int i=0; i < ncables; i++) {
      if (cables[i]->city1 > ncities) ncities = cables[i]->city1;
      if (cables[i]->city2 > ncities) ncities = cables[i]->city2;
      }
  }

  //gives the group their numbers
  void giveGroupnum() {
    int *group = new int[ncities + 1];
    for (int i=0; i <= ncities; i++) group[i] = i;
  }

  //the cycle
  bool isCycle(Cable *cable) {
    if (group[cable->city1] == group[cable->city2]) return false;
    int dummy = group[cable->city2];
    for (int i = 0; i <= ncities; i++)
      if (group[i] == dummy) group[i] = group[cable->city1];
    return true;
  }


  //Solves the problem
  void solve() {
    qsort(cables, ncables, sizeof(Cable*), costcompare);
    for (int i=0; i < ncables; i++) {
      if (isCycle(cables[i])) cables[i]->solution = true;
      else cables[i]->solution = false;
    }
    for (int i=0; i < ncables; i++){
      if (cables[i]->solution == true) 
    cout << i << ": " << cables[i]->city1 << " "
         << cables[i]->city2 << " "
         << cables[i]->cost << "\n"; }
  }

};

int main(int argc, char **argv)
{
  if (argc != 2) {
    cout << "\nUsage: " << argv[0] << " \n";
    exit (0);
  }

  Solver mysolver;

  mysolver.readFile (argv);
  mysolver.findNcity ();
  mysolver.giveGroupnum();
  mysolver.solve();
  return 0;
}
```

---

### Post by SevenMachines on 2012-04-17
I'd suppose you didnt mean to do this
```
 Solver() {
// this is Solvers member variable 'cables'
    this->cables = cables;
}
``` ```
void readFile(char **argv) {
// here you declare a new, local variable called cables, you are *not*
//using Solvers member version, ie cables = new Cable*[ncables];
    Cable **cables = new Cable*[ncables];
```Similarly with the group variable.

> I dont know how to use a debugger at all either and I dont really have the time to learn at the moment.It's the most important tool you'll use in c++ after the compiler itself, it's pretty much essential. If you don't want to use gdb from the command line try graphical interfaces to it such as nemiver or ddd. If you're using a IDE then chances are it'll have an easier to use integrated interface to gdb. In either case, you need to learn the basics at least of debugging, it's an essential part of programming.

---

### Post by SevenMachines on 2012-04-17
Just a quick note, this sort of thing is probably better off in the [programming forum]("http://ubuntuforums.org/forumdisplay.php?f=39")

---

### Post by bjustice54 on 2012-04-17
Ok so I think i made sure I didnt declare them all again and it compiled but I i came up as 

```
terminate called after throwing an instance of 'std::bad_alloc'
  what():  std::bad_alloc
Aborted (core dumped)
```

---

### Post by bjustice54 on 2012-04-17
I take that back , im getting a seg fault again.  I know a debugger is important but we have yet to do anything with them in school, and I cant seem to figure out how to use them.

---

### Post by SevenMachines on 2012-04-17
You would need to post your new failing code because when I make the changes below, it doesnt segfault here
```
--- test.cpp.orig 2012-04-17 17:21:26.844025815 +0100
+++ test.cpp  2012-04-17 17:21:18.692026018 +0100
@@ -47,11 +47,12 @@
       exit(0);
     }

+   ncables = 0;
     while (getline(*fin, buffer)) ncables++;
     fin->close();
     fin->clear();

-    Cable **cables = new Cable*[ncables];
+    cables = new Cable*[ncables];

     int sum = 0;
     fin->open(argv[1], ios::in);
@@ -75,7 +76,7 @@

   //gives the group their numbers
   void giveGroupnum() {
-    int *group = new int[ncities + 1];
+    group = new int[ncities + 1];
     for (int i=0; i <= ncities; i++) group[i] = i;
   }

```
Note, I've added ncables initialisation to 0. There may be other issues but it should at least run through

---

