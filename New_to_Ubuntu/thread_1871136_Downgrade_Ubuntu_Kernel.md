---
title: "Downgrade Ubuntu Kernel"
date: 2011-10-28
forum: New to Ubuntu
---

### Post by vsbladz on 2011-10-28
I recently installed Ubuntu 10.04LTS and really happy with it. My Wacom Bamboo Pen Stylus worked just fine. However, a week ago, I updated my Ubuntu and my Bamboo pen started to misbehave.
When I touch the pad and drag, it's fine, but it stays there and does not follow my pen around unless I touch the pad again.

I have tried various methods of install, but none works.

I want to completely remove it from my system and rebuild it from older Source. Or should I just simply downgrade my kernel?

Thanks

---

### Post by Paqman on 2011-10-28
> **vsbladz said:**
> Or should I just simply downgrade my kernel?


If you know the older kernel worked, this is definitely the easier option. Open up Synaptic Package manager and search for "linux-image", then install the one which worked. To prevent it from updating to a newer version you'll need to find the metapackage that controls kernel upgrades (which is called linux-generic IIRC) then lock that to the version you want. I can't remember the exact menu that option is in in Synaptic, but it is in there.

---

### Post by vsbladz on 2011-10-28
Hey Thanks Paqman. A little more detailed explanation would be nice? Much Appreciated!!:)

---

### Post by philinux on 2011-10-28
Or just choose the older kernel from grub at boot. Press the shift key to see grub if it not displayed.

---

### Post by Paqman on 2011-10-28
> **vsbladz said:**
> Hey Thanks Paqman. A little more detailed explanation would be nice? Much Appreciated!!:)

Philinux is right, it's quite likely you've already got the older kernel installed. If so just boot into that. You can then use a tool like [Startup Manager](apt:startupmanager) to set that kernel to be the default that you boot into every time.

---

