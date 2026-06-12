---
title: "Screen corruption on resume from suspend"
date: 2011-09-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by philinux on 2011-09-15
Anyone else got this with other manufacturers drivers installed.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/849656](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/849656)

---

### Post by madjr on 2011-09-15
> **philinux said:**
> Anyone else got this with other manufacturers drivers installed.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/849656](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/849656)

that looks awful !

but weird the panel is ok...

---

### Post by Quackers on 2011-09-15
Strangely, I had that broken up appearance when resuming from suspend, but the only affected areas were the top panel and the unity panel - NOT the main desktop. These affected areas cleared up when I first clicked on the them.

---

### Post by Seq on 2011-09-15
> **philinux said:**
> Anyone else got this with other manufacturers drivers installed.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/849656](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/849656)

Yes, I get that after every resume. Unity's panels & dash are not affected. Press ALT+F2 and run `unity --replace` "fixes" it by killing unity and starting a new one.

---

