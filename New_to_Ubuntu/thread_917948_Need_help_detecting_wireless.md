---
title: "Need help detecting wireless"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by cdnaerogeek on 2008-09-12
Perhaps I'm missing something.

I think I messed up in an earlier thread when I said that my computer was detecting my wireless card. Now I'm almost certain that it isn't (Networking with the wire is still ok.)

I have 64-bit Hardy Heron loaded onto my Gateway T-1625 Laptop. It has an AMD Turion 64x2 processor. The wireless card is integrated Realtek 802.11g (I'm pretty sure.) Wireless doesn't show up if I type 'lspci' but ethernet does.

Here's the real sticking point: I'm reading the community and Hardy Heron documentation for wireless troubleshooting and it says go to System -> Preferences -> Hardware Information to check if Ubuntu detects the wireless card. **Except that I can't find 'Hardware Information' listed in that menu!** Am I just blind or is that menu not automatically set up when I first installed 8.04?

---

### Post by nothingspecial on 2008-09-12
Can you post the results of -
```

lspci -v
```

Just so we can have a look.

I think you need madwifi for this card.

---

