---
title: "[C++] Macro Concatenation"
date: 2009-05-28
forum: Programming Talk
---

### Post by dwhitney67 on 2009-05-28
I'm trying to define a macro that will define a local object, with the macro parameter as part of the object name.  The issue I am having is with the namespace specifier in the macro parameter.

Is there a special g++ preprocessor directive that I can use to ignore the namespace specifier of the parameter?  Or alternatively, have the parameter evaluated so that the parameter is converted to an int?

Here's the code I am testing with, which obviously does not compile:
```

#define TM_MARKER(type)   TM::Marker mm_##type(type)

namespace TM
{
enum Type { ONE, TWO, THREE };

class Marker
{
public:
  Marker(Type type) {}
  ~Marker() {}
};
}

int main()
{
  TM_MARKER(TM::ONE);
}

```

---

### Post by dwhitney67 on 2009-05-28
Ha!  That's funny... no more than a minute after submitting the post, I came up with a solution (through continued experimentation).

My solution was to alter the macro.
```

#define TM_MARKER(type)   TM::Marker mm_##type(TM::type)

...

int main()
{
  // these should produce unique objects
  TM_MARKER(ONE);
  TM_MARKER(TWO);
}

```

Can someone think of a better/cleaner solution?  I already have lots of code that uses the TM:: namespace qualifier in front of the enum value passed to TM_MARKER.  I'd hate to have to go back to edit those files.

---

### Post by nvteighen on 2009-05-29
Seriously, what you need is almost a Lisp macro system together with something like Scheme's **symbol-append** procedure... 

No, I'm not joking: I really doubt the C or C++ preprocessors allow you to do something different to what you have there. The macro semantics of these languages is really really limited (which is a pity).

---

