---
title: "c++ simple program problem"
date: 2011-09-15
forum: Programming Talk
---

### Post by kaloasd on 2011-09-15
I'm getting an error while compiling this with Anjuta IDE. Could someone point out where i screwed up.

```
# include <iostream>
using namespace std;
int main (void)
    {
       cout >> " Hello World!\n";
       return 0;
    }

```

Error

```
hw.cc:5:16: error: no match for ‘operator>>’ in ‘std::cout >> " Hello World!\012"’
```

---

### Post by karlson on 2011-09-15
> **kaloasd said:**
> I'm getting an error while compiling this with Anjuta IDE. Could someone point out where i screwed up.

```
# include <iostream>
using namespace std;
int main (void)
    {
       cout >> " Hello World!\n";
       return 0;
    }

```

Error

```
hw.cc:5:16: error: no match for ‘operator>>’ in ‘std::cout >> " Hello World!\012"’
```

Think about what you see in the code for starters.

You are redirecting from COUT into "Hello World".  Is that really what you wanted to do?

May be you should start with some examples first:

[http://www.cplusplus.com/](http://www.cplusplus.com/)

---

### Post by surfer on 2011-09-15
try

```
cout << " Hello World!\n";
```

---

### Post by kaloasd on 2011-09-15
Thanks for the help, but it compiles but doesn't run.

```
# include <iostream>
using namespace std;
int main (void)
    {
       cout << " Hello World!\n";
       return 0;
    }

```

I also tried it with 

```
std::cout << " Hello World!\n";
```

also these don't run

[http://www.functionx.com/cpp/examples/simple.htm](http://www.functionx.com/cpp/examples/simple.htm)

I had no such problems with Visual C++

---

### Post by karlson on 2011-09-15
> **kaloasd said:**
> Thanks for the help, but it compiles but doesn't run.

```
# include <iostream>
using namespace std;
int main (void)
    {
       cout << " Hello World!\n";
       return 0;
    }

```

I also tried it with 

```
std::cout << " Hello World!\n";
```

also these don't run

[http://www.functionx.com/cpp/examples/simple.htm](http://www.functionx.com/cpp/examples/simple.htm)

I had no such problems with Visual C++

What do you mean it doesn't run?  What happens when you try running
```

$ g++ -W test.cpp
$ ./a.out

```

---

### Post by kaloasd on 2011-09-15
```
$ g++ -W hw.cpp                                                                        
$ ./hw.o
bash: ./hw.o: cannot execute binary file
```

I've been trying to run it from Anjuta up till now

---

### Post by karlson on 2011-09-15
> **kaloasd said:**
> ```
$ g++ -W hw.cpp                                                                        
$ ./hw.o
bash: ./hw.o: cannot execute binary file
```

I've been trying to run it from Anjuta up till now

By default gcc and g++ and most other compilers on UNIX/Linux systems produce file called a.out as an executable.

hw.o is an object file which cannot be executed and isn't produced in the case like yours.

---

### Post by Arndt on 2011-09-16
> **karlson said:**
> By default gcc and g++ and most other compilers on UNIX/Linux systems produce file called a.out as an executable.

hw.o is an object file which cannot be executed and isn't produced in the case like yours.

If hw.o didn't exist, bash would say something else. It seems something in the building chain has produced it and given it executable rights.

Apart from that, you are correct. It must be the IDE that is doing something behind the scenes.

---

### Post by WinterMadness on 2011-09-16
```

# include <iostream>
using namespace std;
int main (void)
    {
       cout << " Hello World!\n";
       return 0;
    }

```

compiled and worked for me. I didnt use any IDE though, I just simply used my text editor and g++

---

### Post by dwhitney67 on 2011-09-16
> **WinterMadness said:**
> 
compiled and worked for me.

I for one will sleep better knowing that!

---

### Post by karlson on 2011-09-16
> **Arndt said:**
> If hw.o didn't exist, bash would say something else. It seems something in the building chain has produced it and given it executable rights.

Apart from that, you are correct. It must be the IDE that is doing something behind the scenes.

Anjuta may have previously created hw.o, but from the commands shown above it won't.

---

### Post by kaloasd on 2011-09-19
Today it suddenly worked!

```
# include <iostream>
using namespace std;
int main (void)
    {
       cout << " Hello World!\n";
       return 0;
    }
```

```
$ g++ test.cpp
$ ./a.out
```

---

### Post by WinterMadness on 2011-09-19
> **dwhitney67 said:**
> I for one will sleep better knowing that!

Glad I could help!

in all seriousness, the reason i posted that is so he would have further insight in knowing it wasnt necessarily his code that was at fault.

---

