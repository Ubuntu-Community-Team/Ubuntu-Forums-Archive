---
title: "c++ simple array allocation"
date: 2007-01-14
forum: Programming Talk
---

### Post by monkeyking on 2007-01-14
The following progrom shouldn't work, but it does.
Could anyone please explain why it doesn't segfault?
```

#include<iostream>
using namespace std;

int main(){

  int tmp[2]; 

  for (int i=0;i<5; i++)
    tmp[i]=i; 

  for (int i=0;i<5;i++{
    cout << "tmp["<<i<<"i]"<<tmp[i] <<endl;
  }
}

```

The problem shoud clearly be that I'm only alloc'ing for 2 elements in tmp.
So how is it possible for me to access and use the rest.

Thanks in advance

---

### Post by thumper on 2007-01-14
It works due to C++ not checking array bounds for simple arrays.

You have allocated two ints on the stack.  It depends on the stack size that is used by default.  It could just be that your program is so simple that there is nothing else to stomp on.

Just don't do it.  Its like me handing you a sharp knife, you then stabbing yourself on purpose and complaining "why did this knife let me hurt myself?".

---

### Post by Wybiral on 2007-01-14
Yeah... Memory is just memory. It's always there. The thing you have to worry about is that you have no idea what you're writing over or reading. But, when you stay in bounds, the compiler will allocate that space safely...

Eventually you will either mess up a process or you will segfault.

Like thumper said, "Just don't do it"

---

### Post by monkeyking on 2007-01-14
Kewl,
Thanks for the fast answer.

---

### Post by Bobtheknight on 2007-01-14
Think about it this way, when you allocate space for variables, the compiler/kernel (computer) give you the necessary space, so by declaring other variables and allocating more memory compiler/kernel make sure it doesn't go into the memory you originally declared.
When you go into unallocated space, you might be writing into memory that's reserved for other variable, thus erasing its data.  Later, Kernel/compiler might write over your original data, thus erasing data from your array, or if you happen to write into the return address of your program then... ho ho, a buffer overflow hack.

Well anyway, the reason your program work right now because you don't have any variable after it (so you didn't overwrite anything), and by luck the memory you used to write the array does not contain anything important.  The print out command doesn't check anything either, it just prints anything you tell it to.  So if you say println temp[7] it will probably give you the data that is stored 7 spaces in front of temp[0].  Although the data will probably be garbage.

---

