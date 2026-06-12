---
title: "More Gnome Confusion"
date: 2011-09-29
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Trapper on 2011-09-29
I am really discouraged. Unity positively is not going to be a viable option for our production environment here. I have made several attempts to set up Gnome to replace Unity but can't quite seem to grasp exactly what I am suppose to do to accomplish this.

I've been going through all the various threads concerning using Gnome but I guess I just don't have a full understanding of what I need to install and set up.

Let's just say I've just installed 11.10 and have it updated and nothing more. Can someone give me the exact steps I have to take to set up a Gnome classic sort of environment? If I cannot get that it appears we are going to have to move on to some other flavor after 11.04 support ends. I'd appreciate some guidance.

---

### Post by collisionystm on 2011-09-29
> **Trapper said:**
> I am really discouraged. Unity positively is not going to be a viable option for our production environment here. I have made several attempts to set up Gnome to replace Unity but can't quite seem to grasp exactly what I am suppose to do to accomplish this.

I've been going through all the various threads concerning using Gnome but I guess I just don't have a full understanding of what I need to install and set up.

Let's just say I've just installed 11.10 and have it updated and nothing more. Can someone give me the exact steps I have to take to set up a Gnome classic sort of environment? If I cannot get that it appears we are going to have to move on to some other flavor after 11.04 support ends. I'd appreciate some guidance.

Open Software Center, install gnome-shell

Log out, Click on users Name, hit the GEAR icon for options, choose CLASSIC GNOME. Login

---

### Post by collisionystm on 2011-09-29
I think you will find that it looks just like Gnome 2 with updated features.

---

### Post by Trapper on 2011-09-29
> **collisionystm said:**
> I think you will find that it looks just like Gnome 2 with updated features.

Okay, I had gnome-shell
 accomplished and didn't even realize it. Thanks.

Actually I am finding it to be missing a lot from Gnome 2. I have no way of utilizing the panels for launchers, etc. It's missing the Administration menu, etc. and is basically Unity in a Gnome wrapper. There's got to be much more that has to be installed. In all seriousness, I don't need it to look like Gnome 2. I need it to work like Gnome 2.

---

### Post by LADmaticCA on 2011-09-29
> **Trapper said:**
> Okay, I had gnome-shell
 accomplished and didn't even realize it. Thanks.

Actually I am finding it to be missing a lot from Gnome 2. I have no way of utilizing the panels for launchers, etc. It's missing the Administration menu, etc. and is basically Unity in a Gnome wrapper. There's got to be much more that has to be installed. In all seriousness, I don't need it to look like Gnome 2. I need it to work like Gnome 2.

You do realize that Gnome 2, as we know it, is no longer developed by the Gnome developers. Your best chance to keep gnome2 is to stay with 10.04 LTS or possibly use Debian Stable. All distros will drop gnome 2 eventually.

Have you tried Xubuntu with the Xfce environment? It is very similar to gnome2 and it's quite fast.

---

### Post by thatguruguy on 2011-09-29
[http://www.xubuntu.org]("http://www.xubuntu.org/")

---

### Post by Merk42 on 2011-09-29
> **Trapper said:**
> Okay, I had gnome-shell
 accomplished and didn't even realize it. Thanks.

Actually I am finding it to be missing a lot from Gnome 2. I have no way of utilizing the panels for launchers, etc. It's missing the Administration menu, etc. and is basically Unity in a Gnome wrapper. There's got to be much more that has to be installed. In all seriousness, I don't need it to look like Gnome 2. I need it to work like Gnome 2.
Try installing gnome-session-fallback.

It's what (default) GNOME uses when you don't have acceptable hardware to run GNOME Shell.

If **that** isn't good enough, then you'll have to go to a different DE like XCFE, and that'll be the case even if you were to switch to some other GNOME distro.

---

### Post by thatguruguy on 2011-09-29
Incidentally, it's pretty easy to add launchers to the Unity sidebar.

---

### Post by Trapper on 2011-09-29
I realize you all are doing your best to help dumb me in this situation but I think you maybe don't understand what I am looking for. That's probably because of the way I explain things.

I'm not having difficulty getting gnome to run. I'm just saying it's offering no more than Unity does. The problem here is that Unity is too elementary. 

We are probably not going to play around with a workaround situation and will channel our efforts to locating something that's up to the task for us. I note a couple of suggestions in this thread and there are surely other alternatives.

Thanks to everyone for their help and input.

---

### Post by cariboo on 2011-09-29
> **Trapper said:**
> Okay, I had gnome-shell
 accomplished and didn't even realize it. Thanks.

Actually I am finding it to be missing a lot from Gnome 2. I have no way of utilizing the panels for launchers, etc. It's missing the Administration menu, etc. and is basically Unity in a Gnome wrapper. There's got to be much more that has to be installed. In all seriousness, I don't need it to look like Gnome 2. I need it to work like Gnome 2.

Unfortunately if you need gnome 2, you are out of luck as it isn't being developed anymore. Gnome-session-fallback, is a rewritten version of the gnome 2 panel interface with out all the bugs. Instead of right-clicking the panel. now you have to alt-right-click to add applets and make changes to the panel.

Gnome-session-fallback in in the repositories.

---

### Post by robert shearer on 2011-09-29
quick version...
[http://www.liberiangeek.net/2011/08/return-to-ubuntu-classic-desktop-in-ubuntu-11-10/](http://www.liberiangeek.net/2011/08/return-to-ubuntu-classic-desktop-in-ubuntu-11-10/)

and to modify panels use **alt+right click**

---

### Post by VanR on 2011-09-29
Gnome-Session-Fallback (gnome classic) works just peachy for me. I may even consider a fresh install of 11.10 when it is ready. Running it on VM now.

---

### Post by castrojo on 2011-09-29
Here's how you can set up a more classic looking desktop: [http://askubuntu.com/questions/58172/how-to-revert-to-gnome-classic](http://askubuntu.com/questions/58172/how-to-revert-to-gnome-classic)

---

### Post by oboedad55 on 2011-09-29
I also suggest Xubuntu. Just search for it in synaptic. It's very similar to Gnome 2.

---

