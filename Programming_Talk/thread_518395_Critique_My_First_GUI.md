---
title: "Critique My First GUI"
date: 2007-08-05
forum: Programming Talk
---

### Post by fatsheep on 2007-08-05
I have just written a little password generator python script and GUI with Glade and PyGTK.  I have attached it below, (the file to run is passgen_gui.py).  I am somewhat pleased with it but I would like input.  Here are a few of my concerns:

**1.**  When the expander is expanded, it pushes the buttons at the buttom down.  When it is collapsed, the buttons at the bottom do not come back up, leaving a big ugly space.  Is there a way to make the buttons "come back up"?  GIMP's menus do this so I'm sure it's possible, I just don't have a clue how.

**2.**  I would like to have the configuration of the GUI saved (what checkboxes are checked, what is in the text fields, whether or not the expander is expanded, etc...) and restored when passgen starts up again.  On an earlier version of this program, I tried doing that by writing to and reading from a file but that seems kind of messy to me.  Another option is using a class full of variables and pickling the class object but I haven't looked into that fully yet.  What are my options?

**3.**  Using glade did reduce the size of the file by quite a bit.  However, the method I have to import each widget with gtk.glade.XML.get_widget() is a bit tedious (lines 54-65 of passgen_gui.py).  Is there a better way?  

Guidance is much appreciated. :)

---

### Post by Nekiruhs on 2007-08-05
> **fatsheep said:**
> I have just written a little password generator python script and GUI with Glade and PyGTK.  I have attached it below, (the file to run is passgen_gui.py).  I am somewhat pleased with it but I would like input.  Here are a few of my concerns:

**1.**  When the expander is expanded, it pushes the buttons at the buttom down.  When it is collapsed, the buttons at the bottom do not come back up, leaving a big ugly space.  Is there a way to make the buttons "come back up"?  GIMP's menus do this so I'm sure it's possible, I just don't have a clue how.

**2.**  I would like to have the configuration of the GUI saved (what checkboxes are checked, what is in the text fields, whether or not the expander is expanded, etc...) and restored when passgen starts up again.  On an earlier version of this program, I tried doing that by writing to and reading from a file but that seems kind of messy to me.  Another option is using a class full of variables and pickling the class object but I haven't looked into that fully yet.  What are my options?

**3.**  Using glade did reduce the size of the file by quite a bit the way I have to import each widget with gtk.glade.XML.get_widget() is a bit tedious (lines 54-65 of passgen_gui.py).  Is there a better way?  

Guidance is much appreciated. :)
Nice. I am a few steps behind you in my learning. I am working on a project to make a front-end to the CLI program find. My main objective with this is to beable to use Regex filesystem searching from a GUI. As such, I too am interested in seeing if there is an easier way to import the widgets.

---

### Post by Lux Perpetua on 2007-08-05
Not bad at all. Possible extension: allow the user to specify that certain characters must appear in the password (e. g., password must contain at least one digit, one lowercase letter, and one capital letter).

---

