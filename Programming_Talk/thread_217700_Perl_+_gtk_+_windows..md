---
title: "Perl + gtk + windows."
date: 2006-07-17
forum: Programming Talk
---

### Post by Engnome on 2006-07-17
I've been doing some apps in perl (wich work fine on ubuntu) but I want to show/give them to friends so they can use them to but they rely  on perl5, gtk2 and libglade.

I have downloaded [http://www.activestate.com/Products/ActivePerl/?_x=1](http://www.activestate.com/Products/ActivePerl/?_x=1) perl interpreter so my cli based programs work. But when I'm trying my gtk apps is says:

Can't locate Glib.pm in @INC...

I have gtk installed  but I don't know what to do now.

Also is it possible to use glade XML files to generate the gui in windows? I found libglade compiled for windows but it's a .dll what do i do with that?

Linux is so much easier...:)

---

### Post by ifokkema on 2006-07-18
> **Engnome said:**
> Can't locate Glib.pm in @INC...
Did you install libglib-perl? The file is in that package.

---

### Post by Engnome on 2006-07-18
> **ifokkema said:**
> Did you install libglib-perl? The file is in that package.

libglib-perl? Where? Tried google but no luck. What package?

---

### Post by ifokkema on 2006-07-18
As in:
```
sudo apt-get install libglib-perl
```
The Glib.pm file you mentioned, is included in the libglib-perl package. Maybe installing that package may help.

---

### Post by Engnome on 2006-07-18
> **ifokkema said:**
> As in:
```
sudo apt-get install libglib-perl
```
The Glib.pm file you mentioned, is included in the libglib-perl package. Maybe installing that package may help.

With windows in the thread title I mean windows as in Windows XP (c) not as in windows on a house or even windows in wich program outputs information.

Had you followed the link in my first post you would have gotten to a site offering a perl interpreter in .exe format.

But thx for your help anyway, guess this might be the wrong forum even though it says:

[QUOTE=ubuntuforums.org]Programming Talk This forum is for all programming questions.
The questions do not have to be directly related to Ubuntu and any language is allowed.[/QUOTE]

---

### Post by Hezekiah on 2006-07-18
You need to find the Gtk2 package for ActiveState's perl.  ActiveState uses something called Perl Package Manager - look through there and see if you can find anything.

Also, you can take a look at the Gtk2-perl website which may have more information.

---

### Post by ifokkema on 2006-07-19
> **Engnome said:**
> With windows in the thread title I mean windows as in Windows XP (c) not as in windows on a house or even windows in wich program outputs information.
LOL, must have been sleeping or something :)

> **Engnome said:**
> Had you followed the link in my first post you would have gotten to a site offering a perl interpreter in .exe format.
No doubt, but I didn't follow the link because the Windows part in my brain recognized the URL. After that, the Linux side took over again :)

> **Engnome said:**
> But thx for your help anyway, guess this might be the wrong forum (...)
No, it's not. Must people on these forums are Linux users of course, but many of them not exclusively. It was just me ](*,)

---

### Post by Engnome on 2006-07-19
Perl package manager! lol, anyway thx Hezekiah I found what I needed in Gtk2 perl website (I think)

[QUOTE=Henry Spencer]Those who do not understand Unix are condemned to reinvent it, poorly.[/QUOTE]

This seems more appropiate every time I learn something new about unix.

---

### Post by Hezekiah on 2006-07-19
If you do get this working (Gtk2 + Glade + Perl) on Windows, please post back!  I'd be interested to hear how it works out for you :-)

Good luck!

---

