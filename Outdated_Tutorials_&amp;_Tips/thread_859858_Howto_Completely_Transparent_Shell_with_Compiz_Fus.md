---
title: "Howto: Completely Transparent Shell with Compiz Fusion"
date: 2008-07-15
forum: Outdated Tutorials &amp; Tips
---

### Post by Ocxic on 2008-07-15
Here's a tutorial I found from: [http://www.ubuntu-unleashed.com/2007/08/howto-completely-transparent-shell-on.html](http://www.ubuntu-unleashed.com/2007/08/howto-completely-transparent-shell-on.html) and was posted by defcon.
This is basically a copy/paste, but something I thought would be nice to have here.
          ** [Howto: Completely Transparent Shell on your Ubuntu desktop with Compiz Fusion]("http://www.ubuntu-unleashed.com/2007/08/howto-completely-transparent-shell-on.html") **

 I will show how to create a conky'esque transparent shell using only gnome-terminal and Compiz-fusion. Check out the attached screenshots.
[[IMG]http://bp2.blogger.com/_PqI9QqUU5zo/RtKr8J7e_gI/AAAAAAAAAyE/CtQ5SRuWqrE/s320/compizscrn1.jpg[/IMG]]("http://bp2.blogger.com/_PqI9QqUU5zo/RtKr8J7e_gI/AAAAAAAAAyE/CtQ5SRuWqrE/s1600-h/compizscrn1.jpg")
[[IMG]http://bp2.blogger.com/_PqI9QqUU5zo/RtKrhJ7e_fI/AAAAAAAAAx8/Iu73_T8LF4g/s320/compiz+terminal.jpg[/IMG]]("http://bp2.blogger.com/_PqI9QqUU5zo/RtKrhJ7e_fI/AAAAAAAAAx8/Iu73_T8LF4g/s1600-h/compiz+terminal.jpg")

First create a new profile in gnome-terminal (Edit->Profiles->New), name it "*trans*".  Set the following characteristics:

Cursor blinks: **off**
Show menubar: **off**
Initial title: **trans**
Dynamically-set title:** Isn't displayed**
Color scheme: **Black on white**
Transparent Background: **on**
Set the transparency down to** "None"**

The important part here is that now the gnome-terminal is gonna have the title *trans*.  We can now target the gnome-terminal windows that are using trans profile from inside CompizConfig by using "title=trans".

Open CompizConfig (System->Preferences->CompizConfig).  Make sure you have the **regEx** plugin enabled.

Go to the **Window Decoration** plugin and add "!title=trans" to the* Decoration windows* field.  This will skip adding window borders to our trans terminals.
Go to the **Window Rules** plugin.  Add "title=trans" to the following fields (This will turn the terminals into a widget-like windows):
[LIST]
[*]Skip taskbar, Skip pager, Below, Sticky, Non resizable windows, Non minimizable windows, Non maximizable windows, Non closable windows
[/LIST]
In the * Fixed Size Window*s section click add.  Use "title=trans" for the the *Sized Window* field and put the height and width you want for your shells.

Go to the **Place Windows** plugin, go to the *Windows with fixed positions* tab, in *Windows with fixed positions* click add.  Put "title=trans" in *Positioned Windows* field and put x and y coordinates of the default position you want for your shell (top-left corner is 0,0). After they have loaded you can move them by Alt-Dragging them.

To run the transparent gnome-terminal use:
  Code:
  gnome-terminal --window-with-profile=trans 

**Edit:  **
dock: avant-window-navigator
widgets: conky
conky theme: [http://ubuntuforums.org/showpost.php...&postcount=505]("http://ubuntuforums.org/showpost.php?p=3197911&postcount=505")
****



If "Fixed Size Windows" doesn't work specify a gnome-terminal size on command line with:
gnome-terminal --window-with-profile=trans --geometry=150x50
(for 1280x1024px (above is char/lines)

---

### Post by Darkshade on 2008-07-25
Great howto, _but_ I would suggest using a name different from "trans". Something weird like "afas75l124h463h" or any window that you open and contains the word "trans" will lose decoration. Happened to me with Transmission for example, or just typing trans in gedit, firefox, whatever...

---

### Post by billgoldberg on 2008-07-25
The windows decoration part doesn't seem to work in compiz fusion 0.7.6 typing anything but "any" in there seems to loose all decorations for everything. 

Unless I'm doing it wrong.

---

