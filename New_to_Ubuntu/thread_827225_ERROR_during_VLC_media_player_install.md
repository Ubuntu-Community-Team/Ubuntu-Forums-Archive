---
title: "ERROR during VLC media player install"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by xdwmx on 2008-06-12
I was trying out the live CD of 32bit Ubuntu 8.04 on my laptop and I tried to install VLC using "Add/Remove Applications". It downloaded the VLC files and then after it appeared to have been installed I got the following error.

```
VLC media player cannot be installed on your computer type (i386)

Either the application requires special hardware features or the vendor decided to not support your computer type.
```

Other applications install successfully and I have tried to install VLC on my desktop with the same results.

My laptop has an AMD Turion 62 X2 processor and my desktop has a typical P4. Is there problems with the servers?

Anyone got any ideas?

---

### Post by drs305 on 2008-06-12
> **xdwmx said:**
> I was trying out the live CD of 32bit Ubuntu 8.04 on my laptop and I tried to install VLC using "Add/Remove Applications". It downloaded the VLC files and then after it appeared to have been installed I got the following error.

```
VLC media player cannot be installed on your computer type (i386)

Either the application requires special hardware features or the vendor decided to not support your computer type.
```

Other applications install successfully and I have tried to install VLC on my desktop with the same results.

My laptop has an AMD Turion 62 X2 processor and my desktop has a typical P4. Is there problems with the servers?

Anyone got any ideas?

It looks like the liveCD thinks it is installing a 32-bit version (i386) on a 64-bit machine. The VLC version in the repository should match the type of processor you have. Did you just try this installation via synaptic? I have VLC on both 32 and 64-bit machines and have never seen such a message. If you downloaded a file from the videolan site you may have grabbed the wrong version.

If you (or ubuntu) aren't sure what architecture your machine has:
```
uname -m
```
If it says x86_64, it thinks you have a 64-bit computer.

---

### Post by xdwmx on 2008-06-12
I installed using the "Add/Remove Applications" manager, not Synaptic. The Ubuntu version is 32bit, my laptop is 64bit and my desktop is 32bit. The same error appears on both.

---

### Post by wolfen69 on 2008-06-12
remove vlc and add the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repos. then ```
sudo apt-get clean
``` then
```
sudo apt-get install vlc
```

---

