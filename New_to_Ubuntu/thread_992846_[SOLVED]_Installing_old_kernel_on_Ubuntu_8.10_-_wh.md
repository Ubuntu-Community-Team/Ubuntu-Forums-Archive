---
title: "[SOLVED] Installing old kernel on Ubuntu 8.10 - what to do next?"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by krtica on 2008-11-25
I'm asking so many questions, that I probably should open my own forum. :D
Anyway, I start to solve some issues on my own and I'm waiting for some books about Linux and Ubuntu, so I hope that I'll be less tedious. :mrgreen:

I'm trying to install some driver which is still impossible to install on Ubuntu 8.10 /2.6.27-7-generic. I found that driver worked on kernel 2.6.24-19-generic, so I downloaded the linux-image-2.6.24-19-generic package, and install:
```
$ sudo dpkg -i  linux*.deb
```

After I reboot under the newly installed 2.6.24-19-generic kernel, I found that Ubuntu starts painfully slow, and after I finally sow desktop I discovered that a lot of hardware doesn't work.
:confused:

Question is:

Do I have to do something more than just
```
$ sudo dpkg -i  linux*.deb
```

OR

Remove that newly installed 2.6.24-19-generic kernel?

---

### Post by int on 2008-11-25
experment the 2.6.27-10-generic

---

### Post by krtica on 2008-11-25
Everything works fine under 2.6.27-7-generic, so I don't need any newer kernel.
I'm just not sure do I need to somehow configure that 2.6.24-19-generic kernel after I installed it?

---

### Post by theozzlives on 2008-11-25
need more info, what driver you yrying to install?

---

### Post by krtica on 2008-11-25
It's not about driver. :D
I just wanna know did I done everything right, or it's maybe more to do when you wanna install older kernel then you already have.

What I done is this:

[I][COLOR="Sienna"]Through [http://packages.ubuntu.com/hardy-updates/linux-image-2.6.24-19-generic](http://packages.ubuntu.com/hardy-updates/linux-image-2.6.24-19-generic)
download the linux-image-2.6.24-19-generic package.  Install under
Ubuntu with:
$ sudo dpkg -i  linux*.deb
Reboot under the new -2.6.24-19-generic kernel[/COLOR][/I]

But - when I reboot under 2.6.24-19-generic kernel, some of my hardware doesn't work at all.
So, do I need to do something _more_ then [COLOR="DarkRed"]$ sudo dpkg -i  linux*.deb[/COLOR]

I repeat: My original kernel (2.6.27-7-generic) works fine.

---

### Post by sdennie on 2008-11-25
What you are trying to do may not work.  Grabbing the -restricted-modules (and maybe -headers for good measure) might help but, for example, if you have installed nvidia drivers the "normal" way (so, you did nothing or went to System->Administration->Device Manager), the nvidia kernel module in the 2.6.24-generic kernel won't match the driver version that is installed on the machine.  In that case, you'd have to use one of the many guides on manually installing nvidia drivers.

---

### Post by krtica on 2008-11-25
Ok, this is the full story.
I have agere soft modem on intel_hda sound device. After I encounter some problems, I contact "linmodem". They told me that there are some issues with drivers for Ubuntu 8.10, and:

> [I]But to just get on line
quickly there is a faster route.

From [http://linmodems.technion.ac.il/packages/ltmodem/11c11040/](http://linmodems.technion.ac.il/packages/ltmodem/11c11040/)   get the
agrsm-ubuntu8.04.1-2.6.24-19-generic.tar.gz   which contains tested
drivers for kernel 2.6.24-19-generic.

Through [http://packages.ubuntu.com/hardy-updates/linux-image-2.6.24-19-generic](http://packages.ubuntu.com/hardy-updates/linux-image-2.6.24-19-generic)
download the linux-image-2.6.24-19-generic package.  Install under
Ubuntu with:
$ sudo dpkg -i  linux*.deb
Reboot under the new -2.6.24-19-generic kernel

Unpack the tarball with
$ tar zxf agrsm*.tar.gz
Move in
$ cd  agrsm-ubuntu8.04.1-2.6.24-19-generic
Run
$ sudo ./setup
and follow through with the included directions.[/I]

Problem is that after I boot into 2.6.24-19-generic kernel, a lot of my hardware doesn't work.
So - is it possible at all to install older kernel? And if "Yes", then when I download it and install it with
[COLOR="DarkRed"]sudo dpkg -i  linux*.deb[/COLOR],
do I need to do something more for my system to works like it works with original 2.6.27-7-generic Ubuntu 8.10 kernel?

---

### Post by Archmage on 2008-11-25
You should **not** install a Hardy-Kernel in Intrepid. The Kernel is a very essisential piece of your installation and should only replaced if you know what you are doing. In most cases you should try to make the driver work with your kernel, before trying to exchange it.

---

### Post by krtica on 2008-11-26
Ok. Thx.
I removed it.

---

