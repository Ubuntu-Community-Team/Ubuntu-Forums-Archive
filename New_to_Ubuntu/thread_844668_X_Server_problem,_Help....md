---
title: "X Server problem, Help..."
date: 2008-06-29
forum: New to Ubuntu
---

### Post by Unewbeginner on 2008-06-29
Hi Everyone,

My computer worked pretty well before. Today I did some regular update and then I can't get into the UI.

I use Ubuntu 7.04. My monitor is a 19" Hanns.G and my Graphic card is nVidia Geforce 8800GT.

the system message is "Faliled to start the X server"
Could anyone let me know what I should do? 

Thanks

---

### Post by nowshining on 2008-06-29
more than likely u did a kernel update - u gotta re-install the nvidia drivers - i heard in hardy the dpkg-reconfigure-xorg or something has  changed to something else so I won't know right now as I don't use hardy.

---

### Post by neurostu on 2008-06-29
Can you get a terminal?

If you can try:

If you're using the Ubuntu distributed nvidia driver
```

sudo apt-get remove nvidia-glx-new

```

Then reboot, and reinstall the driver.

If you're not then I suggest downloading the latest nvidia driver from nvidia.com and then installing it over the terminal

---

