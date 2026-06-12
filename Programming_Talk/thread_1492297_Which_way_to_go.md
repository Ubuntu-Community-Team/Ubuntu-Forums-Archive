---
title: "Which way to go"
date: 2010-05-24
forum: Programming Talk
---

### Post by Experimental on 2010-05-24
I want to improve myself in desktop programming i'm learning c/c++ and I'm not going to any school of software engineering. Which way do you advice me to go  ? 

for ex:

c/c++ -> c# / Java -> php/asp/etc -> sql

---

### Post by Tony Flury on 2010-05-24
depends what you want to learn.

If you want to turn around useful programs quickly - and get a feel for high level algorithms and concepts without having to worry about the minutae of memory allocation, pointers etc - why not start with python ? SQL is a good tool in the armory if you intend to do useful stuff.

---

### Post by Experimental on 2010-05-24
Yeah I'm thinking about pyhton too . I just I think I don't know what languages are needed. for example in web design/programming you can say. you have html and you need css for styling and a client side language javascript and a server side language asp or php . What's it like for software programming ? 

And another question;

There are lots of websites selling users psd , wordpress etc. templates, codes for ajax php etc. etc. . Are there any websites that sell users softwares ?

---

### Post by era86 on 2010-05-24
If you're most interested in web development, you might want to learn languages that are good with string parsing and such.  Popular web languages are Python, PHP, Groovy, Ruby, etc.  These are loosely typed interpretive languages.  I find C useful when writing software that directly communicates with hardware.

---

### Post by trent.josephsen on 2010-05-24
Your question isn't totally clear, but I'll try to answer it anyway.

I think you're interested in learning what belongs in the toolchest of a desktop application programmer, as opposed to a systems programmer or a Web programmer.  In other words, what would be a typical toolset for writing desktop applications?

If this is indeed your question, then unfortunately the answer is still "it depends".  It depends on the platform you're developing for, the libraries you and your users will have available, the level of control you want to have over the appearance of your program, and what underlying tasks you want to do.  There are enough debates over Qt vs. Gtk+ without even getting into other topics or suggesting other frameworks.  Bare minimum, you'll want a language you're fairly comfortable with and a GUI toolkit.  Languages might be C, C++, Java, or Python, among others.  GUI toolkits could be Gtk+, Qt, Swing (Java only), Tk, or wxWidgets, among others, or you could use something like SDL to get lower level control.

You'll need other libraries that may or may not come with your language of choice; it depends on what you're doing and what other tools you use.  Regular expressions, for instance, are particularly useful in many applications, but require non-standard libraries for C and C++.  Database engines are another sticking point.

If you take my advice, you'll invest in learning something of most of these tools.  Start with, say, Python, and when you become comfortable with just plain Python, then move on to C and its lower level stuff.  Get some Perl under your belt.  Don't start with GUIs until you are pretty proficient with programming in general (I might be preaching to the choir here; don't know your experience level).

But some practical and application-agnostic things to know about might be revision control, documentation practices, makefiles, and using the command line.  I suggest you gain competence with these things before trying to build anything large (more than a few hundred lines).

---

### Post by Experimental on 2010-05-25
I want to do pure desktop programs or programs that can lets say for example an image uploader that can upload to imageshack or elsewhere. Also I don't want to learn too many languages:P 3-4 maybe 5 . There are too many languages and a lot of will come. I want a sector that stays in 3-4 or maybe 5 languages if you know what i mean

---

### Post by nvteighen on 2010-05-25
> **Experimental said:**
> I want to do pure desktop programs or programs that can lets say for example an image uploader that can upload to imageshack or elsewhere. Also I don't want to learn too many languages:P 3-4 maybe 5 . There are too many languages and a lot of will come. I want a sector that stays in 3-4 or maybe 5 languages if you know what i mean

Isn't that just limiting yourself? I'm a hobbyist and just can't understand how someone could think of just learning a fixed number of languages, even if he doesn't use them all.

Ok, now, what do you mean by "pure desktop programs"? GUI programs? Programs expected to be used in a desktop computer (that would include CLI stuff as well)?

As you tell us, you're learning C and/or C++ ("C/C++" isn't a language). Python would be a great complement that would give you a higher-level picture of programming. I did it that way, starting at C and then going to Python and it fit well... ok, I was sort of a "false beginner" because of BASIC coding in my childhood, but nevertheless...

What I want you to know is that in any area of knowledge, more knowledge doesn't hurt. It brings up experience, new techniques, and the most important: new points of views on the same problems. Programming languages not only are tools to code, they also reflect the designers' approaches to fundamental programming issues.

---

### Post by Experimental on 2010-05-25
I think that knowing 2-3 languages at grandmaster level is better than knowing 5-6 languages average level

---

