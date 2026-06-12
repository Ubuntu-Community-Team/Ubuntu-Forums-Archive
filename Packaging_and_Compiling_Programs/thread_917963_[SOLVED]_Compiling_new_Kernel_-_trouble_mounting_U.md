---
title: "[SOLVED] Compiling new Kernel - trouble mounting USB drive."
date: 2008-09-12
forum: Packaging and Compiling Programs
---

### Post by VMC on 2008-09-12
I'm learning how to compile and use a new kernel, and I'm having difficulty mounting USB flash drives.

If I just compile with very little changes everything works okay. I found I can remove languages, select my CPU model, remove extra network cards except mine and then it's okay.

It's when I try to remove other stuff is where USB will not mount. I don't touch the USB settings at all. I have thought all along it's in there somehow. Now I'm thinking it's the format of the USB flash drives itself, and not the USB settings. I was thinking it may have to do with the "FILE SYSTEMS" , but I don't touch those settings either.

 Remember, if I compile it with few changes the USB mounts okay. It's just other seemingly unrelated items that it refuses to mount USB. Below is the steps I take. I've taken them from the "[Ubuntu Master Kernel Thread]("http://ubuntuforums.org/showthread.php?t=311158")", and made them simple steps that I use.

===Get tools
1. sudo apt-get install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev wget libncurses5 libncurses5-dev
2. cd /usr/src
3. sudo -s
===Get the Kernel and extract it
4. wget -c [http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.26.3.tar.bz2](http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.26.3.tar.bz2)
   OR [www.kernel.org](www.kernel.org)
5. tar -xvjf linux-2.6.26.3.tar.bz2
===Link to Kernel Source
6. rm -rf linux
7. ln -s /usr/src/linux-2.6.26.3 linux
8. cd /usr/src/linux
===GET ".config"
9. cp /boot/config-$(uname -r) .config && yes "" | make oldconfig
===APPLY OPTIONS
10. make xconfig or make menuconfig
===Start the compile process
11. make-kpkg clean
12. time make-kpkg  --revision=1custom --initrd kernel_image kernel_headers modules_image|tee MAKE_KPKG_LOG
===Install new Kernel
13. cd .. && dpkg -i linux*2.6.26*.deb

---

### Post by jpkotta on 2008-09-13
Post a diff of the working and non-working .config files.
```
diff -u working.config non-working.config
```

---

### Post by VMC on 2008-09-14
I found the problem. When all else fails read the messages!

I read "dmesg" and I just passed by the answer staring me right the the face. It said something about couldn't read the filesystem and then gave the answer. "NLS ISO 8859-1". It just didn't register at the time. Only until I went inside the "/lib/modules" and discovered the NLS directory that it hit me. That's it.

I was told that English speaking people only needed the three codes:
 Codepage 437 (United States, Canada)
 ASCII (United States)
 NLS UTF-8
So all the others I removed without reading. That was my fault. I finally read this on,
NLS_ISO8859_1:
"If you want to display filenames with native language characters
from the Microsoft FAT file system family or from JOLIET CD-ROMs
correctly on the screen, you need to include the appropriate
input/output character sets. Say Y here for the Latin 1 character
set, which covers most West European languages such as Albanian,
Catalan, Danish, Dutch, English, Faeroese, Finnish, French, German,
Galician, Irish, Icelandic, Italian, Norwegian, Portuguese, Spanish,
and Swedish. It is also the default for the US. If unsure, say Y."

There was the answer. Plain and simple. I just assumed that I could removed all languages that I didn't need. After all, I kept seeing German, Bulgarian, Chinese  and the like. It just never occurred to me that a filesystem mechanism would be among the mix.

---

