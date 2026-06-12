---
title: "Can't customize ANYTHING"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by scylla2 on 2008-11-07
Well I installed Ubuntu 8.10 on my eMachines laptop because I was intrigued by Linux and was bored of the same-old look of WinXP. I really liked the idea of being able to customize with themes and looked at several on the DeviantArt site, etc. before installing.

Ubuntu seems to run fine and I'm sure learning some new things, but forget about any cool desktop customization. I tried downloading some of the GTK+ themes, only to get constant "GTK+ engine not installed" errors. I think the lack of GTK+ support is a bug in 8.10. So much for that idea.

I tried the (much more boring) non-GTK+ themes, but they're impossible to install too. From what I've read, it's simply a matter of pointing the Install button in the Themes app to the downloaded tar.gz file. That didn't work, and neither did unzipping the contents into my /home/MyName/.themes directory or anything else I've tried. So much for that too.

So I read up on and thought I'd install the KDE 4.0 desktop as there seems to be a ton of downloadable customizations out there. I closely followed the instructions in the link [http://www.my-guides.net/en/content/view/120/26/](http://www.my-guides.net/en/content/view/120/26/)


Everything seemed to go fine during the LONG process of installing KDE, but when I reboot (surprise) I'm back to the old uncustomized Gnome desktop. The only difference I see is that I get the blue "Kubuntu" intro page at first boot, but it just goes to the Gnome desktop anyway. There's no way I can see that will let me switch to KDE. The KDE network manager is on my Gnome upper panel (green globe) but that's the only difference in my system after installing KDE that I can find.

So I guess that's it with regards to customizing my desktop, which is mainly why I wanted to switch O/Ss in the first place. I guess I'd better get used to the "Darkroom" theme.

Any ideas?

---

### Post by achase79 on 2008-11-07
at the login screen you have to choose to use KDE by clicking on the sessions button and selecting it and setting it to default.

---

### Post by achase79 on 2008-11-07
If you have a downloaded theme for gnome you should be able to drag and drop the *.tar.gz file directly into the opened themes panel to install it.

---

### Post by scylla2 on 2008-11-07
Thanks that worked. I didn't think to look way down there at the "Options" button. I just logged in thinking I'd get KDE.

Any ideas about my other troubles? I'm sure it's another very simple solution.

---

### Post by scylla2 on 2008-11-07
> **achase79 said:**
> If you have a downloaded theme for gnome you should be able to drag and drop the *.tar.gz file directly into the opened themes panel to install it.

Tried that about a thousand times. Says Invalid Theme file or something like that.

---

### Post by Karilex on 2008-11-07
Go to synaptic package manager and get emerald then type emerald --replace in the terminal then try using emerald to install new themes instead of the default appearance manager you can get themes for emerald here:
[http://www.gnome-look.org/index.php?xcontentmode=103](http://www.gnome-look.org/index.php?xcontentmode=103)
If you get tired of emerald just type metacity --replace in the terminal

terminal is in: applications>accessories>terminal
synaptic package manager is in System>administration>synaptic package manager

---

