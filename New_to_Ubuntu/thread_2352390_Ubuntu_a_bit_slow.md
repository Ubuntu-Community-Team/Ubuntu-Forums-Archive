---
title: "Ubuntu a bit slow"
date: 2017-02-12
forum: New to Ubuntu
---

### Post by alexangel on 2017-02-12
Hi there everyone.
I just installed Ubuntu (64 bits) on my old computer (latest version, updated) and I'm liking it so far there is just one problem.
It seems to be a bit slow compared to my previous OS (Windows 7).
Youtube for example kinda seems a bit off. And if I try in HD streaming even if it's in 720p, forget it! It's slow as hell!
Is this normal? Is Ubuntu this heavy?
Or there's something I can do to boost performance?

My computer specs are: 
-Intel Pentium D 3,2Ghz (2cores);
- 4GB ram DDR2;
- Ati Radeon HD 4650 1GB.

Thanks o/

---

### Post by Perfect Storm on 2017-02-12
You may try some lightweight distros like Lubuntu or elementary OS. But I supect that the Ati Radeon HD 4650 is the sinner of your troubles.

---

### Post by mastablasta on 2017-02-12
check if the card is propperly recognised and if the drivers are loaded.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

> [h=1]Testing the driver[/h] To look for boot messages/errors, check 
dmesg | egrep 'drm|radeon'To  see your OpenGL information, you can run the commands below. Make sure  your OpenGL renderer string does not say "software rasterizer" or  "llvmpipe" because that would mean you have no 3D hardware acceleration:  
sudo apt-get install mesa-utils
LIBGL_DEBUG=verbose glxinfo

---

