---
title: "Windows Switcher vanishing content"
date: 2011-12-09
forum: New to Ubuntu
---

### Post by jermza on 2011-12-09
The longer I have 11.10 running, the more it feels like it's falling apart.

Besides the launcher tooltips and dash appearing behind open applications, when I click on Window Switcher, it shows me my 4 desktops with applications in them. Suddenly - and this is new - when I move apps between the desktops, whatever is currently open on those desktops disappears until I release the moved application.

So, if I drag my Empathy chat conversation from Desktop 1 to Desktop 2, whatever is open on Desktop 2 vanishes until I release the mouse button.

This seems to have happened in the last day or two, and hasn't happened before.

Does anyone else also get this?

---

### Post by beew on 2011-12-09
Don't know how you move applications from one desktop to another, I use the cube to switch desktop and moving windows around with the cube is not working in 11.10.
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/876198](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/876198)

Yeah, 11.10 is very buggy, the more you explore the more bugs you discover, it is hardly a day without me stumbling on something that doesn't work in 11.10 when I was testing it for a couple of days. It is a joke to call this a stable release (and Unity should be people's least problem even though everyone is arguing over it) I am glad that I only give it a 10G test partition while my work machines are natty(with Unity) and Maverick.

---

### Post by jermza on 2011-12-12
I use Unity's "Workspace Switcher" launcher, which opens the 4 workspaces from a distance. If you have more than one application open in any workspace, and you click on one of them, then all other open windows / apps in that workspace vanish on mouse-click.

This didn't happen a few updates ago.

Are you able to replicate this? And any idea why it happens? It's messy and pointless.

---

### Post by jermza on 2011-12-12
I've just seen what I think may be the cause.

In Gnome-Tweak, I turned off "have the file manager handle the desktop". Once I turned it back on, this issue seems to have resolved itself.

Can I ask anyone else to confirm this before I mark this thread as solved?

---

