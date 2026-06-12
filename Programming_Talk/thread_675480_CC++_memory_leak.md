---
title: "C/C++ memory leak"
date: 2008-01-22
forum: Programming Talk
---

### Post by sfabel on 2008-01-22
Hi,

I've got a beginner's question regarding a memory leak that I am experiencing.

I've got this code which creates it:
```

AGradient *ag;

while(k < 50) {    	
    	k++;
    	ag = agradient(tmpimage);
// [then do something with it...]
}

```

AGradient is my own data structure (struct) defined in my own little library.

My funktion "agradient" calculates stuff, then returns a pointer to that structure, just like defined above. The problem I had was this: when I compiled my library, it gave a warning that I was returning a local pointer address, which I could only resolve by making the return variable global, and then returning its address. I don't know if I am going to burn in seventh hell for doing this, but I couldn't find another way.

In any case, the above code creates a ramp in memory usage, so it is a memory leak. I just don't know how to fix it. I read about new and delete, but I am not sure how to implement it. If I do this:

```

AGradient *ag;
ag = new AGradient;

```

And try to delete it before jumping into the next iteration of the while loop, it gives me an error (invalid pointer) and dumps core.

I don't really know what I am doing here, as you probably can tell and would be very glad for any pointers. I have read several tutorials and webpages but fail to see how it relates to my problem.

Thanks for any help or pointers,

Stephan

---

### Post by hod139 on 2008-01-22
You didn't give enough code for me to figure out what you are doing wrong, but I can guess about the waring about a local pointer address.  To allocate a pointer in a function call, you have to pass the pointer by reference.  Here is some sample code:

```

struct AGradient{};

// pass the ptr by reference (*&)
void Allocate(AGradient *& ptrToAGradient){
   ptrToAGradient = new AGradient;
}

int main(void){
   AGradient *ptrToAGradient;
   Allocate(ptrToAGradient); // allocate the pointer

   //...

   delete ptrToAGradient; // delete the pointer

   return 0;
}

```

---

### Post by sfabel on 2008-01-22
Thanks, this really helped me out.

Stephan

---

### Post by dwhitney67 on 2008-01-23
> **hod139 said:**
> To allocate a pointer in a function call, you have to pass the pointer by reference.
Not entirely true.  The function itself can allocate the memory and return the pointer to such without the use of a parameter.  For example:

[PHP]Foo * function()
{
  Foo *f = new Foo;

  // ...

  return f;
}

int main()
{
  Foo *allocF = function();

  //...

  delete allocF;

  //...
}[/PHP]

---

### Post by Wybiral on 2008-01-23
I'd like to throw in that if this is C++, the allocation should be wrapped in an object that can destruct the newly allocated memory on its own. And if it's C, you should follow a "new / free" naming convention for the function, either "Foo *new_Foo() / free_Foo(Foo*)" or "new_Foo(Foo*) / free_Foo(Foo*)". Expecting the user-end code to free it would be an unwise decision.

---

