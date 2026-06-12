---
title: "[Beginners]* Question"
date: 2008-08-09
forum: Programming Talk
---

### Post by solutions on 2008-08-09
:guitar:
Hm, I'm wondering, I have the kernel source code. I've downloaded this from [www.kernel.org](www.kernel.org). How can I go from this .tar.gz file to ubuntu-8.04.1-desktop-i386.iso file ? All of the kernel compiling tutorials end up with with 3 files in the boot directory System.map-2.6.25 
config-2.6.25 
vmlinuz-2.6.25. I want to understand how Ubuntu was created so I can begin studying OS development. Please anyone with the understanding of how to compile ubuntu-8.04.1-desktop-i386.iso give input.

*EDIT*: If my question doesn't make any sense: I will rephrase it += What i'm trying to say is, how can I create my own version of Ubuntu so I can mod it with a publicly available version of the kernel source?

---

### Post by tamoneya on 2008-08-09
I am a little confused but i think you need this: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

Just change the kernel version number in "3 Download The Kernel Sources "

---

### Post by thirddeep on 2008-08-09
Well, if you are serious about understanding how things fit together (as in the entire OS), look up "linux from scratch".

Thd.

---

### Post by LaRoza on 2008-08-09
> **solutions said:**
> :guitar:
Hm, I'm wondering, I have the kernel source code. I've downloaded this from [www.kernel.org](www.kernel.org). How can I go from this .tar.gz file to ubuntu-8.04.1-desktop-i386.iso file ? All of the kernel compiling tutorials end up with with 3 files in the boot directory System.map-2.6.25 
config-2.6.25 
vmlinuz-2.6.25. I want to understand how Ubuntu was created so I can begin studying OS development. Please anyone with the understanding of how to compile ubuntu-8.04.1-desktop-i386.iso give input.

*EDIT*: If my question doesn't make any sense: I will rephrase it += What i'm trying to say is, how can I create my own version of Ubuntu so I can mod it with a publicly available version of the kernel source?

See the sticky in "Other OS Talk" about making your own distro. [http://ubuntuforums.org/showthread.php?t=852868](http://ubuntuforums.org/showthread.php?t=852868)

The way Ubuntu (and other distros) are created is not by recompiling everything, but by packaging.

You can customize the kernel if you want, and there is another thread on that somewhere else (but your questions are showing you don't know where to start, so I wouldn't suggest by starting there)

(The format of your thread title "[Beginners]" isn't very helpful. Perhaps you could read the "How to ask questions" article, see the link in my sig)

---

