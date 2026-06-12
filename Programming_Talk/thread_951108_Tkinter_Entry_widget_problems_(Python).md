---
title: "Tkinter Entry widget problems (Python)"
date: 2008-10-17
forum: Programming Talk
---

### Post by kumoshk on 2008-10-17
I've been trying to port an application I made from WxPython to Tkinter, for added portability. However, I've come across a few problems with the Tkinter text entry widget:
• Ctrl backspace and Ctrl delete won't delete whole words (just one character)
• The compose key (in Gnome, Ubuntu Hardy Heron) doesn't always work how it should (i.e. compose o ' won't output ó, but yet compose s s will make ß).
• Ctrl shift u (also in Gnome, Ubuntu Hardy Heron) won't allow for Unicode number input.

Is there a way to fix these issues? I don't have these same issues with WxPython (although I used to with the Ctrl backspace thing until something was updated or I found some workaround).

I want to use Tkinter so that people only have to download Python to run my program. I don't want them to have to install WxPython, too. Plus, I think Tkinter should work on more platforms more easily (i.e. PuppyLinux and such).

I've been looking at using Cxfreeze and Py2exe as alternatives—sticking with WxPython, but things don't seem ideal there all the time (especially since I don't have a computer with Windows to make the exe files on, and it didn't work properly when I tried it in Wine).

Thanks for any help you offer.

---

### Post by stevescripts on 2008-10-18
It is possible to write your own key/keycombination bindings in tk (and
tkinter).  You may encounter different results, under different
window managers at times.

The following links may help a bit:

[http://www.pythonware.com/library/tkinter/introduction/events-and-bindings.htm](http://www.pythonware.com/library/tkinter/introduction/events-and-bindings.htm)

[http://www.tcl.tk/man/tcl8.4/TkCmd/entry.htm#M16](http://www.tcl.tk/man/tcl8.4/TkCmd/entry.htm#M16)

If you can script a simple example of what is not working like you would expect, perhaps we can find some help ;)

Hope this helps a bit.

Steve

---

