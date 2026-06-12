---
title: "NetBeans or Eclipse, or text editor for java"
date: 2009-03-25
forum: Programming Talk
---

### Post by theDaveTheRave on 2009-03-25
Hello all.

I know that really this topic has probably been done to death but I'm going to open it up again anyhow :P

So I've been using netbeans preety much since I started learning to program in java (with a starting forray using blueJ).

I've recently starting thinking about "packaging" my systems and doing so with a little hassle as possible.

This has lead me to investigate ANT scripts, and the manifest files. With this in mind I was begining to wonder if I really needed to work with an IDE at all??

The stuff I like from IDE's are:

code completion - as it means I don't need to make my brain remember bookfuls of class function.

Drop down selection lists - this again goes with the code completion stuff. enter your object variable name and you get a box with all the available methods of that class object. I love this particularly.

JavaDoc Generation - writting "proper" javadoc is so easy in its self, but the IDE makes generating the html pages a simple single click process too (and they look just like the java core API - which is a big plus in my book).

the other stuff that is available, like "compiling and running" I can in fact live without (especially as I have recently starting doing this from the CLI).

Also my pc is getting a little "old" and running netbeans certainly uses up a heap of processor and memory, and makes my poor old laptop seem slow when I'm not coding - ie writing reports, touching up photo's, creating web pages, messing about with MySQL stuff.

In fact netbeans makes my laptop go as slow as it did when I first got it and it had vista running on it.
As a quick benchmark, it couldn't easily handle viewing a DVD in vista, but in ubuntu I can watch a DVD (with sound from the main speakers). Have music playing (from hdd) and playing out through the headphones, and everything would seem to run fine!

So I guess my real question is this.

Is there a text editor with the advantages of an IDE - code completion, drop down menu's etc, but without the bloat?

I have tried usind gedit in a "tabbed" environment, and although it is nice I miss the fact of being able to select my class methods from a drop down list (or is there a plugin I am missing).

If I could "turn off" all the extra stuff that is available with netbeans I think I would, and then save the profiles as "basic" and "advanced" for switching between the 2, but it takes ages for these option to come on to deslect them, and the default behaviour seems fairly "basic" anyhow!

your help and comments are eagery awaited.

David

---

### Post by CptPicard on 2009-03-25
With Java I really wouldn't use anything else but a full-blown IDE such as Netbeans. It makes things go smoothly, while otherwise managing the Java build process and all that is such a total pain.

As far as packaging goes, I guess you've noticed that you get a nice .jar file in the dist/ directory of your project?

---

### Post by theDaveTheRave on 2009-03-25
CptPicard

Yes I've noticed the jar file and stuff, and I understand what you are saying out the reasons for staying with an IDE.

My problem is that I am a "cheap skate" and I don't want to have to updgrade my laptop and desktop just so as I can keep using Netbeans / Eclipse, when otherwise the 2 systems work just fine!

Essentially I only realy use the "editing" facility of netbeans, and the rest I am learning to do from their own dedicated files.

I've got no reason to do this other than understanding how to do it, so as I can then later work with an automated method and understand how to "tweak" things if I need to.

In this vein I just need a really "basic" text editor with code completion, highlighting, some of the nice extra side bars that show classes and in file methods etc - the real basics. but I'm not sure exactly which modules I need to make this stuff "happen" and I guess I need to be able to turn the other stuff on / off as I need them, which I can do, but I haven't seen a way to "create a profile" to make this easier to do.

Or can I have >1 version running??

or does Eclipse have a smaller system resources footprint than netbeans?

I know that some people prefere Eclipse, because there are more "plugins modules", but I don't use that many of them anyway (yet), or because "there are more people working on it.

I don't think either of these are particularly good arguments, using cars as a quick example...
look how many people build a morgan, and they are great cars, then look at Fiat (water soluble.... or they used to be!).
Cup holders - how are these useful? if you give kids stuff to drink you end up with sticky stains on the seats, if I use them for my coffee it allways go cold as I am concentrating on driving. And with modern motorways / cars you are never more than 1 or 2 hours from a services, or from a local town - just hold on and have a proper rest.

