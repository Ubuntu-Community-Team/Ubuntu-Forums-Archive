---
title: "Theme buttons/scrollbars/panel stuck"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by jcdaggett on 2008-10-26
Ok first of all, I just signed up here and this is my first post. I'm glad to be part of the community and look foreword to learning Ubuntu.

Right now, I'm pretty much a noob with Linux/Ubuntu so bear with me...

I have been playing around with different themes and stuff and have gotten stuck. When I download a new theme and install, the window borders change, but that is it. The panel, buttons, scrollbars and colors seem to be stuck on an OSX type theme. I can't remember exactly what it's called. I've tried [**this theme**]("http://gnome-look.org/content/show.php/Dust+Blue+Metacity?content=91808") to give you an example
When I click "customize" in Apperence Prefences and click the "controls" tab, all control themes seem to be stuck on the OSX-type theme. Hopefully the screen shot will give you an idea of what I'm talking about.
[IMG]http://i318.photobucket.com/albums/mm407/jcdaggett/Screenshot-CustomizeTheme.png[/IMG]

Bottom line: Why can't I change the scrollbars/buttons? and Is there a way to just download one theme file that will change everything at once (window borders, buttons, scrollbars, panels)?

Thanks for any help.

---

### Post by SunnyRabbiera on 2008-10-26
and its stuck that way when you hit another one of the themes?
strange
Did you install your OSX like theme globally?

---

### Post by jcdaggett on 2008-10-26
I don't remember exactly how I installed the theme, this was a couple months ago when I installed a fresh Ubuntu OS. Obviously I did something wrong.

It's really weird it's like the OSX-like theme just overwrote all the other ones that were installed. When I click on different ones nothing changes, it just sticks to the OSX theme. When I download new [**application themes**]("http://art.gnome.org/themes/gtk2/") some work and some don't.

sooo....:confused:

---

### Post by SunnyRabbiera on 2008-10-26
did you install KDE by any chance?

---

### Post by jcdaggett on 2008-10-26
I'm not sure what KDE is, like I said I'm a noob in the Linux world.

I'm going to say no because I would probably know what it is if I installed it.

---

### Post by SunnyRabbiera on 2008-10-26
> **jcdaggett said:**
> I'm not sure what KDE is, like I said I'm a noob in the Linux world.

I'm going to say no because I would probably know what it is if I installed it.

alright double checking.
But your issue is most strange, it seems your OSX themwe has overidden the other themes.
Thats why I dont go for the OSX look in linux

---

### Post by blackened on 2008-10-26
You may have accidentally uninstalled some gtk engines, but usually when a theme uses an unrecognized engine it kicks back to the old crappy gtk1 default.

Still, check Synaptic and make sure you have the appropriate gtk-engine package(s) installed.

Just for informational purposes, go through /usr/share/themes and make sure the actual file contents of each individual theme are different. If you installed them in your home directory, then check the file contents in /home/*yourusername*/.themes.
The gtkrc file for each theme should be similar, but with notable differences.

---

### Post by antmenj on 2008-10-26
> **jcdaggett said:**
> I'm not sure what KDE is, like I said I'm a noob in the Linux world.

I'm going to say no because I would probably know what it is if I installed it.

KDE is a type of desktop.  Hang in there.  You have to google about every second word when your new.  I remember:lolflag:

If you installed any programs starting with K chances are KDE was installed as a required item to make them go.

---

### Post by blackened on 2008-10-26
I guess I totally missed the whole new user thing. Try this in the terminal first:

```
sudo apt-get install gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf
```

Then go back to the Control settings and see if anything changed.

---

