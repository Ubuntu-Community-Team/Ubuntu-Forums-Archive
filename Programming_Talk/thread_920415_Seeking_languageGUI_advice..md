---
title: "Seeking language/GUI advice."
date: 2008-09-15
forum: Programming Talk
---

### Post by SteveHiggins on 2008-09-15
I have 'dabbled' in coding for a while. A bit of C and C++.
Now I want to move up to coding GUI apps.
I have *no* desire to get a job coding. This is just strictly a hobby.
I will be coding for graphics (2D and 3D - I'm not sure if opengl is C or C++). I have a fairly strong mathematical background (undergraduate level).
So, my two main considerations are
1) Do I need to get to grips with OOP for small to medium size GUI apps (in which case I'll just stick with C++ and I guess KDE would be ideal as it's mostly C++)
2) Should I just stick with good old C and code for GNOME (GNOME is C based, yes?) or some other C based GUI.

If anyone can comment I'd be grateful.

Thanks,
Steve.

---

### Post by slavik on 2008-09-15
actually, if you intend on doing heavy OGL stuff, the choice of KDE vs. GNOME is irrelevant ...

---

### Post by SteveHiggins on 2008-09-15
> **slavik said:**
> actually, if you intend on doing heavy OGL stuff, the choice of KDE vs. GNOME is irrelevant ...

Would you care to expand on that?

OpenGL is just one thing, not the only thing, I would code for.

---

### Post by lunisneko on 2008-09-15
OpenGL is a graphics language that is above and beyond simply KDE or Gnome or any other window manager, and for the most part is used to code 3D applications (such as games). For the most part, OpenGL has nothing to do with GUIs. As far as GUI programming goes, you basically just need to choose between Gtk, Qt, and wxWindows (there are probably others) and then choose a programming language that works with your UI choice. Personally I use Python+Gtk. You can use C with Gtk, but I personally don't suggest using C++, since libglade's autoconnect signals feature doesn't really work in it :)

---

### Post by SteveHiggins on 2008-09-15
> **lunisneko said:**
> OpenGL is a graphics language that is above and beyond simply KDE or Gnome or any other window manager, and for the most part is used to code 3D applications (such as games). For the most part, OpenGL has nothing to do with GUIs. As far as GUI programming goes, you basically just need to choose between Gtk, Qt, and wxWindows (there are probably others) and then choose a programming language that works with your UI choice. Personally I use Python+Gtk. You can use C with Gtk, but I personally don't suggest using C++, since libglade's autoconnect signals feature doesn't really work in it :)

I know opengl is independent of the GUI, although of course you can write an opengl 3D plotter in most languages and for any GUI.
But lets not get hung up on opengl as it's only one factor in my decision.
I think whether to bother with OOP is more of an issue for me.
Maybe I'll have to ask on a more specialized forum...

---

### Post by pmasiar on 2008-09-15
Not only desktop (Gnome vs KDE) is irrelevant: even language is: you want to pick a project first, and then use the language they use. 

Because you don't want to get job, you may as well consider any project using the most productive language - which would be high level, like Python. But project is more important than language - they all call same library anyway. You will invest hundreds of hours in the project - so it has to be fun for you. Worldforge?

---

### Post by techmarks on 2008-09-15
> **SteveHiggins said:**
> I have 'dabbled' in coding for a while. A bit of C and C++.
Now I want to move up to coding GUI apps.
I have *no* desire to get a job coding. This is just strictly a hobby.
I will be coding for graphics (2D and 3D - I'm not sure if opengl is C or C++). I have a fairly strong mathematical background (undergraduate level).
So, my two main considerations are
1) Do I need to get to grips with OOP for small to medium size GUI apps (in which case I'll just stick with C++ and I guess KDE would be ideal as it's mostly C++)
2) Should I just stick with good old C and code for GNOME (GNOME is C based, yes?) or some other C based GUI.

If anyone can comment I'd be grateful.

Thanks,
Steve.

I'd prefer mostly C++ for graphics and math type of programming.

C is a good choice but I think the libraries for C++ are better.

You can use C++ with GTK, but the trouble is with the Gtkglext library. I had lots of trouble compiling it as C++, you might have better luck with Gtkglarea, which I've not tried yet.

C has a small performance advantage over C++ for numerical programming.

But still I think just the better libraries in C++ make the choice for me, also OOP is a good help to organise the program more easily.

It's also possible to use Cairo for 2d and 3d graphics and it is coded in C, so C is still a good choice.

Really it comes down to the needs for a specific project, and which libraries will help you most.

---

