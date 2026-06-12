---
title: "The Memory Layout of a C program"
date: 2010-04-12
forum: Programming Talk
---

### Post by PanP5 on 2010-04-12
A C program is composed of the following pieces:

```
The Text segment

The Initialized Data Segment

The Uninitialized Data Segment

The Stack

The Heap
```

The initialized and uninitialized data segment... do those strictly contain the variables declared/initialized in the main function? Is everything declared/initialized inside another function simply stored on the stack?

For example:

```
int foo()
{
   int j = 2;
   return j;
}

int main(int argc, char *argv[])
{
   int k;
   int i = 5;
   k = foo();

   return 0;
}
```

Where in the program memory do i,j,and k reside? When does that happen?

---

### Post by matthew.ball on 2010-04-12
[Stack]("http://en.wikipedia.org/wiki/Stack_(data_structure)").

Heap for [Dynamic memory allocation]("http://en.wikipedia.org/wiki/Dynamic_memory_allocation").

---

### Post by MadCow108 on 2010-04-12
in your example it all lies in the stack. 
the un/initialized segments are for global variables
The stack and heap are dynamic and grow/shrink as the program progresses. the other segments are constant in size
```

static int i = 5; //should be in rw initialized segment
static const char * c = "5"; //should be in read-only initialized segment
static int j;  //should be in uninitialized segment (but initialized to zero)

int main(...) { // machine instructions are in text segment
  int a;
  int b; // both on stack (frame of main)
  char * c = malloc(4); // pointer is on stack, memory allocated on heap
}

int f(void) {
  int a; // stack (frame of f)
}

```

---

### Post by PanP5 on 2010-04-12
> **MadCow108 said:**
> in your example it all lies in the stack. 
the un/initialized segments are for global variables

Thanks! That was exactly what I was unclear about.

---

