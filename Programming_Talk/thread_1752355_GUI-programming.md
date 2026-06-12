---
title: "GUI-programming"
date: 2011-05-07
forum: Programming Talk
---

### Post by Tijssiej on 2011-05-07
Hello,

First of all I'd like to say that I'm not very familiar with linux programming. I've got a bit of problems with getting into it. On windows I tried some programming in C++ and also in C#. I also made websites with HTML/CSS/PHP/MYSQL... So, I know some basic stuff.

In ubuntu I don't really know where to start. I read about Python, but my problem with python is that it has different versions. After looking to Python, I checked C++. It was very easy for me to use code::blocks. But I don't really know how to use tools like I was able in Visual Studio(on windows).

Here is my question:
Is C++ a good programming language for developing on linux? Could someone help me or giving me some web links how to use tools like buttons/text boxes e.d. in code::blocks, or is it better using other programs?

~Tijssiej

p.s. Sorry for my bad english. Currently I'm running xubuntu on my netbook.

---

### Post by cgroza on 2011-05-07
C++ is a great language for Ubuntu. Also C#, Python, Ruby or C.
You can use Glade(GTK) or QtDesigner(Qt) to build UIs. Although I suggest you to learn to program those toolkits by hand first to learn the API.

As for python, version 2.7 is perfect for programming, that is not really a problem.

---

### Post by Tijssiej on 2011-05-07
> **cgroza said:**
> C++ is a great language for Ubuntu. Also C#, Python, Ruby or C.
You can use Glade(GTK) or QtDesigner(Qt) to build UIs. Although I suggest you to learn to program those toolkits by hand first to learn the API.

As for python, version 2.7 is perfect for programming, that is not really a problem.

I was googling againg and now I found something called gtkmm. This is a library for creating GUI apps, I read. Someone experience with this? I will now check their web page...

---

### Post by cgroza on 2011-05-07
> **Tijssiej said:**
> I was googling againg and now I found something called gtkmm. This is a library for creating GUI apps, I read. Someone experience with this? I will now check their web page...
No, but I have some experience with wxWidgets. Very good toolkit and looks native on any platform.
I think there is a designer for it too (wxForms coming to mind.)

---

### Post by farproc on 2011-05-08
For some reason, developer.ubuntu.com is a rather well kept secret.

As a Visual C++ developer (on Windows) I initially tried Code::Blocks - However Anjuta ( [http://developer.ubuntu.com/create/anjuta/](http://developer.ubuntu.com/create/anjuta/) ) is a far better environment for developing apps for Ubuntu. Find it in the Ubuntu software center and also select and install the associated packages to get a C / C++ dev environment up with a minimum of fuss.

---

### Post by simeon87 on 2011-05-08
What are your development goals? You can create a GUI application with Python and GTK+ in minutes which would takes many lines of code in C or C++. Unless you really need the raw speed of C/C++, why not use a language such as Python? If it turns out that you do need the speed, you can write code in C and call that from Python.

---

### Post by SledgeHammer_999 on 2011-05-08
> **Tijssiej said:**
> I was googling againg and now I found something called gtkmm. This is a library for creating GUI apps, I read. Someone experience with this? I will now check their web page...

Yes. If you're going for C++ and Gtk+ then I suggest you use Gtkmm. Gtkmm is a C++ wrapper around the Gtk+ C API.

---

### Post by Tijssiej on 2011-05-08
> **simeon87 said:**
> What are your development goals? You can create a GUI application with Python and GTK+ in minutes which would takes many lines of code in C or C++. Unless you really need the raw speed of C/C++, why not use a language such as Python? If it turns out that you do need the speed, you can write code in C and call that from Python.

Well I'm used to Visual C# and Visual C++. I had the ability to just drag and drop some objects from the toolbar to a windows form. I prefer something like that on linux. Or an easy language with less code. Because I don't really need to know all the details of what's behind a simple Hello World program.

What do I want to make? For example a simple webbrowser or perhaps a media player.

In python, I just don't know the version I have to pick and how to start GUI-developing in an easy way.

---

### Post by simeon87 on 2011-05-08
> **Tijssiej said:**
> Well I'm used to Visual C# and Visual C++. I had the ability to just drag and drop some objects from the toolbar to a windows form. I prefer something like that on linux. Or an easy language with less code. Because I don't really need to know all the details of what's behind a simple Hello World program.

What do I want to make? For example a simple webbrowser or perhaps a media player.

In python, I just don't know the version I have to pick and how to start GUI-developing in an easy way.

You can drag-and-drop with Glade: [http://glade.gnome.org/](http://glade.gnome.org/) . Then you can load the GUI in various languages, including C, C++ and Python. The reason that I'm more or less recommending Python is that for many applications Python works well. Unless you're creating something that is computationally intensive, Python is enough to display a GUI and make something that works.

To get something done, Python requires the least amount of code compared to the many lines of code that are needed in C/C++.

---

### Post by Tijssiej on 2011-05-08
> **simeon87 said:**
> You can drag-and-drop with Glade: [http://glade.gnome.org/](http://glade.gnome.org/) . Then you can load the GUI in various languages, including C, C++ and Python. The reason that I'm more or less recommending Python is that for many applications Python works well. Unless you're creating something that is computationally intensive, Python is enough to display a GUI and make something that works.

To get something done, Python requires the least amount of code compared to the many lines of code that are needed in C/C++.

Do you also have some tutorials for me working with python and glade? What version of python do you recommend?

---

### Post by simeon87 on 2011-05-08
> **Tijssiej said:**
> Do you also have some tutorials for me working with python and glade? What version of python do you recommend?

There are some tutorials here: [http://live.gnome.org/Glade/Tutorials](http://live.gnome.org/Glade/Tutorials) from 2009 (just check if they are still current). Basically, you design the GUI in Glade which produces an XML file. You can then load the XML file in Python. You may have to search for some other tutorials, have a look at the documentation as well.

Most Ubuntu version will have Python 2.x installed. You can check your Python version by typing ```
python --version
``` in a terminal window. You can also start with Python 3 if you like but not all libraries may have been updated for Python 3 yet. Python 3 is, of course, newer and it's the future of Python so if you're new to Python you may wish to start learning there. The version of Python that you have installed should be sufficient.

---

### Post by Tijssiej on 2011-05-08
> **simeon87 said:**
> There are some tutorials here: [http://live.gnome.org/Glade/Tutorials](http://live.gnome.org/Glade/Tutorials) from 2009 (just check if they are still current). Basically, you design the GUI in Glade which produces an XML file. You can then load the XML file in Python. You may have to search for some other tutorials, have a look at the documentation as well.

Most Ubuntu version will have Python 2.x installed. You can check your Python version by typing ```
python --version
``` in a terminal window. You can also start with Python 3 if you like but not all libraries may have been updated for Python 3 yet. Python 3 is, of course, newer and it's the future of Python so if you're new to Python you may wish to start learning there. The version of Python that you have installed should be sufficient.

Thanks for your help already, I will install it on my netbook soon and if I have more questions I'll ask them. :)

---

### Post by cgroza on 2011-05-08
> **Tijssiej said:**
> Thanks for your help already, I will install it on my netbook soon and if I have more questions I'll ask them. :)
It is already installed on Ubuntu.

---

### Post by Tijssiej on 2011-05-08
> **cgroza said:**
> It is already installed on Ubuntu.

Glade isn't :)

---

### Post by cgroza on 2011-05-08
> **Tijssiej said:**
> Glade isn't :)
"It" can mean anything.:D
If you choose wxWidgets (the bindings for python are wxPython) there is python-wxglade which is glade, but for wxPython.

---

