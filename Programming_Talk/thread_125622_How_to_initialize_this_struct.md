---
title: "How to initialize this struct"
date: 2006-02-04
forum: Programming Talk
---

### Post by awais on 2006-02-04
How to properly initialize this struct?

static struct file_operations fops = {
	  .read = device_read, 
	  .write = device_write,
	  .open = device_open,
	  .release = device_release
	};

---

### Post by LordHunter317 on 2006-02-04
What language?  C? C++?

If it's C++, use a constructor.

---

### Post by David Marrs on 2006-02-04
That looks all wrong to me. :p

Try:
```
static struct file_operations { /* file_operations namespace optional */
  type read = device_read;
  type write = device_write;
  /* and so on */
};
static struct file_operations fops1, fops2;
```
Often you will see an instance created directly after the struct is declared:
```
struct namespace {
  int size;
  char *text;
} title;

title.text = "hello";
title.size = 12;
```

What you have above I guess could be correct in part (I've never tried compiling a struct as an array before - I will now, though) but read, write and open would still need to have their types defined.

PS. I just tried to compile something like "struct x = {.foo .bar};" and it's definitely not doable.

---

### Post by phx_one on 2007-11-03
hello. I'm not so new to c++, but now got a problem with simple code. when I define new test_struct structure inside main (), it works fine. but when I define global variable of test_struct type and try to initialize one of it's fields, compiler return error on string 

bstr.a = 1;

expected constructor, destructor, or type conversion before ‘.’ token


```
#include <iostream>
#include <cstdlib>
using namespace std;

struct test_struct {
	
	int a;
	int b;
};

//this dont work
test_struct bstruct ();
bstruct.a = 1;


int main(int argc, char *argv[])
{

	//but this works fine
	test_struct astruct;
	astruct.a = 1;
	
	
	exit(EXIT_SUCCESS);
}

```

without definition and initialization of bstruct program works fine. so, what I'm doing wrong?

---

### Post by LaRoza on 2007-11-03
What are you trying to do?

Wouldn't a class be better for this?

---

### Post by smartbei on 2007-11-03
The problem has nothing to do with the struct... You can't set variables value in the global scope. You could do it in the struct's constructor though:
```

#include <iostream>
#include <cstdlib>
using namespace std;
struct test_struct {
	int a;
	int b;
	test_struct();
};

test_struct bstruct;

int main(int argc, char *argv[])
{

	//but this works fine
	cout<<bstruct.a;
	
	
	exit(EXIT_SUCCESS);
}

test_struct::test_struct() {
	a=155;
	b=156;
}

```

To LaRoza - as far as I know the only difference between a c++ class and struct is that in a class members are by default private, whereas in a struct they are by default public. In this case, since he wants to access the variables a and b directly, a struct seems appropriate.

---

### Post by LaRoza on 2007-11-03
> **smartbei said:**
> 
To LaRoza - as far as I know the only difference between a c++ class and struct is that in a class members are by default private, whereas in a struct they are by default public. In this case, since he wants to access the variables a and b directly, a struct seems appropriate.

Yes, I know, but structures in C (where they came from) are very different from C++ stuctures, and are not used to be best of my knowledge in C++ programs often. For the defaults, never use them. Always explicitly state the private/protected/public data and functions.

It just seems odd that structs are being used in a C++ program.

---

### Post by Awalton on 2007-11-03
The structure in question:
```

static struct file_operations fops = {
.read = device_read,
.write = device_write,
.open = device_open,
.release = device_release
};

```
Is from the Linux kernel, specifically it's loading the file_operations structure with function pointers to the various functions it implements. In this case, you're expected to provide the implementations for each of those functions, then add them all to the structure.

It's perfectly legal, and is a way of saying:
```

static struct file_operations fops;
fops.read = device_read;
fops.write = device_write;
...

```
so that you can define it at the module level, instead of having to have a function load the structure. Perhaps the better way of doing that would actually be
```

static struct file_options fopts = {
 read : device_read,
 write : device_write,
 ....

```
As this is another way of expressing the same concept.

---

### Post by phx_one on 2007-11-03
thank you very much!
well, as to why I use struct instead of class... hmm... because class can not be nested... err, at least, they should not. I want to share data between two classes. they could have parental relation, or they can be two different classes, with different parents. as I know, class is not admitted to be used in another class's  method, or in data field. so, if I want to move data from one class to another, I should use struct as most smart solution. or had to use them...

---

