---
title: "remote connections"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by jmd9qs on 2008-09-19
hi all,

i recently purchased one of those gNetbooks running gOS (which is basically just Hardy, from what i've read). at any rate, i would like to use this laptop to connect to my desktop at home, which is also running hardy. i've done a few google searches and found that ssh is probably the best solution, but i have no idea how to implement it...

does anyone have any other solutions? or can you help me figure out how to use ssh?

**side note** i'm doubting that any of these solutions will enable me to use my desktops GUI, but if it is possible, i'd like to learn how to do that as well.
thanks

---

### Post by grashdur on 2008-09-20
Hi, I'm just starting out with this too, and since nobody has answered you yet I'll share what little I know: It looks like this is easier to do with Hardy Heron because the menu items are now so straightforward: To enable remote login onto your computer, System > Preferences > Remote Desktop. At this point you can also set password, and determine whether to allow login only from inside your local network. To log in to your computer remotely, Applications > Internet > Remote Desktop Viewer. This should show you remotely the complete actual GUI of the target desktop. 

That's basically what I know so far. I intend to work on this myself in a couple days. I know there are other ways, but this looks like the easiest. In case you want to log in remotely from Ubuntu onto a Windows computer, there is a little chapter on how to do this in a book called "Ubuntu Linux for Dummies" -- I just happened to leaf thru it at my local public library and this looked like the only useful piece of info in the book. (You can only set up to log in remotely to a Win Professional edition system, not to Win Home).

Also: For reasons of security, you might want to disable remote login to the target computer whenever you expect to not remote-login for a while.

---

### Post by Liolikas on 2008-09-20
SSH takes time to learn but it is very useful Linux/MAC OS/BSD feature. Look here tutorial:
[http://p25ext.lanl.gov/ssh/ssh-howto.html](http://p25ext.lanl.gov/ssh/ssh-howto.html)

---

