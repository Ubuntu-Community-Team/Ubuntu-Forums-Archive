---
title: "Dell Latitude D600"
date: 2015-01-20
forum: New to Ubuntu
---

### Post by molly_dog on 2015-01-20
I've played around with Ubuntu on disc & I've used it to repair some issues on the hard drive but, otherwise, I know very little about it.

I have an old Dell Latitude D600 Notebook with a Pentium M 1.6 GHz CPU (single core) & 2 GB of RAM. It originally was an XP Pro machine but I've had 32-bit Win 7 on it. It runs slowly & I haven't been able to ever get the wireless card to work because I could not find a driver that works. I'm using a USB dongle for wireless.

My question is which version of Ubuntu be the best option for this laptop? 

Thanks!

---

### Post by sandyd on 2015-01-20
> **molly_dog said:**
> I've played around with Ubuntu on disc & I've used it to repair some issues on the hard drive but, otherwise, I know very little about it.

I have an old Dell Latitude D600 Notebook with a Pentium M 1.6 GHz CPU (single core) & 2 GB of RAM. It originally was an XP Pro machine but I've had 32-bit Win 7 on it. It runs slowly & I haven't been able to ever get the wireless card to work because I could not find a driver that works. I'm using a USB dongle for wireless.

My question is which version of Ubuntu be the best option for this laptop? 

Thanks!

Can you run the following command in a terminal?
It will display information about your system, and allow us to recommend a lighter Ubuntu Distro. The default version of Ubuntu is heaver, both graphically and CPU-wise.
```

cat /proc/cpuinfo
lspci
lsusb
```

---

### Post by grahammechanical on 2015-01-20
The graphic adapter is an often overlooked component. What graphic adapter? How much of its own memory does it have? To run Ubuntu it is necessary that the graphic adapter be able to do hardware accelerated 3D rendering.

Have you run the Ubuntu Try Ubuntu live session? What is the user experience? You can download the ISO images for Xubuntu and Lubuntu and run them in a Try Ubuntu session. You might notice a big improvement.

[http://xubuntu.org/](http://xubuntu.org/)

[http://lubuntu.net/](http://lubuntu.net/)

There is also Ubuntu Mate which is in the process of becoming an official member of the Ubuntu family.

[https://ubuntu-mate.org/](https://ubuntu-mate.org/)

These three have a lower hardware specification than Ubuntu with Unity.

Regards.

---

### Post by sudodus on 2015-01-20
I suspect that your cpu has PAE capability but lacks the PAE flag. In Lubuntu 14.04.1 LTS you can use the **forcepae** boot option according to this link

[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M)

See also the following thread, which I think is about a computer that is very similar to yours
[URL="http://ubuntuforums.org/showthread.php?t=2261048"]
ERROR: PAE when trying fresh install[/URL]

---

### Post by molly_dog on 2015-01-22
Thanks to all of you! To answer some of your questions, I'm currently d/l'ing 32-bit images of 12.04.05 & 14.04.1 to try to get the necessary info. I'll also try the other versions graham recommended to see which works the best.

I have not run Desktop on this machine. Because my other PCs are running 64-bit Windows, I've used the 64-bit version only. 

This machine is one I "inherited" from a customer. I needed a functioning laptop for my wife to use to go on facebook & to play Pogo games until I could find a newer laptop for her. I'd really like to use it to get familiar with Linux & since I'm going to be away for an extended period, I thought it would be a good candidate for the trip. If, of course, I can get everything working! 
 
As to the GPU from what I've been able to find, this model has the Radeon 9000 but the available driver is for XP & will not load. I did find that this model shipped with the AGP 4x 32 MB version of the ATI card/chip.

Thanks for the link to de Bacon's post. It looks eerily like the issues I expect to encounter.

When I return home later, I will try to run Desktop to obtain the info in a more familiar format. In the meantime I will attach the specs yielded from the "systeminfo" command in Windows, for what that is worth. After I have tinkered around with all your suggestions, I'll post back the results.

Thanks again for the help!
M_D

---

### Post by sudodus on 2015-01-22
I think standard Ubuntu will be too much for this computer, but as stated before by grahammechanical, I think Lubuntu or Xubuntu might work well, version 14.04.1 (32-bits). 

And yes, you will probably be helped by the efforts by de Bacon.

---

