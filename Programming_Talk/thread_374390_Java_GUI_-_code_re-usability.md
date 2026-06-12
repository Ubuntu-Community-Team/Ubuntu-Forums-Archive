---
title: "Java GUI - code re-usability"
date: 2007-03-02
forum: Programming Talk
---

### Post by derby007 on 2007-03-02
Could someone point me in the right direction on code re-usability as regards GUI's in Java. maybe examples.....hints......help......links.....
tnx

---

### Post by Ryba on 2007-03-02
Um ... can you be more specific. There are tons of stuff out there on code reusability and java gui and modularization and doing things in a proper MVC model.

I mean a google search on that stuff will come up with thousands of results even and while most are crap there are several decent ones.

What is it that you want exactly?

---

### Post by derby007 on 2007-03-02
Sorry i knew i was kinda brief:
I'm doing a Java-MySQL project & i'm about to start into the design of my GUI's. 
Now when I 1st started out, (while using JavaStudioEnterprise8) using drag'n'drop buttons, combo-boxs etc., and it was doing as i wanted, very basic mind u, like a password entry/checker that also set up my connection to my DB & returning results. 
I have my tables set up & normalised. BUT...... now i want to design my user interfaces, but i want to do it with re-usability in mind. 
SO....can someone point me in the right direction.......ie. the Theory behind & understanding of GUI RE_USABILITY & how its performed, eg's maybe. I've read up on JFrames, containers, RootPanes, JInternalFrames, etc. Using the one Frame for different screens, ie. just replacing buttons, textAreas etc., this is my main AIM really.
I want a main screen (after login), then different user screens to manipulate data, ie. READ and WRITE to DB.

---

### Post by laxmanb on 2007-03-03
BUMP! seems interesting... anybody got any info?

---

### Post by Tomosaur on 2007-03-03
It's kinda difficult to give examples without understanding the purpose of your GUI and how you intend it to look. One way to cut down on code is to use constructor overloading - which some people dislike but if you don't mind it, then it's pretty useful. With constructor overloading you can create very different objects using the same class file.

Alternatively, set up a basic 'new window' or 'new button' class or whatever - then just extend it for each individual object. Essentially - the main idea is to program using a generic approach. A window is a window, despite what contents are in it. No point writing two completely different window classes - just write ONE in such a way that it is easily extended and modified. By putting a greater emphasis on constructors - you can create radically different objects simply by passing different paramaters for different things.

---

### Post by derby007 on 2007-03-03
Yes, thats exactly what i am looking for, as i was creating a different Frame each time, and each Frame was settingvisible( true ) to the next one. 
Can u point me to examples ?
Would u use some of the well known (gang of four) patterns ? factory, decorator, etc.
If windows, Frames, are totally different, do u use the one frame doing the setvisible( true ) to the next one ?
tnx again...
:popcorn:

---

### Post by Tomosaur on 2007-03-03
> **derby007 said:**
> Yes, thats exactly what i am looking for, as i was creating a different Frame each time, and each Frame was settingvisible( true ) to the next one. 
Can u point me to examples ?
Would u use some of the well known (gang of four) patterns ? factory, decorator, etc.
If windows, Frames, are totally different, do u use the one frame doing the setvisible( true ) to the next one ?
tnx again...
:popcorn:

Well - for frames - try and cut down on spawning new ones as much as possible. People just don't like lots of windows. Many people use the menu bar - dual panel combo. The left panel is a context menu, the right panel is a content pane. Seamonkey uses this to great effect - check it out (although it's not written in Java). The side panel is optional, but has a bunch of useful tools. A lesser browser might choose to spawn a seperate window for each of these functions, but here, they're all organised nicely. As I said - it's more about designing in a clean-room style. It's difficult to give examples because each project is different. You really need to use this approach right from the very beginning rather than just fitting it in half way through. Clever use of interfaces, extended classes, constructor overloading etc, will allow you to do what you need to do. Once you begin, it'll gradually become obvious about how to re-use code. Always assume that your code is too verbose and that it can be shortened.

Overloading is often criticised - but as long as you're careful and you keep it to a minimum for your requirements, I see no problem with it. Many people prefer interfaces (again, extending existing objects is often criticised), but this does lead to writing more code than is strictly necessary. It's really just a matter of preference. Polymorphism can be achieved in a number of ways - and you can chop and change between different approaches to see which best suits the problem. Rather than providing you with concrete examples, it's really a better idea to just give you some generic polymorphism examples:

