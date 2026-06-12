---
title: "How to identify the architecture ?"
date: 2006-03-19
forum: Programming Talk
---

### Post by gborzi on 2006-03-19
Maybe this question is quite dumb, but I'm new to AMD64 programming. I have the following C++ code:

[FONT="Fixedsys"]template<typename T> class array {
   public:
      typedef T baseT;
      typedef _array_iter< array<T> > iterT;
      array() : n_(0), data_(0) {}
      array( size_t n ) : n_(n) { data_ = new T[n_]; }
      array( int n ) : n_(n) { data_ = new T[n_]; }
//      array( unsigned int n ) : n_(n) { data_ = new T[n_]; }
      array( unsigned short n ) : n_(n) { data_ = new T[n_]; }
      array( unsigned char n ) : n_(n) { data_ = new T[n_]; }
.....
      template<typename U> array( U rhs ) : n_(0), data_(0) {
         rhs.assign(*this);
      }
.....
};[/FONT]

on 32-bit architectures the constructors taking *size_t* and *unsigned int* are the same because *size_t* is actually an *unsigned int* on them. So I need to comment out one of the two.
But on 64-bit architectures *size_t* is not an *unsigned int*, so I need both constructors. For example, without the constructor with *unsigned int* with a code such as

[FONT="Fixedsys"] unsigned int n = 10; array<double> v(n); [/FONT]

the compiler will try to apply the last constructor ( [FONT="Fixedsys"]template<typename U> array( U rhs )[/FONT] )
and will issue an error.
Is there some macro that identify the architecture, so that I can write the same code for both architectures, i.e. something like:
[FONT="Fixedsys"]template<typename T> class array {
   public:
      typedef T baseT;
      typedef _array_iter< array<T> > iterT;
      array() : n_(0), data_(0) {}
      array( size_t n ) : n_(n) { data_ = new T[n_]; }
      array( int n ) : n_(n) { data_ = new T[n_]; }
#ifdef <macro for 64-bit>
      array( unsigned int n ) : n_(n) { data_ = new T[n_]; }
#endif
      array( unsigned short n ) : n_(n) { data_ = new T[n_]; }
      array( unsigned char n ) : n_(n) { data_ = new T[n_]; }
.....
      template<typename U> array( U rhs ) : n_(0), data_(0) {
         rhs.assign(*this);
      }
.....
};[/FONT]

I know I can modify the makefile so as to define a macro that does the trick, but I would like to have the same code and makefile. Moreover, I think that there should be some macro already defined.

Thanks in advance for your help.

---

### Post by LordHunter317 on 2006-03-19
You have two options:[list=1][*]Pick a datatype and use it consistently.  In otherwise, ignore the fact that unsigned int and size_t are the same on x86 and pretend they aren't.  Use size_t everywhere you must construct the object.  This has its pros and cons: one thing to note is that if you write these objects out to disk in anywhere in binary form that the format will not be the same for both arches.[*]Define via a macro a common datatype.  Hunting around in the GCC manual should show you how, as I forget off hand.  This also has its pros and cons.[/list]

In either case, the declaration of the class shouldn't change based on architecture.  IOW, if you're changing what constructors are included via #if/#else/#endif, your approach is wrong.

---

### Post by hod139 on 2006-03-19
I'm assuming you are using GCC, and they define _LP64 which
> 
These macros are defined, with value 1, if (and only if) the compilation is for a target where long int and pointer both use 64-bits and int uses 32-bit.
 
For a full list of predefined GCC macros on your machine you can type:
touch foo.h; cpp -dM foo.h
assuming of course that foo.h doesn't exist.

For instance, on my Athlon64 I get the following 64-bit related macros pre-defined
#define __x86_64 1
#define __x86_64__ 1
#define _LP64 1
#define __LP64__ 1
#define __amd64 1
But, if the manual is any guide, the only one you can trust across various architectures is _LP64.

Also, these macros won't work on another compiler, say MVC, as it will have its own set of predefined macros.

---

### Post by gborzi on 2006-03-19
Thanks a lot, hod139. You have solved my problem.

One last question. How can I close this thread ?

---

