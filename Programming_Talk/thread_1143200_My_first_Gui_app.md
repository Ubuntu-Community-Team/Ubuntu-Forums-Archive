---
title: "My first Gui app"
date: 2009-04-29
forum: Programming Talk
---

### Post by wsonar on 2009-04-29
I will obviously elaborate more on this but I was over half way through teaching myself c++ when I decided I wanted to make a little gui app and I knew python was the easiest approach I got myself a python book but haven't evn had time to get started on it 

my cheeses I call it vconky-conf.py
 (is it legal  to  use a name in a name for a tool such as this?)

basicly a gui with three buttons one open's the .conkyrc file from the home dir another button is ther to kill conky and another to start it I I could have killed it and started it from a single button but sometimes you may not want to do that so I made them separate buttons

to the seasoned developer it's pretty lame I'm sure but for my first gui I think it's kinda neat

check it out, look at the code, leme know if this is the best approach.

Thanks

---

### Post by scourge on 2009-04-29
> **wsonar said:**
> 
my cheeses I call it vconky-conf.py
 (is it legal  to  use a name in a name for a tool such as this?)


It's highly unlikely that anyone has trademarked the same name for a similar tool, so you're safe.

> check it out, look at the code, leme know if this is the best approach.

As you said yourself, it's basically just a grid of three buttons. There's not much to critique there, except for the excessively large screenshot which shows your whole desktop instead of just your application.

---

### Post by wsonar on 2009-04-29
> **scourge said:**
>  except for the excessively large screenshot which shows your whole desktop instead of just your application.

LOL thanks..

 I'll adjust the screen shot and I'm looking to add some more functionality aswell

---

### Post by wsonar on 2009-04-29
I may update a zip with an how to use but for now it requires

python-tk

so the easiest way to use this script is to download into a folder I have one called appscripts

open a terminal and do a chmod +x vconky-conf.py

then do

sudo apt-get install python-tk 

to satisfy Tkinter

after that I just make and icon on my desktop or panel
by right clicking and choosing create launcher
after browsing to the file and selecting it giving it a name and description,
I'm all set works pretty well for what it is.

------------------------------------------------------------------------------------
so if there are still any vets viewing this thread should I be using wxWidgets instead of Tkinter?

what would make it easier for a user to use without having to install extra stuff?
------------------------------------------------------------------------------------

---

### Post by jimi_hendrix on 2009-04-29
i like your gtk theme

---

### Post by days_of_ruin on 2009-04-29
> **jimi_hendrix said:**
> i like your gtk theme

I like his metacity theme. His gtk theme looks like unthemed gtk.

---

### Post by jimi_hendrix on 2009-04-29
> **days_of_ruin said:**
> I like his metacity theme. His gtk theme looks like unthemed gtk.

thats what i meant, thank you

(i normally just get full theme packs, so i dont worry about specifics there)

---

### Post by wsonar on 2009-04-29
> **jimi_hendrix said:**
> i like your gtk theme

Thanks...yea it is metacity theme.

that was on my work comp so not sure but think it was this one

[http://www.gnome-look.org/content/show.php/VistaUltimate?content=79665]("http://www.gnome-look.org/content/show.php/VistaUltimate?content=79665")

---

