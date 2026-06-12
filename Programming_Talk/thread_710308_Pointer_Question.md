---
title: "Pointer Question"
date: 2008-02-28
forum: Programming Talk
---

### Post by NuNn DaDdY on 2008-02-28
Alrighty, say I have a pointer which is set to "hello", how would I go about appending this pointer with "/world" to have the pointer now be "hello/world".

---

### Post by LaRoza on 2008-02-28
> **NuNn DaDdY said:**
> Alrighty, say I have a pointer which is set to "hello", how would I go about appending this pointer with "/world" to have the pointer now be "hello/world".

How about some code?

"set to "hello""? Is hello a pointer variable or a string?

---

### Post by Wybiral on 2008-02-28
You don't, unless you copy the characters from "hello" into memory large enough to hold the rest (plus a null terminator).

---

### Post by k2t0f12d on 2008-02-28
A pointer cannot be literally assigned the value "hello".  A pointer is simply a integar whose value refers to a memory address.  The type of pointer indicates how many consecutive bytes are included in the pointer's reference. e.g. a char pointer points to 1 byte and int pointer points to 4 bytes (on a 32-bit machine).  Hence, the pointer can point to the memory address of the first character of an array of charaters that spell "hello".  Are you sure you are using a pointer and not a [FONT="Courier New"]char[][/FONT] array?

---

### Post by Wybiral on 2008-02-28
> **k2t0f12d said:**
> Are you sure you are using a pointer and not a [FONT="Courier New"]char[][/FONT] array?

They're probably pointing to the string literal (the "Hello" in the source code that gets embedded in the program). In which case they need to allocate some memory (be it stack or heap) and strcat or sprintf the two together. Assuming they're even programming in C, because if this is C++ they should be using the string class.

---

### Post by k2t0f12d on 2008-02-28
> **Wybiral said:**
> They're probably pointing to the string literal (the "Hello" in the source code that gets embedded in the program). In which case they need to allocate some memory (be it stack or heap) and strcat or sprintf the two together. Assuming they're even programming in C, because if this is C++ they should be using the string class.

++

---

### Post by Wybiral on 2008-02-28
> **Wybiral said:**
> Assuming they're even programming in C, because if this is C++ they should be using the string class.

And for all we know, they could be using some crazy language where pointers have a completely different meaning (I say this because they never told us what language they're using to begin with).

---

### Post by LaRoza on 2008-02-28
> **Wybiral said:**
> And for all we know, they could be using some crazy language where pointers have a completely different meaning (I say this because they never told us what language they're using to begin with).

Don't get into the meaning of "pointer" again, we have a thread for such discussions. :)

---

### Post by Wybiral on 2008-02-28
> **LaRoza said:**
> Don't get into the meaning of "pointer" again, we have a thread for such discussions. :)

lol, get your mind out of the gutter LaRoza...

---

### Post by LaRoza on 2008-02-28
> **Wybiral said:**
> lol, get your mind out of the gutter LaRoza...

Can't help it, it is attached to my body.

---

