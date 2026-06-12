---
title: "how to improve the run program dialog (alt+f2) in xubuntu?"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by darthmob on 2008-06-29
hi,
I'm going to buy a notebook and planned to install xubuntu on it. I already installed it on a virtual machine on my current ubuntu 8.04 installation to test it and so far it seems very neat!

there is one thing which bothers me though: the run program dialog seems less intelligent in xubuntu than in ubuntu. the latter does know all installed programs and proposes them as soon as you write. in xubuntu it does not so and features not even autocomplete with tab.

is there a way to change it?

PS: I attached 2 screens to show what I mean. the first shows ubuntu: I type gca and it proposes the calculator. in xubuntu on the second screen it simply does nothing and I have to type it complete and then press enter.

thanks for your help! :)

---

### Post by sayakb on 2008-06-29
You may have the gnome run dialog, but you might end up installing too many gnome resources for that. At a terminal:
```
sudo apt-get install gnome-panel
```
Now, type:
```
gnome-panel-control --run-dialog
```
For the gnome run dialog. You may also create a launcher pointing to this command.

---

### Post by darthmob on 2008-07-03
thanks for your answer!

it seems like it does not work the easy way! it installed without problems (some additional packages plus openbox for the gnome-panel-control where needed) but it does not react when executed (there is not even an error message).

---

