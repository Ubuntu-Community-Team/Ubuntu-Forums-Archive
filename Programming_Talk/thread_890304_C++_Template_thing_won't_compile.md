---
title: "C++ Template thing won't compile"
date: 2008-08-14
forum: Programming Talk
---

### Post by Afoot on 2008-08-14
Here's the code: [https://gist.github.com/036292304db1be9bdc13](https://gist.github.com/036292304db1be9bdc13)

Compiler: gcc (GCC) 4.2.3 (Ubuntu 4.2.3-2ubuntu7)

This is the error message:
```

/tmp/cc5yomOE.o: In function `main':
main.cpp:(.text+0x6aa): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> > Utils::toString<int>(int)'
collect2: ld returned 1 exit status
```

Thanks!

---

### Post by hod139 on 2008-08-14
You cannot split a templated function into a declaration (.h) and implementation (.cpp) like standard C++ code.  You either have to [specialize]("http://www.cprogramming.com/tutorial/template_specialization.html") it, or keep it entirely in the header.

---

### Post by Jessehk on 2008-08-14
All function and class templates have to be defined inline (ie, when you declare them). Move the implementation to the header file and delete utils.cpp.

EDIT: Oops, hod139 beat me.

---

### Post by Afoot on 2008-08-14
Ah!! Thanks.

---

### Post by dwhitney67 on 2008-08-15
> **Jessehk said:**
> All function and class templates have to be defined inline (ie, when you declare them). Move the implementation to the header file and delete utils.cpp.

EDIT: Oops, hod139 beat me.
Not entirely true.  One can separate the definition and the implementation into separate files, however in this situation, the implementation file is required to be included within the header file.

Here's a simple example...

Template.hpp:
[PHP]#ifndef TEMPLATE_H
#define TEMPLATE_H

template< class T >
class Template
{
  public:
    Template( const T & value );

    T getValue() const;

  private:
    T m_value;
};

#include "TemplateImpl.cpp"    // include implementation here

#endif[/PHP]

TemplateImpl.cpp:
[PHP]template< class T >
Template<T>::Template( const T & value )
  : m_value(value)
{
}

template< class T >
T Template<T>::getValue() const
{
  return m_value;
}[/PHP]

Main.cpp:
[PHP]#include "Template.hpp"
#include <iostream>

int main()
{
  Template<int> temp( 5 );
  std::cout << temp.getValue() << std::endl;
  return 0;
}[/PHP]
To compile all this:
```
$ g++ Main.cpp
```

---

### Post by hod139 on 2008-08-15
> **dwhitney67 said:**
> Not entirely true.  One can separate the definition and the implementation into separate file<snip>
This raises a question for me.  Given this file
[php]
///
/// Class interface
///
template< class T >
class Template1
{
  public:
    Template1( const T & value );

    T getValue() const;

  private:
    T m_value;
}; 

///
/// Now actually implement the functions
///
template< class T >
Template1<T>::Template1( const T & value )
  : m_value(value)
{
}

template< class T >
T Template1<T>::getValue() const
{
  return m_value;
}  


///
/// Implement the functions in the interface
///
template< class T >
class Template2
{
  public:
    Template2( const T & value ) : m_value(value) { }

    T getValue() const {  return m_value; }

  private:
    T m_value;
};
[/php]

To the user, there is absolutely no difference between the classes Template1 and Template2.  What about to the compiler?  I'm interested in the details of how the class member functions are being created.

---

### Post by Zugzwang on 2008-08-15
> **hod139 said:**
> To the user, there is absolutely no difference between the classes Template1 and Template2.  What about to the compiler?  I'm interested in the details of how the class member functions are being created.

To find it out, you need some knowledge of assembler. I give you an example. I put the following into a file called test.cpp:
[PHP]
#include <iostream>

///
/// Class interface
///
template< class T >
class Template1
{
  public:
    Template1( const T & value );

    T getValue() const;

  private:
    T m_value;
}; 

///
/// Now actually implement the functions
///
template< class T >
Template1<T>::Template1( const T & value )
  : m_value(value)
{
}

template< class T >
T Template1<T>::getValue() const
{
  return m_value;
}  


///
/// Implement the functions in the interface
///
template< class T >
class Template2
{
  public:
    Template2( const T & value ) : m_value(value) { }

    T getValue() const {  return m_value; }

  private:
    T m_value;
};  

int main()
{
  
  Template1<int> temp( 5 );
  std::cout << temp.getValue() << std::endl;
  
  int m = 77;
  
  Template2<int> temp2( 5 );
  std::cout << temp2.getValue() << std::endl;
    
  
  return 0;
}
[/PHP]
This is a mixture of code posted above. Then I compiled it to assembler:
```

