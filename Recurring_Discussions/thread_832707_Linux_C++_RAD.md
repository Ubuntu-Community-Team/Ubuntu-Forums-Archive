---
title: "Linux C++ RAD"
date: 2008-06-18
forum: Recurring Discussions
---

### Post by solarwind on 2008-06-18
Hey all, I'm no microsoft fan (actually dislike them), but some of the things that I like about Visual C++ are:

* Integrated debugging.
* Integrated GUI designer for [RAD]("http://en.wikipedia.org/wiki/Rapid_application_development").
* Code completion.

I've been searching for a while but I've found no similar solution for Linux. For me, those three things are the most important for development. I know that for some programmers, vi and gcc are the only tools they'll ever need but I really like having a GUI designer and code completion.

Does anyone know of a solution with the three points described above?

---

### Post by blithen on 2008-06-18
What do you mean like a Linux version of C++ or a different language?

---

### Post by ad_267 on 2008-06-18
For your second point I think Anjuta is integrated with the Glade interface designer. Not sure about the other two though as I haven't used it much.

Edit: Wikipedia says Anjuta has an interactive debugger and code completion. It looks pretty well suited for what you want.

---

### Post by solarwind on 2008-06-18
No, I mean a Linux IDE for C++ RAD with debugger integration, integrated GUI designer and **GOOD** code completion. Something similar to Visual C++ on winblows.

---

### Post by Qrikko on 2008-06-18
Yes I do!

Netbeans :)

Today it have gone form being almost a ok substitute to be my preferred environment over any (including MS-VS).

[www.netbeans.org](www.netbeans.org)

I have it working with everything I could ever ask for, it even come with really handy CVS/SVN tools and really is a full-featured studio.

Codecompletion:
The code completion is what I would say working good for C++ now can have small problems sometimes but it's a very long time since I noticed it now..

Integrated debugging:
Working like in MS but with the better debugger GDB behind it (OBS highly personal opinion about which debugger is a better piece of software)

RAD gui-designer:
Hmmmmm... I am not sure here since I don't use it myself.. check among the MANY plugins I am sure you can find something.. (it have a integrated tool to handle plug-ins so it's a breeze), there is gui designers for Java, j2ME and probably more but it's what I have worked with so far.

I checked and at a glance I didn't find anything that fit that description, I am guessing you are talking more about the VC rad or Borland kind of RAD.. not sure about it, but since there is for SWING in Java, maybe it could be extended into more.. c++

Well good luck and hope I am not just too colored by my experience.

---

### Post by solarwind on 2008-06-18
I've used Netbeans a lot before for Java, but for C++, it doesn't cut it for me. The closest thing I've found so far is Code::Blocks.

---

### Post by Qrikko on 2008-06-18
Yeah, I can understand I think that I first was more just understanding that you were looking for a solid environment, and to me netbeans are perfect really, since I don't need the RAD since most of my work are either in arithmetics, algorithms/data structures and rendering..

But as I was ending my post I started to feel like maybe the focus was more on a good RAD environment in linux.. and I agree there, I like the gui-builder for swing and both the game and the gui-builders for micro edition are superb. but if you are looking for RAD in C++ and linux then I might have spread a bit much misguided Netbeans joy there.

Might still be plug-ins but well then there might also be a better environment for RAD in C++.

---

### Post by Mickeysofine1972 on 2008-06-18
I recommend Code::Blocks with wxGlade

wxGlade will out put its gui designs to C++ and Code::Blocks has great code completion and will even do that for functions you define in your projects. It has a debugger that works just as well as VC++'s and you can watch data very well too.

It has a builtin class wizard for quickly making new classes instead of writing them out by hand.

And if you use wxGlade you can compile for windows and linux from the same code.

Mike

---

### Post by Vadi on 2008-06-18
GTK + Glade 3 + Geany is a very nice RAD setup, does all you listed and more.

(and is cross-platform)

---

