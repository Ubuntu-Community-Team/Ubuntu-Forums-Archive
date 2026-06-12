---
title: "kernel update broke my system"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by Bloch on 2008-10-15
The kernel update from
2.6.24-19-generic
to
2.6.24-21-generic
broke my system. The X-windows system do not start. The error message is something about could not resume image or something.

I have a Nvidia graphics card GeForce Fx 5200.

It took me about 5 hours to install the driver for that several months ago - I had to go to the Nvidia website, serach the web for hacks etc etc.
I don't want to go through that hell again.

Is there any simple way to get it working?

---

### Post by Perfect Storm on 2008-10-15
When using the driver manually from nvidia site and there's an update/patch it will "break" the system. It's because you build the driver for the previous kernel. So you have to build the driver against the new kernel. It's the same way that you install the driver the last time.

Have you tried using the default nvidia restriction driver? Or Envy?

---

### Post by SeanBlader on 2008-10-15
You might be able to select the old kernel from the grub menu when the system starts. 

Your post does make me a little nervous though, I have a few minutes remaining on the download for today's updates. I'll let you know how it goes on my AMD based system with the Nvidia 6150 Go chip.

---

### Post by Perfect Storm on 2008-10-15
Actually boot up in "safe mode"

Then

```
sudo nano /etc/X11/xorg.conf
```


Set the driver from "nvidia" to "nv"

Save [ctrl]+[o] and exit [ctrl]+[x]

then reboot. Now you can get in, but without the 3D stuff etc. From there you can rebuild the driver or find an alternative.

---

### Post by Haruki-kun on 2008-10-15
> **SeanBlader said:**
> You might be able to select the old kernel from the grub menu when the system starts. 

Your post does make me a little nervous though, I have a few minutes remaining on the download for today's updates. I'll let you know how it goes on my AMD based system with the Nvidia 6150 Go chip.

Actually, mine also seems to be having problems with the kernel update. Is there an error of some sort somewhere?

---

### Post by Archmage on 2008-10-15
envyNG might be an solution.

You can even install it via command-line and run it there, too.

---

### Post by diffuze on 2008-10-15
I just had the same exact problem and running envyng solved it for me!
So I highly recommend you to try that!

Also, now my xwindows FINALLY starts up using the correct resolution! So now I don't have to set it in nvidia-settings each time anymore, so some sort of bug must have been fixed.

<---- Extremely happy! :-D

---

### Post by Bloch on 2008-10-15
Thanks for all the replies!

I was able to choose to boot from the old 2.6.24-19-generic kernel.

Then I changed the  /boot/grub/menu.lst
file and commented out the entry for the new 2.6.24-21 kernel.
(This is easy to do, comments begin with a #)

Now the system boots as before.

I recall that Envy did not work for me when I originally installed the drivers for my GeFortce 5200 card. I had to download drivers from the Nvidia site and "build" it myself. (Quotation marks because I only followed line by line instructions).

I searched to see what is new & improved in the 2.6.24-21-generic kernel, and can't find much info.

My question is, do I need the new kernel? Will staying with the old one cause problems in the future - for example when updates to other programs come in?

Thanks guys.

---

### Post by Perfect Storm on 2008-10-15
Bloch, it's security updates. Might be a good idea running the new one.

---

### Post by Bloch on 2008-10-15
For me as a user, a kernel update is like an attack on my system.

It's not the first time an update has broken things.

---

### Post by Perfect Storm on 2008-10-15
> **Bloch said:**
> For me as a user, a kernel update is like an attack on my system.

It's not the first time an update has broken things.

It's still not an update the break things. It's how it works. You build the nvidia driver with a previous kernel. If you have used the one that comes with Ubuntu it wouldn't happend.

By installing non-official stuff (vital stuff), the result might not be as pleasent and smooth.

---

### Post by SeanBlader on 2008-10-15
No problems here. I'm just using the nvidia-glx-new drivers so didn't have any problems with the kernel or nvidia updates that came over the wire today. That is one reason why I've been waiting to bother setting up the touch screen on the tablet though, going to wait for Intrepid to try that one though.

Bloch, since you have the new kernel easy to run from grub, maybe when you have some time you can play with it a bit and try to get the nvidia-glx drivers working on it rather than have to build your own every time there's a kernal update.

---

### Post by Haruki-kun on 2008-10-15
> **Artificial Intelligence said:**
> It's still not an update the break things. It's how it works. You build the nvidia driver with a previous kernel. If you have used the one that comes with Ubuntu it wouldn't happend.

By installing non-official stuff (vital stuff), the result might not be as pleasent and smooth.

Would this also be the case with say.... wireless drivers? even while running the old Kernel?

---

### Post by Perfect Storm on 2008-10-15
> **Haruki-kun said:**
> Would this also be the case with say.... wireless drivers? even while running the old Kernel?

I can't say as I don't have any inside regarding wireless. (I prefer stationary and wired computer ;) )

---

### Post by scarboni on 2008-10-30
> **Artificial Intelligence said:**
>  If you have used the one that comes with Ubuntu it wouldn't happend.

Uh... not quite... same thing happened to me & I'm using straight-up nvidia-glx-new on an 8400.  Can't get it working with new kernel (.21) at all - go back to .18 & sure enough works fine.

Also anyone know why the updater insists on installing xserver intel drivers when I don't have any trace of an intel gfx on my system?  Even the disabled onboard video is nvidia.

Thanks,
Sam

---

