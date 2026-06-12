---
title: "AMD Driver crashes on bootup on Ubuntu 17.04"
date: 2017-06-20
forum: New to Ubuntu
---

### Post by freeos2017 on 2017-06-20
Hello all,
I recently installed the amd graphics driver straight from the website. I followed their instructions first to extract the tar.xz. I then ran this command, "./amdgpu-pro-install -y". This ran perfectly fine except for when I booted my computer back up. When I started ubuntu again, I received the low graphics mode. Since nothing happened I used the Ctrl+Alt+F1 to get to a command prompt. I then removed the drivers using the command "amdgpu-pro-uninstall". After that I rebooted my computer and it booted up normal.

Does anybody have any ideas of what to do to get this to run? I'm using the amdgpu-pro-17.10-429170.tar.xz driver for my amd r9 380x. 

Any help appreciated. 

Thanks

---

### Post by freeos2017 on 2017-06-21
Found out that AMD has not released a driver for 17.04 for my graphics card. Since this is the case, I will "downgrade" to 16.04.

---

