---
title: "glade project options"
date: 2012-11-07
forum: Programming Talk
---

### Post by jgw on 2012-11-07
I am trying to get up to speed on glade 3.12.1 and am running through the tutorials.  There are mysteries here.  The one that is currently stumping me is the reference to project preferences/settings.  They say all one has to do to see this is simply open glade and it will magically appear.  I have tried opening Glade every which way but, everytime it opens it opens with an unsaved project and no project preferences dialog.  I have now read a couple of different manuals and they say the same thing but, still, this simply does not appear and there does not seem to be anyway to just access it.  

Does anybody know how to get to it?  Thanks................

---

### Post by r-senior on 2012-11-08
What are you expecting to see?

Presumably not what is displayed from File | Properties or you wouldn't be asking?

As a general rule, use tutorials to get the basic idea but expect to experiment a lot with Glade. I never found good up to date tutorials. Right-click a lot -- some features are only available by right-clicking.

And save your work often. ;)

---

### Post by jgw on 2012-11-08
Thanks for the reply.

What I am trying to get to are the options for a project.  I cannot figure out how to do that.  I have found lots of tutorials and am running through them but I have yet to see those options! I have no trouble with compiling, moving stuff around, packing and signals but would really like to see them pesky options <g>

Just about ready to start on Anjuta.....

---

### Post by pbrane on 2012-11-08
I think it's like rsenior said, tutorials are not up to date. A previous version on glade did have project options appear when run, however that was mainly to change between libglade and gtkbuilder. We don't do that any more; libglade is deprecated.

Anjuta is a nice IDE if you want to rapidly develope a Gnome GUI application.

---

### Post by jgw on 2012-11-09
One of the reasons for wanting to get to the options is the version of gtk+  My version of glade tells me that it is using gtk+- 3.? but the compiler is using 2.? which is giving me some confusions.  I deal with this by changing some stuff but things are not in sync.  I just keep plugging along with the tutorials.  Things do not turn out as advertised but I am assuming that I am drilling and sso what but it would be nice to be in sync.  As far as I can tell my problem is that the widgets I am using are simply not the same ones in the tutorials.  I just ignore it and carry on (not much choice <g>)

Thank you for the reply

---

### Post by pbrane on 2012-11-09
for Gtk-2.x use glade-gtk2, it's in the repos.
```

sudo apt-get install glade-gtk2

```

It's okay to keep glade 3.12.1 installed and glade-gtk2 has preferences in the edit menu.

---

### Post by jgw on 2012-11-09
Thanks again for the reply.

I am not sure what "glade-gtk2 has preferences in the edit menu." Means.  I have installed as you suggested and see no difference.  Do you mean that, now, gtk2 is the preferred gtk version that Glade recognizes?  I changed something in an existing project saved ut and took a look.  Here is what I got (I had to make <interface> to <glade-interface> to make conversion work):

<?xml version="1.0" encoding="UTF-8"?>
<glade-interface>
  <!-- interface-requires gtk+ 3.0 -->

I took a look at the edit menu and there was no reference or option and I still can't get to the project options.  I am, obviously, missing something?

---

### Post by pbrane on 2012-11-10
go to the **help** menu click on the **about** and make sure it is version 3.8.0. If so then go to the **edit** menu, there should be a **preferences** item you can click.

I have two glades installed. 3.12.1 and 3.8.0. 3.12.1 has an icon with a green triangle shape and 3.8.0 has an icon with a yellow icon shape.

---

### Post by jgw on 2012-11-10
I do have 3.12.1 and there is no preferences in the edit tab.  Perhaps I should remove and re-install? 

Incidentally, there are no icons in my edit menu for any of the options.  Oh, just to make sure we were talking about the right edit I also checked the widget editor and there are none there either.  As a matter of fact there are no icons in any of the menu stuff (file, edit, view, projects, help).  Perhaps I have it setup wrong?

