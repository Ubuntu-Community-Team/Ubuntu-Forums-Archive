---
title: "Please Help"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by nirakarsethy on 2008-04-23
I've a Hp Dv9704tx laptop. I've dual boot , Ubuntu with Vista.
My sound runs good in Vista but its doesn't work on Ubuntu. Its Realtek. My graphics card is NVIDIA 6800M gs. This is also not working. Kindly Help. I tried some ways but I was unsuccessful. My interest for Linux is decreasing day by day.

I like linux....

Kindly help
Nirakar Sethy

---

### Post by ace007 on 2008-04-23
Can you boot into Ubuntu at all?  If you can then your graphics card is working.  It may just be using a generic driver.  Envy can be used to install proprietary drivers for nVidia cards.

If not, can you please explain the problems.  It is difficult to analyze a car for instance if someone just tells you its broken.

As for the sound, I'm not sure.  Dont give up on ubuntu, its much much better than windows.  the issue is just that windows works out of the box better by being bloated and crowded.  Once you get Ubuntu running it is so much better.

---

### Post by rouge568 on 2008-04-23
Have you enabled the restricted drivers? There may be one for your sound card, and definitely one for your graphics card. These can be installed at System>Administration>Hardware Drivers. (Or Restricted Drivers Manager if you're using a version earlier than 8.04) All restricted means is that they are not open-source, but released by the company that makes them.

edit: ace007 beat me to it...

---

### Post by phidia on 2008-04-23
In Gutsy Gibbon the (7.10) release click on the upper menu bar item System>Administration>Restricted Drivers Manager and see if you can select the nvidia driver for your GPU.

From the same upper panel System>Preferences>Sound you can check what device is selected there and test sound with different sound drivers.

---

### Post by nirakarsethy on 2008-04-23
Thanks for you replies:

I've tried the ways you all suggested the problems are :
1. There is a red dot on the right hand side of the NVIDIA row. Its not selectable. Error message comes out.

2. I tried out all the audio options and pressed the button Test, but nothing came out.

So what to do next.

Thanks
nirakar

---

### Post by nirakarsethy on 2008-04-23
Thanks for you replies:

I've tried the ways you all suggested the problems are :
1. There is a red dot on the right hand side of the NVIDIA row. Its not selectable. Error message comes out.

2. I tried out all the audio options and pressed the button Test, but nothing came out.

So what to do next.

Thanks
nirakar sethy

---

### Post by ace007 on 2008-04-23
Have you tried to use envy?

just search envy from synaptic package manager

---

### Post by rouge568 on 2008-04-23
I personally would not recommend envy: it is much more stable if you do things manually. Could you please post that error message?

---

### Post by nirakarsethy on 2008-04-23
In Screenshot is about Video and Screenshot-2 is about Audio

Thanks
Nirakar

---

### Post by rouge568 on 2008-04-23
Did you try clicking "Enable Driver?"
If it didn't work, what was the output?

For the audio, make sure everything is on "ALSA".

---

### Post by nicedude on 2008-04-23
If enabling the restricted Nvidia driver didn't work then I would try envy as the other fellow mentioned as it did better for my laptop then the restricted. You can get a copy at the authors website [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) once you download it to the desktop justt double click it like winblows and it will install then go to Applications -> System Tools -> Envy once started select install Nvidia driver and let it do its magic. It worked like a charm for me.

---

### Post by nirakarsethy on 2008-04-24
The Output Was:
               The software source for the package
               nvidia-glx-new
               is not enabled.

               There is a close button in the End.
               A red minus sign on the Left Top

Thanks
Nirakar

---

