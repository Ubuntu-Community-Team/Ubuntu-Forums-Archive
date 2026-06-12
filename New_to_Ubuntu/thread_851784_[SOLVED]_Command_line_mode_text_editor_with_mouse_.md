---
title: "[SOLVED] Command line mode text editor with mouse support?"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by WitchCraft on 2008-07-07
Question:

Linux has several command line text editors, like emacs, vi, and nano.

What I wanted to know is whether there is a command line text editor that supports the mouse, like old edit.com in DR & MS-DOS ?

I don't want any X-server thing (like gedit), nor any sophisticated stream editor like emacs, just a useful command line text editor WITH MOUSE. Since device drivers should be in the kernel, it should be possible (at least if properly configured), is it?

---

### Post by LordDelta on 2008-07-07
I can't be of any help, but I'd just like to voice that I'd be interested to know about anything you find out about....I don't know editors very well, but I miss a clean solution to my editing needs, like notepad++ on Windows, and I don't know if it makes any difference, but I think its possible to run emacs in the terminal instead of an x window. Something with mouse support would indeed be nice, but I'd think you would have to be running in a modified terminal, no?

---

### Post by WitchCraft on 2008-07-07
> **LordDelta said:**
> I can't be of any help, but I'd just like to voice that I'd be interested to know about anything you find out about....I don't know editors very well, but I miss a clean solution to my editing needs, like notepad++ on Windows, and I don't know if it makes any difference, but I think its possible to run emacs in the terminal instead of an x window. Something with mouse support would indeed be nice, but I'd think you would have to be running in a modified terminal, no?

Indeed, as far as I know there exists nothing. But the edit on dos shows that it is possible. You would probably have to configure the mouse driver, however.

---

### Post by WitchCraft on 2008-08-04
bump.

---

### Post by mcduck on 2008-08-04
At least nano has option to enable mouse. I've only tried it from a gnome terminal, not in a VTT, but you could give it a try..

Check "man nano" & "man nanorc" for more info.

edit: I just tested, and simply enabling mouse for nano is not enough, you also need to enable mouse for the VTT itself.

---

### Post by cdtech on 2008-08-04
What would you like to use the mouse for? I use "pico" (transparent terminal on my desktop) using mouse, cut paste shortcut key's. Does everything I need. What more could you need short of a "sophisticated stream editor"?

---

### Post by Mister.Vash on 2008-08-05
Are you talking about getting the mouse on the various tty consoles?  To do this, install the gpm package
```
sudo apt-get install gpm
```

This will install the General Purpose Mouse Interface and allow the mouse to work for the various ttys - just restart after installing



Or are you looking to have a console text editor running under a gnome-terminal session?

---

### Post by WitchCraft on 2008-08-19
> **Mister.Vash said:**
> Are you talking about getting the mouse on the various tty consoles?  To do this, install the gpm package
```
sudo apt-get install gpm
```

This will install the General Purpose Mouse Interface and allow the mouse to work for the various ttys - just restart after installing



Or are you looking to have a console text editor running under a gnome-terminal session?

No, under the console terminal, not the gnome-terminal. Gnome offers gedit, which is much better.
I wanted one for the console.

Yes, I can now confirm that you can do it with nano:

you need to sudo gedit /etc/nanorc 

and there change
# set mouse
into
set mouse

Then apt-get install gpm, as said, and then it works.

Really simple, install the mouse driver (gpm) just as in DOS, and then it works. The only thing I didn't know was, that you need to change the config file. That's all.

Nano is a really nice console editor, it beats edit.com, even though it is not as user friendly.

---

### Post by VenemousWookiee on 2012-10-03
FTE or eFTE are DOSlike editors with graphical and console interfaces. The graphical interface is mostly the same as the console interface,  just running in a dedicated window, but both support mouse.

[http://fte.sourceforge.net/](http://fte.sourceforge.net/)
[http://efte.cowgar.com/cgi-bin/wiki.pl](http://efte.cowgar.com/cgi-bin/wiki.pl)

---

### Post by oldos2er on 2012-10-03
Old thread closed, please don't bump old threads.

---

