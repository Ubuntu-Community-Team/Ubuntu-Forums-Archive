---
title: "Ubuntu Gnome Emacs22, Emacs23 Scrolling mess"
date: 2010-04-22
forum: Programming Talk
---

### Post by soborobo on 2010-04-22
First off, I do not know if this is a problem of (1) emacs, (2) ubuntu, or (3) gnome !

Scrolling is all messed up in emacs!  When I click in the scroll-bar emacs nicely selects a piece of text and colors the selection.  If at that point one makes a bad click in the buffer, the selection is deleted.  Furthermore, the colored selection makes the text unreadable!  How do I turn off this automatic coloring of text in this exact situation?

In addition, in the scroll-bar ONLY left-clicks are taken into consideration!  This may be a gnome problem, because gnome terminals have this same problem!  Only, if you open an unadorned plain xterm is correct scrolling performed!  Scroll-wheel actions are correct!

Correct scrolling activity in a window:

I will not re-describe above correct behavior!  A left-click in the scroll-bar will scroll down the window the amount relative to the top of the visible window port.  So, if you click near the bottom of the scroll-bar the window scrolls down one page!  If you do the same near the top of the scroll-bar then only a few lines are scrolled down.

A right-click in the scroll bar currently does nothing! :mad: Its operation should be the opposite of the left-click, basically scrolling up the window port based on where in the scroll-bar it is activated.  If you scrolled down with a left-click, then a right-click at the exact same position will return the window to the same position that it was at before that initial left-click!

Can this be corrected within emacs?  Or will gnome or linux need modification? :confused:

Thanks for your comments!

---

### Post by jpkotta on 2010-04-24
[http://www.gnu.org/software/emacs/manual/html_node/emacs/Scroll-Bars.html](http://www.gnu.org/software/emacs/manual/html_node/emacs/Scroll-Bars.html)
[http://www.emacswiki.org/emacs/ScrollBar](http://www.emacswiki.org/emacs/ScrollBar)

I experimented a bit.  It seems like with either GTK or Motif toolkits, you can't bind <mouse-3> to the scrollbar.  If you build emacs using its own toolkit to handle scrollbars, you should be able to bind all mouse events to them.  If the emacs scrollbars are what I'm thinking of, they're little more than a rectangle of one color drawn inside of a rectangle of another color sort of like [this]("http://en.wikipedia.org/wiki/File:X-Window-System.png").

---

### Post by Lux Perpetua on 2010-04-24
> **soborobo said:**
> First off, I do not know if this is a problem of (1) emacs, (2) ubuntu, or (3) gnome !It's not an Ubuntu or GNOME problem, since I noticed the same thing on Arch Linux with XFCE. :-)

---

### Post by soltanis on 2010-04-24
If these scrollbars are ugly and black and only work in one direction, I sympathize with you. If you look into xvncviewer and see the same scroll bars, then these things totally suck, and do not work, at least not how they are supposed to.

I think you should be able to scroll the Emacs buffer using some magical key combination, though good luck finding it.

---

### Post by soborobo on 2010-04-30
Thanks for all the suggestions!  With the source of emacs, that might be a solution!

Nevetheless, to expand the problem, standard terminal windows in Gnome or KDE have neither Mouse-3 bound for their scroll bars!  This make me think that it is a Linux X11 problem!  Ater all, these two window systems were to be similar to Macintosh and Windows XP, respectively!
Have a nice weekend.

---

### Post by Vox754 on 2010-04-30
> **soborobo said:**
> ...

Correct scrolling activity in a window:

I will not re-describe above correct behavior!  **A left-click in the scroll-bar will scroll down the window the amount relative to the top of the visible window port.**  So, if you click near the bottom of the scroll-bar the window scrolls down one page!  If you do the same near the top of the scroll-bar then only a few lines are scrolled down.

**A right-click** in the scroll bar currently does nothing! :mad: Its operation should be the **opposite of the left-click**, basically scrolling up the window port based on where in the scroll-bar it is activated.  If you scrolled down with a left-click, then a right-click at the exact same position will return the window to the same position that it was at before that initial left-click!
...
I really don't understand the problem.

I mean, that "correct scrolling" described is the way Motif-like (Lesstif, Xaw, Athena) toolkits used to work in the far past. It's not the way the modern toolkits like GTK and QT, and Windows work.

To me it is was totally counter-intuitive when I first used "xdvi" or "xawtv".

The fact that the modern Gnome and KDE terminals only scroll with the left mouse is just normal. And scrolling with the scrollwheel is normal too.

Again, I don't understand the problem, I feel like the OP is asking "Why is this thing not working like it used to 20 years ago?"

---

### Post by soborobo on 2010-04-30
That simply means that it is completely counter intuitive !

Now with Gnome and KDE, one will have to move the mouse  up the scroll bar just to do a simple click! [http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif) This must surely cause an increase in carpal tunnel syndrome!  I wonder what the statistics are! [http://ubuntuforums.org/images/smilies/icon_eek.gif](http://ubuntuforums.org/images/smilies/icon_eek.gif)

---

### Post by Vox754 on 2010-04-30
> **soborobo said:**
> That simply means that it is completely counter intuitive !

Now with Gnome and KDE, one will have to move the mouse  up the scroll bar just to do a simple click! [http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif) This must surely cause an increase in carpal tunnel syndrome!  I wonder what the statistics are! [http://ubuntuforums.org/images/smilies/icon_eek.gif](http://ubuntuforums.org/images/smilies/icon_eek.gif)

Seriously, dude. Are you messing with us? Have you been hiding behind a rock for 20 years using an old Unix workstation?

That's the way all modern GUI toolkits work. Never used Windows or Mac? It's the same.

By the way, I don't understand why you decided to put the smilies with the entire URL. Seriously, do you even know how to use a modern computer?

---

### Post by soltanis on 2010-04-30
Now now.

---

### Post by soborobo on 2010-05-03
Hi Dude!

> **Vox754 said:**
> Seriously, dude. Are you messing with us? Have you been hiding behind a rock for 20 years using an old Unix workstation?

That's the way all modern GUI toolkits work. Never used Windows or Mac? It's the same.

By the way, I don't understand why you decided to put the smilies with the entire URL. Seriously, do you even know how to use a modern computer?

Well, I would not call it under a rock, but on top of a big mountain watching the desolation around :D

If all modern GUI are like this, what a shame that on every major turn of computer evolution there are some new features, but always major losses. :(

The best windows were done by the good people at Xerox PARC!  You do know that _they_ invented windows!  Back then, even one of their slow machines could beat out the much faster Sun X11 windows!  Macs came next with their one button mouse!  Can't get things right on the first try...! And MS could never get the subject right; and they don't even know how to simply draw windows, but then looking at the number of years of evolution between Windows 3.1 and Windows 7, makes one shudder.  The tons of software that requires a super fast processor, only to see that Windows still takes approximately the same time to boot! :(

It just depends on where one clicks to add a smiley!  I would call that a bad web page design, but that is not today's subject.

As they say, have a nice day.

---

### Post by ThomasU on 2010-05-16
This is an annoying emacs bug. Until a new emacs23 package that is based on a version later than 23.1+1-4ubuntu7 you'll have to compile emacs from CVS.
See also:
[https://bugzilla.redhat.com/show_bug.cgi?id=543046](https://bugzilla.redhat.com/show_bug.cgi?id=543046)
[http://emacsbugs.donarmstrong.com/cgi-bin/bugreport.cgi?bug=4870](http://emacsbugs.donarmstrong.com/cgi-bin/bugreport.cgi?bug=4870)

---

