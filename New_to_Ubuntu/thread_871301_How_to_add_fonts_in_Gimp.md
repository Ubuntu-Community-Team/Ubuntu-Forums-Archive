---
title: "How to add fonts in Gimp"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by Nazty_Nayt on 2008-07-26
Hey this may seem like a stupid question, but can't figure it out, but can anyone tell me how I can add new fonts to gimp?

---

### Post by Pro-reason on 2008-07-26
> **Nazty_Nayt said:**
> Hey this may seem like a stupid question, but can't figure it out, but can anyone tell me how I can add new fonts to gimp?

I haven't had to do it myself, but this is what I would try:

[LIST]
[*]See if adding fonts systemwide makes them work in GIMP
[*]See if there's an option in the GIMP interface for adding fonts
[*]Dump some font files in *~/.gimp-2.4/fonts* and see if they show up
[/LIST]

---

### Post by raptor2552 on 2008-07-26
The easy way to do this is:
1, create a .fonts folder in your home directory
2. copy or put the font files (somefont.ttf) in the .fonts directory
3. enjoy your new fonts gimp, open office, system, whatever

Umm, remember the period in .fonts (dot)fonts

---

### Post by Nazty_Nayt on 2008-07-30
Hey Raptor, sorry it took me a while to get back with you.  Before I go any further, do I need to run Nautilus, cause when I open up my file browser, and go to my home directory create a folder is disabled.  Also, just wondering if it will appear in my browser after I create it, cause I believe I'm supposed to have a .local folder as well in there but it isn't visible.  Thanks, again sorry it took me so long to respond.

---

### Post by raptor2552 on 2008-07-30
> when I open up my file browser, and go to my home directory create a folder is disabled

What?! Are you sure you're in your home directory and running nautilus as you? You may want to open a new post for that. I don't know. Maybe try opening a terminal and type: nautilus

If you want to see "hidden" files (those with a dot in front of them) in Nautilus press "Control H". 

If you're up to using the command line open a terminal
make sure your in your home directory: cd ~
type: mkdir .fonts
type: ls -al
your .fonts folder should look similar:  drwxr-xr-x  2 urname urgroup  4096 2008-07-30 19:55 .fonts
finally copy the font files to it, eg, cp /from/where/ever/fontfile.ttf ~/.fonts

You'll have to restart any applications that you want to use your fonts in.

If nautilus worked you could just right click and create a new folder then drag and drop.

---

### Post by Nazty_Nayt on 2008-07-30
When I opened Nautilus, and pressed ctrl+H the only (.) file that opened, was .cairo-clock.

---

### Post by raptor2552 on 2008-07-30
What? Nautilus shouldn't open anything unless you double click on it. OK well forget Nautilus. That isn't the focus of this thread.

Where you able to create a .fonts folder and copy your font files to it?

Did you confirm ,fonts was created using ls -al

---

### Post by Nazty_Nayt on 2008-07-30
Yeah Raptor, that works and I'm good.  That's all I need, I doubt I'll need to do anything else with the other files.

---

### Post by unutbu on 2008-07-30
After you move the fonts to ~/.fonts, I think you might have to run the command

```
fc-cache -f -v
```
to make your system aware of the new fonts.

---

### Post by raptor2552 on 2008-07-30
Super

Now open a thread about your nautilus problem, I haven't a clue but it should be interesting.

---

### Post by kapi on 2013-01-25
> **raptor2552 said:**
> The easy way to do this is:
1, create a .fonts folder in your home directory
2. copy or put the font files (somefont.ttf) in the .fonts directory
3. enjoy your new fonts gimp, open office, system, whatever

Umm, remember the period in .fonts (dot)fonts

Works like a charm, Thanks. I made the mistake of installing fonts in the usr/share/fonts folder and gimp kept crashing.

Now it's okay, Thanks very much:D

---

### Post by ubudog on 2013-01-25
Old thread closed.

---

