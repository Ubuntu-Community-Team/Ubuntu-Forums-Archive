---
title: "is it possible to hold different types of function pointers in a table(structure)"
date: 2013-03-25
forum: Programming Talk
---

### Post by IAMTubby on 2013-03-25
Hello,
I want a design like

```

typedef struct _LOOKUP
{
 char* FunctionSignature;
  **_*DONTKNOW*_** FunctionPointer;
}LOOKUP;

```
And I want to populate it something like,

LOOKUP* ptr;
ptr->FunctionSignature = "iic";//which is code for int fun(int, char);
In that case, ptr->FunctionPointer = **_*int (*fptr)(int, char);*_**

Thanks.

PS : Assume my requirement is that, I want to use a function pointer depending on the function supplied as input by a user, and I want to call this function using a FunctionPointer which has been maintained in the LOOKUP table.

---

### Post by Tony Flury on 2013-03-25
you can do that by  using a union - so that you can use the correct type for your pointer when you store them.

The only other option is to store everything as a (void *)(void) , and make sure you cast to the right type when you try to call it.

C does NOT have dynamic typing.

---

### Post by IAMTubby on 2013-03-25
> **Tony Flury said:**
> The only other option is to store everything as a (void *)(void) , and make sure you cast to the right type when you try to call it.

Tony Flury, I'm trying this out right now, and shall get back to you in a few minutes with the result. I'll have to do some googling about typecasting etc, not very comfortable with them. Please help me out after I have tried.

> 
you can do that by using a union - so that you can use the correct type for your pointer when you store them.

I didn't get this, but it's cool, let me try the void pointer method first.

---

### Post by IAMTubby on 2013-03-26
> **Tony Flury said:**
> 
The only other option is to store everything as a (void *)(void) , and make sure you cast to the right type when you try to call it.

TonyFlury, check this out. Is is okay ?
Basically, I am receiving the return from dlsym call as a void* and then typecasting it to type FPTR_REQ.(By REQ, I meant required)

```

#include <stdio.h>
#include <stdlib.h>
#include <dlfcn.h>


float fun(int, char*);
[b]typedef void* (*FPTR_VOID)(void);
typedef float (*FPTR_REQ)(int,char*);[/b]


int main(void)
{
 void* handle;
 char* error;
 FPTR_VOID fptr_void;
 FPTR_REQ fptr_req;
 float ret;


 handle = dlopen(NULL,RTLD_LAZY);
 if(!handle)
 {
  fprintf(stderr,"%s\n",dlerror());
  exit(1);
 }
 dlerror();
** fptr_void = dlsym(handle,"fun");**
 if((error = dlerror()) != NULL)
 {
  fprintf(stderr,"%s\n",error);
  exit(1);
 }
  **fptr_req = (FPTR_REQ)fptr_void;**
 ret = (*fptr_req)(1,"hello");


 printf("ret == [%f]\n",ret);


 return 0;
}


float fun(int a, char* str)
{
 printf("a == [%d]\n",a);
 printf("str == [%s]\n",str);
 return 3.14;
}

```

Build steps : 
gcc -rdynamic -o exe main.c -ldl

---

### Post by Tony Flury on 2013-03-26
what about functions which have a different call signature - you might want your proof of concept code to execute a number of different function signatures before you put this concept into production.

---

### Post by nvteighen on 2013-03-26
Take a look at the first answer to this discussion thread: [http://stackoverflow.com/questions/10519312/how-does-this-make-sense-void-fptr-dlsymhandle-my-function](http://stackoverflow.com/questions/10519312/how-does-this-make-sense-void-fptr-dlsymhandle-my-function)

Interestingly, it seems that the POSIX "approved" way (the horrible and infamous *(void **)(&ptr) cast) that you find on dlsym's manpage breaks the POSIX standard itself... :S (I haven't proven this, but I'll do it right now... Where's my compiler? :D)

---

### Post by IAMTubby on 2013-03-26
> **Tony Flury said:**
> you might want your proof of concept code to execute a number of different function signatures before you put this concept into production.
Sure Sir, I shall do that and get back in some time.

But, just going back, ideally I would like to have a design where, I can call the function using the function pointer returned by dlsym irrespective of the signature of the function.Consider a scenario like this,
[B]
"There are 4 functions defined in a program. Assume all 4 functions are of different signature. The program logic executes the correct function depending on the name of the function supplied as input by the user. Needless to say, I don't want to execute the function using an if-else construct like *if(user says fun3){fun3();*},  but do a dlsym for fun3 and execute using the function pointer returned. "[/B]
Is is possible to achieve this ?

Thanks.

---

### Post by IAMTubby on 2013-03-26
> **nvteighen said:**
> Take a look at the first answer to this discussion thread: [http://stackoverflow.com/questions/10519312/how-does-this-make-sense-void-fptr-dlsymhandle-my-function](http://stackoverflow.com/questions/10519312/how-does-this-make-sense-void-fptr-dlsymhandle-my-function)

Interestingly, it seems that the POSIX "approved" way (the horrible and infamous *(void **)(&ptr) cast) that you find on dlsym's manpage breaks the POSIX standard itself... :S (I haven't proven this, but I'll do it right now... Where's my compiler? :D)
nvteighen, thank you so so much for telling that there could be a mistake there. That code had left me totally confused. To me(maybe my lack of knowledge, but, nevertheless), it was like instead of saying -5 you say, -(--5).
I'll read the link and wait for your reply :).

---

### Post by trent.josephsen on 2013-03-26
If the functions have different signatures, you're going to have to do some kind of if-else construct anyway, in order to pass the correct arguments. No form of polymorphism or dynamic typing is possible in C unless you write it yourself.

