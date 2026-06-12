---
title: "Options for a C/C++ IDE"
date: 2010-02-28
forum: Packaging and Compiling Programs
---

### Post by bornbyforce on 2010-02-28
Hey everybody. First ever Post here.
Please bear with me because it's going to be long. I've been using Ubuntu for months now and I am currently with Jaunty. I am the type who normally does a thousand searches before actually posting the question somewhere.
Been working on finding a good IDE for over a week now. I'm running out of options. Tried code:blocks with wxwidgets installed from repositories. Then tried them from source code. Simply doesn't work. These things are just so full of bugs that even an experienced developer like me is exhausted. Then went after Anjuta. This one is really crazy. The current version even doesn't have a modern solution for adding an include path. Please don't suggest writing code in gedit or the black screen (my term for terminal) and going through debugging in there. Don't get me wrong. I am using Ubuntu for a reason and I am not going to debate that here. The problem is, you can install MS Visual studio 6.0 on Windows and withing 2 or 3 minutes you can create a multi-document framed window with some event handling without even typing a single word. And remember that technology is over 10 years old now.
I need a development environment with a Gui designer and integrated compiling and debugging. Can anyone suggest something? I guess there must be some good options available. Please leave the KDE/QT options out. I also prefer something not using JRE for obvious reasons. Even context sensitive help or auto-complete are luxuries I can easily cope without. I don't know if I am asking for too much but I believe there must be a simple straight-forward solution after all this enthusiasm I see with Linux developers.

---

### Post by mickie.kext on 2010-02-28
> **bornbyforce said:**
> I also prefer something not using JRE for obvious reasons. 

What obvious reasons? 

You practically ruled out everything. QT Creator and KDevelop are good but you leave them out. Eclipse and NetBeans are even better, but use JRE...

There is MonoDevelop... try that.

---

