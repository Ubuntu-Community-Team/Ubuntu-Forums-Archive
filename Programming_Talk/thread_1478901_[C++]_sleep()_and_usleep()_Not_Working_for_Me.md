---
title: "[C++] sleep() and usleep() Not Working for Me"
date: 2010-05-10
forum: Programming Talk
---

### Post by dodle on 2010-05-10
I've been trying to figure out how to get my program to pause for a second or two.  I've found [color=red]sleep[/color]() and [color=red]usleep[/color](), but neither are working as they have been explained to do.  

These are a couple of locations I got my information from:
[http://ubuntuforums.org/showthread.php?t=1425188&highlight=sleep](http://ubuntuforums.org/showthread.php?t=1425188&highlight=sleep)
[http://www.dreamincode.net/forums/topic/16391-sleep-command-in-c/](http://www.dreamincode.net/forums/topic/16391-sleep-command-in-c/)

The program should first print out "Hello ", wait 2 seconds then print out "World".  But "Hello World" is printed out all at once after a 2 second pause:

Using [color=red]sleep[/color]()
[php]#include <iostream>
using namespace std;

int main()
{
  cout << "Hello ";
  sleep(2);
  cout << "World";
  cout << endl;
  
  return 0;
}
[/php]

Using [color=red]usleep[/color]()
[php]#include <iostream>
using namespace std;

int main()
{
  cout << "Hello ";
  usleep(2000000);
  cout << "World";
  cout << endl;
  
  return 0;
}
[/php]
Am I not using the functions correctly?

---

### Post by Compyx on 2010-05-10
Since the standard library uses buffered I/O, you need to flush the output buffer (holding "Hello") before sleeping. In C I would use
```
fflush(stdout);
```, in C++ I believe ```
cout.flush();
``` should do the trick. A newline will also flush the output buffer, but that would break up "Hello World" over two lines.

---

### Post by dodle on 2010-05-10
Thanks Compyx(Commodore), that does just as you say.

---

