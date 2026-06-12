---
title: "defining static vector in c++ stl"
date: 2007-10-25
forum: Programming Talk
---

### Post by monkeyking on 2007-10-25
Hi I got problems defining a static vector, or more correctly initilizing it.
this is the code
```

#include <vector>
#include <iostream>

using namespace std;

class aClass{
private:
  static vector<double*> vec; 
public:
  static void inputVars();
  static void init();
  static void print();
};

vector aClass::vec; // <- compiler complains here

void aClass::inputVars(){
  for(int i=0;i<10;i++){
    double *tmp = new double[3];
    for (int j=0;j<3;j++)
      tmp[j] = i;
    vec.push_back(tmp);
  }
}


void aClass::print(){
  for(int i=0;i<vec.size();i++){
    double *tmp = vec[i];
    for (int j=0;j<3;j++)
      cout <<tmp[j]<<endl;
  }
}

int main(){
  aClass myClass;
  myClass.inputVars();
  myClass.print();
  return 0;
 
}

```
I guess the problems are just syntatic.
First of all I know it seems strange to define everything static, but this is just a small rewritten part of the program.

thanks in advance

By the way the compiler says the following
```

test.cpp:17: error: invalid use of template-name ‘std::vector’ without an argument list

```

---

### Post by aks44 on 2007-10-25
> **monkeyking said:**
> ```

test.cpp:17: error: invalid use of template-name &#8216;std::vector&#8217; without an argument list
```

The error message says it all: you need to provide a template argument list.
How is the compiler going to guess if you want to instanciate a std::vector<double*>, or a std::vector<Whatever> ?


BTW:
- your code is not exception safe
- you don't need an instance of aClass to call its static methods.

---

### Post by monkeyking on 2007-10-25
> **aks44 said:**
> The error message says it all: you need to provide a template argument list.
How is the compiler going to guess if you want to instanciate a std::vector<double*>, or a std::vector<Whatever> ?


BTW:
- your code is not exception safe
- you don't need an instance of aClass to call its static methods.

ok thanks for the fast reply, but I'm still in the dark.
If I change the problematic line to
```

vector aClass::vec<double*>;

```
It still complains, so can you elaborate on the correct syntax,

thanks again

---

### Post by aks44 on 2007-10-25
```
std::vector<double*> aClass::vec;
```

---

### Post by monkeyking on 2007-10-25
Thank you,
now I get the idea :)

---

