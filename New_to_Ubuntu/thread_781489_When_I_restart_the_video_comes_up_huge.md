---
title: "When I restart the video comes up huge"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by captgadget on 2008-05-04
and then I reset it to 1280X1024 in Screens and Graphics, but when I restart it looses the settings. Anyone else having the problem?

---

### Post by imasickboy on 2008-05-04
Nvidia? 

If so, be sure you have nvidia-settings installed. It's in the repos. Then open nvidia-settings with sudo, make your changes there, and click "save to X configuration file". Restart, and it should be fixed.

If you're not using nvidia, I can't help you.

---

### Post by captgadget on 2008-05-04
The video is an onboard VGA Compatible Controller: VIA Technologies, Inc Unichrome Pro IGP (REV01)

---

### Post by SunnyRabbiera on 2008-05-04
did you try the screens and graphics application?
I know I had similar issues to this myself, the screens and graphics application is hidden so to unhide it right click your menu and select "edit menus"
then go down to "other" and in that go to the screens and graphics app and just left click the little box next to it.
this might help you determine your issue, if the system detects your card then it should be a non issue (in the second tab you can ensure that its picking up your card, even if it comes up generic thats fine too)
in the first tab you might have to change your monitor model, like if it says plug in play you may have to toy around with it a bit.
what is the maker of your monitor?

---

### Post by captgadget on 2008-05-04
Solved

---

### Post by starcannon on 2008-05-04
> **captgadget said:**
> Solved

Which post, or how did you solve it, I'm working with a VIA chipset here on a cloudbook, and any information is valuable to me at the moment.

Thanks, and grats on solving.

---

### Post by |{urse on 2008-05-04
god i love it when that happens... good job guys.

>  captgadget
Gee! These Aren't Roasted!
 
Join Date: Nov 2006
Posts: 217 <----
Thanks: 0  <----
Thanked 0 Times in 0 Posts <---- 

maybe he doesnt know that in order to thank someone he must click on the blue ribbon>?
So useful for determining which post lead to a solution =/

---

### Post by SunnyRabbiera on 2008-05-04
> **captgadget said:**
> Solved

did I help?

---

