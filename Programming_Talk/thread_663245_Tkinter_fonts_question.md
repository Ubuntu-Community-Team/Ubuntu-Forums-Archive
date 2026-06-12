---
title: "Tkinter fonts question"
date: 2008-01-09
forum: Programming Talk
---

### Post by TexaCali on 2008-01-09
I'm a longtime Windows/C hobbyist programmer, mostly small graphics utilities (I work in the animation industry.) I recently installed Ubuntu on a spare computer, and have been trying to learn Python. As a learning exercise, I want to recode an earlier Windows utility, using Python and Tkinter. I want to use a font which I developed myself, using Fontographer, for the interface. I cannot make Tkinter recognize my font, although it's installed in the Ubuntu fonts, a TTF file.  Tkinter substitutes a system font! Will Tkinter only use the few fonts I find listed in Tkinter documentation? (Helvetica, Times Roman, etc.) Any advice appreciated.

---

### Post by dwblas on 2008-01-10
Running the command xlsfonts will list all fonts available to X/Tkinter.  If your font is not there, then check /etc/X11/xorg.conf to see if it is in one of the FontPath entries (or xset -q in a terminal).  If not, then you should add it or put your font in one of the paths like "/usr/share/X11/fonts/misc".  You may have to reboot to be able to use it.  You may also have to run ttmkfdir, or a similiar program in order to use them.  This is a very dated howto [http://www.faqs.org/docs/Linux-mini/TT-Debian.html#ss3.4](http://www.faqs.org/docs/Linux-mini/TT-Debian.html#ss3.4)  It has been some time since I have had to manually install a font but it is a two part process, 1) put the font in an existing path or add the path, and 2) create 2 files that let X know about the font, which I think are fonts.dir and fonts.scale in the same dir as the fonts.  If this isn't enough info then post back and I will see if I can dig up some old notes on font installation.

---

### Post by wolfbone on 2008-01-10
There are two font systems in X.org. Tk can only use the core font mechanism (at least for Tk < 8.5, AFAIK). So they won't look too good and are not as easy to install. (If you only wanted to make a ttf font available to apps capable of using the Xft/fontconfig mechanism, you could just put it in the ~/.fonts directory and it would be available immediately.)

[http://www.x.org/archive/X11R7.0/doc/html/fonts.html](http://www.x.org/archive/X11R7.0/doc/html/fonts.html)

---

### Post by TexaCali on 2008-01-11
Thanks much for the feedback! I'm away from my Ubuntu machine now, but will try your suggestions at my earliest opportunity. Peace.

---

