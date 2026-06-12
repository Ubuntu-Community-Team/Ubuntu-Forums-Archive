---
title: "Question with installing Nvidia drivers"
date: 2011-12-01
forum: New to Ubuntu
---

### Post by rapalmer19 on 2011-12-01
I'm brand new to Linux and I'm trying to install graphics drivers. Ive got a Nvidia 9600GT, and the latest version is 290.10. I managed to get as far as installing them ( I had to turn off xserver, did it in the terminal and rebooted) but now the xserver won't start. It says API mismatch: the Nvidia kernel module is ver 173.14.30 but the driver component is ver 290.10. 

So my question is this: how can I update the kernel to match the new driver version?

---

### Post by staf0048 on 2011-12-01
Is there a reason why you didn't just install the driver version that's included with Ubuntu?

From nVidia's site:

Note that many Linux distributions provide their own packages of the NVIDIA Linux Graphics Driver in the distribution's native package management format. This may interact better with the rest of your distribution's framework, and you may want to use this rather than NVIDIA's official package. 

That aside:

Did you do the following command after the installation?

```
nvidia-xconfig
```

Other than that, you might be looking at a bunch of work to get that specific version of the driver working.  See: [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual) for a complete set of instructions if you wish to pursue this path.

---

### Post by anewguy on 2011-12-02
I know for my GeForce 9500GT I just used the restricted drivers to select a driver and install it.  You really shouldn't need to get anything from the vendor.

Dave ;)

---

### Post by rapalmer19 on 2011-12-02
Hmm I guess I missed that on the Nvidia page. I think I'm going to try the other path just to learn how to do it though, so thanks for that link. 

Could you please tell me what blue text means in a directory? I tried to do Nvidia-xconfig, it says unable to write to directory, but I can see it in /etc in blue text. How can I get into that folder?

---

### Post by mikewhatever on 2011-12-02
The blue in terminal usually means a directory.

I'd also recommend using the Additional Drivers utility instead of nvidia.com. First, it's more user friendly, and second, you won't have to reinstall the driver after every kernel update.

---

### Post by anewguy on 2011-12-02
nvidia-xconfig requires super user priviledges -> just type:

sudo nvidia-xconfig


Dave ;)

---

### Post by crazy bird on 2011-12-02
Try adding this PPA to update your Nvidia drivers:
 
- open a terminal
- type the following command:
**sudo add-apt-repository ppa:ubuntu-x-swat/x-updates **
-type the following command:
**sudo apt-get update**
-type the following command:
**sudo apt-get upgrade**
 
Then reboot.

---

### Post by rapalmer19 on 2011-12-02
Ok this is turning out to be harder than I thought. I tried running those commands and it seemed like it was working, but my x server still won't start. I want to uninstall the drivers I put in so I can use the restricted drivers instead, can anyone please tell me how to do that?

---

### Post by jramshu on 2011-12-02
Since you installed the drivers from the site, you may be having a conflict with the nouveau drivers loading first at start and crashing x.

I run 10.04 LTS on here and it can be 'touchy' installing the drivers manually. Haven't tried it on 11.10.

---

### Post by staf0048 on 2011-12-02
> **rapalmer19 said:**
> Ok this is turning out to be harder than I thought. I tried running those commands and it seemed like it was working, but my x server still won't start. I want to uninstall the drivers I put in so I can use the restricted drivers instead, can anyone please tell me how to do that?

That sucks.  Have you already tried running?

```
sudo sh NVIDIA* --uninstall
```

---

