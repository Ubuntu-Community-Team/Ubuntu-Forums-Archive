---
title: "using Python Scripts instead of Javascript for web?"
date: 2008-03-27
forum: Programming Talk
---

### Post by WinterWeaver on 2008-03-27
I've looked around and it seems possible to use Python scripts (server side) rather than javascript. My problem... I'm a html/web scripting noob, and dont even know where to start :P

I have my script, and it should work, but how would I call it in my HTML document?

I tried to call it like I would a normal javascript, ie:
```
<script src="./scripts/myscript.py"></script>
```
but of course it's not gonna be that easy... lol

At the moment I'm just trying to get it running locally.

Can anyone point me in the right direction?

ps: Ive tried searching on google but I'm unable to make much sense of the documentation out there.

Thanks,

WW

---

### Post by LaRoza on 2008-03-27
You can't do that.

ECMAScript (JavaScript and JScript are implemenations of the ECMA-262 standard), is the only way. The browser is a sandbox, at least, it should be.

You can use Java and also Tcl in the client, as they have plugins for their interpreters/VM. (They are called "Applets" or "Tclets"). You can use Python on the Java platform as well (as Jython).

---

### Post by mssever on 2008-03-27
Server-side code can't do client-side work. So you can't use Python on the client side. However, someone around here (Wybiral, I think) is working on a Python to Javascript converter.

---

### Post by LaRoza on 2008-03-27
> **mssever said:**
> Server-side code can't do client-side work. So you can't use Python on the client side. However, someone around here (Wybiral, I think) is working on a Python to Javascript converter.

Yes, Epy I believe.

---

### Post by Wybiral on 2008-03-27
> **LaRoza said:**
> Yes, Epy I believe.

Indeed, although I'm not sure if I should continue it since PyPy has [something similar]("http://codespeak.net/pypy/dist/pypy/doc/js/using.html") (and since it's PyPy, probably way better). Plus the source needs some heavy spring cleaning (my Python style has changed quite a bit in the past few months, I'm not very proud of most of that code).

EDIT:

But if there's demand... I wouldn't mind keeping it up.

---

### Post by WinterWeaver on 2008-03-27
whoops... I guess I'm stuck then. I have a little script that Gets a RSS feed and returns the feed in some html for me, which I wanted to include to a website I'm working on.

I guess I'll have to use it in my zope server then?

I didn't want to do this from the start, as I dont know how I'll convince my client to pay the extra monies to host his site on a zope server.

---

### Post by Wybiral on 2008-03-27
Not necessarily... Python can be used with CGI too. You might want to look into whether their current server is capable of CGI + Python or not.

---

### Post by WinterWeaver on 2008-03-27
How would I set up CGI on my localhost?

sorry for all the questions... But I have not dealt with hosting myself.

ta,

WW

---

### Post by stevescripts on 2008-03-27
You can set up CGI on your local host through the Apache config file ...

Been long since I did so - *if* I recall, somewhere in the script alias

Steve

---

### Post by pmasiar on 2008-03-27
IMHO you are diving into way too deep water for your skill level. Do you have patience to learn programming (will take you couple of months, maybe a year, depending of dedication)? Or will you be satisfied to be just a script kiddie, who will run something scraped together from different advices? What are your goals, what is your aspiration level? And what is your current skill level?

---

### Post by WinterWeaver on 2008-03-28
> IMHO you are diving into way too deep water for your skill level. Do you have patience to learn programming (will take you couple of months, maybe a year, depending of dedication)? Or will you be satisfied to be just a script kiddie, who will run something scraped together from different advices? What are your goals, what is your aspiration level? And what is your current skill level?

Well, I was coding quite a bit when younger. I'm not too bad at coding etc. It's just that I'm self taught, and therefore have many gaps in my education, not to mention a 7 year period of my life that I didn't touch any coding at all.

I've been coding with python for the last year and enjoy it a lot, been writing tools for work to automate some of our tasks. Sure I still have to learn a lot, but I'm enjoying it. I'm a qualified as a Graphic Designer, but was never really good at it. I've only started HTML and web Last year, and I already 3 websites out (2 normal html and css, 1 plone). So basically I'm wanting to combine my two skillsets.

So, yes I'm aware the water is deep, but this is something that I enjoy, and intend to take further, and I'm very serious about it. ^_^

Thanks for the input

WW

---

### Post by pmasiar on 2008-03-28
OK, so you are web app guy! Check [http://learnpython.pbwiki.com/WebApplication](http://learnpython.pbwiki.com/WebApplication) to see **very **simple web application (including your own simple web server). You may want to look at TurboGears, it contains also decent development web server (CherryPy). You don't need JavaScript at all, unless you want to add some functionality on client (without page reload) - called AJAX. For that, you are much better off using some JS library, like MochiKit, jQuery, Yahoo User Interface (YUI) etc - it adds convenience methods and handles cross-browser compatibility. 

Start learning about every term you don't know at wikipedia - it is excellent, wikipedia knows **everyting**. :-)

---

### Post by themusicwave on 2008-03-28
The Book Programming Python also has a section on using Python on the Server Side for CGI and such.

Overall a good Python book, might be worth it for you if it helps.

---

### Post by loell on 2008-03-28
looks interesting :)

[http://www.pyxer.net/](http://www.pyxer.net/)

---

### Post by WinterWeaver on 2008-03-28
Great! Thanks for all the help and info! This will keep me busy for a while lol :)

pmasiar, thanks for the link, that site look like it's exactly what I was looking for, but couldn't find... my google-fu aint good enough it seems :P

Thanks again!

WW

---

### Post by ruy_lopez on 2008-03-28
Python is good for CGI. Especially multi-line """ quoting. You don't need to use '\t' and '\n' so much.

I kinda like Javascript, also. It's fairly quick. 

If I could replace PHP with Python I'd be a lot happier. The only time I use PHP these days, is for the server-side component of AJax, and even that annoys me. The Vim cursor gets sluggish when it enters a PHP block. And it doesn't matter if it's one line or a hundred.

EDIT: back on topic: The [W3Schools]("http://www.w3schools.com/default.asp") page is a good resource for everything from HTML to XML. I use it mainly as a reference, but there are tutorials as well.

---

### Post by gjj391 on 2008-03-28
you could try using mod_python... you should definatly take a sec to learn some html/css, if your wanting to play on the web

---

### Post by WinterWeaver on 2008-03-28
Wowie!

Thanks for all the help.

Right, so I have created my own CGI web server by following the link pmasiar gave me.

This worked great! I put my getRSS.py script into that folder, and it did it's job. I then loaded the scripts' output into a iframe on my local site.

Thanks for all the help.

btw ruy_lopez, have you looked at KSS? It's quite new, and looks promissing. I've not worked with AJAX before, but I was told that KSS aims to do the same.
EDIT: Link >> [http://kssproject.org/](http://kssproject.org/)

ta,

WW

---

### Post by pmasiar on 2008-03-28
> **WinterWeaver said:**
> that site look like it's exactly what I was looking for, but couldn't find... my google-fu aint good enough it seems :P

Of course :-) This is curated collection of links I accumulated over couple years. Google never can match quality of hand-picked links; exactly like human never can search through whole internet like Google spider can.

Enjoy!

---

