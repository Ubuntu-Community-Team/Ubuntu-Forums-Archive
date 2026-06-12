---
title: "What happens when you declare a pointer in c or c++?"
date: 2008-12-19
forum: Programming Talk
---

### Post by night_fox on 2008-12-19
when you declare a pointer in c or c++, it has some crazy nonzero value. Does this value point to anything?

---

### Post by Zugzwang on 2008-12-19
> **night_fox said:**
> when you declare a pointer in c or c++, it has some crazy nonzero value. Does this value point to anything?

In C or C++, if you declare a pointer (or anything else in C or anything else that does not have a constructor in C++), some memory is reserved for the pointer (usually on the stack). However, the pointer is not initialised, meaning that it points to the address corresponding to what was in the respective memory location last. This is not Java, in which every pointer is set to NULL when declaring it.

---

### Post by Bachstelze on 2008-12-19
In other words, you should never assume things to have a specific value unless it was explicitly set (by yourself or by a constructor).

---

### Post by CptPicard on 2008-12-19
No, it doesn't. Values that are uninitialized contain just whatever happens to be in RAM at that location.

---

### Post by kcode on 2008-12-19
> **Zugzwang said:**
> In C or C++, if you declare a pointer (or anything else in C or anything else that does not have a constructor in C++), some memory is reserved for the pointer (usually on the stack). However, the pointer is not initialised, meaning that it points to the address corresponding to what was in the respective memory location last. This is not Java, in which every pointer is set to NULL when declaring it.

Then what advantage does Java achieve while initializing pointer to NULL when declaring it? I've seen people initializing pointer to NULL, in C, as soon as they declare it. Why doesn't C has this feature by default?

Thanks

---

### Post by kcode on 2008-12-19
> **CptPicard said:**
> No, it doesn't. Values that are uninitialized contain just whatever happens to be in RAM at that location.
Can you elaborate it a bit more...Thanks

The size of memory allocated to the pointer variable will be sizeof(pointer), let it be equal to size.
Does size vary between the below declarations? 
```

int *i;
void *v;

```

Well...just did this:
```

 #include <stdio.h>
  2 
  3 int main()
  4 {
  5     int *i;
  6     void *v;
  7 
  8     printf("sizeof(i): %u\n",sizeof(i));
  9     printf("sizeof(v): %u\n",sizeof(v));
 10 
 11     return 0;
 12 }

```
and in both cases i got:
```

sizeof(i): 4
sizeof(v): 4

```

Then what is the difference between declaring void* and x*, where x can be int, char etc. Do we do this only to tell the compiler to what data type the pointer is pointing to?

Thanks

---

### Post by wmcbrine on 2008-12-19
> **kcode said:**
> I've seen people initializing pointer to NULL, in C, as soon as they declare it. Why doesn't C has this feature by default?

Because, for many applications, it would just waste CPU cycles. C is like that... you can write tight, fast code, but the trade-off is that you have to be very explicit about what you want.

---

### Post by Zugzwang on 2008-12-19
> **kcode said:**
> Do we do this only to tell the compiler to what data type the pointer is pointing to?


Yes. The compiler does some type checking for you. This prevents you from accidentally assigning a "float" array to a pointer to an "int" array. Furthermore, if you only had void pointers, each time you wanted to access an array, you would have had to supply the compiler the type of the array.

---

### Post by monkeyking on 2008-12-19
> **Zugzwang said:**
> Yes. The compiler does some type checking for you. This prevents you from accidentally assigning a "float" array to a pointer to an "int" array. Furthermore, if you only had void pointers, each time you wanted to access an array, you would have had to supply the compiler the type of the array.

Sometimes it's handy to have a type that can be anything.
Then use (void *)
This type can be cast to whatever you want.

---

### Post by jpmelos on 2008-12-19
A pointer is an address to a location in memory. So, no matter what the pointer points to, it contains a number that is an address to a location. And the address to an int is a number that occupies the same memory as a void one (be it 4 bytes or whatever in your platform), because it's only stored the address of the first byte of the object. That's why the compiler need to know what the pointer points to.

And, it needs to know it because there is pointer aritmetics. When you do:

```
int *ptrInt;
float *ptrFloat;

ptrInt++;
ptrFloat++;
```

It increases those addresses of different values, because float occupies more memory than int.

And what's initially in a pointer is trash, that was in RAM since the moment you initialized the computer (an electric current went through the memory and left it full of crap) or the last moment you used it (then it has the result that the last application left there).

Hope it helped you!

---

### Post by stroyan on 2008-12-19
An uninitialized variable won't get a value left behind by another application.  Modern operating systems always clean out memory before giving it to a process to use.  But an uninitialized variable will often have a value that is left over from a previous use of that address from within the same application.  Local variables are allocated on the top of a stack.  The values of those stack locations are often left behind from previous functions that allocated variables when they were called and released when the function exited.

