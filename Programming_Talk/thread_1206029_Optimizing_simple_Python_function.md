---
title: "Optimizing simple Python function"
date: 2009-07-06
forum: Programming Talk
---

### Post by Nevon on 2009-07-06
I just wrote a function to convert time from seconds to hours, minutes and seconds and then display them with the correct unit. So for example, if the user were to input 3615 seconds, the function should spit out "1 hour and 15 seconds". 3685 should generate "1 hour, 1 minute and 25 seconds", and so on.

My code seems to work just fine, however, it looks absolutely awful. There just has to be a better way to do this. Can anyone help?

```
def timeDisplay(seconds):
    """Function to easily switch time format depending on duration"""
    m, s = divmod(seconds, 60)
    h, m = divmod(m, 60)
    secondUnit = " second"
    minuteUnit = " minute"
    hourUnit = " hour"
    if s > 1:
        secondUnit += "s"
    if m > 1:
        minuteUnit += "s"
    if h > 1:
        hourUnit += "s"
    if seconds < 60:
        return str(s) + secondUnit
    elif seconds > 59 and seconds < 3600:
        returnstring = str(m) + minuteUnit
        if s != 0:
            returnstring += " and " + str(s) + secondUnit
        return returnstring
    else:
        returnstring = str(h) + hourUnit
        if m != 0 and s != 0:
            returnstring += ", " + str(m) + minuteUnit + " and " + str(s) + secondUnit
        elif m != 0 or s != 0:
            returnstring += " and "
            if m != 0 and s == 0:
                returnstring += str(m) + minuteUnit
            else:
                returnstring += str(s) + secondUnit
        return returnstring
```

---

### Post by Can+~ on 2009-07-06
Like, datetime.timedelta?

[PHP]>>> import datetime
>>> d = datetime.timedelta(seconds=3685)
>>> d
datetime.timedelta(0, 3685)
>>> print d
1:01:25[/PHP]

As for making the code "cleaner", there are many things that can be improved:

-Adding spaces between code blocks.
-Using other data structures to store your variables, for example: timestamp = {"h":[0, "hours"], "m":[0, "minutes"], "s":[0, "seconds"]}. (Just an idea)
-Having a different function that does the printing.

---

### Post by fr4nko on 2009-07-06
You don't need the datetime module, a little bit of math can helps:

```
def format_time(sec):
    s, m, h = sec % 60, sec/60 % 60, sec/3600
    return '%d hour, %d minutes, %d seconds' % (h, m, s)

print format_time(3685) # gives: 1 hour, 1 minutes, 25 seconds
```Francesco

---

### Post by Nevon on 2009-07-07
> **fr4nko said:**
> You don't need the datetime module, a little bit of math can helps:

```
def format_time(sec):
    s, m, h = sec % 60, sec/60 % 60, sec/3600
    return '%d hour, %d minutes, %d seconds' % (h, m, s)

print format_time(3685) # gives: 1 hour, 1 minutes, 25 seconds
```Francesco
That's what I was doing from the beginning, but I don't want to print out 0 of anything. I also don't want to print out the units incorrectly. For example, "2 hour, 1 minutes, 1 second". I need the units to be displayed correctly.

And to make things even more annoying, I want to substitute the last comma for "and" if there are three values to be printed. If only two values are supposed to be printed, I don't want any comma - just an "and". 

The part that does the number magic looks fine to me. What I need help with is that other part. The one with like 10 if-statements.

---

### Post by fr4nko on 2009-07-07
Ok, now you have a beatiful elegant code for your job :-)

```

def mconcat(base, sep, app):
    return (base + sep + app if base else app) if app else base
        
def spoken_concat(ls):
    txt, n = '', len(ls)
    for w in ls[0:n-1]:
        txt = mconcat(txt, ', ', w)
    return mconcat(txt, ' and ', ls[n-1])

def decline(name, nb):
    plural = ('s' if nb > 1 else '')
    return ('%d %s%s' % (nb, name, plural) if nb > 0 else '')

def format_time(sec):
    names = ['hour', 'minute', 'second']
    tvalues = sec/3600, sec/60 % 60, sec % 60
    ls = list(decline(name, n) for name, n in zip(names, tvalues))
    return spoken_concat(ls)

print format_time(3685) # print 1 hour, 1 minute and 25 seconds

```Francesco

