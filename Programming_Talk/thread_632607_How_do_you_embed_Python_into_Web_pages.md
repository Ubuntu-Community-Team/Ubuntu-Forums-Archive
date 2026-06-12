---
title: "How do you embed Python into Web pages?"
date: 2007-12-05
forum: Programming Talk
---

### Post by 1337455 10534 on 2007-12-05
Is there a simple way to use Python in web pages so that windows computers that dont have Python can still access the page completely?
I'm talking;
<html>
<head>
<script type="Python2.x">
mercy = 0
def haha():
...print "hahah"
while mercy == 0:
...haha()
</script>
</head>

---

### Post by LaRoza on 2007-12-05
That is a bad practice, but it depends on what server you are using.

---

### Post by cwaldbieser on 2007-12-05
> **LaRoza said:**
> That is a bad practice, but it depends on what server you are using.

From his example, it actually looks like he is asking if it is possible to run a client side python script that won't cause an error if the client web browser doesn't support python.

---

### Post by LaRoza on 2007-12-05
> **cwaldbieser said:**
> From his example, it actually looks like he is asking if it is possible to run a client side python script that won't cause an error if the client web browser doesn't support python.

The example also looks like the IIS syntax for server side scripts.

@OP You can only use ECMAScript (JavaScript and JScript) and VBScript on the client.

---

### Post by 1337455 10534 on 2007-12-05
I'm sorry, but the whole 'mercy == 0' was just a joke!
All I'm looking for is a multi-platform python-independent way of, say, printing "hi" on the screen using Python, but in an HTML file. By saying Python is server-side, do you mean it can only be used by the server to make an end-product that the user sees? e.g I heard somewhere that YouTube uses Python; does that mean that if I look at the source of the page through a browser, I cant find some Python?

---

### Post by LaRoza on 2007-12-06
> **1337455 10534 said:**
> 
All I'm looking for is a multi-platform python-independent way of, say, printing "hi" on the screen using Python, but in an HTML file. By saying Python is server-side, do you mean it can only be used by the server to make an end-product that the user sees? e.g I heard somewhere that YouTube uses Python; does that mean that if I look at the source of the page through a browser, I cant find some Python?

Server side means the code is executed on the server, before the document is sent. 

