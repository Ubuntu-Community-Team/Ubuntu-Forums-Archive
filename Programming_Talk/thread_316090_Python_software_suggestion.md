---
title: "Python software suggestion?"
date: 2006-12-10
forum: Programming Talk
---

### Post by Vinze on 2006-12-10
Hey, I'm learning Python, and the best way for me to learn is through practise and trial and error. 

Does anyone have a suggestion for a small but useful program I could make? Thanks in advance.

---

### Post by gummibaerchen on 2006-12-10
For GUI also?
Then do an analog clock :)

---

### Post by DaveBorealis on 2006-12-10
> **Vinze said:**
> 
Does anyone have a suggestion for a small but useful program I could make?

Hello,

What are your interests?  Myself, because I like playing with data, I wrote a web scraper a few weeks ago (I'm also just learning Python) that grabed the web server info for several thousand sites.  On my P4 3GHz with a fast connection I made a http connection with 10,000 supposedly rogue sites in just under a couple hours.  (Well...*I* thought it was fun!)  When I get a little free time again I'm feeding it into a MySQL database, which I can access via Python.

Dave

---

### Post by pmasiar on 2006-12-10
You are right, best way of learning programming is doing it. But one thing what we *don't need* is yet another half-baked unmaintained tool with bad design and no user community.

Remember from history lessons: 500 years ago before industrial revolution, to become a craftsman you first spend *years* working with a master, learning from him. Same in programming: join a project you are interested in, ask for simple bug to fix and ask for help doing it. Learn by reading source code of masters how great tools are designed, how to manage project changes, write documentation and support your users. Research says it takes 10 years to become a guru in one technology. You may not even be interested to go that far: you might be happy to become confident and competent python programmer - and move on to become competent in yet another technology. Or make libraries and python bindings for specific tools. 

Get pygame, find a game with source and try add some feature. Or pick editor of choice and try fixing some bugs. Learn inner design of a tool you want to use. MoinMoin wiki, TRAC bug tracker, TurboGears web framework will be happy someone will pitch in and help fixing bugs or writing documentation.

Please don't start new project until you are ready to become a master.

---

### Post by gummibaerchen on 2006-12-10
LOL :) I don't think he wanted to create some big app.

I thought he just wanted to get used to Python programming.

Helping in another Community for a special program could be some hard.

Try what you need. I for example will create something for calculating things in Triangles.

This is Python (object oriented), GTK+ and Maths.
No one really needs this (graphic Calculators are standard today), but it's just for learning to do it myself.

Some Python program I have found, which is not to big, but yet useful is gPodder. Maybe I will contribute there.

---

### Post by studiesrule on 2006-12-10
actually I've been dying to do exactly what psmasair said, but I've always thought it'd be too hard (I hardly know much of the language, but python's easy to read an comprehend)
your words have inspired me to try it out.

---

### Post by pmasiar on 2006-12-11
[Learning to write a GUI app]("http://www.progbox.co.uk/wordpress/?p=183"). Video: building simple GUI applications with python, GTK and glade. Enjoy.

---

### Post by Vinze on 2006-12-11
The problem with joining an existing project is [LIST=1]
[*]When looking for "help wanted" they always want experienced Python programmers, and
[*]The other developer would probably have to help me a lot
[/LIST]

I actually would like to build a GTK app, I'm trying to build yet another media player, not sure if I'll manage though.

---

### Post by pmasiar on 2006-12-11
> **Vinze said:**
> The problem with joining an existing project is [LIST=1]
[*]When looking for "help wanted" they always want experienced Python programmers, and
[*]The other developer would probably have to help me a lot
[/LIST]

I actually would like to build a GTK app, I'm trying to build yet another media player, not sure if I'll manage though.

Both point are obvious. You need to read up at least one book - which one do you use? Write something for your own use first. 

When writing applications, command line text only is the simplest. More complicated, but still simpler that full GUI, is web-based application (once you set up web server), IMHO. Web App  has simpler interaction: read your parameters, print resulting page out, done. GUI is the most complicated, because your program need to respond to different events fired in user-defined order. You may consider building traininig apps in order of increased complexity. YMMV.

To program something interactive on desktop, try to write a game using pygame. Or add a feature to existing game. Half-working game has still better chance someone will finish it, that half-working media player.

Yes, I need to get up and create learnPYdia wiki I am thinking about for a long time. I know. Hope having it before Xmass.

---

### Post by Vinze on 2006-12-11
> **pmasiar said:**
> Both point are obvious. You need to read up at least one book - which one do you use? Write something for your own use first. 

When writing applications, command line text only is the simplest. More complicated, but still simpler that full GUI, is web-based application (once you set up web server), IMHO. Web App  has simpler interaction: read your parameters, print resulting page out, done. GUI is the most complicated, because your program need to respond to different events fired in user-defined order. You may consider building traininig apps in order of increased complexity. YMMV.

To program something interactive on desktop, try to write a game using pygame. Or add a feature to existing game. Half-working game has still better chance someone will finish it, that half-working media player.

