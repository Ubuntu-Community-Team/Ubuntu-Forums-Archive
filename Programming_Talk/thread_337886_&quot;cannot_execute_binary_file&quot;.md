---
title: "&quot;cannot execute binary file&quot;"
date: 2007-01-13
forum: Programming Talk
---

### Post by Rizado on 2007-01-13
Hi all! A long time ago I made a few simple hello world apps in c++ but nothing fancy. Now I've been to java classes for a while and thought I would try some more c++ however I can't run even the simplest hello world applications!

```
#include <iostream>

using namespace std;

int main()
{
  cout<<"HEY, you, I'm alive! Oh, and Hello World!\n";
  cin.get();

  return 1;
}
```The code is taken from [http://www.cprogramming.com/tutorial/lesson1.html](http://www.cprogramming.com/tutorial/lesson1.html). I compile this using "g++ -c hello.cpp -o output" and it works fine but when I try to run it, just doing "./output" it just wont start! All I get is ```
bash: ./output: cannot execute binary file
```What does this mean? I just don't get it, am I not compiling it right?

---

### Post by Wybiral on 2007-01-13
> g++ -c hello.cpp -o output

You need to get rid of that "-c"

It's causing it to compile to an object file instead of an executable.

---

### Post by Rizado on 2007-01-13
Problem solved, guess I was compiling the wrong way after all :D 
All I had to do was "g++ hello.cpp" That's what I tried first but that time it didn't work...

> **Wybiral said:**
> You need to get rid of that "-c"

It's causing it to compile to an object file instead of an executable.aaaaaah, Well you learn something new everyday. Thanks!

---

