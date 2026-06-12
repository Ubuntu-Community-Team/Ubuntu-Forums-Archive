---
title: "Advice in getting started with Python"
date: 2008-10-24
forum: Programming Talk
---

### Post by jukingeo on 2008-10-24
Hello All,

I am looking to interface my computer with the outside world.  I mostly would like to use it to control Haunted House props, but I do want to use it for other things as well such as making my own midi interfaces via the USB port.

EDIT:  I felt the need to edit this post because many people are getting confused that I am looking to learn a programming language to program props for THIS Halloween.  I realize that is not possible and it isn't the case.  I am not working on a haunt this year but instead helping others with their haunts (Basic Stamp programming).  However, lets just say I am getting an early jump on next year and hopefully I can be proficient enough to program by then. 

I am mostly interested in learning to program the USB and Parallel ports.

Outside of programming Basic Stamps, I don't have any programming experience.  I WOULD like to learn C++ but I really wouldn't know where to begin.

Someone recommended Python to me and a couple applets called PyUSB and PyParallel.  I noticed that Python seems to be in the Synaptic repository, so installation looks pretty easy.  However, using the program is a different matter.

Given my background and my intended control applications I would like to know where is a good place to start with learning Python.

I am also interested in any other programming language that is easy to use and has a low learning curve.

Thank You,

Geo

---

### Post by LaRoza on 2008-10-24
I suggest you stick with Python, as it has a lower learning curve (but, goes far) and is suited for this task.

Python is already installed.

I suggest you spend some time learning the language (see my wiki) first, before doing anything with USB.

If you really want to use C++ for whatever reason, my wiki is also a good place for that, however, I don't think C++ is what you need.

Gedit with its plugins (search synaptic for gedit plugins) will be the only editor you'll need. gedit is the default text editor on Ubuntu.

---

### Post by jukingeo on 2008-10-25
> **LaRoza said:**
> I suggest you stick with Python, as it has a lower learning curve (but, goes far) and is suited for this task.

Python is already installed.


Sounds great.  Where is it on my system?  I see that it is installed via the Synaptic repository, but I don't see an application launch button.  Is it something that can only be used in the terminal?


> I suggest you spend some time learning the language (see my wiki) first, before doing anything with USB.

What is your wiki?

> If you really want to use C++ for whatever reason, my wiki is also a good place for that, however, I don't think C++ is what you need.

C (or C++) is something that always came back to me some way or another.  I know it is used a lot for Windows programs and games in general...however, you are not the first to also tell me that it isn't a beginner's language.

While at this point in time I really am not into creating my own video game, I am very interested in input/output control.  Simply put, I would like to control things with my computer.

Perhaps the most involved task that I am interested in, would be to create a computer based pinball machine.  If Python could handle that with respectable speed, AND has a short learning curve, then that is definitely for me.

However, I don't want to put the cart before the horse and jump THAT far ahead to something THAT advanced.

You even mentioned not tackling USB at first.  However, I do have a parallel port on my machine and I know a Parallel I/O board is relatively easy to construct.  Also the parallel I/O is very similar to the I/O buss on a Basic Stamp.  So there is not too much more involved I/O wise.  

Overall I just would like more control options than a Basic Stamp offers.  Stamps are great, but they certainly couldn't do something like the pinball project I mentioned above.


> gedit with its plugins (search synaptic for gedit plugins) will be the only editor you'll need. gedit is the default text editor on Ubuntu.

I did see gedit-plugins on my Synaptic list and it wasn't checked off.  So I checked it off and installed it.  Once again though, I do not see any kind of program launcher anywhere.  Do you have to work with Python in the Terminal?

Thanx for the info.



Geo

---

### Post by dburnett77 on 2008-10-25
Python.org.  There's a community where they update there own code.

It's not only an adaptive program, it is.  Scripts, as well as defines are very manipulable.  What the approach seems to be differentiated from other lang's is the ability to catagorize.  Meaning, create data pools from knowns, then re-define.

This allows you to handle things like some mathematicians do with deltas.  Not static, neither.  Recursive funct's, no prob. w/ this pkg.

Gamma incursions, there built in!

It's extremely complex.

For your application, try having a few friends over to run your house:  Haunty.
You ain't got time to get into all that...

---

