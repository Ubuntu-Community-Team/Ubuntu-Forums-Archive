---
title: "Performance issues with Ubuntu 13.10, 64-bit install"
date: 2014-04-15
forum: New to Ubuntu
---

### Post by mike171 on 2014-04-15
Performance issues with Ubuntu 13.10, 64-bit install.

Two Quad core Xeon @ 3.20GHz, 3 GB memory, Super Micro X7DB8 motherboard.

The machine is fairly old (2006), but a nice machine.  

I had been running Windows Server 2003 on the machine and performance was good.  After installing Ubuntu desktop 64-bit, performance is slow, at least as far as the graphics side of things is concerned.  I have not had the patience to do more thorough testing.

Moving windows around the screen is extremely frustrating as the move of the window lags behind the move of the mouse.

Graphics card is an onboard ATI ES1000.

Default ATI/Radeon graphics driver seems to be loaded properly and appears to support this "card."

Tried suggestions from the Internet to make system changes using Compix.  Unfortunately, the changes made no difference.

Installed Gnome 3 and graphics performance is much better, but the system overall still appears slower than I would expect.

Other than abandoning Ubuntu and installing Xbuntu or Lubuntu, are there any other suggestions?

Would a new graphics card make any difference?

Thanks for any input.

---

### Post by meistersreign on 2014-04-15
Your computer specs aren't that bad, but put it simply yes I think that an updated graphics card would do wonders for you. A lot of what you see on the desktop nowadays is pretty heavy as far as graphics are related, and if you want to keep Ubuntu instead of another flavor your best bet would probably be that upgrade.

---

### Post by Canterwood on 2014-04-15
A new graphics card is an option, but you could also try a few desktop environments. However, if you're using the machine as a server (as I'm deducing from the fact that you used to run Windows Server 2003) installing a GUI is usually considered bad practice since the desktop environment is taking up resources that could be better spent. Once your server is up and running, it's usually a case of set it and forget it aside from the occasional maintenance. You should think about controlling the machine via command line, either over SSH or with physical access.

If you do want to try another desktop environment you should have a look at XFCE and LXDE. They both have a light footprint. You don't have to reinstall the OS, you can use the commands:

```
sudo apt-get install xubuntu-desktop
```

For Xubuntu and

```
sudo apt-get install lubuntu-desktop
```

For Lubuntu.

---

### Post by protoss96 on 2014-04-15
> **mike171 said:**
> Performance issues with Ubuntu 13.10, 64-bit install.

Two Quad core Xeon @ 3.20GHz, 3 GB memory, Super Micro X7DB8 motherboard.

The machine is fairly old (2006), but a nice machine.  

I had been running Windows Server 2003 on the machine and performance was good.  After installing Ubuntu desktop 64-bit, performance is slow, at least as far as the graphics side of things is concerned.  I have not had the patience to do more thorough testing.

Moving windows around the screen is extremely frustrating as the move of the window lags behind the move of the mouse.

Graphics card is an onboard ATI ES1000.

Default ATI/Radeon graphics driver seems to be loaded properly and appears to support this "card."

Tried suggestions from the Internet to make system changes using Compix.  Unfortunately, the changes made no difference.

Installed Gnome 3 and graphics performance is much better, but the system overall still appears slower than I would expect.

Other than abandoning Ubuntu and installing Xbuntu or Lubuntu, are there any other suggestions?

Would a new graphics card make any difference?

Thanks for any input.

Hi, mike

You should try to install ATi drivers it will help perfomance alot. Just open dash and type "drivers" and application named Drivers should appear, then click on it and there would be some recomendations for graphics driver you should check the driver you want to install then wait for installation and then reboot. It's probably low performance because you don't have full graphics driver, it happens on windows too.

---

### Post by mike171 on 2014-04-15
That definitely helped!  I ended up installing several desktops.  Xubuntu seems to be the most responsive of those I tried (Kubuntu, Lubuntu, Xubuntu, Gnome, Unity).

I'm attempting to run virtual machines on this machine using VirtualBox.  This machine will be accessed by users and I do not want them (or myself, honestly) fumbling with command prompts.

I imagine there is a way to manage VMs on a macine with no GUI using commandlines or Web interface and still be open source, but this is where I'm at so far.

I'm copying a 125 GB folder to this machine now and finding that the network transfer speeds are only 22 mbs and the machine is not very responsive during the process.  CPU and memory usage are very low.

I imagine there is an issue with the NIC driver as well.  This machine has 2 GB NICs and is on a GB network.

---

### Post by mike171 on 2014-04-15
I will try installing the ATI drivers next.  Thanks.

---

### Post by Canterwood on 2014-04-15
How exactly will the users access the machine? Locally, or remotely?

If it's the latter there's a few options to get client computers to control the VM's on the server.

---

