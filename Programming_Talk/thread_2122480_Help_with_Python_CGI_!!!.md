---
title: "Help with Python CGI !!!"
date: 2013-03-05
forum: Programming Talk
---

### Post by vikkyhacks on 2013-03-05
I have been doing python CGI programming (moved from php) for a while, Whenever there is a small glitch in my program the entire program stops running and displays only a ```
500 Internal Server Error
```. 

[B]Is there any way to clearly make the CGI tell on what line the error is ??? 
NOTE: I TRIED cgitb.enable()

[/B]```
#!/usr/bin/python


import cgitb


cgitb.enable(display=0)
print "Content-Type: text/html\n"
print "<h1>Server ON</h1>"
print """
<form action="index.py" method="post">
        <input type="text" name="user">
        <input type="password" name="pass">
        <input type="submit">
</form>
""

```The above code was the code I was working with, By just removing the small " from the last print statement the whole program crashes !!!

---

### Post by greenpeace on 2013-03-05
Hi!

Well... without the third " it's not actually valid python (3 x " to open requires 3 x " to close), and so fails to compile!   :)

Also, consider the quotes you're using.  As you have double-quotes inside the quotes it could confuse things.  Try wrapping these things in single-quotes.  There's more information in the first answer here: [http://stackoverflow.com/questions/56011/single-quotes-vs-double-quotes-in-python](http://stackoverflow.com/questions/56011/single-quotes-vs-double-quotes-in-python)

Is it at least now showing the debug as you expect with the cgitb module?

Cheers,
Gp

---

### Post by vikkyhacks on 2013-03-05
Well actually I know that there is one " missing, but my question **Why is the cgi debug stuff not picking tat up ???**

---

### Post by diesch on 2013-03-05
As there is a syntax error Python can't compile your program. None of your code is ever executed.

---

### Post by vikkyhacks on 2013-03-06
then what does cgitb.enable() does ?? What kinda error does it handle, can you be a bit more clear on the type of errors that cgitb.enable() will handle !!!

---

### Post by diesch on 2013-03-06
It handles runtime exceptions, that is errors that occur after your CGI program has started.

Try for example to add
```
print 1/0
```
to your program.

---

### Post by spjackson on 2013-03-06
> **vikkyhacks said:**
> then what does cgitb.enable() does ?? What kinda error does it handle, can you be a bit more clear on the type of errors that cgitb.enable() will handle !!!
cgitb is for providing more information than the default when an exception is thrown at run time. I think [http://pymotw.com/2/cgitb/index.html](http://pymotw.com/2/cgitb/index.html) provides a good explanation.

In php-land I'd expect by default the basic details (and line number) of a syntax error to appear in /var/log/apache2/error.log (or wherever else your Apache error log is configured). I don't know for sure if it's the same with python, but it wouldn't surprise me. Have you looked?

When I first did CGI programming with Perl, I would test first from the command line before trying it through the browser. I found that much more productive for picking up typos and silly syntax errors than going straight to the browser to test.

---

