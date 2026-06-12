---
title: "Compiling a hello world program c++"
date: 2008-07-09
forum: Packaging and Compiling Programs
---

### Post by revenge2 on 2008-07-09
Hey guys im wondering how i would go about compiling a .cpp file using the terminal?

```
is it the same for linux as in windows?
/*Hello.cpp*/
#include <iostream>
using namespace std;
int main()
{
  cout<<"hello world!";
  return 0;
}
```

this is the .cpp file i want to compile. How would i do this?

-thanksa

---

### Post by lisati on 2008-07-09
If you named the file "hello.cpp", the relevant command is```
g++ hello.cpp -o hello
```To run the program once it has compiled, type:```
./hello
```
If you haven't already done so, you might need to run the following first:```
sudo apt-get build-essential
```

---

