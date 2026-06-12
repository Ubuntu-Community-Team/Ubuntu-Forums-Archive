---
title: "»Take a break« keyboard option alternative"
date: 2011-10-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Matyy on 2011-10-07
There used to be an option in the gnome-keyboard-settings that could force the user to take an x minutes break after y minutes of work. This is one of the things that seem to be abandoned. Is it gone or somewhere else? I know it was a strange place for it…

If it's really gone, does anybody know an alternative? 

there is »workaholic« which doesn't seem to be configurable at all and you can postpone the breaks, or even cancel them, which is no use at all.

Thanks in advance

---

### Post by phetre on 2011-10-07
I've had the same problem. [Workrave]("http://www.workrave.org/") is pretty good, but it was deleted from Debian (and hence Ubuntu) for being a GNOME 2 panel app: [http://us.generation-nt.com/answer/bug-642514-workrave-gnome-panel-applet-crashes-help-204881181.html]("http://us.generation-nt.com/answer/bug-642514-workrave-gnome-panel-applet-crashes-help-204881181.html").

The old GNOME typing break app has been [split into a separate package called 'drwright']("http://blog.melchua.com/2011/07/11/drwright-gnome-native-typing-breaks-in-gnome-3/"), but it doesn't seem to be available for Ubuntu yet. And someone points out on that discussion that it might not be compatible with GNOME 3.2 anyway.

Sorry I couldn't be any more help. The search continues.&#8230;

---

### Post by Matyy on 2011-10-07
Thank you, I just found out that it's called  »Typing Break« in english, and so I got more answers. Well I will go back to 11.04 than, right now I'm writing a lot and this function was very useful.

---

### Post by Matyy on 2011-10-07
Well I tried both of your suggestions, sadly I cannot get any of them to compile, I guess we just have to wait a bit more.

drwright is missing* X11/extensions/scrnsaver.h *and I don't know where to get that from. 

workrave is telling me »*configure: error: X RECORD extension headers files required on Unix platform*« which I can't find any solution for either.

Thanks anyway, if anybody knows something new, please tell us! :)

---

