---
title: "[SOLVED] Desktop Ubuntu Freezes"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by blaze41 on 2008-12-01
Ok still having problems with my desktop computer. Everytime i download updates for my desktop, i restart my computer and after i enter login information my screen has horizontal lines and freezes. I cant do anything i need help please! Is there a way to disable or go back or find out what is causing it.... I have reinstalled Ubuntu 3 times and still kind find out the exact update that screws it up.

---

### Post by nhasian on 2008-12-01
have you tried using the previous kernel to see if that resolves your problem?  in my grub bootup menu i have 3 different kernels now.

---

### Post by Catalyst2Death on 2008-12-01
What video card/driver are you using? If you're using a proprietary driver and you upgrade the kernel, you have to recompile the driver for the new kernel.  This may cause your problem, but usually X11 is smart enough to use the vesa driver, and you wouldn't necessarily notice.  The ATI drivers are notorious for graphics corruptions etc. So if it is ATI, I would be highly suspect of the drivers...

---

### Post by blaze41 on 2008-12-01
New here... how do i do that?

---

### Post by blaze41 on 2008-12-01
Ok figured that part out. I tried a diffrent one and it still does the same thing.

---

### Post by blaze41 on 2008-12-01
The video card is a generic one on a motherboard... how do i know what it is?

---

### Post by linux_tech on 2008-12-01
Try running a few commands from the terminal.
What is the output of:
```
lspci | grep -i vga
```
```
gedit /etc/X11/xorg.conf
```
```
sudo lshw -C video
```

---

### Post by blaze41 on 2008-12-02
```
lspci | grep -i vga
```
Output: ```
Nothing
```

```
gedit /etc/X11/xorg.conf
```
Output: ```
Section "Device"
             Identifier: "Configured Video Device"
        Endsection
        Section "Monitor"
             Identifier: "Configured Monitor"
        Endsection
        Section "Screen"
             Identifier: "Default Scree"
             Monitor: "Configured Monitor"
             Device: "Configured Device"
        Endsection
```

```
sudo lshw -C video
```
Output: ```
*-Display UNCLAIMED
        Description: VGA Compatible Controller
        Product: 82810E DC-133 (CGC)
        Vendor: Intel Corporation
        Physical ID: 1
        Bus Info: PCI@0000:00:01.0
        Version: 03
        Width: 32 Bits
        Clock: 66mhz
        Capabilities: Pm bus_master Cap list
        Configuration: Latency=0
```

---

### Post by blaze41 on 2008-12-04
I said screw it. bought a new... well used video card and that seemed to solve the problem

---

