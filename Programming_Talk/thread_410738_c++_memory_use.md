---
title: "c++ memory use"
date: 2007-04-16
forum: Programming Talk
---

### Post by carl.alv on 2007-04-16
Hello all! 

I have a problem regarding to -I suppose- memory allocation with my program. The thing is that I use big arrays -double[500][500]- and when I declare four of these I get "segmentaton fault" when running the program. So I wanted to check the memory status of my machine which has 2Gb of memory and 3Gb swap, but when I run the program -the version w/o too many arrays- and checked the memory and swap on the system monitor I do not see any memory nor swap usage!

So my question is: where is c++ -or g++ compiler- storing the data when the program runs???

Thank you in advance for any help.

---

### Post by samjh on 2007-04-16
Are you accessing or modifying your arrays properly?

Four such arrays could potentially take up to 7.8 Megabytes of memory.  Are you storing them in the stack or the heap?  Attempting to store too much data in the stack will cause stack overflow.  Some OS (I don't know if Linux is one of them) will throw a segmentation fault if this occurs.

---

### Post by carl.alv on 2007-04-16
I am currently using automatic memory, not dynamic, do you think that could be the problem?

---

### Post by Tuna-Fish on 2007-04-16
Depends on what you mean with automatic memory. If you mean true automatic, there is no such thing in C++, if you mean stack, yeah, that is your problem.

you've got 2 choices: 

allocate the memory statically, that is put it outside functions with a nice keyword 'static' in front of it. For various reasons, this is generally a bad idea. 

use dynamic allocation for that kind of memory use.

---

### Post by carl.alv on 2007-04-16
yes I mean stack -I think-. OK I will try with "new" and "delete" for those big arrays. Thanks!

---

### Post by carl.alv on 2007-04-16
Well, I'm using the heap and the problem persists. I is a 6000+ lines program and I don't have a hint where to look for problems, any idea of where can I start my search of possible problem sources (for example is it bad idea to mix heap and stack usage in the same application)?

---

### Post by carl.alv on 2007-04-16
Wait! heap using solved the problem! (the later problem was caused by a mistake when addressing the indexes of the arrays) Thank you all!

---

### Post by Tuna-Fish on 2007-04-16
> **carl.alv said:**
>   (for example is it bad idea to mix heap and stack usage in the same application)?

Absolutely not. They are both powerful tools, but for different purposes. Actually, you kinda have to use stack to use the heap. When you do:
```

int* a = new int[300];

```
you create two variables. "(*a)" which is a 300-entry integer array somewhere in heap, and "a"  which is the address of *a,  is a 32-byte address (unsigned int) existing on the stack.

Stack is meant for storing small stuff, for example individual values and small arrays, counters and such. Heap is for big stuff.

> **carl.alv said:**
> 
I is a 6000+ lines program and I don't have a hint where to look for problems, any idea of where can I start my search of possible problem sources || Wait! heap using solved the problem! (the later problem was caused by a mistake when addressing the indexes of the arrays) Thank you all!

One critical thing to remember about c++ is that it does absolutely no bounds checking. This makes it fast, but also very easy to break unless you are careful. For example, when you type:
```

a[20]=4;

```
it really compiles into the machine-code equivalent of "put 4 into the memory location a+20*(size of int, in 32-bit systems, 4 bytes)".

Absolutely nothing stops you from typing a[-2]=10. What happens then? Depends entirely on what is in memory location a-8. If you are lucky, it is segmented outside of your writable area, and the program immediately segfaults. 

Now, crashing might not be fun, but imagine what would have happened if it wasn't something that you can't write to. Perhaps it was crucial program data, and the program completes successfully, and you're left baffled as the output is garbage and the part of the program that seems to be responsible, is actually completely fine.

Now imagine what would happen if a-8 actually held another pointer to an array. Writing a garbage value on top of that would really mess things up, as you'd be left searching for another f'd up pointer that is wrecking things, but when you find it, you find that it is, in fact, perfectly fine in the code and something else must have broken it during runtime.

To sum things up, when using arrays, be sure of the following things: (if the array is in stack, you can be sure of most of them instantly).

a) that there, in fact, is an array in the location you are using. That is, you have created it (either in stack, or using new), and it hasn't been deleted (either by delete, or by going out of scope - if you declare an array on the stack, make sure you are inside the same curly braces as the array)

bad example:
```

int* f()
{
int a[20];
do something;
return &a;
// a is a valid address to an array, but when the programs returns from f(), 
// the array goes out of scope and ceases to exist.the worst part is that 
// it might actually work for a short time, because the values on stack will 
// likely not be overwritten until you call another function, leaving you mystified 
// how the array first works, then stops working.
}

```

b) That you are not going past the bounds of the array. If you have a 20-unit array, remember that the last unit is a[19], not a[20]. If you get the number from somewhere, make sure it is right there. and last, if the array is variable-length, remember that wherever you use it, it is worthless without knowing just how big it is. (with the obvious exception of null-terminated strings.)

Stuff like this is probably the most common cause of persistent bugs in real used software. When you got 6000 lines worth of code, going trough it all isn't that big of a job. When you got 100 000 lines, it is nearly impossible.

The lesson to carry home is: do arrays properly the first time, or they will haunt your dreams, and be pain² to debug.

---

### Post by carl.alv on 2007-04-16
Thank you for your advice Tuna :). In fact my program managed to work, but now; when I make the program do a long run, the memory usage starts increasing until it uses all of the 2Gb!

The way I am declaring my arrays is this:

```

        double **UR1_intra = new double*[NPART+1];
	double **UR2_intra = new double*[NPART+1];
	double **UR_inter = new double*[NPART+1];
	for(int i = 0; i < NPART+1; i++){
		UR1_intra[i] = new double[NPART+1];
		UR2_intra[i] = new double[NPART+1];
		UR_inter[i] = new double[NPART+1];
	}

```

and then, after manipulating it alot I delete it with

```

        delete[] UR1_intra;
	delete[] UR2_intra;
	delete[] UR_inter;

```

I also declare and delete some other arrays like these inside some loops.

---

### Post by carl.alv on 2007-04-16
Now I realized I was not deleting the UR_inter[i]'s, and thats why the memory was piling up :rolleyes:

---

### Post by Xandei on 2007-04-16
While not directly related to your origional problem, have you considered using std::vector<T> instead of plain arrays for dealing with such large amounts?

Vector's don't need to be explicity set for size when created. (Though they can be, with std::vector.Resize() ) They also make use of templates, resulting in (imho) cleaner looking code.

Instead of:
```

double Ar1[500];
srand( time(NULL) ); // Seed the random generator.

// Fill with random data.
for (short int i; i <= sizeof(Ar1); ++i )
{
    Ar1[i] = rand();
}

// Output the contents.
for (short int i; i <= sizeof(Ar1); ++i )
{
    printf("Ar1[%i]: %f", i, Ar1[i]);
}

// Finally, clean up the array.
delete[] Ar1;

```

You can do:

```

std::vector<double> Ar1;
srand( time(NULL) ); // Seed the random generator.

// Fill with random data.
for ( short int i; i <= 500; ++i; )
{
    Ar1.insert( rand() );
}

std::string TempStr;

for ( short int i; i <= 500; ++i; )
{
    std::cout << "Ar1[" << i << "]: " << Ar1.at(i) << endl;
}

delete Ar1;

```

If one is cleaner than the other is debatable, but I prefer the latter. (though cout still irks me ;))

---

