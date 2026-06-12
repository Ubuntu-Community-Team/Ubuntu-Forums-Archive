---
title: "Cannot install Compiz Fusion."
date: 2008-08-01
forum: New to Ubuntu
---

### Post by chris24300 on 2008-08-01
Hello all, I have just installed ubuntu the other day and now I am looking to install Compiz Fusion. I searched online and found a few tutorials that made it seem pretty straight forward. I used the method where I go through System->Administration->Hardware Drivers. My computer finds the nVidia accelerated graphics driver and goes to download it. However, I receive errors during this process. Below are error I receive.

E: /var/cache/apt/archives/nvidia-glx_1%3a96.43.05+2.6.24.13-19.45_i386.deb: failed in buffer_read(fd)

Reading database... dpkg: error processing (.....).deb (--unpack):
	failed in buffer_read(fd): files list for package 'linux-ubuntu-modules-2.6.24-19-generic': Input/output error
Errors were encountered while processing:
	/var/cache/apt/archives/nvidia-glx_l%3a96.43.05+23.6.24.13-19.45_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:




Please help!!!!

- Chris

---

### Post by eightmillion on 2008-08-01
Could you try opening a terminal and installing the package manually with the command:
> sudo dpkg -i /var/cache/apt/archives/nvidia-glx_1%3a96.43.05+2.6.24.13-19.45_i386.deb

---

### Post by flytripper on 2008-08-01
err is it ubuntu hardy? isnt it already installed by default?

---

### Post by chris24300 on 2008-08-01
Thanks for the immediate reply. I do have Hardy (8.04) and I do believe it is installed. When I look at my desktop settings to change the effects from None to the highest grade, it brings me to the Accelerated Graphics Driver (still hasn't been installed) and it crashes there and gives me the error. I have not tried installing from the terminal yet, I will be doing that when I get home in a few hours. Thanks for the help, I'll let you know how it turns out.

- Chris

---

### Post by oldos2er on 2008-08-01
> **chris24300 said:**
> Thanks for the immediate reply. I do have Hardy (8.04) and I do believe it is installed. When I look at my desktop settings to change the effects from None to the highest grade, it brings me to the Accelerated Graphics Driver (still hasn't been installed) and it crashes there and gives me the error. I have not tried installing from the terminal yet, I will be doing that when I get home in a few hours. Thanks for the help, I'll let you know how it turns out.

- Chris

 Compiz-fusion is installed by default in Gutsy and Hardy. However, to make full use of it you should install the package compizconfig-settings-manager.

---

