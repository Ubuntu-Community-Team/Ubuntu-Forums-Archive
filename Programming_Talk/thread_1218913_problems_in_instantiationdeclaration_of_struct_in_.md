---
title: "problems in instantiation/declaration of struct in c++"
date: 2009-07-21
forum: Programming Talk
---

### Post by monkeyking on 2009-07-21
I'm puzzled by why the code snippet doesnt work,
can anyone clarify

thanks

[PHP]
#include <iostream>
#include <cstring>

struct data{
  char *name;
  int number;
};


int main(int argc, char** argv){
  const char* ns = "John";
  int age = 27;
  data sl = {strdup(ns),age};//woks

  //below doestnt work
  data ls;
  ls =  {strdup(ns),age};
}


[/PHP]

---

### Post by dwhitney67 on 2009-07-21
Your second attempt makes no sense to me, much less to the compiler.  It should yield a syntax error.

Try the same in C and I bet the same thing will occur.

---

### Post by Sockerdrickan on 2009-07-21
Yes why would the second work? That syntax is only available when instantiating.

edit: perhaps check out C++0x?

[php]#include <cstring>

struct data {
  const char *name;
  int number;
};

int main() {
    const char* ns{"John"};
    int age{27};
    data s1;
    s1={strdup(ns),age};
} [/php]seems like a waste to do it like that though

---

### Post by fr4nko on 2009-07-21
> **monkeyking said:**
> I'm puzzled by why the code snippet doesnt work,
can anyone clarify

thanks

[php]
#include <iostream>
#include <cstring>

struct data{
  char *name;
  int number;
};


int main(int argc, char** argv){
  const char* ns = "John";
  int age = 27;
  data sl = {strdup(ns),age};//woks

  //below doestnt work
  data ls;
  ls =  {strdup(ns),age};
}


[/php]
The second attempt does not work because

[LIST=1]
[*]it does define a instance of the class data with the default constructor
[*]it does perform an assignment but you didn't define the assignement operator
[/LIST]
so the following code should work:
[php]
struct data{
  char *name;
  int number;

  data & operator= (const data &rhv) {
    this->name = rhv.name;
    this->number = rhv.number;
    return *this;
  };

  data() : name(NULL), number(0) { };
};
[/php]because we defined a default constructor and an assignment operator that does something meaningful.

Francesco

---

### Post by dribeas on 2009-07-21
The tricky part is that while what you read seem similar in both cases (where it works and where it does not), they are different.

In the first case, what seems like an assignment is really an initialization of an aggregate type. In the case you are instantiating the struct and later trying to assign to it. A workaround is adding a cast operation that will force the compiler into creating a temporary of the type initialized with the *initializer-list*.

```

data sl = { 0, 0 }; // aggregate initialization
data ls;            // variable declaration
//ls = { 0, 0 }; // fails: assignment cannot take an initializer-list
ls = (data) { 0, 0 }; // work-around

```

If you are learning C++, I would recommend that you use the standard library as much as possible (i.e. use std::string instead of char* to hold strings)

@fr4nko proposes that you define constructors for your struct (which in C++ is just a class with default public accessibility). That is a good recommendation.

On the other hand, to be precise I must comment on the two items he lists:

'It defines an instance of the class with default constructor'

Initialization in C++ is tricky to maintain compatibility with C and top-notch performance in the code. In particular, in this example as the struct/class is actually a POD, the implicit (compiler generated) default (parameter-less) constructor will not be called. Had there been a user-defined default constructor it would have been called. The list of possible cases is long, so I won't extend it here.

'It does perform an assignment but you didn't define the assignement operator'

Unless you require specific semantics you do not need to define the assignment operator. The compiler will generate one for you. Assignment is one of the three magic methods that the compiler will provide for you. In particular, for POD types, the compiler generated assignment operator does the equivalent of a memcpy (bit-wise copy of the contents of the POD).

---

### Post by fr4nko on 2009-07-21
Thank you for the precisions and your remarks about POD. I perfectly agree with everything you said :-)

Francesco

---

### Post by monkeyking on 2009-07-22
thanks people

---

