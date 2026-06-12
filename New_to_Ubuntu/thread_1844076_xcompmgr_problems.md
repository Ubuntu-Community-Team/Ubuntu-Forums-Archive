---
title: "xcompmgr problems"
date: 2011-09-14
forum: New to Ubuntu
---

### Post by blade4 on 2011-09-14
Hi everyone . I just recently started using xcompmgr and have hit a few roadblocks - my windows now tend to leave residual images when I bring their size down ( not minimize , just smaller window ) from the maximise state . 

Also, if I close my terminal window on my desktop , it tends to leave a " shadow border " . The attached images will explain . 

I usually use it on the following setting 

 xcompmgr -cC

I have ubuntu l0.04.3 running on intel GMA 965 . I realise that this config essentially puts my laptop on xcomp's **** but if there is a workaround for this , I would be glad to hear it . 
Thanks in advance :)

---

### Post by kerry_s on 2011-09-14
Try xcompmgr -n

---

### Post by blade4 on 2011-09-14
> **kerry_s said:**
> Try xcompmgr -n

Thanks for the tip kerry . It solved te shadow border but I'm still having the window residual image problem ( images attached ) . In addition , now I can't seem to go back to the maximized view . Any suggestions ?

---

### Post by ShodanjoDM on 2011-09-14
How about trying cairo-compmgr? I ditched xcompmgr and use cairo-compmgr with LXDE and it works beautifully. But I still can't get shadow under fluxbox's menu with it though.

Unfortunately I can't find the ppa for 10.04 so you may have to compile yourself.

Anyway, here's the ppa that I'm using (for Natty):

[https://launchpad.net/~janvitus/+archive/ppa]("https://launchpad.net/~janvitus/+archive/ppa")

Or this for Maverick:

[https://launchpad.net/~gekkio/+archive/cairo-compmgr]("https://launchpad.net/~gekkio/+archive/cairo-compmgr")

---

### Post by kerry_s on 2011-09-14
Go into the monitor settings & adjust your hz, it's probably set to low.

---

### Post by ronniew on 2012-02-27
cairo-compmgr is way to much of a resource hog, really taking away from the lubuntu philosophy of low resources. 

cairo-compmgr uses between 20 -30 megs of ram, on the other hand xcompmgr uses between 1.2 and 5 megs of ram. Both depend on the settings and how many visual effects your using. 

Personally I understand and like a little niceness. However I do want to keep lubuntu relatively lightweight so for now xcompmgr is the right fit..

However on the horizon is Unagi,,, due to be in precise repos... not sure if this is going to be the default composite manager for the next lubuntu but maybe because screenshots suggest they are using some kind of composite manager.

well see

---

