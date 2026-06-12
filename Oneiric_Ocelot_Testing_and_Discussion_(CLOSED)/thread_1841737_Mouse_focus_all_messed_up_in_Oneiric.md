---
title: "Mouse focus all messed up in Oneiric"
date: 2011-09-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by SheamusPatt on 2011-09-10
I've recently upgraded my Natty install to Oneiric Beta 1, and picked up lightdm along the way. I was already using Unity (which I'm still using). I'm finding that which window the mouse is focused on is now quite unpredictable. It should, of course, be the topmost window but often the window that will react is somewhere down the stack.

Here's an example. I've brought Terminal on top of Evolution using Alt-Tab (as the Dash is also often unresponsive to the mouse). I've hovered over the title bar, which happens to be over the Send / Receive button in Evolution (though it's complete obscured by the Terminal window). You can see Terminal in the attachment. Note the mouse-over, which was displayed by evolution even though the mouse is over the terminal window.

I'm not sure whether this is something in lightdm, unity, X or something completely different. I didn't see anything similar in the forum either, so perhaps it's obscure.

Any guesses? Quick tricks to fix it? 

Thanks.

---

### Post by RomeReactor on 2011-09-10
Sounds like one of these two bugs:

[Windows are click through after restore from minimize]("https://bugs.launchpad.net/unity/+bug/834034")

Or, more likely:

[Window titlebar is click through after raising a minimized window]("https://bugs.launchpad.net/unity/+bug/840285")

---

### Post by Yfrwlf on 2011-09-10
Maybe related to my bug here too, getting all KINDS of window focusing problems, it's a nightmare using my desktop:  [https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/762058](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/762058)

---

### Post by effenberg0x0 on 2011-09-11
There's a fix committed, pending approval. An update to unity will be released soon. You can see the code change (diff) linked to the bug report, so if if you feel like it, you can patch and compile unity. Beware it is a painful process (too many dependencies).

Regards,
Effenberg

--------------------------
Ubuntu Oneiric is Beta 1. It is expected to not work 100% and is  not  what I would personally recommend for anyone that just needs to get  the  job done. It's aimed at beta testers and people that can afford to   have a broken PC right now. So PLEASE: DO NOT attempt any of the   mentioned procedures if you're working on a server / production machine,   if you don't have backup of your data or if you don't have the habit  of  performing fixes in Ubuntu / Linux distros. You can end up having to  do  a new install from scratch. I can't be held responsible for any  damage,  ok? :smile:

---

