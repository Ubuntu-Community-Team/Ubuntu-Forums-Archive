---
title: "Python Code Review Request"
date: 2010-07-13
forum: Programming Talk
---

### Post by mcphargus on 2010-07-13
Hi all,

I'm working on a project right now. It has a very narrow focus (a small industry will benefit from its release), but I'm wondering if someone could take time out of their busy schedule to criticize it. I'm wondering I should take a different approach to it, or implement a specific design pattern that I'm not aware of.

Background on the project:
It's purpose is to help energy auditors perform surveys of sites. These guys walk around and take note of electric loads (air-conditioners, resistive loads like office equipment, etc) and then plug the information into this thing.

The source of the project is on launchpad at [http://launchpad.net/eesu](http://launchpad.net/eesu)

I'm also curious as to how I can implement unittesting in something like this. It's very GTK focused, and I'm just too lost when it comes to unittesting. There's no real gui/backend separation, its just all sort of folded in together.

Any comments will be greatly appreciated. Thanks again, guys!

---

### Post by StephenF on 2010-07-13
To put data into the user interface for testing I would make the application user interface elements available on D-Bus, then write the tests as a separate program.

Minimalist D-Bus example.
[http://paste.lisp.org/display/45824](http://paste.lisp.org/display/45824)

---

### Post by mcphargus on 2010-07-13
There's a lot of user interface elements, so that will be a challenge, but I imagine it will save that much time in testing. Thanks for the suggestion StephenF!

---

### Post by Bachstelze on 2010-07-14
Including a debian/ directory in your source release is generally frowned upon (I know you didn't make a release yet, but consider that when you do). The code and the packaging should be kept separate.

---

### Post by nvteighen on 2010-07-14
> **Bachstelze said:**
> Including a debian/ directory in your source release is generally frowned upon (I know you didn't make a release yet, but consider that when you do). The code and the packaging should be kept separate.

As someone that still doesn't know how to deal with this (having reverted PycTacToe from having a debian/ folder to not and then back again), I've noticed some projects do have it. Of course, the debian/ folder included is just what's called the "Debian packaging source" (the rules and control files and needed scripts... i.e. what's left after running debian/rules clean).

Such an approach has helped me a lot... But I'm interested in knowing the disadvantages. I've been looking at this issue several times and haven't got anything that could clear my mind a bit :)

---

### Post by mcphargus on 2010-07-18
Thanks for the replies and critiques. 

The debian directory is introduced by [quickly]("https://wiki.ubuntu.com/Quickly"), I need to retool it to make it work again. Quickly is so young that some of it's earlier habits don't work as well now. The original idea was to allow quickly users to push packages to launchpad that would build right away, hence the debian directory.

I'll get it working in the future, I just want the application to run functionally from within the source tree first, then I'll tackle that bit.

EDIT: sry to resurrect a dead thread.

---

### Post by Bachstelze on 2010-07-19
> **nvteighen said:**
> 
Such an approach has helped me a lot... But I'm interested in knowing the disadvantages. I've been looking at this issue several times and haven't got anything that could clear my mind a bit :)

If someone wants to package it for inclusion in a distro's official repos, your /debian dir will get in the way, because it will not work for them.  When a project has a debian/ dir in the uptream tarball, the first thing the packagers do is generally to move it away to debian.upstream/ and then create its own debian/ dir.

---

