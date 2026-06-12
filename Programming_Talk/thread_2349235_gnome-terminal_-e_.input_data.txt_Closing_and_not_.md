---
title: "gnome-terminal -e ./input data.txt Closing and not running the program"
date: 2017-01-12
forum: Programming Talk
---

### Post by slavano on 2017-01-12
Hello,

I am trying to write a CPP program to open a new gnome-terminal and run the program I wrote called input with command line argument data.txt. input works perfectly when run by its self. When I run my main it successfully opens a new terminal and runs input. input then asks me for how long to run the serial connection for, like it is supposed to, but then closes without reading in from the serial port. this only happens when using main. 

main code
```

#include <stdlib.h>


using namespace std;


int main()
{
  system("gnome-terminal -e ./input data.txt");
  system("./run.sh");
  return 0;
}



```

Any thoughts on why this is and how to fix it?

p.s. sorry about the messy code.

---

