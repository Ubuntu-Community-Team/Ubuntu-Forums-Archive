---
title: "Available updates"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by Dermot Doyle on 2008-10-18
Is there somewhere I can see a list of currently available updates? Like many people I updated my computer this morning and the sound stopped working. None of the suggestions I found in these forums worked for me so I have set the previous kernel as a default. However, I did notice that one of the updates improved the touchpad on my laptop and would like to download that if it is not simply part of the -21 kernel. Is that possible, or have I missed something fundamental?

---

### Post by Dougie187 on 2008-10-18
There are a couple things that you can do to check for updates. You can simply push ALT+F2 and type "Update-manager" and then a screen will come up with any updates that are available that you do not have.

In synaptic there is a special button for marking all updates as well. And if you are into using the terminal, you can type
```
sudo apt-get update && sudo apt-get upgrade
```

But if what you are looking for was in fact an upgrade, then you probably already have it. You can paw around in synaptic for it if it is not though.

---

### Post by Dermot Doyle on 2008-10-18
Thanks for the reply. I just want to try to understand what's happening so can you clarify? Since I downloaded the latest eighteen updates this morning, my computer thinks that it's up to date so the upadate manager shows nothing. Now that I'm starting the computer using the previous 2.6.24-19 kernel to get around the sound problem and the touchpad is back to its poor performance, does that mean that all 18 updates (including the one that improved the touchpad performance) were part of the new 2.6.24-21 kernel?

---

### Post by philinux on 2008-10-18
[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/283790](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/283790)

Read down the list some have fixed the sound.

---

### Post by Dermot Doyle on 2008-10-18
Yes I tried all of that before from another thread. The first two sets of commands simply brought up problems of 'no such file or directory' each time. The last seemed to install something and reboot, but unfortunately it still doesn't work.

---

