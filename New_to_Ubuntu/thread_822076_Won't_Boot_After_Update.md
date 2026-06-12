---
title: "Won't Boot After Update"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by OpVines on 2008-06-07
I've been using Hardy for a few weeks and today I got an update. So I did the update and restarted my computer, except now it won't get past the bootup screen where that orange bar is going back and forth. It goes forward for like 3 seconds then completely stops. I even waited like half an hour to see if it would continue booting up but it doesn't. Recovery mode locks up to. The last line is "29.490269 ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1" then it completely stops too.

Can anyone help me figure out how to fix this so I can use my computer?

Even the Gutsy CD I had from before won't even boot. It gets locked up at the screen where the bar is loading...

---

### Post by ZabiGG on 2008-06-07
From the GRUB menu at startup, can you boot any previous kernel? (.16 or .17)

If so, you should try loading with kernel 16 and see if it starts...

---

