---
title: "[SOLVED] So...Do I upgrade the kernal, or not?"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by stoogiebuncho on 2008-10-16
I'm glad this place has an Absolute Beginner forum, because this might just be the noobiest question I've asked yet.

There's an update in my update manager for linux-image-2.6.24-21-generic.  I was going to install it, when I saw this in the description:

"You likely do not want to install this package directly. Instead, install the linux-generic meta-package, which will ensure that upgrades work correctly, and that supporting packages are also installed." 

What does this mean?  Am I supposed to install it or not?

Thanks.

---

### Post by Victormd on 2008-10-16
> **stoogiebuncho said:**
> "You likely do not want to install this package directly. Instead, install the linux-generic meta-package, which will ensure that upgrades work correctly, and that supporting packages are also installed."

Did this show up in the update manager?
You should already have the linux-generic-meta-package installed. If you want to check (just to be sure), go to synaptic and do a search for it and if marked, then it's installed and you can go ahead and install the linux-image-2.6.24-21-generic.

---

### Post by lukjad on 2008-10-16
> **Oldsoldier2003 said:**
> That "warning" applies if you are installing the package manually. It's just there to let the curious fiddlers know that they probably don't need to install the package manually (using synaptic, for example). The fiddlers with more experience need not worry since they generally understand what they are doing :)


 Let the updater do its job and all will be fine, unless of course you have a reason that you don't want that particular kernel update.

That was the best answer I could find, so I quoted it. :twisted:

---

### Post by stoogiebuncho on 2008-10-16
Thanks to both of you.  Lukjad007, your searching skillz are vastly superior to mine.:)

---

### Post by lukjad on 2008-10-16
I have friends... ;)

---