also I'm trying to be highly "modular" in my design and build process, getting all the parts to work, then turn them into beans, then design the GUI and plug the beans into it.

I feel that this should be a "simpler" method... although I could ultimately be wrong!


sorry to sound so "stressed" by it all, the truth is I'm just after some advice before I get bogged down in something that I didn't really want (or worse didn't require), because everyone is saying, like you , it is so much easier with an IDE - I often find that a bit more effort gives much better results (like leaving to catch the train 10 minutes earlier in the morning, means you are allways the first into the office, which is good to impress the boss, and when there is nothing stopping you, why wouldn't you?).

sorry for another long post!

David.

---

### Post by sujoy on 2009-03-25
for text editors, vim and emacs both have code completion plugins, which basically covers what you are asking for, so it might be worth taking a look, but keep netbeans around, just in case ;)

---

### Post by mehaga on 2009-03-25
Next version of Netbeans 6.7 should be much less 'bloated', so they say. RC2 is out, but I'm not sure if the bloat related issues have been addressed already. If I understood correctly, you will have smth like profiles in other IDEs, like JDeveloper. Then, only modules for chosen profile would be loaded and that should reduce the bloat. Also, even with older versions, you can unload modules you don't use. OR, you could go really crazy and use NB platform to create an editor that perfectly suits all your needs ;)

---

### Post by samjh on 2009-03-25
Netbeans: WYSIWYG GUI editor, good project management support, good profiler and debugger, excellent code-completion, good distribution support, and more.

---

### Post by blake82 on 2009-03-25
You may want to check out Anjuta. I haven't used it extensively, but it was definitely a lot snappier than netbeans or eclipse.

Anjuta is written in c++ and supports java projects

I also use geany for small stuff, also very lightweight.

---

