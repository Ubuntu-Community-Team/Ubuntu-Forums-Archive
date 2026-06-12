---
title: "why are there multiple boolean types"
date: 2007-07-06
forum: Programming Talk
---

### Post by moshy on 2007-07-06
I think this is weird, but why is it I can have a bool type, but if i want to do an #include <gdk/gdk.h> all of a sudden everything changes to gboolean, and different libraries all have their own implementation. I mean, it's either true or false, how can it be anything different.

---

### Post by Mr. C. on 2007-07-06
A boolean is a two-valued true/false system, but that can be represented in many ways, such as  0 / 1, "yes" / "no", "true / "false", or 0 / non-zero.  These are all boolean, and each programmer / API is free to chose its implementation.

MrC

---

### Post by DavidBell on 2007-07-06
> **Mr. C. said:**
>  ... can be represented... 

Yeah you *can*, but why, or more to the point *why*, when you could just stick to the original intrinsic type? I've never seen the advantage myself, the only reason I can see is maybe full 32 bit integers execute faster than single bit booleans on pentium processors? (For eg "typedef int BOOL;" is ubiqitous in MS headers, also I believe this is the reason 24 bit colour is often represented as 32 bit with 8 wasted bits)

DB

---

### Post by jespdj on 2007-07-06
The boolean data type of C++ didn't exist in C. So a lot of people writing libraries invented their own boolean-like type for their library. We're still stuck with this...

---

### Post by Quikee on 2007-07-06
> **DavidBell said:**
> I've never seen the advantage myself, the only reason I can see is maybe full 32 bit integers execute faster than single bit booleans on pentium processors? 


You can not store (or process directly) "single-bit booleans" as the minimum is always 8 bit - 1 byte.  Because of this it doesn't matter if boolean is 8 or 32 bit wide as it will in always exist the question what represents "true" and what represents "false".

---

### Post by Mr. C. on 2007-07-06
Ever heard of bit fields ? [ editted ]

---

### Post by Quikee on 2007-07-06
> **Mr. C. said:**
> Ever heard of bit masks ?

Bit masks don't change anything - the minimum to store is still 1 byte and every operation is still on the whole byte and not "per bit" basis. What you did is only used (at least) a byte for storing of more boolean values - which is again nothing more or less as another solution to implement the "boolean" type. ;)

---

### Post by Mr. C. on 2007-07-06
Actually, I meant "bit fields".

That the first one uses a byte is irrelevant to this discussion, and is merely a performance-enhancing implementation detail.

You can store 8 booleans in a single byte using bit fields, and in fact this is done as a matter of routine (esp. at the OS / hardware layer).

MrC

---

### Post by Quikee on 2007-07-06
> **Mr. C. said:**
> Actually, I meant "bit fields".

That the first one uses a byte is irrelevant to this discussion, and is merely a performance-enhancing implementation detail.

You can store 8 booleans in a single byte using bit fields, and in fact this is done as a matter of routine (esp. at the OS / hardware layer).

MrC

I think you don't understand. 

The question was why we have so many boolean types.. the answer I gave was - because we can not store a boolean in only 1 bit as the minimum is 1 byte and because of this multiple boolean types can exists because you have to invent your own rule to which value "true" is and which value "false" is.

On the other hand if we could store and directly operate with just 1 bit this would be obvious and the optimum solution. There would be no reason to invent "yet another custom or standard boolean type". 

Bit fields (or bit masks or whatever.. I knew where you are pointing at) are just "yet another boolean type" with the advantage to pack more booleans together in one or multiple bytes. But If you have only one boolean you still can only pack it in a byte. To retrieve the value of the boolean you still have to perform an operation on the whole byte.

---

### Post by Mr. C. on 2007-07-06
I understand perfectly well, and explained in my original post that there are many types of booleans used; this is not a limitation of computer storage nor the typing limitations of computer languages, but rather various interpretations implementors have chosen to represent TRUE / FALSE values.  0 meaning FALSE and 1 meaning TRUE are not universal, and each implementor programs to either their own coding comfort level, or the existing standard defined by the code in question.

Programmers very often have an NIH attitude, and invent and implement what suits them at the time.  And often implementors choose to define their own types to avoid compatibility issues inherent in cross-platform code.

Again, *how* the data is stored in RAM is completely irrelevant to *why* there are many definitions of a boolean type.

MrC

---

### Post by Wybiral on 2007-07-06
They might use them somewhere different then just boolean. Maybe they are using the value in some boolean algorithm and they need true to be 255 for it to work properly.

Maybe you should ask them :)

I'm a C user so I just use an unsigned char as a bool.

But if your api requires it... There's not much you can do, just use their type, there may be a reason.

---

### Post by kknd on 2007-07-06
Strong typed languages like Java doesn't suffer from this =).

Its a pain to know when use 0, 1, NULL, true, false, etc in C++.... (for me.). Too many ways to do the same thing is confusing.

---

### Post by Mr. C. on 2007-07-06
A toleration for ambiguity helps keep you from getting lost on your way to the market.  Enjoy all the choices.

MrC

---

### Post by Wybiral on 2007-07-06
> **Mr. C. said:**
> A toleration for ambiguity helps keep you from getting lost on your way to the market.  Enjoy all the choices.

MrC

Yeah, you can't always pick and choose. I think it's a programmers responsibility to adapt to new interfaces and API's.


kknd, what if you're using someones api/library in Java and they happen to use their own implementation for one reason or another. These things happen in just about every language.

---

### Post by kknd on 2007-07-06
> **Wybiral said:**
> 
kknd, what if you're using someones api/library in Java and they happen to use their own implementation for one reason or another. These things happen in just about every language.

I like Standards, it helps to keep consistency and sanity :D.
Most of the Java libraries follow some pattern / standard, but as you said, there are always  some re-implementation of the basics.

There is a lot of it in C/C++, gtk, wxWidgets and all others have done it to try to make the code portable and etc (that remembers me managed code like C# and Java).

---

