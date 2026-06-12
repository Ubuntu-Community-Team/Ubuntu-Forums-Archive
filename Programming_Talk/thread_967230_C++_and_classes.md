---
title: "C++ and classes"
date: 2008-11-01
forum: Programming Talk
---

### Post by Emill on 2008-11-01
Hello. I have a little problem...
I have two classes that depend on each other.
```

class A {
private:
    B b;
};

class B {
private:
    A a;
};
```
If I try to compile this I get the error that B is not defined. How can I tell the compiler to check a bit down? ;)

---

### Post by CptPicard on 2008-11-01
Use a "forward declaration"

```

class B;

```

at the top (IIRC).

---

### Post by Emill on 2008-11-01
Aha. So that is allowed for classes too :)

---

### Post by snova on 2008-11-01
I don't think this is possible:

```

$ cat > test.cpp
class A;
class B { A a; };
class A { B b; };
^D
$ gcc -c test.cpp
test.cpp:2: error: field &#8216;a&#8217; has incomplete type

```

Doing it this way won't work. If they were pointers, it'd be fine, but class A contains an instance of class B, which contains an instance of class A. Logic tells me it isn't possible.

---

### Post by Emill on 2008-11-01
Hmm.. This doesn't work:
```

class A;
class B;
class A {
public:
	B b;
};
class B {
public:
	A a;
};

int main(){
	return 0;
}

```
I get this error:
test.cpp:5: error: field 'b' has incomplete type

---

### Post by CptPicard on 2008-11-01
snova is right, it would result in a recursive structure with infinite memory requirement as you're using straight containment... if you need something like that, try pointers or references...

---

### Post by jimi_hendrix on 2008-11-01
> **snova said:**
> I don't think this is possible:

```

$ cat > test.cpp
class A;
class B { A a; };
class A { B b; };
^D
$ gcc -c test.cpp
test.cpp:2: error: field ‘a’ has incomplete type

```Doing it this way won't work. If they were pointers, it'd be fine, but class A contains an instance of class B, which contains an instance of class A. Logic tells me it isn't possible.

didnt you just try to compile a C++ program with a C compiler? or am i really tired...

---

### Post by Emill on 2008-11-01
Ok. I still have a problem.
```

class A;
class B;
class A {
public:
	B *b;
	void something(){
		b->integer = 5;
	}
};
class B {
public:
	A a;
	int integer;
	void some(){
		a = A();
		a.b = this;
	}
};

int main(){
	return 0;
}
```
Error:
test2.cpp: In member function 'void A::something()':
test2.cpp:7: error: invalid use of incomplete type 'struct B'
test2.cpp:2: error: forward declaration of 'struct B'

If I do it this way instead:
```
class A;
class B;
class B {
public:
	A a;
	int integer;
	void some(){
		a = A();
		a.b = this;
	}
};
class A {
public:
	B *b;
	void something(){
		b->integer = 5;
	}
};

int main(){
	return 0;
}
```
I get this error:
test2.cpp:5: error: field 'a' has incomplete type
test2.cpp: In member function 'void B::some()':
test2.cpp:8: error: 'a' was not declared in this scope
test2.cpp:8: error: invalid use of incomplete type 'struct A'
test2.cpp:1: error: forward declaration of 'struct A'

---

### Post by Emill on 2008-11-01
I solved it, i think. I have to use "nested classes" :)

---

### Post by CptPicard on 2008-11-01
Sounds like a very complex solution, I don't think that's it... circular references ought to be well possible in the sense you're trying as long as you're not actually including data recursively...

Here's the same issue

[http://bytes.com/forum/thread649849.html](http://bytes.com/forum/thread649849.html)

How about the suggested "declarations only, a forward declaration and then definition" approach? Put your declarations in a header file...

---

### Post by Emill on 2008-11-01
Is it bad to use nested classes?

---

### Post by CptPicard on 2008-11-01
Whatever works, but Ockham's razor you know... simplest solution is the best one.

---

### Post by snova on 2008-11-01
> **jimi_hendrix said:**
> didnt you just try to compile a C++ program with a C compiler? or am i really tired...

You can compile C++ code with GCC as long as you don't try to use it as a linker.

---

### Post by dwhitney67 on 2008-11-02
> **Emill said:**
> Is it bad to use nested classes?

There are cases where nested classes are used; hence it is not bad.

Concerning your original problem, consider using CptPicard's suggestion of separating the declarations of your classes (into header files) from the implementation (which generally should be in .cpp files).

P.S.  What is really "bad", is seeking advice on a solution when you really haven't presented the problem in full.  There are instances where two classes must depend upon each other, however when an independent party (e.g. me) examines the scant information you have provided, it is logical to question if the dependency is really necessary; after all, it could be the result of a bad design.

---

### Post by Lux Perpetua on 2008-11-02
You can't refer to b->integer until you've defined class B, since the compiler doesn't have enough information before then to compile such code. This is easily fixed. ```
class A;
class B;

class A {
public:
    B *b;
    void something();
};

class B {
public:
    A a;
    int integer;
    void some(){
        a = A();
        a.b = this;
    }
};

inline void A::something() {
    b->integer = 5;
}

int main(){
	return 0;
}
```

---

### Post by Emill on 2008-11-02
Thank you.

---

### Post by dribeas on 2008-11-02
You can use forward declarations to define pointers and references and to declare (but not define/implement) functions or methods that take the incomplete types as arguments or return the incomplete types.

You cannot define member attributes of an incomplete type, as the compiler needs the size of the fully defined object to calculate the size of the containing class.

You cannot use an incomplete type as the compiler does not know whether your (still uncomplete) type has the member methods/attributes you try to use.

Another issue is how you came to this solution and whether it is a good design creating cyclic dependencies.

---

