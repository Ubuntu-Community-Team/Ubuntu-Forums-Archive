---
title: "Python3: How can I repeat part of a while statement until conditions are met?"
date: 2011-11-29
forum: Programming Talk
---

### Post by Thorin Oakenshield on 2011-11-29
Sorry for the awkward wording of the title. I couldn't think of a better way to word it.

Anyhow, is there a way to repeat a statement until certain conditions are met? Or something like "goto"?

---

### Post by Tony Flury on 2011-11-29
You already know about while statements - so you can simply put one while statement inside another (just make sure you get the indentation right).

A silly example : 
```

a = 0 
while a < 10:
    print(a)
    b = 0 
    while b < 10:
       print(b)
       b = b+1
    a = a+1
print "finished"

```

---

### Post by CoffeeRain on 2011-11-29
Are you thinking of an if?

```
while condition:
  if var==var1:
    print "var==var1"
```

---

### Post by Thorin Oakenshield on 2011-11-29
Sort of. I already have an if. I need that to repeat until the user gives specific input.

Tony Flury, that isn't quite what I need.

I have this bit ```

print("Your current total is ", a + b)
total = a + b
hit = input("hit? y or n")
while total < 21:
    if hit == 'y':
        c = random.randint(0, 12)
        print("your new total is ", a + b + c)
        break
    elif 21 == total:
        print("you win!")
        break
    elif 21 < total:
        print("you bust.")
        break
```
I need the first "if" statement to continue to present itsself until the user inputs "n".

---

### Post by CoffeeRain on 2011-11-29
Sorry if I'm bothering you by trying again, but here's what I interpret you wanting.

```
var=raw_input('What is your input? ')
while var != var1:
  var=raw_input('What is your input? ')
```

---

### Post by emiller12345 on 2011-11-29
You could try something like this, but it's not exactly a 'goto' statment...
```
import os,sys,random
random.seed(os.urandom(1))

print "stop when x <= 20"
while(1):
    x = random.randrange(1, 400, 1)
    if x > 20:
        sys.stdout.write("wrong,[x="+str(x)+"] ")
        continue
    #rest of while loop
    print
    print "Correct! x="+str(x)
    exit(0)
```

---

### Post by Thorin Oakenshield on 2011-11-29
I clarified what i wanted in my previous post.

Also I find no attempt to help annoying :)

---

### Post by CoffeeRain on 2011-11-29
Yes!! I believe this is what you want. I tested this, but I use 2.something, so you may have to change something, but it works for me. :)

```
import random

a=random.randint(0, 12)
b=random.randint(0, 12)

print("Your current total is ", a + b)
total = a + b
hit = raw_input("Hit? y or n: ")
while hit !='n':
  c = random.randint(0, 12)
  total=total+c

  if 21 == total:
      print("you win! You got a " + str(c) + "\n")
      break
  elif 21 < total:
      print("\nyou bust. You got a " + str(c) + "\n")
      break

  print("your new total is ", total)
  hit=raw_input("Hit? y or n: ")
```

---

### Post by Thorin Oakenshield on 2011-11-29
That is almost the same as my program. Same problem though. Once you input "y" you can't do it again.

---

### Post by simeon87 on 2011-11-29
```
hit = 'bla'
stop = False
while not stop:
    while hit != 'n':
        hit = input("hit? y or n")

        # do other things here
   # check if you want to stop permanently here
   # stop = True

```

---

### Post by Bodsda on 2011-11-30
2 minute write up in python 2.x

```

import random, sys
total = 0

input = ""
while True:
    input = raw_input("Hit? Y/N: ").lower()
    if input == 'n':
        break
    else:
        total += random.randrange(1, 13)
        print "Total: %s" % total
    
    if total > 21:
        print "BUST!\nGoodbye"
        sys.exit()

dtotal = random.randrange(15, 22)


if total >= dtotal: # quick bodge, assume dealer has between 15 and 21 and cant bust (player wins on draw)
    print "Winner!\nYou got: %s\nDealer got: %s" % (total, dtotal)
else:
    print "Loser!\nYou got: %s\nDealer got: %s" % (total, dtotal)

```

---

