---
title: "Trouble with Nvida geforce 9500m gs"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by TheTrlak on 2008-07-03
I have an asus G1 with windows vista 64-bit. I used Wubi to install Heron. Well Seems the auto driver updates for my card will cause a display error. So I have to manually install the newest drivers from nvidia. Of course I had to disable my gui to install it prompted me to make install the source code for my kernel.

Now here is where the problem lies. It could not find one for me and it can not compile one for me either. I am not sure if its because i don't have the source code or if it's because I don't have a proper linker?

Any one have suggestions for me in order to get my drivers working properly so I can not only get my compiz up but also potentially game?

---

### Post by saitoh on 2008-07-03
first off I would make sure you have the kernel headers installed.
"uname -r" will give you the kernel version you currently have installed.
search for kernel(or linux) headers in synaptic and install the one that matches the results for your kernel version. 

Also make sure you have the newest version of GCC installed.

If it still gives you problems post what it says.

---

### Post by TheTrlak on 2008-07-03
Well thank you for your advice. I am currently installing the source code for my headers, hopefully this will be a breakthrough *crosses fingers* but seems all other major generic headers are already marked installed. Should I bother reinstalling or installing the other packages such as server,etc?

EDIT: Forgot to mention my current GCC is 4.2 with only base, I did add multi library support and documentation for later use.

---

### Post by TheTrlak on 2008-07-03
ok I took the actual error snippet from my install log.

"Building kernel module:...
  
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it...."

The installer says unable to load 'NVIDIA.KO' stating that kernel source may not match or be improperly configured, possibly from a GCC that differed from the original one used to build my kernel.

Also a driver like rviafb/nvidiafb may be present and or preventing NVIDIA kernel from obtaining ownership of my graphic device.

---

### Post by saitoh on 2008-07-03
did you install any of the nvidia drivers in the Ubuntu repos/do you have nvidia-kernel-common installed?

(also make sure you have all the build-essential packages installed, libc6-dev is important)

---

### Post by aktiwers on 2008-07-03
I wrote this yesterday, and it will fit you perfect!

Its howto install manually [if thats what you want to do of cause]
[http://ubuntuforums.org/showpost.php?p=5309952&postcount=6](http://ubuntuforums.org/showpost.php?p=5309952&postcount=6)

---

### Post by phidia on 2008-07-03
How did you install gcc? the correct way to do this in ubuntu is to install the build-essential package.

From the overall guide [here]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") there is [the specific howto]("https://help.ubuntu.com/community/NvidiaManual") for manually installing the nvidia driver.

---

### Post by TheTrlak on 2008-07-03
Well I really didn't alter the install at all, in fact all I did do was add documentation and libraries. So far nothing has been working thus far. I am currently using the last posted official guide for manual install.

Well actually I used a guide provided over in 64 bit section, labeled geforce driver solved or something to that effect. I followed the most up to date guide where i would disable the gui and install the newest driver posted. I removed common drivers as well as glx, and I also removed the restricted modules that were installed.

I build my libraries and hoped that would settle. Well it gets to 47% before it fails every time.

---

### Post by TheTrlak on 2008-07-03
Seriously neither the official guides provided by NVIDIA or by Ubuntu solve this pickle... lol the joys and sorrows of troubleshooting I suppose.

---

### Post by aktiwers on 2008-07-03
Did you try my guide? It has the libs and tools needed for the installation too.

---

### Post by phidia on 2008-07-03
> **TheTrlak said:**
> Well I really didn't alter the install at all, in fact all I did do was add documentation and libraries. So far nothing has been working thus far. I am currently using the last posted official guide for manual install.

Well actually I used a guide provided over in 64 bit section, labeled geforce driver solved or something to that effect. I followed the most up to date guide where i would disable the gui and install the newest driver posted. I removed common drivers as well as glx, and I also removed the restricted modules that were installed.

I build my libraries and hoped that would settle. Well it gets to 47% before it fails every time.

What error messages are you getting?

---

### Post by TheTrlak on 2008-07-04
Yes I did try the installation guide posted by akit, but anywho the error message I get is the one I posted with the log above. So far basically its telling me my current gcc is not working with the original one my last kernel was made with to basically recap.

---

### Post by anewguy on 2008-07-04
Okay, I don't know what your tutorials may have said, so if this is redundant please forgive me:

Have you installed the build-essentials package?

:)

---

### Post by TheTrlak on 2008-07-04
yes i did, but thank you.

---

### Post by TheTrlak on 2008-07-06
so every post tahts similiar or guide I come across is still a no go... Not even Envy is the best solution... Anyone else have any ideas?

---

### Post by cariboo on 2008-07-06
You also need to install **libxft-dev** it is in the repositories and you can use synaptic to install it.

Jim

---

### Post by add2700 on 2008-07-07
you can try 
sudo apt-get remove gcc

sudo apt-get install gcc

sudo apt-get install build-essential

Your problem is also going to be with 4GB RAM, regardless if you run 32 bit or 64 bit OS I think. 

Follow the directions in my post here:

[http://ubuntuforums.org/showpost.php?p=5331990&postcount=11](http://ubuntuforums.org/showpost.php?p=5331990&postcount=11)

---

### Post by TheTrlak on 2008-07-10
hmm well your guide doesnt work becuase your directory that you state to change the directory to does not exist according to the messages my shell tells me. I think it is a 4 gig ram issue but seems otehrs around the net did get it to work but there methods dont work for me that well. The best i can do is to get it installed but upon reboot it only wants the vesa drivers again and runs un "low graphics mode".

---

### Post by add2700 on 2008-07-11
What specific directory are you missing?

---

### Post by saitoh on 2008-07-16
did your issue get resolved?

---

