---
title: "Flash or JavaScript apps"
date: 2008-02-28
forum: Other OS Talk
---

### Post by xlinuks on 2008-02-28
Hi,
I'm asking about your opinions. I noticed that there seem to be "serious" tries by different companies to create "real" online applications. For instance zoho.com tries to create an online word processor using JavaScript, here's a screenshot:
[http://xlinuks.googlepages.com/zoho.jpeg](http://xlinuks.googlepages.com/zoho.jpeg)
They seem to have done a good job but it looks like JavaScript doesn't offer them the functionality/control they need for it (just use it for a few seconds).
So the question is: why they choose JavaScript instead of Flash, I'm not a flash programmer (a Java one) but I'm pretty sure Flash has built in components like text areas, text fields, checkboxes and so on which offer (much) more flexibility, control and (I'm sure) performance including such cases when you need custom components.
I know why people almost never use Java (since I'm a Java developer), but Flash seems to be a lot more lightweight and installed on practically every machine.
I would appreciate any comment especially from those who participated in creating apps of this type..

---

### Post by akudewan on 2008-02-28
> **xlinuks said:**
> Hi,
I'm asking about your opinions. I noticed that there seem to be "serious" tries by different companies to create "real" online applications. For instance zoho.com tries to create an online word processor using JavaScript, here's a screenshot:
[http://xlinuks.googlepages.com/zoho.jpeg](http://xlinuks.googlepages.com/zoho.jpeg)
They seem to have done a good job but it looks like JavaScript doesn't offer them the functionality/control they need for it (just use it for a few seconds).
So the question is: why they choose JavaScript instead of Flash, I'm not a flash programmer (a Java one) but I'm pretty sure Flash has built in components like text areas, text fields, checkboxes and so on which offer (much) more flexibility, control and (I'm sure) performance including such cases when you need custom components.
I know why people almost never use Java (since I'm a Java developer), but Flash seems to be a lot more lightweight and installed on practically every machine.
I would appreciate any comment especially from those who participated in creating apps of this type..

It must be [AJAX]("http://en.wikipedia.org/wiki/AJAX"), not just JavaScript.

I'm not sure if Flash is technically capable of the kind of processes involved for creating an online office suite. Could it be used to save files on the server? Or download/upload/print files? Probably [Adobe Flex]("http://en.wikipedia.org/wiki/Adobe_Flex") could be used. Not really sure...

I have never been happy with the idea of installing non-free plugins to view/use Internet content. Every modern browser comes equipped with JavaScript, and I'm glad its being used...

---

### Post by SunnyRabbiera on 2008-02-28
java by a mile, as at least sun is making an effort for open source.

---

### Post by xlinuks on 2008-02-28
Well akudewan, of course AJAX must be used too, as well as HTML (XHTML), CSS.. I thought it's obvious..
Flash can talk to the server (it has the built in libraries to use the network, so it can go along without "AJAX", I was interested in it a while ago, but since moved to Linux and since their IDE hasn't been ported to Linux I stayed with Java, now learning C++).
So far the (only) reason I heard not to use Flash, is because Flash is closed source..

---

### Post by LaRoza on 2008-02-28
It is easiest to use the technologies they are using. To use Java, one would have to make an applet that is an entire word processor, Flash is for vector animations.

XHTML and ECMAScript is the best way to do this.

---

### Post by xlinuks on 2008-03-01
Are you kidding... flash is much more capable and flexible than you think.. it's not just animations..(it's as right as saying that Linux can only run LAMP) its capable of doing almost everything a Java applet can do and even more since it supports webcams, something Java nor JavaScript don't support by default. 
btw there are rumors that Adobe is getting more open sourced..

> To use Java, one would have to make an applet that is an entire word processor,
Java can talk to the server just as JavaScript and Flash can or even better, (I noticed you got a bias against Java and perhaps other languages telling anyone to use Python) thus no need to load every time an entire "Java word processor"... that's why I mentioned that comments from ppl who were actually involved in projects of this type I would appreciated pretty much..

---

### Post by LaRoza on 2008-03-01
> **xlinuks said:**
> Are you kidding... flash is much more capable and flexible than you think.. it's not just animations..(it's as right as saying that Linux can only run LAMP) its capable of doing almost everything a Java applet can do and even more since it supports webcams, something Java nor JavaScript don't support by default. 
btw there are rumors that Adobe is getting more open sourced..

Java can talk to the server just as JavaScript and Flash can or even better, (I noticed you got a bias against Java and perhaps other languages telling anyone to use Python) thus no need to load every time an entire "Java word processor"... that's why I mentioned that comments from ppl who were actually involved in projects of this type I would appreciated pretty much..

I don't have a bias against Java, I just think for a web based app, using the simplest and most widely tools makes sense.

Now, it may make sense to use Java on the server, or for a local app.

Flash is more capable than I stated, but it is primarily for vector animations.

The simplest, cross platform, and least restrictive option would be to not use Java and Flash because they are not integral parts of the browser and do not degrade gracefully.

I never brought up Python, I was just pointing out the simplicity of the current approach and why it was likely prefered. (Since you brought up Python, it can be used on the Java platform, as can Ruby).

As a web developer, I see the reason why they use the methods they do.

[quote="OP"]
They seem to have done a good job but it looks like JavaScript doesn't offer them the functionality/control they need for it (just use it for a few seconds).
So the question is: why they choose JavaScript instead of Flash, 
[/quote]

I answered that, from a web developer's point of view (which seems to be important in this matter). You accused me of a bias, and recommending Python for everything. Sorry for answering the question...

---

### Post by init1 on 2008-03-02
Javascript definitely has the functionality needed for web apps. Google Docs for example uses a Javascript interface. Also neither the software for developing nor the software for viewing Flash is open source (there's Gnash, but that's not as usable as the official Flash player yet).  
[http://docs.google.com](http://docs.google.com)

---

