---
title: "xubuntu on hp 2710p with AC is very slow and with battery works perfect"
date: 2014-01-20
forum: New to Ubuntu
---

### Post by aronq on 2014-01-20
Hello guys,

Hopefully somebody can help me. I installed xubuntu 12.04. and i have a problem: my cpu is 7% when its working from Battery. And when it works from AC then cpu is 50-100% and its very sloooooooow. I can't really do much. Do anybody has an idea?

Thanks a lot!

---

### Post by robin7 on 2014-01-20
I'll be watching this thread too, to learn about making Xubuntu leaner and meaner.  Two little things I know can help, and both are really easy.

Install an AdBlocker in Firefox to save some processing power on the web.  

Another way is to uncheck the Startup Applications you don't need or aren't using all the time.  **Applications > Settings Manager > Session & Startup >** click the **Application Autostart** tab.


[IMG]http://myphotos.mypclinuxos.com/images/Artim/applicationautostartmenu.png[/IMG]

My computer doesn't have Bluetooth, so why run a Bluetooth daemon, right?  And the Printing daemon is a little resource hungry, so I don't run that - when I want to print *then* I'll use it, but no need to have it running all the time in the background.  Maybe UbuntuOne could be unchecked too, as a startup application.  

I'll be watching for other replies to this thread on how to "lighten up" my Xubuntu!

---

### Post by aronq on 2014-01-20
dear Robin,

Thanks. My computer would not be slow, if it would always go from Battery. there must be something that starts when I plug in AC kabel. I found out that Xorg and gkrellm goes very high when i plug AC kabel in the computer...

any idea?

---

### Post by robin7 on 2014-01-20
I don't even own a laptop yet so I couldn't say since I'm always on AC.  But there must be a setting that lets you continue the same "graphics mode" (that's what Xorg is) even on AC power.  I bet the default is set to "transfer" but I imagine it doesn't have to be.  Try **Applications > Settings Manager > Power Manager** and explore the tabs.  "On AC" might have a setting for your computer that doesn't show up on my desktop machine.

---

