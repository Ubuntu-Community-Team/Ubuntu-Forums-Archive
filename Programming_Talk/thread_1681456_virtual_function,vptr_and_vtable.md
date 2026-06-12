---
title: "virtual function,vptr and vtable??"
date: 2011-02-04
forum: Programming Talk
---

### Post by Praveen30 on 2011-02-04
1.how a virtual function is linked with the vptr and vtable??
2.Can we call the virtual functions by using pointer and reference only??what about object??
3.i got to know that virtual function is treated as an option because late binding is very heavy for compilers..is it right???

---

### Post by Arndt on 2011-02-04
> **Praveen30 said:**
> 1.how a virtual function is linked with the vptr and vtable??
2.Can we call the virtual functions by using pointer and reference only??what about object??
3.i got to know that virtual function is treated as an option because late binding is very heavy for compilers..is it right???

The price is paid at runtime, rather. At one time, it probably was the case that making all methods virtual would have slowed down execution significantly. For example Simula-67 also uses the keyword VIRTUAL. Nowadays, this is probably not the case anymore.

---

### Post by slavik on 2011-02-04
all methods in java are virtual by default. all methods in C++ are static.

---

### Post by psusi on 2011-02-04
The vtable contains pointers to all of the virtual functions in a class.  An object of that class contains a pointer to that vtable.  When you call a virtual function, the compiler just dereferences the vtable pointer, and then calls the virtual function via the pointer in the vtable.  That has extremely low overhead.

---

### Post by worksofcraft on 2011-02-04
> **Praveen30 said:**
> 1.how a virtual function is linked with the vptr and vtable??
2.Can we call the virtual functions by using pointer and reference only??what about object??
3.i got to know that virtual function is treated as an option because late binding is very heavy for compilers..is it right???

Some programming languages don't give you the option of having a choice between virtual or static methods and so they would not be a good choice for exploring the concepts.

C++ can do both virtual and non virtual methods, but the vptr and vtable are internal implementation details that are taken care of by the compiler so you cannot easily access them.

Here is example from elsewhere and I removed a few distractions and added some of my own :D

[php]
#include <iostream>
using namespace std;

struct animal {
#ifdef VIRTUAL
	virtual
#endif
		void talk() { cout << "..." << endl; }
};

struct cat: animal {
    void talk() { cout << "Meow!" << endl; }
};

int main(void) {
	cat Garfield, Felix; // Garfield and Felix are cats

	animal *pAnimal = &Garfield; // point to any animal
	cout << "animal:";
	pAnimal->talk(); // animal behavior ?

	cout << "Felix:";
	Felix.talk(); // The compiler does know what Felix is
	
	// the overhead ?	
	cout << "sizeof(Garfield)=" << sizeof(Garfield) << endl;
	return 0;
}
[/php]

Compile and run without virtual methods:
```

$ g++ cat_dog.cpp
$ ./a.out
animal:...
Felix:Meow!
sizeof(Garfield)=1

```

See how the object class is only one byte in size... well actually it doesn't have any data in it, but C++ won't allow 0 size for things (not sure why).

Notice that when using the generic pointer to a cat it has been statically linked to the generic animal talk method.

```

$ g++ -DVIRTUAL cat_dog.cpp
$ ./a.out
animal:Meow!
Felix:Meow!
sizeof(Garfield)=8

```

In the dynamic case it has added a hidden pointer to the object making it 8 bytes long on my 64 bit system. That pointer points to a hidden table containing pointers to all the virtual methods of the class.

That way the object itself can identify the right method even if all the program specifies is a pointer, or reference to the base class object.

This overhead is not always desirable. There are cases when you don't want the extra indirection. Imagine processing the pixels of images in a movie, adding a virtual method to your base pixel class would simply kill performance and make images huge in memory.

The compiler can do many more optimizations on statically linked methods than on virtual ones. e.g. expanding them inline and leaving out the parameter stack.

You might also want to experiment with the "static" keyword here and see if you can work out why a static method can never be virtual ;)

---

### Post by worksofcraft on 2011-02-04
... anyway just out of interest I had a look at the assembler that the compiler generates to call Garfield's talk method... I commented it here:
```

	movq	$Garfield, -8(%rbp) ; initialize animal pointer
	; to object "Garfield"... see this is an "lvalue" even
	; though object "Garfield" hasn't got ANY data in it ;)

	movq	-8(%rbp), %rax ; pointer to Garfield in rax
	movq	(%rax), %rax ; pointer to Garfield's vtable in rax
	movq	(%rax), %rdx ; first entry from vtable to rdx

	movq	-8(%rbp), %rax ; pointer to Garfield again
	movq	%rax, %rdi ; copy it to in rdi
	; a.k.a "this" pointer in C++

	call	*%rdx ; call Garfield'd meow method

```

---

### Post by worksofcraft on 2011-02-08
I was just reading Stroustrup 21.2.3.1 "Virtual Output Functions" and it reminded me of this thread...
What he says there is:

*"The ostream members are not virtual... One reason for this is to achieve close to optimal performance for simple operations such as putting a character into a buffer. This is a place where runtime efficiency is crucial and where inlining is a must..."*

so...
> **worksofcraft said:**
> ... anyway just out of interest I had a look at the assembler that the compiler generates to call Garfield's talk method... I commented it here:
```

	movq	$Garfield, -8(%rbp) ; initialize animal pointer
	; to object "Garfield"... see this is an "lvalue" even
	; though object "Garfield" hasn't got ANY data in it ;)

	movq	-8(%rbp), %rax ; pointer to Garfield in rax
	movq	(%rax), %rax ; pointer to Garfield's vtable in rax
	movq	(%rax), %rdx ; first entry from vtable to rdx

	movq	-8(%rbp), %rax ; pointer to Garfield again
	movq	%rax, %rdi ; copy it to in rdi
	; a.k.a "this" pointer in C++

	call	*%rdx ; call Garfield'd meow method

```

p.s. oh that was with Garfield as a "global" feline entity btw but as you can see virtual method produces  quite a lot of extra instructions besides that "call" :P

---

### Post by psusi on 2011-02-08
> **worksofcraft said:**
> p.s. oh that was with Garfield as a "global" feline entity btw but as you can see virtual method produces  quite a lot of extra instructions besides that "call" :P

It's two extra movs.  That is hardly "a lot" extra.  The only time you will notice is if the function being called is extremely trivial ( only a handful of instructions itself ), and is called millions of times.

---

### Post by worksofcraft on 2011-02-08
> **psusi said:**
> It's two extra movs.  That is hardly "a lot" extra.  The only time you will notice is if the function being called is extremely trivial ( only a handful of instructions itself ), and is called millions of times.

I agree :)

Just for the record, if the function had **not** been virtual the compiler could have inlined it and then it would have used ZERO instructions.

If there had been paramaters then an inlined non-virtual method would not have needed it's own stack frame for them either.

Writing portable yet near optimal code for computers with [von Neumann architecture ]("http://en.wikipedia.org/wiki/Von_Neumann_architecture")is what languages like C and later C++ were designed to do AFIK... but that is a philosophical issue I suspect ;)

---