### Post by bornbyforce on 2010-03-01
Thanks for the prompt answer Mickie. Yeah, monodevelop is one of the few remaining options. Thanks for mentioning it. 
You know the old debate about the KDE and QT... Of course that is not the case anymore. But for me there is more. QT currently belongs to Nokia and after what they did to Iranians I will feel a bit of smell of blood on my hands if I use it. (No offense to anyone. It's a personal feeling)
I didn't rule out JRE based ones completely. Netbeans is one of my favourite PHP development environments. Just prefer not to use JRE as it uses so much resource. I will try JRE-based IDEs if I run out of other options.

---

### Post by bornbyforce on 2010-03-01
Adding this for people who may later search. I tried Monodevelop too. Please correct me if I am wrong but unlike what is stated in wikipedia's [Comparison of integrated development environments]("http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments#C.2FC.2B.2B") it does not have Gui designer for C/C++ the feature is only available for .NET(C#). So I guess this one is ruled out too.
What's next? Eclipse doesn't have Gui-designer either. Netbeans does, according to Wikipedia. The official website is down however. Anyone can confirm?

---

### Post by matthew.ball on 2010-03-01
I would recommend wxFormBuilder and emacs (with g++ and gdb) as they both achieve what you're after, but you said you don't want terminal stuff so I don't think you'd like it.

Edit: Looking through the first page in this topic returns a GUI front-end to gdb - [ddd]("http://www.gnu.org/software/ddd/")

---

### Post by bornbyforce on 2010-03-01
> **matthew.ball said:**
> I would recommend wxFormBuilder and emacs (with g++ and gdb) as they both achieve what you're after, but you said you don't want terminal stuff so I don't think you'd like it.

I don't know... May be it's because I am coming from Windows development. But seriously... is it possible to debug programs in even twice the time (compared to a graphical IDE) using terminal? 
This is out of curiosity... How you guys handle that? with a graphical IDE you can put a breakpoint in middle of the code with one click of the mouse button and then press the debug button with one more click. program is compiled and starts to run in debug mode and you reach your breakpoint. Now there is the debug window. Just where ever in the code you dblclick on a variable and in that window you see name and type of the variable and its value at the moment in the running program. I know terminal solutions are known for their extreme flexibility. But are they really able to perform such a simple task this easily?

---

### Post by matthew.ball on 2010-03-01
Yeah, you should have a read of some tutorials. For instance: gdb allows conditional breakpoints which are pretty interesting.

Like I hinted to before, in conjunction with emacs, gdb is very nice - just a warning in advance; there is a fairly large learning curve here. I'm telling you this so you don't give up on it early, stick with it.

Here are some quick google results for a tutorial for [gdb]("http://www.cs.cmu.edu/~gilpin/tutorial/") and a tutorial for [emacs]("http://www2.lib.uchicago.edu/keith/tcl-course/emacs-tutorial.html") - personally I found the tutorial included with emacs pretty sufficient, it is an interactive tutorial which is helpful in this context.

I have never used vim, but I have heard many people comparing it to emacs, I would assume it has similar capabilities. If you find emacs a little too extreme (and the learning curve is steep) you might be interested in that. Otherwise, good luck and happy hacking!

Edit: This looks pretty interesting: [http://www.gnu.org/software/emacs/manual/html_node/emacs/GDB-Graphical-Interface.html](http://www.gnu.org/software/emacs/manual/html_node/emacs/GDB-Graphical-Interface.html)

---

### Post by bornbyforce on 2010-03-01
:lol:
Oh man... I really appreciate your suggestion but this one is really so dangerous for social life. I can not imagine myself using several combinations of keystrokes to take a chunk of code and putting it above another chunk of code. I'd rather do it with selecting the piece with mouse button and then dragging and dropping it in the right spot. I seriously believe computers are made to make life easy and however hard I try I can not convince myself this huge learning curve is going to make my life any easier in the long run.

---

### Post by matthew.ball on 2010-03-01
I don't know, there are so many programmers who use emacs and associated tools, something must be working correctly.

I mean, if it wasn't, why would they continue to use these applications (emacs/vim, even to a lesser extent nano etc)?

---

### Post by Calmor on 2010-03-01
I couldn't imagine using nano for any kind of heavy coding.  It's a nice little editor for quick source changes or configuration files, but I feel it lacks the tools to be a serious coding tool.  I haven't taken the time to learn emacs or vim (though I have dabbled with vim a little) and imagine they would be excellent.

When in Linux, I generally just use gedit - I know it's not an IDE, but it's a basic text editor that still gives me the mouse commands.  On Windows, it depends.  My PHP coding is done in Notepad++, since I don't really require all the extra tools that Visual Studio provides.  When doing C# stuff, though, VS really can't be beat.  

And to the OP asking for an IDE similar to VS... I think there is a different paradigm in Linux which makes that option not nearly as preferable.  Many programs are created as command-line-only, then have a GUI attached to them later, when the code is working correctly.  In fact, there are programs you'd think would have to be GUI - photo slideshow video creators, for example - that are command-line driven.  In Windows, the GUI is really your only option (except in rare cases), so Microsoft felt they needed to give beginning coders the framework to make a GUI program.  I personally haven't done much serious coding in Linux (yet) so I'm not well versed on the debugging side of the code.

There are decent GTK GUI builders out there, but I caution that even these deviate from the MS C++ 6.0 theme.  Everything needs to be in a frame/container.  It makes sense from a scalable layout, and in fact newer versions of Visual Studio provide this as an option, but it varies a bit from 6.0 from what I recall.

---

### Post by bornbyforce on 2010-03-01
> **Calmor said:**
> And to the OP asking for an IDE similar to VS... I think there is a different paradigm in Linux which makes that option not nearly as preferable.
...
There are decent GTK GUI builders out there, but I caution that even these deviate from the MS C++ 6.0 theme. 
Overall I agree. If I wanted the VS counterpart in Linux I would have been missing the point of Linux to some extent. That is not what I want. I know I can use something like Glide and then use the XML in something like Gedit (I really don't need much more than that for an editing environment). And then I can compile in terminal. Though I understand it looks very professional I really don't understand why these three steps can't be integrated into one solution. Now a lot of Linux fans (i would say, unfortunately) say why should it be done anyway. It is a bit off the topic but in answer to them and to you I must say that was what made Windows a very successful OS in the first place. It's not MS's philosophy or price of their products or even lack of competition which makes Windows still an OS to beat. It was us developers. They made making an application so easy and so much fun that even people like me who didn't have any training or education started doing it and found themselves stick to it for years and years and in the process we made users of Windows happy by giving them a wide range of applications who looked great while we were not even so good at coding ourselves.
My point is... If Linux was to stay a command-line OS or a low-graphic system that once was (or you would say its predecessors were); we wouldn't have had all this enthusiastic fan base that we see now. We have 1 percent of the market and even this 1% comprises of a lot of people who wish they could change the settings of nautilus by pressing a shortcut rather than using the command line. Now if we want to make it 2% we need more beautiful applications rather than more commands for the terminal. And for that it is necessary to make it easy for semi-geek people like me to make a beautiful application. I seriously believe Linux community is lacking the understanding of this to a great extent.

---

### Post by filofel on 2010-03-02
> Tried code:blocks with wxwidgets installed from repositories. Then tried them from source code. Simply doesn't work. 

I'm a bit puzzled, here: 
I've been using Code::Blocks for a couple of years, and my Ubuntu "software sources" (repository list) is config'd to auto-update from the "nightly builds" (URL here! ->) [Code::Blocks repository]("http://apt.jenslody.de/"). This means that I automatically get an update every 4 or 5 weeks average and always run the bleeding edge version. I get the precompiled binaries (never had to get the sources and recompile it myself). 
And I never ran into a show stopper that required me to backtrack to a previous version...
I also have an "other software" source pointing to apt-wxwidgets.org/lenny-wx main, btw: This provides the wxwidgets that CodeBlocks wants to pull.

All of that is explained on "Jen's unofficial debian-repository for Code::Blocks", at the URL above.

HTH, /Ph.

---

### Post by Kazade on 2010-03-02
Yeah +1 for Code::Blocks. I've used loads of C++ IDEs* over the years and Code::Blocks is the one I've stuck with. Definitely use the pre-packaged nightlies rather than self-compiled, I've never had a problem with them (and the stable version is too old now).

* MSVC6-2009, DevC++, KDevelop, Netbeans, Eclipse, Anjuta, Code::Blocks (probably more).

---

### Post by Keyper7 on 2010-03-02
Okay, here we go. I'll try to be as helpful as I can.

**1) About Code::Blocks.**
I used it for a while, debugger and all, and never faced a showstopper bug. Before giving up on a software because of instability, you should make sure that the software itself is to blame. Maybe it's some library incompatibility, maybe you used a version too much on the bleeding edge, maybe something was missing during compilation, maybe a dependency wasn't installed at the time, who knows? Before giving up on it, did you try to talk to an experienced c::b user about the issues? Or posted a message in their forums?

**2) About Anjuta**
I used it only for one project, but this project has a lot of different dependencies (Gtk, Glade, VTK, linear algebra libraries, to mention a few) and Anjuta took care of everything concerning include paths automatically with its autotools integration. I just sat down, created a new project and started coding. Never once had to add an include path manually.

**3) About Java**
You shouldn't rule out an option because it uses "so much resources". You should rule out an option because it uses "TOO much resources". When you try Eclipse and Netbeans, are they slow enough to affect your productivity? Does RAM usage reach its limits and the computer starts to swap? Is your computer so fragile that you are actually worried about its durability when using a few more megs or RAM or a few more CPU cycles? If the answers to all previous questions were "no", what's the problem?

