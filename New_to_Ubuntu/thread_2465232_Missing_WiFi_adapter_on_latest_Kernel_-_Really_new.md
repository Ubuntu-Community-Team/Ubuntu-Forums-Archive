---
title: "Missing WiFi adapter on latest Kernel - Really new to Linux/Ubuntu"
date: 2021-07-26
forum: New to Ubuntu
---

### Post by truthster13 on 2021-07-26
I was trying to fix a video memory crashing issue and followed some online script I'm not even sure how to find again.  Somehow following those instructions has broken my wifi adapter so my system doesn't see any network adapters at all. I finally found how to hit escape on boot and go into the Grub menu to load an old kernel and re-enable networking but it seems after I reboot it goes back to the newest kernal and no networking again.  I have tried enabling networking when in the new kernel but nothing works. Any tips for a REALLY new person on how to fix my broken kernal (the latest)?

---

### Post by grahammechanical on 2021-07-26
The WiFi adapter is not broken. I say that because when you log in to Ubuntu with the older kernel you get a WiFi connection to the hub and from there to the internet. Am I correct? Therefore, the WiFi adapter is still working.

When running on the older kernel what did you do to re-enable networking? Please explain what you are doing. There are some commands to run that will give information. Please run the commands in both kernels for comparison and post the printouts in this thread

```
iwconfig
```

```
rfkill list
```

There are other commands that might help. But they have to be found. It could be that you have switched off WiFi in Ubuntu with the newer kernel. We need a command that will switch it back on. There was a command that could switch networking on and off but its code is not installed by default in Ubuntu any more. Did you by any chance run a command to install something called ifupdown? And then did run ifdown as a command?

Regards

---

### Post by ActionParsnip on 2021-07-26
Does the system have a make and model?

---

