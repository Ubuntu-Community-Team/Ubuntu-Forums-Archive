---
title: "mixxing file i/o and header,source files problems"
date: 2010-03-30
forum: Programming Talk
---

### Post by fasoulas on 2010-03-30
i have three files in this project in c++. 

main.cpp   lib.h   and   lib.cpp

i want to pass an ifstream to a function that is declared in lib.h and is implemented in lib.cpp

but when i try to do it as if it was one file of code something like

```

in main.cpp
ifstream read("data.txt");
somefunction(read , size);



in lib.h
void somefunction(ifstream& read , int size);



and in lib.cpp
void somefunction(ifstream& read , int size)
{
   ////code////
}

```

when i do this i get errors like ifstream has not been declared and read has not been declared and some other errors.

what might be the cause of the problem?

i tried searching with google but i don't seem to find a solution for this kind of errors,
it's the first time i am mix file i/o and header,source file.

So if anyone knows what the problem is please help

---

### Post by fasoulas on 2010-03-30
the error messages a get

```
In file included from main.cpp:4:
lib.h:37: error: &#8216;ifstream&#8217; has not been declared
main.cpp: In function &#8216;int main()&#8217;:
main.cpp:77: error: &#8216;read&#8217; was not declared in this scope
main.cpp:105: error: invalid initialization of reference of type &#8216;int&&#8217; from expression of type &#8216;std::ifstream&#8217;
lib.h:37: error: in passing argument 2 of &#8216;void somefunction(Contact*, int&)&#8217;
lib.h:37: error: &#8216;ifstream&#8217; has not been declared
In file included from lib.cpp:3:
lib.h:37: error: &#8216;ifstream&#8217; has not been declared
```

---

### Post by nvteighen on 2010-03-30
Have you included fstream in all needed places?

---

### Post by fasoulas on 2010-03-30
> **nvteighen said:**
> Have you included fstream in all needed places?

yes i did 
also in lib.h

---

### Post by TheBuzzSaw on 2010-03-30
```
using namespace std;
```

Have that in the right places?

---

### Post by fasoulas on 2010-03-30
> **TheBuzzSaw said:**
> ```
using namespace std;
```

Have that in the right places?

i don't have it only in lib.h

is that the problem?

---

### Post by TheBuzzSaw on 2010-03-30
> **fasoulas said:**
> i don't have it only in lib.h

is that the problem?

Yup. It needs to be everywhere that you use stuff from the std namespace.

---

### Post by fasoulas on 2010-03-30
> **TheBuzzSaw said:**
> Yup. It needs to be everywhere that you use stuff from the std namespace.

thanks a lot now it works

---

### Post by MadCow108 on 2010-03-30
its bad style to use using namespace std; in header files
this forces the namespace on all who include the header

instead prepend the namespace directly: std::ifstream

---

### Post by fasoulas on 2010-03-30
> **MadCow108 said:**
> its bad style to use using namespace std; in header files
this forces the namespace on all who include the header

instead prepend the namespace directly: std::ifstream

i will have that in mind

---

### Post by nvteighen on 2010-03-31
Well, you can use **using namespace <whatever namespace>** as long as you don't use it in headers. Using it in code files is ok if you consider it to make your code simpler. The issue of using it in headers is that it forces the code including that header to follow "your tastes" about namespaces, besides of possibly cluttering the code's main namespace.

---

