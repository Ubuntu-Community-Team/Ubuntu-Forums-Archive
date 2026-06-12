---
title: "Compiz Fusion hates Easygui..."
date: 2007-12-22
forum: Programming Talk
---

### Post by family on 2007-12-22
the choicebox, multchoicebox, and basically anything not resembling a pop-up that easygui produces is rendered as blank white space inside a window while using Compiz Fusion. A quick metacity --replace shows that easygui works perfectly. Hmmmmm....

Can anyone confirm issue before a file a report? (This is a Python thing btw)

---

### Post by LaRoza on 2007-12-22
> **family said:**
> the choicebox, multchoicebox, and basically anything not resembling a pop-up that easygui produces is rendered as blank white space inside a window while using Compiz Fusion. A quick metacity --replace shows that easygui works perfectly. Hmmmmm....

Can anyone confirm issue before a file a report? (This is a Python thing btw)

choicebox was a big white window, so it is a problem.

msgbox worked though. I am using the Inhuman theme, if that makes a difference.

(EasyGUI used Tkinter, so the problem may be with that)

---

### Post by family on 2007-12-25
Lol, the Ubuntu SE one? Nice!
I just use metacity now. CF blacklisted my video drivers or something retarded like that...

---

### Post by LaRoza on 2007-12-25
> **family said:**
> Lol, the Ubuntu SE one? Nice!
I just use metacity now.

I use the entire ubuntu-satanic package, but use a black background.

What video card? There may be a fix, search the forums.

---

### Post by family on 2007-12-25
Yes, I've made a post;
[http://ubuntuforums.org/showthread.php?t=649822](http://ubuntuforums.org/showthread.php?t=649822)

Thx

---

### Post by LaRoza on 2008-01-30
It is still a problem.

I want to use the easygui.choicebox() but it just freezes my computer.

I don't have to use it, but for my program it is the best option. I can't expect users to not use Compiz-Fusion if I make this program (indeed, I am using it).

Anyone know of any fixes or other issues with Tkinter and EasyGUI?

---

### Post by 1337455 10534 on 2008-01-31
I am having issues with any easygui functions used while the wxWidgets is in the background.
while deluge or my own program is running, easygui returns a type 441 X error and my other program crashes.

another particularily troublesome issue is this;
1. I am in metacity
2. I execute my program
3. easygui is working; buttonbpx()
4. I launch a wxGlade created GUI
5. I try the following things;
msgbox, buttonbox, choicebox, and fileopenbox: all of which cause an X error and kill my program. I am now trying to create a widget that will let me take care of that issue without using easygui...

I wrote to Stephen Ferg. He had no idea why this was happening...

---

