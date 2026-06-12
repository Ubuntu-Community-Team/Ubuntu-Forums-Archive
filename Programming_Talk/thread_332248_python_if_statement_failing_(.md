---
title: "python if statement failing :("
date: 2007-01-05
forum: Programming Talk
---

### Post by pedrotuga on 2007-01-05
Ok this is one of the things the C programmers should be asking all the time

Here is the problem:

```
for pair in pairs:
    has_stop_word = 0
    pair[1].decode
    try:
        flat_string=unescape(pair[1])
        low_string=flat_string.lower()
        for stop_word in stop_words:
            if stop_word in low_string:
                has_stop_word = 1
                break
        print has_stop_word
        if has_stop_word == 0:
            element = [pair[0],flat_string]
            fixed_list.apend(element)
                
    except:
        continue
```

the last if statemnt is never verifyed nor when has_stop_word=1 nor when it equals to zero.

I suspect is some variable type unmatching. I read somewhere that the *if var == number* syntax is not so pythoninc...

does anybody knows why is that if statement failing all the time?

---

### Post by Lord Illidan on 2007-01-05
> **pedrotuga said:**
> Ok this is one of the things the C programmers should be asking all the time

Here is the problem:

```
for pair in pairs:
    has_stop_word = 0
    pair[1].decode
    try:
        flat_string=unescape(pair[1])
        low_string=flat_string.lower()
        for stop_word in stop_words:
            if stop_word in low_string:
                has_stop_word = 1
                break
        print has_stop_word
        if has_stop_word == 0:
            element = [pair[0],flat_string]
            fixed_list.apend(element)
                
    except:
        continue
```the last if statemnt is never verifyed nor when has_stop_word=1 nor when it equals to zero.

I suspect is some variable type unmatching. I read somewhere that the *if var == number* syntax is not so pythoninc...

does anybody knows why is that if statement failing all the time?

the if statement is correct...is that the full program or an excerpt?

---

### Post by Mirrorball on 2007-01-05
If it's never verified, it must be because the loop is broken every time or an exception is thrown. No? Why don't you add an "else: print something" to that if and see what happens?

---

### Post by pmasiar on 2007-01-05
> **pedrotuga said:**
> I read somewhere that the *if var == number* syntax is not so pythoninc...

*if var == number*  is  pythonic enough :-) What is unpythonic is *if boolean_var == 0:* -- because it is same thing as *if boolean_var:* 

0 is false, non-zero is true. So you can use more easy to read *if has_stop_word:*

IMHO in your code you work way too hard for python programmer- codesmell that you write it in C over python. Do you need to create element with flat_string? Why not create a function returning 0/1? Instead of *has_stop_word* and *break* you can just *return 1* or *return 0* in proper place as my solution in [previous thread about this issue]("http://ubuntuforums.org/showthread.php?t=331589"). Or am I missing something?

---

### Post by pedrotuga on 2007-01-06
> **Mirrorball said:**
> If it's never verified, it must be because the loop is broken every time or an exception is thrown. No? Why don't you add an "else: print something" to that if and see what happens?

I did that... and i found out an exeption  was being thrown. It's the first time i use exeption handling and i am pretty new to python. It's pretty cool to have control over the program execution in error situations, but i learned that it's not so good idea to wrap big fragments of code within a *try:... excpet:* block. Basically if a syntax or other error ocur within one of those, it can get prety hard to find out where was it as the whole thing failed.

The problem was: i wrote *apend *instead of *append*. Because of the reason mentioned above i had trouble finding the error

> IMHO in your code you work way too hard for python programmer- codesmell that you write it in C over python. Do you need to create element with flat_string? Why not create a function returning 0/1? Instead of has_stop_word and break you can just return 1 or return 0 in proper place as my solution in previous thread about this issue. Or am I missing something?

You defenatly are right, i tryed a thousand diferente stuff to find the problem and in the end didnt went and clean up the mess. It's a lot of unecessary code.
This will be used with about 400 string against 7 or 8 stopwords, so, according on the other topic on this simple loop is prefered.
About wrapping the stopword match in a function... that's prety much the same, i would call it only once anyway.

---

### Post by Mirrorball on 2007-01-06
> **pedrotuga said:**
> i learned that it's not so good idea to wrap big fragments of code within a *try:... excpet:* block. Basically if a syntax or other error ocur within one of those, it can get prety hard to find out where was it as the whole thing failed.
Always catch a specific exception type, not all of them.

---

### Post by pedrotuga on 2007-01-06
That does not appear to be enough per se.
Whenever a big fragment of code is wraped in a try...exception block,  the error can e basically in all the code.
Anyway, thanks for the advice

---