---

### Post by pmasiar on 2008-12-19
> **stroyan said:**
> Modern operating systems always clean out memory before giving it to a process to use.  

Huh? Why would operating system waste precious time to prepare memory for application, if any **correctly working** app will assign to that memory something anyway?

When you opted for C, you opted for full speed from CPU and full responsibility for what it does. Remember, "with great power comes great responsibility". 

Or if you too distracted (or too weak) to handle and manage all that raw power, use language for people who have more important things to think about that babysiting CPU, like Python

---

### Post by night_fox on 2008-12-19
Thankyou.

---

### Post by slavik on 2008-12-19
> **kcode said:**
> Then what advantage does Java achieve while initializing pointer to NULL when declaring it? I've seen people initializing pointer to NULL, in C, as soon as they declare it. Why doesn't C has this feature by default?

Thanks

Because that assignment is extra work ... why initialise when you are going to change the value anyway?

[quote=kcode]Then what is the difference between declaring void* and x*, where x can be int, char etc. Do we do this only to tell the compiler to what data type the pointer is pointing to?[/quote]

You are correct. All pointers are the same size because they must be able to contain a full memory address. The type is there for when you are dereferencing it (reading the value it points to).

---

### Post by ymo on 2008-12-19
Another reason for using typed pointers is what happens when you increment them.

int *ip;
char *cp;

++cp; /* adds one so cp points to next character in string */
++ip; /* adds sizeof(int) so that ip points to next integer in an array */

If you only had untyped pointers you would need to remember to add the size of the object pointed to.

---

### Post by nvteighen on 2008-12-20
Initializing a pointer to NULL (and sometimes also setting a pointer to free()'d memory to that value) avoids the risk of random behaivor e.g. the chance that you get a pointer to some allocated memory address and you, by mistake, access it (crashing an application, your application, the system, nothing, whatever... it's random!). Ok, if you keep in mind which pointers aren't initialized in order to not access them, you'll be fine, but... anyone can make a mistake ;)

Now, about C's typing system in general. Actually C data types are **only** meant for type-checking and proper allocation (in terms of bytes). But, as pointers are all of the same size (4 bytes in 32-bit; not sure in 64-bit), then it only serves for the first purpose.

---

### Post by jpmelos on 2008-12-20
> **stroyan said:**
> An uninitialized variable won't get a value left behind by another application.  Modern operating systems always clean out memory before giving it to a process to use.  But an uninitialized variable will often have a value that is left over from a previous use of that address from within the same application.  Local variables are allocated on the top of a stack.  The values of those stack locations are often left behind from previous functions that allocated variables when they were called and released when the function exited.

What the hell, dude. Indeed, if you don't have what it takes to control all that power (pmasiar, that was good! haha), go for a higher-level language.

"If you can't take it, grab some milk!"

---

### Post by stroyan on 2008-12-20
> **pmasiar said:**
> Huh? Why would operating system waste precious time to prepare memory for application, if any **correctly working** app will assign to that memory something anyway?

When you opted for C, you opted for full speed from CPU and full responsibility for what it does. Remember, "with great power comes great responsibility". 

Or if you too distracted (or too weak) to handle and manage all that raw power, use language for people who have more important things to think about that babysiting CPU, like Python

The reasson for clearing allocated memory is that it may contain secrets from a previous application that the next program should not have access to.  If memory was recycled without clearing it then people could run programs that went fishing through old data in uninitialized memory.  Such data could include passwords.

---

### Post by pmasiar on 2008-12-20
> **stroyan said:**
> The reasson for clearing allocated memory is that it may contain secrets from a previous application that the next program should not have access to.  If memory was recycled without clearing it then people could run programs that went fishing through old data in uninitialized memory.  Such data could include passwords.

IMHO it makes more sense to let security-sensitive programs to clean after themselves (or ask OS to do it after deallocating the process) than tax every app because of that paranoia.

And even if program got access to part og the heap from previous process, and was able to access bunch of strings allocated there: how would program guess which if the thousands strings is password? you have only the memory allocated to it, but not the variable name? It looks exactly like 10K of other string literals allocated on the heap.

If someone was this paranoid, should not let other programs to share same CPU, IMHO.

---

### Post by night_fox on 2008-12-20
Obviously the OS does not wipe the heap or the stack.

If you wanted to test if these strings were passwords, you would filter them by their length and which characters they would have. Linux would keep a program in the cache after it exited, so you would be able to find out the location of the code and data section. Does data actually get written to the data section of an executable? If so, you might be able to get some pointers from it! If not, then while the program is running, you could easily find out the memory location of the heap! Its even in the gnome system monitor!

---

### Post by Thesuperchang on 2008-12-21
With exception to floating point data types, all data types are of type integer. The range of these integers are dependent on how much space is requested.

