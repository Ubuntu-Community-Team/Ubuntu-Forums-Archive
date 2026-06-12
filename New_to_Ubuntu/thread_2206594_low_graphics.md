---
title: "low graphics"
date: 2014-02-19
forum: New to Ubuntu
---

### Post by scallion172 on 2014-02-19
When ubuntu starts, a screen comes up saying I'm in low graphics mode. Then I really can't do much. What should I do?

---

### Post by open2reason on 2014-02-19
Hi,
Can you please let us know what version of Ubuntu are you attempting to run and if possible the machine name, cpu name and name of any graphics card if used?

This information would help a lot when deciding how to help you.

Thanks

---

### Post by scallion172 on 2014-02-19
ubuntu v.13.10
Dell dimension 4500
Don't really know the rest sorry

---

### Post by varunendra on 2014-02-20
Welcome to the forums scallion172 !

When you are booted into Ubuntu, open a terminal (Ctrl-Alt-T) and run the following command -
```
lspci -nnk | grep -iA3 vga
```

Post back its output here, it will tell us what graphics card your system has and whether a suitable driver is loaded for it or not.

While posting the output, please use the 'Code' tags to preserve its formatting. To see how to use 'Code' tags, please follow the link in my signature.

---

### Post by grahammechanical on 2014-02-20
You can try loading into Recovery mode. With Ubuntu 13.10 we find Recovery Mode in the Advanced Options for Ubuntu sub-menu. There we can select Resume. That will try to load Ubuntu using an open source video driver. The user experience will not be very good because it is an un-accelerated fall back video mode. But it does get us a desktop to work from.

Regards.

---

### Post by mastablasta on 2014-02-20
command can be copied and pasted into terminal...

---

### Post by open2reason on 2014-02-20
The system spec may well be some of [ftp://ftp.dell.com/Pages/Drivers/dimension-4500.html](ftp://ftp.dell.com/Pages/Drivers/dimension-4500.html) [https://en.wikipedia.org/wiki/Dell_Dimension#Dell_Dimension_4xxx_series](https://en.wikipedia.org/wiki/Dell_Dimension#Dell_Dimension_4xxx_series) which might suggest a video of > nVidia 128MB DDR GeForce4 Ti 4600 which if correct [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia) may offer advice [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) on making ubuntu function with your kit.

---

