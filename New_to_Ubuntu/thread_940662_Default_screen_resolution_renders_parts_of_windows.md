---
title: "Default screen resolution renders parts of windows inaccessable"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by JeremyP99 on 2008-10-07
I hope this is appropriate here; a mixture of problems I think, so I will present it as best I can. I installed the 8.10 Alpha, and have upgraded up to the present. Machine is a Dell Precision 370, with 4 gigs memory, lots of disc and 3mhz processor.

I have an Nvidia GeForce 7950GT. The display I get in Ubuntu has a maximum resolution somewhere (sorry, forgot to note it down) around 640 * 780; anyway, the bottom of many windows is obscured by the task bar (Gnome panel), so that I cannot see it or shrink the window, as I cannot suppress the task bar (unlike XP), or haven't found to)

So I am stuck, trying to install Linux drivers for the card. I found EnvyNG, which looks as it is perfect for the job and will install updates automatically.

BUT - When I open the Software Sources window, I cannot see the bottom of the window; tabbing to whatever is there (two buttons, it would seem), and then hitting <enter> does nothing. So I am unable to enable the repository with the software in, and thus I cannot install the graphics drivers, and thus I am stuck with an unusable screen presentation.

What to do? 

Regards

Jeremy Poynton

---

### Post by Paqman on 2008-10-07
EnvyNG is available in the default repos for Hardy, so you shouldn't need to add a new one just to get it. If you're using Gutsy or earlier you can just install the .deb from the Envy website and worry about updates later.

One little trick though: hold down alt and click on any part of a window to drag it.

---

### Post by JoshuaRL on 2008-10-07
Use your Alt button and grab the windows to move them around the screen.  That should be a temporary fix until you get the right drivers installed.

Alt+grab.  A wonderful thing.

---

### Post by JeremyP99 on 2008-10-07
Thanks guys; I'll see that happens and report back. According to the guy who wrote EnvyNG, it is in a "Universe" repository, which I have to add, and this is what I could not do. Will go and see how to get software from an existing repository, and see also if I can shrink the window after moving it; not being able to address the bottom of the window meant it could not be shrunk. 

Cheers

---

### Post by Paqman on 2008-10-08
> **JeremyP99 said:**
> According to the guy who wrote EnvyNG, it is in a "Universe" repository, which I have to add

Universe is one of the official Ubuntu repos. All you have to do is go to Software Sources and tick the box marked "Community maintained Open Source software (Universe)"

---

