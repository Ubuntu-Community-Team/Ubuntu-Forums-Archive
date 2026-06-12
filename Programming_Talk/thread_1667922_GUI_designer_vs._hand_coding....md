---
title: "GUI designer vs. hand coding..."
date: 2011-01-15
forum: Programming Talk
---

### Post by VorpalBunny on 2011-01-15
...what does everyone think?

I just got an assignment in software engineering to do a Java application, and it explicitly said to use Jigloo ([http://www.cloudgarden.com/jigloo/](http://www.cloudgarden.com/jigloo/)) to do the GUI. I went through the quick tutorial on the site and did a small test app on my own, and it seems like a PITA. I've done some fairly elaborate GUIs before using both Swing and QT with C++, writing all the code out by hand, and never really had a problem keeping track of everything. And I really like seeing what pieces of code correspond to what bits of the GUI, and being able to tweak things manually.

I'll use the designer for this project, since I suspect it's as much about testing our ability to adapt to new frameworks and methods as it is our ability to make GUIs, but I'm wondering if this trend will continue as I get real programming jobs. Is using a GUI designer pretty much a de facto standard in the "real world", or are most commercial programs hand coded? Or is there something of a mix? Am I demonstrating my n00bosity by not preferring the method that gets "results faster"?

---

### Post by rg4w on 2011-01-15
Modern software products are often differentiated by the quality of their UI, and it's just more work to type coordinates by hand when you can lay them out visually.

GUI tools let you make your own GUIs faster, so you can spend more time on the code that drives the features behind them.

MS Visual Studio has become the dominant force on that platform, as Apple's XCode GUI tools are for doing layout there.

It's hard to imagine that trend reversing itself.

---

### Post by Simian Man on 2011-01-15
It's important to understand how the underlying code is working and what the GUI designer is doing.  It's also important to get results quickly though.  I've never really done GUI projects professionally, but I'd be very surprised if they hand code the interfaces in most cases.

---

### Post by Reiger on 2011-01-15
GUI designers are PITA at first but that is the learning curve. Once you get past that, a good GUI designer should save you a lot of the adjust->compile->test->that's not right either->start over cycle. When you have a large project you will appreciate the time saved by not building it cleanly over and over and over again.

---

### Post by tgm4883 on 2011-01-15
I don't program professionally, but I always use glade when doing my GUI's. The one exception to that is for a program that I wrote that grabs logs and system information for another piece of software. I did that by hand (and it is very simple) as I wanted to be able to ship everything in a single file.

---

### Post by worksofcraft on 2011-01-15
My experience with GUI designers is that they go out of date and you get tied in to using tools that might become obsolete, unobtainable or no longer supported.

---

### Post by KdotJ on 2011-01-15
I make use of GUI designers, but I do feel that it is worth while doing a fair bit of hard code GUI design/coding. I program in Java, and I think it is important to learn how to use layout managers and components manually. If I didn't and I started programming always using Netbeans to create GUI programs with much more ease... I wouldn't have a clue what Netbeans was really doing...

---

### Post by slavik on 2011-01-16
Designing a GUI has nothing to do with writing the code behind the individual elements. You don't need to know HTML to be able to design a web site that is easy to use and well laid out.

User Interface is a field all it's own in Computer Science and related fields. Look at where Guitar Hero too us in playing video games. Look at the Wii, the Playstation Move and the Microsoft Kinect.

Not only that, but using a designer will allow you to see what it will look like AND generate something that your program can use to create it (GTKBuilder, or straight C code).

---

### Post by slavik on 2011-01-16
Designing a GUI has nothing to do with writing the code behind the individual elements. You don't need to know HTML to be able to design a web site that is easy to use and well laid out.

User Interface is a field all it's own in Computer Science and related fields. Look at where Guitar Hero too us in playing video games. Look at the Wii, the Playstation Move and the Microsoft Kinect.

Not only that, but using a designer will allow you to see what it will look like AND generate something that your program can use to create it (GTKBuilder, or straight C code).

---

