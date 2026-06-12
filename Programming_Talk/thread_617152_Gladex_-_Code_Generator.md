---
title: "Gladex - Code Generator"
date: 2007-11-19
forum: Programming Talk
---

### Post by charlie763 on 2007-11-19
[SIZE="5"]Gladex 0.4.1 is released![/SIZE]

**What is Gladex?**
Gladex is a Python application which takes a .glade file written in the [ Glade User Interface Builder]("http://glade.gnome.org/") and generates code in Perl, Python, or Ruby. The generated code uses libglade to draw a GUI and is not raw pygtk code. Support for additional languages can be added through the plugin API.

**Why Gladex?**
Gladex is a response to several inadequacies found in other scripts that template code. Many scripts were unmaintained, confusing to use, or did not do what we needed them to do. Gladex is unique among these programs in that it has a plugin architecture allowing many languages to be supported through one interface.

**What is the future of Gladex?**
Our goal is to consolide the functionality of and eventually depreciate similar applications such as [glc (Python)]("http://glc.sourceforge.net/"), [tepache (Python)]("http://www.gnomefiles.org/app.php/tepache"), [PyGCG (Python)]("https://launchpad.net/pygcg/"), [eglade (Eiffel)]("http://efsa.sourceforge.net/archive/elphick/eglade.htm"), [Glade# (C#)]("http://eric.extremeboredom.net/2005/06/08/203"), and [ruby-glade-create-template (Ruby)]("http://ruby-gnome2.sourceforge.jp/hiki.cgi?ruby-glade-create-template")

**How can I help?**
Any feedback in this thread would be greatly appreciated as that will help us shape the future of Gladex. Specific comments would be great since that might help us decide what should change and what should remain as the application develops. Also, questions would be very helpful because answering them here will help us write documentation that addresses common questions.

We need help in four main areas:
[LIST]
[*]Testing - Testers are always needed, so we can squash those bugs.
[*]Development - We would love for others to write plugins for languages they are familiar with. Let us know if you are interested in development.
[*]Packaging - Our main need is for an expert packager to give us a hand making a proper source package for use with Launchpad's PPA system.
[*]Documentation - The manual is pretty good, but we could an update to the [wiki]("https://help.ubuntu.com/community/Gladex") and the [tutorial]("https://help.ubuntu.com/community/GladexHowto") pages.
[/LIST]

**Where can I find more information?**
Project main page: [http://www.openphysics.org/~gladex/](http://www.openphysics.org/~gladex/)
Screenshots: [https://help.ubuntu.com/community/Gladex#head-7e96fd09c298bd55b4263eae62e46d8350c2a96e](https://help.ubuntu.com/community/Gladex#head-7e96fd09c298bd55b4263eae62e46d8350c2a96e)
Download: [https://launchpad.net/gladex/+download](https://launchpad.net/gladex/+download)
Manual: [http://www.openphysics.org/~gladex/gladex-manual/](http://www.openphysics.org/~gladex/gladex-manual/)
Launchpad: [https://launchpad.net/gladex](https://launchpad.net/gladex)
Howto: [https://help.ubuntu.com/community/GladexHowto](https://help.ubuntu.com/community/GladexHowto) (outdated)
About wiki: [https://help.ubuntu.com/community/Gladex](https://help.ubuntu.com/community/Gladex) (outdated)

---

### Post by mevets on 2007-11-19
thanks man, i am definetly going to check this out

---

### Post by charlie763 on 2007-11-24
Is there anyone out there who would help make a source package? I'd like to get this in a Launchpad PPA and eventually into Hardy.

---

### Post by Nekiruhs on 2007-11-24
Any word on  how the raw code generation is coming? Was my code of any use? Post #6:  [http://ubuntuforums.org/showthread.php?t=529925&highlight=Gladex](http://ubuntuforums.org/showthread.php?t=529925&highlight=Gladex)

---

### Post by charlie763 on 2007-11-24
> **Nekiruhs said:**
> Any word on  how the raw code generation is coming? Was my code of any use? Post #6:  [http://ubuntuforums.org/showthread.php?t=529925&highlight=Gladex](http://ubuntuforums.org/showthread.php?t=529925&highlight=Gladex)

We took a look at it and have since incorporated similar functionality into Gladex. My brother did the coding, so I don't know if he used any of your code or not. Either way, I'm pretty sure it helped.

There hasn't been much going on with the raw code generator. Checkout the [plugin-pygcg]("https://blueprints.launchpad.net/gladex/+spec/plugin-pygcg") blueprint for information on our plans. I think we'll use [pygcg]("https://launchpad.net/pygcg/") if it develops to a usable state. However, that does not look too promising. This Winter break (I'm a teacher) I'll sit down and make a real effort get that done.

---

### Post by paxmanchris on 2007-11-24
> **Nekiruhs said:**
> Any word on  how the raw code generation is coming? Was my code of any use? Post #6:  [http://ubuntuforums.org/showthread.php?t=529925&highlight=Gladex](http://ubuntuforums.org/showthread.php?t=529925&highlight=Gladex)

Your code did help a little. It mostly gave me a good idea.

I attached a unstable early "jist" of what I want to do. It only works with modification of the output file.

instructions:
1)downloade gladetocode.py

2)make a glade file, of one visible window with one button pack in it. Save this in the same directory as the script and name it testing.py

3) run the the gladetocode.py script like this
```

python gladetocode.py testing.py > out.py

```
this will generate a file called out.py 
4) open out.py
you should see two lines like this:
```

		button1.set_property("label","button")
		button1.set_property("response_id",0)

```
remove them.
then replace this line:
```

button1 = gtk.Button()

```
with this:
```

button1 = gtk.Button("clickme")

```

I think you should get some output if you make the button have a function.

in some situations the scrip wont work, like Menus. I hope to work out the details and figure out a way to handle all of the possible widgets that glade offers. And I want to do this in the most simplest   way possible... in such a way that the perl, python, or any plugin can tap into it and define what the output should be.

---

