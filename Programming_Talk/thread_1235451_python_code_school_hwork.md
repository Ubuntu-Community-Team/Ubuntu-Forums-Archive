---
title: "python code school hwork"
date: 2009-08-09
forum: Programming Talk
---

### Post by leedrew on 2009-08-09
[SIZE=4]Hi [/SIZE]
[SIZE=4]I tried to write a for __ range code that a user could type in a number but it will not work. and also when I had put in range (0, number) it said that I couldn't use 0 why is that ??[/SIZE]

---

### Post by ad_267 on 2009-08-09
This code works fine for me:
```
for i in range(0,5):
    print i
```
If you post an example of the code that doesn't work inside [[COLOR="Black"]CODE[/COLOR]] tags then we can be of more help.

Also, there's no need to post in large bold text. If we can't see well we can increase the font size ourselves.

---

### Post by Tmatherne on 2009-08-09
If you are wanting to be able to do print a range for a user defined end range, this may help.  Note, syntax will change a bit if you are using Python 3:


```

number = int(raw_input ('Enter a number:')
for i in range (0,number):
    print i
else:
    print 'loop over'

```
HTH
Tommie

P.S. Wow, first post and I am trying to help someone instead of asking a question.  This is a new feeling for me.

---

### Post by myle on 2009-08-09
FWIW in python 3:

```

number = int(input('Enter a number:'))
for i in range(0, number):
    print(i)
print('loop is over')

```

---

### Post by leedrew on 2009-08-09
**sorry about the big type I can't see so well so I use bigger font thanks for all the suggestions will try them. **

---

### Post by leedrew on 2009-08-09
Another quick Question about the raw input isn't that just for string variables? 
and the input is for int or real variables?

---

### Post by Joeb454 on 2009-08-09
Thread Closed.

While we are happy to help, homework help isn't permitted in the Code of Conduct.

---

