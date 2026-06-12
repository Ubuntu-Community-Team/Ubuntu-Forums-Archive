---
title: "compiz not working"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by chajuram on 2008-06-01
Hi All,

I am trying to get compiz to work on my computer. I was having trouble with the ATI driver initially, but with the 8.04 upgrade that has been fixed. 

Now, here is the issue. When I do a 
> compiz --replace
nothing happens. If I go to system>preference>appearance>visual effects and select normal or extra, I get the error> Desktop effects could not be enabled
When I go to terminal and type "compiz", I get the error
> Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:94c3 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x960) to maximum 3D texture size (8192): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz: 406: /usr/local/bin/compiz: not found

These are some of the things I saw people looking at, so I attached this information. I believe the ATI driver is correctly installed, here is the part from lspci
> 01:00.0 VGA compatible controller: ATI Technologies Inc RV610 video device [Radeon HD 2400 PRO]


Will be grateful if anyone could help. I am so looking forward to a funky desktop for so many days, first the driver was not working, and now this. by the way I did try installing this software called "Compiz Fusion Icon" and tried playing with that. I believe it was running some form of compiz, but the mouse and keyboard were not functioning properly. 

Thanks,

Chajuram

---

### Post by chajuram on 2008-06-01
Hi All,

Also, is there a very nice intro/howto for compiz and how to play with it. 

Chajuram

---

### Post by Joeb454 on 2008-06-01
what happens if you try ```
sudo apt-get install compiz compiz-core
``` It looks like you're getting a reply saying Compiz isn't installed.

---

### Post by spiderbatdad on 2008-06-01
You may have luck installing the package xserver-xgl ```
sudo apt-get install xserver-xgl
```Then reboot and select custom under the visual effects tab.

---

### Post by chajuram on 2008-06-01
Hi,

Thanks for your quick replies, I tried both, I do have compiz, thats what apt-get install  tells me. The xserver-xgl did not work either, and it screwed up my resolution, so I will go ahead and remove it. 

So, still :(

---

### Post by SunnyRabbiera on 2008-06-01
> **chajuram said:**
> Hi,

Thanks for your quick replies, I tried both, I do have compiz, thats what apt-get install  tells me. The xserver-xgl did not work either, and it screwed up my resolution, so I will go ahead and remove it. 

So, still :(

what is your video card?
There are a few video cards that are still rubbish with compiz, its not compiz's or our fault as most vendors dont co operate with us with providing drivers... like bloody ATI.

---

### Post by chajuram on 2008-06-01
> **Joeb454 said:**
> what happens if you try ```
sudo apt-get install compiz compiz-core
``` It looks like you're getting a reply saying Compiz isn't installed.
This is what I get...
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz is already the newest version.
compiz-core is already the newest version.
The following packages were automatically installed and are no longer required:
  libglitz-glx1 libglitz1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


---

### Post by chajuram on 2008-06-01
> **SunnyRabbiera said:**
> what is your video card?
There are a few video cards that are still rubbish with compiz, its not compiz's or our fault as most vendors dont co operate with us with providing drivers... like bloody ATI.

Hi,

I do sadly have a ATI video card, it is a ATI Radeon HD2400 Pro. 

Chajuram

---

### Post by SunnyRabbiera on 2008-06-01
> **chajuram said:**
> Hi,

I do sadly have a ATI video card, it is a ATI Radeon HD2400 Pro. 

Chajuram

yeh the root of most evils out there concerning a video card.
Thats why nvidia and even intel video cards are more preferred as at least nvidia and intel co operate with linux at least somewhat.

---

### Post by Joeb454 on 2008-06-01
ATI support is getting better though :) Slowly......but steadily :)

---

### Post by SunnyRabbiera on 2008-06-01
> **Joeb454 said:**
> ATI support is getting better though :) Slowly......but steadily :)

Yeh but it will take two years at this rate, ATI is sluggish compared to Nvidia and intel concerning linux support.
Out of all of them though it seems like in built intel cards work best with effects, they might not always be the best but intel seems to be co operating with us more then you would expect.
But I think thats from their deal with apple, I have noticed that Intel has been a lot nicer to us these days.

---

