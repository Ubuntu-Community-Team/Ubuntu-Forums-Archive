---
title: "browser size too small"
date: 2012-10-13
forum: New to Ubuntu
---

### Post by vegas89 on 2012-10-13
Please help, I am using Ubuntu 12.4 my browser window is only half the size of my screen. I have reset Firefox and tried using the mouse to expand the window size but nothing seems to work. Please advise:confused:

---

### Post by Lyfang on 2012-10-13
What about other programs? Have you tried Chromium?

---

### Post by NikTh on 2012-10-13
> **vegas89 said:**
> Please help, I am using Ubuntu 12.4 my browser window is only half the size of my screen. I have reset Firefox and tried using the mouse to expand the window size but nothing seems to work. Please advise:confused:

Open a terminal (Ctrl+Alt+t) and give the results*****

```
/usr/lib/nux/unity_support_test -p
```

*****Put the results between the brackets [noparse]```
Here
```[/noparse]. 

Thanks

---

### Post by vegas89 on 2012-10-13
Thanks, I dowloaded Chrome , installed it to my desktop, but can't get it to the launcher to try it.

---

### Post by vegas89 on 2012-10-13
vegas@vegas-desktop:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Desktop 
OpenGL version string:  3.0 Mesa 8.0.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
vegas@vegas-desktop:~$

---

### Post by NikTh on 2012-10-13
```
sudo apt-get install chromium-browser
``` 

Then click on Dash and write **Chromium**

Thanks

---

### Post by vegas89 on 2012-10-13
Thanks  for that help with the dash. As for the size of the windows, I have the wobbly windows effect installed and if I click and drag the window to the top of the screen, Bam the window will fill the screen. Problem Solved!):P

---

### Post by Lyfang on 2012-10-14
> **vegas89 said:**
> Thanks  for that help with the dash. As for the size of the windows, I have the wobbly windows effect installed and if I click and drag the window to the top of the screen, Bam the window will fill the screen. Problem Solved!):P
Remember to mark thread as solved.

---

### Post by vegas89 on 2012-10-14
Please tell me how to do that, I know I will need your help again, Thanks!

---

