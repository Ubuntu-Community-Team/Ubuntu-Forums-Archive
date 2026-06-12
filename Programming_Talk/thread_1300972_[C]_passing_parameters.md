---
title: "[C] passing parameters"
date: 2009-10-25
forum: Programming Talk
---

### Post by hechizera on 2009-10-25
.

---

### Post by MadCow108 on 2009-10-25
you can only pass by value in C. pass by reference/address is handled by passing a pointer (=address) by value
```

int func(int i) // by value, i is a local variable!
{
  a=6; // no change local variable, no influence on the variable passed in call
  printf("%d\n",i);
}
int func2(int * i) // by reference/address (= pass of pointer by value)
{
   *i = 6; // change value pointed to by i to 6 by use of the dereferencing operator
}
int func3(const int * i) // by reference/address of const value
{
  if (*i == 5) { // read value pointed to by i
    *i = 6; // // ERROR, i points to a read only location
    int * b = (int*) i; // remove constness (!!this usually means logic error! you should practically never need do this!!)
    *b = 6; // now you can change value pointed to by i;
  }
}
...
int a = 5;
func(a); // pass a by value = func cannot manipulate the a in this scope;
func2(&a);  // pass a by reference , func can manipulate a in this scope
func3(&a);  // pass a by reference , func will not manipulate a if programmers don't mess up

```

what do you mean with by name and by result?

---

### Post by Can+~ on 2009-10-25
Sounds like homework.

---

### Post by hechizera on 2009-10-25
.

---

### Post by hechizera on 2009-10-25
.

---

### Post by MadCow108 on 2009-10-25
its not possible
everything is passed by value in C even references/pointers
its impossible to write something more than a trivial C program without pointers, they are sort of the foundation of the language

pass by result is the same as passing a non const pointer see func2 in above example
I still don't understand what you mean by name

---

### Post by hechizera on 2009-10-25
.

---

### Post by Arndt on 2009-10-25
> **MadCow108 said:**
> its not possible
everything is passed by value in C even references/pointers
its impossible to write something more than a trivial C program without pointers, they are sort of the foundation of the language

pass by result is the same as passing a non const pointer see func2 in above example
I still don't understand what you mean by name

Simula has argument passing by name. There, it means a function closure, more or less.

---

### Post by MadCow108 on 2009-10-25
you can only remove the pointers with global variables. but these are considered bad style in most cases.
Just use pointers.

Anyway the code you wrote does not work, better go over the basics of C again.


if pass by name means closures, then again not possible with basic syntax. Standard C has no closures.

---

### Post by hechizera on 2009-10-25
.

---

### Post by dwhitney67 on 2009-10-25
> **hechizera said:**
> the code I wrote works if the library #include <stdio.h> is attached at the beginning. Unfortunately, I cannot use pointers :(

Please define what you mean by "works".  The check() function manipulates the global variable 'i', and as for the other parameters, well these are all local to the function.  You can modify them all day long, but it won't change the values used where check() was called.

> 
P.S. ah, and also if the file is saved with .c extension. for me it works fine, strange that for you doesn't..

For this I have no idea what you a referring to; typically C source code is saved in files with a .c extension; header files, while typically only for function declarations, end with a .h extension.

---

### Post by MadCow108 on 2009-10-25
I didn't mean it does not compile, only it probably does not do what you want
e.g.
```

void check(int x, int y, int z) {
i++;
z = z + y;
y = y*y;
x = x + 2;
}
```

the three lines after i++ are completely useless as they change local variables which get deleted when the function ends.
you could make a structure which holds all three values and return that by value or make three functions with three integer return values

---

### Post by hechizera on 2009-10-25
.

---

### Post by MadCow108 on 2009-10-25
```

struct data {
 int x;
 int y;
 int z;
 double value;
};

struct data funct(struct data dat) //pass by value, may be slow if the struct is huge, in that case use const pointer
{
  dat.x = dat.x -2;
  dat.y += 2;
  return dat;
}

int main(void) {
  struct data bla = {1,2,3,1.5}; // initialise;
  struct data new_bla = funct(bla); // new_bla now holds a modified (by funct) copy of bla, bla is still in the same state as before
  printf("%d\n",new_bla.x);
}

```

for details -> google

---

### Post by hechizera on 2009-10-25
.

---

### Post by dwhitney67 on 2009-10-25
> **hechizera said:**
> the compiler says that there's a mistake here
```
struct data funct(struct data dat)
```

P.S.what an awful exercise, if it would be with arrays I would have it working perfectly..:(

That code is fine except that it is missing the include statement for <stdio.h>.

---

### Post by hechizera on 2009-10-25
.

---

### Post by MadCow108 on 2009-10-25
by address you just pass the pointer to the struct:
```

void funct(struct data * dat) //pass by address by value, function now modifies the memory pointed to by dat
// and does not need a return value (but it can have one for e.g. error handling)
{
  dat.x = dat.x -2;
  dat.y += 2;
}

int main(void) {
  struct data bla = {1,2,3,1.5}; // initialise;
  funct(&bla); // pass pointer to bla, now bla itself is modified and not a copy!
  printf("%d\n",bla.x);
  return 1;
}

```
this is what I understand is pass by result.
I would consider pass by adress a pass of a const pointer (funtc(const struct data * dat)) which means the function needs a return value again to have an effect.
Again: C only has a single pass method: pass by value
this is unlike higher languages which usually have various methods (but which are internally mostly again passes by value of memory addresses)

---

### Post by hechizera on 2009-10-25
thanks!

---

### Post by nvteighen on 2009-10-26
> **hechizera said:**
> thanks!
Don't delete your posts... They can be useful to people experiencing the same troubles. Don't be ashamed from your mistakes, but learn from them and help people learn from them too ;)

---

### Post by Arndt on 2009-10-26
> **hechizera said:**
> .

Why this habit of empty postings?

---

### Post by John Bean on 2009-10-26
> **Arndt said:**
> Why this habit of empty postings?
They were not originally empty; the OP has later chosen for some reason to edit them all to nothing.

It makes a mockery of the whole thread which now may as well be removed. Kids: don't you just love 'em? ;-)

---

