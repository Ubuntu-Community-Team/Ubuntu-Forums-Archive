---
title: "Need advice about a simple, cross-platform project"
date: 2016-04-08
forum: Programming Talk
---

### Post by Dry Lips on 2016-04-08
Hi everyone!

I need some advice about a project that hopefully isn&#8217;t too advanced. I have quite a bit of general computer knowledge, except that I&#8217;m no programmer. However, I have an idea for a project and would like to use this project as learning project, while at the same time making a program that hopefully is genuinely helpful to people. First of all, there are no programs out there that does exactly what I want to do, so there is a real niche that I want to fill.

Fortunately I have a detailed vision of exactly what I want to achieve, but I need advice and pointers about how to go ahead and what I need to learn in order to accomplish this. 

**The project:**

Basically the idea itself is dead simple, and technical users wouldn't need this. Basically the idea is to use a custom hosts file to block certain unwanted webpages. However, even such a simple task as manually editing their hosts file is simply too advanced for the majority of users. (Btw, the idea here isn&#8217;t to block ads or adult content, but an altogether different type of websites/content. There are no programs that blocks exactly the kind of content I have in mind here.) 

_ So the basic idea is to have a simple cross-platform, password protected gui program that adds a list of unwanted websites to the hosts file, while keeping any existing entries intact._

The changes should be possible to disable from within the program, and when uninstalling the program any changes made to the hosts file should be reverted.

**Additional features:**

I also eventually want to include a feature so that program regularly checks for an updated file of blocked sites, and automatically downloads it.

I also eventually want to enable optional blocking of other types of content (for instance ads, adult content), but this isn&#8217;t the primary goal here. (People generally use adblock.)

**Technical Requirements:**

The idea is to make an **open source**, **cross platform** desktop program with a **gui**. (Linux, Windows and OSX.) So, I need suggestions here, first and foremost which programming language and cross-platform graphical toolkit I should use. 

What I&#8217;m looking for is **a)** relative ease of use with the goals above in mind, **b)** learning a programming language and a toolkit that will give me a solid foundation for doing future projects.

General advice about workflow and deployment is also highly valued. (I need to be able to make **packages/installers** on all platforms: Linux, Windows/OSX.)  And as I already wrote, I&#8217;d also be thankful for some specific pointers, what kind of practical programming strategies I need to learn in order to do this.

Thank you in advance!

---

### Post by spjackson on 2016-04-09
I'm not sure I can really answer such a broad question, but I will start the ball rolling.

This sounds rather ambitious for a first project.

The core ingredient is the ability to write to the hosts file which requires elevated privileges on all 3 platforms. If this doesn't work then the project is pointless, so I would start with that. However, as it is your first attempt at programming, you might prefer to tackle another aspect first.

Choice of Gui toolkit and language is a big decision and you need to consider.

- Ease of use for a beginner
- Licensing
- Deployment

Some possibilities: Java and/or other JVM languages. Python/C++, Qt,GTK,wxWidgets. Some may suggest C# but I don't know enough about it to comment.

How are you going to download a file? With http you will hit least resistance from firewalls.

If you really need standalone executables, that effectively rules out Java and C#. While I think there's a tool to turn a python program into a .exe for Windows, I'm not sure if you can do that for the other target platforms, and in any event it isn't for beginners.

I would suggest that C++ and either Qt or wxWidgets would be the best choice for your ultimate objective but C++ in particular is far from the easiest to learn.

---

### Post by Dry Lips on 2016-04-09
**@spjackson**, 

thanks a lot for your feedback, it&#8217;s much appreciated that you took your time to reply to someone who obviously is a beginner! :)

So here is the plan. The first version of the program will be for Linux, and secondly I&#8217;ll make a Windows version. (I have the least knowledge of macs, so an OSX version isn&#8217;t my top priority, but eventually I&#8217;d like to do this too.) The idea is to share as much code as possible across the different platforms, but I realize that there will be some differences between the platforms. But thanks, yeah, privilege escalation and downloads is something that I need to figure out! 

On second thoughts, you made me realize that standalone executables most likely isn&#8217;t what I want. (I&#8217;ve edited my post accordingly.) For instance, an installer for windows, and a deb/rpm package for Linux is probably what I want. 

So then I guess Java perhaps is an option after all? At least I know that it&#8217;s trivial to make a native installable package for Windows using Netbeans + Inno Setup, (I did this last year for a friend who had problems deploying a program) and I don&#8217;t think it&#8217;s too difficult to turn a java program into a .deb either? 

And what do you think about Ruby in this respect? I know that it&#8217;s a rather easy language to learn, and I already use the Ruby ecosystem to some degree.

I have little programming experience, so I&#8217;m obviously free to choose any language I want, but I&#8217;ll never be a professional programmer, so the language I decide to learn will probably be something that I&#8217;ll stick with for a long time. Learning multiple programming languages is probably not realistic in my case, so it&#8217;s kind of important to find something that won&#8217;t limit my options later on when I&#8217;m more experienced. But then again, I won&#8217;t lie, ease of use is obviously a main concern too. (I'm a beginner, after all...)

Anyways, thanks a ton! :)

---

### Post by spjackson on 2016-04-10
> **Dry Lips said:**
> 
And what do you think about Ruby in this respect? I know that it’s a rather easy language to learn, and I already use the Ruby ecosystem to some degree.

Ruby is a pretty decent language but I don't know enough about it to say whether it is suitable for your application. I know that Ruby is well used and respected for webserver development, but I don't know to what extent it is used for desktop development. If I were in your situation I would research this before settling on Ruby. On the other hand I do know that Python is used to some degree for desktop apps. For Ruby I see that wxRuby and QtRuby are both dead projects, qtbindings seems live but does not yet support Qt 5. My early conclusion is that whatever desktop apps are done with Ruby probably use [Shoes!]("http://shoesrb.com/") You can look into this issue yourself, but that would be the question I would be asking: can I trust that Ruby is something I can reliably use for desktop development now and in the future on all relevant platforms?

I don't want to say "avoid Ruby" but Python is more mainstream and you will therefore, for example, find it easier to get help in this forum for Python than for Ruby.

---

### Post by Dry Lips on 2016-04-12
> **spjackson said:**
> Ruby is a pretty decent language but I don't know enough about it to say whether it is suitable for your application. I know that Ruby is well used and respected for webserver development, but I don't know to what extent it is used for desktop development. If I were in your situation I would research this before settling on Ruby. On the other hand I do know that Python is used to some degree for desktop apps. For Ruby I see that wxRuby and QtRuby are both dead projects, qtbindings seems live but does not yet support Qt 5. My early conclusion is that whatever desktop apps are done with Ruby probably use [Shoes!]("http://shoesrb.com/") You can look into this issue yourself, but that would be the question I would be asking: can I trust that Ruby is something I can reliably use for desktop development now and in the future on all relevant platforms?

I don't want to say "avoid Ruby" but Python is more mainstream and you will therefore, for example, find it easier to get help in this forum for Python than for Ruby.

Thanks a lot for your feedback, it's much appreciated. You raise some good points about Ruby, so I'll think this over. I'm not sure about how relevant it is for desktop apps, so perhaps another language is more suitable. :)

---

