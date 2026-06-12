---
title: "[Python][HTML] How do I make a Python script within an HTML page?"
date: 2008-09-16
forum: Programming Talk
---

### Post by fiddler616 on 2008-09-16
Hey,
A few days ago, I saw my first, real-live javascript-in-an-HTML-page, with source, explanation from author, etcetera. All it did was provide a countdown to graduation, with three if statements (it's coming, it's happening, it's gone), but it was embedded in the HTML, and I thought it was kinda neat (OK. I am *now* entering the 21st century. Be quiet :) )
But I don't know Javascript, and it's not on my List of Things to Learn either.
And then I found out that you can do the exact same thing with Python.
And the server for my website supports Python.
And has terrible documentation on how to do it.
So the question is: How do I make this Python script?
(I'm really hoping the answer will look something like this: )
```

<HTML>
<BODY>
<Script language=Python...or something>
#Some crazy Shebang thing...what?
string = "Hello"
other_string = "World!"
print string + other_string
</script>
Woot! I'm normal HTML
</BODY>
</HTML>

```
Thanks

---

### Post by LaRoza on 2008-09-16
It doesn't work that way...

It would require doing some things on the server and communicating back and forth. From your post, it isn't within your abilities.

---

### Post by fiddler616 on 2008-09-16
> **LaRoza said:**
> It doesn't work that way...

It would require doing some things on the server and communicating back and forth. From your post, it isn't within your abilities.
Darn (on both counts). I was kind of under the impression that all the comp--I mean, interpreting would be server-side, but I guess not.
Thanks though.

---

### Post by LaRoza on 2008-09-16
> **fiddler616 said:**
> Darn (on both counts). I was kind of under the impression that all the comp--I mean, interpreting would be server-side, but I guess not.
Thanks though.

You can try: [http://try-python.mired.org/](http://try-python.mired.org/)

I am not sure exactly how it works, but it requires JavaScript. My guess it runs the command on the server and uses Ajax (a way of using JavaScript) but it could (depending on its abilities) be entirely client side but that would require writing something to behaving like Python in JavaScript, a large task.

(After running a few commands, I see it is server side Python using Ajax to communicate with the browser)

---

### Post by fiddler616 on 2008-09-16
> **LaRoza said:**
> You can try: [http://try-python.mired.org/](http://try-python.mired.org/)

I am not sure exactly how it works, but it requires JavaScript. My guess it runs the command on the server and uses Ajax (a way of using JavaScript) but it could (depending on its abilities) be entirely client side but that would require writing something to behaving like Python in JavaScript, a large task.
I think it's a safe bet that it uses the JavaScript to send the user's input through try.py, which is located on their server, and which spits back the interpreted output, using JavaScript to do the spitting.
(This guesswork is based on [this]("http://try-python.mired.org/ajax.js"), the source of the main Try Python page, and the error message:
> >>> purposefulerror
Traceback (most recent call last):
  File "/var/apache2/2.2/htdocs/try.py", line 146, in wrapper
    value, wantmore = evaluate(source, hisvars)
  File "/var/apache2/2.2/htdocs/try.py", line 126, in evaluate
    value = eval(code, hisvars)
  File "<stdin>", line 2, in <module>
But we digress.

---

### Post by Reiger on 2008-09-16
You need to make a distinction:
Server-side (where your webpage get's *generated*);
Client-side (where you can influence user experience by making it feel inter-active (the most))

Python, PHP, Java etc. etc. can be used 'server side'. You can have limited interactivity on the client side with Java (applets) too, there will probably be engines for other languages in some browser (but IIRC these aren't there for *all* mainstream browsers). JavaScript on the other hand is in some form or another among the most widely available client-side scripting languages. There exists, of course, Flash; but as of yet browsers for instance don't come with Flash plug-ins out of the box. And keep in mind the use for HTML pages and JavaScript controls/event handlers thrown serves other uses beyond the usual browser, e.g.: compiled HTML help libraries; scripting for other apps.

EDIT: What your digressing post talks about is do-able; and is more or less one of the concepts behind the design pattern known as AJAX.

---

### Post by LaRoza on 2008-09-16
> **Reiger said:**
> 
EDIT: What your digressing post talks about is do-able; and is more or less one of the concepts behind the design pattern known as AJAX.

Yes, my post states that ;)

---

### Post by fiddler616 on 2008-09-16
> **Reiger said:**
> You need to make a distinction:
Server-side (where your webpage get's *generated*);
Client-side (where you can influence user experience by making it feel inter-active (the most))

Python, PHP, Java etc. etc. can be used 'server side'. You can have limited interactivity on the client side with Java (applets) too, there will probably be engines for other languages in some browser (but IIRC these aren't there for *all* mainstream browsers). JavaScript on the other hand is in some form or another among the most widely available client-side scripting languages. There exists, of course, Flash; but as of yet browsers for instance don't come with Flash plug-ins out of the box. And keep in mind the use for HTML pages and JavaScript controls/event handlers thrown serves other uses beyond the usual browser, e.g.: compiled HTML help libraries; scripting for other apps.

EDIT: What your digressing post talks about is do-able; and is more or less one of the concepts behind the design pattern known as AJAX.
Server-side/client-side: Didn't I say that *reviews posts*. Oh, I guess not...well, by implication "And the server for my website supports Python."
Digressing: Well, I'd hope it's doable, since it's being done over at Try Python (well, I guess it's just a hypothesis that they're doing it that way). Now that LaRoza posted: I guess it depends on how you parse it.
This thread is getting kind of wacky, so here's
**An attempt at disambiguation**
I want to put a Python script on a .html file that will be interpreted by the server.
This is to enable more dynamic webpages, *sort of* like Javascript in the end result, but going about it differently since it's interpreted/compiled in a different location, and is a different language.
----

---

### Post by LaRoza on 2008-09-16
> **fiddler616 said:**
> Server-side/client-side: Didn't I say that *reviews posts*. Oh, I guess not...well, by implication "And the server for my website supports Python."
Digressing: Well, I'd hope it's doable, since it's being done over at Try Python (well, I guess it's just a hypothesis that they're doing it that way). Now that LaRoza posted: I guess it depends on how you parse it.
This thread is getting kind of wacky, so here's
**An attempt at disambiguation**
I want to put a Python script on a .html file that will be interpreted by the server.
This is to enable more dynamic webpages, *sort of* like Javascript in the end result, but going about it differently since it's interpreted/compiled in a different location, and is a different language.
----

It is possible, but no browser I know has support for that.

You'd have to make a plugin for it. It is possible to use TCL to make applets (Tclets), but it isn't wide spread.

---

### Post by pmasiar on 2008-09-16
> **fiddler616 said:**
> I want to put a Python script on a .html file that will be interpreted by the server.

You are missing major point. Use wikipedia and HowStuffWorks to understand how dynamic pages work, it's more tricky than you suspect.

from POV of server (ie Python code), HTML page is just a text file which needs to be (generated according to dynamic parameters and) sent to browser. It's the browser which interprets HTML to show you the page, and possibly detect JavaScript and run it to make page "dynamic".

You may want to try Jython, which might be possible to run as Java applet (not JavaScript).

[http://www.howstuffworks.com/web-page.htm](http://www.howstuffworks.com/web-page.htm)
[http://computer.howstuffworks.com/web-server.htm](http://computer.howstuffworks.com/web-server.htm)
[http://computer.howstuffworks.com/cgi.htm](http://computer.howstuffworks.com/cgi.htm)

---

### Post by pp. on 2008-09-16
> **LaRoza said:**
> It is possible, but no browser I know has support for that.

Since OP wants to do server side python scripts, there will not be any Python in the page at the time the page reaches the browser.

> **pmasiar said:**
> ... to understand how dynamic pages work, it's more tricky than you suspect.

from POV of server (ie Python code), HTML page is just a text file which needs to be (generated according to dynamic parameters and) sent to browser. It's the browser which interprets HTML to show you the page, and possibly detect JavaScript and run it to make page "dynamic".

You're discussing traditional generic web servers with gate interface.

In the case of a php based site, the HTML page is in actual fact a script with some embedded HTML tags (or a HTML page with embedded commands that can be interpreted on the server side by the php interpreter).

It's been some time since I had a closer look, but I think ZOPE and possibly some other Python based CMSs could conceivably offer the capability to embed python code into HTML templates or HTML fragments into Python scripts, which then would be processed on the server and converted into HTML, possibly with some embedded ECMA scripts to be run on the client.

---

### Post by LaRoza on 2008-09-16
> **pp. said:**
> Since OP wants to do server side python scripts, there will not be any Python in the page at the time the page reaches the browser.


It wasn't clear. The OP speaks of putting Python in .html files. To me, that means on the client.

---

### Post by fiddler616 on 2008-09-16
The OP has stated twice that he wants server-side, and used 'Python in HTML' for lack of a better term*. He is also quite tired of speaking in the third person
*What *should* I use?

---

### Post by LaRoza on 2008-09-16
> **fiddler616 said:**
> The OP has stated twice that he wants server-side, and used 'Python in HTML' for lack of a better term*. He is also quite tired of speaking in the third person
*What *should* I use?

The way you worded it was confusing and inaccurate. You should have just said "I want to use Python for server side programming".

---

### Post by fiddler616 on 2008-09-16
> **LaRoza said:**
> The way you worded it was confusing and inaccurate. You should have just said "I want to use Python for server side programming".
Sorry.

---

### Post by LaRoza on 2008-09-16
> **fiddler616 said:**
> Sorry.

As long as you got what you want (pmasiar seemed to have given that?)

It sound like you wanted Python interactively in an HTML document.

---

### Post by forger on 2008-09-16
Edit: I agree that you should've been clear from the first place :)

I think you need mod_python for apache (or whatever http server you might use)
[http://www.howtoforge.com/embedding-python-in-apache2-with-mod_python-debian-etch](http://www.howtoforge.com/embedding-python-in-apache2-with-mod_python-debian-etch)

---

### Post by Reiger on 2008-09-16
Yes, but "sort of like JavaScript" is not possible with Python *on the server*. In actual fact that is not possible with any 'conventional' (CGI) language *on the server*. Because a server, well just, outputs things. You can influence what it outputs and even when; but the *big* difference with JavaScript is that it will be *on the server*.

A good deal about JavaScripting is that it feels so counter-intuitive and wasteful going to the server for every trivial event-handling (onmouseover ?) scenario. So you solve it on the client side by JavaScript. That and the idea of making your pages more interactive, is the basic idea behind D(ynamic)HTML.

You cannot achieve that with an Java wrapper applet to the Jython engine, because; well the applet is just an app of its own embedded in your page. It is not a script to make the browser act interestingly on that page. Jython will let you have a script-able app on your page; but still not offer a script for your browser to act interestingly with. It'll still be that applet that is doing the work and not the browser itself.

See the circle unfold?

---

### Post by pmasiar on 2008-09-17
> **pp. said:**
> 
You're discussing traditional generic web servers with gate interface.

In the case of a php based site, the HTML page is in actual fact a script with some embedded HTML tags (or a HTML page with embedded commands that can be interpreted on the server side by the php interpreter).

It is exactly the same in both cases: web server finds (by URL) and runs a script responsible to generate text file (containing HTML) as response to request. You are fooled by PHP, because PHP programs looks like HTML page (with mixed in PHP commands), it's exactly done so you will not notice the difference.

> ZOPE and possibly some other Python based CMSs could conceivably offer the capability to embed python code into HTML templates or HTML fragments into Python scripts, which then would be processed on the server and converted into HTML,

Of course. And you don't need to use monsters like Zope to do that now: simple and elegant templating engines like Kid/Genshi allow you to define (in template, in Python) little functions generating snippets of HTML from requested data.

> possibly with some embedded ECMA scripts to be run on the client.

Why you mix Javascript again? From POV of server, JS is just text which needs to be packed into HTML file and shipped to the browser.

---

### Post by pp. on 2008-09-17
> **pmasiar said:**
> It is exactly the same in both cases: 

The same file can be claimed to be a HTML document or a PHP document at the same time. Only one case.

> **pmasiar said:**
> you don't need to use monsters like Zope to do that now: simple and elegant templating engines like Kid/Genshi allow you to define (in template, in Python) little functions generating snippets of HTML from requested data.

Ah, I only knew Zope which I don't like. I mentioned it here because it appears to fit the bill for OP's OR (Original Request), namely to use templates with embedded Python code.

> **pmasiar said:**
> Why you mix Javascript again? From POV of server, JS is just text which needs to be packed into HTML file and shipped to the browser.

I don't mix. I merely point out that using server side scripts to generate a page does not preclude the use of client side scripts to enhance the user's "web experience". 

Though, to be truthful, I see some fascinating possibilities using a server side script to construct a client side script which is tailored to a specific context or content. Be a nightmare to maintain, of course.

---

### Post by pmasiar on 2008-09-17
> **pp. said:**
> I don't mix. I merely point out that using server side scripts to generate a page does not preclude the use of client side scripts to enhance the user's "web experience". 

Though, to be truthful, I see some fascinating possibilities using a server side script to construct a client side script which is tailored to a specific context or content. Be a nightmare to maintain, of course.

You mean [http://en.wikipedia.org/wiki/Ajax_(programming](http://en.wikipedia.org/wiki/Ajax_(programming)) , generating AJAX scripts dynamically? It's just plain web2.0, nothing new 8-) It's easy, exactly because JS is just another text to be generated from template. Really interesting AJAX is [http://en.wikipedia.org/wiki/ZK_Framework](http://en.wikipedia.org/wiki/ZK_Framework) which  pushes all page events to be processed by server, and [http://en.wikipedia.org/wiki/Google_Web_Toolkit](http://en.wikipedia.org/wiki/Google_Web_Toolkit) which generates JS from Java sources.

---

### Post by pp. on 2008-09-17
> **pmasiar said:**
> You mean [http://en.wikipedia.org/wiki/Ajax_(programming)](http://en.wikipedia.org/wiki/Ajax_(programming)) , generating AJAX scripts dynamically? It's just plain web2.0, nothing new 8-) It's easy, exactly because JS is just another text to be generated from template. Really interesting AJAX is [http://en.wikipedia.org/wiki/ZK_Framework](http://en.wikipedia.org/wiki/ZK_Framework) which  pushes all page events to be processed by server, and [http://en.wikipedia.org/wiki/Google_Web_Toolkit](http://en.wikipedia.org/wiki/Google_Web_Toolkit) which generates JS from Java sources.

Yes, those are valid and reasonable examples. While there's nothing esoteric or even new about the idea, it could lead to quite attractive sites.

Well, we're a bit off topic.

---

### Post by fiddler616 on 2008-09-17
> **pp. said:**
> 
Well, we're a bit off topic.
Thanks. I couldn't decide if good health debate was going to lead to a solution or not, so I didn't want to interfere. (Never mind that 30% of it was over my head...)
**Rephrased Question**
How do I make a dynamic webpage with Python?
**Notes:**
[LIST]
[*]My server says it supports Python scripting (but doesn't say much else)
[*]I understand that it'll be server-side
[*]I want the Python scripting to mesh smoothly with an HTML page
[/LIST]

---

### Post by pp. on 2008-09-17
> **fiddler616 said:**
> 
**Rephrased Question**
How do I make a dynamic webpage with Python?
**Notes:**
[LIST]
[*]My server says it supports Python scripting (but doesn't say much else)
[*]I understand that it'll be server-side
[*]I want the Python scripting to mesh smoothly with an HTML page
[/LIST]

Partial answer can be derived from that snipped:

> **pmasiar said:**
> ... you don't need to use monsters like Zope to do that now: simple and elegant templating engines like Kid/Genshi allow you to define (in template, in Python) little functions generating snippets of HTML from requested data.

I can not even point toward the full answer as I have yet to write any Python code, do not like Zope and haven't heard of the other products til now.

---

### Post by pmasiar on 2008-09-17
> **fiddler616 said:**
> How do I make a dynamic webpage with Python?
**Notes:**
[LIST]
[*]My server says it supports Python scripting (but doesn't say much else)
[*]I understand that it'll be server-side
[*]I want the Python scripting to mesh smoothly with an HTML page
[/LIST]

These days, when you say "dynamic" web page, everybody assumes AJAX == Javascript. So if you are fine with server side, call it web based application ;-) And don't say "scripting" - what you do is application development, not scripting.

Simplest option is just use plain CGI to process HTTP request and generate HTML response, like in old times (with plain Apache CGI). It is less effective (process is started for each response) but that's what probably your host provides. See wiki in my sig for simple Python CGI apps (simplest is 3 lines, just to test your settings). One thing you **definitely** want to use cgitb module to get traceback in browser, exactly like when you debug in terminal.

If you feel lucky, try to ask your hosting company what web app framework they prefer and allow you to use. There are two leading front-to-end frameworks: Django and TurboGears (as opposed to Pylons, which is meta-framework to build frameworks: TG 2.0 is based on Pylons).

Django is recommended to beginners, but Django uses custom templating language (for in-template expressions). TG can use many different templating packages, and Kid/Genshi use Python as expression language. 

Both Dj and TG use Python as server-side language, and come with non-apache local development server, so you can develop your app on your workstation (as localhost) before deploying it on the server (so you don't need to pay web hosting to learn how to create web apps).

---

