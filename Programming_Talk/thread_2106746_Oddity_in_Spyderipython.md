---
title: "Oddity in Spyder/ipython"
date: 2013-01-19
forum: Programming Talk
---

### Post by memilanuk on 2013-01-19
So... started tinkering with ipython inside spyder.  I like using this particular setup as it has most of what I want/need, and is pretty much the same from Windows to Linux so I get the same features both places.

One issue that I've ran into thus far is that plotting from an ipython console window in spyder doesn't seem to work quite as advertised.

If I start ipython in a regular console window (outside spyder), with 'ipython --pylab' and enter the following:

x = randn(10000)
hist(x, 100)

...it pops up a plot window, like it should.  Same thing if I start ipython just plain, no command-line options, and enter '%pylab' from the interactive prompt.

But in the ipython window inside spyder (running on Ubuntu 12.10)... even after entering '%pylab'... if I run the commands listed above, I get no plot.  Running 'plot()' or 'show()' doesn't help.  But running the commands as:

x = randn(10000)
plot(hist(x, 100))

...brings up the plot window as per normal.

Someone else on the spyder mailing list had the same problem, both of us running Ubuntu.  Other people don't seem to have this issue, which starts to make it sound like it may be an Ubuntu/Debian thing.

Any ideas?

TIA,

Monte

---

### Post by DMJ on 2013-03-05
> **memilanuk said:**
> So... started tinkering with ipython inside spyder.  I like using this particular setup as it has most of what I want/need, and is pretty much the same from Windows to Linux so I get the same features both places.

One issue that I've ran into thus far is that plotting from an ipython console window in spyder doesn't seem to work quite as advertised.

If I start ipython in a regular console window (outside spyder), with 'ipython --pylab' and enter the following:

x = randn(10000)
hist(x, 100)

...it pops up a plot window, like it should.  Same thing if I start ipython just plain, no command-line options, and enter '%pylab' from the interactive prompt.

But in the ipython window inside spyder (running on Ubuntu 12.10)... even after entering '%pylab'... if I run the commands listed above, I get no plot.  Running 'plot()' or 'show()' doesn't help.  But running the commands as:

x = randn(10000)
plot(hist(x, 100))

...brings up the plot window as per normal.

Someone else on the spyder mailing list had the same problem, both of us running Ubuntu.  Other people don't seem to have this issue, which starts to make it sound like it may be an Ubuntu/Debian thing.

Any ideas?

TIA,

Monte


I'm on Fedora 17, and having the same issue. But plotting from IPython doesn't work for me at all. A simple plot(x,y) doesn't work. I've tried opening a figure first. I've tried running show(). Nothing. It works fine from the Python interpreter.

I'm editing this reply. I started looking through the preferences, and noticed that the pylab backend is set to do inline plots. Changing this to --pylab=qt and restarting fixed the problem. It also gave me the default magic functions and shortcut keys back. Not sure why that would be. This only works by launching an ipython kernel, though, not just "ipython interpreter."

I figured this out by connecting an ipython qtconsole session to the kernel running in Spyder, and noticed I could only do inline plots. Apparently inline plots don't work in Spyder. I strange choice for the default setting. 

I'm still not quite sold on Spyder. Using PyDev with ipython qtconsole is more versatile. But it looks promising, and a more integrated solution is welcome. They need to change the default setting though, or they're going to scare away a lot of new users.

---

### Post by memilanuk on 2013-03-05
FWIW... I did get some help from the spyder list eventually.  Seems its a bit of a combination of the usual bugs plus trying to hit a moving target with ipython development moving along briskly.  

I've been running 2.2.0 beta 2 and 3 of spyder and it works *much* better - and integrates with ipython better as well.

I never tried ipython with PyDev... are you running it from inside ipython, or as a separate qt console?

---

### Post by DMJ on 2013-03-06
> **memilanuk said:**
> FWIW... I did get some help from the spyder list eventually.  Seems its a bit of a combination of the usual bugs plus trying to hit a moving target with ipython development moving along briskly.  

I've been running 2.2.0 beta 2 and 3 of spyder and it works *much* better - and integrates with ipython better as well.

I never tried ipython with PyDev... are you running it from inside ipython, or as a separate qt console?

I use PyDev inside Eclipse as a code editor, and IPython separately to run the code and do interactive work. PyDev is great, but it's nice to have a more integrated solution for scientific work. Spyder seems pretty good for trying out simple scripts and calculations, but for large coding projects, PyDev is far superior. I don't know if it's possible to use IPython inside PyDev.

