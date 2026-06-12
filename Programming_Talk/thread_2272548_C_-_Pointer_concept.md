---
title: "C - Pointer concept?"
date: 2015-04-07
forum: Programming Talk
---

### Post by flaymond on 2015-04-07
Hello, I'm still confused about C/C++ pointers. Is a pointer, NULL or 0 ? Pointer is just a blank keyword without need for any malloc or memory for it? Pointer is not an actual variable right? Second, if pointer hold the memory of the pointed variable, will the pointer had the same memory size of the pointed variable? Asking this question is already confusing. Thanks for helping.

---

### Post by Matthew_Harrop on 2015-04-07
I am under the impression that the pointer is just an address to the variable. I.E it points to the variable. Its of a fixed size and (Since its just a memory address) smaller than the variable it points to. If you print a pointer you'll get the hex address of the memory location it points to.

They are there to reduce the memory footprint of a c program.

---

### Post by ofnuts on 2015-04-07
A pointer is a variable, because 1) it takes some space in memory, and 2) you can change its contents (make it points to something else). The memory size of the pointer is the size of the pointer type, not the size of whatever it points to. On 32-bit machines it's 32 bits, and on 64-bit machines it's 64-bit.

Using pointers is more or less like calling people by their role instead of their names. In your town you can call the mayor. If s/he isn't reelected, you will still call the mayor, who will happen to be a different person. "Mayor" behave likes a pointer variable, that has been pointing to "Ann Haydon-Jones" (before elections) and then points to "Engelbert Humperdinck" (after elections).

---

### Post by Rocket2DMn on 2015-04-08
In C/C++, when you declare a pointer without assigning anything to it, it can have a garbage value, which is dangerous.  If you try to check it for NULL, that check could fail, and then trying to access if could produce a segmentation fault.  You need to explicitly set an unassigned pointer to NULL in order to safely check it before trying to access it.  NULL and 0 are interpreted as the same in C/C++, though I always prefer to be explicit when using pointers and check NULL instead of 0.

---

### Post by flaymond on 2015-04-09
Thanks for help! :D

---

