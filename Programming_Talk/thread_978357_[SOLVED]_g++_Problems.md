---
title: "[SOLVED] g++ Problems"
date: 2008-11-11
forum: Programming Talk
---

### Post by Primefalcon on 2008-11-11
I seem to be having weird problem

I have the following real simple c++ program

```
#include <iostream.h>
using namespace std;

int main()
{
cout << "testing";

return 0;
}
```

which shouldn't be a problem.....

yet

primefalcon@BlackBeard:~/Desktop/testing$ g++ program.cpp -o program
primefalcon@BlackBeard:~/Desktop/testing$ ./program
primefalcon@BlackBeard:~/Desktop/testing$ 

obviously something weird is going on I tried reinstall g++ but with no luck.

I am using Ubuntu 8.04.

I am not sure what to look into to fix this problem either the compiler is having a problem or I am having a problem running the program not sure which.

Any help would be appreciated thank you

---

### Post by lisati on 2008-11-11
One thing to check is if the "build-essential" package is installed. You can do this by entering the following in the terminal:
```
sudo apt-get build-essential
```

---

### Post by Primefalcon on 2008-11-11
I've tried reinstalling the compiler no luck there either

---

### Post by Primefalcon on 2008-11-11
I already do have that installed though I just tried reinstalled the build-essential pack, no luck.....

---

### Post by Primefalcon on 2008-11-11
anyone?

---

### Post by namegame on 2008-11-11
I'm not sure if this is the exact problem, but instead of:

#include <iostream.h>

try this:

#include <iostream>

---

### Post by Primefalcon on 2008-11-11
unfrotunately no that's what i had originaly.... :-( it says I have both of those lib files though

---

### Post by Primefalcon on 2008-11-11
Ok I've tested old c++ programs I had compiled and they work, so its the gnu c++ compiler that isn't working for sure

---

### Post by dmizer on 2008-11-11
Moved to Programming talk. People here will be more likely to help you.

Please refrain from bumping your post so frequently. You will still receive help even if your post has dropped off the front page. If you have not received a reply within 24 hours, please feel free to bump. If you need more speedy help, please try using the IRC channel instead. 

Thank you.

---

### Post by Primefalcon on 2008-11-11
I apologize I just needed this work pretty urgently....

though I have one tiny issue the bloody thing just started working now, I didn't do anything to fix it.....

---

### Post by Bichromat on 2008-11-11
> **Primefalcon said:**
> I seem to be having weird problem

I have the following real simple c++ program

```
#include <iostream.h>
using namespace std;

int main()
{
cout << "testing";

return 0;
}
```


You didn't end the line with "\n" or endl. Maybe you program doesn't flush the output as a consequence.

---

### Post by dwhitney67 on 2008-11-11
> **Bichromat said:**
> You didn't end the line with "\n" or endl. Maybe you program doesn't flush the output as a consequence.

+1.

Also, the program will not compile unless the .h is removed from the #include <iostream> statement.


```

$ g++ program.cpp 
program.cpp:1:22: error: iostream.h: No such file or directory
program.cpp: In function ‘int main()’:
program.cpp:8: error: ‘cout’ was not declared in this scope

```

---

