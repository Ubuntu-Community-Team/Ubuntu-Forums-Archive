---
title: "Creating Graphical Setup Tools With Python?"
date: 2011-05-30
forum: Programming Talk
---

### Post by tdrusk on 2011-05-30
Hi guys, I am working with Project Lipsync for my senior project. One of my duties is to create a graphical setup tool for the program, so the user doesn't have to use the commandline. Is there something already out there for this or I am going to have to write the setup from scratch? The tool is for Linux initially, but I want it to be as cross-platform as possible.
Gracias

---

### Post by juancarlospaco on 2011-05-30
a .DEB file (?)

---

### Post by tdrusk on 2011-05-31
> **juancarlospaco said:**
> a .DEB file (?)

Well see, it kind of sets up like Dropbox, where it asks where you want to sync from, sync to, etc.

---

### Post by juancarlospaco on 2011-05-31
I have done a *"next, next, next, next, next..."* thingy on Python, 
i think that is possible on other languages too...    &#664;&#8255;&#664;

[IMG]http://python.org.ar/pyar/TKWizards?action=AttachFile&do=get&target=temp.jpg[/IMG]

---

### Post by DangerOnTheRanger on 2011-05-31
I think he was looking for a more specific response than that.

Personally, I'd go with InstallJammer ([http://installjammer.com]("http://installjammer.com/")) - an open-source installer generator. It can't make .debs or .rpms, but it can make a generic, standalone, graphical Linux installer. It can even generate *Windows installers* on Linux! It can't currently generate OSX installers, though.

It's what I use for my cross-platform game development kit, which I can only develop on Linux, but it must reach users on Windows and Mac OSX. So, it sounds like what you'd want.

---

