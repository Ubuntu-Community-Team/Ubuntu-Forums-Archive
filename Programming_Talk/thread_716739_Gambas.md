---
title: "Gambas"
date: 2008-03-06
forum: Programming Talk
---

### Post by joshdudeha on 2008-03-06
I want to start programming using gambas.
But what language shall I learn as I can not find many tutorials for the Gambas language.
Should I just use Basic?

---

### Post by DoktorSeven on 2008-03-06
Well, Gambas *is* BASIC (well, almost, **G**ambas **A**lmost **M**eans **BAS**IC), so you'll just be doing BASIC, but with GAMBAS's particular dialect.

Check their [documentation page](http://gambas.sourceforge.net/documentation.html) for docs, tutorials, etc.

---

### Post by pmasiar on 2008-03-06
Is there specific reason why you choose Basic, and Gambas? Or you want just to learn programming, and someone told you that Basic is the easiest way?

---

### Post by joshdudeha on 2008-03-07
Well, I want to do RAD programming, with the drag and drop program building. I'd rather use C++ but I can't find a RAD tool to code with C++. I mean, I can code up terminal applications, but coding GUI's in plain code is very difficult.
Any suggestions??
Thanks

---

### Post by Zugzwang on 2008-03-07
> **joshdudeha said:**
> Well, I want to do RAD programming, with the drag and drop program building. I'd rather use C++ but I can't find a RAD tool to code with C++. I mean, I can code up terminal applications, but coding GUI's in plain code is very difficult.


The reason pmasiar is asking is that pmasiar almost always suggests using Python in cases in which the language isn't really fixed (and pmasiar suggests that for a good reason, btw). :) So in fact you *do* have a couple of alternatives for fast GUI building. One of it is the often proposed combination of Python and the Glade GUI designer. As far as I know, there is still a little bit of work to do manually (connecting the GUI elements to your code so that it gets called when the user clicks on a button, for example). This should however be quite straight-forward. 

There are however quite some more alternatives - personally, I prefer the Netbeans GUI builder (without the new Mantisse stuff) for making applications in Java, but it's really just a matter of taste. Unless you have some very specific requirement for you application, you should go fine with any of them. 

If you want to use C++ (unrecommended by a lot of people here), you might want to check out the QT framework and its GUI builder. I found it quite straight-forward to use (except for the adaptation of the build process). You can however also use GLADE and GTK with C++ (or C). And if I remember correctly, there's also a GUI builder for the wxWidgets framework.

You might of course as well stick with GAMBAS.

So you've got plenty of possibilities.

---

### Post by njkt on 2008-03-07
You might take a look at [GTK--]("http://www.gtkmm.org/") and [Glade]("http://glade.gnome.org/") which has a c++ binding, though it's been some time since I've checked up on glade--

---

### Post by joshdudeha on 2008-03-07
Thanks for everyones help.
Will check out all the suggested possibilities for programming.
One problem I have with glade, is that after designing the user interface, I can't add any code to things like buttons.
Could someone please clarify?
Thanks

---

### Post by njkt on 2008-03-07
What glade does is simply create the skeleton file for you, so you can compile it and run it to view the GUI.  You need to go into the actual source files and program your own responces to the events (from buttons and such).

Make sure when using glade you attach an event to your widgets, i would suggest looking at the glade documentation.

---

### Post by LaRoza on 2008-03-07
Don't jump into GUI's too fast.

Learn how to use the language first.

I feel that RAD tools are for advanced programmers that know what they are doing, not for learners using them as a crutch.

---

### Post by hammer v2 on 2008-03-09
Hey if you want a crutch and want to get something done quickly then GAMBAS absolutely rocks!!! 

Depends what you're trying to achieve here.

If you want to be a "proper" programmer (i.e do this for a living) then probably going down the GLADE route and a hardcore language like C++ is the way forward.

If you just want to get a project done quickly with miminal learning curve then GAMBAS is a good way of getting from point a to point b. 

It's brilliantly designed and is a one-stop-shop. The IDE, GUI,even the packaging is handled by the gambas program. 

Like I said, horses for courses...If you're going to create a huge multimedia program or game then GAMBAS would suck....but if you need to make some quick Point of sale stuff, Database front end, GUI configuration options or even a quick front end to a command line app..then GAMBAS is a good choice.

P.S it is well documented. here's the gambas bible;
[http://vectorlinux.osuosl.org/Uelsk8s/gambas-beginner-guide.pdf](http://vectorlinux.osuosl.org/Uelsk8s/gambas-beginner-guide.pdf)

Whichever way you go...good luck with your project!

---

