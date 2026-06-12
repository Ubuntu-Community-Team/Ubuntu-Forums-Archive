---
title: "First python loop - syntax error"
date: 2009-03-04
forum: Programming Talk
---

### Post by blackcoffeeblue on 2009-03-04
Hi all,

Just starting out with python :) I have a syntax error on line 9 - can anyone tell me what I'm doing wrong? I thought a colon was necessary here to indicate a block of statements to follow?

```
#!/usr/local/bin/py3k
#filename: while.py

age = 15
asking = True

while asking:
        guess = int(input('Guess my age: ')
        if age > guess:
                print('I\'m older')
        elif age < guess:
                print('I\'m younger')
        else:
                print('That\'s right I\'m', age)
                asking = False
else:
        print('Loop over')
print('Program over')
```

```
[B]  File "while.py", line 9
    if age > guess:
                  ^
SyntaxError: invalid syntax[/B]
```

---

### Post by sujoy on 2009-03-04
```
guess = int(input('Guess my age: ')
```

you are missing the closing paren ... 

```
guess = int(input('Guess my age: '))
```

---

### Post by blackcoffeeblue on 2009-03-04
Doh well that was silly I should've spotted that :P Thank you sujoy

---

### Post by sujoy on 2009-03-04
you're welcome :)

---

