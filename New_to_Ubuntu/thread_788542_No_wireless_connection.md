---
title: "No wireless connection"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by Rukaru on 2008-05-09
Okay, Ijust installed ubuntu and went through a long process to make my my video card work so I could get a much higher resolution and so I could get compiz fusion.  Now I have a few questions relating to this and then more important questions relating to wireless.  First, I will list what I know of my computer that apply.

[INDENT]OS: Hardy Heron & XP dual boot
Video card: Nvidia Geforce 6150 LE
Type of connection: wireless home network

I already had XP, and then got ubuntu for the first time.  I had no previous versions of ubuntu.

I set up ubuntu on an older desktop nearby the one I'm using.  Everything went smoothly, and internet connected fine.  A belkin USB wireless adapter was used [/INDENT]

Okay, now for my questions relating to the video card

[INDENT]1) What are the disadvantages to using a restrcited driver for the video card?
2) Can the Nvidia Geforce 6150 LE (integrated graphics card) support compiz fusion 3D? (It can support the wobbly window effect)[/INDENT]

Alright, now for my biggest problem....the wireless! Now, I'm not sure what I have, but I know it's some type of Belkin Wireless G desktop card.  Here's what I saw when I looked at network related hardware while in XP:

1394 net adapter
Belkin wireless G desktop card
Nvidia nforce Networking controller

Now, I am currently using the internet....but I'm not sure how well it works because I did something weird to get it.  It also won't come on automatically like it did when I set up ubuntu on the older desktop.  I have to enter the network password each time.  Now, to get the internet, I went to the older desktop with ubuntu and got the wireless info.  I just copied everything (like the IP) and put it on this computer (entering it in the wireless section of network settings), so there will probably be conflicts. I also wasn't sure what to put for the gateway address field, so I just put the "default route" number.  Is that dangerous?  

Also, I seem to have lost the wireless connection bar icon.  I must have deleted it by accident (I was very tired when working on it).  

So, there you go.  That is all I know.  if you need more specific info on the wireless card, tell me how to get it.  If there's a way I could get this info on XP, let me know since that might be easier.

---

### Post by Rukaru on 2008-05-09
Please keep in mind that I know very little about ubuntu and using that "terminal" thing.  I also know very little about drivers.  I am used to XP and I never used anything like "terminal" and I never messed with the drivers.

---

### Post by Rukaru on 2008-05-09
And please remember that there was no problem with the wireless network when setting up ubuntu on the other desktop.

---

### Post by Rukaru on 2008-05-09
bump

---

### Post by ugm6hr on 2008-05-09
> **Rukaru said:**
> Now, I am currently using the internet....but I'm not sure how well it works because I did something weird to get it.  It also won't come on automatically like it did when I set up ubuntu on the older desktop.  I have to enter the network password each time.  Now, to get the internet, I went to the older desktop with ubuntu and got the wireless info.  I just copied everything (like the IP) and put it on this computer (entering it in the wireless section of network settings), so there will probably be conflicts. I also wasn't sure what to put for the gateway address field, so I just put the "default route" number.  Is that dangerous?  

Also, I seem to have lost the wireless connection bar icon.  I must have deleted it by accident (I was very tired when working on it).  

Without knowing what you did, this is going to be tricky.

But it sounds like you removed nmapplet (the wifi manager icon).

In System->Preferences->Sessions, Startup tab, make sure Network Manager is ticked.

---

### Post by Rukaru on 2008-05-09
> **ugm6hr said:**
> Without knowing what you did, this is going to be tricky.

But it sounds like you removed nmapplet (the wifi manager icon).

In System->Preferences->Sessions, Startup tab, make sure Network Manager is ticked.

It's ticked.  I think I just deleted it from the panel.

---

### Post by ugm6hr on 2008-05-09
> **Rukaru said:**
> It's ticked.  I think I just deleted it from the panel.

Have you rebooted?

If yes - do you have any icons in the system tray (e.g pidgin)?

---

### Post by Rukaru on 2008-05-09
> **ugm6hr said:**
> Have you rebooted?

If yes - do you have any icons in the system tray (e.g pidgin)?

Well yeah I have icons...and yes I've rebooted many times since it has been gone.

---

### Post by ugm6hr on 2008-05-09
```
nmapplet
```

What happens with this command?

---

### Post by Rukaru on 2008-05-10
> **ugm6hr said:**
> ```
nmapplet
```

What happens with this command?

command not found.  It looks just gone.

---

### Post by ugm6hr on 2008-05-10
Try reinstalling network-manager-gnome in Synaptic Package Manager (System->Administration).

---

