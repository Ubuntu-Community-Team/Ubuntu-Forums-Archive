---
title: "Intel Graphics problem with 12.04 LTS"
date: 2014-02-16
forum: New to Ubuntu
---

### Post by DrScum on 2014-02-16
I just bought a brand new Laptop from Linux Online Shop (Germany) with a 4th Generation Intel i5 processor. The system came with 12.04 LTS preinstalled. During customization I found out that Unity is running in 2D mode. I was trying to fix that first by getting the Intel graphics driver manager from the intel website which gave me the error messager "release not supported".

Then I added the ppa:xorg-edgers/ppa -y repository following this thread [http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error](http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error)

Upon adding the repository 30 upgrades became available that sounded like they had something to do with graphics. Upon installing those upgrades, the system hangs in low graphics mode when I boot it.

What do I do?

---

### Post by monkeybrain20122 on 2014-02-16
I can be wrong, but my guess is that the kernel in 12.04 is too old for 4th generation. 

So you should probably first remove xorg-edger and revert the changes by
```
sudo ppa-purge ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade

``` 

Now check your kernel version, type the following in the terminal and see the output.
```
uname -r
```

If it is 3.2 something it is probably too old.
Then upgrade your kernel to the 13.10 version [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy/)
make a folder somewhere, say in Downloads and give it a name, say ker
Download from the link above 3 packages and save them in ker
linux-headers all
linux-headers generic
linux image generic

For the latter two choose amd64 or i386 depending on whether you have 64 or 32 bit os
then in the terminal

```
cd Downloads/ker
sudo dpkg -i *.deb
```

When done, reboot.
[B]
Edited:[/B] there are probably simpler ways to ubdate kernels (and graphic stacks) via the  hardware update support, 13.10's kernel and graphic stacks are enabled by default for the new 12.04  point release (12.04.4?) but i have no idea if you can switch to it from  earlier point releases, I don't have 12.04.

---

### Post by DrScum on 2014-02-16
the command sudo ppa-purge.... yields "ppa-purge command not found"

---

### Post by deadflowr on 2014-02-16
> there are probably simpler ways to ubdate kernels via the  hardware  update support, it is enabled by default for the new 12.04  point  release (12.04.4) but i have no idea if you can switch to it from   earlier point releases, I don't have 12.04.                 

You can install the lts-name-of-release packages as explained here
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)



**Edit**: run 
```
sudo apt-get install ppa-purge
```
then try the ppa-purge command again.

---

### Post by monkeybrain20122 on 2014-02-16
You should install it when you install from xorg-edgers, they told you to specifically [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) :)
so
```
sudo apt-get install ppa-purge
```

---

### Post by DrScum on 2014-02-16
the kernel version is 3.11.0-15 generic

---

### Post by monkeybrain20122 on 2014-02-16
Seems kernel is ok. Can you tell us the model of your laptop?

What are the outputs for
```
lshw -C display
```

---

### Post by DrScum on 2014-02-16
Thanks deadflowr!

this pointer
You can install the lts-name-of-release packages as explained here
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
did it, my system is back in shape AND it has 3d graphics mode now

---

