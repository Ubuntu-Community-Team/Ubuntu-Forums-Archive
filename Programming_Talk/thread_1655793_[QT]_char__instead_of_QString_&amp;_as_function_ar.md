---
title: "[QT] char * instead of QString &amp; as function argument"
date: 2010-12-30
forum: Programming Talk
---

### Post by dawwin on 2010-12-30
Hello,
Can someone explain me, why Something like this works, when I compile in QTCreator:
```

myClass {
public:
static void myFunc(QString &text);
};
[...]
myClass:myFunc("abcd");

```But this code will not work, when I compile in terminal
```

myClass {
public:
static void myFunc(std::string &text);
};
[...]
myClass:myFunc("abcd");

```I just don't know, how QTCreator "converts" char * to QString &.

---

### Post by dwhitney67 on 2010-12-30
A constant char* is NOT the same, nor can be converted directly to a _reference_ to an STL string.

You could implement your non-Qt class as:
```

#include <string>

class MyClass
{
public:
   static void myFunc(const char* text) { /* whatever */ }

   static void myFunc(const std::string& text) { myFunc(text.c_str()); }
};

int main()
{
   MyClass::myFunc("abcd");   // calls the const char* version of myFunc()
}

```

As for the Qt QString class, surely it has a constructor that accepts a const char*.  How it stores it internally is beyond the scope of my knowledge.

```

class QString
{
public:
   QString();
   QString(const char* str);
   QString(const QString& qstr);
   // etc.
};

```

P.S.  Alternatively,
```

class QString
{
public:
   QString(const char* str** = 0**);
   QString(const QString& qstr);
   // etc.
};

```

---

### Post by GeneralZod on 2010-12-30
In the OP's example, though, the reference is to *non-const* QString, so the existence of an implict conversion from char* to QString via a QString constructor would not prevent a compile error e.g.

```

class ImplicitFromCharPtr
{
public:
    ImplicitFromCharPtr(char*) {};
};

void f(ImplicitFromCharPtr& blah)
{
};

int main()
{
    f("sausage"); // Error
    return 0;
}

```

---

### Post by MadCow108 on 2010-12-30
> **dwhitney67 said:**
> A constant char* is NOT the same, nor can be converted directly to a _reference_ to an STL string.

there is something missing in that statement:
a const char cannot be implicitly converted to a **non**-const string reference
but it can be converted to a const string reference.
so your example (which uses a const reference) works fine also without the const char overload.

```

   const std::string & a = "abc"; // ok
   std::string & b = "abc"; // error

```

it should also not work with qstrings:
```

void myFunc(QString & text) { }
void myFunc2(const QString & text) { }

int main()
{
  myFunc("abc"); // error
  myFunc2("abc"); // ok
}

```

maybe qtcreator plays around with -fno-const-strings or implicitly converts literals to QStrings?

---

