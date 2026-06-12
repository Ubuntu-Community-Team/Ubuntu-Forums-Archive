---
title: "[SOLVED] [Python]Do I need Django for simple web script?"
date: 2008-11-24
forum: Programming Talk
---

### Post by fiddler616 on 2008-11-24
Hello,
I need to make a website that will accept a few bits of data from the user, query a few websites, calculate, and display a result.
I was getting ready to look into Django, which seems rather complicated, when it occurred to me that it might be possible to just use standard Python with urlllib, and not mess with Django.
A)Back me up--it's allowed to just have straight Python online--I feel like I've seen examples.
B)Am I right in thinking all I need is urllib, HTML and CSS, no Django?

Thanks.

---

### Post by themusicwave on 2008-11-24
You can certainly do form processing without Django.  Keep in mind, Django, or any other framework, is simply a wrapper around Python.  Everything Django does is done from ordinary Python code.  They just make it simpler.

Check out this tutorial.  What you are looking for is Python CGI.

[http://www.cs.virginia.edu/~lab2q/lesson_1/]("http://www.cs.virginia.edu/~lab2q/lesson_1/")

---

### Post by snova on 2008-11-24
CGI?

Then there's mod_python, which is faster (among other advantages), but only works with Apache.

I don't know how useful urllib is. I think it's for accessing websites, not building them.

---

### Post by glok_twen on 2008-11-24
the apress book on "beginning python - novice to professional" has 2-3 quick chapters on creating some simple forms.

---

### Post by fiddler616 on 2008-11-24
> **snova said:**
> CGI?

Then there's mod_python, which is faster (among other advantages), but only works with Apache.

I don't know how useful urllib is. I think it's for accessing websites, not building them.
Well the plan is:
[PHP]
<insert CSS template>
<insert CSS styling>
<Python>
user_input = text_box("input")
import urllib
open("useful site")
<regexp useful data>
<do some math>
if user_input not ""
    goto results.html #er, I mean results.py(?)
</Python>
</HTML>
[/PHP]
in pseudocode.
It's not very complex--which is why I'm leaning away form Django. I just need to find out how to make stuff like text boxes.

@themusicwave thanks for the link

---

### Post by snova on 2008-11-24
If you want to use Python in a manner similar to PHP, then mod_python will do it. It's called PSP (Python Server Pages) or something like that.

I'm pretty sure urllib doesn't do that stuff, or much of anything useful from a server's standpoint.

---

### Post by loell on 2008-11-24
[http://www.cherrypy.org/]("http://www.cherrypy.org/") :)

its nice for simple things..

---

### Post by pmasiar on 2008-11-24
If you want tp keep things simple, don't bother with cerrypy or mod_python, use simples of the simple - Python's cgi module. For example, see wiki in my sig: simplest 3 line CGI script.

---

### Post by fiddler616 on 2008-11-25
> **pmasiar said:**
> If you want tp keep things simple, don't bother with cerrypy or mod_python, use simples of the simple - Python's cgi module. For example, see wiki in my sig: simplest 3 line CGI script.
Thanks for cleaning/clearing things up-- the only visible Python I need is a text box, and I'm *sure* that's easy.

Cheers.

---

