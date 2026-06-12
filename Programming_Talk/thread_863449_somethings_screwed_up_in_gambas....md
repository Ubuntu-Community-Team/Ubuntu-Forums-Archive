---
title: "somethings screwed up in gambas..."
date: 2008-07-18
forum: Programming Talk
---

### Post by Existance0 on 2008-07-18
```
' Gambas class file
PUBLIC SUB Form_Open()
DIM number AS Integer
DIM solution AS Integer
solution = 0
number = 0
DO WHILE number < 1000
IF number MOD 3 == 0 OR number MOD 5 == 0 THEN
  solution += number
ENDIF
INC number
LOOP
label1.text = solution
END
```
should solve this problem just fine...
[http://projecteuler.net/index.php?section=problems&id=1](http://projecteuler.net/index.php?section=problems&id=1)

but it gives me 465336 which is almost double the answer anyone know whats going on?

---

### Post by LaRoza on 2008-07-18
I ran the same algorithm in another language and I get another answer. Probably is likely something with Gambas.

```

#!/usr/bin/python

solution = 0
number = 0
while number < 1000:
    if number % 3 == 0 or number % 5 == 0:
        solution += number
    number+=1
print solution

```

---

### Post by Existance0 on 2008-07-18
To bad I was looking forward to gambas :( what a letdown.

---

### Post by WW on 2008-07-18
It's been less than 20 minutes and you are ready to give up?  How about asking on the Gambas mailing list or forum (link [here](http://gambas.sourceforge.net/))?

---

### Post by Existance0 on 2008-07-18
Um there is nothing wrong with that code it should work fine...

---

### Post by WW on 2008-07-18
How long have you been using Gambas?

I've never used it, and I don't have it installed to try it, but I would try changing this
```

IF number MOD 3 == 0 OR number MOD 5 == 0 THEN

```
to this
```

IF (number MOD 3) == 0 OR IF (number MOD 5) == 0 THEN

```
(The **AND IF** and **OR IF** parts of the **IF** statement are an unusual aspect of Gambas. The parentheses are just to be sure that the logic is evaluated the way you expect it to.)

Of course, this might make no difference.  A Gambas expert could probably help, but they are more likely to be found in a Gambas forum than here.

---

### Post by Existance0 on 2008-07-18
That changed nothing... and that mailing list thing on their website is a joke...

---

### Post by ankursethi on 2008-07-18
Try IRC. Connect to #gambas on irc.freenode.net and chat with some Gambas devs. I'm sure they'll be glad to help.

---

### Post by Existance0 on 2008-07-18
I found the problem for some reason MOD isn't working and its adding all the numbers from 0 to 1000...

---

### Post by WW on 2008-07-18
After a little more poking around in the Gambas wiki, I have one more suggestion: Gambas uses a single **=** for testing equality, so change **==** to **=**.

---

### Post by Existance0 on 2008-07-18
0.o you sir are a god

---