**4) About MonoDevelop**
Because Glade completely separates the interface from the source code, IDE integration is something completely superfluous and there is very little gain in doing it, compared to interface designers that generate source code. It's not much more useful than, say, integrating an YML editor in the IDE because your program uses YML for storing parameters. With Glade, GUI handcoding is usually minimal. Try running MD and Glade simultaneously. You will probably feel no need for true integration.

**5) About GDB**
Command line debugging sounds inefficient to you because your thinking is mouse-oriented. Setting breakpoints in GDB is [incredibly flexible](http://www.ofb.net/gnu/gdb/gdb_29.html#SEC29) and the learning curve is definitely worth it. I am a mouse-oriented debugger myself, but I know some friends who can debug with GDB, like, five times faster than me. If you want pragmatic reasons to believe that, think well: after properly learning and memorizing the main GDB shortcuts, what is more efficient, having to alternate your hands between the mouse and the keyboard all the time for debugging and modifying the code or simply never leaving the keyboard? There is a reason why keyboard shortcuts (for example, for alternating between Firefox tabs) never died despite the popularity of the mouse. It's a matter of not being stuck to predefined habits.

Those were some facts and experiences. Now I will give you my opinion. The best-suited C/C++ IDE for me, and the one I currently use, is **Eclipse CDT**. Supports automatic path finding, code completion, syntax error detection, breakpoint debugging and it doesn't feel heavyweight. That said, I don't know how far it can go in path detection for a large project full of different dependencies. Anjuta and MonoDevelop might do a little better in that regard.

---

### Post by bornbyforce on 2010-03-02
> **Keyper7 said:**
> Okay, here we go. I'll try to be as helpful as I can.
...

OK First of all... Thank you for the long answer. And it was helpful indeed

I am answering these to some extent for people who come back and read these things later. They might get an idea what to expect.

Ok let's go in the order you mentioned.
1. Code:Blocks
I am not really sure what the problem was. It has to be one of the things you mentioned. It can be even something as silly as wxwidgets not being installed properly before because the repository was down and I didn't notice it. Well I have tried installing both from source code and when I started code:blocks I saw the message "starting codeblocks" in taskbar and it just disappeared a few seconds later and with it disappeared my patience after a couple of days working on it.
Now with the link **filofel** kindly provided I gave it another try and it seems to be working though I still haven't successfully compiled a wx program so it's too soon to answer.

2. Anjuta
Well on this one I am confused. May be you have been using an older version. In the tutorials I see the old versions had options for adding paths for the compiler and linker. There is no such thing in 2.26. They just suggest you add odd set of words and signs to make.am file and the likes of these to make your program work (which I did and it did not work anyway). Now remember I know what compile options and ... are and I call it odd symbols and words. Imagine how user-friendly it is for the poor 3rd world country student who is learning C++ and can't afford MS VS and is unfortunate enough to think Anjuta will handle dependencies itself. Now you are telling me it does? ok I can prove it. I just can make a tutorial of steps to install and run anjuta and get stuck in compiling GTK+'s very first tutorial. Would that make you change your mind? A programmer is supposed to know what is a required library or... but how to make your compiler include it is not programming. And Anjuta is terrible at helping you do it.

3. Netbeans and Eclipse.
I have used both on Windows before and I liked them both.
If you happen to have an old Vaio laptop which is just looking for a reason to heat up its CPU and run its noisy fan you probably would give up on a lot of things other than JAVA-based IDEs. I didn't in fact. The Netbeans server have been down for 3 days now. I have installed the main IDE but for the C/C++ support it looks for the plugin in their website which is quite ironically gives 403 forbidden header now that I need it.
Eclipse doesn't have the integrated GUI designer and I will talk about this later.

4. Monodevelop
True integration of GUI design and its loading in code is a tricky question. If we set aside all the matters of personal taste (which I believe are indeed very important) I am still not sure after a while I will not be made to change my favourite editing or designing program for silly reasons like one makes the xml file incompatible with a later version of the other. You pass the (sometimes big) curve of learning before realizing you have just thrown it all away. Same applies to Eclipse. Again I know sometimes you have to settle to a mediocre option because simply there is not a good one in existence. The point is I am just trying to make sure there is not. And remember, even this mediocre option is an option now after around 2 weeks of headache. Knowing about how newer versions of Glade leave the coding out completely is quite a new concept to me as well as to most average programmers with windows background. Honestly... Wouldn't it be better to have a simple and small IDE which handles all these in a single program?

5. GDB
OK let's say this is a good debugging tool and let's really be open-minded and say everybody has a preference. But that's as far as I can possibly agree with you. Please nobody take offense but only thing I believe is the terminal based editor good for, is impressing other geeks of the dozen more shortcuts that one uses.
If both mouse-oriented and keyboard-oriented developers are quite good at what they do there would be no speed difference between them in productivity. If they debug 3 times faster than you it normally means they are either geniuses anyway or that they are like 80% less productive because they just aimlessly cycle through changing code and debugging and randomly change things. Coding and debugging are not physical activities. While you are seeing the debug results your brain is concentrating on the possible things that have possibly gone wrong. Now you either spend that time moving your hand away from mouse and on to keyboard or just keeping it on keyboard. That wouldn't make much difference. The difference is if you are open-minded enough you'd just go learn another language or get some music lessons or have some exercise or even hang out with friends instead of memorizing a dozen more keyboard shortcuts.

And on conclusion. OK I'm working on Code:Blocks now. I'll see if I can get the c/c++-enabled version of Netbeans. Will try CDT Eclipse too. And I will sure come back and say what I ended up using. Thanks a lot to you for the comprehensive answer and for all others who had the patience for reading my post.

---

### Post by Colonel Kilkenny on 2010-03-02
> **bornbyforce said:**
> Of course that is not the case anymore. But for me there is more. QT currently belongs to Nokia and after what they did to Iranians I will feel a bit of smell of blood on my hands if I use it. (No offense to anyone. It's a personal feeling)


Sorry for posting off-topic but NSN sold normal/standard network with normal/standard equipment to Iran. Either there is a standard network or there isn't network at all. This is the situation in pretty much all countries in the world. IIRC, NSN also has a market share of about 30% in Iran, why is the whole fuss about NSN? What about all the other businesses that have sold pretty much same equipment to Iran? What about the fact that the Iran deal was actually done by Siemens before Nokia and Siemens merged their networking businesses? The sad things that have happened / are happening in Iran are sad but there's really no need to exaggerate. Without NSN, Huawei, Ericsson, etc. there wouldn't be any networks at all in Iran and all those companies have to follow certain standards. What they cannot do is control the government.

I really wouldn't turn down Qt Creator just because it's developed by Nokia. It's of course ideal for Qt programming but I think basic C++ is okay with it as well. And it's free, under active development and fast. Of course just gEdit + console might also do the job. IMHO, it's the best IDE I've seen (feature-wise there are better alternatives of course, but the Qt Creator just feels right).

---

### Post by bornbyforce on 2010-03-02
Ok yeah it is a bit off the topic and better keep it out of here. I have enough reason to blame Nokia for it and I am willing to discuss it further but I believe it is not a topic we are supposed to discuss here.

---

### Post by Keyper7 on 2010-03-02
Okay, this is an interesting discussion so I'll make some new points over your replies. It's important to keep in mind that I'm not trying to claim the superiority or inferiority of anything. I'm just trying to show you that other options are neither inherently worse or inherently better, just different, and productivity with them depends on your needs and, sometimes, leaving out some pre-estabilished notions.

About Code::Blocks, I'll wait your review later. :)

About Anjuta, it's strange indeed. I remember using a very friendly "which library you want to use?" graphical menu where I mouse-selected from a list of installed libraries. Never had to touch Makefile.am. If I have the time, I'll make a Gtk hello world in it later.

About Netbeans/Eclipse, you do have a reason then. That's fine with me.

About GUI development. Personal taste matters, a lot, but another thing important is knowing the difference between "easy" and "what you are used to". Back when I started using Linux and multiple desktops, I took a productivity hit in the first days because I got confused remembering where each app was. Had I judged the concept of multiple desktops based on the first days, I would hate it. But I gave it time to sink in and today I can't live without it. I'm not saying it's better, I'm just saying I gave it a chance, despite being different, and it was worth it.

The concept of Glade leaving the coding out is different, but you should ask yourself: *are there technical reasons to believe it's inherently worse*? I don't think so. It's all a matter of opinions. There's nothing in Glade that you surely make you like it, either, but give it a chance, is all that I'm saying.

"Wouldn't it be better to have a simple and small IDE which handles all these in a single program?", you ask. If you consider GUI and non-GUI to be the same thing (coding), perhaps it makes sense. But in Glade it's a different game. Again, not worse, not better, just different.

And fearing a change in the format is exaggerated. The chances of it happening in a way that forces you to do a major rewrite is no greater than fearing a change in the API of one of the libraries you use. Specially because the GtkBuilder format is directly based on the current state of Gtk, and an official part of the Gtk specification.

Finally, about GDB. You misread me a little bit. I didn't mention my friends of an example of any kind of technical superiority of CLI-debugging. What I meant is that, if this is how they are productive, who I am to claim which method is better? It depends on the person and, no, it does not depend on how "geek" and "genius" they are. This entire snippet

> Please nobody take offense but only thing I believe is the terminal based editor good for, is impressing other geeks of the dozen more shortcuts that one uses.
If both mouse-oriented and keyboard-oriented developers are quite good at what they do there would be no speed difference between them in productivity. If they debug 3 times faster than you it normally means they are either geniuses anyway or that they are like 80% less productive because they just aimlessly cycle through changing code and debugging and randomly change things.

is quite offensive (despite this not being your intention), because you are confusing opinions, personal preferences and habits with facts, and judging the skills and competency of people who you never met based on them. The whole quote is a stack of prejudiced statements, not really different from "if you use alt-tab instead of clicking on the taskbar, you are a geek" and I do believe there is a fair share of non-expert Windows VB programmers would would take offense at it.

> Coding and debugging are not physical activities. While you are seeing the debug results your brain is concentrating on the possible things that have possibly gone wrong. Now you either spend that time moving your hand away from mouse and on to keyboard or just keeping it on keyboard. That wouldn't make much difference.

There are several serious HCI statistical studies that say otherwise. Computer usage is a greater physical activity than most people think and moving from mouse to keyboard too frequently can be a significant productivity hit than you might realize. This is one of the main reasons of the success of applications like Quicksilver, even among non-techinical users.

Do you use multiple desktops? Make an experiment: disable either the mouse or keyboard options for changing the desktop and see if having only one option does not start to annoy you after a while.

> The difference is if you are open-minded enough you'd just go learn another language or get some music lessons or have some exercise or even hang out with friends instead of memorizing a dozen more keyboard shortcuts.

This is a gross overestimation of the mental work and time needed to memorize shortcuts (Wrapped inside a not-very-subtle prejudiced stereotype that might insult some people, by the way... One of the friends I mentioned is fit, likes to hang out in bars and is quite an accomplished guitar player). Plus, for most scenarios you don't need more than two or three.

---

### Post by bornbyforce on 2010-03-02
Ok So what we will decide with Anjuta, Code:Blocks, Netbeans and Eclipse depends on what I see when I finish my tests with them.
With separation of GUI and code I agree it is a matter of opinion. When code is mixed with the GUI, you will have difficulties modifying other peoples code or even changing things inside a program which doesn't do conventional things. So it it less flexible. On the other hand it is easier and lets you concentrate on it faster and be more productive with smaller knowledge. So it has its pros and cons which means one has to select the development method (and as we see as a result, select the operating system to develop for) based on some personal taste.
And the bitter part is this CLI thing. The reason I felt you are defending it was you saying some people you know debug in CLI 5 times faster than you. I believe this means you think there is some superiority in that method and I meant to say was if they are doing it faster it means they are either better at it anyway (regardless of the method, they would have been anyway) or that they are merely doing it faster and not really better. It wasn't prejudice. Please read it again and you'd be less offended. Now the rest of my argument remains. If you can do the same thing in the same period of time but with a smaller learning curve, why should you do it the other way. Well, let's set aside the stereotypes and also what we believe are the very offending stereotypes (I have some sort of nerd pride anyway). The question is still there... if you can learn something the easy way why should you choose to learn it the hard way? This is regardless of the prejudice that I might have.
I am starting to think that we are really talking about different things here. I seriously don't understand how using a multiple key keyboard shortcut can be easier to use than pressing pg-down. Now that is the simple scenario. a little more complicated scenario is when you use your mouse roller to go through the code and find when you did a certain thing. And there is the example I talked about earlier; where I select 3 lines of code with mouse and drag and drop it several lines of code before that. I can hardly imagine it can be done easier with keyboard. Now even if it is possible, I really want a justification for the huge learning curve.
Your example of using the Alt-Tab is indeed a very good one. In fact it is exactly my point. I use both Alt-Tab and clicking on Taskbar so often. Now as you said both would be quite annoying not to have. The thing is, in a sophisticated environment you have both while in CLI you only have keyboard; result of which is spending time learning lots of shortcuts to be able to perform a task that you intuitively are able to do by mouse. I consider this a fact, not prejudice.
And finally... the last thing I would want to do is offending people here in a community in which in few days after joining I find caring people who read my long posts and answer them line by line. May be it is my English but I guess you got me wrong too. Your friend is most likely fitter, better guitar player, more social and definitely a better coder than I am. We know it has nothing to do with CLI. With a smaller learning curve he would have had more time for any of these things. And even if he doesn't really care so much about this saved time, there are lots of others who do so. My point is simple: nobody have ever given me any convincing reason for more productivity coming out of CLI rather than usage of mouse. If I get some answer to this, all the time spent on learning something not naturally intuitive can be easily justified.
Sorry If I offended you or anyone else. I assure everybody I didn't mean to do so.

---

### Post by Keyper7 on 2010-03-03
> **bornbyforce said:**
> When code is mixed with the GUI (...) it is easier and lets you concentrate on it faster and be more productive with smaller knowledge.

You gonna need to elaborate on that. From where the "larger knowledge" of using Glade is coming from?

> And the bitter part is this CLI thing. The reason I felt you are defending it was you saying some people you know debug in CLI 5 times faster than you. I believe this means you think there is some superiority in that method

Wrong. What I meant to say is that there is *no inherent inferiority*. The difference is subtle, but important.

Let's do some basic math here. If I were to believe that CLI debugging is inherently less efficient, then that would mean that some of my friends are **more** than 5 times faster than me. Now, I don't have the highest self-esteem in the world, but I don't believe this is true.

In other words, what I'm saying is: does the CLI inherently increases the debugging speed? No, I have no evidence of that? **Does the CLI inherently DECREASES the debugging speed? NO, I have no evidence of that EITHER.**

> and I meant to say was if they are doing it faster it means they are either better at it anyway (regardless of the method, they would have been anyway) or that they are merely doing it faster and not really better.

And why is that? You are failing to provide any technical arguments other than "for me it would be slower, therefore it should be slower to anyone".

> It wasn't prejudice. Please read it again and you'd be less offended.

Okay, let me try reading again:

> (...) it normally means they are either geniuses anyway or that they are like 80% less productive because they just aimlessly cycle through changing code and debugging and randomly change things.

I know they are not geniuses. Therefore, you are calling them incompetent programmers who "just aimlessly cycle through changing code and debugging and randomly change things".

Yeah. Still offended.

> Now the rest of my argument remains. If you can do the same thing in the same period of time but with a smaller learning curve, why should you do it the other way.

You seem to be missing my point: I'm not saying one should try a different method of debugging for that very important project that must deployed tomorrow. I'm saying that, if you have a hobby project, or a side project where deadlines are not an immediate concern, why not try something different to see if you like it?

> The question is still there... if you can learn something the easy way why should you choose to learn it the hard way? This is regardless of the prejudice that I might have.

The prejudice is still there, and it's making you ask the wrong question.

My point is that there is no such thing as "easy way". It depends on the person and the task.

> I am starting to think that we are really talking about different things here. I seriously don't understand how using a multiple key keyboard shortcut can be easier to use than pressing pg-down.

Eh? Elaborate on this. You are comparing using the keyboard with... using the keyboard.

> Now that is the simple scenario. a little more complicated scenario is when you use your mouse roller to go through the code and find when you did a certain thing.

Well, I rarely use the wheel to go through the code. I usually use PgUp/PgDown.

> And there is the example I talked about earlier; where I select 3 lines of code with mouse and drag and drop it several lines of code before that. I can hardly imagine it can be done easier with keyboard.

This is an example of activity I always do with the keyboard. Place cursor in the beginning of first line, hold shift, press down three times, ctrl+x, pgup until I find the desired place, ctrl+v. I can assure you it's faster than with the mouse.

**For me**, maybe not for you.

An important difference between your statements and mine, is that if you say that this method would be slower for you, I will **not** insinuate that there's something wrong with you. To each his own.

> Now even if it is possible, I really want a justification for the huge learning curve.

All of those are trivial commands that anyone who has used the simplest text editor in Windows knows. No learning curve. Furthermore, refer to the "I'm not saying you should this during an urgent project" argument I've given before.

> Your example of using the Alt-Tab is indeed a very good one. In fact it is exactly my point. I use both Alt-Tab and clicking on Taskbar so often. Now as you said both would be quite annoying not to have. The thing is, in a sophisticated environment you have both while in CLI you only have keyboard; result of which is spending time learning lots of shortcuts to be able to perform a task that you intuitively are able to do by mouse. I consider this a fact, not prejudice.

When exactly did I say that, once you start using the CLI, you are forced to use the CLI, and only the CLI, forever and never use the mouse again otherwise blue gnome demons will drag you to hell and poke you with green radioactive forks for all eternity?

I'm presenting the CLI to you as an alternative for specific situations, not a full replacement.

Which specific situations. It's up to you. Might be none. **But you can't know until you learn it.**

> And finally... the last thing I would want to do is offending people here in a community in which in few days after joining I find caring people who read my long posts and answer them line by line. May be it is my English but I guess you got me wrong too. Your friend is most likely fitter, better guitar player, more social and definitely a better coder than I am. We know it has nothing to do with CLI. With a smaller learning curve he would have had more time for any of these things. And even if he doesn't really care so much about this saved time, there are lots of others who do so. My point is simple: nobody have ever given me any convincing reason for more productivity coming out of CLI rather than usage of mouse. If I get some answer to this, all the time spent on learning something not naturally intuitive can be easily justified.
Sorry If I offended you or anyone else. I assure everybody I didn't mean to do so.

"Smaller learning curve", "bigger learning curve", "naturally intuitive", "not naturally intuitive"... all subjective concepts that depend on the person and the task. You can only have a truly conclusive stance when you try.

Another problem is that you are expecting convincing reasons to **replace** your current ways. You will never receive those and it's certainly not my intention to give them. What I am doing is giving suggestions for **improving** your current ways by **adding options** you currently don't know about while **keeping** your current options.

But this is only possible if you drop the "OH MY GOD IF I EVEN TRY TO LEARN IT FIFTY YEARS WILL PASS AND BEFORE I FINISH THE FIRST LINE OF THE MANUAL I WILL DIE!!!" attitude.

Life is short, but not that short.

PS: I messed up my system and can't install Anjuta right now. I'll go back to you on the include path thingie when I solve this, but might take a while. :)

---

### Post by gpstar on 2010-03-03
I use geany and glade for my stuff.

Geany is a fast lightweight IDE. It is available in the repos or you can download it from there website.

[http://www.geany.org/](http://www.geany.org/)

then I use glade for designing the bases of my gui interface.

---

### Post by bornbyforce on 2010-03-04
Apart from repeating my previous arguments I don't have much more to say. I guess for some reason I can not explain my point properly.
Person A using method a is doing job J 5 times faster than person B using method b. Possible results coming out of this a priori are 1. Person A is 5 times better at job J than Person B is. 2. method "a" has 5 times more efficiency than method "b" 3. A combination of the above 2.
Now the a priori was yours. If we consider person B an average programmer, Person A is genius indeed. If he is not, it must be his method which is inherently 5 time or more efficient. Now in previous post you said you didn't claim that is the case either. The only remaining possibility is that they are not both doing the job J. In other words person A is doing a far easier job than person B. These were exactly what I said originally. May be with poor choice of words but the reasoning is there if you look at it carefully. 
> **Keyper7 said:**
> 
From where the "larger knowledge" of using Glade is coming from?

Ok this one is simple. First of all glade is harder to use than visual studio. We are not talking about better or more efficient or anything else here. One example is you not needing any containers in VS. You can not add anything without them in Glade. Then there are things like knowing in your preferred programming language how to load the glade file to create the specific window. In VS it is done when the project is being defined. Another example is handling of events or signals. In VS you double-click on the event and the catching function is ready. You just add the code inside the brackets. In glade I am yet to figure out how it's done. :oops:
What I meant with "I am starting to think that we are really talking about different things here." was exactly what came up. What CLI environment are you exactly talking about? I assumed Emacs because normally when someone is as enthusiastically as you defending CLI, (five times faster thing) they normally are talking about the likes of Emacs. I have never used it. I have never learned it. But unlike what you said I **CAN** know without learning it that using page-up button is easier than Meta-v (?!). I do use keyboard shortcuts. I just feel too awkward to use 3 or 4 of them instead of one mouse drag and drop. And at the same time feel awkward to get my hands off the keyboard and right-click and select paste and click and then get my hands back to keyboard instead of ctrl-v. Now in both cases both options are available in a modern editor. Mouse options are absent in both scenarios in CLI. My never-answered question is in what scenarios a CLI editor does something easier than a modern editor.
> **Keyper7 said:**
> 
"Smaller learning curve", "bigger learning curve", "naturally intuitive", "not naturally intuitive"... all subjective concepts 
NO. These are absolutely objective. Mouse movement is an intuitive thing. The object you move forward and backward which moves another (virtual) object up and down, needs little or no learning. We naturally relate it in our mind. However, keeping down a button with "ctrl" sign on it and then pressing another one with v sign on it to paste something is not intuitive. I don't mean it's not worth learning. I used them too. But sure they are not something we have learned in our mental development period in our childhood. While relating the movement of two objects, to a great extent, is. So, using mouse is more intuitive for the average literate person than using a number of keyboard shortcuts. As a result the former needs less time mastering than the latter. These are all objective matters.
Oh, and I didn't know there are Gnome demons and radioactive material involved with CLI too. Thanks for warning me! ;)

---

### Post by Keyper7 on 2010-03-04
I'm noticing that whenever I write long paragraphs, you seem to focus on just one part and ignore the other. So I'll keep the words at a minimum from now on and go straight to the point.

---

> Person A using method a is doing job J 5 times faster than person B using method b. Possible results coming out of this a priori are 1. Person A is 5 times better at job J than Person B is. 2. method "a" has 5 times more efficiency than method "b" 3. A combination of the above 2. Now the a priori was yours. If we consider person B an average programmer, Person A is genius indeed. If he is not, it must be his method which is inherently 5 time or more efficient.

Wrong. You are forgetting negative values. Hence my quote:

> If I were to believe that CLI debugging is inherently less efficient, then that would mean that some of my friends are more than 5 times faster than me. Now, I don't have the highest self-esteem in the world, but I don't believe this is true.

---

> One example is you not needing any containers in VS. You can not add anything without them in Glade.

Whether this is an advantage or a disadvantage depends on the programmer, the task, the complexity of the layout and the need for future flexibility.

---

> Then there are things like knowing in your preferred programming language how to load the glade file to create the specific window. In VS it is done when the project is being defined.

Something you need to learn **once** and then reuse for all projects in the same language.

Plus, the point is moot if the language in question is not supported by VS.

---

> Another example is handling of events or signals. In VS you double-click on the event and the catching function is ready. You just add the code inside the brackets. In glade I am yet to figure out how it's done.

Integrating the IDE and the GUI editor certainly offers this kind of advantage, it's true.

Hardly a massive productivity hit, though, and can be compensated by the flexibility depending on the project.

It all depends.

---

> What CLI environment are you exactly talking about? I assumed Emacs (...)

I'm not talking about CLI environments. I'm talking about CLI debugging. GDB.

And you do know that Emacs supports mouse and drag-and-drop, right?

---

> NO. These are absolutely objective. Mouse movement is an intuitive thing. The object you move forward and backward which moves another (virtual) object up and down, needs little or no learning. We naturally relate it in our mind. However, keeping down a button with "ctrl" sign on it and then pressing another one with v sign on it to paste something is not intuitive. I don't mean it's not worth learning. I used them too. But sure they are not something we have learned in our mental development period in our childhood. While relating the movement of two objects, to a great extent, is. So, using mouse is more intuitive for the average literate person than using a number of keyboard shortcuts.

One of the most basic things you learn in the first days of any HCI course:

**"more intuitive" does not means "more efficient"**

You didn't learn how to drive a car during your childhood, either.

---

> As a result the former needs less time mastering than the latter. These are all objective matters.

Which maybe matter if you must finish your program tomorrow or you will die. Otherwise, I repeat:

> You seem to be missing my point: I'm not saying one should try a different method of debugging for that very important project that must deployed tomorrow. I'm saying that, if you have a hobby project, or a side project where deadlines are not an immediate concern, why not try something different to see if you like it?

---

> Oh, and I didn't know there are Gnome demons and radioactive material involved with CLI too. Thanks for warning me! ;)

I know you are just joking, but this sentence kinda shows how much attention you are actually paying. I asked the question:

> When exactly did I say that, once you start using the CLI, you are forced to use the CLI, and only the CLI, forever and never use the mouse again otherwise blue gnome demons will drag you to hell and poke you with green radioactive forks for all eternity?

The answer: I did **not** say. So your joke does not really make sense.

Furthermore, you ignored the point behind my comment: I am not saying you should use *only* the CLI, nor I am suggesting programs that restrict you to it.

---

### Post by UncleBoxy on 2010-03-09
I found this thread by doing a search on google for "ubuntu development environment" just to see which ones are currently out there and in use by the general community.  It has been quite informative so far, both despite (and to some extent because of) the back-and-forth between Keyper7 and bornbyforce.

My background a similar, though not quite the same, as bornbyforce.  I primarly use MSVS to do my coding and have been using it since version 4.2 (currently using 2008 ).  Before that, I used Turbo C++ 3.0 in a Win 3.11/DOS environment.  Both had/have really good debuggers built into the IDE.  Btw, what are we defining as an IDE?  By Integrated Development Environment, I mean that the debugger should be integrated into the editor.  I think that's what we all mean, but maybe not.

That being said, I've also worked at a job where I had to use an external editor (I liked emacs after I actually learned the shortcuts and finally got the syntax highlighting set up right) and xldb for debugging.  That worked fine also.  My personal preference?  I liked MSVS way better, but I worked with the tools I was given and was willing to learn them.

I tried Code::Blocks, DevC++, and a few others a while back, and the only one I remember liking was DevC++ (I used it along with Allegro for graphics).

Honestly, I've gotten really spoiled using MSVS (along with ReSharper when doing C#... good god I love that addon).  I think it's made me less likely to want to stretch out and try other options.  I'm in the process of getting familiar with MonoDevelop, though.  From the looks of it, I think it'll work for my needs.

Finally, any framework that respects separation of concerns (UI from business logic from database logic from <insert other stuff here>) is a good thing, imo, architecturally.  That sounds like what the Glade tool that has been mentioned does.

This might have been a little too long, but I hope it helps add to the discussion.

---

### Post by bornbyforce on 2011-04-05
I started this thread a long time ago. It went on to turn to a place for  a polite version of flaming. When people don't read your post carefully  before answering there is no point in continuing the conversation.  However I feel myself obliged to give an answer to this one-time-question of mine for the sake of others.
I am writing this for people with this particular background though it may be useful for others as well:
You learned software development under Windows and though not always  happy, you got used to and were comfortable with Visual Studio. You are  not particularly fond of Java. You are not fond of .Net either.  Generally speaking you want your CPU's cycles to be used for the good  rather than running a magic box that hides your laziness and your boss's  greed which prevent you from writing truly portable code. You want to  write and run code that does what it is supposed to do fast and  reliable. You want interface of your program to be part of your code  rather than loaded from files in runtime. You want your IDE to be geared  towards your needs. You want a professional tool specifically made for  C/C++. You want it to be able to support windowed build  options like MS VS and be able to use makefiles as well. You want to be able to do  your building and debugging by pressing a button in your IDE rather  than going to command line. You want break-points for debugging to be  visible and manageable in the interface.
BUT...
You are not particularly worried about unicode and other  internationalization related issues. And you don't mind spending a  bit of time getting used to a new way of designing a GUI for your  application.

In that case I recommend Code::Blocks-WxWidgets combination.
You can use both nightly builds and official releases of code::blocks. I  have had problems with UTF versions of wxWidgets with Code::Blocks but I don't rule out  my own lack of knowledge being the problem. Also its way of designing a  window is a bit different from what you used in MS VS. So a bit of  learning is needed here. Please have in mind that if you want to have  proper design options you will need to do it outside your IDE. This in  my own view is not really a big deal. If you follow proper program  design you should not need to switch between programs (for designing and  coding) too often.
I don't like the idea of loading xml files in runtime for creating the  GUI. I'd rather see code created when I design the interface. wxWidget  does this for you and how it actually creates the visual effects depends  on how it is compiled and what system it is running on.
Code::Blocks runs smoothly itself even on my old machine because it is  not run on a "runtime environment". I consider this a relatively stable application. Its menus  are intuitive. Debug and edit modes have separate view setup that can be  saved. It is integrated with debug and compiling tools and you will  only be hassled when you need to actually do something out of ordinary.
I do not name its competitors for obvious reasons. This is my thoughts on them:
Some are extremely NOT intuitive. They get a lot of support from  open-source community but I do not understand what the benefit of an IDE  is if you are supposed to type commands to change things! I am not  going to get into a argument about relativity of intuitiveness here.
Some of its competitors on the other hand have a more beautiful and more  intuitive interface. You want the menus to be pleasing to the eye  and easy to find. Unfortunately in my experience I found obvious bugs in  them in first few days of use. And I wondered how many of them are left  in more obscure places where you don't touch so often. If you are going  to spend some time getting used to a new tool you'd better go after one  that has a lower risk of letting you down somewhere down the line. Of  course if you are willing to contribute by debugging, you'd better give them a try.
Again I may create some sort of "response" here. Don't be tempted to go  after programs that make you do things in command line. Mouse is  invented for a reason. Graphic interface is invented for a reason. "A  lot of cool guys use them" is not a reason for wasting your time  learning a tool which you can not use effectively before memorizing  several dozen keyboard shortcuts. And when they tell you about special  abilities that those tools have, just ponder a few seconds... How often  you are going to sit on your computer and use a terminal on your machine  to run an editor in your machine which connects to a machine somewhere  else and edits files and... If you are likely to do this often in future  you have been wasting your time reading this post I guess.
And last and probably also least(!) if you decide to switch back to  Windows one day or you just want your learning to be of some use for you  in both environments I must say the Code::Blocks - wxWidgets  combination is also available in Windows. I have never used them there  so you may want to test their reliability and performance there  yourself. You can also have a look at the programs that use wxWidgets as  their GUI toolkit.
: o did you really read all that?!

---

