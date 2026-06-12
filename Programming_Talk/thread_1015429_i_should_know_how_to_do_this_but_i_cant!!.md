---
title: "i should know how to do this but i cant?!?!"
date: 2008-12-18
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-12-18
in a simple python script i want to have it print waiting... with increasing amount of periods... so its like this (but condensed into one line) where the waiting writes over each other so just the periods move

waiting
waiting.
waiting..
waiting...

and a 1 second pause in between

my problem is i cant figure out the pause without going onto multiple lines...

or i have a blur with the periods when i just do something like

```

while True:
    print "waiting \r waiting. \r waiting.. \r waiting... \r"

``` 

so waht do i need?

---

### Post by ghostdog74 on 2008-12-18
put the word "waiting" before the loop. In the loop , print your dots, with the comma.
```

print "waiting"
while loop
  print ".",

```

---

### Post by jimi_hendrix on 2008-12-18
thank you

---

