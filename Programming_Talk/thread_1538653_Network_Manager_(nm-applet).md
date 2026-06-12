---
title: "Network Manager (nm-applet)"
date: 2010-07-25
forum: Programming Talk
---

### Post by FireLizzard on 2010-07-25
Some of the functionality of the Network Manager applet really annoys me. In Mac OS X and Windows, you can choose not to remember a wireless network and/or autoconnect to it. In Network Manager, there is no way to prevent it from remembering a network, and I manually have to change the settings for that network to prevent NM from autoconnecting. And deleting the network leaves residual data (when I switch to Guest, the network is still saved). There is no way I can describe how much this annoys me an still remain civil and intelligible.

What I want to do is modify the source to my ends. I don't want help modifying it, I can do that myself. I just don't know where to start looking. Is what I need to modify in the source for the GUI, or the backend? Is there a difference between the two (are they compiled separately)? Where would this functionality be in the source?

PS: I tried using Wicd, and it did not serve my purposes. NM connects fluidly and seamlessly to networks, it just has a habit of annoying me.

---

### Post by PmDematagoda on 2010-07-26
What you're talking about probably resides in the backend, if you go to the nm website you can see what I'm talking about.

By the way, you probably would've been better off asking this question on the nm [mailing list]("http://mail.gnome.org/mailman/listinfo/networkmanager-list").

---

