---
title: "Remove Unity"
date: 2013-10-22
forum: New to Ubuntu
---

### Post by czgirb on 2013-10-22
Someone said ... if we do not plan to use **Unity** anymore, we are allowed to remove it from our machine by typing:
> sudo apt-get remove unity unity 2
sudo apt-get autoremove
in Terminal.
My question is, if we remove the unity ... is our machine still stable as before?
I'm trying to install **Lubuntu DE** before. But when I remove it by using the suggestion from [http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu)
It removed **all my installed program** ... and it caused me a trauma. That's why I never try to install any DE anymore.
**Thank you.**

---

### Post by fantab on 2013-10-22
Unity is your desktop interface, without it you will not have an interface, also unity is part of ubuntu-desktop, I don't think you can remove unity without removing ubuntu-desktop.

To keep it simple just install Lubuntu overwriting Ubuntu with a DVD/USB... in other words, do a fresh install of Lubuntu.
OR
Install lubuntu-desktop on you ubuntu and then remove ubuntu-desktop.

---

### Post by 3rdalbum on 2013-10-22
> **czgirb said:**
> Someone said ... if we do not plan to use **Unity** anymore, we are allowed to remove it from our machine by typing:

in Terminal.
My question is, if we remove the unity ... is our machine still stable as before?

Yes, of course. Unity is just a thin layer stretched over the top of the operating system. The real operating system, the real reliability and stability, is underneath the user interface.

However, removing Unity using those commands is not a good idea. Removing Unity removes the ubuntu-desktop metapackage, which is still fine - but it links with so many different packages that if you use "apt-get autoremove" it'll want to remove half your system. Better to just specify the exact Ubuntu packages to remove and then DON'T do Autoremove. Or if you're unsure, do the safe thing and leave Unity installed.

Lubuntu, Xubuntu and Kubuntu are literally Ubuntu, but with Unity removed and a different desktop installed.

> I'm trying to install **Lubuntu DE** before. But when I remove it by using the suggestion from [http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu)
It removed **all my installed program** ... and it caused me a trauma. That's why I never try to install any DE anymore.

Well, there's a few things to this.

1. You can have multiple desktops installed at the same time, and you choose between them at the login screen. Right now I have LXDE, Unity and Gnome installed on the same computer. Just because you've installed a new desktop, doesn't mean you have to remove the old one.

2. Installing the new desktop didn't cause your problem, removing the old desktop did; and more specifically, not being careful when removing things. It asked you if you wanted to remove those extra packages. If you thought it was a bit strange that it wanted to remove a hundred different packages, then you should really have said "no" and then checked what you were doing.

---

### Post by BBQdave on 2013-10-22
> **fantab said:**
> To keep it simple just install Lubuntu overwriting Ubuntu with a DVD/USB... in other words, do a fresh install of Lubuntu.

+1

Back up your data and do a fresh install - it will save you time and headache :)

---

### Post by ian-weisser on 2013-10-22
> **czgirb said:**
> 
I'm trying to install **Lubuntu DE** before. But when I remove it by using the suggestion from [http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu)
It removed **all my installed program** ... and it caused me a trauma.

Well, removing *all* GUI applications is what that tutorial claimed the command would do, and then it disavowed all the damage it would cause.
So the trauma was (sorry) self-inflicted.

You could simply do:
```
sudo apt-get install lubuntu-desktop   # install lubuntu and dependencies
sudo apt-get remove ubuntu-desktop     # remove ubuntu
sudo apt-get autoremove                # remove no-longer-needed ubuntu dependencies
```

Remember to *read* those apt messages, and abort if the message is scary.

And, 3rdalbum knows his stuff:  Your system will still be as stable as before.

---

