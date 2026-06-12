---
title: "I can't believe I have to ask this.."
date: 2008-05-28
forum: Programming Talk
---

### Post by blithen on 2008-05-28
But how do I represent the * in python?
Such as 
said = str(raw_input(""))
if said == *:
	print 'I like pie!'
* obviously means anything the person types in. and it will give that response also I need to know

said = str(raw_input(""))
if said == 'You like'+ * :
	print 'I like pie!'
meaning if the person typed in You like then anything after that it would output that response.

---

### Post by lapubell on 2008-05-28
i'm no expert, but i think all you have to do is

```
if said:
```

because that will return a true if it is set, false if not...

---

### Post by blithen on 2008-05-28
> **lapubell said:**
> i'm no expert, but i think all you have to do is

```
if said:
```

because that will return a true if it is set, false if not...

Hm..well that answers the first question thank you!

---

### Post by bobbocanfly on 2008-05-28
Not sure why you need this but this is how i would implement your script.

```

said = ""
while len(said) < 1: #Makes sure they type something in
    said = str(raw_input(""))
print "You said " + said

```

Edit: The second part looks like you want the user to type something starting with "I like", correct? You can use the startswith() function:

```

if said.startswith("I like"):
    print "WIN"

```

---

### Post by amingv on 2008-05-28
I don't understand why make a condition if you're going to evaluate against "everything"; might as well just do 'print said'.
For the second one you can do:
[PHP]if said.startswith('You like'):
    #do something[/PHP]

Also there's no need to do str(raw_input()); raw_input returns a string by default (even if you input numbers).
EDIT: Dang he beat me to it.

---

### Post by blithen on 2008-05-28
> **bobbocanfly said:**
> Not sure why you need this but this is how i would implement your script.

```

said = ""
while len(said) < 1: #Makes sure they type something in
    said = str(raw_input(""))
print "You said " + said

```

Edit: The second part looks like you want the user to type something starting with "I like", correct? You can use the startswith() function:

```

if said.startswith("I like"):
    print "WIN"

```
SWEET. I love you! Thanks man xD

---

### Post by Lau_of_DK on 2008-05-28
I recommend that you read: [this thread]("http://ubuntuforums.org/showthread.php?t=803185")

...start to finish, it covers questions similar to what you're asking.

/Lau

---

### Post by Can+~ on 2008-05-28
I also have a suggestion:
[http://docs.python.org/lib/re-syntax.html](http://docs.python.org/lib/re-syntax.html)

When the conventional methods (split, startswith, endswith..) just don't cut it.

---

### Post by blithen on 2008-05-28
One more question similar to the one I asked.

feel = str(raw_input('Hello, I am AIS. \nHow are you? '))
if feel == *'horrible'*:
    print 'that sucks'

how would I do that. I get .endswith() and .startswith()
but is there like a .hasin('weeee')??
EDIT: or what I use the 're' module?

---

### Post by Can+~ on 2008-05-28
[FONT="Courier New"]feel.find("horrible") != -1[/FONT]

[http://docs.python.org/lib/string-methods.html](http://docs.python.org/lib/string-methods.html)

With Regular expressions (which I don't master):

[PHP]import re

feel = "I feel horrible man."

if re.compile(".*?(horrible|terrible|awful).*?", re.I).match(feel, 1):
	print "Sorry dude."
else:
	print "uhm."[/PHP]

. being any character
* being 0 or more repetitions of the last character (in this case, any character)
? to avoid greedy.

I think .find is better in this one, regexp is better for other more complex tasks.

---

### Post by slavik on 2008-05-28
comming from a perl background, I would recommend that you look into regular expressions.

---

### Post by ghostdog74 on 2008-05-28
> **blithen said:**
> One more question similar to the one I asked.

feel = str(raw_input('Hello, I am AIS. \nHow are you? '))
if feel == *'horrible'*:
    print 'that sucks'

how would I do that. I get .endswith() and .startswith()
but is there like a .hasin('weeee')??
EDIT: or what I use the 're' module?

```

if "horibble" in feel:
  ...

```

---

### Post by Can+~ on 2008-05-29
> **ghostdog74 said:**
> ```

if "horibble" in feel:
  ...

```

Oh.. right. I forgot about that one.

Anyway, (to the OP), are you using multiple if's for each word? Like "if terrible" "if horrible" "if awful" ... ? That could be easier with regexps.

---

### Post by blithen on 2008-05-29
> **Can+~ said:**
> Oh.. right. I forgot about that one.

Anyway, (to the OP), are you using multiple if's for each word? Like "if terrible" "if horrible" "if awful" ... ? That could be easier with regexps.
o.O Really? How would I use that?

---

### Post by LaRoza on 2008-05-29
> **blithen said:**
> o.O Really? How would I use that?

[http://www.amk.ca/python/howto/regex/](http://www.amk.ca/python/howto/regex/)

---

### Post by ghostdog74 on 2008-05-29
> **Can+~ said:**
> Anyway, (to the OP), are you using multiple if's for each word? Like "if terrible" "if horrible" "if awful" ... ? That could be easier with regexps.

before going into regexps, it might be worthwhile to explore 
```

if ..... in ["horibble","awful","blah"]

```
or
```

for items in ["horrible","awful","blah"]:
 if items in word:
  .....

```

---

