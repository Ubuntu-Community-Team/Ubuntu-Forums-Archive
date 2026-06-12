---
title: "Black screen after updating to 24.10"
date: 2024-10-18
forum: New to Ubuntu
---

### Post by apgp on 2024-10-18
After updating to ubuntu 24.10 appears black screen and is blocked. I can see in graphic mode from recovery mode but in low resolution. Help please.

---

### Post by yancek on 2024-10-18
We can't see your computer and you haven't posted any information on your hardware so do that, particularly graphics which you can get if you can boot to ta terminal with the command:   lspci | grep VGA

---

### Post by apgp on 2024-10-19
Graphics card VGA Nvidida G96 [GeoForce 9400 GT]. CPU Core 4 GiB 64 bits.
I hope these data are useful to you. Thank you.

---

### Post by apgp on 2024-10-21
When I use the command "ubuntu-drivers devices" to see the drivers compatible with my graphics card I don't get a reponse. So I don´t know if it has the correct drivers. What could be the problem?

---

### Post by myxvcx on 2024-10-23
it could be the new 560 driver i had the same problem with my 4070 ti but my monitor said additionally out of specification then i plugged it in the igpu which worked so i tryd switching to the opensource driver that worked but what also worked was to turn down the refreshrate by one step but i still don't have a perfect solution

---

### Post by apgp on 2024-10-24
[LEFT] I also think that the problem is the new 560 driver. But when I try to change the driver with the command ubuntu-drivers devices I don't get a answer. When I tray to see the drivers available, the answer is &#8220;no additional drivers available&#8221; and it can't connect with the repository  
[/LEFT] [LEFT]
 [/LEFT] [LEFT][https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu/oracular](https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu/oracular)
[/LEFT]

---

### Post by apgp on 2024-10-24
How can I update the driver repository?

---

### Post by apgp on 2024-10-24
How can I update the drivers repository? 
I want to change the driver for nvida graphic card. Problems with the driver 560.

---

### Post by deadflowr on 2024-10-24
What repository?
I see the 560 drivers in the Ubuntu default 24.10 repos have never been updated.
If using the gpu-drivers PPA, the 560 drivers from there have not been updated in almost a month.
And both are the same as what nvidia released upstream.

So not really an option to update the repositories. Since there are no new updates to either.
Unless you file bug reports and press that the drivers get fixed.
I don't know.

> I want to change the driver for nvida graphic card.
Downgrade to 555 for now?
Is that what you want?

---

### Post by apgp on 2024-10-24
That's what I want to do, because it seems that the 560 driver is giving problems and I can't see the screen in graphic mode, but I don't know how to install the 555

---

### Post by deadflowr on 2024-10-24
Thread merged.
You're 2 threads are for the same issue.

The problem you have is the fact that your card is no longer supported by any available nvidia drivers.
That's why when you you try running the ubuntu-driver commands nothing happens.

Downgrading won't fix that.

Only current options are
[list=1] [*]Use the open source driver
[*]Build the driver with patches that can be used with the 6.11 linux kernel.[/list]

Option 1 is the easy route since you'd need to know how to build to do option 2


There is an [nvidia legacy ppa]("https://launchpad.net/~kelebek333/+archive/ubuntu/nvidia-legacy"), but alas it does not currently have support for 24.10.
Will it ever have support for 24.10? Unknown.

---

### Post by 1fallen on 2024-10-24
> **apgp said:**
> That's what I want to do, because it seems that the 560 driver is giving problems and I can't see the screen in graphic mode, but I don't know how to install the 555
EDIT: I just saw the OP's card, and it is out of support 9400gt, so this won't help you
[s]If you get to a TTY session you can.
It is best to start a new nVidia driver with a clean install.
```
sudo apt autoremove --purge nvidia*
```
Now we try the requested driver:
```
sudo apt install nvidia-driver-555 nvidia-dkms-555
```
Reboot, and now how is it?  BTW I no issues with either driver.[/s]

---

### Post by grahammechanical on 2024-10-24
May I make a suggestion? Open Software and Updates>Additional Drivers tab. If we are connected to the internet the utility will find a currently supported driver or two. We can also disable the proprietary video driver. The open source drive (Nouveau) might prove just as good.

Also keep in mind that from time to time Nvidia drop support for their video adapters. Once that happens we have no choice but to use the open source video driver.

You might find that your card is no longer supported. In other words there is no Nvidia driver for your card.

