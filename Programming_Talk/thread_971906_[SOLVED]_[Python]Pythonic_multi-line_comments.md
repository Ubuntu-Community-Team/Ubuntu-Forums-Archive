---
title: "[SOLVED] [Python]Pythonic multi-line comments?"
date: 2008-11-05
forum: Programming Talk
---

### Post by fiddler616 on 2008-11-05
Hey,
I was opening my mouth to wonder:
How come in C* and Java, it's considered more readable to start each line of a multi-line comment with a *, and I haven't seen this in Python?

When I realized that I actually haven't seen a proper multi-line comment at all in Python--the only triple-quotes I've seen were for docstrings. For comments that span multiple lines, all I've seen is a bunch of hashes.

So is it considered non-Pythonic to have triple-quoted comments? If no, how does the Python community feel about having a * each line?

I know it's a small point, but.....I just can't stop wondering about it now that I've thought about it.

---

### Post by deuce868 on 2008-11-05
It's the convention. 

[http://www.python.org/dev/peps/pep-0008/](http://www.python.org/dev/peps/pep-0008/)

Check out the section headered "Comments"

---

### Post by cmat on 2008-11-05
I use the following form for multi-line comments

```

"""
    Hello, this is a comment about comments.
"""
```

---

### Post by ericesque on 2008-11-05
>   Block Comments

    Block comments generally apply to some (or all) code that follows them,
    and are indented to the same level as that code.  Each line of a block
    comment starts with a # and a single space (unless it is indented text
    inside the comment).

    Paragraphs inside a block comment are separated by a line containing a
    single #.


per the comments section of [http://www.python.org/dev/peps/pep-0008/](http://www.python.org/dev/peps/pep-0008/)


Sorry - Deuce beat me to it...

---

### Post by fiddler616 on 2008-11-05
Thanks, that solves it.

---

### Post by LaRoza on 2008-11-05
> **cmat said:**
> I use the following form for multi-line comments

```

"""
    Hello, this is a comment about comments.
"""
```

That is a string,  not a comment.

---

### Post by nvteighen on 2008-11-05
> **LaRoza said:**
> That is a string,  not a comment.
Which serves as a comment. :)

The problem is that triple-quotes are usually used for docstrings, which are a Python built-in feature... the idea is you can access the docstring of a certain object by using the doc() function. So, even there's nothing that prevents you to use triple-quote strings as regular multiline comments, it may lead to confusion.

---

### Post by crazyfuturamanoob on 2008-11-05
> **LaRoza said:**
> That is a string,  not a comment.

No! String is with only one quotes, like "string" and comment is with 3 quotes, for example: """comment"""

---

### Post by days_of_ruin on 2008-11-05
> **crazyfuturamanoob said:**
> No! String is with only one quotes, like "string" and comment is with 3 quotes, for example: """comment"""

```
>>>type("""abc""")
<type 'str'>
```

---

### Post by cmat on 2008-11-05
I've seen programs documented with the """ comment """ style. So I kind of followed suit because it works.

EDIT:

>>> """ hello """
' hello '

yeah today's not a good day for me :X

---

### Post by LaRoza on 2008-11-05
> **crazyfuturamanoob said:**
> No! String is with only one quotes, like "string" and comment is with 3 quotes, for example: """comment"""

No, ', ", ''', and """ are all strings.

Also, r"String" and u"String" are strings (raw and unicode).

""" and ''' are multiline.

---

