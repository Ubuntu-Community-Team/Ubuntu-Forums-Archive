---
title: "C: malloc inside function doesn't allocate"
date: 2010-11-03
forum: Programming Talk
---

### Post by Pithikos on 2010-11-03
I was all day long at university today fighting with malloc!
This is a simple testcode to demonstrate the problem:
```
#include <stdio.h>
#include <stdlib.h>

void allocArray(int *array){
  array=(int*)malloc(100);
  array[0]=10;
}

int main(){
  int *array;
  allocArray(array);
  printf("array[0]=%d\n", array[0]);
    return 0;
}
```What it does is making a pointer to an integer(array). Then I run the allocArray that allocates 100bytes for the array. Just after that i give a value to the second element of the array(array[1]).
When all that is done I just have a printf to see what is inside array[1] and I get nothing than "Segmentation fault".

After hours and hours I found out that returning the array and storing it as array in main made the thing work in this way:
```

main(){
..
array=allocArray(array);
..
}

```To me that doesn't make much sense. And although I bypassed the problem I still wonder why the heck I have to return anything when I have already passed a pointer?

---

### Post by GeneralZod on 2010-11-03
When calling allocArray(...) in main, you are passing *array* by value, so it is completely unchanged by the call to allocArray(...) :) (further: you didn't initialise it, so it will likely be pointing to a completely random area of memory).

Edit:

To clarify a little more: even though the *array* in main() is a pointer, you are passing this pointer *by value*: the "*array*" inside allocArray(...) is a *copy* of the original *array* from main(), and it is this *copy* that is assigned the result of the malloc call - not the original *array* in main()!

Here's an example without the confusion of pointers: what do you think will happen here?

```

#include <stdio.h>

void setTo3(int i)
{
    i = 3;
};

int main(void)
{
    int i = 0;
    setTo3(i);
    printf("Surprise! i = %d", i);
    return 0;
}

```

---

### Post by worksofcraft on 2010-11-03
as GeneralZod says, you passed in the pointer's value, which becomes a new pointer in your function. If you want to pass it back out again with the new value that malloc gives it you must pass it by reference.

If you compile it with the C++ compiler you can fix it with a single &
[php]
// g++ malloc_byref.cc
#include <stdio.h>
#include <stdlib.h>

void allocArray(int * &array){
  array=(int*)malloc(100);
  array[0]=10;
}

int main(){
  int *array;
  allocArray(array);
  printf("array[0]=%d\n", array[0]);
    return 0;
}
[/php]

spot the difference ;)

---

### Post by dwhitney67 on 2010-11-03
Two ways to solve this problem:  1) Pass the address of the pointer that you want to update, or 2) just return the allocated memory directly.

```

void allocArray(int** array, const size_t size)
{
   *array = malloc(sizeof(int) * size);
}

/* or */

int* allocArray(const size_t size)
{
   return malloc(sizeof(int) * size);
}

...

int main(void)
{
   int* array = 0;

   allocArray(&array, 100);

   ...

   free(array);

   ...
}

/* or */

int main(void)
{
   int* array = allocArray(100);

   ...

   free(array);

   ...
}

```

---

### Post by dwhitney67 on 2010-11-03
> **worksofcraft said:**
> 
spot the difference ;)
What I do spot is that you are (again) mixing C and C++.  When one programs in C, it is generally for a very specific reason.  You can't just insert concepts from another language at will.  Maybe the code is for an embedded device using an *Acme* processor for which there is no C++ compiler!

---

### Post by Pithikos on 2010-11-03
I didn't really understand what you mean with "passing** array by value" but as about your little exercise I would say that i is still 0. Never thought before about this really. If I didn't get brainwashed with writing code then I would in fact say that as i is a "global" in the function main(), it should in fact be able to change its value by calling setTo3(), if thinking logically with my tiny brain \\:D/

And by the way I just remembered something else that was mentioned by the teacher. "As a function in C can only return one value we use pointers to change values in variables outside the specific function." That was what I had in my mind when making that piece of code that in the end didn't work.

---