g++ -S test.cpp

```
And then test.s contained (on a 32-bit machine):
```

	.file	"test.cpp"
	.section	.ctors,"aw",@progbits
	.align 4
	.long	_GLOBAL__I_main
	.section	.text._ZN9Template1IiEC1ERKi,"axG",@progbits,_ZN9Template1IiEC1ERKi,comdat
	.align 2
	.weak	_ZN9Template1IiEC1ERKi
	.type	_ZN9Template1IiEC1ERKi, @function
_ZN9Template1IiEC1ERKi:
.LFB1412:
	pushl	%ebp
.LCFI0:
	movl	%esp, %ebp
.LCFI1:
	movl	12(%ebp), %eax
	movl	(%eax), %edx
	movl	8(%ebp), %eax
	movl	%edx, (%eax)
	popl	%ebp
	ret
.LFE1412:
	.size	_ZN9Template1IiEC1ERKi, .-_ZN9Template1IiEC1ERKi
.globl __gxx_personality_v0
	.section	.text._ZNK9Template1IiE8getValueEv,"axG",@progbits,_ZNK9Template1IiE8getValueEv,comdat
	.align 2
	.weak	_ZNK9Template1IiE8getValueEv
	.type	_ZNK9Template1IiE8getValueEv, @function
_ZNK9Template1IiE8getValueEv:
.LFB1413:
	pushl	%ebp
.LCFI2:
	movl	%esp, %ebp
.LCFI3:
	movl	8(%ebp), %eax
	movl	(%eax), %eax
	popl	%ebp
	ret
.LFE1413:
	.size	_ZNK9Template1IiE8getValueEv, .-_ZNK9Template1IiE8getValueEv
	.section	.text._ZN9Template2IiEC1ERKi,"axG",@progbits,_ZN9Template2IiEC1ERKi,comdat
	.align 2
	.weak	_ZN9Template2IiEC1ERKi
	.type	_ZN9Template2IiEC1ERKi, @function
_ZN9Template2IiEC1ERKi:
.LFB1417:
	pushl	%ebp
.LCFI4:
	movl	%esp, %ebp
.LCFI5:
	movl	12(%ebp), %eax
	movl	(%eax), %edx
	movl	8(%ebp), %eax
	movl	%edx, (%eax)
	popl	%ebp
	ret
.LFE1417:
	.size	_ZN9Template2IiEC1ERKi, .-_ZN9Template2IiEC1ERKi
	.section	.text._ZNK9Template2IiE8getValueEv,"axG",@progbits,_ZNK9Template2IiE8getValueEv,comdat
	.align 2
	.weak	_ZNK9Template2IiE8getValueEv
	.type	_ZNK9Template2IiE8getValueEv, @function
_ZNK9Template2IiE8getValueEv:
.LFB1418:
	pushl	%ebp
.LCFI6:
	movl	%esp, %ebp
.LCFI7:
	movl	8(%ebp), %eax
	movl	(%eax), %eax
	popl	%ebp
	ret
.LFE1418:
	.size	_ZNK9Template2IiE8getValueEv, .-_ZNK9Template2IiE8getValueEv
	.text
	.align 2
	.type	_Z41__static_initialization_and_destruction_0ii, @function
_Z41__static_initialization_and_destruction_0ii:
.LFB1421:
	pushl	%ebp
.LCFI8:
	movl	%esp, %ebp
.LCFI9:
	subl	$24, %esp
.LCFI10:
	movl	%eax, -4(%ebp)
	movl	%edx, -8(%ebp)
	cmpl	$1, -4(%ebp)
	jne	.L13
	cmpl	$65535, -8(%ebp)
	jne	.L13
	movl	$_ZSt8__ioinit, (%esp)
	call	_ZNSt8ios_base4InitC1Ev
	movl	$__dso_handle, 8(%esp)
	movl	$0, 4(%esp)
	movl	$__tcf_0, (%esp)
	call	__cxa_atexit
.L13:
	leave
	ret
.LFE1421:
	.size	_Z41__static_initialization_and_destruction_0ii, .-_Z41__static_initialization_and_destruction_0ii
	.align 2
	.type	_GLOBAL__I_main, @function
_GLOBAL__I_main:
.LFB1423:
	pushl	%ebp
.LCFI11:
	movl	%esp, %ebp
