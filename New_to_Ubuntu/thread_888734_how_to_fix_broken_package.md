---
title: "how to fix broken package?"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by !ndy on 2008-08-13
hi,

i was playing with ndiswrapper.
i was thinking about loading newer drivers, but i did not know the command "ndiswrapper -r". now i know, but its too late...

you know what i did? 
ctrl+alt+f1 - login as root.
then i deleted everything from the folder ndiswrapper in etc.
(windowze way of thinking - sometimes i did not perform normal unistall for some crazy things, i was just fixing registry then for a while :-))

i installed ndiwsrapper again from .deb packages i have.
i tried to load the new driver. it was okay at that point.
also with "ndiswrapper -m" and system told me, that it;s already done.
then i tried to rmmod ndiswrapper and when it tried to modprobe ndisrapper, it freezes. 

now i cannot even unistall it correctly with sudo apt-get uninstall, nor make it work :-(
should not have played as the big system root :-(

is this the second time i have to reinstall ubuntu in 5 days?  :-(

---

### Post by stoneybroke on 2008-08-13
In terminal enter sudo apt-get autoclean then try re-installing with synaptic

Hope that helps

---

### Post by dudetime on 2011-01-28
in synaptic under edit choose fix broken packages and it will remove packages with unmet dependencies

---

