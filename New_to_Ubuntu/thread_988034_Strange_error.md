---
title: "Strange error"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by fif1189 on 2008-11-20
I will first start by saying that I am brand new to unbuntu and linux in general.  My problem probably has a simple solution but I can't seem to find it.

Currently my "visual Effects" is set to "none."  Every time I try to change it it says, "Desktop effects could not be enabled."

How do I fix this?

Here are some hardware specs:

ATI Radion 4870 HD
AMD Phenom Black Edition Quad core

Is my video card the issue?

Thanks to all who help.

---

### Post by hyper_ch on 2008-11-20
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by shifty_powers on 2008-11-20
when you go to system>administration>hardware drivers what shows up?

and go into a terminal and post the output of

```
glxinfo
```

in code tags as explained above please :D

---

### Post by Dedoimedo on 2008-11-20
Hello,
It seems like your graphics drivers are not installed - and thus enabled. If you go under System > Restricted Hardware, does it show up anything, offering you to download and install drivers?
Dedoimedo

---

### Post by fif1189 on 2008-11-20
The only hardware that shows up is for my wireless internet card, which still functions fine even though it says it is restricted or something like that.

---

### Post by philinux on 2008-11-20
The default ubuntu driver gives 2d and all resolution but not 3d. I.E. Desktop effects.
Unless someone has a better idea this seems to be the way.
[http://ubuntuforums.org/showthread.php?t=878709](http://ubuntuforums.org/showthread.php?t=878709)

---

