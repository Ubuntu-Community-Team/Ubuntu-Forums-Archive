---
title: "Compiler warnings"
date: 2008-08-22
forum: Programming Talk
---

### Post by PeterBBB on 2008-08-22
Building a source package, I am getting shed loads of warning messages, but no obvious bugs in the program. I don't like compiler warnings and would like to get rid of them. However, I am a noob with GCC and have no idea whether these are important, meaningless, or bugs in GCC. 

One that is puzzling me especially is

```
warning: passing argument 2 of ‘R_MarkFragments’ from **incompatible pointer type**
```

The function parameter is defined as 

```
const vec3_t axis[3]
```

where vec3_t is an array of 3 floats. Its a standard 3D graphics thing.

The [auto] variable passed to the function is defined as

```
vec3_t	axis[3]
```

The function call is

```
R_MarkFragments (origin, axis, radius,
```   .....


So the parameter and the variable used are both arrays of 3 lots of vec3_t, its correctly passed, and there are no explicit pointers here. What's causing the warning "**incompatible pointer**"? Can anyone help? 

Playing around with the code, I notice that if I change the call to 

```
(&origin,
``` ....

I get the same warning on the first parameter.

If I change the function definition to remove the 'const', the warning goes away. But that is ridiculous! The const attribute is deliberate guard code here to ensure that the called function does not mess up the value for the calling routine that uses it later and expects it to be unchanged.

It gets worse. If I change the call to

```
axis[99]
```

which is an obvious bug because it is trying the pass the hundredth element of an array that has only three, the warning is unchanged! Whats going on here?

What I would really like to do, would be to get better warnings out of the compiler. When I get 'incompatibles', is there any option to get the compiler to state exactly what the types are considered to be?


Can make errors be piped to a file?   I have tried   make release > make.log   but it just trapped the progress echo commands from the Makefile, with the errors going to the screen, the exact opposite of what would be useful!

I'm not getting off to a very good start with GCC. Any assistance would be most welcome.

---

### Post by nrs on 2008-08-22
Compiler warnings are God's way of telling you ***_YOU'RE DOING SOMETHING WRONG_***. Don't. How is the function actually defined? And 2> for stderr.

---

### Post by hod139 on 2008-08-22
Warnings are very important to listen too, as they can catch many errors.  However, I'm not understanding your question.

Here is a small code snippet, with my best guesses of what a vec3_t is.
[php]
typedef float vec_t;
typedef vec_t vec3_t[3];


void function(const vec3_t axis[3]){ }

int main(){
   vec3_t axis[3]; // array of vec3_t arrays
   
   function(axis);

   return 0;
}
[/php]

This code compiles without warning, but I'm confused as to why you want to have an array of arrays.  Before I try and figure out anything with your code, I want to make sure my snippet is correct.

---

### Post by PeterBBB on 2008-08-22
Thanks for your help guys. Pretty much sorted now.

> "2> for stderr"

Vast improvement.  I see from the line count there exactly 541 warnings.  Its not my code by the way, I'm building someone else's source, so I can't explain why things are being done here.


I should have checked the GCC bug log prior to posting. Sorry! Clarity of incompatibles is due in 4.4

[http://gcc.gnu.org/bugzilla/show_bug.cgi?id=30949](http://gcc.gnu.org/bugzilla/show_bug.cgi?id=30949)


> I want to make sure my snippet is correct

Absolutely!

> This code compiles without warning

**Oh no it doesn't** ;-)

```
peter$ cc test.c
test.c: In function ‘main’:
test.c:10: warning: passing argument 1 of ‘function’ from **incompatible pointer type**
peter$ 
```

> Compiler warnings are God's way of telling you YOU'RE DOING SOMETHING WRONG

I thought that too. Not it would seem if the compiler is called GCC.  

I found the explanation here
[http://gcc.gnu.org/bugzilla/show_bug.cgi?id=17654](http://gcc.gnu.org/bugzilla/show_bug.cgi?id=17654)

The 'pointless warning' bug was raised four years ago and the 'resolution' was not to fix it. Seems strict compliance with the 'standard' seems sadly more important than writing robust code. The developer has sensibly IMHO chosen to restrict the scope of called functions to modify their parameters and is rewarded with a pointless warning!  The problem of course is with over 500 warnings, which if any are real? 

From the link

"Nevertheless they appear to be pointless **and restricting from writing clean code**, which is why I filed this."


I'm still hoping I'm going to awake from a bad dream. Are they really building the kernel with this .... ?

---

### Post by dwhitney67 on 2008-08-22
This compiles:
[PHP]typedef float vec_t;
typedef vec_t vec3_t[3];


void function( const vec3_t axis[3] )
{
}


int main()
{
  const vec3_t axis[3] = { {1,2,3}, {4,5,6}, {7,8,9} };

  function( axis );

  return 0;
}[/PHP]
Now, if you want to declare 'axis' within the main() function as non-const, then when passing 'axis' to function(), cast it to const vec3_t *.  For example:
[PHP]function( (const vec3_t *) axis );[/PHP]

---

### Post by PeterBBB on 2008-08-22
> if you want to declare 'axis' within the main() function as non-const

**      YES**


```
(const vec3_t *) axis
```


**Thats** the answer!   Faith in GCC restored. 


Thanks everyone. Enjoy the weekend.

---

### Post by PeterBBB on 2008-08-23
"I woke up this morning...."

and on reflection do think that this warning text is most unhelpful in this case. Especially given that C++ and PHP do not warn at all.

'const' is not a pointer type.  Its an attribute.


If the message instead of saying

```
passing argument 1 of ‘function’ **from incompatible pointer type**

```
said

```
passing argument 1 of ‘function’ **with inconsistent attribute(s)**
```

the problem should have been obvious, and this thread wouldn't exist. There is also a potential knock on to the enhancement to clarify incompatible types. If the new message just says something like "argument vec3_t[3] incompatible with declaration vec3_t[3]", the developer will be even more confused.

I sense a steep learning curve ahead....

Pete
*unrecognized option '-help'*

---

