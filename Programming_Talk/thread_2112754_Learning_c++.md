---
title: "Learning c++"
date: 2013-02-05
forum: Programming Talk
---

### Post by 3v3rgr33n on 2013-02-05
Hi

I'm a Java programmer learning c++.

I came across namespaces, they've been confusing me for some time. [http://en.wikipedia.org/wiki/Namespace_%28computer_science%29](http://en.wikipedia.org/wiki/Namespace_%28computer_science%29) explains that > In [Java]("http://en.wikipedia.org/wiki/Java_%28programming_language%29"), the idea of a namespace is embodied in [Java packages]("http://en.wikipedia.org/wiki/Java_package")

Judging from this code ```
// using #include <iostream> using namespace std;  namespace first {   int x = 5;   int y = 10; }  namespace second {   double x = 3.1416;   double y = 2.7183; }  int main () {   using namespace first;   cout << x << endl;   cout << y << endl;   cout << second::x << endl;   cout << second::y << endl;   return 0; }
``` which I found at [http://www.cplusplus.com/doc/tutorial/namespaces/](http://www.cplusplus.com/doc/tutorial/namespaces/)

namespaces do not seem like Java packages as you cannot define packages in a java file, they also don't seem to have methods inside them but only variables.

Please help me, what are namespaces?

Regards
[]("http://en.wikipedia.org/wiki/Namespace_%28computer_science%29")

---

### Post by Zugzwang on 2013-02-05
> **3v3rgr33n said:**
> 
namespaces do not seem like Java packages as you cannot define packages in a java file, they also don't seem to have methods inside them but only variables.

Please help me, what are namespaces?


Namespaces in C++ can contain all kinds of things, including functions and classes. In that tutorial, this is simply not done. Just try it out! You will see that it works. The word "method" that you use doesn't precisely apply here, as "methods" are functions within a class.

Note that the wikipedia only states that the idea of packages is embodied in the namespaces, not that they are precisely the same. However, the main difference is that in Java, there is a one-to-one mapping between in which directory a Java file is found and the package. In C++, there is no mapping, and you have to declare your namespaces "manually".

---

### Post by 3v3rgr33n on 2013-02-05
What's the point of havin' namespaces instead of handling possible variable and function name clashes?

---

### Post by lisati on 2013-02-05
> **3v3rgr33n said:**
> What's the point of havin' namespaces instead of handling possible variable and function name clashes?

As I understand it, namespaces are a useful way of organizing and controlling [data scope]("http://en.wikipedia.org/wiki/Scope_%28computer_science%29"). 

In a smaller project, managing what variable "x" means and how it should be used in different parts of a program is relatively straightforward. In larger programs, tracking down the unintended consequences of accidental misuse of variable "x" becomes harder, particularly when you're working on someone else's project, or if you haven't worked on one of your own masterpieces for some time.

---

### Post by r-senior on 2013-02-05
Languages have namespaces so that they scale up from writing small applications to writing large ones. It would be difficult, if not impossible, to resolve all the conflicts in a large application without some sort of namespace mechanism.

C++ has namespaces, Java has packages, Python has modules. 

Objective-C doesn't have namespaces and it has to fall back to a pseudo-namespace mechanism of prefixes like NS, UI, CC, etc. As in NSString, UIColor, CCDirector.

---

### Post by 3v3rgr33n on 2013-02-05
That makes sense. Thnks guys!

---

