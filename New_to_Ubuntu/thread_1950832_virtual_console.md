---
title: "virtual console"
date: 2012-04-01
forum: New to Ubuntu
---

### Post by MaWiSo on 2012-04-01
Can pictures and other files be viewed through virtual consoles or it is just limited to text ??
can i open more than one tab in one virtual console ??
Web browser and Email client in virtual consoles ??
a good text editor ??
editing network settings in terminal or virtual consoles (connecting,disconnecting,adding new network, etc)


can GUI applications be run from virtual consoles ??

---

### Post by gordintoronto on 2012-04-01
The answer is "yes."

What particular virtual console were you thinking about?

---

### Post by MaWiSo on 2012-04-01
I do not understand your question


all I know about virtual consoles is that it is called by (ctrl + alt + F1:F6)

---

### Post by gordintoronto on 2012-04-02
Oh, those "consoles." Text only, AFAIK.

There are text-based web browsers, text editors, email programs, etc. Not things I want to use, except maybe a text editor.

---

### Post by MaWiSo on 2012-04-03
then I can not even see pictures saved on my hard disk ??



ouch !!
how did people view pictures and graphics before GUIs ???!!


and about the mail,web browser and text editors 
their names plz ...

---

### Post by gardnan on 2012-04-03
It is not entirely without graphics. There is the Linux Framebuffer which can be used to render basic graphics for the virtual consoles. Mplayer and fbi use this so that you can view pictures or video, but it is not as well supported as an X server, I would say. You have to be in the video group in order to get it to work though.

Text editors are Emacs and Vi(m), maybe a few derivatives of those. Web browser is links, elinks, or lynx (common naming scheme). Mail is mutt, pine, or heirloom-mailx. To use those though, you generally have to set up your own SMTP server or program, as well as an MRA.

---

### Post by nothingspecial on 2012-04-03
> **MaWiSo said:**
> Can pictures and other files be viewed through virtual consoles or it is just limited to text ??
can i open more than one tab in one virtual console ??
Web browser and Email client in virtual consoles ??
a good text editor ??
editing network settings in terminal or virtual consoles (connecting,disconnecting,adding new network, etc)


can GUI applications be run from virtual consoles ??



To add to the earier response, you can use screen to open another "tab" in the virtual console although framebuffer applications do not work with screen.

wicd-curses will let you edit your network connection in an ncurses text environment.

Gui applications cannot be run.

---

### Post by gordintoronto on 2012-04-03
> **MaWiSo said:**
> ouch !!
how did people view pictures and graphics before GUIs ???!!


We used programs which supported the image format (.GIF) *and* the specific video card in the computer. There were even types of video files which could be displayed, using programs such as such as grasprt.

[http://netghost.narod.ru/gff/graphics/summary/grasp.htm](http://netghost.narod.ru/gff/graphics/summary/grasp.htm)

---

