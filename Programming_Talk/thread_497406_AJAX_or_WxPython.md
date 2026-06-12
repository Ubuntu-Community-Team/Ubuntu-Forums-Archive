---
title: "AJAX or WxPython?"
date: 2007-07-10
forum: Programming Talk
---

### Post by llanitedave on 2007-07-10
I'm starting to conceptualize a stand-alone, self-contained, single-user application that will have some simple SQLite database interactions.  It would be text heavy, and include images and calculations, but nothing really challenging.

Right now I'm undecided about whether to create the GUI in Javascript, and make data retrievals through AJAX, or to create a GUI using WxWidgets with a Python codebase.

I've not gone much further than a few basic layouts in WxWidgets, but it looks pretty learnable, and I've done some Javascript interfaces.

Which approach would be easiest, and result in the nicest looking, most consistently cross-platform interface screens?

Sometimes I'm leaning towards Javascript, sometimes Python.  I'm really starting to annoy myself.

Any advice?

---

### Post by loell on 2007-07-10
go for AJAX with django or turbogears

---

### Post by constrictor on 2007-07-10
I've never been a big fan of wx, if you have to do it outside of the browser i'd suggest GTK otherwise AJAX

---

### Post by pmasiar on 2007-07-10
It is *not* about nice screens - desktop vs. web-based app is very different kind of applications. You need to think about:

- do you have server? if not, desktop is the only option
- multiuser? web based is simpler
- how complicated is interactivity? Ajax is less flexible
- delays? web apps are prone to delay/disconnect
- your learning goals? desktop vs web app are different skills. Using different tools to build GUI, different approach to test/debug.

And for sure ppl can suggest more questions you need to ask before giving you any meaningful (non-random) advice.

---

### Post by llanitedave on 2007-07-10
> **pmasiar said:**
> It is *not* about nice screens - desktop vs. web-based app is very different kind of applications. You need to think about:

- do you have server? if not, desktop is the only option
- multiuser? web based is simpler
- how complicated is interactivity? Ajax is less flexible
- delays? web apps are prone to delay/disconnect
- your learning goals? desktop vs web app are different skills. Using different tools to build GUI, different approach to test/debug.

And for sure ppl can suggest more questions you need to ask before giving you any meaningful (non-random) advice.

It would be a single-user, desktop app.  But that's part of the question.  Would it need to have a server to use a browser interface?  Or, as was suggested previously, if I use Turbogears as the engine, would there even have to be a web server involved?  Or can I call an SQLite database directly from the Python code and send it to the browser?

Part of the question has to do with ease of development, and part has to do with ease of distribution.

---

### Post by pmasiar on 2007-07-10
> **llanitedave said:**
> It would be a single-user, desktop app.  


then why AJAX? AJAX is for web apps (running in browser), to make web page more interactive.

> But that's part of the question.  

This is question you need to ask yourself - what exactly do you want? Including: what do you want to learn? Looks to me you you are not sure yet. AJAX vs wxPython does not make sense - they are different technologies, used in different areas.

> Would it need to have a server to use a browser interface?  Or, as was suggested previously, if I use Turbogears as the engine, would there even have to be a web server involved? 

Absolutely, web apps run over the web :-) 

But question is: does your app *need* web server? Or will it run on desktop, without browser?

> Or can I call an SQLite database directly from the Python code and send it to the browser?

Yes. You can do it manually (using SQLite API), or use ORM (object-relation mapper) - TurboGears makes it simple.

> Part of the question has to do with ease of development, and part has to do with ease of distribution.

Big part is what the goals of apps are, how you want it to work. First select that, *then* select platform and language.

---

### Post by loell on 2007-07-10
you could run the web based app, **"locally"**
since all operting systems now have browser, it is still pretty much a single app , with the option to run the program remotely in the future, so go with web based apps. less coding , plus you can concentrate on what your program can do.

> Part of the question has to do with ease of development, and part has to do with ease of distribution.

all these web frameworks are now portable...

---

### Post by llanitedave on 2007-07-10
From the user's point of view, it wouldn't make much difference whether it was a web app or not -- it would definitely reside locally on the user's machine, and they could run it offline.  The browser would be simply an interface convenience.

If I use a GUI such as WxPython, then essentially python is the only language I need. If I use the browser as my GUI, then I would need Javascript and the DOM.  That sounds more complex when I write it out like that, but I'm not really sure if it is.

I guess the real question is shaping up to be, how *compelling* is having the convenience of a browser interface for users?  I know I like to be able to do many tasks from different tabs on my browser, and the idea of being able to run standalone applications from a browser tab is a tempting one for me.

But if it turns out to be two or three times as much work to implement, I'm not sure it's worth it.

---

