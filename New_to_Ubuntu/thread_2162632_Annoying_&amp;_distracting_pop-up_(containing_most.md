---
title: "Annoying &amp; distracting pop-up (containing mostly redundant info)"
date: 2013-07-15
forum: New to Ubuntu
---

### Post by NuxNik on 2013-07-15
Hello,

I have something new for which multiple searches have provided no clue.

I have this annoying black pop-up with white text, which will sometimes post the first few lines of a post, but most of the time only repeat what is already on display.
This is NOT restricted to the browser, but appears to be OS-based (Lubuntu in my case)
The annoying thing appears in ANY window, if the cursor has been stationary for a few seconds.
In file manager if the cursor is on a file icon, it will pop-up and contain the file name which also is evident under the icon.

This nasty annoying thing is distracting.

How do I get rid of it ??

Thanks

---

### Post by CinTUX on 2013-07-16
Did you try disabling window effects?

---

### Post by NuxNik on 2013-07-30
OK ?

I tried to search for lubuntu & "window effects" but didn't find anything that would help

Where exactly do I change them ?

---

### Post by newb85 on 2013-07-30
Unless you've made changes to your system, Lubuntu should be running on Openbox, not Compiz.  I'm guessing CinTUX was referring to the Window Effects in Compiz.

I have basically no experience with Openbox, but I'm guessing these screentips are something set up there.

---

### Post by vasa1 on 2013-07-30
> **NuxNik said:**
> ...
I have this annoying black pop-up with white text, which ... appears to be OS-based (Lubuntu in my case)
The annoying thing appears in ANY window, if the cursor has been stationary for a few seconds.
In file manager if the cursor is on a file icon, it will pop-up and contain the file name which also is evident under the icon.
...
This pop-up is a tooltip. I suspect it's a feature of gtk rather than "Lubuntu". I haven't tried getting rid of it.

In /usr/share/themes/Lubuntu-default/gtk-2.0/gtkrc:
```
gtk_color_scheme = "tooltip_bg_color:#343330"
gtk_color_scheme = "tooltip_fg_color:#E6E6E6"

```
and
```
style "tooltips" {
	xthickness = 4
	ythickness = 4
	bg[NORMAL]        = @tooltip_bg_color
	fg[NORMAL]        = @tooltip_fg_color
}
widget "gtk-tooltip*" style "tooltips"

```
In /usr/share/themes/Lubuntu-default/gtk-3.0/gtk.css:
```
@define-color tooltip_bg_color #333;
@define-color tooltip_fg_color #fff;

```
I haven't tried fiddling with these codes other than to change the colors. Perhaps someone knows how to disable tooltips..


I'm not sure that Openbox has anything to do with OP's issue. Openbox is the window manager.

---

### Post by Toz on 2013-07-30
GTK-based tooltips can be disabled via creating a .gtkrc-2.0 file in your home directory with the following content:
```
gtk-enable-tooltips = 0
```
You'll need to either log out and back in again or re-load the GTK theme (not sure how that's done on lubuntu) for it to take effect.

---

### Post by vasa1 on 2013-07-30
> **Toz said:**
> GTK-based tooltips can be disabled via creating a .gtkrc-2.0 file in your home directory with the following content:
```
gtk-enable-tooltips = 0
```
You'll need to either log out and back in again or re-load the GTK theme (not sure how that's done on lubuntu) for it to take effect.
Works perfectly. I logged out rather than just changing and reloading themes. Of course, there are some programs that have their own tooltips. I suspect Firefox is one of them.

Now to try that for gtk3 apps. I wonder if settings.ini will be the thing to edit.

The file to modify (for each user) is ~/.config/gtk-3.0/settings.ini. Adding exactly the same code works.

Now to enable the tooltips! I find them very useful.

---

### Post by NuxNik on 2013-10-13
> **NuxNik said:**
> Hello,

I have something new for which multiple searches have provided no clue.

I have this annoying black pop-up with white text, which will sometimes post the first few lines of a post, but most of the time only repeat what is already on display.
This is NOT restricted to the browser, but appears to be OS-based (Lubuntu in my case)
The annoying thing appears in ANY window, if the cursor has been stationary for a few seconds.
In file manager if the cursor is on a file icon, it will pop-up and contain the file name which also is evident under the icon.

This nasty annoying thing is distracting.

How do I get rid of it ??

Thanks

Finally found the solution purely by accident
It was in thread:
   [http://ubuntuforums.org/showthread.php?t=1781320](http://ubuntuforums.org/showthread.php?t=1781320)
And the answer is:
   [COLOR=#000000]Edit the file [/COLOR][B]$HOME/.config/lxpanel/Lubuntu/panels/panel
[/B]**   Search for the string "tooltips=1" and change the 1 to 0. ****   Then restart the desktop.**

---

