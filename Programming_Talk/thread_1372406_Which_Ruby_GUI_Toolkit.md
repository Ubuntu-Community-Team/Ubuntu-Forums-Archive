---
title: "Which Ruby GUI Toolkit?"
date: 2010-01-04
forum: Programming Talk
---

### Post by SunSpyda on 2010-01-04
I've known Ruby for a while, and can build GUIs in many other toolkits, like Java/Swing, GTK(With C and Python, and more recently, .NET), and small bits and bobs from a few others, including WinForms and wxWidgets.

So, I'm interested in picking up a toolkit for Ruby (sounds awfully familiar to a similar thread I made about .NET GUI toolkits for C#) for certain reasons, but I've heard it's a poor language for GUIs... maybe someone here could elaborate. Anyway, I know my other toolkits for certain reasons... Java/Swing for portable GUIs for computer-illiterate end-users, GTK because GNOME is fast becoming the 'standard' GUI for UNIX, WinForms due to it being 'native' Windows, and wxWidgets just because it looked cool. However, my reason for wanting a Ruby GUI toolkit is quite different. Here are factors to take into account... :)

- I don't care about immediate portability, but I care VERY much about potential portability.
- I want free licensing to let me do what I want without costs/restrictions, regardless of whether I sell the code or not (which I won't anyway). This is Qt out automatically.
- It has to be at least remotely stable.
- Don't care if it's really hard to use. If I can use GTK/C and the basics of wxWidgets/C++ then I should be able to see any others through.
- I would rather it be a toolkit designed for cross-platform use, than a single-platform one that was patched/binded for other platforms.
- Reiterating the first point, it should be available on a lot of OSes, and available on most UNIX packaging systems, especially Linux and BSD. Whether it is default on a lot of systems though, I'm less bothered about.
- It should be powerful and advanced. As in, not Ruby/Tk.
- My end-users are technical users. So out-the-box ease of use isn't essential.

I'm thinking wxRuby is the way to go here. BUT, it isn't to stable last I heard, and it isn't on a few packaging systems, like OpenBSD's. So... any alternatives?

Thanks in advance :D

---

### Post by cknoblock on 2010-01-04
[http://wxruby.rubyforge.org/wiki/wiki.pl](http://wxruby.rubyforge.org/wiki/wiki.pl)

This wiki here rates it as production quality, though I have no personal experience with it.  If you have already learned the basics of wxWidgets I would try to stay with that.  Why learning something new again?  Like you I have used several GUI toolkits from Swing, SWT, Qt, etc. and I'm tired of relearning all the nuances.

---

### Post by ggaaron on 2010-01-05
> **SunSpyda said:**
> 
- I want free licensing to let me do what I want without costs/restrictions, regardless of whether I sell the code or not (which I won't anyway). This is Qt out automatically.

You mean non-copyleft license? Newer versions of Qt are available also under LGPL.

I've used ruby with GTK+ and it was ok. Probably choose one of GTK+/wxWindows you like best, both seem to work well. I would discourage Qt with ruby - the bindings are unstable and they don't compile for many users.

---

### Post by bildr on 2010-05-27
I like wxruby except that it doesn't install from gem properly yet on latest ubuntu, i posted installation instructions on another thread.  I do wish ubuntu would give the option of original package install for packages it breaks up into pieces and kind of mangles.  I know why they do it but it's still a little irritating sometimes.

The only reason I would use QT is if I were trying to get to some mobile platform that only supports QT.

---

### Post by nmccrina on 2010-05-27
Have you considered using JRuby and Swing? Like the wxruby, I would think it would be a breeze to pick up since you say you're already familiar with Swing.

---

### Post by bildr on 2010-05-29
Liking wxruby so far.  Many RAD IDEs to choose from.  I like Code::Blocks to generate an xrc file quickly.  The rubygem wx_sugar can then generate the ruby routines to handle the callbacks for buttons and controls.  It is cross platform and allows rapid application development for linux, windows, mac, and unix.  It has support for multimedia and all the common widgets for layout and design.  It even features an odbc connector.  The hardest part for me was getting the initial setup down on linux with multimedia.

---

