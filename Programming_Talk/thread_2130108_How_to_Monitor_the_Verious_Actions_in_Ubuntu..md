---
title: "How to Monitor the Verious Actions in Ubuntu."
date: 2013-03-28
forum: Programming Talk
---

### Post by anandc8788 on 2013-03-28
Hello Friends,

I like to learn the new things with the approach - do something apart from your educational profile.

Now, I need your expertise to educate me on some "How to's".

Requirement : 

I want to create an application which will keep track of all copy/paste or cut/paste actions.

I want to know what file user is trying to mirror and on what device.

Could you please give me a hint, with which I write the program.

- language neutral < means the solution could be anything c/c++/shell/perl >

Regards,
Anand

---

### Post by anandc8788 on 2013-03-29
Could anyone plz. help me?

There are total 101 views but no one is able to respond. am I at wrong place with my question.
I have asked it here because I felt that most of the Ubuntu masters are here....

Someone plz. help.

I am not expecting the program. but at least give me hint.

---

### Post by r-senior on 2013-03-29
> **anandc8788 said:**
> I want to create an application which will keep track of all copy/paste or cut/paste actions.
Clipboard actions and events are handled by the windowing system, which you can access with a windowing toolkit like GTK, wx or QT. 

Your choice of windowing toolkit depends on the systems you are trying to support, the language you prefer to use and whether you want the program to be cross-platform

For example:

[http://python-gtk-3-tutorial.readthedocs.org/en/latest/clipboard.html](http://python-gtk-3-tutorial.readthedocs.org/en/latest/clipboard.html)
[https://developer.gnome.org/gtk3/stable/gtk3-Clipboards.html](https://developer.gnome.org/gtk3/stable/gtk3-Clipboards.html)
[https://developer.gnome.org/gtkmm-tutorial/stable/chapter-clipboard.html.en](https://developer.gnome.org/gtkmm-tutorial/stable/chapter-clipboard.html.en)
[http://www.wxpython.org/docs/api/wx.Clipboard-class.html](http://www.wxpython.org/docs/api/wx.Clipboard-class.html)
[https://qt-project.org/doc/qt-5.0/qtgui/qclipboard.html](https://qt-project.org/doc/qt-5.0/qtgui/qclipboard.html)

> I want to know what file user is trying to mirror and on what device.
Is this question still about the clipboard or are you talking about something else?

> language neutral < means the solution could be anything c/c++/shell/perl
You will be restricted by the availability of language bindings for the windowing toolkit you select. You are most likely to find bindings for languages like C, C++ and Python but others may be supported.

---

### Post by schragge on 2013-03-29
For how to access the standard X selection from shell, see [xsel](http://manpages.ubuntu.com/manpages/precise/en/man1/xsel.1x.html) and [xclip](http://manpages.ubuntu.com/manpages/precise/en/man1/xclip.1.html).

---

### Post by anandc8788 on 2013-03-29
Hi [**[COLOR=#000000]r-senior[/COLOR]**]("http://ubuntuforums.org/member.php?u=288993"), [**[COLOR=#000000]schragge[/COLOR]**]("http://ubuntuforums.org/member.php?u=1783515"),

Thank you for your responses !

Just by looking at the suggestions, it will allow me to understand what text user is attempting to copy from within the file.

However, my area of interest is to monitor - what files/folders user is attempting to copy/paste ( i.e. Mirror on some other device like usb storage ).

I will program the remaining part, just need Hint to understand how to recognize the system copy/paste events.

---

### Post by spjackson on 2013-03-30
I once wrote a program to maintain a "clipboard history" - for Linux and Windows. I don't remember whether it used Qt or wxWidgets. The method I used was simply to poll the clipboard(s) every 200ms or so and save if it had changed. I think KDE's klipper does something like this and there are other implementations.

I'm not sure that your objective of finding out which "file" the copy comes from is achievable. Copying may not necessarily be from a "file", or a user might do for example "cat foo.txt" then copy from the terminal window. Similary, the user might paste into a new untitled document. You don't know at that point that it will later be saved to usb storage. A user might also copy from the original file to an untitled document, then copy from the untitled document to another document. I can't see how you can realistically audit these actions.

---