### Post by worksofcraft on 2010-11-03
> **dwhitney67 said:**
> What I do spot is that you are (again) mixing C and C++.  When one programs in C, it is generally for a very specific reason.  You can't just insert concepts from another language at will.  Maybe the code is for an embedded device using an *Acme* processor for which there is no C++ compiler!

When it comes to explaining a concept it doesn't matter if I use C or C++ or Python or Lisp.... I am trying to explain the concept of passing a pointer by reference. The fact that in C you have to achieve that by passing a pointer to a pointer by value ... is not as clear IMO.

p.s. according to Stroustrup (appendix B.2 "C/C++ Compatability)
"With minor exceptions, C++ is a superset of C... Well written C programs tend to be C++ programs as well." Thus using C++ to explain a concept that isn't part of C is a reasonable thing to do.

---

### Post by Pithikos on 2010-11-03
By the way here is a demonstration about my global assumption I wrote earlier:

```
#include <stdio.h>

int a=1;

void changeVal(){
  a=3;
}

int main(){
  changeVal();
  printf("%d\n", a);
  return 0;
}

```So in this example it's possible to change the value of a without either *return *or pointers.
So if it can work this way, shouldn't it be possible for it to  work this way too?:

```
#include <stdio.h>

void changeVal(){
  a=3;
}

int main(){
  int a=1; /*moved declaration of a here*/
  changeVal();
  printf("%d\n", a);
  return 0;
}

```And yeah I know the subject changed a bit now :roll:

---

### Post by dwhitney67 on 2010-11-03
> **Pithikos said:**
> ... shouldn't it be possible for it to  work this way too?:

You obviously know about global variables; you're first example proves that.

In your second example, you are declaring a **local** variable within the main() function.  I do not know how you can expect it to be usable within any other function unless you pass it by reference (ie the address) or by value.

---

### Post by worksofcraft on 2010-11-03
lol - yes... a global variable is just like a pass by reference but being passed to everything without mention. I presume you saw the [thread about global variables]("http://ubuntuforums.org/showthread.php?t=1611302") asking about genuine applications for them?

---

### Post by trent.josephsen on 2010-11-03
> **worksofcraft said:**
> When it comes to explaining a concept it doesn't matter if I use C or C++ or Python or Lisp.... I am trying to explain the concept of passing a pointer by reference. The fact that in C you have to achieve that by passing a pointer to a pointer by value ... is not as clear IMO.

p.s. according to Stroustrup (appendix B.2 "C/C++ Compatability)
"With minor exceptions, C++ is a superset of C... Well written C programs tend to be C++ programs as well." Thus using C++ to explain a concept that isn't part of C is a reasonable thing to do.

I applaud your attempts to encourage new programmers to mix languages and insist that C is somehow inferior to C++.  Your teaching style, which as far as I can tell consists of saying "Use C++ to do it this way," and defending yourself by claiming to teach broad concepts rather than language details (when in fact you gave no explanation of the concept you claim to be teaching), is certainly novel.  You should call up [Herb Schildt](http://catb.org/jargon/html/B/bullschildt.html); I hear he's a C expert too.  It's a good thing people like you and he exist to correct those who have mere years of practical experience.

@OP:  All function parameters in C are passed "by value"; that is, the value of the real argument is copied into the function parameter at runtime.  Assignment works the same way, so when you assign array=(int*)malloc(100) in your original code, you overwrite the value that was originally stored in array.  (By the way, it's bad form to cast the result of malloc.)

The key is that you can use & to get a pointer to an object.  The value stored in a pointer is a reference to the object, so you can pass this value into a function and use it to access the original object the same way you would in your main code.

Here's a simple example of using a pointer to modify data in main from within a function (untested):

```
#include <stdio.h>

/* takes a pointer-to-int and the new value */
void set(int *p, int value)
{
    *p = value; /* set thing-referenced-by-p to value */
}

int main(void) /* always prototype main */
{
    int a = 3;
    printf("a = %d\n", a);
    set(&a, 4); /* &a evaluates to a pointer to a */
    printf("a = %d\n", a);
    return 0; /* success */
}
```

In the case of your original code, the value you want to set is already a pointer, so you need to pass a pointer that references that pointer if you want to change it in-place.  Think carefully about how you would do that, and then try to understand how dwhitney67 did it.

---

### Post by saulgoode on 2010-11-03
> **Pithikos said:**
> So if it can work this way, shouldn't it be possible for it to  work this way too?:

```
#include <stdio.h>

void changeVal(){
  a=3;
}

int main(){
  int a=1; /*moved declaration of a here*/
  changeVal();
  printf("%d\n", a);
  return 0;
}

```

There is nothing particularly special about the function main() other than it being called by the system after the program has been loaded. Variables defined within main() are not global; they are local to main().

---

### Post by worksofcraft on 2010-11-03
> **trent.josephsen said:**
> I applaud your attempts to encourage new programmers to mix languages and insist that C is somehow inferior to C++.  Your teaching style, which as far as I can tell consists of saying "Use C++ to do it this way,"...



Well actually the intention was to pass something by reference so that it gets the reader thinking about what the difference actually is.

If you want to teach concepts you might consider using a language that actually supports those concepts. While you might not agree with the way I decided to contribute on this thread it doesn't condone ridiculing, scoffing and sneering.

---

### Post by spjackson on 2010-11-03
> **worksofcraft said:**
> 
If you compile it with the C++ compiler you can fix it with a single &
[php]
void allocArray(int * &array){
[/php]
Perhaps it's just something about me but that code makes me squirm, and it's not just the lacing of C code with a spot of C++ sugar in a thread with C in the title. And I don't think it's just because the PHP markup shows the int * in blue and the &array in green. If I ever wanted such an interface in C++, I'm sure that I would always use a pointer to a pointer rather than a reference to a pointer. A reference to a pointer somehow doesn't feel right to me.

I also find it odd not to have a space between the type and the variable. I'm sure I once read that C programmers tend to write char *s (after K&R) and C++ programmers tend to write char* s (after Stroustrup). Maybe that's part of the reason why it looks so odd to me here: it's C++ syntax with a C style.

---

### Post by worksofcraft on 2010-11-03
> **spjackson said:**
> Perhaps it's just something about me but that code makes me squirm...


Coding style is a completely different matter.

I wouldn't use that style either and it wasn't intended as a recommendation.

Personally I don't ever like passing by reference for the sake of returning results, because it isn't clear when you read the code that your parameters are being changed... except that in this case the OP was actually *expecting* it to be changed

---

### Post by nvteighen on 2010-11-04
> **worksofcraft said:**
> When it comes to explaining a concept it doesn't matter if I use C or C++ or Python or Lisp.... I am trying to explain the concept of passing a pointer by reference. The fact that in C you have to achieve that by passing a pointer to a pointer by value ... is not as clear IMO.

p.s. according to Stroustrup (appendix B.2 "C/C++ Compatability)
"With minor exceptions, C++ is a superset of C... Well written C programs tend to be C++ programs as well." Thus using C++ to explain a concept that isn't part of C is a reasonable thing to do.

I'll refrain to enter into the C vs. C++ debate and just tell you this: it's good paedagogical practice to not change the language the original poster is using, no matter how much you dislike that language. Otherwise, you won't be helping, but confusing people. I guess anyone having some lecturing experience will agree with me.

---

### Post by worksofcraft on 2010-11-04
> **nvteighen said:**
> I'll refrain to enter into the C vs. C++ debate and just tell you this: it's good paedagogical practice to not change the language the original poster is using, no matter how much you dislike that language. Otherwise, you won't be helping, but confusing people. I guess anyone having some lecturing experience will agree with me.

I'll just quote from Bjarne Stroustrup C++ programming Language 3rd Edition Appendix B.2

C/C++ Compatability:
"With minor exceptions C++ is a superset of C... Well written C programs tend to be C++ programs as well...

So this is also a C++ program not a change in language. Besides, adding a single character is hardly a big change especially when it then does what the op was expecting it to do in the first place.

---

### Post by NovaAesa on 2010-11-04
> **worksofcraft said:**
> Besides, adding a single character is hardly a big change especially when it then does what the op was expecting it to do in the first place.
Except that the one character turns a valid C program into an invalid C program...

---

### Post by worksofcraft on 2010-11-04
> **NovaAesa said:**
> Except that the one character turns a valid C program into an invalid C program...

No it doesn't. It fixes a bug in a malfunctioning C++ program :D

It further demonstrates a practical application of pass by reference and by using such minimal adaptation of the original post it is beyond doubt didactically vastly superior and more effective than many other solutions posted here :P

---

### Post by dwhitney67 on 2010-11-04
> **worksofcraft said:**
> No it doesn't. It fixes a bug in a malfunctioning C++ program :D

It further demonstrates a practical application of pass by reference and by using such minimal adaptation of the original post it is beyond doubt didactically vastly superior and more effective than many other solutions posted here :P

It's is really comical how you just don't get that C and C++ are not the same.  Quoting Stroustrup out of context makes you seem more the fool.

The mere fact that you use the C++ (g++) version of the GCC compiler to compile C code is testament that you lack perspective into developing software for platforms that only support C language constructs.

As a self-purported "professional" software programmer, your approach to solving problems, and your lack of willingness to accept comments from peers, and your often "left-field" comments tend to indicate that you are more the hobbyist than a serious developer.  Or possibly you just lack the experience.

Merely fumbling through a Stroustrup book, and using quotes to support your position in a debate, IMO, is a sign of weakness.  Although I do agree that Stroustrup was brilliant in developing the C++ language, I do not worship every word uttered by him, and frankly I thought "The C++ Programming" book was poorly written.

Anyhow, perhaps in the future you can grace us with quotes from the K&R book when a person seeks help with a C problem, and leave the Stroustrup for when one seeks C++ help.  *Please*.

---

### Post by nvteighen on 2010-11-04
> **worksofcraft said:**
> I'll just quote from Bjarne Stroustrup C++ programming Language 3rd Edition Appendix B.2

C/C++ Compatability:
"With minor exceptions C++ is a superset of C... Well written C programs tend to be C++ programs as well...

So this is also a C++ program not a change in language. Besides, adding a single character is hardly a big change especially when it then does what the op was expecting it to do in the first place.

0. As Stroustrup says, "C++ is a superset of C with minor exceptions", which is a contradiction in terms: either C++ is a superset of C or it is not, but obviously based on the latter.

1. Even if we accepted that "C++ is a superset of C with minor exceptions" could be seen that C++ is a superset of C, trying to help people to learn C using C++-specific stuff is like trying to teach Spanish by teaching Latin or viceversa.

---

### Post by worksofcraft on 2010-11-04
> **nvteighen said:**
> 0. As Stroustrup says, "C++ is a superset of C with minor exceptions", which is a contradiction in terms: either C++ is a superset of C or it is not, but obviously based on the latter.

1. Even if we accepted that "C++ is a superset of C with minor exceptions" could be seen that C++ is a superset of C, trying to help people to learn C using C++-specific stuff is like trying to teach Spanish by teaching Latin or viceversa.

TBH I really don't see what problem some people are having here. 

Firstly if you want to debate about what is and what is not a superset of C with [Bjarne Stroustrup]("http://www2.research.att.com/~bs/3rd.html") then you will find his web pages there including an e-mail address.
 
Secondly, the OP expected a parameter to be passed by reference and so someone else had already given a good explanation of how C passes parameters by value. I decided to contribute that some programming languages **do** pass by reference. Giving an example using all the OP's same code with just a single character inserted did not appear to be a major leap in understanding.

p.s. @dwhitney67's comments on previous page. I never claimed to be a "professional programmer". It is a hobby in which I seek to be creative and original. Also I want to point out that I am **not** the one who is being critical and argumentative here :P

---

### Post by dwhitney67 on 2010-11-04
> **worksofcraft said:**
> 
p.s. @dwhitney67's comments on previous page. I never claimed to be a "professional programmer".

Actually, you have hinted otherwise in your previous posts.  In one you indicated that you've been programming for over 20 years, in another you indicated that all of the s/w "houses" where you worked at went under.  What was your position at these companies... the savant sanitation engineer?

Anyhow, you're response is welcomed.  Now that I know your background, I can approach your threads/replies with a bit more caution.

---

### Post by Pithikos on 2010-11-04
> **dwhitney67 said:**
> You obviously know about global variables; you're first example proves that.

In your second example, you are declaring a **local** variable within the main() function.  I do not know how you can expect it to be usable within any other function unless you pass it by reference (ie the address) or by value.

Well I was thinking that in the second example the function is called at the same scope. I mean that both  changeValue() and the variable itself are inside main().  But ok I supposed the reason that it doesn't work is that the function is called in main() but the function itself is outside main.
But can you then have the function changeValue() inside main? I don't remember if it's possible. Would it then work to change a value of a variable without return or passing a pointer/address of it? Maybe I just mix different languages :S



**[COLOR=Red]As about my first post about malloc[/COLOR]**
So what I understood is that if you want to change the array's elements or change it's length you just need to pass its address(which is the value of a pointer to the array).
so I could have: 

```


void allocArray(char**array_ptr){
array_ptr=(char*)malloc(100);
}

int main(){
  char *array;
  array_ptr;
  array_ptr=&array;

  allocArray(array_ptr);
}

```

I didn't test that but I guess it's the way to go?
Anyway I still wonder about some things. Why do we need a pointer to a pointer to a pointer to a pointer to a pointer to a pointer when all we need if we want to change something in a variable is to pass it's address? "array" is pointing to the first charachter of the array of characters(string), so practically it holds the address of the first element of the array, right? Isn't that enough to allocate memory for the array? Because as stated all we need is an address/pointer to change a value without using the keyword return.
```
 
 ____                                 ___
|array| points here    -->   |__| 
                                         |__|
                                         |__|
                                         |__|

``` 

Why use it this way?: 
```
      
 ________                                     ____                                    ___
|array_ptr| points here       -->      |array| points here  -->       |__| 
                                                                                                 |__|
                                                                                                 |__|
                                                                                                 |__|

```

---

### Post by Odexios on 2010-11-04
> **Pithikos said:**
> Well I was thinking that in the second example the function is called at the same scope. I mean that both  changeValue() and the variable itself are inside main().  But ok I supposed the reason that it doesn't work is that the function is called in main() but the function itself is outside main.
But can you then have the function changeValue() inside main? I don't remember if it's possible. Would it then work to change a value of a variable without return or passing a pointer/address of it? Maybe I just mix different languages :S



**[COLOR=Red]As about my first post about malloc[/COLOR]**
So what I understood is that if you want to change the array's elements or change it's length you just need to pass its address(which is the value of a pointer to the array).
so I could have: 

```


void allocArray(char**array_ptr){
array_ptr=(char*)malloc(100);
}

int main(){
  char *array;
  array_ptr;
  array_ptr=&array;

  allocArray(array_ptr);
}

```I didn't test that but I guess it's the way to go?
Anyway I still wonder about some things. Why do we need a pointer to a pointer to a pointer to a pointer to a pointer to a pointer when all we need if we want to change something in a variable is to pass it's address? "array" is pointing to the first charachter of the array of characters(string), so practically it holds the address of the first element of the array, right? Isn't that enough to allocate memory for the array? Because as stated all we need is an address/pointer to change a value without using the keyword return.
```
 
 ____                                 ___
|array| points here    -->   |__| 
                                         |__|
                                         |__|
                                         |__|

```Why use it this way?: 
```
      
 ________                                     ____                                    ___
|array_ptr| points here       -->      |array| points here  -->       |__| 
                                                                                                 |__|
                                                                                                 |__|
                                                                                                 |__|

```
Because you have to change the value stored in the variable "array".

"array" is a pointer, so its value is an address. What you want to do is change the value of "array", so that "array" points to a different address. When you do what you did with your first program, you pass the value of the variable "array" to the function allocArray; which means that, calling allocArray, you created a new variable, called "array", with the same value of main's "array", which was a random address. You then changed the value of allocArray's "array", but you did nothing to main's "array".

To change the value of a variable by using a function, you have to pass to the function the address of the variable, so that the function is able to get to that address and actually change the value.

Btw, no, you can't declare a function inside another function, if that is what you were asking. And, yes, you got it right; allocArray isn't inside main, so their scope is not the same.

EDIT: Sorry, I didn't notice. The code isn't right; you are a little confused about how C pointers work, I'd dare say.

Let's see why that code doesn't work.

You first declared a function, allocArray, and told it to expect a parameter, a pointer to pointer to char (in this scenario, a pointer to the index of an array of char). And we're fine, for now. But when you changed the value of array_ptr, you changed the value of a variable which is local to allocArray. Every time you call allocArray(), a new variable, which has *nothing* to do with main's array_ptr, is declared; if you change its value, nothing changes inside main. To change main's array's value, as I said before, you sould pass to the function the address of array, so that the function is directly able to change the value inside array's memory cell. So, inside the function you should change the value pointed by the address you passed to the function; so, (*array_ptr) = whatever;.

Let's look at main(). You used a variable whithout declaring it's type (was it a typo?). Besides, that variable wasn't necessary; you could have just called allocArray(&array). It would have called allocArray, created a new variable, char **array_ptr, local to that single call of allocArray, which contained the address of main's array,  and changed the value pointed by **array_ptr, so the value pointed by the address of main's array, so array's value.

Sorry for any error, but I'm not used to write in English.

---

### Post by worksofcraft on 2010-11-04
> **dwhitney67 said:**
> Actually, you have hinted otherwise in your previous posts.  In one you indicated that you've been programming for over 20 years, in another you indicated that all of the s/w "houses" where you worked at went under.  What was your position at these companies... the savant sanitation engineer?

Anyhow, you're response is welcomed.  Now that I know your background, I can approach your threads/replies with a bit more caution.

I was an electronics engineer responsible for testing electronic  circuits. It usually involved programming to exercise the hardware, but luckily not to the standards of the actual product software :P Anyway I think I already said I stopped working in that industry about 15 years ago.

---

### Post by saulgoode on 2010-11-04
> **Pithikos said:**
> But can you then have the function changeValue() inside main? I don't remember if it's possible. Would it then work to change a value of a variable without return or passing a pointer/address of it? Maybe I just mix different languages :S
Nested functions are not part of the ANSI C standard; however, some compilers (including GNU's GCC) support them. 

> **Pithikos said:**
> Anyway I still wonder about some things. Why do we need a pointer to a pointer to a pointer to a pointer to a pointer to a pointer when all we need if we want to change something in a variable is to pass it's address? "array" is pointing to the first charachter of the array of characters(string), so practically it holds the address of the first element of the array, right? Isn't that enough to allocate memory for the array?
When you first declared 'array' (**char *array;**), the pointer is uninitialized (and not pointing anywhere). All that you've done is reserved some memory space to hold a pointer and assigned the address of that memory location to the symbol 'array'. 

The symbol 'array' has two different meanings in your program depending upon whether or not it appears on the left hand side of an assignment (**=**) operator. If it appears on the left of an assignment, the symbol is interpreted as a reference to the memory location (i.e., its address in memory). If the symbol appears anywhere else then it is interpreted as a reference to the *contents* of the memory at that location. 

This interpretation may be more readily apprehended by considering the assignment "**x = x + 1;**" -- the first 'x' is the address of memory location 'x' while the second 'x' is the contents of that location. Similarly, if the symbol 'x' appears as a parameter being passed to a function, "**foo(x)**", then it is interpreted as the contents of the memory location. The type of variable (pointer, integer, float, etc) associated with the symbol does not really play a role in this interpretation.

Now the above description is not entirely true; because it only describes the *default* behavior. This default behavior can be overridden by either 1) applying the dereferencing operator (*****) to the symbol when it appears to the left of an assignment operation, or 2) applying the referencing operator (**&**) to the symbol when it appears elsewhere. In both of these cases, usage of the modifier results in an interpretation of the symbol opposite of the default interpretation.

Personally, I do not get too caught up with labeling things as call by value or call by reference; as stated earlier, C is always call by value. What is important is whether that value is an address of a memory location, or the value is the contents of a memory location (and noting that the contents of a memory location can be the address of another memory location :) ). 

My apologies if I've confused you -- but this viewpoint works for me.

---

