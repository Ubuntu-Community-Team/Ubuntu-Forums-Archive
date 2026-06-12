---
title: "My first program.  Jiffy a simple CPU monitor."
date: 2008-03-24
forum: Programming Talk
---

### Post by | MM | on 2008-03-24
Hello,

I have written a simple CPU monitor in python using cairo and pango.

It is my first real program, it has a pleasant interface and all that.  I am just learning python, and i have no real prior experience except for a Java 101 a few years back at uni.

My prog is called Jiffy, because that's the name given to the most basic time interval in the kernel, and apparently that's the unit used in /proc/stat to record cpu time doing stuff -- or not doing stuff as it may be.

I am kinda confused about the actual value of a jiffy, originally i read it was 10 ms but then i found another article that said from kernel 2.6.x on a jiffy was now 4ms.  So not sure about that one, any insight appreciated.

Given this confusion, I suspect my y values are based on a wrong assumption, but i am too tired to think it through right now.  The values are still indicative and more or less match what top is seeing. 

I was motivated to write a CPU monitor because the current g-s-m is crap on my pc, a total cpu hog, like > 50% when it renders the graphs.  Jiffy is better, it runs at around 5-6% cpu according to top, given python and the amount of cairo i am quite happy, though i am sure improvements can be made in many places.

This Easter break, writing Jiffy and learning about python has been a thoroughly satisfying experience.  

It seems to be crash free at this point, so hopefully it'll run on other systems :P.  I am using the nvidia proprietary drivers, so i am not sure about cairo performance on other systems.  Also of note is the fact i wrote it on hardy, i am not sure (because i can't test) if this means older version of python or cairo will spew errors.

**I would appreciate any feedback on any aspect of my code, be it my algorithms, best practice or style.**

I've attached some screenshots as well as the source.  :)
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=63622&stc=1&d=1206342454[/IMG]


I wish to thank all those who have put tutorials on the net, giving examples of how to use python, gtk, cairo and pango.
Finally, I have found the following sites especially useful:
[http://www.pygtk.org/pygtk2tutorial/index.html](http://www.pygtk.org/pygtk2tutorial/index.html)
[http://www.tortall.net/mu/wiki/CairoTutorial](http://www.tortall.net/mu/wiki/CairoTutorial)
[http://aruiz.typepad.com/siliconisland/2006/04/threads_on_pygt.html](http://aruiz.typepad.com/siliconisland/2006/04/threads_on_pygt.html)
[http://www.pygtk.org/articles/cairo-pygtk-widgets/cairo-pygtk-widgets2.htm](http://www.pygtk.org/articles/cairo-pygtk-widgets/cairo-pygtk-widgets2.htm)

---

### Post by Quikee on 2008-03-24
Cool.. the program looks nice. ;)

The code is also OK on the first sight. It would be nice to give variable a more descriptive name and get rid of the global as they are totally unnecessary. For example ProcStatCPU could instantiate CPUStatStore and CPUStatGraph himself or got it provided through init (depends on how they relate - what are CPUStatStore and CPUStatGraph to the ProcStatCPU). 

On a second look some methods could also be abstracted further. 

Well done.

---

### Post by lnostdal on 2008-03-24
looks nice .. it runs with no performance problems here .. IBM ThinkPad R52:
```

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

```

---

### Post by | MM | on 2008-03-24
cool! i'll have a stab at getting rid of some of those globals tomorrow.  Thanks for the comments guys!  :D

---

### Post by kostkon on 2008-03-24
For me it crashed, only showing a strange cursor and it created PDFs (!!) of the desktop and open windows. I think it had a problem with some of the imports, maybe something Cairo related.

---

### Post by lnostdal on 2008-03-24
lol .. cairo has a pdf backend .. it probably tried to render to that instead of using any of the "screen backends" .. interesting outcome =)

edit:
a cause for this might be differences wrt. library versions .. maybe a version check should be implemented .. (i haven't looked at the code so i do not know whether it already does this)

---

### Post by | MM | on 2008-03-24
yea it needs a version check, ill add that.

---

### Post by Can+~ on 2008-03-24
I also think you should get rid of the global variables.

Also, I suggest splitting the code in:

-Agent that monitors the CPU.
-Drawing with Cairo.
-The GTK window (a simple .glade)

But in terms of the results, the applications runs smooth and it's pretty nice, congratulations, and if you're just learning python, heck, I can't imagine what you could do later.

*edit*
If you wonder how to use glade, it's pretty simple:
-Use glade 3 to create your window.
-on python use:

```

import gtk
import gtk.glade

#stuff here, a class, __init__...
self.xml = gtk.glade.XML("filename.glade")
self.window = self.xml.get_widget("widgetname")
```

---

### Post by | MM | on 2008-03-25
Thanks.  

I've made some changes, got rid of most of the globals (except the colours, but this i'll change also).  I removed one class.  added a version check, i just check for cairo version 1.4.0 or greater, if false i raise a SystemExit.  I made a few more methods out of blocks of code, so its a bit more organised.  I also made the values into percentages of total time, so that does away with worrying about time values, and actually simplifies things a bit.  

Finally, i added a background to the legend, so there's more contrast between the text and the graph when the graph gets drawn beneath the legend.

---

### Post by nvteighen on 2008-03-25
Wow... it looks great!

But with compiz enabled, I have to resize the window in order to make it work (if I don't do that, it keeps blank). If I disable it, it works perfectly. Maybe cairo has some conflict with compiz?

---

### Post by | MM | on 2008-03-26
> **nvteighen said:**
> Wow... it looks great!

But with compiz enabled, I have to resize the window in order to make it work (if I don't do that, it keeps blank). If I disable it, it works perfectly. Maybe cairo has some conflict with compiz?

wierd because i am sing compiz and it works...  so it redraws on an expose event but not when its called from the thread... strange

---

