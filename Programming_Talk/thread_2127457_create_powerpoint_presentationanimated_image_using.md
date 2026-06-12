---
title: "create powerpoint presentation/animated image using C code"
date: 2013-03-20
forum: Programming Talk
---

### Post by IAMTubby on 2013-03-20
Hello everyone,
 1 week from today, I am asked to do a "Who Am I" session. You don't have to help me with that :). But I was looking to maybe create atleast one slide or something using code. Like I hardcode a few things I want to convey, and they come up like a powerpoint presentation.

How do you think I should start ? 
1. Should I learn some GL and incorporate in C ?
2. Should I do it over the web ? like web slides using some HTML5 or something?

I would like to do it in C, preferably.

Please advise.
Thanks

---

### Post by MG&amp;TL on 2013-03-20
Just...do..it..in powerpoint! ;)

C doesn't lend itself to quick page creation very easily. Go with HTML and do something over the web.

If you're set on doing it in C, I'd cheat and use the WebKit library to render HTML from a C program.

---

### Post by IAMTubby on 2013-03-20
> **MG&TL said:**
> Just...do..it..in powerpoint! ;)
haha :)

> 
C doesn't lend itself to quick page creation very easily. Go with HTML and do something over the web.

I would have done that, but I would quickly begin to start questioning how it is different from creating a web site with drag and drop. So, don't want to go that way.

> 
If you're set on doing it in C, I'd cheat and use the WebKit library to render HTML from a C program.

I just gave that a quick google search. Will go through in more detail.

But can you tell me what is a good graphics library with lot of good API's and decent documentation ? 

Thanks

---

### Post by MG&amp;TL on 2013-03-20
> I would have done that, but I would quickly begin to start questioning how it is different from creating a web site with drag and drop. So, don't want to go that way.


Make something impressive that cannot be done with drag and drop. But hey, whatever.

> I just gave that a quick google search. Will go through in more detail.

It's just an HTML rendering library. So you could make an extremely small, fast HTML renderer (I wouldn't call it a browser...), and put your page in there.

> But can you tell me what is a good graphics library with lot of good API's and decent documentation ? 

Define 'good' APIs. That's like saying a washing machine is good or bad. It's only good or bad at washing things.

Anyway:

Low-level APIs:

[LIST=1]
[*]OpenGL. The mother of all graphics APIs, this is probably overkill as it does pretty much nothing for you apart from hardware abstraction. Previous versions had some features/restrictions, but now you're pretty much on the hardware, writing your own shaders and data streams. Not going to be a quick project if you hadn't used it before. Documentation and tutorials are quite good though. 
[*]OpenGL wrappers. The only one I know of for C that exposes all the OpenGL functionality and not a a lot else is COGL, which is a GNOME product and comes with the GLib idiosyncrasies (take that as you will...). I don't recall the documentation being wonderful. 
[*]Cairo, which as far as I can tell, provides hardware-accelerated 2D rendering and nothing else. As far as I know, quite a few widget toolkits use cairo, which may be worth looking into. Documentation is definitely not wonderful if you haven't worked with the toolkit before. 
[/LIST]

Medium-level APIs:
[LIST=1]
[*]GTK/Cairo. GTK+ can both draw widgets and expose an API for manual drawing with Cairo. Possibly a good choice, depends on what you want to achieve. 
[*]SDL. Technically you can use this for 3D as well (you can use OpenGL in it), but it's mostly a 2D toolkit if I recall. 
[*]Clutter. 2.5D (look up some tutorials, you'll see what I mean) toolkit, really quite good if you can get used to the GNOME stuff. You can also embed this in GTK+, or put GStreamer (media library) content in clutter actors. 
[/LIST]

High-level APIs:
[LIST=1]
[*]None really. C is not high-level. 
[/LIST]

Hope that helped a little. Apologies to authors/users of libraries if I've been inaccurate or just plain wrong, it's been a while since I used any of this stuff.

---

### Post by nvteighen on 2013-03-21
Use LaTeX? There are packages (Beamer seems to be the most popular one) meant for creating slides that are really really awesome. I can't help you a lot with them, because I haven't had the time to get my hands dirty with it yet, but I've seen how the results look like and they are way better than anything produced by Powerpoint. Take a look on this, for instance: [http://en.wikibooks.org/wiki/LaTeX/Presentations](http://en.wikibooks.org/wiki/LaTeX/Presentations) (and these random slides I found: [http://web.mit.edu/rsi/www/pdfs/beamer-tutorial.pdf](http://web.mit.edu/rsi/www/pdfs/beamer-tutorial.pdf) ).

---

### Post by IAMTubby on 2013-03-21
> **nvteighen said:**
> Use LaTeX? There are packages (Beamer seems to be the most popular one) meant for creating slides that are really really awesome. I can't help you a lot with them, because I haven't had the time to get my hands dirty with it yet, but I've seen how the results look like and they are way better than anything produced by Powerpoint. Take a look on this, for instance: [http://en.wikibooks.org/wiki/LaTeX/Presentations](http://en.wikibooks.org/wiki/LaTeX/Presentations) (and these random slides I found: [http://web.mit.edu/rsi/www/pdfs/beamer-tutorial.pdf](http://web.mit.edu/rsi/www/pdfs/beamer-tutorial.pdf) ).
nvteighen, that is really really cool, and I'll give it a shot in the weekend.
If(and hopefully I will) I do it, I'll try and post a few slides I created here.
I was actually looking to do some C coding and get output, but since I don't have a lot of time in my hands, I think I'll go ahead with LaTeX this time.
Thanks once again.

---

### Post by IAMTubby on 2013-03-21
> **MG&TL said:**
> 
Hope that helped a little. 
Thanks a lot MG&TL for giving me so many options. I now know what to google next.
I might go ahead with LaTeX for lack of time, but will see what I can do with one of the GL's.

---