.LCFI12:
	subl	$8, %esp
.LCFI13:
	movl	$65535, %edx
	movl	$1, %eax
	call	_Z41__static_initialization_and_destruction_0ii
	leave
	ret
.LFE1423:
	.size	_GLOBAL__I_main, .-_GLOBAL__I_main
	.align 2
	.type	__tcf_0, @function
__tcf_0:
.LFB1422:
	pushl	%ebp
.LCFI14:
	movl	%esp, %ebp
.LCFI15:
	subl	$8, %esp
.LCFI16:
	movl	$_ZSt8__ioinit, (%esp)
	call	_ZNSt8ios_base4InitD1Ev
	leave
	ret
.LFE1422:
	.size	__tcf_0, .-__tcf_0
	.align 2
.globl main
	.type	main, @function
main:
.LFB1405:
	leal	4(%esp), %ecx
.LCFI17:
	andl	$-16, %esp
	pushl	-4(%ecx)
.LCFI18:
	pushl	%ebp
.LCFI19:
	movl	%esp, %ebp
.LCFI20:
	pushl	%ecx
.LCFI21:
	subl	$52, %esp
.LCFI22:
	movl	$5, -16(%ebp)
	leal	-16(%ebp), %eax
	movl	%eax, 4(%esp)
	leal	-20(%ebp), %eax
	movl	%eax, (%esp)
	call	_ZN9Template1IiEC1ERKi
	leal	-20(%ebp), %eax
	movl	%eax, (%esp)
	call	_ZNK9Template1IiE8getValueEv
	movl	%eax, 4(%esp)
	movl	$_ZSt4cout, (%esp)
	call	_ZNSolsEi
	movl	$_ZSt4endlIcSt11char_traitsIcEERSt13basic_ostreamIT_T0_ES6_, 4(%esp)
	movl	%eax, (%esp)
	call	_ZNSolsEPFRSoS_E
	movl	$77, -8(%ebp)
	movl	$5, -12(%ebp)
	leal	-12(%ebp), %eax
	movl	%eax, 4(%esp)
	leal	-24(%ebp), %eax
	movl	%eax, (%esp)
	call	_ZN9Template2IiEC1ERKi
	leal	-24(%ebp), %eax
	movl	%eax, (%esp)
	call	_ZNK9Template2IiE8getValueEv
	movl	%eax, 4(%esp)
	movl	$_ZSt4cout, (%esp)
	call	_ZNSolsEi
	movl	$_ZSt4endlIcSt11char_traitsIcEERSt13basic_ostreamIT_T0_ES6_, 4(%esp)
	movl	%eax, (%esp)
	call	_ZNSolsEPFRSoS_E
	movl	$0, %eax
	addl	$52, %esp
	popl	%ecx
	popl	%ebp
	leal	-4(%ecx), %esp
	ret
.LFE1405:
	.size	main, .-main
	.local	_ZSt8__ioinit
	.comm	_ZSt8__ioinit,1,1
	.weakref	_Z20__gthrw_pthread_oncePiPFvvE,pthread_once
	.weakref	_Z27__gthrw_pthread_getspecificj,pthread_getspecific
	.weakref	_Z27__gthrw_pthread_setspecificjPKv,pthread_setspecific
	.weakref	_Z22__gthrw_pthread_createPmPK14pthread_attr_tPFPvS3_ES3_,pthread_create
	.weakref	_Z22__gthrw_pthread_cancelm,pthread_cancel
	.weakref	_Z26__gthrw_pthread_mutex_lockP15pthread_mutex_t,pthread_mutex_lock
	.weakref	_Z29__gthrw_pthread_mutex_trylockP15pthread_mutex_t,pthread_mutex_trylock
	.weakref	_Z28__gthrw_pthread_mutex_unlockP15pthread_mutex_t,pthread_mutex_unlock
	.weakref	_Z26__gthrw_pthread_mutex_initP15pthread_mutex_tPK19pthread_mutexattr_t,pthread_mutex_init
	.weakref	_Z26__gthrw_pthread_key_createPjPFvPvE,pthread_key_create
	.weakref	_Z26__gthrw_pthread_key_deletej,pthread_key_delete
	.weakref	_Z30__gthrw_pthread_mutexattr_initP19pthread_mutexattr_t,pthread_mutexattr_init
	.weakref	_Z33__gthrw_pthread_mutexattr_settypeP19pthread_mutexattr_ti,pthread_mutexattr_settype
	.weakref	_Z33__gthrw_pthread_mutexattr_destroyP19pthread_mutexattr_t,pthread_mutexattr_destroy
	.section	.eh_frame,"a",@progbits
