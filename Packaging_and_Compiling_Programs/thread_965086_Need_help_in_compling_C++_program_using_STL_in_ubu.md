---
title: "Need help in compling C++ program using STL in ubuntu 8.10"
date: 2008-10-31
forum: Packaging and Compiling Programs
---

### Post by yinglcs2 on 2008-10-31
Hi,

I just upgrade to ubuntu 8.10, But when I compile my c++ program , it fails because it can't find STL library.

I am getting errors like these:

MyCpp.cpp: error: ‘for_each’ was not declared in this scope
MyCpp.cpp: error: ‘find_if’ was not declared in this scope

It was compling fine when I am using 8.0.4.

Can you please tell me how to fix my problem?

---

### Post by lambros on 2008-10-31
> **yinglcs2 said:**
> 
I am getting errors like these:

MyCpp.cpp: error: ‘for_each’ was not declared in this scope
MyCpp.cpp: error: ‘find_if’ was not declared in this scope

It was compling fine when I am using 8.0.4.


Hi,

Did you properly qualify these with the 'std::' namespace prefix?  Maybe you forgot to put 'using std::for_each;' or 'using namespace std;' somewhere in your code?  Try changing 'for_each' to 'std::for_each', see if that fixes the problem.

The newer version of the gcc compiler might be more fussy about these kinds of things than the older version in Ubuntu 8.04.  That might explain why it was working fine before.

If you're still having problems, could you post some source code that shows the problem?  You don't have to post the whole thing - try to narrow it down to a simple, short bit of code that has the same problem.

Lambros

---

### Post by DBQ on 2008-11-26
I have exactly the same problem.

---

### Post by lambros on 2008-11-26
> **DBQ said:**
> I have exactly the same problem.

Hi,

This thread is a little short on details, so all I can offer is general advice.  To use the "for_each" method, you need **two** ingredients:

```

#include <algorithm>

```

```

using namespace std;
// Alternatively:
// using std::for_each;

```

If either of these ingredients is missing, you will get errors similar to what was reported.

You need to have the "#include..." line, **exactly** as shown above.  **And** you need the "using..." directive.  Please double-check that you have **both** of these in your source file.

Have a look at the example code near the bottom of this page: [http://www.cplusplus.com/reference/algorithm/for_each.html](http://www.cplusplus.com/reference/algorithm/for_each.html)

Try to compile that example yourself, and see if you still have problems.  On my Ubuntu 8.10 system, it compiles just fine:
```

ll@ll-laptop:~$ g++ foreach.cpp -o foreach
ll@ll-laptop:~$ ./foreach
myvector contains: 10 20 30
myvector contains: 10 20 30
ll@ll-laptop:~$ 

```
Hope that helps,

Lambros

---

### Post by DBQ on 2008-11-26
What if I add the #include<algorithm> and instead just do "using namespace std;" -- I tried this, and it does not work.

---

### Post by lambros on 2008-11-26
> **DBQ said:**
> What if I add the #include<algorithm> and instead just do "using namespace std;" -- I tried this, and it does not work.

So you have **both** these lines near the top of your source file:

```

#include <algorithm>
using namespace std;

```

and your code still does not work?

Please could you check that you can compile the example code at that web-site I mentioned before, which is: [http://www.cplusplus.com/reference/algorithm/for_each.html](http://www.cplusplus.com/reference/algorithm/for_each.html) ?

The code I'd like you to compile is near the bottom of that page, beginning with:
```

// for_each example

```

It's very quick and simple - all you need to do is copy and paste that code into a file called "foreach.cpp".  Then try to compile it with this command:

```
g++ foreach.cpp -o foreach
```

Please let us know if that works OK.

It's important to know this information for troubleshooting your problem.  If the code from that web-site works fine, we know your problem must be with your **own** source code.  On the other hand, if that code fails to compile, we know the problem is with your **system** (installed compiler, headers and libraries).

Lambros

---

