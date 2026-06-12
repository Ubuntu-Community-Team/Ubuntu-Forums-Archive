---
title: "[c++] Problem initializing member variable in constructer"
date: 2010-07-23
forum: Programming Talk
---

### Post by NovaAesa on 2010-07-23
Hi all,

I'm having a problem with a C++ program I'm writing. I'm trying to initialize a member variable of a class within it's constructor, and I keep getting compile errors what ever way I try to arrange things. This is my latest attempt:

[php]
class Foo
{
public:

    Foo(int a) {
        this->a = a;
    }

private:

    int a;
};

class Bar
{
public:

    Bar() {
        f = Foo(42);
    }

private:

    Foo f;
};

int main()
{
    Bar b;
    return 0;
}
[/php]

The compile error is as follows:
```

[ps@pris Desktop]$ g++ -Wall test.cpp
test.cpp: In constructor &#8216;Bar::Bar()&#8217;:
test.cpp:18:11: error: no matching function for call to &#8216;Foo::Foo()&#8217;
test.cpp:5:5: note: candidates are: Foo::Foo(int)
test.cpp:2:1: note:                 Foo::Foo(const Foo&)
[ps@pris Desktop]$ 

```

If anyone has any pointers on getting it to work, it would be greatly appreciated.

---

### Post by Some Penguin on 2010-07-23
```

Foo f;

```

is invoking the default, no-argument constructor.

---

### Post by Some Penguin on 2010-07-23
```

Foo f;

```

is invoking the default, no-argument constructor...

---

### Post by NovaAesa on 2010-07-23
Thanks Some Penguin,


I have tried changing the code to:
```

class Foo
{
public:

    Foo(int a) {
        this->a = a;
    }

private:

    int a;
};

class Bar
{
public:

    Bar() {
        
    }

private:

    Foo f(42);
};

int main()
{
    Bar b;
    return 0;
}  

```

But this leaves me with a different problem.

```

[ps@pris Desktop]$ g++ -Wall test.cpp
test.cpp:24:11: error: expected identifier before numeric constant
test.cpp:24:11: error: expected &#8216;,&#8217; or &#8216;...&#8217; before numeric constant
[ps@pris Desktop]$ 


```



EDIT:
There is an obvious way around the problem, which is to make f a pointer to a Foo object rather than a Foo object itself. The Foo object can then be created in the constructor. This seems rather hackish though... does anyone know a better way?

---

### Post by GeneralZod on 2010-07-23
Use the member initialisation list:

```

class Foo
{
public:

    Foo(int a) {
        this->a = a;
    }

private:

    int a;
};

class Bar
{
public:

    Bar()
      :f(42) {

    }

private:

    Foo f;
};

int main()
{
    Bar b;
    return 0;
}

```

---

### Post by NovaAesa on 2010-07-23
Thanks GeneralZod, that was exactly what I was looking for =]

---