You're new to C and trying to do something that is not only unsafe, but needlessly complex and unnecessary. Stop. Learn to use the language properly first; make a text adventure or a program to manage your finances or something. Take a break and learn some assembly instead, if you're into that kind of thing. Then, if some day 10 years from now you find you really *need* to use dlsym, you won't be simultaneously trying to figure out calling conventions and stack frames and function pointer declarations and so forth.

It's perfectly possible to write reusable, maintainable code in C, but to do so you'll have to abandon dynamic typing, polymorphism, overloading and other shortcuts that some languages do for you magically. Don't try to force them to work, because even if you succeed, you will only have made an unmaintainable mixture of C and non-C. And there are enough C++ programmers in the world already.

---

### Post by nvteighen on 2013-03-26
> **trent.josephsen said:**
> If the functions have different signatures, you're going to have to do some kind of if-else construct anyway, in order to pass the correct arguments. No form of polymorphism or dynamic typing is possible in C unless you write it yourself.

You're new to C and trying to do something that is not only unsafe, but needlessly complex and unnecessary. Stop. Learn to use the language properly first; make a text adventure or a program to manage your finances or something. Take a break and learn some assembly instead, if you're into that kind of thing. Then, if some day 10 years from now you find you really *need* to use dlsym, you won't be simultaneously trying to figure out calling conventions and stack frames and function pointer declarations and so forth.

It's perfectly possible to write reusable, maintainable code in C, but to do so you'll have to abandon dynamic typing, polymorphism, overloading and other shortcuts that some languages do for you magically. Don't try to force them to work, because even if you succeed, you will only have made an unmaintainable mixture of C and non-C. And there are enough C++ programmers in the world already.

I wouldn't discourage anyone to research on these topics. If he's interested, great and *endavant*, as Catalans say! However, I agree with you that it's rather counterproductive to try to shoe-horn a homebrewed implementation of dynamic programming into any serious thing you're writing (defining "serious" as "something you care about, be it a hobby or a job"), as you'll be quickly frustrated or may lose a lot of worktime. If you need something like that, you'd either have to switch to a truly dynamic language (I'm excluding you, C++) or, if C is a requirement, use some hard-proven library like GLib or, better, combine C with another language.

Don't set yourself any limits when learning programming, but be realistic on what your tools can do for you when you need them.

---

### Post by IAMTubby on 2013-03-26
> **nvteighen said:**
> I wouldn't discourage anyone to research on these topics. If he's interested, great and *endavant*, as Catalans say! However, I agree with you that it's rather counterproductive to try to shoe-horn a homebrewed implementation of dynamic programming into any serious thing you're writing (defining "serious" as "something you care about, be it a hobby or a job"), as you'll be quickly frustrated or may lose a lot of worktime. If you need something like that, you'd either have to switch to a truly dynamic language (I'm excluding you, C++) or, if C is a requirement, use some hard-proven library like GLib or, better, combine C with another language.

Don't set yourself any limits when learning programming, but be realistic on what your tools can do for you when you need them.
Thanks nvteighen :)

---

### Post by IAMTubby on 2013-03-26
> **trent.josephsen said:**
> If the functions have different signatures, you're going to have to do some kind of if-else construct anyway, in order to pass the correct arguments. No form of polymorphism or dynamic typing is possible in C unless you write it yourself.

You're new to C and trying to do something that is not only unsafe, but needlessly complex and unnecessary. Stop. Learn to use the language properly first; make a text adventure or a program to manage your finances or something. Take a break and learn some assembly instead, if you're into that kind of thing. Then, if some day 10 years from now you find you really *need* to use dlsym, you won't be simultaneously trying to figure out calling conventions and stack frames and function pointer declarations and so forth.

It's perfectly possible to write reusable, maintainable code in C, but to do so you'll have to abandon dynamic typing, polymorphism, overloading and other shortcuts that some languages do for you magically. Don't try to force them to work, because even if you succeed, you will only have made an unmaintainable mixture of C and non-C. And there are enough C++ programmers in the world already.
Sir, okay. Will try for some more time, and if it doesn't happen, won't continue.
As you said, I should learn things one-by-one, but just that I was so excited to put it all together.
Thanks once again.

---

### Post by ofnuts on 2013-03-26
> **IAMTubby said:**
> **"There are 4 functions defined in a program. Assume all 4 functions are of different signature. The program logic executes the correct function depending on the name of the function supplied as input by the user. Needless to say, I don't want to execute the function using an if-else construct like *if(user says fun3){fun3();*},  but do a dlsym for fun3 and execute using the function pointer returned. "**
Is is possible to achieve this ?

Thanks.
If the functions have ***different signatures*** then you have to pass parameters differently (and retrieve the returned results differently too(*)....). Then either: 
[LIST]
[*]you have a finite set of signatures: define a pointer type for each function and keep the pointer in a union (as discussed above)
[*]you have random signatures: you have to define some form of description for the signature (C-like or else) that you can keep together with the function pointer, and that you code can use to dynamically construct the call stack structure.
[/LIST]

(*) which is an interesting problem all by itself since C allows returning structures....

---

### Post by trent.josephsen on 2013-03-26
Eh, there comes a point where coding for the sake of learning to code, without giving thought to design, becomes counterproductive. I'd argue this is such an area.

> **ofnuts said:**
> define some form of description for the signature (C-like or else) that you can keep together with the function pointer, and that you code can use to dynamically construct the call stack structure.
I might add (for the benefit of the future reader) that this would be, at best, an imperfect copy of what your C implementation was doing for you to start with. Which, when you realize it, should normally be its own red flag.

---

