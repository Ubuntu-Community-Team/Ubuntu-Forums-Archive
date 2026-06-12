---
title: "Declaring a function in C"
date: 2012-08-28
forum: Programming Talk
---

### Post by IAMTubby on 2012-08-28
Hi,
I'm really confused about the need for declaring a function in C.

When I write(define) a function of this type
```
int fun(int, int, ...); or
void fun(int, int..)
```
there is no need for any declaration. Direct definition would do.

But the moment, the return type/ any of the arguments is not void/int, it gives me an error message indicating the need for declaration. For example
```
int fun(float a)
{
 printf("\nFloat value = %f",a);
}
```
This function needs a declaration like
```
int fun(float);
```

Why is this ? 
Thanks

PS : Throughout the post, I am talking about definitions after main. If definitions were written before main, there is no need for any declarations,right. Just a disclaimer.

---

### Post by muteXe on 2012-08-28
why are you declaring anything after main()?

---

### Post by IAMTubby on 2012-08-28
Didn't get you on that one.
No, I am not declaring anything after main.

---

### Post by ofnuts on 2012-08-28
> **IAMTubby said:**
> Why is this ? 
If only because this lets  the compiler check tat you are calling functions properly and getting their results the right way?

'Int' used to be a default in early C. 

Btw the way, if you declare a function thus:
```
int fun(float a)
```
Then it should contain:
```
return some_int_value;
```

---

### Post by codemaniac on 2012-08-28
Function prototypes are essential in a C program .

See the "Uses" section in the below link .

[http://en.wikipedia.org/wiki/Function_prototype](http://en.wikipedia.org/wiki/Function_prototype)

---

### Post by IAMTubby on 2012-08-28
Okay. So can we conlude that the default return type is 'int' or 'void' and the arguments are also 'int' or 'void' ?

---

### Post by spjackson on 2012-08-28
> **IAMTubby said:**
> Okay. So can we conlude that the default return type is 'int' or 'void' and the arguments are also 'int' or 'void' ?
It depends which dialect of C you are talking about. There are 3 main language definitions in use to day.

[LIST=1]
[*]Original K&R (from 1970 to 1986 approx).
[*]C89/C90 based on ANSI C 1986.
[*]C99 The current C standard.
[/LIST]
In K&R C, the default return type is int and parameters default to int. There is no void keyword. In C99, both implicit int and implicit function declarations are removed. C90 is somewhere in between!

If you declare function prototypes before use, declare return types and parameter types, then you won't go far wrong whichever standard you are working to, with the caveat that void might not work with the most ancient of compilers.

What are you using as a reference for learning C?

---

### Post by Bachstelze on 2012-08-28
Post. Your. Code.

Declaring functions before use is always desirable but not always required.

---

### Post by IAMTubby on 2012-08-28
> **spjackson said:**
> It depends which dialect of C you are talking about. There are 3 main language definitions in use to day.

[LIST=1]
[*]Original K&R (from 1970 to 1986 approx).
[*]C89/C90 based on ANSI C 1986.
[*]C99 The current C standard.
[/LIST]
In K&R C, the default return type is int and parameters default to int. There is no void keyword. In C99, both implicit int and implicit function declarations are removed. C90 is somewhere in between!

If you declare function prototypes before use, declare return types and parameter types, then you won't go far wrong whichever standard you are working to, with the caveat that void might not work with the most ancient of compilers.

What are you using as a reference for learning C?
Hmm, not really using a fixed reference. sorry!
But I'm using gcc as my compiler ? Is that enough information to figure out which C I'm using ?

---

### Post by muteXe on 2012-08-28
lol he really doesn't want to post his code does he?

---

### Post by IAMTubby on 2012-08-28
haha.. it's not that.
There is really no code. I was just trying to understand what is the default return type for a function and the default data types of the arguments.

---

### Post by Bachstelze on 2012-08-28
This is not an area where just putting nothing and using the default would be a wise decision. You should really always declare your functions, not doing it is asking for trouble.

---

### Post by IAMTubby on 2012-08-28
Okay, thanks for that. Shall take care of it in future.
So what's the return for a failure condition again ?
(Because negative values are never returned)

Sorry : I want to delete this post, but am only able to edit it. No reply necessary!

---

### Post by spjackson on 2012-08-28
> **IAMTubby said:**
> Hmm, not really using a fixed reference. sorry!
But I'm using gcc as my compiler ? Is that enough information to figure out which C I'm using ?
So you are trying to learn the language by trial and error? I wouldn't recommend that.

The default language for gcc is gnu89, which is "GNU dialect of ISO C90 (including some C99 features)." So, if that's what you want to learn, we can answer appropriately for that context.

You can change this default by using -ansi or -std= compiler flags combined with several further switches that affect the language.

---

### Post by IAMTubby on 2012-08-28
spjackson,
I think I'll first look up how these standards differ from each other.
Or maybe if you could tell me the important differences, I can go and google the others. 

Thanks.

---

### Post by Bachstelze on 2012-08-29
In general which version of the standard you should use will be dictated by the project you are working on (if the project uses C89, then you will have to use C89, for example). If you are starting a new project and don't have any other requirement, then the choice is entirely up to you and it's a matter of personal preference. C89 is older and in general more conservative and a little more rigid. For exemple, C99 allows two things that C89 does not and that I find nice, which are illustrated by constructs like:

```
for (int i=0; i<N; i++) {
    /* loop */
}
```

and

```
int main(void)
{
    /* do something */
    if (error) {
        exit(EXIT_FAILURE);
    }
}
```


In the first case, the [font=monospace]i[/font] variable is local to the loop, meaning it does not exist outside of it. I like it because having the counter variable sit around in my program between loops, where it is not needed, bothers me. C99 allows the variable to be declared inside the for () statement, while C89 does not.

In the second case, I do not return 0 from main or otherwise handle the "no error" case, because C99 states that when control reaches the end of [font=monospace]main()[/font], 0 is returned. I like it because I think it helps clearly separate success and failure: if there is an error, I [font=monospace]exit()[/font] with the appropriate error code, and if there isn't, I just do nothing and let the program terminate successfully by itself. This is permitted by C99, but in C89 if you don't put a return statement then [font=monospace]main()[/font] will return an undefined value.

---

