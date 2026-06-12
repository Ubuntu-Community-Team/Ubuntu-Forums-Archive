---
title: "C++ compilation error,is it coding style?"
date: 2011-06-05
forum: Programming Talk
---

### Post by akshay.sulakhe on 2011-06-05
Hello frnds,
           I have been trying to compile a program on Fedora 15,and i am getting the error,link for pastebin is [http://pastebin.com/Hwm2egFG](http://pastebin.com/Hwm2egFG)

Is it because way to program has changed in new GCC...Kindly let me know.. :-):)

---

### Post by Some Penguin on 2011-06-05
s/gcc/g++/

---

### Post by akshay.sulakhe on 2011-06-05
I am sorry,i am unable to understand what ur saying. Kindly elaborate.

---

### Post by amauk on 2011-06-05
He means substitute "gcc" for "g++"
Ie.```
g++ -g error.cpp -o error1
```

---

### Post by akshay.sulakhe on 2011-06-05
Thanks for the reply....Still...same error... :-(

---

### Post by amauk on 2011-06-05
Well, without seeing the code it's impossible to say...

---

### Post by akshay.sulakhe on 2011-06-05
#include <iostream>

int main()
{
  cout << "This program simulates an error" << endl;
  return 12;
}

---

### Post by amauk on 2011-06-05
```
#include <iostream>

int main()
{
    [COLOR="Red"]std::cout[/COLOR] << "This program simulates an error" << [COLOR="Red"]std::endl[/COLOR];
    return 12;
}
```

---

### Post by akshay.sulakhe on 2011-06-05
@Amauk :- It worked...Many thanks...i guess this is some new coding style,Do u know any weblink where i can find all the changes,or what should i look for in search engine... :P..Thanks again...

---

### Post by Vaphell on 2011-06-05
no, it's called namespace, cin, cout, endl belong to std and you need either use std::cout explicitly or put the ```
using namespace std;
``` line in your code

---

### Post by akshay.sulakhe on 2011-06-05
@Vaphell :- using namespace std seems more convenient unless it has some drawbacks... thanks... :-)

---

### Post by amauk on 2011-06-05
It's nothing that has changed in any new GCC
The code you posted would not have compiled on any version of GCC

When you call out to external objects (in this case objects "cout" and "endl" that are in the C++ standard library) you need to specify where they are, so the compiler can find them

---

### Post by amauk on 2011-06-05
> **akshay.sulakhe said:**
> @Vaphell :- using namespace std seems more convenient unless it has some drawbacks... thanks... :-)
There are drawbacks to using "using namespace"

It'll pull in *every* object from the namespace into your program's namespace, and it's bad practise

---

### Post by akshay.sulakhe on 2011-06-05
Oh...ok...M new to programming,so these problems. :-)...thanks everyone.. :-)

---

### Post by akshay.sulakhe on 2011-06-05
@amauk :- will try to avoid namespace and use the other way as specified std::cout... here,it says to look for cout in standard I/O aka input output...Is that correct...i hope m not being too much trouble for u guys.. :-)

---

### Post by cgroza on 2011-06-05
> **akshay.sulakhe said:**
> @Vaphell :- using namespace std seems more convenient unless it has some drawbacks... thanks... :-)
It pollutes your namespace, and because of that, sometimes name conflicts occur.

---

### Post by ve4cib on 2011-06-05
However there are a few times where the "using namespace ____;" line is useful:

- you know you do not have any name conflicts because you have been careful with your class names

- you make heavy use of the same namespace throughout the code (e.g. a class that does nothing but handle program I/O would likely make VERY heavy use of std::cout and std::cin, in which case the "using namespace..." line would make your code cleaner and faster to write

---

### Post by JupiterV2 on 2011-06-05
You can also use:

using std::cout;
using std::endl;

...if you want to avoid appending the namespace to every call of the above functions but limiting it to only those you intend to use.

---

