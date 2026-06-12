---
title: "[SOLVED] Xfce on the Olpc XO"
date: 2008-02-13
forum: Other OS Talk
---

### Post by EnergySamus on 2008-02-13
Hi!
I want and know how to install Xfce on the XO. Here is a link that I found very helpful:

[http://bc.tech.coop/blog/080130.html](http://bc.tech.coop/blog/080130.html)

My only problem is: Once you install it, is there a way to get back to the default SUGAR interface? And if so, how? 

Thank you!
EnergySamus

---

### Post by santiagoward2000 on 2008-02-13
> **EnergySamus said:**
> Hi!
I want and know how to install Xfce on the XO. Here is a link that I found very helpful:

[http://bc.tech.coop/blog/080130.html](http://bc.tech.coop/blog/080130.html)

My only problem is: Once you install it, is there a way to get back to the default SUGAR interface? And if so, how? 

Thank you!
EnergySamus

Hi!
Well, I haven't used the Sugar UI, but most of the times, you can click on Session when you log in and choose the UI you want. Perhaps you can find it there.

---

### Post by EnergySamus on 2008-02-14
You are talking about Xfce when you say "Session"... right? I have never seen a session in Sugar!:lolflag:

EnergySamus

---

### Post by santiagoward2000 on 2008-02-14
> **EnergySamus said:**
> You are talking about Xfce when you say "Session"... right? I have never seen a session in Sugar!:lolflag:

EnergySamus

Well... yes. I haven't ever used Sugar, so I don't know. :confused:

---

### Post by kerry_s on 2008-02-14
well, according to the instructions in that link, it's using .xsession to start xfce4, so removing .xsession should allow the normal gui to boot or changing the "exec startxfce4" to start sugar "exec sugar?", try looking in "/usr/bin" or check that ".xsession-example" for the command that starts sugar.

---

### Post by EnergySamus on 2008-02-14
Thanks for telling me! I haven't installed it yet, but if I don't like it I will just delete the xsession file. 

Once again, thanks!
EnergySamus

---

### Post by EnergySamus on 2008-02-15
... By the way, how DO you get to the xsession file?:lolflag:

Thanks!
EnergySamus

---

### Post by kerry_s on 2008-02-15
> **EnergySamus said:**
> ... By the way, how DO you get to the xsession file?:lolflag:

Thanks!
EnergySamus

it's a hidden file, open up your file manager and press ctrl+h or look in the menu for "show hidden"

---

### Post by EnergySamus on 2008-02-15
Thanks!

---

