---
title: "Use Python like PHP?"
date: 2008-10-16
forum: Programming Talk
---

### Post by jacensolo on 2008-10-16
I'm looking to create a photo album program for my personal website. I know I could install pre-made software but that isn't any fun, now is it? Right now I'm in the process of making software that helps me create my sqlite database since I have a lot of pictures.

I want to use python to create the photo album program. I know I could use php, but I'd rather use python for fun. The problem is I don't know how to set it up. I know there is Django, but that seems too complicated for my simplistic needs. IE: I want to run python like php, no framework (or close to it.) My web server is Apache. I got mod_python working, but there isn't a guide on how to do anything.

My other question is what is the difference between a file database system (sqlite) and a SQL server (MySQL)? I'm using sqlite because I couldn't get MySQL to work. Is there any reason to use MySQL over sqlite other than traffic?

---

### Post by snova on 2008-10-16
mod_python has some documentation. It's a little tricky to set up correctly, but look for PSP- Python Server Pages. It works almost exactly like PHP, all the way up to the <? and ?> tags.

Or you can do it the other way, and generate everything from Python, instead of using the tags.

Django is a web framework, which might be more than you need.

---

### Post by snova on 2008-10-16
Here's how I got things set up:

In /etc/apache2/httpd.conf:

```
DirectoryIndex index.py index.php index.xhtml index.html
```

In .htaccess:

```
AddHandler mod_python .py
PythonHandler mod_python.publisher
PythonDebug On

```

In index.py:

```
from mod_python import apache

def index( req, **args ):
    req.content_type = 'text/plain'
    req.write( 'Hello Again!' )
    req.write( 'args = ' + str( args ) )

def two( req ):
    req.content_type = 'text/plain'
    req.write( 'Hello Two!' )

```

That should be enough to get started. There might be one or two other things I did, though... Remember to enable mod_python ("sudo a2enmod mod_python").

Sqlite runs from the requesting program, as a library. MySQL runs as a server, as a separate program.

---

### Post by jacensolo on 2008-10-16
> **snova said:**
> mod_python has some documentation. It's a little tricky to set up correctly, but look for PSP- Python Server Pages. It works almost exactly like PHP, all the way up to the <? and ?> tags.

Or you can do it the other way, and generate everything from Python, instead of using the tags.

Django is a web framework, which might be more than you need.
I found S[pyce]("http://spyce.sourceforge.net/"), is this what you were talking about? PSP looked like it was meant to work with Jython. Either way, I'm taking a look at Spyce right now. I'll report back later.

I'm still open to comments from anyone though.

Oh, thanks for the tip on mod_python. I need that running for Spyce.

---

### Post by snova on 2008-10-16
What I meant was that mod_python has two primary modes of operation. It's quite flexible though.

The first is PSP, where you embed Python code in HTML files like you would with PHP, but with slightly different tags- <% (I think) instead of <?.

The second is more like CGI, where your scripts are run as plain Python. The only difference between this and CGI is that writing to the client isn't quite as simple as a "print" statement, as you have to go through mod_python instead.

I personally prefer the second way of doing things, but if you come from PHP the first would be more familiar. But my configuration guidelines will have to be changed somewhat.

By the looks of the documentation, it should be as simple as changing the PythonHandler to mod_python.psp.

Edit: Ooh, neat- mod_python can even work as a CGI emulator. PythonHandler is set mod_python.cgihandler for this. That might be interesting.

---

### Post by jacensolo on 2008-10-16
I never got spyce to work for some reason, but I got psp to work. I don't like it though. I'm going back to the publisher handler.

---

### Post by pmasiar on 2008-10-16
if you want it really simple, don't bother with mod_python, use plain cgi module. To make it even simpler for playing arounf, don't bother with Apache either - you can get really simple CGI web server (of course slower and worse thatn Apache - but who cares?) in about 7 lines of Python code.

Then, if you don't want to use templating system, use either plain string substitution, or htmltmpl - the simplest templating engine.

I would definitely advise **against** PSP (Python server pages) - much better approach is templating using Kid or Genshi. Trust me on that. Very flexible, especially if you want to have 100% valid XML.

