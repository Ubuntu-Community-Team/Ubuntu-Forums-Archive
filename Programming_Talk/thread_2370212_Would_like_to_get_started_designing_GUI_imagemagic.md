---
title: "Would like to get started designing GUI imagemagick...no programming experience"
date: 2017-08-31
forum: Programming Talk
---

### Post by BKDW34 on 2017-08-31
Good Afternoon.

I have no programming experience, but I would like to design a polished interface built upon imagemagick to specifically do certain tasks (watermarking, converting pics to pdf, etc). 

Maybe this could be the start of something--like a design suite for Linux. I am astounded how many features imagemagick has.** It does things that Adobe charges money for. **

I am frustrated that linux has so many capabilities but has to be unlocked at the command line. I am not anti-terminal, but sometimes I just want to click a few menu tabs and be done with it. 

There is a program out there (converseen) that is built upon imagemagick--it does specific tasks (batch resizing, batch renaming, rotate and flip,and PDF to image). 

I want to make something like that, but prettier (no insult meant) and does batch watermarking and some pdf work.

I've used phatch, but it's development has stopped and I've had to tweak it over the last few years and it downloads all of these strange fonts....

I gather that designing the interface is one thing, and getting the mouse clicks to actually tell the program to do what you want is another. So maybe I need to take a class to figure this out?

I don't know where to start, but I am willing to learn.

---

### Post by TheFu on 2017-09-01
Learn python as your first step.  You'll want a general purpose language to begin.  After a few weeks with python, you can begin learning to use a GUI library linkage for python and Gnome or KDE.  These are GTK+ or Qt libraries and commonly used for cross-platform development.  Most of the programs you run on Ubuntu with a GUI use one of those.

Any be certain to have the appropriate amount of fun!

So ... you want to learn to program.... [http://blog.jdpfu.com/2011/10/19/how-to-learn-to-program](http://blog.jdpfu.com/2011/10/19/how-to-learn-to-program)

---

### Post by BKDW34 on 2017-09-01
I appreciate your answer.  So I will learn python. Are there any books you'd recommend? I am the type who likes to read first, then get to work. 

Once I learn python, then use a GUI library linkage.  Do these have names? These will allow me to tell imagemagick what to do?

Also, how do I make the program look pretty? I see these programs that make really nice looking UI (sketchapp, etc)....can I use them to design icons and menus?

Thanks.

---

### Post by TheFu on 2017-09-01
Did you click the link and read?

After you learn a little more, come back and read what I wrote above again. It says what you need to know, but you just don't have the vocabulary yet to understand.

---

### Post by dragonfly41 on 2017-09-02
Although python is a recommended development path I may confuse you now by suggesting that you also explore using RStudio (an IDE for R language).  The reason I suggest RStudio is that you might be able to create prototypes much quicker and with less frustration using RStudio.

Read here to see what can be done ..

[https://cran.r-project.org/web/packages/magick/vignettes/intro.html#cut_and_edit](https://cran.r-project.org/web/packages/magick/vignettes/intro.html#cut_and_edit)

You will need to install RStudio which conveniently is found in Ubuntu Software Centre.

You will find it easier to navigate Ubuntu repo if you install Synaptic Package Manager.

```
sudo apt-get update
sudo apt-get install synaptic
```

Then using Synaptic Package Manager install the libraries needed by RStudio.

```
[COLOR=inherit]sudo apt-get install libmagick++-dev[/COLOR]
```

Looking ahead, when you have some prototype applications ready you might post your app as a "shiny app" by creating a free account at [https://www.shinyapps.io/](https://www.shinyapps.io/).   This allows various controls to be used to change arguments for ImageMagick commands.

Here is a very basic shiny app.

[http://shiny.rstudio.com/gallery/image-output.html](http://shiny.rstudio.com/gallery/image-output.html)

A shiny app can then be embedded in a webpage.

But don't let this stop you learning python which you will need at some stage.
Both languages, python and R, have their distinct uses.

---

