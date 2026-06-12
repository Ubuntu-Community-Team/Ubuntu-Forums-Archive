---
title: "JavaScript/greasemonkey help"
date: 2011-01-03
forum: Programming Talk
---

### Post by cela on 2011-01-03
I was wondering how I could do several things in JavaScript:
1. Detect the browser viewing the page
2. Use a different stylesheet for mobile browsers.
3. Create a greasemonkey script to do this to sites not optimized for mobile devices

I know mobile devices don't support greasemonkey, at least not yet, but I would appreciate some help in doing those things.  I already know some JavaScript, but only things that aren't JavaScript specific.  I don't know much about interacting with the browser yet.  Thanks!!

cela0811

(Yes, I am cela0811.  I was having login troubles.  It wouldn't accept my email when I tried to reset my password, and told me I was wrong when I said that the average human has 2 ears.  Ugh.)

---

### Post by odyniec on 2011-01-03
You'll find lots of information on the web that will get you started.

> 1. Detect the browser viewing the page

First Google result for "javascript mobile browser detection": [http://www.hand-interactive.com/resources/detect-mobile-javascript.htm](http://www.hand-interactive.com/resources/detect-mobile-javascript.htm)

> 2. Use a different stylesheet for mobile browsers.

One of the results for "javascript change stylesheet" is a good A List Apart article on this subject: [http://www.alistapart.com/articles/alternate/](http://www.alistapart.com/articles/alternate/). It's a bit old, but should be helpful.

> 3. Create a greasemonkey script to do this to sites not optimized for mobile devices

You can start at [http://wiki.greasespot.net/Main_Page](http://wiki.greasespot.net/Main_Page), there should be some links to Greasemonkey tutorials. You can also learn by example by browsing the scripts at [http://userscripts.org/](http://userscripts.org/).

There, I did the googling for you.

> I know mobile devices don't support greasemonkey, at least not yet, but I would appreciate some help in doing those things.

Since you point that out, I assume you have a reason to do it this way. The standard method of providing a different website layout for mobile browsers is to detect the browser with a piece of server code (or JavaScript), and then redirect the client to the mobile version of the site. There's even a generator of redirection scripts at [http://detectmobilebrowser.com/](http://detectmobilebrowser.com/).

---