char =  8-bits
short int = 16-bits
long int = 32-bits
long long int = 64-bits

As for for the size of pointers, this is dependent on the machine architecture.[LIST]
[*]16-bit address register
If the machine has a 16-bit address pointer register, a pointer will be 16-bits in size and be able to address up to 64KB of memory.

[*]32-bit address register
If the machine has a 16-bit address pointer register, a pointer will be 32-bits in size and be able to address up to 4GB of memory.

[*]64-bit address register
If the machine has a 16-bit address pointer register, a pointer will be 64-bits in size and be able to address up to 16777216TB of memory.
[/LIST]

The following program demonstrates what can be done with mixing pointer types.

[PHP]#include <stdio.h>

int main(void) {
	char *cptr;
	short int  *iptr;
	short int  integer;

	// Show garbage data
	printf("uninitialised = %d\n", (int)(integer));
	iptr = &integer;

	// Initialise and display
	*iptr = 256;
	printf("initialised   = %d\n", (int)(integer));

	// Display values of individual bytes
	cptr = (char *)iptr;
	printf("hight byte    = %d\n", (int)(*(cptr+1)));
	printf("low   byte    = %d\n", (int)(*cptr));

	// Change values by byte
	*(cptr+1) = 0;
	*(cptr)   = -1;
	printf("hight byte    = %d\n", (int)(*(cptr+1)));
	printf("low   byte    = %d\n", (int)(*cptr));

	// Display whole short int
	printf("initialised   = %d\n", (int)(integer));
	
	return 0;
}[/PHP]

Keep in mind that this program will behave in dependance of byte order. ie. big-endian and little-endian.

---

### Post by dribeas on 2008-12-21
There's a bit of misunderstanding on what languages do or don't and what OS do or they don't. First off, Java does not initialize variables for the user. A reference in Java is not initialized to null by the compiler or the system, only member data is automatically initialized. This behavior was directly inherited from C++, with the difference that in Java the compiler does complain (and it is an error, not just a warning) if the user forgets to initialize:

```

void f()
{
    Integer i;
    System.out.println( i ); // Error, i can be uninitialized
}

```

In C++ some compilers will warn, while other will not, and some of the ones that complain make so in only a subset of the circumstances (g++ requires the user to have optimizations)

That is a common misunderstanding and many people extend the guarantee of member initialization to the rest of the language, which is not true.

While I consider the above as a mistake, and as such not only admisable but a start point for a more precise answer, I sadly see how some people keep on offering opinions as if they were facts. The good part is that you can often see that there is a high correlation of poster and quality of the answer, and once again pmasiar, you have proven yourself: whether you like it or not, operating systems have a behavior. MSDOS, nor MacOS 7 initialized memory for the processes. Windows, from 95 (I believe, surely from 2000) on, Mac OS X, Linux since I can remember, and that goes back to 1.x kernels do initialize the memory for the process.

While you can consider that as a performance hit (wonder how this fits with your preaching of python), the fact is that it has been proven to be the good choice, and not doing it would be a sure case of pessimization. Initializing a block of memory is _really_ fast compared with loading the executable from the disk, or swapping other processes memory out for the new process. Lack of initialization would allow one process scan the rest of the computer memory by just requesting more memory blocks. As other processes get swapped off it could read the memory just acquired and have access to all data. We are not only talking passwords, but also any other data (emails from other user mail agents...) , the pages they are browsing from the internet, and any other data. 

The approach with most current OSes is that user data is private, and as such it should be kept. The whole talk about proceses marking themselves for OS data clearing when they end (or are swapped, you forgot) is just plain nonsense.

Pmasiar, I am sure you can find better ways of marketing python, not that you get paid by it... And if you do, please, do so elegantly: say how your language of choice and the advantages it has, but don't spread believes as facts of life.

---

### Post by pmasiar on 2008-12-22
> **dribeas said:**
>  initialized memory for the processes. Windows, from 95 (I believe, surely from 2000) on, Mac OS X, Linux since I can remember, and that goes back to 1.x kernels do initialize the memory for the process.

Good, I stand corrected.

dribeas> While you can consider that as a performance hit (wonder how this fits with your preaching of python), 

"preaching"? Why you try to start heated arguments? I mentioned Python as example of HLL. Is it not? Was it misplaced?

BTW I suggest Python as language which trades runtime efficiency for programmer's productivity: because CPU's cycles are much cheaper then mine's. It is 100% consistent with performance, you just choose not to see it.

> Pmasiar, I am sure you can find better ways of marketing python, not that you get paid by it... And if you do, please, do so elegantly: say how your language of choice and the advantages it has, but don't spread believes as facts of life.

again, I stand corrected. It is decades since I last looked deep into the OS - and I do not care that much about it anymore.

---