See [http://laroza.freehostia.com/home/index.php](http://laroza.freehostia.com/home/index.php)

The document is written in PHP, not Python, but it is the same concept. The actual index.php has no markup in it at all, just PHP code. The server executed the code, then sends the result to the browser. 

In the linked page, there is also client side code. It is what prompts for the download and makes the links a different colour on the current page, and what makes the entire element link to another page, an not just the <a>.

You can view the client side code in Firefox with the web developer toolbar (it is Synaptic and on the Firefox extensions page) here is the direct link: [http://laroza.freehostia.com/home/script/script.js](http://laroza.freehostia.com/home/script/script.js)

The script (ECMAScript) is executed by the browser.

---

### Post by pmasiar on 2007-12-06
>  I heard somewhere that YouTube uses Python; does that mean that if I look at the source of the page through a browser, I cant find some Python?

No. Python runs on the server and generates HTML for your browser to display.

Read [http://en.wikipedia.org/wiki/Common_Gateway_Interface](http://en.wikipedia.org/wiki/Common_Gateway_Interface)

> **1337455 10534 said:**
> All I'm looking for is a multi-platform python-independent way of, say, printing "hi" on the screen using Python, but in an HTML file. 

You are confusing things. "multi-platform" may mean  "running in a browser" - Firefox runs on many platforms, or it mean "runs on any desktop" - and then you need to handle differences between Windows, mac OSX, Linux Gnome, Linux KDE, X, etc. But probably not desktop, because you mixed up HTML.

When you said "python-independent way to print 'hi' using Python" I am totally confused. Are you sure you know what you want?

---

### Post by Wybiral on 2007-12-06
But if you think about it, Python would make one awesome Javascript replacement. I wonder if any browsers in the future might take that step? Obviously large parts of the language will need disabled for security reasons, but it would still be nice to be able to use Python syntax for client-side scripting.

---

### Post by ThinkBuntu on 2007-12-06
> **Wybiral said:**
> But if you think about it, Python would make one awesome Javascript replacement. I wonder if any browsers in the future might take that step? Obviously large parts of the language will need disabled for security reasons, but it would still be nice to be able to use Python syntax for client-side scripting.
JavaScript is great and has been developed for client-side interactions. Now, they could improve it to make it more like Python, but with the rise of AJAX, etc. it will be the client-side standard for some time to come.

But client-side Ruby or Python would just be awesome.

---

### Post by Wybiral on 2007-12-06
> **ThinkBuntu said:**
> JavaScript is great and has been developed for client-side interactions. Now, they could improve it to make it more like Python, but with the rise of AJAX, etc. it will be the client-side standard for some time to come.

But client-side Ruby or Python would just be awesome.

Since Python has modules for DOM manipulation it's capable of AJAX as well. In fact there are several JSON generating/parsing libraries that would make it pretty painless. I'd say the main reason would be security issues since you would have to rip out 75% of the standard modules to prevent code from doing naughty things. But it would definitely be pretty cool. Off topic, but I would also like to see something like Python+PyGame replacing flash and Java applets... That would be seriously awesome.

---

### Post by ThinkBuntu on 2007-12-06
> **Wybiral said:**
> Since Python has modules for DOM manipulation it's capable of AJAX as well. In fact there are several JSON generating/parsing libraries that would make it pretty painless. I'd say the main reason would be security issues since you would have to rip out 75% of the standard modules to prevent code from doing naughty things. But it would definitely be pretty cool. Off topic, but I would also like to see something like Python+PyGame replacing flash and Java applets... That would be seriously awesome.
Flash is the bane of my existence as a web designer. "We'd like to use Flash...", and my response is "you don't need Flash for anything but intricate animations." It's not very accessible and requires Adobe Flash to produce, which are my two biggest complaints about it.

EDIT: I misspoke. IE6 is the bane.

---

### Post by Wybiral on 2007-12-06
> **ThinkBuntu said:**
> Flash is the bane of my existence as a web designer. "We'd like to use Flash...", and my response is "you don't need Flash for anything but intricate animations." It's not very accessible and requires Adobe Flash to produce, which are my two biggest complaints about it.

EDIT: I misspoke. IE6 is the bane.

I hear you load and clear. What really sucks is that there are no open standard media outlets for browsers. So if you want to play a video on a webpage you basically either have to use a flashplayer or embed it for a specific media player... Neither of which are open or standardized. We need a universal standard that supplies a Javascript API capable of controlling and embedding media objects. Maybe if FF and Opera did it IE would have to follow? Nah, they would probably make their own :mad: (but they would steal our tabs).

---

### Post by ThinkBuntu on 2007-12-06
Actionscript is supposed to be very similar to JavaScript, although I've only worked with JS. I'm sure it wouldn't be a stretch.

---

### Post by pmasiar on 2007-12-06
> **ThinkBuntu said:**
> JavaScript ... AJAX, etc. it will be the client-side standard for some time to come.

Yup, even MSFT is not happy that they forgot to "upgrade" javascript couple times, and now JS **is** a kinda standard (ignoring little incompatibilities) and **can** be used for platform-independent processing.

Mozilla plans to replace XUL with Python (because of community size), it will be a start of Python on client: [http://weblogs.mozillazine.org/roadmap/archives/008865.html](http://weblogs.mozillazine.org/roadmap/archives/008865.html)

And we will go from there :-)

---

### Post by Wybiral on 2007-12-06
> **pmasiar said:**
> ... Mozilla plans to replace XUL with Python ...

I got really excited for a minute when I read that, then realized it was dated in 05. I wonder what happened?

---

### Post by pmasiar on 2007-12-06
OK more links deeper from the search:

[tamarin](http://ajaxian.com/archives/mozilla-announces-screaming-iron-action-monkeys-tamarin-in-ie) is IIUC [cross-plaftorm (IE+FF) implementation](http://arstechnica.com/news.ars/post/20071102-major-stakeholders-argue-about-the-future-of-web-scripting.html) of (Iron)Python for browsers. 
"This is big news as it means that Python and Ruby can really be in the browser, for both IE and Firefox" instead of new version of javascript.

I do not follow it in details, but Mozilla plans to implement [IronMonkey](http://wiki.mozilla.org/Tamarin:IronMonkey)

I am waiting for dust to settle. :-)

---

### Post by LaRoza on 2007-12-06
What about SVG? It is a standard language, for vector images, and can do animations.

The browsers, except Opera, need plugins for it, however.

---

### Post by Wybiral on 2007-12-06
> **LaRoza said:**
> What about SVG? It is a standard language, for vector images, and can do animations.

The browsers, except Opera, need plugins for it, however.

I like SVG. It works really well when you use Javascript to control it via DOM (it would be even cooler if Pyhon were controlling it). But it doesn't help with the media issue (audio/video). Also, FF's implementation doesn't support animations yet :( (unless you do it with Javascript)

---

### Post by ThinkBuntu on 2007-12-06
Only problem I can foresee with SVG is browsers being forced to render large vectors. Could be a bear on the processor.

---

### Post by 1337455 10534 on 2007-12-06
By python-independent, I meant that the user doesnt need Python to display that page, but I understand that's a weird demand now.

---

### Post by ThinkBuntu on 2007-12-06
In terms of webpages, everything in the HTML source is dependent on the user's ability to parse it, be it text, an image, or a Flash movie. No way to load Python through source if they don't have some Python plugin for their browser.

---

### Post by pmasiar on 2007-12-06
There is no Python plugin for browsers, so no reason to load it to page. Python is used to generate the page (fill template with data).

---

### Post by ssam on 2007-12-07
i use python on my server.
see [http://www.deviantscience.co.uk/](http://www.deviantscience.co.uk/)
it uses [http://www.cherrypy.org/](http://www.cherrypy.org/) but there are plenty of other ways to use python on the web eg [http://www.modpython.org/](http://www.modpython.org/)

---

### Post by pmasiar on 2007-12-07
For web application, Django was prononnced as simpler and preferred for beginners. TurboGears is more suitable for people who need more control, and more flexibility with used modules.

---

### Post by ThinkBuntu on 2007-12-07
> **pmasiar said:**
> For web application, Django was prononnced as simpler and preferred for beginners. TurboGears is more suitable for people who need more control, and more flexibility with used modules.
I've noticed that this is a mantra of yours, but I think that it is unwise to infer that something that functions in a simple manner is intended for beginners. Now, I have no experience with Django, but from what I've heard, it's as capable as any other framework. For example, although building a large site is simpler with Drupal, it's by no means for beginners.

---

### Post by pmasiar on 2007-12-07
> **ThinkBuntu said:**
> I've noticed that this is a mantra of yours, but I think that it is unwise to infer that something that functions in a simple manner is intended for beginners. Now, I have no experience with Django, but from what I've heard, it's as capable as any other framework. 

I never suggested that Django is inferior to any other web frameworks. But Django **is** simpler (has one way to do it - integration is main goal) and **was** pronounced by Guido for "official" framework. And ppl on TG mailing list repeatedly say they moved from Dj because they preferred other modules and more flexibility (which is not Django's goal). So I am not sure where is the disagreement.

TG and Dj has different goals, different approaches and different target audiences. Is that a problem?

---

