---
title: "(c++) passing i/o/fstream objects to a function"
date: 2007-11-04
forum: Programming Talk
---

### Post by NaSiO6 on 2007-11-04
hi!
how do i write a function to accept different i/o/fstream objects to input words into different files.
as in
void read(ifstream);

void read(ifstream fin)
{int a
fin>>a;
}

there can be logical work arounds to this(i could stop trying to use a function), but then i wanted to know just for knowledge sake.

thanks!

---

### Post by aks44 on 2007-11-04
Pass the parameter by reference:

```
void read(std::ifstream& fin)
{
  // whatever
}
``` (note the ampersand)


The result is the same as passing a pointer, except:
- the syntax is transparent (no need to dereference)
- you can hardly get it wrong

:)

---

### Post by JimmyBEng on 2007-11-04
you can pass stream objects as parameters, without a problem.  Just make sure you pass it by reference, you don't want to be making a copy of the stream object.

Example decalarations:
```
void readData(istream& dataIn);
void writeData(ostream& dataOut); 
```

---

### Post by NaSiO6 on 2007-11-07
hey!
thanks ppl!
it worked!

---

