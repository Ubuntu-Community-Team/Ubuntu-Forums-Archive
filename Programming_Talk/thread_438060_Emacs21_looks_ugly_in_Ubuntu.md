---
title: "Emacs21 looks ugly in Ubuntu"
date: 2007-05-09
forum: Programming Talk
---

### Post by O-pos on 2007-05-09
Hello,

I would like to know how to change the look of my emacs, which at this moment looks like this in this :
 [http://antoine.media-box.net/images/emacs-a.png](http://antoine.media-box.net/images/emacs-a.png)

to look like this:
[http://upload.wikimedia.org/wikipedia/commons/e/e1/Emacs-GTK.png](http://upload.wikimedia.org/wikipedia/commons/e/e1/Emacs-GTK.png)

Mainly, it's about GUI window and font. Any suggestions would be appreciated.

---

### Post by rickardg on 2007-05-09
The picture you link to is emacs 22 which is a development version but stable enough for daily use. I would recommend
```

$ sudo apt-get install emacs-snapshot-gtk

```
and then get a decent font (I like terminus, it is also in the repositories).

If you want antialiased text you probably have to compile from source or find someone that has packaged it unofficially. Google for 'xft emacs' and you'll get several promising hits, but I haven't tried any myself.

That said, I've compiled emacs-unicode-2 a couple of times, but since I started using a decent font (see below for a screenshot with terminus) I haven't felt the need for anti-aliasing.

---

### Post by O-pos on 2007-05-09
Thank you!

I installed emacs-snapshot-gtk and I like it very much. That's what I was looking for.

Regarding Fonts, I'd like to have the same font, that is in Gnome-Terminal. I think it's called monospace.. How can I replace Emacs' default font with that?

---

### Post by rickardg on 2007-05-15
Ah, the problem is that emacs doesn't support anti-aliasing (smoothing) yet. Most fonts that are meant to be used with smoothing will look horrible. To use those fonts with emacs you have to use the emacs-unicode-2 branch of the development version of emacs or you could run emacs in terminal 

```
$ emacs -nw
```

but then you would lose some of the niceities of the X11 version (M-x xterm-mouse-mode) does give you some mouse support though.

Personally, I decided bitmap fonts (designed to be used without smoothing) are easier to read anyway, even when compared to properly anti-aliased fonts.

You can tell emacs which font to use by starting it with 

```
$ emacs -fn -unknown-freemono-bold-o-normal--0-0-0-0-c-0-iso10646-1
```

using the freemono font as an example, and when you find one you like you can put it in your ~/.Xresources file ('$ man emacs' tells you how to do that and '$ xfontsel' helps you find the magical fontnames).

---

### Post by ilautar on 2007-05-15
Take a look here:
[http://peadrop.com/blog/2007/01/06/pretty-emacs](http://peadrop.com/blog/2007/01/06/pretty-emacs)

works great on my kubuntu feisty with monospace font.

---

