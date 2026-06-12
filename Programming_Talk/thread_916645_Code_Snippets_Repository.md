---
title: "Code Snippets Repository"
date: 2008-09-11
forum: Programming Talk
---

### Post by ikex on 2008-09-11
Hiya i've been looking around all day for a good standalone tool to keep all my code snippets in but after not finding any i decided to start writing my own. I've got a pretty much working version that saves all the snippets into a sqlite database. I eventually plan on writing a web backend so all the scripts can be shared\backed up on a webserver and people can view other peoples snippets. Anyway i was wondering if anyone else was interested in this idea? I've started writing it in C# (Using monodevelop) 
Picture Included ^-^

[]("http://img144.imageshack.us/my.php?image=screenshottx0.png")[[IMG]http://img144.imageshack.us/img144/9831/screenshottx0.th.png[/IMG]]("http://img144.imageshack.us/my.php?image=screenshottx0.png")

---

### Post by tinny on 2008-09-11
Cool idea, id use it.

It would be great to have a web application that implements this functionality. This web application could be deployed to the intranet of a software development company to be shared by a software development team.

A bit like an internal code wiki, but tuned to hosting code snippets.

(Just an idea of where / how this idea of yours could be used)

So I guess id encourage you to get this functionality on to a web app.

The webs the future, right? :)

---

### Post by pmasiar on 2008-09-11
a wiki, either desktop or web-based is obvious simple solution for this, and more universal, too.

You can get free wiki at any wikifarm - wikidot.com is my currently most preferred :-)

---

### Post by mike_g on 2008-09-11
Yeah, looks like a cool little app; would be nice for when working offline. I'm working on a site atm with a section for code snippets. I havent got around to setting it up so other people can create accounts and add their own, but this is what I have so far:
[http://grundez.net/](http://grundez.net/)

Edit: oh an it looks broken unless you have Windoze font, I still have a lot to fix.

---

### Post by tinny on 2008-09-11
> **pmasiar said:**
> a wiki, either desktop or web-based is obvious simple solution for this, and more universal, too.

You can get free wiki at any wikifarm - wikidot.com is my currently most preferred :-)

Yeah a Wiki is the simple way to go...

We use mediawiki for our intranet. I find wiki's are ok for this type of functionality, but there may be an opportunity to produce something that is specifically tuned for this code snippet functionality.

EDIT: ikex, having thought about it some more I do quite like the idea of having a personal desktop app to store my code snippets. Alot of the code I work on is commercially sensitive so its good for me to keep these code snippets private.

---

### Post by mike_g on 2008-09-11
Its also nice since you dont have to wait for pages to load or depend on service availability.

---

### Post by ikex on 2008-09-11
I've managed to fix alot of problems i was having (Mainly due to never programming with the GTK toolkit before) its pretty much functional (althought not very userfriendly) and thanks to gtksourceview has brace detection and highlighting. Atm i can't create a toolbar monodevelop decides to freeze everytime i add one so i made a few buttons at the top to add remove snippets, and i've started writing the sharing bit so people can click Share on a snippet to upload it to an online site(eventually i'll write a gtk frontend for people to browse\add other peoples snippets). This way also if people don't want to share they don't have to its all still stored locally ^__^. I hope that makes much sense i just woke up from not sleeping 3 days haha. I still got to add a systray icon and i was thinking maybe global shortcuts? so you can automatically paste snippets into any editor\ide etc.  (I'm just doing a makefile now then i'll upload the sources for people to try out) seeing as its in C# i wanna see how portable it is to run on windows aswell (would be nice to be able to chuck it on a usb stick and use anywhere). 

[[IMG]http://img264.imageshack.us/img264/2961/screenshot1lr9.th.png[/IMG]]("http://img264.imageshack.us/my.php?image=screenshot1lr9.png")


^___^

---

### Post by eightballd on 2008-09-11
Neat....I'd use it, especially once I start developing more in Linux instead of Windows.

---

### Post by ikex on 2008-09-11
Heres the code of what i've done so far!. Theres binaries in bin/Debug. 
Still alot more to do. Im glad other people besides myself would find something like this useful ^_^. (if you poke around the code i know its pretty messy and not very productive but im working on it!)

now time for breakfast :popcorn:

---

### Post by drubin on 2008-09-11
I use a wiki to manage my code snippets (When I remember to update it..).

they are easy they have built in search, categories. auto generated menus.

---

### Post by ikex on 2008-09-11
I've never used a wiki really at all so idk what they are really capable of.
I want to add things like tagging. This has menu's (Every lang the gtksource view is shown on the side, then you just create a new node and name it and type your snippet in). I'll eventually add a search if its really that needed. Also i'd like to add things like assigned a key combination to paste a snippet automatically (or even a modes setup so you can put it in c# mode then one key combination is active and so on) I might install some wiki software just so i can give it a go and look at it might give me some ideas. ^_^

---

### Post by Reiger on 2008-09-11
I *think* that a wiki is probably more useful if you are working on a database actively contributed to by some form of community; but a good deal over-complicated and cumbersome for one's personal collection of fragments.

Apart from that yeah, I think this initiative is really very useful; I've got quite a few things re-invented over the course of time because I either lost the original code (... a nearly fully functioning JavaScript 'engine' doing some real nice stuff) or assumed that I had (couldn't find it when I needed it, but it turned up afterwards)...

---

### Post by ikex on 2008-09-11
Finished alot of the web repos side, now you can upload code at the click of a button to your own personal repository! minor bug fixing. it seems to lock up on exit ughh.
[[IMG]http://img516.imageshack.us/img516/4345/screenshot2ys3.th.png[/IMG]]("http://img516.imageshack.us/my.php?image=screenshot2ys3.png")

you can check out what the web repo's look like at the moment at (nothing great)[ http://ikex.ath.cx:1010/work/snippetmanager/viewsnippets.php?user=debug]("http://ikex.ath.cx:1010/work/snippetmanager/viewsnippets.php?user=debug")

I post way to many screenshots of everything! but its ok i have no life ^_^

---

### Post by cabalas on 2008-09-11
Looks very interesting, is there a code repository that we can check out from? I would be interested in helping if you wanted any.

---

### Post by ikex on 2008-09-11
I would love any help!. Svn is at **:** [http://code.google.com/p/snippetmanagergtk/source/checkout](http://code.google.com/p/snippetmanagergtk/source/checkout)
check it out, if you want edit access just give me a shout ^_^

[]("http://trac.assembla.com/snippetmanager/browser")

---

### Post by cabalas on 2008-09-12
Thanks, but I'll decline write access.  I'll just send you patches for you to review just incase I do something that you don't believe is right for your project.

---

### Post by ikex on 2008-09-12
Okies! =] 
i seem to be having trouble trying to get the right rows to expand after reloading the Treeview. any ideas? (atm it causes the program to crash w/ an Unknown Type error)

---

### Post by ikex on 2008-09-15
To anyone interested i have setup a GoogleCode account for the project at [http://code.google.com/p/snippetmanagergtk/](http://code.google.com/p/snippetmanagergtk/) 

you can grab a .deb to test out from*[COLOR=DarkOrange] **[here]("http://snippetmanagergtk.googlecode.com/files/snippetmanager_0.1-1_i386.deb")**[/COLOR] *or* [**checkout svn **]("http://code.google.com/p/snippetmanagergtk/source/checkout")*

---

### Post by thornmastr on 2008-09-15
Check out [http://www.zotero.org/](http://www.zotero.org/).

Very easy to use.

---

