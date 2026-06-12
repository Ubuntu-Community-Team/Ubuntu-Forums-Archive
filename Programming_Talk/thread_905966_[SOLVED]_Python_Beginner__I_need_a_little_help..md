---
title: "[SOLVED] Python Beginner:  I need a little help."
date: 2008-08-30
forum: Programming Talk
---

### Post by dodle on 2008-08-30
I've seen the answer to this somewhere before, but I can't find it now.  I want to delete some whitespace after a string (I think it would be called).  I know how to do a backspace using "\b", but can't figure out it's opposite.  I am new to programming altogether, and have chosen python to be the first language I learn.  If my problem is unclear, I will try to rephrase it.

---

### Post by LaRoza on 2008-08-30
> **dodle said:**
> I've seen the answer to this somewhere before, but I can't find it now.  I want to delete some whitespace after a string (I think it would be called).  I know how to do a backspace using "\b", but can't figure out it's opposite.  I am new to programming altogether, and have chosen python to be the first language I learn.  If my problem is unclear, I will try to rephrase it.

```

>>> name = " LaRoza "
>>> print name.strip()
LaRoza
>>> print name.rstrip()
 LaRoza
>>> print name.lstrip()
LaRoza 
>>> 

```

By default, the strip()'s will remove any whitespace, but you can specify characters as the argument.

---

### Post by slavik on 2008-08-30
I think you are looking for strip() ...

strip("some string   ") or "some string    ".strip()
or
x= "some string    "
print x.strip()

---

### Post by pmasiar on 2008-08-30
OP: You want to read up string methods.

Really, just read briefly through tutorial, to know what possibilities are. Not to remember everything, just to know the options. And become familiar with language reference - again, not to remember it all, just being able to wander around and find what you need.

---

### Post by slavik on 2008-08-30
> **pmasiar said:**
> OP: You want to read up string methods.

Really, just read briefly through tutorial, to know what possibilities are. Not to remember everything, just to know the options. And become familiar with language reference - again, not to remember it all, just being able to wander around and find what you need.
google helps, too :)

btw, at one time, I took a class, where the prof told us what to do for hw and only mentioned the functions to use (and not their exact names either), needless to say, I learned to love reading manpages :)

---

### Post by Wybiral on 2008-08-30
You can get a lot of help also from the interactive interpreter:

```

dir("")

```

This will list the methods you can use, then

```

help("".split)

```

Will give you a doc-string description explaining its purpose.

---

### Post by dodle on 2008-08-31
Here is a little piece of my code.  It's just something that I want to "print".
```
print 'I don\'t understand "', answer, '\b", try again.'
```If I type in something like "fhei" for the answer I get:```
I don't understand " fhei", try again.
```But what I want is:```
I don't understand "fhei", try again.
```I tried using .strip() like you showed me, but I still can't get rid of the space before the variable named answer.  When I get a minute I'll read up on string methods.

---

### Post by LaRoza on 2008-08-31
> **dodle said:**
> Here is a little piece of my code.  It's just something that I want to "print".
```
print 'I don\'t understand "', answer, '\b", try again.'
```If I type in something like "fhei" for the answer I get:```
I don't understand " fhei", try again.
```But what I want is:```
I don't understand "fhei", try again.
```I tried using .strip() like you showed me, but I still can't get rid of the space before the variable named answer.  When I get a minute I'll read up on string methods.

Give the rest of the code.

---

### Post by dodle on 2008-08-31
```
  answer = raw_input("Which direction would you like to go? \n:")
  if answer == "stats":
    print "Health: ", hp, "\n" "Right Hand: ", equip1, "\n", "Left Hand: ", equip2
  if answer == "inst":
    print instructions
  if answer == "n":
      y = y + 1
  if answer == "s":
      y = y - 1
  if answer == "e":
      x = x + 1
  if answer == "w":
      x = x - 1


  elif answer != "n" and answer != "s" and answer != "e" and answer != "w" and answer != "stats" and answer != "inst":
      print
      print 'I don\'t understand "', answer, '\b", try again.'
      
```Is that enough?

---

### Post by Wybiral on 2008-08-31
It's because the comma separated print statement adds the spaces for you. Use string formatting:

```

variable = 'spaces'
print 'this doesn't add the "%s" to the string' % (variable)

```

---

### Post by dodle on 2008-08-31
> **Wybiral said:**
> It's because the comma separated print statement adds the spaces for you. Use string formatting:

```

variable = 'spaces'
print 'this doesn't add the "%s" to the string' % (variable)

```

Thanks, this worked perfectly.  Someone in python-forum.org gave me the same solution.  I'll keep studying.

---

### Post by azurepancake on 2008-08-31
Hey, I'm a new guy too!

Although I'd much rather use the method stated above, but for the heck of it, if I understand what your trying to accomplish correctly, you could also use string concatenation. 

```

>>> answer = "this"
>>> 
>>> print 'I don\'t understand ' + '"' +  answer + '"' ' try again.'
I don't understand "this" try again.


```

Pretty messy looking, eh?

Best of luck to you and Python! :)

---

### Post by pmasiar on 2008-08-31
> **azurepancake said:**
> Pretty messing looking, eh?

Yup, you can use tripple-quoted string instead:
```

print """I don't understand "%s" try again.""" % answer

```

---

### Post by DaymItzJack on 2008-08-31
> **azurepancake said:**
> Hey, I'm a new guy too!

Although I'd much rather use the method stated above, but for the heck of it, if I understand what your trying to accomplish correctly, you could also use string concatenation. 

```

>>> answer = "this"
>>> 
>>> print 'I don\'t understand ' + '"' +  answer + '"' ' try again.'
I don't understand "this" try again.


```

Pretty messing looking, eh?

Best of luck to you and Python! :)

```
print 'I don\'t understand "' + answer '" try again.'
```
looks better.

---

### Post by azurepancake on 2008-08-31
Doh, good idea! Don't know why I didn't think of that.

---

### Post by Can+~ on 2008-08-31
Here's another method, you can pair it with a dictionary

[PHP]mydict = {"name":"James", "answer":"fhei"}

print "Hello %(name)s; I don't understand \"%(answer)s\", try again" % mydict[/PHP]

And you can use \" to escape the character, or alternate with """, " and ' like pmasiar.

---

### Post by nvteighen on 2008-08-31
> **Can+~ said:**
> Here's another method, you can pair it with a dictionary

[PHP]mydict = {"name":"James", "answer":"fhei"}

print "Hello %(name)s; I don't understand \"%(answer)s\", try again" % mydict[/PHP]

And you can use \" to escape the character, or alternate with """, " and ' like pmasiar.
Wow, nice trick. Thanks!

---

### Post by pmasiar on 2008-08-31
Come on guys, that's not tricks, just plain old RTFM! :-)

And you can use data literals instead of creating dummy variables:

```

print """Hello %(name)s; I don't understand "%(answer)s", 
    try again""" % dict(
        name="James", 
        answer="fhei", 
)
# or
print """Hello %(name)s; I don't understand "%(answer)s", 
    try again""" % {
             'name':"James", 
             'answer':"fhei",
}
```

---

### Post by dodle on 2008-08-31
All of you are waaaaaay too smart for me.  I don't know how I am ever going to catch up.

---

### Post by LaRoza on 2008-08-31
> **dodle said:**
> All of you are waaaaaay too smart for me.  I don't know how I am ever going to catch up.

With time and effort, like they did :-)

---

### Post by dodle on 2008-08-31
*deleted to move to a new thread*
[http://ubuntuforums.org/showthread.php?t=906823]("http://ubuntuforums.org/showthread.php?t=906823")

---

