---
title: "Sharing folders with Mac OS X"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by Thievrey Corporation on 2008-08-17
Hello all,

I've been trying for few days now to share  folders between a PC running Ubuntu 8.04, and a MacBook (running under Leopard).

The MacBook can see the PC (named Ubuntu), but none of the shared folders.

In Ubuntu, I installed Samba: I could activate the sharing options of some folders: but they never show-up on the MacBook.

I am running Ubuntu from the LiveCD, and network is over WiFi.

Any suggestions ?

Thanks,

TC

---

### Post by gobbles414 on 2008-08-17
Try entering *gksu shares-admin* in the command line. This may give you access to more sharing options in Ubuntu. Let me know if this helps.

---

### Post by Thievrey Corporation on 2008-08-18
Hello,

thanks for your kind help. I'll try tonight, and will let you know.

---

### Post by Thievrey Corporation on 2008-08-18
I found a solution on the section Apple users.
I installed openssh-server

sudo apt-get install openssh-server

Found the IP of the Ubuntu machine:

sudo ifconfig

Installed Fugu on the Mac (freeware - light)

And connect via Fugu:

Connect to: IP adress
Username : Ubuntu session username
Password: Ubuntu session username

Don't know about the security, but the interface in Fugu is quite nice !

Thanks anyway.

TC

---

### Post by gobbles414 on 2008-08-18
> **Thievrey Corporation said:**
> I found a solution on the section Apple users.
I installed openssh-server

sudo apt-get install openssh-server

Found the IP of the Ubuntu machine:

sudo ifconfig

Installed Fugu on the Mac (freeware - light)

And connect via Fugu:

Connect to: IP adress
Username : Ubuntu session username
Password: Ubuntu session username

Don't know about the security, but the interface in Fugu is quite nice !

Thanks anyway.

TC I think that my idea would have worked. But I guess what really matters is that you've solved the problem to your satisfaction.

---

