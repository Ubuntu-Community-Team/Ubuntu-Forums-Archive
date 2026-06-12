---
title: "hmmm.. can't decide"
date: 2006-12-26
forum: Programming Talk
---

### Post by maddog39 on 2006-12-26
Hello all,

Before recently, I was mainly a PHP developer with some Python/C++ knowledge and did mostly powerful DB driven web based applications but I'm really tired of PHP because I dont like working with alot HTML and templating engines and the such. So I have been getting into application development more and more lately until a few days ago (christmas eve) I spent the whole day writing my first complete, fully functional and stable, and most of all, useful application I've ever made. I made it using Python and wxPython and I REALLY like that combination. As far as C++ I made some program for health using GTKMM and I really liked that. I tried wxWidgets but for some reason g++ just DOES NOT like it, it just refuses to compile. Even the tutorials which are known to work, wont compile. So I through that out the window.

Anyway, the program I made with Python, I called gPyCompile, and its a GUI for the python bytecode compiler. So my question is, since im not sure really what to do, should I continue with development of my current program (i have plans for a build system for it and stuff) or should I try and port my python program to C++ (because I really like compiled languages and I am most familiar with C-like syntax from my years of work with PHP) or should I start an entirely new project, OR I was thinking about joining a Python or C++ project. Although if I join a project, I normally like to just talk directly to owners/founders, so basically project owners, I would prefer you post here and maybe talk on MSN or something.

I am really comfortable so with Python & wxPython and C++ & GTKMM so I would be able to help in either of those. I really like both languages, I have no complaints about Python nor C++ (well C++ is a PAIN IN THE A*S when it comes to external librariesm) but other than that I like both pretty equally.

:/ So what should I do? If you have a project in either Py/wxPy or C++/GTK feel free to post.

Thanks!
-maddog39 :)

---

### Post by lnostdal on 2006-12-27
Just to complicate things even more; PyGTK is also an option.

I have no suggestions as to what you could do if you only consider Python and C++. But disregarding that; I'd like some help with my SWGtk-project -- written in Lisp. :)

I'm hoping to use FreeNX and SWGtk as a way to "distribute" remote server-executed applications to both Linux, Windows and Mac-users; ignoring all the AJAX-mumbo-jumbo and instead have a client I am able to control (IE is closed source, and I'm pretty much unable to fix any bug in the always hairy FF ..etc.).

---

### Post by Wybiral on 2006-12-27
I have several python and C++ projects going, just hobby stuff. Mostly involving OpenGL. My signature has two of them, some other ones include:

[LIST]
[*] Genetic algorithm alife
[*] A 100% python+OpenGL fps
[*] A c++/python interfacing library (like boost, but simpler)
[*] A tiny byte-language VM (a language could be used to compile to the bytecode)
[/LIST]

And some little experiment projects that I pick up and put back down from time-to-time.

I generally don't do much full-time team work, mostly just open source "do what you can, just keep track of it" type projects.

---

### Post by maddog39 on 2006-12-27
Oooo, first person shooter and the VM sound good. Although anything 3D related is totally out of my realm and I cant do some of the math stuff required for that. Although that FPS sounds reeally nice. Keep going with it. :) I was though, thinking about a programmers editor. Now, I know youur going to say; arent there already enough editors/IDEs out there? The answer is yes, but most of them (in my opinion anyway) really suck, or are too slow for my patience OR are way too bloated OR dont have the right features or good enough features. I've spent countless, and I mean countless, hours searching google and especially sourceforge for good IDEs and text editors and stuff. I pretty much dont like any of them. The only two I can tolerate are jEdit and Geany. Geany, at the current moment is my favorite, I used to like jEdit but on my PowerBook its just too slow and has alot of querks with the plugin system and certain plugins which I deem necissary for my kind of development.

[Edit]
@Wybiral: Just thought, it might be useful to compile that FPS into bytecode. Which gives me another reason to make a build system for python. GUI based too! Autoconf/Automake is a huge hassel to configure and a gigantic pain to deal with. Not to mention it doesnt even support python.

---

### Post by Wybiral on 2006-12-27
lol, yeah, I'm a texteditor kind of guy. Anyway... I do plan to make some kind of scripting interface for the FPS, and it will be python based, so you could write some kick-@*& level/AI scripts whenever I get it rolling for examples of how to script things...

I'm actually kindof leaning towards making it a super-easy to use FPS engine as a python module. That way everything can be neatly obscured from the python programmer and they can use things like "myModel = loadModel('guy.obj')" and "rotateModel(myModel)" to create all of the scenes and such.

Speaking of editors... Basic4SDL is without an editor at the time, if anyone feels like writing an IDE for it, that would really rock too. With python binding, I can actually access Basic4SDL's VM to return variable states and stuff, so a debugging feature could be added to the IDE as well.

