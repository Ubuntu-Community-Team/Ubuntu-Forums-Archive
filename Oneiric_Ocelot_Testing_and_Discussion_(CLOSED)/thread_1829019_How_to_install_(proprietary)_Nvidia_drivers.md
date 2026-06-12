---
title: "How to install (proprietary) Nvidia drivers??"
date: 2011-08-20
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by PhantmKllr on 2011-08-20
Does anyone know how to get the Nvidia drivers working in Oneiric?

I've been living with the experimental Mesa-DRI 3D drivers, but the performance is noticeably slower than the proprietary drivers.

---

### Post by Quackers on 2011-08-20
You can run Additional Drivers or, if you are using a recent Nvidia graphics card you can run the comnmands below in the terminal ```
sudo apt-get install nvidia-current nvidia-settings
```

---

### Post by VinDSL on 2011-08-20
If you're talking about proprietary nVidia .run files...

No, I haven't figured out a way to use them in Oneiric - and I tried for days.

Installing .run files used to be a piece of cake, but it's been impossible, in my experience, with Oneiric.

That said...

If you're simply talking about running the latest nVidia drivers, e.g. not waiting around for releases in the official Ubu repos, xorg-edgers is a close second.

---

### Post by PhantmKllr on 2011-08-20
> **Quackers said:**
> You can run Additional Drivers or, if you are using a recent Nvidia graphics card you can run the comnmands below in the terminal ```
sudo apt-get install nvidia-current nvidia-settings
```

I usually use Jockey GTK to install the drivers.

> **VinDSL said:**
> If you're talking about proprietary nVidia .run files...

No, I haven't figured out a way to use them in Oneiric - and I tried for days.

Installing .run files used to be a piece of cake, but it's been impossible, in my experience, with Oneiric.

That said...

If you're simply talking about running the latest nVidia drivers, e.g. not waiting around for releases in the official Ubu repos, xorg-edgers is a close second.

The drivers in the repos are good enough for me, I'm not really interested in the drivers from the Nvidia website.

The reason I asked for instructions, is that every time I try to install them, I get kicked back to Unity 2D.

I had ran into this problem a few weeks ago, and I remember someone told me that I have to recompile the Nvidia kernel module whenever there's an update to the driver. (Come to think of it, I think it was you who told me that, VinDSL. :o ) I believe that I finally got it working

But that was a few weeks ago, and since then I've wiped clean, switched back to 11.04, and re-upgraded. Suffice it to say that I've forgotten the commands necessary to recompile the kernel module.

---

### Post by VinDSL on 2011-08-20
Oh, okay...

Well, there are several ways to install nVidia drivers.

If you've booted into Unity just use Synaptic (assuming you have it installed).  Do a search for nvidia-current, and install it.

If you prefer the command line, do what Quackers said (above).

If you can't boot into Ubuntu - you have a blank screen with a blinking cursor - you're stuck at the battery check - or some such thing - you probably need to do a "wash, rinse, and set."  That is...

Boot into recovery mode, choose root privs with networking - remove nvidia-current, purge it, and (re)install it - and restart.

Is that the sort of thing you're looking for?

---

### Post by PhantmKllr on 2011-08-20
Yup, I'm gonna go ahead and try it now. :D

I was going to try that anyway. XD

---

### Post by PhantmKllr on 2011-08-20
Alright!!! nvidia-current installed!!! Reboot, Unity 3D working great. Launch nvidia-settings. WTF?!?!?!

---

### Post by Sworddragon on 2011-08-20
Try nvidia-xconfig to create a xorg.conf. What does "dkms status" say?

---

