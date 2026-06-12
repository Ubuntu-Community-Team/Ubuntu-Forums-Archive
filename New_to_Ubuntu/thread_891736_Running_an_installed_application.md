---
title: "Running an installed application"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by DouglasL on 2008-08-16
**_[COLOR="Red"]THE PROBLEM IS SOLVED[/COLOR]_**


[I][COLOR="Silver"]Sorry for posting another thread so quickly.

Okay, so I've downloaded a tar.gz package. I compiled it, and I installed it.

But I just can't figure out how to run it?
I've been googling, without success.[/COLOR][/I]

---

### Post by wolfen69 on 2008-08-16
type the name of the app into a terminal and hit enter. also, check to see if you can add it into the menus by going to system>preferences>main menu.

---

### Post by DouglasL on 2008-08-16
Doesn't work.

I get "kommandot hittades inte" - which in english means "the command wasn't found" or something like that.

---

### Post by jrothwell97 on 2008-08-16
Annoyingly, this is very inconsistent across packages. There should be something about the default installation path in README, and I think if you assign a certain switch to make, it can install it wherever you want. I'm unsure about the workings of make, I'll look into it.

---

### Post by DouglasL on 2008-08-16
The readme says this:
[B]
Run from within this directory for now (use ./gautoclick et cetera) or install
the binaries in some bin directory yourself[/B].

What does this mean? How do I run it from it's directory?

---

### Post by Cheesehead on 2008-08-16
> **DouglasL said:**
> The readme says this:
[B]
Run from within this directory for now (use ./gautoclick et cetera) or install
the binaries in some bin directory yourself[/B].

What does this mean? How do I run it from it's directory?

Look inside the directories the new app created to see if you find the executable file. It shouldn't be a Readme or News or Make or Config, and should resemble the command you're trying to install. 

If you're using Nautilus or Thunar, it should look like an executable (not a page, but a diamond...or whatever executable look like in your current theme).

If you're on the command line, do 'ls -F'. Executables appear in green, with a * at the end (unless you've changed your bash preferences, of course).

For example, /Desktop/Foo_App/fooapp is what's we're looking for.


Once you've found the executable, the next step is to run it.

It's easy - just type the full path+name on the command line:
$/home/me/Desktop/Foo_App/fooapp

Or you can: $cd /Dektop/Foo_App/ 
then simply: $./fooapp

Bash looks for execuable in the /bin, /sbin, /usr/bin, or /usr/sbin directories. Most don't really live there, just links to them do.

In this case, typing simply $fooapp won't work, because you haven't put a link in there yet. Linking (command ln) is a topic for a different 15 minutes.

---

### Post by DouglasL on 2008-08-16
Hrm, the only executable within the (uncompiled) directory is "configure", so that doesn't help.

---

### Post by DouglasL on 2008-08-16
As this is at least somewhat semi-urgent, and seems to be a fairly simple problem I thought I'd bump the thread.

(I still haven't solved anything)

---

