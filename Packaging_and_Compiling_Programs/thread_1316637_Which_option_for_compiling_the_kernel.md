---
title: "Which option for compiling the kernel?"
date: 2009-11-06
forum: Packaging and Compiling Programs
---

### Post by praytor on 2009-11-06
Hi, I was reading the documentation here: [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile) and it's great but I don't completely understand it.  

Under the section "Get the kernel source" it presents 3 options.  The first option is for people who need the bleeding edge source.  But I don't understand the difference between option 2 and 3.  Option 2 downloads the "source archive" and option 3 downloads the "source package."  What is the difference?

Option #3 emphatically states that it is not the same as option #2 and looking down further I can see the commands are almost totally different but what are the reasons to choose one way rather than the other?  Am I restricted from making certain modifications to the kernel if I use option 2 or 3?  

Also, after installing the kernel, what comes next?  It means I have 2 possible kernels on my system right?  How do I get Ubuntu to use the modified one?  

Thanks in advance.

---

### Post by SevenMachines on 2009-11-07
option 2 lets you download the packaging source used to create the kernel packages you install in ubuntu (ie linux-image-2.6.30-generic.deb type packages). This has all the source code you need PLUS the debian packaging code needed to create .deb packages.
using this you can modify the kernel source then create and install your own debian packages.

option 3 downloads the just the kernel source used to generate the packages in option 2 but not the packaging code, you can modify and compile the source ubuntu used to create their debian packages but you don't create any packages yourself, its just kernel source you can compile as you would any other source

Installed kernels are chosen by your bootloader, once you've installed new ones run, for grub, 'update-grub' and then you should be able to choose from a list of installed kernels when you boot

---

### Post by praytor on 2009-11-07
Thanks a lot, SevenMachines!  Looks like option 2 is better suited for me.  :p

---

