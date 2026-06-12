---
title: "Install GNOME 3 Shell in Oneiric"
date: 2011-07-26
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by pcwiz11 on 2011-07-26
I'm testing out Ubuntu 11.10 Oneiric Ocelot and have heard that it is possible to install GNOME 3 shell in Oneiric. I would like to try this out, but how can I install GNOME 3 shell?

---

### Post by jfernyhough on 2011-07-26
Method 1:
Open synaptic, find **gnome-shell**, install, log out, choose GNOME as your session.

Method 2:
$ sudo apt-get install gnome-shell
log out, choose GNOME as your session.

---

### Post by akvik on 2011-09-15
Hi,

I did just that, and I get "failed to load session gnome" in oneiric beta 1 - any other packages that need installing maybe?

EDIT: Ignore the above - read the oneiric FAQ - it probably doesn't work without tweaking on a virtual machine, running oneiric on VirtualBox on a 10.4 host.

---

### Post by MARP1961 on 2011-09-15
I have it running fine on Oracle VM Virtualbox 4.0.12 with** Guest Additions enabled.** You do however need to open 'Settings' then 'Display' on your Oneiric 'guest'. Then make sure you have your **'Video Memory' set to 128MB (maximum)** not the default one. Also make sure in 'Extended Features' that you** enable 3D Acceleration**.

Only once I had done these things would Gnome 3 Shell work properly in Virtualbox. Incidentally, this was also needed to get the 3D version of Unity working.

---

### Post by akvik on 2011-09-15
Thanks for the input,

I have all the things you mentioned set, but to no avail - I think it breaks when updates are installed (even though I never made it work with oneric - it worked for Maverick when that was beta though), at least that was one theory I read on a forum somewhere.

---

