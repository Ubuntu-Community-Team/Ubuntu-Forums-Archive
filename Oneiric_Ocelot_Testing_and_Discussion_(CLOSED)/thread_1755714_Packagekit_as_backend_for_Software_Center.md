---
title: "Packagekit as backend for Software Center?"
date: 2011-05-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Podex on 2011-05-11
I just find out that work will be done to integrate Packagekit with Software Center: 
[http://alex.eftimie.ro/2011/05/05/gsoc-2011-packagekit-and-appstream-integration-for-software-center/](http://alex.eftimie.ro/2011/05/05/gsoc-2011-packagekit-and-appstream-integration-for-software-center/)
[http://swarm.cs.pub.ro/~alexef/gsoc/proposal.html](http://swarm.cs.pub.ro/~alexef/gsoc/proposal.html)

I don't however see it on the agenda of UDS-O of being discussed. The blueprint that has been around for a while also has not had any activity lately:
[https://blueprints.launchpad.net/ubuntu/+spec/other-m-software-center-backend](https://blueprints.launchpad.net/ubuntu/+spec/other-m-software-center-backend)

Does this mean that this guy will do the work on adding Packagekit integration with Software Center but Ubuntu wont take it?

---

### Post by gnomeuser on 2011-05-11
The AppStream project has a student during this work as part of GSoC, working under openSUSE. I suspect we will see it once Ubuntu sees the light.

---

### Post by Starks on 2011-05-11
packagekit has been discussed for years yet it's like a phantom that just won't find peace

---

### Post by Podex on 2011-05-11
Well it least there seems to be some progress now. Just not from the side of Ubuntu. When I was reading this:

> Ubuntu Software Center really kicks ***, although we really need them to drop the CLA. USC will be ported to use PackageKit in the next couple of weeks.
([http://blogs.gnome.org/hughsie/2011/01/24/application-installer-miniconf-trip-report/](http://blogs.gnome.org/hughsie/2011/01/24/application-installer-miniconf-trip-report/))

I thought that Ubuntu was going to it. But then I googled some more and found the blog of the student that's going to do it and he doesn't mention Ubuntu's interests in this at all.

---

### Post by beew on 2011-05-11
Don't know what "packagekit" is but if it is something like KDE's kpackagekit then it is really bad. It is slow and  you get to enter your password twice if you install from "untrusted source". WTF?

But since I don't use the SC anyway,--it is bloated and slow as it is,-- I don't really care. As long as I get Synaptic I am happy. I have Fedora 14 with KDE. The only thing I used the kpackagekit for was to install Yumex (same idea as Synaptic) and then I just deleted the icon for kpackagekit from the menu and forgot about it.

---

### Post by alexef on 2011-05-30
> **Podex said:**
> Well it least there seems to be some progress now. Just not from the side of Ubuntu. When I was reading this:


([http://blogs.gnome.org/hughsie/2011/01/24/application-installer-miniconf-trip-report/](http://blogs.gnome.org/hughsie/2011/01/24/application-installer-miniconf-trip-report/))

I thought that Ubuntu was going to it. But then I googled some more and found the blog of the student that's going to do it and he doesn't mention Ubuntu's interests in this at all.

Hi, I am the GSoC student working on bringing a PackageKit backend and AppStream integration to Ubuntu Software Center.

I'm working closely to the s-c author, Michael Vogt of Canonical, so don't worry, my contributions are going back to Software Center. It's not about taking sides here, ideally, after this summer work is finished, every distro participating in the AppStream initiative (openSUSE, Ubuntu, Debian, Mageia, Fedora) will win.

Cheers.

---

