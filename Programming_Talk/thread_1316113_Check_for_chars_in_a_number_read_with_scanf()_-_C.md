---
title: "Check for chars in a number read with scanf() - C"
date: 2009-11-05
forum: Programming Talk
---

### Post by amrlima on 2009-11-05
Hi all,

As an exercise of learning C I need do check if a number (positive integer with type int) as, somewhere, a char: 132t2. 

The goal is to raise an error of course and prompt the user for to type a new number.

I cannot use str, or functions like isDgit() or isAlpha. This has to be made with basic C operators and/or pointers.

I know that the solution may lie in ASCII tables but I still didn't get the hang of it.
Anyone has any clue? 

Thanks!

---

### Post by samjh on 2009-11-05
Cast the char to an int, then check whether the int value is between 0x31 to 0x39 (ASCII code for 1 to 9 in base-16).

When you cast a char to an int, you do: **int asciival = (int)somechar;**
That will convert somechar to its ASCII code value and assign it to asciival.  Then it's a simple matter of checking whether the value in asciival corresponds to an integer character.

---

### Post by dwhitney67 on 2009-11-05
> **amrlima said:**
> Hi all,

As an exercise of learning C...

I cannot use str, or functions like isDgit() or isAlpha. This has to be made with basic C operators and/or pointers.

...

Posting homework questions is against the forum rules!

---

### Post by amrlima on 2009-11-05
I did not ask anyone to solve my problem, just to give a hint. And who said it's homework? I can be learning by myself.  I did not know that rule.

Thanks samjh!

---

### Post by amrlima on 2009-11-05
> **amrlima said:**
> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums should not be thought of as a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.

Ah, here it is. Well, I think my question was something more like a hint. What I am trying to do is much more then what I asked for. I just needed a little help cause I was stuck :).

---

### Post by dwhitney67 on 2009-11-05
> **amrlima said:**
> Ah, here it is. Well, I think my question was something more like a hint. What I am trying to do is much more then what I asked for. I just needed a little help cause I was stuck :).

You can use scanf() to determine if the input is valid or not.  You do not need to utilize the ASCII table, much less pointers.

Here's some hints of what is a valid input (number), and what is not:
```

123\n     -- valid
abc123\n  -- not valid
123abc\n  -- not valid

```
For a valid input, there are two "entities" on the input stream: the number and a newline character.  After the use of scanf(), verify that the second entity is a newline and that scanf() has indeed returned a value of 2.

---

### Post by amrlima on 2009-11-05
Thanks dwhitney67! I will investigate your tip then. I appreciate your understanding :).

---