### Post by LaRoza on 2008-10-25
> **jukingeo said:**
> Sounds great.  Where is it on my system?  I see that it is installed via the Synaptic repository, but I don't see an application launch button.  Is it something that can only be used in the terminal?

What do you mean? It is usually in /usr/bin/python on Ubuntu, but that hardly matters.

For writing Python programs, I sugget you use gedit (labelled "Text Editor" in Accessories). It has all you need, and more.

> 
What is your wiki?

The link under all my posts that says "My Wiki". A wiki is a type of website. Wikipedia is the most famous (and the most useful).

> 
C (or C++) is something that always came back to me some way or another.  I know it is used a lot for Windows programs and games in general...however, you are not the first to also tell me that it isn't a beginner's language.

See my learn to program page, and I have recommendations for learning. These are not random ;).

C is very lowlevel. It is what Windows and Linux themselves are written in. Most apps that don't need it will be written in another language. C# and VB are popular on Windows.

> 
While at this point in time I really am not into creating my own video game, I am very interested in input/output control.  Simply put, I would like to control things with my computer.

First take the time to learn the language. This can take a short amount of time at first. Programming requires you to program. You can't exclusively look at your goal.

> 
Perhaps the most involved task that I am interested in, would be to create a computer based pinball machine.  If Python could handle that with respectable speed, AND has a short learning curve, then that is definitely for me.

Python could handle that, as could most languages. PyGame would be the module for that.

The learning curve depends on the user. For someone who asked what my wiki was, when there is a link under the post that says "My Wiki", it may be high ;) I hope it was an oversight...

> 
You even mentioned not tackling USB at first.  However, I do have a parallel port on my machine and I know a Parallel I/O board is relatively easy to construct.  Also the parallel I/O is very similar to the I/O buss on a Basic Stamp.  So there is not too much more involved I/O wise.  

It may not be hard, and is probably simple, but you should learn the language first. You'll have to tell the computer what to do with the language, so you should be fluent in it, before discussing things like USB ports. (Think of it as a spoken language, if you know philosophy really well, and want to discuss it in another language, you should master the language first, otherwise, you won't be able to express the thoughts you have)

> 
I did see gedit-plugins on my Synaptic list and it wasn't checked off.  So I checked it off and installed it.  Once again though, I do not see any kind of program launcher anywhere.  Do you have to work with Python in the Terminal?

It is in Gedit (the text editor). Go to Edit->Preferences in the text editor. I suggest you use the Embedded Python terminal and embedded terminal. The directory panel is also very useful. You'll have to go to View and check of the left and bottom panes.

Python is a programming language. Python does have an interactive prompt so you can test things and learn, but writing programs is done in a text editor.

---

### Post by The Cog on 2008-10-25
I agree that python is probably a good language for you. It is fairly easy to learn, and it is well suited to the kind of jobs you want to do. I would suggest you look at geany as the editor. 

Google for python tutorials. The first steps are using the python interactive environment which you get by typing the command **python** on the command line.

---

### Post by pmasiar on 2008-10-25
> **jukingeo said:**
> Do you have to work with Python in the Terminal

You can, but you are better off playing in Python shell (which is kinda terminal, but "understands" Python syntax). These first steps migh be confusing, bacause there are many trivial tricks which are easier to show than write about. So you may consider taking a look at ShowMeDo.com website, they have plenty of screencasts showing off Python.

Wiki in my sig (also linked from LaRoza's) has many links, including "day if IDLE toying" about using IDLE, Python's IDE. And many training tasks too, the only way to learn programming is to program a lot.

---

### Post by jukingeo on 2008-10-25
> **dburnett77 said:**
> Python.org.  There's a community where they update there own code.

It's not only an adaptive program, it is.  Scripts, as well as defines are very manipulable.  What the approach seems to be differentiated from other lang's is the ability to catagorize.  Meaning, create data pools from knowns, then re-define.

This allows you to handle things like some mathematicians do with deltas.  Not static, neither.  Recursive funct's, no prob. w/ this pkg.

Gamma incursions, there built in!

It's extremely complex.

For your application, try having a few friends over to run your house:  Haunty.
You ain't got time to get into all that...

Can it handle interrupt requests?  Most pinball machines do that.  This is something a Basic Stamp cannot do and it is very limited in that aspect.  A Basic Stamp cannot multi-tasks.

As I said earlier, a pinball machine control program would probably be the extreme of my "early" programming, so if Python can do that, then I am sure it could handle anything else.  I guess for the record I should list what I am interested in doing:

1) Halloween Haunted house prop control
2) Midi in/out via usb or parallel port
3) Automated control of machinery
4) Jukebox control system
5) Pinball machine control system

