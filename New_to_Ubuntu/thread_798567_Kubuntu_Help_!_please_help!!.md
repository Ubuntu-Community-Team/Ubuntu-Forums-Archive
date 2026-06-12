---
title: "Kubuntu Help ! please help!!"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by i4gotmyid on 2008-05-18
I installed Ubuntu 7.10 on my DELL laptop with the CD i got from ShipIt . I wish to install KDE desktop in it .

:KS What is the procedure? Can u just download it through the Synaptic Package Manager? Or is it already there in the Ubuntu CD ?

:KS Installing kubuntu is a separate linux installation? How do they exist side by side ?

:KS What is the difference between KDE and GNOME ? Which one is better ?

:KS Will the applications like VLC, Banshee, Pidgin etc work in kubuntu too ? 

:KS I heard about compiz fusion with which graphics can be improved . Is it for Ubuntu or Kubuntu or for both ? Will i have to install it separately for kubuntu and ubuntu ? Is it okay to  install compiz fusion in ubuntu and then install kubuntu or should i install kubuntu 1st and then install compiz fusion .. ?? If installed in ubuntu, will be be applicable to kubuntu ?

Tell me more tips to improve my desktop look and graphics.

I have a NVidia 128 mb Graphics card, 2 Gb ram, 5 gb for linux partition 

Thanks in advance :) :guitar:

---

### Post by shifty_powers on 2008-05-18
right.

kubuntu and ubuntu are the same, just that they use two different desktop managers, kde and gnome. (and use different applications that are nased on kde and gnom).

It is quite possible to have an ubuntu base, with both kde and gnome installed, and to select which one you want to use.

You already have gnome, so go to applications, accessories, terminal and type

```
sudo apt-get install kde-desktop
```

(iirc ;)).

Then when you log in, chagne the session you log in with to kde rather than gnome and there you go.

Gnome apps will work on kde and the other way around, as long as the kde/gnome libraries are installed. If you install a kde app on gnome via synaptic it will do this automatically for you.

as for which is better, well personal preference ;)

---

### Post by BackwardsDown on 2008-05-18
Its:

sudo apt-get install kubuntu-desktop

---

### Post by shifty_powers on 2008-05-18
dammit, knew it was one or the other. don't use the kde desktop, though i might try it in 8.10, when kde 4 should be less buggy ;)

---

