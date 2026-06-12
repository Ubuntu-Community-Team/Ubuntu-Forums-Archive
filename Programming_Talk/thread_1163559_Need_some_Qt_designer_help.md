---
title: "Need some Qt designer help"
date: 2009-05-18
forum: Programming Talk
---

### Post by Vadi on 2009-05-18
If anyone here is a Qt layout expert, speak up. I have this *very weird* scenario where different widgets are behaving to the *same* sizing options *differently*. It's driving me mad.

Here's how the interface looks stretched out. More or less alright:

[[img]http://www.ubuntu-pics.de/thumb/14607/screenshot_100_027__gEWV8Y.png[/img]](http://www.ubuntu-pics.de/bild/14607/screenshot_100_027__gEWV8Y.png)

Here is how I scale it down minimum:

[[img]http://www.ubuntu-pics.de/thumb/14608/screenshot_100_028__EWaHOn.png[/img]](http://www.ubuntu-pics.de/bild/14608/screenshot_100_028__EWaHOn.png)

Problems: the yellow box of pattern list is *bigger* than it's parent. I tried setting both to any combination of options, but it still is like that. It makes no sense.

Add/edit pattern field  and buttons become too small. In this attempt, all 'vertical' fields are set to 'fixed'. I tried 'preferred' before, expanding, etc - seems to work on some, not on others.

Right now on fixed, it seems that just the name & send a command field along with pattern type look decent. The pattern list, add/edit pattern, and the tab area all go below their good minimal size.

Can anyone help? Attaching the file in case a good soul can help me get rid of my misery :(

---

