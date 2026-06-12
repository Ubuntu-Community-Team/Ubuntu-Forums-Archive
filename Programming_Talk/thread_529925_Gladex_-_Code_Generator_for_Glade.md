---
title: "Gladex - Code Generator for Glade"
date: 2007-08-19
forum: Programming Talk
---

### Post by charlie763 on 2007-08-19
Hey, gang! My brother and I have been working on a handy little application called Gladex and I'd like to introduce it to everyone.

Gladex will take a .glade file written in the [Glade User Interface Builder]("http://glade.gnome.org/") and produce code in Python or other supported language that uses libglade to draw a GUI.

The current stable version 0.2 supports only Python output. The 0.3.2 development version supports Python and Perl output. When the 0.3 development series is released at 0.4 stable in September it will additionally support Ruby.

Gladex was conceived from several inadequacies found in other scripts that seek to perform similar functionality. Many scripts were unmaintained, confusing to use, or did not do what we needed them to do. The 0.3 development series is unique among similar applications in that it has a plugin architecture that allows anyone to create a plugin for a language. This plugin archetecture is necessary for us to achieve our goal of consolidating the functionality of and eventually depreciating similar applications such as [glc (Python)]("http://glc.sourceforge.net/"), [tepache (Python)]("http://www.gnomefiles.org/app.php/tepache"), [PyGCG (Python)]("https://launchpad.net/pygcg/"), [eglade (Eiffel)]("http://efsa.sourceforge.net/archive/elphick/eglade.htm"), [Glade# (C#)]("http://eric.extremeboredom.net/2005/06/08/203"), and [ruby-glade-create-template (Ruby)]("http://ruby-gnome2.sourceforge.jp/hiki.cgi?ruby-glade-create-template")

I would really appreciate any feedback at all. Specific comments would be great since that might help us decide what should be changed and what should remain as the application develops. Also, questions would be very helpful because answering them will help us write documentation. And if anyone is interested, we would love for others to write plugins for languages they are familiar with.

Here are all the links you might need:
**Project main page:** [http://www.openphysics.org/~gladex/](http://www.openphysics.org/~gladex/)
**About wiki:** [https://help.ubuntu.com/community/Gladex](https://help.ubuntu.com/community/Gladex)
**Screenshots:** [https://help.ubuntu.com/community/Gladex#head-7e96fd09c298bd55b4263eae62e46d8350c2a96e](https://help.ubuntu.com/community/Gladex#head-7e96fd09c298bd55b4263eae62e46d8350c2a96e)
**Howto:** [https://help.ubuntu.com/community/GladexHowto](https://help.ubuntu.com/community/GladexHowto)
**Download:** [https://launchpad.net/gladex/+download](https://launchpad.net/gladex/+download)
**Launchpad:** [https://launchpad.net/gladex](https://launchpad.net/gladex)

---

### Post by matthew on 2007-08-19
Wow. This looks really good. I'll be following your development with interest!

---

### Post by Nekiruhs on 2007-08-19
XD! I just wrote a quick script to iterate through the glade XML file, use regexes to get out the names of the widgets, and print the corresponding gtk.glade.get_widget() lines for each of them to sdout. Oh well, great minds think alike!

---

### Post by cmat on 2007-08-19
Just what I needed. Keep up the fantastic work!

---

### Post by paxmanchris on 2007-08-19
> **Nekiruhs said:**
> XD! I just wrote a quick script to iterate through the glade XML file, use regexes to get out the names of the widgets, and print the corresponding gtk.glade.get_widget() lines for each of them to sdout. Oh well, great minds think alike!

I too am a Gladex developer. Nekiruhs, would you mind attaching you code in a post and letting us use it in Gladex 0.6? I have made a blueprint for something similar on Launchpad ([https://blueprints.launchpad.net/gladex/+spec/map-code-to-gtk-widgets](https://blueprints.launchpad.net/gladex/+spec/map-code-to-gtk-widgets)) and I think your code might help us achieve that goal. We want to give users the option of producing hard code as an alternative to using the libglade bindings. So, any help from your way would be greatly appreciated.

---

### Post by Nekiruhs on 2007-08-19
> **paxmanchris said:**
> I too am a Gladex developer. Nekiruhs, would you mind attaching you code in a post and letting us use it in Gladex 0.6? I have made a blueprint for something similar on Launchpad ([https://blueprints.launchpad.net/gladex/+spec/map-code-to-gtk-widgets](https://blueprints.launchpad.net/gladex/+spec/map-code-to-gtk-widgets)) and I think your code might help us achieve that goal. We want to give users the option of producing hard code as an alternative to using the libglade bindings. So, any help from your way would be greatly appreciated.
No problem at all. It should only take a few minor changes because I statically pointed to the glade file, but it would take like 2 lines of code to make it accept an argument and use that.

Sorry for using regexes, I don't quite grasp how elementTree works.

---

### Post by charlie763 on 2007-08-19
> **cmat said:**
> Just what I needed. Keep up the fantastic work!

I'm glade to hear it, cmat. If you use Gladex and find bugs, have ideas for features, or have questions, you can [file a bug report]("https://bugs.launchpad.net/gladex/"), [register a blueprint]("https://blueprints.launchpad.net/gladex/"), or [ask a qestion]("https://answers.launchpad.net/gladex/") on [Launchpad]("https://launchpad.net/").

---

### Post by charlie763 on 2007-08-20
Just to let you all know; as of three minutes ago Gladex in bzr now supports Ruby. The Ruby plugin does not check for a file's existence before overwriting it, so be careful. Cheers!

---

### Post by spyheart on 2007-08-20
Hey Charlie

This is one of the best thing i have ever seen.:)

Pavan

---

### Post by charlie763 on 2007-08-20
We just released 0.3.3 ([https://launchpad.net/gladex/0.3/0.3.3/+download/gladex-0.3.3.tar.gz](https://launchpad.net/gladex/0.3/0.3.3/+download/gladex-0.3.3.tar.gz)). Gladex 0.3.3 supports Ruby, Perl, and Python.

Any ideas on where we should go from here?

---

### Post by AlexThomson_NZ on 2007-08-20
> **charlie763 said:**
> We just released 0.3.3 ([https://launchpad.net/gladex/0.3/0.3.3/+download/gladex-0.3.3.tar.gz](https://launchpad.net/gladex/0.3/0.3.3/+download/gladex-0.3.3.tar.gz)). Gladex 0.3.3 supports Ruby, Perl, and Python.

Any ideas on where we should go from here?

C/C++?

// Not that I would use it- prefer using libglade myself

---

### Post by charlie763 on 2007-08-20
> **AlexThomson_NZ said:**
> C/C++?

// Not that I would use it- prefer using libglade myself

The code that Gladex outputs uses libglade. We plan on eventually having more plugins; ones that output raw code that does not use libglade.

Gladex 0.2, but maybe not the current development version, will help manage your code. Here are the steps for using Gladex 0.2:
[LIST=1]
[*]Use Glade to design a GUI and create a .glade file
[*]Use Glade to define callback functions in your .glade file
[*]Use Gladex 0.2 to generate code to some location
[*]Observe that all your defined callback functions appear in the callbacks file
[*]Edit a few of the callback functions in the callbacks file
[*]Use Glade to define one or more new callbacks in the .glade file
[*]Use Gladex 0.2 to generate the code again (to the same location)
[*]Observe that the newly defined callbacks are appended to the original callbacks file leaving your original edits untouched
[/LIST]

---

### Post by AlexThomson_NZ on 2007-08-20
Thanks for clarifying,

I assumed this was a re-implementation of the old code generation that was taken out of Glade 3.x

---

### Post by davim on 2008-04-24
gladex is verry cool and usefull do you have ppa repositories??

---

### Post by charlie763 on 2008-04-24
> **davim said:**
> gladex is verry cool and usefull do you have ppa repositories??

Sure do. From [https://launchpad.net/~gladex/+archive](https://launchpad.net/~gladex/+archive)

deb [http://ppa.launchpad.net/gladex/ubuntu](http://ppa.launchpad.net/gladex/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/gladex/ubuntu](http://ppa.launchpad.net/gladex/ubuntu) hardy main

Development has been slow for the past few months due to the two main developers being in school. Things should pick up in the Summer.

A good place to ask questions about Gladex is the Answers page on Launchpas [https://answers.launchpad.net/gladex/](https://answers.launchpad.net/gladex/)

---

### Post by Ziggy72 on 2008-05-03
Thank you. This looks very promising. Is there a deb for 64-bit? If not, how do install the tar.gz distribution in Hardy? Thanks.

---

### Post by charlie763 on 2008-05-04
> **Ziggy72 said:**
> Thank you. This looks very promising. Is there a deb for 64-bit? If not, how do install the tar.gz distribution in Hardy? Thanks.

I don't have a 64-bit machine to test this on, so I can only give you the steps I take on a 32-bit machine. However, I'm pretty it should work without any problems.

You will first need to install epm to build a package for yourself.
```
sudo apt-get install epm
```
Download the code
```
wget http://edge.launchpad.net/gladex/0.4/0.4.1/+download/gladex-0.4.1.tar.gz
```
Extract the files
```
tar -zxvf gladex-0.4.1.tar.gz
```
Navigate into the directory containing the downloaded files
```
cd gladex-0.4.1
```
Then build the package
```
make deb
```
Now install the package
```
make install
```

To do it all in one shot use
```
sudo apt-get install epm
wget http://edge.launchpad.net/gladex/0.4/0.4.1/+download/gladex-0.4.1.tar.gz
tar -zxvf gladex-0.4.1.tar.gz
cd gladex-0.4.1
make deb
make install


```

To remove Gladex enter the following at the command line
```
sudo apt-get remove gladex
```

Gladex isn't showing up in my menu, so you may have to start it from the command line
```
gladex
```
I think it's a bug that is fixed in the bzr repository.

If you have any other questions, try to use the [Answers]("https://answers.launchpad.net/gladex/") sections on the [Gladex Launchpad page]("https://launchpad.net/gladex/"). You can also [file bug reports]("https://bugs.launchpad.net/gladex/") there.

---

### Post by charlie763 on 2008-05-04
I'd just like to let everyone know that development of Gladex has been slow for the past few months while my brother and I are finishing up undergrad at NJIT and grad school at Rutgers respectively. Things should pick up in about a month and there should be significant release in July or August. [Bug reports]("https://bugs.launchpad.net/gladex/") are always welcome.

---

### Post by Ziggy72 on 2008-05-07
> Originally posted by ziggy72:
Thank you. This looks very promising. Is there a deb for 64-bit? If not, how do install the tar.gz distribution in Hardy? Thanks.

Thank you for your prompt and detailed response - much appreciated.

I've been playing (very, very superficially) with Gladex, but I think I've immediately identified a problem which, if not solved, would prevent me from ever using the program.

The problem I've seemed to identify is with debugging. I use Komodo Professional v4 for program development and it seems that because the Gladex py code is divided into 2 separate sections (startup and callback), if I put a break point somewhere within the callback code Komodo doesn't seem to be able to stop execution as expected.

The debugging experiments I tried were with your calculator example. Maybe I'm doing something wrong and, if so, I apologise.

Currently I use Glade3 to generate a glade file and tepache to generate the initial py code.

Comments appreciated.

---

