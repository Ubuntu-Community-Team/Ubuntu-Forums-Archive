---
title: "[Python] Operators within lists"
date: 2008-12-30
forum: Programming Talk
---

### Post by dodle on 2008-12-30
I have a list:[PHP]Cmem = ["10", "-", "5"][/PHP]How can I extract Cmem[1] and change it from a string to a literal operator?

I know that with numbers I can use either **int(Cmem[1])** or **float(Cmem[1])**.

Full Code:[PHP]# wxCalc v0.0.0.3 console

opers = ("+", "-", "*", "/")
Cmem = ["10", "-", "5"]

def eval_it(Cmem):
    for O in opers:
        if O in Cmem:
            m1 = Cmem.index(O)-1
            a1 = Cmem.index(O)+1
            val1 = Cmem[m1]
            val2 = Cmem[a1]
            answer = val1 O val2
            print answer

eval_it(Cmem)[/PHP]

---

### Post by Ahadiel on 2008-12-30
You could use eval(), ie:
[php]>> print eval("2+2")
4[/php]

---

### Post by Bachstelze on 2008-12-30
> **dodle said:**
> How can I extract Cmem[1] and change it from a string to a literal operator?


You can't. Operators like "+" and "-" are not objects in Python:

```
>>> type(4)
<type 'int'>
>>> type(+)
  File "<stdin>", line 1
    type(+)
          ^
SyntaxError: invalid syntax

```

You could indeed use [font="monospace"]eval()[/font], but that could be dangerous if the string are input by the user. A safer approach would be:

```
>>> l = ["1", "+", "1"]
>>> if l[1] == "+" : res = int(l[0])+int(l[2])
...
>>> res
2

```

That way, if [font="monospace"]l[1][/font] happens to be something else, no potentially harmful operation will be done by blindly [font="monospace"]eval()[/font]'ing it.

---

### Post by dodle on 2008-12-30
So I have to do a bunch of "if", "elif" statements?[PHP]if O == "+":
    answer = val1 + val2
elif O == "-":
    answer = val1 - val2
elif O == "*":
    answer = val1 * val2
elif O == "/":
    answer = val1 / val2[/PHP]
> **Ahadiel said:**
> You could use eval(), ie:
[php]>> print eval("2+2")
4[/php]

[PHP]# wxCalc v0.0.0.3 console

Cmem = ["10", "-", "5"]

          
def eval_it(Cmem):
    answer = eval("".join(Cmem))
    print answer

eval_it(Cmem)[/PHP]This feels like cheating.  But thanks, it does work.

---

### Post by Bachstelze on 2008-12-30
That's probably the safest approach, yes.

---

### Post by dodle on 2008-12-30
Does anybody think this ready for a gui?  I suck at OOP.[PHP]# wxCalc 0.0.0.3 console

opers = ('+', '-', '*', '/')
Cmem = []  # The calculator's temporary memory

def eval_it(Cmem):  # Get the result of the operation in temp memory
    if Cmem[1] == "+":
        answer = float(Cmem[0]) + float(Cmem[2])
    elif Cmem[1] == "-":
        answer = float(Cmem[0]) - float(Cmem[2])
    elif Cmem[1] == "*":
        answer = float(Cmem[0]) * float(Cmem[2])
    elif Cmem[1] == "/":
        answer = float(Cmem[0]) / float(Cmem[2])
    print "%s %s %s = %s" % (Cmem[0], Cmem[1], Cmem[2], answer)  # Show the result value
    Cmem = []  # Clear the calculator's temporary memory
    Cmem.append(str(answer))  # Add the resulting value to the temporary memory
    return Cmem

class MainProgram:
    def __init__(self, opers, Cmem):
        loop_calc = True
        while loop_calc:
            user_in = raw_input(": ")  # Takes integers and operators
            if user_in.lower() in ('quit', 'exit'):  # Quit the program
                loop_calc = False
            elif user_in.lower() in ('clear', 'clr'):  # clears the calculators temporary memory
                Cmem = []
            else:
                if len(Cmem) == 0:  # Verify that first slot in temp memory is available for an integer
                    try:
                        fuser_in = float(user_in)  # Verify that the user has entered a number
                        Cmem.append(user_in)  # Add that number to temp memory
                    except:
                        print "Use an integer"
                elif len(Cmem) == 1:  # Verify that second slot in temp memory is available for an operator
                    if user_in in opers:  # Verify that user entered an operator
                        Cmem.append(user_in)  # Add operator to temp memory
                    else:
                        print "Use an operator (+, -, *, or /)"
                else:  # If first two slots of temp memory are filled
                    if user_in in opers:
                        Cmem[1] = user_in
                    else:
                        try:
                            fuser_in = float(user_in)  # Verify that user entered an number
                            Cmem.append(user_in)  # Add number to temp memory
                            Cmem = eval_it(Cmem)  # Call function to evaluate operation contained in temp memory
                        except:
                            print "Use an integer"[/PHP]Probably not, eh?

---

### Post by nvteighen on 2008-12-30
That's just a procedural program with two different namespaces. That's not bad... and sometimes in Python it is needed, e.g. for modules importing; it just is overkill for your program, in my opinion.

OOP is about objects, which consist on **attributes and actions** that way that you play with different classes' instances interaction to get a final result... It has a great advantage: it allows to create models much easier to understand by emulating the real world... It has a huge disadvantage: it splits the implementation of some feature in several places and therefore making the interface of the involved objects implementation-dependent.

Your program just executes procedures, there are no objects interaction or anything related... And a GUI doesn't need your program to be OOP!

---

### Post by pmasiar on 2008-12-30
> **dodle said:**
> Probably not, eh?

This code is not object-oruented: it is object-obsessed. :-) You use OO paradigm because you can, not because you need it. Drinking too much Java recently? 

Read [Kingdom of Nouns](http://steve-yegge.blogspot.com/2006/03/execution-in-kingdom-of-nouns.html) and why OO is not a silver bullet.

---

### Post by Wybiral on 2008-12-30
You don't need the if's though, a dict of lambdas would make it easier to reuse your opmap:

```

ops = {'+': lambda x, y: x + y,
       '-': lambda x, y: x - y,
       '*': lambda x, y: x * y,
       '/': lambda x, y: x / y}

print ops['+'](10, 11)

```

This also gives you the keys to check if it's a valid op (which you're already doing with a tuple of them, not much extra work).

EDIT:

Also, to simplify this code, there's the operator module (no need to define the lambdas)

```

from operator import add, sub, mul, div

ops = {'+': add, '-': sub, '*': mul, '/': div}

print ops['+'](10, 11)

```

---

