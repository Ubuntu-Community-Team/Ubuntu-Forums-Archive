---
title: "System won't boot or boots wrong."
date: 2008-10-15
forum: New to Ubuntu
---

### Post by Haruki-kun on 2008-10-15
I got the message with the kernel updates last night, so I downloaded them. As expected, this required a system reboot.

I rebooted the system, but when I did I realized that I had to re-install the drivers for the wireless network, so I looked up the instructions in a thread I made a while ago, and followed them again. I went to reboot the system again, but I was surprised when I realized that I couldn't boot at all.

I got the Ubuntu loading screen and the progress bar, but about one square before the end, the bar froze and didn't move. I left it there for a while, but it didn't budge. It just wouldn't boot.

I tried to boot into the other kernel (that is the appropriate term, right?), and I managed it, so I went on with daily business.

This morning, when I went to school, I turned on the computer and booted the old kernel again. Everything was as usual until I tried to get a wireless signal. It connected to the network, but FireFox refused to open any sites.

Why is this happening? And what can I do to fix it?

---

### Post by Aero-Z on 2008-10-15
> **Haruki-kun said:**
> I got the message with the kernel updates last night, so I downloaded them. As expected, this required a system reboot.

I rebooted the system, but when I did I realized that I had to re-install the drivers for the wireless network, so I looked up the instructions in a thread I made a while ago, and followed them again. I went to reboot the system again, but I was surprised when I realized that I couldn't boot at all.

I got the Ubuntu loading screen and the progress bar, but about one square before the end, the bar froze and didn't move. I left it there for a while, but it didn't budge. It just wouldn't boot.

I tried to boot into the other kernel (that is the appropriate term, right?), and I managed it, so I went on with daily business.

This morning, when I went to school, I turned on the computer and booted the old kernel again. Everything was as usual until I tried to get a wireless signal. It connected to the network, but FireFox refused to open any sites.

Why is this happening? And what can I do to fix it?
Make sure you installed the right wireless drivers for the new kernel.
It's a normal procedure that when new kernel comes out, you need to update your wifi drivers for that kernel.

---

### Post by Haruki-kun on 2008-10-15
> **Aero-Z said:**
> Make sure you installed the right wireless drivers for the new kernel.
It's a normal procedure that when new kernel comes out, you need to update your wifi drivers for that kernel.

Yes, but I can't boot the new kernel at all.

---

### Post by Aero-Z on 2008-10-15
> **Haruki-kun said:**
> Yes, but I can't boot the new kernel at all.
Try removing the wireless drivers for the new kernel and then try booting into it. If you can boot and got cable connection to work then try getting the new wireless drivers again and make sure that you get them for the right kernel and architecture and that you get all required packages.

---

### Post by Haruki-kun on 2008-10-15
Alright. How do I remove them?

---

### Post by Aero-Z on 2008-10-15
> **Haruki-kun said:**
> Alright. How do I remove them?
Which drivers do you have? How did you update them?
Best bet is to remove them using Synaptic.

---

### Post by Haruki-kun on 2008-10-15
Atheros drivers, I think it said.

But I'm sorry, I don't know. I don't know how to use synaptic, either. In fact, I don't know much about anything, I've only been using it for like 2 weeks or less. Furthermore, right now I'm on Windows, because Ubuntu is still not working with the wireless.

---

