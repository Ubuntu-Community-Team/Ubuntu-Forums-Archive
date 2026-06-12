---
title: "get restricted graphics driver to be used?"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by littletinman on 2008-04-29
Help!!1

 I just installed Hardy Kubuntu on a new partition and i need my Nvidia graphics card to be used instead of the vesa. How do i enable it to be used in the restricted drivers manager. It says "not in use" and i need it to be used. It has the check by it. Anyone got any ideas?

---

### Post by hermes0710 on 2008-04-29
Have you established an internet connection? Is the check box next to "not in use" checked???

An internet connection is required in order to let hardware manager to download and install the nvidia driver (check your software sources too)

---

### Post by littletinman on 2008-04-29
ok, restarting in a second. I think i may have got it.

---

### Post by littletinman on 2008-04-29
sweet. it worked. Thanks man.

---

### Post by hermes0710 on 2008-04-29
Glad i helped

---

### Post by Unix_Slayer on 2008-05-04
> **hermes0710 said:**
> Glad i helped


Now if you could explain to me how you get dual NVidia 9600 GT OC's [SLI] to work, I would be forever grateful.

---

### Post by hermes0710 on 2008-05-05
Unfortunately I have no experience in configuring these things. But my card is nvidia too and I do know that in "nvidia-settings" application there is an interface through which you may configure a second monitor. If it's not installed ```
sudo apt-get install nvidia-settings
```. Also,I think you should execute this application with root privileges (anyone to confirm this?).

If this is what you wanted get back to me and I will post my paypal account's info because "grateful" means nothing to me... :lolflag: Just kidding, good luck

---

### Post by alienexplorers on 2008-05-05
nvidia-settings does need to be run under root.  Just start terminal and enter:
> sudo nvidia-settings

---

