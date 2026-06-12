---
title: "latest nVidia drivers cause Ubuntu to hang ..."
date: 2011-11-11
forum: New to Ubuntu
---

### Post by cwmoser on 2011-11-11
The last few versions of nVidia drivers cause my Ubuntu 10.04 AMD 64bit OS to hang when I enable Extra Visual Effects (Compiz).  The only version I can get to work properly with Compiz is version 260.19.44.  
The driver file is named:  NVIDIA-Linux-x86-64-260.19.44.run

Is there something I can do to get the later nVidia drivers to function with Compiz?

Thanks

Carl

---

### Post by crazy bird on 2011-11-11
Try using the Nvidia driver in synaptic: nvidia-current.
Does that change anything?

---

### Post by beew on 2011-11-11
> **crazy bird said:**
> Try using the Nvidia driver in synaptic: nvidia-current.
Does that change anything?

Nvidia-current in Synaptic is not current at all. The latest stable nvidia driver is 285.05
Which can be installed using this ppa.
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

A even newer one would be 290.06 beta, but at least on my Natty machine it has a side effect that gnome-terminal doesn't exit and uses 100% of cpu.

---

### Post by cwmoser on 2011-11-11
For some unknown reason, **NVIDA-Linux-x86_64-285.05.09.run** hangs my Ubuntu OS when I enable Compiz.  

The older *19.44.run driver works fine.

Carl

---

### Post by beew on 2011-11-11
> **cwmoser said:**
> For some unknown reason, **NVIDA-Linux-x86_64-285.05.09.run** hangs my Ubuntu OS when I enable Compiz.  

The older *19.44.run driver works fine.

Carl

If the older version works use it. But how do you install your driver? You do know that if you install manually you would have to reinstall each time you have a kernel update, don't you?

There is no advantage installing by downloading the .run file from Nvidia's site as far as I know, only more headaches. There is even less reason if you are installing an old version (some people want bleeding edge without knowing about the ppa option would install from Nvidia)

---

### Post by cwmoser on 2011-11-11
Yeah I have to reinstall on every Kernl update.
So how do I configure nVidia drivers so I don't have to reinstall?

Thanks,

Carl

---

### Post by beew on 2011-11-11
> **cwmoser said:**
> Yeah I have to reinstall on every Kernl update.
So how do I configure nVidia drivers so I don't have to reinstall?

Thanks,

Carl

Just click "Additional Drivers" and let it detect the driver version and install it for you. After that open a terminal and type "sudo nvidia-xconfig" , submit your password, wait for the output and then reboot, that's it. (the output will give an error message saying that xorg-conf is missing something and it has to make a new one, don't worry about it, that is normal) You can find "Additional Drivers" by searching it in the dash if you use Unity, it is under Systems > Administration if you use a "classic desktop"

If you want more up to date driver you should add the x-swat ppa  (linked to in my previous post) to your sources list before you run Additional Drivers. To do that open a terminal and type

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update


```Alternatively you can open Synaptic, go to Settings > Repositories > Other Software and click add and put in > ppa:ubuntu-x-swat/x-updates, then close the dialogue box and click the "reload" button, then close Synaptic.

If you are using 11.10 Synaptic is not installed by default, but it is a good package manager to have, much better than the Software Center, also you may want to install gdebi for right click install of .deb files. By default right click install of .deb is done by the Software Center, but with gedbi you would have finished installing before the USC even starts (of course you can also install .debs using the command "sudo dpkg -i name.deb"  )

To install these 

```
sudo apt-get install synaptic gdebi
```

---