[Developer.com article on polymorphism in Java](http://www.developer.com/tech/article.php/966001). A nice overview with a few examples.

[Java polymorphism tutorial](http://www.tutorialized.com/tutorial/Polymorphism/4645).

[Short constructor overloading example](http://java.sys-con.com/read/38068.htm).

I couldn't find any aimed specifically at GUI development, but the principles are the same.

---

### Post by eXisor on 2007-03-03
[quote='derby007']If windows, Frames, are totally different, do u use the one frame doing the setvisible( true ) to the next one ?[/quote]

I hope I do not offend you with this, but the question reflects a basic missing understanding.

In this example you would look to the container for all the frames to do the visibility controlling. 

The owning container of the frames has direct access to it's contained frames, whereas the owned frames are peers and would have to ask their owning container to expose its member frames. This unecessary extra step is the clue that the visibility controls should lie within the owning container.

Think of an optionbutton in an optiongroup. The button has the responsibility for its initial state, off, being enabled/disabled,  and it's toggleability. It is up to the optiongroup, the container for option buttons, to make sure only one option is selected at a time, or to override the initial off state of an option if that is required.

You mentioned normalisation in an earlier post. Essentially the same principle applies to object hierarchies. **Only the functionality which belongs together and is always true for the purpose of the object belongs in the object.** 

This is the basic philosophy of OOP and is a concept you need to fully grok to set yourself free.

I would strongly recommend you evaluate the base java class hierarchies to see why they  exist. For instance; since a frame extends the container class, why was there a need to create the frame class? What purpose does it serve extra to what the container class provides?

Again, forgive the 'lesson' if inappropriate to your level of understanding.

---

### Post by phossal on 2007-03-03
> **eXisor said:**
> This is the basic philosophy of OOP and is [COLOR="SlateGray"]a concept you need to fully grok to set yourself free.[/COLOR]

lol Quality.

---

### Post by Ziggurat on 2007-03-03
Hi. This is my opinion: you mention a normalized database, great start. Now you design and implement your application COMPLETELY INDEPENDENT from the GUI. Then when you know that you have your application do what you want to do, you make the GUI.

---

### Post by derby007 on 2007-03-05
Thanks for all the help/lesson. But as i am just beginning into GUI's i dont fully grasp what u mean: 
  The owning container of the frames has direct access to it's contained frames, whereas the owned frames are peers and would have to ask their owning container to expose its member frames. This unecessary extra step is the clue that the visibility controls should lie within the owning container.

I would love to see an example of a simple GUI with a few interactive screens talking to a DB, mainly because i want to start out on the right foot........(& not the left one!)

Q. Is it a good idea to have 1 Frame, and hide/display various buttons/dialogs/internal-frames for my other interactive screens ?

I am currently reading up on RootPanes/GlassPanes etc....

---

### Post by phossal on 2007-03-05
The books on Java published by O'Reilly are filled with sample code. O'Reilly and the authors make that code available either at their main site, or the site the author has designated. The book on Swing has a nifty example of a class that extends JFrame and uses a bunch of JDBC (Database Stuff). Plus it shows how you can do cool things with  JTable to show results. There are many different examples at the site though. They basically run as is. [http://examples.oreilly.com/jswing2/code/](http://examples.oreilly.com/jswing2/code/)

Check out Chapter 15, DatabaseTest.java. Short and sweet - *very* powerful code for a beginner. ;)

---

### Post by derby007 on 2007-03-05
I think i have a good handle on Database connectivity but i will certainly check out the JTable stuff as that is exactly what i need.
 
By the way, Phossal, i went into your Website, u have some good threads there, 
but.....its all-over-the-place, ie. maybe you are in development mode at the mo, but its not USER friendly, (eg. very hard to see the light-colored text!).

---

### Post by phossal on 2007-03-05
> **derby007 said:**
> By the way, Phossal, i went into your Website, u have some good threads there, but.....its all-over-the-place, ie. maybe you are in development mode at the mo, but its not USER friendly, (eg. very hard to see the light-colored text!).
I appreciate the criticism. You're right, the lighter text is very difficult to read on *most* monitors. You've helped me come to a better understanding of what I want to accomplish with phossal.com: *nothing*. It would be much better if it was simply black serif text on a white background - much like all of my favorite sites (by the old timers). It isn't supposed to be an *experience*. It's supposed to be a place I can refer people - including myself - to get text I'm sick of typing over and over.

---

### Post by derby007 on 2007-03-05
No problem, i thought i'd let u know, cause when i opened it up, the left window thingy is overlapping onto the main text, & cause my monitor isn't great, i found it hard to see the text.....
But anyway: i'm beginning to like Java, from a programming perspective, ie. messing around with different JAR files/libraries and seeing what functions/classes they have. I really like the Decorator Pattern example i found on the Net, creating a coffee & decorating it with different choices, which all have prices :)

Q for u: i'm using SunStudioEnterprise8 and its very similar to Netbeans5, EXCEPT Netbeans has this Mattisse/FREE-DESIGN that i can't incorporate into SunStudio8? any ideas?

Also: what is the TestPackage & TestLibrary folders in the Projects window for? ie. other folders there are SourcePackages (for my source files) & Libraries (for the Libraries i want to use) ?
Phew, i'm finished....

---

### Post by phossal on 2007-03-05
Derby, I'm curious about what browser you used to access phossal.com. Did you use something other than Firefox? If so, would you consider writing the CSS for your browser? I wouldn't expect you to do it for *free*. Maybe we can work something out? ;)

---

### Post by Wybiral on 2007-03-05
> **phossal said:**
> I appreciate the criticism. You're right, the lighter text is very difficult to read on *most* monitors. You've helped me come to a better understanding of what I want to accomplish with phossal.com: *nothing*. It would be much better if it was simply black serif text on a white background - much like all of my favorite sites (by the old timers). It isn't supposed to be an *experience*. It's supposed to be a place I can refer people - including myself - to get text I'm sick of typing over and over.

I checked out your site too and I agree... I was blinded by the light colors and lack of contrast, very hard to read.

BTW, I noticed the assembly optimizer was on your site (thanks for that code again). You should extend that to take in multiple files so people can use "*" and maybe even make it overwrite the original file. I've actually used that quite a bit, it would be easier to work into makefiles and stuff if it wrote over the original file.

Anywho... The site looks good, but the colors don't contrast enough.

---

### Post by phossal on 2007-03-05
I don't disagree about the colors. They're not perfect. I think the solution I've come up with is making a link to *change* them. Then everyone can choose a color scheme that's suitable for themselves. As for other display problems, though, I would make the same offer to anyone - let me know what browser/version/monitor you're using, write the css for it, and we'll work something out.

Thanks for the input.

[Edit] Here are the changes you mentioned regarding the optimizer: [http://ubuntuforums.org/showthread.php?t=360936](http://ubuntuforums.org/showthread.php?t=360936)

---

### Post by derby007 on 2007-03-06
I aint got the time at the mo, unless a very straight foreward one.......but i can't access your site at the mo as its down.

Edit: i'm using Win2000 IntExp 6, Dell monitor 21inch CRT>>>>>>>>sssshh..work PC..

---

### Post by pmasiar on 2007-03-06
> **phossal said:**
> I don't disagree about the colors. They're not perfect. I think the solution I've come up with is making a link to *change* them. Then everyone can choose a color scheme that's suitable for themselves. 

making everyone to change/set own colors - sounds like KDE solution to me. Ubuntu user expects decent defaults :-) 

Default colors work very nice for me now (Windows/Firefox, Ubuntu feisty/Firefox, Windows/IE). IE has slight problem: main page content is too much to the left, half-inch into the "threads" box. Or "threads" box is too wide in IE?

Another problem: Site requires javascript. I do not surf random websites with JS enabled, only for selected few, if I think provided functionality mandates JS.

Basic functionality, like checking other pages on website, IMHO should NOT require JS. I understand why you used it - AJAX is cool and learning it is in my to-do list :-)

To improve usability of your site, you might find lot of interesting reading at [http://www.useit.com](http://www.useit.com) website - by one of top experts on usability Jakob Nielsen. Design of his website did not changed in 10 years, and is still usable - if not "pretty" by current standards. But IMHO very well worth reading. You can also subscribe to email alerts.

I have other suggestions on usability if you are interested.

Overall, nice page design, phossal. Good job. What web framework is it?

---

### Post by phossal on 2007-03-06
Good suggestions. All of them. With enough talented minds, it would be nearly impossible to end up with something that was beyond improvement. I'm sure Mr. C could reproduce everything I've done in one line. ;) 

As I mentioned in my response to Derby, this incarnation of phossal.com has already met every objective I set out for it. Perhaps someone *else* will find it useful in its current state. If a motivated individual recognized some *potential* and wanted to contribute, I would certainly be willing to allow it and/or contribute myself.

Thanks for the suggestions again. Cheers!

---

