---
title: "Hello Web - simplest web app in python"
date: 2007-01-05
forum: Programming Talk
---

### Post by pmasiar on 2007-01-05
Someone complained that Python web app tutorials are harder than PHP. So I created these two simple python apps to help you started.

I assume you have cgi-enabled directory.

**UPDATE 1:** Find your python first. In terminal, type 'which python'.

Then change first line of following scripts according where your python is:  */usr/bin/python* or  */usr/local/bin/python* or whatever you have.
(end update1)


**Simplest one (3 lines)**: place it in CGI-enabled directory, make executable by web user (or anybody, or all):

```
#!/usr/bin/python
import cgi
cgi.test()
```

It will print your CGI environment variables and you can be sure all is OK. If not, error is in your web server settings. Also, make sure that apache can read/execute this script: ie. make ir readable/executable by all.

**More complicated (35 lines including 13 lines of HTML template)**, but still simple:

```
#!/usr/bin/python
import cgi
import cgitb; cgitb.enable()
import os

##---CONSTANTS -------
BGCOLOR = '#f0f0f0'

##---TEMPLATES ----------------------------------------------------
HTML = """content-type: text/html

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html><head><title>%(TITLE)s</title>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">
</head><body bgcolor="%(COLOR)s"><h1>%(TITLE)s</h1>
    <h2>Hello %(NAME)s</h2>
    <hr /><h2> Who are you?</h2>
    <form action="%(SCRIPT_NAME)s" method="POST" enctype="multipart/form-data">
        <input name="person_name" type="text" size="40"><br />
        <input name="submit" type="submit" value="Try">
    </form>
</body></html>"""

def main():
    FORM = cgi.FieldStorage()
    person = FORM.getfirst('person_name')
    if not person:
        person = '(Nobody yet)'
    next_script = os.environ['SCRIPT_NAME'] # name of this script: it submits to self

    print HTML % dict(TITLE='Hello Web!', NAME=person, 
        SCRIPT_NAME=next_script, COLOR=BGCOLOR)

# idiomatic start of the main() program
if __name__ == '__main__': main()
```

It will ask for name, and after hitting submit, prints it in the page and asks for more. If you have this running, you are on the way.

Good luck!

---

### Post by gummibaerchen on 2007-01-05
Ohh, noone should use CGI in the way you offered.
Maybe a quick start, but not a good one.

That's as lame as PHP + HTML.

A Python Web-Application should be written after WSGI norms.

[http://en.wikipedia.org/wiki/WSGI](http://en.wikipedia.org/wiki/WSGI)

Then their may be and interface for CGI if nothing better, as mod_python for example, is available.

Ok, WSGI looks harder than PHP + HTML, but in the end it's much better than pure CGI programming.

But considering, that you just want to be simple, you're damn right ;)
It's simple, but not nice.

I think you can do a lot better, but maybe for newcomers it's nice, as they want a quick result. But I wouldn't recommend this way.

---

### Post by pmasiar on 2007-01-05
> **gummibaerchen said:**
> Ohh, noone should use CGI in the way you offered.
...
But considering, that you just want to be simple, you're damn right ;)
It's simple, but not nice.

I think you can do a lot better, but maybe for newcomers it's nice, as they want a quick result. But I wouldn't recommend this way.

Agree with you 100%. We can do better - after learning basics.

My first goal was to test CGI is configuration, 3 line script is good enough, and if it does NOT work, your WSGI/mod_python goodness will not work either, it just will be LESS obvious what is wrong.

I am in process with one python beginner to sorting out why 1st example fails (she is on shared hosting) - some misconfigured CGI.

Second example was to show interactiive component without confusing beginner with templating system.  

My 3rd example was supposed to use simples templating (htmltmpl) with the same template and multi-line string in 2nd example but I run out of time :-)

---

### Post by gummibaerchen on 2007-01-07
Yeah, you're totally right.

Maybe you should extend your 2 Examples with an interactive one, that may interested more people.

For example [http://example.com/cgi-bin/sqrt.py/81](http://example.com/cgi-bin/sqrt.py/81)
And the output is

```
<h1>The Squareroot of 81 is 9</h1>
```

---

### Post by lazka on 2007-01-07
[http://webpython.codepoint.net/mod_python_publisher_hello_world](http://webpython.codepoint.net/mod_python_publisher_hello_world)

---

### Post by maddog39 on 2007-01-07
I finally got these two examples working, and here they are.

[http://www.dx-h.com/cgi-bin/cgitest.py](http://www.dx-h.com/cgi-bin/cgitest.py)   - Example 1
[http://www.dx-h.com/cgi-bin/cgitest2.py](http://www.dx-h.com/cgi-bin/cgitest2.py) - Example 2

---

### Post by gummibaerchen on 2007-01-08
> **maddog39 said:**
> I finally got these two examples working, and here they are.

[http://www.dx-h.com/cgi-bin/cgitest.py](http://www.dx-h.com/cgi-bin/cgitest.py)   - Example 1
[http://www.dx-h.com/cgi-bin/cgitest2.py](http://www.dx-h.com/cgi-bin/cgitest2.py) - Example 2

Example 1 isn't working for me

Would you pls also show the source? That may be interesting ;)

---

### Post by pmasiar on 2007-01-08
> **gummibaerchen said:**
> Example 1 isn't working for me

Would you pls also show the source? That may be interesting ;)

Both examples work for me as supposed. Good job! Source code is in #1 -  parent posting.

---

### Post by gummibaerchen on 2007-01-08
> **pmasiar said:**
> Both examples work for me as supposed. Good job! Source code is in #1 -  parent posting.
[http://www.dx-h.com/cgi-bin/cgitest.py](http://www.dx-h.com/cgi-bin/cgitest.py) - Example 1

That one gives me a long list of errors ;)

---

### Post by pmasiar on 2007-02-21
> **gummibaerchen said:**
>  Example 1....gives me a long list of errors ;)

They are not errors - cgi.test() is supposed to print all environment variables, and it does exactly that. How hard can be to understand program 3 lines long with just one library call? Sometimes even that is not easy :-)

---

### Post by gummibaerchen on 2007-02-21
> **pmasiar said:**
> They are not errors - cgi.test() is supposed to print all environment variables, and it does exactly that. How hard can be to understand program 3 lines long with just one library call? Sometimes even that is not easy :-)

Now it works... The List before was different :)

---

