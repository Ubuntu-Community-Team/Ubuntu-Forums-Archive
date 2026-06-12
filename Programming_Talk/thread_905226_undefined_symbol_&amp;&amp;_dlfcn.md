---
title: "undefined symbol &amp;&amp; dlfcn"
date: 2008-08-30
forum: Programming Talk
---

### Post by hamid206 on 2008-08-30
I wrote a simple shared library . 
library code
```

#include <iostream>
using namespace std ;
void print_name()
{
cout<<"My Name is : JOHN ";
}

```
compile command
```
g++  -fPIC -shared libmy_name.cpp -o libmy_name.so 
```
But when I want to run it dynamical in my program , the following massage display 

program
```

#include <iostream>
#include <dlfcn.h>
using namespace std ;
int main()
{
	void *handle;
	char *error;
	void (*print_name)();
		handle = dlopen("libmy_name.so",RTLD_LAZY);
	if(error = dlerror()) {
    		cout<<error<<"\n";
    		return 0;
				}
	print_name=(void (*)())dlsym(handle,"print_name");
	if(error = dlerror()) {
    			cout<<error<<"\n";
    			return 0;
			      }

	dlclose(handle);
return 0;
}

```

compile
```
g++ -rdynamic test.cpp -o test -ldl
```
 massage
```
usr/lib/libmy_name.so: undefined symbol: print_name
```
I dont know where the problem is . can anyone help me with this problem ?

---

### Post by mike_g on 2008-08-30
IIRC you need to declare the print_name function as extern so that it can be called by other libs/progs. IE:

```
extern void print_name()
{
cout<<"My Name is : JOHN ";
}
```

Edit: also, here:
> g++  -fPIC -shared libmy_name.cpp -o libmy_name.so
you are createing a shared object, but its not called dl:
> g++ -rdynamic test.cpp -o test -ldl

---

### Post by hamid206 on 2008-08-30
I did the work you saied but my problem insists . it connects to library but not able to recive name function .

---

### Post by mike_g on 2008-08-30
Yeah, I had problems getting shared libraries to work at first. I managed to get mine working following this tutorial:
[http://www.linux.org/docs/ldp/howto/Program-Library-HOWTO/shared-libraries.html](http://www.linux.org/docs/ldp/howto/Program-Library-HOWTO/shared-libraries.html)

Edit: I think the extern thing may be wrong actually.

---

### Post by generalguy on 2008-08-30
C++ mangles names. print_name in that is actually _Z10print_namev (at least when dumped by nm).

If you want to be sure that the name of the function is ok, use C, or declare it as extern "C".


Run:

```

nm libmy_name.so 

```

And you should see all the symbols being exported. Adding just extern didn't change the symbol as far as i could tell, but making it :
```

extern "C" void print_name ...

```

makes gcc not mangle it.

```

nm libmy_name.so | grep print_name

```

For quickie access.

Now to demangle the name for human consumption, if you didn't declare it as extern "C", pipe it through c++filt like so:

```
 nm libmy_name.so | grep "print_name" | c++filt 
```

---

### Post by generalguy on 2008-08-30
To mike_g: the -ldl part in the compile line of the test.cpp tells gcc to link in the dynamic library handling code for dlopen etc.

---

