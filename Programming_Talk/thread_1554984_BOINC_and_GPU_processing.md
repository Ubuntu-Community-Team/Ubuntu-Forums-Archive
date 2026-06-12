---
title: "BOINC and GPU processing"
date: 2010-08-17
forum: Programming Talk
---

### Post by Thomas Garman on 2010-08-17
I run BOINC on my desktop, which is a compaq SR5707r to which I added an nVida graphics card (see signature).  BOINC processes can run on the GPU on a windows machine but under Ubuntu BOINC does not find the GPU.
 
Does anyone else find this is true?  I saw in the BOINC forums there are some suggestions for how to fix this but I haven't had time to try anything yet.

---

### Post by ju2wheels on 2010-08-17
It requires Nvidia proprietary drivers i believe and your nvidia card must support CUDA, google and look on nvidia's website for a complete list.

I can confirm it does work out of the box with Lucid/BOINC as I have my Nvidia gpu working fine with BOINC and i didnt have to do any manual configuration.

[edit] [http://www.nvidia.com/object/cuda_gpus.html](http://www.nvidia.com/object/cuda_gpus.html)

If you are unsure if you are using the proprietary drivers, check jockey (System->Administration->Hardware Drivers).

---

### Post by Thomas Garman on 2010-08-17
Yes,I am using the propriety drivers  with Lucid so I thought it would work but I had a process from the Prime Grid that never started because the GPU was showing as not available so I am going to have to look into it.
 
 
There are actually sever proprietary drivers availale in the system>...>hardware drivers menu I got through lucid so maybe I have the one that doesn't work.

---

### Post by Thomas Garman on 2010-08-19
Reading around the internet about this issue I am getting the sense that the Ubuntu nVidia drivers from the repository are actually older and so the CUDA functionality might be available with more recent drivers so I am going to try to install the most recent nVidia drivers and see how that goes...

---

### Post by Thomas Garman on 2010-08-19
The easiest way to install the nVidia drivers turns out to be via this PPA suggestion (follow link)

[http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html](http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html)

using the suggestion on that website I upgraded my driver to 

nVidia-Linux-x86-256.44

and the GPU is churning away at BOINC processes.

I am running Ubuntu 10.04 and the install/upgrade of the driver worked perfectly fine with my nVidia GeForce 8400 GS and two monitors.

---

