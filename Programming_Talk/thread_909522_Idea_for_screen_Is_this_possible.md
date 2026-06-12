---
title: "Idea for screen: Is this possible?"
date: 2008-09-03
forum: Programming Talk
---

### Post by sq377 on 2008-09-03
Lets say I have a server at home, where I like to run several gui apps.  I use ssh -X to view them on my system.  Would it be plausable to have x11 support in screen so that I could ssh -X, then screen -r and retrieve my windows?  From what I tell if I can control the events I should be able to just say the window isn't exposed, and have it redraw it after they reconnect.

---

### Post by LaRoza on 2008-09-03
What is the programming question? If you want help with screen/ssh/X, this I can move this for you.

---

### Post by monkeyking on 2008-09-03
I tried doing this,
and it won't work.

The next best thing if you want this is to use ratpoison [http://en.wikipedia.org/wiki/Ratpoison](http://en.wikipedia.org/wiki/Ratpoison) .

never tried it though

---

### Post by slavik on 2008-09-03
you mean like VNC?

---

### Post by sq377 on 2008-09-04
> What is the programming question? If you want help with screen/ssh/X, this I can move this for you.
I'm curious if this can be conceptually done with x11, so I think it's relevant to programming.  If I hear it is possible I'll have a go at it.

> you mean like VNC?
Not quite.  Run ssh -X to another box and you can forward x11 apps over the network.  The X11 calls are all that are forwarded as opposed to bitmaps, so it's much faster.  This can forward glxgears correctly, vnc doesn't come close.  Also it integrates better with my window manager.

> I tried doing this,
and it won't work.

The next best thing if you want this is to use ratpoison [http://en.wikipedia.org/wiki/Ratpoison](http://en.wikipedia.org/wiki/Ratpoison) .

never tried it though
I'm not sure if I'm explaining what I want well.  I want to be able to detach the screen session, and have the x11 apps go with it.  Then when I reattach, the x11 apps redraw themselves on where ever I attached the screen.  Ratpoision doesn't seem to be quite what I'm looking for.

---

### Post by Rich78 on 2008-09-04
What's wrong with standard RDP protocols?

It sounds like all you need is Remote Desktop capability.  

Definitely not a programming question even if it's discussing the capabilities of X11.

---

### Post by SeanHodges on 2008-09-05
Check out teleport: [http://packages.ubuntu.com/hardy/x11/teleport](http://packages.ubuntu.com/hardy/x11/teleport). I can't find the developers website, but it's man page might help you.

As I understand it, the usual problem is that GUI applications often don't support the display migration protocol, which is required for re-attaching applications to displays that they were not started on.

RDP and VNC are heavyweight remote protocols that forward the entire display (even if you set them to only render a portion of it), I believe you're looking for something that only forwards a single *already running* application and uses something like XDMCP for transport. Teleport is designed for this.

---

