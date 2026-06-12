---
title: "Array Memory Deallocation"
date: 2009-08-23
forum: Programming Talk
---

### Post by Abhishek4563 on 2009-08-23
QUE1: If I have declared a really large aaray inside a function, would it be automatically deallocated on exit the scope of the function??

QUE2:While using mpz_class in GMP is the memory automatically deallocated after exiting the scope i.e. are the appropriate destructors for giving the memory back to O.S there or I have to manually do it ?

QUE3: I would like to utilise all the four cores of my intel quad-core and assign 1 ploynomial per processor, what should I use... would fork() do the job???

---

### Post by MadCow108 on 2009-08-23
which language?
I'm guessing C/C++
1. no you need to deallocate it urself with free/delete (except your using STL containers with non-pointer content [C++])

2. check the documentation of the framework. If your using the c++ wrapper maybe not, if you using C probably yes

3. you could look at openMP,pThtread or MPI for that
openMP is by fare the easiest and best suited for multicore pcs

---

### Post by Abhishek4563 on 2009-08-23
Yes I am using C++, I thought the float arrays would be automatically freed on exit from scope, the GMP documentation is not great they dont talk much about mpz_class, and I dont want to look at the source code, if someone has used it please help me...

---

### Post by nvteighen on 2009-08-23
In **what** language? C or C++??

> **Abhishek4563 said:**
> QUE1: If I have declared a really large aaray inside a function, would it be automatically deallocated on exit the scope of the function??

If you declared it without using **new** or **malloc()**, yes. If you used **new** or **malloc()**, it won't.

> 
QUE2:While using mpz_class in GMP is the memory automatically deallocated after exiting the scope i.e. are the appropriate destructors for giving the memory back to O.S there or I have to manually do it ?


In C, not. In C++, destructors are always called at the end of a function for any class instance declared inside of it. The destructors will have to be properly written in order to not leak any memory. But in C++, if you use it through **new**, it won't... as what you actually declare is a pointer to a class instance rather than an instance.

---

### Post by Habbit on 2009-08-23
> **nvteighen said:**
> If you used **new** or malloc(), it depends... In C++, it will be deallocated.

What? If you used "int* myArr = new int[10];", the array will **not** be automatically deallocated on function exit: there _will_ be a memory leak. You need to manually deallocate the memory with "delete[] myArr;".

---

### Post by MadCow108 on 2009-08-23
> **nvteighen said:**
> In **what** language? C or C++??
If you declared it without using **new** or malloc(), yes. If you used **new** or malloc(), it depends... In C++, it will be deallocated. But in C, it won't.


also in c++ you need to delete your memory allocated with new.

you should check your code with valgrind to see if you have any memory leaks.
with debuging symbols (-g in g++) it even gives you the line of the allocation of the leak.

---

### Post by nvteighen on 2009-08-23
Yup, sorry for the confusion... I edited my post while you answered. :p

---

### Post by Abhishek4563 on 2009-08-23
thx a ton all of you people

---

### Post by bender1234 on 2009-08-23
> **Abhishek4563 said:**
> QUE3: I would like to utilise all the four cores of my intel quad-core and assign 1 ploynomial per processor, what should I use... would fork() do the job???

Have a look at pthreads, the standard *nix thread library, fork makes a process like the one you have sort of.

---

### Post by Abhishek4563 on 2009-08-24
I think you mean that fork() by itself wont allocate different processors for the new processes?

---

### Post by Abhishek4563 on 2009-08-24
I am implementing quadratic sieve in c++ using gmp...I am assuming that I can use about 2GB of the available 4GB RAM, am I overlooking something, what is the size of the stack???..do I have to consider L1 or L2 cache... I will need a 10000x10000 array in the program how do i know that stack wont overflow...also is it advantageous to use register keyword or it would be automatically done by g++..thx
Abhishek

---

### Post by MadCow108 on 2009-08-24
the stack is very small compared to the heap memory.
you definitly won't get a 10000*10000 array into stack
you'll have to use the heap
I think you can see how much stack is available with ulimit -a

