---
title: "[SOLVED] Installing software question"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by linesma on 2008-10-06
I jsut switched from Fedora 8 to Ubuntu 8.7, and I am having a minor issue.  I am trying to install packages from the add/remove dialog, and they are not found.  They are listed here:  [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
so I can download them individually.  Why are they not found in the add/remove programs.  I have also tried the apt-get command from the terminal, but it also does not work.  For example, Conky does not show up in the add/remove application, and it is not found using the sudo apt-get command in the terminal, but it is listed in the referenced website.  Hopefully it is just a noob error from not knowing this distro of Linux.

Thanks,

linesma

---

### Post by SunnyRabbiera on 2008-10-06
well lucky for you there is synpatic located under system > administration > synaptic package manager
Synaptic is like a more advanced version of add/remove, it will offer you the full list of ubuntu packages.
otherwise you can use the packages you find on [http://packages.ubuntu.com/](http://packages.ubuntu.com/) by downloading them and double clicking the installer like you do in windows to install a package.

---

### Post by bakie on 2008-10-06
Have you tried searching for it in the command line?
Try aptitude search conky and see if you get something. Then you can simply install it with sudo apt-get install conky or remove it with sudo apt-get remove conky.

Edit: Or use the synaptic thingie that SunnyReabbiera said to have a gui :)

---

### Post by DrMega on 2008-10-06
In your System->Administration menu, there should be an option called "Software Sources" which brings up a dialog. Make sure all the tick boxes are ticked, then close it and launch Synaptic. You can access the same options from within Synaptic but I can't remember how off the top of my head.

---

### Post by linesma on 2008-10-06
> **SunnyRabbiera said:**
> well lucky for you there is synpatic located under system > administration > synaptic package manager
Synaptic is like a more advanced version of add/remove, it will offer you the full list of ubuntu packages.
otherwise you can use the packages you find on [http://packages.ubuntu.com/](http://packages.ubuntu.com/) by downloading them and double clicking the installer like you do in windows to install a package.

Thanks for the reply. Ok, so when it says to install it using a "Software Channel" instead, what does that mean?  

Off-topic - Still getting used to the whole sudo vice su - thing btw.

---

### Post by Flimm on 2008-10-06
In Add/Remove Applications, there's a combo box that a lot of people don't notice, at the top, set Show to "All available applications".
Even with that enabled, you won't get as many packages as with Synaptic, so when in doubt, use the latter.

---

### Post by Flimm on 2008-10-06
> **linesma said:**
> Thanks for the reply. Ok, so when it says to install it using a "Software Channel" instead, what does that mean?  

Off-topic - Still getting used to the whole sudo vice su - thing btw.

"Software Channel" means a Ubuntu repository here. Are you trying to install a downloaded package (.deb) ?

---

### Post by linesma on 2008-10-06
> **DrMega said:**
> In your System->Administration menu, there should be an option called "Software Sources" which brings up a dialog. Make sure all the tick boxes are ticked, then close it and launch Synaptic. You can access the same options from within Synaptic but I can't remember how off the top of my head.

Thanks for the info.  I did what you suggested and all the boxes were checked, and everything still does not show up.  It is more than just Conky, it is other Gnome apps and extensions, and KDE stuff as well.

Thanks again,

linesma

---

### Post by SunnyRabbiera on 2008-10-06
> **linesma said:**
> Thanks for the reply. Ok, so when it says to install it using a "Software Channel" instead, what does that mean?  

Off-topic - Still getting used to the whole sudo vice su - thing btw.

A software channel is basically a alternate repository, if things are working I would not worry about using alternate software channels.

---

### Post by DrMega on 2008-10-06
> **linesma said:**
> Thanks for the info.  I did what you suggested and all the boxes were checked, and everything still does not show up.  It is more than just Conky, it is other Gnome apps and extensions, and KDE stuff as well.

Thanks again,

linesma

There's an option in Synaptic to update the packages list. It's just the 'reload' button. Try clicking that and see if it makes any difference.

---

### Post by linesma on 2008-10-06
> **Flimm said:**
> In Add/Remove Applications, there's a combo box that a lot of people don't notice, at the top, set Show to "All available applications".
Even with that enabled, you won't get as many packages as with Synaptic, so when in doubt, use the latter.

Thanks for the reply.  I will check out Synaptic when I get a chance.  The response from everybody has been great.

Thank you,
linesma

---

### Post by linesma on 2008-10-06
It worked!!!  Thanks to you all for the information and help.  Now I just need to remember it is sudo not su -

linesma

---

