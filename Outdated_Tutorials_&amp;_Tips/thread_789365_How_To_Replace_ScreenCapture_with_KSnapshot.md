---
title: "How To: Replace ScreenCapture with KSnapshot"
date: 2008-05-10
forum: Outdated Tutorials &amp; Tips
---

### Post by AlanB66 on 2008-05-10
On Windows I've become quite happy with Snag-It. In searching for something comparable on Ubuntu, I've found KSnapshot.

I miss the Ctrl-Shift-P shortcut to launch the application, so I've decided to get Fn-PrtSc to launch KSnapshot. Maybe you will find this more to your liking ...

1. Use the Synaptic Package Manager and install 'ksnapshot'
2. Open a Terminal window, after 'ksnapshot' is installed
3. Type the following commands:
[INDENT][I]cd /usr/bin
sudo mv gnome-screenshot gnome-screenshot.orig
sudo ln -s ksnapshot gnome-screenshot[/I][/INDENT]

Now, when you press Fn-PrtSc, KSnapshot will be launched.

The only downside is ... if you're trying to get a screen capture for something going on at that very moment - something that's possibly fleeting fast - this won't be good for you.

But, KSnapshot offers window-under-cursor, section-of-window, screen, and region capture capabilities.

Hope this helps. :)

---

### Post by quadra on 2009-04-19
Great! Thanks. I also installed KolourPaint, faster and easier than Gimp for editing the screenshots.

---

### Post by jure1873 on 2009-07-23
Thanks! Really useful now that I have two monitors and gnome snapshoot only captures both screens.

---

