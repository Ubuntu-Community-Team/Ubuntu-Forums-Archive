---
title: "C++ stream output bug?"
date: 2010-09-15
forum: Programming Talk
---

### Post by worksofcraft on 2010-09-15
```


#include <iostream> // cout
#include <string.h> // strcpy

using namespace std;

int main() {
	char Buf[200];
	cout << strcpy(Buf, " first") << flush << strcpy(Buf, " second") << endl;
	return 0;
}

```

Without running it I woulda thought this should write " first second" to stdout... apparently not :confused:

would that be a bug?

---

### Post by GeneralZod on 2010-09-15
If I were to guess, I'd say it's a result of the fact that the order in which arguments to functions are evaluated is undefined in C++ ("cout <<" is just a call to operator<< with cout as one of its arguments), and there are two "arguments" that modify Buf when they are evaluated.  I thought this undefined order only applied *per function call*, though, but may be wrong.

---

### Post by MadCow108 on 2010-09-15
This is intentional undefined behavior (and thus a feature and no bug :) )

It is basically the same as the classical example:
i=i++;
you assign and change the variable in the same expression with no sequence point in between.
So there order in which the strcpy's are evaluated is undefined.

see also:
[http://en.wikipedia.org/wiki/Sequence_point#cite_note-2](http://en.wikipedia.org/wiki/Sequence_point#cite_note-2)

---

### Post by worksofcraft on 2010-09-15
> **MadCow108 said:**
> This is intentional undefined behavior (and thus a feature and no bug :) )

It is basically the same as the classical example:
i=i++;
you assign and change the variable in the same expression with no sequence point in between.
So there order in which the strcpy's are evaluated is undefined.

see also:
[http://en.wikipedia.org/wiki/Sequence_point#cite_note-2](http://en.wikipedia.org/wiki/Sequence_point#cite_note-2)

It certainly looks that way, but I thought the order of expression evaluation **was** defined in C++. In particular in stream output because otherwise things like stream manipulators might not happen at the right time :shock:

Also boolean expression short circuit used to be guaranteed. Have they changed the standard recently?

---

### Post by MadCow108 on 2010-09-15
the order of evaluation of the operators is defined due to the sequence point after a function return.
Otherwise the stream operators would be pretty much useless.

But the order of evaluation of their arguments is undefined.

And boolean operators are sequence points also in C++

---

### Post by worksofcraft on 2010-09-15
The reason I asked is because I ran into problem using temporaries... I thought they supposed to exist for the full duration of the statement they are in, so not sharing same space for two different ones in the same statement.

```

#include <iostream> // cout
#include <string.h> // strcpy

using namespace std;

inline char * mystrcpy(const char *Src, char *Dst = (char[512]){0}) {
	return strcpy(Dst, Src);
}

int main() {
	cout << strcpy((char[512]){0} , " first") << strcpy((char[512]){0}, " second") << endl;
	cout << mystrcpy(" third") << mystrcpy(" fourth") << endl;
	return 0;
}

```

result:
```

$ ./a.out
 first second
 third third

```

---

### Post by MadCow108 on 2010-09-15
in this case your default argument char *Dst = (char[512]){0}
gets created in the scope of function and then destroyed again when it ends (e.g. before it gets passed to the cout)
In the second call it might use the same memory location and you have the same problem as above.

inlining does not help, because the compiler will respect scopes of the inlined function.
You would need a macro to do this or use dynamic allocated memory.

But I do no recommend this kind of coding. Use std::strings if you want automatic buffer handling.
e.g.:
cout << string(" third") << string(" fourth") << endl

---

### Post by dribeas on 2010-09-15
> **MadCow108 said:**
> in this case your default argument char *Dst = (char[512]){0}
gets created in the scope of function and then destroyed again when it ends (e.g. before it gets passed to the cout)

That´s not quite so. The compiler generates the temporary in the caller scope, in place of the argument and then calls the function. Overall the result is the same, since the lifetime of that temporary does not extend beyond the execution of the function, and thus the compiler can (and will) reuse the same space.

The reason that default arguments get created by the caller and not the callee is that when the compiler is processing the calling code it knows how many arguments are present and how many have to be default generated. If the creation of the temporary had to be performed inside the function then the compiler would have to inject the knowledge of how many arguments are really present through the call, and that would imply changes in the calling convention.

When the compiler sees:

```

int foo( int value = 6 );
int main() {
   foo();
}

```

It translates it to:
```

int foo( int value ); // annotation: __default(value)==6
int main() {
   int __temporary = 6; // generated
   foo( __temporary );
}

```

This enables a single definition of the function and is  the reason why you get this "strange" behavior:

```

struct base {
   virtual void foo( int x = 0 ) {
       std::cout << "base " << x << std::endl;
   }
};
struct derived : base {
   virtual void foo( int x = 5 ) {
       std::cout << "derived " << x << std::endl;
   }
};
int main() {
   derived d;
   base & b = d;
   b.foo(); // derived 0
   d.foo(); // derived 5
   d.base::foo(); // base 0 [*]
}

```

Where the last result deserves special attention. Even if we are calling through a reference to derived, we are explicitly disabling polymorphism and telling the compiler to use the base function. The compiler will not use derived::foo() to interpret the call, just as it would not do it either if we were calling a method in base that was hidden in derived.

---

### Post by worksofcraft on 2010-09-16
[QUOTE=MadCow108;9847897
...But I do no recommend this kind of coding. Use std::strings if you want automatic buffer handling.
e.g.:
cout << string(" third") << string(" fourth") << endl[/QUOTE]

Yeah... it's old code that was written for a system that didn't even have dynamic memory allocation and definitely no STL. I haven't programmed for a long time so it's all good practice to refresh my memory as I'm putting in vectors of unicode characters instead of chars.


First I had to port it back to C++ properly as it had been turned into Java at some stage, but reverse iterators should soon help when I come to mixing R2L and L2R locales.

---