As you see...mostly input output control.

As for THIS Halloween, I am not doing a Haunt this year.  I set up a couple props (Basic Stamp) for a couple of friends.  So I am in no rush.  But I would like to know enough to pull off some computer automation for next year.

> **pmasiar said:**
> You can, but you are better off playing in Python shell (which is kinda terminal, but "understands" Python syntax). These first steps migh be confusing, bacause there are many trivial tricks which are easier to show than write about. So you may consider taking a look at ShowMeDo.com website, they have plenty of screencasts showing off Python.

Python Shell?  Is that like a front end?  I'll check out the ShowMeDo.com site.  Thanx

> Wiki in my sig (also linked from LaRoza's) has many links, including "day if IDLE toying" about using IDLE, Python's IDE. And many training tasks too, the only way to learn programming is to program a lot.

Yeah, the guy that showed me how to program the Basic Stamp said the same thing as well.  He would write a program based on what I needed and then gave tips on how to analyze the program and break it down in steps.  

That was a big help

> **The Cog said:**
> I agree that python is probably a good language for you. It is fairly easy to learn, and it is well suited to the kind of jobs you want to do. I would suggest you look at geany as the editor. 

Is that also a type of Front End?  I will try and look for it in the repositories.

Thanx for the info guys...much research to do.

Geo

---

### Post by jukingeo on 2008-10-25
> **LaRoza said:**
> What do you mean? It is usually in /usr/bin/python on Ubuntu, but that hardly matters.

Well, I didn't know that.  I was looking for an icon in the start menu to launch..."something" that said Python.

I found it in the directory you said, but when I click on it, nothing happens.

> For writing Python programs, I sugget you use gedit (labelled "Text Editor" in Accessories). It has all you need, and more.

Yes, I know gedit.  That is all you need?  How do you get it to work with the program?  As I said above, I clicked on it and it doesn't even open up.  However...it IS there.


> The link under all my posts that says "My Wiki". A wiki is a type of website. Wikipedia is the most famous (and the most useful).

Ok, gotcha


> See my learn to program page, and I have recommendations for learning. These are not random ;).

C is very lowlevel. It is what Windows and Linux themselves are written in. Most apps that don't need it will be written in another language. C# and VB are popular on Windows.

Yes, I have Visual Basic myself, but I never used it.  It was given to me and I dabbled with it for a while, but really never got into it.  That was when I kept hearing the line, "Why bother with VB, learn C++...then you can program anything".


> First take the time to learn the language. This can take a short amount of time at first. Programming requires you to program. You can't exclusively look at your goal.


Python could handle that, as could most languages. PyGame would be the module for that.

Sounds good.   Yeah, there were many simple steps to go through with the Basic Stamp.  Making the machine say "Hello World", flashing LEDs on/off.  Yeah, I know about the 'baby steps'.

> The learning curve depends on the user. For someone who asked what my wiki was, when there is a link under the post that says "My Wiki", it may be high ;) I hope it was an oversight...

That's cute :).  Yes, it was an oversight.  I also asked WHERE was your wiki, not what it was.


> It is in Gedit (the text editor). Go to Edit->Preferences in the text editor. I suggest you use the Embedded Python terminal and embedded terminal. The directory panel is also very useful. You'll have to go to View and check of the left and bottom panes.

Python is a programming language. Python does have an interactive prompt so you can test things and learn, but writing programs is done in a text editor.

Ok, I will check it out.

Thanx for the info.

Geo

---

### Post by LaRoza on 2008-10-25
> **jukingeo said:**
> Well, I didn't know that.  I was looking for an icon in the start menu to launch..."something" that said Python.

I found it in the directory you said, but when I click on it, nothing happens.

Um, you're doing it wrong ;)

