---
title: "which language should i use for my app?"
date: 2005-05-14
forum: Programming Talk
---

### Post by rjs on 2005-05-14
G'day all,

i've never programed anything before (unless you want to count "hello world" in a couple of different languages), but ive always wanted to learn. Now finnaly ive come up with an app that i actually need, and so i now have a real motivation to start hacking away, so id like to get some various opinions of what language i should write this in. From the langauges ive surveyed, i like the look of ruby and PERL, however im more than open to persuasion, if you think a different langauge is more appropriate for my needs.

Ok the basic idea of the program is to help me learn spanish by it giving me an english word, and me giving it the spanish translation or vice versa, where it would ask me ones i get wrong more frequently and ones i get right less frequently. That is version 0.1. Eventually i want a whole heap of other stuff like it giving me an infinitive verb and then i would have to give back the conjugations, and it popping up pictures instead of english words, or definitions in spanish, so that i wouldnt have to think in english at all. And some time in the even more distant future there would be a nice GUI front end on it (though certainly not at first) and it would play an ogg file of the spanish word (or phrase even).

I also want to design it from the ground up, so that i can just throw in a new database (and perhaps a different module or two), and it can query me about japenese, or hungarian, or korean, or what ever.

One last thing, the database will be based around morphemes rather than words. For non-linguists that would mean that for example it would have the base morpheme work and it would also have the morpheme "to -" and "-s" and "-ed" and would automatically turn it in to an infinative (by adding the morpheme "to -" to make "to work"), or past tense (work+ed), or present third person singualr (he/she/it work+s). This is all preety simple in english, but freaking crazy in spanish, and many other languages, and it quickly becomes obvious why its preferable to store things as morphemes (it will cut down the the size of the verb database by around about 200x compared with what it would be if it considered each conjugation as a seperate word). Anyway, it would also have to have some way of being told about irregular cases (such as eat ->ate rather than eat+ed)

anyway, the basic questions are these:

what programing language should i use?
what tools exist in ubuntu for that language?
what are some good sites/books/mailing lists/forums/etc to help me learn the language?
what kind of database (i assume an SQL, but i am again open to persuasion) should i use?
Do you have any general comments about how i should go about doing it?
Do you know any other programs that aim to do something similar (i know of at least one on the lojban site) that i can steal ideas off?
Is there a problem with licensing the program under GPL, but the database under the GFDL (because i will be taking at least some of my stuff from wiktionary (wikipedia sister program) - are things like definitions even copyrightable?)?

sorry for making that so long, but i'd be very thankful if anyone would share thier wisdom.

thanks
-rjs.

---

### Post by monchichi on 2005-05-14
I'm no guru, but I would highly recommend Ruby.

It's easy to learn, powerful, and it's object oriented natue would be good for what you described. Did I mention it's easy?

