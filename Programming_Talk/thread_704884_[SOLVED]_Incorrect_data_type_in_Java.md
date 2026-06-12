---
title: "[SOLVED] Incorrect data type in Java"
date: 2008-02-22
forum: Programming Talk
---

### Post by brennydoogles on 2008-02-22
I am new to java, and for one of my classes at school I have to write a Java class to create "Table" objects for a restaurant type setting. There are several constants, such as the tax rate and the prices of the meals, but when I try to compile, I am getting errors about the data type. In the instructions for the project, my professor said that we needed to return floats for several methods, but javac is throwing out these errors:
```
/home/brendon/Documents/csci 1250/workspace/Meals/src/Meals.java:36: possible loss of precision
found   : double
required: float
        private final float APPETIZER = 3.25;      // Declare and set APPETIZER constant
                                        ^
/home/brendon/Documents/csci 1250/workspace/Meals/src/Meals.java:37: possible loss of precision
found   : double
required: float
        private final float ENTREE = 10.75;        // Declare and set ENTREE constant
                                     ^
/home/brendon/Documents/csci 1250/workspace/Meals/src/Meals.java:38: possible loss of precision
found   : double
required: float
        private final float DESSERT = 4.50;        // Declare and set DESSERT constant
                                      ^
/home/brendon/Documents/csci 1250/workspace/Meals/src/Meals.java:39: possible loss of precision
found   : double
required: float
        private final float DRINK = 1.20;          // Declare and set DRINK constant
                                    ^
/home/brendon/Documents/csci 1250/workspace/Meals/src/Meals.java:40: possible loss of precision
found   : double
required: float
        private final float TAX = .09;             // Declare and set TAX constant
                                  ^
/home/brendon/Documents/csci 1250/workspace/Meals/src/Meals.java:41: possible loss of precision
found   : double
required: float
        private final float TIP = .15;             // Declare and set TIP constant
                                  ^
6 errors

```

Maybe I don't understand primitive data types as well as I thought I did, but I though the only difference was that doubles had 14 places of accuracy while float only had 7. Can anyone help me figure out what I am doing wrong??

---

### Post by DougB1958 on 2008-02-22
If I remember right, floating point literals (e.g., 3.25, 10.75, etc.) are implicitly double-precision to the Java compiler.

Try casting your literals to type float to explicitly tell the compiler that you want your values to have the lower precision, for example

```
private final float APPETIZER = (float)3.25;
```

---

### Post by ZylGadis on 2008-02-22
I'd just make them all doubles. Tell your professor that floats should not be used because of the rather large possibility for loss of precision. If you insist on floats, the above post is correct: you need to cast the literals.

---

### Post by ecimon on 2008-02-22
Another option is appending a 'f' letter at the end of each definition;
```

private final float APPETIZER = 3.25f; 

```

---

### Post by brennydoogles on 2008-02-22
> **ZylGadis said:**
> I'd just make them all doubles. Tell your professor that floats should not be used because of the rather large possibility for loss of precision. If you insist on floats, the above post is correct: you need to cast the literals.

LOL, the main conference room of the computer science department at my school is named after this professor... I don't think he would take well to having a first year Java student tell him how to do his job. If I had to guess though, I would say that he was trying to stump us with casting the literals. During our last assignment he set it up so that we would have to consume a trailing newline character after an integer input in order for a string input to work. Sneaky man.

By the way, the casting did work. I ended up using ecimon's method, because I remembered seeing that in some of the professor's code snippets in class, so I figured that would be my best bet. Thanks!!!

---

### Post by ZylGadis on 2008-02-22
On the contrary, such a figure most probably rose so high because of competence. Competent people are never adverse to hearing good arguments, regardless of the source. Your professor will probably appreciate your input :) 
Of course, there is also the possibility that he/she is a politician who knows how to bootlick and trample and the similar games insidious humans play to rise above their (typically low) ceiling. Fortunately, such people are rare among computer science academicians.

---

### Post by stevescripts on 2008-02-22
SWAG .... in the next week or so, your professor will most probably lecture on the
evils of using floats, and encourage you to use doubles ...

Steve ;)

---

### Post by brennydoogles on 2008-02-22
Note the newest comment in my code:

```

// NOTE: I kept getting errors about the possible loss of precision by using float type numbers, and thought maybe it would be a good idea
 // to get into the habit of using double type numbers in the future. What do you think??

```

---

