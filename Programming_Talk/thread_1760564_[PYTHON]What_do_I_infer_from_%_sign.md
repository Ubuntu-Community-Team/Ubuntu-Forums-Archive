---
title: "[PYTHON]What do I infer from % sign?"
date: 2011-05-17
forum: Programming Talk
---

### Post by Ashish Gaurav on 2011-05-17
Hi. I am a newbie to Python and CGI. As a newcomer I admire its simplicity. But as common, I am having a problem. What do we mean by % sign? I know its MODULUS but in some places it cannot be modulus!

See this:
```
----------------------------------------------------------------------------------------------------
#!/usr/bin/python

# Import modules for CGI handling  import cgi, cgitb 
# Create instance of FieldStorage  form = cgi.FieldStorage() 
# Get data from fields
first_name = form.getvalue('first_name')
last_name  = form.getvalue('last_name')  print "Content-type:text/html\r\n\r\n"
print "<html>" print "<head>" print "<title>Hello - Second CGI Program</title>" print "</head>" print "<body>" print "<h2>Hello [SIZE=3]%s %s[/SIZE]</h2>" % (first_name, last_name) print "</body>" print "</html>"
------------------------------------------------------------------------

```
[FONT=Arial]Here, why was %s %s written after Hello, and why, was first_name,last_name written afterward with % sign.
Can't seem to understand!

Actually this was in the CGI script.
Please help!(No office work, just my zeal!)
Thanks(I hope I have explained my query well)[/FONT]
:)

---

### Post by Tony Flury on 2011-05-17
The %s is a string format code (rather like in sprintf in C)

[http://docs.python.org/library/stdtypes.html#string-formatting](http://docs.python.org/library/stdtypes.html#string-formatting)

---

### Post by StephenF on 2011-05-17
It has to do with a thing generally called operator overloading where a class can define what % does within the context of that class.

In Python % only does what it does because integer and float objects have % defined for them.

```

>>> int.__mod__
<slot wrapper '__mod__' of 'int' objects>

```
```

class A(object):
    def __mod__(self, other):
        print '''"It's just a flesh wound", said %s.''' % other

a = A()
a % "the black knight"

```
Prints: "It's just a flesh wound", said the black knight.

---

### Post by stchman on 2011-05-17
They are called format specifiers.  They are used in C and Java a lot.

---

### Post by Vox754 on 2011-05-17
> **StephenF said:**
> It has to do with a thing generally called operator overloading where a class can define what % does within the context of that class.

In Python % only does what it does because integer and float objects have % defined for them.

```

>>> int.__mod__
<slot wrapper '__mod__' of 'int' objects>

```
```

class A(object):
    def __mod__(self, other):
        print '''"It's just a flesh wound", said %s.''' % other

a = A()
a % "the black knight"

```
Prints: "It's just a flesh wound", said the black knight.

You do realise your explanation is too complicated for a beginner?

---

### Post by ve4cib on 2011-05-18
"%s" is just a placeholder for a variable you want to include in the string.  Read the link Tony posted.  It might help you out.


Dissecting your example a little bit...

```
"Hello %s %s" % (first_name, last_name)
```

We have two %s placeholders inside the string.  When the % operator is applied to the string, each placeholder is replaced with the string value of the items in the tuple; the first "%s" gets replaced with the value of first_name, and the second "%s" gets replaced with the value of last_name.

So if I wrote in a python script

```
first_name = "John"
last_name = "Doe"
grade = "A+"
course = "Intro Computer Science"
print "The student named %s %s got a %s in %s" % (first_name, last_name, grade, course)
```

you would see this printed out:

```
The student named John Doe got a A+ in Intro Computer Science
```

The order you list the variables is important.  Say I mixed up the order and instead had this in my python code:

```
print "The student named %s %s got a %s in %s" % (grade, course last_name, first_name)
```

you'd see:

```
The student named A+ Intro Computer Science got a Doe in John
```

which clearly does not make any sense at all.  (I imagine John is very uncomfortable having a female deer inside him....)


Slightly aside, but a similar technique for implanting variables into a string is by using the string's .format function:

```
print "The student named {0} {1} got a {2} in {3}".format(first_name, last_name, grade, course)
```

would give you:

```
The student named John Doe got a A+ in Intro Computer Science
```

It's the same idea as the %s placeholders, only you can specify the order you want the arguments in, and can use the same place-holder in multiple places.  Every instance of {0} will be replaced with the first argument, every instance of {1} will be replaced with the second argument, and so on.  I find it a little cleaner and more intuitive, but I'm sure other people would prefer using %.

---

### Post by simeon87 on 2011-05-18
> **ve4cib said:**
> I find it a little cleaner and more intuitive, but I'm sure other people would prefer using %.

This is actually the future of string formatting in Python, see [here](http://docs.python.org/release/3.0.1/whatsnew/3.0.html#changes-already-present-in-python-2-6) and [here](http://docs.python.org/release/3.0.1/whatsnew/2.6.html#pep-3101). The % operator will eventually be deprecated.

---

