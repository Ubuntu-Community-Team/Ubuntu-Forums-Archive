---
title: "[SOLVED] How to I find an array size?"
date: 2008-03-29
forum: Programming Talk
---

### Post by Zeotronic on 2008-03-29
C++: I need to find the size of an array... the only access I have to it is through a pointer. Is there any way to do this?

---

### Post by LaRoza on 2008-03-29
Find the size, and divide it by the size of an element.

I am not really familiar with C++, but I imagine a language that claims to be OO has an OO way of doing this. Perhaps with vectors?

---

### Post by Jessehk on 2008-03-29
Short answer: nope.

Longer answer: In these cases, usually the function will take an additional parameter: the size of the array. The better alternative (in C++) would be to use a standard container (like a std::vector) instead of the array.

---

### Post by CptPicard on 2008-03-29
No, unless you explicitly know that there is a certain value at the end of the array, such as \0 for strings. In general with C-style arrays you need to explicitly pass along the length.

However, in C++ you should be using vectors anyway instead of arrays, and those DO know their length.

---

### Post by LaRoza on 2008-03-29
> **Jessehk said:**
> Short answer: nope.

Reading the question again, I see that it is a pointer to an array.

In which case, you would need to know what terminates the array, then count it.

---

### Post by Zeotronic on 2008-03-29
> Longer answer: In these cases, usually the function will take an additional parameter: the size of the array. The better alternative (in C++) would be to use a standard container (like a std::vector) instead of the array.
Oh how often I use std::vector... however in this situation it is not option... I have, however, thought of a way that I can solve this problem, thank you for your input all of you.

---

