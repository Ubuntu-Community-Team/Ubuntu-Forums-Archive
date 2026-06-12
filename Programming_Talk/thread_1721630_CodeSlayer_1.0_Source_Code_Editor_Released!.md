---
title: "CodeSlayer 1.0 Source Code Editor Released!"
date: 2011-04-04
forum: Programming Talk
---

### Post by Jeff Johnston on 2011-04-04
I just released the first version of CodeSlayer! It is a lightweight source code editor that boasts a clean interface but powerful features. It is written in C using the GTK+ toolkit.

I think right now the target audience for CodeSlayer is anyone that does not need the features of a full blown IDE, but still wants a text editor that is geared towards writing code. At the core I always want CodeSlayer to be light and language neutral (aside from what GtkSourceView brings). And I think there is a ton of functionality that can be done with that in mind that other editors have not included. An example of this with CodeSlayer is the groups manager, which allows you to group file system mount points (called projects). This keeps things organized and can be easily searched. In addition you can have as many groups as you want, with an easy way to flip between them. And CodeSlayer will even keep track of the tabs you have opened as you flip between the groups.

Then past the core functionality the goal is to make it easy for anyone to write a quick plugin. I am finishing up the plugin system right now so we will have a real nice way to start in with the language specific features. But, again, I never want any language specific feature to bleed into the core so that CodeSlayer always feels light.

Right now I spend all of my free coding time working on CodeSlayer. Its something that I enjoy working on and I hope other people find  it useful! 

The website is [http://codeslayer.org](http://codeslayer.org) and has all the information about how to install CodeSlayer.

-Jeff Johnston

---

### Post by fallenshadow on 2011-04-05
Looks really nice! You got yourself some nice programming skills. :)

However I don't wanna sound rude or insulting but why develop this when Geany is available? (and IMHO quite a similar idea/application)

---

### Post by Jeff Johnston on 2011-04-05
No problem...I expect the comparisons. 

I was a little hesitant to even post about CodeSlayer because it is still very early days in the project. But I really like the feel of the project and thought other people would like it too. But probably the main thing that CodeSlayer has going for it is that I want this for my personal use and I am fully aware of what I am getting myself into! Hopefully as I get through more releases it will be more obvious on why I think the overall vision of CodeSlayer is different.

---

### Post by fallenshadow on 2011-04-07
Ok regardless im still gonna check it out before I pass any judgement on it... I might post back here for some feedback if you want. :)

---

### Post by dazman19 on 2011-04-07
Wow very nice app. Looks like lots of hours of work. Well Done. I checked out your video, will have to download a copy and see how it goes when i get my debian notebook back.

---

### Post by lexx27 on 2011-04-13
great work! I will give it a try for sure.

---

### Post by cgroza on 2011-04-13
A deb would be very nice.

---

### Post by Jeff Johnston on 2011-04-24
CodeSlayer 1.1.0 is out! The best new feature is the plugin environment. I think CodeSlayers plugin environment is amazing because it is both powerful and simple. I think anyone that knows a little bit of C and the GTK+ toolkit can write a useful plugin in no time!

[http://codeslayer.org/](http://codeslayer.org/)

-Jeff Johnston

---

### Post by Jeff Johnston on 2011-06-09
Not to keep bumping up my own thread but I wanted to let people know that I just released version 1.2.1 of CodeSlayer. The focus of this release has been general usability improvements. I tried to pay a lot of attention to things like shortcut key refinement and being careful about what has focus as you navigate the interface. Overall I think things have a really nice feel to it now. 

In addition, since version 1.2 there is an autotools compiler plugin that bakes in the autotools functionality.

Over the next few months I will be working on integrating the ctags and debugger. At that point I get to start on the real power features such as multiple clipboards, inline diff and a bookmarking system! But do not worry about feature bloat...the core of CodeSlayer will always stay lean.

---

### Post by Petrolea on 2011-06-10
> **Jeff Johnston said:**
> Not to keep bumping up my own thread but I wanted to let people know that I just released version 1.2.1 of CodeSlayer. The focus of this release has been general usability improvements. I tried to pay a lot of attention to things like shortcut key refinement and being careful about what has focus as you navigate the interface. Overall I think things have a really nice feel to it now. 

In addition, since version 1.2 there is an autotools compiler plugin that bakes in the autotools functionality.

Over the next few months I will be working on integrating the ctags and debugger. At that point I get to start on the real power features such as multiple clipboards, inline diff and a bookmarking system! But do not worry about feature bloat...the core of CodeSlayer will always stay lean.

Your program would be awesome if it would be like in Eclipse, where code debugs while writing it. If you'd do that for C it would really be a great IDE :)

---

