---
title: "Install Nvidia controller to GeForce4 Ti 4200"
date: 2014-06-24
forum: New to Ubuntu
---

### Post by AntonioRules on 2014-06-24
I want install the nvidia controller in my old pc: 
[I]
Ubuntu 14.04 LTS
Pentium IV 2ghz
Gigabyte GA-8SR533P
nVIDEA GeForce4 Ti 4200
1536 Mb RAM


[/I]I run in gnome classic better than unity but the streaming videos how youtube or Tv Maxe dont work very good. I have installed restricted drivers to ubuntu and I have checked the restricted driver card manager, but it dont found anything.
I think that this is the last controller Nvidia to my graphic card: [http://www.nvidia.com/download/driverResults.aspx/48996/en-us](http://www.nvidia.com/download/driverResults.aspx/48996/en-us)
How I can install this?

sorry for my bad english. Thanks.

---

### Post by oldfred on 2014-06-24
That looks correct.
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

It should be in repository.
So go to system settings, in 12.04 there was a add'l drivers icon, but in 14.04 I think it is add'l software and then a drivers tab. It should show that driver as an option.

Screen shot is my installing the nVidia driver, but I have a slightly newer card and can use the current version for about one more year.

You also can install synaptic and search for nVidia drivers.

sudo apt-get install synaptic

---

### Post by AntonioRules on 2014-06-24
The tab for additional drivers found nothing.
[[IMG]http://s11.postimg.org/8g7olaokv/Captura_de_pantalla_de_2014_06_24_16_15_41.jpg[/IMG]]("http://postimg.org/image/8g7olaokv/")

From synaptic I do not know which driver is best for my graphics card. [CENTER][COLOR=#000000]](*,)[/COLOR][/CENTER]

[[IMG]http://s30.postimg.org/jmmnoiiwd/Captura_de_pantalla_de_2014_06_24_16_17_49.jpg[/IMG]]("http://postimg.org/image/jmmnoiiwd/")
thanks.

---

### Post by grahammechanical on 2014-06-24
Nvidia-96 is not in the Ubuntu repositories as shown by Synaptic Package Manager so you may have to try Nvidia-173. There is also an Nvidia-173-dev. See if the standard Nvidia-173 works for you. You will need to scroll further down that list to find 173.

The alternative is to download 96 from the Nvidia web site and use the terminal to install it. How? I am not sure.

Regards.

---

### Post by oldfred on 2014-06-24
I was just in 12.04 and it does show a nVidia-96. But when I reboot into 14.04, it is not available.

I have not installed from nVidia directly for years and back then had issues, so standardized  on using only the versions in the repositories.

You could download precise version, but then are on your own if it does not work????
[https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96)

---

### Post by mörgæs on 2014-06-24
Even though you have the correct drivers applied Ubuntu might be too heavy. It's worth considering Lubuntu 14.04.

---

