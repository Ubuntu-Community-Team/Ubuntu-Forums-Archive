---
title: "Simple C++ Not Compiling"
date: 2010-05-03
forum: Programming Talk
---

### Post by dmp1ce on 2010-05-03
Here is my code:
```
#include <iostream>

int main()
{
  std::cout << "Hello World!" << std::endl;
  return 0;
}
``````
CPP = g++
CPP_OPTIONS = -Wall

all:
    $(CPP) $(CPP_OPTIONS) -o test main.cpp

clean:
    rm test
``````
make
g++ -Wall -o test main.cpp
main.cpp: In function &#8216;int main()&#8217;:
main.cpp:5: error: &#8216;cout&#8217; is not a member of &#8216;std&#8217;
main.cpp:5: error: &#8216;endl&#8217; is not a member of &#8216;std&#8217;
make: *** [all] Error 1

```What is going on here?  Is this a problem with my setup?

---

### Post by roelpeeters on 2010-05-03
Hi,

As a fellow C++ programmer, I hate to ask these questions, but sometimes the problem is obvious:

1. Did you save your main.cpp?
2. Are you in the same directory as the source of the main.cpp you showed us?

HTH
Roel

---

### Post by dmp1ce on 2010-05-03
Yes and Yes.

BTW, when I was installing g++ today my computer shutdown because I think it overheated.  I had to reinstall the package.  I don't know if this could cause a problem with the setup.

---

### Post by dwhitney67 on 2010-05-03
Hopefully what you installed is the 'build-essential' package:
```

sudo apt-get install build-essential

```
As for your code, it is syntactically correct.

---

### Post by dmp1ce on 2010-05-03
I removed libstdc++6-4.4-dev using the Synaptic Package Manager and then I ran the command

```
sudo apt-get install build-essential
```and it works now.  Thank you! :D

---

