---
title: "C++ passing pointers by reference."
date: 2008-11-30
forum: Programming Talk
---

### Post by u-slayer on 2008-11-30
I'm learning C++ and have been passing everything by reference in my programs. When I learned about pointers, I started passing them by reference too: 

```
void func(int*& var )
```

However, I look on the internets and can't find out if this is any faster, or when I would want to do this.

Example:
```

bool open_file(string& name, fstream*& file, char mode)
{
	if ( mode == 'w' || mode == 'W' )
		file = new fstream (name.c_str(), ios::binary |  ios::out);
	else
		file = new fstream (name.c_str(), ios::binary |  ios::in);
	
	//cout << "Filename: " << name << endl;
	if ( ! file )
	{
		cout << "Error: Cannot open file: " << name << endl;
		return false;
	}
	return true;
}

bool read_file(string& name)
{
	fstream* file;
	
	if ( ! open_file(name,file,'W') )
		return false;

	file->close();
	delete file;
	return true;
}


```

What do you guys think?	 \\:D/

---

### Post by dwhitney67 on 2008-12-01
Passing an object by reference is more efficient, although hardly noticeable when passing pointers.  For regular objects, passing by reference saves time because the object needn't be copied to a local variable on the stack.

As for your code, it (almost) looks fine.  However I would recommend that you specify that the file-name being passed to open_file() be declared as a const string reference.  Ditto for read_file().

Also, I just noticed... in open_file(), you do not check if the file was actually opened.  I would suggest that the code contain:
[php]
...

if (file && file->is_open())
{
  return true;
}

return false;
[/php]

Also, if the file cannot be opened in open_file(), delete the memory that was allocated and set file equal to 0 (NULL).  You should also consider setting file equal to 0 when you first declare it.  In read_file(), you should only need to delete the memory for file if you successfully opened the file.

You could also consider using Boost's shared pointer.  When the pointer's reference count reaches zero, it is "automatically" destroyed for you.

---

### Post by CptPicard on 2008-12-01
You aren't really gaining much, because the pass by reference of pointer is essentially implemented by passing pointer-to-pointer by the compiler. As dwhitney said, the gain of using references comes from not having to allocate temporaries on stack, and for primitive value types such as pointers, this cost is negligible.

---

### Post by meastp on 2008-12-01
1. Passing an object by reference is **equal to passing the address of that object**.

2. Passing a pointer to an object 'by value' is **equal to passing the address of that object**.

3. Passing a pointer to an object by reference is equal to passing the address of that pointer.

*If I have understood pointers correctly, that is.*

---

### Post by hod139 on 2008-12-01
> **meastp said:**
> 1. Passing an object by reference is **equal to passing the address of that object**.

2. Passing a pointer to an object 'by value' is **equal to passing the address of that object**.

3. Passing a pointer to an object by reference is equal to passing the address of that pointer.

*If I have understood pointers correctly, that is.*
You have a mis-understanding with your point 2.  Passing a pointer by value will pass a copy of that pointer.  The temp/copied pointer will still point to the object so usually there is no distinction.  The common (only?) example of when passing a pointer by reference versus value is important is when you write a function that allocates memory for the pointer.  I think the code and comments speak for themselves, post back if anything is unclear.

[php]

// Correctly allocates the original pointer, using pass-by-reference (C++ reference)
void allocateByRef(int* &refToPtr, size_t size){
  refToPtr = new int[size];
}

// Correctly allocates the original pointer, using pass-by-reference (C++ pointer)
void allocateByPtr(int** ptrToPtr, size_t size){
  *ptrToPtr = new int[size];
}

// Allocates memory for a temporary copy of the pointer
// This temp is never freed, resulting in a memory leak, and the original 
// pointer has not been allocated
void badAllocate(int* tempCopyOfPtr, size_t size){
  tempCopyOfPtr = new int[size]; // mem leak
}

// main entry point
int main(void)
{
    int *ptr1 = NULL;
    int *ptr2 = NULL;
    int *ptr3 = NULL;
    size_t N = 5;
    
    allocateByRef(ptr1, N);
    allocateByPtr(&ptr2, N);
    badAllocate(ptr3, N);        
    
    ptr1[N-1] = 1;
    ptr2[N-1] = 2;
    //ptr3[N-1] = 3; // BOOM
    
    delete[] ptr1;
    delete[] ptr2;
    delete[] ptr3;
}  
[/php]

---

### Post by meastp on 2008-12-01
Thanks, hod139! I understand.

---

### Post by u-slayer on 2008-12-01
Okay, thanks hod139. I think I understand. So long as you don't allocate memory in your function everything will work the same regard less if you pass pointers by ref or by value.

I tested these two functions and they produce the same result.

Pointer by value:
```
void badAllocate(int* tempCopyOfPtr)
{
	*tempCopyOfPtr = 2171;
}
```

Pointer by Ref:
```
void badAllocate(int*& tempCopyOfPtr)
{
	*tempCopyOfPtr = 2171;
}
```


I modified your code to strip the array and just pass normal ints. Also ptr3 is allocated here now:
```
// main entry point
int main(void)
{
	int *ptr1 = NULL;
	int *ptr2 = NULL;
	int *ptr3 = NULL;

	ptr3 = new int; // not a mem leak
	
	allocateByRef(ptr1);
	allocateByPtr(&ptr2);
	badAllocate(ptr3);        
    
	cout << *ptr1 << endl;
	cout << *ptr2 << endl;
	cout << *ptr3 << endl;
    
	delete ptr1;
	delete ptr2;
	delete ptr3;
}  
```

---

### Post by dwhitney67 on 2008-12-01
There is one subtle difference between passing a pointer and passing a pointer by reference.

If you have a function, for example like this:
[php]
void function(int* ptr)
{
  *ptr = 10;
}
[/php]

You can call it like:
[php]
int* p = new int;

function(p);          // sets the value pointed by p to 10
function(new int);    // causes memory leak
function(0);          // causes program to crash!
[/php]

Now if you declare the function to be as follows (i.e. pass the pointer by reference):
[php]
void function(int*& ptr)
{
  *ptr = 10;
}
[/php]
Then the following holds true:
[php]
int* p = new int;

function(p);          // ok
function(new int);    // application will not compile
function(0);          // application will not compile
[/php]

With this information, feel free to ask yourself which method you think is better.  ;)

---

