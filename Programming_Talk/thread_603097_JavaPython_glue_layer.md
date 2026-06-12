---
title: "Java/Python glue layer"
date: 2007-11-04
forum: Programming Talk
---

### Post by Anovadea on 2007-11-04
Hey all,

I'm doing a visualisation project in Java (I can't go into too much detail just yet), and while I'm not even started, I'm already thinking of making a gdesklet out of it.

However, I see a slight snag in my plan. The visualisation project is in Java (and is pretty much a requirement for what I'm doing), while GDesklets operate with plain vanilla CPython. I also want to "sell" (not literally) this as something that any user can use, so I don't want users to mess around with the interpreter just to get my code to work.

So, does anyone know of any nice "glue" libraries I could use, so I could call a java class from python. My idea would be to get python to call the GUI. I've seen [JPype]("http://jpype.sourceforge.net/"), but it seems to be undergoing heavy redevelopment at the moment, and the documentation is sparse. **Can anyone comment on how good JPype is for production code?**

Another way for me to approach it would be to use a different widget set... In that case [Glossitope]("http://www.glossitope.org/site/") looks ideal as it's cross-platform (not locking into GNOME - which is a plus in my books) and based on Java. **Does anyone have any experience with it? How mature/stable is it?**

**Does anyone have any other suggestions to help me do what I want to do?**

Thanks,
Aoife

---

### Post by pmasiar on 2007-11-04
Not sure how easy is to merge Java and Python. You may have more luck with Jython, but C libraries is a problem. It is deliberate compatibility problem introduced by Java.

---

### Post by Anovadea on 2007-11-05
I'm not sure if Jython is an option - my plan is to integrate the display (which will probably be done in swing) with GDesklets, which runs, as far as I know, on just plain cpython. So, I'm either looking for a good cpython/java glue, or an alternative to gdesklets that would let me integrate the display into a desktop widget.

But thanks for the suggestion,
Aoife

---

### Post by cwaldbieser on 2007-11-05
> **Anovadea said:**
> 

**Does anyone have any other suggestions to help me do what I want to do?**

Thanks,
Aoife

Without knowing more about what code you are interfacing, it is difficult to be specific.  However, you could use typical means of communicating between processes (e.g. pipeline, named pipes, sockets, signals, etc.) if the parts of your program ran in separate processes.  I don't know much about GDesklets programming, but briefly glancing at the [documentation]("http://develbook.gdesklets.de/framework-overview.html") suggests that communication with the desklets is handled via sockets:
> 
Clients, e.g. a command line frontend, can thus be implemented as thin remote controls.


---

### Post by Anovadea on 2007-11-05
Hmm, yeah. I really should have checked that first.

I was hoping I could make be as simple as just getting the interface to draw the JPanel/JFrame (unless I end up doing something completely insane, I'd probably use a basic Swing interface) in some way that it would integrate with gdesklets. 

Otherwise, given that the interface would be doing the same job of taking streamed information from a socket as the gdesklet would, it would be doubling my workload. :(

Stupid question - if I compiled the program with gcj and then tried some sort of glue in C to call the function... could that be easier?

Just googled that and found [this]("http://www.python.org/pycon/2005/papers/27/paper.txt") about integrating lucene with python via gcj/SWIG... so it can be done - my new question is "Is it worth the effort?"

Mainly, I'm trying to sound out if this is an avenue I should bother following, given that I'm mainly aiming this as a cheap shiny-feature(tm) where I can say "And if you want this on your desktop... here it is." So I don't want to sink too much time into this, so I'm just to looking into whether  it's worth doing. If that makes any sense.

Thanks
Aoife

---

### Post by cwaldbieser on 2007-11-05
It is hard to offer a suggestion without knowing what you are trying to do.

I am guessing you want a desklet on the tool bar, and that you want it to give you the option to pop up some sort of GUI.  Presumably, this GUI is something you have already written in Java.  I would guess that in your desklet code, you could just do something like:
```

os.system("java myclass")

```
If you need 2 way communication, you could use the subprocess module and open a 2 way pipe.  The java program could write results to its standard output, which the gdesklet could read.

If you are trying to do something different, you will have to be a little more specific  about what you are trying to achieve.

---

### Post by Anovadea on 2007-11-06
No, this isn't for the toolbar. Just to be clear that we're both talking about the same thing - [This is a screenshot of a former workmate's desktop, which was really loaded with gdesklets.]("http://www.opensolaris.org/os/project/jds/tasks/gdesklets/gdesklets.png") Note that they're integrated with the desktop.

Now, what I'll have is some panel that visualises a particular system. This will be written in Java.

I was hoping to turn it into a gdesklet, so a display of the system could be displayed in the background.

The problem with calling it as os.system is that the visualisation pane will then be independent of the python process calling it. I need it to be callable by, and (in essence) be part of, the python process, because it's going to have to be controlled by gdesklets overall, so that gdesklets has control of the pane's size and position rather than java itself, in order to integrate it with the desktop properly.

So, now I'm thinking that if I'm going to do this, an alternative to gDesklets might be a better plan.

Thanks,
Aoife

---

