---
title: "scale function on launcher icon (window picker on window group) broken or changed?"
date: 2011-07-18
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by mc4man on 2011-07-18
The previous behavior, default in natty and earlier O, was to pick all windows from all workspaces of the icon's window group inc. minimized
The current is to only pick from current workspace if more than one.

Curious if it's known as an intended change or a temp break.
In natty there were opposing views, (and confirmed bugs) on what should be the behavior.

This one seems to pull the most weight (John Lea ) though no fix released
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/689733](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/689733)

This one was when the function temp broke on natty, there was no indication the behavior was unintended to be otherwise
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/707214](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/707214)

I prefer the behavior as seen in natty though get the feeling that it's not to be anymore, though with the exception of John Lea not sure anyone else was/is clear on what it should be

---

### Post by mc4man on 2011-08-17
Myself would still find it interesting to know if this is coming back or not, several attempts to get some real info have come up short.
(askubuntu, some new bugs, some old, existing

What brought it back to mind other then not working is I see that in unity-2d, while it doesn't use scale, this function works fine..
A direct new bug, not expecting much
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/811744](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/811744)

An indirect new bug .. 
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/820639](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/820639)

---

### Post by mc4man on 2011-08-17
Finally did get a straightforward answer, window picker on window group is dead and buried, too bad.
As far as unity-2d where it still does work, sooner or later the same..

---

### Post by mc4man on 2011-09-01
What's interesting here is that in the new unity release it's now back to the superior behavior of picking from all workspaces.
In the various bugs linked above it was said that the current workspace only was and is the design and intent.
So by and large I give up, hopefully it remains from all WS's.

The latest direct bug on this which was marked invalid as in - too bad, this is the design
(I've changed it's status to see if any response develops
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/811744](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/811744)

---

