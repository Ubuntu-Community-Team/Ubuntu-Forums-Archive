---
title: "Updating mono to latest release"
date: 2007-09-04
forum: Programming Talk
---

### Post by benton on 2007-09-04
Hi there, I've noticed that mono does not get updated in-between Ubuntu releases. :( In fact I don't even think each ubuntu release comes out sporting the latest mono available at the time. So Is there a way to update the mono framework manually?

I'm considering using apt-get to remove every package with mono in its name and then installing the .bin generic download from the mono project, but I don't know if this would break F-Spot which is mono-based and I use it a lot.

Any ideas? Thanks!

---

### Post by triptoe on 2007-09-05
im not sure... i tried to update my mono from SVN but it still says version 1.2.3.1 . so im stuck

---

### Post by fct on 2007-09-05
If  you don't delete the installed package the newer version of mono might not work, because of the priority of installed packages.

Depending on the application, yes, a newer version of Mono might break it. *But the F-Spot package will get uninstalled anyway if you delete the mono packages*. So I guess it's all or nothing. :)

---

### Post by benton on 2007-09-05
Thanks for all the answers. So in other words, if you must have the latest mono installed at all times, Ubuntu does not fit the bill. :(

So then, in your opinion, which Linux distro would be the best mono development platform? 

Thanks!

---

### Post by emperon on 2007-09-05
Mono 1.2.5 for ubuntu is available here : 
deb [http://www.viraptor.info/repo](http://www.viraptor.info/repo) feisty-custombackports contrib


(It's preview 5 I think but works fine)

---

### Post by fct on 2007-09-05
> **benton said:**
> Thanks for all the answers. So in other words, if you must have the latest mono installed at all times, Ubuntu does not fit the bill. :(

So then, in your opinion, which Linux distro would be the best mono development platform? 

Thanks!

It fits the bill as much as any other distro. If you install unstable versions of libraries you can expect older programs bundled with the distro to have some problems, and if the new version is not configured for a parallel install it can clash with the older version installed in the system. That's completely normal.

---

### Post by benton on 2007-09-05
Granted, though I was rather thinking on  good distro with no mono installed by default, and so, with no packages depending on mono. That way I could install, uninstall and upgrade mono and monodevelop versions without breaking anything. Now in this "good" distro, the generic mono installer should work flawlessly and be easy to upgrade. For me, this hypothetical distro would fit the bill better than Ubuntu as a mono development platform. 

[EDIT] I'm checking the instructions for the generic mono installer. it says it won't disturb existing mono installations. So I think I'll give it a try and hope for the best. :)

---

### Post by emperon on 2007-09-06
Generic Mono installer has GTK# 2.8 . Tomboy won't work with it

---

### Post by samjh on 2007-09-06
> **benton said:**
> Thanks for all the answers. So in other words, if you must have the latest mono installed at all times, Ubuntu does not fit the bill. :(

So then, in your opinion, which Linux distro would be the best mono development platform? 

Thanks!

The Mono Project releases official RPMs for Suse, Red Hat, and Fedora.  It also releases packages for Solaris, if you're into that.

Your best bet will be Suse, because the Mono Project is sponsored largely by Novell, and Suse is Novell's distro. :)

---

