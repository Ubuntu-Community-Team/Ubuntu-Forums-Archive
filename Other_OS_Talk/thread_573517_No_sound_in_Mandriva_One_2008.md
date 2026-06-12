---
title: "No sound in Mandriva One 2008"
date: 2007-10-11
forum: Other OS Talk
---

### Post by arijarot on 2007-10-11
I wanted to try out a new distro... I have no sound in Mandriva One 2008 and I have no idea what info to post or how to retrieve it. Any ideas?

---

### Post by igknighted on 2007-10-11
> **arijarot said:**
> I wanted to try out a new distro... I have no sound in Mandriva One 2008 and I have no idea what info to post or how to retrieve it. Any ideas?

Just like ubuntu, you need to provide specific info as to the hardware you are having trouble with

---

### Post by arijarot on 2007-10-11
> **igknighted said:**
> Just like ubuntu, you need to provide specific info as to the hardware you are having trouble with

OK. how? what do I have to do? e.g., what commands / output?

---

### Post by 67GTA on 2007-10-12
Try changing the master channel. Left click on the speaker(kmix) icon on the panel, and click "Select Master Channel". If you have external speakers, try front or pcm. If that doesn't work, then it is probably an issue with your sound card. Type "lspci" (lists what is in your pci slots) in a terminal window and look for your audio device.

---

### Post by arijarot on 2007-10-12
> **67GTA said:**
> Try changing the master channel. Left click on the speaker(kmix) icon on the panel, and click "Select Master Channel". If you have external speakers, try front or pcm. If that doesn't work, then it is probably an issue with your sound card. Type "lspci" (lists what is in your pci slots) in a terminal window and look for your audio device.

Problem solved. Thanks

---

