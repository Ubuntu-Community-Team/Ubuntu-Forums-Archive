---
title: "[SOLVED] How do I install Linux Mint Menu on Ubuntu"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by MockY on 2008-11-01
After using Linux Mint 5 for 6 months, I really miss the menu that is used in that distro. I installed Ubuntu System Panel using [this guide]("http://code.google.com/p/ubuntu-system-panel/wiki/Installation") but even though it is similar, it is not even close to as nice as the menu used in Mint.

So after 2 hours of looking for a way to install it, I now ask the Ubuntu community for help.
Does anyone have an idea how I can get the Linux Mint Menu on my Ibex?

---

### Post by SunnyRabbiera on 2008-11-01
well there is this page with the mint menu listed as a package, But i ma unsure if it will work in ibex:
[http://www.linuxmint.com/repository/pool/main/m/mintmenu/mintmenu_3.0_i386.deb](http://www.linuxmint.com/repository/pool/main/m/mintmenu/mintmenu_3.0_i386.deb)

---

### Post by Allegretto on 2008-11-01
I tried installing it in Hardy and it didn't quite function properly. There was no icon on the panel, just a small, clickable blank space which brought up the menu.

---

### Post by SunnyRabbiera on 2008-11-01
> **Allegretto said:**
> I tried installing it in Hardy and it didn't quite function properly. There was no icon on the panel, just a small, clickable blank space which brought up the menu.

well there is a bugfix release too from the romeo repository.

---

### Post by MockY on 2008-11-01
> **SunnyRabbiera said:**
> well there is this page with the mint menu listed as a package, But i ma unsure if it will work in ibex:
[http://www.linuxmint.com/repository/pool/main/m/mintmenu/mintmenu_3.0_i386.deb](http://www.linuxmint.com/repository/pool/main/m/mintmenu/mintmenu_3.0_i386.deb)

This is fairly close to the menu I'm looking for. However, it does not have any functionality, as in nothing shows up on the right when hovered of clicked. Furthernore, many empty options appear.
Here is a screen:

[IMG]http://www.sotd.se/blandat/mintmenu.jpg[/IMG]

---

### Post by SunnyRabbiera on 2008-11-01
well what I linked is indeed the official mint menu, however like i said it might not work fully under ibex.
But to see if the updated version will work add this to your etc/apt/sources.list:
## +++ Romeo (unstable) +++
## deb [http://www.linuxmint.com/repository/](http://www.linuxmint.com/repository/) romeo/

---

### Post by MockY on 2008-11-01
> **SunnyRabbiera said:**
> well what I linked is indeed the official mint menu, however like i said it might not work fully under ibex.
But to see if the updated version will work add this to your etc/apt/sources.list:
## +++ Romeo (unstable) +++
## deb [http://www.linuxmint.com/repository/](http://www.linuxmint.com/repository/) romeo/

Did such, but I don't really know what to do after an apt-get update. Reinstall?

---

### Post by OrangeCrate on 2008-11-01
> **MockY said:**
> After using Linux Mint 5 for 6 months, I really miss the menu that is used in that distro. I installed Ubuntu System Panel using [this guide]("http://code.google.com/p/ubuntu-system-panel/wiki/Installation") but even though it is similar, it is not even close to as nice as the menu used in Mint.

So after 2 hours of looking for a way to install it, I now ask the Ubuntu community for help.
Does anyone have an idea how I can get the Linux Mint Menu on my Ibex?

I found this a while back, but haven't had a chance to try it. It might be what you're looking for...

**Get mintInstall, mintMenu and mintDesktop on Ubuntu!!**

[http://helpforlinux.blogspot.com/2008/09/get-mintinstall-mintmenu-and.html](http://helpforlinux.blogspot.com/2008/09/get-mintinstall-mintmenu-and.html)

---

### Post by MockY on 2008-11-01
> **OrangeCrate said:**
> I found this a while back, but haven't had a chance to try it. It might be what you're looking for...

**Get mintInstall, mintMenu and mintDesktop on Ubuntu!!**

[http://helpforlinux.blogspot.com/2008/09/get-mintinstall-mintmenu-and.html](http://helpforlinux.blogspot.com/2008/09/get-mintinstall-mintmenu-and.html)

Thank you so much. That worked perfectly. 
Using the guide, I downloaded the following [DEB]("http://packages.linuxmint.com/pool/main/m/mintmenu/mintmenu_4.0_all.deb"). Simple, easy, and absolutely beautiful.

---

### Post by OrangeCrate on 2008-11-01
> **MockY said:**
> Thank you so much. That worked perfectly. 
Using the guide, I downloaded the following [DEB]("http://packages.linuxmint.com/pool/main/m/mintmenu/mintmenu_4.0_all.deb"). Simple, easy, and absolutely beautiful.

You're welcome, I glad it worked for you.

:)

---

### Post by HanZo on 2008-12-12
great!
I was so missing the mint menu too! Thanks for this solution!

---

