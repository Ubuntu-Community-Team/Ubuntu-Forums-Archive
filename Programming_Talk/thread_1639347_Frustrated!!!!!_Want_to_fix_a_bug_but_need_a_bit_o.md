---
title: "Frustrated!!!!! Want to fix a bug but need a bit of support"
date: 2010-12-06
forum: Programming Talk
---

### Post by pauljwells on 2010-12-06
There is a bug in Ubuntu's wxPython implementation. I filed a bug about menu bars not showing but there are numerous posts about keyboards not responding and other python-based programs not working properly.

How can Ubuntu not have a perfect Python?????

I want to help fix this, but I can't find who to contact,where to start what to do... :-/

I strongly suspect that it's a core problem in Ubuntu's display 'stuff' rather than a bug in wx/Python itself, but where to start?

Any Ubuntu Python admins out there?

---

### Post by Arndt on 2010-12-06
> **pauljwells said:**
> There is a bug in Ubuntu's wxPython implementation. I filed a bug about menu bars not showing but there are numerous posts about keyboards not responding and other python-based programs not working properly.

How can Ubuntu not have a perfect Python?????

I want to help fix this, but I can't find who to contact,where to start what to do... :-/

I strongly suspect that it's a core problem in Ubuntu's display 'stuff' rather than a bug in wx/Python itself, but where to start?

Any Ubuntu Python admins out there?

If so, it's a bug in Gtk. Have you tried the wxPython forum (if there is one), or the wxWidgets forum?

The language python implementation itself is probably not faulty.

---

### Post by roccivic on 2010-12-06
Try launchpad

---

### Post by dwhitney67 on 2010-12-06
> 
Frustrated!!!!! Want to fix a bug but need a bit of support

So!  I'm frustrated too that I have to peruse into a dumb-*** thread to see what it is about.  Is there anything to help me?


What I meant to say... please. next time enter a better title for your thread.

---

### Post by pauljwells on 2010-12-08
I already filed a bug on Launchpad, but I don't see any way of progressing it through there. I can't tell if anyone has even looked at it.

@Arndt - thanks for the GTK tip, I'll try there. I don't think it's a wxPython bug as such, since it works fine on all the other platforms.

@dwhitney67 - Sorry, it was intentionally a dumb title in an attempt to spread the net a bit wider. Sneaky, but my intentions are good!

---

### Post by unknownPoster on 2010-12-08
Post a link to the bug report. All we have so far is you claiming there is a bug in Python itself, which is a fairly bold claim, given it's popularity. To be honest, I'd imagine that the problem was created by you and not a bug in the software itself.

---

### Post by pauljwells on 2010-12-09
I specifically *don't* claim that it's a bug in Python, as it works on other platforms (Win and Mac, and even Ubuntu Netbook) and it works in K/Ubuntu when run as sudo.
Please let me clear up that I'm not complaining about Ubuntu! I only started this thread to try to get a bit of help to try to **fix the bug myself.** I'm happy enough coding Python and a bit of C/C++ but if I need to dig into GTK or some other complex code, frankly, I'm going to need a bit of guidance from better people... 

Good point about posting the bug though. Here it is:

[https://bugs.launchpad.net/ubuntu/+source/wxwidgets2.8/+bug/682478]("https://bugs.launchpad.net/ubuntu/+source/wxwidgets2.8/+bug/682478")

You'll see that I link to two other bugs that have been posted that show the same behaviour and one of these describes that running the wxPython demo code menu bar example shows the problem (I also tried the demo and confirm this.)

Thank for replying!

---

### Post by pauljwells on 2010-12-18
Stani, of this forum, gave me the answer. It *is* a bug in Ubuntu. The fix is to add

```
export UBUNTU_MENUPROXY=0
```

to the launch script (or to ~/.bashrc and run the app from a terminal)

---