### Post by nvteighen on 2010-05-25
> **Experimental said:**
> I think that knowing 2-3 languages at grandmaster level is better than knowing 5-6 languages average level

That's obvious. The thing is that you'll soon see that lots of languages are very similar and learning them (yes, learning them, not just "knowing about them") will be increasingly easier and faster the more languages you already know.

---

### Post by Experimental on 2010-05-25
I see your point . I got another question .Which way should I go to become a freelance programmer. And maybe someone will say again it depends but I don't know the answer of it :P . I just try to find my way from all the possible ways. I just want to know all the ways

---

### Post by trent.josephsen on 2010-05-25
> **Experimental said:**
> I see your point . I got another question .Which way should I go to become a freelance programmer. And maybe someone will say again it depends but I don't know the answer of it :P . I just try to find my way from all the possible ways. I just want to know all the ways

Hit the streets.  Write up a resume and get a list of all the software shops and industries that employ programmers in your area.  Send them each a nice letter saying, "I'm looking to get into this business, these are my skills, and I'm wondering what additional skills I need to be a programmer for your company."  Ask your friends and family who work in software development.  Ask professors at your local college or technical school.  Get a lot of opinions.  Some of them you'll be able to eliminate as too-specific or not in your area of interest (COBOL, perhaps), but of those remaining you should discern some trends.  None of us can tell you what skills are in demand in your region or area of interest better than you can.  But it will take a lot of work:  not only finding out what skills you need, but learning those skills, practicing them, and keeping abreast of the trends -- especially, or so I imagine, as a freelancer.

---

### Post by hyperAura on 2010-05-25
what do you guys think about Java as the first language after C/C++?

---

### Post by trent.josephsen on 2010-05-25
> **hyperAura said:**
> what do you guys think about Java as the first language after C/C++?

Not much.  Especially if you don't know the difference between C and C++.

---

### Post by simeon87 on 2010-05-25
> **hyperAura said:**
> what do you guys think about Java as the first language after C/C++?

If it furthers your goals that you have for yourself as a programmer, then go for it.

---

### Post by linuxisfree on 2010-05-25
> **Experimental said:**
> I want to improve myself in desktop programming i'm learning c/c++ and I'm not going to any school of software engineering. Which way do you advice me to go ? 
 
for ex:
 
c/c++ -> c# / Java -> php/asp/etc -> sql
 
Hi, Experimental... earlier posts were right, it really depends on what you'd like to learn.
 
My experience, though, was this... i learned c++ in college (Intro to Programming), studied a bit of SQL and Java on my own (still not good at it, haha) :D... and i'm using c# here in the office i work in. So there, doesn't really help you, i know, but, that's my experience.
 
All the best!

---

### Post by Experimental on 2010-05-26
Yeah that kinda helped :P Experiences helps me get my way. So you know sql. What do you use with sql ? I don't know much about server-side languages . That's one thing I really want to know. I searched it many months ago and everyone is fanboy about asp or php. I want to know any other alternatives for those. I actuallty want some integrity with internet. I saw a c# application that upload an image to imageshack and copies the link. That was cool and I wanna to be able to do something like that.

---

### Post by Experimental on 2010-05-26
upup

---

### Post by simeon87 on 2010-05-26
> **Experimental said:**
> Yeah that kinda helped :P Experiences helps me get my way. So you know sql. What do you use with sql ? I don't know much about server-side languages . That's one thing I really want to know. I searched it many months ago and everyone is fanboy about asp or php. I want to know any other alternatives for those. I actuallty want some integrity with internet. I saw a c# application that upload an image to imageshack and copies the link. That was cool and I wanna to be able to do something like that.

Then do that.. we can't make such decisions for you. All we can do is answer specific questions but what you develop is your choice.

The question "What do you use with SQL?" can't sensibly be answered because it depends on the project.. if it's a website, you'll use the functions available in PHP/ASP/whatever but if it's a desktop application, it's a SQL library or something. Like you say, it could indeed also be a desktop application that connects to a website and does something there. However, it probably won't be sending the query right away because that would not be safe.

---

### Post by uOpt on 2010-05-27
> **Experimental said:**
> I want to improve myself in desktop programming i'm learning c/c++ and I'm not going to any school of software engineering. Which way do you advice me to go  ? 

for ex:

c/c++ -> c# / Java -> php/asp/etc -> sql

Stop thinking that the more languages you know the better programmer you are.

Not to mention this is all backwards, with the big fat monster C++ in front.

A solid base of C (not C++) is useful for everything. Don't learn Java or C# out of thin air. What's the objective? And don't say "Java/C#", what kind of thing is that. "I do fishing/skateboarding in my free time" isn't a good thing to say on a first date :)

Learning SQL is only useful if you want to do things requiring it. And don't learn just SQL the query language, that's useless. Learn how to install, operate and maintain, and then use, a particular SQL server software package.

---