But this way you are doing it so wrong: Django is right way to do real (and reliable) web app, using MVC pattern. Only good for trivial apps or training.

See wiki in my sig for links

---

### Post by mssever on 2008-10-16
Note that using plain cgi instead of something like Django is a bit like writing C instead of Python. It can be a lot more work up front. My first foray into Python was just that (and I had no prior experience with CGI, since PHP abstracts a fair amount of CGI away. It was a frustrating experience. Nowadays, I could probably do something like that much easier, but I haven't come up with a compelling reason to do so.

The thing with PHP (and its style) is, it's really easy to get started with, but once you learn more, you realize that you wasted your time because you were doing things in such a backwards way that fixing them will require a rewrite.

---

### Post by jacensolo on 2008-10-17
I decided my program will be more complicated than I thought, so I picked up Django. I went through the tutorial and thought it looked hard. But it isn't. The templating system is very easy, the administration intereface is ace if I ever need it, and the best part is the lack of knowledge needed about databases (even though I think I would be fine with databases).

It does have a problem I imagined, I can't figure out what all the commands are, like DateTimeField. I know what that one is, but where do I find info about other ones (that aren't in the tutorial)?
Edit: Wow, found the docs. I'm stupid.

And I can't get it to work with apache. I have mod_python installed and working, and httpd.conf set up the way it says, I think. Will somebody please look at it?

```
<Location "/mysite/">
    SetHandler python-program
    PythonHandler django.core.handlers.modpython
    SetEnv DJANGO_SETTINGS_MODULE settings
    PythonOption django.root mysite
    PythonDebug On
    PythonPath "['/home/myhomedir/website/mysite', '/home/myhomedir/django-1.0'] + sys.path"
</Location>

```

My site Django project is in /home/mydir/website/mysite. The app form the tutorial is /home/mydir/website/mysite/polls Apache's default root is /home/myhomedir/website. My error (summed up) is: ```
Import Error: no module named mysite.
```

---

### Post by jacensolo on 2008-10-18
Anyone know?

---

### Post by snova on 2008-10-18
Remove the "mysite" suffix from the PythonPath invocation. That should work.

---

### Post by jacensolo on 2008-10-18
> **snova said:**
> Remove the "mysite" suffix from the PythonPath invocation. That should work.

Thanks! that worked. I also had to change it to mysite.settings.

---

### Post by jacensolo on 2008-10-18
My admin interface isn't showing up properly under apache. It works, [but...]("http://img73.imageshack.us/my.php?image=screenshotqc5.png")

Now what? It works under the development server.

---

### Post by slavik on 2008-10-19
> **pmasiar said:**
> if you want it really simple, don't bother with mod_python, use plain cgi module. To make it even simpler for playing arounf, don't bother with Apache either - you can get really simple CGI web server (of course slower and worse thatn Apache - but who cares?) in about 7 lines of Python code.

Doesn't this go against the not reinventing the wheel idea? Also, that 7 line http server ... what happens when someone tries to access the site.com/../../../../../etc/passwd file?

---

### Post by pmasiar on 2008-10-19
> **slavik said:**
> Doesn't this go against the not reinventing the wheel idea? Also, that 7 line http server ... what happens when someone tries to access the site.com/../../../../../etc/passwd file?

Reinventing the wheel is the whole point of learning, no?

I never said about using that 7 line web server in **production** but it is heck easier to set up than Apache 8-)

---

### Post by LaRoza on 2008-10-19
> **slavik said:**
> Doesn't this go against the not reinventing the wheel idea? Also, that 7 line http server ... what happens when someone tries to access the site.com/../../../../../etc/passwd file?

It is for personal development use.

Any poorly coded app has a security flaw, but if you consider that a problem, then you have to deal with the fact the only user using that server will be the same person who has access to the shell and likely knows the password.

It isn't re-inventing the wheel. It isn't the same as Apache. It is a small personal development server, that happens to be easily written.

---

### Post by jacensolo on 2008-10-20
> **jacensolo said:**
> My admin interface isn't showing up properly under apache. It works, [but...]("http://img73.imageshack.us/my.php?image=screenshotqc5.png")

Now what? It works under the development server.

Still having this problem.

---

