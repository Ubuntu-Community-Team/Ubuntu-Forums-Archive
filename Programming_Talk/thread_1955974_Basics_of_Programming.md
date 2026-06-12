---
title: "Basics of Programming"
date: 2012-04-10
forum: Programming Talk
---

### Post by openbuntu on 2012-04-10
Hey guys, need advice on this. I finished writing a book for basic programming concepts...
here is the link comment on the content of the book... help me to improve....
[http://yengal-marumugam.blogspot.com/2012/04/books-basics-of-programming.html](http://yengal-marumugam.blogspot.com/2012/04/books-basics-of-programming.html)

---

### Post by ofnuts on 2012-04-10
> **openbuntu said:**
> Hey guys, need advice on this. I finished writing a book for basic programming concepts...
here is the link comment on the content of the book... help me to improve....
[http://yengal-marumugam.blogspot.com/2012/04/books-basics-of-programming.html](http://yengal-marumugam.blogspot.com/2012/04/books-basics-of-programming.html)
Don't bother. Unless you want a good laugh.

---

### Post by openbuntu on 2012-04-10
> **ofnuts said:**
> Don't bother. Unless you want a good laugh.

I cud not get u..

---

### Post by ofnuts on 2012-04-10
> **openbuntu said:**
> I cud not get u..If the 4 pictures and their contents are a "book" about "programming concepts", then I'm the natural son of Grace Hopper and Alan Turing.

---

### Post by Tony Flury on 2012-04-10
I downloaded your "book" to give it the benefit of the doubt. Compared to any other book i have read this is hardly a standout publication or even one useful to anyone. The english is tortured for a start - although i do appreciate that english may not be your first language. 

From your section on variables and values - you don't seem to understand the differences between register/static etc - they are suggestions as to where the compiler might store the values no instructions - in any case any sufficiently complicated program the compiler will almost always do a far better job of optimising code than the programmer will. Your description of arrays is confusing - and you make no mention of struct, or poniters, or stings with null delimiters or floats. You state categorically that a char is always one byte ad an it is always 4 bytes - that is by no means guaranteed.

Also no mention of floating point arithmetic, casts between types, rounding errors, arithmetical operators, etc etc etc.

Your section on flow control is equally difficult to read and no less inaccurate - you don't give sufficient examples of useful code - and all of your loops seem to concentrate on iteation on one variable - no mention of nesting of structures - or looping on other conditions, or items like break.

You state repeatedly that the reader will understand the differences between the few examples you give - but you never explain those differences - so one has to ask if you really understand them.

In your section on functions - two obvious items jump out - no mention of return, and no mention of recursion - two more items that you don't really undestand ?
Also in this chapter to stat using pointers without ever desrcibing them in pevious chapter, and you attempt to describe scope - but don't really succeed. You also suddently introduce two source code files - why not stick with one and make everyone's life so much easier.
You state that C supports functional programmig paradigm - you could not be more wrong - C suppots pocedural, and can be coerced to support OOP in a limited way. Functional is far more than just having fuctions in the language - Haskell is an example of a language that supports the functional paradigm. 


Finally - this is not really a book - it is simply a screen dump of a few blog entries. 

I do hope you don't spend any more time writing the book - at least ot until you are profficient (and preferably an expert in the language)

---

### Post by openbuntu on 2012-04-10
> **Tony Flury said:**
> I downloaded your "book" to give it the benefit of the doubt. Compared to any other book i have read this is hardly a standout publication or even one useful to anyone. The english is tortured for a start - although i do appreciate that english may not be your first language. 

From your section on variables and values - you don't seem to understand the differences between register/static etc - they are suggestions as to where the compiler might store the values no instructions - in any case any sufficiently complicated program the compiler will almost always do a far better job of optimising code than the programmer will. Your description of arrays is confusing - and you make no mention of struct, or poniters, or stings with null delimiters or floats. You state categorically that a char is always one byte ad an it is always 4 bytes - that is by no means guaranteed.

Also no mention of floating point arithmetic, casts between types, rounding errors, arithmetical operators, etc etc etc.

Your section on flow control is equally difficult to read and no less inaccurate - you don't give sufficient examples of useful code - and all of your loops seem to concentrate on iteration on one variable - no mention of nesting of structures - or looping on other conditions, or items like break.

You state repeatedly that the reader will understand the differences between the few examples you give - but you never explain those differences - so one has to ask if you really understand them.

In your section on functions - two obvious items jump out - no mention of return, and no mention of recursion - two more items that you don't really undestand ?
Also in this chapter to stat using pointers without ever desrcibing them in pevious chapter, and you attempt to describe scope - but don't really succeed. You also suddently introduce two source code files - why not stick with one and make everyone's life so much easier.
You state that C supports functional programmig paradigm - you could not be more wrong - C suppots pocedural, and can be coerced to support OOP in a limited way. Functional is far more than just having fuctions in the language - Haskell is an example of a language that supports the functional paradigm. 


Finally - this is not really a book - it is simply a screen dump of a few blog entries. 

I do hope you don't spend any more time writing the book - at least ot until you are profficient (and preferably an expert in the language)

Your reply was so helpful. 

          i .and the register/static variable thing I'm confused. help me there.
         ii. i started this with microcontrollers in mind - forgot to mention this.
        iii. i thought recursion was not important. 
        iv. sorry to say this - a book.

and I'm very thankful for u for reading it completely and attentively. thank u so much... i hope i cud improve it and I spent two long weeks in this, inspite of crushing obsi and recs, I don't just do copy and paste jobs.... I hope u cud understand wat i meant...

---

### Post by Tony Flury on 2012-04-10
> **openbuntu said:**
>  
          i .and the register/static variable thing I'm confused. help me there.
....

        iii. i thought recursion was not important. 


Sorry to say but these two points show how much you need to learn before you try to teach others.

---

### Post by openbuntu on 2012-04-10
> **Tony Flury said:**
> Sorry to say but these two points show how much you need to learn before you try to teach others.

I understand u hav huge exp, but i need to say 

*recursion need more stack slots , that is not feasible in micro controller in which the memory is in terms of bytes to few KBs...

* what I meant by that first statement is "whats is ur point?"...

---

### Post by Tony Flury on 2012-04-10
So if you are ruling out recursion because of the target platform/architecture - then make that very clear.

But still - my point remains, you still need to learn a lot more.

Seriously - please - don't waste your time on this.

---

### Post by openbuntu on 2012-04-10
> **Tony Flury said:**
> So if you are ruling out recursion because of the target platform/architecture - then make that very clear.

But still - my point remains, you still need to learn a lot more.

Seriously - please - don't waste your time on this.


Yeah I get that... I should learn things... but I cud do the review books thing...

---

### Post by Barrucadu on 2012-04-10
Firstly, there's no indication which "page" is first. I had to guess at the order.

This "book" is horribly presented. The positioning of blocks of text on the left and right of each image doesn't give any clear indication in which order they are supposed to be read.

C does not have call-by-reference. It does, however, have pointers which are completely different.

There's absolutely no mention of abstract data types at all.

---

### Post by xytron on 2012-04-10
Functions are a fundamental concept in C programming and in most computer languages and certainly in maths. 

The term "functional programming"  is used in an extremely broad sense, even so it has become associated with computer languages where (amongst other features) functions are side-effect free.  Meaning that their evaluation can't change the environment of computation.

You can program in C applying a functional style throughout. C has function pointers and the use of global variables can be minimized, there's even a book called [Functional C]("http://www.amazon.com/Functional-International-Computer-Science-Series/dp/0201419505/ref=sr_1_20?s=books&ie=UTF8&qid=1334099610&sr=1-20").

Still the functional languages represent a different style and philosophy of the process of programming and it could  be confusing to your readers if you don't qualify how you are referring to "functional programming" in C.

---

### Post by openbuntu on 2012-04-23
Guide is updated. made some changes to the pics... 
[Download it here]("http://yengal-marumugam.blogspot.com/2012/04/books-basics-of-programming.html")

---

### Post by PeterP24 on 2012-04-23
It is too much to convert the pictures into a single pdf or html file? Html file would be better - you can take advantage of those .gifs.  

The flow of reading is a little bit odd. You have two irregular columns, which in my opinion would be improved if they would have each equal widths. Also you should be consistent about the value main() returns: during your pictures it returns either an int or a void (hint - int). Also if you put the pictures into a single pdf file you may want to refrain yourself from putting the part which refers to your blog (the upper part in your picture) because it contains many nonfunctional elements: like what is the purpose of a search box and links to various parts of your website? They are just pixels in the final image - they don't serve any purpose because you can't use them to navigate or to search something on your website. My advice would be to put your work into a single html file and redesign the upper part so it wouldn't look like a screendump of your blog. A discrete link to your website would probably be enough publicity. 
I don't know much C - but I subscribe to what @Barrucadu said - you don't have true call by reference in C. I found this myself several months ago. You see, when you pass a pointer as a parameter to a function, the value (as in called by value) that is copied it is the pointed address - now you have the copy of that address inside the function passed by call by value. However, the copy of the address points to the same memory location as the pointer passed as a parameter to the function. 
If you change the values located in the memory pointed by the copy of the pointer inside the function you change the values pointed by the copy and the pointer passed as a parameter. If you would like to change the address (i.e. have a new location of the memory associated with the passed pointer) the copy points to, you wouldn't succeed - it would change only inside the function. The pointer passed to the function wouldn't change for the same reason a call by value does not change the parameter passed to a function. When the function ends that local copy of the pointer is unreachable (unless you return it). Hope I make some sense.

---

### Post by openbuntu on 2012-04-23
Thanls for ur time guys. I owe u much. and I was wrong to mention that C supports Functional Paradigm. But I'm just making it for Programming(particularly aimed at microcontrollers) and not Programming in C. and about the layout I' should consider them on next version. again thanx u very much

---

