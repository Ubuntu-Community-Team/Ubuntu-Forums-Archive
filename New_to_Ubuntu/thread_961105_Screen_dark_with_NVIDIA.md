---
title: "Screen dark with NVIDIA"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by nickmayfield on 2008-10-28
i'm new to ubuntu/linux. i have the new nvidia driver installed and working fine. my screen was really dark so i adjusted it accordingly to make it normal in the nvidia x server settings. now my problem is when i reboot it really dark again, but if i go to system/administration/nvidia x server setting and just click on it and close it everything goes back to normal. can anyone help me fix that. thanks for your time
Nick

---

### Post by Perfect Storm on 2008-10-28
Open the terminal (Applications ---> Accessories ---> terminal)
Type;
```
gksudo nvidia-settings
```
The reason that the other didn't work is that you need "admin" access to make the change.

---

### Post by nickmayfield on 2008-10-28
that was what i did and when i restart it goes dark again.

---

### Post by Perfect Storm on 2008-10-28
Which version of the driver are you using?

---

### Post by zxscooby on 2008-10-28
How is the brightness set in your power management profile?

---

### Post by nickmayfield on 2008-10-28
i'm using nvidia driver 177.80
as for the settings for the color. if i change the gamma up a little bit everyting looks fine. but when i restart it all goes dark again. but once i click on the nvidia x server and it opens then i close it then everything normal. so confused

---

### Post by ajwaite on 2008-11-08
I'm having the same problem as you with nvidia driver 177.80. My system is MythBuntu 8.10 with a GeForce 6200 128MB AGP 8X using TV-out. I have tried switching between using my LCD monitor using DVI or VGA with no change but once I go to Applications -> System -> Nvidia Settings miraculously the screen instantly brightens up and it works as long as I'm logged in but once I logged out and back in it goes back to dark again. I checked my running settings using "ps -awx" and I don't see anything related to nvidia or xorg. Maybe the nvidia driver is not getting initialized at startup?

---

