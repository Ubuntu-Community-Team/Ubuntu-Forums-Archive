---
title: "c++ grab keyboard input from anywhere"
date: 2008-08-29
forum: Programming Talk
---

### Post by Tatty on 2008-08-29
At best i would describe myself as an enthusiastic amateur when it comes to programming, so please feel free to pre-assume that i do not know what i am talking about. :)

I am trying to write a small background service that listens for a hot-key sequence (say ctrl+super+F1) and then loads a set list of software associated with that. For example ctrl+super+F1 could load firefox + amsn,  and ctrl+super+F2 could load Anjuta, Glade and firefox.

What sort of strategies should i be looking into to get the Hot-Key functionality working? 

At first I was looking at XGrabKey() or XSelectInput() as a method to do this, but then i realised that each key listen was tied into a specific window, whereas i want this to happen at any point and from any window.

I was reading a suggestion to a similar problem on another forum that hot-keys are usually associated with window managers, and perhaps the hotkeys would need to be registered with the relevent window manager.  But I am not sure how to go about this.

Many thanks.

---

### Post by samjh on 2008-08-30
Interesting problem.

If you're programming for Gnome, try the key snooper capability:
[http://library.gnome.org/devel/gtk/stable/gtk-General.html#gtk-key-snooper-install](http://library.gnome.org/devel/gtk/stable/gtk-General.html#gtk-key-snooper-install)

I can't give guarantees it will work, as I know nothing about Gnome programming. ;)

---

### Post by Tatty on 2008-08-30
Many thanks for your reply samjh.

Unfortunately the documentation for those functions isnt very detailed, although after much experimentation im beginning to get the impression that these keys are tied in with specific windows also, so it seems they are not going to yeild the results I am after.  :(

At least I have learned a lot about gtk programming though :)

Im stumped now on this issue...

---

### Post by samjh on 2008-08-31
I think you'll need assistance from subject experts for this one. :)

Perhaps try posting the question on X.org's mailing lists:
[http://www.x.org/wiki/XorgMailingLists](http://www.x.org/wiki/XorgMailingLists)

---

### Post by Tatty on 2008-08-31
Lol, I thought this would be a nice simple project too :)

Many thanks samjh, ill try asking on that mailing list.

---

### Post by Moezzie on 2008-08-31
What your looking for is something called a "Global keyboard hook".   I was trying to acomplish one in c++ for a while back, with no success.
I dont think its very hard, i just didnt find any good documentation on the subject yet. At least not for Unix.

I looked though the source code of some project wich acomplished a hook though working C together with X. I dont remember the name of the software though.

If you find something usefull, plese post it here.
Good luck mate!

---

