---
title: "[SOLVED] C++ question"
date: 2008-07-23
forum: Programming Talk
---

### Post by ceclauson on 2008-07-23
Hello!

I'm a bit new to C++, and I'm having trouble accessing the members of objects stored in automatic memory (i.e., in function scope).

My understanding of objects in C++ is that you use the dot (.) operator to access members (as in myObject.method()), unless the variable is a pointer, in which case you use the pointer-to-member operator (->) (as in myObjectP->method()).

The second way works fine for me, it's what I've been doing so far, but the first way causes a compile error.

Here's the code I'm trying to compile:
```

#include <iostream>

class MyClass {
	
	public:
		void myMethod() {
			std::cout << "Method called" << std::endl;
		}
		
};

int main() {
	
	//allocate an object in dynamic
	//memory, call the method
	MyClass* objp = new MyClass();
	objp->myMethod();	//works fine
	
	//allocate an object in automatic
	//memory
	MyClass obj();
	obj.myMethod();		//this line causes a
				//compile-time error
	
	return 0;
}

```

Here's the error I get:
```

make -k all 
g++ objstorage.cpp
objstorage.cpp:21:2: warning: no newline at end of file
objstorage.cpp: In function ‘int main()’:
objstorage.cpp:18: error: request for member ‘myMethod’ in ‘obj’, which is of non-class type ‘MyClass ()()’
make: *** [all] Error 1

```

I'm a bit baffled by this, because the code here looks like what the code in my book does.  I'd much appreciate any enlightenment that can be shed on this issue.

Thanks in advance,
Cooper

---

### Post by LaRoza on 2008-07-23
[php]
#include <iostream>

class MyClass 
{
	public:
		void myMethod() 
        {
			std::cout << "Method called" << std::endl;
		}
		
};

int main() 
{
	
	//allocate an object in dynamic
	//memory, call the method
	MyClass* objp = new MyClass();
	objp->myMethod();	//works fine
	
	//allocate an object in automatic
	//memory
	MyClass obj;
	obj.myMethod();

	
	return 0;
}
[/php]

---

### Post by StOoZ on 2008-07-23
ignore..solved above

---

### Post by LaRoza on 2008-07-23
> **StOoZ said:**
> try this

My way is better.

---

### Post by Canis familiaris on 2008-07-23
> **LaRoza said:**
> [php]

	MyClass* objp = new MyClass()

[/php]

Why the brackets there? :confused:

---

### Post by StOoZ on 2008-07-23
> **LaRoza said:**
> My way is better.

LOL :lolflag:

I wrote the same thing u did , but when I submitted it , I saw that u already answered , so I deleted my code.

---

### Post by LaRoza on 2008-07-23
> **StOoZ said:**
> LOL

I wrote the same thing u did , but when I submitted it , I saw that u already answered , so I deleted my code.

Yeah, you ruined the joke...

---

### Post by dribeas on 2008-07-23
> **ceclauson said:**
> ```

	MyClass obj();   // *
	obj.myMethod();		//this line causes a

```


As previously posted by LaRoza:

> **LaRoza said:**
> [php]
	MyClass obj;
	obj.myMethod();
[/php]

The rationale behind this is that whenever the compiler finds the first snippet of code (*) it gets confused and instead of consider that line as the definition of obj as an object of type MyClass it believes that it is the definition of a function that receives void and returns MyClass, as explained (if not too clearly though) in [C++FAQ Lite]("http://www.parashift.com/c++-faq-lite/ctors.html").

Sometimes it is hard understanding compiler errors, but g++ is telling you:
```
objstorage.cpp:18: error: request for member ‘myMethod’ in ‘obj’, which is of non-class type ‘MyClass ()()’
```

obj is of non-class type 'function receiving void and returning MyClass'.

---

### Post by ceclauson on 2008-07-23
Thanks so much!

-Cooper

---

