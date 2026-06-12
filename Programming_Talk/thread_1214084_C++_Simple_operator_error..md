---
title: "C++ Simple operator error."
date: 2009-07-15
forum: Programming Talk
---

### Post by fredscripts on 2009-07-15
Hi!

In my class Graph I want to overload operator + (add two Graph objects), so:

(in .hpp)
```

class Graph {
    ...
    const Graph operator+(const Graph& toba) const;
}

```
(in .cpp)
```

const Graph Graph::operator+(const Graph& toba) const {

	Graph pG12; 

	for( Vertex* pv1= G_ov; pv1; pv1=pv1->v_nv )
		pG12.AddVertex( pv1->v_v, pv1->v_x, pv1->v_y );
	for( Vertex *pv2=toba.G_ov; pv2; pv2=pv2->v_nv ) {
		Vertex* pv1;
		for( pv1=G_ov; pv1; pv1=pv1->v_nv )
			if( pv1->v_v == pv2->v_v )
				break;
		if( !pv1 )
			pG12.AddVertex( pv2->v_v, 250+pv2->v_x, pv2->v_y );
	}

	for( Edge *pe1=G_oe; pe1; pe1=pe1->e_ne )
		pG12.AddEdge( pe1->e_e, pe1->e_1v->v_v, pe1->e_2v->v_v, pe1->e_w );
	for( Edge *pe2=toba.G_oe; pe2; pe2=pe2->e_ne )
		pG12.AddEdge( pe2->e_e, pe2->e_1v->v_v, pe2->e_2v->v_v, pe2->e_w );


	return pG12;

 }

```


Then , in other files of the project, I do:

```
StarGraph S; //Simple child class of Graph
CycleGraph C; // Simple child class of Graph
Graph gUnion = S+C;
```

Then, when running, some Adress violation error appears:
```
Unhandled exception at 0x10252758 (msvcr80d.dll) in GCPGL.exe: 0xC0000005: Access violation reading location 0xcdcdcdc1.
```
 Microsoft Visual Studio C++ points me to this line in dbgdel.cpp:
```

           /* verify block type */
            _ASSERTE(_BLOCK_TYPE_IS_VALID(pHead->nBlockUse));
```

I have no idea where the problem could be, seems that it cannot delete the object(gUnion)? Maybe inheritance is doing anything strange here? maybe is just MVS crazy and in Ubuntu with g++ would work?

Thanks in advance.

---

### Post by dwhitney67 on 2009-07-15
Why don't you set a breakpoint in the method, debug the app, then when the breakpoint is hit, step through the code???


Btw, do you remember 8-track tapes??  They went out of "fashion" long ago, along with Hungarian-notation for variable names.  :-)

---

### Post by fredscripts on 2009-07-15
Thanks for answering. I've already posted where the exact error is, in that dbgdel.cpp file on that line.

Thanks for pointing out that my variable names are old-fashioned, will change them. So anyone has any idea what is happening here? anyone could post a simple example of what I want to do that works fine on his/her machine so I can guess if it's a MVS strange error?

Thanks

---

### Post by dwhitney67 on 2009-07-15
Here's a basic program that defines an operator+() method.  Your program employs something similar, thus I do not see a problem with it.

If your program is crashing, it is probably due to your data not being initialized correctly (although you assumed it has), or you are accessing your data incorrectly.

Here's my 5-minute effort:
```

#include <iostream>


class Foo
{
public:
   Foo(int v1 = 0, int v2 = 0) : val1(v1), val2(v2) {}
   Foo(const Foo& other) : val1(other.val1), val2(other.val2) {}

   Foo& operator=(const Foo& other)
   {
      if (this != &other)
      {
         this->val1 = other.val1;
         this->val2 = other.val2;
      }

      return *this;
   }

   const Foo operator+(const Foo& rhs) const
   {
      Foo local;

      local.val1 = this->val1 + rhs.val1;
      local.val2 = this->val2 + rhs.val2;

      return local;
   }

   friend std::ostream& operator<<(std::ostream& os, const Foo& foo)
   {
      os << foo.val1 << ", " << foo.val2;
      return os;
   }

private:
   int val1;
   int val2;
};


int main()
{
  using namespace std;

  Foo foo1(5, 10);
  Foo foo2(10, 5);
  Foo foo3 = foo1 + foo2;

  cout << "foo1 = " << foo1 << endl;
  cout << "foo2 = " << foo2 << endl;
  cout << "foo3 = " << foo3 << endl;
}

```

