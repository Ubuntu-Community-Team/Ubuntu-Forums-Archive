---
title: "new kernel and wireless?"
date: 2004-12-12
forum: Packaging and Compiling Programs
---

### Post by vontez on 2004-12-12
I'm planning on compiling a new 2.6.9 kernel from scratch and installing it on my ubuntu laptop.  I have the default installation right now, and everything works except the SD card reader.  (This is why I'm upgrading the kernel)

My question is when I upgrade the kernel, is my wireless still going to work?  I realize I need to enable wireless device support and a couple encryption options in the kernel config, but other than that will the drivers load properly?  My wireless NIC is an ipw2200.  It is working great right now, but I wanted to check if anything else must be done to get the drivers working with the new kernel.

Thanks for any replies!

---

### Post by randy on 2004-12-13
Your more thank likely going to need to rebuild the related kernel modules that aren't packaged with the kernel.

---

### Post by macpilot on 2004-12-30
How did you got your IPW2200 to work?, I have a latitude d600 and can't even compile the drivers.

I'm new to linux so please no flames.

Thanks 

Joe

---

