---
title: "unable to add packages"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by Randicvs Andersonvs on 2008-08-19
I feel like an idiot, but I cannot add packages either from a c.d. or after downloading from the internet. I have set the permissions to recognise me as the owner, but when I try to extract the packages I cannot put them into the locations I want to.
Specifically, I am trying to add a Chinese language package to Openoffice so I can write in both English and Chinese. I have downloaded the data and burned it onto a c.d. as well, but I cannot figure out how to move it into Openoffice.

---

### Post by Separ on 2008-08-19
I am not quite sure what you are trying to do with these "packages". Are they in .deb format or are they .tar.gz's or what?

---

### Post by alienexplorers on 2008-08-19
Are you using the root command sudo before your untaring program or deb program.

---

### Post by AjBaz100 on 2008-08-19
If you have the deb package, use dpkg -i /path/nameofdebpackage.deb


Otherwise you should be able to install from using apt-get
In either case you must be logged in as user root, or use the sudo command.

Good luck.

---

### Post by mcduck on 2008-08-19
IF you have a working internet connection on that machine, you shouldn't even try downloading and insytalling things by hand. Just use the Synaptic Package Manager (and/or other package management tools available in Ubuntu, like the Add/Remove..-thing in the applications-menu). These tools will download & install all the software for you.

[How to install ANYTHING in Ubuntu]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by lyni on 2008-08-19
if you go to the Synaptic Package Manager you will find Chinese applications there. all you do is click on the box and click Mark for Installation click apply and it does it for you.
it is always a good idea to check the Synaptic Manager first when you want something because it is a lot easier installing from there.
hope this helps.

---

