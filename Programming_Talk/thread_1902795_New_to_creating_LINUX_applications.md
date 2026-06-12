---
title: "New to creating LINUX applications"
date: 2011-12-31
forum: Programming Talk
---

### Post by gambiauser on 2011-12-31
How do I create a application which just show off a single website. Because I want to have an own application to showoff [http://sn131w.snt131.mail.live.com/Handlers/WebIM.mvc](http://sn131w.snt131.mail.live.com/Handlers/WebIM.mvc) because I can't find a good Windows Live Messenger app so I want it like this.

Because WLM only can import all my contacts, I know its weird but it does.. :(

So:

[LIST]
[*]One application
[*]One page
[*][http://sn131w.snt131.mail.live.com/Handlers/WebIM.mvc](http://sn131w.snt131.mail.live.com/Handlers/WebIM.mvc)
[/LIST]
Thankyou!

---

### Post by lisati on 2011-12-31
*Thread moved to **Programming Talk**.*
(Thread also renamed. Linux != Unix)

---

### Post by gambiauser on 2012-01-01
Okay thanks? :) But, anyone?

---

### Post by Paddy Landau on 2012-01-01
Are you asking how to program an application that runs on a server, and to create a website to drive the application? If so, that's not a small question -- you need to be a programmer and a website designer.

---

### Post by gambiauser on 2012-01-02
I want an program which just show off a webpage, thats all.

---

### Post by kaivalagi on 2012-01-02
> **gambiauser said:**
> I want an program which just show off a webpage, thats all.
Taking this literally it sounds like you want a browser :lol:

I am guessing from this all you either want:

[COLOR="red"][SIZE="4"]A)[/SIZE][/COLOR] A web server to render a web site to a browser?

If so install Apache and do some reading here: [http://wiki.apache.org/httpd/](http://wiki.apache.org/httpd/)

As for creating the content there are a lot of options, e.g.:
[LIST]
[*]Static pages using pure HTML and Javascript
[*]CMS based solution using existing frameworks such as Drupal, Joomla, Django etc etc
[*]Own server side driven site using anything from PHP to Java
[/LIST]

[COLOR="Red"][SIZE="4"]B)[/SIZE][/COLOR] An application that renders an existing URL without all the extras you get with a browser? In which case there are a number of languages to use and a number of support libraries for http browsing, if new I would suggest using Python and webkit...you couldn't go much wrong with this as a starting point: [http://ardoris.wordpress.com/2009/04/26/a-browser-in-14-lines-using-python-and-webkit/](http://ardoris.wordpress.com/2009/04/26/a-browser-in-14-lines-using-python-and-webkit/)
e.g.
```
#!/usr/bin/env python
import gtk
import webkit
import gobject
 
gobject.threads_init()
win = gtk.Window()
browser = webkit.WebView()
browser.open("http://sn131w.snt131.mail.live.com/Handlers/WebIM.mvc")
win.add(browser)
win.show_all()
 
gtk.main()
```

Save it as WebKitBrowser.py and run using "python2 WebKitBrowser.py", and make sure you have PyWebKitGTK installed (assuming that's what it's called in Ubuntu land). Example screenshot attached.

To be honest you seem to be someone who is very new to all this, in which case you need to do a LOT of reading...

Good luck

---

### Post by hansdown on 2012-01-02
> **gambiauser said:**
> How do I create a application which just show off a single website. Because I want to have an own application to showoff [http://sn131w.snt131.mail.live.com/Handlers/WebIM.mvc](http://sn131w.snt131.mail.live.com/Handlers/WebIM.mvc) because I can't find a good Windows Live Messenger app so I want it like this.

Because WLM only can import all my contacts, I know its weird but it does.. :(

So:

[LIST]
[*]One application
[*]One page
[*][http://sn131w.snt131.mail.live.com/Handlers/WebIM.mvc](http://sn131w.snt131.mail.live.com/Handlers/WebIM.mvc)
[/LIST]
Thankyou!

Is this the website you wish to "showoff"?

You could go on a forum, and do that...wait, you already did.

My mistake.

---

### Post by fluca1978 on 2012-01-02
Using a browser locked to a single web page? Like setting a fake proxy to all pages except the one you want, or using a kiosk?

---

### Post by gambiauser on 2012-01-02
> **fluca1978 said:**
> Using a browser locked to a single web page? Like setting a fake proxy to all pages except the one you want, or using a kiosk?

Noooo I just want to have an Application for MSN and I don't like the other interfaces and stuff + contacts doing weird stuffs. So I want WLM web :)

---

### Post by gambiauser on 2012-01-02
> **kaivalagi said:**
> To be honest you seem to be someone who is very new to all this, in which case you need to do a LOT of reading...

Well it's true, I met Ubuntu like.. 29 december? And I am working on LINUX.. Because I think its nice to work with Ubuntu and Windows you know what I mean? I want to know how things work in both OS's.

Windows = easy, a app., click install and it runs, but Ubuntu not always.. and I want to discover it :)

---

### Post by lisati on 2012-01-02
> **gambiauser said:**
> Noooo I just want to have an Application for MSN and I don't like the other interfaces and stuff + contacts doing weird stuffs. So I want WLM web :)

So you're asking if someone knows of such an app, not for help creating one?

---

### Post by gambiauser on 2012-01-02
> **kaivalagi said:**
> Save it as WebKitBrowser.py and run using "python2 WebKitBrowser.py", and make sure you have PyWebKitGTK installed (assuming that's what it's called in Ubuntu land). Example screenshot attached.

I've installed those:
[LIST]
[*]WebKit/Gtk Python bindings
[*]WebKit/Gtk Python bindings: development files
[*]WebKit/JavaScriptCore Python bindings
[/LIST] 

And it seems to work! big thanks to you Kaivalagi! 

[IMG]http://a.yfrog.com/img736/7915/wb0k.png[/IMG]

---

### Post by gambiauser on 2012-01-02
Thought it worked :'( I only can access my mail If I want to open the msn then the page freezes or something, doesnt open msn..

---

### Post by Paddy Landau on 2012-01-02
@gambiauser, I think you are getting too complicated. You want to use Hotmail but without Hotmail's functionality. That's going to be difficult!

You could try using Thunderbird and setting up the account to access Hotmail via IMAP (if that is supported; I don't know whether or not it is).

---