My tiny VM project is probably going to be pretty small and useless... I've just been thinking about writing a tiny VM to compile some random language into opcode for. I've been wondering what it would be like to create a brand new language (I'm working on a BASIC VM based off of Basic4GL, but BASIC is... well, BASIC).

---

### Post by maddog39 on 2006-12-27
Hmm... the FPS engine is a real good idea, I dont think any of the current game engines make it nearly as easy as you describe it. So here is where I stand I guess, I think I might add a build system to gPyCompile (btw, its on google code now, [click here]("http://code.google.com/p/gpycompile/")) and I submitted my text editor project idea to SourceForge and I think I will go along with it. It will support VB/VB.NET syntax highlighting which is pretty much compatible with your B4SDL syntax, or atleast pretty close right? I could also use the python-dev package to import and use the module in C++ so that B4SDL programs can run in a VM for debugging.

[Edit]
I also forgot to mention that I have tried PyGTK, but just never did much with it.

---

### Post by pmasiar on 2006-12-27
> **maddog39 said:**
> So my question is ... should I continue with development of my current program (...) or should I try and port my python program to C++ (because I really like compiled languages and I am most familiar with C-like syntax from my years of work with PHP) or should I start an entirely new project, OR I was thinking about joining a Python or C++ project. 

IMHO before you will go and start your own project, it might be useful to participate in a running project first. Just to see how it works from inside, what problems tend to arise and how to handle them. So when you will start your own project (in which you are not sure yet), you will know how to manage it and it will be more smooth ride for you and your community.

Porting something to C++ makes little sense unless performance is critical. Python is easier to maintain and extend, and if speed is not a problem, it is not a problem :-)

So I would suggest joining a python project - easier to read the code to get in, easier to modify/extend to add new features.

You mentioned IDEs - did you looked into my favorite python's IDE, SPE? i especially like sidebar with procedure names and ##--- comments - bookmarks.  If you are interested, I can give you 2 missing little cool features which would be nice to have in the SPE.

BTW you cannot trust Wybiral's advice on IDE: he is known to prefer gedit instead of proper python IDE. (Hi Wybiral  I am back :-) from my vacation)

---

### Post by Wybiral on 2006-12-27
lol, you cannot trust pmasiar because he may or may not eat children...

Gedit rules... In your face!

** The author of this post would just like to specify that this post is meant for entertainment and educational purposes only and does not necessarily reflect his own views **