Read the sticky: [http://ubuntuforums.org/showthread.php?t=692720](http://ubuntuforums.org/showthread.php?t=692720)

> 
Yes, I know gedit.  That is all you need?  How do you get it to work with the program?  As I said above, I clicked on it and it doesn't even open up.  However...it IS there.

I think you are viewing it wrong. Python is the run time for programs written in Python. By itself, it doesn't do anything.

> 
Yes, I have Visual Basic myself, but I never used it.  It was given to me and I dabbled with it for a while, but really never got into it.  

Ah, the source of confusion.

Microsoft makes a product called "Visual Studio" which is an IDE for some languages. It only works on Windows. Programming with certain languages, VB.NET, C#.NET, and others, is done almost exclusively in Visual Studio, and they are tied together. This leads to confusion with people who use Visual Studio first. You can use any editor to program, and then compile on the command line (even with Visual Studio) but people don't know that because Windows wants to sell their technology, their languages. Free alternatives are supressed. You don't need the multi hundred dollar IDE to program (and you'd be restricted to Windows). You don't need the "free" versions, called "Express" that are crippled and designed to get you hooked on them so you end up buying the full versions. 

In the free world, we use whatever we want. You can use any editor you want. 

There are IDE's that you can use, but I doubt their features would be useful for you (I don't find them useful for Python and C programming)

> That was when I kept hearing the line, "Why bother with VB, learn C++...then you can program anything".

Why bother a screw driver. Use a rock, then you can do anything. That is a very stupid attitude (not yours, the one you hear). With C++, you can't program anything. First, find out what other languages they know. I think you will find they are justifying using the harder methods. See [http://www.paulgraham.com/avg.html](http://www.paulgraham.com/avg.html)

People who have an attitude like that are called Blub Programmers. Read the above article and this post: [http://ubuntuforums.org/showthread.php?t=890695](http://ubuntuforums.org/showthread.php?t=890695)

> 
That's cute :).  Yes, it was an oversight.  I also asked WHERE was your wiki, not what it was.

Well, the link was in my sig. I think I need to add some colour to my sig, as the default link colour is hard (IMO) to notice.

---

### Post by Smygis on 2008-10-25
Uhmmm? Well lets put it this way.

Python is a language. Such as say English. You dont 'run' Python. As you dont run English. It is a bridge between you and the computer as English is a bridge between you and me. Here is how it works:

You write a textfile containg your python code using a editor such as gedit or geany. You then tell the python interpreter to run your file. This can be done in the terminal by typing "python mypythonfile". The python interpreter will then Tell the computer to do exactly what you have told it to do in the text file.

So lets do this from the begining.
Open Gedit.
Crate a new file in your homedir you call hello.py
In this file you write the following.

```

#/usr/bin/env python
# coding: UTF-8

print "Hello from python"

```

Now save the file.

Now you open a terminal and type:
```
python hello.py
```

---

### Post by LaRoza on 2008-10-25
> **Smygis said:**
> 
```

#/usr/bin/env python
# coding: UTF-8

print "Hello from python"

```

Now save the file.

Now you open a terminal and type:
```
python hello.py
```

That works, although the first two lines aren't needed.

If you mark the file as executable, the first line will tell the shell how to run it. The second line will tell the interpreter to use unicode. 

You could have just done:

```

print "Hello world"

```

And run it with python manually.

---

### Post by Smygis on 2008-10-25
When i first did try python i didn't need them ether. Or so they said.
And then i wrote my hello world in Swedish "Hallå Världen". And python spat an error in my face. thank you very much.

And since then my opinion is that they should always be there no mater what.

---

### Post by LaRoza on 2008-10-25
> **LaRoza said:**
> 
If you mark the file as executable, the first line will tell the shell how to run it. The second line will tell the interpreter to use unicode. 


> **Smygis said:**
> When i first did try python i didn't need them ether. Or so they said.
And then i wrote my hello world in Swedish "Hallå Världen". And python spat an error in my face. thank you very much.

So? I didn't say they were never needed, just that they weren't needed in that post. 

"Hello world" doesn't require unicode, so without an explanation, it adds un-needed complexity, and the shebang isn't used in your example, and is equally unexplained.

---

### Post by gomputor on 2008-10-25
> **LaRoza said:**
> You don't need the multi hundred dollar IDE to program (and you'd be restricted to Windows). You don't need the "free" versions, called "Express" that are crippled and designed to get you hooked on them so you end up buying the full versions.

