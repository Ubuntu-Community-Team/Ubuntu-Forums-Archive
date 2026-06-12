---
title: "Python code error message- Newbie alert!"
date: 2006-03-19
forum: Programming Talk
---

### Post by lhtown on 2006-03-19
Ok, so I am working my way through the "How to think like a computer scientist" tutorial teaching myself Python as I go. I think it is an excellent tutorial and it makes a lot of sense to me. Python is my first programming language, and so far, I am enjoying learning it and working in it.

Here is my problem. I have written the following code and reviewed it a number of times, but it still returns the following error:

> Traceback (most recent call last):
  File "delete.py", line 54, in ?
    text=ptagstatement()
  File "delete.py", line 41, in ptagstatement
    while string.find(newtext, ptag, [searchstartposition])!=-1:
  File "/usr/lib/python2.4/string.py", line 361, in find
    return s.find(*args)
TypeError: slice indices must be integers or None

I am guessing that the answer is quite simple, but there must be something that I am either overlooking or just haven't learned yet.

Here is my code:
> import string
text="""<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
  <meta content="text/html; charset=ISO-8859-1"
 http-equiv="content-type" />
  <title></title>
</head>
<body>
<h2 id="head-3baadd3f6cf4468e604a717d19bca973c7e37ce4">Linux
for Human Beings</h2>
<p fluff ><strong>"Ubuntu" is an ancient African word, meaning
"humanity to
others". Ubuntu also means "I am what I am because of who we all are".
The Ubuntu Linux distribution brings the spirit of Ubuntu to the
software world.</strong> </p>
<p more fluff >Ubuntu
is a complete Linux-based operating system, freely available with both
community and professional support. It is developed by a large
community and we invite you to participate too!</p>
<p even more fluff >The Ubuntu
community is built on the ideas enshrined in the Ubuntu Philosophy:
that software should be available free of charge, that software tools
should be usable by people in their local language and despite any
disabilities, and that people should have the freedom to customise and
alter their software in whatever way they see fit.</p>
<p yet even more fluff >These freedoms
make Ubuntu fundamentally different from traditional proprietary
software: not only are the tools you need available free of charge, you
have the right to modify your software until it works the way you want
it to.</p>
</body>
</html>"""

print text
def ptagstatement():
    ptag="<p"
    ptagclose=">"
    newtext=text
    searchstartposition=1
    while string.find(newtext, ptag, [searchstartposition])!=-1:
        myptagstatement=string.find(newtext, ptag, [searchstartposition])
        ptagclose=string.find(newtext, ptag_close, [myptagstatement])
        print myptagstatement
        print ptagclose
        myptagstatement=myptagstatement+2
        print myptagstatement
        string1=newtext[:myptagstatement]
        string2=newtext[ptagclose:]
        searchstartposition=ptagclose+1
        newtext=string1+string2
    return newtext

text=ptagstatement()
print text

What I actually want the script to do is to strip the fluff out of the beginning <p fluff> tags. I am working on a site that was developed in Frontpage and maybe with some other junk and I want to strip the frivolous code out while leaving the bold, italics and a few other things.

Thanks for looking.

---

### Post by ow50 on 2006-03-20
You're using the deprecated string.find function. Don't! Remove the string import and then use
```
newtext.find(ptag, searchstartposition)
```

If your tutorial suggests to use the string module functions, then it's time to switch to a newer tutorial.

The brackets, i.e.  [],  in the manuals indicate optional arguments. Don't include the brackets! I did not review your whole code. Next time post your code in the code environment, not as a quote, because in Python indentation is relevant.

---

### Post by flummoxed on 2006-03-20
I wouldn't go so far as to say to switch to a newer tutorial. MOST of 'How to Think Like a Computer Scientist' is still relevant, it seemed to work for me. It's a lot more easy to understand than other tutorials as well.

---

### Post by lhtown on 2006-03-20
Thanks, guys for your help. I made the substitution recommended by ow50 and it now works.

I see the copyright for the "How to Think Like a Computer Scientist" tutorial is 2002 and that Python 2.1.3 was released April 8, 2002. It does indeed appear that it was written for the 1.6 or 2.0 series.

I guess I failed to read the following paragraph in the python help documentation for the string module:
> DESCRIPTION
    Warning: most of the code you see here isn't normally used nowadays.
    Beginning with Python 1.6, many of these functions are implemented as
    methods on the standard string object. They used to be implemented by
    a built-in module called strop, but strop is now obsolete itself.


Thanks for all of your help. You really brightened my day!

Here is my modified code that seems to be working just as intended:

```
text="""<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta content="text/html; charset=ISO-8859-1"
http-equiv="content-type" />
<title></title>
</head>
<body>
<h2 id="head-3baadd3f6cf4468e604a717d19bca973c7e37ce4">Linux
for Human Beings</h2>
<p fluff ><strong>"Ubuntu" is an ancient African word, meaning
"humanity to
others". Ubuntu also means "I am what I am because of who we all are".
The Ubuntu Linux distribution brings the spirit of Ubuntu to the
software world.</strong> </p>
<p more fluff >Ubuntu
is a complete Linux-based operating system, freely available with both
community and professional support. It is developed by a large
community and we invite you to participate too!</p>
<p even more fluff >The Ubuntu
community is built on the ideas enshrined in the Ubuntu Philosophy:
that software should be available free of charge, that software tools
should be usable by people in their local language and despite any
disabilities, and that people should have the freedom to customise and
alter their software in whatever way they see fit.</p>
<p yet even more fluff >These freedoms
make Ubuntu fundamentally different from traditional proprietary
software: not only are the tools you need available free of charge, you
have the right to modify your software until it works the way you want
it to.</p>
</body>
</html>"""
print text
#tags to be removed multiple times
#clean up paragraph tags
def ptagstatement():
    ptag="<p"
    ptagclosure=">"
    newtext=text
    searchstartposition=1
    while newtext.find(ptag, searchstartposition)!=-1:
        ptagposition=newtext.find(ptag, searchstartposition)
        ptagclose=newtext.find(ptagclosure, ptagposition)
        ptagstatement=ptagposition+2
        string1=newtext[:ptagstatement]
        string2=newtext[ptagclose:]
        searchstartposition=ptagclose+1
        newtext=string1+string2
    if newtext.find(ptag, searchstartposition)==-1:
        return newtext


print "this removes the fluff in the paragraph tag"
text=ptagstatement()
print text

```

---

