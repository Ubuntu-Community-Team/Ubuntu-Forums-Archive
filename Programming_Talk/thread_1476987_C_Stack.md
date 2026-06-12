---
title: "C Stack"
date: 2010-05-08
forum: Programming Talk
---

### Post by cap10Ibraim on 2010-05-08
[SIZE=4]I have this question [/SIZE]
[SIZE=2][COLOR=#008000][SIZE=2][COLOR=#008000][SIZE=3][COLOR=#000099] *Add to the "stack.c" an interface function  void multipop(int k) that pops k elements from *[/COLOR][/SIZE][SIZE=3][COLOR=#000099][I]the stack, or until the stack is empty

[/I][COLOR=Black]I can solve it but I changed the prototype to include the name of the stack? How is it possible to do it and stick to this prototype given ?![/COLOR]



[/COLOR][/SIZE][/COLOR][/SIZE][/COLOR][/SIZE]

---

### Post by tookyourtime on 2010-05-08
What's stack.c?

And doesn't pop normally return the value. So multi-pop should surely return multiple values? What your describing should be called something more like a delete.

Are you talking about THE stack or just any stack? If its just any stack and it's C then you will need to give it some sort of pointer to the data structure.

---

### Post by cap10Ibraim on 2010-05-08
> **tookyourtime said:**
> any stack and it's C then you will need to give it some sort of pointer to the data structure.
yes that's what I did but I should stick to the prototype given which is void multipop(int k)

---

### Post by dwhitney67 on 2010-05-08
The only way to adhere to the prototype you describe is to declare your stack object as a global variable, and frankly that would be silly.  After all, this would preclude an application from supporting multiple stacks.

The approach you have taken, of passing the pointer of a stack to the function, is the best solution (for C).

---

### Post by cap10Ibraim on 2010-05-08
Thanks for the support guys ):P

---

