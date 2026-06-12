---
title: "I Wanna Learn XUL To Make Cool Ubuntu Apps"
date: 2007-01-28
forum: Programming Talk
---

### Post by SuperMike on 2007-01-28
Hey ya'll. If you want to learn how to make apps, installers, wizards, GUIs, control panels, or other things for Ubuntu, and don't want to go the Python/PyGTK route, you can do it in a kind of HTML-looking markup language (XUL), programming in Javascript, and with or _**without**_ a web server on the backend. The trick is that a Mozilla runtime tool, 'xulrunner', permits you to use XPCOM objects to go outside the Javascript sandbox. This technology has been around awhile, but by the looks on Google's project hosting site, you'll recognize that this is starting to "gel" as a new way to make apps when you're looking to do something that just doesn't fit well into an ordinary web app.

I've built an SDK here...

[SIZE="3"][http://code.google.com/p/simplexul/](http://code.google.com/p/simplexul/)[/SIZE]

...and you can open it and read the README.txt to learn more. That should get you started.

I hope this encourages more people to build applications for Ubuntu Linux. If you know HTML and Javascript, it's not a far stretch of your learning to move to XUL and XPCOM.

Oh, and as an added bonus, if you do enough testing on multiple platforms, and stick with the XPCOM API, you can build cross-platform apps as well. Yes, that means apps that run on Macs, Windows, Linux, and Unix/Solaris.

These apps can also support embedded Flash, video, HTML, AJAX, rich edit controls, spreadsheet grids, Java applets, and so on.

If you're a Comp Sci professor, I hope you also take a look at this sample because XUL and Javascript might be something you could teach for Programming 101 courses.
[SIZE="1"]
P.S. If you haven't tried Google's new project hosting site at code.google.com, you're missing out. It's way cool and easy to use.
[/SIZE]

---

### Post by smartbei on 2007-01-28
This looks very interesting - thanks for sharing! I will take a more in depth look after some sleep :-).

---

### Post by SuperMike on 2007-01-28
Yeah, XUL and XPCOM isn't documented as well as I like, but once you get the hang of it from 'simplexul' sample project and have a friend help you along, it's not so bad and you can accomplish much in very little time.

---

### Post by MystaMax on 2007-02-19
Sorry to wake the dead.

I do some HTML programming and was interested in XUL, but couldn't find the documentation to get things going. But I did come across the google project in your signature, and became even more interested. I haven't had time to look over the code.

One concern that comes to mind is speed. Are these applications going to be as fast as a python built application or other Linux desktop applications. I know that XULrunner is what the next version of firefox will be ran on top of.

I've got some other questions, but will wait to see if I get some replies here. See ya.

---

### Post by SuperMike on 2007-02-19
Yeah, I'm still here. Funny you should say "dead" at this moment because I'm so sleepy today and thought I'd read these forums to stay awake. You'd think I was dead.

Yeah, I actually find the speed hit to be about the same as a PyGTK app, just slightly slower at first. However, shut the app down and open it again, and it opens faster -- go figure. Then, open both apps again and they'll both open at the same speed and be zippy fast. Linux works like that, I guess.

---

### Post by MystaMax on 2007-02-20
Thanks for replying. I read over the ReadMe.txt file and it looks good. I can't say I'm all too familiar with software development cycle, but I'm in the process of learning. im a novice at this eager to learn.

I have a lot of music files, and love music. I would like my first attempt w/ XUL to be something related to that. Maybe a ID3 tagger or something. We'll see.

I read over [XPCOM ]("http://en.wikipedia.org/wiki/XPCOM")over @ wikipedia, and I'm starting to piece together how it all works in a general sense. I'm in the process of getting my head around ruby, and from the wiki entry XPCOM will support it soon.

---

### Post by SuperMike on 2007-02-20
You can also check out the yt2mp3 project at code.google.com, which is something I also wrote with XUL and can demonstrate something music oriented in relation to XUL.

---

### Post by lloyd mcclendon on 2007-02-21
can XUL connect to my database?  i am very intrigued by this technology but last time i looked at it, i thought that it was just too infantile to do anything useful with - not many external libraries & tools to build off of etc

---

### Post by SuperMike on 2007-02-21
> **lloyd mcclendon said:**
> can XUL connect to my database?

Depends on how you want to implement it. Here's some options:

* XUL on the client reaching into a local client database via XPCOM's SQLite API

* XUL on the client reaching back to the server over AJAX. The server can do whatever it wants with that AJAX, including read/write to a database using their own CGI or Apache mod language of choice.

* XUL on the client reaching into process API via XPCOM and then accessing command-line tools to read/write to the database.

* XUL on the client doing socket connections to a local server on the local workstation, and that server could be web or any other kind of socket server, using any language of choice.

---

