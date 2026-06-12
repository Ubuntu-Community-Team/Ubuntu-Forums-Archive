---
title: "Good tool/IDE for GTK+python"
date: 2009-11-06
forum: Programming Talk
---

### Post by hellmet on 2009-11-06
I want to create simple interfaces for some command-line only programs. After some reading, I decided to use GTK for the GUI and Python for the code (since I'm slightly familiar with Python already).  

I browsed through the software center, but wasn't able to figure a neat tool for programming GUI using Python and GTK. What do you guys use? 

Appreciate your help.

---

### Post by steeleyuk on 2009-11-06
Well you can hard core the GUI, just by typing into the same source code file as the rest of the Python code. OK for learning and small applications, I suppose. Alternatively, you can use Glade and connect the Glade source file with the Python source file. Makes modifying the code simpler in some respects and gives you a separation between the interface and the code.

You might want to take a look at Zenity though. Depending on how complex these apps are, Zenity might just do a good enough job.

---

### Post by maximinus_uk on 2009-11-08
The obvious answer is Glade, but to be honest I generally hand code any GUI that I need to write.

That's not just a knee-jerk 'not written here' response to auto-generated code or saying anything bad about Glade itself; it's just not THAT difficult to build them yourself once you understand how GTK+ works.

---

### Post by hellmet on 2009-11-08
Hmm.. thank you guys. I've installed Glade, and IDLE. The learning shall begin!!

---

### Post by jesuisbenjamin on 2009-11-16
Hello there,

i also would like to make some simple GUI for a program i have built with Python (i am a beginner). 
Now i have downloaded Glade, went quickly through tutorials, but nothing could give me an insight as to how i 'connect' my program to the interface i would make on Glade. How does it work? 
Besides Glade generates C code and those tutorials suggest some C coding on top of using Glade. I'm not really into learning C right now, i am just beginning to use Python. And how is the choice of library affecting my GUI?

So do yo guys know a good tutorial? Is there any simple overview of how the GUI is fitting in a program/code?

I am also very curious about what maximinus_uk said:
> it's just not THAT difficult to build them yourself once you understand how GTK+ works. 

Is it better to start with Glade or hand-writing in order to learn about GUI?  (If hand-writing GUI isn't a titanic task... i plan to round this up before i get gray hair...)

Thanks for your help!

---

### Post by diesch on 2009-11-16
> **jesuisbenjamin said:**
> Hello there,

i also would like to make some simple GUI for a program i have built with Python (i am a beginner). 
Now i have downloaded Glade, went quickly through tutorials, but nothing could give me an insight as to how i 'connect' my program to the interface i would make on Glade. How does it work? 
Besides Glade generates C code and those tutorials suggest some C coding on top of using Glade. I'm not really into learning C right now, i am just beginning to use Python. And how is the choice of library affecting my GUI?

So do yo guys know a good tutorial? Is there any simple overview of how the GUI is fitting in a program/code?


[http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html) has examples in C and Python - just ignore the C parts.

> **jesuisbenjamin said:**
> 
Is it better to start with Glade or hand-writing in order to learn about GUI?  (If hand-writing GUI isn't a titanic task... i plan to round this up before i get gray hair...)


That's just a matter of taste. All the event handling and business logic stuff is the same for both ways.

---

### Post by oldfred on 2009-11-16
+1 on diesch link to micahcarrick

I used some of his older glade tutorials that were before builder. I wanted to use builder as it was the new way at that time. Glade now directly writes the builder version of the html file you connect to from glade into python.

I like using geany as my editor as I can run the program. It lacks debugging but it is easy to add print statements to check variables for debugging purposes.  I often paste some sample code into geany, (you have to save as .py before it works) and then run it to understand what is happening.

---

### Post by Can+~ on 2009-11-16
> **jesuisbenjamin said:**
> Besides Glade generates C code and those tutorials suggest some C coding on top of using Glade. I'm not really into learning C right now, i am just beginning to use Python. And how is the choice of library affecting my GUI?

I feel that you installed the older version of Glade, that generates only C code and .glade files. Search for glade3 on the repos.

---

### Post by jesuisbenjamin on 2009-11-17
> **Can+~ said:**
> I feel that you installed the older version of Glade, that generates only C code and .glade files. Search for glade3 on the repos.

OH i have glade3, thanks for checking -- the tutorial wasn't the right one though...;)

---

### Post by hellmet on 2009-11-17
@jesui... (sry, lazy)
I'm stuck at the same place man.. All tutorials speak in detail, until the point where GUI connects to code. After that its a sample code and some comments and.. good bye!

I would really like a detailed tutorial explaining how each component of GUI can be integrated into the python code.

---

### Post by Can+~ on 2009-11-17
> **hellmet said:**
> @jesui... (sry, lazy)
I'm stuck at the same place man.. All tutorials speak in detail, until the point where GUI connects to code. After that its a sample code and some comments and.. good bye!

I would really like a detailed tutorial explaining how each component of GUI can be integrated into the python code.

Off to the reference.

The GUI connects to code only through: Events and references. It's as simple as that, whenever a button is pushed, text field written to, or anything, you can add a string in the "event window" (can't remember the exact name on Glade3), and append that signal to the python dictionary, and attach a method to decide what to do.

Whenever you need help on a particular component, then head to the reference.

---

### Post by oldfred on 2009-11-17
Here is part of a program I am working on. The glade file exported as a builder file is testimport.glade, I show just some of the other objects: Then I have code to handle all the buttons etc.

Some code to check stuff
try:
            self.builder = gtk.Builder()
            self.builder.add_from_file("testimport.glade")
        except:
            self.show_error_dlg("Failed to load UI XML file: testimport.glade")
            sys.exit(1)

        # get the widgets which will be referenced in callbacks
        self.window = self.builder.get_object("window1")
        self.notebook1 = self.builder.get_object("notebook1")
        self.statusbar = self.builder.get_object("statusbar")
        self.btnimport = self.builder.get_object("btnImport")
        self.btnStore = self.builder.get_object("btnStore")
        self.btnAdd = self.builder.get_object("btnAdd")
        self.btnGetName = self.builder.get_object("btnGetName")

---

### Post by diesch on 2009-11-18
If you define the event handlers in Glade using the "Signals" properties you can use

  ```
self.builder.connect_signals(self)
```

to automatically connect the event handlers to the corresponding methods of your class.

---

### Post by FirstByté on 2009-12-03
> **diesch said:**
> [http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html) has examples in C and Python - just ignore the C parts.



That's just a matter of taste. All the event handling and business logic stuff is the same for both ways.

Thanks for this, I'll surely try it out. I can't believe I've not done any 'Hello World' since I moved to Ubuntu. :(

I started checking out QT but suspect GTK+ might just be the way.

Thanks once again for the guide.;)

---