### Post by jespdj on 2009-03-26
Try [Geany](http://www.geany.org/) - it's a very nice text editor with some IDE features, but it's not as big and complicated as a full IDE.

It's in the Ubuntu repository.

---

### Post by theDaveTheRave on 2009-03-26
Thanks to all.

I now have something that I can use by way of making an informed decision.

I'll try out the various things, and see what I like best.

I suspect I will keep netbeans around (or maybee switch to Eclipse, so see if it really is an improvement).

Geany sounds interesting, I'll probably start with giving that a whirl, then maybee I'll try Eclpise for a while.

I've also turned of a lot of the extra modules that you can get with netbeans, I just don't like the thought that I have a slow process to turn them all back on again - it is a shame I can select a group of them all at once and activate / deactivate them as a group.

Moving from one system to another isn't going to cause me too much grief at the moment as I'm doing most of the compliation stuff from the command line (or copying the class files to a separate location and compiling there as an alternative).

thanks for the advice guys / gals

David

---

### Post by Garratt on 2009-03-26
you could always write a plug-in as a side project for Geany, or any other light weight notepad.

I can definitely say without a doubt eclipse has smaller footprint than Netbeans at the moment.
While i have not used it extensively I have somewhat tested the resource hog.
And a big plus is the almost instant loading, while Netbeans can take up to a few minutes just to start up on some older machines(and even new ones).


 When first introduced to VI most people want to repeatedly smash their head against a wall, but once you are fluent in using this nothing really compares... so I'm told. I have been using it on and off for about 6 months, and I am finding that I am starting to get used to it and it certainly has some power behind it, but that said, I still not convinced that someone fluent in windows shortcuts will fall far behind the speed of it. Interfaces were made for a reason :P

EDIT: Vi is nice in the way you can use CLI from within. But it's not hard to have a small CLI open next to a project when working in windows, it boils down to personal preference.

Personally I use, dual boot vista/ubuntu, when working in Vista I use notepad++ with PATH set to JAVA and CYGWIN /bin, and occasionally VI, and when using Ubuntu I use VI / Geany /, and some toying around with notepad++ running under WINE.

---

### Post by theDaveTheRave on 2009-03-30
Garratt,

I've got a copy of notepad++ on the desktop for when I boot into windows (which is about twice a month for the moment).

A number of people say great things about eclipse... but as I was "brought up" with netbeans I've kinda stuck with it!

I know what you are saying about Vi, it drives me to distraction, and in fact I tend to use Gedit, as I find repeatedly bashing my head against the wall is detrimental to my productivity... and I get strange stares from my colleagues! :biggrin:

David

---

### Post by theDaveTheRave on 2009-05-23
A quick update for anyone following this thread.

So I've tried working with eclipse for a few weeks, and I sort of like it. However I have that age old problem of when you switch from something you are used to to something else (ie going from windows to linux or one gnome to kde) you find that you are suddenly slow in getting certain things done.

Another issue that I haven't been quickly able to solve, and I must admit haven't really tried to, is working on existing netbeans projects in eclipse. I'm sure that there is a plugin out there for doing this, but I have just continued working in with netbeans for existing projects and in eclipse for new ones.... I've even had issues simple copy / pasting the relevant class files (they don't seem to appear as part of the eclipse project for some reason? <shrugs>), so I'm obviously missing something!

So other things I've have been playing with....

I've also been playing around with php of late, some things I've been asked to do are a bit quicker in php, and the results are more easily seen in the web browser, so it's nice and visual which is pleasing.

Again for php I've been using gedit, with the side panel, I find this really great for small projects (or even what are becoming quite large projects!) in php.

All in all, my overall preference has now reverted back to netbeans (again mainly as it is what I have become accustomed too), but I now have a working knowledge of eclipse (admitedly on a limited working knowledge, but I can find my way around.... sort of ;) ), so probably not a bad thing.

I've also descovered some of the other netbeans plugins, such as for creating UML type diagrams of stuff.

However I also found [Dia]("http://projects.gnome.org/dia/") (it is in the repositories), which I really like for this, and I have been using this extensively for creation of the basic structure. What I really like is the ability to export the diagram as a set of basic class files, which I can then cut and paste the information into netbeans (as some of the formating, such as the comments and structure of the files isn't exactly as I like!), also I have notes that automatically appear for the different file types in netbeans pre set, which I am sure I can do in Dia, but haven't yet found out how to.

Well appologies again for a long post.

I'll keep posting as I find other things that I like, but I suspect that this will probably be the end of it for me.

Basically, I'm going to stick with netbeans for my personal projects, and then if I move on somewhere and I need to work on other people project in the eclipse environment then at least I'll not have that horrid learning curve to get to know it, as I've allready done it now.

maybee this thread has been interesting reading / usefull to other users, in which case I'm pleased that my questions and feedback has been more than just good for me.

So its happy < Ubuntuing > to one and all, see you all at the next bug jam.... or maybe a strawberry jam, or just simple perl jam (music or coding!).

David

---

### Post by theDaveTheRave on 2011-08-13
Another quick update for anyone following this thread.

I've recently started a new job, and I decided to eclipse another try on a clean system. So hopefully no netbeans incompatibility issues sneaking in.

And now I've been using it in real anger for numerous stuff I really like eclipse.

Particularly I like how when doing GUI design it doesn't lock out the generated code, i like to add extra comments into the file so as I can be sure that I know what the code is up to. and the manner in which netbeans closes editing on the gui-designer generated code is not nice, also the code created in eclipse is much more pleasant to read after the fact.

If you look back to the initial part of this thread, my main gripe was that netbeans  seemed so slow. Well now I'm using eclipse on the same machine I think my problem is that my development laptop is rather old and slow.

At some point I intend to set up a more powerful pc as a server, so maybe I'll run the eclipse executable from there (not sure that this will make much difference), or maybe I should invest in a new dual chip mobile phone (yes my laptop is so old the new mobile phones have more processing power, and in some cases more internal memory too).

david

---

