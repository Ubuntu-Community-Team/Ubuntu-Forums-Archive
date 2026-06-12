---
title: "Linux HTA"
date: 2006-09-24
forum: Programming Talk
---

### Post by Onomatopoetikon on 2006-09-24
Heyas

Is there a Linux version of MS-HTA, (HTML Applications)?

The ability to write client apps. in DHTML, CSS and Javascript, which will run under the security of the logged in user.. DB access, fileaccess and such.

I know about PhP and Tck/Tcl etc., (I know it's there), but I really like Javascript :)

Thanks in advance.

---

### Post by Brunellus on 2006-09-24
I am moving this to the programming forum in the hopes that someone there will have an answer.

---

### Post by toojays on 2006-09-25
I don't know the exact answer, but there are a couple of avenues of inquiry you could make: 

* [XUL](http://www.mozilla.org/projects/xul/) is Mozilla's application platform, based on JavaScript and XML.

* [KJSEmbed](http://xmelegance.org/kjsembed/) is a JavaScript binding for KDE.

Hopefully someone on one of the mailing lists associated with these projects will be able to tell you if their project can be used to do what you want.

I have been toying with a project along similar lines, using Firefox for the frontend, but with a small Scheme script acting as the webserver. This script (typically running on the local host) will carry out the tasks which require more access than a the standard browser environment allows. The majority of the application will be written in JavaScript and be executed in the browser. Communication between the browser and the server is be AJAX style.

Please let us know here if your inquiries turn up something useful.

---

### Post by Onomatopoetikon on 2006-09-29
XUL seems to be a very cool platform, but it sorely lacks the one feature I really like about HTAs; the smooth simpleness. Keeping everything within good 'ole traditional DHTML and JS, without packing stuff into a new syntax.

I suppose the lack of COM would severely cripple the approach anyway, since that is what allow HTAs to reach outside the boundaries of the browser DOM.

Not too fond of KDE, so haven't tried that approach. 

Anyway, it was just a thing I missed from Windows, not enough to abandon Linux for, but it could've been great to have. Think I'll go with Mono, seeing as how I dragged some .NET experience over from MS too ;)

Thanks for the reply!

---

