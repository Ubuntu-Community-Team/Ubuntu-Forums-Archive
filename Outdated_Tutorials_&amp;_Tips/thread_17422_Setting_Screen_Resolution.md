---
title: "Setting Screen Resolution"
date: 2005-02-28
forum: Outdated Tutorials &amp; Tips
---

### Post by Thanatos9602 on 2005-02-28
I searched on how to get my screen resolution to stay at 800x600. I kept reading about how to make it larger. Most dealt with Hoarty & I use Warty. I finally decided to try to solve it myself, before asking. I didn't have '/etc/X11/xorg.conf', so I did a "sudo gedit /etc/X11/XF86Config-4". I went through it & deleted all the settings higher than '800x600' & saved it. I rebooted & "Perfection!!". Screen was the size I wanted it. All My background pics are made for that size & it's easier to read everything at that size. I guess I'm getting a little more advanced than a newbie. What's the next step up?? I'm still far from the power-user I am in Win/DOS, but I'm learning. So if anyone else has problems with it not displaying the proper settings, just delete all but the ones you want. Just thought I'd put this up, in case someone else had a problem. \\:D/ :grin:

---

### Post by arnoct on 2005-03-02
Sadly, this doesn't work the other way around; if Linux thinks your monitor can't support a certain resolution it won't let you use it. I was using 1152x864 (or something close to that) in Windows for about a year, and all I had to do was tell Windows to let me use whatever resolution I wanted. X thinks that, since my monitor doesn't explicitly support it, I shouldn't be able to use anything higher than 1024 (although I successfully got this up to 1280...)

---

