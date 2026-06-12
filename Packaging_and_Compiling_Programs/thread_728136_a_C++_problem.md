---
title: "a C++ problem"
date: 2008-03-18
forum: Packaging and Compiling Programs
---

### Post by babyboss on 2008-03-18
I have a few lines of code like the following:

template <typename DataType>
inline DataType Digraph<DataType>::data(int k) const{
           return myAdjacencyLists[k].data;
}

After I compiled it, the compiler keeps complaining "Error: expected initializer before '<' token " in the inline DataType line.

Thank you

---

### Post by meatpan on 2008-03-25
Can you provide some more context regarding your program?   List the include files, compilation command, etc....  Also, if you want a faster answer, consider posting in the 'Programming Talk' forum.

---

