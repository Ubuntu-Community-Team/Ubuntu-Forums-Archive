---
title: "visual programming"
date: 2010-07-04
forum: Programming Talk
---

### Post by kokoshmusun on 2010-07-04
I'm not a programmer and I've been trying to make some time to learn Python and maybe Java (but there's too much on my plate nowadays).  In the meanwhile, I'm interested in understanding whether Visual Programming is really a feasible starting point for someone who wants to develop relatively basic applications.

I've done an extensive search on it a couple of times but have only gotten more confused. So, can you really program by drag & drop method in a GUI or is this a joke?  Or at least, would visual programming help one get started in real programming?  And if positive, what are the options (i.e., which visual programming language seems the right place to go to in your view?).

cheers!

---

### Post by StephenF on 2010-07-04
Visual programming is frequently used to program Programmable Logic Controllers as used in industrial machinery.
[http://en.wikipedia.org/wiki/Ladder_logic](http://en.wikipedia.org/wiki/Ladder_logic)

So definitely not a joke. You could program an entire production line like this.

---

### Post by JayD239 on 2010-07-05
These tools do exist. Although you can't expect to click, drag and have a complete application. You can use a graphical editor to design your GUI, but you will have code the function to the GUI yourself.

There is the Visual Editor project for eclipse: [http://www.eclipse.org/vep/](http://www.eclipse.org/vep/). 
I suppose its for Java (Swing) but the website also mentions C(++)

A similar thing for Netbeans: [http://netbeans.org/features/java/swing.html](http://netbeans.org/features/java/swing.html)
This looks more Java only.

I am not sure how good these projects are nowadays. A couple of years ago i couldn't make much with the Visual Editor in Eclipse but i might have improved (to be fair, i didn't put too much effort in it). But I bet none of them come near the GUI-editing options in Visual Studio. VS works great but it will only do c++, c# j# and other Microsoft languages.

My advice: The hardest part of an GUI application is the functionality. Using listeners and events. This would be easier to apply to the code you made by yourself then by a some generated code since, because you're a beginning programmer, you will have to figure out what every piece of code does. 

Java Swing is not that hard to understand and there are some very good [tutorials](http://java.sun.com/docs/books/tutorial/uiswing/start/index.html) by Sun. Try the [Hello World](http://java.sun.com/docs/books/tutorial/uiswing/examples/start/HelloWorldSwingProject/src/start/HelloWorldSwing.java) and [Button demo](http://java.sun.com/docs/books/tutorial/uiswing/examples/components/ButtonDemoProject/src/components/ButtonDemo.java)

---

### Post by kalaharix on 2010-07-05
Try Gambas. Gambas is a modern, robust programming language in the BASIC family. It has a drag and drop GUI which appeals to new programmers. On Ubuntu 10.04, don't install from 'Ubuntu Software Centre'. Rather open Terminal (Applications,Accessories,Terminal) and enter the following:
'sudo apt-get install gambas2' (without parentheses)
give the password and follow the instructions. You should then be able to run Gambas from the same terminal window by entering 'gambas2'. It will also appear in the menu system.

You can find the obligatory 'Hello World' application as a tutorial at:
[http://gambas.sourceforge.net/Getting%20Started%20with%20GAMBAS.odt](http://gambas.sourceforge.net/Getting%20Started%20with%20GAMBAS.odt)

---

### Post by Tony Flury on 2010-07-05
I think the OP was referring to Visual Programming languages - where by you define the structure of your program by using graphical elements that you connect together, rather than refering to GUI designers and IDEs.

IF you want an example of a Visual programming Language - the archetype seems to be scratch : [http://scratch.mit.edu/](http://scratch.mit.edu/) 

Although languages such as GAMBAS, VB etc do have strongly integrated GUI editors (with drag and drop of GUI elements etc), you still have to code any advanced behaviour with a lot of text - i.e. what to do when a button is clicked.

---

### Post by kokoshmusun on 2010-07-05
Right on Tony... I found a number of visual programming languages, including scratch, but was confused about them... There is mindscript, tersus, limnor, phrogram, etoys, etc.  Just google or del.icio.us. 

Since you pointed me in that direction, I will look further into scratch. 

I'm happy to learn and do text programming.  Indeed, I get a kick out of figuring out code (last time I did that was trying to modify a wordpress template, and it was fun without any knowledge of php and css).  However, I thought it might be nice to program the skeleton with a visual language, and then fix the code.

In any case, eventually I would like to master at least Python and hopefully Java, and either or both would be more than enough for my needs.

Thanks to all the responders...

---

### Post by juancarlospaco on 2010-07-05
[First go Here]("http://iamar.net/subpages/PythonVid.html")
[Then go here]("http://www.tutorialspoint.com/python/python_gui_programming.htm")

*happy hacking*

---

### Post by fatality_uk on 2010-07-05
I would suggest having a look at Lazarus ([http://www.lazarus.freepascal.org/](http://www.lazarus.freepascal.org/))
You can very quickly create an app, visually and then delve into the programming.

It's cross platform, Linux (GTK1/GTK2/QT), Mac & Windows (All versions inc Windows 7 and even Windows Mobile 6.1)

Want OpenGL. Does that too with ease.

Have a look.

---

### Post by CptPicard on 2010-07-05
Visual programming may work for some limited domains, but in general, it is totally inappropriate. The core issue of computation is expression of recursion, either implicitly or explicitly, and how do you plan on doing that graphically? Perhaps with some kind of a flow graph, but if you understand that, you're good to go with regular programming languages...

---

### Post by mmix on 2010-07-05
Definitely it is not joke, but still immature, IMHO.

[http://en.wikipedia.org/wiki/Visual_programming_language](http://en.wikipedia.org/wiki/Visual_programming_language)

---