Yes, I need to get up and create learnPYdia wiki I am thinking about for a long time. I know. Hope having it before Xmass.

I already know PHP, I wanted to learn Python for programming desktop apps if ever needed. If the media player will be half-working I'll just not publish it, it's a simple as that ;)

The wiki's a good idea, the name I like less :P

---

### Post by gummibaerchen on 2006-12-11
> **pmasiar said:**
> Yes, I need to get up and create learnPYdia wiki I am thinking about for a long time. I know. Hope having it before Xmass.

That's sounds really cool :)

Vinze: I'm sure you MediaPlayer will work, as long as you don't try to reach standards as amaroK, then Python may be to slow.

---

### Post by Vinze on 2006-12-12
> **gummibaerchen said:**
> That's sounds really cool :)

Vinze: I'm sure you MediaPlayer will work, as long as you don't try to reach standards as amaroK, then Python may be to slow.

Well, firstly, I don't think I'll soon reach those standards ;), secondly, it probably won't be slower than AmaroK on my GTK system and thirdly [Exaile](http://www.exaile.org/) does quite well IMHO.

---

### Post by pmasiar on 2006-12-14
i just suggested [free software activist project]("http://ubuntuforums.org/showpost.php?p=1885542&postcount=3") - you may want to look at it too.

---

### Post by Vinze on 2006-12-14
> **pmasiar said:**
> i just suggested [free software activist project]("http://ubuntuforums.org/showpost.php?p=1885542&postcount=3") - you may want to look at it too.

I agree it is important, but I would need **a lot** of help. If you would be willing to give it to me, bring it on :D 

No deadlines though, I'm also busy on a PHP project still.

---

### Post by gummibaerchen on 2006-12-14
> **pmasiar said:**
> i just suggested [free software activist project]("http://ubuntuforums.org/showpost.php?p=1885542&postcount=3") - you may want to look at it too.


Sounds technically not to bad.

---

### Post by pmasiar on 2006-12-14
Absolutely. You will get all the help I can gather, and first dip into learnPYdia as a bonus. :-)

---

### Post by engla on 2006-12-14
Find two really cool bindings/libraries that do something great, and combine those to make something no one ever thought of!

Uh, what? I dunno. Perhaps: RSS feeds and graphs -- I'd like a cool alternate representation of RSS feeds that is not a list of titles -- perhaps a graph, picture, map?

Find a library for PDF manipulations and write a PDF stiching tool -- I have always wanted something like that, to take ranges of pages from one pdf and add together with a range from a 2nd, 3rd pdf and then produce 2x1-paginated pdfs from that etc.


EDIT: I forgot I actually keep a collection of these ideas. Here is a cut from a personal list I keep of ideas:

* Doc reader for reading /usr/share/doc files!
* QCDesktop for linux? Probably unpossible
* Free-form RSS reader that is more fun..  
[INDENT]
  * Some kind of "alternative representation" of articles
  * Think about circular "pie" arrangements, or trees/graphs
  * Visualize outbound links as shaded nodes?
  * Relation to liferea? Plugins?[/INDENT]

* Icon manager!
  [INDENT]* Manager for custom folder icons in nautilus[/INDENT]
* Photo lightboard? See lowfat (but simpler)
* man page maker
* Noise, White, Pink whatever noise
* Yet another desktop organizer
  [INDENT]* Outliner, recent documents (cf. zim)
  * Autosave 
  * Can refer and use local documents 
  * Uses markdown or wiki or plaintext
  * Exports to everything[/INDENT]
* Contacts manager with semantic web perspective
  [INDENT]* Keep contacts as FOAF files.
  * Update against a URL, cache locally
  * Import/export abilities[/INDENT]
* A Shell-script Automator (cf. Apple app)
  [INDENT]* Know shell scripts and systematically encapsulate them -- implement categorization by templates that are modified, flags like takes_many_files, text_pipe (text in/out-piped) etc. 
  * Allows user to Put together "sentences"
  * Concepts of input and output as files or utf8 text (and more?)
  * Think over the relation to shell scripts[/INDENT]
* PDF-Lab. Split, concatenate, transform pdf files in gnome
  [INDENT]* With the help of tools like pdfjam, pdfnup, pdfjoin[/INDENT]
* Earth -- google earth copy/gaia copy with wwd data and python-opengl surface for earth drawing

---

### Post by tomchuk on 2006-12-15
Get a cheap webcam, install python-opencv and have at it. Computer vision is a blast. Get your hands dirty digging around in the data structures, experimenting with the algorithms, etc. GUI apps are a dime a dozen, replacing peoples faces with big yellow smileys in realtime video is priceless.

---

### Post by pmasiar on 2006-12-18
wooohooo ! learnPYdia (beta) is up and running, [http://learnpydia.pbwiki.com/](http://learnpydia.pbwiki.com/) almost dozen  tasks to solve for beginners and advanced programmers are there. No GUI needed!

If you have more ideas for tasks, PM me and I'll post it there

---

