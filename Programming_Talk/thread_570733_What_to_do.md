---
title: "What to do"
date: 2007-10-08
forum: Programming Talk
---

### Post by keiffee30 on 2007-10-08
I am looking into programming for the very 1st time. I'm not too sure where to start. so lets start at the beginning. now i am not going to use tecky talk here, so please dont start shooting me (just yet)

What i would like to do Stage 1?
I would like to make a small GUI app that will help me with the “core/kernel version number” is 2.6.0.1 or 2.4.0.1 etc, then for it to show me in the GUI box. Then to show me what Video driver i am running (Nvidia is a nightmear to set up and to find out about). Also i would like this app to access the config file so any changes can be done without drilling down the tree.  

What i would like to do Stage 2?
To extend this into installing the correct video driver. now i know that there is a app out there called envy that dose a good job of installing (but this never worked for me). 

What i would like to do next Stage 3?
in a tab from the main page i would like to make a GUI interface that will look at the Network card (NIC) settings so i can view and/or change the link speed.

so to my question (at long last i hear you say) . I have seen on many many many website and in here about what language to use and what on is better for doing what. From what i can see Python is the better language for newbys to start in. But i have also seen that there is VB. (i know i'm swearing in here). now coming from a Windows based GUI and i have used front page for a web site and the WYSIWYG. is there a language that dose the same as WYSIWYS? 

The PC spece is a P4 3Ghz, 1G ram 600Gb HDD 256Mb video (Nvidia) Ubuntu 7.04

---

### Post by Wybiral on 2007-10-08
There is [Glade]("http://glade.gnome.org/"), which can export an XML representation of your interface that languages like Python can load (or it can directly output C code for it). Python has a module for loading glade output so that's no worry.

---

### Post by pmasiar on 2007-10-08
You may consider to add stages 0.1 to 0.9, where you will write some command-line programs, to learn programming without overhead of GUI. GUI is hard.

VB is Windows-only - and honestly, it is NOT a good language. Used widely on Windows? yes. But good? Don't get me started. :-)

---

### Post by ryno519 on 2007-10-08
You might want to start a little more basic. Write some simple command line applications first. Figure out how the core of the language works before you get into the more advanced aspects. Learning to program a GUI can be quite tricky and is not typically for a beginner. There is a lot you have to learn before you can code a GUI app comfortably.

You could code in C# using mono and monodevelop. C# is pretty easy to pick up and you have access to the .net libraries.

---

### Post by j_g on 2007-10-08
> **Wybiral said:**
> Glade.. directly output C code for i)

I'd recommend Glade (version 2) as well. But just a slight point. The latest glade doesn't output any C code to paste into your app to present the UI. That has been deprecated. What you do now is use the libglade shared library to call a function that loads the XML and "presents" the UI for you.

---

### Post by Wybiral on 2007-10-08
> **j_g said:**
> I'd recommend Glade (version 2) as well. But just a slight point. The latest glade doesn't output any C code to paste into your app to present the UI. That has been deprecated. What you do now is use the libglade shared library to call a function that loads the XML and "presents" the UI for you.

Ah, my bad. I haven't used glade recently. That definitely sounds like an advantage (especially if you plan to port your app from one language to another).

---

### Post by Yz85Racer on 2007-10-08
Oh y god you're all dumb.  For simple GUI? Use Java - Swing ;)
Or C++.

---

### Post by ryno519 on 2007-10-08
> **Yz85Racer said:**
> Oh y god you're all dumb.  For simple GUI? Use Java - Swing ;)
Or C++.

Well that certainly deserves to be taken seriously.

---

### Post by j_g on 2007-10-09
> **Yz85Racer said:**
>  For simple GUI? Use C++.

I certainly hope this doesn't degenerate into yet another one of those tireless and useless language wars, as is so often the case on this forum, but I just want to point out that the C++ language has no inherent GUI capabilities. If you want to create a GUI in a C++ app, you'll have to use some additional API such as... well, GTK and libglade. I say this so that no one may be misled by the insinuation quoted above.

---

### Post by LaRoza on 2007-10-09
Most languages give the ability to make GUI's, but when starting out, it is best to use cli programs.

You could check out my wiki for language and gui references, but for a project like this, Python or Perl would be the best. For the GUI, you can use EasyGUI in Python. It is extremely simple, and is uncomplicated, but you can't do anything really cool in it.

---

### Post by keiffee30 on 2007-10-19
many thanks to every body for the input into this page. The one last qwestion i would like to ask but has anyone tired "runtime revolution" i 1st found this on Novell website. Its free to down load. 

[http://www.runrev.com/](http://www.runrev.com/)

This looks like the type of thing i could get my teeth (well tooth) into.

---

### Post by ghostdog74 on 2007-10-19
> **keiffee30 said:**
> I am looking into programming for the very 1st time. I'm not too sure where to start. so lets start at the beginning.
first, learn how to program in your shell.  bash/bourne/ etc...learn how to use your tools, grep/awk/sed/cut..etc....then as you slowly do more complex programs requiring complex operations, you can try other languages..

---