.Lframe1:
	.long	.LECIE1-.LSCIE1
.LSCIE1:
	.long	0x0
	.byte	0x1
	.string	"zP"
	.uleb128 0x1
	.sleb128 -4
	.byte	0x8
	.uleb128 0x5
	.byte	0x0
	.long	__gxx_personality_v0
	.byte	0xc
	.uleb128 0x4
	.uleb128 0x4
	.byte	0x88
	.uleb128 0x1
	.align 4
.LECIE1:
.LSFDE9:
	.long	.LEFDE9-.LASFDE9
.LASFDE9:
	.long	.LASFDE9-.Lframe1
	.long	.LFB1421
	.long	.LFE1421-.LFB1421
	.uleb128 0x0
	.byte	0x4
	.long	.LCFI8-.LFB1421
	.byte	0xe
	.uleb128 0x8
	.byte	0x85
	.uleb128 0x2
	.byte	0x4
	.long	.LCFI9-.LCFI8
	.byte	0xd
	.uleb128 0x5
	.align 4
.LEFDE9:
.LSFDE11:
	.long	.LEFDE11-.LASFDE11
.LASFDE11:
	.long	.LASFDE11-.Lframe1
	.long	.LFB1423
	.long	.LFE1423-.LFB1423
	.uleb128 0x0
	.byte	0x4
	.long	.LCFI11-.LFB1423
	.byte	0xe
	.uleb128 0x8
	.byte	0x85
	.uleb128 0x2
	.byte	0x4
	.long	.LCFI12-.LCFI11
	.byte	0xd
	.uleb128 0x5
	.align 4
.LEFDE11:
.LSFDE13:
	.long	.LEFDE13-.LASFDE13
.LASFDE13:
	.long	.LASFDE13-.Lframe1
	.long	.LFB1422
	.long	.LFE1422-.LFB1422
	.uleb128 0x0
	.byte	0x4
	.long	.LCFI14-.LFB1422
	.byte	0xe
	.uleb128 0x8
	.byte	0x85
	.uleb128 0x2
	.byte	0x4
	.long	.LCFI15-.LCFI14
	.byte	0xd
	.uleb128 0x5
	.align 4
.LEFDE13:
.LSFDE15:
	.long	.LEFDE15-.LASFDE15
.LASFDE15:
	.long	.LASFDE15-.Lframe1
	.long	.LFB1405
	.long	.LFE1405-.LFB1405
	.uleb128 0x0
	.byte	0x4
	.long	.LCFI17-.LFB1405
	.byte	0xc
	.uleb128 0x1
	.uleb128 0x0
	.byte	0x9
	.uleb128 0x4
	.uleb128 0x1
	.byte	0x4
	.long	.LCFI18-.LCFI17
	.byte	0xc
	.uleb128 0x4
	.uleb128 0x4
	.byte	0x4
	.long	.LCFI19-.LCFI18
	.byte	0xe
	.uleb128 0x8
	.byte	0x85
	.uleb128 0x2
	.byte	0x4
	.long	.LCFI20-.LCFI19
	.byte	0xd
	.uleb128 0x5
	.byte	0x4
	.long	.LCFI21-.LCFI20
	.byte	0x84
	.uleb128 0x3
	.align 4
.LEFDE15:
	.ident	"GCC: (GNU) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)"
	.section	.note.GNU-stack,"",@progbits