[http://www.rubycentral.com/book/index.html](http://www.rubycentral.com/book/index.html) 

Use sql.

And there's tons of ruby bindings in the apt repositories...
It sounds like youll want at least ruby, libruby, gtk2-ruby, and libdbdsqlite-ruby.

I cant help you about other similar projects, don't know of any. It's a good idea though!

I think wikipedia /wiktionary stuff is GPL or something similar... yes i'm pretty sure definitions can be copywritten... there should be license information on the respective sites?

Hope this helps some. Good luck!

---

### Post by rjs on 2005-05-14
[QUOTE=monchichi]I'm no guru, but I would highly recommend Ruby.

It's easy to learn, powerful, and it's object oriented natue would be good for what you described. Did I mention it's easy?
[/QUOTE]

Yeah, as i said i like the look of it, but really, as a non-coder, i wasnt sure what was good or bad

> 
Use sql.

MySQL, PostgreSQL...?

> 
I think wikipedia /wiktionary stuff is GPL or something similar... yes i'm pretty sure definitions can be copywritten... there should be license information on the respective sites?

No, its all under the Gnu Free doc license, which is a real screwy license. Jimbo (the founder of wikimedia) put it under that to start with because at the time it was the only free lincencse avaliable for things which werent programs (though many people would counter that GFDL really isnt free), now cause of backward compatability we are stuck with it. For more about the GFDL see <en.wikipedia.org/wiki/GFDL>

thanks.

---

### Post by monchichi on 2005-05-14
Oops, sorry, I would use SQLite. I think MySQL is more of a web backend, postresql is hardcore and complicated. SQLite is simpler, easier.

---

### Post by rjs on 2005-05-14
thanks, ill check it out.

anyone else have any ideas?

-rjs

---

### Post by rjs on 2005-05-14
After reading some of the sticky threads above, if eventually i wanted to be able to run this on other OS such as OSX or *shudder* windoze, what would i have to do. From what i understand, to make a gui interface for KDE and Gnome all you have to do is write an XML doc (how different would the two docs be?) what does one do for other operating systems? 

This is all way in the futue though. I gotta get it running in termanal first.

thanks,
-rjs

---

### Post by wtd on 2005-05-14
[QUOTE=rjs]After reading some of the sticky threads above, if eventually i wanted to be able to run this on other OS such as OSX or *shudder* windoze, what would i have to do. From what i understand, to make a gui interface for KDE and Gnome all you have to do is write an XML doc (how different would the two docs be?) what does one do for other operating systems? [/QUOTE]

You'd either use a croos-platform GUI, create unique GUIs for each different platform (which all use the same underlying code to access and manipulate data).

The former approach is likely more appealing.  Fortunately Ruby and other languages provide access to GTK, Tk and Fox, as well as probably an even wider range of GUIs.

---

### Post by Mike Buksas on 2005-05-14
I'm a python fan, so I'm going to cheerlead for it here. I don't know much about Ruby, but I've heard that it and Python have a lot of the same strengths. Both are elegant object-oriented languages with a wide collection of libraries and plugins to facilitate developing large applications. Some of the things in Python that would be useful to you are it's windowing tool kits (e.g. wxPython) SQL interfaces and XML parsers. It's also part of the standard Ubuntu distribution, I think.

Python also gives great cross-platform portability, including Windows. You'll just need to make sure that the external libraries are corss-platform as well, or be able to use more than one.

One advantage that Python may have over Ruby is that is has a relatively larger and more active developer base (at least in the English speaking world. I hear Ruby is much more popular in Japan) and you may have an easier time finding tools for Python, and other projects to work on or contribute to.

Mike

---

### Post by tread on 2005-05-14
For the gui, you can use mono .. c#. But if you are going to be doing a lot of text parsing, searching, matching etc. you might want to program in perl or python.

---

### Post by rjs on 2005-05-15
[QUOTE=wtd]You'd either use a croos-platform GUI, create unique GUIs for each different platform (which all use the same underlying code to access and manipulate data).

The former approach is likely more appealing.  Fortunately Ruby and other languages provide access to GTK, Tk and Fox, as well as probably an even wider range of GUIs.[/QUOTE]

cross-platform GUI... umm, ?que?
hows that work?

-rjs

---

### Post by rjs on 2005-05-15
G'day again,

i was looking around some more, and came across a thing called "regualr expressions" which exist in PERL and ruby. It looks like it would come in handy when dealing with certain irregualr verbs (for example "to sleep" is dormir". All the conjugations in the present tense have regular endings, but the root "dorm-" is changed to "duerm-", and in the imperfect subjunctive, the root becomes "durm-". So then with regular expressions i could refer to all three permutations of the root as "d(o|ue?)rm" which would probably come in handy.

anyway, does python have this too? it seems that im tossing up between python, perl and ruby atm.

**Update:** After reading more about perl, i think it isnt appropriate here. From what i understand perl is a sys admin's dream cause it is so quick to write, has so many libraries, and is so powerful, but it seems to be aimed at providing quick and dirty solutions to problems, where as i want to create an elegant easily expandable program. So now its between ruby and python. Is there a free book avaliable online about python (a la the ruby book already linked to in this thread)?

thanks,
-rjs

---

### Post by Lagiv on 2005-05-15
I've been learning Ruby a couple of days, and it seems very similar to Python. Both are excellent choices and you can't go wrong using either one of them.

For me Python was a bit easier to learn but I knew C++ before so that probably helped somewhat. Perl is very object orientated and it's very powerful but the syntax isn't imho as easy as Pythons.

Here is the Python book:
[http://diveintopython.org/](http://diveintopython.org/)
And here is a great official tutorial too:
[http://www.python.org/doc/current/tut/](http://www.python.org/doc/current/tut/)

Remember that when you learn one language learning more is very easy! Have fun!

---

### Post by Quest-Master on 2005-05-15
[QUOTE=rjs]cross-platform GUI... umm, ?que?
hows that work?

-rjs[/QUOTE]

Simply use a GUI library that works on many platforms.

I'd recommend using wxPython, wxRuby, etc. etc. for whatever language you use. Works across BSDs, Linux, OS X, and Windows perfectly.

---

### Post by psychic on 2005-05-15
_Graphical Libs:_
*GTK(mm), tk, wxWindows, Qt*

_Languages:_
*ruby, python, perl, c(++)*

_or..._
*java (*shudder*)*

It does not really matter which one you use, basically you can only make a good decision on what you should use, or what you want to use once you master them all.

But any combination is a good thing to begin with, though you need a different compiler for the c(++) apps. 
Java is a thing for itself, (disregarding its exceptions) you only have awt and swing there, it is a language which either gives you a wooden wheel (awt) or a F1 racing tire (swing) which are both a pain when you go off-road. And you end up re-inventing the wheel again. Suffice it to say i do not really like java that much.

---

### Post by rjs on 2005-05-15
ok, thanks everyone for your replies. I'm gonna have a good look at python and ruby, and learn some basics and then make a final choice. Anyone with futher ideas/features/ways of implementing my program, please leave some more replies. I'll keep everyone updated on my progress toward world domination of the language learning market  :razz:

thanks again.
-rjs

---

### Post by LordHunter317 on 2005-05-17
[QUOTE=monchichi]Oops, sorry, I would use SQLite.[/quote]This is probably the best choice for his project, but not for the reasons you're thinking.

The only reason it's a good choice is because it's easy to embed.  No other reason.  In fact, that's the only good thing about SQLite.  Everything else about it is bad.   Those familar with the language will understand what I mean when I say, "It's the TCL of datbases."

>  I think MySQL is more of a web backend,It's a perfectly fine DBMS for all sorts of tasks, including this one.

> postresql is hardcore and complicated.How so?  It's certainly more featureful than all the other options.  But I find it eaiser to develop and administer than MySQL, as there are less configuration options and details to worry about.

More Features is not necessarily equal to more complex.

You'd do well to read about these other DBMSes before rejecting them.

[quote=tread]For the gui, you can use mono .. c#.[/quote]The Mono project currently doesn't provide a cross platform GUI and their emulation of System.Windows.Forms has a long way to go to being complete.

> But if you are going to be doing a lot of text parsing, searching, matching etc. you might want to program in perl or python.C#/.NET's text manipulation abilites are on the level and about identical to Python's.  PERL makes it easier to use regular expressions (which isn't inherently a good thing, nor relevant here, I think) but that's about it.

[quote=psychic]Java is a thing for itself, (disregarding its exceptions) you only have awt and swing there,[/quote]Seeing as new apps aren't really supposed to be written in bare AWT and that JFC (Swing) uses AWT internally, you really have one choice: simple AWT, or complex AWT.  The latter being the perferred choice because the former isn't featureful enough.

---

### Post by cwaldbieser on 2005-05-23
[QUOTE=rjs]After reading some of the sticky threads above, if eventually i wanted to be able to run this on other OS such as OSX or *shudder* windoze, what would i have to do. From what i understand, to make a gui interface for KDE and Gnome all you have to do is write an XML doc (how different would the two docs be?) what does one do for other operating systems? 

This is all way in the futue though. I gotta get it running in termanal first.

thanks,
-rjs[/QUOTE]

Well, typically you use some GUI toolkit.  Since you probably don't want to have to recode the GUI for each platform, you probably should think about using a cross platform tool kit.

Some different toolkits available on *NIX, Mac, and Windows include Tk, QT, WxWindows, Java AWT & Swing, GTK (?), SDL (?).  The last two I gave question marks, because I have not direct experience programming with them, though I have seen apps written with them running on *NIX and Windows.  Undoubtedly there are others.

Tk is really simple, but some folks feel it is a little *too* simple and not polished enough looking for a "professional" grade app.  On the plus side, there are a lot of languages that have built in bindings to it-- TCL of course, Python has a built in module called Tkinter, there are lots of others.

QT is used throughout KDE, so you can get good idea what its widget set looks like if you are running Kubuntu or any other KDE based distro.  Its native language binding is C++, but there are bindings to scripting languages as well (PyQT for Python, et al).  It used to be hard to find implementations of QT for Windows, but I heard that support in that area has gotten a lot better lately.

WxWindows has native C++ bindings with bindings to scripting languages.

Googling the home pages for these tool kits will give you the best info.  Also, make sure that it is easy to work with the toolkit with the programming language you are going to use.

---

### Post by rjs on 2005-05-23
I've actaully been talking to my brother about this. His first answer was perl, however thats just cause he's a perl nazi. When he heard what i actually wanted to do, he suggested LISP, because be believes that a lot of what i want to do is similar to AI. The more i think about it the more i think he is right. So looks like ill be jumping in the VERY deep end.

hmmm... from "hello world" to AI. Most ppl have bits inbetween. Oh well.

Anyway, i presume some of them gui things ppl were talking about would work with LISP since it is such an old language.

paz y amor,
-rjs

---

### Post by crazeinc on 2005-05-23
[QUOTE=rjs]I've actaully been talking to my brother about this. His first answer was perl, however thats just cause he's a perl nazi. When he heard what i actually wanted to do, he suggested LISP, because be believes that a lot of what i want to do is similar to AI. The more i think about it the more i think he is right. So looks like ill be jumping in the VERY deep end.

hmmm... from "hello world" to AI. Most ppl have bits inbetween. Oh well.

Anyway, i presume some of them gui things ppl were talking about would work with LISP since it is such an old language.

paz y amor,
-rjs[/QUOTE]
 Lisp is a hell of a jump, but it's a good language to understand. That having been said, I certainly don't think I could've handled it straight out of the gate. Ruby is about the most fun you can have programming.

---

### Post by sas on 2005-05-23
> 
[quote]
Originally Posted by tread
For the gui, you can use mono .. c#.
The Mono project currently doesn't provide a cross platform GUI and their emulation of System.Windows.Forms has a long way to go to being complete.[/quote]

Mono does have gtk bindings (gtk#) which is cross platform

---