(I tried to use screenshot to send you picture but it wouldn't let me keep the edit open)

---

### Post by pbrane on 2012-11-10
You need to be using glade 3.8.0 for GTK2. That's the glade-gtk2 I posted about earlier. Then you can access the preferences menu in glade-gtk2. There isn't a preferences menu item or other option in glade version 3.12.1.

---

### Post by jgw on 2012-11-10
I think what I had best do is to move onto anjuta and mess around in there.  What I am trying to do is to convert some dos code to gui and I shouldn't be worried about this stuff so much as getting on with what I need to do.  I keep fighting myself with stuff that, in the end, I suspect isn't going to make much difference and I would be better off just doing it all in anjuta from the getgo with what I have installed right now.  The dos stuff is pretty straight forward and REALLY simple (which makes sense since simple is what was available at the time)  so what I really should be doing is creating a basic menu and integrating it into my own code which is pure vanilla c. 

I also suspect I am going to have to move my dbase to sqlite which is yet another learning hurdle.  Interesting times............

I apologize for being such a pain - an artifact of old age I suspect <G>

Thanks again...........

---

### Post by pbrane on 2012-11-12
I think you'll like anjuta. I didn't think you were a pain... perhaps it's because I'm kinda old too.

---

### Post by jgw on 2012-11-12
Still, I appreciate your help.  I do have yet another question.  Will glade widgets, that need a string as input, accept a string variable?  If it does then does glade deal with the memory issue?  Just wondering......

The widget documentation, incidentally, is quite good!  Description, example, signals, the whole magilla <g>

---

### Post by pbrane on 2012-11-13
> **jgw said:**
> Still, I appreciate your help.  I do have yet another question.  Will glade widgets, that need a string as input, accept a string variable?  If it does then does glade deal with the memory issue?  Just wondering......

The widget documentation, incidentally, is quite good!  Description, example, signals, the whole magilla <g>

text widgets will accept a string (char array) as input in the 'C' verion of GTK. Gtkmm works with C++ strings and Glib::ustring. Any memory allocation that you do, you will need to clean up as well. When you assign a char array or string to a text or edit widget it will manage that copy.

---

### Post by jgw on 2012-11-13
thank you!  Instead of flying at glade I had the thought to first get sqlite up.  That will not work as it really is not setup to run under dos which my existing programs do.  I tested their program and got a bunch of errors which would easy to clean up but I think I would also lose functionality.  So, I think, I will have to start with glade, get rid of all the references to dbase (leaving remarks to tell me what I was doing (pretty straightforward, all I did was read and write).  then, after getting all that compiled forage ahead to the sqlite stuff.

---

### Post by Peter Ketel on 2012-11-14
> **pbrane said:**
> for Gtk-2.x use glade-gtk2, it's in the repos.
```

sudo apt-get install glade-gtk2

```It's okay to keep glade 3.12.1 installed and glade-gtk2 has preferences in the edit menu.

Is GLADE a working tool????? If I copy the sudo apt-get..the systems tells me that the newest version has already been installed.
This is tool with one can design an ugly and primitive GUI...There is no scaling of buttons or other stuf. Microsoft had a much better product 12 years ago.
Let's try to save it. OOPS...there are errors...controls are outdated.... This is what we call a CRAP product. This should not happen if the newest version is installed. 

So I am really flabbergasted that people have found a working GUI design tool
Please do tell how to obtain this tool...because GLADE 3.8 is CRAP.

---

### Post by jgw on 2012-11-14
If something is outdated, and you have the latest and greatest Glade then I am assuming that you also need the latest and greatest GTK+ which, incidentally you can also use.  Less automation but its not all that bad.

Just a thought.....

---

### Post by Peter Ketel on 2012-11-15
> **jgw said:**
> If something is outdated, and you have the latest and greatest Glade then I am assuming that you also need the latest and greatest GTK+ which, incidentally you can also use.  Less automation but its not all that bad.

Just a thought.....
The latest GTK+ libs are also installed...otherwise it would be unjust to make the remark that GLADE sucks.

For example: There is no way you can move buttons around, scale them or whatsoever.   There is no way to control any widget on how it is presented. Microsoft tends to frustrate programmers with awkward behaviour. Glade tends to drive programmers to insanity. Sorry, that I can't find anything positive about Glade or any other GUI design tool for Linux (that also includes QT that beats Glade by a mile in being a terrible GUI designer). Apple offers better tools. So is Apple the platform of the future?
  
P.S. By the way: In the preference menu 2.8 is actually 1.8. This solves the issues of the outdated widgets and classifies the ones that are actually obsolete correctly.

---

### Post by pbrane on 2012-11-15
> **Peter Ketel said:**
> The latest GTK+ libs are also installed...otherwise it would be unjust to make the remark that GLADE sucks.

For example: There is no way you can move buttons around, scale them or whatsoever.   There is no way to control any widget on how it is presented. Microsoft tends to frustrate programmers with awkward behaviour. Glade tends to drive programmers to insanity. Sorry, that I can't find anything positive about Glade or any other GUI design tool for Linux (that also includes QT that beats Glade by a mile in being a terrible GUI designer). Apple offers better tools. So is Apple the platform of the future?
  
P.S. By the way: In the preference menu 2.8 is actually 1.8. This solves the issues of the outdated widgets and classifies the ones that are actually obsolete correctly.

I would suggest you find a tutorial on glade and Gtk programming. I have no problems placing or sizing buttons or any other widget for that matter.

Gtk/Glade and windows resource editors are completely different systems.

---

