---
title: "Monodevelop 2.0 and Ubuntu 8.10"
date: 2009-08-05
forum: Programming Talk
---

### Post by lordbah on 2009-08-05
Where can I find a package to install Monodevelop 2.0 on Ubuntu 8.10? Or must I build it from source?

---

### Post by argor on 2009-08-06
it is in the repo just use synapatic to install it

---

### Post by lordbah on 2009-08-06
> **argor said:**
> it is in the repo just use synapatic to install it

Synaptic only sees version "**1.0**+dfsg-3 (intrepid)", which I already have installed.

---

### Post by Bufke on 2009-08-07
I don't have 8.10 to test, but maybe

2 alpha at getdeb [http://www.getdeb.net/search.php?search_distro_id=9&keywords=monodevelop](http://www.getdeb.net/search.php?search_distro_id=9&keywords=monodevelop)

Maybe try to install jaunty's package just to see.  It may want you to upgrade mono though. [http://packages.ubuntu.com/jaunty/monodevelop](http://packages.ubuntu.com/jaunty/monodevelop)

PPA's [https://launchpad.net/ubuntu/+ppas?name_filter=monodevelop](https://launchpad.net/ubuntu/+ppas?name_filter=monodevelop)

---

### Post by directhex on 2009-08-07
MD2.0 was not stable when 8.10 released

And I have better things to do than backport it

---

### Post by lordbah on 2009-08-09
In the end I decided to just upgrade to 9.04.

So now I have Monodevelop 2.0, according to Synaptic, but almost every choice under every menu is grayed out. Even Help/About.

I guess I'll try completely removing monodevelop and reinstalling it - maybe something is broken with upgrades.

EDIT: No luck from the uninstall/reinstall. I did find that Help/About works while looking at the Welcome page. After I select one of my existing solution files and it loads that up, then Help/About (and everything else) becomes grayed out. The splash screen stays stuck at "Loading Workbench", which I see other people have reported. I started trying the workarounds listed -- Tried to remove the Welcome Page add-in, it throws an exception during removal and the GUI hangs, on restart it is still there; so I disabled the addin, tried to remove it and it hung, restarted and it remained disabled, tried to remove it now and it says "The uninstallation failed!" -- but I can now load a solution and menus still work afterward.

---

### Post by directhex on 2009-08-09
Try removing your ~/.config/.MonoDevelop (I think that's where it stores stuff) and starting it again

---