Just for the record, *Visual C# 2008 Express Edition* isn't crippled at all. And now that Mono 2.0 supports Windows.Forms among others, it means that you can create a C# app in Windows and run it in Ubuntu or any other distro that has Mono installed (and vice versa). The only restriction is that you can program only in C#.

---

### Post by Smygis on 2008-10-25
> **LaRoza said:**
> So? I didn't say they were never needed, just that they weren't needed in that post. 

"Hello world" doesn't require unicode, so without an explanation, it adds un-needed complexity, and the shebang isn't used in your example, and is equally unexplained.

Well then. Explain to the guy here how he connects his exavangizmodode to his trapeziums and point to a wiki that will tell him how to squeeze orangejuice out of his GPU.

If someone bother to read between his lines you would have realized he does not even know what a programming language is. Or what an IDE is.

If he asked what the shebang line and coding declaration is i would have told him.

---

### Post by LaRoza on 2008-10-25
> **Smygis said:**
> 
If someone bother to read between his lines you would have realized he dose not even know what a programming language is. Or what an IDE is.

I am not good at reading between the lines.

> 
If he asked what the shebang line and coding declaration is i would have told him.

Why do you have such a problem with me informing? You posted an example, so I explained it for the OP's benefit.

---

### Post by LaRoza on 2008-10-25
> **gomputor said:**
> Just for the record, *Visual C# 2008 Express Edition* isn't crippled at all....The only restriction is that you can program only in C#.

That is crippled.

---

### Post by gomputor on 2008-10-25
> **LaRoza said:**
> That is crippled.

The IDE is called *Visual **C#** 2008 Express Edition*.
***C#***, it's for C#, you know that. How can an IDE for a specific language can be crippled? Because it doesn't support any other languages? But it's for C# only, it says it on the title. Is IDLE crippled because I can't edit or run any Ruby scripts from there? I don't think so!

---

### Post by Smygis on 2008-10-25
> **LaRoza said:**
> 
Why do you have such a problem with me informing? You posted an example, so I explained it for the OP's benefit.

I don't have a problem with clarification being made upon my posts. 
What i have a problem with is this sentence: "That works, although the first two lines aren't needed". The first two lines are definitely needed, only not in my example.

You are making it sound like it is something that will never ever be of any use and i only put it there to seem l33t.

> **gomputor said:**
> The IDE is called *Visual **C#** 2008 Express Edition*.
***C#***, it's for C#, you know that. How can an IDE for a specific language can be crippled? Because it doesn't support any other languages? But it's for C# only, it says it on the title. Is IDLE crippled because I can't edit or run any Ruby scripts from there? I don't think so!

It may not be crippled but it still is retarded. :)

---

### Post by LaRoza on 2008-10-25
> **gomputor said:**
> The IDE is called *Visual **C#** 2008 Express Edition*.
***C#***, it's for C#, you know that. How can an IDE for a specific language can be crippled? Because it doesn't support any other languages? But it's for C# only, it says it on the title. Is IDLE crippled because I can't edit or run any Ruby scripts from there? I don't think so!

Yes, that is crippled. It is basically an editor restricted to one language. There would be outrage if there were individual editors for languages in Linux. Gedit Python Edition.

> **Smygis said:**
> I don't have a problem with clarification being made upon my posts. 
What i have a problem with is this sentence: "That works, although the first two lines aren't needed". The first two lines are definitely needed, **only not in my example.**

The first two are not needed. You said so yourself. They can be needed, and they are useful.

> 
You are making it sound like it is something that will never ever be of any use and i only put it there to seem l33t.

Remember when I said I am not good at reading between the lines? You are reading between the letters. How can you even consider statements of facts for technical help personal attacks or otherwise based on emotion? I am not that type of person.

---

### Post by gomputor on 2008-10-25
> **LaRoza said:**
> Yes, that is crippled. It is basically an editor restricted to one language. There would be outrage if there were individual editors for languages in Linux. Gedit Python Edition.

I don't get it if all you want is to code in a specific language.
Is it wrong to have different ide's for different languages?
If I follow your way of thinking, then all the editors are crippled, gedit too.
Anyway....

---

### Post by LaRoza on 2008-10-25
> **gomputor said:**
> 
Is it wrong to have different ide's for different languages?

It has nothing to do with right or wrong. 

> 
If I follow your way of thinking, then all the editors are crippled, gedit too.
Anyway....
No, gedit is free.

---