regarding fast memory usage you should read this:
[http://people.redhat.com/drepper/cpumemory.pdf](http://people.redhat.com/drepper/cpumemory.pdf)

---

### Post by Abhishek4563 on 2009-08-24
thanx madcow... actually I misqueried the array would be on the heap.. can we take the size of heap to be comparable to that of the RAM

---

### Post by dribeas on 2009-08-24
1. Stack allocated objects will be destroyed when they go out of scope. Heap allocated memory (new/malloc) will not be destroyed when it goes out of scope unless it is held in an object implementing RAII (smart pointers in general)

2. No idea, read the docs

3. I recommend using the boost library (if you are using C++). It is close to the new standard (yet to be approved standard) and eases thread usage.

```

void find_primes( int first, int last, std::vector<int>& data ); // just an example of a complex operation

int main()
{
   std::vector<int> v1, v2, v3, v4;
   boost::thread thr1( find_primes, 1, 100, boost::ref(v1) ); // find primes in 1..100 with one thread
   boost::thread thr2( find_primes, 101, 200, boost::ref(v2) ); // another thread
   boost::thread thr3( find_primes, 201, 300, boost::ref(v3) ); // yet another thread
   boost::thread thr4( find_primes, 301, 400, boost::ref(v4) ); // a last thread

   // simplest join for threads, read the docs for better results
   thr1.join();
   thr2.join();
   thr3.join();
   thr4.join();

   // join all data
   std::vector<int> all_primes;
   std::copy( v1.begin(), v1.end(), std::back_inserter(all_primes) );
   std::copy( v2.begin(), v2.end(), std::back_inserter(all_primes) );
   std::copy( v3.begin(), v3.end(), std::back_inserter(all_primes) );
   std::copy( v4.begin(), v4.end(), std::back_inserter(all_primes) );

   // printout result
   std::cout << "There are " << all_primes.size() << " primes in the range [1, 400]: ";
   std::copy( all_primes.begin(), all_primes.end(), std::ostream_iterator<int>( std::cout, " " );
   std::cout << std::endl;
}

```

The only magic part there is the boost::ref() that creates a reference wrapper. Threads copy the arguments, so that is required to avoid the thread working on a copy of the input vectors and thus loosing the results at the end. But as you can see the thread management is rather simple.

---

### Post by WitchCraft on 2009-08-24
Use threads instead of forking, i think it's faster:
You can use my thread code, i just posted it 5 minutes ago.
```

http://ubuntuforums.org/showthread.php?t=1248065

```

For a quadratic sieve, I would use one of the high-performance math libraries around (=not boost).

Actually, you can create a C++ class with malloc and free instead of new and delete. This bypasses the constructors and/or destructors ;-))


```

all:~# ulimit -a
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
pending signals                 (-i) 16382
max locked memory       (kbytes, -l) 64
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) unlimited
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited

```

---

### Post by Abhishek4563 on 2009-08-25
> **dribeas said:**
> 1. Stack allocated objects will be destroyed when they go out of scope. Heap allocated memory (new/malloc) will not be destroyed when it goes out of scope unless it is held in an object implementing RAII (smart pointers in general)

Thanx for the informative reply.
I think that whenver main() calls a function all the declarations inside it are on the heap but I believe they are automatically de-allocated...???

---

### Post by Abhishek4563 on 2009-08-25
> **WitchCraft said:**
> Use threads instead of forking, i think it's faster:
You can use my thread code, i just posted it 5 minutes ago.

Thanx witchcraft

---

### Post by dribeas on 2009-08-25
> **Abhishek4563 said:**
> Thanx for the informative reply.
I think that whenver main() calls a function all the declarations inside it are on the heap but I believe they are automatically de-allocated...???

Only memory allocated with new/malloc is heap allocated. Local variables inside a function are stack allocated.

```

struct X {};
void f()
{
   X a; // stack allocated X variable, will be destructed at the end of 
        // the scope

   X *p = new X(); // p is a stack allocated pointer variable
                   // *p is a heap allocated X instance
   delete p;       // you must deallocate the heap memory

   std::auto_ptr<X> ap( new X() ); // ap is stack allocated auto_ptr
                   // *ap is heap allocated X instance
   // no need to deallocate, when ap goes out of scope ~auto_ptr will do it for you
}

```