---

### Post by ghostdog74 on 2009-07-07
the datetime module is there for you to use. No need to reinvent the wheel.

---

### Post by fr4nko on 2009-07-07
The point is that Nevon was asking to print the results in a spoken form and I don't know if datetime can output the results in this form.

He was also asking to have some idea because his code looks awful so it is also an exercise of programming style.

Francesco

---

### Post by Nevon on 2009-07-07
> **fr4nko said:**
> Ok, now you have a beatiful elegant code for your job :-)

```

def mconcat(base, sep, app):
    return (base + sep + app if base else app) if app else base
        
def spoken_concat(ls):
    txt, n = '', len(ls)
    for w in ls[0:n-1]:
        txt = mconcat(txt, ', ', w)
    return mconcat(txt, ' and ', ls[n-1])

def decline(name, nb):
    plural = ('s' if nb > 1 else '')
    return ('%d %s%s' % (nb, name, plural) if nb > 0 else '')

def format_time(sec):
    names = ['hour', 'minute', 'second']
    tvalues = sec/3600, sec/60 % 60, sec % 60
    ls = list(decline(name, n) for name, n in zip(names, tvalues))
    return spoken_concat(ls)

print format_time(3685) # print 1 hour, 1 minute and 25 seconds

```Francesco

Thank you. That looks a lot better than my mess. Now I'm trying to understand exactly what everything does. Some of the variable names are a little confusing, but I think I can figure it out.

EDIT: Actually, it doesn't quite work the way it's supposed to. For example, if you input the equivalent of 15 minutes (or any other number that is at least one minute, but less than one hour) in seconds, you get "0 hour, 15 minutes".

---

### Post by .Maleficus. on 2009-07-07
Why not use the datetime module, store the output in a variable and then format from there?  Hours/minutes/seconds are separated by a ":" so that would be extremely easy.

---

### Post by CrazyMonkeyFox on 2009-07-07
> **Nevon said:**
> 
EDIT: Actually, it doesn't quite work the way it's supposed to. For example, if you input the equivalent of 15 minutes (or any other number that is at least one minute, but less than one hour) in seconds, you get "0 hour, 15 minutes".


It's working perfectly for me, fulfills all the specifications you asked for.

---

### Post by Nevon on 2009-07-07
> **.Maleficus. said:**
> Why not use the datetime module, store the output in a variable and then format from there?  Hours/minutes/seconds are separated by a ":" so that would be extremely easy.

The hard part is not to get the seconds converted into minutes and hours. The hard part is formatting it into spoken English, along with correct punctuation and grammar.

EDIT: Think I might have solved it.

```
def mconcat(base, sep, app):
    return (base + sep + app if base else app) if app else base
        
def spokenConcat(ls):
    txt, n = '', len(ls)
    for w in ls[0:n-1]:
        txt = mconcat(txt, ', ', w)
    return mconcat(txt, ' and ', ls[n-1])

def decline(name, nb):
    plural = ('s' if nb > 1 and nb != 0 else '')
    return ('%d %s%s' % (nb, name, plural) if nb >= 1 else '')

def timeDisplay(sec):
    names = ['hour', 'minute', 'second']
    tvalues = sec/3600, sec/60 % 60, sec % 60
    ls = list(decline(name, n) for name, n in zip(names, tvalues))
    return spokenConcat(ls)
```

> **CrazyMonkeyFox said:**
> It's working perfectly for me, fulfills all the specifications you asked for.

Didn't for me. However, with some small changes (see above) it now is.

---

### Post by fr4nko on 2009-07-07
I don't understand, my original code seems to work perfectly, here the output that I obtain
> 
>>> format_time(120)
'2 minutes'
>>> format_time(15 * 60)
'15 minutes'
>>> format_time(60)
'1 minute'
the logic in my code is

[LIST]
[*]put the 's' to form the plural if nb > 1
[*]if nb > 0 output a descriptive string but otherwise, if nb == 0, output the empty string
[/LIST]
Anyway that's not important, it seems that the code is fine for you and you understood how it works :-)

Francesco

---

