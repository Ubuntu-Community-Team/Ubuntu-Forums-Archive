---
title: "How do make Forms in Eclipse?"
date: 2011-08-27
forum: Programming Talk
---

### Post by edwardpatch1 on 2011-08-27
How do i make forms in eclispe :)

---

### Post by apollothethird on 2011-08-27
> **edwardpatch1 said:**
> How do i make forms in eclispe :)

Hi, Edwardpatch1.  I haven't used forms with Eclipse and C++ yet.  I'm performing some research for a forms plugin for Eclipse and will make a recommendation based on what I find.

If someone else are familiar with available Eclipse, C++, and creating forms, I'm sure they will chime in.

By the way, I'm currently looking at wxWidgets.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by edwardpatch1 on 2011-08-27
> **apollothethird said:**
> Hi, Edwardpatch1.  I haven't used forms with Eclipse and C++ yet.  I'm performing some research for a forms plugin for Eclipse and will make a recommendation based on what I find.

If someone else are familiar with available Eclipse, C++, and creating forms, I'm sure they will chime in.

By the way, I'm currently looking at wxWidgets.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

ok

---

### Post by apollothethird on 2011-08-27
> **edwardpatch1 said:**
> ok

Hi, Edwardpatch1.

I'm still working on becoming familiar with using forms with Eclipse.  I'll give you some of what I've come up with so far so that you can experiment with it.  Many someone familiar with it (or something different) will chime in.  If someone does, there's a good chance that I'll be learning at the same time that you learn.

I haven't set it up yet, but when I get a chance I'll be starting with the steps on this page:

Using wXWidgets in eclipse:
[http://max.berger.name/howto/wxWidgets/wxWidgets_Eclipse.jsp#d43e41](http://max.berger.name/howto/wxWidgets/wxWidgets_Eclipse.jsp#d43e41)

There are setup steps and a Sample Hello World Program.  There are a lot of steps involved.  Since I haven't done it yet I won't be sure it'll work  But it's a start and something you can look at while I find time to test it.

I'm sure it's substantially complicated for a new user like you.  But, again, its something you can look at for now and I'll go over the steps about it later.

Again, if someone comes up with an easier form implantation for Eclipse and C++, hopefully they will chime in.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by edwardpatch1 on 2011-08-28
> **apollothethird said:**
> Hi, Edwardpatch1.

I'm still working on becoming familiar with using forms with Eclipse.  I'll give you some of what I've come up with so far so that you can experiment with it.  Many someone familiar with it (or something different) will chime in.  If someone does, there's a good chance that I'll be learning at the same time that you learn.

I haven't set it up yet, but when I get a chance I'll be starting with the steps on this page:

Using wXWidgets in eclipse:
[http://max.berger.name/howto/wxWidgets/wxWidgets_Eclipse.jsp#d43e41](http://max.berger.name/howto/wxWidgets/wxWidgets_Eclipse.jsp#d43e41)

There are setup steps and a Sample Hello World Program.  There are a lot of steps involved.  Since I haven't done it yet I won't be sure it'll work  But it's a start and something you can look at while I find time to test it.

I'm sure it's substantially complicated for a new user like you.  But, again, its something you can look at for now and I'll go over the steps about it later.

Again, if someone comes up with an easier form implantation for Eclipse and C++, hopefully they will chime in.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

hi i know a friend who uses netbeans its gd for c++ java and more

---

### Post by apollothethird on 2011-08-28
> **edwardpatch1 said:**
> hi i know a friend who uses netbeans its gd for c++ java and more

Yes.  the forms are native in Java with Eclipse also.

I'll be glad to help you with the C++ project in Eclipse if you would like.  I'd look forward to some programming contribution on your part if I'm to contribute.  Some educational value would be lost if I did all the work.

Also, I believe there would be more contribution from other forum members base on efforts they see on your part.

You'd be more in position to contribute if you understood the IDE environment better.  It would go both for Eclipse and Netbeans if you decide to change IDE's.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by edwardpatch1 on 2011-08-28
> **apollothethird said:**
> Yes.  the forms are native in Java with Eclipse also.

I'll be glad to help you with the C++ project in Eclipse if you would like.  I'd look forward to some programming contribution on your part if I'm to contribute.  Some educational value would be lost if I did all the work.

Also, I believe there would be more contribution from other forum members base on efforts they see on your part.

You'd be more in position to contribute if you understood the IDE environment better.  It would go both for Eclipse and Netbeans if you decide to change IDE's.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)
shall i take netbeans?

---

### Post by forrestcupp on 2011-08-28
Edward, you have to keep in mind that programming in Linux and C++ is going to be a lot different than programming in Visual Basic with .Net. There are no forms built into C++. You'll have to learn a whole new way of programming. If you want an easier way to program a GUI, you need to look up wxWidgets, GTK+, or Qt. They are all frameworks that make programming GUIs easier.

But no one on here has the time to teach you all about programming GUIs in a thread. You'll have to go to their web sites and look for tutorials and documentation.

But if you want to program in a somewhat familiar environment to .Net, you can learn to program in C# with Mono using [MonoDevelop](http://monodevelop.com/). I really think that's probably your best bet. It will be the most similar thing to what you are used to in Visual Studio.

---

### Post by edwardpatch1 on 2011-08-28
> **forrestcupp said:**
> Edward, you have to keep in mind that programming in Linux and C++ is going to be a lot different than programming in Visual Basic with .Net. There are no forms built into C++. You'll have to learn a whole new way of programming. If you want an easier way to program a GUI, you need to look up wxWidgets, GTK+, or Qt. They are all frameworks that make programming GUIs easier.

But no one on here has the time to teach you all about programming GUIs in a thread. You'll have to go to their web sites and look for tutorials and documentation.

But if you want to program in a somewhat familiar environment to .Net, you can learn to program in C# with Mono using [MonoDevelop](http://monodevelop.com/). I really think that's probably your best bet. It will be the most similar thing to what you are used to in Visual Studio.
i just downloaded netbeans and that should be easy a friend said :)

