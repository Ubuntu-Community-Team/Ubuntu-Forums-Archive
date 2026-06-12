---
title: "Python programming simplistic question"
date: 2009-03-05
forum: Programming Talk
---

### Post by s3a on 2009-03-05
What's the difference between implicit and explicit line joining? Can someone explain this to me in VERY easy to understand words please because I've not understood with multiple attempts.

Thanks in advance!

---

### Post by Can+~ on 2009-03-05
Well, there are situations where using multiple lines can be problematic, for example:

```
if a > b and
b > c and
c > d:
```

That won't work, the interpreter won't understand it, so to break into multiple lines, you should tell him to read multiple lines. If you don't get it, try to do it in the interactive prompt.

```
if a > b and \
b > c and \
c > d:
```

That's the explicit version, now, when you use (), [] or {}, the interpreter can deduct that:

```
dictionary = {
 "foo":"bar",
 "hello":"world"
}
```

Is a single block {"foo":"bar", "hello":"world} without the need to use \, that's implicit.

Edit:
I think your problem is more in the definition of "explicit" and "implicit", let's make a more simple example with math:

I give you the following arithmetic problem:

5 * 3 + 4 - 8 / 2 * 7 + 9 / 3

Now, you'll "implicitly" now that multiplication and division comes first, then adding and substracting. Then:

(5 * 3) + ((4 - 8 ) / 2) * (7 + 9 / 3)

I'm telling you how exactly I want it to be, that's "explicit".

---

### Post by WW on 2009-03-05
> **Can+~ said:**
> 

```
if a > b \
b > c \
c > d:
```


Acutally, that won't work either.  That's the same as
```

if a > b b > c c > d:

```
which is not valid syntax.  Did you mean to put some **and**s in there, or perhaps only one b and one c?

---

### Post by s3a on 2009-03-06
So, is the following true (trying to say it in my own words to see if I understand):

**[I]Implicit Line Joining:**
Objects relate but don't depend on each other. (The interpreter understands the individual statements)[/I]

**[I]Explicit Line Joining:**
Objects relate and depend on eachother so we need either (), [] or {} to make the statements work together because the interpreter will not understand the statements on their own.[/I]

Are these definitions true? (I made them up based on what I read)

---

### Post by wmcbrine on 2009-03-06
No.

If I may redo Can+~'s example:

Bogus:

```

if a > b and
   b > c and
   c > d:

```

Explicit:

```

if a > b and \
   b > c and \
   c > d:

```

Implicit:

```

if (a > b and
    b > c and
    c > d):

```

The symbol "\" means "take the next line and join it to this one". It's "explicit" because the symbol explicitly directs a join. An implicit join is just a continuation of a bracketed expression, which could be all on one line, or could be on several. Objects don't enter into the definitions at all.

Implicit is preferred.

Alternate explicit:

```

if \
   a > \
   b and \
   b > c and \
   c > d \
   :

```

See, the explicit join has no concept of the underlying syntax. It just makes everything into one virtual line. Of course, you could say pretty much the same about implicit:

Alternate implicit:

```

if (
   a >
   b and
   b > c and
   c > d
   ):

```

One reason to prefer implicit is what happens if you rewrap:

Gibberish:

```

if \ a > \ b and \ b > c and \ c > d \ :

```

Still good:

```

if ( a > b and b > c and c > d ):

```

Also good:

```

if ( a > b and b >
     c and c > d ):

```

So you can mangle the implicitly-wrapped expression a lot more without messing up the code.

---

### Post by Can+~ on 2009-03-06
> **WW said:**
> Acutally, that won't work either.  That's the same as
```

if a > b b > c c > d:

```
which is not valid syntax.  Did you mean to put some **and**s in there, or perhaps only one b and one c?

Yes, I forgot the ands.

---

### Post by s3a on 2009-03-06
So,
[I]
**explicit line joining:** when you use "\" to combine several lines.
**implicit line joining:** when you just continue typing lines normally[/I]

Is the above correct? If so, would the following hypothetical example I made also be correct:

*Explicit:*

if True:
   print "We're not done yet!"

*Implicit:*

if True:
   print 'We\'re not done yet!'

(I don't know why the indentation before the print is not showing but I put indentation)

---

### Post by wmcbrine on 2009-03-06
> **s3a said:**
> **implicit line joining:** when you just continue typing lines normallyOnly if you're within a bracketed expression.

> *(I don't know why the indentation before the print is not showing but I put indentation)*You need to use the [ code ] tags (without the spaces) to preserve indentation.

I'm not sure what you're getting at with your new examples, since they don't involve any line joining at all.

---

### Post by s3a on 2009-03-06
What I am trying to say is, it could be (or something like that, correct me if I'm wrong please):

```
if True:
   print 'We\
're not done yet!
```

couldn't it?

(I still don't see the indentation even with the quotes tag)

---

### Post by WW on 2009-03-06
> **s3a said:**
> 

(I still don't see the indentation even with the quotes tag)
Use the **code** tag, not the **quote** tag.

---

### Post by imdano on 2009-03-06
> **s3a said:**
> So,
[I]
**explicit line joining:** when you use "\" to combine several lines.
**implicit line joining:** when you just continue typing lines normally[/I]

Is the above correct? If so, would the following hypothetical example I made also be correct:

*Explicit:*

```
if True:
   print "We're not done yet!"
```

*Implicit:*

```
if True:
   print 'We\'re not done yet!'
```
All you're doing in this example is escaping the apostrophe in "We're" so you don't get a syntax error.  Escaping is another common use for the backslash character, but in this case it has nothing to do with line joining.

edit: You can actually think of line joining with a backslash as a special case of escaping.  You're basically escaping a line break, so that Python doesn't interpret the break as the start of a new expression.

---

### Post by s3a on 2009-03-06
> **wmcbrine said:**
> Only if you're within a bracketed expression.

You need to use the [ code ] tags (without the spaces) to preserve indentation.

I'm not sure what you're getting at with your new examples, since they don't involve any line joining at all.

In the following definitions that I made:

explicit line joining: when you use "\" to combine several lines.
implicit line joining: when you just continue typing lines normally

I got the definition for explicit line joining right? As for implicit line joining, you said I was right only on braketed expressions? Can you elaborate my definition of implicit line joining for me then please?

---

### Post by imdano on 2009-03-06
Have you read this?: [http://docs.python.org/reference/lexical_analysis.html#explicit-line-joining](http://docs.python.org/reference/lexical_analysis.html#explicit-line-joining)

---

### Post by s3a on 2009-03-06
> **imdano said:**
> Have you read this?: [http://docs.python.org/reference/lexical_analysis.html#explicit-line-joining](http://docs.python.org/reference/lexical_analysis.html#explicit-line-joining)

I read it very slowly and I think I understand. I will again reiterate it hopefully this time it'll be right. Sorry for being stupid and wasting a lot of time :(.

*_**My Definitions:**_*

***Implicit Line Joining:***
You can have a lot of statements on different physical lines and the chunk of statements will all be combined by the single (), [] or {}.

***Explicit Line Joining:***
Instead of using (), [] or {} to combine a lot of different statements on different physical lines, \ is used instead.

Are those definitions right?

---

### Post by imdano on 2009-03-06
That mostly seems right, though I wouldn't use the word "statements" to describe what's getting joined.  I'd describe them like this:

Implicit: Multiple physical lines are wrapped in (), [], or {} (depending on the context) to join them into one logical line.

Explicit: Multiple physical lines are ended with a '\' to join them into one logical line.

Just to be clear, a "logical line" is what the Python interpreter treats as a single line, and a "physical line" is a line as you see it in your text editor.

---

### Post by s3a on 2009-03-06
Are you sure "statements" is not the right word to use? If it isn't, is there a 'logical' word because 'physical lines' are lines interpreted by humans and not by python.

Edit: Sorry I think my last comment was a stupidity. So, in my own definition, I just need to change "statements" to "physical lines" and then my definitions are right?

Edit #2: Your definitions are nice actually. Thanks!

---

### Post by wmcbrine on 2009-03-07
"Statements" is definitely not the right word. The whole thing, the whole joined line, comprises a single statement. Also, again, the various brackets -- '(', '{', '[' -- can't just join *anything*; they have to surround an expression, or a sequence, or a dict, as appropriate. So, I'd agree with imdano on the definition of explicit joining, but not quite on implicit. In an implicit join, the purpose of the brackets is not to join lines, but to enclose the expression; the fact that the expression can span multiple lines is just a side effect.

---

### Post by s3a on 2009-03-07
> **wmcbrine said:**
> "Statements" is definitely not the right word. The whole thing, the whole joined line, comprises a single statement. Also, again, the various brackets -- '(', '{', '[' -- can't just join *anything*; they have to surround an expression, or a sequence, or a dict, as appropriate. So, I'd agree with imdano on the definition of explicit joining, but not quite on implicit. In an implicit join, the purpose of the brackets is not to join lines, but to enclose the expression; the fact that the expression can span multiple lines is just a side effect.

What's the difference between "joining lines" and "enclosing an expression?"

---

### Post by imdano on 2009-03-07
Sometimes the purpose of parenthesis is just to join lines.
```
if (True and
     1 > 0):
    print ("This is a really long string that" +
           " I am putting on two lines.")
```Is not serving a different purpose than
```
if True and \
   1 > 0:
    print "This is a really long string that" \
          " I am putting on two lines.
```

I do understand your point, though.  When using '()' to define a tuple or make a function call, the primary purpose clearly isn't joining lines.

---

