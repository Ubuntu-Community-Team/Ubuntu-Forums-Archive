---
title: "Move top panel icons in Unity?"
date: 2017-02-22
forum: New to Ubuntu
---

### Post by Joe_Martin on 2017-02-22
Is there an easy way to do this?

Hoping I can realign top panel and I am stumped so far.

---

### Post by deadflowr on 2017-02-22
It's not possible to move the icons around from one side to the other in unity.
But it is possible to move the icons around within the area that they sit (the indicator icons on the right)

To do this you simply edit the corresponding icon's indicator file in /usr/share/unity/indicators.
Change the [Indicator Service] sections Position = #.
(Position runs from right to left, so 10 is the point at the farthest right on the screen, and 100 (or more?) would be farthest left on the screen.
Note that the positioning left can only go so far)

This is the easiest way as far as I know, unless there is an app plugin in some tweak tool somewhere.

Caveat is you may want to backup the folder after you finally set it how you want, as in case the rare unity update happens, the update may overwrite your settings.

Not sure if that's what you want, probably not, but anyway there it is.

---

