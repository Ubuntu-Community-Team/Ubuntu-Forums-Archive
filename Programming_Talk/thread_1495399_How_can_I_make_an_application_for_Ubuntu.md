---
title: "How can I make an application for Ubuntu?"
date: 2010-05-28
forum: Programming Talk
---

### Post by iampriteshdesai on 2010-05-28
Well, I've been an Ubuntu user for a long time, but now I'd like to start making application for Ubuntu.
I know C, C++, bit of Python and Perl. Nothing advanced here.
I have no experience for creating Ubuntu or in general GTK apps.
Is there any nice resource for it?
Some tutorials and stuff like that?
I want to create a blog writer.
What software should I use?

---

### Post by amauk on 2010-05-28
I believe the preferred way to make desktop apps is using Quickly
(so, you'll be programming in Python)

[https://wiki.ubuntu.com/Quickly](https://wiki.ubuntu.com/Quickly)

I believe it's also recommended you have a launchpad account as well
so you can easily upload your project to launchpad (covered in the link above)

---

### Post by lisati on 2010-05-28
Moved to "Programming talk"

---

### Post by iampriteshdesai on 2010-05-28
> **amauk said:**
> I believe the preferred way to make desktop apps is using Quickly
(so, you'll be programming in Python)

[https://wiki.ubuntu.com/Quickly](https://wiki.ubuntu.com/Quickly)

I believe it's also recommended you have a launchpad account as well
so you can easily upload your project to launchpad (covered in the link above)
Quickly helps you to create GUIs quickly, doesn't it?
So why is Quickly a command line software?

---

### Post by amauk on 2010-05-28
> **iampriteshdesai said:**
> Quickly helps you to create GUIs quickly, doesn't it?
So why is Quickly a command line software?

cause it's quick

---

### Post by iampriteshdesai on 2010-05-28
> **amauk said:**
> cause it's quick
lol

---

### Post by amauk on 2010-05-28
> **iampriteshdesai said:**
> lol

Seriously,
check out some of the UDS videos (either this years or last years)
the guy makes an address book application in eight seconds

---

### Post by simeon87 on 2010-05-28
For completeness, we should add that Quickly is just one approach to creating an application. In fact, most applications don't use it but they are simply written in a language, like Python, built on existing libraries, like Gtk.

---

### Post by iampriteshdesai on 2010-05-28
> **amauk said:**
> Seriously,
check out some of the UDS videos (either this years or last years)
the guy makes an address book application in eight seconds
UDS means Ubuntu Dev Summit???
Can you please give me a link to the address book?

---

### Post by iampriteshdesai on 2010-05-28
> **simeon87 said:**
> For completeness, we should add that Quickly is just one approach to creating an application. In fact, most applications don't use it but they are simply written in a language, like Python, built on existing libraries, like Gtk.
How do you do that?
Is there any starting tutorial?

---

### Post by towb on 2010-05-28
[PyGTK sans Quickly]

> **iampriteshdesai said:**
> How do you do that?
Is there any starting tutorial?

I got my start using [gtkmvc]("http://sourceforge.net/apps/trac/pygtkmvc/wiki") which has a lot of documentation in one place.

---

### Post by iampriteshdesai on 2010-05-28
What do majority of developers use?
say Amarok or Rhythmbox?

---

### Post by towb on 2010-05-28
> **iampriteshdesai said:**
> say Amarok or Rhythmbox?

Just look at their source...

C++/Qt and C/Gtk respectively. Totally different projects.

---

### Post by iampriteshdesai on 2010-05-28
I've always loved Qt interfaces..
Opera, KDE etc they some how look cute :P

---