### Post by gomputor on 2008-10-25
> **LaRoza said:**
> No, gedit is free.
Ah, ok. I suppose that's what you meant when you said in the first place that Visual Studio Express is crippled. You meant that it isn't open software, ok.
So guys, if you still wanna make any app in C# and you are on Windows, then do it in SharpDevelop. It's free and not crippled! :)

---

### Post by LaRoza on 2008-10-25
> **gomputor said:**
> So guys,
What about girls :(

> 
 if you still wanna make any app in C# and you are on Windows, then do it in SharpDevelop. It's free and not crippled! :)

Or any editor. That is freedom :-)

---

### Post by pmasiar on 2008-10-25
> **gomputor said:**
> The IDE is called *Visual **C#** 2008 Express Edition*.
***C#***, it's for C#, you know that. How can an IDE for a specific language can be crippled?

Like many other proprietary programs, this one is also designed to be "gateway drug" for full Visual Studio. Like drug dealer gives free samples to get you hooked up.

Time is not free, MSFT is aware that time spent learning VS is not spent learning Free software. Free as Freedom and free speech (libre), not free beer - VS Express is free but not Free. 

And is cripled because many Free editors can be used with many different languages, so your time learning them is better spent.

---

### Post by LaRoza on 2008-10-25
> **pmasiar said:**
> Like many other proprietary programs, this one is also designed to be "gateway drug" for full Visual Studio. Like drug dealer gives free samples to get you hooked up.

Time is not free, MSFT is aware that time spent learning VS is not spent learning Free software. Free as Freedom and free speech (libre), not free beer - VS Express is free but not Free. 


Exactly. It is not something that can be downloaded without giving away information, and its sole purpose is to be a fishhook.

---

### Post by The Cog on 2008-10-26
@jukingeo:

Ignore the needling match. To get back to the subject, the python interpreter offers you a command-line invironment in which you can enter python language lines directly, and see the results. It's a good way to experiment with a programming language and get immediate feedback.

Open a terminal (Applications, Accessories, Terminal) and type the command **python**. You are given a prompt that looks like >>> and where you can type python language like:
> >>> x=1
>>> y=2
>>> print x+y
3
>>> 
You can end the session and return to the command prompt by typing Ctrl-D.

Here is a tutorial to get you started:
[http://docs.python.org/tutorial/](http://docs.python.org/tutorial/)

I actually use the python interpreter this way quite a lot, whenever I need to work out something I can't quite do in my head. I guess others might open a spreadsheet for little calculations like that.

---

### Post by gomputor on 2008-10-26
> **LaRoza said:**
> What about girls :(
I should have suspected that you are a girl by the fact that you always want to have the last word on everything, regardless if you are right or wrong. :)

---

### Post by gomputor on 2008-10-26
> **pmasiar said:**
> Like many other proprietary programs, this one is also designed to be "gateway drug" for full Visual Studio. Like drug dealer gives free samples to get you hooked up.

Time is not free, MSFT is aware that time spent learning VS is not spent learning Free software. Free as Freedom and free speech (libre), not free beer - VS Express is free but not Free. 

And is cripled because many Free editors can be used with many different languages, so your time learning them is better spent.
Are you talking about yourself? Or are you saying that all people are the same? It didn't took me more than 10 mins to create a very simple gui app in Visual C# when I first run it. And no, I'm not using VS. Right now I'm making a Tag Editor. I'm coding it not in Python that is my beloved language, but in C#, it fits more for this task, at least for me with the libraries I chose to work. When I'm on windows I use #Develop, and when I'm on ubuntu I use geany and the command line, not MonoDevelop.
So what you've said, just doesn't apply to me and I beleive it doesn't apply to a lot of people. When I decide to make something I simply choose the tools that I find more apropriate for me for the specific task and not leting the tools use me. And I'm not a professional programmer, but you are as far as I can understand. I'm a hobbyist programmer (if I can call myself a programmer), so many things that apply to you just don't apply for me, and vice versa.

I smoke a lot. But I can't blame cigarettes for the bad health they give me. I can only blame myself for the bad habit I have.
And anything can be a bad habit, anything...
Anyway, enough off-topic, at least from me :)

---

### Post by LaRoza on 2008-10-26
> **gomputor said:**
> I should have suspected that you are a girl by the fact that you always want to have the last word on everything, regardless if you are right or wrong. :)

