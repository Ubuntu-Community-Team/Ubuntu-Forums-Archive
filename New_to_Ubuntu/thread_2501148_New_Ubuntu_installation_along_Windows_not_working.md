---
title: "New Ubuntu installation along Windows not working"
date: 2024-09-24
forum: New to Ubuntu
---

### Post by jefemaestro6117 on 2024-09-24
Hi everyone.

I'm new using Ubuntu. I was using Ubuntu through VirtualBox for 1 month, even along Windows without issues.

I tried to install Ubuntu 24.04.1 on my PC with Windows. Windows works, but I can't log in on Ubuntu after installation finish. I write my password for the first log in, but nothing happen.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294301&stc=1[/IMG] *Screenshot taken from Virtual Box

I tried to reinstall Ubuntu with default options, but it doesn't works neither.

My PC:
Main OS: Windows 11
CPU: Ryzen 5 5600G
RAM: 16 GB
GPU: RX 6600
Motherboard: Gigabyte GA-A320M-S2H
Storage: 1x NVMe 1TB, 1x SSD SATA 2TB and 1x HDD 1TB
DP Monitor plugged in GPU *used for gaming
HDMI Monitor plugged in Motherboard (iGPU) *Used for multimedia and browsing



=======
UPDATE
=======

I reinstalled Ubuntu like the first attempt but I unplugged HDMI Monitor (plugged in Motherboard).
The installation finished and I can login without no issues. I think probably I have to research why I cannot use my secondary monitor using iGPU


=======
UPDATE 2
=======

Ubuntu works fine without the second monitor.

---

### Post by TheFu on 2024-09-25
You can try using a different GUI display server by clicking on the "gear" in the lower right-hand corner and choosing the "Xorg" option. This will use Xorg instead of Wayland for the graphical server.  Xorg has been around since the early 1990s. Wayland isn't quite stable for all uses yet, though it is best supported using the GPU and iGPU that you have.  

I'm just guessing.  I have the same GPU/APU that you do, but a different motherboard (different vendor).  The B320 MB chipset are a bit older. I have a B450-based motherboard. That makes me wonder about the support for the new CPU/APU.  Found this: [https://steamcommunity.com/discussions/forum/11/3395163747102652073//1000](https://steamcommunity.com/discussions/forum/11/3395163747102652073//1000)  but don't know how relevant those gamer's comments are in your situation.  Sometimes gamers are superstitious about hardware?  IDK.

---

### Post by cryofreeze666 on 2024-09-25
i had that problem also, what solved it for me was unplugging second hard drive so windows and linux could be installed on the same drive.  for some reason linux kept installing on second drive when i would click the alongside option.   turned out to just be easier to unplug hardware, then format second drive later.  hope that helps.  otherwise i'm just as new as you., about 2 1/2 months now, since windows finally p***ed me off enough to throw all my copies in the trash.

---

### Post by jefemaestro6117 on 2024-09-25
I didn't find the "gear" ;-;
But the issue also happen with LiveCD as soon as I change the position of the monitors.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294304&stc=1[/IMG] *Image from windows.

Issue video
[https://youtu.be/dl4f1NQxQio](https://youtu.be/dl4f1NQxQio)

I think the login loop could be for GPU/iGPU issues.

Talking about a320 chipset... 
It's old, but there are no issues compared with a520. Both aren't recommended for overclock and lacks conectivity (USB, fans, M.2, SATA ports, etc.). A320 chipset only lacks PCI Express 4.0.

---

### Post by TheFu on 2024-09-25
The "gear" is in the image you posted originally.  That icon in the bottom right corner.  Click it.

---

### Post by jefemaestro6117 on 2024-09-25
Oh. I erase all ubuntu data from my disk #-o
The gear wasn't available on Live CD :c.
Let me reinstall ubuntu to try.

---

### Post by jefemaestro6117 on 2024-09-25
> **cryofreeze666 said:**
> i had that problem also, what solved it for me was unplugging second hard drive so windows and linux could be installed on the same drive.  for some reason linux kept installing on second drive when i would click the alongside option.   turned out to just be easier to unplug hardware, then format second drive later.  hope that helps.  otherwise i'm just as new as you., about 2 1/2 months now, since windows finally p***ed me off enough to throw all my copies in the trash.
It looks like the issue is because I tried to use my second monitor with iGPU instead GPU.

But thanks for the help c:

---

### Post by jefemaestro6117 on 2024-09-25
> **TheFu said:**
> The "gear" is in the image you posted originally.  That icon in the bottom right corner.  Click it.
For unknow reason, I still without find the gear. I can find it in Virtual Box.

But now I can login. I just needed to unplug HDMI monitor, but the login loop starts when I plug the second monitor. 
If I unplug the second monitor again; I can login, but all opened apps are closed.

---

### Post by cryofreeze666 on 2024-09-29
i don't understand what you all are talking about because i'm new to ubuntu, i have questions so i can understand better what you're saying (in other words trying to learn).  ok, it seems like jefemaestro6117 is using 2 monitors, if i understand what i read correctly.  i stopped using 22.04 because i didn't know how i was "magically" opening work stations with that version, and couldn't get programs back that were connected to the subsequent work station after i thought i closed them.  so if he is opening workstations to use two monitors, why would he loose the information when unplugging a monitor?  why is it he can't keep the info he wants, and why couldn't i get rid of it?  the computer that happened to, has riser cards for multiple gpu's, if that would make a difference.

---

### Post by jefemaestro6117 on 2024-09-30
> **cryofreeze666 said:**
> i don't understand what you all are talking about because i'm new to ubuntu, i have questions so i can understand better what you're saying (in other words trying to learn).  ok, it seems like jefemaestro6117 is using 2 monitors, if i understand what i read correctly.  i stopped using 22.04 because i didn't know how i was "magically" opening work stations with that version, and couldn't get programs back that were connected to the subsequent work station after i thought i closed them.  so if he is opening workstations to use two monitors, why would he loose the information when unplugging a monitor?  why is it he can't keep the info he wants, and why couldn't i get rid of it?  the computer that happened to, has riser cards for multiple gpu's, if that would make a difference.
I realized they are trying to help me with answers that maybe are far from fixing the issue. But I understand that I didn't give enough information.

I tagged this thread as solved because Ubuntu works ignoring the second monitor issue. So I start a new thread looking for help about the actual issue.
[https://ubuntuforums.org/showthread.php?t=2501222](https://ubuntuforums.org/showthread.php?t=2501222)

---