---

### Post by Abhishek4563 on 2009-08-25
> **dribeas said:**
> Only memory allocated with new/malloc is heap allocated. Local variables inside a function are stack allocated.


*When a program begins executing in the main() function, [I]all variables declared within main() will be stored on the stack*.[/I]
*If the [FONT=courier new]main()[/FONT] function calls another function in the program, for example [FONT=courier new]calcSize()[/FONT], additional storage will be allocated for the variables in [FONT=courier new]calcSize()[/FONT]. This storage will be allocated in the heap memory segment.*

The above is from [http://www.maxi-pedia.com/what+is+heap+and+stack](http://www.maxi-pedia.com/what+is+heap+and+stack)
This caused the confusion in the first place if it is inaccurate do point out.
Thx

---

### Post by dribeas on 2009-08-26
> **Abhishek4563 said:**
> *When a program begins executing in the main() function, [I]all variables declared within main() will be stored on the stack*.[/I]
*If the [FONT=courier new]main()[/FONT] function calls another function in the program, for example [FONT=courier new]calcSize()[/FONT], additional storage will be allocated for the variables in [FONT=courier new]calcSize()[/FONT]. This storage will be allocated in the heap memory segment.*

The above is from [http://www.maxi-pedia.com/what+is+heap+and+stack](http://www.maxi-pedia.com/what+is+heap+and+stack)
This caused the confusion in the first place if it is inaccurate do point out.
Thx

That is false. The article is full of errors and absurdities. The problem is that I have tried browsing and did not really find any simple clear article to refer you to (maybe you should browse this [question and answers]("http://stackoverflow.com/questions/79923/what-and-where-are-the-stack-and-heap") in stackoverflow).

---

### Post by Abhishek4563 on 2009-08-26
are objects always declared on the heap ..without using new or malloc...this was also written in the article, please confirm or disconfirm it

---

### Post by nvteighen on 2009-08-26
> **Abhishek4563 said:**
> are objects always declared on the heap ..without using new or malloc...this was also written in the article, please confirm or disconfirm it
False.

```

myClass myObject = myClass(); // Allocated in stack
myClass *myObject2 = new myClass(); // Allocated in heap

```

The first will be deallocated when the function returns... exactly like any other variable created without new.

EDIT: Thanks to dribeas... I forgot a * :p

---

### Post by MadCow108 on 2009-08-26
I think this article is wrong
atleast I get a stack overflow if I do this:
someclass obj[1000000];
so there on stack not heap

so far I know only new/malloc allocated objects land in heap and only those have to explicitly be freed/deleted again (except your using some kind of smart pointer)

---

### Post by Abhishek4563 on 2009-08-26
thank you all .. this discussion clarified a lot of things

---

### Post by dribeas on 2009-08-26
nvteighen: In the second case you are missing a pointer in the type definition:

> **nvteighen said:**
> ```

myClass myObject = myClass(); // Allocated in stack
myClass *myObject2 = new myClass(); // Allocated in heap

```

It is important to note the difference between the pointer variable and the pointed memory: both myObject and myObject2 are local stack allocated variables, the first of type myClass, the second of type pointer to myClass.

Now, the value of myObject2 is the address of the memory allocated in the heap with 'new myClass()'. The stack allocated pointer points to a heap allocated object.

Technically, all function/method variables (auto variables) are stack allocated, but in the case of pointers (or references) can refer to heap allocated memory.

The memory space taken by the pointer will be released when the function goes out of scope, the memory referred by the pointer contents will not.

---

### Post by nvteighen on 2009-08-26
> **dribeas said:**
> nvteighen: In the second case you are missing a pointer in the type definition:



It is important to note the difference between the pointer variable and the pointed memory: both myObject and myObject2 are local stack allocated variables, the first of type myClass, the second of type pointer to myClass.

Now, the value of myObject2 is the address of the memory allocated in the heap with 'new myClass()'. The stack allocated pointer points to a heap allocated object.

Technically, all function/method variables (auto variables) are stack allocated, but in the case of pointers (or references) can refer to heap allocated memory.

The memory space taken by the pointer will be released when the function goes out of scope, the memory referred by the pointer contents will not.
Thanks... my mistake.

---

### Post by Abhishek4563 on 2009-09-11
Hey there places in the program where I have to declare arrays of sizes dependent on the input... and one of the arrays is going to be centre of action in the most computation extensive part of the algorithm ... so either I can declare it on the stack or heap .. is the heap significantly slower than the stack ??? ... also the stack size is 8MB and I have declared arrays local to some functions on the stack (size about 240 kb) ..QUestion: is it a bad programming practice..when I know that it will be deallocated when the function exits???(If I had my way I would declare variables on the stack quite liberally unless I reach about 4MB of stack space) I am asking this because all the good codes I see use malloc or new very liberally ... and I don't want to write a sub-standard code ..kindly help

---

### Post by nvteighen on 2009-09-11
> **Abhishek4563 said:**
> Hey there places in the program where I have to declare arrays of sizes dependent on the input... and one of the arrays is going to be centre of action in the most computation extensive part of the algorithm ... so either I can declare it on the stack or heap ..

No, if its size depends on user input, you need it to be declared dynamically in heap.

> QUestion: is it a bad programming practice..when I know that it will be deallocated when the function exits???(If I had my way I would declare variables on the stack quite liberally unless I reach about 4MB of stack space) I am asking this because all the good codes I see use malloc or new very liberally ... and I don't want to write a sub-standard code ..kindly help

Simple... very simple: If you use malloc/new, then you have to deallocate the array manually. If you don't use any of those, it will be deallocated automatically. That's all.

---

### Post by Abhishek4563 on 2009-09-11
*]No, if its size depends on user input, you need it to be declared dynamically in heap.*

I think I didnt put the question well ..  basically there is upper limit to the size of the array and I would have declared it to be of the maximum size... the question was whether the heap is slower?... and by computation extensive I just meant lots of access to the array... thats why it matters if the heap is slower...


Thanx

---

### Post by MadCow108 on 2009-09-11
caution I'm not sure this is really correct:
it is my understanding of stack and heap that the performance difference is just in the allocation and freeing. The usage performance should be rather similar.
so unless you need to allocate memory inside heavy loops (which should very rarely be the case) it makes no difference
if this is for some case unavoidable have a look at other high performance malloc implementation as for example:[http://code.google.com/p/google-perftools/wiki/GooglePerformanceTools](http://code.google.com/p/google-perftools/wiki/GooglePerformanceTools)

so its better practice to use the heap for stuff beyond the basic types and small structures as it is a lot bigger (= your program can scale a lot better to the user input) and you have better error handling.

---

### Post by Abhishek4563 on 2009-09-11
thanx madcow .. this pretty much solves my problem

on a side-note it would be great if anyone could help me in locating the source code gmp's c++ interface .. I already tried but in vain I am sure its just my ignorance of the how opensource works ..its located at [http://gmplib.org/](http://gmplib.org/) .. I just want to make sure that appropriate destructors are called at the exit of scope...now it sure does look like spoonfeeding but belive me I am trying and it is important.. thanx

---

### Post by MadCow108 on 2009-09-11
activate sources repository 
mkdir somedirname
cd somedirname
apt-get source libgmpxx4ldbl

or directly from their site (you need mercurial: sudo apt-get install mercurial):
hg clone [http://gmplib.org:8000/gmp-4.3/](http://gmplib.org:8000/gmp-4.3/)

but you mostly can trust stable libraries that they have no memory leaks.

but its always a good idea to run valgrind over your code.
this program will check for any memory leaks your program has an also report where they appear.

And you should not hang yourself on too many detail, like what is faster stack or heap. get a working implementation first and then see if its to slow.
only they start to optimize your code.
valgrind also has a few nice profiling tools callgrind and cachegrind. [http://valgrind.org/info/tools.html](http://valgrind.org/info/tools.html)

---

### Post by Abhishek4563 on 2009-09-12
thanx again madcow .. yes I think I should first get it ready and then fuss about details...

---