### Post by kknd on 2008-06-18
Maybe [www.ultimatepp.org](www.ultimatepp.org).

You will not find an all-in-one IDE like visual studio for C/C++ here.

But, I'm much more productive with a simple text editor and GTK / Glade.

---

### Post by LaRoza on 2008-06-18
First, C++ isn't a language well suited to RAD...

Second, the quest for Visual Studio on Linux has been posted many, many times. So far, many useful tools and IDE's were found, but nothing is just like Visual Studio. 

Third, the IDE's listed here are nothing new. It is another "Which IDE" thread...

---

### Post by Vadi on 2008-06-18
... which was just *so* hard to ignore, eh?

---

### Post by Erunno on 2008-06-18
If you are looking for very feature-rich class library which goes far beyond just creating a GUI and allows you to quickly develop applications I'd say use Qt. You'll be hard pressed to find anything similar in the Linux in specific or C++ world in general.

Trolltech also developed a Qt plug-in for Eclipse ([link]("http://trolltech.com/developer/downloads/qt/eclipse-integration-download")) which builds upon CDT as far as I know (Eclipse's C++ development framework). The plug-in also integrates QtDesigner ([link]("http://trolltech.com/products/qt/features/tools/designer")), which allows you to easily build GUIs. GDB is integrated for debugging.

---

### Post by KingTermite on 2008-06-18
> **Vadi said:**
> ... which was just *so* hard to ignore, eh?

Seems like it always is. :(

---

### Post by KingTermite on 2008-06-18
Yes, from what I've seen there is no tool that does it all either. Most things are probably available, but from different tools.

Here's a wikipedia page I found helpful to know what tools I'll be testing out.
[http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments](http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments)

---

### Post by jomiolto on 2008-06-18
> **Erunno said:**
> If you are looking for very feature-rich class library which goes far beyond just creating a GUI and allows you to quickly develop applications I'd say use Qt. You'll be hard pressed to find anything similar in the Linux in specific or C++ world in general.

Trolltech also developed a Qt plug-in for Eclipse ([link]("http://trolltech.com/developer/downloads/qt/eclipse-integration-download")) which builds upon CDT as far as I know (Eclipse's C++ development framework). The plug-in also integrates QtDesigner ([link]("http://trolltech.com/products/qt/features/tools/designer")), which allows you to easily build GUIs. GDB is integrated for debugging.

I'll second this. To be honest, I haven't really done that much programming with Qt, but from the little I've seen and experienced, it seems just brilliant (I'm currently doing CLI stuff, but I'm going to use Qt for my upcoming graphical project). It's got oodles of nice features and it's really cross-platform; it's got its own thread system, for example, so you don't need to use platform specific stuff.

I haven't used it with Eclipse, though. I used KDevelop instead and it seemed nice enough for me -- but of course it's very much about personal preference.

---

### Post by solarwind on 2008-06-18
> **kknd said:**
> Maybe [www.ultimatepp.org](www.ultimatepp.org).

You will not find an all-in-one IDE like visual studio for C/C++ here.

But, I'm much more productive with a simple text editor and GTK / Glade.

I would use glade if I found a good tutorial on how to make a simple good looking form. For some reason, I'm never able to make a simple form. Glade seems so hard to use. Are there any good tutorials for Glade 3 on how to make a simple form?

Also, wxGlade is ugly. I much prefer **wxSmith** or wxFormBuilder.

---

### Post by Vadi on 2008-06-18
A form line what? A wizard-like thing, or just a dialog with a bunch of labels & text entries?

---

### Post by solarwind on 2008-06-18
> **Vadi said:**
> A form line what? A wizard-like thing, or just a dialog with a bunch of labels & text entries?

Just a simple form with a bunch of buttons, text boxes, combo boxes, labels and the like.

---

### Post by solarwind on 2008-06-18
> **Erunno said:**
> If you are looking for very feature-rich class library which goes far beyond just creating a GUI and allows you to quickly develop applications I'd say use Qt. You'll be hard pressed to find anything similar in the Linux in specific or C++ world in general.

Trolltech also developed a Qt plug-in for Eclipse ([link]("http://trolltech.com/developer/downloads/qt/eclipse-integration-download")) which builds upon CDT as far as I know (Eclipse's C++ development framework). The plug-in also integrates QtDesigner ([link]("http://trolltech.com/products/qt/features/tools/designer")), which allows you to easily build GUIs. GDB is integrated for debugging.

Sounds very interesting! Thanks a lot!

---

### Post by ad_267 on 2008-06-18
> **solarwind said:**
> I would use glade if I found a good tutorial on how to make a simple good looking form. For some reason, I'm never able to make a simple form. Glade seems so hard to use. Are there any good tutorials for Glade 3 on how to make a simple form?

Also, wxGlade is ugly. I much prefer **wxSmith** or wxFormBuilder.

I found this tutorial pretty good to get started:
[http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html)

---

### Post by Vadi on 2008-06-18
Just make a dialog, put a table in it, and then add your widgets. I'm not sure what would be the point of a tutorial for that.

Just read at least the first couple pages of the official gtk tutorial first, so you grasp how things work. With those basics, it was very easy for me.

---

### Post by solarwind on 2008-06-18
> **Vadi said:**
> Just make a dialog, put a table in it, and then add your widgets. I'm not sure what would be the point of a tutorial for that.

Just read at least the first couple pages of the official gtk tutorial first, so you grasp how things work. With those basics, it was very easy for me.

It's just that I could never get the packing to work right. Sometimes the buttons would be too huge and so on...

---

### Post by Mickeysofine1972 on 2008-06-18
Its true!

you get lots of info on how to used the libraries but there doesn;t seem to be much that tells you haw to make GUI layout behave.

i would love as comprehensive wx howto 'place you stuff and make it stay there' type tutorial myself.

Mike

---

### Post by Vadi on 2008-06-18
> **solarwind said:**
> It's just that I could never get the packing to work right. Sometimes the buttons would be too huge and so on...

I understand you, but read through the first few pages of the GTK tutorial. I was lost too before understanding it (well, the basics, and I took off from there).

And what you're looking at is the "fill" property. Anyway, read through that tutorial at micah carricks website and a few pages of the official gtk one, and you'll be good.

---

### Post by solarwind on 2008-06-18
> **Vadi said:**
> I understand you, but read through the first few pages of the GTK tutorial. I was lost too before understanding it (well, the basics, and I took off from there).

And what you're looking at is the "fill" property. Anyway, read through that tutorial at micah carricks website and a few pages of the official gtk one, and you'll be good.

I sure hope so. Thanks a lot for your help, and everyone's on this forum. I'll be sure to write up a tutorial once I learn so that other people have an easier time.

---

### Post by Vadi on 2008-06-19
This is kind of a tricky thing to say. You either learn programming in school or on your own. But you still need to do *some* reading, which you did none of. So... if anyone else wants to get into this, just googling gtk, going to documentation -> tutorials, will do it.

---

### Post by solarwind on 2008-06-19
> **Vadi said:**
> This is kind of a tricky thing to say. You either learn programming in school or on your own. But you still need to do *some* reading, which you did none of. So... if anyone else wants to get into this, just googling gtk, going to documentation -> tutorials, will do it.

This is also a kind of a tricky thing to say, but you obviously don't know how much reading I did. And you obviously don't know how to look at anyone's perspective other than you own...

---

### Post by Vadi on 2008-06-19
Not sure how could've you missed the "fill" and the "expand" properties then. But I hope you get it now!

---

### Post by solarwind on 2008-06-19
> **Vadi said:**
> Not sure how could've you missed the "fill" and the "expand" properties then. But I hope you get it now!

No, I did quite a bit of experimenting before posting this thread, but I guess making the right gui takes a lot of practice and time. I program as a hobby so I'll look at it a bit later on.

Thanks to all those who helped!

---

### Post by solarwind on 2008-06-19
Ok here's an example problem:

[[IMG]http://img384.imageshack.us/img384/7650/200806191741001680x1050qr8.th.png[/IMG]](http://img384.imageshack.us/img384/7650/200806191741001680x1050qr8.png)

How do you remove that extra space around the buttons? I've experimented with the fill and expand properties but they don't seem to work.

---

### Post by Vadi on 2008-06-19
Post the .glade please.

---

### Post by Mr. Picklesworth on 2008-06-20
I am finding MonoDevelop 1.0 to be an excellent IDE for quick C / C++ development. For one thing, it's clean, stable and tidy. Being written in Mono is a decent thing in the case of an IDE since it supports all kinds of extensions already in its life.

It does not have an integrated debugger for C, or a GUI designer for that matter (there are both available for C# so far; C support is growing). However, it has a really good project management end. For example, does code processing, integrates with and generates Makefiles. Deals with depending packages really nicely. (Right click on the Packages for a project, go to Edit Packages, choose the ones you want). Deals with translation stuff. Has an SVN plugin. (Looking forward to a bzr one. It's bound to happen some day!).

Actually, in my case, I think that's perfect for an IDE. Everything directly related to compiling and managing the code really smoothly, nothing to do with running it. For a debugger, I have recently noticed a program called Nemiver Debugger in the repositories (via gnome-app-install). I haven't really put it through much so far, but it has helped me solve a few problems and looks rather featureful. Just tell MonoDevelop to launch Nemiver when you choose to run the program in Debug mode and it should do the trick. (Personally, I just tell Nemiver to run the compiled program and change nothing in the Monodevelop project, but I'm weird that way).

Another missing feature is integrated documentation, which is another thing I for one do not miss. With the load of managing docs offloaded to another process, I get a more stable and more efficient experience. If you don't have it installed, get DevHelp from the repositories and download the -doc package for every library you are interested in. Enjoy!



It looks like those buttons in your GUI are placed within a three column container. Would need to see the Glade file to be sure. Something I have noticed with GTK, though, is that one should never force things; they will just happen as the missing widgets get added and the toolkit then has a logical reason to size things as you envision them. Forcing GTK leads to abominations such as Evolution's user interface.



PS: Normally I can immediately accept something being in Recurring Discussions. However, I am doubting the decision with this thread. I do not see an awful lot of similar discussions, unless that is recurring discussions in the context of the programming talk forum...
At least, I consider this less recurring a discussion than 99% of the other junk that pops up in the cafe. (Bill Gates threads, anyone?).

---

### Post by solarwind on 2008-06-20
> **Mr. Picklesworth said:**
> I am finding MonoDevelop 1.0 to be an excellent IDE for quick C / C++ development. For one thing, it's clean, stable and tidy. Being written in Mono is a decent thing in the case of an IDE since it supports all kinds of extensions already in its life.

It does not have an integrated debugger for C, or a GUI designer for that matter (there are both available for C# so far; C support is growing). However, it has a really good project management end. For example, does code processing, integrates with and generates Makefiles. Deals with depending packages really nicely. (Right click on the Packages for a project, go to Edit Packages, choose the ones you want). Deals with translation stuff. Has an SVN plugin. (Looking forward to a bzr one. It's bound to happen some day!).

Actually, in my case, I think that's perfect for an IDE. Everything directly related to compiling and managing the code really smoothly, nothing to do with running it. For a debugger, I have recently noticed a program called Nemiver Debugger in the repositories (via gnome-app-install). I haven't really put it through much so far, but it has helped me solve a few problems and looks rather featureful. Just tell MonoDevelop to launch Nemiver when you choose to run the program in Debug mode and it should do the trick. (Personally, I just tell Nemiver to run the compiled program and change nothing in the Monodevelop project, but I'm weird that way).

Another missing feature is integrated documentation, which is another thing I for one do not miss. With the load of managing docs offloaded to another process, I get a more stable and more efficient experience. If you don't have it installed, get DevHelp from the repositories and download the -doc package for every library you are interested in. Enjoy!



It looks like those buttons in your GUI are placed within a three column container. Would need to see the Glade file to be sure. Something I have noticed with GTK, though, is that one should never force things; they will just happen as the missing widgets get added and the toolkit then has a logical reason to size things as you envision them. Forcing GTK leads to abominations such as Evolution's user interface.



PS: Normally I can immediately accept something being in Recurring Discussions. However, I am doubting the decision with this thread. I do not see an awful lot of similar discussions, unless that is recurring discussions in the context of the programming talk forum...
At least, I consider this less recurring a discussion than 99% of the other junk that pops up in the cafe. (Bill Gates threads, anyone?).

Thanks for pointing me to Nemiver!

---

### Post by Vadi on 2008-06-20
> **solarwind said:**
> Ok here's an example problem:

[[IMG]http://img384.imageshack.us/img384/7650/200806191741001680x1050qr8.th.png[/IMG]](http://img384.imageshack.us/img384/7650/200806191741001680x1050qr8.png)

How do you remove that extra space around the buttons? I've experimented with the fill and expand properties but they don't seem to work.

From what I see, you made an GtkHBox with 3 items, and placed the buttons in the middle column. Delete the things on left and right, make the hbox have 1 item, and that should do it.

Just a guess though, because that's one of the ways that I could think of to accomplish what you did there.

---

### Post by LaRoza on 2008-06-20
> **Mr. Picklesworth said:**
> 
PS: Normally I can immediately accept something being in Recurring Discussions. However, I am doubting the decision with this thread. I do not see an awful lot of similar discussions, unless that is recurring discussions in the context of the programming talk forum...
At least, I consider this less recurring a discussion than 99% of the other junk that pops up in the cafe. (Bill Gates threads, anyone?).

It contains a "which IDE is like Visual Studio" topic and has been hijacked.

---

### Post by solarwind on 2008-06-20
> **Vadi said:**
> From what I see, you made an GtkHBox with 3 items, and placed the buttons in the middle column. Delete the things on left and right, make the hbox have 1 item, and that should do it.

Just a guess though, because that's one of the ways that I could think of to accomplish what you did there.

Thanks, I'll try it!

---

### Post by klange on 2008-06-20
> **Mr. Picklesworth said:**
> [Wall of Text]

+1 for MonoDevelop. Only IDE I actually use.

---

### Post by Jaiibee on 2008-06-29
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=53](http://appdb.winehq.org/objectManager.php?sClass=application&iId=53)

That help??

---

### Post by solarwind on 2008-06-29
> **Jaiibee said:**
> [http://appdb.winehq.org/objectManager.php?sClass=application&iId=53](http://appdb.winehq.org/objectManager.php?sClass=application&iId=53)

That help??

Thanks, but not really.

---

### Post by Silpheed2K on 2008-06-30
[http://www.wxwidgets.org](http://www.wxwidgets.org)
[http://www.wxformbuilder.org](http://www.wxformbuilder.org)
[http://www.codeblocks.org](http://www.codeblocks.org)

---

### Post by solarwind on 2008-06-30
> **Silpheed2K said:**
> [http://www.wxwidgets.org](http://www.wxwidgets.org)
[http://www.wxformbuilder.org](http://www.wxformbuilder.org)
[http://www.codeblocks.org](http://www.codeblocks.org)

That's exactly what I'm using now.

---

### Post by smartdb on 2012-11-28
Try the most comprehensive C++ RAD [http://sdb.net.in  ]("http://sdb.net.in")
[]("http://sdb.net.in")
or

[  ]("http://sdb.net.in")[http://smartdb.dyndns.info](http://smartdb.dyndns.info)

---

### Post by smartdb on 2012-11-28
Try [http://sdb.net.in](http://sdb.net.in)
(most comprehensive)

---

