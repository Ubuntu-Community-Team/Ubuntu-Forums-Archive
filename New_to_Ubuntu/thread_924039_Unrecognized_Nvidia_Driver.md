---
title: "Unrecognized Nvidia Driver"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by patree on 2008-09-19
Hey,

i recently built from scratch a beautiful new computer, and am dual booting Ubuntu along with windows XP. 
Anyways I cant get Ubuntu to recognize my video card. It is an e-GeForce 9800 GTX. 
Ive read on other forums that it is possible, but I am a complete noob at linux. 

I have downloaded the driver that apparently works for my card called:

NVIDIA-Linux-x86-173.08-pkg1.run

but i have no idea how to make it work through terminal commands.
do you think anybody here could give me simple, step-by-step instructions?

the driver is saved to my desktop, and my user thing is called patree-desktop i think.

Also i have another question. i accidentally setup my keyboard wrong so when i hit the ? key it actually types É or é,, i had to copy and paste the question mark to use here lol im sure this is an easy fix also...

oh my version of ubuntu is hardy heron 8.04..
all help is appreciated TY!

---

### Post by MockY on 2008-09-19
So the card is not listed in the Restricted Drivers Manager? System - Administration - Restricted Drivers Manager. If not, I suggest that you install Envy and install the drivers with that.

[http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

---

### Post by cariboo on 2008-09-19
If you want to compile your own driver do the following steps:

Make sure you don't have any closed source nvidia drivers installed. In a Applications-->Accessories--Terminal type:

```
lsmod | grep nv
```

If the result is **nv** you are running open source drivers. If you get **nvidia** you are using closed source drivers and will need to uninstall them. Got to System-->Administration-->Synpatic Package Manger and search for nvidia. When they are listed, right click all the installed files and mark for complete removal.

Next press Ctrl-Atl-F1, this will take you to a command prompt, type:

```
sudo /etc/init.d/gdm stop
```

This will stop the desktop manager.

I am assuming you have the driver file on your desktop, so type at the prompt:

```
sudo chmod +x ~/Desktop/NVIDIA-Linux-x86-173.08-pkg1.run
```

This will make the driver file executable. Now comes the fun part, at the prompt type:

```
sudo ~/Desktop/NVIDIA-Linux-x86-173.08-pkg1.run

```

This will start the script that compiles and installs the driver, answer yes to all the prompts.

Once the driver has been installed, at the prompt type:

```
sudo /etc/init.d/gdm start
```

The desktop manager should start if you have followed the instructions correctly.

Jim

---

### Post by bumanie on 2008-09-19
It is generally best to use the driver from the repositories. You can find it under System --> Administration --> Hardware Drivers Enable your card there. Installing the nvidia driver from their site is usually only done if the ubuntu hardware driver doesn't work for some reason.

---

### Post by Nepherte on 2008-09-19
> **bumanie said:**
> It is generally best to use the driver from the repositories. You can find it under System --> Administration --> Hardware Drivers Enable your card there. Installing the nvidia driver from their site is usually only done if the ubuntu hardware driver doesn't work for some reason.
I believe the driver supplied in the repositories are not recent enough for his card. He will need a newer driver. You can follow cariboo907's instructions, but you will most likely need the compile/build tools to get it to work. So before you follow his instructions run the following in a console:
```
sudo apt-get install build-essential
```

---

### Post by patree on 2008-09-19
oh wow! thank you so much! 
those step by step instructions worked perfectly! 
my screen resoloution is 1000% clearer and all of the graphics functions are now working!
i appreciate your help very much!
:):):):):):)

---

### Post by patree on 2008-09-19
i hope that this thread can remain on here to help all of those having the same problem i did.

---

### Post by verlyn13 on 2008-10-12
I had the exact same problem, (exact same video card). I downloaded a bit more recent driver from Nvidia but followed the instructions exactly and it worked great.  Thanks!

---

