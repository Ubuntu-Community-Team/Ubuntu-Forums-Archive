---
title: "Screen resolution problem"
date: 2013-06-07
forum: New to Ubuntu
---

### Post by epix13 on 2013-06-07
I followed a tutorial on how to change your resolution for a monitor through the terminal and this happened.

[IMG]http://i44.tinypic.com/dwditd.png[/IMG]

It looks like two taskbars and screens overlapping each other. And I'm running 12.04.

---

### Post by sum1nil on 2013-06-08
From the site: [https://wiki.archlinux.org/index.php/Xorg](https://wiki.archlinux.org/index.php/Xorg)

If a problem occurs, then view the log at /var/log/Xorg.0.log. **Be on the lookout for any lines beginning with (EE), which represent errors, and also (WW), which are warnings that could indicate other issues**.

If there is an empty .xinitrc file in your $HOME, either delete or edit it in order for X to start properly. If you do not do this X will show a blank screen with what appears to be no errors in your Xorg.0.log. Simply deleting it will get it running with a default X environment.

...

To see if your display size and DPI are detected/calculated correctly:

$ xdpyinfo | grep -B2 resolution

Check that the dimensions match your display size. If the Xorg server is not able to correctly calculate the screen size, it will default to 75x75 DPI and you will have to calculate it yourself.

...

I would read the entire page.
Best of luck.

---

### Post by firekage on 2013-06-08
i have exacly the same problem and haven't found solution yet. I assume that you have nvidia card and nvidia drivers (doesen't matter if there are from nvidia, from ubuntu repos or xorg-eadgers). I have it on every boot with never nvidia drivers even when i don't change resolution. In fact, drivers detects that i have few monitors and give them different resolution when in fact i have only one monitor - lcd screen.

---

