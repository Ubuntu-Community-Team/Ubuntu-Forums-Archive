---
title: "Installing KDE4.1?"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by chris062689 on 2008-08-08
Is there a Live CD available with **just** KDE 4.1?
I don't want to update a KDE 3.x installation, and every time I do a CLI Install, it puts me with a server kenel.
Any suggestions?

---

### Post by eightmillion on 2008-08-08
You know you can install 4.1 along side 3.5 right? You can select which one you want to run at the log in screen. Otherwise, there is a live/install CD available. It's the [Kubuntu KDE 4 Remix.]("http://cdimage.ubuntu.com/kubuntu-kde4/releases/hardy/release/")

---

### Post by benerivo on 2008-08-08
There's a live cd with 4.0 [here]("http://cdimage.ubuntu.com/kubuntu-kde4/releases/hardy/release/"), but you'll have to add the launchpad repository to be able to upgrade to 4.1. As far as i know, [opensuse]("http://home.kde.org/~binner/kde-four-live/") is the only live kde4.1 cd (other than various betas and alphas) that is currently available.

---

### Post by prabhakaran1989 on 2008-08-08
I don have any idea check out the canonical store!

---

### Post by chris062689 on 2008-08-08
So there's no Live CD that installs a CLI with a Desktop Kernel?
I don't want to upgrade a KDE 3.x / 4.0 installation, because things may break and I don't want KDE 3.x applications mixed in with KDE 4 apps.  I don't want to install it alongside GNOME either.

---

### Post by prabhakaran1989 on 2008-08-08
then wat else u gonna do ??

---

### Post by chris062689 on 2008-08-08
I really don't want to use OpenSUSE (mostly due to it's connections with Microsoft).
There's no way to control which packages are installed on a Live CD?

---

### Post by eightmillion on 2008-08-08
> So there's no Live CD that installs a CLI with a Desktop Kernel?
You can always installa desktop kernel after you've installed the system.
```
sudo apt-get install linux-image-2.6.24-18-generic
```
> I don't want to upgrade a KDE 3.x / 4.0 installation, because things may break and I don't want KDE 3.x applications mixed in with KDE 4 apps. I don't want to install it alongside GNOME either.
No, there's no KDE 4.1 CD available right now unless you want to install Intrepid Ibex Alpha 3. I'm not sure why you're so worried about upgrading 4.0. Many people have done it and not had any problems, including myself. It's not even difficult. You just add this to your **/etc/apt/sources.list**:
```

deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main
deb-src http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main

```
and then do 
```

sudo apt-get update && sudo apt-get upgrade

```

---

### Post by chris062689 on 2008-08-08
> **eightmillion said:**
> You can always installa desktop kernel after you've installed the system.
```
sudo apt-get install linux-image-2.6.24-18-generic
```

I assume I can uninstall the server kernel, and continue using it normally as a Desktop Kernel (installing updates, updating kernel, etc.)?

---

### Post by eightmillion on 2008-08-08
> I assume I can uninstall the server kernel, and continue using it normally as a Desktop Kernel (installing updates, updating kernel, etc.)?
Yes.

---

### Post by eightmillion on 2008-08-08
What you really may be looking for is the [minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD"). It has an option, "Install a command-line system". Installing that installs the generic kernel and modules.

---

### Post by chris062689 on 2008-08-09
I'm already installing the server edition, but thanks for that, if I ever need to reinstall I'll remember this thread, thank you!

---

