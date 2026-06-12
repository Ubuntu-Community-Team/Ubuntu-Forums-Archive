---
title: "can i deploy ?"
date: 2008-07-12
forum: Programming Talk
---

### Post by lucky.developer on 2008-07-12
hi all,

I like developing for linux so much... 
basically i am  a computer science student. My college wants me to do a project in my pre-final year of my computer science course. 
My colllege computers use some old version of red hat(gnome interface). I use ubuntu(gnome interface). I want to do a GUI app(using gtk+) in either c or c++.

can i develop the app in my ubuntu(gnome) machine and deploy it in my college's red hat(gnome) machines. 

what are the pro's and con's for this kinda thing... 

thanks

---

### Post by HalPomeranz on 2008-07-12
It should work find to develop on Ubuntu and deploy on Red Hat.  You may need to recompile on Red Hat, since some shared libraries may not have the same versions, but from a functionality perspective everything should be close enough that things should work.

---

### Post by lucky.developer on 2008-07-12
ok.. then.. u say that i should install those extra shared libraries on red hat for the full functionality...???
thanks

---

### Post by CptPicard on 2008-07-12
> **lucky.developer said:**
> ok.. then.. u say that i should install those extra shared libraries on red hat for the full functionality...???


Yes, sure.

Read up on autotools and create a standard GNU source package. Then based on that, if you are so inclined, you can roll your own rpm or deb binary packages for your favourite distributions. But making a GNU-style source tarball is the first step.

Mind you, autotools is the most horrible piece of crap of a collection of tools I've ever come across, but it works remarkably well regardless... ;)

---

### Post by lucky.developer on 2008-07-12
hey CptPicard... 
i am relatively new to linux ( i'm 6 months old ubuntu baby). i have just started tweaking into it...
regarding the case about GNU source package.. and similar stuff.. i know nothing..

it would be great if i could be in touch with you for more guidance through my project life cycle.

---

### Post by HalPomeranz on 2008-07-12
> **lucky.developer said:**
> ok.. then.. u say that i should install those extra shared libraries on red hat for the full functionality...???
thanks

Actually, the libraries you're using on Ubuntu (GTK+, etc) will likely already be available on Red Hat.  All you should have to do is just recompile your code on that platform so that your binary links to whatever version number of the libraries Red Hat installs by default.  It's even possible that you can just move your binary over without recompiling.

If the libraries aren't already there on the Red Hat system, it's likely that they're available from the Red Hat repos.  See this document for information on translating between Ubuntu and the Red Hat package management system: [https://help.ubuntu.com/community/SwitchingToUbuntu/FromLinux/RedHatEnterpriseLinuxAndFedora](https://help.ubuntu.com/community/SwitchingToUbuntu/FromLinux/RedHatEnterpriseLinuxAndFedora)

For Open Source software RPMs that aren't in the standard Red Hat repos see: [http://dag.wieers.com/rpm/](http://dag.wieers.com/rpm/)

---

### Post by lucky.developer on 2008-07-12
i dont know where to start.
i know c and c++ .
i want to design a gui app in ubuntu

i have no trace about this...

will somebody show me a way to learn about MAKING SOFTWARE AND DEPLOYING IT

---

### Post by Vadi on 2008-07-12
Ask your CS professor? Making a GUI app in Linux is like in any other OS - use a gui toolkit, and make the core, connect the gui widgets together, and they work. If you don't have the basics down, you'll have troubles beginning.

Try this series of guides a try, they're relatively easy to follow and understand: [http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html)

---

### Post by henchman on 2008-07-12
and have a look at the stickies in this forum. they are very informative :)

---

### Post by kknd on 2008-07-12
You must take care about the version of GTK that you will use. GTK versions are "binary-compatible", but you can't use a funcion added in GTK 2.12 on GTK 2.10 for example.

---

