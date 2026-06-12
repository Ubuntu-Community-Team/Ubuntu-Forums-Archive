---
title: "Glade - embed a program into another?"
date: 2006-03-26
forum: Programming Talk
---

### Post by zachtib on 2006-03-26
I'm working on a carputer project, and I'm building the software to run it on.  Currently, I'm building the UI using Glade

see here: [http://ubuntuforums.org/showthread.php?t=150584](http://ubuntuforums.org/showthread.php?t=150584)

in the screenshot, I have several tabs along the left side.  What I would like to have eventually, is if the user clicks the music player icon, it would launch rhythmbox inside of my program in full screen mode, so no window border, but still show the tabs along the left side so the user could switch over to say, a map and get directions somewhere while their music still plays.  then if they navigate back to the music player, it will return them to their current rhythmbox session. (in other words, it would just hide the window until they go back to it)

is any of this even plausable?

---

### Post by gord on 2006-03-26
i highly doubt it, unless you hack up the source of rythembox to maybe include a gtk plug, but even then i have my doubts. allthough im hardly a gtk wizzkid ;)

---