---

### Post by dribeas on 2009-07-18
The problem you are facing is not with the operator, but with initialization. Visual Studio in debug mode will write 0xcdcdcdcd in all allocated memory before you initialize it. Whenever you hit an access violation dereferencing that pointer the problem is that you are dereferencing an uninitialized pointer. In your case you are not really dereferencing that pointer but 12 positions before that... that probably means that you are initializing the pointer as a relative position with respect to an uninitialized pointer (12 bytes before another pointer).

Check your constructors and the pointer values before the error occurs (use the debugger)

---

### Post by fredscripts on 2009-07-19
Thank you so much for answering.

I thought the problem might be that I had an operator+ but not a operator= implemented, so I tried adding it:

```
class Graph {

...

Graph& operator=(const Graph& other);
const Graph operator+(const Graph& toba) const;

}
```

Then the implementation works as follow (will change variable names as soon as possible):

```
Graph& Graph::operator=(const Graph& other) {
	 if (this != &other)
      {
		for( Vertex* pv1= other.G_ov; pv1; pv1=pv1->v_nv )
			this->AddVertex(pv1->v_v,pv1->v_x,pv1->v_y,pv1->v_z);

		for( Edge *pe1=other.G_oe; pe1; pe1=pe1->e_ne )
			this->AddEdge(pe1->e_e, pe1->e_1v->v_v, pe1->e_2v->v_v, pe1->e_w );


      }
	  return *this;
 }

 const Graph Graph::operator+(const Graph& toba) const {

	Graph pG12; 

	for( Vertex* pv1= G_ov; pv1; pv1=pv1->v_nv )
		pG12.AddVertex( pv1->v_v, pv1->v_x, pv1->v_y );
	for( Vertex *pv2=toba.G_ov; pv2; pv2=pv2->v_nv ) {
		Vertex* pv1;
		for( pv1=G_ov; pv1; pv1=pv1->v_nv )
			if( pv1->v_v == pv2->v_v )
				break;
		if( !pv1 )
			pG12.AddVertex( pv2->v_v, 250+pv2->v_x, pv2->v_y );
	}

	for( Edge *pe1=G_oe; pe1; pe1=pe1->e_ne )
		pG12.AddEdge( pe1->e_e, pe1->e_1v->v_v, pe1->e_2v->v_v, pe1->e_w );
	for( Edge *pe2=toba.G_oe; pe2; pe2=pe2->e_ne )
		pG12.AddEdge( pe2->e_e, pe2->e_1v->v_v, pe2->e_2v->v_v, pe2->e_w );


	return pG12;

 }
```

And still, when in another function in another file of the project I do:

```

StarGraph S(  ); //Simple child class of Graph
CycleGraph C( ); //Simple child class of Graph

Graph gUnion = S+C;
```

I don't even use gUnion anywhere else, nor call any methods or attributes; that function ends and the program continues doing other things and then crashes with that violation error.

I still have the same violation error.


dribeas, thanks for answering. I kinda understand your point but I still can't figure out how to solve this issue. Maybe disabling the debugger? initializing the objects in another way?


Thanks so much again,

---

### Post by fredscripts on 2009-07-19
Hi again,

I've run the program here on Ubuntu 9.04. 

The error here appears of the form:

