---
title: "not clear with typedef"
date: 2010-11-01
forum: Programming Talk
---

### Post by jamesbon on 2010-11-01
I have used typedef in my C programs previously many times.
So it is not new to me.
I was reading through a header file 
linux-2.6/include/net/iw_handler.h
and found following use of typedef 
```
typedef int (*iw_handler)(struct net_device *dev, struct iw_request_info *info,
                          union iwreq_data *wrqu, char *extra);

```I was not able to understand what does above typedef is doing?
Or what is the programmer trying to achieve with typedef definition.

---

### Post by spjackson on 2010-11-01
> **jamesbon said:**
> I have used typedef in my C programs previously many times.
So it is not new to me.
I was reading through a header file 
linux-2.6/include/net/iw_handler.h
and found following use of typedef 
```
typedef int (*iw_handler)(struct net_device *dev, struct iw_request_info *info,
                          union iwreq_data *wrqu, char *extra);

```I was not able to understand what does above typedef is doing?
Or what is the programmer trying to achieve with typedef definition.
 Can you at least see that it's a function pointer? You should install cdecl, which in this case reports:
"declare iw_handler as typedef pointer to function that expects (dev as pointer to struct net_device, info as pointer to struct iw_request_info, wrqu as pointer to union iwreq_data, extra as pointer to char) returning int;"

---

### Post by dwhitney67 on 2010-11-01
> **jamesbon said:**
> I was not able to understand what does above typedef is doing?
Or what is the programmer trying to achieve with typedef definition.

Maybe a small example might help...
```

#include <stdio.h>

int square(int val)
{
   return val * val;
}

int doubler(int val)
{
   return val * 2;
}

int main(void)
{
   typedef int (*mathfnc)(int val);

   mathfnc fnc = square;
   printf("10^2 = %d\n", fnc(10));

   fnc = doubler;
   printf("10x2 = %d\n", fnc(10));

   return 0;
}

```

---

### Post by Vox754 on 2010-11-01
> **dwhitney67 said:**
> Maybe a small example might help...
```

#include <stdio.h>

int square(int val)
{
   return val * val;
}

int doubler(int val)
{
   return val * 2;
}

int main(void)
{
   typedef int (*mathfnc)(int val);

   mathfnc fnc = square;
   printf("10^2 = %d\n", fnc(10));

   fnc = doubler;
   printf("10x2 = %d\n", fnc(10));

   return 0;
}

```

Mmm... Wikipedia explains it more like "using type declaration syntax but can be used as if it were created using type cast syntax."

```

typedef int (*funcptr)(double);         // pointer to function of double returning int
funcptr x = (funcptr) NULL;             // C or C++
funcptr y = funcptr(NULL);              // C or C++
funcptr z = static_cast<funcptr>(NULL); // C++ only

```

> 
funcptr is used on the left-hand side to declare a variable and is used on the right-hand side to cast a value. Thus, typedefs can be used by programmers who do not wish to figure out how to convert declaration syntax to type cast syntax.


---

### Post by dwhitney67 on 2010-11-01
> **Vox754 said:**
> Mmm... Wikipedia explains it more like "using type declaration syntax but can be used as if it were created using type cast syntax."

```

typedef int (*funcptr)(double);         // pointer to function of double returning int
funcptr x = (funcptr) NULL;             // C or C++
funcptr y = funcptr(NULL);              // C or C++
funcptr z = static_cast<funcptr>(NULL); // C++ only

```

What's your point?  What the heck do you think I did in my example?  I declared a variable (left hand side), and assigned it a value (right hand side).  All you did was assign NULL... whoop tee doo.

---

### Post by spjackson on 2010-11-01
> **Vox754 said:**
> Mmm... Wikipedia explains it more like "using type declaration syntax but can be used as if it were created using type cast syntax."

```

typedef int (*funcptr)(double);         // pointer to function of double returning int
funcptr x = (funcptr) NULL;             // C or C++
funcptr y = funcptr(NULL);              // C or C++
funcptr z = static_cast<funcptr>(NULL); // C++ only

```
Whatever the point of your quoting this example, Wikipedia is wrong. The initialisation of y is not valid C syntax, neither in K&R, nor in c89 nor in c99.

---

### Post by Vox754 on 2010-11-01
> **dwhitney67 said:**
> What's your point?  What the heck do you think I did in my example?  I declared a variable (left hand side), and assigned it a value (right hand side).  All you did was assign NULL... whoop tee doo.

Woa!

I'm not saying you are wrong. I only posted that because Wikipedia editors give a different explanation, which the OP or other people may find first.

Your code is definitely superior, it is simple and understandable, while Wikipedia's is confusing.

That's not my code. Please don't assassin the messenger!

---

### Post by dwhitney67 on 2010-11-01
> **Vox754 said:**
> Woa!

I'm not saying you are wrong. I only posted that because Wikipedia editors give a different explanation, which the OP or other people may find first.

Your code is definitely superior, it is simple and understandable, while Wikipedia's is confusing.

That's not my code. Please don't assassin the messenger!

You should have stated in your first post that you disagree with what is stated in the Wiki site; or that one needs to beware because it contains confusing/wrong code.

Don't worry... I'm not out to harm anyone.  I'm too bored with s/w these days to hold a conversation lasting more than 5 minutes.

---

### Post by jamesbon on 2011-06-20
> **dwhitney67 said:**
> Maybe a small example might help...
```

#include <stdio.h>

int square(int val)
{
   return val * val;
}

int doubler(int val)
{
   return val * 2;
}

int main(void)
{
   typedef int (*mathfnc)(int val);

   mathfnc fnc = square;
   printf("10^2 = %d\n", fnc(10));

   fnc = doubler;
   printf("10x2 = %d\n", fnc(10));

   return 0;
}

```


Thanks a lot for this code I have been trying to understand spiral rule from c-faqs.com and today your code when I revisited helped me a lot to understand it better.

---

