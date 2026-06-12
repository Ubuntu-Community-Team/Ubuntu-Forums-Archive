---
title: "MyUnity"
date: 2012-10-01
forum: New to Ubuntu
---

### Post by piqueta on 2012-10-01
When I run MyUnity I get this message:

Your Ubuntu 12.04 is running in 2D mode.
Many features will not be available.

and most options are unavailable. I did not log into Ubuntu 2D.

---

### Post by NikTh on 2012-10-01
Hi , 

please open a terminal and post the results of this command 

```
[B]/usr/lib/nux/unity_support_test -p
```

Thanks
[/B]

---

### Post by piqueta on 2012-10-01
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  22
  Current serial number in output stream:  22

---

### Post by NikTh on 2012-10-01
```
lspci -nnk | grep -iA2 vga
``` 

Thanks

---

### Post by piqueta on 2012-10-01
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 12)
	Subsystem: Lenovo Device [17aa:3952]
	Kernel driver in use: i915
--
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Madison [Mobility Radeon HD 5000 Series] [1002:68c0]
	Subsystem: Lenovo Device [17aa:3952]
	Kernel driver in use: fglrx_pci

Thanks for the help.

---

### Post by NikTh on 2012-10-02
I think here is the problem. 

You have 2 graphic cards enabled. Its the known Hybrid graphics. Intel & AMD. Ubuntu and linux generally not going well with hybrid especially with Intel & AMD. 

If it was Nvidia and Intel , there is a project called Bumblebee that can work, but for AMD & Intel I don't know. 

You installed the closed source driver fglrx for AMD , open the catalyst center and see if you can disable one card from there , or boot into BIOS config page and see if you can disable the Intel (integrated) graphics from there.

Also there is a project that I don't know if works well , but you must have the Open Source driver for AMD/ATI , that means you have to uninstall the fglrx. 
Here it is: [https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

Here is another thread from these forums. Read it : [http://ubuntuforums.org/showthread.php?t=1930450/](http://ubuntuforums.org/showthread.php?t=1930450/)

So , my suggestions are 

1) Try to disable one of the two cards . 

2) Try to uninstall fglrx driver and enable and use "vga_switcheroo"

Thanks

---

### Post by piqueta on 2012-10-02
Ok, so I've decided to uninstall drivers first and when I did it and rebooted, GUI seemed to be different. I ran MyUnity again and there was no error, I could access all the features. Should I proceed to enabling switcheroo and disabling one of the cards?

---

### Post by NikTh on 2012-10-02
> **piqueta said:**
> Ok, so I've decided to uninstall drivers first and when I did it and rebooted, GUI seemed to be different. I ran MyUnity again and there was no error, I could access all the features. Should I proceed to enabling switcheroo and disabling one of the cards?

My opinion is , If you have no problem , then leave it as it is. 

Mark the thread as solved. :) :)

Run again the commands and post the results 
```
/usr/lib/nux/unity_support_test -p**
```**

```
lspci -nnk | grep -iA2 vga
```

Thanks

---

### Post by piqueta on 2012-10-02
```
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Mobile 
OpenGL version string:  2.1 Mesa 8.0.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

```

```
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 12)
	Subsystem: Lenovo Device [17aa:3952]
	Kernel driver in use: i915
--
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Madison [Mobility Radeon HD 5000 Series] [1002:68c0]
	Subsystem: Lenovo Device [17aa:3952]
	Kernel driver in use: radeon

```

Here's the result.

Theank you for your help.

---

