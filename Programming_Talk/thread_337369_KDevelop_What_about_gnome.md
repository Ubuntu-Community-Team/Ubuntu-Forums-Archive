---
title: "KDevelop? What about gnome?"
date: 2007-01-12
forum: Programming Talk
---

### Post by rekahsoft on 2007-01-12
Hi all, is there a app like KDevelop for gnome? I was looking at Kdevelop liked the look of it but don't really want to use KDE software in Gnome. Is there a gnome alternative that matches KDevelop?

---

### Post by Grey on 2007-01-12
I've used Anjuta.  It's a pretty nice program, but can be a bit of pain to properly install all dependencies.

I've also heard good things about Code::Blocks.

---

### Post by deadlydeathcone on 2007-01-12
Just a note on Anjuta: use the 1.24 version! The 2.02 version that shipped with edgy is horribly, horribly broken.

Other than Anjuta I recommend Wing for python (it's commercial, but they're nice people and will let you use it for free if you are an OSS developer) and Geany for anything else.

---

### Post by studiesrule on 2007-01-13
> **deadlydeathcone said:**
> Just a note on Anjuta: use the 1.24 version! The 2.02 version that shipped with edgy is horribly, horribly broken.

Other than Anjuta I recommend Wing for python (it's commercial, but they're nice people and will let you use it for free if you are an OSS developer) and Geany for anything else.

I thought Anjuta breaking was just me. I just can't get it to work. I even tried to compile my own version...

Code:Blocks is an extremely good IDE for C/C++. But it's quite specific towards the two. You should definately give it a try (use the nightly builds).

---

### Post by tc101 on 2007-02-04
I am confused about the original post that suggests there is a problem using KDE Software with Gnome.  I thought Gnome was the standard desktop that runs with Ubuntu.  Am I confused about this?  Why should there be any problem running and of the available Linux software with Gnome?

---

### Post by rekahsoft on 2007-02-04
> **tc101 said:**
> I am confused about the original post that suggests there is a problem using KDE Software with Gnome.  I thought Gnome was the standard desktop that runs with Ubuntu.  Am I confused about this?  Why should there be any problem running and of the available Linux software with Gnome?

There is no problem at all. Any KDE app fits nicely into gnome, i am just a little bit picky and want  a gnome app. It is just personal preferance. Really, it is just that i want it to look like gnome, not KDE and integrate better with other gnome apps instead of with KDE apps ;)

---

### Post by tc101 on 2007-02-04
On the subject of KDevelop, I have installed KDevelop and would like to try using it for Ruby. When I open help I get a message "Could not launch the KDE help center, Could not find service khelpcenter". How do I fix that?

---

### Post by maxamillion on 2007-02-04
Geany ..... [http://geany.uvena.de/](http://geany.uvena.de/) ... if its an IDE you want, this is the one I like...

its in the repos too (universe)
```
sudo aptitude install geany
```

gvim for quick hacking, but Geany has all the features of an IDE I could ever want and I recommend it to others who don't want to bother with kde-libs for KDevelop

---

### Post by lnostdal on 2007-02-04
> **rekahsoft said:**
> Hi all, is there a app like KDevelop for gnome? I was looking at Kdevelop liked the look of it but don't really want to use KDE software in Gnome. Is there a gnome alternative that matches KDevelop?

* glade for GUI-design (use libglade and load your .glade file @ runtime)
* emacs or your favorite editor for coding
* `scons -u' called from the editor above via a shortcut key for building (most editors parse the output of GCC and allows you to jump directly to locations of errors)
* gdb and ddd for debugging
* valgrind for further debugging

..is all the IDE you'll ever need.

I do not understand why people keep insisting on having programs that have everything "inside them". It doesn't make sense, and I've actually found these programs to be of inferior quality in some way or another than using many small programs that each are good at their specialized task. 

[http://en.wikipedia.org/wiki/Unix_philosophy](http://en.wikipedia.org/wiki/Unix_philosophy) ??

Create multiple desktops (navigate using ctrl-alt arrow-keys and/or add shortcut keys to jump to desktop *N*) and put each type of program(s) that does specific task on each desktop. One desktop for graphics work, one for GUI-design and one for coding and debugging. It's so simple.

---

### Post by Paul Gibbons on 2008-02-07
Eclipse with CDT is great with built in GUI to gdb. You can use autotools by expressing the build command as make.

---

### Post by RIchard James13 on 2008-02-07
> **tc101 said:**
> When I open help I get a message "Could not launch the KDE help center, Could not find service khelpcenter". How do I fix that?

You probably need to install the help subsystem as well as Kdevelop's help files.

kdehelp and kdevelop-doc

When I installed Kdevelop I installed all of KDE first, which would install the kdehelp package, but that doesn't install files like kdevelop-doc.

I also had other problems with Kdevelop and it's inbuilt help for program documents but I can't remember how I fixed it.

---

### Post by johnnyb1726 on 2008-02-07
> **lnostdal said:**
> * glade for GUI-design (use libglade and load your .glade file @ runtime)
* emacs or your favorite editor for coding
* `scons -u' called from the editor above via a shortcut key for building (most editors parse the output of GCC and allows you to jump directly to locations of errors)
* gdb and ddd for debugging
* valgrind for further debugging

..is all the IDE you'll ever need.

I do not understand why people keep insisting on having programs that have everything "inside them". It doesn't make sense, and I've actually found these programs to be of inferior quality in some way or another than using many small programs that each are good at their specialized task. 

[http://en.wikipedia.org/wiki/Unix_philosophy](http://en.wikipedia.org/wiki/Unix_philosophy) ??

Create multiple desktops (navigate using ctrl-alt arrow-keys and/or add shortcut keys to jump to desktop *N*) and put each type of program(s) that does specific task on each desktop. One desktop for graphics work, one for GUI-design and one for coding and debugging. It's so simple.

I agree.  Sometimes keeping it simple is the best idea.

---

### Post by mohbana on 2008-02-07
kde sports some excellent programs that i can't find good replacements for;

1.amarok
2. kile

its a shame that gnome doesn't have alternatives on the same level.

---

### Post by mcmonkeys1 on 2008-12-19
OK. the original question was is there an equivalent to kdevelop.
well?
i am *not* a noob at programming at all, but a noob at linux programming and use kubuntu, and just wrote my first prog in kdevelop as an ide. And assume it has kde specific features that i *will* want. SO! the question remains is there a gnome ( fags:-) ) equivalent to kdevelop? coz it seems ubuntu lads are more in the norm, AND i'm going to africa next summer to teach linux programming on a voluntary program, and don't wanna mess them up by changing tools , etc.....

wat think u???

inb4 vim/emacs/gay-editor...

cheers mates!

---

### Post by slavik on 2008-12-19
Answer has been given and there was no need to bring this thread up again.
Hint: Gnome

---

