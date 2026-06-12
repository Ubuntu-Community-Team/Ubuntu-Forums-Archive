---
title: "[SOLVED] Simple Question Regarding Using Gedit as a Programming Text Editor"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by Bad.Wulf on 2008-08-15
I was told that gedit would do highlighting, indenting, color coding, etc  for a variety of programming languages.  As this is my home PC I prefer a light text editor over heavy IDE's for the small scripts and programs I write for home type applications.  I was told gedit had many languages formats built in like Python, c++, c# etc.  How do I set it up for a given language I want to use?  I don't seem to see any language options.  I want to throw together a few Python scripts but I figured I might as well get gedit setup while I'm at it.

If gedit is not capable or has no plugins for what I described can someone point me at a more capable text editor like some of the equivalent editors for Windows I am used to.

Thanks for your time

---

### Post by DGortze380 on 2008-08-15
> **Bad.Wulf said:**
> I was told that gedit would do highlighting, indenting, color coding, etc  for a variety of programming languages.  As this is my home PC I prefer a light text editor over heavy IDE's for the small scripts and programs I write for home type applications.  I was told gedit had many languages formats built in like Python, c++, c# etc.  How do I set it up for a given language I want to use?  I don't seem to see any language options.  I want to throw together a few Python scripts but I figured I might as well get gedit setup while I'm at it.

If gedit is not capable or has no plugins for what I described can someone point me at a more capable text editor like some of the equivalent editors for Windows I am used to.

Thanks for your time

I use Geany

sudo apt-get install geany

---

### Post by jordanmthomas on 2008-08-15
For me, gedit automatically does syntax highlighting.  It figures out on its own what language I'm using once you save the file.

I admit I'm not sure what you mean when you say it "has many language formats built in"
Perhaps you could clarify?

---

### Post by drs305 on 2008-08-15
Gedit: Edit, Preferences, Plugins. There are some plugins pre-listed, including Python. I've added Tidy (an html editor). Synaptic has a set of plugins you can install (gedit-plugins).

Be sure to read appi2102's post below. You mentioned plugins but I think what he mentions is actually what you are looking for.

---

### Post by Bad.Wulf on 2008-08-15
Thanks drs, I still haven't gotten used to all the preferences and options being hidden in edit.

Thomas, I tried saving a .py file to see if it would use python highlighting and coloring before posting, it did not :confused:

If you are confused by that line I don't think anyone could clarify more specifically without talking to you like a child but I guess I will try....

All languages have syntax and all languages have customary formats for easier reading etc.  Example, we write our code with these indentations, spaces, and comments because it is easier to read and understand.

Decent text editors have these customary formats programmed to facilitate the user with things like tabs, highlighting, color coding, word completion etc....  I was told gedit "understood" a fare deal of languages including the ones I use frequently....

---

### Post by appi2012 on 2008-08-15
View -> Highlight Mode -> Choose language
Python is in the scripts sections

---

### Post by jordanmthomas on 2008-08-15
There's no need to speak to me like a child, I've just never heard syntax highlighting referred to as a "language format" so I asked for clarification.  I thought perhaps you wanted a button to compile c code or run your python script or something.

Also, the plugin drs305 mentioned is just a python console, it has nothing to do with gedit's syntax highlighting at all.

Something's wrong with your gedit if you saved a valid python script and it didn't detect it and color it appropriately.  In that case, try what appi2012 said.  I will say that I don't like gedit's syntax highlighting very much, though, and I don't find it very easy to customize.  If you do much editing at all, you'll probably end up looking for another editor.

---

