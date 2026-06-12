---
title: "Best Latex editor"
date: 2005-10-29
forum: Programming Talk
---

### Post by inechita on 2005-10-29
Hi. I would like to hear your opinions on the best latex editor on Ubuntu. Already tried Kile (feels weird with gnome) and winefish (pretty cool IMHO). 

Thanks

---

### Post by LaserJock on 2005-10-29
don't you think you should have more options? I mean there is teXmacs, lyx, texmaker and just plain old emacs/autex and gvim/latex-suite to name a few.

When in KDE I do really like Kile but since moving to Ubuntu and Gnome I tend to use gvim with latex-suite or even gedit if it's something small. I don't much care for lyx and haven't tried the others I have mentioned.

just my $0.02

-LaserJock

---

### Post by Manny C on 2005-10-29
[quote=LaserJock]don't you think you should have more options? I mean there is teXmacs, lyx, texmaker and just plain old emacs/autex and gvim/latex-suite to name a few.

When in KDE I do really like Kile but since moving to Ubuntu and Gnome I tend to use gvim with latex-suite or even gedit if it's something small. I don't much care for lyx and haven't tried the others I have mentioned.

just my $0.02

-LaserJock[/quote]

Try [EmacsCVS]("http://www.emacswiki.org/cgi-bin/wiki/EmacsCvsAndDebian") (has GTK2 support). Need Breezy to install this.

---

### Post by inechita on 2005-10-30
[QUOTE=LaserJock]don't you think you should have more options? I mean there is teXmacs, lyx, texmaker and just plain old emacs/autex and gvim/latex-suite to name a few.
-LaserJock[/QUOTE]

Yes, you're right. But texmacs and lyx are wysiwyg, contrary to latex principles and all the software you mentioned is not gnome/kde native and hard to use for a person who comes from windoze. I want something simple, integrated, installable by synaptic (if possible - I'm no computer scientist, justa wanna type my math articles), and with a fast learning curve (emacs is a show breaker - different shortcuts, etc).

Thanks

---

### Post by inechita on 2005-10-30
By the way, I don't think it's possible to add more options to the poll.... Sorry

---

### Post by ssam on 2005-10-30
gedit
because
*syntax highlighting
*spell check (wiggly red line type)
*mouse support

---

### Post by ubuntumaneh on 2005-10-30
emacs/auctex can be installed from synaptic. There is highlight and everything. I would say it is not that simple (configuring it can be very frustrating sometimes). Once you are used to it, it is a good tool. I suggest opening a new poll with more options. BTW, I know lots of people that still use vim, including very young people. If you are not working with heavy articles, you can even use nano.

---

### Post by jerome bettis on 2005-10-30
[quote=LaserJock] gvim/latex-suite[/quote]

yep that's what i use.

---

### Post by LorenzoD on 2005-10-31
[QUOTE=jerome bettis]yep that's what i use.[/QUOTE]

+1

---

### Post by bdash on 2005-10-31
Emacs with Auctex.

---

### Post by GoldBuggie on 2005-10-31
I think Kile is a perfext TeX editor. Has help on command...nice gui...shortcut buttons for those commands that you might not remember...some predifined macros so that you can get a table a bit faster...and the compile and view buttons.

In short..it's perfect.

---

### Post by parktownprawn on 2005-11-12
If you are using gnome I think that texmaker ([http://www.xm1math.net/texmaker/](http://www.xm1math.net/texmaker/))
is a better option than kile - although also qt based it seems to load a lot faster than kile under gnome. it also doesn't depend on a lot of kde stuff. it does have less features than kile though.

personally i like lyx or emacs with auctex.

---

### Post by Velvet Elvis on 2005-11-12
> personally i like lyx or emacs with auctex.

Those are the only two I use as well.

---

### Post by darth_vector on 2005-11-13
vim!

this place is a jungle, too many emacs ppl :D

---

### Post by macgyver2 on 2005-11-13
[QUOTE=jerome bettis]yep that's what i use.[/QUOTE]
Same here.

---

### Post by cynoclast on 2009-09-10
[Jedit]("http://www.jedit.org/").

Open source, java, cross platform, very powerful.

And I wanted a really quick and easy way to regenerate the output PDF, so I used a complicated looking bash command that kills any outstanding pdf being viewed, regenerates and redisplays the new pdf, then returns you to the command line.  That way you can just hit up, enter and regenerate.

Here's the command:
```
psg evince | awk '{print $2}' | xargs kill 2>/dev/null 1>&2; pdflatex doc.tex 2>/dev/null 1>&2 && evince doc.pdf & 2>/dev/null 1>&2;
```

psg is just a simple .bashrc function that greps ps -aux for the the first argument you give it.

While I'm at it, here's that function:
```
psg() {
  if [ ! -z "$1" ] ; then
    ps aux | grep -i "$1" | grep -v grep
  else
    echo "Need a process name to grep processes for"
  fi
}
```

---

### Post by Can+~ on 2009-09-11
Old post is old. But still:

```
sudo apt-get install gedit-latex-plugin
```

Now gedit becomes a LaTeX editor.

---

### Post by kranny on 2009-09-11
+1 for kile

---

