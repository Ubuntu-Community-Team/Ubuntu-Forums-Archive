---
title: "NetworkManager on Docky?"
date: 2010-11-05
forum: Philippine Team
---

### Post by VirtualEdgar on 2010-11-05
Haven't found any resource for this. I planned in removing the Gnome panel and use Docky and Screenlet instead. Problem is, I can't seem to add the nm-applet in both.

Any ideas or work-arounds on how to do this?

Thanks!

---

### Post by oobermensch on 2010-11-05
I think Docky has a Network Manager docklet. Go to the Docky settings and find the network manager docklet in the Docklets tab.

---

### Post by VirtualEdgar on 2010-11-05
> **oobermensch said:**
> I think Docky has a Network Manager docklet. Go to the Docky settings and find the network manager docklet in the Docklets tab.

Sad to say, it doesn't have one. I'm using v2.0.5 by the way.

Thanks for the reply.

---

### Post by oobermensch on 2010-11-06
It might not be available in the latest stable build. I'm using the development build, so it always has all the latest features. Launch terminal and copy paste this code to add the Docky PPA:
> ppa:docky-core/ppa

After that, use Update Manage to check for new updates. Docky should appear on the list. Just update it, then look for the Network Manager docklet again.

---

### Post by oobermensch on 2010-11-06
Correction. The correct code should be: 

> sudo add-apt-repository ppa:docky-core/ppa

Sorry I overlooked the important part. LOL

---

