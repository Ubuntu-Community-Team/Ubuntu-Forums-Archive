---
title: "Re-sending XEvents"
date: 2011-10-29
forum: Programming Talk
---

### Post by Simme on 2011-10-29
Hey there!

I'm the main developer of Gnome-Pie ([Homepage]("http://www.simonschneegans.de/?page_id=12"), [GitHub]("https://github.com/Simmesimme/Gnome-Pie")), maybe you heard of it. While creating new features for version 0.3 I ran into a problem with no obvious solution. At least not for me.

I just want to ask for some advise --- maybe I misunderstood something...

**The problem:** I want to implement *delayed* key bindings for Gnome-Pie: When the user clicks with a bound key of his mouse (for example the middle click) somewhere on the screen, a pie menu should open. But it should only pop up if the key is hold down for a second. Else a normal middle mouse click should be executed.

**My thoughts:** I tried to implement this functionality as follows:
[LIST]
[*]use XGrabButton to grab the desired button
[*]add a filter to the Gdk Rootwindow in order to receive notifications when the grabbed button is pressed
[*]wait until the key is released - if it's to early *re-send* the previously received event, else open the pie window
[/LIST]

The re-sending part is the tricky thing: I use XSendEvent to send the received event, but nothing happens. Sending happens as follows (It's Vala, but even if you don't know Vala - it's easy to read):

```

Gdk.Window rootwin = Gdk.get_default_root_window();
X.Display display = Gdk.x11_drawable_get_xdisplay(rootwin);
X.ID xid = Gdk.x11_drawable_get_xid(rootwin);
display.send_event(xid, true, X.EventMask.ButtonPressMask, ref delayed_event);

```

**Another example:** When I grabbed the right mouse button, I want a normal context menu to pop up when the button is released. But when it is hold down for a longer period, I want to open a pie menu at the mouse.

**My questions:**
[LIST]
[*]is the above approach right? Or is there something totally wrong with it?
[*]is there a more convieniant way to capture long key/button presses?
[*]do you know another forum where this question may be more appropriate?
[/LIST]

Thanks for your help!

---