[https://www.reddit.com/r/Ubuntu/comments/1ewn66w/nvidia_geforce_9400gt_graphics_driver_installation/](https://www.reddit.com/r/Ubuntu/comments/1ewn66w/nvidia_geforce_9400gt_graphics_driver_installation/)

Regards

---

### Post by apgp on 2024-10-25
When I open software update, the response is "Failed to download repository information". 
I have a good internet connection but I can't see the drivers available to install the open source one.

---

### Post by 1fallen on 2024-10-25
> **apgp said:**
> When I open software update, the response is "Failed to download repository information". 
I have a good internet connection but I can't see the drivers available to install the open source one.

Please do this for us, so we can clearly see to help, instead of guessing;
Please run and copy and paste the return back here:
```
sudo apt update
```

---

### Post by apgp on 2024-10-25
This is the result:
Obj:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oracular InRelease
Ign:2 [https://ppa.launchpadcontent.net/budgie-remix/ppa/ubuntu](https://ppa.launchpadcontent.net/budgie-remix/ppa/ubuntu) noble InRelease
Des:3 [https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu](https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu) oracular InRelease [24,1 kB]
Ign:4 [https://ppa.launchpadcontent.net/xorg-edgers/ppa/ubuntu](https://ppa.launchpadcontent.net/xorg-edgers/ppa/ubuntu) oracular InRelease
Err:5 [https://ppa.launchpadcontent.net/budgie-remix/ppa/ubuntu](https://ppa.launchpadcontent.net/budgie-remix/ppa/ubuntu) noble Release
  404  Not Found [IP: 185.125.190.80 443]
Err:6 [https://ppa.launchpadcontent.net/xorg-edgers/ppa/ubuntu](https://ppa.launchpadcontent.net/xorg-edgers/ppa/ubuntu) oracular Release
  404  Not Found [IP: 185.125.190.80 443]
Error: El repositorio «[https://ppa.launchpadcontent.net/budgie-remix/ppa/ubuntu](https://ppa.launchpadcontent.net/budgie-remix/ppa/ubuntu) noble Release» no tiene un fichero de Publicación.
Notice: No se puede actualizar de un repositorio como este de forma segura y por tanto está deshabilitado por omisión.
Notice: Vea la página de manual apt-secure(8) para los detalles sobre la creación de repositorios y la configuración de usuarios.
Error: El repositorio «[https://ppa.launchpadcontent.net/xorg-edgers/ppa/ubuntu](https://ppa.launchpadcontent.net/xorg-edgers/ppa/ubuntu) oracular Release» no tiene un fichero de Publicación.
Notice: No se puede actualizar de un repositorio como este de forma segura y por tanto está deshabilitado por omisión.
Notice: Vea la página de manual apt-secure(8) para los detalles sobre la creación de repositorios y la configuración de usuarios.

---

### Post by 1fallen on 2024-10-25
Wow you have a mess there, with 2 different sources for different versions of a OS (Noble and Oracular) even if they are just PPA's

Best suggestion a clean re-install, backing up what you want to keep first. And I would also recommend to stick with Noble 24.04, 24.10 is just a point release only good for 9 months.

---

### Post by apgp on 2024-10-25
Thank you so much. I'll try.

---

### Post by deadflowr on 2024-10-25
If you reinstall Noble you can run the 340 driver from the butterfly ppa I linked earlier.
(I see it added a second http entry in the link, so i fixed it.
But repostng it here too):
[https://launchpad.net/~kelebek333/+archive/ubuntu/nvidia-legacy](https://launchpad.net/~kelebek333/+archive/ubuntu/nvidia-legacy)

You probably also want to change kernel versions from the default HWE stack to the GA stack, as the HWE kernel will probably break the driver eventually.

I'm sure there are threads on how to do that.

---

### Post by cryofreeze666 on 2024-10-26
to give the folks the info they are looking for you need to type inxi into your command terminal.  if it doesn't give you a complete inventory of your hardware, copy and paste the sudo command it gives you in the next line then follow the command prompts.  did you download the latests drivers from your gpu provider?  nvidia and amd both provide them. after you turn down the resolution can you use the os?  if you can, open the show applications icon there in the bottom left corner.  then open the software and updates ap, click on the additional drivers tab and see if any of the drivers for your gpu show up.  if not you may have to use the command terminal to update your drivers.

---

### Post by jesusr1960 on 2024-11-17
Solution: Install KDE desktop. Gnome is the problem

---

