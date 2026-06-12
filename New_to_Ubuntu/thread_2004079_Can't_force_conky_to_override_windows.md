---
title: "Can't force conky to override windows"
date: 2012-06-15
forum: New to Ubuntu
---

### Post by slavssn on 2012-06-15
Hello,

I am obviously aware that this is quite a common issue, but after doing some research I did not found any satisfying solutions. So, here I am in a newbie corner where someone hopefully can help me.

As for my .conkyrc, it is fine, so let's focus on **own_window_type** line. These are the results of changing it:

**normal** - conky works fine until I click on the desktop - then it is gone forever
**desktop** - again, everything is fine, but showing the desktop (Super+D) hides it
**panel, dock** - it won't hide, but looks ghastly and always stays in top left corner even though I set it in top right corner

**override** - conky won't start at all, all I get is a warning message like this:
```
Conky: desktop window is root window
```
So, I figured maybe to add this in sudoers file (the path to conky is valid):
```
ALL   ALL=NOPASSWD:/usr/bin/conky
```
And then run it like this:
```
sudo conky -c ~/.conkyrc
```
...but it did not start as well.

Help.

EDIT: I forgot to mention that what I want from my conky is, to just stay always on my desktop whatever I click, just like some folder icon.

---

### Post by NoTryDO on 2012-06-15
[own_window_type]("http://conky.sourceforge.net/config_settings.html") - **if own_window is yes**, you may specify type         normal, desktop, dock, panel or override *(default: normal).*

**Desktop** windows are special windows that have no window         decorations; are always visible on your desktop; do not         appear in your pager or taskbar; and are sticky across all         workspaces.

**Panel** windows reserve space along a desktop         edge, just like panels and taskbars, preventing maximized         windows from overlapping them. The edge is chosen based on         the alignment option.

**Override** windows are not under the         control of the window manager. Hints are ignored. This type         of window can be useful for certain situations.

---

### Post by slavssn on 2012-06-15
No offence mate, but it's not particularly helpful what you've written. I had read [this manual]("http://conky.sourceforge.net/config_settings.html") thoroughly enough.

---

### Post by NoTryDO on 2012-06-15
> **slavssn said:**
> No offence mate, but it's not particularly helpful what you've written. I had read [this manual]("http://conky.sourceforge.net/config_settings.html") thoroughly enough.

I did not see where you said you had read it.

```
Conky: desktop window is root
```is normal

```
 sudo conky -c ~/.conkyrc
```not require

You say conkyrc is ok but do not show it.  Hard to tell what problem is.

[LIST=1]
[*] Are you using composite manager?
[*] What desktop manager?
[*] Conky version?
[*] Can you show conkyrc?
[*] In a terminal & show results of:
[/LIST]
     ```
conky -DD
```

---

### Post by jmfal on 2012-06-15
In the Tips and Tutorials section of the forum is a tutorial on how to set up conky I think there is a command or something to add to your startup script to stop it from disappearing.

Also in the Community Cafe is the ::: "Post your Conkyrc" thread , somebody there can help you for sure.

---

### Post by NoTryDO on 2012-06-15
Good advice ... better there.

---

