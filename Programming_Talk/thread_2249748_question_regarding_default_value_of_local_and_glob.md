---
title: "question regarding default value of local and global variables"
date: 2014-10-24
forum: Programming Talk
---

### Post by IAMTubby on 2014-10-24
Hello,
 I have a question regarding default value of local and global variables.

_I understand that the default values are as follows : _
[B]Local variable   - it is indeterminate
Global variable - 0

[/B]_Trying to understand the reason :_
I went through a few resources on the internet and tried to understand why. I basically kept bumping into these reasons
1. **Local variables **are allocated memory and initialized at **run time**; 
    **Global** at **compile time**
2. **Local variables** are **stored on the stack**, whereas 
    **Global** variables have a fixed memory location either in the** data segment(fixed memory allocation)** or on **the heap(fynamic memory allocation)**

_My questions : _
But, hmm, I still haven't been able to get it completely. My question is more like, 
1. Why does a variable which is initialized at run time have to have a default value which is indeterminate?
2. Why does a variable which resides on the stack have to have a default value which is indeterminate?
3. By the way, if a local variable is allocated dynamically, is it still stored in the stack and not in the heap?

Thanks.

---

### Post by ofnuts on 2014-10-24
To make it a bit simpler than it really is:

[LIST]
[*]The uninitialized global variables are allocated from a chunk of memory that is "cleaned" by the operating system before being given to your program, so everything is set to 0.
[*]The local variables are allocated in the [stack](http://en.wikipedia.org/wiki/Stack_%28abstract_data_type%29#Basic_architecture_of_a_stack). Two functions called one after another by the same parent function will end up using the same stack area for their local variables, so the variables in the second one will be mapped to bytes that still contain the values of the variables of the first one (but don't count on that as a good way to pass values across functions). So if you want your variables to contains something specific, even 0 or NULL, you have to initialize them explicitly.
[/LIST]
In any case it is always a good idea to initialize your variables explicitly, and let the compiler decides if it generates code or specifically initialized data areas for them.

---

### Post by 3246251196 on 2014-10-24
3. By the way, if a local variable is allocated dynamically, is it still stored in the stack and not in the heap?

```

void myFunc() {
  int *pInt = (int*)malloc(sizeof(int));
  *pInt = 3;
  //some more stuff
  free(pInt);
}

```

pInt is a local variable (a pointer) to the function myFunc. But its value is a pointer to the heap (sometimes called the free store). Dynamically allocated memory points to the heap, locals to the stack. I do not think question 3 makes sense: that you can have a local variable whose address is dynamically allocated in this simple questions context(?)

---

### Post by IAMTubby on 2014-10-24
> **ofnuts said:**
> To make it a bit simpler than it really is:

[LIST]
[*]The uninitialized global variables are allocated from a chunk of memory that is "cleaned" by the operating system before being given to your program, so everything is set to 0.
[*]The local variables are allocated in the [stack]("http://en.wikipedia.org/wiki/Stack_%28abstract_data_type%29#Basic_architecture_of_a_stack"). Two functions called one after another by the same parent function will end up using the same stack area for their local variables, so the variables in the second one will be mapped to bytes that still contain the values of the variables of the first one
[/LIST]
Thanks ofnuts, got it.

---

### Post by IAMTubby on 2014-10-24
> **3246251196 said:**
> 3. By the way, if a local variable is allocated dynamically, is it still stored in the stack and not in the heap?

```

void myFunc() {
  int *pInt = (int*)malloc(sizeof(int));
  *pInt = 3;
  //some more stuff
  free(pInt);
}

```

pInt is a local variable (a pointer) to the function myFunc. But its value is a pointer to the heap (sometimes called the free store).
Thank you, that was very clear.
So pInt is a local variable and so part of the stack, but the value it holds(the address it holds) is an address in the heap because that memory is allocated dynamically.

---

