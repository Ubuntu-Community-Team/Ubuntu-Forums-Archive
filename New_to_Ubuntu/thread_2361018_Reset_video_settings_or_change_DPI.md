---
title: "Reset video settings or change DPI"
date: 2017-05-11
forum: New to Ubuntu
---

### Post by artemkyz89 on 2017-05-11
Hello.
After using kvm-121 d-link, my fonts became small. And after start system my resolution became 1024x768, but really i used always 1920x1080. How I can restore my default settings (resolution 1920x1080 and normal fonts size (dpi))?

---

### Post by artemkyz89 on 2017-05-11
add
After installing Nouveau drivers all works. I try install again Nvidia Driver, but he find my old config. Where is config save?

---

### Post by Autodave on 2017-05-12
Where are you getting the Nvidia driver from? I always get mine from the repositories and have never had a problem.

---

### Post by SeijiSensei on 2017-05-13
I've had the problem of tiny fonts when using NVIDIA cards with a TV.  I've had to use
```
sudo nvidia-xconfig
```
to create a basic /etc/X11/xorg.conf file to match the NVIDIA device, then modify it to add "Option DPI 96x96" to the "Monitor" section of the file.  On this machine that section of xorg.conf looks like this:
```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
    Option         "DPI" "96x96"
EndSection

```
You may have different sync values.  Note the use of quotation marks around DPI and 96x96.

---