```
*** glibc detected *** ./gcpgl: free(): invalid pointer: 0xb7dd1560 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7ce1604]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb7ce35b6]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0xb7ec4231]
/usr/lib/libstdc++.so.6(_ZdaPv+0x1d)[0xb7ec428d]
./gcpgl[0x804e112]
./gcpgl[0x804b9f7]
./gcpgl[0x804d179]
./gcpgl[0x8054c9c]
/usr/lib/libglut.so.3[0xb7f0d5bb]
/usr/lib/libglut.so.3(fgEnumWindows+0x43)[0xb7f10ea3]
/usr/lib/libglut.so.3(glutMainLoopEvent+0x690)[0xb7f0df80]
/usr/lib/libglut.so.3(glutMainLoop+0x5d)[0xb7f0e3dd]
./gcpgl[0x8054bd4]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7c88775]
./gcpgl[0x8049751]
======= Memory map: ========
08048000-08057000 r-xp 00000000 08:06 712452     /home/diffred/Desktop/GCPGL_Linux/gcpgl
08057000-08058000 r--p 0000e000 08:06 712452     /home/diffred/Desktop/GCPGL_Linux/gcpgl
08058000-08059000 rw-p 0000f000 08:06 712452     /home/diffred/Desktop/GCPGL_Linux/gcpgl
09906000-09991000 rw-p 09906000 00:00 0          [heap]
b6200000-b6221000 rw-p b6200000 00:00 0 
b6221000-b6300000 ---p b6221000 00:00 0 
b6398000-b639a000 rwxp 00000000 00:0f 728        /dev/zero
b639a000-b639b000 rw-s 00000000 00:09 7667745    /SYSV00000000 (deleted)
b639b000-b6603000 rw-s d0d28000 00:0f 7140       /dev/nvidia0
b6603000-b686b000 rw-s d0504000 00:0f 7140       /dev/nvidia0
b686b000-b686c000 rw-s 00000000 00:09 7634976    /SYSV00000000 (deleted)
b686c000-b696c000 rw-s e0114000 00:0f 7140       /dev/nvidia0
b696c000-b696d000 rw-s 0e003000 00:0f 7140       /dev/nvidia0
b696d000-b6a6f000 rw-p b696d000 00:00 0 
b6a6f000-b6b71000 rw-s e0011000 00:0f 7140       /dev/nvidia0
b6b71000-b6bb2000 rw-p b6b71000 00:00 0 
b6bb2000-b6c15000 rw-p 00000000 00:0f 728        /dev/zero
b6c15000-b7115000 rw-s d0000000 00:0f 7140       /dev/nvidia0
b7115000-b7136000 rw-p b7115000 00:00 0 
b7136000-b7160000 rw-s 00000000 00:09 0          /SYSV00000000 (deleted)
b7160000-b71c5000 rw-p b7160000 00:00 0 
b71c5000-b71c9000 r-xp 00000000 08:03 173684     /usr/lib/libXdmcp.so.6.0.0
b71c9000-b71ca000 rw-p 00003000 08:03 173684     /usr/lib/libXdmcp.so.6.0.0
b71ca000-b71e2000 r-xp 00000000 08:03 174641     /usr/lib/libxcb.so.1.1.0
b71e2000-b71e3000 r--p 00017000 08:03 174641     /usr/lib/libxcb.so.1.1.0
b71e3000-b71e4000 rw-p 00018000 08:03 174641     /usr/lib/libxcb.so.1.1.0
b71e4000-b71e5000 rw-p b71e4000 00:00 0 
b71e5000-b71e7000 r-xp 00000000 08:03 173673     /usr/lib/libXau.so.6.0.0
b71e7000-b71e8000 r--p 00001000 08:03 173673     /usr/lib/libXau.so.6.0.0
b71e8000-b71e9000 rw-p 00002000 08:03 173673     /usr/lib/libXau.so.6.0.0
b71e9000-b71eb000 r-xp 00000000 08:03 245681     /lib/tls/i686/cmov/libdl-2.9.so
b71eb000-b71ec000 r--p 00001000 08:03 245681     /lib/tls/i686/cmov/libdl-2.9.so
b71ec000-b71ed000 rw-p 00002000 08:03 245681     /lib/tls/i686/cmov/libdl-2.9.so
b71ed000-b71ee000 r-xp 00000000 08:03 195508     /usr/lib/tls/libnvidia-tls.so.96.43.10
b71ee000-b71ef000 rw-p 00000000 08:03 195508     /usr/lib/tls/libnvidia-tls.so.96.43.10
b71ef000-b7a3c000 r-xp 00000000 08:03 174920     /usr/lib/libGLcore.so.96.43.10
b7a3c000-b7a71000 rwxp 0084d000 08:03 174920     /usr/lib/libGLcore.so.96.43.10
b7a71000-b7a75000 rwxp b7a71000 00:00 0 
b7a75000-b7b5f000 r-xp 00000000 08:03 173667     /usr/lib/libX11.so.6.2.0
b7b5f000-b7b60000 ---p 000ea000 08:03 173667     /usr/lib/libX11.so.6.2.0
b7b60000-b7b61000 r--p 000ea000 08:03 173667     /usr/lib/libX11.so.6.2.0
b7b61000-b7b63000 rw-p 000eb000 08:03 173667     /usr/lib/libX11.so.6.2.0
b7b63000-b7b65000 rw-p b7b63000 00:00 0 
b7b65000-b7b73000 r-xp 00000000 08:03 173686     /usr/lib/libXext.so.6.4.0
b7b73000-b7b74000 r--p 0000d000 08:03 173686     /usr/lib/libXext.so.6.4.0
b7b74000-b7b75000 rw-p 0000e000 08:03 173686     /usr/lib/libXext.so.6.4.0
b7b75000-b7be4000 r-xp 00000000 08:03 173622     /usr/lib/libGLU.so.1.3.070300
b7be4000-b7be5000 ---p 0006f000 08:03 173622     /usr/lib/libGLU.so.1.3.070300
b7be5000-b7be6000 r--p 0006f000 08:03 173622     /usr/lib/libGLU.so.1.3.070300
b7be6000-b7be7000 rw-p 00070000 08:03 173622     /usr/lib/libGLU.sAborted

```