### Post by pmasiar on 2007-08-05
Randomly generated passwords were tested and proved to be - hard to memorize, so users hate them. Instead, [better methods](http://wolfram.org/writing/howto/password.html) are suggested.

I have no problem with your program as training task (it's nice effort etc), but I wanted you to warn about inflicting your program on some innocent bystanders :-)

---

### Post by fatsheep on 2007-08-06
> **pmasiar said:**
> Randomly generated passwords were tested and proved to be - hard to memorize, so users hate them. Instead, [better methods](http://wolfram.org/writing/howto/password.html) are suggested.

I have no problem with your program as training task (it's nice effort etc), but I wanted you to warn about inflicting your program on some innocent bystanders :-)

Fair enough but how would I make this program generate easy to remember passwords?

---

### Post by Nekiruhs on 2007-08-06
> **fatsheep said:**
> Fair enough but how would I make this program generate easy to remember passwords?
Maybe take user input for a few words. And make a password from them.
Like you ask the user for some words they associate with themselves. Maybe they put a city, pets name, or something. Then you mix them around to generate a password. I remmber AOL did this sometime before.

---

### Post by pmasiar on 2007-08-06
> **Nekiruhs said:**
> 
Like you ask the user for some words they associate with themselves. Maybe they put a city, pets name, or something. 

This is exactly the *wrong* way to do it, and link above described why, did you bothered to read it?

You don't need program for it: user can make up a (longish) sentence which will be easy to remember.

If you want, you may make user to enter the sentence, and then make some magic on first letters: replace with 1337-speak, '=' instead of 'is' etc, but it is better made by user.

---

### Post by fatsheep on 2007-08-06
> **pmasiar said:**
> 
If you want, you may make user to enter the sentence, and then make some magic on first letters: replace with 1337-speak, '=' instead of 'is' etc, but it is better made by user.

That's not a bad idea.  I'll try that.

---

### Post by Nekiruhs on 2007-08-06
I just thought of it! We could do a big for loop for every line in the .glade file. Then check to see if the line matches a Regex, when we find the line that contains the name of the widget, extract it with regex and pass it to GTK.

---

### Post by fatsheep on 2007-08-06
> **Nekiruhs said:**
> I just thought of it! We could do a big for loop for every line in the .glade file. Then check to see if the line matches a Regex, when we find the line that contains the name of the widget, extract it with regex and pass it to GTK.

What is this for?  Extracting widgets from the xml?  If so, there's an inbuilt function for that.  gtk.glade.XML is the XML class which has the get_widget(widget_name) function.  So... 

```

xml = gtk.glade.XML("yourgladefile.glade")
window = xml.get_widget("window1")

```

would import the "window1" widget from the glade XML file as window.  For more information, see the gtk.glade.XML pyGTK class reference page:

[http://www.pygtk.org/docs/pygtk/class-gladexml.html](http://www.pygtk.org/docs/pygtk/class-gladexml.html)

Also, check out the gui script in the attached archive as I use this method.

---

### Post by Nekiruhs on 2007-08-06
> **fatsheep said:**
> What is this for?  Extracting widgets from the xml?  If so, there's an inbuilt function for that.  gtk.glade.XML is the XML class which has the get_widget(widget_name) function.  So... 

```

xml = gtk.glade.XML("yourgladefile.glade")
window = xml.get_widget("window1")

```

would import the "window1" widget from the glade XML file as window.  For more information, see the gtk.glade.XML pyGTK class reference page:

[http://www.pygtk.org/docs/pygtk/class-gladexml.html](http://www.pygtk.org/docs/pygtk/class-gladexml.html)

Also, check out the gui script in the attached archive as I use this method.
I know, you said it was cumbersome to list all the widgets. I was thinking that we could use regexes to extract the names of the widgets and pass them to get_widget(). That way you would have them passed to pygtk without listing them all. Also you could change the glade file and it would adapt automatically.

---

### Post by cprofitt on 2007-08-06
I have not run your program yet, but I made a random password generator to use when importing users to Active Directory. The purpose of the random password was to serve as a temporary password only. The users were required to change their passwords upon first logon.

I allowed the following items to be set by the user:

number of characters (7-14)
complex (true or false)
- complex passwords contained 1 cap letter, one non-alphanumeric, one numeric and the rest small case letters.

I also allowed them to import the passwords from a file; though that would not be applicable in your case.

To build a more sophisticated system you could make an array of words and allow you program to merge two or move of them together - though that would result in more crackable passwords. I would never use a pregenerated password as a permanent password because of the inability of users to remember it so I didn't worry about using words.

if I get time I will download your app and run it so I can give you specific input.

---

### Post by Nekiruhs on 2007-08-06
> **Nekiruhs said:**
> I know, you said it was cumbersome to list all the widgets. I was thinking that we could use regexes to extract the names of the widgets and pass them to get_widget(). That way you would have them passed to pygtk without listing them all. Also you could change the glade file and it would adapt automatically.
So close... I got the glade file imported, and i've iterated through it. Now I just need to perfect the regex.

---

### Post by fatsheep on 2007-08-07
> **Nekiruhs said:**
> So close... I got the glade file imported, and i've iterated through it. Now I just need to perfect the regex.

If you get something working, please do post it.  However, also note that you probably don't want to import *everything* from the gladefile, you only want to import what you are going to manipulate.  For example, importing an HBox object would only be useful if you are going to manipulate it (pack more items into it, reorder it, etc...).  You don't have to worry about that now, but once you do get it working where it imports all of the widgets in the gladefile, the next step would be to specify which objects you are importing and what you are importing them as.

---

### Post by pmasiar on 2007-08-07
"from <module> import *" is wrong: it pollutes your namespace with Guido-knows-what. Ie you may have your own function with same name, and it will silently clash. Or you will get error report for a name, and you have no idea where this name came from.

Always import only selected names: "from <module> import n1, n2", or if you need whole module, import it as-is, and qualify names:

```

import mmm
mmm.n1()

```

---

### Post by fatsheep on 2007-08-08
> **pmasiar said:**
> "from <module> import *" is wrong: it pollutes your namespace with Guido-knows-what. Ie you may have your own function with same name, and it will silently clash. Or you will get error report for a name, and you have no idea where this name came from.

Always import only selected names: "from <module> import n1, n2", or if you need whole module, import it as-is, and qualify names:

```

import mmm
mmm.n1()

```

What exactly are you refering to?  I don't believe I did that in my script...

---

### Post by fatsheep on 2007-08-09
Does anyone have comments concerning questions #1 and #2 of my first post?

---

### Post by pmasiar on 2007-08-09
> **fatsheep said:**
> 
**2.**  I would like to have the configuration of the GUI saved (what checkboxes are checked, what is in the text fields, whether or not the expander is expanded, etc...) and restored when passgen starts up again.  

remember: "batteries are included!": [http://docs.python.org/lib/module-ConfigParser.html](http://docs.python.org/lib/module-ConfigParser.html)

---

### Post by charlie763 on 2007-08-18
If anyone is interested in using Glade and Python, I would highly recommend taking a look at [Gladex: https://help.ubuntu.com/community/Gladex]("https://help.ubuntu.com/community/Gladex").

---

