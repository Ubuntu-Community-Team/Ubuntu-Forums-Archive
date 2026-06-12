---
title: "[Bash]find a window with specific titlebar text?"
date: 2007-12-23
forum: Programming Talk
---

### Post by threefcata on 2007-12-23
hi, i want to a bash script that opens 4 terminals with different profiles that give different window different titlebar text, depending on if a window with such a profile is open.

So i want find something that can help me find a window, taking the window's titlebar text as argument or something like that..

Does anyone have any idea how i can achieve this?

thx

---

### Post by Trumpen on 2007-12-23
You can use *xwininfo* to display windows properties and then filter them with grep/awk so that you can check if your title is already used.

Here is an example of how to print the title of the currently opened terminals:

[php]yourterminal=gnome-terminal

xwininfo -root -children | grep $yourterminal | awk '{print $2}'[/php]

---

