---
title: "System/ About Ubuntu Program"
date: 2008-05-26
forum: Programming Talk
---

### Post by saj0577 on 2008-05-26
How would i go about creating my own program like this and what language would be best?

System/About Ubuntu

Saj

---

### Post by LaRoza on 2008-05-26
> **saj0577 said:**
> How would i go about creating my own program like this and what language would be best?

System/About Ubuntu

Saj

Not exactly what you want to find out. To get info on the machine, you will just need a text processing language. Shell (and standard Unix tools), Perl, Python, or Ruby.

Try this for starters:
```

cat /proc/cpuinfo | grep "model name"

```

Am I getting what you want?

---

### Post by saj0577 on 2008-05-27
I want more how i would make an applicaton that I can make it read a basic text file in a windowed window like that (but not inside a text editor) do you understand?

Saj

---

### Post by xlinuks on 2008-05-27
There is such a program, called "sysinfo", to install it type
```

sudo apt-get install sysinfo

```

I contains lots of info, I guess it's what you're looking for, to the left you find tabs to select the type of info you're looking for.

---

### Post by Dambrosio on 2008-05-27
saj,
I have been working with Qt4 which is based on C++. It is used to create programs (KDE uses it for their operating system). Here is a good tutorial to get started with Qt4: 
[Create a Linux Desktop App...]("http://www.clivecooper.co.uk/tutorial/index.html")

Is this what you are looking for?

Dan

---

### Post by saj0577 on 2008-05-27
Yeah thanks alot just without the add box of course. :)
Thank You.

Is that possible in python as well just as easily?


Saj

---

### Post by pointone on 2008-05-27
The "About Ubuntu" program is ***yelp***, and you can browse/edit the source code yourself, if interested:

```
apt-get source yelp
```

> **saj0577 said:**
> I want more how i would make an applicaton that I can make it read a basic text file in a windowed window like that (but not inside a text editor) do you understand?

This would be very simple to accomplish with Python + GTK (for Ubuntu integration), or any other GUI toolkit, for that matter.

---

### Post by saj0577 on 2008-05-27
Hpw would i go about accomplishing it then mate?

Saj

---

### Post by pointone on 2008-05-27
Well, it's relative. When I say "very simple", I mean simple in terms of creating a GUI with Python (since it only needs to display text). This is not simple if you know absolutely no Python or have no prior programming experience, however.

More information on exactly what you're trying to accomplish would be useful, though. If you're just trying to display data in a window where it cannot be edited, you could consider txt2html + Firefox.

```
sudo apt-get install txt2html
txt2html /path/to/some/text_file > output.html
firefox output.html
```

Otherwise, the simplest you could probably get with Python + GTK is using a [label widget]("http://www.pygtk.org/pygtk2tutorial/ch-MiscellaneousWidgets.html#sec-Labels").

---

### Post by Can+~ on 2008-05-28
> **saj0577 said:**
> Yeah thanks alot just without the add box of course. :)
Thank You.

Is that possible in python as well just as easily?


Saj

EasyGUI, GTK, TK (comes with python) are all good choices.

[http://ubuntuforums.org/showthread.php?t=772507](http://ubuntuforums.org/showthread.php?t=772507)

---

### Post by saj0577 on 2008-05-28
Well just a box that shows information that is not editable. It has to be displayable in its own window not in another application. As its for my own About on my distro.

Saj

---

### Post by saj0577 on 2008-05-28
Thanks il have a look i wil probably just edit the source for the ubuntu one if its not breakingany rules or anything.

Saj

---

### Post by saj0577 on 2008-05-28
> **pointone said:**
> The "About Ubuntu" program is ***yelp***, and you can browse/edit the source code yourself, if interested:

```
apt-get source yelp
```



This would be very simple to accomplish with Python + GTK (for Ubuntu integration), or any other GUI toolkit, for that matter.



Anyone know how to edit just the content easily?

Saj

---

### Post by pointone on 2008-05-28
yelp can load arbitrary manpage files and certain html/xml files if formatted properly (not sure what kind of formatting is required, though). Why not simply [create a man page]("http://www.unixreview.com/documents/s=8925/ur0312i/") and open it with "yelp /path/to/file"?

---

### Post by saj0577 on 2008-05-28
I like the layout of the ubuntu information and they way it works so want to edit it slightly and obviously change the content and that would be perfect.

Saj

---

### Post by dtmilano on 2008-05-28
Try this

> 
yelp file:///usr/share/gnome/help/about-ubuntu/C/about-ubuntu.xml


If you want to generate your own help file, the *easiest* alternative is using OpenOffice and saving as DocBook (i.e.: example.xml):

> 
yelp file:///tmp/example.xml


---

### Post by saj0577 on 2008-05-28
Thanks.

Saj

---

