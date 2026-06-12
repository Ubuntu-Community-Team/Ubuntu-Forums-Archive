---
title: "c++ enum help"
date: 2009-02-09
forum: Programming Talk
---

### Post by justanotherhandle on 2009-02-09
I'm just not getting how to deal with enums in c++.

In class Foo I have declared an enum and a variable of enum type like so ...

```

class Foo {
   public:
   enum MYENUM { ONE, TWO, THREE };
   void setSelection(MYENUM)

   private:
   MYENUM selection;
}; 

#include "Foo.h"
Foo::setSelection (MYENUM mye) {
  this->selection = MYENUM(mye)
}

```
But when I try to set the variable 'selection' in the main I get a out of scope on any of the named enums. 

```

#include "Foo.h"
int main() {
   Foo f;
   f.setSelection(TWO); // this causes out of scope.
}

```
Changing the parameters and arguments into an int and sending a '2' both compiles and works fine, but I want to send 'TWO'.

What am I doing wrong?

---

### Post by geirha on 2009-02-09
The enum is defined inside the Foo class, so you need to:
```

    f.setSelection(Foo::TWO);

```

However, if you just define the enum outside the class, your current main() should work fine.

---

### Post by justanotherhandle on 2009-02-09
Oh THANK YOU!  That worked :)

---

