---
title: "Python: Syntax Error in if statement"
date: 2010-03-28
forum: Programming Talk
---

### Post by imaginaryfruit on 2010-03-28
Hello,

I'm trying to run the following code

```

def inv(p):
    inverses = []
    for a in range(p - 1):
        inverses.append(0)
        for b in range (p - 1):
            c = (((b+1)*(a+1)) % p
            if c == 1:
                inverses[a] = b
                break
    return inverses

print inv(5)

```and I'm getting

```
    
if c == 1 :
          ^
SyntaxError: invalid syntax

```Can anyone explain why? I'm new to Python and don't see the difference between my if statement and the examples I've seen online.

Thanks!

---

### Post by MadCow108 on 2010-03-28
there is a closing parentheses missing in the line above the if

these kind of errors usually give error messages on wrong lines, so always check for this when you can't see anything wrong on the line the compiler/interpreter indicates

---

### Post by imaginaryfruit on 2010-03-28
Ahh -- of course! Thanks very much!

---