(I was kidding btw, to the best of my knowledge, pmasiar hasn't eaten children in years...)

ANYWAY... If you make an IDE, I recommend not adding too much stuff (as cool as it may sound) and trying to keep it small and CPU efficient... I just can't stand having a bunch of junk in the way and this [SIZE="1"]tiny[/SIZE] little box to code in... I want nothing extra, some syntax highlighting, maybe a pull-down menu with tools and stuff... But big boxes rule.

---

### Post by po0f on 2006-12-27
I am also a fan of the text editor for all of my work, though I tend to jump between GEdit and Vim (if I could get Vim to insert spaces instead of tabs I'd be gravy).  I decided to look into SPE.  Guess what?  Website's down, and from what I can tell, [it's been down a while](http://wiki.python.org/moin/SPE/).

---

### Post by Wybiral on 2006-12-27
I got curious and tried SPE, but after I closed all of the excess stuff to get a decent sized text box... I might as well have used Gedit, lol. I just don't understand how people can program with those tiny viewports... Especially with python, you need that space for tabs, there should be no stuff on left/right.

My programming style: open a terminal in the folder I am using, open my source files in that folder, edit with Gedit, click on terminal, enter my compile commands... Enter my execute commands. Once I enter them, I can just press up in the terminal to get them back with the command line history.

If a project requires more than 2-4 commands to compile, I write up a makefile, and then all I have to do is type make. I don't think it's any more than clicking a menu, then a compile/run button in an IDE. Plus, gedit has tabs, so I can open multiple files when I need to. And syntax highlighting... And I really don't see the need for auto complete. So, while pmasiar thinks I'm a caveman, I just don't see a need for an IDE, especially for a language as simple as python.

---

### Post by po0f on 2006-12-27
Wybiral,

If you like GEdit, you'll probably love Kate.  It *is* a KDE app, but it is just a little more powerful (has more programming plug-ins) than GEdit.  If you can spare the RAM (>256MB), you should give it a try.

---

### Post by pmasiar on 2006-12-28
> **po0f said:**
>   I decided to look into SPE.  Guess what?  Website's down,.

Stani is just a one man, probably something got wrong while on vacations. I would be rather sad if SPE died. oh no! :-(

**Update** Stani's host went out of business, he is looking for new host. (blog is also down, but cached by google)

But you can install SPE from synaptic/apt, no need for website.

---

### Post by pmasiar on 2006-12-28
> **Wybiral said:**
> I got curious and tried SPE, ...  with python, you need that space for tabs, there should be no stuff on left/right.

I use 4-space TABs, and right edge indicator, so my lines don't grow too far to the right. If they do, printing page is confusing. IMHO if you have more than 4-5 levels of tabs, you need to refactor, not close sidebar. And with sidebar opened, refactoring is easier ;-)

> gedit has tabs

SPE has tabs too.

Maybe difference is that Wybiral mixes languages: C, make, python, and wants to use same editor for all. Tha't not my case, so I pick IDE optimalized for python. But I often use gedit to edit input text files or templates for python.

I really think that one of best SPE's features are permanent bookmarks/comments (##--- label), including label like TODO and FIXME. Really nice to see it in sidebar. Wybiral, seems to me you never used them?

---

### Post by Wybiral on 2006-12-28
> Maybe difference is that Wybiral mixes languages: C, make, python, and wants to use same editor for all.

That could very well be a good point...

Anyway, it's also not a matter of NEEDING the room for tabs, more of a discomfort issue... Having all of that extra stuff is really distracting to me.

Also, when I said "gedit has tabs" what I meant was... Gedit has tabs, so I don't have a need for the project tree on the left, I can open the files I plan to edit in tabs.

Nope, I've never used the "permanent bookmark" thing...

But I think what it sums down to is taste. I like things to be simple, and small. Not cluttered and bloated (I'm not saying SPE is btw). So, maybe this could be considered in writing an editor... Everyone will want it different, so keep *customizability* in mind.

None of the extra stuff should pop up by default, it should be an option, and should definitely be an option to shut off. Your editor should have the potential to go from the simple gedit look that people like I feel comfortable with, to having all of the tools that people like pmasiar enjoy.

I also think customization is what makes linux itself so nice (ONE of the things)... My old OS had some skin changes, but you couldn't really customize it, and it made me seek out another OS.

---

### Post by maddog39 on 2006-12-28
> ANYWAY... If you make an IDE, I recommend not adding too much stuff (as cool as it may sound) and trying to keep it small and CPU efficient... I just can't stand having a bunch of junk in the way and this [SIZE=1]tiny[/SIZE] little box to code in... I want nothing extra, some syntax highlighting, maybe a pull-down menu with tools and stuff... But big boxes rule.
Yeah I know, I hate that too. I just like to have my project manager on the side, the menus at the top, maybe with a toolbar and my code box.

> If a project requires more than 2-4 commands to compile, I write up a makefile, and then all I have to do is type make. I don't think it's any more than clicking a menu, then a compile/run button in an IDE. Plus, gedit has tabs, so I can open multiple files when I need to. And syntax highlighting... And I really don't see the need for auto complete. So, while pmasiar thinks I'm a caveman, I just don't see a need for an IDE, especially for a language as simple as python.
I dont really mind auto-completion but yeah I agree, I dont really find the need for it either. This "IDE" if I make it will end up being more of a standard programmers text editor with a few other non-standard tools. What I can't stand though in most IDE's/text editors, they dont have ANY sort of project management and that really gets to me. I really need an easy uncluttered way of accessing just the files in my project directory without any other filesystem nonesense. Also alot of editors have this stupid function/class browser on the side, wtf is that for, its like the most useless feature ever.

>  If you like GEdit, you'll probably love Kate.  It *is* a KDE app, but it is just a little more powerful (has more programming plug-ins) than GEdit. If you can spare the RAM (>256MB), you should give it a try.
I personally like Kate although I completely hate KDE. I tried compiling kate from the kde-base package and it wouldnt let me so I said screw it. I just can't stand KDE, everytime I try it and I try to like it, there is just so much that bogs me down and its entirely too slow for my PowerBook G4 (1GHz) and uses a boatload of RAM. But please, this is my personal opinion from my experience with KDE, as my experiences overall have not been good, I just seem to always run into problems with it, so please, do not turn this thread into a rant. Just thought i'd mention it.

> Stani is just a one man, probably something got wrong while on vacations. I would be rather sad if SPE died. oh no! :sad:

**Update** Stani's host went out of business, he is looking for new host. (blog is also down, but cached by google)

But you can install SPE from synaptic/apt, no need for website.
Hey! I own a webhost, I have two seperate resellers. I could host him for free on my personal reseller at a really reliable and stable host (called ASmallOrange), its got PHP4/5, Ruby on Rails, Python, MySQL, and Subversion. Someone give me his contact.

Well anyway,  I started making a basic code layout for the text editor or "IDE" in C++ and started making a few classes. Although i'm becoming increasingly scared about it. C++ is ALOT harder and this project is ALOT more challenging than I expected. I am struggling alot with compatibility between datatypes and stuff. if I want alot of flexibility, I have no choice but to use PHP-GTK, because I'm almost 3 years into active development in PHP and I understand 97% of the language and functions. I could also try PyGTK but I find it much harder to use than wxPython. The original reason I tried GTKMM/C++ is because it has the GtkSourceView widget which has built in syntax highlighting. Unfortunetly there is just NO documentation/examples WHAT SO EVER for using GtkSourceView in other languages except C, it was trial and error for 5 hours trying to get it to work. Same problem with Scintilla/wxPython, little to NO documentation/examples.

Also, I would really like to join a python project  however I would like to have direct contact with the project founder/owner and preferably a fairly small project with either no or a small amount of other developers. Thing is, i've never worked on a team before so something I really need and something that would do me alot of good. Yes, I know i'm b eing really particular lol but until i'm used to that envionrment, you know .. :/

With that said, Wybiral, tried adding you to aim but you havnt logged on yet or something. :P Also sent u a PM.

---

