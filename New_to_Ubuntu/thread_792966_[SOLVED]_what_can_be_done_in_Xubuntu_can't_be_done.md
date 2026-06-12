---
title: "[SOLVED] what can be done in Xubuntu can't be done in Ubuntu--why?"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by Amanda HazLaPaz on 2008-05-13
Background: I am a big fan of Mystery Science Theater 3000. There is a website called Digital Archive Project that does P2P sharing of items *not* in the official Rhino Home Release catalog.

Issue: The DAP's downloads didn't work for me in Ubuntu. I tried multiple apps from the Add/Remove: donkeys and mules and rabbits galore, and nothing worked. I figured it had something to do with my inexperience with Ubuntu: only in the past six months have I been able to figure out how to get a torrent to work properly. The link for "Main Download Categories" is:  [http://www.dapcentral.org/modules.php?op=modload&name=Downloads&file=index](http://www.dapcentral.org/modules.php?op=modload&name=Downloads&file=index)

On a whim, I tried the P2P again back when I thought Xubuntu was a much more separate/different distro and it worked flawlessly, with little to no problems or hassles. Now that I have figured out how to run Ubuntu 7.10 in Xfce session, and get what is essentially Xubuntu, I am guaranteed months of laughter.

Question: *WHY*would something work in Xubuntu that didn't work in Ubuntu? How are the two systems different? I'm asking because I'd like to know more; it's not necessary an issue that needs to be solved, and the thread is titled **Absolute Beginner Talk: [SIZE="1"]The perfect starting place to find out more about computers, Linux and Ubuntu.[/SIZE]**

(I didn't dual-boot; I enabled all Xubuntu packages in synaptic and choose "Xfce session" at boot-up.)

---

### Post by crjackson on 2008-05-13
Did you install firestarter in ubuntu.  It sounds like your ports are closed in ubuntu (i.e. firewall blocking).  You may need to configure iptables to open up the needed port for your file transfer applications.

---

### Post by Amanda HazLaPaz on 2008-05-13
a-HA!

I *do* have Firestarter running (it doesn't run in the Xfce environment?)

I'll mark this solved: thank you so much. I've learned my thing for the day.

---

### Post by crjackson on 2008-05-13
> **Amanda HazLaPaz said:**
> a-HA!

I *do* have Firestarter running (it doesn't run in the Xfce environment?)

I'll mark this solved: thank you so much. I've learned my thing for the day.

You're welcome.  I've done it before too...

---

### Post by bapoumba on 2008-05-13
That is an interesting question. I run Xubuntu, and have firestarter running fine on it. May be the wizard has to be configured on both desktops, so that the proper files are set up at the proper places (most of the config files do not go at the same place on Xfce and gnome) ?

---

### Post by Amanda HazLaPaz on 2008-05-14
Would Firestarter even run in Xubuntu?

I don't recall seeing it in Add/Remove when I installed Xubuntu on a separate laptop to "get a feel for it"; otherwise I would have chosen Firestarter to be my firewall. As it was, I *had* no firewall for that month. I remember an icon for a red dog (sorry to be so vague). 

Would Firestarter be listed in the synaptic package manager of Xubuntu?

Thanks for your input, bapoumba.

---

### Post by eriqjaffe on 2008-05-14
I'm pretty sure that Synaptic lists things regardless of your DE/WM.  Technically speaking, Firestarter isn't a firewall itself, it's just a GUI front-end to iptables.

To answer your question of how Xubuntu and Ubuntu are different - Ubuntu uses Gnome for its' DE, Xubuntu uses XFCE (albeit with a fair amount of Gnome dependencies) for its' interface.  But you can run apps designed for Ubuntu on Xubuntu and vice-versa.  The same rule holds true for Kubuntu, as well.

---

### Post by Amanda HazLaPaz on 2008-05-14
Man, I don't think there's enough time in the day for thanking everyone who is being so helpful. Eric-- more information you've provided to me, and I am very grateful for it.

DE means desktop environment; what's WM?

---

### Post by eriqjaffe on 2008-05-14
WM is shorthand for a "Window Manager", which is responsible for actually drawing & decorating windows...every DE has a WM, but not every WM is part of a DE.

Gnome, for example, uses metacity (or compiz, if you're so inclined) as its' WM, and XFCE uses xfwm.

It's entirely possible to run **just** a Window Manager, in fact.  Many people with older systems (myself included) prefer to run this way.  You don't get all the panels & GUI config tools, but it's still entirely possible.

---

### Post by gn2 on 2008-05-14
Firestarter works fine in Xubuntu, well it does for me anyway :-)

---

### Post by Amanda HazLaPaz on 2008-05-14
CONFIRMED: this evening I logged in under GNOME session and disabled the firewall. I was easily able to connect to the seeders via the link in the Digital Archive Project.

Thanks to all for such great input and support.

---

