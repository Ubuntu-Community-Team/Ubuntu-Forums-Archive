---
title: "tail recursion"
date: 2011-03-18
forum: Programming Talk
---

### Post by cybo on 2011-03-18
i started reading a book called mastering algorithms with c and it talks about tail recursion which really confuses me. 

here is the code for regular recursive factorial:

```
int fact(int n) {
  if (n < 0) return 0;
  else if (n == 1 || n == 0) return 1;
  else return n*fact(n-1);
}

```
here is the code for tail recursion

```
// a must be set to 1
int facttail(int n, int a) {
  if (n < 0) return 0;
  else if (n == 1 || n == 0) return 1;
  else return fact(n-1, n*a);
}
```

and here is the definition of tail recursion which really confuses me
> 
a recursive function is said to be tail recursive if all recursive calls within it are tail recursive. a recursive call is tail recursive when it is the last statement that will be executed within the body of a function and its return value is not a part of an expression. tail-recursive functions are characterized as having nothing to do during the unwinding phase. this characteristic is important because most modern compilers generate code to take advantage  of it.


it says that a recursive call is tail recursive when it is the last statement that will be executed within the body of the function and its return value is not part of the expression. what does that mean? in both codes the last statement is the function call. so why do we call the last one tail recursive? what does "its return value is not part of an expression" mean? 

any help is appreciated. also if you could give more examples of tail recursion it will also be appreciated.

---

### Post by schauerlich on 2011-03-18
Basically, the recursive call doesn't leave any "pending operations" for when the call returns. With n*fact(n-1), you have to wait for the recursive call to fact to return, then multiply it, then return it up to the next level. With tail recursion, you can just change the arguments in place and run the function call in the same stack frame. Wikipedia has examples. Don't worry if you can't read scheme, the code is basically the same as your C example above. [http://en.wikipedia.org/wiki/Tail_recursion#Example_programs](http://en.wikipedia.org/wiki/Tail_recursion#Example_programs)

---

### Post by The Cog on 2011-03-20
If a function is tail recursive, then the exit from the function is a series of return statements all handing the final value unmodified tothe caller. 

In such a case, where the innermost call has the final value, it is possible to smiplify things and rewrite as a straightforward loop. In your code above, rather than calling itself again, the compiler can replace n and a with n-1 and n*a and simply jump to the start of the function again. The final (one and only) return returns the correct value which would have previously been repeatedly returned to outer callers. There is a significant saving in time and memory if the compiler can simplify a recursive function this way.

---