---

### Post by apollothethird on 2011-08-28
> **edwardpatch1 said:**
> shall i take netbeans?

I have used both.  I find Eclipse to be easier and have more facility.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by edwardpatch1 on 2011-08-28
> **apollothethird said:**
> I have used both.  I find Eclipse to be easier and have more facility.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

so how do i make forms

---

### Post by apollothethird on 2011-08-28
> **edwardpatch1 said:**
> so how do i make forms

One of the things that attracted me to Eclipse is its very wide and versatile support for many addons. If I were going to program only in Java I would have stayed with Netbeans which I used for a long time.

When I first started with Netbeans, the first thing I did was to go through one of the tutorials so that I could get familiar with the environment, and my questions for support would have more meaning. I did the same thing when I went to Eclipse... performed the tutorial to become familiar with the environment.

I believe if you would do this same thing you'd have a better learning curb on the IDE platform you choose, whether it's Netbeans or Eclipse.

I'd be glad to work with you on setting up and using Forms, but it'd be very cumbersome to try to do this if you can't navigate the environment.

I asked you to send me the HelloWorld program that you created with Eclipse. I believe it's a kind of simple task. If you had done that, you'd be very familiar with Eclipse and it'd be fairly easy to add the forms plugins., and start to use them.

I was surprised at how quickly you had produced the HelloWorld program, because I hadn't made it though (this time). By the time I completed the Helloworld program I noticed the one I did and the one you uploaded was significantly different. It became apparent that you didn't go through the tutorial and become familiar with the IDE. You uploaded the program that you compiled from the terminal.

That was a good feat working with the terminal and creating the helloworld program. However, it'd be very hard to make form applications working at the terminal. You'd best use an IDE for that. If you perform the first tutorial you'd become familiar with the IDE and find it easier to follow the steps for form development.

I know you installed the C/C++ Development tools into Eclipse. But since you didn't do the tutorial, I'm not sure if you have actually configured the actually C++ compiler into Eclipse. The C compiler (as well as the Java compiler) is not installed with the IDE tools. So, my suggestion is for you to save a lot of time and get familiar with the IDE environment and perform the first tutorial. Once you are familiar with the environment, your questions will be more academic... sound more like a programmer, and you'd get better assistance for the bulk of the users.

If you ask questions on most forums and it sounds like you haven't done any of the tutorials and become familiar with the documentation, your questions would be ignored, or have short answers suggesting that you read the manual and show examples of what you've done so far.

I'm sorry for such a long message. I feel like I should type more to make it clear and more friendly. But if it becomes too long it the point might become lost.

I'm mainly suggesting that you perform the tutorial in the previous thread you started, then I'll install all the plugins necessary to achieve your goal (on my computer) so that I can assist you with any of the problems you're having.

If you don't, I'd probably be wasting a lot of time, because it'd be you'd be trying to use an environment that you can't navigate.

If you do the eclipse tutorial, it'd even help you even if you decide to use Netbeans instead.

I'm not sure if Netbeans have support for Python and Webpage (HTML) development, but Eclipse has support for just about any programming Language you might become interested in. All the plugins for all the different languages are independently developed. So that's a good thing also. If as new facilities become available in the various programming languages, the independent developers upgrades the plugins quicker, than it just waiting for the next edition of Eclipse (or Netbeans).

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by edwardpatch1 on 2011-08-28
> **apollothethird said:**
> One of the things that attracted me to Eclipse is its very wide and versatile support for many addons. If I were going to program only in Java I would have stayed with Netbeans which I used for a long time.

When I first started with Netbeans, the first thing I did was to go through one of the tutorials so that I could get familiar with the environment, and my questions for support would have more meaning. I did the same thing when I went to Eclipse... performed the tutorial to become familiar with the environment.

I believe if you would do this same thing you'd have a better learning curb on the IDE platform you choose, whether it's Netbeans or Eclipse.

I'd be glad to work with you on setting up and using Forms, but it'd be very cumbersome to try to do this if you can't navigate the environment.

I asked you to send me the HelloWorld program that you created with Eclipse. I believe it's a kind of simple task. If you had done that, you'd be very familiar with Eclipse and it'd be fairly easy to add the forms plugins., and start to use them.

I was surprised at how quickly you had produced the HelloWorld program, because I hadn't made it though (this time). By the time I completed the Helloworld program I noticed the one I did and the one you uploaded was significantly different. It became apparent that you didn't go through the tutorial and become familiar with the IDE. You uploaded the program that you compiled from the terminal.

