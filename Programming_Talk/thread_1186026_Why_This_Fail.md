---
title: "Why This Fail"
date: 2009-06-12
forum: Programming Talk
---

### Post by huangyingw on 2009-06-12
Hello, 
    In order to match out ```
"102-113/102-113" 
```from ```
"/media/storage/102-113/102-113.34.jpg"
```.
    I write such a regular expression:```
"\d{2,3}-(\d{2,3})(.*?)-(\1)"
```,
    In order to simplify it, I improve it to following one: ```
"(\d{2,3})-(\1)(.*?)-(\1)"
```. While it could not match out the thing I desire.
    The confusing thing for me is that the non-simplified one works, while, it does not work after simplifying. And I can't see there is any difference between this two version:(

---

### Post by CptPicard on 2009-06-12
Does the non-simplified one work? If it does, don't worry and just use the clearer one, because there is *exactly one* finite state automaton that matches what you want anyway.

---

### Post by huangyingw on 2009-06-13
> **CptPicard said:**
> Does the non-simplified one work? If it does, don't worry and just use the clearer one, because there is *exactly one* finite state automaton that matches what you want anyway.
Yes, the non-simplified one work, while, the simplified one does not work, that is my confusion.
(I have updated my origin post to stress my confusion:()

---

### Post by soltanis on 2009-06-13
"\d{2,3}-(\d{2,3})(.*?)-(\1)"
vs
"(\d{2,3})-(\1)(.*?)-(\1)"

The second pattern backreferences the second set of digits to the first. This would match a file such as this:

102-102/13958-102.13.jpg

But the first two digit groups have to be the same. \1 means, match whatever the first group was; and the first group matches 2-3 digits. That's why your pattern isn't working.

Use the first one; it works. Your simplified version is...oversimplified. It will not work for what you want it to do.

---

### Post by huangyingw on 2009-06-13
> **soltanis said:**
> "\d{2,3}-(\d{2,3})(.*?)-(\1)"
vs
"(\d{2,3})-(\1)(.*?)-(\1)"

Hi, thanks. So, my understanding of your meaning is:
the root cause is: "(\d{2,3})-(\1)" is not equal to "(\d{2,3})-(\d{2,3})", am I right?
After all, your answer encourage me to go ahead:)....

---