Should I need to delete that gUnion object? made it static? I can't figure out the problem.

If anyone could help me I would be very grateful.

Thanks in advance.

---

### Post by MadCow108 on 2009-07-19
run the program through valgrind, that maybe gives a hint to the problem.

These kind of problems are very hard to find by just looking at a snippet of code.
I would need a running piece of code to play with to really help you.

---

### Post by dwhitney67 on 2009-07-19
It would appear the OP is attempting to delete an invalid pointer.  He really should not have to delete anything if he were to use smart pointers.

Example:
```

#include <tr1/memory>

class MyClass
{
...
};

typedef std::tr1::shared_ptr<MyClass> MyClassPtr;

int main()
{
   MyClassPtr obj(new MyClass);

   ...

}  // here, when obj goes out of scope, the allocated MyClass object
   // will be destroyed if its reference count is zero.

```

---

### Post by dribeas on 2009-07-19
You are facing initialization and destruction problems. These are hard to debug without the code, so there is only so much we can recommend you to do.

Some general tips:

Make sure that you use constructors, all constructors initialize all members and they do so in the same order that they are declared in the class definition. The compiler will call the initialization code in the initializer list in the order the fields were declared in the class, not the order in which they appear in your constructors' initialization list.

If a class deals with resources (memory or any other), try to encapsulate them using RAII (smart pointers and the like). This is the best you can do, consider std::tr1::shared_ptr (or boost::shared_ptr) as a general solution, or other smart pointers when you cannot use these or your requirements allow you. Fall back to std::auto_ptr if you must, but know the semantics, as they are unnatural.

If you need to provide a destructor then you are handling resources, and that is as much as saying that you must also provide a copy constructor and assignment operators since the implicitly declared ones are of no use (i.e. if a destructor deletes a pointer attribute, and you let the compiler generate copy constructor/operator, then the destructor of the second object will try to free an already freed memory region). Determine whether you want to perform deep or swallow copies, for deep copies implement them, for swallow copies delegate on shared_ptr (boost/std::tr1).

The code seems to use your own (or maybe they are library generated) containers, like lists and the like. Reuse the STL containers, they are tested and will greatly reduce the risk of errors to your logic.

Do not disable the debugger. It is telling you what data is uninitialized, consider that if the bit pattern was not there (the pointer had random data from memory) then it would have been much harder to diagnose a initialization problem, it could be an uninitialized pointer, a pointer that was incorrectly overwritten at a later time or a pointer that was previously freed.

---