Sexist Fail...

If I truly wanted to have the last word on everything, and there were indeed a sign of being female, you would have thought I was a girl before I said anything. 

Please don't allow assumptions about people, especially females, leak onto the forum.

---

### Post by gomputor on 2008-10-26
> **LaRoza said:**
> Sexist Fail...

If I truly wanted to have the last word on everything, and there were indeed a sign of being female, you would have thought I was a girl before I said anything. 

Please don't allow assumptions about people, especially females, leak onto the forum.

Hey LaRoza, it was just a joke. Do I have so much bad taste of humor that it showed up like a sexist statement? What can I say...
And I trully don't care if you are a boy or a girl, or how old are you or what's the color of your skin or where you are from. I only care in what you write (you and everybody else.)

---

### Post by LaRoza on 2008-10-26
> **gomputor said:**
> Hey LaRoza, it was just a joke. Do I have so much bad taste of humor that it showed up like a sexist statement? What can I say...


Joanna, fire.

---

### Post by gomputor on 2008-10-26
> **LaRoza said:**
> Joanna, fire.
Sorry, but english is not my native language so I can't understand what that means. Anyway, you know...

---

### Post by LaRoza on 2008-10-26
> **gomputor said:**
> Sorry, but english is not my native language so I can't understand what that means. Anyway, you know...

It was a joke ;)

[http://xkcd.com/322/](http://xkcd.com/322/)

---

### Post by pmasiar on 2008-10-26
> **gomputor said:**
> Do I have so much bad taste of humor that it showed up like a sexist statement? 

yes, you do, and it did.

> What can I say...

Please just say nothing. Stay on topic, leave your gender-related prejudices and biases to yourself.

> And I trully don't care if you are a boy or a girl, or how old are you or what's the color of your skin or where you are from. I only care in what you write (you and everybody else.)

If you did, you would never wrote what you did couple posts above. Try be the person as you say you are next time. So your pet dog can be proud of you.

In case you don't know the joke, it is about saying "I hope to be the person my dog thinks I am" ;-)

And one more thing: stop smoking, you know it is wrong for you ;-)

---

### Post by gomputor on 2008-10-26
> **LaRoza said:**
> Joanna, fire.

Bobo, a link ;)

---

### Post by gomputor on 2008-10-26
> **pmasiar said:**
> yes, you do, and it did.

> What can I say...

Please just say nothing. Stay on topic, leave your gender-related prejudices and biases to yourself.

> And I trully don't care if you are a boy or a girl, or how old are you or what's the color of your skin or where you are from. I only care in what you write (you and everybody else.)

If you did, you would never wrote what you did couple posts above. Try be the person as you say you are next time. So your pet dog can be proud of you.

In case you don't know the joke, it is about saying "I hope to be the person my dog thinks I am" ;-)

And one more thing: stop smoking, you know it is wrong for you ;-)

And one thing for you: stop giving advice and look up yourself ;)

---

### Post by wmcbrine on 2008-10-26
A point that I think should be made to the OP, since he mentioned haunted house automation: You will not learn to program by Halloween. Maybe in time for *next* Halloween...

---

### Post by jukingeo on 2008-10-27
Hello guys, 

I was away from my computer yesterday and thus didn't check responses.  I been a bad boy as well and didn't do any reading up on Python as of yet.  However, coming back today I was amazed at the explosion (and some more confusion as well) here in this post.  I tried to follow along but did get lost on the way.


> **LaRoza said:**
> Um, you're doing it wrong ;)

