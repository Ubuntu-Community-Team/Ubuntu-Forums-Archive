---
title: "need help installing nvivia drivers on new xubuntu install"
date: 2013-04-26
forum: New to Ubuntu
---

### Post by s1baker on 2013-04-26
hi,
I am about to install nvidia video drivers on a new xubuntu 12.04 install.
Questions:

1) Will the new xubuntu install recognize the nvidia video card and install the drivers automatically
    and will these drivers be the open source drivers or will they be nvidia proprietary drivers?

2) If I need to install the nvidia proprietary drivers after my xubuntu install, will I need
    to wipe out the drivers that are in xubuntu first and then install the nvidia proprietary
    drivers, or does it matter?

Thanks

---

### Post by agnewton on 2013-04-26
I have subscribed to your thread because I am interested in the response of the community.

to question #1:
I think that the open source drivers will be installed by default.  And if they aren't, you should be able to install them from the terminal (sudo apt-get install nvidia-current).  The open source drivers should work. They (for the most part) have for me.

to question #2:
I  don't know if you'll have to wipe the open-source drivers out, but you might need to  blacklist them (or chronically re-install the proprietary driver everytime there is an  update that effects the display/ X-window/ etc.)

My answer is  experiential (and not based on a thorough study of the ?ubuntu  architecture).  My experience kind of goes like this...

I  upgraded from Ubuntu 10.04 LTS to 12.04 LTS and had no problems with the  video driver with the exception of one open source program.  I have an  NVidia GeForce GTX 550 Ti card and it has worked with the available  "version current" and "post-release updates" without incident (except  for the one open source program).  The authors of the conflicting  program recommend the proprietary drivers, but it seemed to have no  effect.  I am running the NVIDIA-Linux-x86_64-310.44 driver. The problem  I have is with the program trying to use the GPU as the "CUDA  accelerator". The X11 "Composite" extension is not consistent with the  code- this extension results in an unstable video display that on  occasion crashes the OS.  If I disable the "Composite" setting, the  program doesn't crash the OS, but the video display for the OS is less  than "sleek" (it has big, chunky, borders around many of the app windows  and notification dialogs- very MS-DOS).

So, if my experience with the Unity  interface (with the one exception) is an indication, then you're  probably right to ask the question but might not notice any conflicts  depending on the your software.

For what it's worth.

---

