---
title: "Talking to WM"
date: 2011-12-22
forum: Programming Talk
---

### Post by jesuisbenjamin on 2011-12-22
Hello,

I've been playing around to learn more on Window Management, so I can make some shell-like application for the desktop.

Anyway, I've dug into python-xlib, but it's a real nightmare, because 1. I am trying to make sense of ICCCM, which is much to technical for my purpose and assumes much prior knowledge, and because 2. there is no doc on python-xlib.
So I've had contacts on the mailing list, I've browsed code (like PLWM's) etc. but it's a real pain for me to do simple window management stuff like maximize, minimize, raise, lower etc.

Then I came across [Xdotool]("http://www.semicomplete.com/projects/xdotool/#id270150"), which apparently does much of what I need to make task-bar like application. I yet have to try it and wonder whether it's not going to be too heavy to go through command-line programmatically, what do you reckon?

I am wondering then if there are not more such tools out there. I'm especially looking for a python API to talk to the WM and make it do the basic stuff mentioned above.

Also is there any means to do that through d-bus perhaps?

If there was an easier tool than python-xlib it would really make my life easier.

Cheers,
Benjamin

---

### Post by jesuisbenjamin on 2011-12-22
I have found out I could use wmctrl too, but that's not a proper tool for what I want to do (mainly because it works with strings to pick up windows, rather than using their X window ID, and also because I'd require a listener for new windows popping up).

---

### Post by jesuisbenjamin on 2011-12-23
OK so I've discovered that whereas Gnome (apparently) does not offer any API, XFCE does offer [pyxfce]("http://pyxfce.xfce.org/index.php?page=overview&lang=en")!

That's really cool: since I don't really care which WM/DE the shell should be in, as long as it's efficient.

---

