---
title: "Desktop does not show up"
date: 2013-07-01
forum: New to Ubuntu
---

### Post by Joel0604 on 2013-07-01
Hello, 
After type in my login password, the ubuntu boots in and the desktop does not show up. It just shows the background. Can't even figure out how to open the terminal from there. Anyways this happened after I installed ATI 2400 HD graphics driver and catalyst control center. I have ubuntu 12.04 LTS 64 bit. 

Thanks, 
Joel

---

### Post by deadflowr on 2013-07-01
Was this a new copy of Ubuntu from Ubuntu.com?
If so, then your running Ubuntu 12.04.2, which uses a newer xserver and is incompatible with the drivers for your card.
You'll need to uninstall those drivers, unfortunately.
Somewhere in here might help.
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Joel0604 on 2013-07-01
Yes its ubuntu 12.04 LTS from ubuntu.com. So how do I uninstall? The link that was posted doesn't show how to uninstall.

Thanks, 

Joel

---

### Post by deadflowr on 2013-07-01
Here's one method
[https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx)
The driver would be fglrx.

Of course with the card you have, I'm not sure what driver, whether fglrx or the legacy version you have installed.

You could see about removing it, through the additional drivers program, if you installed it through Ubuntu, and not through the AMD directly.

If you could tell us how you installed it, a better method for that one will help.

---

### Post by me2space on 2013-07-01
Does Ctrl + Alt + T open the terminal?

---

### Post by Joel0604 on 2013-07-01
Thanks for all your suggestions. I just did a fresh re-install of ubuntu. How/where do I install the open source drivers for my graphics card? ATI Radeon HD 2400 with ubuntu lts 12.04. 

Thanks

Joel

---

### Post by NikTh on 2013-07-01
> **Joel0604 said:**
> Thanks for all your suggestions. I just did a fresh re-install of ubuntu. How/where do I install the open source drivers for my graphics card? ATI Radeon HD 2400 with ubuntu lts 12.04. 

Thanks

Joel

Open source driver is pre-installed. You don't need to install anything. See the driver you use with this command ```
lspci -nnk | grep -iA2 vga
```. It should return **kernel driver in use: radeon** , then you are OK. 

If everything works OK with the open source driver, you can mark the thread as solved (see my signature for a how to). 

Regards
 NikTh

---

### Post by Joel0604 on 2013-07-01
I want to mark the thread solved, but that option doesn't come up when click thread tools D:

Joel

---

### Post by deadflowr on 2013-07-01
Sorry you had to do a reinstall, I was hoping you'd give more info so you would could avoid that.
Oh well, water under the bridge, I guess.

And yes, the open-source drivers are provided by default, so an out of the box system will be running those, and nothing else.

Solve markings solutions [here]("http://ubuntuforums.org/showthread.php?t=2121377").

---

### Post by NikTh on 2013-07-01
> **deadflowr said:**
> 
Solve markings solutions [here]("http://ubuntuforums.org/showthread.php?t=2121377").

Thanks for the link. I guess I must update my signature. :)

---

