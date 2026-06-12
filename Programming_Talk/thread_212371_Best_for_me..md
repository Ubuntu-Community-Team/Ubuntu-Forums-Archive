---
title: "Best for me."
date: 2006-07-09
forum: Programming Talk
---

### Post by Locked on 2006-07-09
OK im sorry if yous have answered this before but i would like your opinions on witch programming language would be best for me.

With the specific programming language i will be creating gui apps. That is really the only spec i have oh and not VB ;)

---

### Post by Locked on 2006-07-09
Sorry, must be a for windows :)

---

### Post by Engnome on 2006-07-09
Languages are like tools, you choose the right one for the task. If you want good recomendations you will have to be more detailed with what you will do with the language.

---

### Post by Note360 on 2006-07-09
GUI apps hmm for windows ey. C# is highly recommended by many people and has sparked enough intrest for the development of Mono on Linux and GTK# so if it is good enough for people to pour a large portion of time and money into for it to work on Linux it should be good enough for you.

I would recommend C#, Python (not really made for windows), Ruby (it is again slow on windows), C, C++ or Java. They are all good. Out of all of them I think C# is most recent and the recent work in MONO allows C#, Boo, and VB (as well as IronPython and some other .NET languages) to be programmed on Linux. The Linux IDE I would suggest for C# is MonoDevelop and for Windows you can Use SharpDevelop (#develop) which is open-source or Microsofts Visual Studio (Express is free).

Good luck in your venture and welcome to the wonderous world of Debuging and learning on a daily basis.

---

### Post by Max Luebbe on 2006-07-09
If you're doing Windows stuff - I reccommend C#. You get managed memory, and a java like language that got right most of the stuff java got wrong. Rich api, and fast learning curve.

That'd be my vote.

---

### Post by thumper on 2006-07-10
Don't use C++ for GUI work.  It is too fanickity (speaking as a C++ person).

If I was forced to write GUI apps for windows (and it would have to be forced), and they only had to work on windows, then I'd use C#.

I've not yet done any GUI stuff with python so can't really comment on that.  However IronPython might be a good option if your clients are on XP-SP2.  IronPython works with .NET and has tested faster than C-Python in some areas.

---

### Post by Locked on 2006-07-10
Thanks for the replys :)

---

### Post by Daverz on 2006-07-11
Python + wxpython might be worth considering.  It wouldn't leave you locked into windows.

The "native" C# GUI library is Windows Forms, and I'm curious how well that works under Mono.

---

### Post by Locked on 2006-07-11
Anyone know any good tutorials for this.

---

### Post by Note360 on 2006-07-11
For what C#?
For C# go to Synaptic type in Mono. Get a package called Mono that should install everythign scroll to MonoDevelop and get that. That should do it.
To run things in the command line you type:
```

$ mcsc path/to/file
$ mono path/to/resulting/.exe

```
I found a couple I am not sure how good they are:
[http://csharpcomputing.com/Tutorials/TOC.htm](http://csharpcomputing.com/Tutorials/TOC.htm)
[http://www.softsteel.co.uk/tutorials/cSharp/cIndex.html](http://www.softsteel.co.uk/tutorials/cSharp/cIndex.html)
(list of tutorials)[http://www.c-sharpcorner.com/Tutorials.asp](http://www.c-sharpcorner.com/Tutorials.asp)

As for books Programming C# and Learning C# are both good I kinda skimmed through them a bit.

---

### Post by 3rdalbum on 2006-07-12
Python is quite good for GUI programming really; some of the features of the Python language are very useful for talking to GUI toolkits.

Python comes with Tkinter, which is very easy to write simple programs in, but if you wanted to write for Linux as well as Windows, best to use its binding to WxWidgets (which always looks native... Tkinter looks like an old-school Gtk1 GUI).

---

