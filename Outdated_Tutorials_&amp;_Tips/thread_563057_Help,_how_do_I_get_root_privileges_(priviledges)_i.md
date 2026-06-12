---
title: "Help, how do I get root privileges (priviledges) in /var/www/ in Apache2 on my login?"
date: 2007-09-29
forum: Outdated Tutorials &amp; Tips
---

### Post by easytec on 2007-09-29
Try this:
That is too easy.
The Ubuntu Server Edition from Dapper to Gutsy Gibbon support for permission, you do this.
If you are already are using the ROOT account, which can't be accessed directly for security.
Follow these steps:
[LIST=1]
[*]Make sure your an administrator / substitute (super) user.
[*]If you are not, log in to the main account your created when you set up Ubuntu Server Edition.
[*]If you now are, go to the Administration menu in the GNOME System menu.
[*]Setup groups, put yourself into the super user / root group.
[*]Try again, if that fails reboot.
[*]Try again, it should work. If not it is advised you upgrade to Feisty Fawn or Gutsy Gibbon.
[/LIST]
(Sorry if this post is out dated, only Ubuntu Forums stick for ages)!
Any other way I should list?

By the way if you are changing the path in Apache2 YOU MUST turn Apache2 off before doing so, try Webmin to do this.

Ooops, did you think you installed Apache2 but it isn't?
You should of hit the space bar when selecting the LAMP server at setup, you can also select other modules too.
Gutsy Gibbon works great, try that!

---

