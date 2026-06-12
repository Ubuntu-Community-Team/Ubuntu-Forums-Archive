---
title: "IDT High Definition Audio Codec"
date: 2016-02-11
forum: New to Ubuntu
---

### Post by Imola on 2016-02-11
Hello.

I just switched from Windows 7 to Ubuntu 14.04 (I have never used any other kind of OS besides Windows 7 before, so I have no idea how to achieve the things I want).

I don't have any particular problem with the sound but I really miss the sound I used to have in Windows. It was so much better and I could customise it. I just simply cannot install the driver (this and many other things - and for a beginner like me it's annoying as hell).

I had this IDT High-Definition Audio driver for my Dell Inspiron, Windows installed automatically. If any other information is needed in order to achieve a solution ask me but please write down how and/or where do I get it in this OS. 

Could somebody please help me how to get this little thing work?

---

### Post by Frogs Hair on 2016-02-12
I too have IDT combined with an SRS premium sound mixer on the Windows 7 side of my dual boot and they simply don't make a Linux Driver. IDT was sold to a different company and the Windows driver hasn't been updated since. Some Win 10 users are having the same problem with IDT because the sound card software is incompatible.

---

### Post by Nuno_Abreu on 2016-02-12
What kind of difference do you have comparing to ALSA (Advanced Linux Sound Architecture)? Do you happen to use OSS (Open Sound System - it's obsolete)?

---

### Post by Geoffrey_Arndt on 2016-02-12
Yes, . . . as far as Mr. Google knows, this sound system is only supported on Windows OS's . . . no drivers furnished by the ODM's (original design manufacturers) for Linux, BSD.    

For best overall user experience, for next PC, consider . . .   

[http://linuxpreloaded.com/](http://linuxpreloaded.com/)

---

### Post by Yellow Pasque on 2016-02-12
> **Imola said:**
> I just simply cannot install the driver. I had this IDT High-Definition Audio driver for my Dell Inspiron, Windows installed automatically (this and many other things - and for a beginner like me it's annoying as hell

I'm not really sure what you're going on about with the driver. The driver is built into the Linux kernel and loaded automatically (or else you wouldn't have any sound). It's actually easier on Linux because it works out of the box without you or the OS doing a thing (assuming you have a modern version of kernel).

> I really miss the sound I used to have in Windows. It was so much better and I could customise it. 

Don't hold your breath waiting for SRS Labs (now owned by DTS) to open source their software and/or make a Linux version. They're all about making money on the licensing and patents.
There's a lot of notebook makers using proprietary sound enhancers (Asus has "Sonicmaster" and Lenovo uses some kind of special Dolby-made software). Those things are terrible for Linux users. The bottom line is that you should use a notebook that doesn't need any proprietary "3D sound" voodoo to have decent audio quality.

About the best you can do with your current notebook is play with equalizers and DSP plugins and maybe you can get it closer to the Windows sound. Maybe not...

---

### Post by p-lazar on 2016-03-25
There might be a solution... kind of:

[http://ubuntuforums.org/showthread.php?t=2080315](http://ubuntuforums.org/showthread.php?t=2080315)

It consists of installing hda-jack-retask to manually remap audio pins (work usually done by sound driver, but since that's not possible, you will have to do it manually). Just beware, it is trial-and-error solution.

---

