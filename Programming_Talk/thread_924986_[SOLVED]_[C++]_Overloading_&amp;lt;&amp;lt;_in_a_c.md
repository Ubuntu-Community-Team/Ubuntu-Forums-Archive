---
title: "[SOLVED] [C++] Overloading &amp;lt;&amp;lt; in a class template"
date: 2008-09-20
forum: Programming Talk
---

### Post by NovaAesa on 2008-09-20
Hi, I'm trying to overload the << operator in a template class, but I seem to be running into a few problems. The function has to be a friend function because I need to access private member variables in the function. Yes, this is for an assignment, but I have replicated the problem below so that it's not my assignment that you would be working on, jus the basic principal:

In main.cpp:
```

#include "example.h"
#include <ostream>

int main() {
    Example<int> example_instance_1(55);
    cout << example_instance_1 << endl;
    return 0;
}

```

In file example.h:
```

#ifndef EXAMPLE_H
#define EXAMPLE_H
#include <ostream>
using namespace std;

template <class T> class Example {
    template <class T> friend ostream& operator << (ostream& out, const Example<T>& ex);
    public:
    Example(T a); //constructor
    private:
    T a;
};

#include "example.template"
#endif

```

In file example.template:
```

#include <iostream>
using namespace std;

template <class T> ostream& operator << (ostream& out, const Example<T>& ex) {
    cout << ex.a;
    return out;
}

template <class T> Example<T>::Example(T a) {
    this->a = a;
}

```


During compilation:
```

ps@ps-desktop:~/Desktop/untitled folder$ g++ main.cpp -o main -Wall
In file included from main.cpp:1:
example.h:7: error: declaration of ‘class T’
example.h:6: error:  shadows template parm ‘class T’
ps@ps-desktop:~/Desktop/untitled folder$ 

```

If anyone could shed some light on what these errors mean and/or how to fix them it would be much appreciated.

-Nova

---

### Post by Heinzelotto on 2008-09-20
```

template <class T> class Example {
    template <class T> friend ostream& operator << (ostream& out, const Example<T>& ex);
    public:
    Example(T a); //constructor
    private:
    T a;
};

```

why do you define a new template for the operator<< ?

```

template <class T> friend ostream& operator << (ostream& out, const Example<T>& ex);
```

this is wrong:
for example let the compiler create a template-specialization Example<int>. This class would now have the operator<< of _any_ Example<...> class as a friend, since what you are doing is specifying a template within a template. You are specifying the template-parameter as "T" again though, which you can't do.

what you meant probably was:

```

template <class T> class Example {
    friend ostream& operator << (ostream& out, const Example<T>& ex);
    public:
    Example(T a); //constructor
    private:
    T a;
};

```

The operator<< now takes an Example<T> as an argument and the "T" "in Example<T>" is defined in the template declaration "template <class T>"

---

### Post by NovaAesa on 2008-09-20
Thank you for the reply Heinzelotto. I understand why what I am tring to do in the above code is not working now. I was trying what you suggested a while ago though, but that wasn't working either. This is what I get when I try to do what you suggest:

```

ps@ps-desktop:~/Desktop/untitled folder$ g++ main.cpp -o main -Wall
In file included from main.cpp:1:
example.h:7: warning: friend declaration &#8216;std::ostream& operator<<(std::ostream&, const Example<T>&)&#8217; declares a non-template function
example.h:7: warning: (if this is not what you intended, make sure the function template has already been declared and add <> after the function name here) -Wno-non-template-friend disables this warning
/tmp/ccbyOjuu.o: In function `main':
main.cpp:(.text+0x1af): undefined reference to `operator<<(std::basic_ostream<char, std::char_traits<char> >&, Example<int> const&)'
collect2: ld returned 1 exit status
ps@ps-desktop:~/Desktop/untitled folder$ 

```

---

### Post by NovaAesa on 2008-09-20
I just realised I could make it compile (and work) if I change the line to:
```
template <class U> friend ostream& operator << (ostream& out, const Example<U>& ex);
```
Is this semantically correct and considered good programming practice though? Does anyone know? It sort of feels like a hack job to get around a compile error.

---

### Post by Heinzelotto on 2008-09-20
you can ignore the warnings in this case (or use the gcc-option to make them disappear) because what you have written is what you wanted.

The "undefined reference" error though comes from the fact that you (seem to) have not yet _defined_ the actual function. As you can read [here]("http://gcc.gnu.org/faq.html#friend"), you have to explicitly define each specialization of operator<<. You don't have to do something like
```

operator<<(ostream&, const type1&) { ... }
operator<<(ostream&, const type2&) { ... }
operator<<(ostream&, const type3&) { ... }
operator<<(ostream&, const type4&) { ... }

```

though, you can just let a template do the work for you:

```

template<class T>
ostream& operator<< (ostream& out, const Example<T>& ex) {
    return out << ex.a;
}

```

this would create all your needed specializations on demand.



edit (answer to your latest reply):
in your first posted attempt you tried to create a template with a template argument named "T" in a template which also has a template argument named "T". This led to ambiguity. What you now have done is create a template U in your "T"-template. This is syntactically correct, but not semantically. It would for example make the function "operator<<(ostream&, const Example<Class_number_one>&);" a friend of any other Example<>'s such as Example<int> or Example<std::string>

---

### Post by NovaAesa on 2008-09-20
Thanks Heinzelotto, I'll look into that and see if I can't make it work =]

---

### Post by NovaAesa on 2008-09-20
Okay, this is what I finally came up with (in case anyone has the same problems).

In main.cpp:
```

#include "example.h"
#include <ostream>

int main() {
    Example<int> example_instance_1(55);
    cout << example_instance_1 << endl;
    return 0;
}

```

In example.h:
```

#ifndef EXAMPLE_H
#define EXAMPLE_H
#include <ostream>
using namespace std;

//class must be forward declared because it contains a friend function template
template<class T> class Example;

//friend function also must be forwards declared
template<class T> ostream& operator<<(ostream& out, const Example<T>& ex);

template <class T> class Example {
    friend ostream& operator<<<>(ostream& out, const Example<T>& ex);
    public:
    Example(T a); //constructor
    private:
    T a;
};

#include "example.template"
#endif

```

In example.template:
```

#include <iostream>
using namespace std;

template <class T> ostream& operator<<(ostream& out, const Example<T>& ex) {
    cout << ex.a;
    return out;
}

template <class T> Example<T>::Example(T a) {
    this->a = a;
}

```


Thanks for the help =]
It does what it's meant to, compiles without any problems, and I'm almost certain it's semantically correct.

---