```
Not that's hard to read, isn't it? However, note that the labels "_ZN9Template1IiEC1ERKi:" and "_ZN9Template2IiEC1ERKi:" are the definitions for the constructors of your templates. Guess what? They are identical. And so are the other functions.

However, I must admit that things may change once you have virtual methods. I've never used them for templates, so I don't have a clue whether that's possible and what will happen there.

---

### Post by hod139 on 2008-08-15
> **Zugzwang said:**
> To find it out, you need some knowledge of assembler. I give you an example. I put the following into a file called test.cpp:<snip>

Thanks, but that doesn't quite answer my question.  I expected the compiler to produce similar (if not the same) assembly.  I'm more interested in what the compiler has to do though.  

For a more concrete example of what I am saying
[php]
template< class T >
class Template1
{
  public:
    Template1( const T & value);

    T getValue() const;

  private:
    T m_value;
    int val;
}; 

template< class S >
Template1<S>::Template1( const S & value )
  : m_value(value)
{
}

template< class S >
S Template1<S>::getValue() const
{
  return m_value;
}
[/php]

The templated type (T in the definition, S in the implementation) is different.  Does this mean the compiler first make a class for a given type, and then specialize a method for the same given type (the two 'S' and 'T' eventually resolve to the same type)?

When the methods are defined inside the class, the template parameter is the same.  It is this difference that I am interested in, and the effect (if any) it has on the code.

---

### Post by dwhitney67 on 2008-08-15
Hod139,

I'm sure you have already tried compiling/running your experimental code, right?

Well, I took the code I submitted earlier, edited the implementation file, substituting the 'T' for an 'S', and the code still compiled and ran as expected.

I'm not sure what answer you are looking to get concerning the "effect" this has on the code.

---

### Post by hod139 on 2008-08-15
> **dwhitney67 said:**
> Hod139,

I'm sure you have already tried compiling/running your experimental code, right?

Well, I took the code I submitted earlier, edited the implementation file, substituting the 'T' for an 'S', and the code still compiled and ran as expected.

I'm not sure what answer you are looking to get concerning the "effect" this has on the code.

I know the end result of the class is identical, I'm more interested in what the compiler has to do to generate the code.  Maybe this code example will better illustrate my confusion:

[php]
#pragma once

#include <iosfwd>

///
///
///
template< typename T >
class Template1
{
  public:
    Template1( const T & value);

    T getValue() const;
    
    template<class S>
    friend std::ostream& operator<< (std::ostream &os, const Template1<S> &me);

  private:
    T m_value;
    int val;
}; 

template< class S >
Template1<S>::Template1( const S & value )
  : m_value(value)
{
}

template< class S >
S Template1<S>::getValue() const
{
  return m_value;
}  


template< class S >
std::ostream &operator<<(std::ostream &os, const Template1<S> &me)
{
  return os << me.m_value;
}


///
///
///
template< class T >
class Template2
{
  public:
    Template2( const T & value = 0) : m_value(value) { }

    T getValue() const {  return m_value; }  
    
    friend std::ostream& operator<< (std::ostream &os, const Template2<T>& me)
    {
       return os << me.m_value;
    } 
    
  private:
    T m_value;
}; 
[/php][php]
#include "templates.h"
#include <iostream>

int main(void){

  Template1<int> temp1(5);
  Template2<double> temp2(1.0);
  
  std::cout << "temp1 value = " << temp1.getValue() << "\n";
  std::cout << "temp1 = " << temp1 << "\n";
  std::cout << "temp2 value = " << temp2.getValue() << "\n";
  std::cout << "temp2 = " << temp2 << "\n";

  return 0;
}
[/php]The resulting programs will of course produce the same output:

```

 ./a.out 
temp1 value = 5
temp1 = 5
temp2 value = 1
temp2 = 1

```But the compiler obviously has to do something different.  I am just curious about what gcc has to do.  Breaking apart the definition and implementation always the better option with standard code, since it makes the class prototype much easier to read.  I'm just wonder what effects (on the compiler) it has when the class is templated and if anything could break.

---

### Post by dwhitney67 on 2008-08-15
I'm sure the answer lies somewhere in the Stroustrup book, a book that I tossed away a long time ago.

As far as I can tell the "variable" 'T' (or 'S') is treated as a placeholder for the data type that is used to instantiate the template class.  It is used throughout the class definition.  For a friend function, these functions are defined within the class but are not part of the class.  They are in essence a C-style function that will be implemented elsewhere.  Thus one can choose to use the same template "variable" or choose another.

If template class methods are implemented outside the class, then the template "variable" used with these methods is local to the method implementation.  Once again, this "variable" does not have to be the same used in the class definition.

As I write this, I'm sure all of this is obvious from experimenting with the code you wrote.  As to what the compiler is doing, I don't have a clue.  I am simply satisfied to know that it works!

---

### Post by DavidBell on 2008-08-15
> **hod139 said:**
> But the compiler obviously has to do something different.  I am just curious about what gcc has to do.... I'm just wonder what effects (on the compiler)

I think it's all the same, I've always assumed templates are just a more sophisticated version of the precompiler that gets applied before the main compile, so when you instance Template1<int> all the Ts get substituted with ints before it compiles. 

I do know with at least one version of gcc when you instance for eg Template1<int> and Template<float> that part of the compiled code roughly doubles in size, even when you optimise for small size, just as if you had written out two complete class definitions by hand. That seems to say there is no trickery going on in the compile.

HTH DB

---