That was a good feat working with the terminal and creating the helloworld program. However, it'd be very hard to make form applications working at the terminal. You'd best use an IDE for that. If you perform the first tutorial you'd become familiar with the IDE and find it easier to follow the steps for form development.

I know you installed the C/C++ Development tools into Eclipse. But since you didn't do the tutorial, I'm not sure if you have actually configured the actually C++ compiler into Eclipse. The C compiler (as well as the Java compiler) is not installed with the IDE tools. So, my suggestion is for you to save a lot of time and get familiar with the IDE environment and perform the first tutorial. Once you are familiar with the environment, your questions will be more academic... sound more like a programmer, and you'd get better assistance for the bulk of the users.

If you ask questions on most forums and it sounds like you haven't done any of the tutorials and become familiar with the documentation, your questions would be ignored, or have short answers suggesting that you read the manual and show examples of what you've done so far.

I'm sorry for such a long message. I feel like I should type more to make it clear and more friendly. But if it becomes too long it the point might become lost.

I'm mainly suggesting that you perform the tutorial in the previous thread you started, then I'll install all the plugins necessary to achieve your goal (on my computer) so that I can assist you with any of the problems you're having.

If you don't, I'd probably be wasting a lot of time, because it'd be you'd be trying to use an environment that you can't navigate.

If you do the eclipse tutorial, it'd even help you even if you decide to use Netbeans instead.

I'm not sure if Netbeans have support for Python and Webpage (HTML) development, but Eclipse has support for just about any programming Language you might become interested in. All the plugins for all the different languages are independently developed. So that's a good thing also. If as new facilities become available in the various programming languages, the independent developers upgrades the plugins quicker, than it just waiting for the next edition of Eclipse (or Netbeans).

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)
what do you mean??/

---

### Post by apollothethird on 2011-08-28
> **edwardpatch1 said:**
> what do you mean??/

Get to know the IDE environment by performing the tutorial in this thread:

