---
title: "Pseudocode problems"
date: 2010-06-28
forum: Programming Talk
---

### Post by esmeco on 2010-06-28
I'm having some troubles regarding how to structure the pseudocode of a problem.
The problem asks me to make a function in C which adds a new person to a phonebook. The function receives a name,a telephone and two list pointers.

The main list is responsible for storing information about the various contacts: each node has one person's name and phone number.The list is alphabetically ordered. In order to make the access more efficient,there's a second list that allows access to the 1st person in the main list,whose name begins by a given letter. In the secondary list the nodes are also alphabetically ordered.  

I'm actually having problems with the pseudocode instead and not with the actual code, and I suspect those are the problems(bad pseudocode) that are leading me to have some repeated code throughout my C code.
Could someone give me out a hand on the pseudocode?

---

### Post by lisati on 2010-06-28
Is this homework? We don't mind offering suggestions if there's something specific you're stuck with.

---

### Post by Iowan on 2010-06-28
Describe *exactly* what the function should do (or list what you currently have for pseudocode). We can offer some pointers (pardon the pun).

---

### Post by wmcbrine on 2010-06-28
Why do you even need pseudocode? Is that a requirement of the assignment?

There's no standard for pseudocode (if there were, it wouldn't be "pseudo" anymore), so I'm not sure how it can be "bad". Do you just mean that you can't work out the logic? Because I have to tell you... working out the logic is the central skill in programming. Translating that into actual code is minor by comparison.

---

### Post by esmeco on 2010-06-28
Well,I think pseudocode could really help me with the program logic.
This is what I expect my function to be able to accomplish:


-Create a structure and add a given letter to the secondary linked list if the letter isn't already there. Add the name to the main linked list .
- If a letter is found check the main linked list for the name. If it's already there print something like "Name already in the list!". If it's not create a structure and add the name to the primary list. If that name is the smallest of a certain letter,put the pointer that accesses the secondary list(through a field in the structure), pointing to that name .

How can I translate this into pseudocode?

---

### Post by Can+~ on 2010-06-28
> **esmeco said:**
> Well,I think pseudocode could really help me with the program logic.
This is what I expect my function to be able to accomplish:


-Create a structure and add a given letter to the secondary linked list if the letter isn't already there. Add the name to the main linked list .
- If a letter is found check the main linked list for the name. If it's already there print something like "Name already in the list!". If it's not create a structure and add the name to the primary list. If that name is the smallest of a certain letter,put the pointer that accesses the secondary list(through a field in the structure), pointing to that name .

How can I translate this into pseudocode?

Again, there's no pseudocode standard, you can make any assumption, make anything you want, as long as you're consistent.

For instance, you could go like:

```
procedure check(x:contact, L1:list, L2:list):
    letter <- contact name first letter
    
    if letter is in L2:
        ...
```

Do some analytic over the same things you wrote above, recognize input and output, determinate the existance of a certain procedure which handles said I/O, determine what's essential to achieving the task.

---

### Post by nvteighen on 2010-06-29
Actually, is there something we could call pseudocode? One could write pseudocode in C for a Perl program (although viceversa would seem a bit more practical).

Anyway, in my opinion, yours is a design problem because of lack of abstraction. Whenever you see you're repeating code it's because you're failing to see a more abstract procedure or data structure that's underlying your logic.

Mantaining two lists that way doesn't seem too effective to me... IIRC, this sort of things is usually done by using some kind of hashing in order to reduce searching time.

---

### Post by Quikee on 2010-06-29
> **nvteighen said:**
> Actually, is there something we could call pseudocode? One could write pseudocode in C for a Perl program (although viceversa would seem a bit more practical).

Pseudocode is anything that is resembling code and makes sense to the programmer. For example you could write something like this (I just made this up):

```
my_house is a new instance of House.
loop over list_of_houses and for each element current_house do:
  if current_house address is '117'
    copy current_house to my_house

```

Pseudo code is useful when learning programming - because in pseudo code you are not restricted by the programming language but you can write down the algorithm in your understandable way. When you get the experience in more programming languages this is not useful anymore because you could just pick one dynamic language instead.

When learning it is also useful for teachers because they can see if the student is thinking in the "right" way.

---

