---
title: "Jammy Jellyfish - Surface Pro 6 - No touchscreen with Ubuntu dual boot"
date: 2022-04-26
forum: New to Ubuntu
---

### Post by normstraker on 2022-04-26
I just installed 22.04 along side my windows 10 on my Surface Pro 6.  I have no touchscreen at all when in Ubuntu. (works fine in windows) I assume this is a driver issue? I would greatly appreciate some help.

---

### Post by tea for one on 2022-04-28
Here is a website with info about Microsoft Surface devices and Linux.
[https://github.com/linux-surface/linux-surface/wiki/Supported-Devices-and-Features#feature-matrix](https://github.com/linux-surface/linux-surface/wiki/Supported-Devices-and-Features#feature-matrix)

Your device SP6 [COLOR="#0000FF"]Requires linux-surface kernel[/COLOR]

I'm only supplying info, I do not own a Microsoft Surface Laptop.

---

### Post by normstraker on 2022-04-28
Thanks for the link.  I tried my best to follow the guide however when rebooting the new kernel i get error: bad shim signature and error: You need to load the kernel first. This is above my head!

---

### Post by tea for one on 2022-04-28
Disable secure boot in your UEFI settings and see if you can launch Ubuntu?

---

### Post by normstraker on 2022-04-28
Yes! Thank you! Booted to UEFI (Surface UEFI), Security tab, Secure Boot - change configuration.  Has 3 choices, Microsoft only (didn't work), Microsoft & 3rd party CA (didn't work), and None (Worked!)  Hope this helps someone else as well.  Thanks 'tea for one'

---

### Post by tea for one on 2022-04-29
> **normstraker said:**
> Yes! Thank you! Booted to UEFI (Surface UEFI), Security tab, Secure Boot - change configuration.  Has 3 choices, Microsoft only (didn't work), Microsoft & 3rd party CA (didn't work), and None (Worked!)  Hope this helps someone else as well.  Thanks 'tea for one'

Marking the thread as solved will make it more visible and hopefully other users/searchers may find the info. useful.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

