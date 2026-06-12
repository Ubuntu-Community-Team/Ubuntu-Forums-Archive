---
title: "need programming advice"
date: 2007-09-27
forum: Programming Talk
---

### Post by cubytes on 2007-09-27
I have a few questions

I have made some rough sketches and desings for a simple yet elegant yet aesthetically pleasing RSS reader client thingy!! I have a good idea about how it will look, work and function, but I dont know what programming language I should use.......................

I want to make it cross platform
light weight
and fast

I want it to look flashy
have beveled edges
with a sort of 3D translucent feel
and have a kind of mini cover flow for RSS subscription logos

should I use C++ with a cut and paste of Firefox or other open source RSS clients or should I make it from scratch with some other language, or should I just basically use flash running on adobe air to achieve the lightweight fast functionality!!

what would you use or what would use suggest?

I promise I will listen and take your advice into consideration!!!

---

### Post by slavik on 2007-09-28
as far as the way you want it to look, it could be tricky, unless you are doing something like xmms/winamp/qcd that doesn't use system theme and has it's own.

other than that, lots of people will say Python, I will say Perl ... but you can also use C/C++/Java.

If you go with Python/Perl/C, I would recommend GTK, for C++ I would recommend QT4, and for Java, swing

---

### Post by cubytes on 2007-09-28
thanks for the advice

why perl? what are the benefits for using perl?

and to be honest I am having doubts about my whole design, so unfortunately I am back to the drawing board.

As for the idea it still seems like a mix between iTunes and google reader, but I think I might go social, so therefor now it will be a mix between iTunes, google and digg, which sheds a whole new light to the situation

why is python so popular what would be the benefit for using python to create this social RSS reader?

thank you for your time!!!

---

### Post by pmasiar on 2007-09-28
Beauty is a skin deep. Do it in any language, when (and if) it will work correctly, you can start worrying about how it looks.

And of course the more cross-platform it is, the less it uses from any specific platforms. Look into wxWidgets, and wxPython is you decide to go Python way.

---

### Post by Wybiral on 2007-09-28
Whatever language you do it in, to get that cover-flow type 3d effect, I would use OpenGL (which is a 3d api).

GTK has an OpenGL width (GtkGlExt) that you can use in your gtk app.

Python has bindings for both Gtk AND the GtkGL extension.

I will warn you that 3d graphics are a pretty complex area of programming... Especially with a GUI (like GTK).

You could use OpenGL on its own, but that would require even more work with displaying the feeds (too much work, in fact).

I would start with a simple non-coverflow feed reader. Then see about adding it after that part is done (so you'll at-least have a functional program to work with).

Nice to see you're finally coming around to programming!

EDIT:

For the actual feed reader... Python has plenty of libraries for reading from the web. It also has XML parsing libraries to parse the feeds.

---

### Post by cubytes on 2007-09-28
ok so python is good for gathering information from the web (very nice)

you say the cover flow will be difficult, so I might do just a 2D filmstrip instead, just until I get the rest to work fluently!!

I am seriously considering in making it social sort of like digg.......any suggestions for what I would have to use to make it social? would I have to use php or some kind of  database? 

another thing I am considering is a new view for RSS feeds I am still working on this of course, but I plan to display thumbs of the web-pages that the RSS feeds is associated with...... any thoughts about this idea?

would python be able to achieve this kind of functionality?

---

### Post by cubytes on 2007-09-29
I am not ignoring you guys but my post are on moderation, just in case your wondering about the delay. 

I have finally revised my original design enough to where I am now once again confident it will be a huge success. I have made it passed the rough drafts and into the first final cut and by using that as a guide I have pretty much mapped out the entire application by drawing story-boards.

 In a few days I will be ready to start writing code, or rather start experimenting with writing code until I am ready to actually write code. I have tried a few times in the past and I got no where in a hurry, I guess it takes full commitment and a LOT of patience and patience isn't one of my best qualities!!

 I only wish I knew how to program as much as you guys, I would most likely be rich or very successful by now. Another reason I have failed in the past is because of the daunting nature of my ideas and concepts, I usually take a car and try and make it into a boat and a plane and a time machine, metaphorically speaking, but this application is really simple because after all it is JUST a social RSS client and that is all it WILL be.

I am still indecisive about what  language to use, I need something that has good vector window properties, something that can handle a cover flow view, something that can handle and manipulate rich web-site thumbs, and something that can retrieve and send a lot of data across the internet.

Their will most likely need to be web servers, with all kinds of web services and possibly php or some sort of database to facilitate the social aspect, and last but not least I need something that can facilitate IM and comment or thread posting and possibly file sharing or embedding pictures and video in the future, because after all this will be a social RSS client that will be totally separate from the web browser.

I know I am CRAZY, who would ever use a social RSS reader, but then again who would ever use a social search engine, and there is already a couple of those out on the internet right now, there is one thing I know and that is people love social software, plain and simple!!

any suggestions? or if you don't mind can you point me in the right direction? and where should I start?

thanks for all of your help I truly appreciate it

---

### Post by cubytes on 2007-09-29
oh and I almost forgot.................

this application will be called "Zoom"

---

