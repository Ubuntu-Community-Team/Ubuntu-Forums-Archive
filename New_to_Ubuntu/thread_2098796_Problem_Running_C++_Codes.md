---
title: "Problem Running C++ Codes"
date: 2012-12-27
forum: New to Ubuntu
---

### Post by BlindSoothsayer on 2012-12-27
Hello all,

I am trying to get started using c++ on Ubuntu 12.10.  I saved the following code as "first.cpp"

```
#include <iostream>

int main()
{
    std::cout << "Hello world!\n";
    return 0;
}
```

After navigating to the appropriate directory in the terminal, I compile it using the following command:

```
g++ first.cpp -o first
```

This of course creates a compiled executable named "first", which I would run by typing "first".  However, I get the following error message:

```
The program 'first' is currently not installed. You can install it by typing:
sudo apt-get install yagiuda
```

What have I done wrong?  Thank you in advance.

---

### Post by LuisGMarine on 2012-12-27
[http://askubuntu.com/questions/36520/how-could-i-begin-c-programming-on-ubuntu]("http://askubuntu.com/questions/36520/how-could-i-begin-c-programming-on-ubuntu")

I think this might actually help you.

I think you have to run it by typing:

```
./first
```

---

### Post by steeldriver on 2012-12-27
it's because the current directory is not part of your executable search path - to execute a file called 'first' in the current directory you need

```
**./**first
```

---

