---
title: "Image Viewer using high %CPU"
date: 2014-01-28
forum: New to Ubuntu
---

### Post by amarumayo on 2014-01-28
Hi all

I am trying to view images (JPEG) with image viewers on Ubuntu 12.04 and they are all incredibly slow ~10 seconds or more to switch between photos.  I have tried the default viewer, gthumb, Mirage, Shotwell and feh all with the same results.  My system seems to be running fine otherwise. Any suggestions to troubleshoot this problem?

Thanks in advance.

---

### Post by ajgreeny on 2014-01-28
Start the applications in terminal with the appropriate command, **eog** for the default image viewer, **gthumb** for (surprise, surprise) gthumb, etc etc and see if any error messages appear when you open a file/image with each.

---

### Post by amarumayo on 2014-01-28
Hi,
Thanks for your response.  I have loaded eog from the terminal and loaded the image.  I don't see any errors reported, the only thing that happens is that the image loader bar moves while the image loads.  Still slow about 10 seconds for each image.  Is there a way to see an error log if there are any errors reported?

cheers

---

### Post by tgalati4 on 2014-01-29
How much RAM do you have?  Perhaps you have run out of memory.  Open a terminal and post the output of:

```
free
```

If you are running from swap then things will slow down quite a bit.

---

### Post by amarumayo on 2014-01-29
output of free from terminal gives:

             tot       used        free          shared    buffers      cached
Mem:       5802560    5247784     554776             0         193540      3459168
-/+ buffers/cache:    1595076    4207484
Swap:      5875708      18892    5856816

**Additional info
When I run top in the terminal it shows that my image viewer is the top program using around 5% of memory and between 50 and 110% of cpu.  Could this indicate a problem?


Thanks

---

### Post by amarumayo on 2014-01-29
Hello,

Ubuntu 12.04
I am having an issue with my image viewers being very slow to scroll between images (JPG).  I have tried several image viewers (eog,gthumb,mirage,feh) all with the same results.  Here is the output of free showing my memory usage:

                  total       used       free     shared    buffers     cached
Mem:          5666       2568       3098          0         63       1061
-/+ buffers/cache:       1443       4223
Swap:         5737          0       5737

When I run top from the terminal, my image viewer seems to be using about 5% of memory between scrolls however, the CPU% jumps to extremely high values - over 100% sometimes approaching 200%.  Could this indicate a problem and be what is causing the lengthy lag time (5-10 secs) between images?  Is there any way to proceed with solving this problem?

Thank in advance

---

### Post by claracc on 2014-01-29
You have an equal post started in: [http://ubuntuforums.org/showthread.php?t=2202342](http://ubuntuforums.org/showthread.php?t=2202342) , please stand with it since you had receive yet some reponses about what the problem could be. I suposse, a moderator will merge the two posts.

About your problem, what is your hardware?, what processor do you have in your computer?, and graphic card?, perhaps the .jpg image is very big?.

---

### Post by ajgreeny on 2014-01-29
That is a huge amount of cpu power just to open a jpeg image.

What graphic card do you have and what driver does it use?

---

### Post by amarumayo on 2014-01-30
Thanks for your reply,

from lspci | grep VGAGraphic Card =Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 6310]


and from lshw -c video:
Driver = fglrx_pci

---

### Post by amarumayo on 2014-01-30
Lenovo G575 6GB
[COLOR=#000000]VGAGraphic Card =Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 6310]
[/COLOR][COLOR=#000000]Video Driver = fglrx_pci
Processor = [/COLOR]AuthenticAMD 780MHZ

[COLOR=#000000]
The problem is with all of my jpegs which average about 5MB in size.

Thanks![/COLOR]

---

### Post by mörgæs on 2014-01-30
Please stop multiposting.
Threads merged.

---

