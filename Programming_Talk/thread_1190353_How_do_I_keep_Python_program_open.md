---
title: "How do I keep Python program open?"
date: 2009-06-17
forum: Programming Talk
---

### Post by swoll1980 on 2009-06-17
When I run a Python program outside of the interpreter, it runs through the program, and closes before I can read the output. How do I stop this. Thanks.

---

### Post by simeon87 on 2009-06-17
Does it print to the terminal? If so, you could open a terminal and then run the program from the terminal. It'll then display the output in the terminal, which doesn't close after the program is finished.

---

### Post by swoll1980 on 2009-06-17
> **simeon87 said:**
> Does it print to the terminal? If so, you could open a terminal and then run the program from the terminal. It'll then display the output in the terminal, which doesn't close after the program is finished.

Yeah it prints to the terminal. Thanks for the tip. Have a great day!

---

### Post by smartbei on 2009-06-18
Alternately, you could stick:
```

raw_input("This is here just so the program doesn't close on me!! :-)")

```
At the end, and it will make the program wait for your Enter until it closes.

---

### Post by swoll1980 on 2009-06-20
> **smartbei said:**
> Alternately, you could stick:
```

raw_input("This is here just so the program doesn't close on me!! :-)")

```
At the end, and it will make the program wait for your Enter until it closes.

Good Idea.

---

### Post by Eisenwinter on 2009-06-20
Keep a while loop going on "True".

while True:
    if condition: print data

---

### Post by pokerbirch on 2009-06-20
Ewwww, yuk! An infinite loop is NOT the way to solve this simple problem. As suggested above, run your script via the terminal. It's the correct way to do things.

---

