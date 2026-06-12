---
title: "Problems with using gcc"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by zdog291 on 2008-07-12
okay so I am relatively new to Linux and am looking to use the gcc and g++ compilers for Linux to compile and run some basic c/c++ code. I have already "installed" gcc and g++ with sudo apt-get install but i run into a problem when trying to compile,
------------------------------
zachary@zachary-desktop:/media/sda2/zach/School Stuff/programs$ g++ bored.cpp -o bored.lnx
bored.cpp: In function ‘int main()’:
bored.cpp:8: error: ‘cout’ was not declared in this scope
bored.cpp:8: error: ‘endl’ was not declared in this scope
-----------------------
and heres the code I'm trying to compile 
-----------------------
//Zachary Hoeffner
//program for me to make something of when im bored

#include <iostream>

int main()
{
	cout << "hello world" << endl;
	return 0;
}
------------------------------

can anyone tell me why it is not getting cout and endl from Iostream or what is wrong with my code?

---

### Post by Bachstelze on 2008-07-12
The compiler itself is not the only thing required to compile. You also need the preprocessor, the standard libraries, and so on. The command

```
sudo apt-get install build-essential
```

will install it all for you.

---

### Post by zdog291 on 2008-07-12
> **HymnToLife said:**
> The compiler itself is not the only thing required to compile. You also need the preprocessor, the standard libraries, and so on. The command

```
sudo apt-get install build-essential
```

will install it all for you.


I have done this and still encounter the same problem

---

