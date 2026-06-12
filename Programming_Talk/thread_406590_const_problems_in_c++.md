---
title: "const problems in c++"
date: 2007-04-11
forum: Programming Talk
---

### Post by aquavitae on 2007-04-11
I'm having a general problem with const in classes.  Here's a trivial example:

```

class MyClass {
   private:
      QString* data1;
      QString* data2;

      // Return a number depending on the value of param
      QString* privateData(const int param);

   public:
      // Return a string reflecting the internal data
      const QString readData(const int param) const;

      // Append to the internal data
      void appendData(const int param, QString* value);

      // Add ctors/dtors, etc
};

QString* MyClass::privateData(const int param) {
   if (param == 1)
      return data1;
   else
      return data2;
}

const QString* MyClass::readData(const int param) const {
   const QString* data = privateData(param);
   return data;
}

void MyClass::appendData(const int param, QString* value) {
   QString* data = privateData(param);
   data->append(&value);
}

```

This example doesn't do much, but it illustrates my problem:  the function appendData uses the function privateData to find a QString, then writes to it.  For this reason, privateData cannot be const.  However, the compiler throws an error in the function readData as it is const but is calling privateData, which is not const.

I think I could probably use const_cast to deal with this, but I'd rather find a better way, if there is one.  I've always thought casts to be a bit of a hack!

Does anyone know how to do this?

---

### Post by duff on 2007-04-11
Amazingly, in C++ you can over load on method's const-ness (it's actually a different type for the "this" parameter).  Try this out:

```
#include <iostream>

struct C {

   void foo() const {
      std::cout << "const foo" << std::endl;
   }

   void foo() {
      std::cout << "non-const foo" << std::endl;
   }

   void bar() const {
      foo();
   }

   void baz() {
      foo();
   }
};

int main() {
   C c;
   c.bar();
   c.baz();
}
```

---

### Post by aquavitae on 2007-04-13
Thanks, its works!

---

