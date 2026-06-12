---
title: "Question about dynamically allocated arrays in C++"
date: 2005-05-02
forum: Programming Talk
---

### Post by Merc248 on 2005-05-02
One thing that I thought was interesting was when my CS professor was showing us how to use GDB, where he exploits the fact that there is always a "0" right outside the bounds of a dynamically allocated integer array in order to prove a point in debugging a program.  For instance:

int *array = new int [5];
int a = array[5];

And now, a will be equal to 0.  My question to you guys is, why is this so in every single execution of the program?  I just thought it was extremely peculiar behavior that happens too often for it to be a coincidence...

---

### Post by Xerampelinae on 2005-05-02
> 
bren@itu:~/tmp$ cat test2.cpp
#include <iostream>
using namespace std;

int main(void)
{
        int *array = new int[5];
        int a = array[5];
        cout << a << endl;
}

bren@itu:~/tmp$ g++ test2.cpp
bren@itu:~/tmp$ ./a.out
135145
bren@itu:~/tmp$


random junk here so ubuntuforums doesn't reject my post

---

### Post by Merc248 on 2005-05-02
Weird... I actually get the same number on my end as well.  I also tried array[6] and it gives 0 every time the program is executed.  Same with new int[6] and array[6], it will produce 0 every execution.  Why is that?  Is it because it allocates the same portion of memory from the heap in every execution?

---

### Post by Xerampelinae on 2005-05-02
[QUOTE=Merc248]Weird... I actually get the same number on my end as well.  I also tried array[6] and it gives 0 every time the program is executed.  Same with new int[6] and array[6], it will produce 0 every execution.  Why is that?  Is it because it allocates the same portion of memory from the heap in every execution?[/QUOTE]
 I think you're right that it takes the same memory from the heap each time.  I guess you could make a for loop and repeatedly create new memory without freeing it to test..

---