---

### Post by memilanuk on 2013-03-06
In general I'd agree PyDev is a more full-meal-deal IDE... but I'm at that point where I depend heavily on pep8 and pylint to help keep me on the straight and narrow - its astounding how much less *problems* I have when vetting code w/ pylint - and when last I used pydev in late fall, it was having some issues w/ pylint.  Specifically:  [http://stackoverflow.com/questions/12825900/pylint-doesnt-show-anything-on-eclipse](http://stackoverflow.com/questions/12825900/pylint-doesnt-show-anything-on-eclipse) - and it didn't seem to be getting much if any attention from the developer.

So far spyder still has some small bugs as far as the document links in its help menus, but for the most part does what I want, at least in the beta 3 version.  I haven't tried running it from a portable installation alongside PortableApps and Portable Python which circumstances dictate I use fairly regularly when away from the house and my personal computer... but I don't see why it *wouldn't*.  I know Eclipse/PyDev did, but sometimes managing the 'projects' seemed like a massive PITA/over-kill for my level of use.

YMMV,

Monte

---

### Post by DMJ on 2013-03-08
> **memilanuk said:**
> In general I'd agree PyDev is a more full-meal-deal IDE... but I'm at that point where I depend heavily on pep8 and pylint to help keep me on the straight and narrow - its astounding how much less *problems* I have when vetting code w/ pylint - and when last I used pydev in late fall, it was having some issues w/ pylint.  Specifically:  [http://stackoverflow.com/questions/12825900/pylint-doesnt-show-anything-on-eclipse](http://stackoverflow.com/questions/12825900/pylint-doesnt-show-anything-on-eclipse) - and it didn't seem to be getting much if any attention from the developer.

So far spyder still has some small bugs as far as the document links in its help menus, but for the most part does what I want, at least in the beta 3 version.  I haven't tried running it from a portable installation alongside PortableApps and Portable Python which circumstances dictate I use fairly regularly when away from the house and my personal computer... but I don't see why it *wouldn't*.  I know Eclipse/PyDev did, but sometimes managing the 'projects' seemed like a massive PITA/over-kill for my level of use.

YMMV,

Monte

I upgraded to 2.2 beta using pip, which required also upgrading matplotlib and ipython.  It's definitely a big improvement. IPython integration is much better, although debugging is still a little quirky. It works better if I connect to the kernel from an external console. It's definitely worth having the most recent versions of packages for scientific computing in Python. Unfortunately, no distributions are that up to date. Thank goodness for pip. 

I still prefer PyDev, though. The real-time error checking is much better, and I've done a lot of development in Eclipse, so I'm used to it. Spyder is nice for short scripts and interactive work though, and the code completion and documentation pop ups are better. I really like the object inspector. 

The editor's a bit glitchy, though. Do you know what it's based on? Probably Kate or Kwrite. If I use "from package import *" then it will give me a warning, and mask all other code inspection. Do you know of a work-around for this? For projects, I always import explicitly. But for interactive work it's convenient to do "from pylab import *".

---

### Post by memilanuk on 2013-03-08
Interesting... after this got brought back up I decided to revisit Eclipse/PyDev again as I really do like it also and had kind of gotten used to its way of doing things.  Plus it does work on my laptop in Win7 and Ubuntu as well as from a portable install on a USB thumb drive @ work.  Couldn't quite get spyder 2.2.0b3 to fly from the thumb drive...

Seems like I was running into some of the same problems again with PyDev and pylint... some of the source files I open up from books, etc. aren't exactly pep8 compliant, and the sheer amount of warnings overwhelms any useful info I might otherwise get from the code analysis.  I finally just opted to turn off code analysis in PyDev and just run pylint, as it seems easier to control via comment tags to it.  Tried demos of pycharm and sublime too... eh.

The all-in-one aspect of spyder is nice for me, as I spend a lot of time tinkering and learning vs. trying to write code in the absolute fastest most efficient manner.  But I did stumble on one aspect of PyDev's 'code intelligence' that I hadn't known about and think is pretty sweet... if I type something like 'Label<Ctrl+Space>' it gives me a list of all the 'Label' related methods, even if I haven't imported anything yet.  Once I select 'Label - ttk' from the dropdown, pydev auto-populates the imports at the top of the file with 'import Tkinter' and 'from ttk import Label'.  Sweet!

---