Read the sticky: [http://ubuntuforums.org/showthread.php?t=692720](http://ubuntuforums.org/showthread.php?t=692720)


I think you are viewing it wrong. Python is the run time for programs written in Python. By itself, it doesn't do anything.

Well, I have to read up more on it.  Usually there is some sort of compiler or program that has to be 'turned on'.  With Dos, Basic Stamps, Visual Basic, there always some kind of program.  So that is what I was looking for...something to turn on to enter the source code in.  Sure it is easy to say use a text editor, but doesn't something have to be invoked to tell the system that you are creating a file for Python?


> Ah, the source of confusion.

Microsoft makes a product called "Visual Studio" which is an IDE for some languages. It only works on Windows. Programming with certain languages, VB.NET, C#.NET, and others, is done almost exclusively in Visual Studio, and they are tied together. This leads to confusion with people who use Visual Studio first. You can use any editor to program, and then compile on the command line (even with Visual Studio) but people don't know that because Windows wants to sell their technology, their languages. Free alternatives are supressed. You don't need the multi hundred dollar IDE to program (and you'd be restricted to Windows). You don't need the "free" versions, called "Express" that are crippled and designed to get you hooked on them so you end up buying the full versions. 

In the free world, we use whatever we want. You can use any editor you want. 

Well, that is one of the reasons why I was turned on to Linux.  Not necessarily because of the "free" part, but because of the big corporation part.  I much rather would work with a programming language/system that I could pop in just about any OS and have it work. For example...I have a JRE (Java Runtime) program that I use in Windows, and I am happy to say that JRE is also supported in Linux, so with JRE installed in Linux, I was just able to move my program over and it runs fine in Linux.  After learning that I decided to not bother with learning VB.  I would learn Java first. But as I take it, that isn't an easy language to work with, correct? 

> Why bother a screw driver. Use a rock, then you can do anything. That is a very stupid attitude (not yours, the one you hear). With C++, you can't program anything. First, find out what other languages they know. I think you will find they are justifying using the harder methods. See [http://www.paulgraham.com/avg.html](http://www.paulgraham.com/avg.html)

People who have an attitude like that are called Blub Programmers. Read the above article and this post: [http://ubuntuforums.org/showthread.php?t=890695](http://ubuntuforums.org/showthread.php?t=890695)

I will read those posts later on as I am at work right now. I am surprised that you are saying that C++ cannot program anything?  I always thought it could.  But I am not one to speak for myself because I have not played around with the language.  I DID see what it looks like and it is far from being intuative and straight forward.  Visual Basic was the first language I said, "Ok, this doesn't look too bad".  I just didn't do too much with it because it was just "so big".   I wanted to start smaller and I did with the Basic Stamps.  While I am still far from an expert with those, I can program them to do decent I/O tasks.  

> Well, the link was in my sig. I think I need to add some colour to my sig, as the default link colour is hard (IMO) to notice.

That was probably why I didn't pay attention to it the first time around.

As I said before there is still much I have to read up on.  I tried to follow along here, but there seems to be quite a bit of bantering going on later in this thread (while I was gone) and I was getting confused again.So my apologies if I don't respond to everyone.

Thanx,
Geo

---

### Post by jukingeo on 2008-10-27
> **wmcbrine said:**
> A point that I think should be made to the OP, since he mentioned haunted house automation: You will not learn to program by Halloween. Maybe in time for *next* Halloween...

I never said that I needed to do this by THIS halloween.  I am not doing a haunt project this year (although I am helping others out with haunts instead).  BUT I probably will be back next year!

I did edit my first post just now to mention this as well so hopefully new readers will understand that I am not looking to do this for THIS Halloween, but more then likely I will be back to do it next year.  So lets just say I am thinking "early" for next year.

---

### Post by udrage on 2008-12-16
Ok I am currently in about my 3rd week of learning to program myself. I found this forum while searching for answers myself.

You are in the perfect situation.

Heres your solution.

[http://greenteapress.com/thinkpython/thinkCSpy/](http://greenteapress.com/thinkpython/thinkCSpy/)

How to Think Like a Computer Scientist: Learning with Python

Its open source due to the GNU Free Documentation License.
About half way down the page you can even download the PDF format of it so you dont have to surf to it every time you want to read it.

It is originally based from 
How to Think Like a Computer Scientist: Learning with Java.
Which is one of the most recommended books for programming of all times (if you checked your search results back in the early 90's :P) and then a high school teacher got a hold of it. Between the original author, the high school teacher, and a pro programmer, they came up with this book. Being a COMPLETE scrub when I started, I finished this book in 3 weeks and am now going back through it as a touch up to make sure i covered/understood everything and have moved on to harder tasks.(You might go through the book faster since I have the completed version of the book and this is a "manuscript copy" not the finished product) It has a lot of good mathematical skills, programming skills, problem solving skills, and actual walk through examples. It also has several built in personal challenges (tweaks on examples that make you think and try to work what you already know and what you don't to progress your skill as far as your willing to push.)   

I think even though this post is a couple months old you could still REALLY benefit from this book.

---