How to download a programming language:
[http://ubuntuforums.org/showpost.php?p=11192885&postcount=253](http://ubuntuforums.org/showpost.php?p=11192885&postcount=253)

Go further than step 2 and it'll be easier for you to install the form plugins and use them.

Respond to that message with where you're stuck at on step 2.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by edwardpatch1 on 2011-08-28
> **apollothethird said:**
> Get to know the IDE environment by performing the tutorial in this thread:

How to download a programming language:
[http://ubuntuforums.org/showpost.php?p=11192885&postcount=253](http://ubuntuforums.org/showpost.php?p=11192885&postcount=253)

Go further than step 2 and it'll be easier for you to install the form plugins and use them.

Respond to that message with where you're stuck at on step 2.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

what u mean ?? for eclispe or net beans

---

### Post by apollothethird on 2011-08-28
> **edwardpatch1 said:**
> what u mean ?? for eclispe or net beans

I mean if you want to program you'll have to be able to go further than one step in the tutorial.  You only when one step.  That's not far enough.  It doesn't appear as if you're trying.  It takes actually takes lots of work to program.  You only did one step in the tutorial.  That's not enough work.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by edwardpatch1 on 2011-08-28
> **apollothethird said:**
> I mean if you want to program you'll have to be able to go further than one step in the tutorial.  You only when one step.  That's not far enough.  It doesn't appear as if you're trying.  It takes actually takes lots of work to program.  You only did one step in the tutorial.  That's not enough work.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

i did go past step 2 ages ago

---

### Post by apollothethird on 2011-08-28
> **edwardpatch1 said:**
> i did go past step 2 ages ago

I can't tell from the thread that you did.  If you completed the tutorial, please reply to the thread and upload the Hello World file... the one from the terminal.  Not the one from the terminal.

Look at the message I liked.  You said you got stuck at step 2 and didn't type any more.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by edwardpatch1 on 2011-08-28
> **apollothethird said:**
> I can't tell from the thread that you did.  If you completed the tutorial, please reply to the thread and upload the Hello World file... the one from the terminal.  Not the one from the terminal.

Look at the message I liked.  You said you got stuck at step 2 and didn't type any more.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

i sent u the one made from eclispe it wanted me to do hello world thing

---

### Post by apollothethird on 2011-08-28
> **edwardpatch1 said:**
> i sent u the one made from eclispe it wanted me to do hello world thing

Was that the one in the tutorial?  If you performed the tutorial, I'm impressed.  You performed it substantially faster than I did.

I'm surprised the your output is different than mine.

Will you do two things?

1) Reply to the other thread ( [http://ubuntuforums.org/showthread.php?t=1832247&page=26](http://ubuntuforums.org/showthread.php?t=1832247&page=26) );

2) In your reply post the "HelloWord" code to a message (or post an image of Eclipse with the code)?

I have an important comment to make about the code.

After that is done, I'll come back to this thread and only talk about making forms.

(Edit:  If you completed the tutorial, you won't have any problems at all with the forms.)

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by apollothethird on 2011-08-28
> **edwardpatch1 said:**
> ????????????????????????

????????????????????????

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by cgroza on 2011-08-28
Hello OP.

You have to understand that no one is going to teach you writing programs and GUIs here. You will have to find tutorials and documentation and study them.
I am sure there is documentation out there about how to make forms in Eclipse, since it is pretty popular, just look for it and read it.

The current approach you take is wrong and won't lead you anywhere.

We are glad to help you find solutions for problems, but we don't teach programming and IDEs here.
Plenty of resources for that already exist.
Sorry.

---

### Post by edwardpatch1 on 2011-08-28
ok

---

### Post by forrestcupp on 2011-08-28
Edward, are you just getting a laugh from riling everyone up?

If you want to easily make forms like you did in Visual Basic, you need to forget about Eclipse and Netbeans and install [MonoDevelop](http://monodevelop.com/). You can use it to program in C# or Visual Basic, which is what you said you were used to in Windows. If you use MonoDevelop to program in C#, it even has a visual designer where you can visually design your forms, just like in Visual Basic. The only thing is, it generates the code in C# instead of Visual Basic, so you'll also need to learn the C# programming language for Mono and GTK# instead of the regular .Net version. If you really have to use the .Net way of programming, you just need to go back to Windows.

[This tutorial](http://zetcode.com/tutorials/monowinformstutorial/) is a good place to start for learning C# with Mono. At the bottom of that page are links to other good tutorials to check out after that one.

I strongly encourage you to go this route because it is the closest thing to what you have experience with, and you seem to be having a lot of trouble with everything else. MonoDevelop will let you visually design your forms.

---

### Post by apollothethird on 2011-08-28
> **forrestcupp said:**
> Edward, are you just getting a laugh from riling everyone up?

If you want to easily make forms like you did in Visual Basic, you need to forget about Eclipse and Netbeans and install [MonoDevelop]("http://monodevelop.com/"). You can use it to program in C# or Visual Basic, which is what you said you were used to in Windows. If you use MonoDevelop to program in C#, it even has a visual designer where you can visually design your forms, just like in Visual Basic. The only thing is, it generates the code in C# instead of Visual Basic, so you'll also need to learn the C# programming language for Mono and GTK# instead of the regular .Net version. If you really have to use the .Net way of programming, you just need to go back to Windows.

[This tutorial]("http://zetcode.com/tutorials/monowinformstutorial/") is a good place to start for learning C# with Mono. At the bottom of that page are links to other good tutorials to check out after that one.

I strongly encourage you to go this route because it is the closest thing to what you have experience with, and you seem to be having a lot of trouble with everything else. MonoDevelop will let you visually design your forms.

Hi, Forrestcupp.  I'm sure you know, though you most likely linked the MonoDevelop support site for general information, that MonoDevelop is available from the Ubuntu repo.  It can be installed just by typing it in the Launch menu.

Also, C# and .Net is supported by Eclipse.  Windowsbuilder Pro is another such plug in for Eclipse.

By the way, typing the various IDE's into Synaptic shows and interesting description for them.  Look at what is says when you highlight Netbeans;  look at what it says when you hightlight MonoDevelop;  look at what it says when you highlight Eclipse.

You've probably already mentioned it, but I'm curious.  Which IDE do you use?

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by Nyromith on 2011-08-28
Obvious troll.

---

### Post by edwardpatch1 on 2011-08-29
> **apollothethird said:**
> Hi, Forrestcupp.  I'm sure you know, though you most likely linked the MonoDevelop support site for general information, that MonoDevelop is available from the Ubuntu repo.  It can be installed just by typing it in the Launch menu.

Also, C# and .Net is supported by Eclipse.  Windowsbuilder Pro is another such plug in for Eclipse.

By the way, typing the various IDE's into Synaptic shows and interesting description for them.  Look at what is says when you highlight Netbeans;  look at what it says when you hightlight MonoDevelop;  look at what it says when you highlight Eclipse.

You've probably already mentioned it, but I'm curious.  Which IDE do you use?

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)
IDE do you mean the software or the coding

---

### Post by edwardpatch1 on 2011-08-29
> **forrestcupp said:**
> Edward, are you just getting a laugh from riling everyone up?

If you want to easily make forms like you did in Visual Basic, you need to forget about Eclipse and Netbeans and install [MonoDevelop](http://monodevelop.com/). You can use it to program in C# or Visual Basic, which is what you said you were used to in Windows. If you use MonoDevelop to program in C#, it even has a visual designer where you can visually design your forms, just like in Visual Basic. The only thing is, it generates the code in C# instead of Visual Basic, so you'll also need to learn the C# programming language for Monos and GTK# instead of the regular .Net version. If you really have to use the .Net way of programming, you just need to go back to Windows.

[This tutorial](http://zetcode.com/tutorials/monowinformstutorial/) is a good place to start for learning C# with Mono. At the bottom of that page are links to other good tutorials to check out after that one.

I strongly encourage you to go this route because it is the closest thing to what you have experience with, and you seem to be having a lot of trouble with everything else. MonoDevelop will let you visually design your forms.
i downloaded monodevelop but doesn it do c++ ??

---

### Post by apollothethird on 2011-08-29
> **edwardpatch1 said:**
> IDE do you mean the software or the coding

I mean Integrated Programming Environment.  You can say it's the software.  Currently in your case it's Eclipse.  Before you came to Linux it was Microsoft Visual Studio (or Visual C++)..

The IDE (Integrated Development Environment) will usually at minimum have an Editor to write the program.  
That's equivalent to the Gedit that you used to write your silly.cpp program on the terminal.  It'll have the compiler for compiling the program (instead of having to go and run a different program).  This is equivalent to the "gcc" command that you used to compile the silly.cpp program.  It'll have some type of errors and warning display.  This is what you saw after you compiled the program if you had made a mistake with your compiling.  Most good IDE's will show you these compiling errors while you're writing the program in the editor so that you can fix it while you're typing.  When you were writing in the terminal you had left out a closing bracket and didn't know that until you had tried to compile the program and it didn't work.

The IDE will usually have lots of debugging tools also.  You'll usually see something like a "Play" button where you can run the program from the IDE to see what it does.  While playing the program you can mark it to stop at certain parts of the program while you inspect the code to see what's happening.  You can also step through the code to see if it will execute the lines in the order you intended them to.

Many people have more than one IDE for various programming they perform on their computers.  Some IDE's are easier to use for certain tasks.

In your other thread when you asked about downloading a programming language, many of the users were suggesting that you start out by using the terminal and doing everything by hand.  I have been kind of consistent with a suggestion to grab a very full IDE and become familiar with using that.

In the course of your quest you've also been given lots of suggestions concerning which program to use.  Some of them include Perl, Python, C#, C++, Visual Basic and a number of others.

I suggested using Eclipse because it has support for just about any program you might decide to use.  It's very powerful.  Once you learn to use the environment if you change programming language for any reason, you'll still have the familiar environment of the one IDE to use.

There are many other reasons for my suggestion of Eclipse, but I'll try to keep the message as short as I can.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by edwardpatch1 on 2011-08-29
> **apollothethird said:**
> I mean Integrated Programming Environment.  You can say it's the software.  Currently in your case it's Eclipse.  Before you came to Linux it was Microsoft Visual Studio (or Visual C++)..

The IDE (Integrated Development Environment) will usually at minimum have an Editor to write the program.  
That's equivalent to the Gedit that you used to write your silly.cpp program on the terminal.  It'll have the compiler for compiling the program (instead of having to go and run a different program).  This is equivalent to the "gcc" command that you used to compile the silly.cpp program.  It'll have some type of errors and warning display.  This is what you saw after you compiled the program if you had made a mistake with your compiling.  Most good IDE's will show you these compiling errors while you're writing the program in the editor so that you can fix it while you're typing.  When you were writing in the terminal you had left out a closing bracket and didn't know that until you had tried to compile the program and it didn't work.

The IDE will usually have lots of debugging tools also.  You'll usually see something like a "Play" button where you can run the program from the IDE to see what it does.  While playing the program you can mark it to stop at certain parts of the program while you inspect the code to see what's happening.  You can also step through the code to see if it will execute the lines in the order you intended them to.

Many people have more than one IDE for various programming they perform on their computers.  Some IDE's are easier to use for certain tasks.

In your other thread when you asked about downloading a programming language, many of the users were suggesting that you start out by using the terminal and doing everything by hand.  I have been kind of consistent with a suggestion to grab a very full IDE and become familiar with using that.

In the course of your quest you've also been given lots of suggestions concerning which program to use.  Some of them include Perl, Python, C#, C++, Visual Basic and a number of others.

I suggested using Eclipse because it has support for just about any program you might decide to use.  It's very powerful.  Once you learn to use the environment if you change programming language for any reason, you'll still have the familiar environment of the one IDE to use.

There are many other reasons for my suggestion of Eclipse, but I'll try to keep the message as short as I can.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")
So what do i do ????

---

### Post by apollothethird on 2011-08-29
> **edwardpatch1 said:**
> So what do i do ????

You have lots of suggestions for lots of people that have different approaches.  Many of them are suggesting that you change your programming language or change your IDE or both.  I'm suggesting that you become familiar with using Eclipse and the programming language you have already chosen.

You can do this by completing the tutorial in your other thread.  I believe if you complete the tutorial you'll start understanding the IDE and C++ well enough to have a good start for the other advance things you want to do.

I'm not telling you not to do all the other things that have been suggested to you, such as using the terminal.  But while you consider doing some of the other suggestions, performing the completing the tutorial would still be a great accomplishment under your belt.

If you performed the tutorial, I believe even if you decide to use Monodevelop for your project, it'd be easier to use it because you learned some important things about using the IDE.  They all have enough similarity that you'll always have a great learning curb if you use a different one.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3..com/~ljames](www.apollo3..com/~ljames)

---

### Post by edwardpatch1 on 2011-08-29
> **apollothethird said:**
> You have lots of suggestions for lots of people that have different approaches.  Many of them are suggesting that you change your programming language or change your IDE or both.  I'm suggesting that you become familiar with using Eclipse and the programming language you have already chosen.

You can do this by completing the tutorial in your other thread.  I believe if you complete the tutorial you'll start understanding the IDE and C++ well enough to have a good start for the other advance things you want to do.

I'm not telling you not to do all the other things that have been suggested to you, such as using the terminal.  But while you consider doing some of the other suggestions, performing the completing the tutorial would still be a great accomplishment under your belt.

If you performed the tutorial, I believe even if you decide to use Monodevelop for your project, it'd be easier to use it because you learned some important things about using the IDE.  They all have enough similarity that you'll always have a great learning curb if you use a different one.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3..com/~ljames](www.apollo3..com/~ljames)
what u mean

---

### Post by cgroza on 2011-08-29
> **edwardpatch1 said:**
> what u mean
What do you mean?

---

### Post by edwardpatch1 on 2011-08-29
> **cgroza said:**
> What do you mean?

im stuck thats what i mean hehe

---

### Post by apollothethird on 2011-08-29
> **edwardpatch1 said:**
> what u mean

I put too much in my last message.  You asked me did IDE man software or coding.  The quick answer is it's software used for coding.

> **edwardpatch1 said:**
> im stuck thats what i mean hehe

You'd be less stuck if you completed a tutorial on some of the software.  Try performing the tutorial on programming HelloWorld using Eclipse and C++.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by edwardpatch1 on 2011-08-29
> **apollothethird said:**
> I put too much in my last message.  You asked me did IDE man software or coding.  The quick answer is it's software used for coding.



You'd be less stuck if you completed a tutorial on some of the software.  Try performing the tutorial on programming HelloWorld using Eclipse and C++.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

i did complete it i done what it said to

---

### Post by cgroza on 2011-08-29
So as far as I understand, you just wrote a Hello World program and you already want to learn GUI programming?
No offence, but you don't know how the learning process works.
I suggest you:
Buy a book that teaches the language you want.
Study it.
Learn about classes, objects, inheritance and polymorphism.
Try a GUI tutorial.
 
I am sorry but programming is not a game. (I admit it can be fun though.)

---

### Post by edwardpatch1 on 2011-08-29
> **cgroza said:**
> So as far as I understand, you just wrote a Hello World program and you already want to learn GUI programming?
No offence, but you don't know how the learning process works.
I suggest you:
Buy a book that teaches the language you want.
Study it.
Learn about classes, objects, inheritance and polymorphism.
Try a GUI tutorial.
 
I am sorry but programming is not a game. (I admit it can be fun though.)

but its not fun if you cant design the form 
:(

---

### Post by apollothethird on 2011-08-29
> **edwardpatch1 said:**
> i did complete it i done what it said to

If you really completed it, you're further ahead than I think.  I can't tell that you completed it.  You stopped responding to the messages in that thread.

If you will update the other thread that you started by posting the code from Eclipse that you compiled I have a comment about the code, but need to see it.

If you don't know how to get to the code of the program, you probably missed that important part of the tutorial.

Again, there are just a few parts of the tutorial that I want to help you to understand, then I'd be glad to type in this thread about forms.

The tutorial is a step that has to be done and actually understood.  The forms is another step.  You can't get to the forms step without understanding the tutorial.

Saying you did it, and actually showing parts of the tutorial are different things.  You have to show me the parts so that I can show you from those parts where to put the forms, in this thread.

Someone else might have a different method of answering your question.  But this is my method.

Again, your question is how to do the forms.  My answer is finish the tutorial in the other thread, then I'll talk about the forms.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by apollothethird on 2011-08-29
> **edwardpatch1 said:**
> but its not fun if you cant design the form 
:(

And you can't design forms if you don't understand how to use the application.  The tutorial will show you how to use the application.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by edwardpatch1 on 2011-08-29
> **apollothethird said:**
> If you really completed it, you're further ahead than I think.  I can't tell that you completed it.  You stopped responding to the messages in that thread.

If you will update the other thread that you started by posting the code from Eclipse that you compiled I have a comment about the code, but need to see it.

If you don't know how to get to the code of the program, you probably missed that important part of the tutorial.

Again, there are just a few parts of the tutorial that I want to help you to understand, then I'd be glad to type in this thread about forms.

The tutorial is a step that has to be done and actually understood.  The forms is another step.  You can't get to the forms step without understanding the tutorial.

Saying you did it, and actually showing parts of the tutorial are different things.  You have to show me the parts so that I can show you from those parts where to put the forms, in this thread.

Someone else might have a different method of answering your question.  But this is my method.

Again, your question is how to do the forms.  My answer is finish the tutorial in the other thread, then I'll talk about the forms.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")
I DID!! i completed ages ago i sent you the link to it how many times do i have to say this

---

### Post by apollothethird on 2011-08-29
> **edwardpatch1 said:**
> I DID!! i completed ages ago i sent you the link to it how many times do i have to say this

You sent me the execution file.  You never did send me the code.  The code is a very important part of the tutorial and understanding the environment.

How many times do you have to say that?  Only once.  I'm not asking you to send me what you sent me.  I'm asking you for some very important parts of the tutorial.  How many times do I have to ask this?

I understand what you're saying that you did.  I'm trying to help you to understand these important parts of the tutorial and understanding the IDE.

The questions you are asking make it clear that you missed some important parts of the tutorial.  If I could see your code I could easily point out some of the important parts that you missed.

I much would rather to use the other thread for the tutorial and use this thread for the form development.

If you will finish the tutorial (that is answer these questions and provide the code to the other thread) I won't talk about the tutorial in this thread.  I'd only talk about the form development.  But at present, because I don't have the code, I can't talk much about the form development because there is a very important link in using the tools that you're missing.

I don't mind explaining this point lots of times to help you to understand it.  I know I'm putting too much in one message.  I'll try to put less in each message and be more focus on your specific question.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by apollothethird on 2011-08-29
> **edwardpatch1 said:**
> ??????//

??????//

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by forrestcupp on 2011-08-29
> **apollothethird said:**
> Hi, Forrestcupp.  I'm sure you know, though you most likely linked the MonoDevelop support site for general information, that MonoDevelop is available from the Ubuntu repo.  It can be installed just by typing it in the Launch menu.Yeah, I just linked to their web page for reference. Considering his lack of understanding, I probably shouldn't have done that.

> **apollothethird said:**
> Also, C# and .Net is supported by Eclipse.  Windowsbuilder Pro is another such plug in for Eclipse.That's good to know. I didn't know it supports C# and that there is a Windowsbuilder plugin. I guess I shouldn't be surprised.

> **apollothethird said:**
> You've probably already mentioned it, but I'm curious.  Which IDE do you use?I use Visual Studio in Windows, and I also use Eclipse for Android SDK. Eclipse was a pain to set up, but after it's set up, I think it's probably about the best one I've used outside of VS. I'm glad to see it's more extensible than I realized. I just suggested MonoDevelop because I thought it would be the closest experience to what Edward is used to.



> **edwardpatch1 said:**
> i downloaded monodevelop but doesn it do c++ ??Actually, MonoDevelop *does* support C++. But I suggested MonoDevelop because I thought that you need to forget about C++ and work with C# and the built in visual form designer. It seems to me that you're not ready for C++, and if you can use MonoDevelop to visually design your forms through the GUI, then learn the easier C# language for the coding, you'll be a lot better off.

> **edwardpatch1 said:**
> but its not fun if you cant design the form 
:(Which is why I suggested for you to use the visual form designer in MonoDevelop. You can just choose whatever buttons or widgets you want, drag them to your window and place them where you want. Then when you're done, it automatically generates the code for you. Then all you have to do is finish out the code to make things do what you want. You'll have to learn C#, though, but it's much easier than C++, and it will be the most similar to Visual Basic.

If you need to learn how to program in C#, look at the link I gave you in my previous post.

If what I am saying does not make sense to you at all, then maybe you need to wait a few years before you start trying to learn to program.

---

### Post by saltmarshlamb on 2011-08-29
> **edwardpatch1 said:**
> ??????//

You need to read this thread here and think about it and the way you are posting. 

[http://ubuntuforums.org/showpost.php?p=8920811&postcount=1](http://ubuntuforums.org/showpost.php?p=8920811&postcount=1)

People are not going to be wanting to spoonfeed you constantly - if you need constant help then perhaps you need to look at getting one on one paid support.

Good luck though :)

---

### Post by cgroza on 2011-08-29
> **saltmarshlamb said:**
> You need to read this thread here and think about it and the way you are posting. 

[http://ubuntuforums.org/showpost.php?p=8920811&postcount=1](http://ubuntuforums.org/showpost.php?p=8920811&postcount=1)

People are not going to be wanting to spoonfeed you constantly - if you need constant help then perhaps you need to look at getting one on one paid support.

Good luck though :)
Agreed. Posting some question marks won't tell anyone which part you do not understand.

---

### Post by edwardpatch1 on 2011-08-29
> **cgroza said:**
> Agreed. Posting some question marks won't tell anyone which part you do not understand.

ok

---

### Post by forrestcupp on 2011-08-29
> **edwardpatch1 said:**
> ok

I've got a feeling your sitting on the other side of your computer screen just getting a good laugh at all of us. :)

---

### Post by apollothethird on 2011-08-29
> **forrestcupp said:**
> I've got a feeling your sitting on the other side of your computer screen just getting a good laugh at all of us. :)

I'm sure he's not.  I work with autistic children.  They are usually very serious and of very few words.  They communicate substantially different from people who are not autistic.  They are not ignorant.  They just communicate differently.

There are lots of other differences.  Some people who don't know a child has this condition can easily take some of the things they way or the ways they act and fell insulted, aggravated, and often respond belligerent to the children (or autistic adults).

He probably thinks that we know what's in his mind, that's why his answers are so short and lacking description.  He appears to be very respectful, and really trying to get along in this community.

He might be a bit over his head.  But very often, they have some abilities that are far above normal, then others that are the opposite.

He probably knows very specific what he wants to do, but he doesn't know how to express it.

I'm not trying to impose the other members of the forum to go out and learn, or try to diagnose the OP.  But I hope my broad reference might ease some of the aggravation of some of the users that might follow some of the OP's threads.

I believe he has done a lot in having changed his computer OS from the norm.  He has even changed it from what's on his parent's computer.  He has apparently done a lot on his own, but has gaps.

I could be wrong, but I'm sure its very unlikely that anyone would have the skill and patience to type 200 messages in the course of a few days and fake a text book example of the training I have with children that has his condition.

I believe he's very sincere.  I commend his parents for having discussed his condition with him so that he can make references when its called for such as he did in the previous thread.

The OP isn't stupid.  He's just different.  He communicates, sees things, and focuses on things different than the "norm".

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by edwardpatch1 on 2011-08-29
> **forrestcupp said:**
> I've got a feeling your sitting on the other side of your computer screen just getting a good laugh at all of us. :)
nope i can record if u want hehe

---

### Post by nvteighen on 2011-08-29
> **forrestcupp said:**
> I've got a feeling your sitting on the other side of your computer screen just getting a good laugh at all of us. :)

Look at his other thread. He's not a troll.

Thankfully, apollothethird seems to be the most appropriate person to help him. I was completely overwhelmed.

---

### Post by edwardpatch1 on 2011-08-29
> **apollothethird said:**
> I'm sure he's not.  I work with autistic children.  They are usually very serious and of very few words.  They communicate substantially different from people who are not autistic.  They are not ignorant.  They just communicate differently.

There are lots of other differences.  Some people who don't know a child has this condition can easily take some of the things they way or the ways they act and fell insulted, aggravated, and often respond belligerent to the children (or autistic adults).

He probably thinks that we know what's in his mind, that's why his answers are so short and lacking description.  He appears to be very respectful, and really trying to get along in this community.

He might be a bit over his head.  But very often, they have some abilities that are far above normal, then others that are the opposite.

He probably knows very specific what he wants to do, but he doesn't know how to express it.

I'm not trying to impose the other members of the forum to go out and learn, or try to diagnose the OP.  But I hope my broad reference might ease some of the aggravation of some of the users that might follow some of the OP's threads.

I believe he has done a lot in having changed his computer OS from the norm.  He has even changed it from what's on his parent's computer.  He has apparently done a lot on his own, but has gaps.

I could be wrong, but I'm sure its very unlikely that anyone would have the skill and patience to type 200 messages in the course of a few days and fake a text book example of the training I have with children that has his condition.

I believe he's very sincere.  I commend his parents for having discussed his condition with him so that he can make references when its called for such as he did in the previous thread.

The OP isn't stupid.  He's just different.  He communicates, sees things, and focuses on things different than the "norm".

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)
1+ to this :)

---

### Post by saltmarshlamb on 2011-08-29
I'm pretty sure there's no troll involved either - that said I'm not so sure that a forum situation is the best place to be getting support given what I've seen.

You do though need to stop the single posts quoting a whole post from someone else with just a line of ? as the answer.

As this is a forum - the intention is that other people can then come here and geet help with similar issues in the future :p

As I said previously - Good Luck

---

### Post by forrestcupp on 2011-08-29
> **apollothethird said:**
> 
I believe he's very sincere.  I commend his parents for having discussed his condition with him so that he can make references when its called for such as he did in the previous thread.

The OP isn't stupid.  He's just different.  He communicates, sees things, and focuses on things different than the "norm".
I didn't read in the other thread where he talked about being autistic. I sincerely apologize, and this helps me be much more understanding. 

Edward, I am deeply sorry for my ignorant reaction.

> **nvteighen said:**
> 
Thankfully, apollothethird seems to be the most appropriate person to help him. I was completely overwhelmed.
With the current revelation, I'm grateful that apollothethird is here to help.

---

### Post by edwardpatch1 on 2011-08-30
> **forrestcupp said:**
> I didn't read in the other thread where he talked about being autistic. I sincerely apologize, and this helps me be much more understanding. 

Edward, I am deeply sorry for my ignorant reaction.


Thats ok :)

---

### Post by kbaumen on 2011-08-30
> **apollothethird said:**
> I'm sure he's not. I work with autistic children. They are usually very serious and of very few words. They communicate substantially different from people who are not autistic. They are not ignorant. They just communicate differently.
 
There are lots of other differences. Some people who don't know a child has this condition can easily take some of the things they way or the ways they act and fell insulted, aggravated, and often respond belligerent to the children (or autistic adults).
 
He probably thinks that we know what's in his mind, that's why his answers are so short and lacking description. He appears to be very respectful, and really trying to get along in this community.
 
He might be a bit over his head. But very often, they have some abilities that are far above normal, then others that are the opposite.
 
He probably knows very specific what he wants to do, but he doesn't know how to express it.
 
I'm not trying to impose the other members of the forum to go out and learn, or try to diagnose the OP. But I hope my broad reference might ease some of the aggravation of some of the users that might follow some of the OP's threads.
 
I believe he has done a lot in having changed his computer OS from the norm. He has even changed it from what's on his parent's computer. He has apparently done a lot on his own, but has gaps.
 
I could be wrong, but I'm sure its very unlikely that anyone would have the skill and patience to type 200 messages in the course of a few days and fake a text book example of the training I have with children that has his condition.
 
I believe he's very sincere. I commend his parents for having discussed his condition with him so that he can make references when its called for such as he did in the previous thread.
 
The OP isn't stupid. He's just different. He communicates, sees things, and focuses on things different than the "norm".
 
-- L. James
 
-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")
 
I respect your patience man. I really do.
 
And good luck to you edwardpatch1. Programming is indeed very exciting. :)

---

### Post by edwardpatch1 on 2011-08-30
> **kbaumen said:**
> I respect your patience man. I really do.
 
And good luck to you edwardpatch1. Programming is indeed very exciting. :)

thanks

---

### Post by CptPicard on 2011-08-30
I always thought that autistic people would be good at pedantically following every single step of exact instructions though... which seems to be the hurdle here?

---

### Post by kbaumen on 2011-08-30
> **CptPicard said:**
> I always thought that autistic people would be good at pedantically following every single step of exact instructions though... which seems to be the hurdle here?

It seems to me that the problem is not following instructions but explaining any encountered issues. I've met a few autistic chaps and they all seemed pretty clever. They just had trouble expressing themselves.

---

