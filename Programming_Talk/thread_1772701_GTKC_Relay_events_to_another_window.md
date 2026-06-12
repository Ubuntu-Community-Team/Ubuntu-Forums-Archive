---
title: "GTK/C: Relay events to another window?"
date: 2011-06-01
forum: Programming Talk
---

### Post by Githlar on 2011-06-01
This is going to take a little explanation, so bear with me:

Program purpose: to record/replay actions into a Java applet

Due to complexities with how the system displays Java applets (above everything else in a window), my program has two windows - one directly overlapping the other. The bottom window uses WebKit to display a web page containing a Java applet and the top window is an invisible overlay for the bottom window so that events can be recorded that should be going into the applet, but then replayed into the applet as if the overlaying window was not there. For simplicities purposes, we can call this a keylogger. A keylogger would take note of keys pressed, but allow them to propagate into the window they are supposed to go into so you wouldn't notice it. The only difference between this and a keylogger is that it will also record mouse clicks.

I've got all of this working except for relaying the events to the bottom window. How can I take an event that's been captured in the top window and repeat the same event (in the same place) on the bottom window? For example, the user clicks at point (25,35) on the top window (but they don't know the top window is there), how can I pass that same event to the window below so that the click at (25,35) does what the user expects?

Theoretically I shouldn't even need an event handler for this (or a dummy event handler).

I managed to use g_signal_emit_by_name to "replay" a click event on the bottom window (the bottom window's dummy event handler fires), however the click doesn't happen.

After toying around with the code a bit just now, I realized that no GdkEvent is actually passed to it, perhaps that's why it isn't working? I'm not sure how I'd solve that problem though...

I'm brand new at GTK programming (and graphical programming in its entirety). Is there some subtlety between signals and events that I'm not understanding?

PS: I'll bet some of you reading this are thinking "Why not just use an EventBox?" Oh, I tried that, but even with the EventBox set to overlay children, it still does not receive events once focus has passed to the Java applet.

---

### Post by Githlar on 2011-06-01
bump

---

### Post by Githlar on 2011-06-02
Bump

---

### Post by simeon87 on 2011-06-02
If this is not shady software, how does the user benefit from having an invisible window on top of everything else, without even knowing it is there? Why do actions need to be replayed?

---

### Post by Githlar on 2011-06-02
It's simply to automate repetitive tasks. The reason that there has to be an invisible window over the other window is because of the way Java is rendered by the system - over everything else in a window. I had a Java applet inside a WebKitWebView which itself was inside an EventBox (with above children property set), but the applet still rendered over everything. Therefore the only logical conclusion to me was to place another window over the applet in order to capture what actually goes into the applet.

I make a lot of things that are purely in the pursuit of knowledge. This is something that I've been wanting to make a for a long while (several years actually) and now I have the means to do so. But like I said before, rest assured that this is purely for personal dis-use. By that I mean, once I figure it out and get the basic principles down I'll know more than (I'd assume) most people about events/signals and I can let this program sit around and gather dust. But, perhaps later I can pull from my experiences with this program and be able to apply them somewhere else.

Honestly, I don't see why I'd have to justify my motives (which, I assure you, are completely innocent) in order to get a response out of anybody. Plus, this program loads a particular web page with a particular applet in it. I made it to do what it needs to do and nothing more. The only reason I'm doing this, though, is because currently I have some global keyboard commands set that use a script and xdotool in order to achieve the same thing, but I'm trying to encapsulate those keyboard commands into a program so that they don't run the risk of interfering with normal system operations.

And just remember, when you say "the user" that means me as I'll be the only person that'll ever use this.

---

### Post by simeon87 on 2011-06-02
It's not really a common problem so I can't tell you from experience how to do this. I can imagine other people are in the same situation. It also sounded a bit shady with keylogging / mouselogging things but even with that aside, I wouldn't be able to share how to do it because I haven't tackled a problem like this before.

---

### Post by Githlar on 2011-06-02
I read a little bit more into events and signals yesterday, and it appears that events cause signals that get caught by callbabcks. So, with g_signal_emit_by_name() it seems to be skipping the whole "event" part which is probably why nothing happens on the bottom window (and why any reference to GdkEvent->[property] results in a seg fault - it's probably NULL, but I haven't checked that). So, the question is: If I created a GdkEvent object with all the necessary data (which would just be a matter of using the one from the event handlers on the top window), is it possible to throw that GdkEvent at a window (which, as I understand it, would cause a signal emission)?

Dang, I'm using parenthetical phrases like a champ today =D Hooray for offhand comments!

---

### Post by Githlar on 2011-06-02
It would appear that it's not a common problem anywhere from my Google searches. I just figured I'd try at my favorite Linux-friendly forums! Mainly because in the 15+ years I've been mastering all that is computers I have never figured out mailing lists =P

---

### Post by Githlar on 2011-06-02
Still not finding much that's GTK+ specific. I did, however, find an X extension called XTEST. Looks like it can simulate events as well, however I can't seem to find any worthwhile documentation on it. Of course, this means I'm going to have to do a little "hack" on it. I'll have to collect the click's coordinates, convert them to screen coordinates (if they aren't already), hide the invisible window (that'll cause some problems), do the action(s), and then re-"reveal" the invisible window. Well, it's a start at least. Now to find some useful XTEST documentation.

---

