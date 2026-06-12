---
title: "Python - No \n at the end of a print statement?"
date: 2007-03-01
forum: Programming Talk
---

### Post by ironfistchamp on 2007-03-01
Hey everyone

Just a quickie I hope. How can I stop Python from putting a \n at the end of a print statement. After looking at the documentation it appears that it won't put one if there is a comma at the end but that stops it from printing my string entirely.

Any ideas?

Thanks

Ironfistchamp

---

### Post by ghostdog74 on 2007-03-01
usually, the comma does the trick. You could post some example of what you want to achieve and the desired output.

---

### Post by ironfistchamp on 2007-03-01
Thanks for the reply. Basically I want to present a list of options number 1-n and then accept input. I have a function to get a keypress and try to turn the keypress into an int. That works fine. The problem is that I want it to say "What do you want? " and then give the prompt.

Doing this will print out the string and then have the flashing input block on a new line. 
```


#menu code here

print "What do you want? "
keypress.int_in()

```

Doing this will just give me the flashing input block and then indent the next printed line.

```


#menu code here

print "What do you want? ",
keypress.int_in()

```

What am I doing wrong?

Thanks

Ironfistchamp

---

### Post by ghostdog74 on 2007-03-01
i don't know how you did your keypress method, but usually when i want to ask for input, i just use raw_input(). raw_input writes to stdout without newline. you using curses?

---

### Post by pmasiar on 2007-03-01
> **ironfistchamp said:**
>  How can I stop Python from putting a \n at the end of a print statement. After looking at the documentation it appears that it won't put one if there is a comma at the end but that stops it from printing my string entirely.

You have some other issue. Comma at the end does the trick:

```

>>> print "this", ; print "that"
this that
>>> print "this" ; print "that"
this
that

```

Show us your code which does not work

---

### Post by pmasiar on 2007-03-01
> **ironfistchamp said:**
>  I want to present a list of options number 1-n and then accept input. I have a function to get a keypress and try to turn the keypress into an int. That works fine. The problem is that I want it to say "What do you want? " and then give the prompt.

why not use build-in function input() or raw_input for this? They have optional prompt parameter.

Or add prompt parameter to your int_in() custom function

---

