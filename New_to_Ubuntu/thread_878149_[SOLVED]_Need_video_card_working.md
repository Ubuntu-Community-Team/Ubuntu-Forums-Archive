---
title: "[SOLVED] Need video card working"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by TJCIB on 2008-08-02
I have a GeForce4 MX 440 AGP 8x video card.
I know it's old, its a computer donated to our school.

Without the normal driver I get 800x600 resolution
With the restricted driver I can only get 640x480.

Can someone point me in the right direction.  Right now I'm working with the restricted driver disabled.

Thanks.

---

### Post by jualin on 2008-08-02
Try installing the "nvidia-settings" package using Synaptic Package Manager or via terminal > sudo apt-get install nvidia-settings so you can control the resolution. Remember that nvidia-settings only works with the restricted driver installed. After you install it you can open nvidia-settings via terminal but you need to open it as root > sudo nvidia-settings and then change the resolution and save the X file. Hope this works!

---

### Post by TJCIB on 2008-08-02
```
library@server:~$ sudo nvidia-settings

ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.


ERROR: Unable to determine number of NVIDIA VCSCs on ':0.0'.

```

doesn't give me the option to change resolution or anything

---

### Post by TJCIB on 2008-08-02
wait, I think I got it........

---

### Post by TJCIB on 2008-08-02
got it, thanks

---

### Post by jualin on 2008-08-02
Did you install the restricted drivers and the nvidia-settings package?

****omit this post, didn't refresh the screen quickly enough :lol:***

---

### Post by jualin on 2008-08-02
> **TJCIB said:**
> got it, thanks

Were you able to change the resolution?

---

### Post by TJCIB on 2008-08-02
yes, resolution is changed and desktop effects are working normally...

---

### Post by jualin on 2008-08-02
Ok, I am glad you got it working.

---

