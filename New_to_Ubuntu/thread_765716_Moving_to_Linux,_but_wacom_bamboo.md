---
title: "Moving to Linux, but wacom bamboo?"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by welldone101 on 2008-04-24
Hey all,

     I'm contemplating trying out this Ubuntu thing.  However, I mostly use my computer for internet, word processing, and drawing.  I have looked and looked to see if Hardy Heron supports the Wacom Bamboo tablet and every thread that I have found is completely unintelligible to me.

If you were to hazard a guess for me, do you think it would be possible for a complete beginner to get this tablet working like it does in Windows?  My level of programming is about zero, and when I read the threads there's basically nothing I understand.  I do have a vague idea of what a driver is.

How long would you guess it would take me to learn how to set it up once I started digging in.  If it'll only take a few days then I might consider finally making the switch (I'm sure the tablet will be the only problem I have, since it seems that Firefox and OpenOffice work just fine, eh?).

Thanks,
Welldone101

---

### Post by Bodsda on 2008-04-24
I dont know of this tablet you speak of but i can hazard a guess -- if you were to try on your own, i think it would take a few months to get it working, however if you embrace the forums and irc then this tablet malarky could 'probably' be sorted in a couple of hours 'max'

Now that was no disrespect to you just that was the time frame it took be to be fairly confident with the switch,.,. have fun

---

### Post by welldone101 on 2008-04-25
> **Bodsda said:**
> I dont know of this tablet you speak of but i can hazard a guess -- if you were to try on your own, i think it would take a few months to get it working, however if you embrace the forums and irc then this tablet malarky could 'probably' be sorted in a couple of hours 'max'

Now that was no disrespect to you just that was the time frame it took be to be fairly confident with the switch,.,. have fun

Thanks for the advice.  Yeah of course I didn't mean that I would try to get it running on my own.  I meant by using the forums.  The only problem being of course that when I ask "can you point me toward this file I'm supposed to edit" nobody is able to tell me in a way that navigates me to the file :confused:

Last time I tried I spent a few days even trying to install linux and every kind-hearted soul that tried to help jumped miles over my head.

---

### Post by neko18 on 2008-04-25
I began a thread a few hours ago with instructions to install the Wacom drivers. I admit they are troublesome and I can't promise you'll be able to get your tablet to work. I'm willing to help anyone with their tablet though.

The thread is located at: [http://ubuntuforums.org/showthread.php?t=765915](http://ubuntuforums.org/showthread.php?t=765915)

If the instructions are too confusing, please post a reply in that thread and I'll try to improve my instructions.

---

### Post by welldone101 on 2008-04-25
> **neko18 said:**
> I began a thread a few hours ago with instructions to install the Wacom drivers. I admit they are troublesome and I can't promise you'll be able to get your tablet to work. I'm willing to help anyone with their tablet though.

The thread is located at: [http://ubuntuforums.org/showthread.php?t=765915](http://ubuntuforums.org/showthread.php?t=765915)

If the instructions are too confusing, please post a reply in that thread and I'll try to improve my instructions.

Thank you I am definitely going to make the leap after reading your thread.  Exciting!!

---

### Post by apienk01 on 2008-04-25
I'm using Wacom Bamboo on Ubuntu. Works great - stylus, eraser, wheel, pressure sensitivity, and all the rest - but did not initially. When I first plugged in, it turned out that Ubuntu Gutsy Gibbon doesn't support Bamboo, so I had to download, compile and install updated drivers. I believe in Hardy Heron this shouldn't be a problem because the drivers are already updated. I also had to manually edit /etc/X11/xorg.conf to comment out some lines enabling tablets (don't know if it is necessary in Hardy Heron). The second thing you should know is the function keys (FN1 & FN2) do not work initially, because by default they are not bound to any commands. You can easily bind them to anything in tablet preferences.

One more note: if you hotplug Bamboo exchanging it for an USB mouse, it works in mouse mode, which means the cursor doesn't jump to the point you touch with your pen. The way to solve this quickly is to restart X Windows system by pressing Ctrl-Alt-Backspace.

Bamboo works like a charm in GIMP, Inkscape and Xournal.

Have fun!

---

